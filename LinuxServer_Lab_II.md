# Tasks
# 1 
- Using either using your host computer or a VM, configure secure SSH using a certificate generated to authenticate to lst1. Disable password authentication for SSH on lst1.
- Turn in a screenshot of your ~/.ssh/authorized_keys file on lst1 showing that the public key was added and a screenshot of your modified sshd configuration showing password authentication is disabled.

# 2

- Allow a banner in /etc/ssh/sshd_config.
- “Banner file-to-store-message”
- Create a banner file in /etc and that includes: “RESTRICTED SYSTEM AUTHORIZED USERS ONLY” and your name.
- After logging in submit a screenshot of the warning.

 
# 3

- Install the at service. Your output should include the service is active and runnin
- Submit a screenshot using systemctl with the status of the atd service.

# 4
- Submit a screenshot using systemctl status of the atd server before stopping the atd service and another after stopping the service.

# 5

- Mask the atd service. Submit a screenshot proving that the atd service is masked. 

# 6

- Install apache. Change the apache unit and use the override feature with "Linux is Awesome" and your name. 
- Submit a screenshot of the service with your custom description.

# 7
- using journalctl to display messages from sysstat.service and use an output file in json format.
- Submit a screenshot of your json file (use head)

-------------------------------------------------------------------------------------------------------------------
# Performance
# 1
- Access to my first vm lst2 and generate SSH key

ssh-keygen -t ed25519 -C "lst2"

![Linux](/Images/Lab2-pic0.png)

ssh-keygen: This is the command used to generate SSH key pairs.

-t ed25519: This option specifies the type of key to generate. In this case, it's set to ed25519, which is a modern and secure elliptic curve cryptography (ECC) algorithm for SSH keys.

-C "lst2": This option adds a comment to the generated key pair. The comment here is set to "lst2", which can be helpful for identifying the key's purpose or association with a specific server (like lst2 in this case).

Verify 
ls -l .ssh

![Linux](/Images/Lab2-pic1.png)

- Copy the key to a target VM (VM1: lst1)

![Linux](/Images/Lab2-pic2.png)

- Go to the VM1 to check for the key that is added by lst2
  
When I go to VM1, it does not ask for a password anymore!

![Linux](/Images/Lab2-pic3.png)

Verify: cat .ssh/authorized_keys

![Linux](/Images/Lab2-pic4.png)

- Edit sshd configuration to enable Certificate-based Authentication and disable Password authentication (in VM1)
nano by changing PubkeyAuthentication yes and PasswordAuthentication no

![Linux](/Images/Lab2-pic5.png)

- Troubleshoot:
It did not allow me to save <- permission denied

![Linux](/Images/Lab2-pic5.2.png)

I changed mode for the file

u + w

W for write permission

Result: editable + save (Ctrl 0, then Ctrl X). Remember using sudo to "nano" the file

![Linux](/Images/Lab2-pic5.3.png)
![Linux](/Images/Lab2-pic5.png)

- Verify
sudo cat /etc/ssh/sshd_config
![Linux](/Images/Lab2-pic6.png)





