
# Omarchy Linux WFH Audio & Video Setup

This is a concise, step-by-step guide for turning Omarchy (Arch-based) into a stable work-from-home machine for video calls, audio work, and office productivity. Keep this file for reference.

# 1. Confirm PipeWire

1. Check status:

```plaintext
systemctl --user status pipewire
systemctl --user status pipewire-pulse
systemctl --user status wireplumber
```

2. If all show `active (running)`, proceed. If not, enable and start them.

# 2. Install required packages

Run as root:

```plaintext
sudo pacman -Syu
sudo pacman -S pipewire-alsa pipewire-pulse pipewire-jack wireplumber easyeffects pavucontrol pavucontrol-qt
```

If you use an AUR helper (optional):

```plaintext
yay -S zoom teams-for-linux onlyoffice-bin obs-studio visual-studio-code-bin discord
```

# 3. Reboot

Reboot the system to ensure PipeWire and modules load cleanly.

# 4. Verify audio interface (Audient EVO 4)

1. Plug EVO 4 in.

2. List PipeWire nodes:

```plaintext
pw-cli ls Node | grep -i evo
```

3. Or use GUI: `pavucontrol`.

4. Set EVO as default input and output in Sound settings.

# 5. PipeWire tuning for low latency (optional)

Try buffer quantum 128 or 256 if you need lower latency.

```plaintext
pw-metadata -n settings 0 clock.force-quantum 128
```

# 6. EasyEffects: basic setup

1. Launch EasyEffects.

2. Input device: EVO 4 mic.

3. Output device: EVO 4 headphones/monitor.

4. Add and enable these chains for voice work:

   - Noise reduction (RNNoise)

   - Noise gate (set threshold to remove background hiss)

   - Compressor (ratio 3:1, attack 5ms, release 100ms)

   - EQ (mild boost 100-250Hz for warmth, mild boost 3-5kHz for clarity)

   - Limiter (prevent clipping)

5. Save preset as `Voice Work`.

6. Test by recording or using a test call.

# 7. Routing apps through EasyEffects

Most apps will use PipeWire default input. If an app shows wrong device, set its input to EVO 4 in the app's settings.

Use `pavucontrol` to move streams between devices live.

# 8. Camera guidance

1. Test Elgato Facecam as UVC device:

```plaintext
v4l2-ctl --list-devices
```

2. If it appears, test in `cheese` or OBS. Settings control may be limited.

3. Recommended reliable Linux cameras: Logitech C920, C922, Brio family, Brio 500.

4. Buy a UVC-compliant camera for full compatibility.

# 9. Essential apps for office work

Install these (pacman or AUR):

- Firefox or Chromium (web apps)

- Zoom (package)

- Microsoft Teams (web or teams-for-linux AUR)

- Slack (web or AUR)

- Thunderbird (email)

- LibreOffice or OnlyOffice

- Syncthing or Nextcloud client

- OBS Studio (recording)

- Flameshot (screenshots)

- OBS or Peek for screen recording

# 10. Workflow example

- Meetings: Browser/Zoom → input = EVO 4 with EasyEffects preset.

- Notes: Obsidian or Joplin + Syncthing.

- Files: Nextcloud or Google Drive via browser.

- Recording: OBS + EasyEffects for mic chain.

# 11. Backup and restore

1. Install Timeshift:

```plaintext
sudo pacman -S timeshift
```

2. Create a snapshot after setup:

```plaintext
sudo timeshift --create --comments "Post-audio-setup"
```

# 12. Quick verification commands

```plaintext
# Check PipeWire
systemctl --user status pipewire

# List audio devices
pw-cli ls Node

# List video devices
v4l2-ctl --list-devices

# Start EasyEffects
easyeffects
```

# 13. Notes and tips

- Audient EVO 4 is class-compliant. No drivers needed. Plug and play.

- Keep buffer at 128 or 256 for low latency. Increase if you get xruns.

- Do not replace PipeWire shipped by Omarchy. Extend it by installing the packages above.

- If an app fails to see the camera, check `dmesg` after plug-in to find driver issues.

# 14. Camera purchase shortlist

- Logitech C920 (stable, affordable)

- Logitech C922 (better low-light)

- Logitech Brio 300 or Brio 500 (UHD, modern features)

# 15. If you want a one-line installer

I can produce a script that runs the installs and basic config. Ask and I will create it.

---

Document created for quick reference.