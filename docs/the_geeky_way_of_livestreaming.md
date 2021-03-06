Imagine you find out about this world of video streaming to sites like Twitch.tv, Justin.tv and livestream.com. After browsing on these sites you obtain the urge to join this club. After getting to know the basics of streaming you try multiple tools, but to your demise none delivers the streaming output you want.

This tutorial is directed at Windows XP users.

Explanation of the Problem
--------------------------

Windows XP is seen as a dying platform that no publisher of expensive software wants to support anymore. For this reason, the Twitch.tv platform no longer offers support for Windows XP users. Tools like Open Broadcasting Software (OBS) depend on DirectX 10 and therefor Windows Vista and up. Without hardware support of a additional relay sound mix card, Windows XP users are faced with a very shocking problem: what broadcasting software can I use that I combine with which virtual sound card software?

### List of failed attempts

#### Streaming solutions

-   XSplit - any combination with this software fails flat out since extended audio preferences are unavailable under Windows XP, making live streaming to platforms like Twitch.tv or Justin.tv pointless due to missing audio; do not even try!
-   OBS - although an interesting piece of software that I gladly recommend to Windows Vista/7 users, it is incompatible to Windows XP and hence worthless

#### Virtual Sound Cards

-   Virtual Audio Cable (VAC) - this is an excellent piece of software that I recommend to buy if you lack a Windows 7 computer that has a Stereo Mix feature offered by its sound card, it is not even expensive! Since the reader of this article wants to find a solution for absolutely no cost: nope, annoying 'trial' woman voice
-   VB-audio cable - although this definately is a free software and supports audio transfer to a singular instance, it fails since multiple devices cannot listen to it.
-   REaudio - crashes when a device attempts to send audio to it
-   VAcard - very obscure driver that is not offered by its publisher anymore
-   Virtual Audio Streaming - is infected with the same 'trial' woman voice virus as Virtual Audio Cable is, and has less features than VAC, making it less valuable; turn to VAC instead if you need a professional solution

It is time to enter the scumbag world and delve into hack and slash installations! After all, we are living in a Windows world where applications are sold/distributed all over the Internet.

A working solution
------------------

There indeed is a working solution that gets you streaming your favorite videos, but it has its limitations. You can only stream to the livestream.com service. This service offers a “Livestream PROCASTER” software that is excellent for streaming your desktop, games and webcams. This is how you do it:

-   Register an account at [Livestream Original](http://livestream.com)
-   Download [Livestream PROCASTER](http://new.livestream.com/broadcast-live/encoder) and install it
-   Log into the program using the Livestream Original account and set it up (skip audio config for now)
-   Install the [AV Voice Changer Software 8.0 Diamond](http://www.audio4fun.com/voice-over.htm) for its audio mixing driver
-   Install [Virtual Audio Cable](http://software.muzychenko.net/eng/vac.htm) for its free and excellent audio repeater software
-   Return to the Livestream PROCASTER audio configurations and launch the audio mixer
-   Select **Avnex Virtual Audio Device** as the used audio device
-   Under Windows XP, go to System settings -&gt; Sound- and Audiodevices
-   Select **Avnex Virtual Audio Device** as your standard audio device
-   Restart all programs on your computer that are outputting audio, so they will use the new default audio device as output
-   Under Windows XP, go to Start -&gt; “All Programs” -&gt; Virtual Audio Cable, launch “Audio Repeater (MME)”
-   Under “Wave in” select **Avnex Virtual Audio Device** and under “Wave out” select your hardware sound card: hit Start.
-   (optional) Launch your favorite radio station to check if your sound works, if not check that you have performed the steps in this tutorial correctly
-   Click on the big, red “Go live” button in Livestream PROCASTER
-   Check that audio and video work by browsing and watching your stream in a browser

Success! By the end of this tutorial, you have a 'Stereo Mix'-like virtual sound card that is used to distribute sound output to your hardware and your streaming software. When you have finished streaming, you have to reset your default audio device (see Step 8/9) to your hardware soundcard. Each time you want to stream, you have to redo all steps beginning from Step 8.

The Limitations
---------------

-   You cannot manage scenes like in XSplit or OBS
-   You are limited to streaming to **livesteam.com**
-   Getting to start the stream is a complex task.

What can be said? It works!
