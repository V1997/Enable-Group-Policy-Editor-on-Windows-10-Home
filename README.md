# Enable-Group-Policy-Editor-on-Windows-10-Home
Enable Group Policy Editor on Windows 10 Home

## 💻 Enable Group Policy Editor on Windows 10 Home

Windows 10 Home doesn't include the Group Policy Editor (`gpedit.msc`) by default, but you can manually enable it using the following steps:

### ✅ Steps to Install Group Policy Editor:

1. **Create a Batch File**  
   Open **Notepad** and paste the following script:

   ```bat
   @echo off
   pushd "%~dp0"
   dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientExtensions-Package~3*.mum >gp.txt
   dir /b %SystemRoot%\servicing\Packages\Microsoft-Windows-GroupPolicy-ClientTools-Package~3*.mum >>gp.txt
   for /f %%i in ('findstr /i . gp.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"
   pause
   ```

2. **Save the File**  
   Save it as `gpedit-install.bat`.  
   > ⚠️ Make sure to select **"All Files"** in the Save dialog (not `.txt`).

3. **Run as Administrator**  
   Right-click the file and select **"Run as administrator"**.

4. **Wait for Installation**  
   Let the script complete. Once it's done, you should be able to launch the Group Policy Editor by pressing `Win + R`, typing `gpedit.msc`, and hitting Enter.

---

### ⚙️ Configure Windows Updates to Ask Before Downloading

Once Group Policy Editor is installed:

1. Open `gpedit.msc`
2. Navigate to:  
   `Computer Configuration > Administrative Templates > Windows Components > Windows Update > Manage end user experience`
3. Double-click **"Configure Automatic Updates"**
4. Select **Enabled**, then choose option:  
   **2 - Notify for download and auto install**
5. Click **Apply**, then **OK**
6. Restart your PC to apply changes

 
 
