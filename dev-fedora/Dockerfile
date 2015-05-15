FROM fedora:21
MAINTAINER Jason Knight
RUN yum -y update; yum install -y \
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
  Cython \
  freetype-devel \
  libpng-devel \
  jq \
  htop \
  tar \
  wget \
  make \
  m4 \
  gmp-devel \
  patch \
  bzip2 \
  dnf || true
RUN pip install \
  pandas \
  ipython \
  pyzmq \
  redis \
  msgpack-python \
  flake8 \
  python-snappy \
  blosc \
  lz4 \
  tornado \
  jinja2 \
  jsonschema \
  matplotlib \
  awscli \
  bokeh
RUN dnf install -y dnf-plugins-core && dnf copr enable -y nalimilan/julia-nightlies && dnf install -y julia
RUN julia -e '[Pkg.add(x) for x in split("DataFrames Distributions Gadfly Bokeh HDF5 MsgPack")]'
RUN git clone git://github.com/andsens/homeshick.git $HOME/.homesick/repos/homeshick && \
  printf '\nsource $HOME/.homesick/repos/homeshick/homeshick.sh\n' >> $HOME/.bashrc
RUN source $HOME/.bashrc && \
  homeshick clone -qqq https://github.com/binarybana/dotfiles.git && \
  homeshick link dotfiles
RUN chsh --shell /bin/zsh && echo 'alias sudo=""' >> ~/.zshrc

CMD ["/bin/zsh"]
