<font size="2">10 minutes</font>

# Getting Started

In this tutorial, you will create your first development environment with [Vagrant](https://developer.hashicorp.com/vagrant/docs). This quick start provides a brief introduction to [Vagrant](https://developer.hashicorp.com/vagrant/docs), its prerequisites, and an overview of the most important [Vagrant](https://developer.hashicorp.com/vagrant/docs) commands to understand.</br></br>


## Create a directory

Make a new directory for the project you will work on throughout these tutorials.</br></br>

````sh
mkdir getting-started
````
</br>

Once the directory is created, we will access it with the `cd` command.</br></br>

````sh
cd getting-started
````
</br>

The first step to configure any [Vagrant](https://developer.hashicorp.com/vagrant/docs) project is to create a [Vagrantfile](https://developer.hashicorp.com/vagrant/docs/vagrantfile). The [Vagrantfile](https://developer.hashicorp.com/vagrant/docs/vagrantfile) allows you to describe the kind of machine and resources you need to run your project, as well as what software to install and how you want to access it.</br></br>

## Initialize a Project Directory

Vagrant has a built-in command for initializing a project, `vagrant init`, which can take a box name as arguments.</br></br>

````sh
vagrant init ubuntu/focal64 -m
````
</br>

The above command allows us to initialize the directory and specify the box to use, in this case `ubuntu/focal64`. The `m` flag allow as to create a `Vagrantfile` that does not contain the instructional comments that the normal `Vagrantfile` contains. Once the command is executed we will see a message like this.</br></br>

````sh
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
````
</br>

You now have a `Vagrantfile` in your current directory. You can validate the creation of the `Vagrantfile` with the `ls` command.</br></br>

````sh
-a----        07/12/2022     19:41           3090 Vagrantfile
````
</br>

## Bring up a virtual machine

Now that you have initialized your project and configured a box for it to use, it is time to boot your first [Vagrant](https://developer.hashicorp.com/vagrant/docs) environment. Run the following command from your terminal:</br></br>

````sh
vagrant up
````
</br>

In less than a minute, this command will finish and you will have a virtual machine running `Ubuntu`.</br></br>

````sh
Bringing machine 'default' up with 'virtualbox' provider...                                                             
==> default: Importing base box 'ubuntu/focal64'...                                                                     
==> default: Matching MAC address for NAT networking...                                                                 
==> default: Checking if box 'ubuntu/focal64' version '20221201.0.0' is up to date...                                   
==> default: A newer version of the box 'ubuntu/focal64' for provider 'virtualbox' is                                   
==> default: available! You currently have version '20221201.0.0'. The latest is version                                
==> default: '20221202.0.1'. Run `vagrant box update` to update.                                                        
==> default: Setting the name of the VM: 01-getting-started_default_1670399683525_6463                                  
==> default: Clearing any previously set network interfaces...                                                          
==> default: Preparing network interfaces based on configuration...                                                         
default: Adapter 1: nat                                                                                             
==> default: Forwarding ports...                                                                                            
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
default: Removing insecure key from the guest if it present...                                                        
default: Key inserted! Disconnecting and reconnecting using new SSH key...                                          
==> default: Machine booted and ready!                                                                                  
==> default: Checking for guest additions in VM...                                                                          
default: The guest additions on this VM do not match the installed version of                                           
default: VirtualBox! In most cases this is fine, but in rare cases it can                                               
default: prevent things such as shared folders from working properly. If you see                                        
default: shared folder errors, please make sure the guest additions within the                                          
default: virtual machine match the version of VirtualBox you have installed on                                          
default: your host and reload your VM.                                                                                  
default:                                                                                                                
default: Guest Additions Version: 6.1.38                                                                                
default: VirtualBox Version: 7.0                                                                                    
==> default: Mounting shared folders...                                                                                     
default: /vagrant => 01-getting-started
````
</br>

You will not actually see anything though, since [Vagrant](https://developer.hashicorp.com/vagrant/docs) runs the virtual machine **without a user interface**. To prove that it is running, you can use `vagrant status` command.</br></br>

````sh
vagrant status
````
</br>

Once the command is executed we will see a message like this.</br></br>


````sh
Current machine states:

default                 running (virtualbox)

The VM is running. To stop this VM, you can run `vagrant halt` to 
shut it down forcefully, or you can run `vagrant suspend` to simply 
suspend the virtual machine. In either case, to restart it again, 
simply run `vagrant up`.
````
</br>

As we can see, there is a machine running with [Virtualbox](https://www.virtualbox.org). At the moment, let's ignore the message that tells us how to stop the **VM**. At the end of this guide we will see how we can [suspend](#suspense), [shut down](#halt) and [restart](#restart-the-vm) a **VM**. At this point, we have been able to build our virtual machine, but how do we access it?</br></br>

## SSH into the machine

[Vagrant](https://developer.hashicorp.com/vagrant/docs) provide us the `ssh` command, this will connect into a running [Vagrant](https://developer.hashicorp.com/vagrant/docs) machine and give us access to a shell.</br></br>

````sh
vagrant ssh
````
</br>

Once the command is executed we will see a message like this.</br></br>

````sh
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 5.4.0-135-generic x86_64)

* Documentation:  https://help.ubuntu.com                                                                               
* Management:     https://landscape.canonical.com                                                                       
* Support:        https://ubuntu.com/advantage

System information as of Wed Dec  7 13:58:07 UTC 2022                                                                                         

System load:  1.06              Processes:               119                                                            
Usage of /:   3.6% of 38.70GB   Users logged in:         0                                                              
Memory usage: 21%               IPv4 address for enp0s3: 10.0.2.15                                                     
Swap usage:   0%                                                                                                                             


0 updates can be applied immediately.                                                                                                         

New release '22.04.1 LTS' available.                                                                                    
Run 'do-release-upgrade' to upgrade to it.                                                                                                   


vagrant@ubuntu-focal:~$ 
````
</br>

On a simple [Vagrant](https://developer.hashicorp.com/vagrant/docs) project, the instance created will be named `default`. In fact, the previously executed command connects directly to vagrant `default` image. We can also run the command using the name seen with the `vagrant status` command.</br></br>

````sh
vagrant ssh default
````
</br>

You can check for yourself that we get the same result. Finally, we cant terminate the SSH session with `CTRL+D`, or by logging out.</br></br>

````sh
vagrant@ubuntu-focal:~$ logout
Connection to 127.0.0.1 closed.
````
</br>


## Suspense

A suspend effectively **saves the exact point-in-time state of the machine**, so that when you resume it later, it begins running immediately from that point, rather than doing a full boot.</br></br>

````sh
vagrant suspend
````
</br>

Once the command is executed we will see a message like this.</br></br>

````sh
==> default: Saving VM state and suspending execution...
````
</br>

Now, if we execute `vagrant status` command again.</br></br>

````sh
Current machine states:

default                   saved(virtualbox)

To resume this VM, simply run `vagrant up`.
````
</br>

We will see that the `default` VM is **saved** now.</br></br>

## Restart the VM

I don't know if you have noticed, but in the previous section he has given us a clue. Basically we will always use the `up` command to start a machine.
</br></br>

````sh
vagrant up
````
</br>

Once the command has been executed, we can use the `vagrant status` command and check that the virtual machine runs correctly again</br></br>

````sh
Current machine states:

default                 running (virtualbox)

The VM is running. To stop this VM, you can run `vagrant halt` to 
shut it down forcefully, or you can run `vagrant suspend` to simply 
suspend the virtual machine. In either case, to restart it again, 
simply run `vagrant up`.
````
</br>

## Halt

This command shuts down the running machine. If this fails, or if the `--force` flag is specified, [Vagrant](https://developer.hashicorp.com/vagrant/docs) will effectively just shut off power to the machine.</br></br>

````sh
vagrant halt
````
</br>

Once the command is executed we will see a message like this.</br></br>

````sh
==> default: Attempting graceful shutdown of VM...
````
</br>

Now, if we execute `vagrant status` command again.</br></br>

````sh
Current machine states:

default                   poweroff(virtualbox)

The VM is powered off. To restart the VM, simply run `vagrant up`
````
</br>

We will see that the `default` VM is **poweroff** now.</br></br>

## Destroy

This command **stops the running machine and destroys all resources that were created during the machine creation process**. After running this command, your computer should be left at a clean state, as if you never created the guest machine in the first place.</br></br>

````sh
vagrant destroy
````
</br>

When we execute the command, it will show us a confirmation message.</br></br>

````sh
default: Are you sure you want to destroy the 'default' VM? [y/N]
````
</br>

Once confirmed by entering `y`, it will start to shut down the virtual machine and remove the associated resources.</br></br>

````sh
default: Are you sure you want to destroy the 'default' VM? [y/N] y
==> default: Forcing shutdown of VM...
==> default: Destroying VM and associated drives...
````
</br>


At this point, if we execute the `vagrant status` command, we will see that the default virtual machine appears as **not created**.</br></br>

````sh
Current machine states:

default                   not created (virtualbox)

The environment has not yet been created. Run `vagrant up` to 
create the environment. If a machine is not created, only the 
default provider will be shown. So if a provider is not listed, 
then the machine is not created for that environment. 
````
</br>

That's all, I hope you found it useful.