# chef-docker [![Build Status](https://secure.travis-ci.org/bflad/chef-docker.png?branch=master)](http://travis-ci.org/bflad/chef-docker)

## Description

Installs/Configures Docker. Please see [COMPATIBILITY.md](COMPATIBILITY.md) for more information about Docker versions that are tested and supported by cookbook versions.

This cookbook was inspired by @thoward's docker-cookbook: https://github.com/thoward/docker-cookbook

## Requirements

### Platforms

* Ubuntu 12.04
* Ubuntu 12.10

### Cookbooks

[Opscode Cookbooks](https://github.com/opscode-cookbooks/)

* [apt](https://github.com/opscode-cookbooks/apt)
* [git](https://github.com/opscode-cookbooks/git)

Third-Party Cookbooks

* [golang](https://github.com/NOX73/chef-golang)
* [lxc](https://github.com/hw-cookbooks/lxc)
* [modules](https://github.com/Youscribe/modules-cookbook)

## Attributes

These attributes are under the `node['docker']` namespace.

Attribute | Description | Type | Default
----------|-------------|------|--------
arch | Architecture for docker binary (note: Docker only currently supports x86_64) | String | auto-detected (see attributes/default.rb)
install_dir | Installation directory for docker binary | String | auto-detected (see attributes/default.rb)
install_type | Installation type for docker ("binary", "package" or "source") | String | "package"

### Binary Attributes

These attributes are under the `node['docker']['binary']` namespace.

Attribute | Description | Type | Default
----------|-------------|------|--------
url | URL for downloading docker binary | String | auto-detected (see attributes/default.rb)

### Package Attributes

These attributes are under the `node['docker']['package']` namespace.

Attribute | Description | Type | Default
----------|-------------|------|--------
distribution | Distribution for docker packages | String | auto-detected (see attributes/default.rb)
repo_url | Repository URL for docker packages | String | auto-detected (see attributes/default.rb)

### Source Attributes

These attributes are under the `node['docker']['source']` namespace.

Attribute | Description | Type | Default
----------|-------------|------|--------
ref | Repository reference for docker source | String | "master"
url | Repository URL for docker source | String | "https://github.com/dotcloud/docker.git"

## Recipes

* `recipe[docker]` Installs/Configures Docker
* `recipe[docker::aufs]` Installs/Loads AUFS Linux module
* `recipe[docker::binary]` Installs Docker binary
* `recipe[docker::package]` Installs Docker via package
* `recipe[docker::source]` Installs Docker via source
* `recipe[docker::upstart]` Installs/Starts Docker via Upstart

## Usage

### Default Installation

* Add `recipe[docker]` to your node's run list

## Testing and Development

Here's how you can quickly get testing or developing against the cookbook thanks to [Vagrant](http://vagrantup.com/) and [Berkshelf](http://berkshelf.com/).

    vagrant plugin install vagrant-berkshelf
    git clone git://github.com/bflad/chef-docker.git
    cd chef-docker
    vagrant up BOX # BOX being ubuntu1204

You can then SSH into the running VM using the `vagrant ssh BOX` command.

The VM can easily be stopped and deleted with the `vagrant destroy` command. Please see the official [Vagrant documentation](http://docs.vagrantup.com/v2/cli/index.html) for a more in depth explanation of available commands.

## Contributing

Please use standard Github issues/pull requests and if possible, in combination with testing on the Vagrant boxes.

## License and Authors

* Author:: Brian Flad (<bflad417@gmail.com>)
* Copyright:: 2013 Brian Flad

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
