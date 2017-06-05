# EternalJukebox


The source files for the EternalJukebox, a rehosting of the Infinite Jukebox.  
This repo contains everything you need to host the EternalJukebox on your own server!  


You can visit the official site here:  
https://eternal.abimon.org/  
Incase you want to mess around with it without doing all the hard stuff.  


# Documentation


## Prerequisites

### Java:
##### Windows
download and install Java from https://www.java.com/en/download/  
##### Debian-based Linux distributions
For Ubuntu or Debian-based distributions execute `sudo apt-get install default-jre` in the terminal   
##### Fedora and CentOS
There is a tutorial for installing java on Fedora and CentOS at https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora   

### Youtube-dl:
##### Windows
Download the .exe at https://yt-dl.org/latest/youtube-dl.exe and place it in `C:\Windows\`
##### Linux
Use these commands in the terminal to install youtubedl on Linux:  
`sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`   
`sudo chmod a+rx /usr/local/bin/youtube-dl`

## Getting the project files:
### Windows
There is two ways to get the files depending on what you prefer:
###### Without git 
You can download the zip directly here https://github.com/UnderMybrella/EternalJukebox/archive/master.zip 
Then extract them in any folder you like e.g. C:\EternalJukebox

###### Using git
First download and install Git for Windows from https://git-scm.com/downloads
After that open the Command Prompt, move to a folder you like to have the server files. 
For example you can type `CD C:\Github\` (Folder has to exist)

Then you can just use the command `git clone https://github.com/UnderMybrella/EternalJukebox.git` and the files should download to the folder you executed the command in.

### Linux
On Linux there is also two ways to get the files depending on what you prefer:
###### Without git
First off, if you have a desktop environment you can just download the zip with the files directly from https://github.com/UnderMybrella/EternalJukebox/archive/master.zip and extract them in a folder you like.  
However it might be better to use Git so you can update the files more easily!

###### Using git
You can generally install Git tools through the package-management tool that comes with your linux distribution.   

For example on **Fedora** you can use `sudo dnf install git-all`  
And on **Debian/Ubuntu** you can use `sudo apt-get install git-all"`  

After that you can move to a folder you'd like to keep the files using the `cd` command and then clone EternalJukebox to it with:  
`git clone https://github.com/UnderMybrella/EternalJukebox.git`  

#### Prebuilt jar
Unless you want to build the jar yourself with Gradle you need to download it here https://eternal.abimon.org/built.jar and place it in the folder containing `default-config.json` and `jukebox_index.html`

## Configuring
First rename default_config.json to config.json and open it with notepad/notepad++ on windows or nano on linux "nano config.json"

Now you should go to https://developer.spotify.com/my-applications/ and log in to your spotify account.
Then click the Create an app button, give it a name and description and click create.
You should get to your new application's page, the only thing you need is your Client ID and Client Secret (Note: Never share these with anyone!)

Now fill in the Config file accordingly, you can also change the port if you'd like it to be something else but other than that there is no need to touch options.

For the search function to work you will need a SQL Database running on the same machine the server will be running on.
If you want this you need to replace the config content with this and fill this in instead.

{
  "comment":"This is the default config used by EternalJukebox, make sure to fill everything in for EternalJukebox to work correctly!",
  "ip":"http://$ip:$port",
  "port":11037,
  "logAllPaths":true,
  "spotifyClient":"Insert your Spotify Client ID Here",
  "spotifySecret":"Insert your Spotify Client Secret Here",
  "mysqlUsername":"Your SQL username",
  "mysqlPassword":"Your SQL password",
  "mysqlDatabase":"The SQL database used by EternalJukebox",
  "uploads":true
}

When you are done save the config and move on to the next step.

## Starting the server:

Now you should be able to start the server,
Open the terminal (or Command Prompt as Administrator on windows) and move to the folder you saved EternalJukebox.jar in, i.e. "cd C:\EternalJukebox"
Then type "java -jar EternalJukebox.jar" (remember to use sudo in linux and running the Command Prompt as admin on windows)
it should return something like "Listening at http://0.0.0.0:11037" this means it is running correctly.

you should now be able to connect to it with a browser through http://localhost:11037 congrats!

Building with gradle (for those who want to): 
Firstly ofcourse you need to install gradle.
There is a full documentation here https://gradle.org/install

Open a Command Prompt as Administrator or Terminal on linux and move to the folder you cloned the project files to earlier. i.e. "cd C:\EternalJukebox" if you cloned to the C drive
Now use the command "gradle clean shadowJar" or on Linux "sudo gradle clean shadowJar"

Then move the .jar from build/libs/ to the project folder and rename it to EternalJukebox.jar

Now you should be done!
