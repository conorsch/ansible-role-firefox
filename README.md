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

Example Playbook
----------------
```
- name: Install Firefox
  hosts: workstations
  roles:
    - role: conorsch.firefox
```

License
-------

MIT
