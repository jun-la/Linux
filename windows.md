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
