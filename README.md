Supervisor
=========
Designed to only install supervisor and give you full controll over the configuration.

Only tested on Ubuntu 18.04.

Role Variables
--------------

    supervisor_disable (Default True)

    artisan_template - Where to find the template for artisan commands (Default role template)
    raw_template - Where to find the template for raw commands (Default role template)

    supervisor_command_user - default user to run command as
    supervisor_command_numprocs - default number of procs of command to run

    app_directory - where the artisan app is installed
                  - also where to find supervisor/supervisor_commands.yml

    Commands can be specified in 'supervisor_commands' map var from the included supervisor_commands.yml or default_vars

    Simple example:
    File: supervisor_commands.yml:
    artisan_commands:
      - my:artisan_cmd
      - my:artisan_cmd2
      - my:artisan_cmd3
    raw_commands:
      - /full/path/to/my/cmd


    With overrides in role group_vars example:
    (note the override vars are merged to those loaded from supervisor_commands.yml)
    File: group_vars/all/main.yml:
    artisan_commands_override:
       - cmd: artisan_cmd2
         user: myuser
         numprocs: 4
    raw_commands_override:
      - /additional/path/of/thing/to/run

    File: supervisor_commands.yml:
    artisan_commands:
      - my:artisan_cmd
      - my:artisan_cmd2
      - my:artisan_cmd3
    raw_commands:
      - /full/path/to/my/cmd


    With user/numproc overrides in supervisor_commands.yml example:
    (note: list item can be a string or map)
    File: supervisor_commands.yml:
    artisan_commands:
      - my:artisan_cmd
      - cmd: my:artisan_cmd2
        user: myuser
        numprocs: 3
      - cmd: my:artisan_cmd3
        numproc: 2


Disables supervisor on boot

Example Playbook
----------------

    - hosts: servers
      roles:
         - entanet-devops.supervisor
