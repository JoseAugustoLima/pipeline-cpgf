# Pipeline de Dados para Análise dos Gastos do Cartão de Pagamento do Governo Federal (CPGF)

Este projeto cria uma pipeline de dados para obtenção de dados públicos sobre os gastos do cartão de pagamento do governo federal do Brasil, incluindo transformação, limpeza e apresentação dos dados referente ao ano de 2024.

## Visão Geral

Os dados brutos foram obtidos através do Portal da Transparência da Controladoria Geral da União (https://portaldatransparencia.gov.br/download-de-dados/cpgf) e todo o processo de ETL (Extração, Transformação, Carregamento) e visualização foi realizado utilizando a stack de soluções do Google Cloud.

## Principais Componentes

*   **Cloud Storage:** usado para armazenar os dados brutos no formato .CSV 
*   **Google Cloud DataFusion:** serviço principal para criação e deploy do pipeline
*   **Google Dataproc:** serviço gerenciado para execução do Apache Hadoop
*   **BigQuery:** usado análise e armazenamento de dados transformados
*   **Looker Studio:** usado para visualização e apresentação dos dados.

## Configuração

2.  **Crie um projeto no Google Cloud:** [Se você ainda não tiver um projeto, crie um.]
3.  **Habilite as APIs necessárias:** Certifique-se de que as APIs do DataFusion, Cloud Storage e BigQuery estejam habilitadas no seu projeto.
4.  **Crie uma instância do DataFusion:** Use o console do Google Cloud ou a ferramenta `gcloud` para criar uma instância do DataFusion.
5.  **Configure as credenciais:** Configure as credenciais para que o DataFusion possa acessar outros serviços do Google Cloud.

## Implantação

[Descreva como implantar e executar seu projeto. Isso pode envolver:]

1.  **Importar o pipeline do DataFusion:** Importe o pipeline do DataFusion a partir do arquivo [nome do arquivo].
2.  **Configurar os parâmetros do pipeline:** Defina os parâmetros do pipeline, como os caminhos para os buckets do Cloud Storage, os nomes das tabelas do BigQuery, etc.
3.  **Executar o pipeline:** Execute o pipeline do DataFusion para processar os dados.

## Uso

[Explique como usar seu projeto. Inclua exemplos de como executar o pipeline, como visualizar os resultados, etc.]

## Monitoramento

[Descreva como monitorar a execução do seu projeto. Isso pode envolver:]

*   **Painéis do DataFusion:** Use os painéis do DataFusion para monitorar o desempenho do pipeline.
*   **Cloud Logging:** Use o Cloud Logging para visualizar os logs do DataFusion.
*   **Cloud Monitoring:** Use o Cloud Monitoring para criar alertas e painéis personalizados.

