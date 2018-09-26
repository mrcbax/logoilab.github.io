---
layout: post
title: DyingLight: Software and Hardware to Bring Back Brightness Functionality of MacBooks.
author: Chad Baxter
date: 2018-09-24
tags: ["MacBook", "Brightness", "dGPU", "Hardware", "Mod", "gMux", "os x", "ATTiny85"]
---

# DyingLight: Software and Hardware to Bring Back Brightness Functionality of MacBooks.

## Introdu​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ction

## Why

## Hardware
<div style="display: block; margin-left: auto; margin-right: auto; text-align: center;">
<img src="assets/img/pcb-brd.svg" height="25%" width="25%">
<br>
<strong>The Mk.I DyingLight PCB</strong>
<p>Actual size: 24mmx25mm</p>
</div>

<!--Purchase Links-->

## Softw​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿are

### Requirements

#### _OS X_

Just install the driver it's all good!

<hr>

#### _Windows 7/8/10_

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
#### _Linux_

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

Log out and log back in and you should be ready to go.

### <strong>_Downlo​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿ads_</strong>

[Win​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿dows 64-bit](downloads/x86_64-pc-windows-gnu-DyingLight.zip)

[Li​﻿​﻿﻿​﻿﻿﻿​​​​﻿​﻿​​﻿﻿﻿﻿​​​​﻿﻿​​​﻿﻿​﻿﻿​﻿﻿﻿​﻿​​﻿​﻿​﻿​​﻿﻿​﻿​﻿​﻿﻿﻿​﻿﻿​​​﻿﻿​﻿﻿﻿﻿﻿​﻿﻿​​​​​﻿​​﻿​​﻿​﻿﻿﻿﻿﻿nux 64-bit](downloads/x86_64-unknown-linux-gnu-DyingLight.zip)
