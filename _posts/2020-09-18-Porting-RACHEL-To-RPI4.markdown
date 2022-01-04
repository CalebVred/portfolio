---
title: Porting RACHEL to RPI4
layout: post
date: 2020-09-18 11:20:00
author: Caleb Vredevoogd
tags: project
comments: true
---

# Porting RACHEL to Raspberry Pi 4

Since this past summer I have been working on porting the educational software RACHEL (Remote Access Community Hotspot for Education and Learning) to the Raspberry Pi 4. Professor Derek Schuurman, A professor of mine introduced me to the project when I was asking him about something else Raspberry Pi-related. It seemed like a fun challenge, so I went with it.

A little background on RACHEL PI itself: RACHEL is a project started by the foundation Worldpossible in order to "...ensure that anyone can access the best educational resources from the web anytime, anywhere, regardless of internet connection". RACHEL is a web front-end that runs on a machine configured to be a server (like a Raspberry Pi, for instance). Through this front end RACHEL can provide a wide variety of individually-installed modules that  provide the educational content. Such modules include an offline version of Wikipedia, Khan Academy and the Gutenberg Project among others. This all can then be accessed by a student through a web browser running on a connected computer.

One example of its use is in the Calvin University Computing Department's mission trip to Zambia. While they were there they fitted out 6 computer labs with Raspberry Pis including a RACHEL PI server.

As of right now RACHEL can work just fine on the Raspberry Pi 3, but not the 3B+ or any of the later Pi models. The thing is you can buy a Raspberry Pi 4 for the same $35 price and get faster internet (wired and wireless) and twice the RAM among other hardware and software improvements. Then there's the fact that the Raspberry Pi 3 will eventually be discontinued. Either way, even if we aren't able to take advantage of all the Pi 4's capabilities, it's important to be compatible with current hardware if we want a current solution for education.

Professor Schuurman wanted me to get the RACHEL front-end fully functioning on the Raspberry Pi 4. However, on top of that he wanted me to also write out easy to understand step-by-step instructions so that somebody could manually install RACHEL on a fresh image of Raspberry Pi OS. This involved setting up four main parts: a wireless access point to connect with a student computer; a LAMP web server to run the RACHEL front end; the RACHEL front end itself to hold the modules and last but not least the educational modules themselves.

We sourced our instructions from various tutorials around the web as well as the original RACHEL code for reference on what libraries and dependencies were needed. Speaking of which: in that source code we found a handy python installation script which automated the setup. We decided to write our own imitation of this.

I was working only part time on this project but by late July we got a Raspberry Pi 4 up and running RACHEL just by running our installation script.
