About me
============================

I am a postdoctoral fellow  at the National Institutes of Health, laboratory of NIMH director Joshua Gordon.
There, I implant, infect, and stimulate the brains of mice in order to understand how brain regions 
communicate and to find novel ways to improve psychiatric conditions. After setting up a project's surgery 
and behavioral testing schedule, I work on ingesting and processing data and deploying generated visualization/statistics to an internal website.

## Interests
* Rich data
* Organization of robust data analysis pipelines
* Spontaneous and perturbed brain activity
* Focus on estimation rather than prediction

## Work principles
* Industry-grade code for academia-grade research
* Repoducible data analysis workflows without stifling innovation
* Inferential statistics
* Unit testing and command-line interface for every project
* Carry every statistical/mental model to its breaking point and learn from how it breaks

## Organizational accomplishments at NIH
* Wrote a core suite of data analysis 
  - Multichannel (up to 64) sensor readings at 30kHz
  - Modular, scalable, adaptable
  - Results in a condensed MySQL database (~50TB -> 400Gb)
  - Forked by all other sensor users in the organization
* Set up a complete pipeline for ingestion -> internal html report publishing 
* Wrote automated maze software (Python) and accompabying embedded realtime stimulation (C)/recording controller
* Trained multiple junior personnel in using tools I've developed
* Introduced git workflow to organization
* Unit testing for every repo

## Goals for next career step
* Small- to midsize group of enthusiasts to join
* Team that includes experts in stats/ML and devops 
* Novel sensors resulting in rich datasets
* Semi-automated statistical inference/ML
* Real-time processing with potential for realtime manipulation

## My research at NIH 
### Inter-region communication
How do brain regions communicate? Is that even a relevant question? Is the brain modular at all? One would wish to have access to activity of many thousands of neurons recorded simultaneously from many regions in order to infer causality at a useful scale. Local field potentials are easier, but observing them passively is useless to this end.

### Perturbation
Perturbation is essential because of these limitations. I perturb distal parts of neurons, but not the cell bodies. In a first brain surgery, I inject the virus carrying code for light-sensitive proteins ChR2 in ventral hippocampus, wait for it to travel to prefrontal cortex, and shine my laser there rather than ventral hippocampus. In a second brain surgery, I implant recording 
leads in both brain regions.

### Applications
People with psychiatric conditions such as schizophrenia have impaired working memory. I use a working memory maze task in mice 
as I perturb neurons as described above. Neuronal activity under such perturbation during the task and outside of the maze may show us how neuronal communication
is impaired in psychiatric disorders. 