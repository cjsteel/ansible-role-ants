
# ansible-role-ants

An Ansible role to install and manage Advanced Normalization Tools (ANTs) on Ubuntu 16.04.1LTS. ANTs computes high-dimensional mappings to capture the statistics of brain structure and function.  See the [FAQ page](https://github.com/stnava/ANTsTutorial/blob/master/handout/antsGithubExamples.Rmd) for more information about ANTs.

## Notes

ANTs takes a **very** long time to compile. You might want to start this before leaving the office.

## Resources

* ( https://github.com/stnava/ANTs/releases )[ https://github.com/stnava/ANTs/releases ]
* [ updated ANTs compile instructions: ITKv4]( https://brianavants.wordpress.com/2012/04/13/updated-ants-compile-instructions-april-12-2012/ ) 



Requirements
------------

```shell
sudo apt-get update
sudo apt-get install git
sudo apt-get install cmake-curses-gui
sudo apt-get install zlib1g-dev
```


Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in

 ### defaults/main.yml

```yaml
---
# roles/ants/defaults/main.yml

ants_state         : 'present'
ants_build         : true
ants_reboot_target : false
ants_ssh_port      : 22

ants_git_version        : 'v2.1.0'
ants_git_url            : 'git://github.com/stnava/ANTs.git'
ants_dir_path           : '/usr/bin/ants'
ants_src_path           : '/usr/src/ANTs'
#ants_dir_path           : '~/bin/ants' # Adjust ants_owner
#ants_src_path           : '~/src/ANTs' # and ants_group...

ants_directory_state    : 'directory'
ants_owner              : 'root'
ants_group              : 'root'
ants_mode               : '0755'

ants_cmake_command     : '/usr/bin/ccmake'
ants_cmake_binary_dir  : '{{ ants_dir_path }}'
ants_cmake_source_dir  : '{{ ants_src_path }}'
ants_cmake_jobs        : 1
```


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.


Example Playbooks
----------------

### project_name/ants.yml

The roles playbook might look something like this:

```shell
---
# file: {{ project_name }}/ants.yml
- hosts: ants
  become: true
  gather_facts: true
  pre_tasks:

    - set_fact: fact_controller_user="{{ lookup('env','USER') }}"
    - debug: var=fact_controller_user

    - set_fact: fact_controller_home="{{ lookup('env','HOME') }}"
    - debug: var=fact_controller_home

  roles:

    - ants
```

Copy the example role playbook and edit if required.

```shell
cp roles/ants/files/ants.yml .
```

### projects/systems.yml

Example of projects main playbook:

```shell
---
- hosts: all
  become: false
  gather_facts: false

- include: ants.yml
```

### project/ants.yml

Create an example playbook using the roles included default. From the projects main directory:

```shell
cp roles/ants/files/ants.yml .
```

#### content example:

    ---
    - hosts: ants
      become: true
      gather_facts: false
      roles:
        - ants

## ansible-playbook command

```shell
ansible-playbook -i inventory/dev systems.yml
```


License
-------

MIT


Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
