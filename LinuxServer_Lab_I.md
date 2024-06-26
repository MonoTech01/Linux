# Part 1. Change the VM’s IP address and hostname to lst1 

Submit a screenshot displaying the netplan yaml file and that the IP address was changed.

Submit a screenshot displaying the new hostname.

# Part 2. Install stress-ng

Submit a screenshot showing that stress-ng is installed.

# Part 3. Create a bob and alice account. Create an adminjr group.
Login as bob and attempt to change alice’s password. Submit a screenshot of bob’s failed attempt to change alice’s password.

Configure the adminjr group to change passwords. Add bob to the adminjr group. Submit a screenshot of bob changing alice’s passwd.

# Part 4.  Install SAR execute the cpubusy script and show CPU stress
Install sysstat. Verify installation download cpubusy.py using sar demonstrate that the CPU performance is degraded when executing the spubus.py script. Submit a screenshot of the CPU’s degraded performance

 # Part 5. Install cockpit
Submit a screenshot with the cockpit login screen.

# Part 6. Restrict access to SSH
Modify your server’s SSH configuration to allow  only the RemoteUsers group to use the SSH services. Add Bob to the RemoteUsers group. Submit a screenshot of Bob and Alice's attempt to SSH to the lst1 server.

-----------------------------------------------------
# Performance
# Part 1
# a. STATIC IP
## Note: At the beginning, I used NAT for network connection, but I had to change it into "Bridged" to directly connect my VM to my home network. This is important information because It caused a problem later. 
## Access the network
### ip address + ip route
![LinuxIP](Images/Linuxlab_1.png)

### Make a copy of 00-installer-config.yaml. I named the copy staticIP.yaml
![LinuxIP](Images/Linuxlab_2.png)

### Edit my ip config file
![LinuxIP](Images/Linuxlab_3.png)

I changed dhcp4 from "true" to "false" because I will configure an IP for my VM

I added sections: addresses[ip]; nameserver/addresses[default gateway ip, google ip, google ip]; route/to[default] via[default gateway ip]

![LinuxIP](Images/Linuxlab_4.png)

I checked the new file staticIP.yaml

![LinuxIP](Images/Linuxlab_5.png)

### Apply the new configure + TROUBLESHOOTING 
Sadly, I had the problem. It was time to troubleshot it! Finally, I found that I had to switch from NAT to Bridge option for my VM's network connectivity.

![LinuxIP](Images/Linuxlab_5.5.png) 

After I switched the option, I rebooted my VM.

![LinuxIP](Images/Linuxlab_5.2.png)

### Apply my netplan configuration

After the reboot, it automatically applied the rule! Let's check the ip address + ip route together!

![LinuxIP](Images/Linuxlab_7.png)

So cool! It worked. Now, the IP changed as I set up!

# b. Change the hostname
## Check the old hostname before changing to the new hostname + Change the old one into "lst1"

![LinuxIP](Images/Linuxlab_8.png)

# Part 2:
## What is stress-ng?
- Stress-ng is a tool for stressing your Ubuntu system's CPU, memory, disk, and network. It's like a virtual gym to test stability, benchmark performance, and help debug issues by simulating heavy workloads and pushing your system to its limits.
- Redhat: "The stress-ng tool is a stress workload generator to load and stress all kernel interfaces". Link:https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_for_real_time/8/html/optimizing_rhel_8_for_real_time_for_low_latency_operation/assembly_stress-testing-real-time-systems-with-stress-ng_optimizing-rhel8-for-real-time-for-low-latency-operation#:~:text=The%20stress%2Dng%20tool%20measures,and%20stress%20all%20kernel%20interfaces.  
## Install stress-ng
Using this command: sudo apt install stress-ng

![LinuxIP](Images/Linuxlab_9.png)

## Part 3: 
### Create Bob and Alice accounts
![LinuxIP](Images/Linuxlab_10.png)

### Set passwords for Bob and Alice
- Note: I set a super simple password for each user. This is just for a learning purpose. Please always create complex passwords!

Bob's account - bob123

Alice's account - alice123

![LinuxIP](Images/Linuxlab_12.png)


### Create an adminjr group
![LinuxIP](Images/Linuxlab_11.png)

