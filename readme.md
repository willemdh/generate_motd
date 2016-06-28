# Bash tool to display system information after logging into a Linux system

### Idea

This tool displays useful system information after logging into a Linux system, such as version, CPU information, 
memory, disk information. 

### Screenshots

Modern:

![MotD Generator Modern Raspbian](/../screenshots/generate-motd-modern-raspbian.png?raw=true "MotD Generator Modern Raspbian")

Blue:

![MotD Generator Blue Raspbian](/../screenshots/generate-motd-blue-raspbian.png?raw=true "MotD Generator Blue Raspbian")

Red:

![MotD Generator Red Raspbian](/../screenshots/generate-motd-red-raspbian.png?raw=true "MotD Generator Red Raspbian")

Original:

![MotD Generator Original Raspbian](/../screenshots/generate-motd-original-raspbian.png?raw=true "MotD Generator Original Raspbian")


### Status

Production ready.

### How To

Please check https://outsideit.net/FireMotD/ for more information on how to use this plugin.

### Help

In case you find a bug or have a feature request, please make an issue on GitHub.

### Usage Help

```
$ FireMotD --help
FireMotD v5.05.160628

Usage: 
 FireMotD [-v] -t <Theme Name> 
 FireMotD [-v] -C ['String']
 FireMotD [-vUhVs]

Options:
 -h | --help               Shows this help and exits
 -v | --verbose            Verbose mode (shows messages)
 -V | --version            Shows version information and exits
 -t | --theme <Theme Name> Shows Motd info on screen, based on the chosen theme
 -C | --colortest [string] Prints color test to screen using the provided string,
                           or the default string 'FireMotD' if none provided.
 -U | --updates            Checks for system updates and prints count to stdout
 -s | --saveupdates        Checks for system updates and saves count to disk
                           same as [ FireMotD -U > /var/tmp/updatecount.txt ]

Available Themes:
 original
 modern
 red
 blue
 clean
 html

Examples:
 FireMotD -t original
 FireMotD --theme Modern
 FireMotD --colortest '###'
 sudo FireMotD --saveupdates

Note:
 Some functionalities may require superuser priviledges. Eg. check for updates.
 Please try doing sudo ./FireMotD if you have problems.
```

### System Install

You need to have `make` installed on the system.

##### To install to /usr/local/bin/FireMotD:
```bash
sudo make install
```
With this you can probably run FireMotD from anywhere in your system. If not, you need to add /usr/local/bin to your $PATH variable. To adjust the installation path, change the var `IDIR=/usr/local/bin` in the Makefile to the path you want.

##### To install bash_completion:
```bash
sudo make bash_completion
```
With this you can use TAB to autocomplete parameters and options.
Does not require the sudo make install above (system install), but requires the `bash-completion` package to be installed and working.

### Crontab example 

This is an example on how to record the system update package count daily.  
This will update the file /var/tmp/updatecount.txt for later access.  
Root privilege is required for this operation.

##### To edit root's crontab:
```bash
sudo crontab -e
```

##### Then add this line (updates everyday at 3:03am)
```bash
3 3 * * * /usr/local/bin/FireMotD -s
```

##### Or using the old way:
```bash
3 3 * * * /usr/local/bin/FireMotD -U > /var/tmp/updatecount.txt
```

### Adding to an SSH session

##### To add this to a single user, just call the program from the user's ~/.profile file.
```bash
nano ~/.profile
```

##### Then add to the end (choose your theme):
```bash
/usr/local/bin/FireMotD -t red
```

### On Nagios Exchange

https://exchange.nagios.org/directory/Utilities/FireMotD/details

### Copyright

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public 
License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later 
version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the 
implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more 
details at <http://www.gnu.org/licenses/>.
