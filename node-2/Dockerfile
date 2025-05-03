# Instrucciones: 
#     Usa como imagen Ubuntu en su version mas reciente
#     Tendrá preinstalado los mismos paquetes que "devops-tools"
#     nano, git, openssh y postgresql-client
#     Al igual que la imagen de devops-tools tendrá un usuario sin privilegios
#     Como lo vimos en sesiones anteriores el CMD principal del contenedor
#     será un interprete de bash (para poder interactuar con el contenedor desde
#     nuestra terminal)

FROM ubuntu:latest

RUN apt-get update && apt-get install -y \
    nano \              
    git \               
    openssh-server \    
    bash \              
    postgresql-client \ 
    && rm -rf /var/lib/apt/lists/*

RUN groupadd -r node2-user && \
    useradd -r -g node2-user -d /home/node2-user -s /bin/bash node2-user && \
    mkdir -p /home/node2-user/workspace && \
    chown -R node2-user:node2-user /home/node2-user


WORKDIR /home/node2-user/workspace
USER node2-user

CMD ["/bin/bash"]