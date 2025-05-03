# Instrucciones:
#     El segundo servicio:
#         Se llama: node-1
#         Usa como imagen debian en su version mas reciente
#         Tendrá preinstalado los mismos paquetes que "devops-tools"
#         nano, git y openssh
#         Al igual que la imagen de devops-tools tendrá un usuario sin privilegios
#         Como lo vimos en sesiones anteriores el CMD principal del contenedor
#         será un interprete de bash (para poder interactuar con el contenedor desde
#         nuestra terminal)

FROM debian:latest


RUN apt-get update && apt-get install -y \
    nano \
    git \
    openssh-server \
    bash \
    && rm -rf /var/lib/apt/lists/*


RUN groupadd -r node-user && \
    useradd -r -g node-user -d /home/node-user -s /bin/bash node-user && \
    mkdir -p /home/node-user/workspace && \
    chown -R node-user:node-user /home/node-user


WORKDIR /home/node-user/workspace
USER node-user


CMD ["/bin/bash"]