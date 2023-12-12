```
Описание домашнего задания
Основная часть:
- `vagrant up` должен поднимать 2 настроенных виртуальных машины
(сервер NFS и клиента) без дополнительных ручных действий;
- на сервере NFS должна быть подготовлена и экспортирована
директория;
- в экспортированной директории должна быть поддиректория
с именем __upload__ с правами на запись в неё;
- экспортированная директория должна автоматически монтироваться
на клиенте при старте виртуальной машины (systemd, autofs или fstab -
любым способом);
- монтирование и работа NFS на клиенте должна быть организована
с использованием NFSv3 по протоколу UDP;
- firewall должен быть включен и настроен как на клиенте,
так и на сервере.
```
```
Файл Vagrant находится в репозитории и последовательно разворачивает сервера nfss и nfsс.
Скрипты для каждого из серверов выполняют требуемое задание.
Результат выполнения Vagrant up ниже.
Ещё ниже проверка работоспособности сервиса на машинах.

```

```
Bringing machine 'nfss' up with 'virtualbox' provider...
Bringing machine 'nfsc' up with 'virtualbox' provider...
==> nfss: Importing base box 'centos/7'...
==> nfss: Matching MAC address for NAT networking...
==> nfss: Checking if box 'centos/7' version '2004.01' is up to date...
==> nfss: Setting the name of the VM: nfs1_nfss_1702414966036_73967
==> nfss: Clearing any previously set network interfaces...
==> nfss: Preparing network interfaces based on configuration...
    nfss: Adapter 1: nat
    nfss: Adapter 2: intnet
==> nfss: Forwarding ports...
    nfss: 22 (guest) => 2222 (host) (adapter 1)
==> nfss: Running 'pre-boot' VM customizations...
==> nfss: Booting VM...
==> nfss: Waiting for machine to boot. This may take a few minutes...
    nfss: SSH address: 127.0.0.1:2222
    nfss: SSH username: vagrant
    nfss: SSH auth method: private key
    nfss: 
    nfss: Vagrant insecure key detected. Vagrant will automatically replace
    nfss: this with a newly generated keypair for better security.
    nfss: 
    nfss: Inserting generated public key within guest...
    nfss: Removing insecure key from the guest if it's present...
    nfss: Key inserted! Disconnecting and reconnecting using new SSH key...
==> nfss: Machine booted and ready!
==> nfss: Checking for guest additions in VM...
    nfss: No guest additions were detected on the base box for this VM! Guest
    nfss: additions are required for forwarded ports, shared folders, host only
    nfss: networking, and more. If SSH fails on this machine, please install
    nfss: the guest additions and repackage the box to continue.
    nfss: 
    nfss: This is not an error message; everything may continue to work properly,
    nfss: in which case you may ignore this message.
==> nfss: Setting hostname...
==> nfss: Configuring and enabling network interfaces...
==> nfss: Rsyncing folder: /home/max/nfs1/ => /vagrant
==> nfss: Running provisioner: shell...
    nfss: Running: /tmp/vagrant-shell20231213-18960-l8fram.sh
    nfss: Loaded plugins: fastestmirror
    nfss: Determining fastest mirrors
    nfss:  * base: mirror.serverius.net
    nfss:  * extras: mirror.serverius.net
    nfss:  * updates: centos.mirror.triple-it.nl
    nfss: Resolving Dependencies
    nfss: --> Running transaction check
    nfss: ---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
    nfss: ---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7.2 will be an update
    nfss: --> Finished Dependency Resolution
    nfss: 
    nfss: Dependencies Resolved
    nfss: 
    nfss: ================================================================================
    nfss:  Package          Arch          Version                    Repository      Size
    nfss: ================================================================================
    nfss: Updating:
    nfss:  nfs-utils        x86_64        1:1.3.0-0.68.el7.2         updates        413 k
    nfss: 
    nfss: Transaction Summary
    nfss: ================================================================================
    nfss: Upgrade  1 Package
    nfss: 
    nfss: Total download size: 413 k
    nfss: Is this ok [y/d/N]: Is this ok [y/d/N]: Exiting on user command
    nfss: Your transaction was saved, rerun it with:
    nfss:  yum load-transaction /tmp/yum_save_tx.2023-12-12.21-03.e53IL7.yumtx
    nfss: Created symlink from /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service to /usr/lib/systemd/system/firewalld.service.
    nfss: Created symlink from /etc/systemd/system/multi-user.target.wants/firewalld.service to /usr/lib/systemd/system/firewalld.service.
    nfss: success
    nfss: success
    nfss: Created symlink from /etc/systemd/system/multi-user.target.wants/nfs-server.service to /usr/lib/systemd/system/nfs-server.service.
==> nfsc: Importing base box 'centos/7'...
==> nfsc: Matching MAC address for NAT networking...
==> nfsc: Checking if box 'centos/7' version '2004.01' is up to date...
==> nfsc: Setting the name of the VM: nfs1_nfsc_1702415041195_17350
==> nfsc: Fixed port collision for 22 => 2222. Now on port 2200.
==> nfsc: Clearing any previously set network interfaces...
==> nfsc: Preparing network interfaces based on configuration...
    nfsc: Adapter 1: nat
    nfsc: Adapter 2: intnet
==> nfsc: Forwarding ports...
    nfsc: 22 (guest) => 2200 (host) (adapter 1)
==> nfsc: Running 'pre-boot' VM customizations...
==> nfsc: Booting VM...
==> nfsc: Waiting for machine to boot. This may take a few minutes...
    nfsc: SSH address: 127.0.0.1:2200
    nfsc: SSH username: vagrant
    nfsc: SSH auth method: private key
    nfsc: 
    nfsc: Vagrant insecure key detected. Vagrant will automatically replace
    nfsc: this with a newly generated keypair for better security.
    nfsc: 
    nfsc: Inserting generated public key within guest...
    nfsc: Removing insecure key from the guest if it's present...
    nfsc: Key inserted! Disconnecting and reconnecting using new SSH key...
==> nfsc: Machine booted and ready!
==> nfsc: Checking for guest additions in VM...
    nfsc: No guest additions were detected on the base box for this VM! Guest
    nfsc: additions are required for forwarded ports, shared folders, host only
    nfsc: networking, and more. If SSH fails on this machine, please install
    nfsc: the guest additions and repackage the box to continue.
    nfsc: 
    nfsc: This is not an error message; everything may continue to work properly,
    nfsc: in which case you may ignore this message.
==> nfsc: Setting hostname...
==> nfsc: Configuring and enabling network interfaces...
==> nfsc: Rsyncing folder: /home/max/nfs1/ => /vagrant
==> nfsc: Running provisioner: shell...
    nfsc: Running: /tmp/vagrant-shell20231213-18960-bctite.sh
    nfsc: Loaded plugins: fastestmirror
    nfsc: Determining fastest mirrors
    nfsc:  * base: mirror.serverius.net
    nfsc:  * extras: mirror.serverius.net
    nfsc:  * updates: mirror.wd6.net
    nfsc: Resolving Dependencies
    nfsc: --> Running transaction check
    nfsc: ---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
    nfsc: ---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7.2 will be an update
    nfsc: --> Finished Dependency Resolution
    nfsc: 
    nfsc: Dependencies Resolved
    nfsc: 
    nfsc: ================================================================================
    nfsc:  Package          Arch          Version                    Repository      Size
    nfsc: ================================================================================
    nfsc: Updating:
    nfsc:  nfs-utils        x86_64        1:1.3.0-0.68.el7.2         updates        413 k
    nfsc: 
    nfsc: Transaction Summary
    nfsc: ================================================================================
    nfsc: Upgrade  1 Package
    nfsc: 
    nfsc: Total download size: 413 k
    nfsc: Is this ok [y/d/N]: Is this ok [y/d/N]: Exiting on user command
    nfsc: Your transaction was saved, rerun it with:
    nfsc:  yum load-transaction /tmp/yum_save_tx.2023-12-12.21-05.GqHnV7.yumtx
    nfsc: Created symlink from /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service to /usr/lib/systemd/system/firewalld.service.
    nfsc: Created symlink from /etc/systemd/system/multi-user.target.wants/firewalld.service to /usr/lib/systemd/system/firewalld.service.
```

