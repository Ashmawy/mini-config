# mini-config

This is a very rudimentary configuration management tool. This tool can be used
to configure servers for the production service of a simple PHP application. 

The design of the tool is fairly simple, relying entirely on config yamls similar to Ansible's way of executing. Currently, additional to package installation, the script supports file content and metadata copying as instructed. 

## Abstractions:

1. Automates setup of LAMP stack
1. Install specific Debian packages
1. Remove specific Debian packages
1. Specify content and metadata for files
1. Will check for services that need to be restarted

## Structure:
``` bash
  mini-config/
  +-- bootstrap.sh
  +-- mini-conifg
  +-- packages
      +-- install.txt
      +-- uninstall.txt
  +-- files
      +-- index.php
  +-- config
      +-- config.yaml

```

## How to Configure:

* To install a package, add the package name to the text file labeled "install.txt" inside the `/packages` directory. Each package name should be on it's own line without any trailing whitespace.
* For removing an installed package, do the same as you did to install a package. This time you will add the package names to the "uninstall.txt" file inside the `/packages` directory.
* To copy files, you will need to save the file you wish to copy under `/files`. Once there, you can specify the required metadata in `config.yaml` under `/config`. Follow the example already in there for index.php. 

## **_Usage_**

* Transfer directory to the destination server using the following syntax:

  ```bash
  scp -r mini-config/ your_username@remotehost
  ```

* CD into the directory

  ```bash
  cd mini-config/
  ```

* Make the scripts executable

  ```bash
  chmod +x mini-config bootstrap.sh
  ```

* Install dependency

  ```bash
  source bootstrap.sh
  ```

* Run the script

  ```bash
  ./lumos_config
  ```