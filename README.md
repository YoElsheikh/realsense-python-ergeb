# realsense_python_ergeb
showcase updates

## Inhalt
* [MobileNetSSD](#trainierte-MobileNetSSD-+-Realsense-D400)
* [PoitNet Preparation](#Camera-depth-colormap-+-pointcloud-of-the-depth-colormap)
* [PoitNet Classification](#PointNet-Classification)



## trainierte MobileNetSSD + Realsense D400
* Ergebnisse von der trainierte MobileNetSSD mit der Tiefe separat gerechnet von den Kamera
* Tiefdaten und Klassifizierung sind in einem OpenCV Label combiniert

     ![Pointcloud](realsense-detection.gif)     
     ![Pointcloud](person_mit_label.PNG) 


## Camera depth colormap + pointcloud der depth colormap
* Kamera Tiefenkarte

     ![Depth_colormap](depth_colormap.PNG)


* PointCloud, die den depth_colormap entspricht
     

* ![Pointcloud](raw.png) ![Pointcloud](man_cleaned.png) ![Pointcloud](downsampled.png)

## PointNet Classification

![rs_pntoclass](rs_pntoclass.jpg)
