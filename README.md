# Backup de arquivos locais para AWS S3

Este projeto foi desenvolvido para realizar o **backup automático de arquivos de uma pasta local para um bucket S3 da AWS**.

Para garantir mais segurança no acesso, foi criada uma estrutura dedicada na AWS com:

- **um bucket S3 específico** para armazenar os arquivos de backup
- **um usuário IAM exclusivo** para essa automação
- **permissões restritas somente ao bucket utilizado no projeto**, evitando acesso desnecessário a outros recursos da conta AWS

## Objetivo do projeto

O objetivo deste script é automatizar o envio de arquivos de uma pasta local para a nuvem, utilizando o Amazon S3 como repositório de backup.

O fluxo do processo funciona da seguinte forma:

1. O script lê as credenciais e configurações salvas no arquivo `.env`
2. Busca os arquivos disponíveis em uma pasta local
3. Envia os arquivos para o bucket S3 configurado
4. Após a conclusão do upload, remove os arquivos locais da pasta

## Segurança e controle de acesso

Para este projeto, foi adotada uma configuração de acesso mais segura na AWS.

Foi criado:

- **um bucket S3 dedicado ao armazenamento dos backups**
- **um usuário IAM exclusivo para integração do script**
- **uma política de permissão limitada**, permitindo que esse usuário acesse e altere apenas o bucket definido para o projeto

Essa abordagem é importante porque evita o uso de credenciais com acesso amplo à conta AWS, seguindo uma prática mais segura de segregação de permissões.

## Tecnologias utilizadas

O projeto utiliza:

- `Python`
- `boto3` para integração com o Amazon S3
- `python-dotenv` para leitura das variáveis de ambiente
- `os` para manipulação de arquivos locais
- `Poetry` para gerenciamento de dependências

## Pré-requisitos

Antes de executar o projeto, é necessário ter:

- Python instalado
- Poetry instalado, ou alternativamente `pip`
- Uma conta AWS
- Um bucket S3 já criado
- Um usuário IAM com permissão de acesso ao bucket utilizado no projeto

## Configuração do `.env`

Antes de executar o script, crie um arquivo chamado `.env` na raiz do projeto com as informações de acesso.

Exemplo:

```env
AWS_ACCESS_KEY_ID=coloque_sua_access_key_aqui
AWS_SECRET_ACCESS_KEY=coloque_sua_secret_key_aqui
AWS_REGION=sa-east-1
BUCKET_NAME=nome-do-seu-bucket