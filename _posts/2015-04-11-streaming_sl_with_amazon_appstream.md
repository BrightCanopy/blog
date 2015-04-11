---
layout: post
title: Notes on Streaming SL wht Amazon AppStream
---

I'm in a hotel room in Reno for a conference, but I'm grabbing what time I can to do some quick proof of concept stuff.

I setup a stream with the Firestorm and was able to use it from both a Chromebook and an Android phone. It was really very responsive over a hotel wifi network, but there are many caveats.

tl;dr:  It works, but it's expensive and nowhere near being useful for just casually streaming SL without some custom client development and viewer integration.

## Observations (in rough chronological order)

 * Created a development (StandAloneStack) AppStream instance, but didn't find an easy way to really use it with the clients.
 * Created a regular AppStream instead.
 * Only two AWS regions supported (East-1 and Tokyo)
 * Form for the cloud formation template was very rudimentary with no lookups for things like keypairs etc.
 * Taking a very long time to come up: started at 9:36 - 9:51
 * Now there's a message: "It can take from 30 minutes to several hours to deploy your application for streaming, depending on its size. In the meantime, you can leave this page and the deployment will continue."
 * Took 30 minutes.
 * Creates an AMI for the application
 * Application ID is long and unfriendly
 * Firestorm complains that the system does not meet minimum requirements.
 * Testing with a Chromebook client works with maximum graphics settings, not sure about all of the shaders though.
 * Mouselook is erratic and Esc and Alt seem to be bound to shortcuts.
 * No sound of any kind on Chromebook
 * Exiting the the viewer crashed the example chrome client. 
 * Loaded the Andriod client and tested on a Samsung S4
 * No mobile friendly controls obviously, but hacker keyboard arrows work.
 * Maximum graphics settings work.
 * No sound here either.
 * Unable to zoom and all text so small as to be nearly unreadable.
 * Fat-fingered go back killed the session.
 * Didn't have a chance to try chattng, but it would have been painful.
 * Pricing is $0.83USD/hr per user session with a starting limit of ten simultaneous users. Extending the limit is possible, but Amazon wants to know how many users you want to be able to support. There's no automatic scaling.


## Initial Questions

 * Q: Will it take 30 minutes to an hour to deploy upgraded apps?
 * Q: How to observe the applictation launch process for debugging?
 * Q: How to gather application logs? (Found a partial answer, but unresolved)
 * Q: How to detect and recover from application crashes?
 * Q: How much cheaper are reserved streams.
 * Q: What will it take to just replace this with dedicated hardware.

## Conclsions

 * AppStream might work for prototyping, but it looks too expensive to work as a permanent solution. It will be worth exploring just building our own h.264 or even V9 streaming cluster. 


## Follow-Up

  * For completeness sake, I'll dig deeper and start prototyping a new intergrated client, probably on Chrome or Linux first for convenience. These will be [open source at Github](https://github.com/BrightCanopy) assuming the other licensing allows it.

More to come.