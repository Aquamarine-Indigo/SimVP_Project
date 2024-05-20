# Project of SimVP (Simple Yet Better Video Prediction)

## Interpretation of Roles of Each Python File

### modules.py

Mainly basic CNN modules in the SimVP architecture, including: 

* basic Convolution 2d
* Convolution Shortcut
* Group Convolution
* Inception

Calling structure as follows:

* ConvSC
  * using basicConv2d: enforcing that transposition is only possible when the stride is greater than 1, implying adjustments based on the stride for either downsampling or upsampling purposes.
* Encoder
  * ConvSC
* Translator
  * Multiple Inception modules
* Decoder
  * ConvSC

### Editing Parameter Settings

Function ```create_parser``` in main.py:

* $N_s$: Number of (un)ConvNormReLU blocks in 'Encoder' and 'Decoder'.
* $N_t$: Number of Inception modules in 'Translation'.

Modify net settings (i.e. number of channels, epochs, etc.) by giving different parsers when running in command line.

## Project Details

### Changing Number of Output Channels in the Encoder

The notation $(T, C, H, W)$ in the paper of SimVP is the ```in_shape``` parameter in the SimVP code, defined in main.py by parsers, and used in exp.py for SimVP module. $T$ represents the number of images, $C$ represents channel number of colours ($C = 1$ for moving MNIST with no colour but black and white), $H$ and $W$ represents height and width of the image. In the code class ```Encoder```, ```C_in``` and ```C_out``` represents the input and output number of channels respectively. In class ```SimVP```, ```C_in``` and ```C_out``` is assigned as ```C``` and ```hid_S```. While changing ```C_out``` in ```Encoder``` by changing ```hid_S```, ```C_hid``` in ```Decoder``` will also be changed.
