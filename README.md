# realsense_python_ergeb
showcase updates

## Inhalt
* [MobileNetSSD](#trainierte-MobileNetSSD-+-Realsense-D400)
* [PoitNet Preparation](#Camera-depth-colormap-+-pointcloud-of-the-depth-colormap)
* [PoitNet Classification](#PointNet-Classification)
* [VoteNet Inference (SUN RGBD + eigine PointCloud)](#VoteNet-Inference-(SUN-RGBD-+-eigine-PointCloud))
* [Update 02.06.2022](#Update-02.06.2022)
* [Labeling-Datenaufbereitung](#Labeling-Datenaufbereitung)



## trainierte MobileNetSSD + Realsense D400
* Ergebnisse von der trainierte MobileNetSSD mit der Tiefe separat gerechnet von den Kamera
* Tiefdaten und Klassifizierung sind in einem OpenCV Label combiniert

     ![Pointcloud](realsense-detection.gif)     
     ![Pointcloud](person_mit_label.PNG) 


## Camera depth colormap + pointcloud der depth colormap
* Kamera Tiefenkarte

     ![Depth_colormap](depth_colormap.PNG)


## PointNet Classification

   ![rs_pntoclass](rs_pntoclass.jpg)

## VoteNet Inference (SUN RGBD + eigine PointCloud)
* SUN RGB-D PC


   ![votenet_sunrgbd](votenet_sunrgbd.png)
   
* eigine PC


   ![votenet_realsense_pc](votenet_realsense_pc.png)
   
* # Problem?
die Daten von die eigine PC würden manuell durch Meshlab ausgerichtet um den 3D bounding box zu entsprechen, da in der SUN RGB-D Datensatz, mussen erst rigid body transformationen als Vorbereitung für VoteNet durchgeführt werden. D. h., die Daten können auch möglicherweise in eine bestimmte Art sein müssen, bevor die Inferenz durchgeführt würde; welche in die eigine PC nicht der Fall ist.

## Update 02.06.2022

* Das Netzwerk ist jetzt für den Dummy Datensatz angepasst. Das heißt, dass man einen Datensatz mit der Interl Realsense RGBD Kamera PointClouds als daten erzeugen kann und die Annotation Tool "3d-on-3d.annotate" dafür, um die Labels zu generieren, zu nutzen, -> damit die dazugehörigen Bounding Boxes (Ground Truth).
* Der genutzte Datensatz besteht aus:
     * 15 PointClouds, i.e. 15 Szenen, indiziert von 0-7: Testing und von 7-15: Training
     * 3 Klassen: Desk, Chair und Background 
* Ein Trainings Forward Pass wurde erfolgreich durchgeführt 
* Ein Evaluierungs Forward Pass wurde auch erfolgreich durchgeführt 
* Trainierung und Evaluierung wurden in der Cloud durchgeführt und dort wurde auch die Environment und Laufzeittyp dafür bestätigt 
* ![training_eval](training_eval.png)

## Labeling-Datenaufbereitung
* Statt transformieren von "3d-on-3d.annotate" annotierte Daten, ein neues Labeling Tool wurde benutzt (LabelCloud)
* Das VoteNet Code wurde dafür angepasst bzw. ein Forward Pass bestätigt (anders als 3d-on-3d.annotate, LabelCloud bearbeitet die Daten im Kamera Koordinatenframe bzw. keine weitere geometrische bearbeitung is notwendig) 
* soweit: ca. 90 PCs wurden gemacht und 70 davon glabelt
* Trainierung mit total 150-180 PCs vorgesehen. 
* ![klt21_bs](klt21_bs.png) 
   
