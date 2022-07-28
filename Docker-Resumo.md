# Docker 

### Links 

[Docker - Site oficial](https://www.docker.com/)    
[Docker HUB](https://hub.docker.com/)  
[Docker Documentação - Oficial](https://docs.docker.com/)  
[Download](https://docs.docker.com/get-docker/)  
#
- Isolar Aplicações 
- independência
- Sistema de arquivos isolados
- Reutilização de camadas de imagens 
- Agilidade 
- Portabildiade
- Redução de problemas com SO 

![Docker](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltb6200bc085503718/5e1f209a63d1b6503160c6d5/containers-vs-virtual-machines.jpg "container docker")


# 
## Comandos 
[Documentação Oficial](https://docs.docker.com/)

Parar container:  
    
    docker stop ID_CONTAINER

Iniciar Container:   
    
    docker start ID_CONTAINER

Pausar Container:  
    
    docker pause ID_CONTAINER

Voltar funcionamento de Container:
    
    docker unpause ID_CONTAINER

Monstrar portas Container:  

    docker port ID_CONTAINER 

Parar todos os containers

    docker stop $(docker container ls -q)
#
## Rodar Container
    docker run IMAGEM

- Criar e executar containers

 Procura Localmente a Imagem -> Baixa se não existir -> Validade hash da imagem -> Executa o Container

- Mapear Porta do Container  
`` -p HOST_PORT:CONTAINER_PORT`` 
### Apresentar container em execução

    docker ps  ou  docker container ls

Obs: para visualizar todos os container ``docker ps -a `` 

#
## Executar container

    docker exec -it ID bash

``it ``  para usar terminal de forma interativa

``-d `` sem travar terminal/roda e volta ao normal

#
### Remover Container  

    docker container rm ID_CONTAINER 

OBS:  
pode ser usada floag `` -force `` 

#
### Criação de portas de redes
- Namespace NET -> Isolamento das interfaces de rede
- Porta Container não é a mesma que o host



#
### Criar Rede

        Docker network create --driver TIPO_REDE NOME_REDE

Docker possui 3 redes padróes 
- Bridge 
    - Cria a 'ponte' entre Containers
- Host 
- None
    - Remove a possibilidade de conexão entre containers

Rede  do tipo Bridge é utilizada para Comunicação entre os Containers

OBS: Para conectar dois containers é necessário adicionar a mesma rede 
#
##  Imagens 

Imagem possuem somente camadas de leitura / quando container é gerado criar camada de escrita e leitura 

- Visualizar imagens

        docker images

-  Visualizar informações de imagens

         docker inspect ID

-  Visualizar camadas da imagem

         docker history ID


## Criação de Imagem 

![Docker Image](https://miro.medium.com/max/1400/0*CP98BIIBgMG2K3u5.png)

1- Criar arquivo Dockerfile   
``` DockerFile 
FROM node:VERSÃO   
WORKDIR /app-node   
ARG PORT_BUILD = 6000   
ENV PORT  = $PORT_BUID     
EXPOSE $PORT_BUILD
COPY . .  
RUN npm install  
ENTRYPOINT npm start
```
- ``FROM``  / Definir uma imagem de base  
- ``WORKDIR`` / Definir diretório de trabalho
- ``CMD``  / Comandos executatados após a criação do Container e também pode ser usado para definir os argumentos
- ``ENTRYPOINT `` / Definir onde e como será executada imagem
- ``RUN`` / Executar uma linha de Comando
- ``EXPOSE `` / Expoe a porta de funcionamento
- ``ENV`` / Variáveis de Ambiente 
- ``COPY `` / Copia arquivos do HOST para o CONTAINER 

2 - Fazer build da imagem
```
Docker build -t NOMECONTA/NOMEAPLICAÇÃO:VERSÃO .
```


# 
## Persistência de dados


![Dados](https://speedmedia.jfrog.com/08612fe1-9391-4cf3-ac1a-6dd49c36b276/https://media.jfrog.com/wp-content/uploads/2019/05/20130837/image1-1-1024x500.png/mxw_1080,f_auto "dados")

`` Usar label -v não é recomendado ``   

Utilizar `` --mount type="TIPO_ARMAZENAMENTO, SOURCE="DIRETORIO_HOST(SE FOR BIND MOUNT)",TARGET="DIRETORIO_CONTAINER"`` 

### Volumes:
- Não dependem da estrutura de pastas do sistema
- São gerenciados pelo Docker 

    ```
    -v LOCAL_DESEJADO / TESTE

    docker volume create NOME_VOLUME

    docker run -it -v NOME_VOLUME:/DIRETORIO_CONTAINER (ex:/app)  ubuntu bash
    
    ```

### Bind Mount:  
- Depende da estrutura de pastas do sistema
- Não é um volume
- tipo de armazenamento

    ```
  docker run  type = bind,source="LOCAL_DESEJADO" NOME_IMAGEM  bash
    ```
  ou 
  ```
   docker container run -it -v ARMAZENAMENTO_HOST:ARMAZENAMENTO_CONTAINER NOME_IMAGEM 
  ```

### tmpfs
- Armazenamento Temporário
- Memória RAM
```
docker container run -it --tmpfs /PASTA
```

#
## Docker Compose 
- Ajuda a montar aplicações 
- Iniciar Containerss

![Docker Compose](https://www.biaudelle.fr/wp-content/uploads/2021/07/docker-compose-archi.png)

ARQUIVO : docker-compose.yml

``` yml
version /
services:
    SERVICO1:
        image:
        container_name:
        network:
    SERVICO2:
        image:
        container_name:
        network:
            - NOME_REDE
    ports:
        - PORTA/PORTA
networks:
    compose-brigde:
        driver: NOME_REDE
```

### Rodar Aplicação 
- docker-compse up 

### Depends_on
- Definir serviços dependentes

### Visualizar Composes
```
Docker-composer ps
```
### Remover Compose 
```
docker-compose down 
```
#

## Docker Multi-Stage Build 

- Construção de Multiplos estágios
- Otimização
- Geração de Imagens a partir de varias etapas
- Retirar arquivos e procedimentos desnecessários
- Imagens geradas a partir de outras

![Multi-Stage Build](https://programmerlib.com/wp-content/uploads/2020/12/docker-multi-stage-build-754x445.png "Multi-Stage Build")

[Documentação Multi-Stage Build - Docker](https://docs.docker.com/develop/develop-images/multistage-build/)

# 
## Cluster

- Conjunto de máquinas dividindo poder computacional

```
docker-machine shh NOME_MAQUINA_VIRUTAL
```
```
docker swarm init
```

Cria Serviços em espopo do swarm
```
docker service create-p8000/3000  NOME_PROJETO
```

Visualizar onde tarefa está sendo executado   
Tarefa = `` instância  de um servico`` 
```
docker ps ID_TAREFA  ID_SERVIÇO
```


## Docker Swarm
- Orquestadror
- Alocar e reinciar containers de maneira automatica

 ## Virtual Box
 - Criação de Máquinas Virtais
```
docker-machine craeate -d virutalbox NOME_VIRUTAL_MACHINE
```