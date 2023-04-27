# Manual de criação de container Docker para página web da empresa Help Soluções em TI

Esse manual tem como objetivo explicar de forma passo a passo como disponibilizar a página web da empresa Help Soluções em TI em um container Docker no Laboratório Elan.

## Pré-requisitos

### Antes de começarmos, você precisará ter:

1.	Acesso ao servidor web onde o código HTML da página web da empresa Help Soluções em TI está disponível.
2.	Uma conta no Laboratório Elan e acesso remoto.
3.	O Docker instalado em sua máquina local ou no servidor remoto.

## Passo 1: Preparar o ambiente Docker

Antes de iniciar o processo de criação do container, vamos preparar o ambiente Docker. Para isso, siga os seguintes passos:
1.	Conecte-se ao servidor remoto através do terminal com o comando:
__**ssh <SEU_USUARIO>@200.17.141.82 -p 3333**__
2.	Verifique se o Docker está instalado no servidor através do comando:
__**docker –version**__

3.	Caso o Docker por algum motivo inesperado não esteja instalado, você pode seguir as instruções de instalação na documentação oficial do Docker: https://docs.docker.com/get-docker/.

## Passo 2: Criação do container

Agora que o ambiente está configurado, vamos criar o container para a página web da empresa Help Soluções em TI. Para isso, siga os seguintes passos:
1.	Crie um arquivo chamado Dockerfile na pasta raiz do seu projeto com o seguinte conteúdo:
__**FROM nginx
COPY . /usr/share/nginx/html**__
2.	No terminal, navegue até a pasta raiz do seu projeto e execute o seguinte comando para criar a imagem do container:

__**docker build -t <NOME_DA_IMAGEM>**__

3.	Agora que a imagem do container foi criada, vamos criar o container a partir dessa imagem. Execute o seguinte comando:
__**docker run -d -p <PORTA_EXTERNA>:80 --name <NOME_DO_CONTAINER> <NOME_DA_IMAGEM>**__
Onde <PORTA_EXTERNA> é a porta que será utilizada para acessar a página web da empresa Help Soluções em TI através do navegador. Por exemplo, se você escolher a porta 8080, a página web estará disponível em http://localhost:8080.
O <NOME_DO_CONTAINER> é o nome que você deseja dar ao container para identificação.

O <NOME_DO_CONTAINER> é o nome que você deseja dar ao container para identificação.

## Passo 3: Disponibilização da página web no container

Com o container criado, agora você precisa disponibilizar o código HTML da página web da empresa Help Soluções em TI dentro do container. Para isso, siga os seguintes passos:
1.	Copie o código HTML da página web da empresa Help Soluções em TI para a pasta raiz do seu projeto.
2.	No terminal, navegue até a pasta raiz do seu projeto e execute o seguinte comando para acessar o shell do container:
__**docker exec -it <NOME_DO_CONTAINER> sh**__
3.	Agora que você está dentro do container, navegue até a pasta onde o código HTML será copiado. No caso da imagem do Nginx, a pasta é /usr/share/nginx/html. Execute o seguinte comando para copiar o código HTML para dentro do container:
__**cp <NOME_DO_ARQUIVO_HTML> /usr/share/nginx/html**__

## Passo 4: Manutenção do container

Após a criação do container, é importante mantê-lo atualizado e seguro. Para isso, siga as seguintes boas práticas:
1.	Mantenha o sistema operacional do servidor atualizado.
2.	Mantenha o Docker atualizado.
3.	Mantenha o código HTML da página web da empresa Help Soluções em TI atualizado.
4.	Faça backups do container regularmente.
5.	Monitore o container em busca de possíveis problemas de segurança e desempenho.
Com essas boas práticas em mente, você funcionário poderá manter o container da página web da empresa Help Soluções em TI seguro e atualizado.



