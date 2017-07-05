# iOS-related
Tools for iOS research

## ASLR-Remover.c
Code originally from the internet only supports 32, I add 64 support.
To remove ASLR is to change the flag.
The idea is change #define MH_PIE 0x200000 in file header. 
```
struct mach_header_64 {
 uint32_t magic;  /* mach magic number identifier */
 cpu_type_t cputype; /* cpu specifier */
 cpu_subtype_t cpusubtype; /* machine specifier */
 uint32_t filetype; /* type of file */
 uint32_t ncmds;  /* number of load commands */
 uint32_t sizeofcmds; /* the size of all the load commands */
 uint32_t flags;  /* flags */
 uint32_t reserved; /* reserved */
};
```
To make the modified APP run again, re-codesign is required. 
Tested on ios8.3 JB iphone.

## tcprelay.py & usbmux.py
WIFI SSH connection is very unstable and annoying. A solution is using TCP relay:
Code originally from https://cgit.sukimashita.com/usbmuxd.git/, tcprelay.py and usbmux.py are enough for me.
1. chmod +x tcprelay.py
1. Run ./tcprelay.py -t 22:2222
1. forwarding local port 2222 to remote port 22

Then you can log into your device via ssh root@localhost -p 2222. You can also apply to debugserver.
