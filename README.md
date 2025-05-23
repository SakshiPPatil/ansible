# ansible
Anisible is open source automation tool used for software provisioning ,infrasturcture management and application deployment.It is developed by Red Hat.<br/>
It enables infrastructure as code, meaning it allows you to manage your infrastructure using code instead of manually configuring it. Ansible is known for its simplicity, ease of use, and strong focus on security and reliability.<br/> 
Ansible uses simple, human-readable scripts called playbooks to automate your tasks. You declare the desired state of a local or remote system in your playbook. Ansible ensures that the system remains in that state.<br/>

-----------------------------------------------------------------------------------------------------------------------------------------------------

**Key Features and Benefits:** <br/>

**Agentless:** <br/>
Ansible doesn't require any agents to be installed on the managed nodes, it uses SSH for communication.
<br/>
**Idempotent:** <br/>
Ansible ensures that each action is performed only once, even if the configuration is applied multiple times.
<br/>
**Declarative:** <br/>
Ansible uses a declarative language (YAML) to describe the desired state of your infrastructure, making it easier to understand and manage.
<br/>
**Scalable:** <br/>
Ansible can manage a large number of nodes and perform complex tasks efficiently. 
<br/>
**Open Source:** <br/>
Ansible is free to use and modify, making it accessible to a wide range of users. 
<br/>
**Community Supported:** <br/>
Ansible has a large and active community that provides support and resources. 
<br/>

<h3>Why anisible needed:</h3>
  Suppose we want to install appache server on multiple server at same time,then we use ssh But it is time consuming.So we use ansible to install apache server on multiple servers at 
  same time.

<h2>Working of ansible:</h2>
  Multiple servers connect to ansible server using ssh.For access to the multiple servers, ansible have inventory file(hosts), ansible.cfg file and modules.
  <br/>
  
  **Inventory File/hosts:**  It contains the information about hosts(virtual machines) like Ip address and name of the virtual machine.
  <br/>
  **ansible.cfg:** It contains the information about the configuration like path of the inventory file.
  <br/>
  **modules:** A small program that performs actions on a local machine, application programming interface (API), or remote host.
  <br/>
  **playbook:** configuration file 
  <br/>
  <br/>
  ![Screenshot 2025-05-19 190327](https://github.com/user-attachments/assets/5c287349-ecc3-4f69-acd7-b2b9d89ba396)

  <h3>Install ansible for Ubuntu server:</h3>
  $ sudo apt update
$ sudo apt install software-properties-common<br/>
$ sudo add-apt-repository --yes --update ppa:ansible/ansible<br/>
$ sudo apt install ansible<br/>

<h3> steps for ansible configuration</h3> <br/>

1)create the virtual machine(instance/host1) for connect to the ansible server <br/>
2)use ansible server- <br/>
  i) check ansible install or not ansible --version.<br/>
  ii) provide private IP address of host1 in the hosts file of ansible file (/etc/ansible/hosts).<br/>
  iii) copy private key of host1 machine in ansible server in /etc/ansible directory.<br/>
  iv) To take access of host1 server to ansible use command-<br/>
            **ansible -i hosts all -u ubuntu --private-key=./key_name -m shell -a hostname**  =this command provide the access of host1 machine.all the commands runs through host1 server and provide output through ansible server.<br/>
  v)provide the private key and user in the ansible.cfg file.then run command using<br/>
                  **ansible -i hosts all -m shell -a hostname** <br/>
  
  <h3>vi)create first.yml file</h3> <br/>
      write the first program<br/>

  **Use of different variables in ansible** <br/>

  **1)Global variable**: Accessible throughout the playbook and roles.<br/>
  **2)Local Variables** :refers to variables scoped only within a block, task, or role.<br/>
  **3)Register Variables**: Stores the output of a task in variable.<br/>
  **4)Prompt Variables**:Used to prompt the user for input at runtime.<br/>

  <h3>Example of variables</h3>

