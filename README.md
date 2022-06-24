# MTL_Framework_1

The multi-tasking classification and segmentation network used in this work is shown in figure.

![alt text](https://github.com/Gopika-Gopan-K/MTL_Framework_1/blob/230434b59b392850bcb3a77113717a086e8f2b2f/pics/block_diagram.png)

Base network of U-net is used here. The CT slices are input to the encoder and the decoder outputs 3 channels, namely, lung mask, lesion mask and background. Sigmoid activation function is used after the final decoder layer. The rich feature representation from the bottleneck layer is passed to a 1x1 convolution layer followed by ReLu activation to reduce the channel number from 1024 to 128. The output is then flattened and passed through a fully connected layer to three output neurons corresponding to the three classes. Since the loss function is "BCEwithLogitLoss", there is no activation function after the dense layer. Due to imbalance in the regions of lungs and lesion with respect to background, Focal Tversky loss is used in segmentation. The classification part of the framework distinguishes the given CT slice as belonging to : (a) Closed Lung, (b) Open Lung - Normal and (c) Open Lung - Covid. The segmentation part outputs the lungs and lesion masks.

Ensure the CT volumes are in folder named “Data”, lung mask in folder “Lung Mask” and lesion mask in folder “Lesion Mask”. Both the lung mask and lesion mask should have same name as the corresponding CT volume and all three are in .nii format. The CT scans are extracted and lung window of -1000 to 400 is applied before the slices are normalized for further analysis.
