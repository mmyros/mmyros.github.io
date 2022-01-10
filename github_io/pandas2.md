Very often, you need to do something to groups of rows of a dataframe that match some condition, for instance a certain mouse or brain region. The most intuitive solution is to use a for loop.

For instance, let's start with this dataframe:

|    | experiment                | brain_region   |   neuron |   Mean ISI |
|---:|:--------------------------|:---------------|---------:|-----------:|
|  0 | bucket_1_m026_1568757659_ | pfc            |        0 |    3.08281 |
|  1 | bucket_1_m026_1568757659_ | pfc            |        1 |    8.37044 |
|  2 | bucket_1_m026_1568757659_ | pfc            |        2 |   38.5265  |
|  3 | bucket_1_m026_1568757659_ | pfc            |        3 |   31.795   |
|  4 | bucket_1_m026_1568757659_ | pfc            |        4 |    3.43186 | 

We can loop over experiments, brain regions, and neuron like so:
```python
log_mean_isi = []
for neuron in df['neuron'].unique():
    for brain_region in df['brain_region'].unique():
        for experiment in df['experiment'].unique():
            sub_df=df[
                (df['experiment']==experiment) & 
                (df['brain_region']==brain_region) & 
                (df['neuron']==neuron) 
            ]
            log_mean_isi.append(np.log(sub_df['Mean ISI']).values)
print(np.hstack(log_mean_isi))
```
```python 
[ 1.12584188  2.19215951 -1.98074317 -0.25722232  2.1247061   0.0063244 0.92415014 -1.93038317  3.6513468   2.28266164  1.39365976 -3.23681353  3.459308    1.48402753 -0.65003803  1.4140086   1.23310109 -0.8740564  1.29957486 -0.60594385 -0.61921541  4.51176028  0.5622578   3.48668087 -1.57394565 -1.15482997  3.62078013 -0.64878302 -2.08398518  0.28354575 -0.92326873 -2.23523802 -1.15944804 -1.16315081  1.29454247 -0.89566237  0.72300259 -1.38527266  1.3694298   2.95919545  3.07555102 -1.38317331  2.3510588  -1.68488011  2.15864159  2.92067342  0.20249933  1.76685816 -1.14606501 -2.54545905  2.17651238  2.49333615 -1.08762839 -1.10690211  1.79675315  1.08438564 -1.61687289  3.64009558  2.50376142  3.53577889 -2.31447026 -0.9560716  ...]
```

 However, nested for loops are evil for many reasons. Let's use the `groupby` command:

```python
log_mean_isi=[]
for index, sub_df in df.groupby(['neuron', 'brain_region', 'experiment']):
    log_mean_isi.append(np.log(sub_df['Mean ISI']).values)
print(np.hstack(log_mean_isi))
```
or even in one line:
```python
mean_isi_list=[np.log(sub_df['Mean ISI']).values for index, sub_df in df.groupby(['neuron', 'brain_region', 'experiment'])]
print(np.hstack(mean_isi_list))
```
Much more readable and efficient! Furthermore, the `index` part can be used for reconstructing the modified dataframe. I might make a post on that in the future.