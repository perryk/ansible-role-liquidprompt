Ansible Role Liquidprompt
=========

This role downloads and configures liquidprompt for current ansible user or a specified user. 

https://github.com/nojhan/liquidprompt.git

Requirements
------------

If setting this for a different user than ansible is running as then likely you need to prompt for sudo access.

```ansible-playbook -K playbook.yml```


Role Variables
--------------

liquidprompt_repo_url:  This defaults to primary liquidprompt repo on github. https://github.com/nojhan/liquidprompt.git
liquidprompt_repo_version: This defaults to master.


Example Playbook
----------------

Here is an example including how this can used to install this for a different user than Ansible is running as:

```yml
    - hosts: servers

      vars:
        - liquidprompt_user: 'bob'
      
      roles:
        - { role: ansible-role-liquidprompt, become: yes, become_user: "{{ liquidprompt_user }}" }
```

License
-------

MIT

Author Information
------------------

Perry Kollmorgen - https://github.com/perryk
