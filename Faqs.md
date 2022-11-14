[<img src="drawing2.png" alt="SAFE logo" style="width:10%;" >](./index.md/) 

## SAFE Toolbox: Frequently Asked Questions

Here you can find a list of Frequently Asked Questions on GSA in general and SAFE in particular.

***Q: I DO NOT HAVE A MATLAB LICENCE, CAN I STILL USE SAFE?***

If you do not have Matlab you can use SAFE in Octave. Octave is freely available at:
www.gnu.org/software/octave/download.html
In order to use SAFE in Octave, you also need to download the “statistics” package:
http://octave.sourceforge.net/statistics/

Alternatively, you can download the R or Python version of SAFE.

***Q: WHY DO I GET NEGATIVE VARIANCE-BASED SENSITIVITY INDICES (OR INDICES LARGER THAN 1)?***

In principle variance based indices take values between 0 and 1. However, this might not happen in practice 
because we use an approximation procedure to estimate the indices (analytical computation being impossible). 
For instance, imagine that the ”true” (unknown) value of a sensitivity index is 0.05 and your 
estimation error is -0.06, you will get a sensitivity estimate of  -0.01. So, obtaining indices below 0 (or above 1) 
is an evidence that the approximation errors are relatively large.

***Q: HOW DO I ESTIMATE APPROXIMATION ERRORS?***

The extent of approximation errors can be assessed by using the bootstrapping option to derive confidence intervals.

***Q: HOW DO I REDUCE APPROXIMATION ERRORS?***

If you want to reduce approximation errors (and hopefully obtain index values in [0,1]), you must increase the sample size. 
To do this efficiently, you can add new samples to an already existing dataset, rather than creating a new sample of bigger size 
from scratch (see point 4 in “workflow_vbsa_hymod”). Depending on the case study, the sample size needed to achieve good approximation 
may vary a lot, ranging from 1,000 up to 10,000 (or more) times the number of input factors (see for example Figure 5 in 
[Pianosi et al. (2016)](http://www.sciencedirect.com/science/article/pii/S1364815216300287))
A final remark: if the true unknown value of the sensitivity index is 0, a negative index can be obtained even when using 
a very large sample size, although very small in absolute value, because the sensitivity index coincides with the approximation error.

***Q: MY VARIANCE-BASED SENSITIVITY INDICES STILL HAVE VERY LARGE CONFIDENCE BOUNDS, WHAT CAN I DO?***

If you cannot afford to run more model evaluations to reduce the confidence intervals of VBSA indices, you might: <br>
1) Extract as much information as possible from the sensitivity estimates you possess. For example, if confidence intervals 
are large but they do not overlap, then you might still be able to derive reasonably robust conclusion about the ranking 
of the inputs, even if the sensitivity indices values are not exactly estimated. 
This is also discussed in Sarrazin et al. (2016). <br>
2) Apply a different, less computationally demanding method, for example the Elementary Effects Test (EET). 
Notice that if you used Saltelli’s resampling strategy to generate the input/output samples for VBSA 
(as implemented in the vbsa_resampling function of SAFE) you can apply the EET to those samples without 
re-running the model (you only need to rearrange the samples in the right way before passing them to the EET_indices function). 
The workflow to do this (in Matlab) is available here.

***Q:HOW DO I SET A THRESHOLD FOR IDENTIFYING UNINFLUENTIAL FACTORS?***

In theory, uninfluential input factors should have zero-valued sensitivity indices. However, since sensitivity indices 
are typically computed by numerical approximations rather than analytical solutions, an uninfluential factor may still
be associated with a non-zero (although small) index value. One way to identify uninfluential factors is to define a threshold 
value for the sensitivity indices: if the index is below the threshold, then the input factor is deemed uninfluential. 
The problem then is how to sensibly define the threshold. A simple and effective way to set the threshold for variance-based 
and PAWN sensitivity indices is by using the estimated sensitivity to a ‘dummy parameter’. The approach is described and demonstrated in:
Farkhondeh KZ, Nossent J, Sarrazin F, Pianosi, F, van Griensven A, Wagener T, Bauwens, W (2017), Comparison of variance-based and moment-independent global sensitivity analysis approaches by application to the SWAT model, Environmental Modelling & Software, 91, 210–222.

***Q: ARE THERE OTHER METHODS TO ASSESS THE ROBUSTNESS OF RANKING AND SCREENING RESULTS?***

Yes, for example the Model Variable Augmentation (MVA) method allows to assess the quality of SA results without performing 
any additional model runs or requiring bootstrapping. More information about the method:
Mai, J., & Tolson, B. A. ( 2019). Model Variable Augmentation (MVA) for diagnostic assessment of sensitivity analysis results. 
Water Resources Research, 55, 2631– 2651.
A Python implementation of this method is available here (code by Juliane Mai), and can be easily integrated in the Python version of SAFE.

***Q: MY MODEL’S INPUT FACTORS ARE CORRELATED: CAN I STILL APPLY VARIANCE-BASED GSA?***

