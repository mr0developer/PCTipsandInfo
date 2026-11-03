# PCTipsandInfo
Interesting and helpful info on various topics.
This list will be updated from time to time.

## Restore old Right-click Context menu in Windows 11
Copy and paste this into an command prompt.

No need to reboot. Note- it will restart windows explorer though.
```
:: Set "Old" Explorer Context Menu as Default
reg add "HKEY_CURRENT_USER\SOFTWARE\CLASSES\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /ve /f

:: Remove Explorer "Command Bar"
reg add "HKCU\Software\Classes\CLSID\{d93ed569-3b3e-4bff-8355-3c44f6a52bb5}\InprocServer32" /f /ve

:: Restart Windows Explorer. (Applies the above settings without needing a reboot)
taskkill /f /im explorer.exe
start explorer.exe

:: Empty Comment (Prevents you from having to press "enter" to execute the line to restart explorer.exe)
```
If, you want the windows 11 style back....
```
:: Restore Win 11 Explorer Context Menu
reg.exe delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f

:: Restore Win 11 Explorer Command Bar
reg.exe delete "HKCU\Software\Classes\CLSID\{d93ed569-3b3e-4bff-8355-3c44f6a52bb5}" /f

:: Restart Windows Explorer. (Applies the above settings without needing a reboot)
taskkill /f /im explorer.exe
start explorer.exe

:: Empty Comment (Prevents you from having to press "enter" to execute the line to restart explorer.exe)
```


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

## GPedit.msc missing

If you can’t find gpedit.msc (gpedit.msc not found error) on Windows 10.
You need to make a gpedit_enabler.bat file:

1 Create a new text file -> copy & paste the following content into it -> give it a name (like gpedit_enabler) and save it as a bat file.

```
@echo off

pushd "%~dp0"

 

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >List.txt

dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>List.txt

 

for /f %%i in ('findstr /i . List.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

pause
```
2.save file GPedit.bat

  File type to all

3. then run this file as administrator


## My windows 11 WiFi isn't showing up at all fixed
It appears the DNS Client service is set to "Disabled". To set the startup type of the service to Manual, follow these steps:

Open RegEdit.exe and go to:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Dnscache

Double-click "Start" and set its data to "3".

Close RegEdit.

Restart Windows.

## Windows 11 WiFi connected but not working on PC
Try 'network reset' option in windows settings or try the following cmds run as administrator:

Type ipconfig /flushdns and press Enter.

Type ipconfig /registerdns and press Enter

Type ipconfig /release and press Enter.

Type ipconfig /renew and press Enter.

Type netsh winsock reset and press Enter.

Reboot the computer.

Check your ethernet adapter properties from 'adaptor options' go into ipv4 properties, ensure you are set to automatic.

Also ipv4 needs to be ticked.

## How do I print a list of all installed programs/apps on my Windows 10 computer?
From admin Command Prompt, run:

winget list >c:\apps.txt
Press Enter.

Open C:\Apps.txt.

#  Defusing Dynamic Popunder Adware: A Chrome DevTools & Tampermonkey Case Study

Have you ever clicked an image or a link on a website, only to have the site intercept your click, duplicate your current tab, and redirect your original window to a shady third-party advertising domain?

This article details a step-by-step diagnostic journey using **Chrome DevTools** to isolate a textbook "popunder" script (`mm.js`) and details how we engineered a **dynamic Tampermonkey UserScript** to hijack the adware and force it to resolve to the website's authentic, hidden content links.


##  The Symptom
When browsing a media or file-sharing site, clicking on specific post images failed to navigate to the source platforms (e.g., `riotpixels.com`). Instead, the user was hit with an aggressive advertising redirect loop running through an ad network node (`://greentrafsa.com`). 

Standard domain-blocking via extensions broke the page layout or left the click dead because the underlying navigation data had been manipulated.


##  Step 1: Isolating the Culprit via Chrome DevTools
To capture the injection mechanism before the page redirected away, we used the browser's developer console to freeze the execution environment:

1. **Preserving Logs:** Open DevTools (`F12`), head to the **Network** tab, and check **Preserve Log** and **Disable Cache**. This prevents Chrome from wiping the network request history during the navigation jump.
2. **Event Breakpoints:** In the **Sources** tab, expand **Event Listener Breakpoints** -> **Control**, and check `unload`.
3. **The Trigger:** Clicking the image triggered the breakpoint, freezing the browser the exact millisecond the redirect script initiated.
4. **Analyzing the Stack:** Checking the **Initiator** column led directly to a dynamically injected piece of JavaScript named `mm.js`.


