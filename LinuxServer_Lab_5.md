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
  
  ![Linuxlab5](/Images/Lab5-pic8.png)

  ![Linuxlab5](/Images/Lab5-pic1.png)
  
  ![Linuxlab5](/Images/Lab5-pic2.png)
  
  ![Linuxlab5](/Images/Lab5-pic3.png)
  
  ![Linuxlab5](/Images/Lab5-pic4.png)
  
  ![Linuxlab5](/Images/Lab5-pic5.png)
  
- After creating my clone VM, it had the same IP address and name with my 1st VM's. I had to change them! 

Checked: .201

  ![Linuxlab5](/Images/Lab5-pic6.png)

Changed IP: .201 to .202 

  ![Linuxlab5](/Images/Lab5-pic7.png)

  ![Linuxlab5](/Images/Lab5-pic18.png)

Changed host name (from lst1 to lst2) by this command: hostnamectl set-hostname lst2

## Task 1
### Install and configure SAMBA in my original VM.


  ![Linuxlab5](/Images/Lab5-pic10.png)

Verify

  ![Linuxlab5](/Images/Lab5-pic11.png)

### Create a file to place in the sambashare directory

Create a sambashare directory and a file in there

  ![Linuxlab5](/Images/Lab5-pic12.png)

  ![Linuxlab5](/Images/Lab5-pic13.png)

### Configure Samba config file
- Edit the file
  
sudo nano /etc/samba/smb.conf

- Add new config and save by Ctrl-O
  
  ![Linuxlab5](/Images/Lab5-pic26.png)

- Restart Samba and update firewall rules

  ![Linuxlab5](/Images/Lab5-pic14.png)

### Set up Samba Client on Mono2 (the clone one)
- Install the client

  sudo apt install smbclient

- Set up a client samba account's password

  ![Linuxlab5](/Images/Lab5-pic20.png)

- Set up the server's path for the client
  
 smbclient //192.168.10.201/my_sambashare -U monotech

 Note: the "my_sambashare" should match with the name that I configured in the samba config file!

### Note - troubleshooting

If you have any problem about "connection_refused", please consider to work on you firewall. I had the problem and fixed it with the following commands.

  ![Linuxlab5](/Images/Lab5-pic19.png)



# Task 1 - Result

My vm2 (lst2) can access sambashare in vm1 (lst1).

  ![Linuxlab5](/Images/Lab5-pic27.png)

# Task 2 - NFS - Server & Client Settings
## Install NFS server on VM1 (original - lst1)

  ![Linuxlab5](/Images/Lab5-pic28.png) 

## Start the NFS server on VM1

  ![Linuxlab5](/Images/Lab5-pic29.png)

## Create a directory on VM1 + a file on the Server (VM1)

  ![Linuxlab5](/Images/Lab5-pic35.png)

## Change... Check IP address to set up the correct network + Apply the new configuration!

  ![Linuxlab5](/Images/Lab5-pic36.png)

  ![Linuxlab5](/Images/Lab5-pic38.png)

## Verify on VM1

  ![Linuxlab5](/Images/Lab5-pic39.png)


## Client: VM2 (clone-lst2) - Update app and install NFS on client side

  ![Linuxlab5](/Images/Lab5-pic32.png)

## Create a directory to mount the NFS share on the Client (VM2)

  ![Linuxlab5](/Images/Lab5-pic40.png)

## Mount the NFS share on VM2 - Mount to the folder create on VM2

  ![Linuxlab5](/Images/Lab5-pic41.png)
## Verify on VM2

  ![Linuxlab5](/Images/Lab5-pic42.png)
  ![Linuxlab5](/Images/Lab5-pic43.png)

# Submission
 ![Linuxlab5](/Images/Lab5-pic45.png)



  



