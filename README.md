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

