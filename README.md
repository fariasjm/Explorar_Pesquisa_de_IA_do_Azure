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
5. No portal do Azure, selecione o contêiner coffee-reviews. No contêiner, selecione Carregar.






