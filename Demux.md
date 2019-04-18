---
layout: post
title: DeMux: MuxHat in software form
author: Chad Baxter
date: 2018-09-17
tags: ["MacBook", "dGPU", "Hardware", "Mod", "gMux", "os x", "Graphics"]
---

# DeMux: MuxHat in software form

DosLab Electronics is proud to announce that DeMux is ready for release. Below, you will find details on how to use it to flash the gMux IC on your MacBook Pro logic board.

If you have already got everything set up, you can [purchase license keys here](https://selly.gg/p/d97a35a0).

Questions, comments, and concerns can be forwarded to the [DosLab Electronics email](mailto:doslabelectronics@gmail.com)

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

- A Lattice HW-USBN-2A ICSP FPGA Programmer (you can get one cheaply [here](https://cpcde.page.link/axst))
- Wires and connector to connect from the Lattice programmer to the MacBook logic board.
- A copy of the DeMux flashing software

## Installing the software<a name="software"></a>

Installing the software comes in three steps. First, download the package, and extract it. You should then connect your programmer and install the programmer drivers. After this is done, you can purchase a flash license from us and use it with the DeMux utility to flash your gMux IC. These steps are covered in further detail below.

### Downloads<a name="download"></a>

A 64 Bit Windows system is required to use DeMux.

Download the following package:

[Windows 64-bit](https://cpcde.page.link/Aj4R) PGP signature: [here](https://computeco.de/well-known/demux.zip.sig) [![PGP 0xDEBECAEE](https://peegeepee.com/badge/orange/DEBECAEE.svg)](https://peegeepee.com/DEBECAEE)

SHA256: *d2d3d09635d047d29dcf51bec412a527a047b801d26bf26f6a2fba57d3bdde67*

Once the package is downloaded, go ahead an extract it somewhere safe. You are now ready for the next step.

### Drivers<a name="drivers"></a>

Once the package has been extracted, plug your Lattice HW-USBN-2A ICSP programmer into a USB port on your computer. Then, open the driver installer executable, and use it to install the USB driver. The program will tell you if it was successful.

### License keys<a name="licensing"></a>

If you don't yet have a license key, you'll need to [purchase one](https://selly.gg/p/d97a35a0). Keys cost $20 each, and are good for one gMux IC flash. Once purchased, save the key in a safe place, as it will be needed later.

### DeMux client<a name="client"></a>

Next, open up the DeMux flashing application. Here, you will need to enter the license key you purchased. If it's a valid key, the program will indicate so. Once the license has been verified as valid, you can proceed to the next steps.

- Please note that once a license key is verified as valid on one machine, it CANNOT be used on another.

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/demux_util.png"><img src="assets/img/demux_util.png" height="35%" width="35%">
<br>
<strong>The DeMux utility ready to flash.</strong></a>
<br>
</div>

<br>

## Preparing your programmer<a name="programmer"></a>

In order to prepare the hardware for gMux flashing, you will need to correctly connect your Lattice programmer to the gMux IC JTAG header of your MacBook logic board. This will require either soldering wires to each pad of the header, or using our custom pogo-pin solderless connector (coming soon).

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<a href="assets/img/programmer-min.png"><img src="assets/img/programmer-min.png" height="30%" width="30%">
<br>
<strong>The Lattice programmer ready to go.</strong></a>
<br>
</div>

<br>

### Soldering<a name="solder"></a>

To solder the JTAG wires to the logic board, start by tinning each of the 6 header pads with fresh solder. Then, strip and tin 6 wires that you can connect to your Lattice programmer. Solder each wire to the respective pin, as shown in the diagrams below:

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

### No soldering<a name="nsolder"></a>

This option is coming soon. We will be providing pogo-pin based connector that allows for flashing of the gMux without the need for soldering.

## Flashing<a name="flashing"></a>

Lastly, once your Lattice programmer is properly connected to the logic board, and you have a valid license entered in the DeMux flashing utility, you are ready to proceed with flashing. To flash, perform the following steps:
- Apply power to the logic board. To do so, simply connect the machine to power, and turn it on. It is recommended that you disconnect all hard disks during this process, to prevent the machine from booting into an OS. When the machine is powered on, the status LED on your Lattice programmer will turn from amber to green.
- Once the LED is stable solid green, you are ready to press the "FLASH GMUX" button in the DeMux flashing utility. This process will take a bit to complete, so be patient.
- Do NOT disconnect the Lattice programmer, close the DeMux flashing utility, or power off the machine during this process.
- If the process fails, check your JTAG connections and try again. If successful, turn the machine off and back on, and you should now be running only off Intel HD Graphics, indicating that the DeMux firmware was flashed successfully.
