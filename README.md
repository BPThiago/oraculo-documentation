# DevLake - Guia de Instalação e Configuração

## Introdução
O **DevLake** é uma plataforma de engenharia de dados projetada para coletar, armazenar e analisar dados de desenvolvimento de software a partir de diversas ferramentas.

Este guia fornece instruções detalhadas para configurar e utilizar o DevLake em seu ambiente local.

## Requisitos
- Docker e Docker Compose instalados.
- Um **GitHub Access Token** (para integração com o GitHub).

## Instalação

1. Clone o repositório do DevLake:
   ```sh
   git clone https://github.com/leds-org/leds-dashboard.git
   cd leds-dashboard
   ```

2. Configure as variáveis no `docker-compose.yml` e `.env` conforme sua necessidade.

3. Gere o `ENCRYPTION_SECRET` utilizando o seguinte comando:
   ```sh
   openssl rand -base64 2000 | tr -dc 'A-Z' | fold -w 128 | head -n 1
   ```

4. Inicie o DevLake executando:
   ```sh
   docker-compose up -d
   ```
   Isso iniciará os contêineres necessários para rodar o ambiente DevLake.

5. Acesse o painel do DevLake em [`http://localhost:4000`](http://localhost:4000).
   - Utilize o **usuário** e **senha** configurados no `docker-compose.yml` para autenticar.

## Configuração e Integração

### Criando uma Conexão com o GitHub

1. No menu lateral, clique em **Connections**.
2. Selecione **GitHub** e clique em **Create a New Connection**.

   ![Manage Connections](./images/manage_connections.png)

3. Preencha os dados necessários e insira o **GitHub Access Token** para autenticação.

   ![Manage Connections Details](./images/manage_connections_details.png)

4. Teste a conexão clicando em **Test Connection**.
5. Clique em **Save Connection**. Após salvar, você será redirecionado para a tela de conexão:

   ![Connection Details](./images/connection_details.png)

6. Clique em **+ Add Data Scope**, selecione os repositórios desejados e clique em **Save**.

### Criando um Projeto

1. No menu lateral, clique em **Projects** e depois em **+ New Project**.
2. Dê um nome ao projeto e clique em **Save**.
3. Ao editar o projeto, na seção **Data Connection**, clique em **+ Add a Connection**.
4. Selecione a conexão criada anteriormente, escolha os repositórios desejados e clique em **Save**.
5. Ajuste a frequência de sincronização dos dados no menu **Sync Policy** dentro do projeto.

Agora seu ambiente DevLake está configurado e pronto para uso!

## Visualização de Dados com Grafana
O DevLake utiliza o **Grafana** para exibir os dados coletados.

1. Acesse o Grafana em [`http://localhost:4000/grafana`](http://localhost:4000/grafana).
2. Utilize as credenciais padrão **admin:admin** para autenticar (recomenda-se alterar a senha após o primeiro login).
3. Acesse a tela principal do Grafana.

   ![Grafana dashboards](./images/grafana_dashboards.png)

4. No menu lateral, clique em **Painéis de Controle** para visualizar os dashboards disponíveis.

   Exemplo de dashboard do GitHub:

   ![Dashboard GitHub](./images/dashboard_github.png)

## Conclusão
Seu ambiente DevLake está pronto para uso! Agora você pode explorar e analisar os dados coletados a partir das ferramentas integradas.

Se precisar de mais informações, consulte a [documentação oficial](https://devlake.apache.org/docs/GettingStarted).

