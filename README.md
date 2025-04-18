# Pipeline de Dados para Análise dos Gastos do Cartão de Pagamento do Governo Federal (CPGF)

Este projeto cria uma pipeline de dados para análise de dados públicos sobre os gastos do cartão de pagamento do governo federal do Brasil, incluindo transformação, limpeza e apresentação dos dados referente ao ano de 2024.

## Visão Geral

Os dados brutos foram obtidos através do Portal da Transparência da Controladoria Geral da União (https://portaldatransparencia.gov.br/download-de-dados/cpgf), sendo que o processo de ETL (Extração, Transformação, Carregamento) e visualização foi realizado utilizando a stack de soluções do Google Cloud, através de um processo em lote (batch).

## Principais Componentes

*   **Cloud Storage:** usado para armazenar os dados brutos no formato .CSV 
*   **Cloud Data Fusion:** serviço principal para criação e deploy do pipeline
*   **Dataproc:** serviço gerenciado para execução do Apache Hadoop
*   **BigQuery:** usado para análise e armazenamento de dados transformados
*   **Looker Studio:** usado para visualização e apresentação dos dados
*   **Cloud Monitoring:** usado para geração de alertas por SMS com status da pipeline.

## Pré-Requisitos

1.  **Uma conta no Google Cloud:** todo o processo pode ser realizado através de uma nova conta no GCP (gratuita com créditos de US$300).
2.  **Um projeto no Google Cloud:** no caso de ainda não existir um.
3.  **Habilitar as APIs necessárias:** certifique-se de que as APIs do Data Fusion, Cloud Storage e BigQuery estejam habilitadas no seu projeto.
4.  **Habilitar o Billing:** ainda que com uso de créditos, se faz necessário associar o projeto à um billing account.
5.  **Criar uma instância do Data Fusion:** use o console do Google Cloud ou a ferramenta `gcloud` para criar uma instância do DataFusion.
6.  **Configurar as credenciais:** configure as credenciais para que o Data Fusion possa acessar outros serviços do Google Cloud como Cloud Storage, Dataproc e BigQuery.

## Configuração

1.  **Criação do bucket e importação dos dados brutos:** após criar o bucket, importe os arquivos .CSV baixados diretamente do Portal da Transparência ou se preferir, a partir da pasta [dados_brutos](https://github.com/JoseAugustoLima/pipeline-cpgf/tree/main/dados_brutos).
2.  **Importação do pipeline do Data Fusion:** Importe o pipeline pré-configurado do DataFusion a partir do arquivo [pipeline-cpgf-cdap.json](https://github.com/JoseAugustoLima/pipeline-cpgf/blob/main/pipeline-cpgf-cdap.json).
        #### Atenção
        Atualizar o parâmetros "path" com o caminho do bucket de origem dos dados.

3.  **Importação do alerta de status:** Importe a configuração da geração de alertas a partir do arquivo [cloud-monitoring-job-status.json](https://github.com/JoseAugustoLima/pipeline-cpgf/blob/main/cloud-monitoring-job-status.json). 

## Execução

Após importação da configuração do pipeline no Data Fusion, clicar no botão "Run".

![](https://github.com/JoseAugustoLima/pipeline-cpgf/blob/main/datafusion-run-pipeline.png)

Neste momento, o Data Fusion irá realizar a leitura dos arquivos .CSV, limpeza dos dados, provisionar um cluster Hadoop temporário através do serviço Dataproc para execução das transformações necessárias, e por fim, escrever o resultado num dataset no BigQuery.

## Visualização

Para a visualização dos dados, o Looker Studio permite a criaçao de reports de acordo com diferentes critérios de consulta que podem ser criados no BigQuery.

Segue link com exemplo de report:
https://lookerstudio.google.com/reporting/e53372f4-8772-4ca4-83c5-4fce6143634e 

