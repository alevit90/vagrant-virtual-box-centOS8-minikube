# vagrant-virtual-box-centOS8-minikube

Requirements:

1. Download the following repository

2. Download virtualbox through the following link and install it:

```shell
https://www.virtualbox.org/wiki/Downloads
```

3. Download vagrant via the following link and install it:

```shell
https://developer.hashicorp.com/vagrant/install?ajs_aid=9b11add8-dcb2-4b9e-bb1b-7714cbf79e32&product_intent=vagrant#windows 
```

Installation

Unzip the repository folder. Open powershell and then navigate to the folder where the Vagrantfile is present. For example:

```shell
cd C:\Users\username\Desktop\Laboratory\Vagrant
```
Run the following command to initialize a new Vagrant environment:

```shell
vagrant init
```
Replace the vagrant file that was created with the vagrant init command with the vagrant file from the following repository.
After that, run the following command to create a new Vagrant environment:

```shell
vagrant up
```

The following command via Vagrant creates a centOS8 virtual machine on virtual box. It also automatically installs minikube and its dashboard where it is possible to manage, create and modify resources on Kubernetes.

The script will take some time to get all the environment up. But once finished you will be able to access the dashboard via the following link:

```shell
http://192.168.33.10:8080/
```

If you want to connect to the centos machine it is possible using the following command:


```shell
vagrant ssh
```

To turn off the vm you can use this command:

```shell
vagrant halt
```
