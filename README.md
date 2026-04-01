

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

---


## Dataset

To comprehensively evaluate the performance of the proposed method in complex aerial scenarios, we utilize a specialized aerial vehicle dataset comprising 2,698 high-resolution images captured by UAVs from top-down perspectives. The dataset covers diverse scenes, including urban roads, highways, and parking lots, under varying lighting conditions. It focuses on six key vehicle categories (articulated-bus, car, small-bus, bus, freight, and truck), with filtering applied to emphasize fine-grained classification challenges. Representative visual samples of these categories are illustrated in Figure 6. The dataset exhibits typical aerial characteristics such as extremely small object sizes, high density, and significant fine-grained visual confusion. Following a standard protocol, the dataset is randomly divided into training, validation, and testing sets with a ratio of 7:1:2.






##### Task1: Performance Comparison of Different Feature Enhancement Strategies on Backbone.

| Backbone (Improvement 1)                   | mAP@50 ↑ | mAP@50:95 ↑ |
|-------------------------------------------|----------|-------------|
| YOLOv11 (Baseline)                        | 0.828    | 0.602       |
| + Adaptive Fine-Grained Channel Attention | 0.830    | 0.611       |
| + Channel Prior Convolutional Attention   | 0.838    | 0.608       |
| + MultiPath Coordinate Attention          | 0.830    | 0.603       |
| + SimAM                                   | 0.830    | 0.605       |
| + TripletAttention                        | 0.832    | 0.604       |
| + BiLevelRoutingAttention                 | 0.825    | 0.605       |
| + Vision Transformer w/ Deformable Attn   | 0.838    | 0.610       |
| + Contrast Driven Feature Aggregation     | **0.840**| **0.616**   |


#### Task2: Ablation Study on High-Level and Low-Level Feature Fusion Mechanisms.

| High-Level and Low-Level FeatureFusion (Improvement 2)      | mAP@50 ↑ | mAP@50:95 ↑ |
|--------------------------|----------|-------------|
| YOLO + CDFA (Baseline)   | 0.840    | 0.616       |
| + CGAFusion              | 0.841    | 0.614       |
| **+ SDFM**        | **0.843**| **0.631**   |
  

#### Task3: Impact of Different Detection Head Architectures on Detection Performance.

| Detection Head (Improvement 3)          | mAP@50 ↑ | mAP@50:95 ↑ |
|--------------------------------|----------|-------------|
| YOLO + CDFA + SDFM (Baseline)  | 0.843    | 0.631       |
| + Detect-MultiSEAM             | 0.826    | 0.596       |
| + Detect-LADH                  | 0.824    | 0.594       |
| + Detect-RSCD                  | 0.780    | 0.532       |
| + Detect-LSCD                  | 0.843    | 0.621       |
| **+ Detect-SEAM**       | **0.848**| **0.635**   |
  

#### Task4: Comparative Analysis of Different Bounding Box Regression Loss Functions.

| Loss Function(Improvement 4)     | mAP@50 ↑ | mAP@50:95 ↑ |
|--------------------------------------|----------|-------------|
| YOLO + CDFA + SDFM + SEAM (Baseline) | 0.848    | 0.635       |
| + GIoU                               | 0.844    | 0.616       |
| + DIoU                               | 0.837    | 0.611       |
| + EIoU                               | 0.840    | 0.604       |
| + SIoU                               | 0.839    | 0.603       |
| + ShapeIoU                           | 0.845    | 0.616       |
| **+ NWD**                     | **0.857**| **0.642**   |
#### Task5: Robustness Evaluation Under Varying Model Scales and Input Resolution.

