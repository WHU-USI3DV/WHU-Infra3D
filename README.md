<h1 align="center"><p>WHU-Infra3D: A Full-stack Multi-modal Dataset and Benchmark for 3D Roadside Infrastructure Inventory</p></h1>

## Introduction 🚀

WHU-Infra3D is a large-scale multi-modal benchmark for urban roadside infrastructure inventory. The dataset is designed to bridge geometric perception and fine-grained cognitive diagnosis by jointly providing panoramic images, LiDAR point clouds, 2D-3D instance association, and rich attribute/status annotations.

Key characteristics:

- Cross-city collection across **Wuhan**, **Shanghai**, and **Nanjing**.
- Large-scale coverage of **53.8 km** urban trajectories.
- **5,449** images and **175,021** 2D box annotations.
- **3,199** 3D instances and **181,351** attribute/status labels in the Core Set.
- Full-stack support for detection, matching, localization, segmentation, and attribute recognition.

<p align="center">
  <img src="media/Teaser.jpg" alt="WHU-Infra3D teaser" style="width:100%" />
</p>

## Dataset Overview & Visual Highlights 🧭

The core objective of WHU-Infra3D is to transform raw multi-modal observations into a structured roadside asset profile that possesses accurate geometry and fine-grained maintenance semantics. Rather than acting strictly as a collection of disjointed data frames, WHU-Infra3D provides a cohesive, full-stack narrative bridging 2D perception, 3D structure, and cognitive diagnosis.

### 1. The Inventory Pipeline and Architecture
At its foundation, the dataset maps physical city environments to a digital twin. We construct a complete loop: defining the infrastructure inventory task, capturing the scene with images and point clouds, and systematically translating those observations into structured asset instances.

<p align="center">
  <img src="media/inventory_definition.jpg" alt="Infrastructure inventory definition" style="width:55%" />
</p>

### 2. Large-scale Acquisition and Generalization Challenges
To ensure robust model generalization across domain gaps, data collection spanned 53.8 km of continuous trajectories across three megacities: Wuhan, Shanghai, and Nanjing. The realistic city-scale sampling brings natural class imbalance, vividly illustrated by a strict long-tail distribution in both 2D targets and 3D points.

<p align="center">
  <img src="media/Trajectory.jpg" alt="Collection trajectories" style="width:70%" />
</p>

### 3. Comprehensive Perception in 2D and 3D Spaces
Perceiving these heterogeneous assets begins with comprehensive and varied annotations. The dataset features robust dense 2D bounding boxes in overlapping panoramic views, tightly coupled with high-quality 3D point cloud labels (including semantic classes, instance clusters, and distinct 3D geometry constraints).

<p align="center">
  <img src="media/Object_detect_annotation.jpg" alt="2D annotations"style="width:100%" />
</p>

<p align="center">
  <img src="media/3D_annotation.jpg" alt="3D annotations"style="width:100%" />
</p>

### 4. Continuous Association Across Views and Frames
Beyond independent frame perception, WHU-Infra3D manages cross-view duplicate observations through globally consistent cross-frame data association, which is essential for robust deduplication and stable multi-view fusion.

<p align="center">
  <img src="media/Track_annotation.jpg" alt="Cross-frame association" style="width:52%" />
</p>

### 5. Fine-grained Attribute and Status Annotation (Key Strength)
Attribute and status annotation is a core highlight of WHU-Infra3D rather than an auxiliary label. The benchmark goes beyond category recognition to capture instance-level maintenance semantics, enabling cognitive diagnosis of infrastructure conditions.

<p align="center">
  <img src="media/Attribute_Schema.jpg" alt="Attribute schema" style="width:46%" />
</p>

## News 📰

- 2026-05-28: WHU-Infra3D dataset is now publicly available. 🎉
<!-- - 2026-XX-XX: Our WHU-Infra3D paper is published on arXiv: TBD -->

## Download 📦

