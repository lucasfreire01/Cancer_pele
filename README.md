# Cancer_pele
Melanoma is a type of skin cancer that develops in the cells that produce pigmentation, called melanocytes. It is one of the most aggressive forms of skin cancer and can spread quickly to other parts of the body if not detected and treated early.
Next the treatment the patient is followed for 5 subsequent years if there is some change in melanin cells, if have some change
the patient must search a doctor. To help these doctor was created a copetition at drivedata.com and the goal is predict if the cell will have change in the next 5 years.
This competition provided 3 datasets train, test, train_label

this is the columns at train dataset:
   
   filename (str) - unique identifier for each WSI
   
   age (str) - age range of the patient at initial diagnosis
   
   sex (int) - sex of the patient at initial diagnosis, where 1=male and 2=female
   
   body_site (str) - the site of the melanoma at initial diagnosis
  
   melanoma_history (str) - whether the patient had melanoma before
   
   breslow (str) - thickness of the melanoma in mm at initial diagnosis
   
   ulceration (str) - whether the melanoma had ulceration, which is a total loss of epidermal tissue
   
   resolution (float) - the resolution at level 0 of the slide in microns per pixel
   
   tif_cksum (str) - the result of running the unix cksum command on the TIF image
   
   tif_size (int) - the file size in bytes of the TIF image
   
   us_tif_url (str) - file location of the pyramidal TIF in the public s3 bucket in the US East region
   
   eu_tif_url (str) - file location of the pyramidal TIF in the public s3 bucket in the EU region
   
   asia_tif_url (str) - file location of the pyramidal TIF in the public s3 bucket in the Asia Pacific region
  

train_label:
   
   
   filename (str) - unique identifier for each patient
   
   relapse (int) - whether there was a relapse, where 0=no relapse and 1=relapse(This is the target column)
  
test dataset:
   
   filename (str) - unique identifier for each WSI
   
   age (str) - age range of the patient at initial diagnosis
   
   sex (int) - sex of the patient at initial diagnosis, where 1=male and 2=female
   
   body_site (str) - the site of the melanoma at initial diagnosis
   
   melanoma_history (str) - whether the patient had melanoma before
   
   resolution (float) - the resolution at level 0 of the slide in microns per pixel
 
We starting to do the preprocess in train_dataset see the column melanoma_history and the balance it so we take the missing values this column and put this places the values YES to have a column a little more balace. Next te going to treat other categorical column the Age, strategy was take the first value each line and transform this value in int.

At melanoma_history then to try the balence the column we used the one_hot_encoder to transform this value at numeric, we have now two column melanoma Yes and melanoma NO. We take some column for model because two reasons the first id the intention of project the first contact with deep learning model so we don't used this information give us images we prefer use just the datas is explicits in dataset the second reason is the test dataset we prefer just take the columns there is in train and test dataset

We still have other categorical column is the body_site this case we treated the missing values use the pandas.mode() and next the one_hot_encoder. we start to see the column resolution and decided to leave this column with just 2 decimal places.

To help the model was did the normalization with Min_Max_Scaler just in train data take over the target column. After splitnig the train and test datasets at x_train,x_test,y_train,ytest used test_size=0.2. Finally to build the model we used the sequention that is a model in Keras also the Dense as switch among leyres how I said before this project is just the first concat with deep learning models so this model juist have one entry leyer, one hidren with activation mode is relu and one output leyer and the activation mode is sigmoid.

We compile the model with loss='binary_crossentropy', optimizer='adam', metrics=['accuracy']
Next fit this model with train split[x_tra,y_train] 15- epochs batch_size=33 and the validation datas
We see the acurrancy and the predict, this pediction had values between 0 and 1 but we needed values 0 and 1 so all value in 0.5 or hight we transformed for 1
Take The mean_absolut erro and this showed us 0.40 and the accuracy 86.24 (this is an acceptable result for the proposal of this project as the first contact to deep learning)

Next we loaded the validation dataset that just have 2 line so we start to preprocess this dataset the categorical column useing the one_hot_encoder tho transform this column, using the model to have prediction of this dataset and finishing the project.
