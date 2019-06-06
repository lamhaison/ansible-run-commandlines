Role Name
=========

If you want run some commandline on the remote server and get the result without acessing to each servers.

Requirements
------------
No need any module

Role Variables
--------------
- printing_stdout(default true): You want printing stdout of the command lines
- printing_stderr(default is false): You want priting stderr of the command lines. Generally, when you want to get the result of the commandline even it was error when running. It will combine with ignore_error: yes
- ignore_error(default is no): If you want stop if you get any error when running command lines.

Dependencies
------------
ansible-galaxy install lamhaison.ansible_run_commandlines

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
- hosts:
    - all
  become: true
  become_user: root
  vars:
    - ignore_error: yes
    - printing_stderr: true
    - commandlines: |
         hostname && uname -srv && id;date;uname -n

  tasks:
    - name: Running commandline on remote server
      include_role:
        name: ansible-run-commandlines
        tasks_from: main
      vars:
        - execute_command_line: "{{ item }}"
      with_items: "{{ commandlines }}"
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
