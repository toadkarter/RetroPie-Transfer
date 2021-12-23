# RetroPie-Transfer

A small Bash script to efficiently transfer games from a desktop computer to a Raspberry Pi running RetroPie over SSH. 

## Introduction

I decided to write this script at a time when I did not have easy access to an SD card and was becoming frustrated with having to use the cumbersome SCP command every time I wanted to transfer a new game to my Raspberry Pi. While I am sure that there are many ways to achieve what this script does, such as using FTP (or by buying a cheap SD card reader!), I decided to do it this way to practice my Bash scripting skills. I am somewhat satisfied with my result, and I can say with some certainty that it suits my purposes reasonably well, although I have set out in the last section of this ReadMe some areas of improvement that I might try to implement at some stage. 

## Set Up

1. This tool is designed for use with [RetroPie](https://retropie.org.uk/download/). Please ensure that you have RetroPie installed (either by using a standalone image or by installing on top of an existing operating system such as Raspbian).

2. Please ensure that SSH is enabled on you Raspberry Pi. Instructions can be found [here](https://retropie.org.uk/docs/SSH/).

3. Please make a note of your login details and the IP address being used by your Raspberry Pi - this is needed to transfer files over SSH.

4. Place your ROMs into a folder on your local computer, ensuring that it has the same sub-directory structure as the one used by RetroPie. This means that ROMs should be grouped into sub-folders, where each sub-folder name has the name of the console on which those particular ROMs are played. Please ensure that the names of your sub-folders match the ones used by RetroPie. For example, your main folder (which could have any name you want) could have sub-directories entitled "snes", which contain ROMs for SNES games, and "gba", which contains ROMs for GBA games.   

5. Finally, you should make some changes to the pitransfer script specific to your Raspberry Pi as follows:
* **Line 4**: The directory in which your ROMs are stored on your Raspberry Pi should be included in the quotation marks. A sample is included in the script.
* **Line 5**: The directory on your local computer from which you would like to send your ROMS should be included in the quotation marks. A sample is included in the script. 
* **Line 34**: "pi@XXX.XXX.X.XXX" should be replaced, with "pi" being your Raspberry Pi username, and XXX.XXX.X.XXX being the IP address of your Raspberry Pi (I have censored the sample in the script for security purposes).

## Using RetroPie-Transfer

1. Once the steps above have been completed, the user just needs to run the script from any directory and the transfer of files will begin. Please note that the user will be asked for their Raspberry Pi password each time that a new sub-folder of ROMs is being transferred.

2. The script allows the user to input one of two optional "flags" as arguments when running the script. 

* The "-d" flag (which stands for "delete") will delete all the files from a sub-folder once it has completed the transfer.

* The "-c" flag (which stands for "clean") will not transfer any files and will instead simply delete all the files in the various sub-directories of your local machine folder.   

3. As such, the three ways in which the script can be called are as follows:

    pitransfer

    pitransfer -d

    pitransfer -c

## Possible Improvements

As mentioned above, I am still a beginner at using Bash, so I am sure that there are much more efficient ways of achieving what I set out to do with this script. Having said that, I do think there are some additional features that can be implemented, which I have set out below, and which I may incorporate at a later stage.

1. Find a way to transfer all the files with a single SCP command in the script, so that the user is asked for the password only once. I had considered incorporating the sshpass utility, but decided against it, as this method would include the user having to include their password in the script, which is obviously very unsafe.

2. Set up a config file, so that the user can input their target and source directories, as well as their Raspberry Pi info, there without having to make changes to the script. 

3. Add a new flag that allows the user to transfer just one single game. 

4. Find a way to error check a situation where the user is trying to transfer a file that already exists on the Raspberry Pi, or is trying to transfer to a folder that doesn't exist on the Raspberry Pi.

5. It should be theoretically possible to transfer BIOS using this script, but I would like to look into it more to ensure that there are no errors arising from doing so.

***

### DISCLAIMER: I do not condone piracy. Please support game developers by ensuring that any ROMs that you use are of games that you own.