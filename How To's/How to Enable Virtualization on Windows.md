# How to Enable Virtualization on Windows

## Check if Virtualization is Already Enabled

1. Press **Ctrl + Shift + Esc** to open Task Manager
2. Go to the **Performance** tab
3. Click on **CPU**
4. Look at the bottom right - if it says "Virtualization: Enabled", you're all set!

## If It's Disabled, Enable it in BIOS/UEFI

### Step 1: Enter BIOS/UEFI
- Restart your computer
- As it boots up, repeatedly press the BIOS key (usually **F2**, **F10**, **F12**, **Delete**, or **Esc** - it varies by manufacturer)
- You'll usually see a brief message during boot telling you which key to press

### Step 2: Find the Virtualization Setting

The location varies by manufacturer, but look for:
- **Intel processors**: "Intel VT-x", "Intel Virtualization Technology", or "Vanderpool"
- **AMD processors**: "AMD-V" or "SVM Mode"

Common locations in BIOS:
- Advanced > CPU Configuration
- System Configuration > Virtualization Technology
- Security > Virtualization
- Advanced > Advanced Processor Options

### Step 3: Enable It
- Change the setting to **Enabled**
- Save changes (usually **F10**) and exit
- Your computer will restart

## Manufacturer-Specific Tips

- **Dell**: Press F2 at the Dell logo
- **HP**: Press F10 or Esc, then F10
- **Lenovo**: Press F1 or F2
- **ASUS**: Press F2 or Delete
- **MSI**: Press Delete
- **Gigabyte**: Press Delete or F2

## For Gigabyte Motherboards Specifically

### Accessing BIOS
1. **Restart your computer**
2. **Press the Delete key** repeatedly as soon as it starts booting

### Finding AMD-V Setting
1. Look for the **"Advanced"** or **"M.I.T."** tab at the top
2. Navigate to **"Advanced CPU Settings"** or **"CPU Configuration"**
3. Find **"SVM Mode"** (Secure Virtual Machine - AMD's virtualization)
4. Change to **Enabled**
5. Press **F10** to save and exit

After enabling virtualization, you'll be able to use tools like Hyper-V, VirtualBox, VMware, or Windows Subsystem for Linux 2 (WSL2).
