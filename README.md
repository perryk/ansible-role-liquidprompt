Ansible Role Liquidprompt
=========

This role downloads and configures liquidprompt.
https://github.com/nojhan/liquidprompt.git

Requirements
------------

If setting this for a different user than ansible is running as then you need to prompt for sudo access.

```ansible-playbook -K playbook.yml```


Role Variables
--------------

liquidprompt_user_to_liquidify: This defaults to ansible_user_id which is the user ansible is connecting as.
liquidprompt_repo_url:  This defaults to primary liquidprompt repo on github. https://github.com/nojhan/liquidprompt.git
liquidprompt_repo_version: This defaults to master.


The most common use case is likely for installing liquidprompt as the user which ansible is connecting as. For this, all the above variables can be left as defaults and the -K option for sudo password doesn't need to entered when running the playbook.

I've often needed though to be installing liquidprompt for a different user, usually a service user I'm creating also during another earlier playbook so the liquidprompt_user_to_liquidify variable is available for this. Provided the user ansible is connecting as can use sudo, it should work however please note Ansible can run into permission problems in some cases when trying to run tasks as 1 unprivledged user as another unprivledged user. 


Example Playbook
----------------

Here is an example including how this can used to install this for a different user than Ansible is running as:

```yml
    - hosts: servers

      vars:
        - liquidprompt_user_to_liquidify: 'bob'
      
      roles:
        - perryk.liquidprompt
```

n.b the above works if this repo is downloaded using Ansible Galaxy, if cloning from this repo directly the role is called: ansible-role-liquidprompt

License
-------

MIT

Author Information
------------------

Perry Kollmorgen - https://github.com/perryk