| Model Size | Image Size | mAP@50 ↑           | mAP@50:95 ↑        |
|------|-----------|--------------------|--------------------|
|    | 640       | 0.828 / 0.857 (+2.9%) | 0.602 / 0.642 (+4.0%) |
| n    | 960       | 0.882 / 0.906 (+2.4%) | 0.653 / 0.673 (+2.0%) |
|     | 1280      | 0.900 / 0.917 (+1.7%) | 0.684 / 0.695 (+1.1%) |
|     | 640       | 0.876 / 0.901 (+2.5%) | 0.651 / 0.669 (+1.8%) |
| s    | 960       | 0.920 / 0.932 (+1.2%) | 0.708 / 0.727 (+1.9%) |
|     | 1280      | 0.924 / 0.935 (+1.1%) | 0.727 / 0.741 (+1.4%) |
|     | 640       | 0.890 / 0.903 (+1.3%) | 0.682 / 0.696 (+1.4%) |
| m    | 960       | 0.924 / 0.937 (+1.3%) | 0.732 / 0.744 (+1.2%) |
|     | 1280      | 0.926 / 0.940 (+1.4%) | 0.743 / 0.757 (+1.4%) |


#### Task6: Comparison with Aerial-Specific SOTA Methods on Aerial Vehicle Dataset.

| Method            | mAP@50 ↑ | mAP@50:95 ↑ |
|----------------------|----------|-------------|
| YOLOv11-n (Baseline) | 0.828    | 0.602       |
| UAV-YOLO             | 0.835    | 0.610       |
| Drone-YOLO           | 0.840    | 0.615       |
| TPH-YOLOv5-Air       | 0.846    | 0.625       |
| EBR-YOLO             | 0.843    | 0.620       |
| YOLO-DD              | 0.850    | 0.630       |
| **Ours**             | **0.857**| **0.642**   |

<table align="center">
  <tr>
    <td valign="top" align="center">

<table>
  <tr>
    <th>Backbone (Improvement 1)</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>YOLOv11 (Baseline)</td><td>0.828</td><td>0.602</td></tr>
  <tr><td>+ Adaptive Fine-Grained Channel Attention</td><td>0.830</td><td>0.611</td></tr>
  <tr><td>+ Channel Prior Convolutional Attention</td><td>0.838</td><td>0.608</td></tr>
  <tr><td>+ MultiPath Coordinate Attention</td><td>0.830</td><td>0.603</td></tr>
  <tr><td>+ SimAM</td><td>0.830</td><td>0.605</td></tr>
  <tr><td>+ TripletAttention</td><td>0.832</td><td>0.604</td></tr>
  <tr><td>+ BiLevelRoutingAttention</td><td>0.825</td><td>0.605</td></tr>
  <tr><td>+ Vision Transformer w/ Deformable Attn</td><td>0.838</td><td>0.610</td></tr>
  <tr><td><b>+ Contrast Driven Feature Aggregation</b></td><td><b>0.840</b></td><td><b>0.616</b></td></tr>
</table>

<p align="center"><em>Task1: Performance Comparison of Different Feature Enhancement Strategies on Backbone.</em></p>

    </td>
    <td valign="top" align="center">

<table>
  <tr>
    <th>High-Level and Low-Level Feature Fusion (Improvement 2)</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>YOLO + CDFA (Baseline)</td><td>0.840</td><td>0.616</td></tr>
  <tr><td>+ CGAFusion</td><td>0.841</td><td>0.614</td></tr>
  <tr><td><b>+ SDFM</b></td><td><b>0.843</b></td><td><b>0.631</b></td></tr>
</table>

<p align="center"><em>Task2: Ablation Study on High-Level and Low-Level Feature Fusion Mechanisms.</em></p>

    </td>
    <td valign="top" align="center">

<table>
  <tr>
    <th>Detection Head (Improvement 3)</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>YOLO + CDFA + SDFM (Baseline)</td><td>0.843</td><td>0.631</td></tr>
  <tr><td>+ Detect-MultiSEAM</td><td>0.826</td><td>0.596</td></tr>
  <tr><td>+ Detect-LADH</td><td>0.824</td><td>0.594</td></tr>
  <tr><td>+ Detect-RSCD</td><td>0.780</td><td>0.532</td></tr>
  <tr><td>+ Detect-LSCD</td><td>0.843</td><td>0.621</td></tr>
  <tr><td><b>+ Detect-SEAM</b></td><td><b>0.848</b></td><td><b>0.635</b></td></tr>
</table>

<p align="center"><em>Task3: Impact of Different Detection Head Architectures on Detection Performance.</em></p>

    </td>
  </tr>

  <tr>
    <td valign="top" align="center">

