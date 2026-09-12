# NetTransfer

A small tool for transferring files between two computers over the local
network, without reaching for a USB stick. Tested on Windows 11, should
also run on Linux.

Built with AI assistance. I wrote it before I knew `scp` existed — see
[Notes](#notes) at the bottom.

## Requirements

- Python 3.13 (that's what I used; older 3.x versions will probably work)
- tkinter for the GUI
- No pip packages — standard library only

### Installing tkinter

**Linux**

```bash
# Ubuntu / Debian
sudo apt install python3-tk

# Fedora
sudo dnf install python3-tkinter

# Arch
sudo pacman -S tk
```

**Windows**

tkinter ships with Python by default. If it's missing, reinstall Python
and tick "tcl/tk and IDLE" during setup.

## Usage

Run the app on both machines:

```bash
python file_transfer_app.py
```

On Windows you can also just double-click `execute.bat`.

One machine sends, the other receives. The receiving side listens on
port 5555.

## Firewall

Port 5555 has to be open on the receiving machine.

```bash
# Linux (UFW)
sudo ufw allow 5555/tcp

# Linux (firewalld)
sudo firewall-cmd --permanent --add-port=5555/tcp && sudo firewall-cmd --reload
```

On Windows, allow port 5555 in Windows Defender Firewall.

## Notes

Transfers are unencrypted and unauthenticated, so this is meant for a
trusted home network only. I built it before I knew about `scp`, which
solves the same problem properly. I'm keeping it up tho!

## License

MIT — feel free to do whatever you like with it.
