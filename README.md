Enable SSH from local host/PC to the VM

>>Confirm that the VM in the VirtualBox is properly configured.
>>When the VM terminal opens>> Login with VM credentials during setup 




>>When the VM terminal opens>> Login with VM credentials during setup 
>>When successfully logged into VM with her newvmcloud@vmware 
>>Then type the following command to initialize SSH -sudo systemctl status ssh -VM would require password: type VM user password 
>>VM confirms if SSH is enabled on the VM to the local host or not. if SSH not found, then 
install SSH 
>>Installing SSH: Type command -sudo apt install openssh-server -y (-y(yes) is confirming SSH)


>>When SSH is installed, confirm the status of the installed SSH 
-type command: sudo systemctl status ssh 


=========================================

SSH CONNECTION>>step by step 
>>Open the command prompt>>run as admin 
>>Test if ssh is established between the local host and the VM 
Type command: ssh newvmcloud@10.0.2.15 
Note: The ip address 10.0.2.15 is a private IP address commonly used by default in 
VirtualBox virtual machines. VirtualBox default automatically assigns this specific IP to a 
guest operating system when using Network Address Translation (NAT) mode. 



>>Set port forwarding in the VM for the local host/PC to locate the VM 


Then test the VM with the configured port from the local host in the command interface 
Type command: ssh newvmcloud@10.0.2.15 -p 2222 

>>If connection can’t be established, then open PowerShell to diagnose custom secure 
SSH network and connection status 
Note: Test-NetConnection: A built-in Windows PowerShell tool used to diagnose network 
and connection status. -ComputerName 127.0.0.1: Targets the loopback address, which means your own local 
machine. -Port 2222: Specifies TCP port 2222, often used for custom Secure Shell (SSH) redirects, 
alternative remote management tools, or local developer applications -IP address 127.0.0.1 is the standard IPv4 loopback address on the localhost/PC 
Type command: Test-NetConnection -ComputerName 127.0.0.1 -port 2222 



>>If (TCP) TcpTestSucceeded : True, then a service or application is actively listening on 
port 2222 on the machine. (Reason why tcptestsucceeded=true is because localhost can 
listen to port 2222 on the VM  as SSH has been established and enabled on the VM to 
localhost) 
Then, 
>>Resolve localhost Dns ip address>>Verifies loopback and confirm that local machine 
correctly recognizes "localhost" as my own device with ip address 127.0.0.1 
Type command: Resolve-DnsName localhost



Once localhost is resolved>>then test SSH connection from localhost to VM 
Type command: ssh newvmcloud@127.0.0.1 -p 2222 
Confirm yes to connect 
Then, enter VM (newvmcloud) password 



When connection is successful, the localhost user on the command line changes to the 
VM user. Meaning I am now logged into the virtual machine 


SSH is enabled and confirmed that I am logged into my VM. 


