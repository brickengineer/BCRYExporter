# BCRYExporter
# Note
* Blender 4.5 LTS will be the last major version to support. This is because Blender 5.0 has removed collada support, which is used by CryEngine Resource Compiler as intermediate file format.<br/>
* However, this plugin will still be maintained in the future.
* If encounter with any bugs or issues (even in rare cases). I'd appreciate it if you could bring them into the 'Issues' with detailed description and some screen shots or error message. This would help to make this tool better. Thanks.

# Installation:
Copy `io_bcry_exporter` folder to `<BLENDER PATH>\scripts\addons` directory.<br>
<b>Example:</b> `C:\Users\<YOUR USER NAME>\AppData\Roaming\Blender Foundation\Blender\4.5\scripts\addons`

# Version History
## Repo & Authors History
* Current repo author: brickengineer, https://github.com/brickengineer/BCRYExporter
* Blender 2.79-2.8 repo author: LeonidasWhite, https://github.com/LeonidasWhite/BCRYExporter
* Initial author: AFCStudio, https://github.com/AFCStudio/BCRYExporter

## Update History
### 1.3.0
* [Animation] Support animation frame rate write into metadata during export. (Note: This does not mean you can play 60 fps animation in CryEngine. To support 60 fps aniamtions, you need to modify the engine and RC accordingly.)
* [Utils] Fixed 'Add Root Bone' utility function
### 1.2.0
* [UI] Removed obslete UI functions when update from blender 2.79 to 2.8
* [Material] Improved all material utility functions and fixed some errors
* [Physics] Improved physical proxy material naming convention on creation
* [General] Fixed all __init__ errors due to Blender 4.5 api changes
### 1.1.1
* Fixed Add export node and "feet on floor" utility function error due to blender 4.5 LTS API changes by @AbhijitL in https://github.com/brickengineer/BCRYExporter/pull/5
### 1.1.0
* Supports Blender 4.5 LTS (4.5.3)
### 0.9.0
* Supports Blender 4.4
* Fixed possible error during temp replacing smooth by angle modifier (geom node) by edge split on export and restore after done

# Known issues/limitation:
## Confirmed
1) Failed to export skin node if check "export selected only"
## NOT Confirmed INFO
<b>NOTE: The following description is not up tp date so not confirmed yet</b>
1) There is no way to set active any collection, so be careful that current active collection be unhide and not disable. Otherwise you can expect Error that Object is Null. I put in some operators code which set Master collection(Scene Collection) active.
2) In some cases when you modify the armature as add bones through edit_bones.new() method or other way BCRYExporter will be export armature with broken bones hierarchy. I think that is Blender bug because I nothing changed in export code except fix errors with Bmesh convertation. <br> <b>Solution:</b> I added a button in Bone utilities: Rebuild-armature. It rebuild selected armature from zero and copy all bones parameters: name, matrix, roll, parent, some properties and custom properties then delete old bones. It don't copy bone constraints at the moment.<br> <b>IMPORTANT:</b> vertex groups renames too, but only if the object is a children of this armature. Do skin object a child of armature before use this button.
