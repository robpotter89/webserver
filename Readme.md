# webserver.py
### Raspberry Pi - Simple python Stand Alone Local Network Web Server
#### Reads folder and file entries into a right pane list. 
#### Selected folder opens new tab and Selected file displays in left pane.

### Description
This is a single file stand alone python webserver that needs minimal or no setup.
This webserver can be used to remotely view images, video, documents, html, java, Etc.
files from your(LAN) local area network connected computers using a web browse. 
Directory links to files and subfolders are dynamically created and displayed
in a right side listing that can be arranged and sorted via variables. 
Variables are contained in the settings.py file and allow customization of
webserver display and configuration settings.

I use webserver.py in my pi-timolo and other projects
to allow easy browsing of image, video or other files.

This web server can display other types of content
like javascript, css Etc will run. A sample calculator program is
include in the calculator folder of the www web root.
If a folder has an index.html it will take over
the browser tab. html files will be displayed full screen in browser tab.

If a folder is selected on the right pane listing
the folder contents will appear in a new browser tab.

***IMPORTANT***
You cannot navigate back to the previous folder from
this new tab so when you are done with the folder
tab just close it.  You can navigate through a
folder structure but remember each folder will
open a new tab.

This browser can only access local raspberry pi files.
It cannot access internet web pages.

***Please Note***
You will need at least two entries in a folder
before the web server will display content.

***Change Web Root***
Edit the settings.py to change the default www folder web root to
another folder location of your choice.

### Quick Install
For Easy webserver-install.sh onto raspbian RPI.

    curl -L https://raw.github.com/pageauc/webserver/master/webserver-install.sh | bash

From a computer logged into the RPI via SSH(Putty) or desktop terminal session
* Use mouse to highlight curl command above, right click, copy.
* Select RPI SSH(Putty) window, mouse right click, paste.
The command will download and execute the GitHub webserver-install.sh script

### Manual Install
From logged in RPI SSH session or console terminal perform the following. You can review
the webserver-install.sh script code before executing.

    cd ~
    wget https://raw.github.com/pageauc/webserver/master/webserver-install.sh
    chmod +x webserver-install.sh
    ./webserver-install.sh

### How to Run webserver.py

Use menubox.sh for an easy way to manage the webserver

    cd ~/webserver
    ./menubox.sh

or to manually start webserver.py in the foreground (ctl-c to stop)
Note if you exit the terminal session the webserver will exit.  See below
for manually running webserver.py in background using webserver.sh

    cd ~/webserver
    ./webserver.py

A message will be displayed indicating the ip address:port to enter in
a browser url bar.  This will access the webserver files in the server web root.

If you want to run the webserver.py as a background daemon then use webserver.sh
If no parameter is specified it will display the PID or indicate webserver.py is
not running.

To Start webserver.py as a background daemon

    cd ~/webserver
    ./webserver.sh start

To Stop webserver.py

    cd ~/webserver
    ./webserver.sh stop

### Run webserver.py on Boot

To auto launch webserver.py on boot-up of raspberry pi perform the following

    sudo nano /etc/rc.local

In nano add the following command to the rc.local file just before the exit 0 command.
This will launch webserver and the webserver in the background running under the pi user (not root).
Note the webserver startup is optional.

    su pi -c "/home/pi/webserver/webserver.sh start > /dev/null"

ctrl-x y to save and exit nano editor

Reboot RPI and test operation by triggering motion and checking images are successfully saved to your motion or timelapse folder.

    sudo reboot

use menubox.sh to verify that webserver.py is running after reboot

### Customize Settings

The webserver.py variables are stored in the settings.py file.  These can be
edited using the nano editor to customize for your particular needs if required

Edit settings.py file using nano editor per the following commands

    cd ~/webserver
    nano settings.py

ctrl-x y to exit nano editor and save changes

You can also use menubox.sh to edit/view the webserver settings

    cd ~/webserver
    ./menubox.sh

### Reference Links
webserver wiki - https://github.com/pageauc/pi-timolo/wiki/Access-images-via-webserver   
github webserver repo - https://github.com/pageauc/webserver


Good Luck
Claude Pageau
