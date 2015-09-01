# Introduction #

CutList installation instructions for both Windows and Mac


# Who can use it? #

If your computer supports Sketchup, then the plugin is suitable to use.

Installation procedure is the same for both Windows (all OSes) and Mac (all versions) and for all versions of Sketchup.

The plugin works on all versions of Sketchup (Free, Make and Pro)

## Installation for version 4.1.6 and newer (.rbz file) ##

Follow Sketchup plugin instructions [here](http://support.google.com/sketchup/bin/answer.py?hl=en&answer=38583)

## Installation for version 4.1.5 and older ##

It's a 2 step process.

  1. Download the plugin. The download file is a zipped file containing everything needed for the plugin. The zipped file contains the main ruby script cutlist.rb and a folder called cutlist which contains all other files required.
  1. Unzip the contents of the downloaded file into the plugins directory of Sketchup
The actual location of the plugins directory for Sketchup depends on whether you are running Windows or Mac.

|Windows using Sketchup 8|Mac using Sketchup 8|
|:-----------------------|:-------------------|
|C:\Program Files\Google\Google SketchUp 8\Plugins\|HD/Library/Application Support/Google SketchUp 8/SketchUp/Plugins/|

This is how your directory should look like after installation:
![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_41/CutListInstall.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_41/CutListInstall.jpg)


## Notes: ##
  * If you are upgrading from an older version of cutlist, make sure you first remove the older files.

  * Some older versions were contained in a single file called CutListAndMaterials.rb. Please remove this as it will conflct with the newer versions. In CutList 4.0 there was the file CutListAndMaterials.rb as well as a folder called 'cutlistui'. If you are upgrading from this version, remove the cutlistui folder as well.

#### Windows users ####

On Windows Vista and Windows 7, there is something called User Account Control (UAC). The user you are using needs Administrator status before you can copy files to the plugins directory, otherwise it will look like you installed it, but in fact it installed in a 'ghost' directory and Sketchup won't see it. ( Confusing? - tell Microsoft. Another one of their helpful features that only a geek can understand )

You may have to switch users ( there is always at least one user on a machine with Administrator status but it may not be the one you are using) or you can temporarily ( or permanently as I have) disable UAC. Since I am the only user on my machine, it is ok for all users to have Administrator status. In any case, this has tripped up quite a few installs.

#### Mac users ####

Some users have reported that after installing Cutlist plugin neither the Plugins menu ( and therefore ) nor the CutList menu item appears. If this is the case, the recommended solution is the following:
Try going to SketchUp>Preferences>Extensions, then check Ruby Script Examples. Close SketchUp and then restart it. You should get the Plug In menu when SketchUp opens again.

All features work for Mac users except for the display of the layout in a window. This has to do with the way the display is created in html and Safari, the default browser which Sketchup uses regards this as a security issue ( because CutList produces a script which is then executed to draw the window).

So that Mac users can use the layout feature, the SVG option was created (works for Windows users as well). The SVG option creates a set of files which are viewable in most browsers now and the output is the same as if it had been displayed in a window, except that each page is in a separate file.

## Other resources: ##
  * A good summary of the installation procedure and some Q&A is available at [Dave Richard's Design.Click.Build blog on Fine Woodworking](http://www.finewoodworking.com/item/32267/cut-list-plugin-installation)