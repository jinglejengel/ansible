Requires Ansible 1.5+ and Pyrax

Set up an SSH key prior to use to make Ansible that much easier. Change the value of rax_key in group_vars/main.yml to the name of your key

```ini

#Example .raxpub file:
[rackspace_cloud]
username = myclouduser
api_key = XXXXXXXXXXXXXX

```

Topographical Breakdown:

```
# Where global variables go
./group_vars
  | # Full of the main goods, like your rax_pub, image, flavour, etc.
  └ ./group_vars/main.yml

./hosts
  └ # Contains only localhost, since we build dynamic hosts
  
./README.md
  └ # This README (:
  
./roles
  | # The roles for CentOS Hosts
  └ ./roles/centos
    | # Where we store CentOS variables
    └ ./roles/centos/defaults
      | # The CentOS vars file
      └ ./roles/centos/defaults/main.yml
    | # Where we store handlers like reboots  
    └ ./roles/centos/handlers
      | # The actual handlers yml
      └ ./roles/centos/handlers/main.yml
    | # Where we store tasks, such as config changes and installs
    └ ./roles/centos/tasks
      | # The actual tasks yml
      └ ./roles/centos/tasks/main.yml
    | # Where we store templates for configs
    └ ./roles/centos/templates
      | # The template for redis.conf on CentOS (Due to versioning)
      └ ./roles/centos/templates/redis.conf.j2
  
  | # The Roles to deploy on ALL hosts
  └ ./roles/common
    | # Where we store common variables
    └ ./roles/common/defaults
      | # The common vars files
      └ ./roles/common/defaults/main.yml
    | # Where we store handlers like reboots
    └ ./roles/common/handlers
      | # The actual handlers yml
      └ ./roles/common/handlers/main.yml
    | # Where we store tasks, such as config changes and installs
    └ ./roles/common/tasks
      | # The actual tasks yml
      └ ./roles/common/tasks/main.yml
    | # Where we store templates for configs
    └ ./roles/common/templates
        | # Sentinel placements, not working needs redis 2.8+
        | ./roles/common/templates/sentinel.conf.j2
        └ ./roles/common/templates/redis-sentinel.j2
  
  | # The roles to deploy on Ubuntu hosts
  └ ./roles/ubuntu
    | # Where we store Ubuntu variables
    └ ./roles/ubuntu/defaults
      | # The ubuntu vars file
      └ ./roles/ubuntu/defaults/main.yml
    | # Where we store handlers like reboots
    └ ./roles/ubuntu/handlers
    | # Where we store tasks, such as config changes and installs
    └ ./roles/ubuntu/tasks
      | # The actual tasks yml
      └ ./roles/ubuntu/tasks/main.yml
    | # Where we store temples for configs
    └ ./roles/ubuntu/templates
      | # The redis.conf for Ubuntu due to versioning issues
      └ ./roles/ubuntu/templates/redis.conf.j2
      
./site.yml
  └ # This is the main deployment!
```
