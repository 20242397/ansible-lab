# Práctica 2do Parcial - Ansible + Docker

## Objetivo

Crear un laboratorio con dos servidores Linux (Ubuntu 24.04) utilizando Docker, y administrarlos de forma automatizada con Ansible mediante conexión directa a contenedores (`ansible_connection=docker`), sin necesidad de SSH.

## Requisitos previos

- Docker y Docker Compose instalados
- Ansible instalado (en este caso, vía WSL2 en Windows)

## Comandos para iniciar los contenedores

\`\`\`bash
docker compose up -d
docker ps
\`\`\`

Instalar Python en cada contenedor (requerido por Ansible):

\`\`\`bash
docker exec -it server1 bash -c "apt update && apt install -y python3"
docker exec -it server2 bash -c "apt update && apt install -y python3"
\`\`\`

## Comando para verificar la conexión

\`\`\`bash
ansible docker -i inventory.ini -m ping
\`\`\`

## Comando para ejecutar el playbook

\`\`\`bash
ansible-playbook -i inventory.ini playbook.yml
\`\`\`

## Tareas automatizadas por el playbook

1. Mostrar el nombre del host
2. Mostrar el sistema operativo
3. Crear el directorio `/tmp/ansible-demo`
4. Crear el archivo `info.txt` con el nombre del servidor y el SO
5. Crear los directorios `logs`, `backup` y `config` mediante un loop
6. Mostrar un mensaje condicional únicamente cuando el sistema operativo es Ubuntu

## Captura de la ejecución exitosa

![Ejecución del playbook](screenshot.png)
