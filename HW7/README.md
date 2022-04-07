# Reading
The Hazards of Extrapolation in Regression Analysis
Gerald J. Hahn

https://www.tandfonline.com/doi/pdf/10.1080/00224065.1977.11980791?needAccess=true

This is an old (1977) paper on the risks of extrapolating. It makes an interesting prediction about year 2000. It would be interesting to verify how the prediction actually went

# Feature extraction and Gaussian Processes
Follow the instructions in the notbeook in this folder. You will be guided to select 4 or more features from a time series dataset. 
This will be done with simple statistical tools that you already have encounters (moments of distributions, parameter values of fits to the data etc)
Furthermore you will be asked to fit a GP model to a subset of the time series. Use the george package and the example developed in class and posted here as a guide on how to use the george GP package.
https://github.com/fedhere/MLTSA22_FBianco/tree/main/Lab5GP
Make consideration on what kernel you decide to choose and how you decide to treat the uncertainty in the data. 

NOTE: there is an interesting extra credit, which is to fit GPs in 2 dimension. This is not substantially more complext than the 1D case and this github issue on the goerge repo may help

https://github.com/dfm/george/issues/41

