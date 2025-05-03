# Instrucciones: 
#     El primer servicio: 
#         Se llama: devops-tools
#         Usa como imagen python 3.12 en su imagen mas reciente (no-slim)
#         Tendrá preinstalados los siguientes paquetes:
#         nano, git y openssh
#         La imagen tendrá un usuario sin privilegios de root el cual será
#         el principal usuario del contenedor.
#         Como lo vimos en sesiones anteriores el CMD principal del contenedor
#         será un interprete de bash (para poder interactuar con el contenedor desde
#         nuestra terminal)

FROM python:3.12

# Instalar paquetes requeridos
RUN apt-get update && apt-get install -y \
    nano \
    git \
    openssh-server \
    && rm -rf /var/lib/apt/lists/*

# Crear usuario sin privilegios
RUN groupadd -r devops-user && \
    useradd -r -g devops-user -d /home/devops-user -s /bin/bash devops-user && \
    mkdir -p /home/devops-user/workspace && \
    chown -R devops-user:devops-user /home/devops-user

# Configurar entorno
WORKDIR /home/devops-user/workspace
USER devops-user

# Iniciar bash al ejecutar el contenedor
CMD ["/bin/bash"]