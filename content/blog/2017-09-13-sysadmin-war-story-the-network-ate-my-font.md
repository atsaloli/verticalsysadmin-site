---
title: "Sysadmin war story: \"The network ate my font!\""
date: 2017-09-13
---

About 15 years ago, I was the only UNIX sys admin in a factory, and I was asked to help with a "network issue" which hit the Help Desk.

The problem, it was explained to me, was that the network was eating the [MICR](https://en.wikipedia.org/wiki/Magnetic_ink_character_recognition) font (Magnetic Ink Character Recognition -- machine-readable font) on the checks.

Look at the last line on the below check image for an example of MICR font.

![](https://devverticalsysadmin.wordpress.com/wp-content/uploads/2017/09/canadianchequesample.png?w=300)

Image credit: [Wikipedia](https://en.wikipedia.org/wiki/Magnetic_ink_character_recognition#/media/File:CanadianChequeSamplePAR.png)

The finance office was in Toronto and they were printing checks to printers in Toronto and in Hollywood, California. The checks were coming out OK in Toronto but in Hollywood the bank routing number and account number was printed in regular font instead of in MICR font. The Toronto printer was printing numbers in MICR.

I said there is no way the network is "eating" the MICR font. That's not how networks work! Show me the check. Sure enough, the account number and the routing number (and the check number) were all in regular font.

I asked the Toronto office to fax me the check printed there -- it had the MICR font. Same check, mind you!

I asked the guy responsible for maintaining the finance system if anything changed recently (as the problem had just started) and he was very sure there was no change. Real head-scratcher!

I ended up capturing the postscript of the check using tcpdump as it was printed from Toronto UNIX server (that was running the finance system) to the printer in Hollywood and poured over the dump.

What I found was that the postscript image was referencing a font but the font was not included into the image. So how did this ever work?

Digging into this a bit deeper with the finance tech guy, why, yes, there is a checkbox in the check editor for whether to encapsulate (bundle) the font in with the image and by default, every time you go in to edit the check, the box is unchecked!

However the last time the check image was edited was months ago. Why did it stop working only now? Any guesses?

Turns out the printer had a cache for fonts and was using the font cached from the earlier check image which included the font! Moreover, the Toronto and Hollywood offices were on a different printer maintenance schedule -- and as part of the maintenance the printers are rebooted which clears the font cache!

To confirm this, we rebooted the Toronto printer and it stopped printing the MICR font on the check.

The resolution was to edit the check image and check the "include fonts" checkbox.

If you are in the San Francisco Bay Area next month, drop by the [USENIX LISA](https://www.usenix.org/conference/lisa17) conference next month, you can hear some great war stories there.

I'll be there to teach ["Setting up CI/CD pipelines"](https://www.usenix.org/conference/lisa17/training-program/session/setting-cicd-pipelines).
