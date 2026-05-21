# Linux Toolkit

A collection of Linux automation, diagnostics, maintenance, and offensive security workflow scripts built for Kali Linux and cybersecurity lab environments.

These scripts were designed for personal lab use, Hack The Box workflows, system maintenance, and streamlined offensive security operations.

---

## Features

- System maintenance and cleanup
- Go offensive security tool updates
- VMware shared folder mounting
- Hack The Box VPN automation
- System health monitoring
- OpenClaw launcher workflow
- VPN cleanup and stale interface removal
- Offensive security lab convenience scripts

---

## Repository Structure

```text
linux-toolkit/
├── scripts/
│   ├── cleanse
│   ├── dragon
│   ├── health
│   ├── htb
│   └── claw
├── LICENSE
└── README.md
```

---

## Included Scripts

### `cleanse`

System maintenance and cleanup automation for Kali Linux.

#### Features
- `apt update` + `full-upgrade`
- Package cleanup
- DNS reset
- Broken symlink cleanup
- x86_64 binary removal on ARM systems
- Broken binary detection
- VMware shared folder mounting
- Go offensive security tool updates
- OpenVPN cleanup
- Stale VPN interface cleanup

#### Usage

```bash
sudo cleanse
```

---

### `health`

Terminal-based Linux system health dashboard.

#### Features
- CPU / RAM / Disk usage
- DNS servers
- Internet connectivity
- VMware shared folder status
- PostgreSQL status
- VPN detection
- Public IP
- Largest directories
- Top processes
- Network interfaces

#### Usage

```bash
sudo health
```

Live mode:

```bash
sudo health --live
```

---

### `htb`

Launches Hack The Box VPN in a separate terminal window.

#### Features
- VPN config verification
- Separate terminal session
- Returns focus to current window
- Simplified HTB workflow

#### Configuration

By default:

```bash
VPN_DIR=/mnt/hgfs
VPN_FILE=academy-regular.ovpn
```

Optional overrides:

```bash
export VPN_DIR=/path/to/vpn/folder
export VPN_FILE=myvpn.ovpn
```

#### Usage

```bash
sudo htb
```

---

### `claw`

Launch helper for OpenClaw gateway and dashboard.

#### Features
- Opens OpenClaw gateway in a separate terminal
- Automatically launches dashboard
- Configurable port

#### Usage

```bash
sudo claw
```

Optional custom port:

```bash
OPENCLAW_PORT=18789 claw
```

---

### `dragon`

Workflow launcher that chains multiple tools together.

#### Workflow

```text
cleanse → htb → health
```

#### Important Dependency Notice

`dragon` depends on the following scripts being installed and accessible in your PATH:

- `cleanse`
- `htb`
- `health`

If these are missing, `dragon` will not function properly.

#### Usage

```bash
sudo dragon
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/linux-toolkit.git
cd linux-toolkit
```

Make scripts executable:

```bash
chmod +x scripts/*
```

Install system-wide:

```bash
sudo cp scripts/* /usr/local/bin/
```

Verify installation:

```bash
which cleanse
which health
which htb
which claw
which dragon
```

---

## Requirements

Recommended environment:

- Kali Linux
- VMware (optional)
- QTerminal
- OpenVPN
- Go
- PostgreSQL (optional)
- OpenClaw (optional)

Install dependencies:

```bash
sudo apt install qterminal xdotool openvpn curl -y
```

---

## Disclaimer

These scripts are intended for educational purposes, lab environments, authorized systems, and cybersecurity research only.

Always ensure you have permission to access or test any environment.

---

## License

MIT License
