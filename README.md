<div align="center">
	<img src="assets/logo.svg" alt="Rostar logo" width="20%"/>
	<h1>Rostar</h1>
	Dead simple fully managed Rojo helper for Roblox projects
</div>

## Description

Rostar is a command-line tool that unpacks/packs Roblox place files (`rbxl`/`rbxlx`) into model files and `.lua` scripts in the filesystem, for use with [Rojo](https://rojo.space/). It is useful to both developers that prefer Roblox Studio, but also to Rojo users that would like a fully managed workflow without a hassle.

Think of it like being able to treat your .rblx files like a .zip file.

We made this for users who do all of their work in Roblox Studio, who also wanted an easy way to get access to a tree of files for .git to work against.

If you wish to use full Rojo, this can also be a good starting point but you'll probably want to use custom Rojo project configurations.

Eg: 

>rostar unpack myplace.rbxl

{A filesystem is created containing .lua files, models, and folders in a best-attempt to recreate the myplace.rblx Roblox Studio workspace}

>rostar pack newplace.rbxl

{packs the previously unpacked filesystem back into newplace.rbxl, ready to be loaded into Roblox Studio}


## Documentation

https://tacheometry.github.io/Rostar


## Thanks

A huge thankyou to Tacheometry who literally put this entire thing together and was patient while we described what we wanted!

A MEGA HUGE thankyou and shoutout to the whole Rojo and Remodel team and community, because this is 100% derived and dependent on their work.


## How does it work

This works by wrappering Remodel and Rojo and turning their functionality into the "unpack" and "pack" commands.
Rostar walks your .rblx datamodel and tries to create folders and files that match what was found.

Generally:
* Scripts are extracted to lua files (No they are not all collected into a single location - Go organize your workspace!)
* Folders are recreated 1:1
* Models are extracted to their own .RBXM files, if it can (see below)
* "Loose Instances" (eg: random parts in your scene) get included into a parent .rbxm


## Limitations

* Currently cannot handle package links, as Rojo/Remodel doesn't understand those either.
* Currently cannot extract scripts with _duplicate names and paths_ into their own files, instead they'll be packaged into a parent .rbxm and you'll get a warning.
* Currently cannot extract models or instances with _duplicate names and paths_, they will be treated as "loose instances" and packaged into a parent .rbxm





