
Questions:

Q1) What are Channels and Kernels (according to EVA)?

channels is a container of similar things like input image can be divided into 3 channels RGB.R channel contains red color object information.similarly green and blue.
Each filter applied to image will generate one result.

If input image is 224*224*3 it is convolved with 5 of 3*3 kernels with stride=1 result will be 222 *222 *5


Q2)Why should we only (well mostly) use 3x3 Kernels?
In convolution we do combination of element-wise product of 2 matrices. convolution is done to encode input image in terms of kernel/feature extractor/filter. More specifically we encode pixels in neighbourhood of anchor/source pixels. Each kernel will have source pixel- anchor point at which kernel is centered and encoded all neighboring pixel and source pixel. kernel should be symmetrically shaped meaning it should have equal number of pixel on all sides of anchor pixel.Therefore, whatever this number of pixels maybe, the length of each side of our symmetrically shaped kernel is 2*n+1 (each side of the anchor + the anchor pixel), and therefore filter/kernels are always odd sized.

- asymmetric kernels suffer from aliasing errors, and so we don't do it. We consider the pixel to be the smallest entity, i.e. there is no sub-pixel concept here.


For an odd-sized filter, all the previous layer pixels would be symmetrically around the output pixel. Without this symmetry, we will have to account for distortions across the layers which happens when using an even-sized kernel. Therefore, even-sized kernel filters are mostly skipped to promote implementation simplicity. If you think of convolution as an interpolation from the given pixels to a center pixel, we cannot interpolate to a center pixel using an even-sized filter.



Q3)How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)

199x199|3x3 >197x197


