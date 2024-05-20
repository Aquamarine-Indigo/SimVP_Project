# Project of SimVP: Interpretation of Roles of Each Python File

## modules.py

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

## Editing Parameter Settings

Function ```create_parser``` in main.py:

* $N_s$: Number of (un)ConvNormReLU blocks in 'Encoder' and 'Decoder'.
* $N_t$: Number of Inception modules in 'Translation'.

Modify net settings (i.e. number of channels, epochs, etc.) by giving different parsers when running in command line.
