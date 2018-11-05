Supervisor
=========
Designed to only install supervisor and give you full controll over the configuration.

Only tested on Ubuntu 18.04.

Role Variables
--------------

    supervisor_disable (Default True)

Disables supervisor on boot

Example Playbook
----------------

    - hosts: servers
      roles:
         - entanet-devops.supervisor