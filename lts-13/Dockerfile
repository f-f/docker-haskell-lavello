FROM fpco/stack-build:lts-13.0

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN stack build --resolver lts-13.0 \
  dhall dhall-json megaparsec repline serialise \
  turtle filepath file-embed aeson aeson-pretty containers directory bytestring \
  http-client http-client-tls \
  async process basement zlib tls transformers-base unliftio-core exceptions \
  dotgen

# Install nix
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN curl https://nixos.org/nix/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
