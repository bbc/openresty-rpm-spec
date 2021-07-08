openresty-rpm-spec
==================

This spec file will build an RPM for OpenResty. I've only tried it on CentOS 6/7, but it will likely work on other RedHat-like Linuxes.

To build the RPM, you'll first need to set up your build environment. Typically, this means creating some directories and installing some packages:

	mkdir -p ~/rpmbuild/{SOURCES,SPECS}
	yum install -y  git zlib-devel lua lua-devel lua-json lua-filesystem rpm-build make openssl-devel pcre-devel GeoIP-devel readline-devel gcc-c++ wget perl-Digest-SHA perl-Digest-MD5 perl-Data-Dumper perl-Time-HiRes

Then get the relevant files into your tree (replacing `version` with the appropriate version string):
Note : The spec file is written for version 1.19.3.2 of openresty, edit .spec file and change version with the appropriate version :

	cd ~/rpmbuild/SOURCES
	wget http://openresty.org/download/openresty-1.19.3.2.tar.gz
	wget https://raw.githubusercontent.com/bbc/openresty-rpm-spec-eotk/master/openresty.init
	cd ~/rpmbuild/SPECS
	wget https://raw.githubusercontent.com/bbc/openresty-rpm-spec-eotk/raw/master/openresty.spec

Then just build the RPM:

	rpmbuild -ba ~/rpmbuild/SPECS/openresty.spec

The RPM will be in `~/rpmbuild/RPMS/{platform}/` and the SRPM will be in `~/rpmbuild/SRPMS/`.
