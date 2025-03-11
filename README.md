<img src="https://raw.githubusercontent.com/geerlingguy/mac-dev-playbook/master/files/Mac-Dev-Playbook-Logo.png" width="250" height="156" alt="Mac Dev Playbook Logo" />

# Mac Development Ansible Playbook

[![CI][badge-gh-actions]][link-gh-actions]

This playbook installs and configures most of the software I use on my Mac for web and software development. Some things in macOS are slightly difficult to automate, so I still have a few manual installation steps, but at least it's all documented here.


## Mac Setup
### Requirements
- A mac *(no shit sherlock)*
- 16GB USB thumb drive
- An Internet connection
  
### Internet Recovery (if you haven't already)
On reboot, do `⌘R` to go into Internet Recovery.  Because I am using the Mac that I found next to a dumpster, it will try to install *macOS 10.9 Mavericks*.  We don't want that!

### macOS Mavericks
Install macOS mavericks, and do basic setup
  - username
  - name
  - etc

Then, download the DMG for macOS Sierra, and install it--we need at least Sierra to run OpenCore Legacy Patcher.

### macOS Sierra
You'll want to go to the [OpenCore website](https://dortania.github.io/OpenCore-Legacy-Patcher/INSTALLER.html#downloading-the-installer) to download the OpenCore Legacy Patcher.

Download and open the `.app` file.  You'll need at least a 16GB USB thumb drive.

Flash macOS Ventura to your thumb drive, and install OpenCore.

Reboot, and boot off of the USB stick.  Install Ventura.

### macOS Ventura
  1. Ensure Apple's command line tools are installed (`xcode-select --install` to launch the installer).
  2. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):

     1. Run the following command to add Python 3 to your $PATH: `export PATH="$HOME/Library/Python/3.9/bin:/opt/homebrew/bin:$PATH"`
     2. Upgrade Pip: `sudo pip3 install --upgrade pip`
     3. Install Ansible: `pip3 install ansible`

  3. Clone or download this repository to your local drive.
  4. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible roles.
  5. Run `ansible-playbook main.yml --ask-become-pass` inside this directory. Enter your macOS account password when prompted for the 'BECOME' password.

> Note: If some Homebrew commands fail, you might need to agree to Xcode's license or fix some other Brew issue. Run `brew doctor` to see if this is the case.

[badge-gh-actions]: https://github.com/geerlingguy/mac-dev-playbook/actions/workflows/ci.yml/badge.svg
[link-gh-actions]: https://github.com/geerlingguy/mac-dev-playbook/actions/workflows/ci.yml
