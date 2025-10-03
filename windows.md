# Windows Tips

### Restore the “Import pictures and videos” AutoPlay Option in Windows 10/11

To add the Import pictures and videos option to the AutoPlay dialog in Windows:

Open an admin Command Prompt window.

Run the following commands:
```
cd "C:\Program Files (x86)\Windows Photo Viewer"
regsvr32 PhotoAcq.dll
regsvr32 PhotoViewer.dll
```
Note: For Windows 32-bit systems, use C:\Program Files instead of C:\Program Files (x86)

### Restore Classic Notepad
Open CMD as ADMIN, then run the following:
```
assoc .txt=txtfile
ftype txtfile="C:\Windows\System32\NOTEPAD.EXE" "%1"
```

### Restore Classic Copy& Paste
Open CMD, then run the following:
```
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```
### Disable 'Search the Web' Completley in windows 11
1. Open the Registry Editor by searching for "regedit" in the Start menu and clicking the top result. Click yes if prompted by User Account Control.
2. Navigate to HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Explorer. If the Explorer key does not exist, right-click on Windows and create a new key called Explorer.
3. Create a new DWORD (32-bit) registry key and name it DisableSearchBoxSuggestions.
4. You can create a new registry key by right-clicking in the right window pane and selecting New->DWORD.
5. Double-click on DisableSearchBoxSuggestions to edit it and set the Value data field to 1 and click OK.
6. Close the Registry Editor and reboot your computer. 
