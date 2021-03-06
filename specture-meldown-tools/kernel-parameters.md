* 针对Power架构，可通过增加如下参数进一步减轻CPU漏洞补丁对性能影响：
no_rfi_flush nopti nospectre_v1 nospectre_v2 spec_store_bypass_disable=off

* 某些高版本内核可以简化为mitigations=off参数，改参数等价于：
nopti [X86,PPC]
kpti=0 [ARM64]
nospectre_v1 [X86,PPC]
nobp=0 [S390]
nospectre_v2 [X86,PPC,S390,ARM64]
spectre_v2_user=off [X86]
spec_store_bypass_disable=off [X86,PPC]
ssbd=force-off [ARM64]
l1tf=off [X86]
mds=off [X86]
kvm.nx_huge_pages=off [X86]
tsx_async_abort=off [X86]

[Controlling the Performance Impact of Microcode and Security Patches for CVE-2017-5754 CVE-2017-5715 and CVE-2017-5753 using Red Hat Enterprise Linux Tunables](https://access.redhat.com/articles/3311301)
> 
> IBM POWER Defaults
> The mitigation for Spectre (Variants 1 and 2) are provided by the system firmware provided by the vendor. Currently there is no tunable available on Linux to disable these mitigations. The mitigation for variant 3 is provided by the Linux kernel, without depending on system firmware (although an optimized implementation is used in case system firmware provides support for it). It is enabled by default, and can be disabled on boot time, with the kernel command line parameters no_rfi_flush or nopti), or at run time, with either of the following tunables:
> On initial zstream/errate updates:
> /sys/devices/system/cpu/rfi_flush
> The above tunable will change with upcoming zstream/errata updates to the following:
> /sys/kernel/debug/powerpc/rfi_flush
> 
