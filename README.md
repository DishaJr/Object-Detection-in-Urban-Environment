# **Object Detection in an Urban Environment 2.0**
## **Task :**
* Test at least two pretrained models (other than EfficientNet)
* Choosing the best model for deployment
## **Pre-trained models tested :**
* **EfficientNet-D1**
* **SSD MobileNet V1 FPN**
* **SSD ResNet50 V1 FPN coco17 tpu-8**

## **Running training process on Google Colab :**
**AWS** provides smoothness and speed in every process included in machine learning and deep learning through many of its services. As a result it was Udacity provided such service to its students to complete the project professionally.

Unfortunately working on **AWS** for the first time has lead to surpassing the budget limit provided. However, I was able to successfully train and test the default applied pre-trained model, EfficientNet D1. Inorder to achieve success in the following tasks, shifting the training procedure to be on **Google Colab** was a necessity.

**Tensorflow Object detection API** is downloaded into **Google Colab's Virtual Machine**. A link is established between **Google Colab** and **Google Drive** where the dataset files ( **training** and **validation** ) are stored as well as a folder containing the data to be used for testing.

## **Overview of the training process :**
Prior to proceeding with the training process, the ***"Project"*** folder is transfered to the ***Google Drive*** along with the ***"Object Detection in an Urban Environment 2.ipynb"*** notebook.

Going through **steps 1** to **5**, the required libraries are imported, a link is established between **Google Colab** and **Google Drive**, and te pre-trained model is intsalled.

The pre-trained model's pipeline configuration file is adjusted. Due to limitations in the resources provided the **training steps** had to be **decreased** from 300,000 steps to 6,000 and the **batch size** from 64 to 8.

![Batch size](InkedScreenshot_5.jpg)

**Tenserflow's TensorBoard** is started at **step 7** to monitor the training, validation, and testing process. At **step 8** the training process starts followed by the validation process. Once the step runs successfully the model is exported into the Project Folder. **Step 9** uses the frames provided for testing and the saved model to start the process of testing. The resulting detections are placed on the frames and exported together forming a video.

## **Comparing final results :**
|                        | EfficientNet                        |  SSD MobileNet | SSD ResNet50  |
|:-:                     |:-:                                  |:-:             |---            |
| Batch size             |        4                            |        8       |         8     |
| Number of training steps|       5000                          |    6000       |     6000     |
| Detection sample result|![Batch size](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/25-eff.png)  ![Batch size](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/25-eff.png)|![Batch size](25.png)  ![Batch size](88.png)|![Batch size](25-res.png)  ![Batch size](88-res.png) |
| Video sample           | ![video](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/ezgif.com-video-to-gif.gif)   |![video](gif-1.gif)                                 |   ![video](gif-2.gif)            |
| TensorBoard result     |         ![tensor](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/Screenshot_3.png)    |![tensor](Screenshot_4.png)       |       ![tensor](Screenshot_1.png)        |


----------------------------------------------------------

## Accuracy (mAP) values of the models tested :

* EfficientNet-D1 :

![eval_5](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_5.png)
![eval_6](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_6.png)

* SSD MobileNet V1 FPN :

![eval_1](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_1.png)
![eval_2](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_2.png)

* SSD ResNet50 V1 FPN coco17 tpu-8 :

![eval_3](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_3.png)
![eval_4](https://github.com/DishaJr/Object-Detection-in-Urban-Environment/blob/main/eval_4.png)


|        Network         |             Loss (total)            |  mAP(IOU = 0.50)  |
|:-:                     |:-:                                  |:-:                |
| EfficientNet           |           0.444299                  |        0.140458   |
| SSD MobileNet          |           1.229567                  |        0.342583   |
| SSD ResNet50           |           0.805846                  |        0.270022   |

----------------------------------------------------------

## Loss vs steps :

By observing the result of the three models, Resnet50 was able to reach low loss values sooner than both the EfficientNet and MobileNet models. MobileNet took more steps to minimize the loss compared with EfficientNet.

Rank:

1) Resnet50
2) EfficientNet
3) MobileNet


## Detection :
The models are trained to detect three classes:

* Vehicles
* Pedestrians
* Cyclists

All three models were able to detect ***vehicles*** in the provided frames for testing. Further observation showed that ***MobileNet*** was able to detect ***vehicles*** but with extra noiseness. This was not the case with ***EfficientNet*** and ***ResNet50*** models.

***Resnet50*** and ***MobileNet*** models detected ***pedestrians*** most of the time. ***MobileNet*** was having difficulties detecting ***pedestrians*** in some cases that seemed **critical**. ***EfficientNet***, on the other hand, detected pedestrians all along the testing phase with almost no noise.

All three models were not able to detect the ***cyclists***. This can be due to low number of steps in training and validation.

Rank:

1) EfficientNet
2) ResNet50
3) MobileNet

By analyzing the results from TensorBoard after training the model, the total loss amd mAP of each model, and observing the detection results on the test samples, the ***EfficientNet D1*** pre-trained model can be chosen as the best model among the three tested models for deployment.
