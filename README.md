## How to build this repository

The following should get you started building this repository, in case that you are unfamiliar with building from source RPMs on CentOS 7.x.

**This should be done in a CentOS 7.x environment**:

```shell
git clone https://git.centos.org/git/centos-git-common
git clone https://github.com/kernelim/centos-kasan
cd centos-kasan
../centos-git-common/get_sources.sh -b c7
rpmbuild --define "%_topdir `pwd`" -ba SPECS/kernel.spec
```

(The scriptlet above is based on information provided in the CentOS Wiki [Sources](https://wiki.centos.org/Sources?highlight=%28get_sources%29) page).

It is possible that `rpmbuild` complains about missing dependencies if it's the first time you are building a CentOS kernel on this particular CentOS system. Don't worry - you can get them by using `yum`.

The builts RPMs should reside in RPMS directory once execution ends.

Please note that a KASAN-based kernel may boot much more slowly than a normal kernel.
