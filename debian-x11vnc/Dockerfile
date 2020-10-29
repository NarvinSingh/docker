# Debian Xll over VNC

FROM debian
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y xvfb x11vnc && \
    mkdir ~/.vnc
EXPOSE 5900
CMD x11vnc -storepasswd "${VNC_PASSWD:-1234}" ~/.vnc/passwd && \
    x11vnc -forever -usepw -create

