 # Uncertainty-Aware 3D Object Detection using Voxel-based Methods
 
This repository contains code for the Voxel R-CNN-based object-detection model
incorporating uncertainty-based bounding box regression measures. 

---

The [OpenPCDet](https://github.com/open-mmlab/OpenPCDet/) library is used to create the model. The model architecture
is inspired by Voxel R-CNN and uses an additional head to estimate the log-variance
of the bounding box parameters (`x, y, w, h`). 


![uncertainty1](https://user-images.githubusercontent.com/25719320/180066123-d25d0f37-4c99-451c-920a-240144c8ec56.png)

*Fig. 1 : Yellow Outlines indicate bbox measurements one standard deviation away*

---

![Uncertainty2](https://user-images.githubusercontent.com/25719320/180066325-b025dbfb-fb55-405c-8d3c-fa546f4a688f.png)
*Fig. 2: Car on the right is more occluded from the ego vehicle's perspective, and the resulting bounding box has a higher uncertainty*

---

The results of the model are summarized in the table below (bold results indicate improvements over
baseline implementation)

| Car AP_R40 | 0.70 (easy)  | 0.70 (moderate) | 0.70 (hard)        |
|------------|--------------|-----------------|--------------------|
| bbox       | **98.9521%** | 94.7311%        | **94.4563%** (+2%) |
| bev        | **95.5206%** | 90.9908%        | 88.8129%           |
| 3d         | 92.0782%     | 84.8040%        | **82.5419%**       |
| aos        | **98.92%**   | 94.58%          | **94.23%**   (+2%) |


The OpenPCDet model for Voxel R-CNN (baseline) has the following results
for comparison

| Car AP_R40 | 0.70 (easy) | 0.70 (moderate) | 0.70 (hard) |
|------------|-------------|-----------------|-------------|
| bbox       | 98.7723%    | 94.9265%        | 92.5585%    |
| bev        | 93.5534%    | 91.1812%        | 88.9215%    |
| 3d         | 92.1587%    | 85.0157%        | 82.4832%    |
| aos        | 98.74%      | 94.79%          | 92.37%      | 


We can see that the model exhibits either similar or better
performance across the KITTI dataset. The `bbox` and `aos`
categories especially show an increase of 2% in AP in KITTI Hard.


![voxel_graph](https://user-images.githubusercontent.com/25719320/180067285-ad5ba31c-6d1a-4b15-982a-6f4dc8fa8b9d.png)
*Fig. 3: Network Architecture*

