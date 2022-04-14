## scope
This homework is quite open ended. There is no scheleton notebook for it. 


## due 4/20 midnight:
Use the PLAsTiCC challenge data you used in HW7 and prepare the time series for ingestion by an autoencoder
Make sure you save your reorganized time series into a file (e.g. https://numpy.org/doc/stable/reference/generated/numpy.save.html)


## due 4/27 midnight:
extract features from the time series via autoencoder (you have examples of the autoencoders in the notebooks distributed in class, so you just need to modify them
Then combine the feature space you used in HW7 with the new features created by the autoencoder, and train a classifier to predict the object class. 

## what are the challenges in this work?

For each object in the dataset there are 7 time series for 7 optical filters. 
Each time series is composed of a series of time stamps and a series of fluxes (i.e. the time series are sparsely sampled).
Think about how you can feed these data to a neural network:

1. Neural network need each "datapoint" (each astrophysical object with its associated vectors of brightness in this case) to be of a fixed dimension. But in this data the time series are "sparse" i.e. the observations are taken at irregular intervals, with a non constant number of observations per object.

2. There are multipe time series associated with each object: one per filer (or "band"). You need to choose how you want to combine these vectors. You could extract features from each of the 6 vector separately, or combine them into a single input to your feature extraction model. From a domain point of view, the relationship between what happens in different filters (i.e. at different wavelengths) is important. From a practical point of view ignoring it may be easier. Your choice

3a. You **must choose a common time frame for all observations**: for example for each *object* choose the timestamps of the first observation and set it to 0. Count time forward in days from that point. That means you need to _interpolate_ the time series in some way. You can use a "simple" method like a cubic interpolation, spline, or, ideally, something more sophisticated like **gaussian processes** but you do not have to. If you do a good job with a simpler model and discuss the results well that is also ok. Then you can extract _evenly sampled_ values by generating the value of each vector at N points in time.

3b. You can also deal with the sparsely sampled time series if you really do not want to interpolate... but
 - you will need to preserve the time stamps or at least the interval between observations and let your model know about them. 
 - you will need to end up with the same number of data points for each object (for example by throwing away the some from the time series that have more)
 
 4. You need to choose the dimensionality of the data in input to your autoencoder: easiest option to design your data imput is to flatten the time series into a 1D object. If you have evenly sampled the time series you can concatenate the six bands: suppose the bands are called A B C D E F and there are N observations in each then you can pass your data as

|A1|A2|A3|......|AN|B1.....|BN|.....|C1|....|CN|....|FN| 

Or you can pass it as a 2D object that is 6xN dimensional

|A1|A2|A3|......|AN|
|B1|B2|B3|......|BN|
....
|F1|F2|F3|......|FN|


If you have not interpolated your time series you may want to pass the time stamps as well as the data, but be careful: preprocessing (e.g. normalization) is going to be complex       
        
       t1|t2|t3|t4...
       f1|f2|f3|f4...


you can pass it as 

         input = t1|t2|t3|t4....f1|f2|f3|f4

## this has been pushed to HW 9 (4/27) so it is not due on 4/20, but here is a look ahead

Create an autoencoder where the middle layer is smaller than the original size of the time series (or set of time series if you work with all colors at once). After training the NN on the training data extract the bottleneck layer of your neural network. This will be a set of N numbers (where N depends on the choice you made when you generated the model architecture). Those numbers should be used as N features to be fed to the same random forest classifier you created in HW7 (which you will need to retrain).  You should include the same features you had used in HW7 **plus the new N feature** and then print the accuracy, and the classification matrix. Are there any improvements?

I would default to a Random Forest: its easy to implement and gives good results, but feel free to try other things!


You should ask your autoencoder to reproduce the data so the output will be the same as the input (or, if you did not interpolate perhaps you only want it to reproduce the flux values.... I have not tried so I am not sure how well it may work)
 
         output = f1_out|f2_out|f3_out|f4_out
         
         
then when you want to see if your autoencoder reproduces the time series you will compare
```
pl.plot(t, f) # the original time series
```
with 
```
pl.plot(output[:N], output[N:])
```

and measure the accuracy as the mean squared error for example: the mean squared difference between value in and value out.


Or you can think of some other creative reorganizaion. 






