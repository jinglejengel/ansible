Requires Ansible 1.5+ and Pyrax

Set up an SSH key prior to use to make Ansible that much easier. Change the value of rax_key in group_vars/main.yml to the name of your key

-----------------------

Example .raxpub file:

[rackspace_cloud]

username = myclouduser

api_key = XXXXXXXXXXXXXX

-----------------------
