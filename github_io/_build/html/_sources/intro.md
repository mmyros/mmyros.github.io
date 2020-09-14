Maxym Myroshnychenko
============================

Welcome to the page dedicated to my shameless self-promotion. I am a postdoc at the National Institutes of Health in Bethesda, MD.
There, I implant, infect, and stimulate the brains of mice. This is done in order to understand better how brain regions 
communicate, and to find novel ways to improve psychiatric conditions.

Let's unpack that.
## Research goals at NIH 
### Inter-region communication
This is a hard question. One would need so, so many neurons recorded simultaneously from many regions in order to start 
to believe the analysis. Local field potentials are easier, but observing them passively is useless to this end.
Therefore, perturbation is essential. I perturb distal parts of neurons, but not the cell bodies (hopefully).  
### Applications
People with psychiatric conditions such as schizophrenia have impaired working memory. I use a working memory task in mice 
as I perturb the neurons as described above. 
 
 

## Some web pages with notes and open-source data results
* [Here](http://mmyros.github.io/mmyros_iu.github.io/) is my old page from grad school
* [Here](dev.to/mmyros) are my notes on development in python and jupyter, primarily to answer FAQs from students
* [Here](http://mmyros.herokuapp.com/) are some interactive pretty visualizations/dashboards of data I made using generative models
* [Here](https://mmyros.gitlab.io/web-steinmetz/intro.html) are some visualizations of an open-source dataset
* [Here](https://mmyros.github.io/data_pfc3/intro.html) is another

## CV
* [Informal](), 
* [formal as html](https://mmyros.github.io/extras/cv_myroshnychenko.html)
* [formal as pdf](https://www.dropbox.com/s/12cgy9fgsjeldvp/CV_Myroshnychenko%2C_Maxym.pdf?dl=0) 

## My open-source projects on github
Outside my day job, I contribute to open-source projects. I made a few on my own time that are not used in the lab,
but may help someone out there.
 
[Overview](https://github.com/mmyros) 
### Some highlights
* [Cluster quality](https://github.com/mmyros/cluster_quality): measurements of how well spikes were isolated from noise.
Parallelized and packaged into a CLI interface.
* [Phy extras](https://github.com/mmyros/phy_extras) are enhancements to the popular Phy interface for inspecting 
clustering. Includes:
    -    Alt+R to cycle through raw data and waveform views: raw, highpass, mean+highpass, median+highpass, highpass+median, highpass+mean
    -    s for Scrub outliers using Local Outlier Factor (also implemented are Robust covariance, One-Class SVM, and Isolation Forest. See plugins/custom_split.py)
    -    t for Time split using gaussian hierarchical model
    -    x for k-means split
    -    d for GAC split (Due to Swindale lab, gradient ascent clustering (GAC) algorithm, a variant of the mean-shift algorithm)

* [PulsePal port to Python 3](https://github.com/mmyros/PulsePal): Port to Python 3 of a mainly-Matlab project 
from Sanworks LLC. They had some Python code, but it broke a while ago.
 
