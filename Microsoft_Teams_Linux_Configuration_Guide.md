# Microsoft Teams Linux Configuration Guide

## Introduction
This guide provides a comprehensive overview of configuring Microsoft Teams on Ubuntu 24, including audio troubleshooting and PipeWire configuration.

## Requirements
- Ubuntu 24 or later
- Microsoft Teams installed

## Microsoft Teams Installation
To install Microsoft Teams on Ubuntu, follow these steps:
1. Open a terminal.
2. Download the Microsoft Teams DEB package:
   ```bash
   wget https://packages.microsoft.com/teams/teams_1.4.00.26453-1_amd64.deb
   ```
3. Install the package using dpkg:
   ```bash
   sudo dpkg -i teams_1.4.00.26453-1_amd64.deb
   ```
4. If there are dependency issues, run:
   ```bash
   sudo apt-get install -f
   ```

## Configuration
### Setting Up Microsoft Teams
- Launch Microsoft Teams from the Applications menu.
- Sign in with your organizational account.
- Configure your settings from the profile menu.

## Audio Troubleshooting
### Common Audio Issues
1. **No sound during calls**:
   - Ensure your audio devices are correctly selected in Teams settings.
   - Check system sound settings and ensure the output device is active.

2. **Poor audio quality**:
   - Check your internet connection.
   - Test your microphone and speaker functionality.

### Testing Audio Devices
To test your audio devices, follow these steps:
1. Open the `Sound Settings` from the system menu.
2. Speak into your microphone and check the input level.
3. Play audio through your speakers to test.

## PipeWire Configuration
PipeWire is often required for advanced audio usage. Here’s how to configure it:
### Installing PipeWire
Run the following commands to install PipeWire:
```bash
sudo apt install pipewire pipewire-audio-client-libraries
```
### Configuring PipeWire
- Edit the PipeWire configuration file:
```bash
nano ~/.config/pipewire/pipewire.conf
```
- Ensure that the following settings are included:
```ini
context.global.alsa.period-size = 256
context.global.alsa.ringbuffer.size = 2048
```
- Save and exit the editor.

### Restarting PipeWire
After making changes, restart PipeWire with:
```bash
systemctl --user restart pipewire
```

## Conclusion
Following these steps should assist you in effectively configuring Microsoft Teams on Ubuntu 24. For further assistance, consult the Microsoft support documentation or community forums.
