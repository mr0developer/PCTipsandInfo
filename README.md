# PCTipsandInfo
Interesting and helpful info on various topics.
This list will be updated from time to time.

## Restore old Right-click Context menu in Windows 11
Restore the old Context Menu in Windows 11



Right-click the Start button and choose Windows Terminal.

Copy the command from below, paste it into Windows Terminal Window, and press enter.

reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

Restart File Explorer or your computer for the changes to take effect.

You would see the Legacy Right Click Context menu by default.



![image](https://github.com/user-attachments/assets/5bf3ef0e-1864-4d48-8f18-010ccdcf2167)


Command in Windows Terminal to Restore old context menu 



The Registry change masks the new COM object that executes the compact menus with the "Show more options" entry. Once you get this performed, Explorer reverts to the Legacy context menu. 




## Restore Modern Context menus in Windows 11



To undo this change, in a Terminal Window, execute this command:

reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f



Restart the File Explorer or Computer for the changes to take effect.


These steps can help you to enable the old context menu in Windows 11.

## Steps to fix unarc.dll error and error code - 11
Finally found a fix for Unarc Error Codes
Tried "every" bullshit advice on Youtube. Probably "25 different suggestions" and NONE work.
Everyone always comments right away "VCredist, bad ram stick, disable antivirus, page file size, clear temp folder, sfc scan checks" lolol the list goes on and on. That's not the fix for a lot of people.
Try this if you have the latest Intel gen processors and run into these Unarc error codes:

Set Power Plan in Windows to "Balanced"

Edit Power Plan --> Advanced Power Plan Options --> Processor Power Management --> maximum processor state at "99%

Open Msconfig --> boot --> Advanced Options --> Set cores to 6 - 8. (Depending on what processor you have)
I found the reason for Unarc error codes to pop up or BSOD when installing DODI/Fitgirl repack was because "the way these massive 50-100gb files have to be decompressed causing the processor to overheat at 95C Degrees" when monitoring HWInfo and therefore causing windows to throttle with error codes or BSODs. By Setting these 2 things, my CPU Temps stayed stable 60C Degrees thus not prompting any errors

## Is it possible to spoof user-agent and OS with Chrome?

You can change the User Agent string in Dev Tools:

Open Developer Tools (F12)
![image](https://github.com/user-attachments/assets/3ad81010-bd50-4d82-b825-a7a02bee8155)


Show the Console Drawer at the bottom by hitting Esc
![image](https://github.com/user-attachments/assets/68f036eb-c23f-4f39-86bb-47780f3d1c4a)


Add the Network Conditions tab to the drawer
![image](https://github.com/user-attachments/assets/cd22e85d-0cae-4d9b-8a16-2f89770c2691)


Under User Agent, uncheck "Select automatically", and pick a browser you wish to emulate or customize the string however you'd like
![image](https://github.com/user-attachments/assets/1639e539-de0c-4a1d-9b57-780983ec6359)


