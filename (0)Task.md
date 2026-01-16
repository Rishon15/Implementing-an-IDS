Set up 6 Linux namespaces to isolate processes and networks, thus forming 6 different subnets.
From 5 of those subnets, you have to send all network traffic through Suricata to a service listening on the sixth subnet (this can be any service, such as SSH, FTP, SFTP, etc. Ensure you understand the protocol you have chosen and how it works in depth.)    

Configure Suricata to apply different rules to the incoming traffic from each of the five networks (subnet 1 will have a set of rules A, subnet 2 will have a set of rules B, subnet 3 will have rules C, etc).  

Run a different exploit from each of the networks to the 6th subnet, and show that the Suricata rules you have applied work and detect/block the exploit.  

The given task can be broken into 3 main parts 
1. Network Topology setup
2. Configure Suricata
3. Rules to alert & block traffic

The goal is to configure an Intrusion Detection System or IDS from scratch by simulating a network using a linux kernel provided feature called Namespaces. It helps in creating an isolated instance with its own resources, it has 8 types - 
1. **Mount Namespace** - isolated mount points, allowing different file views.
2. **Process-ID Namespace** - private set of process-is starting from pid 1 (init).
3. **Network Namespace** - isolated network devices, ip addresses, routing tables and ports.
4. **Inter-Process Communication Namespace** - isolated resources like POSIX and System V IPC.
5. **UNIX Time-Sharing Namespace** - isolated hostname and domain name.
6. **User Namespace** - isolated user and group IDs, enables privilege to unprivileged users withing container.
7. **Control Group Namespace** - isolated cgroup virtual filesystem.
8. **Time Namespace** - isolated system clocks (new).

In this task we will be using Network namespace to create isolated networking environment with its own IP address and subnet mask.