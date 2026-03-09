# KoSim-GL: Korean Simulation-based Geo-Localization Benchmark

**KoSim-GL** is a large-scale cross-view geo-localization benchmark dataset
constructed using an AirSim and ROS-based drone flight simulator.
To the best of our knowledge, KoSim-GL is the first geo-localization benchmark
targeting Korean urban environments, comprising 2,450,315 drone images and
1,704 satellite images across 284 locations in Sinseong-dong, Daejeon,
Republic of Korea.

---

## Highlights

- **First** cross-view geo-localization benchmark targeting Korean urban environments
- **5-Camera Multi-View Platform**: 1 Nadir + 4 directional Oblique views captured simultaneously
- **Multiple Altitudes**: 100m–600m (6 levels at 100m intervals)
- **Multiple Scenes**: High-rise apartments, low-rise residential areas, mountainous terrain, research institutes, educational facilities, and more
- **Contiguous Area** coverage with **Arbitrary Free-Path** drone positions
- **Multi-Scale Satellite Images** providing altitude-matched patch sets
- Compatible with **University-1652 format**

---

## Dataset Statistics

| Split | Locations | Drone Images | Satellite Images |
|-------|-----------|-------------|-----------------|
| Train | 255 | 2,188,425 | 1,530 |
| Test | 29 | 261,890 | 174 |
| **Total** | **284** | **2,450,315** | **1,704** |

---

## Comparison with Existing Benchmarks

| Dataset | Drone Images | Contiguous Area | Multiple Altitudes | Multiple Scenes | Multi-Scale Satellite | Multi-View |
|---------|-------------|----------------|-------------------|----------------|----------------------|------------|
| University-1652 | 37,854 | ✗ | ✓ | ✗ | ✗ | ✗ |
| SUES-200 | 24,210 | ✗ | ✗ | ✗ | ✗ | ✗ |
| DenseUAV | 18,198 | ✓ | ✗ | ✗ | ✗ | ✗ |
| UAV-VisLoc | 6,742 | ✓ | ✗ | ✓ | — | ✗ |
| GTA-UAV | 33,763 | ✓ | ✓ | ✓ | ✓ | ✗ |
| **KoSim-GL (Ours)** | **2,450,315** | **✓** | **✓** | **✓** | **✓** | **✓** |

---

## Data Collection Details

- **Simulator**: AirSim + ROS
- **Location**: Sinseong-dong, Doryong-dong, and Gajeong-dong, Daejeon, Republic of Korea
- **Flight Paths**: 5 distinct paths (Path 1–5), each flown at 6 altitudes
- **Satellite Imagery**: Google Maps Tile API (Zoom Level 17, ~0.96 m/pixel at latitude 36.35°N)
- **Camera Resolution**: 640×480, FOV 30°
- **Drone Speed**: 3 m/s

### Camera Configuration

| Camera | Position | Orientation |
|--------|----------|-------------|
| Center CAM | Drone body center | 90° nadir-facing (directly downward) |
| Front / Back / Left / Right CAM | 1m from center along each axis | 25° from horizontal (oblique) |

### Flight Paths

![Flight Path Overview](assets/all_path.png)

| Path | Distance | Key Locations |
|------|----------|---------------|
| Path 1 | 2.280 km | Geumseong Elementary School → Lucky Hana Apartment → Hanwha Solutions Central Research Institute → Korea Research Institute of Chemical Technology |
| Path 2 | 2.593 km | Geumseong Elementary School → Hanwoo Kimsatgat → Samyang Group R&D Center |
| Path 3 | 1.380 km | National Science Museum → TJB Daejeon Broadcasting |
| Path 4 | 1.679 km | Sinseong Crossroads → Sinseong Neighborhood Park (Mountain) → Daedeok Research Complex Sports Complex |
| Path 5 | 1.780 km | International Intellectual Property Training Institute → Daedeok High School |

---

## Baseline Performance

### Single-View

| Method | Backbone | R@1 | R@5 | R@10 | AP |
|--------|---------|-----|-----|------|----|
| FSRA | ResNet-50 | 44.08 | 88.17 | 97.94 | 29.13 |
| MFRGN | ConvNeXt-Base | 43.64 | 82.44 | 88.91 | 21.77 |
| LPN | ResNet-50 | 42.74 | 85.49 | 97.60 | 29.00 |
| MCCG | ConvNeXt-Small | 42.52 | 91.15 | 98.22 | 27.91 |
| DWDR | ResNet-50 | 41.11 | 88.18 | 97.14 | 27.71 |
| DAC | ConvNeXt-Base | 42.08 | 87.79 | 93.45 | 22.65 |
| Sample4Geo | ConvNeXt-Base | 40.56 | 89.37 | 94.16 | 19.37 |
| MuseNet | ResNet-50 | 40.68 | 86.24 | 95.27 | 26.08 |
| CVCities | DINOv2-ViT-B/14 | 37.97 | 82.62 | 90.55 | 18.65 |

### Multi-View

| Method | Backbone | R@1 | R@5 | R@10 | AP |
|--------|---------|-----|-----|------|----|
| CAMP | ConvNeXt-Base | 42.16 | 86.13 | 92.40 | 20.42 |
| FSRA | ResNet-50 | 41.78 | 88.92 | 97.79 | 27.56 |
| DWDR | ResNet-50 | 41.77 | 83.31 | 95.70 | 27.83 |
| Sample4Geo | ConvNeXt-Base | 40.42 | 81.69 | 88.18 | 18.39 |
| CVCities | DINOv2-ViT-B/14 | 39.26 | 85.44 | 93.18 | 19.62 |
| MFRGN | ConvNeXt-Base | 39.03 | 81.67 | 90.56 | 20.94 |

> The highest R@1 of 43.64% is substantially lower than performance on existing benchmarks
> such as University-1652 (60–80%), confirming that KoSim-GL presents a higher level of difficulty.

---

## Download

The dataset is available for download via Google Drive.

| Split | Drone Images | Satellite Images | Link |
|-------|-------------|-----------------|------|
| Full Dataset | 2,450,315 | 1,704 | [Google Drive](YOUR_LINK) |

> The full dataset includes both train and test splits in University-1652 format.

---

## Citation

If you use KoSim-GL in your research, please cite our paper:
```bibtex
@article{ahn2026kosimgl,
  title   = {KoSim-GL: Korean Simulation-based Geo-Localization Benchmark},
  author  = {Ahn, Heejin and Lee, Changhwan and Lee, Sangwook and
             Seo, Minseok and Wi, HyeonJoong and Jang, Insung and
             Choi, Dong-geol},
  journal = {IEEE Access},
  year    = {2026}
}
```

---

## License

This dataset is licensed under the
**Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** license.

- Free to use, modify, and redistribute for research and non-commercial purposes
- Attribution to the original authors is required
- Commercial use is not permitted

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)

---

## Contact

For any questions or issues, please open an [Issue](../../issues) in this repository.
