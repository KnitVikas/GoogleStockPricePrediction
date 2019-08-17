# GoogleStockPricePrediction

Our task is :
1.predict the google stock price for the month JAN 2017  with only 20 working days.
2.Draw a trend between predicted stock price vs actual price for the JAN 2017. 

LOADING THE DATA:

Here we are having google stock price data from Jan,3.2012 to Dec 2016. As are taining set.
We will simply import this csv file and which consist of six columns including the Date.
As shown:

	Date	Open	High	Low	Close	Volume

As in our model we have to train our model using single indicator i.e we wll predict
usning the only Opening price of google Stock data. So i wll import only open price to our
Train dataset.


FEATURE SCALING:

scaling the feature so that the range of each feature could lie within a given range
between maximum to minimum.i here used the normalization functon to range the feature between
zero and one.
The normalization is applied on the train_data set.Renamed it to training_set_scaled.
the data is stored in numpy array of 2D.


DATA PREPROCESSING:

As i am considering the timestamp of three month i.e 60 working days. This means i will train my
data on 60 days and i will predict the price of 61st day.The every previous 60 days values i will
append to the train data  and the evry 61st value to the y_train data . 

Exaplaination:like if we start from the Jan 3,2012 we take next 60 working day take them to train set
and the corresponding 61st value is stored in y_train.Now in next step will take our 60 days value
from Jan 4,2012 store it to x_train and coresponding 61st value is stored in y_train. this process is
repeated untill we iterate on whole data.
so now as our x_train and Y_train are ready to feed it to our model.

MODEL ARCHITECTURE :

The neural networks used here is  simple sequential network. using  which we will
simply form the stack of layers of LSTM.the LSTM is long short term memory network which
could simply remember the predictions from every last 60 days.

 Along with LSTM layers im adding the dropout layers for regularization purpose as to avoid 
overfitting the data.
Final layer is dene layer which is an output layer will return the prediction make by the model.
 
the optimizer used is well known 'adam'to optimize the loss function.  the loss function used 
is mean_squared_error helps in decreasing the errors in the model

TRAINING:

AS our X_train and the y_train are ready and evenn we have compiled our model. Now its time to
Fit our data into the compilwd model to train the model on our data.

The number of batch used are 32. the # bathces are nothing but the size of batch in which we will
break our data like if we have suppose 160 rows in data then if batch size is 32 then we can break it
into 5 batches.Batch sizes are computationally efficient especially when dealing with massive datasets.

The epoch is nothing but the one cycle in which our whole batchs will be trained once.
if we take N epochs then all batchs will be trained N times.if we take less number of epochs thn
our data wll be underfit if we tak too many number of epochs than the model  will overfit on the data
so right number of epochs must be taken for making robust model.

MAKING THE PREDICTION:

As we have  to predict the trend on the test_dataset.I imoprt the test data which consist of data
for one month i.e 20 rows for working days.Thn concate the test data with train data set Then
we wll to get 60 days data from Dec 3, 2016 to onwards call it as x_test  on we will predict
using our model.The predicted values are stored predicted_stock_price.
 
 VISUALIZATION:

The trend curve of predicted_stock_price is drawn with real_stcock_prce (i.e with our acctual values
 from Jan 3 2017 onwards).
From both  the trends we can observe that both the trends are moving up and down simultaneously
hence our predicted trend is much simliar to actual trends Only leaving on some spikes in actual trends.



                              
