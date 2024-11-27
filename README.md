# Hashable fails to build with WASM backend on arrach64 darwin

## Background

The same constraints builds successfully within Linux x86_64 container.

## Procedure

Just build fails:

```bash
$ source ~/.ghc-wasm/env
$ wasm32-wasi-cabal build
Build profile: -w ghc-9.10.1.20241115 -O1
In order, the following will be built (use -v for more details):
 - hashable-1.4.4.0 (lib) (requires build)
 - ghc-wasm-hashable-build-0.1.0.0 (exe:ghc-wasm-hashable-build) (first run)
Created semaphore called cabal_semaphore_1 with 10 slots.
Starting     hashable-1.4.4.0 (lib)
Building     hashable-1.4.4.0 (lib)

Failed to build hashable-1.4.4.0.
Build log (
/Users/hiromi/.ghc-wasm/.cabal/logs/ghc-9.10.1.20241115/hshbl-1.4.4.0-8f71226e.log
):
Configuring library for hashable-1.4.4.0...
Preprocessing library for hashable-1.4.4.0...
Building library for hashable-1.4.4.0...
[1 of 7] Compiling Data.Hashable.Imports ( src/Data/Hashable/Imports.hs, dist/build/Data/Hashable/Imports.o, dist/build/Data/Hashable/Imports.dyn_o )
[2 of 7] Compiling Data.Hashable.LowLevel ( src/Data/Hashable/LowLevel.hs, dist/build/Data/Hashable/LowLevel.o, dist/build/Data/Hashable/LowLevel.dyn_o )
In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:223:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/cdefs.h:1022:2: error:
     error: Unsupported architecture
     1022 | #error Unsupported architecture
          |  ^
     |
1022 | #error Unsupported architecture
     |  ^

In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:226:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/_types.h:27:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:33:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/machine/_types.h:36:2: error:
     error: architecture not supported
       36 | #error architecture not supported
          |  ^
   |
36 | #error architecture not supported
   |  ^

In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:226:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/_types.h:27:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:55:9: error:
     error: unknown type name '__int64_t'; did you mean '__int128_t'?
       55 | typedef __int64_t       __darwin_blkcnt_t;      /* total blocks */
          |         ^~~~~~~~~
          |         __int128_t
   |
55 | typedef __int64_t       __darwin_blkcnt_t;      /* total blocks */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:56:9: error:
     error: unknown type name '__int32_t'; did you mean '__int128_t'?
       56 | typedef __int32_t       __darwin_blksize_t;     /* preferred block size */
          |         ^~~~~~~~~
          |         __int128_t
   |
56 | typedef __int32_t       __darwin_blksize_t;     /* preferred block size */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:57:9: error:
     error: unknown type name '__int32_t'; did you mean '__int128_t'?
       57 | typedef __int32_t       __darwin_dev_t;         /* dev_t */
          |         ^~~~~~~~~
          |         __int128_t
   |
57 | typedef __int32_t       __darwin_dev_t;         /* dev_t */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:60:9: error:
     error: unknown type name '__uint32_t'; did you mean '__uint128_t'?
       60 | typedef __uint32_t      __darwin_gid_t;         /* [???] process and group IDs */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
60 | typedef __uint32_t      __darwin_gid_t;         /* [???] process and group IDs */
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:61:9: error:
     error: unknown type name '__uint32_t'; did you mean '__uint128_t'?
       61 | typedef __uint32_t      __darwin_id_t;          /* [XSI] pid_t, uid_t, or gid_t*/
          |         ^~~~~~~~~~
          |         __uint128_t
   |
61 | typedef __uint32_t      __darwin_id_t;          /* [XSI] pid_t, uid_t, or gid_t*/
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:62:9: error:
     error: unknown type name '__uint64_t'; did you mean '__uint128_t'?
       62 | typedef __uint64_t      __darwin_ino64_t;       /* [???] Used for 64 bit inodes */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
62 | typedef __uint64_t      __darwin_ino64_t;       /* [???] Used for 64 bit inodes */
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:68:9: error:
     error: unknown type name '__darwin_natural_t'
       68 | typedef __darwin_natural_t __darwin_mach_port_name_t; /* Used by mach */
          |         ^
   |
68 | typedef __darwin_natural_t __darwin_mach_port_name_t; /* Used by mach */
   |         ^

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:70:9: error:
     error: unknown type name '__uint16_t'; did you mean '__uint128_t'?
       70 | typedef __uint16_t      __darwin_mode_t;        /* [???] Some file attributes */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
70 | typedef __uint16_t      __darwin_mode_t;        /* [???] Some file attributes */
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:71:9: error:
     error: unknown type name '__int64_t'; did you mean '__int128_t'?
       71 | typedef __int64_t       __darwin_off_t;         /* [???] Used for file sizes */
          |         ^~~~~~~~~
          |         __int128_t
   |
71 | typedef __int64_t       __darwin_off_t;         /* [???] Used for file sizes */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:72:9: error:
     error: unknown type name '__int32_t'; did you mean '__int128_t'?
       72 | typedef __int32_t       __darwin_pid_t;         /* [???] process and group IDs */
          |         ^~~~~~~~~
          |         __int128_t
   |
72 | typedef __int32_t       __darwin_pid_t;         /* [???] process and group IDs */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:73:9: error:
     error: unknown type name '__uint32_t'; did you mean '__uint128_t'?
       73 | typedef __uint32_t      __darwin_sigset_t;      /* [???] signal set */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
73 | typedef __uint32_t      __darwin_sigset_t;      /* [???] signal set */
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:74:9: error:
     error: unknown type name '__int32_t'; did you mean '__int128_t'?
       74 | typedef __int32_t       __darwin_suseconds_t;   /* [???] microseconds */
          |         ^~~~~~~~~
          |         __int128_t
   |
74 | typedef __int32_t       __darwin_suseconds_t;   /* [???] microseconds */
   |         ^

note: '__int128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:75:9: error:
     error: unknown type name '__uint32_t'; did you mean '__uint128_t'?
       75 | typedef __uint32_t      __darwin_uid_t;         /* [???] user IDs */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
75 | typedef __uint32_t      __darwin_uid_t;         /* [???] user IDs */
   |         ^

note: '__uint128_t' declared here
/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types.h:76:9: error:
     error: unknown type name '__uint32_t'; did you mean '__uint128_t'?
       76 | typedef __uint32_t      __darwin_useconds_t;    /* [???] microseconds */
          |         ^~~~~~~~~~
          |         __uint128_t
   |
76 | typedef __uint32_t      __darwin_useconds_t;    /* [???] microseconds */
   |         ^

note: '__uint128_t' declared here
In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:227:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types/_wchar_t.h:34:9: error:
     error: unknown type name '__darwin_wchar_t'
       34 | typedef __darwin_wchar_t wchar_t;
          |         ^
   |
34 | typedef __darwin_wchar_t wchar_t;
   |         ^

In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:229:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/stdint.h:53:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types/_intptr_t.h:30:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/machine/types.h:39:2: error:
     error: architecture not supported
       39 | #error architecture not supported
          |  ^
   |
39 | #error architecture not supported
   |  ^

In file included from /var/folders/pv/mtbzyjyj229g928n710c9d_40000gn/T/ghc52896_0/ghc_10.c:2:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/Rts.h:23:0: error:
    

In file included from /Users/hiromi/.ghc-wasm/wasm32-wasi-ghc/lib/wasm32-wasi-ghc-9.10.1.20241115/lib/../lib/wasm32-wasi-ghc-9.10.1.20241115/rts-1.0.2/include/stg/Types.h:32:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/inttypes.h:229:0: error:
    

In file included from /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/stdint.h:53:0: error:
    

/Library/Developer/CommandLineTools/SDKs/MacOSX.sdk/usr/include/sys/_types/_intptr_t.h:32:9: error:
     error: unknown type name '__darwin_intptr_t'
       32 | typedef __darwin_intptr_t       intptr_t;
          |         ^
   |
32 | typedef __darwin_intptr_t       intptr_t;
   |         ^

fatal error: too many errors emitted, stopping now [-ferror-limit=]
20 errors generated.
<no location info>: error:
    `wasm32-wasi-clang' failed in phase `C Compiler'. (Exit code: 1)

