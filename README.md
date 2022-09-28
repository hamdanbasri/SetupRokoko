<a name="readme-top"></a>

# HOW TO SETUP ROKOKO CHARACTERS WITH LIVE LINK IN UNREAL ENGINE 4
![Unreal Engine](https://img.shields.io/badge/unrealengine-%23313131.svg?style=for-the-badge&logo=unrealengine&logoColor=white)

<em>VERSION: 4.26.2
ROKOKO SMARTSUIT

DIFFICULTY: INTERMEDIATE</em>

> Note: Has not been tested for Unreal Metahumans.

<details>
<summary>Table of Contents</summary>
<ol>
    <li><a href="#plugins-required">Plugins Required</a></li>
    <li><a href="#ready-player-me-characters">Ready Player Me Characters</a></li>
    <li><a href="#importing">Importing</a></li>
    <li><a href="#setup">Setup</a></li>
    <li><a href="#bone-binding">Bone Binding</a></li>
    <li><a href="#linking-to-rokoko-live-link">Linking to Rokoko Live Link</a></li>
</ol>
</details>

<hr>

## 1.PLUGINS REQUIRED

<br><div align="center">
<img src="images/Picture1.png">
<img src="images/Picture2.png">
<img src="images/Picture3.png">
<img src="images/Picture4.png">
</div><br><br>

<p align="right">(<a href="#readme-top">back to top</a>)</p><hr>

## 2.READY PLAYER ME CHARACTERS
> For this example we are using a Ready Player Me Asset, you can create your own at:
https://readyplayer.me/hub

> To download, go to the Home Tab, click on the download button at the bottom right of the screen next to the Customize Look button. Click on the Download Avatar on .glb file button.

<br><div align="center">
<img src="images/Picture5.png">
</div><br><br>

> Note that .glb files are not supported in Unreal Engine, you need to use a 3D software to convert the .glb file into .fbx format. In this case we are using Blender.

<br><div align="center">
<img src="images/Picture6.png">
<img src="images/Picture7.png">
<img src="images/Picture8.png">
</div><br><br>

> Ready Player Me Asset has Blendshapes that controls the facial animations.

> Select all in the viewport and Shift + Click the Bone

<br><div align="center">
<img src="images/Picture9.png">
</div><br><br>

> Then export to .fbx. Make sure to select Selected Objects, Armature and Mesh.
Set the Smoothing to Face (See settings below).

<br><div align="center">
<img src="images/Picture10.png">
<img src="images/Picture11.png">
</div><br><br>

<p align="right">(<a href="#readme-top">back to top</a>)</p><hr>

## 3.IMPORTING
> Import the Ready Player Me asset into Unreal.
IMPORTANT: IF SHAPE KEY/BLENDSHAPE IS AVAILABLE, MAKE SURE TO IMPORT MORPH TARGETS

<br><div align="center">
<img src="images/Picture12.png">
</div><br><br>

<p align="right">(<a href="#readme-top">back to top</a>)</p><hr>

## 4.SETUP

> IMPORTANT: If not T-Pose > Select Skeleton, Make Character T-Pose
Select the skeleton in the Content Browser, double click, a window will pop up, in this case rotate the Left Arm and Right Arm of the Skeleton. For best results make sure the fingers are all straighten. 

<br><div align="center">
<img src="images/Picture13.png">
<img src="images/Picture14.png">
<img src="images/Picture15.png">
</div><br><br>

> Inside the Skeleton Window, create a Pose Asset by going to 
Create Asset > Create Pose Asset > Current Pose

<br><div align="center">
<img src="images/Picture16.png">
</div><br><br>

> A new Pose Asset will be created in the Content Browser and a new Window will be popped up.

<br><div align="center">
<img src="images/Picture17.png">
<img src="images/Picture18.png">
</div><br><br>

> In the Pose Asset window you can see a Tab that has a Pose Name inside. If you move the slider all the way to 1.0 you can see the pose asset that you created earlier.

<br><div align="center">
<img src="images/Picture19.png">
</div><br><br>

> Now we need to create an Anim Blueprint, this blueprint will control the input data we get from our smart suit that is connected to the Live Link.

> Click on the Skeleton in the Content Browser and create an Anim Blueprint. 
Skeleton > Create > Anim Blueprint.

<br><div align="center">
<img src="images/Picture20.png">
</div><br><br>

> A new Anim Blueprint will be created in the Content Browser, double click on the Anim Blueprint and a new window will pop up.

<br><div align="center">
<img src="images/Picture21.png">
<img src="images/Picture22.png">
</div><br><br>


> Search for the following nodes and connect them as follows:
Rokoko Face Pose > Local To Component > Rokoko Body Pose > Component To Local

<br><div align="center">
<img src="images/Picture23.png">
</div><br><br>

> Now drag the Pose Asset in the Content Browser we created earlier into the Anim Blueprint.

<br><div align="center">
<img src="images/Picture24.png">
<img src="images/Picture25.png">
</div><br><br>


> Connect the Pose Asset to the Rokoko Face Pose as above. Right click on the Pose Asset node and then click on the Convert To Pose By Name. Click on Compile.

<br><div align="center">
<img src="images/Picture26.png">
</div><br><br>

> The details panel now should have a Pose Name with None in the Parameters.

<br><div align="center">
<img src="images/Picture27.png">
</div><br><br>

> In the Pose Name write the Pose Name found in the Pose Asset.

<br><div align="center">
<img src="images/Picture28.png">
<img src="images/Picture29.png">
</div><br><br>

<p align="right">(<a href="#readme-top">back to top</a>)</p><hr>


## 5.BONE BINDING

> Now all that is left is to Map Out the name of the bones from the Ready Player Me Asset to the Rokoko bones naming convention. To do this we need to create a Data Asset. To do this, in your Content Browser, right click on an empty area and select
Miscellaneous > Data Asset.

<br><div align="center">
<img src="images/Picture30.png">
</div><br><br>

> A Pick Data Asset Class window will pop up, in the Search bar type, Smartsuit. Click on the SmartsuitBodyMapData and press Select.

<br><div align="center">
<img src="images/Picture31.png">
<img src="images/Picture32.png">
</div><br><br>


> A new Data Asset will be created in the Content Browser, double click on the Data Asset and a new Window will open. 

<br><div align="center">
<img src="images/Picture33.png">
</div><br><br>

> The Data Asset windows is where we will replace the bone names with the names of the bones from the Ready Player Me Asset.

<br><div align="center">
<img src="images/Picture34.png">
</div><br><br>

> To see the name of the bones from the Ready Player Me Asset, double click on the Skeleton in the Content Browser.

<br><div align="center">
<img src="images/Picture35.png">
</div><br><br>

> For reference purpose undock the Skeleton window and Data Asset window and place them side by side as below:

<br><div align="center">
<img src="images/Picture36.png">
</div><br><br>

> Rename the Bones in the Data Asset to match the bones from Ready Player Me’s Asset. To do this right click on the bone name in the Skeleton window, and click on Copy Selected Bone Names. Do this for all the bones available in the Data Asset.Once all the name is replaced click Save.

<br><div align="center">
<img src="images/Picture37.png">
<img src="images/Picture38.png">
<img src="images/Picture39.png">
</div><br><br>

> Open back the Anim Blueprint and click on the Rokoko Body Pose, you should see the Bone Map Override in the Details Panel as below. Replace the Bone Map Override with the Data Asset that you created earlier.

<br><div align="center">
<img src="images/Picture40.png">
<img src="images/Picture41.png">
</div><br><br>


> Lastly, we need to change the Anim Class in the Details Panel to the AnimBlueprint that we created earlier.

<br><div align="center">
<img src="images/Picture42.png">
<img src="images/Picture43.png">
</div><br><br>

<p align="right">(<a href="#readme-top">back to top</a>)</p><hr>

## 6. LINKING TO ROKOKO LIVE LINK
> Open up Rokoko Studio.

<br><div align="center">
<img src="images/Picture44.png">
<img src="images/Picture45.png">
</div><br><br>


> Rename the Rokoko Actor Name on the Rokoko Face Pose node and the Rokoko Body Pose Node to match the Actor name in your Rokoko Studio.

<br><div align="center">
<img src="images/Picture46.png">
<img src="images/Picture47.png">
</div><br><br>

> Click on Start Live Stream, a new window will appear, make sure to toggle Unreal Engine.

<br><div align="center">
<img src="images/Picture48.png">
<img src="images/Picture49.png">
</div><br><br>

> Inside Unreal Engine, go to WIndow and click on Live Link. A new tab will appear.

<br><div align="center">
<img src="images/Picture50.png">
<img src="images/Picture51.png">
</div><br><br>

> Click on Source > Rokoko Studio Source > Studio

<br><div align="center">
<img src="images/Picture52.png">
</div><br><br>

> You will know that you have successfully connect the Livelink from Rokoko Studio to Unreal if you get a green icon.

<br><div align="center">
<img src="images/Picture53.png">
</div><br><br>

> To view your mocap in the editor in realtime, select your character, in the Details panel scroll all the way down to the Skeletal Mesh component, tick the Update Animation in Editor.

<br><div align="center">
<img src="images/Picture54.png">
<img src="images/Picture55.png">
</div><br><br>

> That’s all, good luck.
