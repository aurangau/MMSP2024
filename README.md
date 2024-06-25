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

| ![Image 1](Dataset_Examples/keyboard1_original_crop.png) | ![Image 2](Dataset_Examples/keyboard1_lbc_crop.png) | ![Image 1](Dataset_Examples/keyboard1_mbc_crop.png) | ![Image 2](Dataset_Examples/keyboard1_hbc_crop.png) |
| --- | --- | --- | --- |

| ![Image 1](Dataset_Examples/peppermintTea3_original_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_lbC_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_mbC_crop.png) | ![Image 1](Dataset_Examples/peppermintTea3_hbC_crop.png) |
| --- | --- | --- | --- |
| Original Image | Low Blur Image | Medium Blur Image | High Blur Image |



## Results
We test our proposed method on synthetically degraded (blurred) imagees and real-world out-of-focus images (proposed above)
### Synthetically Blurred Dataset
For synthetically blurred datasets, we use two degradation models -  
* Blur of size 5 $\times$ 5 with 0 noise.
* Blur of size 5 $\times$ 5 with 0.3 variance noise.

We also investigate the effect of weighting coefficient $\beta$ on the sharpness of an image
### Effect of Weighting Coefficient $\beta$ on Sharpness
| $\beta$ | PSNR (dB) | SSIM | $Q$ | LPIPS
| --- | --- | --- | --- | --- |
| **0** | **35.069** | **0.944** | **0.153** | **0.127**
| 0.001 | 35.102 | 0.945 | 0.152 | 0.117
| 0.01 | 35.101 | 0.945 | 0.154 | 0.117 
| 0.05 | 34.844 | 0.945 | 0.166 | 0.122
| 0.1 | 33.641 | 0.940 | 0.183 | 0.127

### Visual Comparison of Varying $\beta$

| ![Image 1](Beta_Value_Comp/kodim01_blurry.png)| ![Image 2](Beta_Value_Comp/kodim01_b_r_onlyMAE.png) | ![Image 3](Beta_Value_Comp/kodim01_b_r_0_001.png) | 
| --- | --- | --- |
| Blurry Image | $\beta$ = 0 | $\beta$ = 0.001 |

| ![Image 4](Beta_Value_Comp/kodim01_b_r_0_01.png) | ![Image 5](Beta_Value_Comp/kodim01_b_r_0_05.png) | ![Image 6](Beta_Value_Comp/kodim01_b_r_0_1.png) |
| --- | --- | --- |
| $\beta$ = 0.01 | $\beta$ = 0.05 | $\beta$ = 0.1 |

### Average Blur Images

| ![Image 1](MMSP_Comparisons/kodim19_original.png) | ![Image 2](MMSP_Comparisons/kodim19_blurry.png) | ![Image 3](MMSP_Comparisons/kodim19_b_ddnet.png) | ![Image 4](MMSP_Comparisons/kodim19_XYD.png) |
| --- | --- | --- | --- |
| Original Image | Blurry Image | DDNet [1] | XY-Deblur [2] |

| ![Image 5](MMSP_Comparisons/kodim19_al.png) | ![Image 6](MMSP_Comparisons/kodim19_mlm.png) | ![Image 7](MMSP_Comparisons/kodim19_mrl.png) | ![Image 8](MMSP_Comparisons/kodim19_SDM.png) |
| --- | --- | --- | --- |
| aL [3] | mLM | mRL | RED-SDM [4] |

| ![Image 9](MMSP_Comparisons/kodim19_FP.png) | ![Image 10](MMSP_Comparisons/kodim19_b_Wiener.png) | ![Image 11](MMSP_Comparisons/kodim19_b_r_onlyMAE.png) | ![Image 12](MMSP_Comparisons/kodim19_b_r_QSharp.png) |
| --- | --- | --- | --- |
| RED-FP | Wiener Filter | Ours (w/o. FT) | Ours (w. FT) |

### Blurry and Noisy Images

| ![Image 1](MMSP_Noisy_Blurry/kodim01.png)| ![Image 2](MMSP_Noisy_Blurry/kodim01_b.png) | ![Image 3](MMSP_Noisy_Blurry/kodim01_b_r.png) | 
| --- | --- | --- |
| ![Image 4](MMSP_Noisy_Blurry/kodim03.png)| ![Image 5](MMSP_Noisy_Blurry/kodim03_b.png) | ![Image 6](MMSP_Noisy_Blurry/kodim03_b_r.png) |
| --- | --- | --- |

## Real-World Out-of-Focus Dataset

## Code
The Tensorflow Implementation of our model can be found in this repository.

## References
