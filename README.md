
Asset Status Overlay Plugin Documentation
Overview

The Asset Status Overlay plugin adds visual status indicators to assets in the Unreal Editor's Content Browser. It allows content creators and teams to track the production status of assets through customizable overlays that appear directly on asset thumbnails.
Features
Customizable status labels with colors
Configurable font size for overlays
Context menu integration in Content Browser
Quick status removal option
Status persistence via asset metadata
Level Viewport Status Visualisation (New)
Installation
Enable the plugin in Edit → Plugins → Editor → Asset Status Overlay
Configuration
Accessing Settings
Open Edit → Project Settings
Navigate to Plugins → Asset Status Overlay
Configure the following settings:



Available Settings
Available Statuses: List of status configurations
Status Name: Text displayed on the asset
Status Color: Color of the status text
Tooltip: Description shown on hover (optional)
Show Status Change Dialog: Toggle notification when status changes
Show Toolbar Icons : Toggles the viewport debug icons on the main toolbar (off if you want less clutter)
Overlay Font Size: Size of the status text (6-72 points)


Default Status Configurations
The plugin comes with three default statuses:
L0 (Red) - "Test"
L1 (Orange) - "Production"
L2 (Green) - "Final"
Other use case examples
Track asset review stages: WIP → Approved → Final (or L0 > L1 > L2)
Manage level design passes: Blockout → Playtest → Polish
Support VFX or animation review workflows: Needs Review → Final
QA and testing pipelines: Pending Test → Passed → Reopened
Internal communication: Owned by X → On Hold → Needs Update

Production Status Overlay helps teams stay organized and reduces friction in large productions by keeping asset progress visible to everyone at a glance.
Usage

!! Important Note on Status Management !!
This plugin is a manual tracking tool - it does not automatically detect or update asset states. Status changes require human input as assets progress through production. Team members must manually:
Set appropriate status when starting work on an asset
Update status as the asset progresses through production stages
Review and update status after quality checks or revisions
Remove status when needed


Managing Asset Status
Select one or more assets in the Content Browser
Right-click to open the context menu
Navigate to Asset Status submenu
Choose from:
Remove Status: Removes status overlay completely
Available statuses list (L0, L1, L2, etc.)

Setting Asset Status
Select any status from the list to apply it
Status appears immediately as colored text overlay
Multiple assets can be updated simultaneously
Removing Status
Select "Remove Status" from the Asset Status submenu
Works on multiple selected assets
Completely removes the status overlay
Careful, no confirmation needed, action is immediately applied
Visual Feedback
Status appears as colored text overlay on asset thumbnails
Refreshing the Content Browser view is needed to update the thumbnails



!! Viewport Debug View (NEW FEATURE)


In version 2.0 a new viewport debug was added, now you can see the status of a Static Mesh, Skeletal Mesh, PLA and Level Instances or Material*(first material in the list)

This is using the ActorColorization debug and can be turned on by the two toolbar icons (eye icon and material icon)
 
OR by navigating to Window Menu > Scroll down to Asset Status Overlay 

This will turn on this debug:

Tips
To refresh thumbnail overlay display: Change folders or refresh the Content Browser view style
To disable notifications: Uncheck "Don't show this message again" in the status change dialog
Multiple assets can be updated simultaneously by selecting them before applying or removing a status


Technical Details

Metadata
Status is stored as "AssetStatus" metadata tag
No additional files or databases required
Clean removal via metadata tag deletion
Performance
Lightweight implementation using asset metadata
Minimal impact on Content Browser performance
Status changes are immediately saved
Requirements
Unreal Engine 5.x
Editor Scripting Utilities plugin (auto-enabled)
Best Practices
Establish consistent status naming conventions
Use distinct colors for different status levels
Update statuses as assets progress through pipeline
Configure status options before wide team usage
Use "Remove Status" when returning assets to untracked state
Troubleshooting & Support
Common Issues
Overlays not visible
Solution: Refresh Content Browser view
Workaround: Switch folders and return

Status not saving
Verify asset is not read-only
Check source control status
Menu option not appearing
Verify plugin is enabled
Restart editor if recently enabled
Remove Status not working
Verify asset is not read-only
Check for source control locks
Try refreshing Content Browser

For issues or feature requests send an email to IANistor
Version History
Current Version: 2.0
Bug fixing and optimization
Added viewport overlay debug
Version: 1.0
Initial release
Core status overlay functionality
Status removal capability
Customizable statuses and appearance
Content Browser integration
Configurable font size


Frequently Asked Questions
Q: Can I add my own custom statuses? Or more of them?
A:Yes ! You can, using the project settings.


Q:Can I change the color of each status?
A: Yes, using the plugin’s project settings.


Q:Overlay does not update after status change
A:Yes, that is one of the known limitations, content browser needs to be refreshed, I couldn't find a way to do that so far. So for you to see the updated overlay you need to navigate to a different folder and then back to your selection.


Q:What's the intended use case?
A: I developed it for Production status tracking,  so i can quickly see if im using an asset that is not meant for production 


Q:Does it support Version Control ?(Perforce)
A:Yes it does, meaning If an asset is open for changes/checked out, it will check out and save your change, otherwise If the asset is not in an edit state then you will still see the overlay locally but until you submit your status change others won't see them.

Q:Does it connect to Jira?
A: Not right now, I will probably look into adding this functionality in future versions however.


Q:Does the viewport visualizer support PLA and Level Instances?
A: Yes, as long as the meshes are not merged each status will retain their display of status using the visualizer even if they are part of a Packed Level Actor or Level Instance.


