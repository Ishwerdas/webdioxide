---
published: true
layout: post
date: '2016-8-30 00:08:19 +0530'
categories: links
author: Shaina Sabarwal
image: notes.jpg
permalink: /meteor-app-on-android-device
comments: true
title: Running My Meteor App on Android Device
---

Working in meteor is already super easy and a bliss. I have worked in meteor before, but this time, I wanted to use one of the best features of meteor that is making a cross platform application. 
So the challenge here was to run and install my meteor app in my Xiaomi Redmi Note 3 Android (version Lollipop) phone.

Let's see how I did that.

#### 1. Installing Meteor 

Connect your computer with Internet and run this command in terminal

` curl https://install.meteor.com/ | sh `

Linux curl will download meteor installation script and linux sh command is used to run that script.

#### 2. Create new Meteor project
 
` meteor create piaoma `

Meteor will create a project named piaoma having two folders Clients and Server and a package.json file. Explaining what these are about are out of scope of this post. You can anyway learn development in Meteor from https://guide.meteor.com/index.html

Now I wanted to run and install this project piaoma at my Android phone.
For this, I followed the Meteor guide https://guide.meteor.com/mobile.html#installing-prerequisites

To run your meteor application inside your android device, you need first to add android platform 
` meteor add-platform android `

But, it will require you to install some prerequisites including JDK (Java Development Kit) and Android Studio.

I am working in Ubuntu, so I preferred to use Ubuntu make as it installed JDK and Android Studio both easily just by using a few commands. 

**Add ubuntu make ppa first**
` sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make `

**Update your system**
` sudo apt-get update `

**Install Ubuntu make**
` sudo apt-get install ubuntu-make `

**Run umake to install android**
` umake android `

Next step is Setting **ANDROID_HOME** and adding the tools directories to your **PATH**

If you see the guide, the path to Sdk that is to be put into **ANDRIOD_HOME** variable is ~/Library/Android/sdk, but Ubuntu-make made Android folder in my home folder and so the path that I had to store in ANDROID_HOME is "/home/shaina/Android/Sdk" , where 'shaina' is my username

**export ANDROID_HOME="/home/shaina/Android/Sdk"
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools**

I added above two lines in .bashrc file which resides in my home. To do that, just open the **.bashrc** file (I use vim as editor)

`sudo vim ~/.bashrc `

and add those lines at the last of the file.
Save and Quit

Then Reload .bashrc (by executing source ~/.bashrc)
` source ~/.bashrc`

When I tried to run my project by 

` cd ~/piaoma `
` meteor run android-device `

It asked me to install android-target: android 23 using SDK manager.
It is given in the hint, how to run sdk manager, as shown in screenshot below

![Terminal Screenshot]({{ site.url }}/images/terminal.png)

Just go inside the **Android/Sdk/tools** and run android 

` cd ~/Android/Sdk/tools `
` ./android `

Sdk manager dialog box opened up. Just select and install the SDK tools you require. 
![SDK Manager]({{ site.url }}/images/sdkManager.png)

It is showing status installed in this screenshot as I just installed Android API 23.

### Connect your phone before running the app again.###

1. Connect your android device to your computer through USB.  

2. Enable the USB debugging from Developer options settings into your android device. On Android 4.2 and higher, the Developer options screen is hidden by default. To make it visible, go to Settings > About phone and tap Build number seven times. Return to the previous screen to find Developer options at the bottom.

(At my phone Xiaomi Redmi Note 3, nothing happened by tapping on Build Number seven times, after few searches, I came to know how to get to Developers options. Go to Settings > About phone and tap MIUI version seven times. Go to Settings > Additional Settings and you will find Developers Options. Open it and Enable USB debugging.)
Found this from http://xiaomiadvices.com/miui-7-enable-developer-options-and-usb-debugging-on-xiaomi-android-phones/

If you're developing on Ubuntu Linux, you need to add a udev rules file that contains a USB configuration for each type of device you want to use for development. In the rules file, each device manufacturer is identified by a unique vendor ID, as specified by the ATTR{idVendor} property.
Log in as root and create this file: /etc/udev/rules.d/51-android.rules.

` sudo vim /etc/udev/rules.d/51-android.rules `

Use this format to add each vendor to the file:

`SUBSYSTEM=="usb", ATTR{idVendor}=="2717", MODE="0666", GROUP="plugdev" `
2717 is the vendorID of XIAOMI, you can search vendorID of your device online easily. 

Now execute:
` sudo chmod a+r /etc/udev/rules.d/51-android.rules `

Now run the app, Go to your project
` cd piaoma `
` meteor run android-device `

This will install and run your app into your android device.

Thank you :)









