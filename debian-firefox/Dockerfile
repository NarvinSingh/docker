# Firefox over VNC on Debian

FROM narvin/debian-x11vnc
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y firefox-esr && \
    printf 'firefox\n' >> /etc/bash.bashrc
CMD x11vnc -storepasswd "${VNC_PASSWD:-1234}" ~/.vnc/passwd && \
    x11vnc -forever -usepw -create

