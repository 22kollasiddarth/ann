# Overview
The task of building my very first neural network from scratch was such a rewarding experience. While I’ve worked with the clustering and anomaly detection aspects of machine learning before, neural networks and image classification turned out to be slightly similar, but so much more different. With it came a difficult, steep learning curve, but in the end, this project turned out to be so much fun and very enjoyable. The task I attempted was image classification using neural networks, which, as previously stated, was something I’ve never done. So, to start off, I created a simpler binary classification neural network, and then proceeded to create a multiclass neural network. Throughout this entire process, I’ve learned so much about the math behind NN’s, how powerful NN’s really are, and how they can have some unique and amazing applications in the satellite and space industries. Below, I talk a bit about how I approached this project, some analysis and discussion, and at the very end, I give my final thoughts on this entire experience.  


# Process: 
There were 4 main steps during this project:

**1. Building a binary NN:** Learning the foundations of neural nets and understanding the underlying math was probably the most difficult part of the entire process, but was definitely the most important. I began by reading a bunch of online tutorials and watching a lot of YouTube videos; it definitely wasn’t the most straightforward information to understand, but after a while, things started to make much more sense. I wanted to ensure I had a foundational understanding of NN’s before I built a multiclass image classifier, so I started off building a binary classification NN. I ran into many hurdles during the process: coding errors, not enough CPU power, and slight misunderstandings about how all the code fit together. But soon enough, everything came together, and I tested my NN on cats and dogs (seemed like a pretty fun and straightforward way to start)! I created the dataset by downloading images from Google, as this seemed like the simplest way to form a dataset with specific requirements and a wide range of images. The model worked quite well, and seeing the NN work for the first time was such an exciting and rewarding experience. The file with this binary NN is *ann_main_binary*.

**2. Testing out various uncertainty quantifications:** From here, I wanted to experiment a bit with uncertainty quantifications, and see how that would influence the NN’s accuracy. I tried many different things, including Ensemble Models and Bayesian Networks, but none seemed to create a significant increase in accuracy. Moreover, they ended up making the code run for much longer, and utilizing them (at least for a binary image classifier) didn’t seem like the best option. Instead, to improve accuracy, I added batch normalization and dropout (which I discuss in further detail below), and this seemed to provide more accuracy improvements than earlier methods.  

**3.  Creating a multiclass image classifier:** I was satisfied with my binary classification NN, and now wanted to modify it to be a multiclass image classifier. Because I now knew a bit about the math behind NN’s, adapting the NN didn’t seem too difficult of a challenge. After some code edits, I tested my image classifier on 4 animals instead of 2. The model ended up performing really well. So, I took this NN and ran it with the CIFAR-10 dataset (I ended up choosing CIFAR over MSCOCO and LSUN because my laptop doesn’t have the CPU power to run a lot of images with high resolution). Again, the model ended up performing quite well (after modifications to the model including increased robustness and added forms of uncertainty quantifications). The file with the animal classifier is *ann_main_general*, and the file with the CIFAR classifier is *ann_main_cifar*.  

**4.  Testing the NN to space-related applications:** Now that the NN was mostly complete, I knew that I could have a bit more fun and creativity with some of the applications of this NN, especially on how it could be applied to some of Turion Space’s goals. Listed below are three ways that I used the NN for more experimental applications:
  - **a.  Space debris detection:** One of Turion’s primary goals is space debris detection, so I wanted to find a way to apply my NN towards this goal. So, I came up with a list of 4 objects that Turion’s DROID satellites might come across in LEO orbit, like payload adapters, payload fairings, RCS thrusters, and rocket stages, and tried running datasets with these images through the NN. Similar to the two experiments below, the way I created the image datasets was through downloading a bunch of images from Google. The issue is that Google Search often does not have strict boundaries for different search queries, so there are a lot of images in folders that technically shouldn’t be there. This resulted in some low accuracy from the NN (as further described below). One interesting way this NN could be used for Turion is by detecting which space debris lies where, which can be helpful when deorbiting loose objects in space. The corresponding file is *ann_debris*.
  - **b.  Satellite component detection:** While the previous program can assist with space debris detection, I wanted to create a NN that can assist with satellite repair from space. So, I created a NN model to classify images of different parts of a satellite from close up, including deployable booms, reaction wheels, satellite cameras, and solar panels. Thus, when Turion’s satellites are close to a satellite it wants to repair, it could use a NN similar to this to determine different satellite components and figure out what parts of the satellite need repair. The corresponding file is *ann_satellite_parts*. 
  - **c.  Asteroid detection:** This final application, asteroid detection, was a lot more experimental than the last 2. First off, there aren’t many distinguishing features between each type of asteroid, and on top of that, Google often shows images of one type of asteroid even if the other type is searched instead.  So, the accuracy of this program was a lot lower than the other 2, but as expected. One way that Turion might be able to use a NN similar to this is for asteroid mining (which is one of Turion’s future goals with their satellites). This NN classifies images of asteroids as either c-type, s-type, or m-type (the m-type asteroid contains a much higher concentration of metals, which could be helpful when searching for specific elements to mine). The corresponding file is *ann_asteroids*.

