---
title: Spoofing Virtual Hosts for Fun and Profit
description: What to do with that deanonymized IP of a CloudFlare protected server.
published_date: "2021-05-11 05:40:00 +0000"
layout: default.liquid
is_draft: false

---
## Or: What to do with that deanonymized IP of a CloudFlare protected server.

## Introduction

CloudFlare is a security focused HTTP proxy. It protects the real IP address of a webserver by sitting between it and the outside world. When configured correctly an HTTP server behind CloudFlare should be inaccessible via any route other than CloudFlare.

The most important part of utilizing CloudFlare is to ensure the direct IP address has never been associated with the domain you wish to protect. Often times CloudFlare is added after an attack, and pointed to the direct IP address which has been associated with the original domain for quite some time. A well known way of finding the direct IP of a CloudFlare protected site is to use historic DNS lookup services like [DNSTrails](https://securitytrails.com/dns-trails).

The second most important part of this configuration is setting up virtual hosts and firewall rules to block direct IP access. Often times virtual hosts are created to handle this properly but firewall rules are too annoying or hard for server operators to implement properly. In this post we will utilize these two issues to bypass CloudFlare and connect to a CloudFlare protected HTTP server as if CloudFlare doesn't exist.

## Getting Started

You will need two basic bits of data to accomplish this task.

1. The direct IP of the HTTP server (obtained via historic records or other means)
2. The domain associated with this IP address.

## The Basics

This is a simple attack requiring a single HTTP header spoof. Your system must be set up to pass the correct `Host` HTTP header to trigger the correct match in either the Apache or NGINX target server's virtual host routes.

Let's say you have the IP address `123.123.123.0` and the domain `somedomain.tld` the target server has a virtual host set up for both the IP address and the domain name. The domain name routes to the normal page that is behind CloudFlare, the direct IP routes to a blank page or some other page. Attempting to access the IP address gives you the blank page when you want the page served for the domain name.

In order to trick Apache or NGINX into displaying the protected page simply set the `Host` header on your request like so:

```
Host: somedomain.tld
```

## In Practice

Here are some examples of the simplest way to do this with your system or tool of choice.

### Linux

Edit `/etc/hosts` and add the domain and IP address like so (edit to match your use case):

```
# /etc/hosts
123.123.123.0 somedomain.tld
```

After a reboot any request to the specified domain will be resolved to the listed IP and contain the proper `Host` header.

### Windows

Open `C:\Windows\System32\drivers\etc\hosts` as Administrator and add the following line (edit to match your use case):

```
123.123.123.0 somedomain.tld
```

After a reboot any request to the specified domain will be resolved to the listed IP and contain the proper `Host` header.

### curl

Simply start your curl command like this (edit to match your use case):

```
curl curl -H "Host: somedomain.tld" http://123.123.123.0/
```

## Conclusion

Once the `Host` header matches, and if firewall rules have not been configured properly on the target, you should see the CloudFlare protected page in the response from your request. This time though, it was loaded directly, bypassing CloudFlare completely.
