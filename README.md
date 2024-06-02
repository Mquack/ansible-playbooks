# ansible-playbooks
Useful Ansible playbooks

Create a file named "inventory" with the IP of the computers you want to handle with the scripts.
Mine look something like this:

all:
  hosts:
    192.168.7.45
    192.168.7.46
    192.168.7.47
    192.168.7.48
    192.168.7.49

newUsers:
  hosts:
    192.168.7.50

Run the playbooks with command:
ansible-playbook -i inventory -u <username> <nameOfPlaybook.yml>

-i specifies the inventory file.
-u specifies the username that should connect to the computers. This user should be able to connect via ssh to the computers, if possible via ssh-copy-id <username>@192.169.7.XX to avoid PW login each time.


newCTBook.yml - updates apt for the new container and installs both curl and perl. It also creates a new user named <hostname>-user and the corresponding home folder.
updateBook.yml just runs a apt update && apt upgrade with a bit more output and reports back if any of the computers need a reboot.
installBook.yml just installs curl and perl. More applications can be added to the list if needed in the future.
