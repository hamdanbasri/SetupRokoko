HOW TO SETUP ROKOKO CHARACTERS WITH LIVE LINK IN UNREAL ENGINE 4
UNREAL ENGINE VERSION: 4.26.2
ROKOKO SMARTSUIT

DIFFICULTY: INTERMEDIATE


Content:
1.Plugins Required
2.Ready Player Me Characters
3.Importing
4.Setup
5.Bone Binding
6.Linking to Rokoko Live Link


1.PLUGINS REQUIRED






2.READY PLAYER ME CHARACTERS
For this example we are using a Ready Player Me Asset, you can create your own at:
https://readyplayer.me/hub

To download, go to the Home Tab, click on the download button at the bottom right of the screen next to the Customize Look button. Click on the Download Avatar on .glb file button.



Note that .glb files are not supported in Unreal Engine, you need to use a 3D software to convert the .glb file into .fbx format. In this case we are using Blender.





Ready Player Me Asset has Blendshapes that controls the facial animations.
Select all in the viewport and Shift + Click the Bone



Then export to .fbx. Make sure to select Selected Objects, Armature and Mesh.
Set the Smoothing to Face (See settings below).





3.IMPORTING
Import the Ready Player Me asset into Unreal.
IMPORTANT: IF SHAPE KEY/BLENDSHAPE IS AVAILABLE, MAKE SURE TO IMPORT MORPH TARGETS








4.SETUP

IMPORTANT: If not T-Pose > Select Skeleton, Make Character T-Pose
Select the skeleton in the Content Browser, double click, a window will pop up, in this case rotate the Left Arm and Right Arm of the Skeleton. For best results make sure the fingers are all straighten. 



Inside the Skeleton Window, create a Pose Asset by going to 
Create Asset > Create Pose Asset > Current Pose

A new Pose Asset will be created in the Content Browser and a new Window will be popped up.


In the Pose Asset window you can see a Tab that has a Pose Name inside. If you move the slider all the way to 1.0 you can see the pose asset that you created earlier.
Now we need to create an Anim Blueprint, this blueprint will control the input data we get from our smart suit that is connected to the Live Link.

Click on the Skeleton in the Content Browser and create an Anim Blueprint. 
Skeleton > Create > Anim Blueprint.



A new Anim Blueprint will be created in the Content Browser, double click on the Anim Blueprint and a new window will pop up.




Search for the following nodes and connect them as follows:
Rokoko Face Pose > Local To Component > Rokoko Body Pose > Component To Local



Now drag the Pose Asset in the Content Browser we created earlier into the Anim Blueprint.





Connect the Pose Asset to the Rokoko Face Pose as above. Right click on the Pose Asset node and then click on the Convert To Pose By Name. Click on Compile.



The details panel now should have a Pose Name with None in the Parameters.



In the Pose Name write the Pose Name found in the Pose Asset.







5.BONE BINDING

Now all that is left is to Map Out the name of the bones from the Ready Player Me Asset to the Rokoko bones naming convention. To do this we need to create a Data Asset. To do this, in your Content Browser, right click on an empty area and select
Miscellaneous > Data Asset.



A Pick Data Asset Class window will pop up, in the Search bar type, Smartsuit. Click on the SmartsuitBodyMapData and press Select.




A new Data Asset will be created in the Content Browser, double click on the Data Asset and a new Window will open. 



The Data Asset windows is where we will replace the bone names with the names of the bones from the Ready Player Me Asset.



To see the name of the bones from the Ready Player Me Asset, double click on the Skeleton in the Content Browser.



For reference purpose undock the Skeleton window and Data Asset window and place them side by side as below:



Rename the Bones in the Data Asset to match the bones from Ready Player Me’s Asset. To do this right click on the bone name in the Skeleton window, and click on Copy Selected Bone Names. Do this for all the bones available in the Data Asset.Once all the name is replaced click Save.





Open back the Anim Blueprint and click on the Rokoko Body Pose, you should see the Bone Map Override in the Details Panel as below. Replace the Bone Map Override with the Data Asset that you created earlier.




Lastly, we need to change the Anim Class in the Details Panel to the AnimBlueprint that we created earlier.








6. LINKING TO ROKOKO LIVE LINK
Open up Rokoko Studio.




Rename the Rokoko Actor Name on the Rokoko Face Pose node and the Rokoko Body Pose Node to match the Actor name in your Rokoko Studio.





Click on Start Live Stream, a new window will appear, make sure to toggle Unreal Engine.




Inside Unreal Engine, go to WIndow and click on Live Link. A new tab will appear.





Click on Source > Rokoko Studio Source > Studio



You will know that you have successfully connect the Livelink from Rokoko Studio to Unreal if you get a green icon.



To view your mocap in the editor in realtime, select your character, in the Details panel scroll all the way down to the Skeletal Mesh component, tick the Update Animation in Editor.




That’s all, good luck.