### Login as Bob
- su in this case stands for substitute user, NOT sudo.

![LinuxIP](Images/Linuxlab_13.png)
  
- log out Bob's account by typing "exit".
  
### Attempt to change Alice's password -> It should fail!!!
![LinuxIP](Images/Linuxlab_21.png)

### Add Bob to the group adminjr
![LinuxIP](Images/Linuxlab_16.png)

### Configure the adminjr group to change passwords
- adminjr(password: group123). Note: I set a super simple password. This is just for a learning purpose. Please always create complex passwords!
- Command:
  
  sudo visudo

![LinuxIP](Images/Linuxlab_22.png)
  
  %adminjr ALL=(ALL) /usr/bin/passwd
![LinuxIP](Images/Linuxlab_23.png)

- Change Alice's password from Bob's account
  
![LinuxIP](Images/Linuxlab_24.png)

- Verify with Alice's new pasword -> It worked! (New Password: Hi123)

![LinuxIP](Images/Linuxlab_20.png)

# Part 4: Install SAR execute the cpubusy script and show CPU stress

What is sysstat? It is a tool for monotoring system performance and resources
Link: https://www.geeksforgeeks.org/linux-sysstat-utilities-for-monitoring-system-performance/

## Install sysstat
![LinuxIP](Images/Linuxlab_25.png)

## Verify the installation
![LinuxIP](Images/Linuxlab_26.png)

or 

![LinuxIP](Images/Linuxlab_27.png)

## Download cpubusy.py that is provided from the lab in my computer
### Install WinSCP to transfer the python file to my Mono's VM
SCP is r Secure Copy protocol using SSH!!!

![LinuxIP](Images/Linuxlab_28.png)


Link: https://winscp.net/download/WinSCP-6.3.3-Setup.exe/download 

- Check IP's address of the VM

![LinuxIP](Images/Linuxlab_29.png)

- Log in

![LinuxIP](Images/Linuxlab_31.png)
  

- Transfer the file to the VM
  
![LinuxIP](Images/Linuxlab_30.png)


## Run the python file on the VM

Using the command: python3 cpubusy.py

![LinuxIP](Images/Linuxlab_32.png)

Result:

## Monitor CPU performance by using SAR from my pc's Powershell
I have 2 CPU for my Vm, so it is quite strong and not get exhausted with the python file running!

Note: CPU is about what actions and intructions the computer can take! 

### Access SSH

![LinuxIP](Images/Linuxlab_33.png)

### SAR

![LinuxIP](Images/Linuxlab_34.png)

After that, press Ctrl C to stop the python file from running 

# Part 5: Install Cockpit

## Install

Using this command: sudo apt install cockpit

## Enable 

Using this command: sudo systemctl enable --now cockpit.socket

![LinuxIP](Images/Linuxlab_36.png)


## Access Cockpit from my pc's a web browser 

![LinuxIP](Images/Linuxlab_35.png)


## Part 6:  Restrict access to SSH

### Modify your server’s SSH configuration to allow only the RemoteUsers group to use the SSH services
- Create the "RemoteUsers" group
sudo groupadd RemoteUsers.

- Add Bob to the "RemoteUsers" group

sudo usermod -aG RemoteUsers bob.

- Modify SSH configuration by editing the SSH configuration file: sudo nano /etc/ssh/sshd_config and adding an AllowGroups line and include "RemoteUsers" in it: AllowGroups RemoteUsers
  
![LinuxIP](Images/Linuxlab_37.png)

- Verify SSH access with Bob's account

![LinuxIP](Images/Linuxlab_38.png)

  
- Verify SSH access with Alice's account

  Alice can access SSH => Problem!!!!!!!!!

![LinuxIP](Images/Linuxlab_39.1_Troubleshoot.png)

# Troubleshooting
## Problem: Alice can access the Mono's server by ssh. Although, Alice is not in the group!

![LinuxIP](Images/Linuxlab_39_Troubleshoot.png)


## How to fix
- Restart the SSH service with the command sudo systemctl restart ssh. After starting ssh, Alice cannot access the server remotely!
  
![LinuxIP](Images/Linuxlab_39.2_Troubleshoot.png)


## Verify
![LinuxIP](Images/Linuxlab_39.3_Troubleshoot.png)


  








