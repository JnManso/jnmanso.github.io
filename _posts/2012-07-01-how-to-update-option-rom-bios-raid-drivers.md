---
title: How to update option rom / bios raid drivers.
date: 2012-07-01 21:33
category: 
author: 
tags: [bios, drivers, option rom, p5qle, raid]
summary: 
---

I have described below the steps I take to update my Option ROM on the motherboard P5QLE (I found these steps on <a href="http://vip.asus.com/forum/view.aspx?board_id=1&amp;model=Rampage+II+Gene&amp;id=20100221171206093&amp;page=3&amp;SLanguage=en-us">Asus forum</a>).

1. Get MMTool_3.22_Mod_21FiX
2. Open MMTool and "Load ROM" to open your BIOS ROM
3. Highlight the Option ROM (typically under the name column there will be "PCI Option ROM" and has a "RunLoc" of 8086:2822 for the ICH10). IF YOUR RUNLOC IS DIFFERENT LOCATE THE CORRECT ONE! 8086 means the manufacturer is Intel and 2822 means it is a ICH10 chipset ROM. For a list of Vendor and Device IDs goto www.pcidatabase.com
4. Once you have the CORRECT option ROM highlighted, select the "Replace" tab. (Do NOT delete and insert the updated ROM)
5. On the Replace tab, click Browse to find your updated Option Rom.
6. Once the correct ROM has been selected, click Replace.
7. Use "Save ROM as..." to make a new ROM file and keep your stock ROM intact.
8. Use the Asus EZ Flash 2 utility in your BIOS to update your Option ROM.

Note: You can download the latest Intel Raid Rom and Intel Rapid Storage Technology from <a href="http://forums.tweaktown.com">http://forums.tweaktown.com</a>
<p>WARRANTY!!</p>
![options](/assets/images/2012/07/works-on-my-machine-starburst_3.png)
<p> I AM NOT RESPONSIBLE IF YOU BRICK YOUR MOTHERBOARD!</p>
