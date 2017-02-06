
# ansible-role-ants

An Ansible role to install and manage Advanced Normalization Tools (ANTs) on Ubuntu 16.04.1LTS. ANTs computes high-dimensional mappings to capture the statistics of brain structure and function.  See the [FAQ page](https://github.com/stnava/ANTsTutorial/blob/master/handout/antsGithubExamples.Rmd) for more information about ANTs.

## Notes

ANTs takes a **very** long time to compile. You might want to start this before leaving the office.

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
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    - hosts: ants
      become: true
      gather_facts: true
      roles:
        - ants


License
-------

MIT


Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
