firefox
=========

Ansible role for installing Firefox Developer Edition on Debian and Ubuntu.
For Ubuntu, a PPA will be used, and for Debian, the latest tarball will be
downloaded, extracted, symlinked to /usr/local/bin.

Role Variables
--------------
```
# Ubuntu installation vars.
# Repo URL taken from: https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next
firefox_ubuntu_ppa: "deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu {{ ansible_lsb.name }} main"
firefox_ubuntu_ppa_apt_key_content: "{{ lookup('file', 'mozilla-firefox-apt-key.asc') }}"

# Apt preferences to ensure stable repos are prioritized. In the task
# list we'll install Firefox Quantum from the "testing" repo via
# a task parameter. Only relevant for Debian (Ubuntu uses PPA).
firefox_apt_preferences_content: |-
  Explanation: Uninstall or do not install any Debian-originated
  Explanation: package versions other than those in the stable distro
  Package: *
  Pin: release a=stable
  Pin-Priority: 900

  Package: *
  Pin: release o=Debian
  Pin-Priority: -10

# Tarball installation logic. Not currently used, documented for legacy reasons.
firefox_lang: en-US
firefox_arch: linux-x86_64
firefox_version: "57.0"
firefox_download_base_url: "https://download-installer.cdn.mozilla.net/pub/firefox/releases"
firefox_download_url: "{{ firefox_download_base_url }}/{{ firefox_version }}/{{ firefox_arch }}/{{ firefox_lang }}/firefox-{{ firefox_version }}.tar.bz2"
firefox_download_tarball: "{{ firefox_download_url|basename }}"
firefox_download_directory: /usr/local/src

# Base directory into which firefox will be installed. A subdirectory
# name "firefox" will be automatically created during tarball extraction.
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
