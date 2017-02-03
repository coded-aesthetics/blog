---
layout: post
title: MusiCookie - A portable music player operated by NFC tags
---

<div class="message">
  This article will show you how to make your own portable music player that is operated by NFC tags. 
  While the player presented here is designed for children, it can easily be adapted 
  to make e.g. a music player to hook up to your car's stereo.
</div>

### MusiCookie

This is the device. The Rasberry PI has been mounted in such a way that it protrudes out of the balsa wood top for better NFC reception. 

![MusicCookie]({{ site.url }}/assets/musicookie/musicookie.jpg)

It is operated by these balsa wood figures that have an [NFC sticker](https://www.amazon.de/Tags-Sticker-NTAG213-Circus-168Byte/dp/B00BTKAI7U/ref=sr_1_4?ie=UTF8&qid=1478949107&sr=8-4&keywords=nfc+tags) on the backside.

![MusicCookie]({{ site.url }}/assets/musicookie/cookies-both-sides.jpg)

To play a song, you simply need to place one of the figures on the Raspberry PI. 

![MusicCookie]({{ site.url }}/assets/musicookie/musicookie-play.jpg)

### The interiour

This is what the MusiCookie-box looks like on the inside. There is the Raspi with the SD card holding the Raspian OS (Jessie) and music-files. 
The Raspberry PI gets its power through a smartphone charger battery-pack, that is connected via micro USB cable. Sound is played through a little active bathroom speaker.  

![MusicCookie]({{ site.url }}/assets/musicookie/innenleben.jpg)

### The components

![MusicCookie]({{ site.url }}/assets/musicookie/components.jpg)

Computer: [Raspberry PI Model 1 B](https://www.raspberrypi.org/products/model-b/)   
NFC module: [ExploreNFC by NXP](http://www.exp-tech.de/en/nxp-explore-nfc-fuer-raspberry-pi?___from_store=de)   
Casing: [PiBow](http://www.avc-shop.de/epages/64272905.sf/de_DE/?ObjectPath=/Shops/64272905/Products/PiBow)   
Speakers: [HAMA "Pocket" blue](https://www.hama.com/00139602/hama-pocket-mobile-speaker-blue)   
Power supply: [AKTronic 2600mAh Smartphone charger](https://www.otto.de/p/ak-tronic-powerbank-2-600-mah-567325052/#variationId=-28974452)   


Note that there is no need to use the exact same components that I used. 
To successfully build the MusiCookie as described in this tutorial however, at least the NFC module has to be the one that is used here.

### Software installation

#### Prerequisites

You need to have an SD card with an installation of **Raspian Jessie Lite**.   
All files and instructions can be found here: [https://www.raspberrypi.org/downloads/raspbian/](https://www.raspberrypi.org/downloads/raspbian/)

#### Install Explore NFC drivers
[Download the driver files here](https://www.nxp.com/webapp/sps/download/license.jsp?colCode=SW282816&appType=file1&location=null&DOWNLOAD_ID=null)
and install as described in this document: [http://www.nxp.com/documents/application_note/AN11480.pdf](http://www.nxp.com/documents/application_note/AN11480.pdf)

#### Download and install libraries

libvlc
```shell
sudo apt-get update   
sudo apt-get upgrade   
sudo apt-get install vlc libvlc-dev   
```

and libglib
```shell
sudo apt-get install libglib2.0-dev
```

#### Clone the musicookie repo
First, you need to install git:   
```shell
sudo apt-get install git
```
Then go to the home directory of the pi user and clone the repository like so:
```shell
cd /home/pi
git clone https://github.com/coded-aesthetics/musicookie.git
```
Change to the newly created folder and install the missing packages:
```shell
cd musicookie
sudo dpkg -i libneardal0_0.14.3-1_armhf.deb libwiringpi2-2.25-1_armhf.deb libneardal-dev_0.14.3-1_armhf.deb neard-explorenfc_1.2-1_armhf.deb
```

#### Create songs folder

```shell
mkdir /home/pi/songs
```

#### Testdrive

To run the software and see if everything works, type in the following:  
```shell
cd /home/pi/musicookie/neard-explorenfc-1.2
./go.sh
```
Now you should see the output `Waiting for tag or device...`  
Ctrl+C your way out of there. We first need a way to get our music files onto the Raspi.

#### Install FTP-server
In order to get songs onto the PI, we need to install an FTP server.  
The folder that holds the files is hardcoded as /home/pi/songs.  
Make sure to exchange any usage of /home/pi/FTP by /home/pi/songs in the following step-by-step guide:  
[https://www.raspberrypi.org/documentation/remote-access/ftp.md](https://www.raspberrypi.org/documentation/remote-access/ftp.md)

Now you can use your favorite FTP-client program to upload files to the PI.  

#### Coding the NFC tags

With the help of the smartphone app [TagWriter by NXP](https://play.google.com/store/apps/details?id=com.nxp.nfc.tagwriter&hl=de) you can store the name of the mp3-files on the NFC tags.
The type of the entry needs to be 'text' and simply contain the name of the mp3 (complete with .mp3 suffix), as stored in the /home/pi/songs folder.   
So, in the main menu of the TagWriter app, choose: `Write -> New dataset -> Text`

### Configure the musicookie software to automatically start after bootup

and also add a little energy saving trick which turns off the HDMI port.
To do so, go to the /home/pi directory and append the following lines to .bash_profile 
    
    /opt/vc/bin/tvservice -o
    
    cd musicookie/neard-explorenfc-1.2/
    ./go.sh

### Configure the PI to login on boot

```
sudo raspi-config
```
By typing this, you get into the raspberry configuration tools.   
Press `"3 Boot Options"` then `"B1 Desktop / CLI"` followed by `"B2 Console / Autologin"`, save and reboot the raspi by typing:
```
shutdown -r now
```

### You should be good to go

If you are having trouble with any of the above steps, or noticed errors feel free to write me an email to jan@coded-aesthetics.com.