AUTHOR : mzaabar@gmail.com (Mehdi ZAABAR)
DATE : September 11th 2022

SDK has been generated using yocto Dunfell branch 
RDA8810PL is similar to atmel sama5d4 : an application processor from microchip. Both have the cortexA5 ARMv7 Processor rev 1 with tuning parameters "swp half thumb fastmult vfp edsp thumbee neon vfpv3 tls vfpv4". I copied and changed meta-atmel yocto metalayer to create rda8810 soc family and rda8810pl chip for a new board definition orangepi-i96.
I used poky linux-dummy as kernel and poky u-boot as bootloader and I was only interested in creating the toochain.

I have not tested recompiling orangepii96 kernel and u-boot with this toolchain, linaro toochain is always available and provides the needs of a kernel and u-boot. Though, I could not cross compile userland applications with linaro toochain, I had a problem with the --sysroot, so I decided to build a more recent toochain.

SDK is compatible with Orangepi-2G-IOT also.


Assemble SDK installation script parts :
cat poky-rda8810-glibc-x86_64-core-image-minimal-armv7at2hf-neon-orangepi-i96-toolchain-3.1.19.sh-aa poky-rda8810-glibc-x86_64-core-image-minimal-armv7at2hf-neon-orangepi-i96-toolchain-3.1.19.sh-ab >poky-rda8810-glibc-x86_64-core-image-minimal-armv7at2hf-neon-orangepi-i96-toolchain-3.1.19.sh
check md5sum of the installator against md5sum.txt file contents
md5sum poky-rda8810-glibc-x86_64-core-image-minimal-armv7at2hf-neon-orangepi-i96-toolchain-3.1.19.sh


Install the SDK : 
run the script on your PC ( ubuntu 19.10 tested) to install the toolchain
#poky-rda8810-glibc-x86_64-core-image-minimal-armv7at2hf-neon-orangepi-i96-toolchain-3.1.19.sh
run :
#source /path/to/chosen/install/dir/environment-setup-armv7at2hf-neon-poky-linux-gnueabi
Done, that's all.
To crosscompile, use 
#$CC source_file_dir.c -o exe_name

transfer exe_name to your OrangePi I96 with zmodem over serial line or with scp then execute it.
Good fun with orangepi i96.
