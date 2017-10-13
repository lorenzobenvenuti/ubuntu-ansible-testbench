# ubuntu-ansible-testbench

A Docker image to test Ansible automation on an Ubuntu server. `sudo`, `openssh` and `python` are installed on top of an `ubuntu` Docker image.
The default build creates a a sudoer user `ansible` with password `ansible`; user and password can be customized using build arguments `username` and `password`.

## Building the image

Default username and password:

```
$ docker build -t ubuntu-ansible-testbench .
```

Custom username and password:

```
$ docker build -t ubuntu-ansible-testbench --build-arg username=lorenzo --build-arg password=secret .
```

## Running the container

```
$ docker run -d -p 5555:22 ubuntu-ansible-testbench
```

In your inventory file you can then define

```ini
ubuntu-server ansible_host=x.y.z.w ansible_port=5555
```

where `x.y.z.w` is the IP address of the host running Docker.
