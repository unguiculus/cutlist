# Introduction #

The following lists the main features of the CutList plugin for Sketchup. It is not necessarily complete but will help decide if it is something which will be useful for you.


# List of features available in Sketchup plugin CutList 4.1 #

  * Cutlist is produced from the set of components you select from your model.
  * Can automatically select all components if none was selected.
  * Splits cutlist into solid wood components, sheet good components or hardware/other parts based on keywords which you select. Keywords can also be specified to exclude items with the '-' options if there is ambiguity between part names. ( For example a hardware 'part' and solid wood 'partition' )
  * Summarizes cutlist showing board feet or square feet (for sheet goods) by material and also gives totals.
  * Cutlist can be displayed in summary (compact) form, in order of the selected components or in a sorted list.
  * Handles metric and imperial measure based on the options selected in your model.
  * All options can be saved, with the 'save setting' option. These are stored in a cookie and are reloaded next time you use CutList 4.1.
  * CutList output can be saved in CSV format or CSV format compatible with CutListPlus or displayed in an html page.
  * OS's set to a Non-English 'locale' will have CSV files generated using ';' as a field delimiter. This is to allow for countries which use the ',' as a decimal character rather than the".'" ( decimal).
  * Layout can be displayed in an html page or saved as a SVG fileand displayed using an SVG reader. Firefox supports SVG ( just open the file using Firefox). MS IE with the Adobe SVG plugin is another option.
  * Layout is made on board sizes which you select, both length and width and thickness for boards and length and width for sheet goods.
  * Boards can be selected to be specified in a  nominal size or actual size. Layout will occur on the nominal size if selected.
  * Nominal thicknesses supported are 4/4, 5/4, 6/4, 8/4 and 10/4
  * Layout options are split into general options,boards and sheets options
  * Layout options include 'split wide parts' which splits wide parts in even pieces based on your widest board, 'split thick boards' - will divide parts into pieces based on the thickest board selected.
  * Layout on boards when a thickness is specified can include a margin for planing. Part placement will take this into account and board feet will be increased as needed.
  * The layout calculates an efficiency usage of each board and an overall efficiency for boards and and an overall efficiency for sheets.
  * Saw kerf size can be specified for the layout and the layout automatically leaves enough room for the boards including the wood lost to the cutting operation. Saw kerf can be specified in any size and multiple units in both metric and imperial measures, allowing a full range of saw kerf sizes. This feature can also be used to add additional space onto each board for other operations such as final dimensioning and planing.
  * Some things not included in this version:
  * Part orientation is assumed to be grain running in the direction of the longest side. No support for part rotation.

## Known Issues: ##
  * Functional Mac support but there is still an issue between Sketchup and Safari that prevents the layout html display from working. Your alternative is to use the SVG layout format and reading the SVG from Firefox, for example. The solution probably requires a fix to be sorted by Sketchup ( if you could select your browser, this issue would go away - hint Google!) or a different design which avoids the incompatility.