Schemacrawler RPM package builder
==========================================

[![Build Status](https://travis-ci.org/adriens/schemacrawler-rpm.svg?branch=master)](https://travis-ci.org/adriens/schemacrawler-rpm) [![Dependency Status](https://www.versioneye.com/user/projects/570db48efcd19a00415b1248/badge.svg?style=flat)](https://www.versioneye.com/user/projects/570db48efcd19a00415b1248)

Set version in session
------------------------------------------

    export SCHEMACRAWLER_VERSION=14.07.07

Download and install .rpm
------------------------------------------

    wget https://bintray.com/artifact/download/adriens/rpm/schemacrawler-${SCHEMACRAWLER_VERSION}-1.noarch.rpm
    yum --nogpgcheck localinstall schemacrawler-${SCHEMACRAWLER_VERSION}-1.noarch.rpm

Pre-requisite to build the .rpm yourself
------------------------------------------

**DO NOT SKIP THESE STEPS !**

To get the proper non-bugged jdbc sqlite driver (3.7.8) and to be able to successfully run the build, **you have to
run** the following command :

    mvn install:install-file -DgroupId=org.xerial -DartifactId=sqlite-jdbc -Dversion=3.7.8 -Dfile=lib/sqlite-jdbc-3.7.8.jar -Dpackaging=jar -DgeneratePom=true

To be able to build the rpm, you need to have the proper package on your OS.

On Debian like distros :

    sudo apt-get install rpm

On RRPM based distros (Red Hat like, CentOS, Fedora) :

    yum install rpm


Build docs and rpm installer
------------------------------------------

    mvn clean package site -Ddependency.locations.enabled=false


Build all and Install
------------------------------------------

    mvn clean package site -Ddependency.locations.enabled=false && yum --nogpgcheck localinstall target/rpm/schemacrawler/RPMS/noarch/schemacrawler-${SCHEMACRAWLER_VERSION}-1.noarch.rpm`




Build all and (re)install
------------------------------------------

    mvn clean package site -Ddependency.locations.enabled=false && yum remove schemacrawler.noarch && yum --nogpgcheck localinstall target/rpm/schemacrawler/RPMS/noarch/schemacrawler-${SCHEMACRAWLER_VERSION}-1.noarch.rpm


Install test
------------------------------------------

To rapidly check if schemacrawler is already installed :

    yum list installed | grep schemacrawler

Get infos about liquibase package :

    yum info schemacrawler.noarch


Uninstall
------------------------------------------

    yum remove schemacrawler.noarch

Contribute
------------------------------------------

If you are familiar with bash auto-complete files, you are welcome to provide me one 
to make schemacawler linux experience even better.


