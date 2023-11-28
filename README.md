# Building a Custom ANN for Image Classification

# **1. Overview** 

This program implements an artificial neural network using TensorFlow for image classification. this
folder contains several Python files that all have a similar underlying NN model, but use the model for
different applications (including CIFAR-10 classification and more space and satellite-related
classifications). The NN architecture used is adapted from typical NN architectures implemented for
image classification.


# **2. File List/Components**
   
**a. ann_main_binary:** creates a NN that performs simple binary classification of images. The two classes
used are cats and dogs.

**b. ann_main_general:** creates a NN that performs image classification for multiple classes. The four
classes include cats, dogs, rhinos, and giraffes.

**c. ann_main_cifar:** utilizes image classification model from ann_main_general for a more rigorous and
complex dataset, CIFAR-10 (created by the Department of CS at the University of Toronto).

**d. ann_main_debris_2:** This program is 1 of 3 programs that apply the NN from ann_main_general for
industry-related applications. Ann_main_debris is used for debris detection, where the NN can classify
different forms of space debris, including payload fairings and rocket stages.

**e. ann_main_satellite_parts_2:** This program applies the NN for satellite component detection, including
detecting solar panels and deployable booms.

**f. ann_main_asteroids_2:** This is the final industry-specific NN program, and it applies the created NN to
classify asteroid images as m-type, s-type, or c-type.

# **3. How to Run**
Each of the 6 programs listed above requires specific images for the validation, testing, and training
dataset. This Google Drive link
(https://drive.google.com/file/d/1N3AwPj0gpn8XWl5eeNjFehmNcpQnrXR_/view?usp=sharing) provides
all of these images and their corresponding folders. To get the images into their right place, simply
download the “All_Images” ZIP folder, and place all the subfolders of “All_Images” (i.e. image_asteroids,
image_binary) into the same directory as the 6 main files listed above.
Instead of providing a .yaml file to create the Python environment, each of the 6 main files has a section
at the top where all necessary libraries are automatically installed as the program runs.
Each of the 6 main programs runs independently of each other. In other words, each of the 6 programs
performs its own setup, NN model building, training, and calculations. This was done primarily to add
flexibility and to customize each NN for its associated use case and dataset. So, in order to see each NN
run, simply run the corresponding main file and choose Python as the kernel when prompted.

# **4. Code Components**
Each of the 6 main program files follows the same structure and contains the same components. Listed
below are the key components of each program:

**a. Data Preprocessing:** Before training the NN, each program loads and processes the image data. In all
cases (excluding CIFAR), images are sourced from their respective directories, and images that are not of
a certain data type are deleted. Then, the images are divided into training, testing, and validation
datasets; the proportions of each vary a bit from program to program. Finally, images are resized and
normalized before the NN runs.

**b. Model Architecture:** These NNs were designed using the Keras Functional API. The NNs across the
different programs are mostly similar: they all have 3 layers, and all use a combination of sigmoid, relu, and
softmax activation functions, and they all take images as inputs and output the class prediction for
various images. Where these NNs differ is in the number of filters and forms of uncertainty
quantification.

  - **bi. Layers:** The model begins with the input layer, which is configured differently for each program
based on the image sizes. There are 3 subsequent layers, and each layer has 3 components: a Conv2D
function, followed by batch normalization and a max pooling layer. Because the dataset and image sizes
for each program are different, the number of filters in each layer differs for each program. Finally, there
is a dropout and output layer, which uses a softmax activation function for the multi-class classification
programs and a sigmoid activation function for the binary classification program. The output layer
serves as the neural network&#39;s decisive component, as this layer determines what class the image
belongs to.

  - **bii. Uncertainty Quantification:** A few methods of uncertainty quantification, like Bayesian
Networks and Ensemble models, were initially used but ultimately not implemented because they
did not provide a lot of accuracy improvement. Instead, in their current state, the NNs use dropout to
drop some inputs during training so that there is increased randomness. This allows the model to learn
features in a more generalized and robust manner. To further increase accuracy, the NN uses batch
normalization to normalize the input layer, which helps prevent overfitting to a certain extent.

**c. Training:** The model is trained for 20 epochs, which allows the NN to gradually become more accurate
over 20 iterations before it finishes training. For most programs, the data validation split is 20%.

**d. Evaluation:** The last component of the program is evaluation. Here, the loss and accuracy are plotted,
and the NN attempts to classify a random image from one of the corresponding folders.
