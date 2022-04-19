# Transfer Learning tested in some case

## About Data
I used kind of data to test the efficient of Transfer Learning in training model:
- Bird with little class (30 classes): use to test the effection of Transfer Learning on the data with **small number of class**
- Bird with many class (400 classes): use to test the effection of Transfer Learning on the data with l**arge number of class**
- Chest Xaray (2 class): use to test the effection of Transfer Learning on the data **not related with imagenet**
## All I used to apply to train model
All model apply some techniques: **MobileNet V2 model, MobileNet V2 preprocessing, Softmax activation, Sparse Categorical Crossentropy loss, Adam optimizer**
| Model | Input | Batch Size | Epochs | Augmentation | Number Layer Fine Tuning | Last Layers | Learning Rate | Learning Rate Reduction
| -------------------------------------------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Bird with little class train with scratch** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | Yes |
| **Bird with little class train with fine tuning** | 224x224x3 | 32 | 70 | Yes | 140 | GlobalMaxPooling2D | 1e - 3 | Yes |
| **Bird with little class train with pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D + Dense(units = 1024) | 1e - 3 | Yes |
| **Bird with little class train with initialize pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | Yes |
| **Bird with many class train with scratch** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | No |
| **Bird with many class train with fine tuning** | 224x224x3 | 32 | 70 | Yes | 140 | GlobalMaxPooling2D | 1e - 3 | No |
| **Bird with many class train with pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D + Dense(units = 1024) | 1e - 3 | No |
| **Bird with many class train with initalize pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | No |
| **Chest Xaray train with scratch** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | No |
| **Chest Xaray class train with fine tuning** | 224x224x3 | 32 | 70 | Yes | 140 | GlobalMaxPooling2D + Dense(units = 1024)| 1e - 3 | No |
| **Chest Xaray class train with pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | No |
| **Chest Xaray class train with initialize pretrain** | 224x224x3 | 32 | 70 | Yes | 0 | GlobalMaxPooling2D | 1e - 3 | No |

## Visual Data and Training Model
### Bird With Little Class - 30 class
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_show.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_figure.png?raw=true)
#### Train Model with Scratch
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_scratch_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_scratch_acc.png?raw=true)
* **Some problem**:
  - Overfiting.
  - Accuracy of validation test is decreasing and Loss of validation test is increasing.









