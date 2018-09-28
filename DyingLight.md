---
layout: post
title: DyingLight: Software and Hardware to Bring Back Brightness Functionality of MacBooks.
author: Chad Baxter
date: 2018-09-24
tags: ["MacBook", "Brightness", "dGPU", "Hardware", "Mod", "gMux", "os x", "ATTiny85", "Graphics"]
---

# DyingLight: Software and Hardware to Bring Back Brightness Functionality of MacBooks.

## Introdu​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ction

This project is the byproduct of a simple pr​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿oblem described over a late night burrito at Chipotle. DosDude1 _(Of High Sierra Patcher fame)_ had created a mod for MacBooks who's dedicated graphics chip had died. This mod allowed an owner to permanently bypass the dedicated graphics to use the integrated graphics instead. This was d​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿one by bypassing the graphics muxing chip on the mainboard of the machine. You can read more about it [here](https://cpcde.page.link/isR1) on his MacRumors post.

There was one slight problem. This mod required the owner to pass 3.3v to the backlight controller. This device, becau​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿se it takes a PWM signal would interpret the 3.3v as max brightness. This usually isn't an issue, until someone would like to use their MacBook in the dark.

Quite simply a solution to output the proper PWM signal to the backlight controller was nee​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ded. This was easy, until you factor in the fact that the user is going to want to control the backlight using the native controls on their system. DosDude and I began our deep dive into hardware modding taking on the concatenation of our usern​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ames _Dos_**Lab** as our psuedonym for this project. Below you will learn all about project **DyingLight** including how to use it to return your MacBook to almost-native glory.

##Table of contents
- [Hardware](#hardware)
  - [Overview](#hw_overview)
  - [Installation](#hw_install)
- [Software](#software)
  - [Requirements](#sw_reqs)
    -[OS X](#sw_reqs_osx)
    -[Windows](#sw_reqs_win)
    -[Linux](#sw_reqs_nix)
  - [Downloads](#downloads)

## Hardware<a name="hardware"></a>
<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<img src="assets/img/pcb-brd.svg" height="25%" width="25%">
<br>
<strong>The Mk.I DyingLight PCB</strong>
<br>
<p>Actual size: 24mmx25mm</p>
</div>

### Overview <a name="hw_overview"></a>

DyingLight is a simple USB v1.1 device that is solde​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿red onto an unused USB header on MacBook mainboards. It takes power from any 3.3v rail on the system and sits above the hard drive in the hard drive tray. The PWM signal line for the backlight controller requires that a 0Ohm resistor be removed at a specific point on the board. The signal line will be sold​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ered to the pad the 0Ohm resistor used to use. Once everything is wired up you're all set for first boot to install the drivers. The DyingLight chip defaults to full brightness on first boot enabling you to access the system to install the drivers. If all soldering jobs are done perfectly the backlight should come on immediately at boot.

### Installation <a name="hw_install"></a>

### <u>Warning: When following the install steps below please be ​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿sure to use insulated wire and pay attention to all steps of the process. Skipping a step or skimping on insulation like conformal coating or electrical tape wrappings may result in shorts on the board causing permanent damage to your system.</u>

<!--Purchase Links-->

## Softw​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿are <a name="software"></a>

### Requirements <a name="sw_reqs"></a>

#### _OS X_ <a name="sw_reqs_osx"></a>

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<img src="assets/img/osx_drv_0.png" height="35%" width="35%">
<br>
<strong>DyingLight device registered with OS X.</strong>
</div>

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<img src="assets/img/osx_drv_1.png" height="5%" width="5%">
<br>
<strong>Integrated manual slider.</strong>
</div>

<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<img src="assets/img/osx_drv_2.png" height="25%" width="25%">
<br>
<strong>Native-feel keyboard button support and feedback.</strong>
</div>

Just install the driver it's all good!

<hr>

#### _Windows 7/8/10_ <a name="sw_reqs_win"></a>

The driver is a command lin​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿e interface with flags that allow easy keybinding and startup entries.

The driver comes bundled with the libusb DLL files it requires, do not separate them.

```

DyingLight 0.2.1
LogoiLab:DosDude1
A utility to set the backli​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ght brightness of a system with the DyingLight mod installed.

USAGE:
    dyinglight [FLAGS] [OPTIONS]

FLAGS:
    -a, --align      Fixes brightness after a reb​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿oot. Should be called by a startup process
    -d, --down       Turns the brightness down one tick
    -h, --help       Prints help inform​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ation
    -u, --up         Turns the brightness up one tick
    -V, --version    Prints version information

OPTIONS:
    -s, --set <set>    <1-16>: Sets the brightness to a specific value
```
<hr>
#### _Linux_ <a name="sw_reqs_nix"></a>

The driver is a command li​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ne interface with flags that allow easy keybinding and startup entries.

There are a few things you must do to get the driver working for linux.

Install the `libusb` package.

_ArchLinux:_ `libusb`


_Ubuntu/Debian:_ `libusb-1.0-0-dev`

Then type the following comma​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿nd into your terminal:
```
sudo vim /etc/udev/rules.d/99-dying_light.rules
```

Then paste this into vim:
```
ACTION!="add|change", GOTO="dying_light_rules_end"
SUBSYSTEM!="usb|tty|hidraw", GOTO="dying_light_rules_end"

ATTRS{idVendor}=="fa11", ATTRS{idProduct}=="5afe", MODE="664", GROUP="plugdev"

LABEL="dying_light_rules_end"
```

Save your changes by hitting `esc` and typing `:wq`.

Type the following command:
```
sudo usermod -aG plugdev $USER
```

You may have to replace `$USER` with your username.

Log out and log b​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ack in and you should be ready to go.

### <strong>_Downlo​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ads_</strong> <a name="downloads"></a>

[MacOS X >= 10.6 Sn​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ow Leopard 64-bit](downloads/x86_64-apple-darwin-DyingLight.zip)

[Win​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿dows 7/8/10 64-bit](downloads/x86_64-pc-windows-gnu-DyingLight.zip)

[Li​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿nux 64-bit](downloads/x86_64-unknown-linux-gnu-DyingLight.zip)
