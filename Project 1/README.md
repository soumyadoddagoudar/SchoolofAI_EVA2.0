
Questions:

# Q1) What are Channels and Kernels (according to EVA)?

channels is a container of similar things like input image can be divided into 3 channels RGB.R channel contains red color object information.similarly green and blue.
Each filter applied to image will generate one result.

If input image is 224x224x3 it is convolved with 5 of 3*3 kernels with stride=1 result will be 222x222x5


# Q2)Why should we only (well mostly) use 3x3 Kernels?

In convolution we do combination of element-wise product of 2 matrices. convolution is done to encode input image in terms of kernel/feature extractor/filter. More specifically we encode pixels in neighbourhood of anchor/source pixels. Each kernel will have source pixel- anchor point at which kernel is centered and encoded all neighboring pixel and source pixel. kernel should be symmetrically shaped meaning it should have equal number of pixel on all sides of anchor pixel.Therefore, whatever this number of pixels maybe, the length of each side of our symmetrically shaped kernel is 2*n+1 (each side of the anchor + the anchor pixel), and therefore filter/kernels are always odd sized.

- asymmetric kernels suffer from aliasing errors, and so we don't do it. We consider the pixel to be the smallest entity, i.e. there is no sub-pixel concept here.


For an odd-sized filter, all the previous layer pixels would be symmetrically around the output pixel. Without this symmetry, we will have to account for distortions across the layers which happens when using an even-sized kernel. Therefore, even-sized kernel filters are mostly skipped to promote implementation simplicity. If you think of convolution as an interpolation from the given pixels to a center pixel, we cannot interpolate to a center pixel using an even-sized filter.



# Q3)How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)

solution: - Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is: 99

n=199  <br/>
count=0 <br/>
while n>=3: <br/>
    count=count+1 <br/>
    print('<br>'+str(n)+'x'+str(n)+'  '+'conv'+'  '+'3x3'+'----------------> '+ str(n-2)+'x'+str(n-2)+'<br/>') <br/>
    n=n-2 <br/>
    
print("Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is:",count)<br/>


