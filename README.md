# Classification of injuries in a MRI of abdominal regions.

## Summary:
The competition was held in Kaggle hosted by the RSNA (Radiological Society of North America). The dataset consists of CT (Computer Tomograph) of many patients that suffered of traumas in the abdominal region. The Task was to classify the injuries by the labels given by the dataset.  
The labels consists of injuries:  
-bowel_healthy,bowel_injury  
-extravasation_healthy,extravasation_injury,  
-kidney_healthy,kidney_low,kidney_high,  
-liver_healthy,liver_low,liver_high,  
-spleen_healthy,spleen_low,spleen_high.  
So, there are 5 types of labels, two of them are binary classes (bowel and extrabasation). And the remaining are also the degree (low or high) of the injury.  

Since the data consists of a sequence of images as slices of the CT of each patient, I decided to experiment two approaches:
-Extract the features of each image in a sequence pre-defined for each patient, and fitting these features into a LSTM model as a sequence.
-Create a volume for each CT (50 slices evenly spaced) and create a "3D" image with 50 channels and fitting to a Resnet18 model modified to receive 50 channels.
Both approaches manage to yield a reasonable accuracy. However, my naive and basic approach didn't get to the high positions in the rank of the competition.
CNN pre-trained model (Resnet18) to extract features of a sequence of images (slices) of MRI of Abdominal Region to classify injuries in different organs.
# The Schema of the Resnet18-3D model:
![image](https://github.com/thomasfsr/RSNA-MRI-of-Abdominal/assets/95254072/f0d61916-6d00-4a22-896b-809b3ff1c4ab)

# The Schemma of the Resnet18 + LSTM model:
![image](https://github.com/thomasfsr/RSNA-MRI-of-Abdominal/assets/95254072/9a2e8a18-c99e-4f38-a63e-7f0285a03c18)

