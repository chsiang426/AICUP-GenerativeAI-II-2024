# 以生成式AI建構無人機於自然環境偵察時所需之導航資訊競賽 II － 導航資料生成競賽：競賽報告與程式碼 TEAM_5171
## Set Up Environment
根據合適的顯卡版本安裝 [pytorch、cudatoolkit](https://pytorch.org/)
```
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```
安裝套件
```
pip install -r requirements.txt
```

## Repository Structure
（* 符號：因檔案內容過大，需自行新增，參考 **File Description** 1、2、3）
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
1. **存放 Private Leaderboard 使用之模型權重**  
   [模型權重檔下載連結](https://drive.google.com/drive/folders/1-EiTXvRRYNAr4StBn47Q_sWFIwtV5o-c)。下載後存放於 ```best_models_weight``` 資料夾中
```
├── *best_models_weight
│   ├── *EncoderDecoder_epoch_230.pth
│   ├── *UNet_epoch_465.pth
│   ├── *UNet_epoch_645.pth
│   ├── *UNet_epoch_680.pth
└── └── *UNet_epoch_775.pth
```
2. **存放 Public testing dataset 及 Private testing dataset**  
   ```Public_testing_dataset``` 及 ```Private_testing_dataset``` 可從[競賽官網](https://tbrain.trendmicro.com.tw/Competitions/Details/35)下載，解壓縮後資料夾名修改為 'Public_testing_dataset' 及 'Private_testing_dataset'
```
├── *Public_testing_dataset
│   └── *img
├── *Private_testing_dataset
└── └── *img
```
3. **存放拆分過後的訓練資料集**  
   將訓練資料集（共 4320 張圖像）拆分為 8:1:1，分別存放於 ```train```、```validation```、```test``` 三資料夾中的 ```imgs``` 以及 ```gts```  
   我們已事先拆分，可從[拆分後訓練集下載連結](https://drive.google.com/drive/folders/1kpdUyI5xJUwnJnk_qU78NpusmoHFGszS)下載，解壓縮後存放於 ```Training_dataset``` 資料夾中
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
4. **存放 EncoderDecoder-PatchGAN 及 Unet-PatchGAN 模型定義**
```
├── models
│   ├── _init_.py
│   ├── EncoderDecoderPatchGAN.py
└── └── UnetPatchGAN.py
```
5. **進行資料擴增**  
   執行後會在 ```Training_dataset``` 產生 ```aug_train``` 資料夾，存放原圖像及擴增後的圖像
```
├── preprocess.ipynb
```
6. **進行模型訓練**  
   ```train_EncoderDecoder.ipynb```（```train_Unet.ipynb```） 執行過程會產生 ```models_EncoderDecoder```（```models_Unet```） 及 ```EncoderDecoder_validation_output```（```Unet_validation_output```） 兩個資料夾，分別存放訓練過程模型權重及驗證生成圖像
```
├── train_EncoderDecoder.ipynb
└── train_Unet.ipynb
```
7. **進行測試與生成 public testing dataset 及 private testing dataset 結果**  
   測試生成圖像存放於 ```test_result``` 資料夾中，public testing dataset 及 private testing dataset 生成結果存放於 ```submission``` 資料夾中
```
├── evaluation.ipynb
```

## Model Structure
**EncoderDecoder-PatchGAN：**  
| Generator | Discriminator |
| ----- | ----- |
| <div style="text-align: center;"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/generator_encoderdecoder.png" alt="Generator"></div> | <div style="text-align: center;"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/discriminator_pix2pix.png" alt="Discriminator"></div> |

**Unet-PatchGAN：**  
| Generator | Discriminator |
| ----- | ----- |
| <div style="text-align: center;"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/generator_pix2pix.png" alt="Generator"></div> | <div style="text-align: center;"><img src="https://github.com/chsiang426/AICUP_GenerativeAI_II_2024/blob/main/README_images/discriminator_pix2pix.png" alt="Discriminator"></div> |


