# GOAL
demonstrate moving an existing service to a Docker container using Ubuntu
successful results will correctly answer service queries from clients
 
# RESOURCES
Existing Servers with DHCP, DNS, and Apache2 
lst1 has DNS and DHCP running on IP 192.168.59.201
lst2 has a secure Apache2 server running on IP 192.168.59.202
DNS correctly resolves www.lst.lanLinks to an external site. to the Apache2 web server
Client using DHCP from the DHCP and DNS server running on IP at 192.168.59.201
 

TASK

 

Provide a screenshot of DHCP and resolvectl output for the DHCP Client
Implement Docker on lst2. Provide a screenshot of a “docker version” output.
Replace the existing Apache2 configuration with a Docker container on lst2. Provide a screenshot of your running “docker ps” command showing the Docker container running
Provide a screenshot of existing Apache2 services not running (the service that was replaced by your Docker container)
Provide a screenshot of either a curl or web browser navigating to www.lst.lanLinks to an external site. from a DHCP client
Grading:

Accessing the Apache server running on a DHCP client 30 points

Docker installed on lst2              20 points

Apache2 correctly running in a container 100 points

 
