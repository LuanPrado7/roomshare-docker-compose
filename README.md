<h1 align="center"> RoomShare App </h1> 
<a href="https://opensource.org/licenses/MIT" rel="ugc">
  <img src="https://img.shields.io/github/license/aagarwal1012/animated-text-kit?color=red" alt="License: MIT">
</a>
<br>
<p align="center">
  <a href="https://github.com/LuanPrado7/roomshare-docker-compose">
    <img alt="RoomShare" title="RoomShare" src="https://i.imgur.com/fpKX2dS.png" width="450">
  </a>
</p>

A RoomShare é uma aplicação Web em Next.Js, com microsserviços em .Net Core, de gerenciamento de aluguel de salas comerciais.

## Contruído com

- [Next.js](https://nextjs.org/)
- [.Net Core](https://dotnet.microsoft.com/en-us/)
- [Kafka](https://kafka.apache.org/) 
- [MongoDB](https://www.mongodb.com/)
- [MySQL](https://www.mysql.com/)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Arquitutera da aplicação

<p align="center">
  <a>
    <img alt="Arquitutera" title="Arquitutera" src="https://i.imgur.com/b5JAuNi.png" width="1000">
  </a>
</p>

## Front-end

<p align="center">
  <a>
    <img alt="FrontEnd" title="FrontEnd" src="https://i.imgur.com/H1ds4n9.png" width="1000">
  </a>
</p>

Repositório GitHub: https://github.com/LuanPrado7/roomshare-front-end

## Microsserviços

- Autenticação (roomshare-room-service-auth):
  <br><br>Descrição: Permite criar, alterar e deletar usuários, e gerar o Token de autorização que precisa ser passado para os outros serviços.
  <br>Imagem Docker Hub: https://hub.docker.com/repository/docker/luanprado7/roomshare_auth_api/general
  <br>Repositório GitHub: https://github.com/Gouget/auth-api
  
- Room Command (roomshare-room-service-command): 
  <br><br>Descrição: Permite cadastrar, alterar e deletar salas comerciais, utilizando o banco de dados MySQL. Essas alterações produzem mensagens que são adicionadas a uma fila do Kafka.
  <br>Imagem Docker Hub: https://hub.docker.com/repository/docker/luanprado7/roomshare_room_service_command/general
  <br>Repositório GitHub: https://github.com/LuanPrado7/roomshare-room-service-command
  
- Room Query (roomshare-room-service-query): 
  <br><br>Descrição: Permite buscar uma lista de salas cadastradas ou apenas uma sala cadastrada, utilizando o banco de dados MongoDB.
  <br>Imagem Docker Hub: https://hub.docker.com/repository/docker/luanprado7/roomshare_room_service_query/general
  <br>Repositório GitHub: https://github.com/LuanPrado7/roomshare-room-service-query

- Room Consumer (roomshare-room-service-consumer):
  <br><br>Descrição: Consome as mensagens da fila do Kafka e registra no MongoDB através de um End-point do serviço Room Query.
  <br>Imagem Docker Hub: https://hub.docker.com/repository/docker/luanprado7/roomshare_room_service_consumer/general
  <br>Repositório GitHub: https://github.com/LuanPrado7/roomshare-room-service-consumer

 ## Pré-requisitos
 - É preciso ter o Docker e o Docker Compose instalados na máquina para rodar os microsserviços, e o NPM para rodar o Front-End.

 ## Como rodar o projeto localmente
 - Front-end
 <br>Ao clonar o projeto do [Front-End](https://github.com/LuanPrado7/roomshare-front-end), basta entrar na pasta do projeto e executar na linha de comando:
 ```shell
 npm i
 npm run dev
 ```

 - Serviços
 <br>Ao clonar este projeto, basta entrar na pasta do projeto e executar na linha de comando:
 ```shell
 docker-compose up -d
 ```

## Contribuidores
- Luan Prado
- Lucas Marinho
- César Pimenta
- Guilherme Ferrace
