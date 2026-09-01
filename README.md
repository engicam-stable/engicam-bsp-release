# ENGICAM BSP RELEASE

To get the BSP you need to have repo installed and use it as:

Install the repo utility:

    $: mkdir -p ~/bin
    $: PATH="${HOME}/bin:${PATH}"
    $: curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    $: chmod a+rx ~/bin/repo

Download the BSP source:

    $: export PROJ_ROOT=`pwd`
    $: repo init -u https://github.com/engicam-stable/engicam-bsp-release.git -b rity-scarthgap-v26.0 -m engicam-bsp-release.xml
    $: repo sync

Configure Build Environment:

    $: export TEMPLATECONF=$PROJ_ROOT/src/meta-engicam-mediatek/conf/templates/default
    $: source src/poky/oe-init-build-env build
    $: export BUILD_DIR=`pwd`

Compile and flash image:

    $: bitbake rity-demo-image

Once the image is compiled it will be possible to find in the build directory a deploy folder with the image files. The relative path to this folder from the yocto directory will be:

    $: tmp/deploy/images/genio-720-smarcore-evb-ufs
