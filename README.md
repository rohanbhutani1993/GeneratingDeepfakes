# GeneratingDeepfakes
The word “deepfake” is a play on the words “Deep Learning” and “fake”. It is an AI-based technology that uses a person's face and voice to create fake videos and audio that look and sound real.
In this repository, you'll find the code to generate Deepfakes using DCGAN. To keep it simple, I have used MNIST dataset as the source and then I have generated deepfakes fo the handwritten digits.

The tfutils package can be downloaded using the following command:
pip3 install git+https://github.com/am1tyadav/tfutils.git

Here's the summary of the model.
Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d (Conv2D)              (None, 13, 13, 64)        640       
_________________________________________________________________
leaky_re_lu (LeakyReLU)      (None, 13, 13, 64)        0         
_________________________________________________________________
batch_normalization (BatchNo (None, 13, 13, 64)        256       
_________________________________________________________________
conv2d_1 (Conv2D)            (None, 5, 5, 128)         204928    
_________________________________________________________________
leaky_re_lu_1 (LeakyReLU)    (None, 5, 5, 128)         0         
_________________________________________________________________
batch_normalization_1 (Batch (None, 5, 5, 128)         512       
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 1, 1, 256)         819456    
_________________________________________________________________
leaky_re_lu_2 (LeakyReLU)    (None, 1, 1, 256)         0         
_________________________________________________________________
batch_normalization_2 (Batch (None, 1, 1, 256)         1024      
_________________________________________________________________
flatten (Flatten)            (None, 256)               0         
_________________________________________________________________
dense (Dense)                (None, 1)                 257       
=================================================================
Total params: 1,027,073
Trainable params: 1,026,177
Non-trainable params: 896
_________________________________________________________________
Model: "sequential_1"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_1 (Dense)              (None, 256)               512       
_________________________________________________________________
reshape (Reshape)            (None, 1, 1, 256)         0         
_________________________________________________________________
conv2d_transpose (Conv2DTran (None, 5, 5, 256)         1638656   
_________________________________________________________________
batch_normalization_3 (Batch (None, 5, 5, 256)         1024      
_________________________________________________________________
conv2d_transpose_1 (Conv2DTr (None, 9, 9, 128)         819328    
_________________________________________________________________
batch_normalization_4 (Batch (None, 9, 9, 128)         512       
_________________________________________________________________
conv2d_transpose_2 (Conv2DTr (None, 21, 21, 64)        204864    
_________________________________________________________________
batch_normalization_5 (Batch (None, 21, 21, 64)        256       
_________________________________________________________________
conv2d_transpose_3 (Conv2DTr (None, 25, 25, 32)        51232     
_________________________________________________________________
batch_normalization_6 (Batch (None, 25, 25, 32)        128       
_________________________________________________________________
conv2d_transpose_4 (Conv2DTr (None, 28, 28, 1)         513       
=================================================================
Total params: 2,717,025
Trainable params: 2,716,065
Non-trainable params: 960
_________________________________________________________________

Model: "model"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
input_1 (InputLayer)         [(None, 1)]               0         
_________________________________________________________________
sequential_1 (Sequential)    (None, 28, 28, 1)         2717025   
_________________________________________________________________
sequential (Sequential)      (None, 1)                 1027073   
=================================================================
Total params: 3,744,098
Trainable params: 2,716,065
Non-trainable params: 1,028,033
_________________________________________________________________
Steps per epoch =  107

The first model acts as a discriminator and the second as a generator.
For the implementation part, I have used this research paper as my reference - FaceNet: A Unified Embedding for Face Recognition and Clustering
Link to the papaer - https://arxiv.org/pdf/1503.03832.pdf
