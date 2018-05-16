Schemacrawler RPM package builder
==========================================

[![Build Status](https://travis-ci.org/adriens/schemacrawler-rpm.svg?branch=master)](https://travis-ci.org/adriens/schemacrawler-rpm) [![Dependency Status](https://beta.gemnasium.com/badges/github.com/adriens/schemacrawler-rpm.svg)](https://beta.gemnasium.com/projects/github.com/adriens/schemacrawler-rpm)
<a href="https://zenhub.com"><img src="https://raw.githubusercontent.com/ZenHubIO/support/master/zenhub-badge.png"></a>


Set version in session
------------------------------------------

    export SCHEMACRAWLER_VERSION=14.21.01

Download and install .rpm
------------------------------------------

Go to the release section to manually download or :
    
        wget https://github.com/adriens/schemacrawler-rpm/releases/download/${SCHEMACRAWLER_VERSION}/schemacrawler-${SCHEMACRAWLER_VERSION}-1.noarch.rpm

Build the .rpm yourself
------------------------------------------

See ```.travis.yml``` instructions.

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
