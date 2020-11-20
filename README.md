# Image-Captioning
It is the implementation of a soft attention based Image Caption Generator. It is based on widely used Encoder-Decoder Framework, where the encoder is a Convolutional Neural Network (CNN) and the decoder has long short-term memory(LSTM) architecture. This repository uses [ResNet-50](https://arxiv.org/abs/1512.03385) model pretrained on [ILSVRC-2012](http://www.image-net.org/challenges/LSVRC/2012/) dataset for encoding. Soft attention mechanism is implemented to better understand the semantics of the images. The captions are generated using Beam-Search algorithm. This implementation is roughly based on the paper "Show, Attend and Tell: Neural Image Caption Generation with Visual Attention" by Xu et al. (ICML2015).

### Usage

To train a model using any dataset, first download and place the training images in `./train_images/`. The path for training images and captions can be configured from `utils_rasha.py`. 

Example code for training the model:
```shell
python main_rasha.py --gpu 0 --embed_size 512 --hidden_dim 512 --num_layers 1 --batch_size 8 --lr 4e-4 --epochs 10 --train True --train_enc False --bw 5
```

### Arguments

<ul>
  <li> gpu   - Indicates GPU index
  <li> embed_size - Embedding dimension of encoder module
  <li> hidden_dim - Hidden Dimension in LSTM 
  <li> num_layers - Number of layers in LSTM
  <li> batch_size - Batch Size to train with
  <li> lr - Learning rate of training
  <li> epochs - Number of epochs to train the model
  <li> train - If <b>True</b>, indicates to train the model from scratch, else loads saved checkpoints
  <li> train_enc - If <b>True</b>, uses pre-trained CNN as encoder
  <li> bw - Beam Width for Beam Search Algorithm
    
</ul>

### Results 

For experimenting, an Italian caption dataset is used. Training images can be found [here](https://owncloud.iitd.ac.in/nextcloud/index.php/s/bpsRreMBSEAZyy7) and training captions are [here](https://owncloud.iitd.ac.in/nextcloud/index.php/s/ZiAsmexxADBcb3J). A SacreBleu score of 14.64 is obtained through evaluation on test data ([Testing images](https://owncloud.iitd.ac.in/nextcloud/index.php/s/eGZydAwPwrCygen), [Testing captions](https://owncloud.iitd.ac.in/nextcloud/index.php/s/8ZoDbDno7aiRBo7)) 




### References
* [Show, Attend and Tell: Neural Image Caption Generation with Visual Attention](https://arxiv.org/abs/1502.03044). Kelvin Xu, Jimmy Ba, Ryan Kiros, Kyunghyun Cho, Aaron Courville, Ruslan Salakhutdinov, Richard Zemel, Yoshua Bengio. ICML 2015.
