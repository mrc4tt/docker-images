FROM        ubuntu:18.04

LABEL       author="Pterodactyl Software - Edited by mrc4tt" maintainer="mikkel.linddk@gmail.com"

ENV         DEBIAN_FRONTEND noninteractive
ENV         TERM screen
# Install Dependencies
RUN         dpkg --add-architecture i386 \
            && apt-get update \
            && apt-get upgrade -y \
            && apt-get install -y tar curl gcc g++ lib32gcc1 libgcc1 libcurl4-gnutls-dev:i386 libssl1.0.0:i386 libcurl4:i386 curl lib32tinfo5 libtinfo5:i386 ca-certificates lib32z1 lib32stdc++6 libncurses5:i386 libcurl3-gnutls:i386 iproute2 gdb libsdl1.2debian libfontconfig libsdl2-2.0-0:i386 telnet net-tools netcat tzdata \
# clean our package cache to keep img size down
            tput setaf 2; echo "Cleaning packages..."; tput sgr0;           \
            apt-get autoremove -y                                           \
            && apt-get clean                                                \
            && rm -rf /var/lib/apt/lists/*;                                 \
# create our container user
            tput setaf 2; echo "Creating container user..."; tput sgr0;     \
            useradd -U -m -d /home/container -s /bin/bash container;        \
            tput setaf 2; echo "Done!"; tput sgr0;

USER        container:container
ENV         HOME /home/container
WORKDIR     /home/container

COPY        source-sourcemod/entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]