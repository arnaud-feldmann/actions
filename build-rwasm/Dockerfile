ARG WEBR_IMAGE=ghcr.io/r-wasm/webr:main

# Container image that runs your code
FROM $WEBR_IMAGE

RUN git clone --depth 1 --branch apache-arrow-24.0.0 https://github.com/apache/arrow.git /tmp/arrow && \
    cd /tmp/arrow/cpp && \
    emcmake cmake --preset "ninja-release-emscripten" && \
    ninja install && \
    rm -rf /tmp/arrow

# Copies your code file from your action repository to the filesystem path `/` of the container
COPY code.R /code.R

# Code file to execute when the docker container starts up (`entrypoint.sh`)
ENTRYPOINT [ "Rscript" ]
# ENTRYPOINT [ "/bin/bash", "-l", "-c" ]
