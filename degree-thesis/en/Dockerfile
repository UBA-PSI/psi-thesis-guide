FROM alpine:3.19
RUN apk update
RUN apk add --no-cache \
  wget \
  gpg \
  make \
  bash \
  perl 
RUN mkdir install-tl
Run wget http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz; \
  tar -xvf install-tl-unx.tar.gz -C install-tl --strip-components=1; \
  echo "selected_scheme scheme-basic" > install-tl/texlive.profile; \
  install-tl/install-tl -profile install-tl/texlive.profile; \
  rm -rf install-tl; \
  rm install-tl-unx.tar.gz

ENV PATH="/usr/local/texlive/2023/bin/x86_64-linuxmusl:${PATH}"
WORKDIR /build
COPY deps.txt /build/deps.txt
# Install packages
RUN tlmgr install `cat deps.txt`
COPY . /build
Volume ["/build"]
ENTRYPOINT ["make"]
