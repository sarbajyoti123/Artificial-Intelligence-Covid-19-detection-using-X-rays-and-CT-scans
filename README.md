# Covid-19-detection-using-X-rays-and-CT-scans
This Covid-19 detection detects Covid-19,Pneumonia and Normal from Xrays &amp; CT-scans.Its accuracy rate is 98% on training and 93% on testing

Methodology:- Here we take a 256 x 256 input image and multiply it with a different feature detector with a stride of 1 and also with rectilinear activation function to get the best feature from the input image .Here we take  3 x 3 feature detector and multiply with huge matrix of 256 x 256 input image to reduce the size of the matrix of the image. After that we apply Max pooling, so we take a box of two by two pixels and place it in the top left hand corner and we find the maximum value in that box and then we reduced only that value. Then we move the box to the right with a stride of two. Here  we do Max pooling to reduce the size of the 32 different feature maps and as a result we get 32 pooled feature map. To get best accuracy in our train and test set we have added 3 more convolution layer - First one with 3 x 3 matrix of 32 feature detector. Second one is with 3 x 3 matrix of 64 feature detector and third one is 3 x 3 matrix of 128 feature detector and I have added max pooling with each of these convolution layer. Now we take each and every pooled feature map and flatten it into a column so basically you just take the number row by row from pooled feature map and put them into one long column to get a one huge vector of inputs for an artificial neural network .

![2019-11-21 (49)](https://user-images.githubusercontent.com/44479743/89053554-06fb7a80-d375-11ea-8704-f7485f0c2cae.png)


Now we make two fully connected layer with output_dim(Dimension of dense embedding ) of 128 and also with rectilinear activation function we use categorical cross entropy to calculate the loss so the error is calculated in the output layer with softmax activation function and with adam optimizer is back propagated through the network again and again to adjust the network and to optimize the performance. After that we train the dataset of Normal, Pneumonia and Covid-19 with a target size of 256 x 256 batch size of 10 and also the test set of Normal, Pneumonia and Covid-19 with a target size of 256 x 256 batch size of 2 and with 50 epoch .

![Screenshot (87)](https://user-images.githubusercontent.com/44479743/89053570-0cf15b80-d375-11ea-98e5-f967836889dd.png)


and we get 98% accuracy on train set and 93% accuracy on  test set. Then we take a infected x-ray image of a lung and test it in which category it was either it is covid-19 infected lung, pneumonia or normal. If the result is either covid-19 or pneumonia we take the image and do some image processing on that image to get more details. The image processing we used in our model are Binary, Binary Inverted, Zero, Zero Inverted, contours and truncated. After image processing the images are

![2020-04-30 (1)](https://user-images.githubusercontent.com/44479743/89053713-44600800-d375-11ea-8f11-ab3c60163b23.png)
Fig:-After applying image processing of Binary , Binary Inverted , Zero , Zero Inverted & Truncated

![2020-05-01 (6)](https://user-images.githubusercontent.com/44479743/89053898-86894980-d375-11ea-963e-f862c3d0dfa9.png)
Fig:-After filtering the Covid-19 X-Ray image

![2020-05-02 (4)](https://user-images.githubusercontent.com/44479743/89053907-8ab56700-d375-11ea-8855-f38bf2fc6c80.png)
Fig:-After applying Contours on Covid-19 X-Ray image

![fig4](https://user-images.githubusercontent.com/44479743/89053931-97d25600-d375-11ea-9fc8-cf16efa9d5ba.png)
Fig:- Negative image of Covid-19 X-Ray image

