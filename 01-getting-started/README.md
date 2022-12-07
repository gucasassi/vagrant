# Getting Started

In this tutorial, you will create your first development environment with **Vagrant**. This quick start provides a brief introduction to **Vagrant**, its prerequisites, and an overview of the most important **Vagrant** commands to understand.</br></br>


## Create a directory

Make a new directory for the project you will work on throughout these tutorials.</br></br>

````sh
mkdir getting-started
cd getting-started
````
</br>


## Initialize a Project Directory

The first step to configure any **Vagrant** project is to create a `Vagrantfile`. The `Vagrantfile` allows you to describe the kind of machine and resources you need to run your project, as well as what software to install and how you want to access it.</br>

Vagrant has a built-in command for initializing a project, `vagrant init`, which can take a box name as arguments.</br></br>

````sh
vagrant init ubuntu/focal64
````
</br>

The above command allows us to initialize the directory and specify the box to use, in this case `ubuntu/focal64`.</br></br>

````sh
A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
````
</br>

You now have a `Vagrantfile` in your current directory.</br></br>


## Bring up a virtual machine

Now that you have initialized your project and configured a box for it to use, it is time to boot your first **Vagrant** environment. Run the following command from your terminal:</br></br>

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
default: SSH auth method: private key                                                                                   default:                                                                                                                
default: Vagrant insecure key detected. Vagrant will automatically replace                                              
default: this with a newly generated keypair for better security.                                                       default:                                                                                                                
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
default: your host and reload your VM.                                                                                  default:                                                                                                                
default: Guest Additions Version: 6.1.38                                                                                
default: VirtualBox Version: 7.0                                                                                    
==> default: Mounting shared folders...                                                                                     
default: /vagrant => 01-getting-started
````
</br>

You will not actually see anything though, since **Vagrant** runs the virtual machine **without a UI**. To prove that it is running, you can use `vagrant status` command.</br></br>

````sh
vagrant status
````
</br>

Result of execute `vagrant status` command.</br></br>


````sh
Current machine states:

default                 running (virtualbox)

The VM is running. To stop this VM, you can run `vagrant halt` to shut it down forcefully, or you can run `vagrant suspend` to simply suspend the virtual machine. In either case, to restart it again, simply run `vagrant up`.
````
</br>

As we can see, there is a machine running with **virtualbox**. At the moment, let's ignore the message that tells us how to stop the **VM**. At the end of this guide we will see how we can [shut it down](#halt-vs-suspense), [suspend](#halt-vs-suspense) and [restart](#restart-the-vm) a **VM**.</br></br>
 To prove that it is running, you can [SSH into the machine](#ssh-into-the-machine).</br></br>


## SSH into the machine

To prove that it is running, you can SSH into the machine.</br></br>

## Halt vs Suspense

## Restart the VM

## Destroy the VM