# Results:
To evaluate the performance of these NNs, I calculated the accuracy and loss of each epoch during training. Below are images of the graphs of accuracy and loss for each of the 6 programs.

**Ann_main_binary:**

![binary_loss](https://github.com/22kollasiddarth/ann/assets/34851034/1c2c57b5-10df-46e6-83a2-6a7393020ab6)
![binary_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/01caaea9-a140-49b5-b596-9d5b53546dea)

**Ann_main_general:**

![general_loss](https://github.com/22kollasiddarth/ann/assets/34851034/6f665198-a42b-4f1f-b41a-cfbcfabaad1a)
![general_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/a8f4a0cc-37fd-454a-8849-e5120f1305d5)

**Ann_main_cifar:**

![cifar_loss](https://github.com/22kollasiddarth/ann/assets/34851034/5b92e135-b2a2-4dee-b4a9-b66c89fadd9d)
![cifar_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/c4274c7b-8c86-44cc-bb97-e3f67dabcb9f)

**Ann_debris:**

![debris_loss](https://github.com/22kollasiddarth/ann/assets/34851034/7ac87017-d801-43e9-a475-b85c01a441c8)
![debris_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/5790dacf-b26a-4fd8-b593-8a59a24fa9fb)

**Ann_satellite_parts:**

![satellite_loss](https://github.com/22kollasiddarth/ann/assets/34851034/343d55f4-6b2e-42a9-ae8d-35bdb0c0e89b)
![satellite_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/d5971936-ee66-4711-995a-bf3db81bd13a)

**Ann_asteroids:**

![asteroid_loss](https://github.com/22kollasiddarth/ann/assets/34851034/b956a982-aff0-4abf-97a1-81b2c4f3c3cf)
![asteroid_accuracy](https://github.com/22kollasiddarth/ann/assets/34851034/91c000c0-f908-4fa2-8e75-1c063d2c05b7)

# Analysis/Discussion:
The accuracy for the binary classifier was quite high, scoring between 95-100% for the validation and training accuracy at the end of 20 epochs. Similar results were achieved for the multiclass image classifier (with animal images), with the training and validation accuracies scoring around the 90-100% range for the final epoch. These high accuracies are seen in lower loss values as well. These results were pretty expected, as each class is relatively distinct, and the Google Image datasets were pretty accurate with having the right animals in each folder. 

The CIFAR NN classifier followed similar patterns as the binary and multiclass image classifiers but did not achieve as high of an accuracy and had more loss at the end of training. This could be due to many reasons, including the fact that there are many more classes, and the images are more downsized in resolution. To compensate for this, I tried adding complexity to the NN, and this helped increase accuracy to a certain extent. 

The 3 experimental NN, which were for asteroid detection, satellite component detection, and space debris detection achieved a lot lower accuracy than the other 3 NNs. I tried many things to increase the performance of these NNs, including various normalization techniques and increasing/decreasing model complexity, but they didn’t help too much. For all 3 programs, the validation dataset accuracy was a lot less than the testing dataset accuracy, which could mean that the models are overfitting. After decreasing model complexity, the results still remained the same, so I’m thinking that these accuracy discrepancies might have to do with dataset issues, especially because Google Images does not produce the most accurate datasets.  

However, I still had so much fun trying to apply the NN towards these experimental industry-related applications, and it was cool comparing the performances of one NN with the other. Perhaps with more accurate datasets that are larger, some of the model accuracies can increase. Similarly, I could experiment more with various forms of uncertainty quantification and normalization for these 3 experimental applications. 

With regards to validating the bounds of the NN, many of the datasets (as a result of being from Google Images) contained images that may not have belonged to the category, which hopefully helped train the NN for when it sees images that may not be very similar to the “dictionary image” of what that object may look like. In contrast, because datasets like CIFAR are a lot more reliable, these datasets allow the NN to be a lot more confident when it sees an image from a certain class. 

Nonlinearity in the NNs was introduced through the activation functions, which allows the model to make more intricate distinctions between different features. The relu activation functions specifically change negative input values to zero, which assists the model in understanding complexities in the image data. The output layers in the NNs were either softmax or sigmoid activation functions. Softmax functions work by converting output scores into probability distributions for all the classes, whereas sigmoid functions work by “squashing” the final relu outputs into a range between 0 and 1. All of these activation functions work together to introduce nonlinearity and improve accuracy/decrease loss. 

For the multiclass NNs (which were all the programs except binary classification), cross-entropy loss was used to optimize the NN models. The overarching objective of the model is to minimize the cross-entropy loss, and it does this by computing gradients from the loss function and using that gradient to adjust the weights and biases of the different nodes and layers. The addition of a dropout layer creates regularization, which helps prevent overfitting that may result from computations in the loss function. 

Overall, this entire process was such an amazing introduction to Neural Networks and their many applications. While building the NNs themselves was tough, looking back, I learned so much and gained many insights into ML/AI. Hopefully, I can use what I learned from this experience for classes, jobs, and even personal projects in the future!



