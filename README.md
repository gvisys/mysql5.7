<div class="fs-5"><p class="text-black mb-2 text-break">Para configurar um ambiente Docker Compose com o MySQL 5.7, você precisará criar um <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> Arquivo que define os serviços necessários para o seu aplicativo, incluindo o MySQL. Abaixo está um guia passo a passo sobre como fazer isso:</p></div>

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
<div class="fs-5"><p class="text-black mb-2 text-break">No diretório do seu projeto, crie um arquivo chamado <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code>. Este arquivo definirá os serviços (MySQL) e quaisquer outros componentes que você possa precisar para o seu aplicativo.</p></div>

<div class="fs-5"><p class="text-black mb-2 text-break">Abra seu editor de texto favorito e cole o seguinte conteúdo em <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code>:</p></div>

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

<li>Usa a versão 3.8 do formato de arquivo Docker Compose.</li> 
<li>Define um único serviço chamado db.</li>
<li>Specifies that we want to use the mysql:5.7 image from Docker Hub.</li>
<li>Define o nome do contêiner como mysql_57_container.</li>
<li>Configura o servidor MySQL com uma senha root (rootpassword), cria um banco de dados (mydatabase) e configura um usuário (myuser) com uma senha (mypassword).</li>
<li> Mapeia a porta 3306 dentro do contêiner para a porta 3306 na máquina host, permitindo acesso externo ao servidor MySQL.</li>
<li>Cria um volume chamado <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">mysql_data</code> Para persistir dados em todas as reinicializações do contêiner.</li>
<p></p> 

**Passo 4: Inicie Seus Serviços** 
<div class="fs-5"><p class="text-black mb-2 text-break">Com o seu <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> Arquivo pronto, inicie seus serviços executando o seguinte comando no mesmo diretório que o seu <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> Arquivo:</p></div> 

```
docker-compose up -d
```

<div class="fs-5"><p class="text-black mb-2 text-break">Este comando inicia todos os serviços definidos no seu <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> Arquivo no modo separado, o que significa que eles são executados em segundo plano.</p></div>

**Passo 5: Verifique Sua Configuração**  \

Para verificar se o seu contêiner MySQL está em execução, execute:

```
docker ps
```

<div class="fs-5"><p class="text-black mb-2 text-break">Procure pelo seu <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">mysql_57_container</code> Na lista de contêineres em execução.</p></div>

**Passo 6: Conecte-se ao seu servidor MySQL**  \

Você pode se conectar ao seu servidor MySQL usando qualquer ferramenta de cliente MySQL. Por exemplo, se você estiver usando o cliente de linha de comando MySQL, poderá fazer login com:

```
mysql -h localhost -P 3306 -u myuser -p
```

<div class="fs-5"><p class="text-black mb-2 text-break">Quando solicitado, digite a senha que você especificou no seu <code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">docker-compose.yml</code> Arquivo (<code style="background-color: rgb(40, 42, 54); padding: 3px; border-radius: 8px; color: white; cursor: pointer;">mypassword</code>).</p></div>

É isso. Agora você tem uma configuração do Docker Compose com o MySQL 5.7 em execução.
