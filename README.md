

## A Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles
This repository(MADA) is the official PyTorch implementation of the paper "A Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles".  

---
### Overall architecture of the proposed Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles.

<img src="pictures/MADA.png" alt="MADA" width="500" height="300"/>




### The schematic diagram of the Contrast-Driven Feature Aggregation (CDFA) module.

<img src="pictures/CDFA.png" alt="MADA" width="600" height="400"/>


### The detailed structure of the Scale-Aware Dynamic Fusion Module (SDFM).
<img src="pictures/SDFM.png" alt="MADA" width="600" height="400"/>

---
## Dataset

To comprehensively evaluate the performance of the proposed method in complex aerial scenarios, we utilize a specialized aerial vehicle dataset comprising 2,698 high-resolution images captured by UAVs from top-down perspectives. The dataset covers diverse scenes, including urban roads, highways, and parking lots, under varying lighting conditions. It focuses on six key vehicle categories (articulated-bus, car, small-bus, bus, freight, and truck), with filtering applied to emphasize fine-grained classification challenges. Representative visual samples of these categories are illustrated in Figure 6. The dataset exhibits typical aerial characteristics such as extremely small object sizes, high density, and significant fine-grained visual confusion. Following a standard protocol, the dataset is randomly divided into training, validation, and testing sets with a ratio of 7:1:2.



## MADA



#### Task1: Performance Comparison of Different Feature Enhancement Strategies on Backbone.

<table>
    <tr>
    <td><img src="PaperFigs\Fig7.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>
  

#### Task2: Ablation Study on High-Level and Low-Level Feature Fusion Mechanisms.

<table>
    <tr>
    <td><img src="PaperFigs\Fig8.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>
  

#### Task3: Impact of Different Detection Head Architectures on Detection Performance.

<table>
    <tr>
    <td><img src="PaperFigs\Fig9.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>
  

#### Task4: Comparative Analysis of Different Bounding Box Regression Loss Functions.

<table>
    <tr>
    <td><img src="PaperFigs\Fig9.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>

#### Task5: Robustness Evaluation Under Varying Model Scales and Input Resolution.
<table>
    <tr>
    <td><img src="PaperFigs\Fig9.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>


#### Task6: Comparison with Aerial-Specific SOTA Methods on Aerial Vehicle Dataset.

<table>
    <tr>
    <td><img src="PaperFigs\Fig9.png" width = "100%" alt="Single-Modality semantic segmentation"/></td>
    </tr>
</table>




### Training

```
python ./ultralytics/train.py
```
### Evaluation

```
python ./ultralytics/val.py
```
### Prediction

```
python ./ultralytics/predict.py
```


## Description of MSCL-SwinUNet

If you have any question, please discuss with me by sending email to wq@cap.edu.cn.


# References
Many thanks to their excellent works


* **YOLOv11** – [Code](https://github.com/ultralytics/ultralytics)