Data request form 📝: [Fill out the questionnaire](https://wj.qq.com/s2/26835830/80bf/)

Please fill in the questionnaire first. The dataset download links will be provided after submission. 🔗

## Dataset 🗂️

### Categories 🏷️

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

The category distribution exhibits a clear long-tail pattern in both 2D and 3D annotations:

<p align="center">
  <img src="media/dataset_longtail_pies.png" alt="Long-tail category distribution" style="width:52%" />
</p>

### Annotation Dimensions 📐

WHU-Infra3D provides four complementary annotation dimensions:

1. 2D detection annotations on panoramic images.
2. 3D perception annotations (semantic labels, instance masks, and 3D geometry).
3. Cross-frame and cross-modal instance association IDs.
4. Fine-grained attribute and status annotations for asset diagnosis.

### Current Release Structure 🧱

```text
WHU-Infra3D-Dataset/
  Wuhan/
    BaseSet/
      PanoImages/
      coco_base.json
    CoreSet/
      PanoImages/
      image_detect_track_3dbox/
      coco_core.json
      INSPose_refined.txt
      PointCloud/
  Shanghai/
    BaseSet/
      PanoImages/
      coco_base.json
    CoreSet/
      PanoImages/
      image_detect_track_3dbox/
      coco_core.json
      INSPose_refined.txt
      PointCloud/
  Nanjing/
    BaseSet/
      PanoImages/
      coco_base.json
    CoreSet/
      PanoImages/
      image_detect_track_3dbox/
      coco_core.json
      INSPose_refined.txt
      PointCloud/
```

### Folder Contents 📁

For each city (Wuhan/Shanghai/Nanjing), the folder roles are:

1. `BaseSet/PanoImages/`
  - Stores panoramic images for the full collected trajectory of that city.
  - These images are used as the large-scale image pool.
2. `CoreSet/PanoImages/`
  - Stores the core subset of panoramic images used for benchmark construction.
  - File stems are aligned with `CoreSet/image_detect_track_3dbox/` annotations.
3. `CoreSet/image_detect_track_3dbox/`
  - Stores per-image annotation TXT files (same stem as image name).
  - Each row describes one observed infrastructure instance with 2D box + 3D box + tracking/object identity.
4. `CoreSet/PointCloud/`
  - Stores point cloud data aligned with the core subset.
  - Used for 3D perception and cross-modal tasks.
5. `BaseSet/coco_base.json`
  - COCO-format annotation file for BaseSet images.
  - Includes `images`, `annotations`, and `categories`.
6. `CoreSet/coco_core.json`
  - COCO-format annotation file for CoreSet images.
  - Includes `images`, `annotations`, `categories` (and metadata fields such as `info`, `licenses` when provided).
7. `CoreSet/INSPose_refined.txt`
  - Refined camera pose file for panoramic frames in the city trajectory.
  - Used to recover exposure position and camera orientation for geometry and cross-modal alignment.

### INSPose_refined.txt Format 🧭

Example row:

```text
00000000000000001 20210524053219323904 19939.323019 -1937.155469 -1345.304770 8.388862 30.48317300962 114.49022292385 0.185377 1.407768 -107.045143
```

Each line in `INSPose_refined.txt` contains 11 whitespace-separated columns:

1. `frame_id`: frame/image identifier (matches pano stem, e.g., `000...` or `ladybug_panoramic_...`).
2. `time_1`: time-related field from acquisition records (can be ignored in current processing).
3. `time_2`: time-related field from acquisition records (can be ignored in current processing).
4. `pos_x`: camera exposure position X in the mapped/world coordinate system.
5. `pos_y`: camera exposure position Y in the mapped/world coordinate system.
6. `pos_z`: camera exposure position Z (height).
7. `geo_lon_or_aux`: geographic longitude or auxiliary geodetic field (source-dependent).
8. `geo_lat_or_aux`: geographic latitude or auxiliary geodetic field (source-dependent).
9. `roll`: camera roll angle (degrees).
10. `pitch`: camera pitch angle (degrees).
11. `heading`: camera heading/yaw angle (degrees).

Columns used by the current processing code in this repository:

- `frame_id` (column 1)
- `pos_x, pos_y, pos_z` (columns 4-6)
- `roll, pitch, heading` (columns 9-11)

Columns 2 and 3 are time-related metadata and are ignored by the current processing pipeline.

Reference from code logic: `np.loadtxt(..., usecols=(0, 3, 4, 5, 8, 9, 10))`.

### image_detect_track_3dbox TXT Format 🧾

Example row:

```text
Traffic Sign,1200.0,980.0,1288.0,1082.0,2.1,0.5,0.2,132.4,87.3,6.8,-1.57,10452
```

Each annotation file is comma-separated. Each row has 13 columns:

1. `class_name`: semantic category name.
2. `x1`: left pixel coordinate of 2D box.
3. `y1`: top pixel coordinate of 2D box.
4. `x2`: right pixel coordinate of 2D box.
5. `y2`: bottom pixel coordinate of 2D box.
6. `h`: 3D box height.
7. `w`: 3D box width.
8. `l`: 3D box length.
9. `x`: 3D box center X in world/map coordinate system.
10. `y`: 3D box center Y in world/map coordinate system.
11. `z`: 3D box center Z in world/map coordinate system.
12. `rot_y`: yaw/orientation of the 3D box.
13. `object_id`: cross-image instance ID for the same physical infrastructure object.

### PointCloud Fields ☁️

Point cloud files include geometric coordinates and additional attributes. Key fields include:

1. `Intensity`: LiDAR return intensity for each point.
2. `Semantic`: semantic class label per point.
3. `Instance`: instance ID per point.

`Semantic` field value mapping:

| Semantic ID | Category |
|---|---|
| 1 | Traffic Sign |
| 2 | Street Light |
| 3 | Signal Light |
| 4 | Surveillance Camera |
| 5 | Cylindrical Bollard |
| 6 | Fire Hydrant |
| 7 | Trash Bin |
| 8 | Manhole |
| 9 | Traffic Cone |
| 10 | Spherical Bollard |

Together with point coordinates (`x`, `y`, `z`), these fields support semantic segmentation and instance-level 3D reasoning.

## Benchmark Tasks 🎯

WHU-Infra3D defines five benchmark tasks:

1. 2D Infrastructure Detection
2. 2D Cross-view Matching
3. 3D Geo-identification
4. Point Cloud Segmentation
5. Attribute Recognition

## Citation 📚

If you find WHU-Infra3D useful in your research, please cite:

```bibtex
To be updated
```

## Contact ✉️

For questions, please contact the maintainers via email (liuchongwhu@whu.edu.cn).

