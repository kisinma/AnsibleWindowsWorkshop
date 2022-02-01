# Welcome to the Ansible for Windows Automation workshop!

![Ansible Automation Platform](https://raw.githubusercontent.com/ansible/workshops/master/images/rh-ansible-automation-platform.png)

Advanced playbooks

What is happening here!? (Note 1)

    vars: You’ve told Ansible the next thing it sees will be a variable name
    
    - iis_sites You are defining a list-type variable called iis_sites. What follows is a list of each site with it’s related variables
    - win_file: This module is used to create, modify, delete files, directories, and symlinks. You are telling Ansible that this will expand into a list item. Each item has several variables like name, port, and path.
    - with_items: This is your loop which is instructing Ansible to perform this task on every item in iis_sites
    - notify: restart iis service This statement is a handler, so we’ll come back to it in Section 3.
    
So… what did I just write? (Note 2)

    win_firewall_rule: This module is used to create, modify, and update firewall rules. Note in the case of AWS there are also security group rules which may impact communication. We’ve opened these for the ports in this example.

    - win_template: This module specifies that a jinja2 template is being used and deployed. used in Ansible to transform data inside a template expression, i.e. filters.
    - debug: Again, like in the iis_basic playbook, this task displays the URLs to access the sites we are creating for this exercise
    
    
You can’t have a former if you don’t mention the latter (Note 3)

    handler: This is telling the play that the tasks: are over, and now we are defining handlers:. Everything below that looks the same as any other task, i.e. you give it a name, a module, and the options for that module. This is the definition of a handler.

    notify: restart iis service …and here is your latter. Finally! The notify statement is the invocation of a handler by name. Quite the reveal, we know. You already noticed that you’ve added a notify statement to the win_iis_website task, now you know why.


