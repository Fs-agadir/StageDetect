# StageDetect: An image-based tool for automatic water stage detection

This program detects water stage using image sequences. It includes camera orientation, template 
matching for GCP detection, master retrieval from image sequence, image co-registration, water line 
detection, and transforming 2D points into 3D coordinates.

## Additionally needed Python libraries:
- openCV version 2.4.13
- scikit-image
- scipy
- statsmodels
- seaborn
- shapely
- scikit-learn
- Tkinter

## Short Guideline:

1. Retrieve master image of each image sequence for further analysis: rider “get GCP image 
coordinates”  button “Img Master List”
- Folder with images is folder “img_raw” in tutorial dataset
- save all masters in a new folder

<img hight="300" width="700" alt="GIF" align="center" src="https://github.com/fs-agadir/stagedetect/blob/main/cap1.png">

2. Retrieve GCP image points for each master image of all sequences: rider “get GCP image 
coordinates”  „Template Matching“
- for first image GCP coordinates have to be measured in image manually, e.g. using GIMP 
in tutorial dataset it is file “Template_GCP_img.txt”
- corresponding image to initial GCP image coordinates has to be given/defined  in tutorial 
dataset it is file “firstImgTemplate.jpg”
- master image folder (step 1) should be used for template matching

![alt text](https://github.com/fs-agadir/stagedetect/blob/img/cap2.png?raw=true)

3. Get approximation of water line (to define RoI): rider “2D to 3D (and again 2D)”  check “Water 
line Approx”  button “Get 3D form 2D”
- initial water line file has to be defined manually, e.g. getting xy image coordinates using 
GIMP  in tutorial dataset it is file “waterline_approx.txt”
- interior camera geometry (e.g. from calibration file has to be given to correct for image 
distortion and to orient image)  in tutorial dataset it is file “CameraCalibration.txt”
(CameraCalibration_explained.txt includes definition of parameters)
- GCP coordinates have to be given  in tutorial dataset it is file “GCP_coordinates.txt”
- Corresponding image measurements to GCP coordinates are in result folder of step 2

![alt text](https://github.com/fs-agadir/stagedetect/blob/img/cap3.png?raw=true)

4. Estimate waterline: rider “waterline image”  button “Detect waterline”
- Water line approximations from step 3 are needed or if only one RoI defined for all 
sequences (i.e. if no camera movement is expected) “Waterline approx.: single file” has to be 
checked

![alt text](https://github.com/fs-agadir/stagedetect/blob/img/cap4.png?raw=true)

5. Get 3D water stage from water line in images considering 3D reference data (e.g. scaled SfM point 
cloud): rider “2D to 3D (and again 2D)”  check “Water level Retrieval”  button “Get 3D form 
2D”
- interior camera geometry (e.g. from calibration file has to be given to correct for image 
distortion and to orient image)  in tutorial dataset it is file “CameraCalibration.txt” 
(CameraCalibration_explained.txt includes definition of parameters)
- GCP coordinates have to be given  in tutorial dataset it is file “GCP_coordinates.txt”
- Corresponding image measurements to GCP coordinates are in result folder of step 2
- 3D point cloud of observed river area has to be given  in tutorial dataset it is file 
“PointCloud_3D.txt”
- Detected water lines from step 5 are needed

![alt text](https://github.com/fs-agadir/stagedetect/blob/img/cap5.png?raw=true)


# How to cite

Eltner, A., Elias, M., Sardemann, H., Spieler, D.: Automatic image‐based water stage measurement for long‐term observations in ungauged catchments. Water Resources Research, 54(12), 10362-10371, 2021
