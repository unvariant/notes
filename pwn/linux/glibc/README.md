## ret2csu
## ret2dlresolve
On x86, the resolver must save the register state on the stack before calling `_dl_fixup`. However the size of the register state is cpu dependent (AVX512, TILE, etc) and may change on remote. An AVX512 enabled processor allocates an additional 0x8c0 bytes of space in the resolver, which can crash the ret2dlresolve chain if it takes place in the binary BSS section.
The amount of extra space that is allocated is stored in the global readonly linker state[1].
[^1]: https://elixir.bootlin.com/glibc/glibc-2.40.9000/source/sysdeps/x86_64/dl-trampoline.h#L59
## libc unwind

## printf tables

## exit functions
## tls destructors
## FILE vtables
## FILE wide vtables
## libc setcontext
## libc GOT overwrite
## house of muney
- [https://maxwelldulin.com/BlogPost/House-of-Muney-Heap-Exploitation](https://maxwelldulin.com/BlogPost/House-of-Muney-Heap-Exploitation)