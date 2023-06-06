# ENGICAM BSP RELEASE

To get the BSP you need to have repo installed and use it as:

Install the repo utility:

    $: mkdir ~/bin
    $: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+x ~/bin/repo

Download the BSP source:

    $: PATH=${PATH}:~/bin
    $: mkdir -p ~/yocto/kirkstone
    $: cd ~/yocto/kirkstone
    $: repo init -u https://github.com/engicam-stable/engicam-bsp-release.git -b kirkstone-rockchip -m engicam-bsp-release.xml
    $: repo sync

## Set enviroment variables

Enter Yocto folder and launch the script setting enviroment variables:

```shell
~/yocto $ source poky/oe-init-build-env
```

Now you need to edit the **conf/local.conf** file inserting your machine, to check the available machines look in the **conf/machine** of this meta-layer.

```
  MACHINE = "px30-icore-starterkit"
```

## Configure yocto layers

Now you need to update the layers:

```
~/yocto $ bitbake-layers add-layer ../poky/meta-openembedded/meta-oe
~/yocto $ bitbake-layers add-layer ../poky/meta-rockchip
~/yocto $ bitbake-layers add-layer ../poky/meta-engicam-rockchip
```

## Compile and flash image on sdcard

Compile the desired image with bitbake using the command:

	bitbake engicam-image-weston

At the end of a successful build, you should have an .wic image in `/path/to/yocto/build/tmp/deploy/images/<MACHINE>/`.