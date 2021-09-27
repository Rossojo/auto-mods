FROM ubuntu:20.04

RUN apt-get update && apt-get install -y --fix-missing gcc g++ cmake libboost-iostreams-dev libboost-program-options-dev zlib1g-dev liblz4-dev tree
COPY . /mods-build/auto-mods
WORKDIR /mods-build/auto-mods

RUN chmod +x scripts/build.sh
RUN scripts/build.sh

FROM ubuntu:20.04

COPY --from=0 /mods-build/auto-mods/build/create-data-mod /opt/auto-mods/create-data-mod
RUN chmod u+x /opt/auto-mods/create-data-mod

WORKDIR /opt/auto-mods
