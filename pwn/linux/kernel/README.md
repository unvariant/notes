# **protections**
### SMAP
- supervisor mode access prevention
- enabled when bit 21 in CR4 is set
- prevents ring 0 code from reading or writing ring 3 virtual memory
- SMAP does not cover instruction fetches
	- an SMAP enabled kernel with SMEP disabled can still execute userland memory
### SMEP
- supervisor mode execution prevention
- enabled when bit 20 in CR4 is set
- prevents ring 0 code from executing ring 3 virtual memory
### KASLR
- kernel address space layout randomization
- randomized the kernel load base virtual address
- location is bruteforcable
	- 256 possible locations on i386
	- 512 possible locations on x86-64
- disabled with the `nokalsr` cmdline parameter
- TODO: kalsr leaks
### FGKASLR
- fine grained kernel address space layout randomization
- NOT implemented in the mainline kernel, exists as a patchset for linux 5.xx and early 6.xx
- randomized the offsets between certain sections in the kernel on boot
	- TODO: list randomized sections
	- TODO: list which sections still have a constant offset
### KPTI
- kernel page table isolation
- protection against MELTDOWN style attacks
- separate page tables from ring 3 and ring 0
	- ring 3 page tables map the process userland memory, as well as the kernel trampoline
	- ring 0 page tables map all of userland memory, as well as all of kernel memory
- `(ring 3 cr3) = (ring 0 cr3) | 0x1000`
- `(ring 0 cr3) = (ring 3 cr3) & ~0x1000`
- disabled with the `nopti` cmdline parameter
# **techniques**
### cross cache
- [https://ruia-ruia.github.io/2022/08/05/CVE-2022-29582-io-uring/#crossing-the-cache-boundary](https://ruia-ruia.github.io/2022/08/05/CVE-2022-29582-io-uring/#crossing-the-cache-boundary)
# **exploits**
### dirty page table
# **privesc**
### modprobe
- `modprobe_path` symbol holds a path to a binary on the system
- `modprobe_path` is run when linux can't figure out how to execute a binary
	- full root permissions and outside of any namespace
- accessible through `/proc/sys/kernel/modprobe_path`
- privesc
	- overwriting `modprobe_path` directly, requires writing a string in kernel memory
	- overwriting the `modprobe_path` permissions in `kern_table`, requires single bit flip or single byte write
[^1]: https://elixir.bootlin.com/linux/v6.11.5/source/kernel/module/kmod.c#L64
[^2]: https://elixir.bootlin.com/linux/v6.11.5/source/kernel/sysctl.c#L1732
### commit creds
### modifying process credentials