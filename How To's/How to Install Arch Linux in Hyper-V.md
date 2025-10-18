# How to Install Arch Linux in Hyper-V

## Prerequisites
- ✅ Hyper-V enabled and computer restarted
- ✅ Arch Linux ISO downloaded from https://archlinux.org/download/

## Step 1: Enable Hyper-V

### Run PowerShell as Administrator
1. **Close any current PowerShell window**
2. **Click the Windows Start button** (bottom-left)
3. **Type**: `PowerShell`
4. **Right-click** on "Windows PowerShell" in the results
5. **Click "Run as administrator"**
6. **Click "Yes"** when Windows asks for permission

### Enable Hyper-V Feature
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

You'll see `[Y/n]` asking if you want to restart - type `Y` and press Enter to restart.

## Step 2: Download Arch Linux ISO

1. **Open your web browser**
2. **Go to**: https://archlinux.org/download/
3. **Scroll down** to the "HTTP Direct Downloads" section
4. **Click on any mirror** near your location (like a US mirror if you're in the US)
5. **Download the file** that looks like: `archlinux-2025.xx.xx-x86_64.iso` (about 800MB-1GB)
6. **Save** it somewhere easy to find like your **Downloads** or **Desktop** folder

## Step 3: Open Hyper-V Manager

1. **Press the Windows Key**
2. **Type**: `Hyper-V Manager`
3. **Click on "Hyper-V Manager"** to open it

## Step 4: Create the Virtual Machine

Once Hyper-V Manager is open and the ISO is downloaded:

1. In Hyper-V Manager, click **"New"** > **"Virtual Machine"** in the right panel
2. Click **"Next"** on the wizard welcome screen
3. **Name**: Enter "Arch Linux" or any name you prefer
4. Click **"Next"**
5. **Generation**: Select **"Generation 2"** (recommended for modern systems)
6. Click **"Next"**
7. **Memory**: Assign at least **2048 MB (2 GB)** of RAM (more is better if available)
8. Click **"Next"**
9. **Networking**: Select your network connection from the dropdown
10. Click **"Next"**
11. **Virtual Hard Disk**: 
    - Leave default name or customize
    - Set size to at least **20 GB** (recommended: 40-50 GB)
12. Click **"Next"**
13. **Installation Options**: 
    - Select **"Install an operating system from a bootable image file"**
    - Click **"Browse"** and select your downloaded Arch Linux ISO
14. Click **"Next"**
15. Review settings and click **"Finish"**

## Step 5: Start the VM

1. In Hyper-V Manager, find your new "Arch Linux" VM in the list
2. Right-click on it and select **"Connect"**
3. Click **"Start"** in the new window
4. The Arch Linux installer will boot up

The installation will take about 20-30 minutes total.

## Notes

- For complete Arch installation, you'll need to follow the official Arch Linux installation guide once the VM boots
- Consider using `archinstall` script for easier setup
- Hyper-V provides better integration than other virtualization tools on Windows