Проверка сервера
```
max@max-VirtualBox:~/nfs$ vagrant ssh nfss
Last login: Tue Dec 12 19:02:21 2023 from 10.0.2.2

[vagrant@nfss ~]$ systemctl status nfs
● nfs-server.service - NFS server and services
   Loaded: loaded (/usr/lib/systemd/system/nfs-server.service; enabled; vendor preset: disabled)
  Drop-In: /run/systemd/generator/nfs-server.service.d
           └─order-with-mounts.conf
   Active: active (exited) since Tue 2023-12-12 20:08:20 UTC; 2min 7s ago
  Process: 809 ExecStartPost=/bin/sh -c if systemctl -q is-active gssproxy; then systemctl reload gssproxy ; fi (code=exited, status=0/SUCCESS)
  Process: 787 ExecStart=/usr/sbin/rpc.nfsd $RPCNFSDARGS (code=exited, status=0/SUCCESS)
  Process: 784 ExecStartPre=/usr/sbin/exportfs -r (code=exited, status=0/SUCCESS)
 Main PID: 787 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/nfs-server.service

[vagrant@nfss ~]$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2023-12-12 20:08:14 UTC; 3min 0s ago
     Docs: man:firewalld(1)
 Main PID: 401 (firewalld)
   CGroup: /system.slice/firewalld.service
           └─401 /usr/bin/python2 -Es /usr/sbin/firewalld --nofork --nopid

[vagrant@nfss ~]$ sudo exportfs -s
/srv/share  192.168.56.11/32(sync,wdelay,hide,no_subtree_check,sec=sys,rw,secure,root_squash,no_all_squash)

[vagrant@nfss ~]$ showmount -a 192.168.56.10
All mount points on 192.168.56.10:
192.168.56.11:/srv/share

[vagrant@nfss ~]# cd /srv/share/upload/
[vagrant@nfss upload]# touch file
```

Проверка клиента
```
max@max-VirtualBox:~/nfs$ vagrant ssh nfsc
Last login: Tue Dec 12 19:35:08 2023 from 10.0.2.2
[vagrant@nfsc]$ mount |grep mnt
systemd-1 on /mnt type autofs (rw,relatime,fd=47,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=25389)
192.168.56.10:/srv/share/ on /mnt type nfs (rw,relatime,vers=3,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,timeo=11,retrans=3,sec=sys,mountaddr=192.168.56.10,mountvers=3,mountport=20048,mountproto=udp,local_lock=none,addr=192.168.56.10)

[vagrant@nfsc ~]# cd /mnt/upload
[vagrant@nfsc upload]# ll  
total 0
-rw-r--r--. 1 root root 0 Dec 12 19:49 file
[vagrant@nfsc upload]# touch client_file
[vagrant@nfsc upload]$ ll
total 0
-rw-r--r--. 1 nfsnobody nfsnobody 0 Dec 12 19:50 client_file
-rw-r--r--. 1 root      root      0 Dec 12 19:49 file
```