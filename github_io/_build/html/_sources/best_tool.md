# Best tool for the job
Rather than reinvent a tool, it's better to use an existing one and contribute to its improvement. But it has to be a good
one to begin with! Here are my favorites:
- Data management:
  - large project (>3Gb): `datajoint` (or another DAG + *sql)
  - small project (<3Gb): `NetCDF` through Xarray
  
- Array manipulation:
  - First choice: Xarray (`df.to_xarray()`)
  - Second choice: Pandas longform (`an_xarray.to_pandas()`)
  
- Speedup:
  - `numba` for single-threaded performance
  - `joblib` and `datajoint` for parallelization  

- Visualization, must have faceting: 
  - Quick: `an_xarray.plot(col='column_dimension')`
  - Powerful+interactive: `Holoviews`+`datashader`
  - Quick and powerful: `df.hvplot(col='column_dimension')`
  - Beautiful: altair (+altair_save to reduce file size)
  
- Estimation, Bayes, Monte Carlo, bespoke ML:
  - `numpyro` for speed and future potential
  - `stan` for examples and debugging
  - `arviz` to use either of the above interchangeably. Bonus: Xarray!
  
- Sharing figures:    
  - `Jupyter-book`
  - `Gitlab pages`
  - `nbconvert` to html 
  - Excited for `papermill`