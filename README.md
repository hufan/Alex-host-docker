# Summary

This repository provides a Docker container for building Variscite software releases. These configurations have been tested:

|Container Version   | Variscite Release                                                          |
|--------------------|----------------------------------------------------------------------------|
| Ubuntu 20.04       | - Yocto Dunfell, Hardknott<br>- Android 10, 11<br>- Debian Bullseye<br>- Boot2Qt Dunfell
| Ubuntu 18.04       | - Yocto Zeus


# Host Setup

From a brand new Ubuntu installation:

1. Install Docker `$ sudo apt update && sudo apt install docker.io`
2. Install Host Linux Headers (required for some Yocto versions) `$ sudo apt install linux-headers-$(uname -r)`
3. Give permissions to run docker without sudo `$ sudo usermod -aG docker ${USER}`
4. Logout and Login again for permissions to take effect
5. Clone this repository

# Usage

On Host Computer:
```
$ mkdir ~/workspcae
$ ./run.sh -w ~/workspcae
```
You're now running in a container with all build dependencies, and can build as normal.


## Container Authentication

You may use the sudo command inside the container with these credentials:

|Username   | Password  |
|-----------|-----------|
| alex      | ubuntu
<br>

# Rebuilding Docker Image

The Docker Image will be built automatically by ./run.sh the first time. Any commits to the GIT repository will cause the image to be rebuilt with the new changes using cache (not necessarily the latest from Ubuntu)

To force the container to be rebuilt with the latest from Ubuntu, pass the `-f` argument:

```$ ./run.sh -f ...```
