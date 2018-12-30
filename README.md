## If you are using Vagrant and facing performance hits while running web-server or unit tests, the solution can be using NFS. It is used for sharing folders between host and guest machines.

* Vagrant uses VirtualBox default sharing mechanism, which is very slow. After you'll switch to NFS, file access speed will increase by ~ 10 - 100 times.

## Installation
* On your local machine do 

```
sudo apt-get install nfs-kernel-server nfs-common portmap
```
* This comes pre-installed on Mac OS X 10.5+ (Leopard and higher).
* Inside your Vagrant box (guest machine) do 

```
sudo apt-get install nfs-common portmap
```
## Configuration
* Set :nfs option to true when configuring shared folder(s).

* config.vm.synced_folder "v-root", "/vagrant", :nfs => true
* NFS requires Private network, so you need to switch to it, in case you are using other network options, like :public_network (i.e. bridged).

* config.vm.network :private_network, ip: "10.11.12.13"
