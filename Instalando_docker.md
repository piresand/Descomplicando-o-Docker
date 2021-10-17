## Docker Container Expert  

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