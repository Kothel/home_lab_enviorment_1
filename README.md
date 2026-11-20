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
### 9.0 Finished product
<img width="1911" height="921" alt="image" src="https://github.com/user-attachments/assets/8494e778-5c93-4a4d-b85a-2eebc19986f9" />





# home_lab_environment_1

<img width="800" height="508" alt="Flash" src="https://github.com/user-attachments/assets/f637784e-bf18-415e-af3d-b0658bf021e0" />

## 1.Plan the Architecture of the Computer
###   &nbsp;&nbsp;&nbsp;    1.Plan the internal Architecture of the server
####  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  <img width="592" height="542" alt="Better lab plan" src="https://github.com/user-attachments/assets/bb291bcb-6c3a-4afa-b0d8-e89415976303" />
###   &nbsp;&nbsp;&nbsp;   2.Aquire harware and install extra drive
####  &nbsp;&nbsp;&nbsp; <img width="4000" height="2250" alt="20261019_195258" src="https://github.com/user-attachments/assets/973c228c-8322-462e-92b0-c0e036fa389d" />
###   &nbsp;&nbsp;&nbsp;   3



## 2.Install and setup the Server
###     1. flash drive Debian OS
<img width="800" height="508" alt="Flash" src="https://github.com/user-attachments/assets/f637784e-bf18-415e-af3d-b0658bf021e0" />
###     1. boot from flashdrive
<img width="2250" height="4000" alt="20261006_190539" src="https://github.com/user-attachments/assets/24b320da-ec0b-44ed-bf80-4f8e259a46fb" />
###     2.select wanted setting in bios for OS
<img width="4000" height="2250" alt="20261006_191115" src="https://github.com/user-attachments/assets/d6a35c64-d38d-4d41-bf42-40e419aa5d8a" />
<img width="4000" height="2250" alt="20261006_205901" src="https://github.com/user-attachments/assets/4986de33-a068-46e4-a073-b1d0927e1fb8" />



###     1. Problem 1
##### A. give me this error then goes black
<img width="2250" height="4000" alt="linux err 1" src="https://github.com/user-attachments/assets/76202e5e-88a3-49be-a0e6-c1ddedaf947d" />
<img width="4000" height="2250" alt="20261006_220813" src="https://github.com/user-attachments/assets/fd1b14e9-743d-41b7-bf68-75bbbbaf7cba" />

##### B.  add cmmnds to make it show all bios errors (video)
#####     <img width="2250" height="4000" alt="20261006_213413" src="https://github.com/user-attachments/assets/8b46ea34-fb81-4034-a706-18178ddbeb04" />

  ##### tested ping to make sure the server was actualy on
  ##### remove the quiet moduel in the line that starts with string linux
  ##### recorded process with phone to err4.Mp4 and played it back slower to look at errors
  ##### video shows the debian OS is actually booting trie to see if it is a monitor issue and add nomodeset
  ##### nomodeset was the fix
<img width="4000" height="2250" alt="20261007_155147" src="https://github.com/user-attachments/assets/5185553f-0189-4c48-9fcf-5993d61ed050" />

###     1. Install and run ssh
### <img width="4000" height="2250" alt="20261007_162031" src="https://github.com/user-attachments/assets/0b43e925-e83d-478c-9611-7d6a9071eb74" />


### <img width="912" height="290" alt="2026-10-07_16-24" src="https://github.com/user-attachments/assets/84bfce35-0849-4639-acf9-054f78fca626" />
### 1. Problem 2
#### Pc Turns itself off after about 30 minutes
#### first guess is that PC is sleeping so check that
#### <img width="1247" height="290" alt="Found-issue" src="https://github.com/user-attachments/assets/db5d3cb3-977b-46d5-ac1f-67410642b900" />
#### fix it with the commands to no longer enter sleep mode
#### <img width="1242" height="507" alt="Find_SLEEP" src="https://github.com/user-attachments/assets/ef56bcf8-440f-4840-9ba0-43f9ba15e0f4" />




###     1.  Confirm status of new ssd and mount it
#### <img width="1150" height="898" alt="drives" src="https://github.com/user-attachments/assets/23ff0c01-b2cb-4832-9bf7-22543047d99c" />
#### <img width="1242" height="200" alt="mounting" src="https://github.com/user-attachments/assets/08f185dc-07c4-4155-8b71-034d87f90255" />
### <img width="627" height="302" alt="100 gib partition" src="https://github.com/user-attachments/assets/a6240106-4df8-4641-9f84-4dbdcba14655" />



###
## 3.Install Next Cloud Software

###       1. Install Docker
#### <img width="785" height="507" alt="docker install" src="https://github.com/user-attachments/assets/68e07774-0eb0-4937-9f0b-6075ac7d9d2f" />
###       2. setup Docker 
#### <img width="1485" height="804" alt="docker password configure" src="https://github.com/user-attachments/assets/687ca393-1a8c-48e6-9247-221ea9ff846f" />
###       3. confirm status of docker container
#### <img width="1000" height="154" alt="Docker-apps" src="https://github.com/user-attachments/assets/c5b55edf-c062-4465-ac07-4e8deb1d0dd2" />
###        4. Create Compe.yamle file
#### file created is listed in git




### A. 
## 4.Set Up Tailscale
#### 1. install tailscale
<img width="1150" height="422" alt="tailscale intall" src="https://github.com/user-attachments/assets/64e04cc2-44d9-4967-ad75-60ba5616cee3" />
#### 2. install taiscale on mobile device and add ip to compose 
<img width="523" height="394" alt="tailscale port" src="https://github.com/user-attachments/assets/017e0c11-db46-4868-87a8-e87e2b4a9138" />
#### 4. replace private ip with tailscale IP
## 5. Set up nextcloud
### 1.open nextcloud in a seperate device
<img width="720" height="1600" alt="noip" src="https://github.com/user-attachments/assets/19c73e89-260e-412b-a525-17b69702ad7a" />
### 2use the admin account that was newly created
<img width="1592" height="783" alt="nextcloud account" src="https://github.com/user-attachments/assets/dda69770-eb76-49b6-a534-a10386436636" />
### 3create accounts for family
<img width="259" height="293" alt="image" src="https://github.com/user-attachments/assets/affd9efe-2026-4594-8d6d-8ff1d5260666" />
## 6. add Google SSO functionality
### 1. install openID Connect APP in nextcloud GUI
<img width="1541" height="153" alt="image" src="https://github.com/user-attachments/assets/51422026-1311-4516-be93-d365d7913b7f" />
### 2. enable Https on tailscale and use Magic DNS name from tailsacle for server IP
### <img width="1224" height="358" alt="https troubleshoot" src="https://github.com/user-attachments/assets/f05acb10-6fa8-41a8-9a8a-7f14d242e0f6" />
### 3. opened google OAuthen
created google cloud project
opened google auth Program
created clients
added google client secrete to openID connect app in nextcloud

## 3 Problem 3
### https does not want to connect
<img width="1161" height="219" alt="googleSSO" src="https://github.com/user-attachments/assets/3120b830-6aa7-426b-82d6-aefd31d76959" />

<img width="1224" height="358" alt="https troubleshoot" src="https://github.com/user-attachments/assets/51c3fbd1-2950-4324-83c4-13beebc2aede" />




