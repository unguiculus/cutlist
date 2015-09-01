

# Introduction #

Answers to common questions. These apply to all versions unless specifically stated otherwise. Some issues have been fixed and where this is true, the recommended version is given.

# Q&A #

## I am running Sketchup 8 or Sketchup 2013 and I am getting an error when trying to produce the layout ##

Upgrade to a CutList v4.1.6 or higher.

Download the latest from here: https://code.google.com/p/cutlist/downloads/list
and install using  the extension installer from within Sketchup (4.1.6 was the first version which came in the .rbz format) or find and install using Extension Warehouse.

The issue is that Sketchup 8/2013 was upgraded to accept only html5 as a baseline for html code and parts of the script producing the layout used some older constructs which are no longer supported in html5

## I have a board or a sheet which is a different size from the standard sizes available through the layout sheet or layout board tab. How can I enter a custom size? ##

In the current version, it is not possible to enter custom sizes for layout. However, in the short term, it is possible to customize your copy of the plugin with a minor change to the source code ( if you feel comfortable doing this).

You can customize Cutlist to your own sheet sizes if you are willing to modify the ruby script a tiny bit. The infrastructure is there for custom sizes but this was planned to be added in a future release.

It’s easy enough, however, to override the existing sizes for now. For example, to have the 4’x8’ selection in the sheet layout configuration screen mean something else, follow these instructions.

In the Sketchup plugins folder, find and open the folder called 'sr\_cutlist' ('cutlist in older versions), then find and open for editing ( using any text based editor) the file reporter.rb

Find the following lines:

![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/CustomSheetSizes.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/CustomSheetSizes.jpg)

Now change, in this case, the last width option and the last length option to be the value that you want it to be. So, for example if you want to layout on a plastic sheet 60”x144”, you would have to change the line:

![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetWidthLine.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetWidthLine.jpg)

to

![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetWidthLineNew.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetWidthLineNew.jpg)

and the line:

![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetLengthLine.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetLengthLine.jpg)

to

![http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetLengthLineNew.jpg](http://i222.photobucket.com/albums/dd242/daltxguy/Cutlist_40/SheetLengthLineNew.jpg)

Then save the file.

For those of you dealing with metric sizes, unfortunately everything has to be converted to inches ( 1” = 25.4mm) because inches are used internally for all measures. (It’s a sketchup thing but rather arbitrary anyway – they could have used rods or chains or light years!) This has no bearing on whether you’ve used metric or imperial measures in your sketchup model. No need to change anything there.

If you haven’t yet opened sketchup, then the next time you open sketchup it will load this new version of the cutlist plugin. If you already have sketchup open, the easiest thing to do is to close sketchup and re-open it. Otherwise you’ll need to open the ‘ruby console’ window ( Window->Ruby Console), close any open windows for cutlist and then type in

load “cutlist.rb”

in the ruby console window ( don’t forget the double quotes, this is an important part of it). When you press return, it will print the word ‘true’.



If you now open up Cutlist, it will be running your modified version.
Select sheet option 4×8 and you will now have everything laid out on a 60×144 sheet.

Of course, other sizes can be made in the same way. You can even change the meaning of the other options too and have a few variations available to you other than the pre-programmed options.

The same methodology can be used for board sizes too. It works the same way. The settings for the board options are found just above the sheet settings in the ruby script.


---


## I have some parts which I want to layout on sheet goods but they are being layed out on boards. How do I get my parts to be recognized as sheet parts? ##

In order to get parts recognized as sheet parts, either the part name or the material applied to the component must match all of or a part of one of the 'sheet words' on the first page of the  menu. This is the only way that parts can be distinguished from being a solid part or a sheet part.

So for example, name your part as 'mdf shelf' or 'plywood shelf' and then make sure either 'mdf' or 'plywood' is included in the list of 'sheet words'.

You can tell how it has interpreted the part when you just run the cutlist without the layout. It divides the list into parts and sheets. If the part doesn't come up as sheet in the list, it won't be placed on a sheet good in the layout.


---


## I use your cutlist plus interface. I can't get items like screws and hinges to come across as hardware. It gets listed as Dimensional Lumber (DL). What can I do? ##

Make sure the version you are using is at least v4.1.4 because that's when this functionality was first added. In previous versions all 'hardware' parts were added as standard board parts.


---


## I get "~" in front of my dimensions and my dimensions are not what I expect. Is this a problem with Cutlist? ##

If you are getting dimensions other than what you expect and there is a ~ in front of it,this means that Sketchup can't figure out an exact dimension for your component. The plugin merely extracts the value from Sketchup's database and displays it in the cutlist so this is not an issue with the plugin.

Usually this means that your component does not have parallel edges. You may have inadvertently stretched one side or corner. Many people use the presence of ~ in a dimension to mean that there is a likely error in their model and will review the dimensions and geometry more carefully.

The other possibility is that you have changed the accuracy of your model and your drawn component cannot be represented in your current scale. Usually this happens if you've reduced the accuracy. So, for example you drew something accurate to 1/16ths but then you change the model accuracy to be 1/8ths, then a value like 3/16 cannot be represented in the less accurate scale and ~ will be added to the dimension and some rounding will likely take place in the displayed dimension.

If the dimensions are much larger than you would expect, then the other thing to check is to see if the component axes are parallel to model axes. Sketchup draws a bounding box around the component in the direction of the component axes. If your component is skewed, then it has to draw a bigger box. Cutlist gets its dimension from the bounding box (this is the blue box which appears when you click on a component). There are other reasons why bounding boxes get larger than the component, so double check these.

The bounding box itself does not have to be parallel to any of the model axes as Cutlist correctly gets a dimension from a tilted bounding box, but the bounding box itself should be made to be the smallest dimension possible to contain the component, or else the displayed component dimensions will not appear to be what you would expect, based on your drawn component dimensions.


---


## The layout is not what I expect. Some small parts spill over onto another board or sheet. Is this a bug? ##

Yes and No.

There are certain combinations of parts which are not optimally layed out with the current version. This is a technical issue with the implementation of the layout algorithm. Especially with lots of parts of varying sizes - some large some small, these 'fracture' the remaining space calculated on a board or sheet forcing parts to move to another board or sheet when otherwise it is obvious by eye that it could have gone on a previous board or sheet.

This is a case of the human being better than the computer or the case where the computer algorithm has not yet mimicked obvious human skills with an appropriate mathematical model.

Use the resulting layout as a guide, then use your human cognition to adjust if necessary. Like any tool, it does not replace human common sense.

This will hopefully be improved in later versions...but there are paid programs out there which do a much better job if that is absolutely required. CutListPlus is one suggestion (no connection to this plugin - however this plugin is designed to interwork with it).


---
