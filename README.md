# welearntui
Personal repo for quickly downloading my uploaded class lectures on Welearn.

## Installation
1. Create `id.file` file in `~/.local/share/welearntui/` directory and edit it according to your courses. (See `id.file` section below).
2. Create `credentials.txt` file in `~/.local/share/welearntui/` directory and edit it according to your credentials. (See `credentials.txt` section below).
3. Change the `SAVE_DIR` in `welearn` script according to where you want to save the downloaded files.
4. Place `welearn`, `welearnlogin` scripts (after giving executable permissions) in a directory which is in your `PATH` environment variable.

OR

Just use `welearninstall` script to guide you through the above process.

## `id.file`
It consists of three tab separated columns, the first is the *Course ID* (e.g. `ma3201`) the second is its *Welearn ID* (e.g. `1018`) and the third is the *Course Name* (e.g `Topology`).  
You will have to edit `id.file` each time the list of courses changes (be it due to logging in as another user who does not have the same set of courses or moving to another semester).
1. The *Course ID* (set it to your choice) is the string which you will need to enter as the first argument when invoking `welearn`. Hence, its better to keep it lowercase. (e.g. `welearn ma3201`).
2. The *Welearn ID* can be attained by looking at the course links on the Welearn website. E.g. if the course link is `https://welearn.iiserkol.ac.in/course/view.php?id=1018`, then the *Welearn ID* for this course is `1018`. (Will write a script for auto generating that later, maybe).
3. The *Course Name* (`course_name`) (set it to your choice) will be the name of the directory under `SAVE_DIR` where the files for that particular course will be saved. For e.g. `welearn ma3201` will save files in `SAVE_DIR/Topology/` (if `Topology` is the *Course Name* for `ma3201`).  

Sample `id.file` has been provided.

## `credentials.txt`
Two separate lines should be present:
1. First containing username.
2. Second containing password. 

Sample `credentials.txt` has been provided.

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
This will automate the setup process.

## Dependencies
The only dependency is `fzf`: https://github.com/junegunn/fzf

## TODO
Replace webpage scraping with Moodle Web Services API. (Maybe)
