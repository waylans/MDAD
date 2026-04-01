

## A Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles
This repository(MDAD) is the official PyTorch implementation of the paper "A Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles".  

---
<p align="center">
  <img src="pictures/MDAD.png" width="400"/>
  <br>
  <em>Overall architecture of the proposed Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles.</em>
</p>

<table align="center">
  <tr>
    <td align="center">
      <img src="pictures/CDFA.png" width="400"/><br>
      <em>The schematic diagram of the Contrast-Driven Feature Aggregation (CDFA) module.</em>
    </td>
    <td align="center">
      <img src="pictures/SDFM.png" width="400"/><br>
      <em>The detailed structure of the Scale-Aware Dynamic Fusion Module.</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="pictures/SEA.png" width="400"/><br>
      <em>The detailed structure of the Semantic Enhancement and Aggregation Module.</em>
    </td>
    <td align="center">
      <img src="pictures/Visualization.png" width="400"/><br>
      <em>Visualization of Gaussian modeling and Wasserstein distance calculation for bounding boxes.</em>
    </td>
  </tr>
</table>

<p align="center">
  <img src="pictures/Dataset_Visualization.png" width="400"/>
  <br>
  <em>Visualization of the six fine-grained vehicle categories in the specialized dataset.</em>
</p>

---

---

<p align="center">
  <img src="pictures/MDAD.png" width="500"/>
  <br>
  <em><b>Figure 1.</b> Overall architecture of the proposed Multi-Dimensional Adaptive Detector for Low-Altitude Fine-Grained Vehicles.</em>
</p>

<br>

<table align="center">
  <tr>
    <td align="center">
      <img src="pictures/CDFA.png" width="280"/><br>
      <em><b>(a)</b> CDFA Module</em>
    </td>
    <td align="center">
      <img src="pictures/SDFM.png" width="280"/><br>
      <em><b>(b)</b> SDFM Module</em>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="pictures/SEA.png" width="280"/><br>
      <em><b>(c)</b> SEA Module</em>
    </td>
    <td align="center">
      <img src="pictures/Visualization.png" width="280"/><br>
      <em><b>(d)</b> Gaussian Modeling & NWD</em>
    </td>
  </tr>
</table>

<p align="center">
  <em><b>Figure 2.</b> Detailed structures of core modules in the proposed method.</em>
</p>

<br>

<p align="center">
  <img src="pictures/Dataset_Visualization.png" width="500"/>
  <br>
  <em><b>Figure 3.</b> Visualization of the six fine-grained vehicle categories in the specialized dataset.</em>
</p>

---

## Dataset

To comprehensively evaluate the performance of the proposed method in complex aerial scenarios, we utilize a specialized aerial vehicle dataset comprising 2,698 high-resolution images captured by UAVs from top-down perspectives. The dataset covers diverse scenes, including urban roads, highways, and parking lots, under varying lighting conditions. It focuses on six key vehicle categories (articulated-bus, car, small-bus, bus, freight, and truck), with filtering applied to emphasize fine-grained classification challenges. Representative visual samples of these categories are illustrated in Figure 6. The dataset exhibits typical aerial characteristics such as extremely small object sizes, high density, and significant fine-grained visual confusion. Following a standard protocol, the dataset is randomly divided into training, validation, and testing sets with a ratio of 7:1:2.



## MDAD



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



