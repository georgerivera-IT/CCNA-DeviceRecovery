# CCNA-DeviceRecovery

### Overview:
Performing factory reset, password recovery, configuration backup, and system image backup and recovery on a Cisco router. Additionally, performing an IOS upgrade on a Cisco switch.

### What I configured:
3 Routers to be DNS clients.

### Skills demonstrated:
Cisco IOS familiarity

### Screenshots:
#### Topology
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
Assigned new secret password.

<img width="650" height="86" alt="PR1" src="https://github.com/user-attachments/assets/f338c206-458e-499f-9b54-2392481011be" />

<br>
<br>

Configured router to boot into rommon prompt on next reload, and copied the running-config to the startup-config.

<img width="653" height="100" alt="PR2" src="https://github.com/user-attachments/assets/0809adb0-d691-4db0-838b-1d0a23fecc73" />
<img width="650" height="74" alt="PR3" src="https://github.com/user-attachments/assets/a8b0bda9-9654-4b79-a168-5bba30e48db8" />



