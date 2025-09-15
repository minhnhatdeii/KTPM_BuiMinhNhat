FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

# Cập nhật và cài các gói cần thiết
RUN apt-get update && apt-get install -y \
    xfce4 xfce4-goodies \
    x11vnc xvfb \
    sudo \
    net-tools \
    vim \
    dbus-x11 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Tạo user không phải root
RUN useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo
USER docker
WORKDIR /home/docker

# Mật khẩu VNC
RUN mkdir -p ~/.vnc && \
    x11vnc -storepasswd 1234 ~/.vnc/passwd

EXPOSE 5900

CMD ["x11vnc", "-forever", "-usepw", "-create"]
