# Generative-AI Navigation Information Competition for UAV Reconnaissance in Natural Environments II：Navigation Data Generation—TEAM_5171

## Overview
This is AI CUP 2024 spring competition ([website](https://tbrain.trendmicro.com.tw/Competitions/Details/35)). The competition focuses on using generative AI to transform images of roads and rivers captured by drones into navigational maps, enabling autonomous navigation. It also highlights the scarcity of competitions that combine these two fields, aiming to deepen participants' understanding and capabilities in applying these technologies to real-world scenarios.  

We ([Chang Hsiang](https://github.com/chsiang426) and [Wang Mu-Hong](https://github.com/allenw415)) received The Honorable Mention Award（Top 5%）in this competition.
## Set Up Environment
Install [pytorch、cudatoolkit](https://pytorch.org/) according to the appropriate GPU version.
```
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```
Install the required packages.
```
pip install -r requirements.txt
```

## Repository Structure
(The **\*** Symbol: Due to the large file content, you'll need to add them manually, referring to **File Description** 1., 2., 3.)  
```
├── *best_models_weight
│   ├── *EncoderDecoder_epoch_230.pth
│   ├── *UNet_epoch_465.pth
│   ├── *UNet_epoch_645.pth
│   ├── *UNet_epoch_680.pth
│   └── *UNet_epoch_775.pth
│
├── *Public_testing_dataset
│   └── *img
├── *Private_testing_dataset
│   └── *img
│
├── *Training_dataset
│   ├── *test
│   │   ├── *gts
│   │   └── *imgs
│   ├── *train
│   │   ├── *gts
│   │   └── *imgs
│   └── *validation
│       ├── *gts
│       └── *imgs
│
├── models
│   ├── _init_.py
│   ├── EncoderDecoderPatchGAN.py
│   └── UnetPatchGAN.py
│
├── .gitignore
├── README.md
├── requirements.txt
├── preprocess.ipynb
├── train_EncoderDecoder.ipynb
├── train_Unet.ipynb
├── evaluation.ipynb
├── report.pdf
└── README_images
```

## File Description
1. **To store the model weights used for the Private Leaderboard**  
   [Model weights download link](https://drive.google.com/drive/folders/1-EiTXvRRYNAr4StBn47Q_sWFIwtV5o-c) After downloading, store them in the best_models_weight folder.
```
├── *best_models_weight
│   ├── *EncoderDecoder_epoch_230.pth
│   ├── *UNet_epoch_465.pth
│   ├── *UNet_epoch_645.pth
│   ├── *UNet_epoch_680.pth
└── └── *UNet_epoch_775.pth
```
2. **To store the Public testing dataset and the Private testing dataset**  
   ```Public_testing_dataset``` and ```Private_testing_dataset``` can be downloaded from the [competition official website](https://tbrain.trendmicro.com.tw/Competitions/Details/35). After unzipping, rename the folders to 'Public_testing_dataset' and 'Private_testing_dataset'.
```
├── *Public_testing_dataset
│   └── *img
├── *Private_testing_dataset
└── └── *img
```
3. **To store the split training dataset**  
   Split the training dataset (a total of 4,320 images) into an 8:1:1 ratio and store them in the ```train```, ```validation```, and ```test``` folders under the ```imgs``` and ```gts``` subfolders.
   We have already split the dataset, and you can download it from [Split Training Dataset Download Link](https://drive.google.com/drive/folders/1kpdUyI5xJUwnJnk_qU78NpusmoHFGszS). After extracting, store it in the ```Training_dataset``` folder.
```
├── *Training_dataset
│   ├── *test
│   │   ├── *gts
│   │   └── *imgs
│   ├── *train
│   │   ├── *gts
│   │   └── *imgs
│   └── *validation
│       ├── *gts
└──     └── *imgs
```
4. **To store the definitions of the EncoderDecoder-PatchGAN and Unet-PatchGAN models**
```
├── models
│   ├── _init_.py
│   ├── EncoderDecoderPatchGAN.py
└── └── UnetPatchGAN.py
```
5. **Perform data augmentation**  
   After execution, an ```aug_train``` folder will be created in the ```Training_dataset``` folder, containing the original images and the augmented images.
```
├── preprocess.ipynb
```
6. **Model training**  
   During the execution of train_EncoderDecoder.ipynb (or train_Unet.ipynb), two folders will be created: ```models_EncoderDecoder``` (or ```models_Unet```) and ```EncoderDecoder_validation_output``` (or ```Unet_validation_output```). These folders will store the model weights from the training process and the validation-generated images, respectively.
```
├── train_EncoderDecoder.ipynb
└── train_Unet.ipynb
```
7. **Conduct testing and generate results for the public testing dataset and private testing dataset**  
   The generated test images will be stored in the ```test_result``` folder, while the results from the public testing dataset and private testing dataset will be stored in the ```submission``` folder.
```
├── evaluation.ipynb
```

## Model Structure
<table>
  <tr>
    <th colspan="2" align="center">EncoderDecoder-PatchGAN</th>
  </tr>
  <tr>
    <td align="center">Generator</td>
    <td align="center">Discriminator</td>
  </tr>
  <tr>
    <td align="center"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/generator_encoderdecoder.png" alt="Generator"></td>
    <td align="center"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/discriminator_pix2pix.png" alt="Discriminator"></td>
  </tr>
</table>

<table>
  <tr>
    <th colspan="2" align="center">Unet-PatchGAN</th>
  </tr>
  <tr>
    <td align="center">Generator</td>
    <td align="center">Discriminator</td>
  </tr>
  <tr>
    <td align="center"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/generator_pix2pix.png" alt="Generator"></td>
    <td align="center"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/discriminator_pix2pix.png" alt="Discriminator"></td>
  </tr>
</table>

## Awards

<div style="display: flex; justify-content: space-between;">
   <a href="https://www.aicup.tw/post/%E3%80%90ai-cup-2024%E3%80%91%E5%BE%97%E7%8D%8E%E5%90%8D%E5%96%AE%EF%BC%8D%E4%BB%A5%E7%94%9F%E6%88%90%E5%BC%8Fai%E5%BB%BA%E6%A7%8B%E7%84%A1%E4%BA%BA%E6%A9%9F%E6%96%BC%E8%87%AA%E7%84%B6%E7%92%B0%E5%A2%83%E5%81%B5%E5%AF%9F%E6%99%82%E6%89%80%E9%9C%80%E4%B9%8B%E5%B0%8E%E8%88%AA%E8%B3%87%E8%A8%8A%E7%AB%B6%E8%B3%BD-ii%EF%BC%8D-%E5%B0%8E%E8%88%AA%E8%B3%87%E6%96%99%E7%94%9F%E6%88%90%E7%AB%B6%E8%B3%BD">
      <img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/Awards1.png" alt="My Image" width="500px">
   </a>
</div>
