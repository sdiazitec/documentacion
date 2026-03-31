# Microsoft Teams Linux Configuration Guide (Extended)

## Chapter 1: Microsoft Edge Installation
### Full Installation Steps
1. Open your terminal and run:
   ```bash
   sudo apt update
   sudo apt install microsoft-edge
   ```
2. Verify the installation:
   ```bash
   microsoft-edge --version
   ```

## Chapter 2: Office 365 PWA
### Installation of Office 365 as PWA
1. Open Microsoft Edge.
2. Go to the Office 365 website.
3. Click the three dots in the upper right corner, then 'Apps' -> 'Install this site as an app'.

## Chapter 3: Teams Historical Context
Teams has evolved from initial office communication tools to a robust platform.

## Chapter 4: Teams Installation as PWA with Launcher Creation
- After installation, create a launcher on your desktop:
  - Right-click and select 'Create Launcher'.
  - Set the command to:
    ```bash
    microsoft-edge --app=https://teams.microsoft.com
    ```

## Chapter 5: Complete Linux Audio Stack Architecture
- **OSS**: Open Sound System
- **ALSA**: Advanced Linux Sound Architecture
- **PulseAudio**: Sound server for POSIX OSes.
- **PipeWire**: Multimedia processing.
- **WirePlumber**: Session manager for PipeWire.

## Chapter 6: Edge Configuration
- Set up your preferences under settings > advanced.

## Chapter 7: Initial Diagnosis of auto_null
- Check that the auto_null sink is enabled and works correctly.

## Chapter 8: Problem 1: PipeWire Without Real Sinks
### Solution and Validation
- Ensure PipeWire is properly configured:
  ```bash
  pactl list sinks
  ```

## Chapter 9: Problem 2: Multiple Audio Outputs
### Sink Identification and Solution
- Use:
  ```bash
  pacmd list-sinks
  ```

## Chapter 10: Problem 3: Audio Video Permissions
### Commands to Grant Permissions
- Run the following:
  ```bash
  sudo chmod +r /dev/snd/*
  ```

## Chapter 11: Problem 4: Speaker Error in Teams
### Explanation
Ensure the default sink is set correctly using:
```bash
pactl set-default-sink <sink-name>
```

## Chapter 12: Problem 5: pavucontrol Validation
- Launch `pavucontrol`:
  ```bash
  pavucontrol
  ```

## Chapter 13: Problem 6: Device Profiles Not Available
### Explanation of ACL vs UCM
- ACL: Access Control Lists manage permissions.
- UCM: Use Case Manager for sink-sink communication.

## Chapter 14: Problem 7: Post Reboot Instability
### Root Cause Analysis
- Investigate system logs to identify audio service failures after reboot.