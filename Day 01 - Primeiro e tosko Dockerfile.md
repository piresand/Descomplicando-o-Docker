## Dia 01


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

### Verificar o uso de recursos CPU, Memória, IO Rede e Disco (Blocks) no docker 

### Configurando CPU e memória para os meus containers  

        docker container stats nginx    

### Usar aplicativo para testar carga do containeir   

        apt-get install stress
        stress --help
        stress --vm 1 --cpu 1 --vm-bytes 64Mdock

### Verificar os processos em execução nos container   

        docker container top nginx   

### Criando container com definição de memória    

        docker container run -d -m 128M nginx    

### Usando uma calculadora em modo texto  

        bc   

### Criando container com definição de memória e cpu (0.5 = 50% de uma CPU)   

        docker container run -d -m 128M --cpus 0.5 nginx    
        cat /proc/cpuinfo    

### Configurar cpus do container   

        docker container update --cpus 0.2 nginx  
        docker container update --cpus 0.2 --memory 65M nginx   

### Resumo dos comandos:   

        docker container stats [CONTAINER ID]      
        docker container top [CONTAINER ID]    
        docker container run -d -m 128M --cpus 0.5 nginx     
        docker container update --memory 64M --cpus 0.4 nginx     
        docker container inspect[CONTAINER ID]     
        docker container stats [CONTAINER ID]    
        docker container top [CONTAINER ID]    

### Comando executados dentro do container:

        apt-get update    
        apt-get install stress    
        stress --cpu 1 --vm-bytes 128M --vm1    

### Criando o container a partir do arquivo do dockerfile criado

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

