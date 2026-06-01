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





