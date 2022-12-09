<font size="1">8 min</font>

# Vagrant boxes

**Boxes** are the package format for [Vagrant](https://developer.hashicorp.com/vagrant/docs) environments. You specify a box environment and operating configurations in your `Vagrantfile`. You can use a box on any supported platform to bring up identical working environments.

**Boxes** require a [provider](https://developer.hashicorp.com/vagrant/docs), a virtualization product, to operate. Before you can use a box, ensure that you have properly installed a [supported provider](https://developer.hashicorp.com/vagrant/docs).</br></br>

So far we have seen that when executing the `vagrant init` command we had to specify the box to use, in our case `ubuntu/focal64`.</br></br>

````sh
vagrant init ubuntu/focal64 -m
````
</br>

Once this command is executed we see that a Vagrantfile has been generated.</br></br>

````sh
# All Vagrant configuration is done below. 
# The "2" in Vagrant.configure configures the configuration version.
Vagrant.configure("2") do |config|
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/focal64"
end
````
</br>

As we will see in the [next section](/05-machine-settings/README.md), settings within `config.vm` modify the configuration of the machine that [Vagrant](https://developer.hashicorp.com/vagrant/docs) manages. In this case, `config.vm.box` allows us to configures what box the machine will be brought up against. The value here should be the name of an installed box or a shorthand name of a box in [HashiCorp's Vagrant Cloud](https://app.vagrantup.com/boxes/search).</br></br>

## Discover boxes

The quickest way to get started is to select a pre-defined box environment from the publicly available catalog on [Vagrant Cloud](https://app.vagrantup.com/boxes/search). You can also add and share your own customized boxes on [Vagrant Cloud](https://app.vagrantup.com/boxes/search).

If we access the [Vagrant Cloud Website](https://app.vagrantup.com/boxes/search), we will see a screen similar to this.</br></br>

![](/04-boxes-and-providers/img/vagrant-cloud.png)</br></br>


Let's imagine that we want to create a virtual machine with **Centos 7** using **Virtualbox**. We can use the [Vagrant Cloud](https://app.vagrantup.com/boxes/search) browser in this way.</br></br>

![](/04-boxes-and-providers/img/vagrant-cloud-centos.png)</br></br>

The box's description includes instructions on how to add it to an existing Vagrantfile or initiate it as a new environment on the command-line.</br></br>

## Using Centos 7 Box

Continuing with the previous example, we can use the `Centos` image using the `vagrant init` command.</br></br>

````sh
vagrant init bento/centos-7.2 --box-version 2.3.1 -m
````
</br>

In this case, we are using `--box-version` flag to determinate specific version of the box.</br></br>

````sh
Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.2"
  config.vm.box_version = "2.3.1"
end
````
</br>

## Managing boxes

The `vagrant box` CLI utility provides all the functionality for box management.</br></br>

### List boxes

Using the `vagrant box list` command we can see a list of installed boxes. Let's see an example:</br></br>

````sh
vagrant box list
````
</br>

At this point in the guide, we should have two boxes installed: `ubuntu/focal64` and `bento/centos-7.2`.</br></br>

````sh
bento/centos-7.2 (virtualbox, 2.3.1)                      ubuntu/focal64   (virtualbox, 20221201.0.0)
````
</br>

### Remove a box

Using the `vagrant box remove` command we can remove an installed box. Let's see an example:</br></br>

````sh
vagrant box remove bento/centos-7.2
````
</br>

Once the command is executed, we should see a message similar to this.</br></br>

````sh
Removing box 'bento/centos-7.2' (v2.3.1) with provider 'virtualbox'...
````
</br>

At this point, if we run the vagrant box list command again, we will see that now we only have the ubuntu box.</br></br>

````sh
ubuntu/focal64 (virtualbox, 20221201.0.0)
````
</br>

### Add a box

In some cases we may be interested in adding a box to the system but we do not want to create a **Vagrantfile**. This is possible using the `vagrant add` command. let's see an example.</br></br>

````sh
vagrant add bento/centos-7.2
````
</br>

Once the command is executed, we should see a message similar to this.</br></br>


````sh
==> box: Loading metadata for box 'bento/centos-7.2'
    box: URL: https://vagrantcloud.com/bento/centos-7.2
This box can work with multiple providers! The providers that it 
can work with are listed below. Please review the list and choose                                                       the provider you will be working with.                                                   

1) parallels
2) virtualbox
3) vmware_desktop

Enter your choice: 
````
</br>

Enter a `2` and press enter.</br></br>

````sh
==> box: Adding box 'bento/centos-7.2' (v2.3.1) for provider: virtualbox
    box: Downloading: https://vagrantcloud.com/bento/boxes/centos-7.2/versions/2.3.1/providers/virtualbox.box
    box:
==> box: Successfully added box 'bento/centos-7.2' (v2.3.1) for 'virtualbox'!
````
</br>

If we execute the `vagrant box list` command again, we will see that we have the two boxes available again.</br></br>

````sh
bento/centos-7.2 (virtualbox, 2.3.1)
ubuntu/focal64   (virtualbox, 20221201.0.0)
````
</br>


Finally, we can avoid the dialog when executing the `vagrant box add` command using the `--provider` flag.</br></br>

````sh
vagrant box add bento/centos-7.2 --provider=virtualbox
````
</br>

That's all, I hope you found it useful. In the next section we will talk about [machine settings](/05-machine-settings/README.md).


