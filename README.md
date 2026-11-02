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
### pending updates
### 1.4
#### [Character]
* Fixed failure to export skin node if check "export selected only". (_Keep skeleton export helpers separate per armature and preserve the selected export nodes while creating them._)
* Check Resource Compiler exit codes and wait for character/skin second-pass compilation; propagate conversion failures as cancelled exports.
* Remove the experimental `Rebuild Armature` tool and its bone, vertex-group, and action rewriting logic; the historical Known issues #2 rebuild workaround is no longer available.
#### [Model]
* Fixed custom normal export. (_Preserve custom corner normals and color seams, including active BYTE/FLOAT and POINT/CORNER color attributes._)
#### [Material]
* Preserve material slot indices, including repeated and object-linked materials; reject faces using missing materials before writing output.
* Add seperate `Include Material Textures` option. (_Disabled by default, to Export, Quick Export, and Generate Materials. This can prevent texture path false alarm/error when export to a different disk but blend has textures (in different paths) assigned to mesh materials._)
#### [General]
* Preserve unrelated selected objects when clearing skeleton physics, and keep existing objects untouched when export helper names collide.
* Restore scene mode, pose, frame/subframe, selection, bone visibility, and original smoothing modifiers after successful or failed exports.
* Include COLLADA image definitions and recognize node textures in both Cycles and EEVEE.
* Honor `Save TIFFs`, preserve source images and existing TIFFs, skip absent/duplicate textures, and apply normal-map green inversion to the actual compiler input.
* Run DAE and texture conversion synchronously on Blender's main thread instead of background Python threads; export operators finish after conversion, and the UI may pause during compilation.
* Fix UDP property editing, weight normalization, single-material physics colors, animation channel references, rotation transform targets, and rotation tangent units.
* Remove obsolete `Rebuild Armature` functionality.

### 1.3.1
* [Character] Add Primitive Mesh character utility. Fixed created primitive mesh (triangle) become orphaned if selected armature's all collection belongs to is Non exportable node collection.
* [Animation] Improved locomotion locator auto find movement bone name.
* [Animation] Fixed locomotion locator auto initial key frame offset
* [Mesh] Fixed Generate LOD errors: AttributeError: 'NodesModifier' object has no attribute 'ratio'
### 1.3.0
* [Character] Support character skin mesh LODs export. (Just export with seperate export node with suffix 'LOD#')
* [General] Support F32 vertex format
* [General] Support force 8 weights
* [Animation] Support animation frame rate write into metadata during export. (Note: This does not mean you can play 60 fps animation in CryEngine. To support 60 fps aniamtions, you need to modify the engine and RC accordingly.)
* [Utils] Fixed 'Add Root Bone' utility function
* [Physics] Fixed false alarm of "Please select a bone in POSE mode!" when use 'Edit Bone Physics and IKs"
* [General] Fixed Use Custom Normals export option is always true no matter if it is checked. Note: Usually should be checked
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