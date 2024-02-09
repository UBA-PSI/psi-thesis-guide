FROM alpine:3.19

# update and install system dependencies
RUN apk update
RUN apk add --no-cache \
  wget \
  gpg \
  make \
  bash \
  perl \
  python3 \
  py3-pygments

# install texlive
RUN mkdir install-tl
RUN wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz; \
  tar -xvf install-tl-unx.tar.gz -C install-tl --strip-components=1; \
  echo "selected_scheme scheme-basic" > install-tl/texlive.profile; \
  install-tl/install-tl -profile install-tl/texlive.profile; \
  rm -rf install-tl; \
  rm install-tl-unx.tar.gz

ENV PATH="/usr/local/texlive/2023/bin/x86_64-linuxmusl:${PATH}"

# setup a work directory
WORKDIR /build

# only copy the depenency file to avoid reinstalling on every file change
COPY deps.txt /build/deps.txt

# Update tlmgr to make sure we are using the latest version
RUN tlmgr update --self

# Install packages from deps.txt
RUN grep -v '^#' deps.txt | xargs tlmgr install

# copy the rest of the files
COPY . /build

# setup a volume for the build
VOLUME ["/build"]

# build the pdf
ENTRYPOINT ["make"]
