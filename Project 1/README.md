
Questions:

Q1) What are Channels and Kernels (according to EVA)?

channels is a container of similar things like input image can be divided into 3 channels RGB.R channel contains red color object information.similarly green and blue.
Each filter applied to image will generate one result.

If input image is 224x224x3 it is convolved with 5 of 3*3 kernels with stride=1 result will be 222x222x5


Q2)Why should we only (well mostly) use 3x3 Kernels?
In convolution we do combination of element-wise product of 2 matrices. convolution is done to encode input image in terms of kernel/feature extractor/filter. More specifically we encode pixels in neighbourhood of anchor/source pixels. Each kernel will have source pixel- anchor point at which kernel is centered and encoded all neighboring pixel and source pixel. kernel should be symmetrically shaped meaning it should have equal number of pixel on all sides of anchor pixel.Therefore, whatever this number of pixels maybe, the length of each side of our symmetrically shaped kernel is 2*n+1 (each side of the anchor + the anchor pixel), and therefore filter/kernels are always odd sized.

- asymmetric kernels suffer from aliasing errors, and so we don't do it. We consider the pixel to be the smallest entity, i.e. there is no sub-pixel concept here.


For an odd-sized filter, all the previous layer pixels would be symmetrically around the output pixel. Without this symmetry, we will have to account for distortions across the layers which happens when using an even-sized kernel. Therefore, even-sized kernel filters are mostly skipped to promote implementation simplicity. If you think of convolution as an interpolation from the given pixels to a center pixel, we cannot interpolate to a center pixel using an even-sized filter.



Q3)How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)
solution: - Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is: 99

n=199
count=0
while n>=3:
    count=count+1
    print(str(n)+'x'+str(n)+'  '+'conv'+'  '+'3x3'+'----------------> '+ str(n-2)+'x'+str(n-2))
    n=n-2 
    
print("Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is:",count)



199x199  conv  3x3----------------> 197x197
197x197  conv  3x3----------------> 195x195
195x195  conv  3x3----------------> 193x193
193x193  conv  3x3----------------> 191x191
191x191  conv  3x3----------------> 189x189
189x189  conv  3x3----------------> 187x187
187x187  conv  3x3----------------> 185x185
185x185  conv  3x3----------------> 183x183
183x183  conv  3x3----------------> 181x181
181x181  conv  3x3----------------> 179x179
179x179  conv  3x3----------------> 177x177
177x177  conv  3x3----------------> 175x175
175x175  conv  3x3----------------> 173x173
173x173  conv  3x3----------------> 171x171
171x171  conv  3x3----------------> 169x169
169x169  conv  3x3----------------> 167x167
167x167  conv  3x3----------------> 165x165
165x165  conv  3x3----------------> 163x163
163x163  conv  3x3----------------> 161x161
161x161  conv  3x3----------------> 159x159
159x159  conv  3x3----------------> 157x157
157x157  conv  3x3----------------> 155x155
155x155  conv  3x3----------------> 153x153
153x153  conv  3x3----------------> 151x151
151x151  conv  3x3----------------> 149x149
149x149  conv  3x3----------------> 147x147
147x147  conv  3x3----------------> 145x145
145x145  conv  3x3----------------> 143x143
143x143  conv  3x3----------------> 141x141
141x141  conv  3x3----------------> 139x139
139x139  conv  3x3----------------> 137x137
137x137  conv  3x3----------------> 135x135
135x135  conv  3x3----------------> 133x133
133x133  conv  3x3----------------> 131x131
131x131  conv  3x3----------------> 129x129
129x129  conv  3x3----------------> 127x127
127x127  conv  3x3----------------> 125x125
125x125  conv  3x3----------------> 123x123
123x123  conv  3x3----------------> 121x121
121x121  conv  3x3----------------> 119x119
119x119  conv  3x3----------------> 117x117
117x117  conv  3x3----------------> 115x115
115x115  conv  3x3----------------> 113x113
113x113  conv  3x3----------------> 111x111
111x111  conv  3x3----------------> 109x109
109x109  conv  3x3----------------> 107x107
107x107  conv  3x3----------------> 105x105
105x105  conv  3x3----------------> 103x103
103x103  conv  3x3----------------> 101x101
101x101  conv  3x3----------------> 99x99
99x99  conv  3x3----------------> 97x97
97x97  conv  3x3----------------> 95x95
95x95  conv  3x3----------------> 93x93
93x93  conv  3x3----------------> 91x91
91x91  conv  3x3----------------> 89x89
89x89  conv  3x3----------------> 87x87
87x87  conv  3x3----------------> 85x85
85x85  conv  3x3----------------> 83x83
83x83  conv  3x3----------------> 81x81
81x81  conv  3x3----------------> 79x79
79x79  conv  3x3----------------> 77x77
77x77  conv  3x3----------------> 75x75
75x75  conv  3x3----------------> 73x73
73x73  conv  3x3----------------> 71x71
71x71  conv  3x3----------------> 69x69
69x69  conv  3x3----------------> 67x67
67x67  conv  3x3----------------> 65x65
65x65  conv  3x3----------------> 63x63
63x63  conv  3x3----------------> 61x61
61x61  conv  3x3----------------> 59x59
59x59  conv  3x3----------------> 57x57
57x57  conv  3x3----------------> 55x55
55x55  conv  3x3----------------> 53x53
53x53  conv  3x3----------------> 51x51
51x51  conv  3x3----------------> 49x49
49x49  conv  3x3----------------> 47x47
47x47  conv  3x3----------------> 45x45
45x45  conv  3x3----------------> 43x43
43x43  conv  3x3----------------> 41x41
41x41  conv  3x3----------------> 39x39
39x39  conv  3x3----------------> 37x37
37x37  conv  3x3----------------> 35x35
35x35  conv  3x3----------------> 33x33
33x33  conv  3x3----------------> 31x31
31x31  conv  3x3----------------> 29x29
29x29  conv  3x3----------------> 27x27
27x27  conv  3x3----------------> 25x25
25x25  conv  3x3----------------> 23x23
23x23  conv  3x3----------------> 21x21
21x21  conv  3x3----------------> 19x19
19x19  conv  3x3----------------> 17x17
17x17  conv  3x3----------------> 15x15
15x15  conv  3x3----------------> 13x13
13x13  conv  3x3----------------> 11x11
11x11  conv  3x3----------------> 9x9
9x9  conv  3x3----------------> 7x7
7x7  conv  3x3----------------> 5x5
5x5  conv  3x3----------------> 3x3
3x3  conv  3x3----------------> 1x1
Number of times required to perform 3x3 convolution operation to reach 1x1 from 199x199  is: 99




