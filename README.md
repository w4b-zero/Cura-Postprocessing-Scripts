# Cura-Postprocessing-Scripts
Compilation of personnal Ultimaker Cura postprocessing scripts


Installation
--

The files must be stored in the user script directory of the respective Cura version: **\AppData\Roaming\cura<version>\scripts**

After the next start of Cura the script can be added via Extension / Post-Processing / Modify G-Code Add a script.

![Adding script](./images/plugins.jpg)


DisplayPrintInfosOnLCD.py
-----

Description:  This plugin shows custom messages about your print on the Printer Panel...
              Please look at the option
               - LayerId: Use the Layer ID coded in the Gcode and not an increment starting from 0
               
![DisplayPrintInfosOnLCD.py](./images/PrintInfos.jpg)

GCodeDocumentation.py
-----
Description: Add slicing paramter in the GCode Header

![GCodeDocumentation.py](./images/GcodeDocumentation.jpg)

SpeedTower.py
-----
Description:  postprocessing-script to easily define a Speed Tower.

![SpeedTower.py](./images/speedtower.jpg)

TempFanTower.py
-----

Description:  postprocessing-script to easily use an temptower and not use 10 changeAtZ-scripts

 The default values are for this temptower PLA model [https://www.thingiverse.com/thing:2493504](https://www.thingiverse.com/thing:2493504)
- Temp Tower PLA de 210 à 170
- Possibility to define also a Fan Tower , Fan percentage speed indicate with semi-colon as seprator

![TempFanTower.py](./images/tempfan.jpg)


RetractTower.py
-----

Description:  postprocessing-script to easily create a Retract Tower

Two options :

    - Speed   :  Speed variation
	
    - Retract :  Distance retract variation

![RetractTower.py](./images/retract-tower.jpg)


ZMoveIroning.py
-----

Description: ZMoveIroning for 3D prints. Z hop for ironing

![ZMoveIroning.py](./images/ZmoveIroning.jpg)


RepRapPrintInfos.py
-----

Description: add header infos and part thumbnail for RepRap machine 3DWOX  

![part thumbnail](./images/benchy.jpg)

**Not fuly tested**

GradientInfill.py (original idea from [CNCKitchen](https://github.com/CNCKitchen/GradientInfill) )
-----

**Version : 1.5**

GradientInfill.py Posprocessing Script for Cura PlugIn. Save the file in the _C:\Program Files\Ultimaker Cura **X.X**\plugins\PostProcessingPlugin\scripts_ directory.

Extrusion mode in Cura must be set in relative mode. If it's not the case an error message will be raised in Cura.

![Message](https://user-images.githubusercontent.com/11015345/72720216-c1662580-3b79-11ea-9583-60de8240eef2.jpg)

No Gcode will be generated by Cura in this case. Same behaviour if Cura settings are not suitable for Gradient Infill modification :

- Infill pattern type ZigZag , Concentric , Cross and Cross3D not allowed  
- In cura the option "Connect Infill Lines" for the other patterns musn't be used.

The wall must be done before the Infill element. So In Cura the Option infill_before_walls must be set to Off

**Postprocessing Options**

![PostProcessing](./images/gradient.jpg)

- Gradient Distance :  Distance of the gradient (max to min) in mm
- Gradient Discretization : Only applicable for linear infills; number of segments within the gradient(segmentLength=gradientThickness / gradientDiscretization) use sensible values to not overload
- Max flow : Maximum extrusion flow
- Min flow : Minimum extrusion flow
- Short distance flow : Extrusion flow for short distance < 2x Gradient distance
- Gradual speed : Activate also Gradual Speed linked to the gradual flow
- Max over speed : Maximum over speed factor
- Min over speed : Minimum over speed factor
- Extruder Id : Define extruder Id in case of multi extruders
- Test with outer wall : "Test the gradiant with the outer wall segments


A new Flow Value for short distance (Linear move < 2 x Gradient distance) added to the standard GradientInfill script.

Add a gradual speed variation for machine without direct drive extruder.

![gradient infill](./images/gradient2.jpg)

Sample part with a Gradient distance set to 8 mm :
![Gradient distance set to 8 mm](./images/gradient3.jpg)

CommentGCode.py
----

This Cura Postprocessing Script adds comments to the G-Code. The user can select or deselect comments for M-Commands and G-Commands separately.

G0 and G1 commands are only commented if a retract is included.

Command, description and parameters are read from a CSV file. If a command is not contained, the required data is determined once via the website http://marlinfw.org/docs/gcode/ and added to the CSV file.

![CommentGCode.py](./images/commentGcode.jpg)


InsertAtLayerChange.py
----

Modification of the official script with Layer Increment.
	

FastFirstInfill.py
----

Script cura to set a higher filling speed for the first layer.

![FastFirstInfill.py](./images/fastfirstinfill.jpg)

	
Original first layer speed before modification
	
	
![First layer speed](./images/origine.png)

First layer speed after modification with the script.
	
	
![First layer speed after modification](./images/result.png)
	
	
SlowZ.py
----

Script cura to reduce the speed according to the print height. 

![SlowZ.py](./images/slowz.jpg)
	
	- Slow Z percentage : Positive value to slow the print as the z value rises up to this percentage.
	
	- Slow Z height : Positive value to define the start height of the speed reduction.
	
	- Display details on LCD : This setting will insert M117 gcode instructions, to display current modification in the G-Code is being used.

![SlowZ settings](./images/slowzsettings.jpg)
	


MultiBrim.py
----

Script cura to duplicate the initial Brim/skirt to obtain a thick Brim. 

![MultiBrim.py](./images/multibrim.jpg)
	
	- Brim multiply : Number of brim to multiply.
	
	- Brim speed : Speed for the subsequent brim.
	
Multi layer brim height request on Cura Github [#6929](https://github.com/Ultimaker/Cura/issues/6929)
	
Different tests made with the current release (V1.6)

![MultiBrim test](./images/multilayerbrim.svg)
