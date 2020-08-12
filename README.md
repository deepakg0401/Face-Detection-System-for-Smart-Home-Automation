# Face-Detection-System-for-Smart-Home-Automation

A prototype for a face detection system for both images as well as video input which can be used in Smart Homes is presented.This prototype is modelled not for embedded systems but can be used in microcontrollers like Arduino and Raspberry Pi.This model uses a pre-trained ResNet network Architecture for getting encodings for images of 5 different people.It uses deep metric learning which involves getting the encodings in form of 128-d vector and then getting predictions using kNN-based model.

## Model and libraries used
- Libraries used:- dlib,facerecognition,opencv.
- Instead, of trying to output a single label (or even the coordinates/bounding box of objects in an image), we are instead outputting a real-valued feature vector using ’deep metric learning’.
- For the dlib facial recognition network, the output feature vector is 128-d (i.e., a list of 128 real-valued numbers) that is used to quantify the face. Training the network is done using triplets(2 same person images and one different person image).

- From there, the general idea is that well tweak the weights of our neural network so that the 128-d measurements of the two images of same person will be closer to each other and farther from the measurements for the image with different person.

- The dlib library, maintained by Davis King, contains our implementation of deep metric learning which is used to construct our face embeddings used for the actual recognition process.

- Our network architecture for face recognition is based on ResNet-34 but with fewer layers and the number of filters reduced by half.The network itself was trained by Davis King on a dataset of 3 million images. On the Labeled Faces in the Wild (LFW) dataset the network compares to other state-of-the-art methods, reaching 99.38 per cent accuracy.


- Used the pre-trained network to construct 128-d embeddings for each of the 150 faces(30 images of 5 different people) in our dataset.Then, during classification, we can use a simple k-NN model + votes to make the final face classification.

## Results and Conclusion

- A net accuracy of 81.94 per cent was observed on the manually compiled dataset.In real time video input mostly correct predictions are made throughout the video stream.
- Some improvements can be made by gathering a larger dataset with much wider and different range of images at various angles,brightness,with extremely localised faces and other different features.
