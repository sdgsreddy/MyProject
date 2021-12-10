PROJECT ON RECOGNITION OF TRAFFIC SIGNS
Project made by- Durga Guna Sekhar Reddy Savanam
Abstract
Traffic signs classification is the process of identifying which class a traffic sign 
belongs to. In the world of Artificial Intelligence and advancement in 
technologies, many researchers and big companies like Tesla, Uber, Google, 
Mercedes-Benz, Toyota, Ford, Audi, etc. are working on autonomous vehicles 
and self-driving cars. So, for achieving accuracy in this technology, the vehicles 
should be able to interpret traffic signs and make decisions accordingly. To 
recognize the traffic signs automatically by the vehicles automatically. For this 
project we are using the public dataset (.csv file) available at Kaggle. The dataset 
contains more than 50,000 images of different traffic signs. It is further 
classified into 43 different classes. The dataset is quite varying, some of the 
classes have many images while some classes have few images. The size of the 
dataset is around 300 MB. The dataset has a train folder which contains images 
inside each class and a test folder which we will use for testing our model.

INTRODUCTION
You must have heard about the self-driving cars in which the passenger can fully 
depend on the car for traveling. But to achieve level 5 autonomous, it is necessary 
for vehicles to understand and follow all traffic rules. In the world of Artificial 
Intelligence and advancement in technologies, many researchers and big 
companies like Tesla, Uber, Google, Mercedes-Benz, Toyota, Ford, Audi, etc are 
working on autonomous vehicles and self-driving cars. So, for achieving 
accuracy in this technology, the vehicles should be able to interpret traffic signs 
and make decisions accordingly. A key part of being able to diagnose a problem 
with advanced driver assistance systems (ADAS) is understanding how the 
system works. Knowing what is happening inside the system will help you 
properly diagnose why the system may be failing. This will prevent replacing 
parts that are not causing the system issue. Let’s take a look at the inner workings 
of a traffic sign recognition system.
The traffic sign recognition system "sees" road signs and then displays them to 
the driver of the vehicle. They are typically displayed on a screen located in the 
instrument cluster. This system usually uses a forward-facing camera located 
behind the windshield that "looks" for road signs. Some vehicles use a dedicated 
forward-facing camera for this system, while others use the same ADAS camera 
used for lane departure warning and other systems.
Some vehicles have a haptic (vibration) or audible warning that is activated when 
the driver, for example, is not following the posted speed limit, or is entering a 
"do not enter" roadway. The system may save recognized signs to "memory" after 
displaying them, so that same sign is more easily identified the next time. It is 
important to look at vehicle-specific OEM service information to make sure you 
know what components are part of this system, and what is needed to repair the 
system correctly.
Understanding how the system functions can shorten diagnostic times. Knowing 
what part of the system to test will help prevent installing parts that don’t actually 
fix the problem. There are several different types of traffic signs like speed limits, 
no entry, traffic signals, turn left or right, children crossing, no passing of heavy 
vehicles, etc. Traffic signs classification is the process of identifying which class 
a traffic sign belongs to.

PROJECT APPROACH
Our approach to building this traffic sign classification model is discussed in four 
steps:
✓ Explore the dataset
✓ Build a CNN model
✓ Train and validate the model
✓ Test the model with test dataset
Our ‘train’ folder contains 43 folders each representing a different class. The 
range of the folder is from 0 to 42. With the help of the OS module, we iterate 
over all the classes and append images and their respective labels in the data and 
labels list. We need to convert the list into numpy arrays for feeding to the model.
The shape of data is (39209, 30, 30, 3) which means that there are 39,209 images 
of size 30×30 pixels and the last 3 means the data contains colored images (RGB 
value).With the sklearn package, we use the train_test_split() method to split 
training and testing data.From the keras.utils package, we use to_categorical 
method to convert the labels present in y_train and t_test into one-hot encoding.
To classify the images into their respective categories, we will build a CNN model 
(Convolutional Neural Network). CNN is best for image classification purposes.
The architecture of our model is:
• 2 Conv2D layer (filter=32, kernel_size=(5,5), activation=”relu”)
• MaxPool2D layer ( pool_size=(2,2))
• Dropout layer (rate=0.25)
• 2 Conv2D layer (filter=64, kernel_size=(3,3), activation=”relu”)
• MaxPool2D layer ( pool_size=(2,2))
• Dropout layer (rate=0.25)
• Flatten layer to squeeze the layers into 1 dimension
• Dense Fully connected layer (256 nodes, activation=”relu”)
• Dropout layer (rate=0.5)
• Dense layer (43 nodes, activation=”softmax”)
We compile the model with Adam optimizer which performs well and loss is 
“categorical_crossentropy” because we have multiple classes to categorise. After 
building the model architecture, we then train the model using model.fit(). I tried 
with batch size 32 and 64. Our model performed better with 64 batch size. And 
after 15 epochs the accuracy was stable.
Our dataset contains a test folder and in a test.csv file, we have the details related 
to the image path and their respective class labels. We extract the image path and 
labels using pandas. Then to predict the model, we have to resize our images to 
30×30 pixels and make a numpy array containing all image data. From the 
sklearn.metrics, we imported the accuracy_score and observed how our model 
predicted the actual labels. We achieved a 95% accuracy in this model.

REFERENCES
https://data-flair.training/blogs/python-project-traffic-signs-recognition/
https://rts.i-car.com/collision-repair-news/understanding-the-traffic-signrecognition-system.html
