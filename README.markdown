# A Recipe for a Redis RPM on CentOS

Perform the following on a build box as a normal user.

## Create an RPM Build Environment

    sudo yum install rpmdevtools
    rpmdev-setuptree

## Install Prerequisites for RPM Creation

    sudo yum groupinstall 'Development Tools'

## Download Redis

    cd ~/rpmbuild/SOURCES
    wget http://redis.googlecode.com/files/redis-2.2.2.tar.gz

## Get Necessary System-specific Configs

    git clone git://github.com/tobert/redis-centos.git
    cp redis-centos/sources/redis.conf ~/rpmbuild/SOURCES/
    cp redis-centos/spec/redis.spec ~/rpmbuild/SPECS/

## Build the RPM

    cd ~/rpmbuild/
    rpmbuild -ba SPECS/redis.spec

The resulting RPM will be:

    ~/rpmbuild/RPMS/x86_64/redis-2.2.2-1.el6.x86_64.rpm

## Credits

Based on the `redis.spec` file from Jason Priebe, found on [Google Code][gc].

 [gc]: http://groups.google.com/group/redis-db/files

Rebased on spec by Silas Sewell via Koji.

 http://koji.fedoraproject.org/koji/packageinfo?packageID=11032

