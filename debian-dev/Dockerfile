FROM debian
ENV ME='hacker'
COPY install_packages create_user /tmp
RUN /tmp/install_packages && /tmp/create_user
CMD zsh

