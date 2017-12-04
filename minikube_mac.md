# kubectl y Minikube for Mac

- [kubectl y Minikube for Mac](#kubectl-y-minikube-for-mac)
    - [Use Brew to install kubectl](#use-brew-to-install-kubectl)
    - [Verify that the install worked](#verify-that-the-install-worked)
    - [Use Brew to install Minikube](#use-brew-to-install-minikube)
    - [Use Brew to install the xhyve lightweight hypervisor for Mac](#use-brew-to-install-the-xhyve-lightweight-hypervisor-for-mac)
    - [Set the user owner of xhyve to be root](#set-the-user-owner-of-xhyve-to-be-root)
    - [Grant it the ability to setuid](#grant-it-the-ability-to-setuid)
    - [Start Minikube with the following command](#start-minikube-with-the-following-command)

## Use Brew to install kubectl

```shell
$ brew install kubectl
Updating Homebrew…
```

This puts the kubectl binary in /usr/ local/ bin and makes it executable.

## Verify that the install worked

```shell
$ kubectl version —client 
Client Version: version.Info{ Major:" 1", Minor:" 8"…
```

Now that we’ve installed the kubectl client, let’s install Minikube.

## Use Brew to install Minikube

```shell
$ brew cask install minikube
 = = > Downloading https://storage.googlapis.com/minikube…
```

Provide your password if prompted.

## Use Brew to install the xhyve lightweight hypervisor for Mac

Other Hypervisor options are available - VirtualBox and VMware Fusion - but we’re only showing *xhive*.

```shell
$ brew install docker-machine-driver-xhyve
= = > Downloading https:// homebrew.bintray.combottles…
```

## Set the user owner of xhyve to be root

```shell
$ sudo chown root:wheel $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
```

## Grant it the ability to setuid

```shell
$ sudo chmod u+s $(brew --prefix)/opt/docker-machine-driver-xhyve/bin/docker-machine-driver-xhyve
```

## Start Minikube with the following command

```shell
$ minikube start --vm-driver=xhyve
Starting local Kubernetes cluster…
Starting VM…
```

minikube start is the simplest way to start Minikube. Specifying the `--vm-driver=xhyve` flag will force it to use the *xhyve* hypervisor instead of VirtualBox.