FROM fpco/stack-build:lts-12.21

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN stack build --resolver lts-12.21 \
  dhall-1.19.1 dhall-json-1.2.5 megaparsec-7.0.2 repline-0.2.0.0 serialise-0.2.1.0 \
  turtle filepath file-embed aeson aeson-pretty containers directory bytestring \
  http-client http-client-tls \
  async process basement zlib tls transformers-base unliftio-core exceptions \
  dotgen-0.4.2@sha256:309b7cc8a3593a8e48bee7b53020d5f72db156d58edf78a0214f58fbb84b292b

# Install nix
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN curl https://nixos.org/nix/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
