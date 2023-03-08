## Concepts to keep in mind
### Machine specific override
- A variable/function specific for a machine **will always override** the original variable
    - This does not care about layer priorities
    - eg : `DUDE:${MACHINE}`'s value will override `DUDE`'s value.
    - Important to remember as machine BSP layer can override your variables, ex `WKS_FILE`
    - Best practice is to always specify it to your machine.

## Important variables
- `SDKTARGETSYSROOT` : Refers to the sysroot of the target in an SDK
- `OECORE_NATIVE_SYSROOT` : Refers to the sysroot of the native packages in an SDK

## Syntax and examples
- Parallel Make. Refers to how many cores each bitbake worker will use to compile
    - `PARALLEL_MAKE = "-j 4"`

- BB number of threads. Refers to how many workers bitbake spawns
    - `BB_NUMBER_THREADS = "4"`

- Extra paths for an append file
    - Kirstone : `FILESEXTRAPATHS:prepend := "${THISDIR}/files:"`
    - Pre kirksone : `FILESEXTRAPATHS_prepend := "${THISDIR}/files:"`

- To make image rootfs readonly:
    - `IMAGE_FEATURES:append = "read-only-rootfs"`


## How to add custom commands to SDK env-setup script
- Create a new append file called `meta-environment.bbappend`
- Append function `create_sdk_files:append()`
- echo your commands to the file `${SDK_OUTPUT}/${SDKPATH}/environment-setup-${REAL_MULTIMACH_TARGET_SYS}`

```
# Add custom varialbes to be exported when SDK environment is setup
create_sdk_files:append() {
    # CMake sysroot should be the target sysroot
    echo 'export CMAKE_SYSROOT=$SDKTARGETSYSROOT' >> ${SDK_OUTPUT}/${SDKPATH}/environment-setup-${REAL_MULTIMACH_TARGET_SYS}

    # For CMake to find programs, it should look at the native SDK sysroot.
    echo 'export CMAKE_PROGRAM_PATH=$OECORE_NATIVE_SYSROOT/usr/bin' >> ${SDK_OUTPUT}/${SDKPATH}/environment-setup-${REAL_MULTIMACH_TARGET_SYS}
}
```

## How to flash a wic image
- if its compressed to bz2 : 
    - `bzcat <image.wic.bz2> | sudo dd of=/dev/<dev> bs=1M status=progress && sync`
