Vagrant the Atom
================

Simple vagrant box for building Atom from source. It pulls atom from a submodule locally, in `atom`.

To use, clone this repository (or fork if you want) and get the submodules.

# Get this repo, get going

```bash
git clone git@github.com:rgbkrk/vagrant-atom.git
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
```
