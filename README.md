# Convolution Animations

Figures to explain how convolutional neural networks work.

Here are the equivalent commands in TensorFlow and PyTorch for the 2D convolution below.

[**TensorFlow**](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Conv2D)
```
  tf.keras.layers.Conv2D(
                        filters=2, 
                        kernel_size=(3,3), 
                        strides=(1, 1), 
                        padding='valid',
                        activation=None
                        )
```

[Arguments:](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Conv2D#args)
+ `filters=2` Indicates you want 2 convolutional kernels/filters. This means the output will have 2 channels (regardless of how many channels/layers are in the input tensor)
+ `kernel_size=(3,3)` Indicates a 3x3 convolutional kernel/filter
+ `strides=(1,1)` Indicates the kernel should move 1 pixel at a time in the first and second axes
+ `padding='valid'` Indicates no padding of the input. The kernel/filter must completely cover a valid pixel.
+ `activation=None` Indicates no activation function after the convolution. Applied to every pixel in the output. (e.g. ReLU, tanh, Sigmoid)

[**PyTorch**](https://pytorch.org/docs/stable/generated/torch.nn.Conv2d.html)
```
  torch.nn.Conv2d(in_channels=3, 
                  out_channels=2, 
                  kernel_size=(3,3), 
                  stride=1, 
                  padding=0, 
                  padding_mode='zeros'
                  )
```
+ `in_channels=3` Indicates there are 3 channels in the input tensor
+ `out_channels=2` Indicates you want 2 convolutional kernels/filters. This means the output will have 2 channels (regardless of how many channels in the input tensor)
+ `kernel_size=(3,3)` Indiciates a 3x3 convolutional kernel/filter
+ `stride=1` Indicates the kernel should move 1 pixel at a time in the first and second axes
+ `padding=0` Indicates no padding of the input. The kernel/filter must completely cover a valid pixel.
+ `padding_mode='zeros'` Indicates how to pad (ignored here since padding=0). `zeros` pad with zeros.


### First convolutional layer:

Note that a "2D convolution" goes through the channel dimension. So the kernel/filter is actually 3 x 3 x number of channels (in this case 3 x 3 x 3). One output channel/layer is produced for each filter/kernel. If there were 123 channels/layers in the input tensor, then the kernel would be 3 x 3 x 123. Again, only 1 output channel/layer per kernel/filter.

*n.b. Moving through the channels is not the same as 3D convolution (even though the kernel has 3 dimensions). A true "3D convolution" has 4 dimensions in the filter (H x W x D x C)*

![build_layer1](build_layer_1/convolution_layer1.gif)

### Second convolutional layer (note the kernel/filter is different):

![build_layer2](build_layer_2/convolution_build_layer2.gif)

## What if there are more than 3 channels?

The "2D convolution" goes through the channel dimension. So the kernel/filter in the example below if 3 x 3 x 4. It still outputs only one channel/layer per filter/kernel.
![conv_more_input_channels](build_layer_more_channels/convolution_4layers_2outs.gif)