![Screenshot 2025-05-23 094725](https://github.com/user-attachments/assets/309daf4a-3585-49a7-ba0f-1aa29fb47b71)

![Screenshot 2025-05-23 094741](https://github.com/user-attachments/assets/304919ce-120c-43eb-a3df-801608185aa5)

**5)File variable(write var.txt file and use in .yml file)** :
    
![Screenshot 2025-05-23 100127](https://github.com/user-attachments/assets/f9dcfeec-c595-4a17-9720-ec7b5da32798)


![Screenshot 2025-05-23 100339](https://github.com/user-attachments/assets/f9b3ac1c-3278-47a3-af9c-e99640e4a1ca)

**6)command line variable**: It is used when pass the value at the runtime.<br/>
           commmand:  ansible-playbook -e variable_name=value filename <br/>

------------------------------------------------------------------------------------------------------------------------------

<h2>Modules</h2> <br/>

In Ansible, a core module refers to a built-in module that is maintained and supported by the Ansible development team. 
These modules are part of the main Ansible distribution and are considered stable, well-documented, and safe to use in production environments.
<br/>

**1)apt module for (ubuntu/debian):** <br/>
![Screenshot 2025-05-23 115243](https://github.com/user-attachments/assets/c6a875c7-af9b-4d1a-872e-79e0bbb26c65)

**2)yum module for(centos):** same as apt
**3)package module:** This is used when we dont know which AMI is used for the server is ubuntu or centos,then package modue perform task as per the os requirement.

![Screenshot 2025-05-23 115942](https://github.com/user-attachments/assets/5250819c-40a6-4653-a2a3-7139c6ddf9f8)

**4)systemd module:**  used for start,restart,stop service
  ![Screenshot 2025-05-23 120131](https://github.com/user-  attachments/assets/f4ef89d9-d530-40bf-9bf8-f7e6c81c6832)

**5)copy module:** To copy files from local to remote machines

![Screenshot 2025-05-23 121323](https://github.com/user-attachments/assets/ba708cfd-928c-41f7-8d15-1816cbb9852b)

---------------------------------------------------------------------------------------------------------------------------

**lineinfile module**:The lineinfile module in Ansible is used to add, modify, or remove lines in a file on a managed host. It's particularly useful for making idempotent changes to configuration files, such as adding configuration directives or ensuring certain lines are present or absent.<br/>

![Screenshot 2025-05-23 123652](https://github.com/user-attachments/assets/31dd3331-6e51-46bc-884a-79cd44208b5b)

**blockinfile module:** The blockinfile module allows you to manage multiple lines of text as a block, which is useful for:<br/>
      Inserting configuration snippets<br/>
      Managing multiple related lines together<br/>
      Making idempotent and easily reversible changes<br/> 
    
![Screenshot 2025-05-23 123657](https://github.com/user-attachments/assets/ca83180e-669a-4f69-9b1a-d7c53aa7655a)

 **tags in ansible:** In Ansible, tags allow you to run specific parts of your playbook selectively. This is very useful when:<br/>
            You're debugging and don’t want to run the entire playbook.<br/>
            You want to re-run only certain tasks (e.g., only restart a service).<br/>
            You want to group related tasks under a single label.<br/>

![Screenshot 2025-05-23 123702](https://github.com/user-attachments/assets/68d7e372-faec-403a-a459-8a291b0eb947)

---------------------------------------------------------------------------------------------------------------------------------------

<h2>Looping in ansible:</h2>
In Ansible, looping allows you to run a task multiple times with different items. This is useful for repetitive tasks such as:<br/>
  Installing multiple packages<br/>
  Creating multiple users<br/>
  Managing several files or services<br/>

![Screenshot 2025-05-23 124203](https://github.com/user-attachments/assets/5ce5f563-ae72-42ba-b6c3-7e9a356c359b) 



