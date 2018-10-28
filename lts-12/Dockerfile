FROM fpco/stack-build:lts-12.14

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN stack build --resolver lts-12.14 \
  dhall-1.18.0 dhall-json-1.2.4 megaparsec-7.0.2 repline-0.2.0.0 serialise-0.2.1.0 \
  turtle filepath file-embed aeson aeson-pretty containers directory bytestring  

# Install nix
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN curl https://nixos.org/nix/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