Error: [Cabal-7125]
Failed to build hashable-1.4.4.0 (which is required by exe:ghc-wasm-hashable-build from ghc-wasm-hashable-build-0.1.0.0). See the build log above for details.
```

Specifying `--with-*` options more explicitly didn't help:

```bash
wasm32-wasi-cabal \
--with-compiler=wasm32-wasi-ghc-9.10.1.20241115 \
--with-ghc=wasm32-wasi-ghc-9.10.1.20241115 \
--with-ghc-pkg=wasm32-wasi-ghc-pkg-9.10.1.20241115 \
--with-hc-pkg=wasm32-wasi-ghc-pkg-9.10.1.20241115 \
--with-hsc2hs=wasm32-wasi-hsc2hs-ghc-9.10.1.20241115 \
build
```

## Newer hashable

Building with hashable-1.5.0.0 will result in different error:

```bash
Resolving dependencies...
Build profile: -w ghc-9.10.1.20241115 -O1
In order, the following will be built (use -v for more details):
 - hashable-1.5.0.0 (lib) (requires build)
 - ghc-wasm-hashable-build-0.1.0.0 (exe:ghc-wasm-hashable-build) (first run)
Created semaphore called cabal_semaphore_9 with 10 slots.
Starting     hashable-1.5.0.0 (lib)

Failed to build hashable-1.5.0.0. The failure occurred during the configure
step.
Build log (
/Users/hiromi/.ghc-wasm/.cabal/logs/ghc-9.10.1.20241115/hshbl-1.5.0.0-19bf027f.log
):
Configuring library for hashable-1.5.0.0...
Error: [Cabal-4345]
Missing dependency on a foreign library:
* Missing (or bad) header file: HsHashable.h
If the header file does exist, it may contain errors that are caught by the C compiler at the preprocessing stage. In this case you can re-run 'Setup configure' with the verbosity flag -v3 to see the error messages.

Error: [Cabal-7125]
Failed to build hashable-1.5.0.0 (which is required by exe:ghc-wasm-hashable-build from ghc-wasm-hashable-build-0.1.0.0). See the build log above for details.
```

