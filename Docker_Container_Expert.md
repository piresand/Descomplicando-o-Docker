## Docker Container Expert  

## Instalando Máquina Linux    

[Baixe maquina Ubuntu Linux](https://releases.ubuntu.com/20.04.3/ubuntu-20.04.3-desktop-amd64.iso)   

        user: servidor   
        password: Senha@123  
 
[Documentação offical](docs.docker.com/install)   
 
## Instalando o Docker    

Comando baixa o script e direciona para a execução do bash     

        apt-get update   
        apt-get install curl   
        curl -fsSL https://get.docker.com | bash   
        docker version   
        docker container ls     

### Executando e administrando containers Docker   
Ver containers (comando versão antiga)   

        docker ps   

### Ver containers em execução (comando CLI novo)       
        docker container ls (em execução)   
        docker container ls -a (em execução e parado)     

### Criar a primeira imagem   
        
        docker container run -ti hello-world
        ou docker pull hello-world

### Conectar a um container em execução  
        
        docker container attack "nomedocontainer ou ID"   

### Verificar todos os container   
        
        docker container ls -a    

### Deixar o container nginx executando como um daemon   

        docker container run -d nginx   

### Acessando o processo nginx (primeiro plano)  

        docker container attach "id_do_container"   

### Ctrl+c - finaliza o processo    
Vamos então conectar no container de processo do nginx via shell (docker container exec -ti "id_do_container" comando)     

        docker container exec -ti nginx bash
        apt-get update
        curl localhost
        ctrl+D (porém o processo não vai morrer, pois o principal é o nginx e não o bash)   

### Comando para pausar decontacoterminado container    

        docker container pause [Container_ID]   
        docker container unpause [Container_ID]    

### Start, Stop, Restart, pause e unpause no container nginx   

        docker container start nginx   
        docker container stop nginx   
        docker container restart nginx   
        docker container pause nginx   
        docker container unpause nginx     

### Fazer inspeção no container (visualizar detalhes)   
        
        docker container inspect nginx    

### Verificar os logs do container, com o docker container attach nginx (processo) automaticamente ja vejo os logs do processo  

        docker container logs -f nginx    

### Remover um container, somente container em stop   

        docker container rm nginx  

### Forçar Remoção de um container  

       docker container rm -f nginx   

### Resumo dos comandos:   
    docker container start [CONTAINER ID]    
    docker container stop [CONTAINER ID]    
    docker container restart [CONTAINER ID]    
    docker container pause [CONTAINER ID]    
    docker container unpause [CONTAINER ID]    
    docker container inspect [CONTAINER ID]   
    docker container logs -f [CONTAINER ID]   
    docker container rm [CONTAINER ID]
    docker container attach [CONTAINER ID]   
    docker container rm -f [CONTAINER ID]    
    docker container exec -ti [CONTAINER ID] [COMANDO]      
    docker container run -d nginx    