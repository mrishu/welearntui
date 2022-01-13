# welearntui
Personal repo for quickly downloading my uploaded class lectures on Welearn.

## Installation
Use `welearninstall` script to guide you through the setup process.

## Setup Process Instructions
I. First you will be asked to enter your username and password.

II. Then you will be asked to enter `SAVE_DIR`, where the downloaded files will be saved under their corresponding *Course Name*s which you will have to enter later.

III. Now you will be asked to fill three variables for each course: *Course ID*, the *Welearn ID* and the *Course Name*.  

1. The *Course ID* (set it to your choice) is the string which you will need to enter as  argument when invoking `welearn`. Hence, its better to keep it lowercase. (e.g. `welearn ma3201` or `welearn -na ma3201` etc.).
2. The *Welearn ID* can be attained by looking at the course links on the Welearn website. E.g. if the course link is `https://welearn.iiserkol.ac.in/course/view.php?id=1018`, then the *Welearn ID* for this course is `1018`. (Will write a script for auto generating that later, maybe).
3. The *Course Name* (`course_name`) (set it to your choice) will be the name of the directory under `SAVE_DIR` where the files for that particular course will be saved. For e.g. `welearn ma3201` will save files in `SAVE_DIR/Topology/` (if `Topology` is the *Course Name* for `ma3201`).  

## Usage
`welearn *course_id*` will open the resources available for `*course_id*` in `fzf`. `fzf --multi` option is enabled, so multiple resources can be dowloaded at once. Use `TAB` to select multiple resources in `fzf`.

If `welearn *course_id*` is called without options, and if a file which is to be downloaded already exists in the download location, a prompt will come up asking whether the user wants to replace the existing file or not. Choosing `y` or `Y` will overwrite/replace the existing file with the new one; any other choice will skip it and the older file will not be overwritten.  

### Options
`welearn -b *course_id*` will turn on blacklisting mode. This won't download any files but is used for blacklisting unwanted files. You can select multiple resources for blacklisting using the `fzf` menu. Blacklisted resource names with their links will be stored in `SAVE_DIR/course_name/blacklist.txt` and won't be downloaded in any download mode unless manually removed from there.  

`welearn -f *course_id*` will **replace** all existing files automatically.    
`welearn -n *course_id*` will **skip** all existing files automatically.  

`welearn -fa *course_id*` will select all files for download (without `fzf` menu) and **replace** all existing files automatically.  
`welearn -na *course_id*` will select all files for download (without `fzf` menu) and **skip** all existing files automatically.  

### `welearnlogin`
`welearnlogin username password` script will log you in. But, there is no need to do it as `welearn` script logs in automatically if logged out.

### `welearninstall`
This will guide the user through the setup process.

### `welearnup`
Helper script using `welearn` which applies the `welearn -na *course_id*` command for every `*course_id*` in `~/.local/share/welearntui/id.file`. This will automatically skip all existing files and download the new ones for each course.

## Dependencies
The only dependency is `fzf`: https://github.com/junegunn/fzf
