Requirements:

    - Vagrant https://www.vagrantup.com/downloads.html
    - Virtualbox https://www.virtualbox.org/wiki/Downloads

1 - Clone repository

```console
$ git clone git@github.com:krixapolinario/lab-vagrant-ansible.git
```

3 - Access directory with code

```console
$ cd lab-vagrant-ansible
```

4 - Start infrastructure

```console
$ sudo vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'centos/8'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'centos/7' version '1905.1' is up to date...
==> default: Setting the name of the VM: cicd_default_1565714204727_69186
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: You are trying to forward to privileged ports (ports <= 1024). Most
==> default: operating systems restrict this to only privileged process (typically
==> default: processes running as an administrative user). This is a warning in case
==> default: the port forwarding doesn't work. If any problems occur, please try a
==> default: port higher than 1024.
==> default: Forwarding ports...
    default: 80 (guest) => 80 (host) (adapter 1)
    default: 1936 (guest) => 1936 (host) (adapter 1)
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: No guest additions were detected on the base box for this VM! Guest
    default: additions are required for forwarded ports, shared folders, host only
    default: networking, and more. If SSH fails on this machine, please install
    default: the guest additions and repackage the box to continue.
    default:
    default: This is not an error message; everything may continue to work properly,
    default: in which case you may ignore this message.
==> default: Rsyncing folder: /Users/caboe/Vagrant/cicd/ => /vagrant
==> default: Running provisioner: ansible...
Vagrant has automatically selected the compatibility mode '2.0'
according to the Ansible version installed (2.8.2).

Alternatively, the compatibility mode can be specified in your Vagrantfile:
https://www.vagrantup.com/docs/provisioning/ansible_common.html#compatibility_mode

    default: Running ansible-playbook...

PLAY [Start CI CD] *************************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [config server] ***********************************************************
included: /Users/krixapolinario/github/lab-vagrant-ansible/config-server.yml for default

TASK [install epel-release] ****************************************************
changed: [default]

TASK [install dependences - yum] ***********************************************
changed: [default]

TASK [install dependences - pip] ***********************************************
changed: [default]

TASK [check docker-ce repository] **********************************************
ok: [default]

TASK [add docker-ce repository] ************************************************
changed: [default]

TASK [install docker-ce] *******************************************************
changed: [default]

TASK [start docker] ************************************************************
changed: [default]

TASK [start docker swarm] ******************************************************
changed: [default]

TASK [create docker compose to deploy stack] ***********************************
changed: [default]

TASK [deploy stack] ************************************************************
changed: [default]

TASK [remove temp files] *******************************************************
changed: [default] => (item=/tmp/docker-compose.yml)

PLAY RECAP *********************************************************************
default                    : ok=17   changed=14   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0`

```

5 - Access the services by browser:

Jenkins: http://localhost:8080

Sonar: http://localhost:9000
