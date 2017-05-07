# teachingbox

A Vagrant box I use for my machine learning lectures.

Includes

* Ubuntu Trusty 64 (14.04)
* Lubuntu desktop with Firefox web browser
* Anaconda3-4.3.1
* keras
* tensorflow

## Prerequisites

* vagrant
* virtualbox

## Install

Run

    vagrant up

in the folder where you downloaded or cloned the files from this repository, and vagrant should take care of building the virtual machine. Make sure you have a fast and stable internet connection!

During the build a window will pop up asking username and password. Ignore that window for the time being, and when Vagrant has finished building, close that window. Don't select the "save machine status" option, as we want to force a full restart of the virtual machine.

## Usage

You can start the virtual machine from the VirtualBox application: it should appear as a machine named "teachingbox_default_...". Alternatively, run

    vagrant up

again in the folder where you downloaded or cloned the contents of this repo.

Once the Graphical User Interface shows up, select the user "vagrant" and type the password "vagrant". If you are asked whether you want to update to a new Ubunbu distribution, don't do it!

### Configuring keyboard layout

If you are not using an US keyboard it is recommended that you change the machine keyboard layout settings:

* Right click on the "US" symbol on the bottom-right part of the screen, then select "Keyboard Layout Handler Settings"
* Uncheck "Keep system layouts"
* Click "+ Add"
* Select your desired keyboard layout (e.g. Spanish) and click "OK"
* Move the newly created keyboard layout to the top of the list, using the "Up" and "Down" buttons.

### Opening a comand line terminal

* Click on the menu symbol at the bottom-left part of the screen, then "Accesories", then "LXTerminal"

### Starting Jupyter notebook

* Open a command line terminal following the steps above.
* Run "jupyter notebook" on the command line.

This should open the Jupyter notebook on a browser inside the virtual machine. The machine is also configured to bind the Jupyter port to the local host, so you can also connect to it in from your local browser by typing the url http://localhost:8888 .

