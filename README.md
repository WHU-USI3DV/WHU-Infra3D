<h1 align="center"><p>WHU-Infra3D: A Full-stack Multi-modal Dataset and Benchmark for 3D Roadside Infrastructure Inventory</p></h1>

This repository hosts the website materials and documentation for **WHU-Infra3D**.

## Introduction

WHU-Infra3D is a large-scale multi-modal benchmark for urban roadside infrastructure inventory. The dataset is designed to bridge geometric perception and fine-grained cognitive diagnosis by jointly providing panoramic images, LiDAR point clouds, 2D-3D instance association, and rich attribute/status annotations.

Key characteristics:

- Cross-city collection across **Wuhan**, **Shanghai**, and **Nanjing**.
- Large-scale coverage of **53.8 km** urban trajectories.
- **5,449** images and **175,021** 2D box annotations.
- **3,199** 3D instances and **181,351** attribute/status labels in the Core Set.
- Full-stack support for detection, matching, localization, segmentation, and attribute recognition.

## Visual Explanation (from Paper Figures)

### 1) What is infrastructure inventory?

The following figure summarizes the core objective of WHU-Infra3D: transforming raw multi-modal observations into a structured asset profile with geometry and diagnostic semantics.

<p align="center">
  <img src="media/inventory_definition.jpg" alt="Infrastructure inventory definition" style="width:78%" />
</p>

### 2) Overall dataset design

WHU-Infra3D jointly models image-space perception, point-cloud understanding, and cross-modal/cross-frame instance association.

<p align="center">
  <img src="media/Teaser.jpg" alt="WHU-Infra3D teaser" style="width:92%" />
</p>

### 3) Cross-city data acquisition

Data are collected in Wuhan, Nanjing, and Shanghai to introduce realistic domain gaps for generalization evaluation.

<p align="center">
  <img src="media/Trajectory.jpg" alt="Collection trajectories" style="width:62%" />
</p>

### 4) 2D annotation quality and diversity

Panoramic imagery is annotated with dense 2D boxes in diverse urban scenes.

<p align="center">
  <img src="media/Object_detect_annotation.jpg" alt="2D annotations" style="width:92%" />
</p>

### 5) 3D geometry and instance-level labels

The dataset provides semantic, instance, and geometric supervision in point clouds.

<p align="center">
  <img src="media/3D_annotation.jpg" alt="3D annotations" style="width:62%" />
</p>

### 6) Cross-frame tracking and association

A globally consistent ID mechanism supports object deduplication and robust multi-view integration.

<p align="center">
  <img src="media/Track_annotation.jpg" alt="Cross-frame association" style="width:62%" />
</p>

### 7) Attribute and status schema

Beyond category labels, WHU-Infra3D defines fine-grained attributes and statuses for maintenance-oriented cognition.

<p align="center">
  <img src="media/Attribute_Schema.jpg" alt="Attribute schema" style="width:62%" />
</p>

### 8) Long-tail distribution challenge

Class imbalance is explicit in both 2D and 3D annotations, motivating robust long-tail learning.

<p align="center">
  <img src="media/dataset_longtail_pies.png" alt="Long-tail distribution" style="width:55%" />
</p>

## News

- 2026-XX-XX: WHU-Infra3D website repository initialized.
- 2026-XX-XX: Dataset release information will be updated soon.

## Download

Dataset download link:

- Google Drive: **TBD**
- Baidu Netdisk: **TBD**

Data request form:

- **TBD**

## Dataset

### Categories

WHU-Infra3D contains 10 roadside infrastructure categories:

- Traffic Sign
- Street Light
- Signal Light
- Surveillance Camera
- Cylindrical Bollard
- Fire Hydrant
- Trash Bin
- Manhole
- Traffic Cone
- Spherical Bollard

### Annotation Dimensions

WHU-Infra3D provides four complementary annotation dimensions:

1. 2D detection annotations on panoramic images.
2. 3D perception annotations (semantic labels, instance masks, and 3D geometry).
3. Cross-frame and cross-modal instance association IDs.
4. Fine-grained attribute and status annotations for asset diagnosis.

### Suggested Folder Structure

```text
WHU-Infra3D/
├── images/
│   ├── wuhan/
│   ├── shanghai/
│   └── nanjing/
├── pointclouds/
│   ├── wuhan/
│   ├── shanghai/
│   └── nanjing/
├── annotations/
│   ├── det2d/
│   ├── seg3d/
│   ├── tracking/
│   └── attributes/
└── metadata/
```

## Benchmark Tasks

WHU-Infra3D defines five benchmark tasks:

1. 2D Infrastructure Detection
2. 2D Cross-view Matching
3. 3D Geo-identification
4. Point Cloud Segmentation
5. Attribute Recognition

## Citation

If you find WHU-Infra3D useful in your research, please cite:

```bibtex
@article{whuinfra3d,
  title={WHU-Infra3D: A Full-stack Multi-modal Dataset and Benchmark for 3D Roadside Infrastructure Inventory},
  author={Liu, Chong and Fu, Luxuan and Feng, Xuyu and Dong, Zhen and Yang, Bisheng},
  journal={ISPRS Journal of Photogrammetry and Remote Sensing},
  year={2026},
  note={to be updated}
}
```

## Contact

For questions, please contact the maintainers via project email (to be updated).

