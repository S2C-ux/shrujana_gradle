open Ubuntu 
type: 

1.sudo adduser shrujana
it will ask password give any you want
if again new password asked give that only same password.
press enter for everything don't give anything 

2.ssh -keygen
  y
 enter
3. sudo apt update 
4. sudo apt install ansible -y
5. ansible --version 
6. vi inventory.ini
    now the blank page will come in that at first line type
    localhost ansible_connection=local
    at last line 
    :WQ
    (it will come to terminal)
 7. ansible-inventory -i inventory.ini --list
 8. ansible all -i inventory.ini -m ping
 9. nano basic_playbook.yml
 now the blank page will open in that type

---
name: My First Playbook
        hosts: all
        tasks:
name: Print a message
                ansible.builtin.debug:
                msg: "Hello from Earth!”

after typing this ctrl+o
                  enter 
                  ctrl+x

10. ansible-playbook -i inventory.ini basic_playbook.yml
11. nano basic_playbook.yml                  

👉in that page type this
---
name: Create a directory
hosts: localhost
tasks:
name: Create the 'my_test_directory'
ansible.builtin.file:
path: /tmp/my_test_directory
state: directory

after typing this ctrl+o
                  enter 
                  ctrl+x 

12. ansible-playbook -i inventory.ini basic_playbook.yml                  
13. ls /twp



 
 
    
