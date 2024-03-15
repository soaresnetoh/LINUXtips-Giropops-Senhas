## Tarefa Day2
- Criar o Dockerfile para subir o projeto (giropops-senhas)[https://github.com/badtuxx/giropops-senhas] e tambem usar o banco redis em container.

### Sequencia de passos
- Criar 
    - uma rede para ser usada na criação do container tanto para o app quanto para o redis
    ```bash
    docker network create linuxtips
    ```
    - Dockerfile com python para subir a aplicação
    ```bash
    docker build -t hernanisoares/linuxtips-giropops-senhas:1.0 .
    ```
    - subir o redis
    ```bash
    docker run --name redis --network linuxtips -d redis
    ```
    - subir o app
    ```bash
    docker container run -itd --network linuxtips -p 5000:5000 --name giropops-senhas hernanisoares/linuxtips-giropops-senhas:1.0
    ```
- subir para o github o projeto e para o dockerhub a imagem
    - Projeto para o github: Clone o repositorio (giropops-senhas do badtuxx)[https://github.com/badtuxx/giropops-senhas]
    - crie e clone um repositorio em seu github chamado (LINUXtips-Giropops-Senhas)[https://github.com/soaresnetoh/LINUXtips-Giropops-Senhas]
    - acesse o repositorio LINUXtips-Giropops-Senhas e mova o o diretorio giropops-senhas para seu diretorio e dentro do diretorio giropops-senhas que foi copiado, apague o .git
    ```bash
    git clone https://github.com/soaresnetoh/LINUXtips-Giropops-Senhas
    cd LINUXtips-Giropops-Senhas
    mv ../giropops-senhas .
    rm -Rf giropops-senhas/.git
    git add .
    git commit -am "add giropops-senhas and Dockerfile created"
    git push origin main
    ```
    - Imagem para o dockerhub
    ```bash
    docker login
    docker push hernanisoares/linuxtips-giropops-senhas:1.0
    ```


