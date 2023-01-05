
# Redshift

Ansible playbook that installs a set of offensive tools on Fedora Linux. The
playbook has been tested on Fedora Linux 37. Some of the tools that it installs
include:

- BloodHound
- AzureHound
- Burp Suite Community Edition
- Metasploit Framework
- CrackMapExec

It also installs common tools used in pentesting and red teaming such as Nmap,
Evil-WinRM, ldapsearch, and kerbrute. The playbook also includes two wordlists:
[RockYou](https://gitlab.com/kalilinux/packages/wordlists) and
[Seclists](https://github.com/danielmiessler/SecLists).

# Usage

To use the playbook, you must first install Ansible, clone the repository, and
run the playbook:

```
$ sudo dnf install ansible -y
$ git clone https://github.com/hakbyte/redshift
$ cd redshift
$ ansible-playbook -i hosts playbook.yml -K
```

> :memo: **Note:** in order to proceed you have to provide the root password
> (*BECOME* password in Ansible parlance).

You can customize the playbook by specifying the `-t` option to install only
certain tools or by using the `--skip-tags` option to exclude certain tools from
being installed. For instance, to only install Burp Suite, you can use the
following command:

```
$ ansible-playbook -i hosts playbook.yml -K -t burpsuite
```

This will run the playbook and only execute tasks that are associated with the
*burpsuite* tag. Meaning it will install only Burp Suite and not any of the
other tools that are included in the playbook.

Conversely, to install all of the tools included in the  playbook EXCEPT for
Burp Suite, you can use the `--skip-tags` option:

```
$ ansible-playbook -i hosts playbook.yml -K --skip-tags burpsuite
```
