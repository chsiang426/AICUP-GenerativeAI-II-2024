# AICUP_GenerativeAI_II_2024

## Repository Structure
（* 符號：因檔案內容過大，需自行新增，參考**File Description** 1、2）
```
├── *best_models_weight
│   ├── autoencoder_epoch_230.pth
│   ├── UNet_epoch_465.pth
│   ├── UNet_epoch_645.pth
│   ├── UNet_epoch_680.pth
│   └── UNet_epoch_775.pth
│
├── *Public_testing_dataset
│   └── img
├── *Private_testing_dataset
│   └── img
│
├── Training_dataset
│   ├── test
│   │   ├── gts
│   │   └── imgs
│   ├── train
│   │   ├── gts
│   │   └── imgs
│   └── validation
│       ├── gts
│       └── imgs
│
├── models
│   ├── _init_.py
│   ├── autoencoderPatchGAN.py
│   └── UnetPatchGAN.py
│
├── .gitignore
├── README.md
├── requirements.txt
├── evaluation.ipynb
├── preprocess.ipynb
├── train_autoencoder.ipynb
└── train_Unet.ipynb
```

## File Description
*1. [模型權重檔下載連結](https://drive.google.com/drive/folders/1vI8NS6J3swXml3Ksrf4vWbSQ3AYMQoJ9?usp=sharing)。下載後存放於 ```best_models_weight``` 資料夾內
```
├── *best_models_weight
│   ├── autoencoder_epoch_230.pth
│   ├── UNet_epoch_465.pth
│   ├── UNet_epoch_645.pth
│   ├── UNet_epoch_680.pth
└── └── UNet_epoch_775.pth
```
*2. ```Public_testing_dataset``` 及 ```Private_testing_dataset``` 可從[競賽官網](https://tbrain.trendmicro.com.tw/Competitions/Details/35)下載，解壓縮後修改資料夾名為 'Public_testing_dataset' 及 'Private_testing_dataset'
```
├── *Public_testing_dataset
│   └── *img
├── *Private_testing_dataset
└── └── *img
```
3. 將訓練資料集（共 4320 張圖像）拆分為 8:1:1，分別存放於 ```train```、```validation```、```test``` 三資料夾中的 ```imgs``` 以及 ```gts```
```
├── Training_dataset
│   ├── test
│   │   ├── gts
│   │   └── imgs
│   ├── train
│   │   ├── gts
│   │   └── imgs
│   └── validation
│       ├── gts
└──     └── imgs
```
4. autoencoder-PatchGAN 模型及 Unet-PatchGAN 模型定義
```
├── models
│   ├── _init_.py
│   ├── autoencoderPatchGAN.py
└── └── UnetPatchGAN.py
```
5. 進行資料擴增，執行後會產生 ```Training_dataset/aug_train```，存放原圖像及擴增後的圖像於 ```imgs``` 以及 ```gts```
```
├── preprocess.ipynb
```
6. 進行模型訓練
```
├── train_autoencoder.ipynb
└── train_Unet.ipynb
```
7. 進行測試與上傳 public testing dataset 及 private testing dataset 生成結果
```
├── evaluation.ipynb
```

## Set Up Environment
安裝套件
```
pip install -r requirements.txt
```
