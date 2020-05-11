---
layout: blog
title:  "HelSec virtual meetup stream setup, part 1"
date:   2020-05-11 13:00:00 +0300
categories: blog
published: true
author: osku
author-link: https://twitter.com/oh2osq
---

Our first meetup was a success -- it seems the audience liked it, and
from my point of view, the stream setup was easy to use and we didn't
break it even once while the stream is running. Due to a few requests,
I'm documenting our setup so that others can build on it and host
their own virtual events with ease.

We couldn't have got this right the first time if not with the
valuable input from
[Dist](https://twitter.com/dist/),
[Jaroneko](https://twitter.com/jaroneko), and
[whois](https://twitter.com/JuhoJauhiainen), who had prior
experience in working with streams and setting up advanced features
and bots on a Discord server. (For me, this was my first time
streaming anything.)

The basic setup was:
`Zoom meeting --> OBS --> Twitch`
1. Speakers connected to a Zoom call and shared their screen and video
(whois and me were on the call too to host & stream it)
1. My streaming (=gaming) PC was running OBS. Said PC runs Windows 10.
1. OBS streamed to Twitch

User roles in the Zoom call:
* Whois acted as a meetup host
* Presenters did their thing
* I observed the Zoom call and streamed it, and admitted members
(presenters) prior to the zoom call being live on the stream

Let's look at these in detail.

## Zoom call setup

We got a paid Zoom account so that we can run meetings longer than the
40 minutes on the free version. We likely got other useful features as
well (I never hosted Zoom previously so I don't know). I scheduled a
basic Zoom meeting and sat on it with my streaming PC for the duration
of the stream, as did whois the meetup host. By default, Zoom places
call participants in a "waiting room" and can only be admitted to the
call by the call host -- so that while we were live with the stream,
none of us who had the call details could just accidentally crash in
the meeting.

## OBS setup

![OBS screenshot](assets/img/obs_screenshot_1.PNG)

The OBS setup was central to running the whole stream. It provided
content to the Twitch stream at all times. OBS has a concept called
"scenes". An OBS scene has a number of sources which it mixes into an
output. For example, the scene that had the presenter talking and
presenting slides, the scene contained the following sources:
* Window capture, from the Zoom window
* Audio output from my PC
* Static image source -- the layout that provided nice borders, the
HelSec logo, so that the basic Zoom window looked like a nice
HelSec-branded live presentation

We had a few other scenes as well:
* A few static images showing various messages, like: the
programme/schedule
* A screen showing "continuing soon" I could have
displayed if everything broke and would need some setting up again,
etc.
* A few alternative layouts (borders and HelSec logos) for the Zoom
call, if we wanted to present participant video without screen share
(we didn't)

We made switching screens quite simple. When a presentation was over,
I switched the current scene to show the meetup schedule (static
screen, no audio capture from the zoom call). Then, the new presenter
joined the Zoom call and started the screen share, so that the layout
within the Zoom call window matched the one layout we had to decorate
the content. Then, when the presenter and host (whois) were ready I
switched to the scene capturing Zoom window & audio. This was fully
manual of course and I only had to keep a close eye on the Zoom call
not breaking during presentations, and switching scenes between the
presentations (and admitting the new presenters to the call).

There were a few gotchas while setting up the scenes:
* The Zoom window needed to be fullscreen at all times. Also the Zoom
window has UI elements at the top and bottom edges of the screen that
we didn't want to include in the stream. To fix this, I added a
"Crop/Pad" filter to the Window Capture source.
* The OBS "Window capture" source didn't initially actually work and
only showed a black screen. The
Zoom application had an option in its Settings -> Advanced to switch
the rendering output mode into something that worked.
* Zoom audio didn't work initially either, that was due to my gaming
headset having two audio output devices (audio and "voice chat"), and
OBS actually captures audio from a specific audio device. Explicitly
telling Zoom to direct its output from the correct audio device fixed
this issue.
* I configured the source format for the OBS output to Twitch as
1920x1080. Also, both my screens on my gaming PC are 1920x1080. To
avoid weird upsampling / downsampling fuzziness in the video, I
virtually made the other screen with the fullscreen Zoom a higher
resolution. Luckily the Nvidia GPU had a setting to show a virtual
resolution than what the display actually had, and downsample on the
(physical) display. This enabled OBS to capture a screen area larger
than the OBS output, so that no upsampling occurred.

## Other notes

The reason everything worked smoothly during the stream was that we
actually tested and practiced everything before the actual event. We
developed and tested the setup with our stream task force whois, Dist,
and Jaroneko, and one of the presenters (joohoi) who happened to be
around, a few nights before the meetup. Then, one night before the
virtual meetup, I urged every presenter to do comms check with us when
we thought we had the stream setup done. I asked every presenter to
test screen share and video and do some talking while I took a local
recording (an OBS feature) and checked that audio and video did indeed
work nominally by checking the recording. (The local recording should
look like the actual stream output.) During the comms checks I also
tested the scene transitions. IMO doing a separate comms check is
absolutely necessary -- you all know how every zoom/Teams/google
hangout meeting always starts with the "can you hear me? It should
work? Oops I was on mute" and we didn't want that on a live stream.

Also, we had Q&A sessions after the presentations. We had a Discord
bot flagging and picking specially formatted questions from one text
chat into another. Then, at the end of each presentation, whois the
meetup host had all questions for the presenters nicely in one place
so that he could present the questions.

Finally, the afterparty was a blast! We couldn't do a virtual meetup
without an attempt to have a virtual afterparty -- a HelSec event
without an afterparty is like a keyboard without mechanical switches.

The Discord server we built for this and future HelSec events in
itself was an awesome setup built with love by members Dist and
Jaroneko and will be documented in a future post.

Contact us if you need help running your own virtual meetups!