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

* **Accuracy**:
  - Greatest accuracy of Training set: 
  - Greatest accuracy of Validation set:
  
* **Some problem**:
  - Overfiting.
  - Accuracy of validation test is decreasing and Loss of validation test is increasing.
  - Greatest accuracy: 

#### Train Model with Fine Tuning
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_fine_tuning_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_fine_tuning_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 97%

* **Improvement from Scratch**:
  - Not Overfiting.
  - Accuracy of validation test is increasing and Loss of validation test is decreasing as I want.
  - Train faster than Scratch.
 
#### Train Model with Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 90%
  - Greatest accuracy of Validation set: 88%

* **Improvement from Scratch**:
  - Not Overfiting.
  - Accuracy of validation test is increasing and Loss of validation test is decreasing as I want.
  - Train faster than Scratch and Fine Tuning.
  
* **Some problem**:
  - Not efficient than Fine Tuning but stable converging than Fine Tuning.

#### Train Model with Initalize Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_initialize_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_initialize_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 97%

* **Improvement from Scratch**:
  - Not Overfiting.
  - Accuracy of validation test is increasing and Loss of validation test is decreasing as I want.
  
* **Some problem**:
  - Slow and unstable converging.

### Bird With Many Class - 400 class
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_show.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_figure.png?raw=true)

#### Train Model with Scratch
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_scratch_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_scratch_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 97%
  - Greatest accuracy of Validation set: 91%
  
* **Some problem**:
  - The distance between accuracy of Training set and  accucary of Validation set is large.
  - The accurcary of Validation set is not stable.
  
#### Train Model with Fine Tuning
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_fine_tuning_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_fine_tuning_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 97%

* **Improvement from Scratch**:
  - Not Overfiting.
  - Quick and stable converging than Scratch.
  - Train faster than Scratch.
  
#### Train Model with Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 4%
  - Greatest accuracy of Validation set: 6%%
  
* **Some problem**:
  - Accuracy of Training set and Validation set is very small.
  - The accuracy of Validation set is greater than the accuracy of Training set.
  - Not efficient than Scratch.
  - The accuracy of Validation set is unstable.

#### Train Model with Initalize Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_initialize_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_initialize_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 92%
  - Greatest accuracy of Validation set: 88%
  
* **Some problem**:
  - The accuracy of Training set and Validation set is smaller than Scratch.
  - The accuracy of Validation set untably converges.
  - Not efficient than Fine Tuning
