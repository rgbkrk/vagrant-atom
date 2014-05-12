Vagrant the Atom
================

Simple vagrant box for building
[Atom from source](https://github.com/atom/atom/blob/master/docs/build-instructions/linux.md)
on an Ubuntu 14.04 Desktop box. It pulls atom from a submodule locally, in
`atom`.

To get started, clone this repository (or fork if you want) and setup the
submodules.

# Clone and submodule dance

```bash
git clone git@github.com:rgbkrk/vagrant-atom.git # or your fork!
cd vagrant-atom
git submodule init
git submodule update
```
# Get in, build it

```bash
vagrant up
vagrant ssh
cd atom
script/build
sudo script/grunt install
script/grunt mkdeb
```
