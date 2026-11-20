# Home Lab Environment

This repository documents the planning, installation, configuration, and troubleshooting of my home server and Nextcloud environment.

## Table of Contents

1. [Server Architecture and Hardware](#1-server-architecture-and-hardware)
2. [Debian Server Installation](#2-debian-server-installation)
3. [Server Configuration and Troubleshooting](#3-server-configuration-and-troubleshooting)
4. [Storage Setup](#4-storage-setup)
5. [Docker and Nextcloud Installation](#5-docker-and-nextcloud-installation)
6. [Tailscale Remote Access](#6-tailscale-remote-access)
7. [Nextcloud Initial Setup](#7-nextcloud-initial-setup)
8. [Google Single Sign-On](#8-google-single-sign-on)

---

## 1. Server Architecture and Hardware

### 1.1 Plan the server architecture

The initial planning included the server's internal layout and storage arrangement.

![Initial home lab plan](https://github.com/user-attachments/assets/bb291bcb-6c3a-4afa-b0d8-e89415976303)

### 1.2 Acquire hardware and install the additional drive

![Server hardware and additional drive](https://github.com/user-attachments/assets/973c228c-8322-462e-92b0-c0e036fa389d)

---

## 2. Debian Server Installation

### 2.1 Create the Debian installation USB

![Creating the Debian installation USB](https://github.com/user-attachments/assets/f637784e-bf18-415e-af3d-b0658bf021e0)

### 2.2 Boot from the USB drive

![Booting from the USB drive](https://github.com/user-attachments/assets/24b320da-ec0b-44ed-bf80-4f8e259a46fb)

### 2.3 Configure the BIOS

Select the appropriate BIOS settings for installing and booting the operating system.

![BIOS settings](https://github.com/user-attachments/assets/d6a35c64-d38d-4d41-bf42-40e419aa5d8a)

![Additional BIOS configuration](https://github.com/user-attachments/assets/4986de33-a068-46e4-a073-b1d0927e1fb8)

---

## 3. Server Configuration and Troubleshooting

### 3.1 Troubleshooting the Debian installation display

**Problem:** The installation displayed an error and then the screen went black.

![Debian installation error](https://github.com/user-attachments/assets/76202e5e-88a3-49be-a0e6-c1ddedaf947d)

![Black screen during installation](https://github.com/user-attachments/assets/fd1b14e9-743d-41b7-bf68-75bbbbaf7cba)

#### Troubleshooting steps

- Tested network connectivity with `ping` to confirm that the server was still running.
- Removed the `quiet` parameter from the Linux boot line to display more boot messages.
- Recorded the boot process and reviewed the video at a slower speed to identify the error.
- Determined that Debian was booting and that the issue was related to display output.
- Added the `nomodeset` boot parameter.

**Result:** `nomodeset` resolved the display issue.

![Debian boot after applying nomodeset](https://github.com/user-attachments/assets/5185553f-0189-4c48-9fcf-5993d61ed050)

### 3.2 Install and configure SSH

SSH was installed to allow the server to be administered remotely.

![SSH installation and configuration](https://github.com/user-attachments/assets/0b43e925-e83d-478c-9611-7d6a9071eb74)

![SSH connection](https://github.com/user-attachments/assets/84bfce35-0849-4639-acf9-054f78fca626)

### 3.3 Troubleshoot automatic shutdown

**Problem:** The PC powered off or became unavailable after approximately 30 minutes.

The initial suspicion was that the server was entering sleep mode. The power-management settings were checked, and commands were used to prevent the system from sleeping.

![Identified sleep setting](https://github.com/user-attachments/assets/db5d3cb3-977b-46d5-ac1f-67410642b900)

![Commands used to change sleep behavior](https://github.com/user-attachments/assets/ef56bcf8-440f-4840-9ba0-43f9ba15e0f4)

---

## 4. Storage Setup

### 4.1 Identify and mount the additional SSD

The new SSD was checked and mounted for server storage.

![Identified storage devices](https://github.com/user-attachments/assets/23ff0c01-b2cb-4832-9bf7-22543047d99c)

![Mounting the SSD](https://github.com/user-attachments/assets/08f185dc-07c4-4155-8b71-034d87f90255)

![SSD partition layout](https://github.com/user-attachments/assets/a6240106-4df8-4641-9f84-4dbdcba14655)

---

## 5. Docker and Nextcloud Installation

### 5.1 Install Docker

![Docker installation](https://github.com/user-attachments/assets/68e07774-0eb0-4937-9f0b-6075ac7d9d2f)

### 5.2 Configure Docker

![Docker configuration](https://github.com/user-attachments/assets/687ca393-1a8c-48e6-9247-221ea9ff846f)

### 5.3 Verify the Docker containers

![Docker container status](https://github.com/user-attachments/assets/c5b55edf-c062-4465-ac07-4e8deb1d0dd2)

### 5.4 Create the Docker Compose file

The Docker Compose configuration is included in this repository.

---

## 6. Tailscale Remote Access

Tailscale is used to access the server remotely through the private tailnet.

### 6.1 Install Tailscale on the server

![Tailscale installation](https://github.com/user-attachments/assets/64e04cc2-44d9-4967-ad75-60ba5616cee3)

### 6.2 Install Tailscale on mobile devices

Install Tailscale on the mobile device and connect it to the same tailnet as the server.

![Tailscale configuration](https://github.com/user-attachments/assets/017e0c11-db46-4868-87a8-e87e2b4a9138)

### 6.3 Configure access to Nextcloud

Use the server's Tailscale address or MagicDNS hostname when configuring remote access. The original notes also reference replacing the private IP address in the configuration with the Tailscale IP.

---

## 7. Nextcloud Initial Setup

### 7.1 Open Nextcloud from another device

![Opening Nextcloud](https://github.com/user-attachments/assets/19c73e89-260e-412b-a525-17b69702ad7a)

### 7.2 Sign in with the administrator account

Use the administrator account created during the initial Nextcloud setup.

![Nextcloud administrator account](https://github.com/user-attachments/assets/dda69770-eb76-49b6-a534-a10386436636)

### 7.3 Create family accounts

Create individual accounts for family members.

![Creating family accounts](https://github.com/user-attachments/assets/affd9efe-2026-4594-8d6d-8ff1d5260666)

---

## 8. Google Single Sign-On

Google Single Sign-On (SSO) was configured using the OpenID Connect app for Nextcloud.

### 8.1 Install the OpenID Connect app

Install the OpenID Connect app from the Nextcloud app interface.

![OpenID Connect app](https://github.com/user-attachments/assets/51422026-1311-4516-be93-d365d7913b7f)

### 8.2 Enable HTTPS for remote access

Enable HTTPS through Tailscale and use the server's Tailscale MagicDNS hostname rather than its private LAN IP address.

![HTTPS troubleshooting](https://github.com/user-attachments/assets/f05acb10-6fa8-41a8-9a8a-7f14d242e0f6)

### 8.3 Configure Google OAuth

The recorded setup steps were:

1. Create a project in Google Cloud.
2. Open the Google authentication configuration.
3. Create OAuth client credentials.
4. Add the Google client ID and client secret to the OpenID Connect app in Nextcloud.

### 8.4 Troubleshoot HTTPS connectivity

**Problem:** HTTPS would not connect during the Google SSO setup.

The following screenshots document the issue and troubleshooting process.

![Google SSO connection issue](https://github.com/user-attachments/assets/3120b830-6aa7-426b-82d6-aefd31d76959)

![HTTPS troubleshooting details](https://github.com/user-attachments/assets/51c3fbd1-2950-4324-83c4-13beebc2aede)
