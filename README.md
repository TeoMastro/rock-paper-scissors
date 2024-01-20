# Rock-Paper-Scissors
My choice to solve an image classification problem like this, was to implement a CNN model.
First, I mapped the images to "rock": 0, "scissors": 1, "paper": 2.
Then I preprocessed the images to 128x128 pixels and I split the dataset to 80% train and 20% test.
# CNN-Model architecture
Model: "sequential_2"

=================================================================
 conv2d_4 (Conv2D)           (None, 126, 126, 32)      896       
                                                                 
 max_pooling2d_4 (MaxPoolin  (None, 63, 63, 32)        0         
 g2D)                                                            
                                                                 
 conv2d_5 (Conv2D)           (None, 61, 61, 64)        18496     
                                                                 
 max_pooling2d_5 (MaxPoolin  (None, 30, 30, 64)        0         
 g2D)                                                            
                                                                 
 flatten_2 (Flatten)         (None, 57600)             0         
                                                                 
 dense_4 (Dense)             (None, 128)               7372928   
                                                                 
 dense_5 (Dense)             (None, 3)                 387       
                                                                 
=================================================================
Total params: 7392707 (28.20 MB)
Trainable params: 7392707 (28.20 MB)
Non-trainable params: 0 (0.00 Byte)

# Explanation of the model
CNNs are fully connected feed forward neural networks. CNNs are very effective in reducing the number of parameters without losing on the quality of models. Images have high dimensionality (as each pixel is considered as a feature) which suits the above described abilities of CNNs
* conv2d_4 layer with 32 filters. Input shape is 128x128 (size of image) and a 3x3 filter to capture small local feature of the image. Relu is used on both conv2d layers to introduce non-linearity to the model.
* max_pooling2d_4 Used to reduce dimensionality.
* conv2d_5 with 64 filters.
* max_pooling2d_5 Used to reduce dimensionality.
* flatten_2 a flattened vector of 1d features. 
* dense_4 A dense layer that processes the 128 flattened vector of the previous layer.
* dense_5 A softmax layer with 3 units (rock, paper, scissors)

# The actual game
After training the model for 10 epochs and testing (by hand), I created the logic for the Agent and set up an environment for 100 rounds. My model with all the extra preprocessing steps (gausian blur and flipping of the image), managed to win 64 rounds, although the images in which it was trained were not preprocessed that wayt.

# Internet images
After all the above steps, I downloaded random rock-paper-scissors images from the internet and tried to see wether my model would sucessfully recognize them.
