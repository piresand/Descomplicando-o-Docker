## Dia 02 

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

