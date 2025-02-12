# Wake-on-LAN Manager

A command-line tool for managing and sending Wake-on-LAN (WoL) magic packets to wake up network devices remotely. This tool allows you to save device MAC addresses with friendly names for easier access and wake up devices either by their MAC address directly or using saved device names.

## Features

- Send Wake-on-LAN magic packets to wake up remote devices
- Save device MAC addresses with custom names for easy reference
- List all saved devices
- Remove saved devices
- Support for custom IP addresses and ports
- Configuration persistence across sessions

## Installation

1. Ensure you have Python 3.x installed on your system
2. Clone this repository or download the script
3. Make the script executable (Unix-like systems):
   ```bash
   chmod +x wol.py
   ```

## Usage

### General Syntax

```bash
./wol.py <command> [arguments]
```

### Available Commands

#### Wake a Device

Wake up a device using either its MAC address or saved name:

```bash
./wol.py wake <MAC_address/device_name> [--ip IP_ADDRESS] [--port PORT]
```

Examples:
```bash
# Wake using MAC address
./wol.py wake 00:11:22:33:44:55

# Wake using saved device name
./wol.py wake mycomputer

# Wake with custom IP and port
./wol.py wake mycomputer --ip 192.168.1.255 --port 7
```

#### Save a Device

Save a device's MAC address with a friendly name:

```bash
./wol.py save <name> <MAC_address>
```

Example:
```bash
./wol.py save mycomputer 00:11:22:33:44:55
```

#### List Saved Devices

Display all saved devices and their MAC addresses:

```bash
./wol.py list
```

#### Remove a Saved Device

Remove a device from the saved devices list:

```bash
./wol.py remove <name>
```

Example:
```bash
./wol.py remove mycomputer
```

## Configuration

The tool automatically creates and manages a configuration file in the user's home directory:

- Location: `~/.wol/config.json`
- Format: JSON file containing device names and their corresponding MAC addresses
- Created automatically on first use

## Requirements

- Python 3.x
- Standard Python libraries (no additional dependencies required):
  - socket
  - struct
  - argparse
  - json
  - os
  - pathlib

## Technical Details

- Magic packets are sent using UDP broadcast
- Default broadcast address: 255.255.255.255
- Default port: 9
- MAC addresses can be specified with or without delimiters (: or -)
- Configuration is stored in JSON format for easy manipulation

## Troubleshooting

1. Ensure the target device has Wake-on-LAN enabled in its BIOS/UEFI settings
2. Verify that your network allows UDP broadcast packets
3. Check that the MAC address is correctly specified
4. Ensure you have the necessary permissions to send network packets
5. For wake-ups across subnets, ensure your router supports directed broadcasts

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.