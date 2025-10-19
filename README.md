# BCRYExporter
<H1>History Authors</H1>

* Current author: brickengineer, https://github.com/brickengineer/BCRYExporter
* Blender 2.8 author: LeonidasWhite, https://github.com/LeonidasWhite/BCRYExporter
* Initial author: AFCStudio, https://github.com/AFCStudio/BCRYExporter

<H1>Installation:</H1>

Copy `io_bcry_exporter` folder to `<BLENDER PATH>\scripts\addons` directory.<br>
<b>Example:</b> `C:\Users\<YOUR USER NAME>\AppData\Roaming\Blender Foundation\Blender\4.3\scripts\addons`

<H1>(NOT CONFIRMED INFO) Known issues/limitation:</H1>

<b>NOTE: The following description is not up tp date</b>
1) Custom split normal doesn't support Sharp edges in skin node. <br> <b>Solution:</b> Add Edge split modifier before Armature modifier, set up and apply. The skin mesh will be rip in Sharp edges places.
2) There is no way to set active any collection, so be careful that current active collection be unhide and not disable. Otherwise you can expect Error that Object is Null. I put in some operators code which set Master collection(Scene Collection) active.
3) In some cases when you modify the armature as add bones through edit_bones.new() method or other way BCRYExporter will be export armature with broken bones hierarchy. I think that is Blender bug because I nothing changed in export code except fix errors with Bmesh convertation. <br> <b>Solution:</b> I added a button in Bone utilities: Rebuild-armature. It rebuild selected armature from zero and copy all bones parameters: name, matrix, roll, parent, some properties and custom properties then delete old bones. It don't copy bone constraints at the moment.<br> <b>IMPORTANT:</b> vertex groups renames too, but only if the object is a children of this armature. Do skin object a child of armature before use this button.
