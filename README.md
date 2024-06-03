# 以生成式AI建構無人機於自然環境偵察時所需之導航資訊競賽 II － 導航資料生成競賽
Team Name : TEAM_5171  
Team Member : 張翔 (隊長)、王睦閎  
Public Score : 	0.783753 (9th/128)  
Private Score : 0.782478 (9th/128)  

[競賽連結](https://tbrain.trendmicro.com.tw/Competitions/Details/35)  
## Repository Structure
（* 符號：因檔案內容過大，需自行新增，參考 **File Description** 1、2）
```
├── *best_models_weight
│   ├── *autoencoder_epoch_230.pth
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
1. **存放 Private Leaderboard 使用之模型權重**  
   [模型權重檔下載連結](https://drive.google.com/drive/folders/1vI8NS6J3swXml3Ksrf4vWbSQ3AYMQoJ9?usp=sharing)。下載後存放於 ```best_models_weight``` 資料夾內
```
├── *best_models_weight
│   ├── *autoencoder_epoch_230.pth
│   ├── *UNet_epoch_465.pth
│   ├── *UNet_epoch_645.pth
│   ├── *UNet_epoch_680.pth
└── └── *UNet_epoch_775.pth
```
2. **存放 Public testing dataset 及 Private testing dataset**  
   ```Public_testing_dataset``` 及 ```Private_testing_dataset``` 可從[競賽官網](https://tbrain.trendmicro.com.tw/Competitions/Details/35)下載，解壓縮後修改資料夾名為 'Public_testing_dataset' 及 'Private_testing_dataset'
```
├── *Public_testing_dataset
│   └── *img
├── *Private_testing_dataset
└── └── *img
```
3. **存放拆分過後的訓練資料集**  
   將訓練資料集（共 4320 張圖像）拆分為 8:1:1，分別存放於 ```train```、```validation```、```test``` 三資料夾中的 ```imgs``` 以及 ```gts```
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
4. **存放 autoencoder-PatchGAN 及 Unet-PatchGAN 模型定義**
```
├── models
│   ├── _init_.py
│   ├── autoencoderPatchGAN.py
└── └── UnetPatchGAN.py
```
5. **進行資料擴增**  
   執行後會產生 ```Training_dataset/aug_train```，存放原圖像及擴增後的圖像於 ```imgs``` 以及 ```gts```
```
├── preprocess.ipynb
```
6. **進行模型訓練**  
   ```train_autoencoder.ipynb```（```train_Unet.ipynb```） 執行過程會產生 ```models_autoencoder```（```models_Unet```） 及 ```autoencoder_validation_output```（```Unet_validation_output```） 兩個資料夾，分別存放訓練過程模型權重及驗證生成圖像
```
├── train_autoencoder.ipynb
└── train_Unet.ipynb
```
7. **進行測試與生成 public testing dataset 及 private testing dataset 結果**  
   測試生成圖像存放於 ```test_result``` 資料夾中，public testing dataset 及 private testing dataset 生成結果存放於 ```submission``` 資料夾中
```
├── evaluation.ipynb
```

## Set Up Environment
安裝套件
```
pip install -r requirements.txt
```
