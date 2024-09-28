# PCTipsandInfo
Interesting and helpful info on various topics

# Restore old Right-click Context menu in Windows 11
Restore the old Context Menu in Windows 11



Right-click the Start button and choose Windows Terminal.

Copy the command from below, paste it into Windows Terminal Window, and press enter.

reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

Restart File Explorer or your computer for the changes to take effect.

You would see the Legacy Right Click Context menu by default.



![image](https://github.com/user-attachments/assets/5bf3ef0e-1864-4d48-8f18-010ccdcf2167)


Command in Windows Terminal to Restore old context menu 



The Registry change masks the new COM object that executes the compact menus with the "Show more options" entry. Once you get this performed, Explorer reverts to the Legacy context menu. 




# Restore Modern Context menus in Windows 11



To undo this change, in a Terminal Window, execute this command:

reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f



Restart the File Explorer or Computer for the changes to take effect.


These steps can help you to enable the old context menu in Windows 11.
