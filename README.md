# Semantic Segmentation
A project to semantically segment images with SegNet-like architecture

The reference paper [1] can be found at https://arxiv.org/pdf/1511.00561.pdf

SegNet-like because the Maxpooling indices are not shared with decoder.

Use KITTI semantic segmentation dataset and create following folder structure

    |_kitti/
    |    |__train/
    |    |   |_images/
    |    |   |_labels/
    |    |__test/
    |        |_images/
    |        |_labels/
    |_main.py
    |_helper.py

## Usage
    $ pip install -r requirements.txt
    $ python main.py
    $ tensorboard --logdir=graph/
    
## Background
This semantic segmentation neural network architecure follows an Encoder-Decoder pattern. Here the image in convolved and maxpooled in the encoder and transpose-convolved and upsampled in the decoder network. Encoder network is used for image recognition and decoder for image segmentation. Utilising the transfer learning [2] technique, the encoder network was replaced with pre trained VGG16 [3] CNN to reduce training time and improve the accuracy. This made the CNN smaller and simpler enough to be trained using a GeForce 940M.

Training ran for 200 epocs with 8 images per batch. 
    
## References:

 [1]   V. Badrinarayanan, A. Kendall, and R. Cipolla, "SegNet: A Deep Convolutional Encoder-Decoder Architecture for Image    Segmentation",  *arXiv:1511.005eprint61*, 2015.
 
 [2]  A. Karpathy, "CS231n Convolutional Neural Networks for Visual Recognition", Available: http://cs231n.github.io/transfer-learning/
 
 [3] K. Simonyan & A. Zisserman, "Very Deep Convolutional Networks for Large-Scale Image Recognition", *ICLR 2015*, https://arxiv.org/pdf/1409.1556.pdf