<br>199x199  conv  3x3----------------> 197x197<br/>
<br>197x197  conv  3x3----------------> 195x195<br/>
<br>195x195  conv  3x3----------------> 193x193<br/>
<br>193x193  conv  3x3----------------> 191x191<br/>
<br>191x191  conv  3x3----------------> 189x189<br/>
<br>189x189  conv  3x3----------------> 187x187<br/>
<br>187x187  conv  3x3----------------> 185x185<br/>
<br>185x185  conv  3x3----------------> 183x183<br/>
<br>183x183  conv  3x3----------------> 181x181<br/>
<br>181x181  conv  3x3----------------> 179x179<br/>
<br>179x179  conv  3x3----------------> 177x177<br/>
<br>177x177  conv  3x3----------------> 175x175<br/>
<br>175x175  conv  3x3----------------> 173x173<br/>
<br>173x173  conv  3x3----------------> 171x171<br/>
<br>171x171  conv  3x3----------------> 169x169<br/>
<br>169x169  conv  3x3----------------> 167x167<br/>
<br>167x167  conv  3x3----------------> 165x165<br/>
<br>165x165  conv  3x3----------------> 163x163<br/>
<br>163x163  conv  3x3----------------> 161x161<br/>
<br>161x161  conv  3x3----------------> 159x159<br/>
<br>159x159  conv  3x3----------------> 157x157<br/>
<br>157x157  conv  3x3----------------> 155x155<br/>
<br>155x155  conv  3x3----------------> 153x153<br/>
<br>153x153  conv  3x3----------------> 151x151<br/>
<br>151x151  conv  3x3----------------> 149x149<br/>
<br>149x149  conv  3x3----------------> 147x147<br/>
<br>147x147  conv  3x3----------------> 145x145<br/>
<br>145x145  conv  3x3----------------> 143x143<br/>
<br>143x143  conv  3x3----------------> 141x141<br/>
<br>141x141  conv  3x3----------------> 139x139<br/>
<br>139x139  conv  3x3----------------> 137x137<br/>
<br>137x137  conv  3x3----------------> 135x135<br/>
<br>135x135  conv  3x3----------------> 133x133<br/>
<br>133x133  conv  3x3----------------> 131x131<br/>
<br>131x131  conv  3x3----------------> 129x129<br/>
<br>129x129  conv  3x3----------------> 127x127<br/>
<br>127x127  conv  3x3----------------> 125x125<br/>
<br>125x125  conv  3x3----------------> 123x123<br/>
<br>123x123  conv  3x3----------------> 121x121<br/>
<br>121x121  conv  3x3----------------> 119x119<br/>
<br>119x119  conv  3x3----------------> 117x117<br/>
<br>117x117  conv  3x3----------------> 115x115<br/>
<br>115x115  conv  3x3----------------> 113x113<br/>
<br>113x113  conv  3x3----------------> 111x111<br/>
<br>111x111  conv  3x3----------------> 109x109<br/>
<br>109x109  conv  3x3----------------> 107x107<br/>
<br>107x107  conv  3x3----------------> 105x105<br/>
<br>105x105  conv  3x3----------------> 103x103<br/>
<br>103x103  conv  3x3----------------> 101x101<br/>
<br>101x101  conv  3x3----------------> 99x99<br/>
<br>99x99  conv  3x3----------------> 97x97<br/>
<br>97x97  conv  3x3----------------> 95x95<br/>
<br>95x95  conv  3x3----------------> 93x93<br/>
<br>93x93  conv  3x3----------------> 91x91<br/>
<br>91x91  conv  3x3----------------> 89x89<br/>
<br>89x89  conv  3x3----------------> 87x87<br/>
<br>87x87  conv  3x3----------------> 85x85<br/>
<br>85x85  conv  3x3----------------> 83x83<br/>
<br>83x83  conv  3x3----------------> 81x81<br/>
<br>81x81  conv  3x3----------------> 79x79<br/>
<br>79x79  conv  3x3----------------> 77x77<br/>
<br>77x77  conv  3x3----------------> 75x75<br/>
<br>75x75  conv  3x3----------------> 73x73<br/>
<br>73x73  conv  3x3----------------> 71x71<br/>
<br>71x71  conv  3x3----------------> 69x69<br/>
<br>69x69  conv  3x3----------------> 67x67<br/>
<br>67x67  conv  3x3----------------> 65x65<br/>
<br>65x65  conv  3x3----------------> 63x63<br/>
<br>63x63  conv  3x3----------------> 61x61<br/>
<br>61x61  conv  3x3----------------> 59x59<br/>
<br>59x59  conv  3x3----------------> 57x57<br/>
<br>57x57  conv  3x3----------------> 55x55<br/>
<br>55x55  conv  3x3----------------> 53x53<br/>
<br>53x53  conv  3x3----------------> 51x51<br/>
<br>51x51  conv  3x3----------------> 49x49<br/>
<br>49x49  conv  3x3----------------> 47x47<br/>
<br>47x47  conv  3x3----------------> 45x45<br/>
<br>45x45  conv  3x3----------------> 43x43<br/>
<br>43x43  conv  3x3----------------> 41x41<br/>
<br>41x41  conv  3x3----------------> 39x39<br/>
<br>39x39  conv  3x3----------------> 37x37<br/>
<br>37x37  conv  3x3----------------> 35x35<br/>
<br>35x35  conv  3x3----------------> 33x33<br/>
<br>33x33  conv  3x3----------------> 31x31<br/>
<br>31x31  conv  3x3----------------> 29x29<br/>
<br>29x29  conv  3x3----------------> 27x27<br/>
<br>27x27  conv  3x3----------------> 25x25<br/>
<br>25x25  conv  3x3----------------> 23x23<br/>
<br>23x23  conv  3x3----------------> 21x21<br/>
<br>21x21  conv  3x3----------------> 19x19<br/>
<br>19x19  conv  3x3----------------> 17x17<br/>
<br>17x17  conv  3x3----------------> 15x15<br/>
<br>15x15  conv  3x3----------------> 13x13<br/>
<br>13x13  conv  3x3----------------> 11x11<br/>
<br>11x11  conv  3x3----------------> 9x9<br/>
<br>9x9  conv  3x3----------------> 7x7<br/>
<br>7x7  conv  3x3----------------> 5x5<br/>
<br>5x5  conv  3x3----------------> 3x3<br/>
<br>3x3  conv  3x3----------------> 1x1<br/>
Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is: 99




