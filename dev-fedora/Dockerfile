FROM fedora:21
MAINTAINER jknight@humanlongevity.com
RUN yum -y update && yum install -y \
  git \
  curl \
  vim-enhanced \
  tmux  \
  gcc \
  gcc-c++ \
  openssh-server  \
  zsh  \
  numpy  \
  scipy  \
  python-tables  \
  python-pip  \
  zlib-devel \
  snappy \
  snappy-devel \
  blosc \
  blosc-devel \
  lz4 \
  lz4-devel \
  Cython
RUN pip install \
  pandas \
  ipython \
  pyzmq \
  redis \
  msgpack-python \
  flake8 \
  python-snappy \
  blosc \
  lz4
RUN git clone git://github.com/andsens/homeshick.git $HOME/.homesick/repos/homeshick && \
  printf '\nsource $HOME/.homesick/repos/homeshick/homeshick.sh\n' >> $HOME/.bashrc
RUN source $HOME/.bashrc && \
  homeshick clone -q https://github.com/binarybana/dotfiles.git && \
  homeshick link dotfiles && \
  vim -E +PluginInstall +qall > /dev/null; true
