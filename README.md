# DICOM Image Tracking and Eye Tracking System for Radiologists
We introduce a DICOM viewer that can record the status of medical images in real time and some modules for eye tracking.

<div align="center">
    <img src="/res/ovreall.png">
</div>

# DICOM Viewer

## Contributions
We modified the source code of the [ClearCanvas](https://clearcanvas.github.io/) open source project to accomplish the following functions.

- Custom image list. After the software is pre-loaded with the list, the radiologists can switch to observe the images in the list at will on the software.

- Real-time image status tracking. We captured the software's graphical interface parameters in the source code, including the software's screen position, the screen position of each display panel, and the most important the position and zoom ratio of medical images in the display panel.

- The module of writing diagnostic reports. Radiologists can open the report writing module when observing images, and write reports while observing.

- Eye tracking module. We added the interface of tobii eye tracker, so that the eye tracker can run and collect the radiologists' eye movement data at the same time.

- Data saving. The state of medical image at all times is saved as a csv file, which contains data such as the system timestamp, the current image position, image size, etc.


## Software Introduction

**1. Define the list of images to be displayed before using the software.**

The contents include the root directory of the medical images the layout of the software display panel used to display the images. If there are four images (four views of a mammogram as an example), the layout is set to 2 rows and 2 columns. Of course, it is possible to display two images in 1 row and 2 columns, or just one image.

<div align="center">
    <img src="/res/image_list.png">
</div>



**2. Open the software.** 
Open the software and select **Our Menu Contorl** in the menu bar, click on **Set_Materials** inside, find the file in the pop-up dialogue window and load it. 

<div align="center">
    <img src="/res/materials_menu.png">
</div>

Then the viewer will open the first set of images in the image list.

<div align="center">
    <img width="600px" src="/res/interface.png">
</div>



**3. Diagnosising, writing reports, and switching images.** 

At this point the radiologists is ready to start the diagnosis. The radiologists can adjust the size, position and contrast of the images at will, as well as view each dispaly panel in full screen.

<table style="width:100%; table-layout:fixed;">
  <tr>
    <td><img width="300px" src="/res/adjust.png"></td>
    <td><img width="300px" src="/res/full_screen.png"></td>
  </tr>
  <tr>
    <td><font size="1">Adjusting Images<font></td>
    <td><font size="1">Full Screen of One Dispaly Panel<font></td>
  </tr>
</table>


While diagnosing, the diagnostic report writing module pops up automatically so that the radiologists can write the report while reading it. After the diagnosing, click **Next Case** in the menu bar to switch to the next case.

<div align="center">
    <img src="/res/top_menu.png">
</div>


**4. Close Software.** 

The current diagnostic progress is displayed in the menu bar. 

<div align="center">
    <img src="/res/progress.png">
</div>


Once all cases have been diagnosed, the software can be closed directly. The data generated during the diagnosis process will be automatically saved in a **.csv** file.


## Data

All the collected data is saved in a **.csv** file. Each row in the file is the state of a particular image at a point in time.

<div align="center">
    <img src="/res/data.png">
</div>

As shown above, each line from left to right is, respectively, the system timestamp, the position of the upper left corner of the image on the screen (img_pos_x, img_pos_y), the width and height of the image (img_size_w, img_size_h), the scaling of the image (img_scale_x, img_scale_y), the position of the current display panel on the screen (box_pos_x, box_pos_y), the size of the display panel (box_size_w, box_size_h), the display panel id (position index, e.g., four panel layouts numbered 0-3), and the image path in the current window (dcm_path).


## Build

**1. You should download the ClearCanvas source code and compile it.**

ClearCanvas source code can be found at [ClearCanvas Project](https://clearcanvas.github.io/).
ClearCanvas is an open source code (C#) base for enabling software innovation in medical imaging. It contains a DICOM Viewer and a DICOM Server. In this project, we only use DICOM Viewer for image viewing. You have to open "ImageViewer.sln" with VisualStudio software and compile the project.


**2, Copy the code from the "Modified Code" folder to the appropriate location to overwrite the original code.**


**3, Make your own change like Data Saving Path, Data Saving Format, etc.**



# Eye Tracking Module

The eye tracking module is relatively independent and is implemented through software running an external program.


Still modifying...
