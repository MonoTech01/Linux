# Task 1
Install and configure SAMBA. Share a document folder with SAMBA clients. Place a file in the new documents folder with your name as the title.

Submit a screenshot from a client with the document folder displaying the shared file. Include a copy of your smb configuration files.

# Task 2
Install and configure NFS. Share a documents folder with NFS clients. Place a file in the new documents folder with your name as the title.

Submit a screenshot from a client with the document folder displaying the shared file. Include a copy of the showmount command on the client.

---------
# Performance

## Note
- I created a clone of my "already created" VM in Linux Lab 1.
- 
  ![Linuxlab5](/Images/Lab5-pic1.png)
  
  ![Linuxlab5](/Images/Lab5-pic2.png)
  
  ![Linuxlab5](/Images/Lab5-pic3.png)
  
  ![Linuxlab5](/Images/Lab5-pic4.png)
  
  
  ![Linuxlab5](/Images/Lab5-pic5.png)
  
- After creating my clone VM, it had the same IP address and name with my 1st VM's. That is why I m changes in Netplan below!

Checked: .201

![Linuxlab5](/Images/Lab5-pic6.png)

Changed: .201 to .202 
![Linuxlab5](/Images/Lab5-pic7.png)


## Task 1
### Install and configure SAMBA in my original VM.


![Linuxlab5](/Images/Lab5-pic10.png)

- Verify

### Create a file to place in the sambashare directory
Before creating a file, I've created a sambashare directory.

### Configure Samba config file
- Edit the file
sudo nano /etc/samba/smb.conf
- Add new config and save by Ctrl-O
- Restart Samba and update firewall rules

### Set up Samba Client on Mono2 (the clone one)
- Install the client

sudo apt install smbclient

- Set up a client samba account's password

- Set up the server's path for the client
  



