# Project-1
While learning to code on my HP ElteBook 840 G1 I realized that the home, page up, page down and end keys were driving me crazy.
I would constantly accidently hit one of them while reaching for other keys, sending me text flying all the way to the other side of the screen mid typing.
I thought of many ways to get rid of these keys such as physically taking out the buttons so I couldn't type them, downloading other people’s software to deal with the problem, but none of those solutions seemed okay with me. 
It was then I learned about scancode maps and after looking through I finally found a decent guide/explanation to them and made the changes manually.
Once that was done I figured since I went through the trouble of learning how to implement scancode maps into Windows, I might as well set that to be my first project and make a program to reassign keys based on user inputs.

And that’s basically it. 
If you don't want to use my program that’s understandable (I frankly didn't want to use others since the whole thing seems sketch), for those people I've unboringed a lot of other people’s explanations into just the things you need to know to get rid of those pesky keys.
look at my scancode table to know what to write, please bear in mind that table was made with UK keyboards in mind. US and other keyboards have some different keys, though most of them are the same.


Got to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout 
Make a binary value and call it "Scancode Map"
 
1 Key
00,00,00,00
00,00,00,00
01,00,00,00
??,??,??,??
00,00,00,00

in the "??,??,??,??" The first two sets are what you are re-mappng the keys to (00,00 if you want it to do nothing).
the second set is the key you are re-mapping

example: 1d,00,53,e0 This will re-map the delete key (53,e0) to the control key (1d,00).

Find a table online to know what value each key is. Restart computer when the change is made for it to take effect. 

To do multiple keys change the "1" in the third line the number of keys you want to change, 
then add another row of "??,??,??,??" for each key. example for 4 keys below.

4 Keys
00,00,00,00
00,00,00,00
04,00,00,00
??,??,??,??
??,??,??,??
??,??,??,??
??,??,??,??
00.00.00.00

etc  

Scancode for getting rid of pgup, pgdn, home and end. 

00,00,00,00,00,00,00,00,05,00,00,00,00,00,51,e0,00,00,49,e0,00,00,47,e0,00,00,4f,e0,00.00.00.00 <-- this is roughly what it should look like