<table>
  <tr>
    <th>Loss Function (Improvement 4)</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>YOLO + CDFA + SDFM + SEAM (Baseline)</td><td>0.848</td><td>0.635</td></tr>
  <tr><td>+ GIoU</td><td>0.844</td><td>0.616</td></tr>
  <tr><td>+ DIoU</td><td>0.837</td><td>0.611</td></tr>
  <tr><td>+ EIoU</td><td>0.840</td><td>0.604</td></tr>
  <tr><td>+ SIoU</td><td>0.839</td><td>0.603</td></tr>
  <tr><td>+ ShapeIoU</td><td>0.845</td><td>0.616</td></tr>
  <tr><td><b>+ NWD</b></td><td><b>0.857</b></td><td><b>0.642</b></td></tr>
</table>

<p align="center"><em>Task4: Comparative Analysis of Different Bounding Box Regression Loss Functions.</em></p>

    </td>
    <td valign="top" align="center">

<table>
  <tr>
    <th>Model Size</th>
    <th>Image Size</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>n</td><td>640</td><td>0.828 / 0.857 (+2.9%)</td><td>0.602 / 0.642 (+4.0%)</td></tr>
  <tr><td>n</td><td>960</td><td>0.882 / 0.906 (+2.4%)</td><td>0.653 / 0.673 (+2.0%)</td></tr>
  <tr><td>n</td><td>1280</td><td>0.900 / 0.917 (+1.7%)</td><td>0.684 / 0.695 (+1.1%)</td></tr>
  <tr><td>s</td><td>640</td><td>0.876 / 0.901 (+2.5%)</td><td>0.651 / 0.669 (+1.8%)</td></tr>
  <tr><td>s</td><td>960</td><td>0.920 / 0.932 (+1.2%)</td><td>0.708 / 0.727 (+1.9%)</td></tr>
  <tr><td>s</td><td>1280</td><td>0.924 / 0.935 (+1.1%)</td><td>0.727 / 0.741 (+1.4%)</td></tr>
  <tr><td>m</td><td>640</td><td>0.890 / 0.903 (+1.3%)</td><td>0.682 / 0.696 (+1.4%)</td></tr>
  <tr><td>m</td><td>960</td><td>0.924 / 0.937 (+1.3%)</td><td>0.732 / 0.744 (+1.2%)</td></tr>
  <tr><td>m</td><td>1280</td><td>0.926 / 0.940 (+1.4%)</td><td>0.743 / 0.757 (+1.4%)</td></tr>
</table>

<p align="center"><em>Task5: Robustness Evaluation Under Varying Model Scales and Input Resolution.</em></p>

    </td>
    <td valign="top" align="center">

<table>
  <tr>
    <th>Method</th>
    <th>mAP@50 ↑</th>
    <th>mAP@50:95 ↑</th>
  </tr>
  <tr><td>YOLOv11-n (Baseline)</td><td>0.828</td><td>0.602</td></tr>
  <tr><td>UAV-YOLO</td><td>0.835</td><td>0.610</td></tr>
  <tr><td>Drone-YOLO</td><td>0.840</td><td>0.615</td></tr>
  <tr><td>TPH-YOLOv5-Air</td><td>0.846</td><td>0.625</td></tr>
  <tr><td>EBR-YOLO</td><td>0.843</td><td>0.620</td></tr>
  <tr><td>YOLO-DD</td><td>0.850</td><td>0.630</td></tr>
  <tr><td><b>Ours</b></td><td><b>0.857</b></td><td><b>0.642</b></td></tr>
</table>

<p align="center"><em>Task6: Comparison with Aerial-Specific SOTA Methods on Aerial Vehicle Dataset.</em></p>

    </td>
  </tr>
</table>



<p align="center">
  <img src="pictures/Dataset_Visualization.png" width="400"/>
  <br>
  <em>Visualization of the six fine-grained vehicle categories in the specialized dataset.</em>
</p>


### Visualization of the six fine-grained vehicle categories in the specialized dataset.
<p align="center">
  <img src="pictures/Dataset_Visualization.png" width="400"/>
  <br>
</p>
---
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



