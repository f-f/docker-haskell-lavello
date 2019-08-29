FROM fpco/stack-build:lts-14.3

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN stack build --resolver lts-14.3 \
  dhall dhall-json megaparsec repline serialise \
  turtle filepath file-embed aeson aeson-pretty containers directory bytestring \
  http-client http-client-tls http-conduit Glob ansi-terminal binary-instances-1 \
  async process basement zlib tls transformers-base unliftio-core exceptions \
  dotgen github retry time semver-range tar temporary versions safe fsnotify

# Install nix
USER root
RUN  mkdir -p /nix /etc/nix && chmod a+rwx /nix && echo 'sandbox = false' > /etc/nix/nix.conf
USER ubuntu
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN touch .bash_profile && curl https://nixos.org/releases/nix/nix-2.2.2/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
