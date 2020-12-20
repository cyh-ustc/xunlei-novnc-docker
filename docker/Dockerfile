FROM ubuntu:bionic

#RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list

# Install git, supervisor, VNC, & X11 packages
RUN set -ex; \
    export DEBIAN_FRONTEND=noninteractive; \
    apt-get update; \
    apt-get install -y \
      bash \
      fluxbox \
      git \
      net-tools \
      novnc \
      supervisor \
      x11vnc \
      xterm \
      xvfb \
      openssh-server

# Setup demo environment variables
ENV HOME=/root \
    DEBIAN_FRONTEND=noninteractive \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    LC_ALL=C.UTF-8 \
    DISPLAY=:0.0 \
    DISPLAY_WIDTH=1024 \
    DISPLAY_HEIGHT=768 \
    RUN_XTERM=yes \
    RUN_FLUXBOX=yes

RUN apt-get install -y \
    language-pack-zh-hans \
    fonts-droid-fallback \
    ttf-wqy-zenhei \
    ttf-wqy-microhei \
    fonts-arphic-ukai \
    fonts-arphic-uming

RUN git clone https://github.com/cyh-ustc/deepin-wine-ubuntu.git; \
    cd deepin-wine-ubuntu; \
    ./install.sh

RUN git clone https://github.com/wszqkzqk/deepin-wine-containers-for-ubuntu.git --depth=1; \
    cd deepin-wine-containers-for-ubuntu; \
    dpkg -i deepin.com.thunderspeed_7.10.35.366deepin18_i386.deb

COPY . /app
CMD ["/app/entrypoint.sh"]
EXPOSE 8080 22