The SAFE functions currently implemented for VBSA require that input factors be independent. However the literature on extending variance-based sensitivity estimators to the case of correlated inputs is growing. A good starting point is:
S. Kucherenko, S. Tarantola, P. Annoni (2012), Estimation of global sensitivity indices for models with dependent variables, Computer Physics Communications, 183, 937–946.
A Python implementation of this method is available here (code by Alessio Ciullo), and can be easily integrated in the Python version of SAFE.

***Q: MY MODEL’S INPUT FACTORS MUST RESPECT CERTAIN INEQUALITY CONSTRAINTS: HOW TO CONSIDER THEM WITHIN MY GSA?***

A slightly simpler case than in the previous question is when input factors can be sampled independently from one 
another but they must respect some inequality constraints (for example, “x1 must be larger than x2”). 
A simple way to handle this case is to create a loop where (i) samples are created using the standard (unconstrained) 
sampling function available in SAFE; (ii) the samples that do not satisfy the constraints are discarded; 
and (iii) new samples are added, again using standard SAFE functions for extending a given sample. 
The three steps are repeated until the required sample size is reached. 

For example, the Matlab code to get a Latin-Hypercube sample of size N respecting the constraint “x1>x2” would be: <br>
X = AAT_sampling(samp_strat,M,distr_fun,distr_par,N) ; % initial unconstrained sampling  <br>
constr = X(:,1) > X(:,2) ; % find indices of feasible samples  <br>
if sum( constr ) == N ; flag = 1; else; flag = 0; end % check how many samples are feasible  <br>
while flag == 0 ; % while the number of feasible samples has not reached N yet:  <br>
    X = X( ~constr , : ) ; % discard unfeasible combinations  <br>
    X = AAT_sampling_extend( X,distr_fun,distr_par,N ) ; % extend sample  <br>
constr = X(:,1) > X(:,2) ; if sum( constr ) == N ; flag = 1; end  <br>
end

***Q: SAMPLING FROM DISCRETE UNIFORM DISTRIBUTION: HOW TO MODIFY THE LOWER BOUND OF THE RANGE? (Matlab version)***

The sampling functions OAT_sampling and AAT_sampling in SAFE rely on the Matlab/Octave function unidinv, 
which assumes that the lower bound of a discrete uniform distribution be 1. This is why OAT_sampling and AAT_sampling
allow to specify only one parameter (the upper bound) for discrete uniform distributions. 
If one wants to sample from a range with lower bound different from 1, we suggest to still use the OAT_sampling 
and AAT_sampling functions as they are, and simply shift the results after sampling by adding/subtracting 
the due amount. 
A simple script with some examples is available here.

***Q: WHY DO I GET AN ‘OUT OF MEMORY’ ERROR MESSAGE WHEN USING AAT_sampling FUNCTION? (Matlab version)***

You can get an ‘out of memory’ error when using the AAT_sampling.m function with a large number of model evaluations 
(N) or forcing inputs (M). The error is typically caused by another function, lhcube.m, which is called by AAT_sampling.m.
The problem occurs when lhcube.m tries to calculate the minimum distance between two points in the Latin Hypercube Sample 
(lines 85-88 of lhcube.m). This step can take a lot of memory as it requires creating a matrix that includes 
the distances between all possible pairs of two points in the LHS. In the lhcube.m function, we have two options to perform this step. 
The first option (default) is given on line 86, and it uses the pdist.m function of the Matlab Statistical Toolbox: <br>
dk = min(pdist(Xk)) ; % Requires Statistical Toolbox <br>
The second option (which should not be active in the copy of SAFE you have received) is given on the (commented) line 88, 
and it uses the ipdm.m function (an open access function included in SAFE): <br>
dk=(ipdm(Xk,’metric’,2)); dk=min(dk(dk>0)); <br>
The reason why we use the first option by default is that it uses less memory, meaning that it should avoid ‘out of memory’ 
errors more frequently. However, we also give the second option for those who do not have the Statistical Toolbox – 
they will just need to comment line 86 and uncomment line 88.

***Q: HOW DO I FIX THE PROBLEM?***

If you have the Statistical Toolbox and can thus use the more efficient pdist.m function, double check that this is the option 
being used by lhcube.m. If you are already using the first option (or if you do not have the Statistical Toolbox, so you cannot 
use this option) and you still get an ‘out of memory’ message, then you can try increase the memory allocated to Matlab. 
Look at the Mathworks documentation on how to do that – for example instructions for Matlab R2018b are given 
[here](https://uk.mathworks.com/help/matlab/matlab_prog/resolving-out-of-memory-errors.html)).

As a last resort, you can force lhcube.m to avoid calculating the minimum distance between points at all by commenting 
all lines 85-95 in lhcube.m. What happens in those lines is that lhcube.m selects the ‘best’ LHS 
(to be delivered as output of the function) out of a certain number of ‘candidate’ LHSs (10 in our case), 
and the selection criterion is that the ‘best’ LHS is the one where the minimum distance is maximum (so called ‘maximin’ approach). 
So, if we comment these lines, the selection will not be made, and lhcube.m will simply return as output the last candidate LHS
– so, still a LHS but possibly suboptimal with respect to the maximin LHS.
(Want to learn more about LHS optimisation? See for instance: Damblin, Couplet, Iooss (2013) Numerical studies of space 
filling designs: optimization of Latin Hypercube Samples and subprojection properties. Journal of Simulation)


