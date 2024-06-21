# Supplementary Material for IEEE MMSP 2024
Supplementary material for IEEE MMSP 2024
**A Sharpness Based Loss Function for Removing Out-of-Focus Blur**<br />
Authors:<samp>{aurangau, ramsookd, anil.kokaram}@tcd.ie</samp>

## Abstract
The advances in the field of image deblurring can
be attributed to the adoption of $l_p$, ($p$ = 1,2) as loss functions in
Deep Neural Network (DNN) based architectures. These losses,
albeit simple, do not capture the perceptual quality markers of
an image, such as sharpness. In this work, we propose a novel
method of utilizing a no-reference sharpness metric $Q$ introduced
by Zhu and Milanfar for removing out-of-focus blur. We also
introduce a dataset comprising of real-world out-of-focus images
for assessing and benchmarking restoration models. Our method
shows a 7.5% increase in the perceptual quality as compared to
a standard model trained on the $l_p$ norm as a loss

## Network Architecture
![Network Architecture](Network_Architecture/UNet_MMSP.png)
| --- |
| Network Architecture |

## Dataset
Our dataset consists of 305 5K (5796 x 3870) images. Each image has three blurry counterparts labelled as low blur, medium blur and high blur.
As the dataset is approximately 240 GB of raw images (.cr format), interested parties are encouraged to contact the first author mentioned above. We are in the process of hosting the dataset on a dedicated server.
Example crops of images from the dataset are given below:

| ![Image 1](Dataset_Examples/soda2_original_crop.png) | ![Image 2](Dataset_Examples/soda2_lbC_crop.png) | ![Image 1](Dataset_Examples/soda2_mbC_crop.png)  | ![Image 2](Dataset_Examples/soda2_hbC_crop.png) |
| --- | --- | --- | --- |
| Original Image | Low Blur Image | Medium Blur | High Blur |


| ![Image 1](Dataset_Examples/keyboard1_original_crop.png) | ![Image 2](Dataset_Examples/keyboard1_lbc_crop.png) | ![Image 1](Dataset_Examples/keyboard1_mbc_crop.png) | ![Image 2](Dataset_Examples/keyboard1_hbc_crop.png) |
| --- | --- | --- | --- |
| Original Image | Low Blur Image | Medium Blur Image | High Blur Image |

| ![Image 1](Dataset_Examples/peppermintTea3_original_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_lbC_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_mbC_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_hbC_crop.png) |
| --- | --- | --- | --- |





## Results
## Synthetically Blurred Dataset

### Average Blur Images

### Blurry and Noisy Images

## Real-World Out-of-Focus Dataset

## References

## Code
