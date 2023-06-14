FROM alpine:3.18
LABEL maintainer=opensource@rpil.io
RUN \
    addgroup -S nvimuser && \
    adduser -S nvimuser -G nvimuser && \
    apk update && \
    apk add --no-cache curl=8.1.2-r0 wget=1.21.4-r0 zip=3.0-r12 tar=1.34-r3 gzip=1.12-r1 alpine-sdk=1.0-r1 \
    neovim=0.9.0-r2 ripgrep=13.0.0-r3 lazygit=0.38.2-r0 \
    nodejs=18.16.0-r1 npm=9.6.6-r0 python3=3.11.4-r0 py3-pip=23.1.2-r0 cargo=1.70.0-r0 go=1.20.5-r0
USER nvimuser:nvimuser
WORKDIR /home/nvimuser
RUN \
    mkdir /home/nvimuser/.config && \
    git clone --depth=1 https://github.com/NvChad/NvChad /home/nvimuser/.config/nvim
COPY chadrc.lua /home/nvimuser/.config/nvim/lua/custom/chadrc.lua
RUN nvim --headless "+Lazy! sync" +q
CMD ["nvim"]
