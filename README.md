# ndctl
[![Build Status](https://travis-ci.org/pmem/ndctl.svg?branch=master)](https://travis-ci.org/pmem/ndctl)

Utility library for managing the libnvdimm (non-volatile memory device)
sub-system in the Linux kernel
  
<a href="https://repology.org/project/ndctl/versions">
    <img src="https://repology.org/badge/vertical-allrepos/ndctl.svg" alt="Packaging status" align="right">
</a>

Build
=====

```
meson setup build;
meson compile -C build;
```

Optionally, to install:

```
meson install -C build
```

There are a number of packages required for the build steps that may not
be installed by default.   For information about the required packages,
see the "BuildRequires:" lines in cxl-tool.spec.in.

https://github.com/computexpresslink/cxl-tool/cxl-tool.spec.in

Documentation
=============
See the latest documentation for the NVDIMM kernel sub-system here:
  
https://www.kernel.org/doc/html/latest/driver-api/nvdimm/index.html

A getting started guide is also available on the kernel.org nvdimm wiki:

https://nvdimm.wiki.kernel.org/start

Unit Tests
==========
1. Obtain the kernel source.  For example,  
  `git clone https://github.com/torvalds/linux.git`

1. Compile the kernel with the following options turned on.

   ```
	 CONFIG_CXL_BUS
	 CONFIG_CXL_PCI
	 CONFIG_CXL_ACPI
	 CONFIG_CXL_PMEM
	 CONFIG_CXL_MEM
	 CONFIG_CXL_PORT
   ```

1. Build and install the modules

   ```
   make -j 8
   sudo make modules_install
   ```

1. Now run `meson test -C build` in the cxl-tool source directory.

1. To run the 'destructive' set of tests that may clobber existing pmem
   configurations and data, configure meson with the destructive option after the
   `meson setup` step:

   ```
   meson configure -Dtest=enabled -Ddestructive=enabled build;
   ```

here is a page showing how to test cxl with qemu:
https://sunfishho.github.io/jekyll/update/2022/07/07/setting-up-qemu-cxl.html

Troubleshooting
===============

The unit tests will validate that the environment is set up correctly
before they try to run. If the platform is misconfigured, i.e. the unit
test modules are not available, or the test versions of the modules are
superseded by the "in-tree/production" version of the modules `meson
test` will skip tests and report a message like the following in
`build/meson-logs/testlog.txt`
