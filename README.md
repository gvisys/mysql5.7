<div class="fs-5"><p class="text-black mb-2 text-break">To set up a Docker Compose environment with MySQL 5.7, you'll need to create a <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> file that defines the services required for your application, including MySQL. Below is a step-by-step guide on how to do this:</p></div>

**Passo 1: Instale o Docker e o Docker Compose** \
Certifique-se de ter o Docker e o Docker Compose instalados no seu sistema. Caso contrário, baixe e instale-os no site oficial do Docker.

• Docker: https://www.docker.com/products/docker-desktop \
• Docker Compose: https://docs.docker.com/compose/install/ \

**Passo 2: Crie um Diretório para o Seu Projeto** \
Crie um novo diretório para o seu projeto e navegue até ele no seu terminal ou prompt de comando.
```
mkdir my-mysql-project
cd my-mysql-project
```

**Passo 3: Crie um Arquivo de Composição Docker**  \
<div class="fs-5"><p class="text-black mb-2 text-break">In your project directory, create a file named <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code>. This file will define the services (MySQL) and any other components you might need for your application.</p></div>

<div class="fs-5"><p class="text-black mb-2 text-break">Open your favorite text editor and paste the following content into <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code>:</p></div>

```
version: '3.8'
services:
  db:
    image: mysql:5.7
    container_name: mysql_57_container
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: mydatabase
      MYSQL_USER: myuser
      MYSQL_PASSWORD: mypassword
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
```
Esta configuração faz o seguinte: \

• Usa a versão 3.8 do formato de arquivo Docker Compose. \
• Define um único serviço chamado db. \
• Specifies that we want to use the mysql:5.7 image from Docker Hub. \
• Define o nome do contêiner como mysql_57_container. \
• Configura o servidor MySQL com uma senha root (rootpassword), cria um banco de dados (mydatabase) e configura um usuário (myuser) com uma senha (mypassword). \
• Mapeia a porta 3306 dentro do contêiner para a porta 3306 na máquina host, permitindo acesso externo ao servidor MySQL. \
• Creates a volume named mysql_data to persist data across container restarts.

**Passo 4: Inicie Seus Serviços** \
<div class="fs-5"><p class="text-black mb-2 text-break">With your <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> file ready, start your services by running the following command in the same directory as your <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> file:</p></div> 

```
docker-compose up -d
```

<div class="fs-5"><p class="text-black mb-2 text-break">This command starts all the services defined in your <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> file in detached mode, meaning they run in the background.</p></div>

**Passo 5: Verifique Sua Configuração**  \
Para verificar se o seu contêiner MySQL está em execução, execute:

```
docker ps
```

<div class="fs-5"><p class="text-black mb-2 text-break">Look for your <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">mysql_57_container</code> in the list of running containers.</p></div>

**Passo 6: Conecte-se ao seu servidor MySQL**  \
Você pode se conectar ao seu servidor MySQL usando qualquer ferramenta de cliente MySQL. Por exemplo, se você estiver usando o cliente de linha de comando MySQL, poderá fazer login com:

```
mysql -h localhost -P 3306 -u myuser -p
```

<div class="fs-5"><p class="text-black mb-2 text-break">When prompted, enter the password you specified in your <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> file (<code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">mypassword</code>).</p></div>

É isso. Agora você tem uma configuração do Docker Compose com o MySQL 5.7 em execução.
