# Dashboards do Grafana para DevLake

Esta pasta contém dashboards do Grafana utilizados para a exibição dos dados coletados no [Apache DevLake](https://devlake.apache.org/). Esses dashboards fornecem insights essenciais sobre os projetos e ajudam na identificação de problemas e oportunidades de melhoria.

## Estrutura do Repositório

Os arquivos JSON contidos nesta pasta correspondem a dashboards pré-configurados do Grafana. Esses dashboards podem ser importados diretamente no Grafana para exibir visualizações dinâmicas dos dados do DevLake.

### Descrição dos Dashboards

- **Dashboard de Erros**: Apresenta erros encontrados no preenchimento de issues dentro do GitHub, como por exemplo: issues sem tipo, sem descrição ou sem assignees. Este painel ajuda a garantir que as issues sejam criadas corretamente, melhorando a qualidade dos dados.

- **SonarQube**: Exibe dados coletados do [SonarQube](https://www.sonarqube.org/), uma ferramenta de análise de qualidade de código que detecta vulnerabilidades, bugs e problemas de manutenção no código-fonte dos projetos.

- **Throughput**: Exibe o throughput de issues dentro dos projetos do GitHub sob diferentes perspectivas para análise. O throughput é uma métrica essencial pois mede a quantidade de trabalho concluído dentro de um período, ajudando a avaliar a produtividade da equipe e identificar gargalos no processo de desenvolvimento.

## Como Importar os Dashboards

Para importar os dashboards no Grafana, siga os passos abaixo:

1. Acesse o Grafana no seu navegador. O link padrão é `http://localhost:4000/grafana`.
2. Realize login com suas credenciais.
3. No menu lateral, clique em **Painéis de Controle** > **Novo** > **Importar**.
4. Selecione o arquivo `.json` do dashboard desejado.
5. Preencha as informações necessárias, como a fonte de dados.
6. Clique em **Import** para concluir a importação.

Agora seu dashboard está disponível para uso no seu ambiente Grafana.

## Personalização

Você pode editar os dashboards diretamente no Grafana para atender melhor às necessidades do seu projeto. Modifique os painéis, ajuste as fontes de dados e crie novas visualizações conforme necessário.

