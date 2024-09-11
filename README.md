# ENGICAM BSP RELEASE

To get the BSP you need to have repo installed and use it as:

Install the repo utility:

    $: mkdir ~/bin
    $: curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+x ~/bin/repo

Download the BSP source:

    $: PATH=${PATH}:~/bin
    $: mkdir -p ~/yocto/mickledore_v24.06-st
    $: cd ~/yocto/mickledore_v24.06-st
    $: curl https://raw.githubusercontent.com/engicam-stable/engicam-bsp-release/mickledore_v24.06-st/Dockerfile > Dockerfile
    $: repo init -u https://github.com/engicam-stable/engicam-bsp-release.git -b mickledore_v24.06-st -m engicam-bsp-release.xml
    $: repo sync

|   yocto-codename      |         modules       |
|:---------------------:|:---------------------:|
| mickledore_v24.06-st  |    iCore STM32MP257   |

## Set enviroment variables

Enter Yocto folder and launch the script setting enviroment variables:

	DISTRO=<distro name> MACHINE=<machine name> source layers/meta-engicam-st/scripts/envsetup.sh <build dir>

where ``<machine-name>`` corresponds to the module for which the operative system image will be compiled and ``<build-dir-name>`` is the bulding directory name chosen by the user, as in the following example:

	 DISTRO=openstlinux-weston MACHINE=stm32mp25-icore.conf source layers/meta-engicam-st/scripts/envsetup.sh build

where a directory named ``build`` is created and enviroment variables are set to compile images for the module ``iCore STM32MP2``. Please notice that the available ``<machine-name>`` correspond to the names of the relative configuration files in ``layers/meta-engicam-st/conf/machine``.

## Compile and flash image on sdcard

Compile the desired image with bitbake using the command (in this example we compile the recipe ``st-image-weston.bb`` for ``iCore STM32MP2``):

	bitbake st-image-weston

Once the image is compiled it will be possible to find in the build directory a deploy folder with the image files. The relative path to this folder from the yocto directory will be:

	tmp-glibc/deploy/images/stm32mp25-icore

