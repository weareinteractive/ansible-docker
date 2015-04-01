# Ansible Docker Role

[![Build Status](https://travis-ci.org/weareinteractive/ansible-docker.png?branch=master)](https://travis-ci.org/weareinteractive/ansible-docker)
[![Stories in Ready](https://badge.waffle.io/weareinteractive/ansible-docker.svg?label=ready&title=Ready)](http://waffle.io/weareinteractive/ansible-docker)

> `docker` is an [ansible](http://www.ansible.com) role which:
>
> * installs docker
> * configures docker

## Installation

Using `ansible-galaxy`:

```
$ ansible-galaxy install franklinkim.docker
```

Using `requirements.yml`:

```
- src: franklinkim.docker
```

Using `git`:

```
$ git clone https://github.com/weareinteractive/ansible-docker.git
```

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```
# docker_options:
#   - "--dns 8.8.4.4"

# apt package
docker_package: lxc-docker-1.5.0
# start on boot
docker_service_enabled: yes
# current state: started, stopped
docker_service_state: started
# docker default options
docker_options: []
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

* `restart docker`

## Example playbook

```
- host: all
  roles:
    - franklinkim.docker
  vars:
    docker_service_state: started
    docker_service_enabled: yes
    docker_package: lxc-docker-1.2.0
    docker_images:
      - { name: 'wordpress', tag: '4.0.0' }
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-docker.git
$ cd ansible-docker
$ vagrant up
```

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.
