# PCTipsandInfo
Interesting and helpful info on various topics.
This list will be updated from time to time.

## Restore old Right-click Context menu in Windows 11
Restore the old Context Menu in Windows 11



Right-click the Start button and choose Windows Terminal.

Copy the command from below, paste it into Windows Terminal Window, and press enter.

reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve

Restart File Explorer or your computer for the changes to take effect.

You would see the Legacy Right click Context menu by default.



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


## How can I permanently disable Windows Update service and better control when Update is run?

### By modifying the group policy

Open "Start" Or open the Run app (win + R)

Search for gpedit.msc, then click on the top result to launch the local Group Policy Editor.

Navigation to the following path: Computer Configuration>Administrative Templates>Windows Components>Windows Update>Manage end user experience

Double click on the "Configure Automatic Update" policy on the right side.

Select the disable option to permanently turn off automatic updates on Windows 11.

Click the "Apply" button.

Click the "OK" button.

After completing these steps, Windows 11 will automatically stop downloading and installing updates.

OR

### By modifying the registry
Press Win+R to open the "Run" dialog box, enter regedit, and then press Enter to open the Windows Registry Editor.

Enter the following path in the address bar and press enter

HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows
![image](https://github.com/user-attachments/assets/ddb0e006-3787-44b8-a3f0-e982b09abeeb)
Right-click on the Windows folder and select New > Key.
![image](https://github.com/user-attachments/assets/0e331f4c-c162-42b4-9079-efc8534a0e66)
Rename the newly created key as WindowsUpdate and press enter to save.
![image](https://github.com/user-attachments/assets/1ff73105-c3f0-4452-aa52-519eb2dc1c56)
Now, right-click on the new WindowsUpdate folder and select New > Key again.
![image](https://github.com/user-attachments/assets/157adb6c-8956-438b-8d54-c5aebfab82b0)
Name the key AU.
![image](https://github.com/user-attachments/assets/38969ca0-2654-4b28-9035-6b8a0468614c)
Move your cursor to the adjacent panel, right-click anywhere, and select New followed by DWORD (32-bit) Value.
![image](https://github.com/user-attachments/assets/1250417a-888b-4058-845a-4569617837a2)
Rename the new DWORD Value as NoAutoUpdate.
![image](https://github.com/user-attachments/assets/8adaf0e4-aac9-4c4c-b196-7a48394a64d0)
Right-click on the NoAutoUpdate value and choose Modify (or double-click on it to bring up the Modify dialogue box).
![image](https://github.com/user-attachments/assets/00bb5f68-515a-4a55-a0a8-b13bdfadc6fd)
The default value data will be 0, i.e., disabled; change the value data to 1 and enable the NoAutoUpdate.
![image](https://github.com/user-attachments/assets/5783b4e7-3a2e-4d26-b4ef-2b4f77228a06)


If you need to update the system, you must manually perform this operation from "Settings">"Windows Update", and then click the "Check for Updates" button.

## How can I prevent VS Code from replacing a newly opened, unmodified (preview) tab with a subsequently opened one?
When you [single-]click a file in the left sidebar's file browser or open it from the quick open menu (Ctrl-P, type the file name, Enter), Visual Studio Code opens it in what's called "Preview Mode", which allows you to quickly view files.

Preview Mode tabs are not kept open. As soon as you go to open another file from the sidebar, the existing Preview Mode tab (if one exists) is used. You can determine if a tab is in Preview Mode, by looking at its title in the tab bar. If the title is italic, the tab is in preview mode.

To open a file for editing (i.e. don't open in Preview Mode), double-click on the file in the sidebar, or single-click it in the sidebar then double click the title of its Preview Mode tab.

If you want to disable Preview Mode all together, you can do so by setting "workbench.editor.enablePreview": false in your settings file. You can also use the "workbench.editor.enablePreviewFromQuickOpen" option to disable it only from the quick open menu.

Before you can disable Preview Mode, you'll need to open your Settings File.

Pro Tip: You can use the Command Palette(shortcut Ctrl+Shift+P) to open your settings file, just enter "Preferences: Open User Settings"!

Once you've opened your settings file (your settings file should be located on the right), add the "workbench.editor.enablePreview" property, and set its value to false.






