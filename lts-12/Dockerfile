FROM fpco/stack-build:lts-12.21

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN stack build --resolver lts-12.21 \
  dhall-1.19.1 dhall-json-1.2.5 megaparsec-7.0.2 repline-0.2.0.0 serialise-0.2.1.0 dotgen-0.4.2 \
  text turtle filepath file-embed aeson aeson-pretty containers dhall dhall-json \
  bytestring prettyprinter async-pool process network-uri github versions lens \
  safe fsnotify Glob async stm directory mtl exceptions unliftio \
  http-client http-client-tls basement zlib tls transformers-base unliftio-core exceptions

# Install nix
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN curl https://nixos.org/nix/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
