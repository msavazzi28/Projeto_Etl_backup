# Backup de arquivos locais para AWS S3

Este projeto tem como objetivo realizar o **backup automático de arquivos de uma pasta local para um bucket S3 da AWS**.

O funcionamento do script é simples:

1. Lê as credenciais e configurações da AWS a partir de um arquivo `.env`
2. Lista os arquivos existentes em uma pasta local
3. Envia esses arquivos para um bucket S3
4. Após o upload, remove os arquivos da pasta local

## Como funciona

O script utiliza:

- `boto3` para comunicação com a AWS S3
- `python-dotenv` para carregar variáveis de ambiente do arquivo `.env`
- `os` para manipulação de arquivos e diretórios locais

## Pré-requisitos

Antes de executar o projeto, você precisa ter instalado:

- Python 3.10+ (ou a versão do seu projeto)
- Poetry ou pip
- Uma conta AWS com acesso ao S3
- Um bucket S3 já criado

## Instalação

### Usando Poetry

```bash
poetry install