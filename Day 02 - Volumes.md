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
    //Pasta com o volume criado, criar arquivo GIROPOPS e STRIGUS com touch
        ---- Adicionando o volume ao Container -----
        docker container run -ti --mount type=volume,src=giropops,dst=/giropops debian
    // usando o volume giropos no destino /giropops com a imagem debian
  
### Volumes - Data-Only e Prune
    docker volume prune // apaga todos os volumes que não esteja sendo usado por pelo menos um container - cuidado
    docker container prune // remove todos os container que estiver parado
    docker image prune // remove as imagens que estão quebradas (dump)

    -------------------------------Criando Volume Data-Only-------------------
    //docker container create -v /opt/giropops/:/data --name dbdados centos // sintaxe antiga
    docker container create -v /data --name dbdados centos // Evitar problemas de direito no container postgresql
    
    -------------------Montado um postgres-------------------
    docker container run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamiu/postgresql
    docker container ls
    docker container run -d -p 5433:5432 --name pgsql2 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamiu/postgresql
    docker logs -f [CONTAINER] // Verificar logs do container
    cd /var/lib/docker/volumes/  // Aqui estará todos os volumes, use o docker inspect para descobrir a subpasta do container _data

### Volumes - Resumo de comandos   

    docker container run -ti --mount type=bind,src=/volume,dst=/volume ubuntu    
    docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume ubuntu    
    docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume,ro ubuntu     
    docker volume create giropops    
    docker volume rm giropops      
    docker volume inspect giropops    
    docker volume prune     
    docker container run -d --mount type=volume,source=giropops,destination=/var/opa  nginx    
    docker container create -v /data --name dbdados centos    
    docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql    
    docker run -d -p 5433:5432 --name pgsql2 --volumes-from dbdados -e  POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql     
    docker run -ti --volumes-from dbdados -v $(pwd):/backup debian tar -cvf /backup/backup.tar /data     
