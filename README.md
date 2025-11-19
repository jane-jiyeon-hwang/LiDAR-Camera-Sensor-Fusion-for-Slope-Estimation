# Multimodal LiDAR–Camera Sensor Fusion for Road Longitudinal Slope Estimation

A multimodal perception pipeline that fuses LiDAR point clouds and camera images to extract road surface points and estimate longitudinal slope. The pipeline uses geometric calibration, 3D–2D projection, semantic segmentation, and DBSCAN clustering to robustly remove roadside noise and reduce slope estimation error.


## Repository Overview
This repository contains:
- Sensor fusion and preprocessing code (projection, alignment, and filtering)
- DBSCAN-based road-surface extraction
- Slope estimation logic
- Visualization samples (camera, segmentation, LiDAR, final outputs)

---

## Methods

### **1. Multimodal Input Processing**
- Forward facing camera image
- LiDAR point cloud (XYZ + intensity)
- Semantic segmentation using pretrained vision model

### **2. Geometric Calibration & Projection**
- Apply camera intrinsic/extrinsic calibration
- Project LiDAR XYZ into 2D image coordinate system
- Road region is isolated through segmentation masks

### **3. Road-Surface Extraction (DBSCAN)**
- Normalize + weight features (x, y, z, intensity)
- Cluster using DBSCAN to remove roadside noise  
  (e.g., guardrails, trees, vehicles)
- Select the largest connected road-surface cluster

### **4. Longitudinal Slope Estimation**
- Extract farthest road point along driving direction
- Compute horizontal distance, vertical rise, and slope (%)
- Estimate slope improvement compared to raw fusion outputs

---

## Sample Outputs

### **Raw Inputs**
<div align="center" style="display: flex; justify-content: center; gap: 20px;">
  <div style="text-align: center; width: 30%;">
    <img src="Multimodal LiDAR-Camera Sensor Fusion Algorithm for Road Longitudinal Slope Estimation/images/364804.999997.jpg" width="100%" />
    <p><b>Original Camera Image</b></p>
  </div>
  <div style="text-align: center; width: 30%;">
    <img src="Multimodal LiDAR-Camera Sensor Fusion Algorithm for Road Longitudinal Slope Estimation/images/364804.999997_mask_rgb.png" width="100%" />
    <p><b>Semantic Segmentation Output</b></p>
  </div>
  <div style="text-align: center; width: 30%;">
    <img src="Multimodal LiDAR-Camera Sensor Fusion Algorithm for Road Longitudinal Slope Estimation/images/364804.999997_raw.png" width="100%" />
    <p><b>Raw LiDAR Point Cloud</b></p>
  </div>
</div>

---

### **Final Outputs**
<div align="center" style="display: flex; justify-content: center; gap: 20px;">
  <div style="text-align: center; width: 45%;">
    <img src="Multimodal LiDAR-Camera Sensor Fusion Algorithm for Road Longitudinal Slope Estimation/images/364804.999997_Final_4.png" width="100%" />
    <p><b>DBSCAN Road-Surface Cluster</b></p>
  </div>
  <div style="text-align: center; width: 45%;">
    <img src="Multimodal LiDAR-Camera Sensor Fusion Algorithm for Road Longitudinal Slope Estimation/images/364804.999997_Final_5.png" width="100%" />
    <p><b>Final Road-Slope Estimation</b></p>
  </div>
</div>

---

## Data Availability
The raw data used in this project is **corporate confidential** and cannot be publicly shared.  
This repository contains only analysis code and visualization samples.  
All sensitive paths and metadata have been removed for security reasons.

---

## Dependencies
- Python 3.8+
- NumPy
- OpenCV
- Open3D
- scikit-learn
- Matplotlib
