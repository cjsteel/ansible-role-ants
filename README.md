
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
ants_state   : 'present'
ants_git_url : 'git://github.com/stnava/ANTs.git'
ants_bin_dir_path : '~/antsbin'
ants_src_dir_path : '~/ANTs'
ants_make_jobs: 1

# ants_cmake_command  : '/usr/bin/cmake' 
ants_cmake_source_dir : '/opt/ANTs_src'  # /home/aceadmin/ANTs
ants_cmake_binary_dir : '/opt/ants'      # /home/aceadmin/antsbin
```


Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbooks
----------------

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
