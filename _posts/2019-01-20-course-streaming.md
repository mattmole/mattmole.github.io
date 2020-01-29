---
title: "Streaming, recording and creating remote training sessions"
excerpt: "Recording or streaming training sessions can be carried out with a mixture of OBS, NDI and various plugins..."
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - obs
  - streaming
  - edtech
  - hangouts
  - conferencing
---

**Please note, this post is rather text heavy. Hopefully following ones will have some images to make things as clear as possible**

The MAT that I work for offer out a large number of training courses. It is sometimes necessary to record these sessions where staff cannot attend or for QA purposes. Also, as the distance attendees travel increases, there are occasions where remote attendance would be useful.

# Setting the scene

Our training room consists of three large screens at the front of the room, a comfort monitor for the presenter and the usual tables and seating for the delegates.

We use a presenter PC for the presenter to be able to show their resources. I did not want the presenter to have to think about the recording / streaming software.

The second PC is used for recording / streaming.

The screens in the room are set up as follows. The comfort monitor is able to show either the presenter PC or the recording PC (more on this later). The centre screen at the front of the room is setup to show either the presenter resources or the recording PC (more on this later). The other two screens at the front of the room are setup to show presenter resources.

# The software and kit

* **A presenter PC** - I chose a refurbished HP800 Desktop with 4th gen Intel i7, 16GB RAM and a 240GB SSD
* **A recording PC** - I chose a refurbished HP800 Desktop with 4th gen Intel i7, 16GB RAM and a 240GB SSD. For this machine I opted for an NVidia 1050Ti graphics card as well
* **A boundary mic** - [Tascam TM-90](https://www.tascam.eu/en/tm-90bm.html)
* **Digital mixing desk** - I chose a [Behringer XR18](https://www.behringer.com/Categories/Behringer/Mixers/Digital/XR18/p/P0BI8) digital mixing desk
* The streaming software called [OBS](https://obsproject.com/)
* The software which can convert video / PC display output and transmit over the network, [NDI Tools](https://ndi.tv/tools/)
* Plugins for OBS to interface with [NDI](https://obsproject.com/forum/resources/obs-ndi-newtek-ndi%E2%84%A2-integration-into-obs-studio.528/), the Behringer mixing desk [ASIO](https://github.com/Andersama/obs-asio) and a [virtual webcam](https://obsproject.com/forum/resources/obs-virtualcam.539/) plugin
* [Logitech C930](https://www.logitech.com/en-gb/product/c930e-webcam) webcams

# Tying it all together

OBS running on the recording PC captures the following sources:

* The display of the presenter PC using NDI
* The two C930 webcams, connected to the recording PC via USB
* The output of the Behringer XR18 digital mixing desk using the ASIO plugin. 

We use a layout where the presenter (and audience if required) webcam is shown in the top left corner and then in a larger section in the bottom right we display the screen of the presenter PC.

With the setup as above, it is possible to stream sessions to a youtube channel or record the local harddrive on the PC or a NAS drive, perhaps.

By using the virtual webcam plugin, it is possible to output the video from OBS to video conferencing solution such as zoom, google hangouts meet or skype.

To be able to send audio across the video conference, then either the Behringer USB sound device could be selected in the conference settings.

A more flexible solution, allows any audio sources added to OBS to be sent across the conference. To accomplish this I use a second sound device on the PC, with the line out connected to the line in. I then use the advanced audio channels to output the required sources to this extra sound device. The loopback then provides an input device, which can be used.

# Even better if...

If I was to carry out this project again I would pick a slightly different webcam. I think that the Logitech C920 has a better lens for the purpose of capturing the video of the presenter. The C930 has a wider angle than the C920.

Should there be any issues capturing audio, the webcam mics could be used as backup audio. This can be enabled in OBS by using the advanced audio recording and selecting a codec which allows multiple tracks. These tracks can be selected in the advanced audio options.

# Issues worked out during the process / since completing the setup

* **Reverberation** - originally I used NDI to capture the audio from the recording PC. This caused issues with the boundary mic in the room also picking up the same audio. I looked at trying to use a side-chain effect to cut the boundary mic when the recording PC was playing, but decided against as sometimes people speak over backing audio. The simplest option was to stop capturing the audio from NDI and rely solely on the boundary mic.

* Another consideration I made for the cameras were unifi security cameras. I decided against these in the end due to the slight delay in getting the feed into OBS. This would then have caused issues with syncing the audio.