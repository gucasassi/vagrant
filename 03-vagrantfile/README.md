<font size="1">4 min</font>

# Vagrantfile

The primary function of the `Vagrantfile` is to **describe the type of machine required for a project**, and how to configure and provision these machines.</br></br> 

## Lookup Path

When you run any `vagrant command`, [Vagrant](https://developer.hashicorp.com/vagrant/docs) **climbs up the directory tree looking for the first Vagrantfile it can find**, starting first in the current directory. So if you run vagrant in /`home/projects/03-vagrantfile`, it will search the following paths in order for a `Vagrantfile`, until it finds one:</br></br>

````sh
/home/projects/03-vagrantfile/Vagrantfile
/home/projects/Vagrantfile
/home/Vagrantfile
/Vagrantfile
````
</br>

This feature lets you run vagrant from any directory in your project.

You can change the starting directory where [Vagrant](https://developer.hashicorp.com/vagrant/docs) looks for a `Vagrantfile` by setting the `VAGRANT_CWD` environmental variable to some other path.</br></br>

## Load Order and Merging

An important concept to understand is how Vagrant loads `Vagrantfiles`. [Vagrant](https://developer.hashicorp.com/vagrant/docs) actually loads a series of `Vagrantfiles`, merging the settings as it goes. This allows `Vagrantfiles` of varying level of specificity to override prior settings.</br></br>

1) `Vagrantfile` packaged with the [box](https://developer.hashicorp.com/vagrant/docs/boxes).

2) `Vagrantfile` in your [Vagrant](https://developer.hashicorp.com/vagrant/docs) **home directory**. This lets you specify some defaults for your system user.

3) `Vagrantfile` from the **project directory**.</br></br>

Within each `Vagrantfile`, you may specify a `Vagrant.configure` blocks.</br></br>

## Configuration Version

Configuration versions are the mechanism by which `Vagrant 1.1+` is able to remain **backwards compatible** with `Vagrant 1.0.x` Vagrantfiles, while introducing dramatically new features and configuration options.

If you run `vagrant init` today, the `Vagrantfile` will be in roughly the following format:</br></br>

````sh
# All Vagrant configuration is done below. 
Vagrant.configure("2") do |config|
  # ...
end
````
</br>

The `"2"` in the first line above represents the **version of the configuration object** config that will be used for configuration for that block (the section between the `do` and the `end`). 

That's all, I hope you found it useful. In the next section we will talk about [boxes](/04-boxes/README.md).