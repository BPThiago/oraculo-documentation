# Oráculo

## Introduction

Este projeto almeja desenvolver uma plataforma de chatbot para responder perguntas sobre o estado das tarefas de um time de desenvolvimento.

Para este fim, planejamos integrar ferramentas como repositório do Github, JIRA... e utilizando uma IA para fazer queries SQL e retornar a resposta certa.

## Ferramentas

### DevLake

**DevLake** é uma plataforma de engenharia de dados projetada para coletar, armazenar e analisar dados de desenvolvimento de software de diversas ferramentas.

Acessível em: [localhost:4000](localhost:5678)

### MySQL

Sistema de gerenciamento de banco de dados (SGBD) de código aberto, que permite armazenar e gerir dados estruturados.

Utilizado para armazenar os dados do **DevLake**.

### Grafana

Ferramenta de análise e visualização de dados de código aberto.

Utilizado para visualizar os dados no **MySQL** populado pelo **DevLake**.

Acessível em: [localhost:4000/grafana](localhost:5678)

### N8N

[N8N](https://github.com/n8n-io/n8n) é uma plataforma de automação de fluxo de trabalho de código aberto que oferece às equipes técnicas a flexibilidade do código com a velocidade do no-code.

Neste repositório, usaremos essa plataforma para integrar diferentes sistemas de monitoramento do fluxo de trabalho da equipe.

Acessível em: [localhost:5678](localhost:5678)

## Requerimentos

- Docker e Docker Compose instalados 
- A **GitHub Access Token**, Token de acesso do Github para integração do mesmo.

## Instalação

1. Clone o repositório do DevLake:

   ```sh
   git clone https://github.com/bedrohenr/oraculo.git
   cd oraculo
   ```

2. Configure as variáveis necessárias nos arquivos `docker-compose.yml` e `.env`.

3. Gere o `ENCRYPTION_SECRET` executando o comando a seguir: 

   ```sh
   openssl rand -base64 2000 | tr -dc 'A-Z' | fold -w 128 | head -n 1
   ```

4. Inicie o projeto rodando o comando:

   ```sh
   docker-compose up -d
   ```

   Isso iniciará todos os contêineres (DevLake, ConfigUI, Nginx, MySQL, Grafana) necessários para executar o ambiente DevLake e o N8n, que será usado para integrar a IA para pesquisar no banco de dados MySQL.

5. Acesse o Dashboard DevLake em [`http://localhost:4000`](http://localhost:4000).  
   - Use o **username** e **password** configurados préviamente no arquivo  `docker-compose.yml` para prosseguir.

## Credenciais
   - Devlake:
      - **Username**: devlake
      - **Password**: 123
   - MySQL
      - **Database**: lake
      - **Username**: merico
      - **Password**: 123
   - Grafana
      - **Username**: admin
      - **Password**: admin

## Configuração e Integração

### Criando uma conexão GitHub

1. No menu lateral, clique em **Conections**. 
2. Selecione **GitHub** e clique em **Create a New Connection**.

   ![Manage Connections](./images/manage_connections.png)

3. Preencha as informações necessárias e insira o **GitHub Access Token** para autenticação.

   ![Manage Connections Details](./images/manage_connections_details.png)

4. Teste a conexão clicando em **Test Connection**.  
5. Clique em **Save Connection**. Após salvar, você será redirecionado para a tlea de conexões:

   ![Connection Details](./images/connection_details.png)

6. Clique em **+ Add Data Scope**, selecione o repositório desejado, e clique em  **Save**.

### Criando um projeto

1. No menu lateral, clique em **Projects** e logo após em **+ New Project**.  
2. Insira o nome do projeto e clique em **Save**.  
3. Quando estiver editando o projeto, na seção **Data Connection**, clique em **+ Add a Connection**.  
4. Selecione a conexão previamente criada, escolha o repositório desejado e clique em **Save**.  
5. Ajuste a frequência de sincronização dos dados no menu **Sync Policy**, dentro do projeto.

Seu ambiente DevLake agora está configurado e pronto para uso!

## Visualização de dados com Grafana

DevLake usa o **Grafana** para mostrar os dados coletados.

1. Accesse o Grafana em [`http://localhost:4000/grafana`](http://localhost:4000/grafana).  
2. Use as credenciais padrão **admin:admin** para logar (É recomenddado trocar a senha após o primeiro login).  
3. Accesse o dashboard principal do Grafana:

   ![Grafana dashboards](./images/grafana_dashboards.png)

4. No menu lateral, clique em **Dashboards** para visualizar os dashboards disponíveis.

   Example of a GitHub dashboard:

   ![Dashboard GitHub](./images/dashboard_github.png)

### Funcionamento

Por agora, ainda em desenvolvimento, o DevLake é usado para popular a database (MySQL) vinculando o repositório escolhido (estamos utilizando o Github).

Assim podendo tentar fazer com que o n8n, junto de um AI Agent, consiga fazer queries na database com os issues e commits.

#### Supersimplificação do fluxo de execução:

   ![Fluxo de execução](./images/executional_flow_visualization.png)


Desta forma, podemos conectar o n8n ao MySQL e fazer com que a AI Agent possa lidar com os dados. 

#### Exemplo de um rag do n8n:

   ![N8N example](./images/n8n_example.png)

Esta configuração nos proporciona a capacidade de fazer perguntas como esta:

   ![N8N chat example](./images/n8n_chat_example.png)

# Conclusão

Longe da conclusão do projeto
