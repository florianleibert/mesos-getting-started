# Mesos Getting Started Tutorial

This tutorial explains how to build a simple distributed fault-tolerant framework on top of Mesos.
The example framework can launch a given number of instances of a command across a cluster,
and will restart the command if it fails.

## Prerequisites

Mesos uses autotools to build. Install via Homebrew on a Mac:

    brew install autoconf automake

### Install Autotools

### Install Mesos

#### On your Mac

    https://s3.amazonaws.com/mesos-pkg/osx/mesos.rb

#### On your Debian

    https://s3.amazonaws.com/mesos-pkg/ubuntu/12.10/mesos_0.14.0_amd64.deb

#### Manually

The Mesos repo on Github is currently out of sync. You can use the one below for now.

    git clone https://git-wip-us.apache.org/repos/asf/incubator-mesos.git
    cd incubator-mesos
    ./bootstrap
    mkdir build
    cd build
    ../configure
    make
    make install

### Run Zookeeper and Mesos

Mesos ships with Zookeeper. Run these commands in different terminal windows to start a local Zookeeper, Mesos master, and Mesos slave.

    cd /path/to/incubator-mesos/build/third_party/zookeeper-3.3.4
    cp conf/zoo_sample.cfg conf/zoo.cfg
    ./bin/zkServer.sh start

    /usr/local/sbin/mesos-master --zk=zk://localhost:2181/mesos

    /usr/local/sbin/mesos-slave --master=zk://localhost:2181/mesos
