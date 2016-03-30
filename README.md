firefox
=========

Ansible role for installing Firefox Developer Edition on Debian and Ubuntu.
For Ubuntu, a PPA will be used, and for Debian, the latest tarball will be
downloaded, extracted, symlinked to /usr/local/bin.

Role Variables
--------------

```
# defaults file for firefox
firefox_lang: en-US
firefox_arch: linux64
firefox_download_url: "https://download.mozilla.org/?product=firefox-aurora-latest-ssl&os={{ firefox_arch }}&lang={{ firefox_lang }}"
firefox_download_directory: /usr/local/src
firefox_download_tarball: "firefox-aurora-latest-{{ firefox_arch }}-{{ firefox_lang }}.tar.bz2"

# Base directory into which firefox will be installed.
# A subdirectory named "firefox" will be created during tarball extraction.
firefox_install_directory: /opt

firefox_create_symlink: true
firefox_symlink_src: "{{ firefox_install_directory }}/firefox/firefox"
firefox_symlink_dest: /usr/local/bin/firefox
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
