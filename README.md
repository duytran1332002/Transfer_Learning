# Transfer Learning tested in some case

## About Data
I used a different kind of data to test the efficiency of Transfer Learning in the training model:
- Bird with little class (30 classes): use to test the effection of Transfer Learning on the data with **small number of classes**
- Bird with many classes (400 classes): use to test the effection of Transfer Learning on the data with a l**arge number of classes**
- Chest X-ray (2 class): use to test the effection of Transfer Learning on the data **not related with imagenet**
## Detail of All Models
All models apply some techniques: **MobileNet V2 model, MobileNet V2 preprocessing, Softmax activation, Sparse Categorical Crossentropy loss, Adam optimizer**.
I use **Accuracy and Loss** to evaluate the model.
| Model | Input | Batch Size | Epochs | Augmentation | Number Layer Fine-Tuning | Last Layers | Learning Rate | Learning Rate Reduction
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
### Bird With Little Class - 30 classes
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_show.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_figure.png?raw=true)
#### Train Model with Scratch
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_scratch_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_scratch_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 90%
  - Greatest accuracy of Validation set: 88%
  
* **Some problems**:
  - The accuracy of the Validation set is still small -> I want much more than it.

#### Train Model with Fine Tuning
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_fine_tuning_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_fine_tuning_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 97%

* **Improvement from Scratch**:
  - Not Overfitting.
  - Accuracy of the validation test is increasing and the Loss of the validation test is decreasing as I want.
  - Train faster than Scratch.
* **Some problems**:
  - The accuracy of the Validation set is unstably converging.
  
#### Train Model with Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 90%
  - Greatest accuracy of Validation set: 88%

* **Improvement from Scratch**:
  - Not Overfitting.
  - Accuracy of the validation test is increasing and the Loss of the validation test is decreasing as I want.
  - Train faster than Scratch and Fine Tuning.
  
* **Some problems**:
  - It is not more efficient than Fine-Tuning but stable converging than Fine Tuning.
  - The accuracy is still the same with Scratch.

#### Train Model with Initalize Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_initialize_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_little_class_initialize_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 97%

* **Improvement from Scratch**:
  - Not Overfiting.
  - The accuracy is better than Scratch
  
* **Some problems**:
  - Slow and unstable converging.
 
**Greatest of Accuracy and Smallest of Loss**
| Types | Accuracy of Train  | Accuracy of Validation | Loss of Train | Loss of Validation | 
| ------- | :---: | :---: | :---: | :---: | 
| Sratch | 90%  | 88% | 0.3 | 0.45 |
| Fine Tuning | 99%  | 97% | 0.01 | 0.15 |
| Pretrain | 90%  | 88% | 0.3 | 0.36 |
| Initialize Pretrain | 99%  | 97% | 0.01 | 0.1 |

### Bird With Many Class - 400 classes
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_show.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_figure.png?raw=true)

#### Train Model with Scratch
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_scratch_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_scratch_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 97%
  - Greatest accuracy of Validation set: 91%
  
* **Some problems**:
  - The distance between the accuracy of the Training set and the accuracy of the Validation set is large.
  - The accuracy of the Validation set is not stable.
  
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
  
* **Some problems**:
  - Accuracy of the Training set and Validation set is very small.
  - The accuracy of the Validation set is greater than the accuracy of the Training set.
  - It is not more efficient than Scratch.
  - The accuracy of the Validation set is unstable.

#### Train Model with Initalize Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_initialize_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/bird_many_class_initialize_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 92%
  - Greatest accuracy of Validation set: 88%
  
* **Some problems**:
  - The accuracy of the Training set and Validation set is smaller than Scratch.
  - The accuracy of the Validation set unstably converges.
  - Not efficient than Fine Tuning


**Greatest of Accuracy and Smallest of Loss**
| Types | Accuracy of Train  | Accuracy of Validation | Loss of Train | Loss of Validation | 
| ------- | :---: | :---: | :---: | :---: | 
| Sratch | 97%  | 91% | 0.08 | 0.42 |
| Fine Tuning | 99%  | 97% | 0.01 | 0.23 |
| Pretrain | 4%  | 6% | 4.65 | 4.45 |
| Initialize Pretrain | 92%  | 88% | 0.24 | 0.5 |

### Chest XAray- 2 classes
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_show.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_figure.png?raw=true)

#### Train Model with Scratch
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_scratch_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_scratch_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 97%
  - Greatest accuracy of Validation set: 85%
  
* **Some problems**:
  - The accuracy of Validation set is still small.
  - The accurcary of Validation set is not stable.
  - Overfitting.
  
#### Train Model with Fine Tuning
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_fine_tuning_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_fine_tuning_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 95%

* **Improvement from Scratch**:
  - The accuracy is better than Scratch.
  - Quick converging than Scratch.
  - Train faster than Scratch.
  
* **Some problems**:
  - The accuracy of the Validation set is not stable.
  - Overfitting sometimes happens.
  
#### Train Model with Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 96%
  - Greatest accuracy of Validation set: 93%
  
* **Improvement from Scratch**:
  - The accuracy of Validation set is better than Scratch.
  - Train faster than Scratch. 
  
* **Some problems**:
  - The accuracy of the Training set is smaller than Scratch.
  - Overfitting sometimes happens.
  - The accuracy of the Validation set is unstable.

#### Train Model with Initalize Pretrain
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_initialize_pretrain_loss.png?raw=true)
![alt text](https://github.com/duytran1332002/Transfer_Learning/blob/main/images/chest_xaray_initialize_pretrain_acc.png?raw=true)

* **Accuracy**:
  - Greatest accuracy of Training set: 99%
  - Greatest accuracy of Validation set: 96%
  
* **Improvement from Scratch**:
  - The accuracy of the Validation set is better than Scratch, Fine Tuning, and Pretrain.
  
* **Some problems**:
  - The accuracy of the Validation set unstably converges.
  
**Greatest of Accuracy and Smallest of Loss**
| Types | Accuracy of Train  | Accuracy of Validation | Loss of Train | Loss of Validation | 
| ------- | :---: | :---: | :---: | :---: | 
| Sratch | 97%  | 85% | 0.07 | 0.3 |
| Fine Tuning | 99%  | 95% | 0.02 | 0.39 |
| Pretrain | 96%  | 93% | 0.09 | 0.19 |
| Initialize Pretrain | 99%  | 96% | 0.02 | 0.03 |
