# Debian dev build
# ================
FROM debian:buster
LABEL maintainer="Narvin Singh <Narvin.A.Singh@gmail.com>"

# Install zsh
# -----------
RUN apt-get update \
  && apt-get install -y zsh \
  && rm -rf /var/lib/apt/lists/*

# Configure environment
# ---------------------
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
RUN ln -sf /usr/share/zoneinfo/America/New_York /etc/localtime \
  && printf "\nexport TERM=xterm-256color\n" >> /etc/zsh/zshenv \
  && printf "\nexport ZDOTDIR=\${HOME}/.config/zsh\n" >> /etc/zsh/zshenv \
  && printf "\nexport TERM=xterm-256color\n" >> /etc/bash.bashrc \
  && printf "\nsource \${HOME}/.config/bash/bashrc\n" >> /etc/bash.bashrc \
  && rm /etc/skel/.bashrc

# Create user
# -----------
RUN useradd -m -s /bin/zsh dev

# Give user sudo
# --------------
RUN apt-get update \
  && apt-get install -y sudo \
  && rm -rf /var/lib/apt/lists/* \
  && printf 'debian\ndebian\n' | passwd dev \
  && gpasswd -a dev sudo

# Install packages
# ----------------
RUN apt-get update \
  && apt-get install -y \
    git \
    vim \
  && rm -rf /var/lib/apt/lists/*

# Switch user
# -----------
USER dev
WORKDIR /home/dev

# Start shell
# -----------
ENTRYPOINT ["zsh"]

