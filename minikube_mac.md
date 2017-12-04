# kubectl y Minikube for Mac

- [kubectl y Minikube for Mac](#kubectl-y-minikube-for-mac)
    - [1. Use Brew to install kubectl](#1-use-brew-to-install-kubectl)
    - [2. Verify that the install worked](#2-verify-that-the-install-worked)
    - [3. Use Brew to install Minikube](#3-use-brew-to-install-minikube)
    - [4. Use Brew to install the xhyve lightweight hypervisor for Mac](#4-use-brew-to-install-the-xhyve-lightweight-hypervisor-for-mac)
    - [5. Set the user owner of xhyve to be root](#5-set-the-user-owner-of-xhyve-to-be-root)
    - [6. Grant it the ability to setuid](#6-grant-it-the-ability-to-setuid)
    - [7. Start Minikube with the following command](#7-start-minikube-with-the-following-command)

## 1. Use Brew to install kubectl

```shell
$ brew install kubectl
Updating Homebrew…
```

This puts the kubectl binary in /usr/ local/ bin and makes it executable.

## 2. Verify that the install worked

```shell
$ kubectl version —client 
Client Version: version.Info{ Major:" 1", Minor:" 8"…
```

Now that we’ve installed the kubectl client, let’s install Minikube.

## 3. Use Brew to install Minikube

```shell
$ brew cask install minikube
 = = > Downloading https://storage.googlapis.com/minikube…
```

Provide your password if prompted.

## 4. Use Brew to install the xhyve lightweight hypervisor for Mac

Other Hypervisor options are available - VirtualBox and VMware Fusion - but we’re only showing *xhive*.

```shell
$ brew install docker-machine-driver-xhyve
= = > Downloading https:// homebrew.bintray.combottles…
```

## 5. Set the user owner of xhyve to be root

```shell
$ sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
```

## 6. Grant it the ability to setuid

```shell
$ sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
```

## 7. Start Minikube with the following command

```shell
$ minikube start --vm-driver=xhyve
Starting local Kubernetes cluster…
Starting VM…
```

minikube start is the simplest way to start Minikube. Specifying the `--vm-driver=xhyve` flag will force it to use the *xhyve* hypervisor instead of VirtualBox.