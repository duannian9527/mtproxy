FROM debian:12

RUN apt update -y && \
    apt install -y openssl python3 python3-cryptography && \
    apt autoremove -y && apt clean all && rm -rf /var/lib/apt/lists/*

RUN useradd -m mtproxy -u 10000

WORKDIR /home/mtproxy/

COPY --chown=mtproxy:mtproxy docker/mtproxy.py docker/config.py docker/entrypoint.sh ./

RUN chmod +x entrypoint.sh

USER mtproxy

ENTRYPOINT ["./entrypoint.sh"]
