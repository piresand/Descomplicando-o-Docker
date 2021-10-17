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