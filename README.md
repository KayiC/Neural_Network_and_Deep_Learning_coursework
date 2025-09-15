# Neural_Network_and_Deep_Learning_coursework
Model Architecture Overview
Stem

Function: Takes the input image and extracts a feature representation.
Implementation: Typically consists of a convolutional layer.
Backbone

Structure: Composed of N Blocks (B1, B2, ..., Bn).
Block Structure:
Expert Branch:

Receives input from the Stem for the first block and from the previous block for subsequent ones.
Function: Generates a vector 
𝑎
=
[
𝑎
1
,
𝑎
2
,
.
.
.
,
𝑎
𝑘
]
a=[a 
1
​
 ,a 
2
​
 ,...,a 
k
​
 ] from the input tensor 
𝑋
X.
Steps:
Spatially pool the features: 
𝑋
′
=
AvgPool
(
𝑋
)
X 
′
 =AvgPool(X).
Forward through a Fully Connected layer 
FC1
FC1 to reduce channel dimensions by a factor 
𝑟
r.
Apply a non-linear activation function 
𝑔
g.
Another Fully Connected layer 
FC2
FC2 projects to 
𝐾
K.
Final output is passed through a Softmax layer to obtain 
𝑎
a.
Convolutional Branch:

Consists of 
𝑘
k convolutional layers.
Combines outputs using the vector 
𝑎
a:
𝑂
=
𝑎
1
⋅
Conv
1
(
𝑋
)
+
𝑎
2
⋅
Conv
2
(
𝑋
)
+
…
+
𝑎
𝑘
⋅
Conv
𝑘
(
𝑋
)
O=a 
1
​
 ⋅Conv 
1
​
 (X)+a 
2
​
 ⋅Conv 
2
​
 (X)+…+a 
k
​
 ⋅Conv 
k
​
 (X)
Classifier

Input: Output from the last block 
𝑂
𝑛
O 
n
​
 .
Function: Computes a mean feature 
𝑓
=
SpatialAveragePool
(
𝑂
𝑛
)
f=SpatialAveragePool(O 
n
​
 ).
Implementation: Can be a softmax regression classifier or a multi-layer perceptron (MLP).
