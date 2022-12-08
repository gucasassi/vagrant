# Synced Folders

Virtual machines are convenient for developing in, but not many people want to edit files using a plain terminal-based editor over SSH. [Vagrant](https://developer.hashicorp.com/vagrant/docs) automatically syncs files to and from the guest machine. This way you can edit files locally and run them in your virtual development environment.

By default, [Vagrant](https://developer.hashicorp.com/vagrant/docs) **shares your project directory** (the one containing the Vagrantfile) to the `/vagrant` **directory in your guest machine**.</br></br>

## Bring up a virtual machine

Create and configure a guest machine, as specified by [Getting Started](../01-getting-started/README.md) guide.</br></br>

````sh
vagrant up
````
</br>

SSH into your virtual machine to see the synched file.</br></br>

````sh
vagrant ssh
````
</br>

## Explore the synced folder

 When you `vagrant ssh` into your machine, you're in `/home/vagrant`, which is a different directory from the synced `/vagrant` directory. On the virtual machine, list the files in the `/vagrant` directory.</br></br>

````sh
vagrant@ubuntu-focal:~$ ls /vagrant
Vagrantfile               
````
</br>

Believe it or not, the `Vagrantfile` that you see inside the virtual machine is actually the same `Vagrantfile` that is on your actual host machine.</br></br>

## Test the synced folder

To see the files sync between the guest machine and yours add a new file in your virtual machine's `/vagrant` directory.</br></br>

````sh
vagrant@ubuntu-focal:~$ echo "Hi there!" > /vagrant/synced-test.txt           
````
</br>

End your SSH session.</br></br>

````sh
vagrant@ubuntu-focal:~$ exit         
````
</br>

List the contents of your local directory, and notice that the new file `synced-test.txt` you created on your virtual machine is reflected there.

That's all, I hope you found it useful. In the next section we will learn how to  [configure basic settings of a VM using Vagrantfile](/03-vagrantfile/README.md).