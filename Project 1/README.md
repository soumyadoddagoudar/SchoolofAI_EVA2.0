
Questions:

Q1) What are Channels and Kernels (according to EVA)?

channels is a container of similar things like input image can be divided into 3 channels RGB.R channel contains red color object information.similarly green and blue.
Each filter applied to image will generate one result.

If input image is 224*224*3 it is convolved with 5 3*3 kernels with stride=1 result will be 222 *222 *5


Q2)Why should we only (well mostly) use 3x3 Kernels?


Q3)How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)
