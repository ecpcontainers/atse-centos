FROM centos:7
LABEL maintainer="Andrew Younge"


# Install minimum set of dependencies, keep in alphabetical order
RUN yum clean all && rpm --rebuilddb && yum update -y && yum install -y \
	deltarpm \
	ethtool \
	gcc-gfortran \
	glibc-devel \
	glibc-static \
	libarchive-devel \
	libnl3 \
	libstdc++-static \
	lzo-devel \
	logrotate \
	lsof \
	nano \
	numactl-libs \
	pciutils \
	strace \
	sudo \
	tcl \
	tcsh \
	tk \
	wget \
	libyaml-devel \
	zlib-static \
	zlib-devel \
	which \
	environment-modules \
	perl \
	libmnl

# Install Mellanox MFED user-level drivers 
#TODO: Ensure OFED is open before pushing tgz publicly. Right now this won't work
WORKDIR /tmp
COPY MLNX_OFED_LINUX-4.5-1.0.1.0-rhel7.5alternate-aarch64.tgz .
RUN tar -xzvf MLNX_OFED_LINUX-4.5-1.0.1.0-rhel7.5alternate-aarch64.tgz && \
	MLNX_OFED_LINUX-4.5-1.0.1.0-rhel7.5alternate-aarch64/mlnxofedinstall --user-space-only --without-fw-update --all -q && \
	rm -rf MLNX_OFED_LINUX-4.5-1.0.1.0-rhel7.5alternate-aarch64 && \
	rm -rf MLNX_OFED_LINUX.1.logs && \
	rm MLNX_OFED_LINUX-4.5-1.0.1.0-rhel7.5alternate-aarch64.tgz && \
	m ofed.conf

# Setup ATSE repo
COPY atse.repo /etc/yum.repos.d/atse.repo
RUN yum makecache && yum install -y \
atse-filesystem \
lmod-atse \
autoconf-atse \
automake-atse \
libtool-atse \
cmake-atse \
ninja-atse \
git-atse \
binutils-atse \
gnu7-compilers-atse \
openmpi3-gnu7-tx2-atse \
openblas-gnu7-tx2-atse \
papi-gnu7-atse \
numactl-gnu7-atse \
hwloc-gnu7-atse \
pmix-atse \
munge-atse \
munge-libs-atse \
slurm-atse \
slurm-slurmctld-atse \
slurm-slurmd-atse \
slurm-libpmi-atse \
slurm-devel-atse  \
slurm-example-configs-atse  \
spack-atse \
boost-gnu7-openmpi3-tx2-atse \
bzip2-gnu7-tx2-atse \
hdf5-gnu7-atse \
netcdf-gnu7-openmpi3-atse \
openucx-gnu7-tx2-atse \
phdf5-gnu7-openmpi3-atse \
pnetcdf-gnu7-openmpi3-atse \
xz-gnu7-tx2-atse \
zlib-gnu7-tx2-atse

