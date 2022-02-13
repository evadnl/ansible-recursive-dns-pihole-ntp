# ansible-recursive-dns-pihole-ntp
An Ansible Playbook that installs recursive DNS, Pihole and NTP.

# To-do:
- Install recursive DNS (Unbound)
- Install NTP
- Tidy things up in the playbook :))

# What does it do?
It currently installs a few things based on the settings in example.config.yml:

`hardening_enabled: true`

Setting the above to true will do the following:

1. Harden your SSH setup by removing the ability to login to ssh with passwords;
2. Copy over your public keys based on the URL or location you supply;
3. Install firewalld and add the nessacary ports to operate.

**IMPORTANT NOTE**: Failing in setting this up properly may result in your system becoming inaccassible. It's safer to set this to false if you do not know what this means!

`pihole_install: true`

This will install Docker and the Pi Hole Docker container.

`poe_hat: true`

If you run this on a Raspberry Pi with a POE+ Hat, you may have noticed the annoying sound coming from its fan. This will reduce the noise significantly. Thanks to Geerlingguy.


## Usage

1. Make a copy of example.config.yml and name it config.yml;
2. Go through the settings in this file and change accordingly. 
3. Make a copy of the example.inventory.ini to inventory.ini and change HOSTNAME, HOSTIP and SSHUSER
4. Run `ansible-playbook main.yml -K` the first time you run this and fill in the password when asked. Later on you do not need the -K option anymore.