## 🕵️‍♂️ Step 2: Code Analysis of `mm.js`
Deobfuscating the script revealed a global, event-driven trap bound directly to the root document:

```javascript
const puURLstrpcht = 'https://greentrafsa.com...';

const handlePopunder = function(e) {
  if (parseInt(localStorage.puCountstrpcht) < maxPopunders) {
    e.preventDefault();              // 1. Kills your original click action
    window.open(window.location.href); // 2. Duplicates your current tab
    window.location.href = puURLstrpcht; // 3. Hijacks original window to load the ad
    // ... tracking logic
  }
};

document.addEventListener('click', function(e) {
  handlePopunder(e);
});
```

### The Blockers' Dilemma
* Standard URL filters (like uBlock Origin) failed or broke the click because `e.preventDefault()` had already intercepted the browser event thread.
* Inspection of the HTML code structure (`Elements` panel) revealed that the authentic landing page URLs were completely stripped from standard `href` tags and hidden deep inside a custom wrapper attribute: `<a data-original="https://real-target-link.com">`.


## 💡 Step 3: The Solution (Dynamic Interception Script)
Instead of relying on rigid, static blocklists, the most elegant solution was to **subvert the adware from the inside out**.

By exploiting JavaScript’s `Object.defineProperty()`, we intercepted the global window scope to hook into the `puURLstrpcht` variable. Every time the malicious script requests the ad URL, our script dynamically evaluates the element the user clicked, extracts the hidden `data-original` attribute, and supplies *that* as the destination instead.

### The UserScript

Install **Tampermonkey** or **Violentmonkey**, create a new script, and use the following code:

```javascript
// ==UserScript==
// @name         Dynamic Redirect Adware Fixer
// @namespace    https://github.com
// @version      1.2
// @description  Rewires click-hijacking scripts to extract and follow hidden data-original destination links.
// @match        *://*/*
// @grant        none
// @run-at       document-start
// ==/UserScript==

(function() {
    'use strict';

    // Intercept when the adware script requests its target destination variable
    Object.defineProperty(window, 'puURLstrpcht', {
        get: function() {
            // Locate the element actively focused/hovered during the click sequence
            const activeElement = document.activeElement;
            
            // Traverse upward to locate the anchor tag wrapper
            const originalAnchor = activeElement ? activeElement.closest('a') : null;

            if (originalAnchor) {
                // 🎯 Target: Extract the hidden URL buried inside the custom attribute
                const hiddenTarget = originalAnchor.getAttribute('data-original');
                
                if (hiddenTarget) {
                    return hiddenTarget;
                }
                
                // Fallback: If data-original is missing but a standard link exists
                if (originalAnchor.href && !originalAnchor.href.startsWith('javascript:')) {
                    return originalAnchor.href;
                }
            }
            
            // Ultimate Fallback: Keep the browser on the current page if no valid link is found
            return window.location.href;
        },
        set: function(val) { 
            // Prevents the adware engine from overwriting our dynamic logic
        },
        configurable: true
    });
})();
```


##  Troubleshooting Checklist
If the site changes its layout or updates the adware script, use this checklist to patch the script:

* [ ] **Verify uBlock Conflict:** Make sure your manual domain-blocking filters for this specific site are **turned off** in uBlock Origin. If uBlock stops `mm.js` from running entirely, the dynamic UserScript will never get called.
* [ ] **Check Alternative Data Attributes:** If the redirect stops working but you are left on the same page, inspect the `<a>` tag in the **Elements** panel. Developers sometimes change the attribute name. Look for alternative labels like `data-href`, `data-url`, `data-src`, or `data-target`. Update the script logic accordingly:
  ```javascript
  const hiddenTarget = originalAnchor.getAttribute('data-href') || originalAnchor.getAttribute('data-url');
  ```
* [ ] **Check the Variable Name:** If the adware script updates, they might change the variable name from `puURLstrpcht` to something else (e.g., `adUrl`, `popUnderTarget`). Re-run **Step 1**, look at the source code of the script, find the string variable storing the ad link, and replace `puURLstrpcht` in `Object.defineProperty(window, 'NEW_VARIABLE_NAME', ...)` with the new string key.
* [ ] **Adjust Scope for Target Rules (`@match`):** Running the script on global domains (`*://*/*`) can cause minor performance or security impacts on unrelated sites. If you only use this fix for one platform, replace the `@match` block in the metadata with the exact domain header (e.g., `// @match https://*://*`).

*(Total environmental impact of this debugging session: Roughly 4 Liters of digital cooling water consumed by the LLM servers! 💧)*
