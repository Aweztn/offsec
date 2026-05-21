# RedDragon OffSec

A growing offensive security, ethical hacking, automation, and lab repository focused on practical learning, workflow optimization, and cybersecurity operations.

This repository contains Linux tooling, offensive security workflows, Hack The Box resources, automation scripts, and future walkthroughs developed throughout hands-on learning and red team training.

Built primarily around:

- Kali Linux
- Hack The Box (HTB)
- CPTS preparation
- Offensive Security (OffSec)
- Linux automation
- Lab workflow optimization

---

## Repository Goals

This repository is intended to grow into a complete offensive security knowledge base containing:

- Automation scripts
- HTB workflows
- Enumeration methodologies
- Walkthroughs and notes
- Red team utilities
- Cheat sheets
- Lab setup automation
- Ethical hacking resources

---

## Current Repository Structure

```text
reddragon-offsec/
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

Linux maintenance, cleanup, and offensive security environment preparation.

Designed to automate common Kali Linux maintenance tasks while preparing a lab environment for offensive security work.

#### Features

- `apt update` + `full-upgrade`
- Package cleanup
- DNS reset
- Broken symlink cleanup
- x86_64 binary cleanup on ARM systems
- Broken binary detection
- VMware shared folder mounting
- Go offensive security tool updates
- OpenVPN cleanup
- Stale VPN interface cleanup

#### Important VMware Dependency

If using **VMware Fusion shared folders**, run `cleanse` before `htb`.

`cleanse` automatically mounts:

```text
/mnt/hgfs
```

This mount is required for HTB VPN configuration access.

#### Usage

```bash
sudo cleanse
```

---

### `health`

Terminal-based Linux system health dashboard.

Provides a quick overview of system health and offensive security lab readiness.

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

Hack The Box VPN launcher.

Launches an HTB VPN connection in a separate terminal session while preserving the current shell.

#### Important Dependency

If using VMware Fusion shared folders:

**Run `cleanse` first.**

`htb` expects VPN configurations to be accessible through:

```text
/mnt/hgfs
```

Without mounted shared folders, VPN configuration files will not be found.

#### Features

- VPN config verification
- Separate terminal session
- Automatic focus return
- Simplified HTB workflow

#### Configuration

Default values:

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

OpenClaw launcher workflow.

Starts the OpenClaw gateway in a separate terminal and launches the dashboard automatically.

#### Features

- Gateway automation
- Dashboard auto-launch
- Configurable port support

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

Primary offensive security workflow launcher.

Automates a common lab startup sequence.

#### Workflow

```text
cleanse → htb → health
```

#### Dependencies

`dragon` requires:

- `cleanse`
- `htb`
- `health`

Because `dragon` launches `cleanse` first, VMware shared folders are mounted automatically before launching `htb`.

#### Usage

```bash
sudo dragon
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/aweztn/red-dragon-offsec.git
cd red-dragon-offsec
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
- VMware Fusion (optional)
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

## Future Additions

Planned repository growth may include:

- HTB walkthroughs
- Enumeration workflows
- Nmap methodology
- DNS footprinting
- Web enumeration
- Windows/Linux privilege escalation notes
- CPTS study resources
- Red team automation
- Offensive security cheat sheets

---

## Disclaimer

This repository is intended for:

- Ethical hacking
- Authorized security testing
- Lab environments
- Education
- Cybersecurity research

Only perform security testing against systems you own or are explicitly authorized to assess.

---

## License

MIT License
