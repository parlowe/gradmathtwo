# gradmathtwo
Gaspari, E., Franke, A., Robles-Diaz, D., Zweigerdt, R., Roeder, I., Zerjatke, T., & Kempf, H. (2018). Paracrine mechanisms in early differentiation of human pluripotent stem cells: Insights from a mathematical model. Stem Cell Research, 32, 1–7. https://doi.org/10.1016/j.scr.2018.07.025

Introduction 
Pluripotent stem cells have recently become the source for much excitement in tissue engineering and regenerative medicine applications because of their theoretical capability to differentiate into any cell type. However, differentiation mechanisms are poorly understood making it difficult to achieve this promise in reality . The aim of this paper is to model the differentiation of human pluripotent stem cells into mesendoderm cells through positive and negative interactions with paracrine factors. The authors propose a mechanism by which stem cells differentiate into MIXL+ or pro-mesendoderm lineage cells via positive enhancement by CHIR99021 (CHIR). Additionally, paracrine factors can further enhance or dampen this differentiation. Figure 1 demonstrates how these factors relate to promote differentiation. 

While the most complex of the models incorporates all of the interactions in Figure 1, to replicate this work I have chosen to examine a simplified model that incorporates the effects of CHIR and one paracrine factor that has an inhibitory effect on differentiation, Factor X. The model is a system of three ordinary differential equations that model the cell count of mesendoderm cells (M) which are MIXL+, differentiated cells that are not mesoendoderm lineage (N) which are MIXL-, and the concentration of factor X which is produced by the cells. The model is included below in Figure 2. 





Where 
M = MIXL+ cell numbers
N = MIXL- cell numbers
Γ = total number of cells
X =  concentration of factor X 
C = concentration of CHIR
d0 = basal differentiation rate 
ac = enhancement of differentiation rate by CHIR
ix = inhibition rate of differentiation by factor X
dN = differentiation into non mesendoderm lineages
px = production rate of factor X
icx = inhibition rate of factor X by CHIR
ex = degradation rate of factor X

Model Construction and Parameter Fitting 
The model was parameterized using the scipy module and the minimize function to minimize the root mean square error of the ODE solution compared to the experimental data in the paper when different values for the parameters were applied. In the paper the authors assumed that the cell number and CHIR concentration was constant throughout the analysis. In this analysis, a CHIR concentration of 7.5 μM was assumed along with a population of 7.7 million cells. A plot digitizer was used to digitize the following plot which was included in the paper (Figure 3).

Since a concentration of 7.5  μM was assumed, the data was taken from the upper left hand portion of the figure. The final error value was calculated to be 97.5, and the following estimates for the parameters compared to those obtained by the authors in the paper. (Table 1).

The parameters for the model were much different than those proposed in the paper, however it is likely that these parameter estimates came from analysis of the effects of all paracrine factors. When the fits of the solutions were compared to the experimental data for M, it was clear that the fit was not ideal for the system (Figure 4). 

This was also likely due to missing data for the other modeled values in the system since values for M were the only values reported. 

Bifurcation Analysis 
A bifurcation analysis was performed to assess how changes in the parameter ac impact the steady state behavior of the solution for M. I chose to examine this parameter because it relates to the action of CHIR on the differentiation process. CHIR is a common inhibitor that is used in stem cell differentiation and I had a personal interest related to my own research in how it affects the dynamics of the system  For this analysis N and X were held constant to create three flow diagrams for the system when ac (Figures 5 -7). 

From the flow diagrams it is clear that there is a constant steady state around 68000 cells differentiated. This is a transcritical steady state that depends on the value of the parameter value of ac. When the value of ac is less than zero there is an unstable steady state for the system otherwise this steady state is stable. Since it is known that CHIR positively influences the differentiation rate of pluripotent stem cells, it is unlikely that the unstable steady state will be encountered in a living system. The bifurcation diagram for this analysis is included in Figure 8 below. 

Sensitivity Analysis 
In order to determine which parameters have the highest impact on the value of M sensitivity analysis was also performed. Local sensitivity was performed by perturbing the fits for each of the parameters by 1% and normalizing the perturbation value based on the effect that it had on the system. Figure 9 shows the impact of the different parameters on the value of M due to local perturbations. 

Locally, d0 and ac have the largest impact on the system when perturbed. More insight into these parameters would more easily demonstrate parameter effects for this model and thus should be focused on in order to improve it. 

Global sensitivity analysis was also performed to check the results of the local sensitivity analysis and to gain insight into the system for larger perturbations. Values for the parameters were randomly simulated within a 20% tolerance around the fitted parameter and these values were used to calculate normalized sensitivities and fit a linear model to the parameters. The resultant linear model was: 

M=  1623.39 d0 +  60.73 ac + 26.55 ix- 231.57 dN + 25.39 px+ 43.87 icx - 40.43 ex . This demonstrates that in addition to having a local effect d0 and ac have a global effect on the system. However, when this model is used to predict values for M it does not accurately predict the values as is demonstrated in FIgure 10. Thus this analysis should be taken sparingly. 

Conclusion 
Completing this analysis demonstrates the complexity of modeling for cellular behaviors. The resultant fits and parameter estimates for the simplified model did not match the experimental data, nor the authors parameter estimates well. However, sensitivity and bifurcation analysis demonstrated some parameters that could be manipulated in further experimental or computational analyses to provide greater insight into the behavior of this model. Studies that more accurately measure the activation of differentiation by CHIR or the basal differentiation rate could help to better parameterize this system. Furthermore, understanding why the value of ac does not impact the steady state behavior of the system over any observable range would be of interest. 
