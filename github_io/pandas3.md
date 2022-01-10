# Pandas tools you didn't know you needed 3: groupby+from_records


Say we are trying to fetch unique instances of several conditions: 
```python
index_cols = 'brain_region', 'stim_type', 'frequency', 'phase_delay_frac', 'stim_amplitude', 'phase_type', 'brain_region'
```
Each of these dataframe columns contains several unique entries repeated multiple times. Eg `brain region` takes the values of `pfc` and `v_hpc`. 
Let's use an example key to examine:
```python
# Fetch an entire day's worth of events:
summary = (SpikePhase * MazeTrials & key).fetch(format='frame').reset_index()
key = dict(fid='bucket_5_m036_1570900150_', single_unit=1, phase_type='theta_hilbert_bessel')
for brain_region in summary['brain_region'].unique():
  for stim_amplitude in summary['stim_amplitude'].unique():
    for phase_delay_frac in summary['phase_delay_frac'].unique():
      for frequency in summary['frequency'].unique():
        for phase_type in summary['phase_type'].unique():
          for stim_type in summary['stim_type'].unique():
             # specify primary key for fetching and populating
             group_key['stim_amplitude'] = stim_amplitude
             group_key['phase_delay_frac'] = phase_delay_frac
             group_key['frequency'] = frequency
             group_key['stim_type'] = stim_type
             group_key['phase_type'] = phase_type
             group_key['brain_region'] = brain_region
# fetch specific to treatment
             spikes_phases = (MazeTrials *
                              * EventRelatedSpikesAndPhases 
                              & group_key
                              ).fetch(format='frame')
```
becomes simply:
```python
# Iterate over indices of interest:
for index, dff in summary.groupby(index_cols):
    # make a dictionary holding values of index
    group_key = {key: value for (key, value) in zip(index_cols, index)}
    # fetch specific to treatment
    spikes_phases = (MazeTrials * EventRelatedSpikesAndPhases & group_key).fetch(format='frame').reset_index()
```
Note the absence of nested for loops! 
Once we have all treatment-specific events, we can do some computation on them within this loop and build the list of computed results. In the last line of the snippet below, we will concatenate them into a dataframe: 
```python
    # ...continued from above
    # do some computation here
    spikes_phases['log_stim_amplitude'] = np.log(spikes_phases['stim_amplitude'])
    # add to our list of dataframes (preallocated outside the loop):
    group_results.append(spikes_phases)
# Concatenate dicts into a dataframe:
group_df=pd.DataFrame.from_records(group_results).set_index(index_cols)
```
The columns of group_df now have our index_cols, original data column, and our computed column:
```python
> group_df.columns
Index(['brain_region', 'stim_type', 'frequency', 'phase_delay_frac', 'stim_amplitude', 'phase_type', 'spike_phase','log_spike_phase'])
```