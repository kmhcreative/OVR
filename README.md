OVR
(Object VR Viewer)
Version 1.5
Created By K. M. Hansen
Email: software@kmhcreative.com
Website: http://www.kmhcreative.com/labs/ovr/

OVR is a script that can automatically turn image sequences into rotating virtual reality objects.  Your first image must have a file name ending in "vr_00" and all subsequent frames use that same naming convention.  You may have up to 100 frames (numbered vr_00 - vr_99).  File format just needs to be something browsers can show (JPG, JPEG, GIF, PNG).

QUICK START INSTRUCTIONS
========================
1. upload all scripts to your site (for example "js")
2. call scripts into your HTML page in this order:
<link rel="stylesheet" type="text/css" href="ovr/ovr.css" />
<script type="text/javascript" src="js/getElementsByClassName-1.0.1.js"></script>
<script type="text/javascript" src="ovr/ovr.config.js"></script>
<script type="text/javascript" src="ovr/ovr.swap.js"></script>
<script type="text/javascript" src="ovr/ovr.js"></script>

Note: first script is optional for IE support and is not included.  Get the latest version from the author at http://robertnyman.com/2008/05/27/the-ultimate-getelementsbyclassname-anno-2008/

3. Include the following attributes in your <BODY> tag:
````
<body onload="OVR.init();" onresize="window.location.href=window.location.href;" onorientationchange="OVR.vrSliderFix();">
````
onload event runs the OVR script
onresize event reloads page so new variables are used
onorientationchange event may or may not be read as a resize depending on device.  If not then the slider coordinates need to be adjusted for the new orientation.

4. In the content of your page, wherever you would like to include an OVR player add:
````
<div class="ovr f-16">
	<img src="mypic-vr_00.jpg" />
</div>
````
The "ovr" class helps the OVR script find each image that should be turned into a OVR player.
The "f-16" part is optional.  The number indicates the number of frames in the animation sequence.  If you omit the f-xx style the script will assume your animation has 8 frames.

You do not need to give the image a width and a height.  OVR will use either the size as set in the stylesheet or, if no CSS is applied to the image, the actual size of the image.

5. You will most likely want to set at least some styles in your CSS:
````
.ovr {} /* Image width + borders x 2 & image height + borders x 2 + 50 pixels
.ovr img, .ovr .vr img {} /* Set image size in this one */
.vr {}
.ovrmsg /* Optional message on what users should do */
````
6. Look at the sample documents for working examples if this didn't make sense to you.

IMAGE SWAP OPTIMIZATIONS
========================
1. If you include the "ovr.swap.js" file it must be included AFTER the "ovr.config.js" file.
2. In that file set ovrCount = to the number of OVR Players in the HTML page.
3. For each image add to the multi-dimensional array in the following format:
````
	ovrData[x][0] = "path/to/first/phone/image_vr_00.jpg"; 			<- for low-res phones
	ovrData[x][1] = "path/to/first/desktop/image_vr_00.jpg"; 		<- for desktop (also laptops and tablets)
	ovrData[x][2] = "path/to/first/hires_phone/image_vr_00.jpg";	<- for high-density phones
	ovrData[x][3] = "path/to/first/hires_desktop/image_vr_00.jpg";	<- for high-density desktops (also laptops and tablets) 
````	
4. Paths to the images can be relative to the HTML file or full paths
5. If you leave the high-density options empty it will default to the low-res versions
6. Generally speaking the high-density images should be twice the pixel size of the low-res versions:
low-res phones 	 = 240 x 160, high-res phones  = 480 x 320, low-res desktop  = 640 x 480, high-res dekstop = 1280 x 960
	
Portrait images swap width and height, and you can change these default sizes in the "ovr.css" file.

QUICK START INSTRUCTIONS 
========================
(Embed in Ryuzine 0.9.6.1+ Publication)

1. Make sure that the OVR Add-On is your Ryuzine "addons" folder
2. In the <HEAD> of your Ryuzine HTML file add the script links as shown in step 2 above.
3. DO NOT ADD OVR FUNCTION CALLS TO <BODY> TAG!
4. Insert the OVR Player into a Ryuzine Publication lightbox container element
5. Create a lightbox link thumbnail to open the lightbox into which you placed the OVR Player
6. The OVR players will be initialized automatically by Ryuzine.

INSTALL/UPDATE RYUZINE ADD-ON
=====================
Simply drag the "ovr" folder into the Ryuzine publication's "/addons" folder.  If you have a previously installed version of OVR in the "addons" folder just overwrite it, and its contents, with the new one.


CHANGELOG
=========
1.5 Fixed touch-tracking so it isn’t “sticky” anymore, removed config options no longer needed,
    fixed minor CSS issues, switched slider limits calculation to getBoundingClientRect() method
1.4 Reorganized files so users can drag-n-drop update the Ryuzine Add-On
1.3 More intuitive interface (no slider), no resizing of vr box, no image map fallback
1.2 added OVR alias for script calls, shortened script names, fixed touch slider tracking issue.
1.1 minor fixes to CSS and JS for embedding
1.0 first public release

LICENSE
=======
Released under the MIT license (same license as getElementsByClassName script)
See LICENSE.TXT file included with distribution for full notice.


