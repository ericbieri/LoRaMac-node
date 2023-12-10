# VSCode Dev Container development

A Dockerfile has been added, which contains a complete development environment that is consistent across all operating systems supporting Docker.

When VSCode encounters a `.devcontainer` directory, it will prompt you to open the workspace inside a [DevContainer](https://code.visualstudio.com/docs/devcontainers/containers).  The entire build system is defined by the *DockerFile*, 

## Initial Setup
1. Install all [prerequisites](##prerequisites)
2. Open `hellow_world.code-workspace` in VSCode.  You may be prompted to open the workspace in a dev container - select **Reopen In Container**.  This will build and start the docker contain, then reopen VSCode *inside* the container. 

    ![Alt text](images/dev_container_prompt.png)

    After VSCOde is running inside the container, the lower left corner of VSCode wil look something like this:

    ![Alt text](images/env_devContainer.png)
3. Your environment is all setup, continue with instructions from development-environment.md

## Prerequisites

### MS Windows based development

* [Docker Desktop](https://www.docker.com/products/docker-desktop/)
* WSL 2
* VSCode
* VSCode Extension : Dev Containers - Microsoft
* VSCode Extension : C++ Extension Pack - Microsoft
* VSCode Extension : CMake - twxs (optional - CMake syntax highliting)

### Linux based development
* Docker Desktop
* VSCode
* VSCode Extension : Dev Containers - Microsoft
* VSCode Extension : C++ Extension Pack - Microsoft
* VSCode Extension : CMake - twxs (optional - CMake syntax highliting)


## Commands
working cmake call:

cmake -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_TOOLCHAIN_FILE="../cmake/toolchain-arm-none-eabi.cmake" \
        -DAPPLICATION="ping-pong" \
        -DMODULATION="LORA" \
        -DREGION_EU868="ON" \
        -DREGION_US915="OFF" \
        -DREGION_CN779="OFF" \
        -DREGION_EU433="OFF" \
        -DREGION_AU915="OFF" \
        -DREGION_AS923="OFF" \
        -DREGION_CN470="OFF" \
        -DREGION_KR920="OFF" \
        -DREGION_IN865="OFF" \
        -DREGION_RU864="OFF" \
        -DBOARD="NucleoL476" \
        -DMBED_RADIO_SHIELD="LR1110MB1XXS" \
        -DUSE_RADIO_DEBUG="ON" ..



cmake -DCMAKE_BUILD_TYPE=Release \
        -DTOOLCHAIN_PREFIX="/opt/arm-gnu-toolchain-12.3.rel1-x86_64-arm-none-eabi/bin" \
        -DCMAKE_TOOLCHAIN_FILE="../cmake/toolchain-arm-none-eabi.cmake" \
		-DCMAKE_C_COMPILER="/opt/arm-gnu-toolchain-12.3.rel1-x86_64-arm-none-eabi/bin/arm-none-eabi-gcc"  \
		-DCMAKE_ASM_COMPILER="/opt/arm-gnu-toolchain-12.3.rel1-x86_64-arm-none-eabi/bin/arm-none-eabi-gcc"  \ 
		-DCMAKE_CXX_COMPILER="/opt/arm-gnu-toolchain-12.3.rel1-x86_64-arm-none-eabi/bin/arm-none-eabi-g++" \
        -DAPPLICATION="LoRaMac" \
        -DSUB_PROJECT="periodic-uplink-lpp" \
        -DCLASSB_ENABLED="ON" \
        -DACTIVE_REGION="LORAMAC_REGION_EU868" \
        -DREGION_EU868="ON" \
        -DREGION_US915="OFF" \
        -DREGION_CN779="OFF" \
        -DREGION_EU433="OFF" \
        -DREGION_AU915="OFF" \
        -DREGION_AS923="OFF" \
        -DREGION_CN470="OFF" \
        -DREGION_KR920="OFF" \
        -DREGION_IN865="OFF" \
        -DREGION_RU864="OFF" \
        -DBOARD="NucleoL476" \
        -DMBED_RADIO_SHIELD="LR1110MB1XXS" \
        -DSECURE_ELEMENT="LR1110_SE" \
        -DSECURE_ELEMENT_PRE_PROVISIONED="ON" \
        -DUSE_RADIO_DEBUG="ON" ..
