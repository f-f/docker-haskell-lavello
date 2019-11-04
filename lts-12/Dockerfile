FROM fpco/stack-build:lts-12.21

# Make new user, make it passwordless sudo
RUN useradd -d /home/ubuntu -ms /bin/bash -g root -G sudo -p ubuntu ubuntu
RUN echo "ubuntu ALL=(ALL:ALL) NOPASSWD: ALL" > /etc/sudoers.d/ubuntu
USER ubuntu
WORKDIR /home/ubuntu

# Build Haskell dependencies that we use
RUN mkdir -p /home/ubuntu/.stack/global-project
RUN printf "resolver: lts-12.21\nallow-newer: true\npackages: []" > /home/ubuntu/.stack/global-project/stack.yaml
RUN stack setup
#  Regenerate this list with:
#  $ stack ls dependencies | grep -vE '^(spago|rts) ' | sed "s/ /-/g" | sed 's/\(^.*$\)/  \1 \\/g'
RUN stack build Cabal
RUN echo "allow-newer: true" > /home/ubuntu/.stack/config.yaml
RUN stack build \
  Cabal-2.2.0.1 \
  Diff-0.3.4 \
  Glob-0.10.0 \
  StateVar-1.1.1.1 \
  adjunctions-4.4 \
  aeson-1.4.4.0 \
  aeson-better-errors-0.9.1.0 \
  aeson-pretty-0.8.7 \
  ansi-terminal-0.8.2 \
  ansi-wl-pprint-0.6.8.2 \
  array-0.5.2.0 \
  asn1-encoding-0.9.5 \
  asn1-parse-0.9.4 \
  asn1-types-0.3.2 \
  async-2.2.1 \
  async-pool-0.9.0.2 \
  attoparsec-0.13.2.2 \
  attoparsec-iso8601-1.0.1.0 \
  base-4.11.1.0 \
  base-compat-0.10.5 \
  base-orphans-0.8.1 \
  base-prelude-1.3 \
  base16-bytestring-0.1.1.6 \
  basement-0.0.8 \
  basic-prelude-0.7.0 \
  bifunctors-5.5.3 \
  binary-0.8.5.1 \
  binary-instances-1 \
  binary-orphans-1.0.1 \
  blaze-builder-0.4.1.0 \
  bower-json-1.0.0.1 \
  byteable-0.1.1 \
  bytestring-0.10.8.2 \
  bytestring-conversion-0.3.1 \
  cabal-doctest-1.0.6 \
  case-insensitive-1.2.0.11 \
  cborg-0.2.1.0 \
  cborg-json-0.2.1.0 \
  cereal-0.5.7.0 \
  charset-0.3.7.1 \
  chunked-data-0.3.1 \
  classy-prelude-1.4.0 \
  clock-0.7.2 \
  cmdargs-0.10.20 \
  colour-2.3.4 \
  comonad-5.0.4 \
  conduit-1.3.1 \
  conduit-extra-1.3.0 \
  connection-0.2.8 \
  constraints-0.10.1 \
  containers-0.5.11.0 \
  contravariant-1.4.1 \
  cookie-0.4.4 \
  cryptohash-sha1-0.11.100.1 \
  cryptonite-0.25 \
  data-default-class-0.1.2.0 \
  data-fix-0.2.0 \
  deepseq-1.4.3.0 \
  deepseq-generics-0.2.0.0 \
  dhall-1.27.0 \
  directory-1.3.4.0 \
  distributive-0.5.3 \
  dlist-0.8.0.5 \
  dlist-instances-0.1.1.1 \
  dotgen-0.4.2 \
  double-conversion-2.0.2.0 \
  either-5 \
  enclosed-exceptions-1.0.3 \
  errors-2.3.0 \
  exceptions-0.10.2 \
  fail-4.9.0.0 \
  fgl-5.6.0.0 \
  file-embed-0.0.10.1 \
  filepath-1.4.2 \
  foldl-1.4.5 \
  free-5.0.2 \
  fsnotify-0.3.0.1 \
  ghc-boot-th-8.4.4 \
  ghc-prim-0.5.2.0 \
  github-0.23 \
  half-0.3 \
  hashable-1.2.7.0 \
  haskeline-0.7.4.3 \
  hinotify-0.3.10 \
  hostname-1.0 \
  hourglass-0.2.12 \
  http-api-data-0.3.8.1 \
  http-client-0.5.14 \
  http-client-tls-0.3.5.3 \
  http-conduit-2.3.2 \
  http-link-header-1.0.3.1 \
  http-types-0.12.3 \
  integer-gmp-1.0.2.0 \
  integer-logarithms-1.0.2.2 \
  invariant-0.5.1 \
  iso8601-time-0.1.5 \
  kan-extensions-5.2 \
  keys-3.12.1 \
  lens-family-core-1.2.3 \
  lifted-async-0.10.0.3 \
  lifted-base-0.2.3.12 \
  managed-1.0.6 \
  math-functions-0.2.1.0 \
  megaparsec-7.0.3 \
  memory-0.14.18 \
  microlens-0.4.9.1 \
  mime-types-0.1.0.8 \
  monad-control-1.0.2.3 \
  mono-traversable-1.0.9.0 \
  mono-traversable-instances-0.1.0.0 \
  mtl-2.2.2 \
  mutable-containers-0.3.4 \
  mwc-random-0.13.6.0 \
  network-2.6.3.6 \
  network-uri-2.6.1.0 \
  open-browser-0.2.1.0 \
  optional-args-1.0.2 \
  optparse-applicative-0.14.3.0 \
  parsec-3.1.13.0 \
  parser-combinators-1.0.0 \
  parsers-0.12.9 \
  pem-0.2.4 \
  pointed-5.0.1 \
  pretty-1.1.3.6 \
  prettyprinter-1.2.1 \
  prettyprinter-ansi-terminal-1.1.1.2 \
  primitive-0.6.3.0 \
  process-1.6.5.1 \
  profunctors-5.2.2 \
  random-1.1 \
  repline-0.2.1.0 \
  resourcet-1.2.2 \
  retry-0.7.7.0 \
  rio-0.1.12.0 \
  safe-0.3.17 \
  say-0.1.0.1 \
  scientific-0.3.6.2 \
  semigroupoids-5.2.2 \
  semigroups-0.18.5 \
  semver-range-0.2.8 \
  serialise-0.2.1.0 \
  shelly-1.8.1 \
  socks-0.5.6 \
  split-0.2.3.3 \
  stm-2.4.5.1 \
  stm-chans-3.0.0.4 \
  streaming-commons-0.2.1.0 \
  system-fileio-0.3.16.4 \
  system-filepath-0.4.14 \
  tagged-0.8.5 \
  tar-0.5.1.0 \
  template-haskell-2.13.0.0 \
  temporary-1.3 \
  terminfo-0.4.1.1 \
  text-1.2.3.1 \
  text-binary-0.2.1.1 \
  th-abstraction-0.2.8.0 \
  th-lift-0.8.0.1 \
  th-lift-instances-0.1.13 \
  time-1.8.0.4 \
  time-compat-1.9.2.2 \
  time-locale-compat-0.1.1.5 \
  tls-1.4.1 \
  transformers-0.5.5.0 \
  transformers-base-0.4.5.2 \
  transformers-compat-0.6.5 \
  turtle-1.5.14 \
  typed-process-0.2.6.0 \
  unix-2.7.2.2 \
  unix-compat-0.5.1 \
  unliftio-0.2.12 \
  unliftio-core-0.1.2.0 \
  unordered-containers-0.2.10.0 \
  uri-bytestring-0.3.2.1 \
  uri-encode-1.5.0.5 \
  utf8-string-1.0.1.1 \
  uuid-types-1.0.3 \
  vector-0.12.0.1 \
  vector-algorithms-0.7.0.4 \
  vector-binary-instances-0.2.5.1 \
  vector-builder-0.3.6 \
  vector-instances-3.4 \
  vector-th-unbox-0.2.1.6 \
  versions-3.5.0 \
  void-0.7.2 \
  x509-1.7.5 \
  x509-store-1.6.7 \
  x509-system-1.6.6 \
  x509-validation-1.6.11 \
  zlib-0.6.2

# Install nix
USER root
RUN  mkdir -p /nix /etc/nix && chmod a+rwx /nix && echo 'sandbox = false' > /etc/nix/nix.conf
USER ubuntu
SHELL ["/bin/bash", "-c"]
ENV USER=ubuntu
RUN touch .bash_profile && curl https://nixos.org/releases/nix/nix-2.2.2/install | sh
RUN source /home/ubuntu/.nix-profile/etc/profile.d/nix.sh
