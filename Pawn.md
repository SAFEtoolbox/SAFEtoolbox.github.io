[<img src="drawing2.png" alt="SAFE logo" style="width:10%;" >](./index.md/) <br>
[Home](./index.md/) - [Documentation](./Documentation.md/) - [Applications](./Applications.md/) - [PAWN](./Pawn.md/) - [FAQ](./Faqs.md/)

## The PAWN method

PAWN is a new moment-independent GSA method that can be used in place of or as a complement of 
variance-based (Sobol’) GSA. Moment-independent methods differ from Sobol’ in that they consider 
the entire distribution of the model output, rather than its variance only. As such, they can be 
preferable when variance is not an adequate proxy of uncertainty, for example when the output 
distribution is highly-skewed or multi-modal. The difference between PAWN and other moment-independent 
(or “distribution-based”) methods is that PAWN uses the Cumulative Distribution Function of the output, 
rather than the Probability Density Function, which simplifies numerical implementation. 
Other advantages of PAWN are that it can be easily tailored to focus on output sub-ranges, 
for instance extreme values, and that intermediate results generated in the application of PAWN 
can be visualized to gather insights about the model behaviour (“factor mapping”).

PAWN was introduced in the paper:
[Pianosi, F., Wagener, T. (2015), A simple and efficient method for global sensitivity analysis based on 
cumulative distribution functions, Environmental Modelling & Software, 67, 1-11.](http://www.sciencedirect.com/science/article/pii/S1364815215000237)

A new (and recommended) approximation strategy of PAWN sensitivity indices is discussed in the paper:
[Pianosi, F., Wagener, T. (2018), Distribution-based sensitivity analysis from a generic input-output sample, 
Environmental Modelling & Software, 108, 197-207.](https://www.sciencedirect.com/science/article/pii/S1364815218303220)

<!--The Matlab code to implement the new strategy (including workflow scripts to reproduce the paper results) is available here.-->

A comparison between PAWN and Sobol’ for parameter screening and ranking of a relatively 
complex environmental model (SWAT) is presented in the paper:
[Zadeh FK, Nossent J, Sarrazin F, Pianosi, F, van Griensven A, Wagener T, Bauwens, W (2017), 
Comparison of variance-based and moment-independent global sensitivity analysis approaches 
by application to the SWAT model, Environmental Modelling & Software, 91, 
210–222.](http://www.sciencedirect.com/science/article/pii/S1364815217301159)

The robustness of PAWN sensitivity indices to the tuning parameters of the approximation algorithm 
presented in Pianosi and Wagener (2018) is analysed in:
Puy, Lo Piano, Saltelli (2020) A sensitivity analysis of the PAWN sensitivity index, Env. Mod & Soft. 127
The paper makes some strong conclusions that we think are not completely supported by the experiments presented 
therein, as we have discussed in our review of the original manuscript, which included a further analysis of those experiments. 
Unfortunately the authors decided to ignore the results of our analysis and the manuscript was accepted 
without further revision. We are therefore sharing our review here and the code to reproduce our analysis here, 
so users of the PAWN method can further investigate what we know (so far) about the robustness of PAWN indices.

