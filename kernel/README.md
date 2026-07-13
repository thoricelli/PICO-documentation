# Kernel
This file contains information about the Phoenix modified Linux kernel, the AOSP and drivers the Pico 4 runs on.

GPL-2.0 Phoenix Linux kernel source code:  
https://github.com/bytedance/phoenix-kernel
## Version table

| Name         | Type          | Version | Notes             |
| ------------ | ------------- | ------- | ----------------- |
| Linux kernel | Kernel        | 4.19.81 |                   |
| Android      | OS            | 10      |                   |
| kgsl         | Kernel driver | /       | Adreno GPU driver |

## zImage vmlinux-to-elf log dump
```shell
[+] Version string: Linux version 4.19.81-perf+ (smartcm@n151-190-200) (clang version 8.0.12 for Android NDK) #1 SMP PREEMPT Wed Jul 2 11:42:08 CST 2025
[+]   Other related strings containing the version number: [b'Linux version 4.19.81-perf+ (smartcm@n151-190-200) (clang version 8.0.12 for Android NDK) #1 SMP PREEMPT Wed Jul 2 11:42:08 CST 2025', b'4.19.81-perf+ SMP preempt mod_unload modversions aarch64', b'/lib/firmware/updates/4.19.81-perf+', b'/lib/firmware/4.19.81-perf+', b'4.19.81-perf+']
[+]   Architecture string: mod_unload modversions aarch64
[+] Guessed architecture: aarch64 successfully in 0.64 seconds
[+] Kernel found in database
[+]   Read kernel source: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/?id=v4.19
[+]   Download kernel: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/snapshot/v4.19.tar.gz
[+]   Kernel release date: 2018-10-22
[+]   Interesting files:
[~]     - kernel/kallsyms.c: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/kernel/kallsyms.c?id=v4.19
[~]     - scripts/kallsyms.c: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/scripts/kallsyms.c?id=v4.19
[~]     - include/linux/elf.h: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/include/linux/elf.h?id=v4.19
[~]     - include/uapi/linux/elf-em.h: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/include/uapi/linux/elf-em.h?id=v4.19
[~]     - include/uapi/linux/elf.h: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/include/uapi/linux/elf.h?id=v4.19
[~]     - Documentation/process/changes.rst: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/process/changes.rst?id=v4.19
[+]   Architecture arm64 (EM_AARCH64) supports 64-bit, big-endian, little-endian
[~]     - Documentation/arm64/booting.txt: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/arm64/booting.txt?id=v4.19
[~]     - arch/arm64/kernel/vmlinux.lds.S: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm64/kernel/vmlinux.lds.S?id=v4.19
[~]     - arch/arm64/kernel/head.S: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm64/kernel/head.S?id=v4.19
[~]     - arch/arm64/kernel/Makefile: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm64/kernel/Makefile?id=v4.19
[~]     - arch/arm64/boot/Makefile: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm64/boot/Makefile?id=v4.19
[~]     - arch/arm64/include/asm/elf.h: https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/arch/arm64/include/asm/elf.h?id=v4.19
[+]   Suggested build environment: docker run -it debian/eol:stretch (Debian 9.0 "Stretch" released 2017-06-17)
[+] Found kallsyms_token_table at file offset 0x0183c600
[+] Found kallsyms_token_index at file offset 0x0183ca00
[+] Found kallsyms_markers at file offset 0x0183b600
[+] Found kallsyms_names at file offset 0x016a3500 (123246 symbols)
[+] Found kallsyms_num_syms at file offset 0x016a3400
[+] Found relocations table at file offset 0x1c56898 - 0x1e46e58 (count=84712)
[+] Guessed kernel base from relocation offsets range 0xffffff8008062320-0xffffff80090a7000 -> 0xffffff8008080000
[+] Successfully applied 84687 relocations.
[!] WARNING: Less than half (0%) of offsets are negative
             You may want to re-run this utility, overriding the relative base
[!] WARNING: More than half (100%) of offsets look like absolute addresses
[!]          You may want to re-run this utility, overriding the relative base
[+] Note: sometimes there is junk at the beginning of the kernel, and the load address is not the guessed
          base address. You may need to play around with different load addresses to get everything
          to line up. There may be some decent tables in the kernel with known patterns that could be
          used to line things up heuristically, but this has not been explored this yet.
[+] Negative offsets overall: 0 %
[+] Null addresses overall: 0 %
[+] Found kallsyms_offsets at file offset 0x0162ad00
[+] Reconstructing ELF with guessed base address (ffffff8008080000)
[+] Successfully wrote the new ELF kernel to vmlinux
```