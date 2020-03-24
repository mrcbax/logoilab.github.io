---
layout: post
title: DeMux: MuxHat in software form
author: Chad Baxter
date: 2018-09-17
tags: ["MacBook", "dGPU", "Hardware", "Mod", "gMux", "os x", "Graphics"]
---
<meta http-equiv="refresh" content="0; url=https://doslabelectronics.com/Demux.html" />
# [An important update regarding mail-ins and NCOVID-19](https://doslabelectronics.com/announcements.html)

# DeMux: MuxHat in software form

<script src="https://embed.selly.gg"></script>
<script>
function onload() {
var button = document.getElementsByClassName("uc_yv");
var exit_button = document.getElementsByClassName("selly-close");
if(exit_button[0].addEventListener) {
exit_button[0].addEventListener("click", function() {ga('send', 'event', 'purchases', 'purchase_canceled', 'demux', 20);});
} else {
exit_button[0].attachEvent("click", function() {ga('send', 'event', 'purchases', 'purchase_canceled', 'demux', 20);});
};
if(button[0].addEventListener) {
button[0].addEventListener("click", function() {ga('send', 'event', 'purchases', 'purchase_clicked', 'demux', 20);});
} else {
button[0].attachEvent("click", function() {ga('send', 'event', 'purchases', 'purchase_clicked', 'demux', 20);});
};
};
window.onload = onload;
</script>

DosLab Electronics is p​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿roud to announce that DeMux is ready for release. Below, you will find details on how to use it to flash the gMux IC on your MacBook Pro logic board.

## Please read this page in its entirety before purchasing to understand what is required.

# We are accepting mail-ins! The base rate is $60+SH for a flash. Only $40+SH if you already bought a key. Please email us at doslabelectronics@gmail.com if you would like to do a mail-in.

If you have already got everything set up, you can <button data-selly-product="d97a35a0" onclick="ga('send', 'event', 'purchases', 'initiate_buy', 'demux', 0)">Purchase A License Key</button><a name="purchase"></a> (If you would like to do a bulk order please contact us before purchasing, we may be able to give you a discount.)

Questions, comments, and concerns can b​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿e forwarded to the [DosLab Electronics email](mailto:doslabelectronics@gmail.com)

## Important notes

### For those with repeated failed flashes. We have determined the cause to be noise on the `TCK` line. This can be fixed by adding a 100pF capacitor between `TCK` and ground(`GND`).

### If the above fix still isn't working for you, you can temporarily remove `L2406` before flashing. Make sure to solder it back on when you are done flashing.

If you are getting errors saying a DLL is missing please install the following Microsoft Redistributable:

