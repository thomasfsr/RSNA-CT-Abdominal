# Classification of abdominal injuries by CT (computer tomograph) of the abdominal region. (Kaggle Competition)
link of the competition: https://www.kaggle.com/competitions/rsna-2023-abdominal-trauma-detection

## Summary:
The competition was held in Kaggle hosted by the RSNA (Radiological Society of North America). The dataset consists of CT (Computer Tomograph) of many patients that suffered of traumas in the abdominal region. The Task was to classify the injuries by the labels given by the dataset.  
The labels consists of injuries:  
* Bowel_healthy,bowel_injury
* Extravasation_healthy,extravasation_injury,  
* Kidney_healthy,kidney_low,kidney_high,  
* Liver_healthy,liver_low,liver_high,  
* Spleen_healthy,spleen_low,spleen_high.

So, there are 5 types of labels, two of them are binary classes (bowel and extrabasation). And the remaining are also the degree (low or high) of the injury.  

Since the data consists of a sequence of images as slices of the CT of each patient, I decided to experiment two approaches:
-Extract the features of each image in a sequence pre-defined for each patient, and fitting these features into a LSTM model as a sequence.
-Create a volume for each CT (50 slices evenly spaced) and create a "3D" image with 50 channels and fitting to a Resnet18 model modified to receive 50 channels.
Both approaches manage to yield a reasonable accuracy. However, my naive and basic approach didn't get to the high positions in the rank of the competition.
CNN pre-trained model (Resnet18) to extract features of a sequence of images (slices) of MRI of Abdominal Region to classify injuries in different organs.
## The Schema of the Resnet18-3D model:
![resnet18_3d](https://github.com/thomasfsr/RSNA-MRI-of-Abdominal/assets/95254072/8e0ea0c8-04d5-4d80-ae25-0b18011b75f0)

## The Schemma of the Resnet18 + LSTM model:
![cnn_lstm_summary](https://github.com/thomasfsr/RSNA-MRI-of-Abdominal/assets/95254072/ed72fdcb-6128-463f-8c01-328d29279341)

## Loss Functions:
The Loss function chosen for each group of class was:
* BCE With Logits Loss for binary classification.
* Cross Entropy Loss for multiclass classification.

## Results:
The accuracy of both models were pretty close, Resnet with 50 channels: 73.33% and the CNN+LSTM: 73.49%. Looking to the top competitors solutions, all of them also implemented a segmentation dataset to make the model recognize the region around each organ, making the prediction more precise.
Since the purpose of this project is for practice only, I think we can get a reasonable result with a simpler model. But there is always room for improvement.


