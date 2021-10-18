## Criando o container a partir do arquivo do dockerfile criado

<p align="center"><img src="https://user-images.githubusercontent.com/30474126/137650184-639badec-bd72-4929-8dd2-80573389bb6d.png" /></p>

    docker image build -t toskeira:1.0     
    docker image ls      
    docker container run -d toskeira:1.0      
    docker container logs -f [CONTAINER ID]      

### Criando a pasta para Dockerfile   

    mkdir /opt/tosko_dockerfile    
    cd /opt/tosko_dockerfile    
    vim Dockerfile    

### No Dockerfile:    
 
    FROM debian     
    LABEL app="Giropops"    
    ENV ANDRE="LINDO"    
    RUN apt-get update && apt-get install -y stress && apt-get clean     

    CMD stress --cpu 1 --vm-bytes 64M --vm1    

### Criando a imagem toskeira versão 1.0   

    docker image build -t toskeira:1.0 .

### Na pasta /opt/tosko_dockerfile    

Obs: Run → Executa no momento da build. CMD → Executa no momento da instanciação do container.

<p align="center"><img src="https://user-images.githubusercontent.com/30474126/137652637-1a71e33a-3f52-40ce-9dad-8141ace87d80.png" /></p>

    docker container logs -f [ID_Container]   
    docker container stats [ID_Container]   

### Volumes - Tipo Bind (montando pasta como volume no container)   

    mkdir /opt/giropops     
    docker container run -ti --mount type=bind,src=/opt/giropops,dst=/giropops debian    
    docker container run -ti --mount type=bind,src=/opt/giropops,dst=/giropops,ro debian //somente leitura    

### Volumes - Tipo Volume   

    docker volume ls 
    docker create giropops 
    docker inspect giropops

//Olhar o Mointpoint no resultado do inspect    

    cd /var/lib/docker/volumes/giropops/_data/   

//Pasta com o volume criado, criar arquivo           

    GIROPOPS e STRIGUS com touch    
    
---- Adicionando o volume ao Container     

    docker container run -ti --mount type=volume,src=giropops,dst=/giropops debian     

// usando o volume giropos no destino /giropops com a imagem debian

