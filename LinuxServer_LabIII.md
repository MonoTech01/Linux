# TASK #1

From another VM, use ncat to listen on port 4455

Using ncat on lst1, call the other VM with the -e /bin/bash option

Using tshark on lst1, in another shell, capture packets on port 4455 or use a filter. Use the pcapng format for the file

Submit screenshots of your listening and calling sessions for ncat. Submit a screenshot of your tshark trace file of the first 10 packets in the trace file.

# TASK #2 

Transfer the trace file on lst1 to Wireshark on another VM or host machine with Wireshark installed. Open the trace file. Click on the first packet and display the Transmission Control Protocol layer

Submit a screenshot of your TCP layer detail in Wireshark

# TASK #3

Enable ssh and cockpit ports on lst1 using UFW. You will have to enable UFW. Increase logging to high. Using netcat or telnet try to access lst1 TCP port 25

Submit a screenshot of the UFW log showing the packets attempting to use port 25. Also, submit a screenshot of the current rules in verbose mode for UFW.

# Task #4

Configure DHCP on lst1 for the bottom half of the network block for your subnet. IP addresses below 128. Please account for your gateway and host network IP addresses usually 1. and .2 for VMWare). Your lst1 server should have been configured with a static address using .201. Use another VM, server or desktop to receive a dynamic DHCP address.

Submit a screenshot of your DHCP configuration on lst1.

Submit a screenshot of the DHCP leases file showing that the IP address was issued.

Submit a screenshot of the DHCP address on your client VM. 
