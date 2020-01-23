# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. 

  `/Users/nwcreper/Desktop/temp/wats1030-intro-to-unix`

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. 

  ```zsh
  LICENSE                       nix_scavenger_hunt.md
  README.md                     nix_scavenger_hunt_stretch.md
  challenge_files               super_scavengers.md
  ```

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. 

  ```zsh
  total 48
  drwxr-xr-x    9 nwcreper  admin   288B Jan 22 22:36 .
  drwxr-xr-x   14 nwcreper  admin   448B Jan 22 22:32 ..
  drwxr-xr-x   14 nwcreper  admin   448B Jan 22 23:08 .git
  -rw-r--r--    1 nwcreper  admin   1.1K Jan 15 18:53 LICENSE
  -rw-r--r--    1 nwcreper  admin   2.7K Jan 15 18:53 README.md
  drwxr-xr-x  111 nwcreper  admin   3.5K Jan 15 18:53 challenge_files
  -rw-r--r--    1 nwcreper  admin   5.9K Jan 22 23:11 nix_scavenger_hunt.md
  -rw-r--r--    1 nwcreper  admin   319B Jan 15 18:53 nix_scavenger_hunt_stretch.md
  -rw-r--r--    1 nwcreper  admin   255B Jan 15 18:53 super_scavengers.md
  ```

  *It is displaying a significant amount of additional data. When I looked up what these mean, it makes more sense. `-l` is short for long list, and shares more attributes like permissions and file size. `-h` is short for human, which translates file sizes to a more human-friedly notation. `-a` stands for all, which shows hidden folders and files.*

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://man.he.net/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. 
  - *man...* `formats  and  displays the on-line manual pages.`
  - *ls -a...* `List all entries except for . and ...  Always set for the super-user.`
  - *ls -l...* `long (-l) output.`
  - *ls -h...* `print this help message.`

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. 

  ```zsh
  Applications Users        cores        home         sbin         var
  Library      Volumes      dev          opt          tmp
  System       bin          etc          private      usr
  ```

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues)

  `/`
* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. 

  `/Users/nwcreper`

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. 

  *There are three files:*
  ```zsh
  -rw-r--r--   1 nwcreper  admin      0 Jan 15 18:53 2015_special_stuff.demo
  -rw-r--r--   1 nwcreper  admin      0 Jan 15 18:53 cloaked-wookie.demo
  -rw-r--r--   1 nwcreper  admin      0 Jan 15 18:53 scooter-double-mamba.demo
  ```
* Use the `cd` command to move "up" one directory.

  `/Volumes/g/g2/wats1030-intro-to-unix`

* Press the up arrow on your keyboard. 

  *It tabbed back to my last entered command, which was* `pwd`

* Press the up arrow a few more times. 

  ```zsh
  ls -l | grep ".demo"
  ```

* Run the `history` command.

  *5,316 previously entered commands*
  

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*
* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*
* How long has your system been running? Use `uptime` to see, and *paste the result here:*
* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*
* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*
* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*
* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*
* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*
* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*
* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*
