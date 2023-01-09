# RNN Classification of Atrial Fibrillation from Echos
## Methods
### Data Preparation
First, Echo videos were converted into images. This was done by sampling 64 frames equally spaced across each video. This was done to reduce the size of input into the model. Data was split into 90% train and 10% test. When images are loaded into the model, they are downsampled to 112 by 112. Transformations are also performed, namely Random Horizontal Flip, Random Affine, and normalization. 
### Model Definition
The model used was a combined convolutional neural network (CNN) and recurrent neural network (RNN) with 16 timesteps. The CNN component is used to extract high-level features, which are then fed into the RNN with 16 timesteps to incorporate memory between frames. The CNN model used was ResNet18 pre-trained on ImageNet with dropout rate of 0.1, and the RNN had 1 hidden layer of size 100. 
### Model Training
Since the base CNN model was already pre-trained, we will only fine tune on the Echos. We trained for 20 epochs with a Cross Entropy loss function, Adam optimizer with starting learning rate of 3e-5, and reducing learning rate on plateau with factor 0.5 and patience of 5. 
### Model Testing
Predictions were made on test data. 
