PTP - Precision Time Protocol

Description:
I've been loooking for guide where is simply described how to sync two hosts via PTP protocol.
So I've read some amount of guides/manuals and decided to post it here so it's will be the most simple and complete guide for PTP, that you can just follow step by step.


REQUIRED:
- Linux OS
- Direct connection between hosts (at least via Ethernet)
- root access

Step 1:
- Install 'ptpd' package on machines you need to synchronize
- YOU MIGHT ALSO NEED OTHER PACKAGES FROM THIS LIST(not sure): ptp4l linuxptp
- ALL COMMANDS BELLOW YOU NEED RUN AS A ROOT OR USING SUDO

Step 2:
- Connect machines to each other with Ethernet.
- Use 'ip a' command to see what interfaces you have, thei names and see what interface you will use. Ethernet interface might have name such as "enp5s0f0", "eth0"

Step 3:
- Start a PTP-server daemon with command 'ptpd --masteronly --interface <network interface over which PTP synch messages will be sent>'

Step 4:
- Start a PTP-client daemon with command 'ptpd --slaveonly --interface <network interface over which PTP synch messages will be sent>'

Step 5:
- On the PTP-server host execute command 'pmc -u -b 0 'GET TIME_STATUS_NP'

It's done!

My sources:

- https://www.kaitotek.com/resources/documentation/probe/install/debian-ubuntu/clock-synchronization-linux
- https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-configuring_ptp_using_ptp4l#sec-Specifying_a_Configuration_File

