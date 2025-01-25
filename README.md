# Explorar Pesquisa de IA do Azure

Objetivo: criar uma solução de mineração de conhecimento que facilita a pesquisa de insights sobre as experiências dos clientes.

Cenário: A Fourth Coffee, uma rede nacional de cafés, decidiu criar um índice de Pesquisa de IA do Azure usando os dados extraídos de revisões de clientes.

Etapas:
- Criar recursos do Azure
- Extrair dados de uma fonte de dados
- Enriquecer os dados com habilidades de IA
- Usar o indexador do Azure no portal do Azure
- Consultar o índice de pesquisa
- Examinar os resultados salvos em um Repositório de Conhecimento

## Criar recursos do Azure
### Recursos do Azure necessários
A solução proposta para a Fourth Coffee inclue os seguintes recursos na sua assinatura do Azure:
- Um recurso do da Pesquisa de IA do Azure, que gerenciará a indexação e a consulta
- Um recurso dos serviços de IA do Azure, que fornece serviços de IA para habilidades que a sua solução de pesquisa pode usar para enriquecer os dados na fonte de dados com insights gerados pela IA
- Uma Conta de armazenamento com contêineres de blob, que armazena documentos brutos e outras coleções de tabelas, objetos ou arquivos.

## Extrair dados de uma fonte de dados
### Carregar documentos no Armazenamento do Azure
1. Após a criação da Conta de armazenamento, selecione Contêineres no painel de menu à esquerda
![image](https://github.com/user-attachments/assets/9e67609c-1b85-4c8a-b02b-52588409291b)

2. Selecionar + Contêiner. Um painel no lado direito será exibido
3. Insira as seguintes configurações e clique em Criar:
    - Nome: coffee-reviews
    - Nível de acesso público: contêiner (acesso de leitura anônimo para contêineres e blobs)
    - Avançado: sem alterações
4. Em uma nova guia do navegador, faça o download das revisões de café compactadas de https://aka.ms/mslearn-coffee-reviews e extraia os arquivos para a pasta revisões
5. No portal do Azure, selecione o contêiner coffee-reviews. No contêiner, faça o Upload dos arquivos extraídos.

## Enriquecer os dados com habilidades de IA e Usar o indexador do Azure no portal do Azure
Depois de ter os documentos armazenados, use a Pesquisa de IA do Azure para extrair insights dos documentos. O portal do Azure fornece um assistente de importação de dados. 

1. No portal do Azure, selecione o recurso da Pesquisa de IA do Azure anteriormente criado
2. Na página Visão geral, selecione Importar dados
3. Na página Conectar-se aos seus dados, na lista Fonte de Dados, escolha Armazenamento de Blobs do Azure
4. Preencha os detalhes do armazenamento de dados com os seguintes valores:
    - Fonte de dados: Armazenamento de Blobs do Azure
    - Nome da fonte de dados: coffee-customer-data
    - Dados para extração: Conteúdo e metadados
    - Modo de análise: Padrão
    - Cadeia de conexão: *selecione Escolher uma conexão existente. Selecione sua conta de armazenamento, selecione o contêiner de coffee-reviews e clique em Selecionar
    - Autenticação da identidade gerenciada: Nenhuma
    - Nome do contêiner: essa configuração é preenchida automaticamente depois que você escolhe uma conexão existente
    - Pasta do blob: deixe essa opção em branco
    - Descrição: Avaliações da rede de cafés Fourth Coffee
    - Selecione Avançar: adicionar habilidades cognitivas (opcional).
5. Na seção Anexar Serviços de IA, selecione o recurso de serviços de IA do Azure e adicione os enriquecimentos.

## Consultar o índice de pesquisa
Use o Gerenciador de pesquisa para escrever e testar as consultas. O Gerenciador de pesquisa é uma ferramenta criada no portal do Azure que oferece uma maneira fácil de validar a qualidade de seu índice de pesquisa.

1. Na página Visão geral do serviço Pesquisa, selecione Gerenciador de pesquisa na parte superior da tela
2. Selecione o índice coffee-indexer que você criou
3. Abaixo do índice selecionado, altere a exibição para o modo de exibição JSON
4. No campo editor de consultas JSON, copie e cole:
  code
  {
      "search": "*",
      "count": true
  }
5. Selecione Pesquisar.
A consulta de pesquisa retorna todos os documentos do índice de pesquisa, incluindo uma contagem de todos os documentos no campo @odata.count
O índice de pesquisa retornar um documento JSON contendo os resultados da pesquisa.

## Examinar os resultados salvos em um Repositório de Conhecimento
1. No portal do Azure, navegue de volta para a conta de armazenamento do Azure
2. No painel de menu à esquerda, selecione Contêineres. Selecione o contêiner knowledge-store
![image](https://github.com/user-attachments/assets/e449077d-aa10-41c4-9c6e-8a51a6f19e18)

4. Você verá uma lista de pastas. Há uma pasta para todos os metadados de cada documento de revisão. Selecione qualquer uma das pastas. Na pasta, clique no arquivo objectprojection.json
5. Selecione Editar para ver o JSON produzido por um dos documentos do seu armazenamento de dados do Azure.










