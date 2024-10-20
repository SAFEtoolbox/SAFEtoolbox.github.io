---
title: Documentation
nav: true
---

[<img src="drawing2.png" alt="SAFE logo" style="width:20%;" >](./index.md/) <br>

<!-- [Home](./index.md/) - [Documentation](./Documentation.md/) - [Applications](./Applications.md/) - [PAWN](./Pawn.md/) - [FAQ](./Faqs.md/)-->

<!--## Scientific and Technical Documentation-->

This page lists some of the scientific publications developed by our research group about SAFE and Global Sensitivity Analysis in general. These are useful readings to learn about the rationale of the SAFE toolbox and how to use it, as well as learning more broadly about GSA: what kind of questions GSA can address, how to choose the most appropriate GSA method for the problem at hand and how to make key set-up choices. This page also includes links to a set of interactive Jupyter Notebooks, which can be run locally (in Python) or directly from the browser, and that provide a hands-on introduction to SAFE/GSA.<br>

**Interactive Jupyter Notebooks**

These notebooks provide simple application examples of GSA for a range of different purposes and models. They are meant to be used as a quick, hands-on introduction to SAFE/GSA. The notebooks can downloaded and run locally using [jupyter](https://jupyter.org/) (and Python), or they can be run directly from the browser using the free [JupyterLite](https://jupyterlite.readthedocs.io/en/stable/) service (this means you do not need to have neither Python or SAFE installed on your computer). Currently available notebooks provide examples of: <br>
-- Using GSA to identify the most important parameters for model calibration - hydrological model example:
[Download](https://github.com/SAFEtoolbox/demos/blob/main/content) | 
[Run from browser](https://safetoolbox.github.io/demos/lab/index.html?path=Hyd_example.ipynb)<br>
-- Using GSA to find the key controls of a system - ecological model example: 
[Download](https://github.com/SAFEtoolbox/demos/blob/main/content) | 
[Run from browser](https://safetoolbox.github.io/demos/lab/index.html?path=Eco_example.ipynb)<br>
-- Using GSA to enhance model-informed decisions under uncertainty - epidemiological model example: 
[Download](https://github.com/SAFEtoolbox/demos/blob/main/content) | 
[Run from browser](https://safetoolbox.github.io/demos/lab/index.html?path=Flu_example.ipynb)
<!-- old links:
https://mybinder.org/v2/gh/SAFEtoolbox/Miscellaneous/HEAD?urlpath=notebooks/Introductory_Notebooks/GSA_hydrological_model.ipynb
https://mybinder.org/v2/gh/SAFEtoolbox/Miscellaneous/HEAD?urlpath=notebooks/Introductory_Notebooks/GSA_predator_prey_model.ipynb
[Using GSA to enhance model-informed decisions: application example to a flu model](https://mybinder.org/v2/gh/SAFEtoolbox/Miscellaneous/HEAD?urlpath=notebooks/Introductory_Notebooks/GSA_flu_model.ipynb)
-->

**Papers about the SAFE toolbox**

A general introduction to the rationale and architecture of SAFE is given in:<br>
[Pianosi, F., Sarrazin, F., Wagener, T. (2015), A Matlab toolbox for Global Sensitivity Analysis, 
Environmental Modelling & Software, 70, 80-85.](http://www.sciencedirect.com/science/article/pii/S1364815215001188)<br>
Detailed documentation on how to use the toolbox is given in the workflow scripts 
provided with the Toolbox and in the help of each function.

**_Getting started_**

To get started using SAFE, we suggest opening one of the workflow scripts and running the code step by step. 
The header of each workflow script gives a short description of the method and case study model, 
and of the main steps and purposes of that workflow, as well as references for further reading. 
The name of each workflow is composed as: <br>
>> workflow\_\<method\>\_\<model\>

\<model\> includes: two hydrological models (Hymod and HBV) and two benchmark functions (the Ishigami and Homma function, and the Sobol' g-function). <br>
\<method\> includes: eet (elementary effects test, or method of Morris), fast (Fourier amplitude sensitivity test), rsa (regional sensitivity analysis), vbsa (variance-based sensitivity analysis, or method of Sobol'), PAWN. <br>
Furthermore, SAFE includes additional workflow scripts on how to connect SAFE to a model running outside matlab/octave
(external) and how to use visualisation functions for qualitative GSA (visual).

**Papers about Global Sensitivity Analysis**

**_Why doing GSA_**

A literature review of GSA applications in the context of earth systems modelling, 
focusing on what can be learnt about the construction, testing and use of environmental
models through the application of GSA: <br>
[Wagener, T. & Pianosi, F. (2019), What has Global Sensitivity Analysis ever done for us? 
A systematic review to support scientific advancement and to inform policy-making in earth 
system modelling, Earth-Science Reviews, 149, 1-18.](https://www.sciencedirect.com/science/article/pii/S0012825218300990) <br>
This paper could be a useful starting point to explore the type of questions GSA can address, and why using GSA in the first place.

A discussion about the connection between GSA and model evaluation particularly for impacts assessment under change: <br>
[Wagener, T., Reinecke R., Pianosi, F. (2022) On the evaluation of climate change impact models, WIREs Climate Change, 13(3), e772](https://wires.onlinelibrary.wiley.com/doi/full/10.1002/wcc.772)

**_How to set-up a GSA_**

A general introduction to the working principles of Global Sensitivity Analysis 
and how to make key set-up choices (how to choose the GSA method, the sampling strategy, 
the sample size, etc.) is given in: <br>
[Pianosi, F., Beven, K., Freer, J.W. Hall, J. Rougier, J. Stephenson, D.B., Wagener, T. (2016), 
Sensitivity analysis of environmental models: A systematic review with practical workflow, 
Environmental Modelling & Software, 79, 214-232.](http://www.sciencedirect.com/science/article/pii/S1364815216300287)

More discussion on the practical effects of some of the key set-up choices,
and how to interpret them, is given in:<br>
[Noacco, V., Sarrazin, F., Pianosi, F. and Wagener, T. (2019), 
Matlab/R workflows to assess critical choices in Global Sensitivity Analysis 
using the SAFE toolbox, MethodX, 6, 2258-2280.](https://www.sciencedirect.com/science/article/pii/S2215016119302572)

Specific discussion on the choice of the sample size for EET, RSA and VBSA can be found in:<br>
[Sarrazin, F., Pianosi, F., Wagener, T. (2016), Sensitivity analysis of environmental 
models: Convergence and validation Environmental Modelling & Software, 79, 135-152.](http://www.sciencedirect.com/science/article/pii/S1364815216300251)

