# End-effector Computing

## Yiren (Ramon) Qu, Rosario Scalise

![CSE](img/prl.PNG) ![CSE](img/cse.PNG)

![ADA](img/intro.jpg)

---

# Table of Contents

1.  [What you'll need](#org11f013c)
2.  [Mechanical](#org437c511)
    1.  [Printing the 3D files](#orgf55114f)
    2.  [Mounting the enclosure to the robot arm](#org37ac3e7)
    3.  [Fitting the hardware to the 3D enclosure](#org6f79684)
    4.  [Thermal mitigation](#org3c07fc7)
3.  [Electrical](#org4b2b1a1)
    1.  [Recommended power source](#org7981dc9)
    2.  [Fabricating the cables](#org4e38be8)
    3.  [Connecting the cables](#org54e2305)
    4.  [Cable summary](#orgdba8e15)
4.  [Software](#org84be803)
    1.  [Installing the OS to the Joule™](#orgcbfb208)
    2.  [Installing Required Libraries](#org4290339)
5.  [Recommended Networking Configuration](#orgea01b4a)
    1.  [Client-side (off-board computing) Networking](#org06cd64d)
    2.  [Server-side (end-effector computing) Networking](#orgc67814a)
    3.  [ROS](#orge867589)
6.  [Running](#orgdd11d53)


<a id="org11f013c"></a>

# What you'll need

1.  Intel® Joule™ 570X Developer Kit (or comparable board)

![Intel® Joule™](img/joule.jpg)

2.  Intel® RealSense D415 or D435 RGBD Camera (or openni2 support RGBD cameras)

    2.1 USB type C to A 3.0 cable
    
    > You may use the one come within the box, or order a shorter one.

![Intel® RealSense](img/realsense.png)

3.  3D Printed Parts 
    > Model and printed object will be shown in [3D File section](#orgf55114f)

    3.1 Intel® Joule™ enclosure body

    3.2 Intel® Joule™ Box Flat enclosure Top

    3.3 Intel® Joule™ Box Incline enclosure Top

    3.4 Mount cuff connector
4.  Pololu 12V, 2.2A Step Down. (Voltage Regulator D24V22F12)
5.  Screws:

    5.1 #2 Screw......

    5.2 #3 Screw ......

6. Flat Flex, Ribbon Jumper Cables (20 pins 2.000" (50.80mm)) Molex, LLC 0152670357

![pinConnector](./img/pin_connector.jpg)

7. Round power source plug

8. Active Cooling System for Intel® Joule™ Module

![Active cooling](./img/cooling.png)

9.  Optionally, but best for this application Kinova Mico (you could use your own robot and modify the 'cuff mount')

[Here's a detailed Bill of Materials](#orgdr23442) with pricing (as of June 2018) and links to distributors.


<a id="org437c511"></a>

# Mechanical

<a id="orgf55114f"></a>

## Printing the 3D files

-   Here is the [3D Print-ready files](./3d_model/) for the Intel® Joule™ housing box and mount with the End-Effector.

![Intel® Joule™ enclosure body](img/enclosure_view.PNG)

[Intel® Joule™ enclosure body](./3d_model/enclosure_final.STL)

[Intel® Joule™ Box Flat enclosure Top](./3d_model/Top_regular.STL)

[Intel® Joule™ Box Incline enclosure Top ]()

![Mount cuff connector](./img/cuff_link.PNG)

[Mount cuff connector](./3d_model/ring_final.STL)

![Flat Assembly](./img/flat_assembly.PNG)

![Incline Assembly](./img/incline_assembly.PNG)

Assembly

- I used Solidworks designed each part and test the final assembled parts.
- I printed the model with [Ultimaker 2+](https://ultimaker.com/) and [Creator Pro](http://www.flashforge.com/creator-pro-3d-printer/) and settings are listed below:
    - Layer height: 0.1 mm
    - Infill Percentage: 50%
    - Temperature: 225°C

> - Alternatively, Shapeways supplies high quality 3D print services.

- The final printed model:

![Mount cuff connector](./img/connector_printed.jpg)

Mount cuff connector

![Intel® Joule™ enclosure body](./img/enclosure_printed.jpg)

Intel® Joule™ enclosure body

![Intel® Joule™ Box Flat enclosure Top]()

Intel® Joule™ Box Flat enclosure Top

![Intel® Joule™ Box Incline enclosure Top]()

Intel® Joule™ Box Incline enclosure Top

<a id="org37ac3e7"></a>

## Mounting the enclosure to the robot arm

![mount step 1]()

1. Connect the enclosure body [#3.1] and the end effector cuff connector [#3.4] with 2 Screws [#]

![mount step 2]()

2. Unscrew the Kinova Mico last joint's three screws, which are the three screws shoing in the image. 

![mount step 3]()

3. Direct securely screw the assembled parts(enclosure body + cuff connector) to the arm with screw [#]


<a id="org6f79684"></a>

## Fitting the hardware to the 3D enclosure

### Insert the Joule™ into the enclosure

![insert the Joule™ into the enclosure]()

![mount step 4]()

-  Secure the Intel® Joule™ board [#1] into the enclosure with 4 X Screws [#].

> Please make sure the two wifi antenna would not touch each other and able to be fit in the enclosure.

### Attach camera to the enclosure

Camera Mount 1

![Picture of attaching camera position 1]()

Camera Mount 2

![Picture of attaching camera position 2]()

1. Install flat front camera mount:

    5.1 Mount the Intel® RealSense camera with 2 X screw [#]. 

    > Make sure the camera is securely mounted with the enclosure, which would not resulting much vibration when the end effector's moving

    5.2 Connect camera and the Intel® Joule™ with USB type C to A 3.0 cable [#2.1]

    5.3 Secure the flat enclosure top with 4X screws [#]

2. (Optional) Install incline camera mount:

    6.1 Secure the incline enclosure top with 4X screws [#]

    6.2 Mount the camera on the enclosure.

    > Make sure the camera is securely mounted with the enclosure, which would not resulting much vibration when the end effector's moving

    6.3 Connect camera and the Intel® Joule™ with USB type C to A 3.0 cable [#2.1]


<a id="org3c07fc7"></a>

## Thermal mitigation

Parts[#8]

-   ![Picture of cooler](./img/cooling.png)

You may purchase the part from this [site](https://store.gumstix.com/fansink-intel.html). 

The problem we encouter is the Joule™ would auto-shut down due to the high temperatures. The passive cooling option is not sufficient to cool it down when the camera is running.Then, we used this active cooling part to solve the issue.

![active_cooling](img/active_cooling.PNG)

> When installing this module, you need to take off the four screws which directly on the CPU module. Please remove them carefully and screw them securely with the active cooling module.

<a id="org4b2b1a1"></a>

# Electrical


<a id="org7981dc9"></a>

## Recommended power source

-   Intel® Joule™ with Intel® RealSense running requires at least 1.5A with 12V
> Intel® joule only requires about 0.6A with 12V to boot up.
-   Kinova Mico Joint 6 supplies max 3A with 24V
-   Inside the hand, there is limited space to store the power conversion circuit. We use buck convertor from Pololu [#4] to convert the power from Kinova arm to supply intel Joule™. 


<a id="org4e38be8"></a>

## Fabricating the cables

![schematic diagram](img/elec.PNG)

-  The electronic schematic diagram of the power system. 


![final connected cable image1](img/connected_1.PNG)

![final connected cable image2](img/connected_2.PNG)

-  Final connected cable



<a id="org54e2305"></a>

## Connecting the cables

-   Show Kinova side with pictures

![Kinova side]()

-   Show plugging into board

![plugging into board]()


<a id="orgdba8e15"></a>

## Cable summary

-   ![Picture with Joule™ and all the things plugged into it]()

<a id="org84be803"></a>

# Software

<a id="orgcbfb208"></a>

## Installing the OS to the Joule™

- Please check [this post](./Intel®-Joule™-Setup.md) to install the OS onto the Intel® Joule™.
- In my project, I used Lubuntu (Ubuntu/Linux core 16.03 LTS) with ROS-Desktop version installed. 


<a id="org4290339"></a>

## Installing Required Libraries

- [ROS required packages (with minor modifications)](https://github.com/ramonidea/prl_wireless_perception.git)

    - [ROS Image Transport Plugins](https://github.com/ros-perception/image_transport_plugins.git)

    We used Compressed Image Transport Plugins to compressed the RGB Images. 

    - [ROS Image Pipeline](https://github.com/ros-perception/image_pipeline.git)

    We used one function `point_cloud_xyzrgb` inside the `depth_image_proc` to reconstruct the point cloud data from RGB and Depth images.

    > And their dependency packages `image_common` and `image_geometry`

    - [RGBD_Message](https://github.com/ramonidea/prl_wireless_perception/tree/master/rgbd_message)
        
        This is a custom package trying to solve the problem that depth and color images are not arriving at the same time. This send a message with serialized rgb and depth image data. And we used JPEG lossy compression on Color and lossless compression on Depth.

- [Realsense Camera Driver](https://github.com/Intel®RealSense/librealsense)

    Please follow the [README document](https://github.com/Intel®RealSense/librealsense/blob/master/readme.md) to install the driver.

- [RealSense Camera ROS Wrapper](https://github.com/intel-ros/realsense)

    Please build this after installing the driver.

> If you are using Intel® Realsense R435, you may need to change the parameter to .
>......The code to do that.

## Networking Diagram

![Optiuon 1](./img/option_1.PNG)

Option 1

This option is mainly rely on Python codec and ROS realsense wrapper. It compresses RGB and Depth into one serialized array topic with custom message type: `/camera/rgbd`. And the client side run the decompress methods to separate the one topic into two topics: `/camera/color/decompressed` and `/camera/depth/decompressed`, or it may use the decompression pacakge, which you can call the decompress function in your client side and decompress into two frames without republishing.



![Option 2](./img/option_2.PNG)

Option 2

This option is mainly rely on C++ and ROS realsense wrapper. It compresses RGB and Depth image separately into two topics: `/camera/color/image_raw/compressed` and `/camera/depth/image_raw/compressedDepth`. And the client side may use `Message_filter` to synchronize those two topics. 

<a id="orgea01b4a"></a>

# Recommended Networking Configuration

![Networking](img/networking.PNG)

<a id="org06cd64d"></a>

## Client-side (off-board computing) Networking

-   We are currently using [#] TP-Link XXXX Router. 
-   We set the static IP addresses for both the client side and the server side. 

> For example, you may set the client side to be static as 192.168.2.171. And the joule be 192.168.2.176.

We will run the roscore on the client side. 

<a id="orgc67814a"></a>

## Server-side (end-effector computing) Networking

-   Because we run the rerscore on the client side, please use command to set `ROS_MASTER_URI` and `ROS_IP` on each machine.


<a id="orge867589"></a>

## ROS

-   use command `ifconfig` to retrieve the IP address from your workstation. 

> The ip addresses should be always the same, because we save the ip address in the router setting from the last step.

-  Please make sure the Joule™'s `ROS_MASTER_URI` has been set to that ip address. And set the `ROS_IP` correctly. 


    As an example, if your workstation (ip address `192.168.1.10`) running `roscore` has a wireless adapter IP of `192.168.1.12`, then make sure your terminal running the ROS environment has its `ROS_MASTER_URI` pointed to the workstation like so: `export ROS_MASTER_URI=http://192.168.1.10:11311` and set joule ip address with command: `export ROS_IP=192.168.1.12`


<a id="orgdd11d53"></a>

# Running

-   Please refer to the ADA-Joule™ demo described in this [document](Intel-Joule-ADA-Perception-Demo.md).

<a id="orgdrr23431"></a>

# Appendix

<a id="orgdr23442"></a>

## Bill of Material

|                   Part Name                   | Num of Part |    Price   |
|:---------------------------------------------:|:-----------:|:----------:|
|         Intel Joule 570x Developer Kit        |      1      |   $585.00  |
|             Intel Real Sense D435             |      1      |   $179.00  |
|             3D PLA 1.75mm Filement            |  1kg Spool  |   $20.00   |
|                  Kinova Robot                 |      1      | $40,000.00 |
|           Intel Joule Box (3d print)          |      1      |    Free    |
|             Wrist Mount(3d print)             |      1      |    Free    |
|                   M3 Screws                   |     100     |            |
|                   M3 Washer                   |      20     |            |
|                   M2 Screws                   |     100     |            |
|              Active cooling parts             |      1      |            |
| Pololu 12v 2.2A step down regulator D22V22F12 |      1      |            |
