# ELK-Stack-Project
Elk Stack Project

Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
 
 ![Week13](https://user-images.githubusercontent.com/82536342/137604648-27ad74d8-29f3-4819-bed5-02f9da8e5503.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the following ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

  Ansible/install-elk.yml   https://github.com/abdinoor11/ELK-Stack-Project/blob/6d02dd99cf716faa4a492340e3254f462c68c766/Ansible/install-elk.yml 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? 
Load balancer ensures the machines running DVWA are directly accessible from the internet. It also protects against unauthorized SSH access from outside the network. 
Jump Box ensures the other machines are only accessible from the docker container running within.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the VM metrics and system logs.
Filebeat: Monitors system logs
Metricbeat: Monitors VM metrics

The configuration details of each machine may be found below.

| Name                 | Function    | IP Address | Operating System |
|----------------------|-------------|------------|------------------|
| Jump-Box-Provisioner | Gateway     | 10.1.0.4   | Linux(Ubuntu)    |
| Web-1-New            | DVWA server | 10.1.0.5   | Linux(Ubuntu)    |
| Web-2-New            | DVWA sever  | 10.1.0.6   | Linux(Ubuntu)    |
| Elk Vm               | Elk Stack   | 10.0.0.4   | Linux(Ubuntu)    |


Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- home IP address

Machines within the network can only be accessed by Jumpbox.
-	Jumpbox can access the Elk VM. 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly available | Allowed IP Addresses |
|----------------------|--------------------|----------------------|
| Jump-Box-Provisioner | Yes                | 10.1.0.4             |
| Web-1-New            | No                 | 10.1.0.4             |
| Web-2-New            | No                 | 10.1.0.4             |
| Elk-VM               | No                 | 10.1.0.4             |


Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it reduces chances of human error when configuring the machine.


The playbook implements the following tasks:
-	install docker.io using apt
-	install python3-pip using apt
-	install docker module using pip
-	using systl, configure the VM to use more memory 
-	download and launch the docker container for the ELK stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.  

![docker-ps](https://user-images.githubusercontent.com/82536342/137604669-bc770b71-96da-4977-a693-8156f8fe7562.png)


Target Machines & Beats
This ELK server is configured to monitor the following machines:
-	Web-1-New
-	Web-2-New


