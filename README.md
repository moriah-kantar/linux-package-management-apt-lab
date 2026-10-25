# Linux Package Management with APT | Debian Lab

**Author:** Moriah Kantar

**Course:** Google Cybersecurity Professional Certificate

**Completed:** September 2026

**Project type:** Simulated Linux Package Management

## Overview

This hands-on Google Skills lab focused on managing software packages in a Debian Linux environment using the command-line interface (CLI) and the Advanced Package Tool (**APT**). I practiced installing, inspecting, removing, and reinstalling packages, while verifying changes to the system's software inventory.

The lab introduced two network-related utilities: **`nload`**, a terminal-based network traffic monitor, and **`tcpdump`**, a packet-capture tool. The work documented here covers **software management and installation**, not a live packet capture or traffic analysis exercise.

## Lab Environment

| Component | Details |
| --- | --- |
| Training platform | Google Skills (guided, temporary lab environment) |
| Operating system | Debian GNU/Linux (Bookworm) |
| Interface | Bash terminal / Linux CLI |
| Package manager | APT (`apt`) |
| Software packages | `nload`, `tcpdump` |

## Objectives

- Explore basic APT commands and help output.
- Install software from configured Debian package repositories.
- View a package's command-line usage options.
- Remove a package and verify that its executable is no longer available.
- Install an additional tool used in network analysis.
- Review installed packages and reinstall previously removed software.

## Procedure and Evidence

### 1. Explore APT

I began by running `apt` without additional arguments to review available package-management operations, including `list`, `show`, `install`, `remove`, `update`, and `upgrade`.

```bash
apt
```

**Observation:** APT provides a consistent interface for working with software packages and their dependencies.

### 2. Install and inspect `nload`

```bash
sudo apt install nload
nload -h
```

APT retrieved and installed `nload` and its required dependency, `libncurses6`. Running `nload -h` displayed the program's command syntax and options, confirming that its executable was available.

**Evidence:** [Installation and help output](screenshots/01-nload-install-and-help.png)

### 3. Remove `nload` and verify the change

```bash
sudo apt remove nload
nload -h
```

APT removed the `nload` package. A subsequent attempt to run `nload -h` returned a **“No such file or directory”** error, showing that the program was no longer available at its prior executable path.

**Observation:** After the removal, APT indicated that `libncurses6` was no longer required and could be cleaned up using `apt autoremove`. I did **not** run that cleanup command in the documented steps.

**Evidence:** [Removal and verification](screenshots/02-nload-removal-verification.png)

### 4. Install `tcpdump`

```bash
sudo apt install tcpdump
```

I installed `tcpdump` with APT. The terminal output showed `libpcap0.8` being installed as a dependency. An initial command contained a typo (`instal` instead of `install`), which APT rejected; I corrected the command and proceeded with the installation.

**Important scope note:** This lab demonstrates **installation** of `tcpdump`; it does not demonstrate running packet captures, filtering packets, or analyzing traffic.

**Evidence:** [Installation output](screenshots/03-tcpdump-install-and-package-list.png)

### 5. Review installed packages

```bash
apt list --installed
```

I reviewed the installed package inventory and confirmed that `tcpdump` appeared among the installed software. This step reinforced how package listings can be used to check which tools are present on a Linux system.

**Evidence:** [Installed package list](screenshots/04-installed-package-verification.png)

### 6. Reinstall `nload`

```bash
sudo apt install nload
```

To complete the software lifecycle exercise, I reinstalled `nload` using APT after previously removing it.

**Evidence:** [Reinstallation output](screenshots/05-nload-reinstallation.png)

## Results

| Task | Outcome |
| --- | --- |
| Explore APT help and commands | Completed |
| Install and inspect `nload` | Completed |
| Remove `nload` and verify removal | Completed |
| Install `tcpdump` | Completed |
| Review installed packages | Completed |
| Reinstall `nload` | Completed |

## Cybersecurity Relevance

Linux software administration supports many security operations. This lab reinforced several useful foundational practices:

- **Tool readiness:** Install utilities that support network monitoring and troubleshooting.
- **System visibility:** Check installed packages to understand a host's software inventory.
- **Change verification:** Validate that software installations and removals had the intended effect.
- **Dependency awareness:** Recognize how package managers install dependencies and identify unused packages.
- **Administrative access:** Distinguish everyday inspection commands from changes requiring elevated privileges via `sudo`.

## Key Takeaways

1. APT simplifies package lifecycle management on Debian-based Linux systems.
2. Reading command help and terminal output is an effective way to learn tools and confirm results.
3. Installing a package may also install dependencies; removing the package does not necessarily remove all of them.
4. Reviewing installed packages helps establish what software exists on a system.
5. A small command-line typo can cause an operation to fail; carefully checking syntax and error messages helps resolve it.

## Documentation Notes

This repository documents a **guided educational lab**, not a production system or an independent security assessment. The included screenshots have been cropped to omit the temporary lab URL. No packet captures, exploit activity, or network traffic findings are claimed.
