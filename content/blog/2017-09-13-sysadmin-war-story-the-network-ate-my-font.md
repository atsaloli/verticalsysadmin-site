---
title: "Sysadmin War Story: \"The Network Ate My Font!\""
date: 2017-09-13
author: "Aleksey Tsalolikhin"
---

Finance offices in Toronto and Hollywood were printing checks to separate printers. Toronto produced correct [MICR (Magnetic Ink Character Recognition)](https://en.wikipedia.org/wiki/Magnetic_ink_character_recognition) font; Hollywood printed those same numbers in regular font. The finance team blamed the network for "eating" the MICR font.

The author captured PostScript data via tcpdump and found the PostScript referenced the font without embedding it. The check editor had an "encapsulate fonts" checkbox that was unchecked. The Hollywood printer had cached the font from earlier check images that did include it. When Toronto's printer was rebooted for maintenance, its font cache cleared — revealing the underlying problem.

Fix: enable the "include fonts" checkbox in the check template editor.

Presented at [USENIX LISA](https://www.usenix.org/conference/lisa17).
