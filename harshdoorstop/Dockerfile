FROM cm2network/steamcmd

ENV APPID=950900 \
    VALIDATE=1 \
    INSTALL_DIR=/home/steam/ohd

RUN /home/steam/steamcmd/steamcmd.sh +force_install_dir ${INSTALL_DIR} +login anonymous +app_update ${APPID} ${VALIDATE} +quit
WORKDIR ${INSTALL_DIR}

# Game Port (Inbound UDP; in the .bat command line argument this is represented as “-Port=”)
EXPOSE 7777/udp

# Steam Client Port 7778/udp (Outbound UDP; this is always the Game Port +1), no need to expose this as it is outbound

# Steam Query Port (Inbound UDP; in the .bat command line argument this is represented as “-QueryPort=”)
EXPOSE 27005/udp
# RCON Port (Inbound TCP; the “ListenPort” in Game.ini
EXPOSE 7779/tcp

COPY HarshDoorstopServer.sh .
# Make ini file read open to reading and writing from any user


ENTRYPOINT ["./HarshDoorstopServer.sh"]
