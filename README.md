# Lincukoo USB-Dongle Firmware upgrade Tool

**Firmware Repository**: [https://github.com/lincukoo/dongle/tree/main/firmware]

**USB-Dongle Firmware upgrade Tool**: [https://lincukoo.github.io/zigbee-dongle/]

A web-based firmware upgrade tool for Lincukoo USB-Dongle devices. This tool allows you to upgrade device firmware directly from your web browser using the Web Serial API.

## Features

- **Web-based Interface**: No installation required, works directly in your browser
- **Serial Port Connection**: Direct communication with USB-Dongle via serial port
- **Firmware Selection**: 
  - Download firmware from GitHub repository
  - Select local firmware files (.gbl)
- **Real-time Progress**: Visual progress bar and detailed status logs
- **XModem Protocol**: Reliable firmware transfer using XModem protocol
- **Cross-platform**: Works on Windows, macOS, and Linux (with compatible browsers)

## System Requirements

### Browser Support

- **Chrome/Edge 89+** (Recommended)
- **Opera 75+**
- **Other Chromium-based browsers** with Web Serial API support

> ⚠️ **Note**: Firefox and Safari do not support Web Serial API. Please use Chrome or Edge.

### Hardware Requirements

- Lincukoo USB-Dongle device
- USB cable for connection
- USB port on your computer

### Driver Installation

**For Windows/macOS users**: Install CH340 Driver to enable device detection.

## Quick Start

### 1. Open the Tool

Simply open `index.html` in your web browser (Chrome/Edge recommended).

### 2. Connect Your Device

1. Insert your USB-Dongle into an available USB port
2. Click the **"Connect"** button
3. Select your device's COM port from the system dialog
4. Wait for the connection status to show "Port connected"

### 3. Select Firmware


#### Download from GitHub
1. Select a firmware version from the dropdown
2. The firmware will be automatically downloaded


### 4. Start Upgrade

1. Click the **"Flash"** button to start the upgrade process
2. Monitor the progress bar and status logs
3. Wait for "Upgrade completed successfully" message
4. The device will automatically restart after upgrade

### 5. Disconnect

Click the **"Disconnect"** button to release the serial port when finished.

## Detailed Usage Guide

### Device Connection

1. **Connect Button**: Opens the system serial port selection dialog
   - Shows all available COM ports
   - Select your USB-Dongle's port
   - Connection status will update automatically

2. **Disconnect Button**: Releases the serial port
   - Appears after successful connection
   - Use this to free the port for other applications

3. **Connection Status**:
   - Green box: Port connected successfully
   - Red box: No port connected (with troubleshooting tips)


### Upgrade Process

1. **Enter Upgrade Mode**: 
   - Sends "1\r\n" command to device
   - Waits for "begin upload" response
   - Retries up to 10 times if needed

2. **File Transfer**:
   - Uses XModem protocol for reliable transfer
   - 128-byte packets with CRC-16 checksum
   - Automatic retry on errors
   - Real-time progress updates (0-100%)

3. **Completion**:
   - Sends EOT (End of Transmission) signal
   - Sends restart command "2\r\n"
   - Displays success message in green

### Status Log

The status log shows:
- **Info messages** (blue): General operation status
- **Success messages** (green): Successful operations
- **Error messages** (red): Errors and warnings
- **Debug mode**: Enable checkbox to see raw data (optional)

## Troubleshooting

### Device Not Detected

1. **Check USB Connection**:
   - Ensure USB cable is properly connected
   - Try a different USB port
   - Try a different USB cable

2. **Check Drivers**:
   - Verify CH340 driver is installed (Windows/macOS)
   - Check Device Manager (Windows) or System Information (macOS)
   - Reinstall driver if necessary

3. **Check Browser**:
   - Use Chrome/Edge 89+ or newer
   - Ensure Web Serial API is enabled
   - Try refreshing the page

4. **Port Already in Use**:
   - Disconnect from other applications
   - Close other serial port tools
   - Restart the browser if needed

### Upgrade Fails

1. **Check Firmware File**:
   - Verify file is not corrupted
   - Ensure file format is `.gbl`
   - Try downloading again from GitHub

2. **Check Connection**:
   - Ensure device stays connected during upgrade
   - Avoid unplugging USB cable
   - Check serial port connection status

3. **Retry Upgrade**:
   - Disconnect and reconnect the device
   - Select firmware again
   - Click Flash button to retry

4. **Check Logs**:
   - Review error messages in status log
   - Enable debug mode for detailed information
   - Note any specific error codes

### Connection Issues

1. **Port Selection Fails**:
   - Ensure device is properly connected
   - Check if port appears in Device Manager
   - Try disconnecting and reconnecting

2. **Port Disconnects Unexpectedly**:
   - Check USB cable quality
   - Avoid using USB hubs (connect directly)
   - Check power supply to device

## Technical Details

### Serial Port Configuration

- **Baud Rate**: 115200
- **Data Bits**: 8
- **Stop Bits**: 1
- **Parity**: None
- **Flow Control**: None

### Protocols Used

- **XModem**: For firmware transfer
  - Packet size: 128 bytes
  - CRC-16 checksum validation
  - Automatic retry mechanism

- **Web Serial API**: For serial port communication
  - Direct browser-to-device communication
  - No additional software required

### Firmware Format

- **Supported**: `.gbl` (Gecko Bootloader)
- **Source**: GitHub repository or local files
- **Download**: Automatic download on selection (GitHub)

## Safety Notes

⚠️ **Important Warnings**:

1. **Do not disconnect** the device during upgrade
2. **Do not close** the browser tab during upgrade
3. **Ensure stable** USB connection before starting
4. **Verify firmware** compatibility with your device
5. **Backup** current firmware if possible before upgrading

## Support

For issues or questions:
- Check the troubleshooting section above
- Review the status log for error messages
- Ensure all requirements are met
- Verify device compatibility

## License

This tool is provided as-is for use with Lincukoo USB-Dongle devices.

## Version History

- Current version supports firmware upgrade via XModem protocol
- GitHub firmware integration
- Real-time progress tracking
- Enhanced error handling

---

**Last Updated**: 2025

