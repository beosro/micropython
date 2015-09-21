FROM ubuntu:14.04
RUN apt-get update -y && apt-get install -y software-properties-common
RUN add-apt-repository "deb http://us.archive.ubuntu.com/ubuntu/ trusty universe multiverse"
RUN add-apt-repository "deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe multiverse"
RUN apt-get update -y && apt-get install -y make unrar autoconf automake libtool gcc g++ gperf \
    flex bison texinfo gawk ncurses-dev libexpat-dev python python-serial sed \
    git unzip 
RUN apt-get update -y && apt-get install -y wget bash-completion
RUN mkdir /build
RUN useradd build -d /build; chown build /build
RUN cd /build; sudo -iu build git clone --recursive https://github.com/pfalcon/esp-open-sdk.git
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n crosstool-NG/ct-ng || (cat crosstool-NG/build.log; exit 1)"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n toolchain"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n esptool"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n libcirom"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n standalone"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n sdk"
# RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make STANDALONE=n sdk_patch"
RUN sudo -iu build -- bash -c "cd /build/esp-open-sdk; make"
RUN sudo -iu build git clone https://github.com/micropython/micropython
RUN sudo -iu build -- bash -c "cd micropython/esp8266; git checkout v1.4.5; export PATH=/build/esp-open-sdk/xtensa-lx106-elf/bin:$PATH; make"



