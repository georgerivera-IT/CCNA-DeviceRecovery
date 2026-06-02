# CCNA-DeviceRecovery

### Problem:
Work department reports a router went down, forgotten password to the router, or requests file/system image backups.

### Solution:
Performing factory reset, password recovery, configuration backup, and system image backup and recovery on a Cisco router. Additionally, performing an IOS upgrade on a Cisco switch.

### Skills demonstrated:
Cisco IOS familiarity

#### Topology:
<img width="673" height="282" alt="DR1" src="https://github.com/user-attachments/assets/ac056625-d1cc-4409-bb5a-26f436ac5f6f" />
<br><br>

#### Factory Reset
Used 'write erase' command in privileged exec mode and 'reload' command to reload the router. This erases the startup configuration from NVRAM and forces the router to reload - the initial steps to performing a factory reset.

<img width="623" height="95" alt="DR2" src="https://github.com/user-attachments/assets/dbf86a20-17d7-4ee5-a2d3-10f64fcc8091" />

<br>
<br>

Post-reload, logged new router configurations by assigning hostname and IP address to Interface Gigabit Ethernet 0/0.

<img width="647" height="468" alt="DR3" src="https://github.com/user-attachments/assets/c9a4d895-676b-49e8-854a-0fcd0bcb0b44" />

<br>
<br>

#### Password Recovery
Assigned a secret password, mimicking a "forgotten" password throughout these steps.

<img width="650" height="86" alt="PR1" src="https://github.com/user-attachments/assets/f338c206-458e-499f-9b54-2392481011be" />

<br>
<br>

Configured router to boot into rommon prompt on next reload, and copied the running-config to the startup-config.

<img width="653" height="100" alt="PR2" src="https://github.com/user-attachments/assets/0809adb0-d691-4db0-838b-1d0a23fecc73" />
<img width="650" height="74" alt="PR3" src="https://github.com/user-attachments/assets/a8b0bda9-9654-4b79-a168-5bba30e48db8" />

<br>
<br>

Reloaded router and in rommon, entered the command 'confreg 0x2142' to ignore the contents of the startup-config in order to bypass the "forgotten" password.

<img width="649" height="404" alt="PR4" src="https://github.com/user-attachments/assets/cd77c159-fe07-4266-9ea9-f85b7be893ed" />

<br>
<br>

Skipped setup wizard. Show running-config displays that the running-config was not saved because the router bypassed loading the startup-config on bootup from command 'confreg 0x2142'. 

<img width="652" height="173" alt="PR5" src="https://github.com/user-attachments/assets/8f2c8970-fe8b-4bd8-8e61-554a66fedca4" />

<br>
<br>

Copied the startup-config to the running-config. Missing this step will factory reset the router. Command is successful when router hostname changes from 'Router' to 'R1'.

<img width="652" height="108" alt="PR6" src="https://github.com/user-attachments/assets/674cf76e-5741-43db-a957-fbe97eedbe9b" />

<br>
<br>

Removed the enable secret password and ensured the router reboots normally on next reload with command 'config-register 0x2102'. Copied the running-config back to the startup-config and proceed with reload.

<img width="650" height="275" alt="PR7" src="https://github.com/user-attachments/assets/d1ab5e3d-4a68-485d-8318-6d7ce6ac5f7b" />

<br>
<br>

Post-reload is observed that no enable secret password was enabled correctly (not prompted for password: ), and new reload shows hostname as 'R1' rather than 'Router'. The password is successfully recovered, and a new one can be established.

<img width="654" height="355" alt="PR8" src="https://github.com/user-attachments/assets/22edf15c-8ee5-4390-abc5-3c5c95303bf1" />

#### Configuration Backup
Stored the running-config to Flash on R1 as a backup file: "Backup1". Verified backup via 'show flash' command and observing "Backup1".

<img width="651" height="238" alt="CB" src="https://github.com/user-attachments/assets/9afffd96-f722-4d52-b331-efe68cea23f7" />

<br>
<br>

Stored the startup-config to TFTP server (10.10.10.10 via Topology) as a backup file: "Backup2". Verified backup via Server Services TFTP.

<img width="652" height="85" alt="CB2" src="https://github.com/user-attachments/assets/b2b6bcd5-12f5-489d-acb9-98ee16d2a45e" />
<img width="699" height="223" alt="CB3" src="https://github.com/user-attachments/assets/a2f60c3a-9547-4ae4-8e1e-72aa47e99a94" />

#### IOS System Image Backup & Recovery
IOS system image is stored in Flash. Copied Flash to TFTP server at 10.10.10.10, with copied Flash filename "c2900-universalk9-mz.SPA.151-4.M4.bin". Verified backup via Server Services TFTP

<img width="650" height="420" alt="image" src="https://github.com/user-attachments/assets/85d0d963-6e79-4162-b3ce-e4c6c0df618f" />

<img width="697" height="707" alt="IOS2 (2)" src="https://github.com/user-attachments/assets/5685a93d-917f-4d96-8ce2-5a6ed9b1da58" />

#### IOS System Image Backup & Recovery
Deleted existing Flash file: "c2900-universalk9-mz.SPA.151-4.M4.bin". Force router reload and observed rommon mode.

<img width="651" height="291" alt="IOSR1" src="https://github.com/user-attachments/assets/f5e7f227-b849-4007-a2bd-c84716bbc9a0" />

<br>
<br>

Used Internet search to find system recovery instructions for the model of the router. For this use case of a Cisco 2900 router, this link is used: https://www.cisco.com/c/en/us/td/docs/routers/access/1900/software/configuration/guide/Software_Configuration/appendixCrommon.html#69806

<br>

Using the command 'tftpdnld' assists user with IOS recovery instructions.

<img width="652" height="316" alt="IOSR2" src="https://github.com/user-attachments/assets/be40fda9-1713-4b55-8cb9-89920c3a4cc1" />

<br>
<br>

Filled in IP Address, Subnet Mask, Default Gateway, TFTP Server & Filename. Proceed with 'tftpdlnd command', followed by 'reset'.

<img width="653" height="212" alt="IOSR4" src="https://github.com/user-attachments/assets/3d6a8bd6-255a-42df-acc8-78c668d8b270" />
<img width="649" height="250" alt="IOSR3" src="https://github.com/user-attachments/assets/c01a78d1-db11-42f0-a66f-8b024f897612" />

#### IOS Image Upgrade
Verified current version (12.0). Copy upgraded TFTP Flash (15.0) file to SW1.

<img width="652" height="82" alt="IOSU1" src="https://github.com/user-attachments/assets/d032945f-b755-4aa2-9fa1-ad6a826f01d4" />
<img width="699" height="592" alt="IOSU2" src="https://github.com/user-attachments/assets/142efc13-5d98-4965-9b2d-80d3b7fa8d4f" />
<img width="651" height="239" alt="IOSU3" src="https://github.com/user-attachments/assets/58b1ca43-b4e2-40c9-bfda-717d8f498f1e" />

<br>
<br>

Use 'boot system c2960-lanbasek9-mz.150-2.SE4.bin' command to set primary IOS image for next reload. Reload and verify new software version.

<img width="651" height="174" alt="IOSU4" src="https://github.com/user-attachments/assets/4b3ca57e-e940-4d4f-8278-65411335a4ad" />
<img width="650" height="249" alt="IOSU5" src="https://github.com/user-attachments/assets/ffc06c65-20f1-4b3a-835b-9d3b86556605" />








