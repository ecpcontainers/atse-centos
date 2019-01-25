FROM centos:7
LABEL maintainer="Andrew Younge"


# Update yum repo and install base
RUN yum clean all && rpm --rebuilddb && yum update -y && \
	yum install -y yum-plugin-ovl wget git m4


# Setup ATSE repo
COPY atse.repo /etc/yum.repos.d/atse.repo
RUN yum repolist && yum install -y \
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

