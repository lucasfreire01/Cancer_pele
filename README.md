# Cancer_pele
Melanoma is a highly aggressive form of skin cancer that originates in the cells responsible for pigmentation (melanocytes). Early detection and treatment are crucial in preventing the cancer from spreading to other parts of the body. To aid doctors in this process, a competition was created on DrivenData.com that provides three datasets: train, test, and train_label.

The train dataset contains several columns such as the patient's age, sex, body site, melanoma history, breslow thickness, ulceration, and other relevant information. The target column is in the train_label dataset and indicates whether there was a relapse or not.

During preprocessing, we addressed the missing values in the melanoma_history column by replacing them with 'YES' to balance the column. Other categorical columns such as Age and body_site were also transformed accordingly. The resolution column was rounded off to two decimal places to simplify the data.

The team then normalized the data using Min_Max_Scaler and split the data into training and testing datasets with an 80/20 split. They built a Keras sequential model with one input layer, one hidden layer, and one output layer with sigmoid activation. The model was compiled with binary_crossentropy loss, Adam optimizer, and accuracy metrics.

After fitting the model with the training data, they calculated the accuracy and prediction values. Predictions were transformed to binary values using a threshold of 0.5. The mean_absolute_error was 0.40, and the accuracy was 86.24%, which is an acceptable result for the first deep learning model on this project.

Finally, the team preprocessed the small validation dataset and used the model to make predictions on it, successfully completing the project.

PS(The itention of this project is have the first contact with deep learning model so tehre is somes column with characters lead for a image dataset but how I said we proposal is the first contact wirh deep learning then we just use the explicit datas at dataset)
