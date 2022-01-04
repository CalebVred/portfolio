---
title: Good Morning From Raspberry Pi Part 1 - Alarm and Message Reading
layout: post
date: 2021-11-01 11:00:00
author: Caleb Vredevoogd
tags: project
comments: true
---

# Good Morning!

I've decided to create a "smart" alarm clock using a Raspberry Pi. I want an alarm clock system that isn't my phone and something that can present me with news updates without the tempting links found on an email news feed, website, etc.

I've decided to use Python because it can work on a number of devices, namely a Raspberry Pi as well as my laptop for writing and testing. It's also high-level enough that I can find a text-to-speech library as well as any APIs I might need to read data from news sources.



Here's the base code for a talking clock script. No alarm function yet, just a TTS library saying the current date and time.

```
import pyttsx3
import time


def main():

    engine = pyttsx3.init()
    engine.say("Good morning")
    engine.say("It is ")
    engine.say(time_to_string())
    #Any additional info gets passed in as a string to engine.say() here
    engine.runAndWait()
    engine.stop()

'''
time_to_string()
@output: t_string - The string representation of the current date and time.
'''
def time_to_string():

    t_string = ""

    seconds = time.time()
    local_time = time.localtime(seconds)
    dotw = local_time.tm_wday
    dotw_str = ""
    if(dotw == 6):
        dotw_str = "Sunday"
    elif(dotw == 0):
        dotw_str = "Monday"
    elif(dotw == 1):
        dotw_str = "Tuesday"
    elif(dotw == 2):
        dotw_str = "Wednesday"
    elif(dotw == 3):
        dotw_str = "Thursday"
    elif(dotw == 4):
        dotw_str = "Friday"
    elif(dotw == 5):
        dotw_str = "Saturday"

    t_string += dotw_str
    t_string += ", "

    month = local_time.tm_mon
    month_str = ""
    if(month == 1):
        month_str = "January"
    elif(month == 2):
        month_str = "February"
    elif(month == 3):
        month_str = "March"
    elif(month == 4):
        month_str = "April"
    elif(month == 5):
        month_str = "May"
    elif(month == 6):
        month_str = "June"
    elif(month == 7):
        month_str = "July"
    elif(month == 8):
        month_str = "August"
    elif(month == 9):
        month_str = "September"
    elif(month == 10):
        month_str = "October"
    elif(month == 11):
        month_str = "November"
    elif(month == 12):
        month_str = "December"

    t_string += month_str
    t_string += " "

    dotm = local_time.tm_mday
    t_string += str(dotm)
    t_string += " "

    hour = local_time.tm_hour
    meridian = ""
    if hour > 12:
        meridian = "PM"
    else:
        meridian = "AM"

    if hour != 12:
        hour = hour % 12

    t_string += str(hour)
    t_string += " "

    minute = local_time.tm_min
    if minute < 10:
        t_string += "o'"
    t_string += str(minute)
    t_string += " "

    t_string += meridian
    t_string += "."
    return t_string


main()
```

You can find the link to the project with some updated code [here](https://github.com/CalebVred/goodmorning).

What you'll find in the repo is a pretty simple alarm clock script. However, in order to change things, for now, at least, you have to stop the script, change hard-coded values and then restart. I want this to be running on a Raspberry Pi as its own independent appliance with a working user interface; the less I have to stop and open up the hood the better. I've been looking for solutions to change things using a webapp I could access from my phone. I think I've found [something](https://github.com/CorticoAI/raspberrypi-iot), but I'll save it for another post.
