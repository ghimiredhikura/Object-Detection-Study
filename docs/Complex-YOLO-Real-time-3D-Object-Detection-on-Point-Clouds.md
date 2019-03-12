## [Complex-YOLO: Real-time 3D Object Detection on Point Clouds](https://arxiv.org/pdf/1803.06199.pdf)  
Authors: Martin Simon, Stefan Milz, Karl Amende, Horst-Michael Gross  
[PDF](https://arxiv.org/pdf/1803.06199.pdf), [code-pytorch](https://github.com/AI-liu/Complex-YOLO)
****
#### Summary

* The authors present a single-stage LIDAR-only model for 3D object localization of vehicles (BEV - bird's eye view).   
* The point cloud data is converted into BEV map, which they also called [BEV RGB map - R: density channel, G: height channel, B: intensity channel](https://github.com/AI-liu/Complex-YOLO/blob/master/utils.py#L31).
  The BEV covers the front 80m x 40m in point cloud. The size of the covering area, i.e. grid map, is defined with `n = 2014` and `m = 512`.
  Therefore grid resolution is about `g = 8cm` In summary covering area is: `PΩ = {P = [x, y, z]T|x ∈ [0, 40m], y ∈ [−40m, 40m], z ∈ [−2m, 1.25m]}` 
* Now, YOLO-v2 is applied on BEV map which will predict object geometry(6: x, y, w, l, im, re), conf(1) and class probabilities(7).
The object orientation information is also included along with location information, therefore they named it as complex-yolo. 
If 5 anchors are used the output map will be W x H x C = 32 x 16 x 70.  
* 