[Microsoft Visual C++ 2012 Rev4](https://www.microsoft.com/en-us/download/details.aspx?id=30679)

Please make sure you are installing the 64-bit ve​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿rsion by selecting it in the menu that comes up when you click "Download".

DisplayPort is a functionality of the dedicated GPU only, disabling the dedicated GPU will also disable the DisplayPort.

Backlight brightness is currently not supported by Demux. We will be releasing a software fix for this at a later date.

## Table of contents

- [Preparation](#prep)
- [Installing the software](#software)
  - [Downloads](#download)
  - [Drivers](#drivers)
  - [License keys](#licensing)
  - [DeMux client](#client)
- [Preparing your programmer](#programmer)
  - [Soldering](#solder)
  - [No soldering](#nsolder)
- [Flashing](#flashing)

## Preparation<a name="prep"></a>

To get started, you'll need the following:

- A Lattice HW-USBN-2A ICSP FPGA Programm​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿er (you can get one cheaply [here](https://cpcde.page.link/axst))
- Wires and connector to connect from the Lattice programmer to the MacBook logic board.
- A copy of the DeMux flashing software

## Installing the software<a name="software"></a>

Installing the software comes in three steps. Fir​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿st, download the package, and extract it. You should then connect your programmer and install the programmer drivers. After this is done, you can purchase a flash license from us and use it with the DeMux utility to flash your gMux IC. These steps are covered in further detail below.

### Downloads<a name="download"></a>

A 64 Bit Windows system is required to use DeMux.

Download the following package:

[Windows 64-bit](https://cpcde.page.link/Aj4R) PGP signature: [here](https://computeco.de/well-known/demux.zip.sig) [![PGP 0xDEBECAEE](https://peegeepee.com/badge/orange/DEBECAEE.svg)](https://peegeepee.com/DEBECAEE)

SHA256: *2fa7064168d9aebb9eb169e4d0818705d3b645ae8c04df15b7414e17a1f367fe*

Once the package is downloaded, go ahe​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ad an extract it somewhere safe. You are now ready for the next step.

### Drivers<a name="drivers"></a>

Once the package has been extracted, plug your Latt​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ice HW-USBN-2A ICSP programmer into a USB port on your computer. Then, open the driver installer executable, and use it to install the USB driver. The program will tell you if it was successful.

### License keys<a name="licensing"></a>

If you don't yet have a license key, yo​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿u'll need to [purchase one](#purchase). Keys cost $20 each, and are good for one gMux IC flash. Once purchased, save the key in a safe place, as it will be needed later. (If you would like to do a bulk order please contact us before purchasing, we may be able to give you a discount.)


### DeMux client<a name="client"></a>

Next, open up the DeMux flashing application. Here, you wi​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ll need to enter the license key you purchased. If it's a valid key, the program will indicate so. Once the license has been verified as valid, you can proceed to the next steps.

- Please note that once a license key is verified as valid on one machine, it CANNOT be used on another.

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/demux_util.png"><img src="assets/img/demux_util.png" height="35%" width="35%">
<br>
<strong>The DeMux utility ready to flash.</strong></a>
<br>
</div>

<br>

## Preparing your programmer<a name="programmer"></a>

In order to prepare the hardware for gMux flashing, you will ne​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ed to correctly connect your Lattice programmer to the gMux IC JTAG header of your MacBook logic board. This will require either soldering wires to each pad of the header, or using our custom pogo-pin solderless connector (coming soon).

When soldering the wires on a 15" board, please be sure to route them away from or around the large black inductor, located just to the right of the JTAG header. This inductor will interfere with the data lines if they are routed overtop of it. This leads to a failed flash.

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/programmer-min.png"><img src="assets/img/programmer-min.png" height="30%" width="30%">
<br>
<strong>The Lattice programmer ready to go.</strong></a>
<br>
</div>

<br>

### Soldering<a name="solder"></a>

#### Important note: Only use a temperature controlled soldering iron or you WILL remove pads which are required for the flash to work. Most of the pads are ONLY available in this ONE place. The loss of a pad will PERMANENTLY ruin your ability repair the board.

To solder the JTAG wires to the logic board, start by tin​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ning each of the 6 header pads with fresh solder. Then, strip and tin 6 wires that you can connect to your Lattice programmer. Solder each wire to the respective pin, as shown in the diagrams below:

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/15in-min.png"><img src="assets/img/15in-min.png" height="30%" width="30%">
<br>
<strong>15" Board (820-2915)</strong></a>
<br>
</div>

<br>

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/17in-min.png"><img src="assets/img/17in-min.png" height="30%" width="30%">
<br>
<strong>17" Board (820-2914)</strong></a>
<br>
</div>

<br>

There is now a video detailing these steps available:

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/lJUyOysbl08" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>
### No soldering<a name="nsolder"></a>

#### We are selling the adapter in limited quantities as a pre-release to high volume customers only. You must meet the following requirements to be able to purchase:

- Flash a minimum of 25 machines a month.
- Are a repair shop of some kind.
- Will continue to have a use for the adapter after its initial use.

No other customers will be considered at this time.

## Flashing<a name="flashing"></a>

Lastly, once your Lattice programmer is properly connected to the l​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ogic board, and you have a valid license entered in the DeMux flashing utility, you are ready to proceed with flashing. To flash, perform the following steps:
- Apply power to the logic board. To do so, simply conne​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ct the machine to power, and turn it on. It is recommended that you disconnect all hard disks during this process, to prevent the machine from booting into an OS. When the machine is powered on, the status LED on your Lattice programmer will turn from amber to green.
- Once the LED is stable solid green, you are rea​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿dy to press the "FLASH GMUX" button in the DeMux flashing utility. This process will take a bit to complete, so be patient.
- Do NOT disconnect the Lattice programmer, close the DeMux flas​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿hing utility, or power off the machine during this process.
- If the process fails, check your JTAG connections and try ag​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿​﻿﻿﻿﻿​﻿﻿﻿​﻿﻿​​﻿​﻿﻿​​﻿ain. If successful, turn the machine off and back on, and you should now be running only off Intel HD Graphics, indicating that the DeMux firmware was flashed successfully.
