---
title: ""
nav: true
---

# The Sensitivity Analysis For Everyone (SAFE) toolbox #

<img src="drawing2.png" alt="SAFE logo" style="width:20%;" >

The SAFE Toolbox provides a set of functions to perform Global Sensitivity Analysis. 
It implements several methods, including the Elementary Effects Test, Regional Sensitivity Analysis,
Variance-Based (Sobol’) sensitivity analysis and the PAWN method. 
SAFE was originally developed for the Matlab/Octave environment [(Pianosi et al. 2015)](/index#references)
but was then made available also in R and Python. <br>

### Who uses SAFE ###

SAFE was first released in 2015. Until 2022, when the code was moved to GitHub,
SAFE was distributed open-source and free-of-charge through a bespoke 
website (safetoolbox.info) upon filling in a download request. This distribution model enabled us to monitor 
the number of downloads and gathering contact details and some basic information about the users (affiliation, 
role, and area of expertise). <br>
In 2018, we used these information to run a survey of the users community 
at the time, and get their evaluation of SAFE. 
The results of this survey are discussed in [Pianosi et al (2020)](/index#references). <br>
As of February 2023, when the safetoolbox.info website 
was closed and the code moved to Github, the toolbox had been downloaded over 4000 times
from students and researchers from 160 different countries and across a range of areas in
engineering and science. A visual summary is available [here](./Statistics.md/). <br>

### Download ###

The SAFE Toolbox is available on GitHub in three versions:
* [Matlab version](https://github.com/SAFEtoolbox/SAFEtoolbox/tree/master/SAFE-matlab/)
* [Python version](https://github.com/SAFEtoolbox/SAFEtoolbox/tree/master/SAFE-python/)
* [R version](https://github.com/SAFEtoolbox/SAFEtoolbox/tree/master/SAFE-R/)

Use SAFE freely but please cite the paper [Pianosi et al. (2015)](/index#references) in any publication
presenting results obtained using SAFE.

### Learn more ###

* [Scientific and technical documentation](./Documentation.md/)
* [Applications](./Applications.md/)
* [PAWN method](./Pawn.md/)
* [Frequently Asked Questions](./Faqs.md/)

<!--
### Install iRONS locally ###
To install iRONS on your computer: [Install iRONS](./Install.md/)
-->

### References ###
Pianosi, F., Sarrazin, F., Wagener, T. (2015), A Matlab toolbox for Global Sensitivity Analysis, Environmental Modelling 
& Software, 70, 80-85. [doi.org/10.1016/j.envsoft.2015.04.009](https://doi.org/10.1016/j.envsoft.2015.04.009)

Pianosi, F., Wagener, T., Sarrazin, F. (2020), How successfully is open-source research software adopted? Results and implications of surveying the users of a sensitivity analysis toolbox, Environmental Modelling & Software, 124. [doi.org/10.1016/j.envsoft.2019.104579](https://doi.org/10.1016/j.envsoft.2019.104579)

### License
This software is distributed under the [GNU Public License Version 3](https://www.gnu.org/licenses/gpl-3.0.en.html).

### Contributors ###

SAFE was originally developed in Matlab by Francesca Pianosi, Fanny Sarrazin and Thorsten Wagener 
at the Department of Civil Engineering at the University of Bristol. The R version was developed
by Isabella Gollini and Valentina Noacco. The Python Jupyter Notebooks were developed by
Andres Penuela-Fernandez.

### Acknowledgements ###

The development of SAFE was originally supported by the UK Natural Environment Research Council 
through the Consortium on Risk in the Environment: Diagnostics, Integration, Benchmarking, Learning 
and Elicitation (CREDIBLE) [NE/J017450/1].
The further development of SAFE, including the implementation of the Python version, 
has been supported by the UK Engineering and Physical Sciences Research Council through 
a Living with Environmental Change Fellowship [EP/R007330/1] and the EPSRC Impact Acceleration Account.

<!--&nbsp;
<div class="row">
  <img src="logo-full-colour.png" alt="Uni logo" style="width:20%;" hspace="20"> <img src="EPSRC_logo.png" alt="EPSRC logo" style="width:25%;" hspace="00">
<div >
-->
