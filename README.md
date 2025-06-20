# PrjEscolaVM
Projeto Integração e Implementação de Software para o fim do semestre 
Alunos
Victor Vinicius Ramos Pinheiro de Almeida - RA 6323096
Murilo Marchesini de Camargo - RA 6320051
Nesse repositório vamos salvar os arquivos mais polidos e completos referentes ao projeto ' Integração e Implementação de Software ' que será entregue no final do semestre.

# PostgreSQL Docker Image

Este repositório contém um Dockerfile para criar uma imagem Docker do PostgreSQL.

## Dockerfile

O Dockerfile utiliza a imagem oficial do PostgreSQL como base e configura um banco de dados, usuário e senha padrão. Além disso, copia um script SQL de inicialização para o diretório de inicialização do PostgreSQL.

### Estrutura do Dockerfile

```dockerfile
# Use a imagem oficial do PostgreSQL como base
FROM postgres:latest

# Defina variáveis de ambiente para configurar o PostgreSQL
ENV POSTGRES_DB=init_escola
ENV POSTGRES_USER=faat
ENV POSTGRES_PASSWORD=faat

# Copie o script de inicialização para o diretório de inicialização do PostgreSQL
COPY init.sql /docker-entrypoint-initdb.d/

# Exponha a porta padrão do PostgreSQL
EXPOSE 5432
```
## Como Utilizar
### Passo 1: Construir a Imagem Docker
Para construir a imagem Docker, execute o seguinte comando no diretório onde o Dockerfile está localizado:
```bash
docker build -t my-postgres-image .
```

### Passo 2: Executar o Contêiner
Para executar o contêiner Docker com a imagem criada, utilize o seguinte comando:
```bash 
docker run -d --name my-postgres-container -p 2000:5432 my-postgres-image
```
### Passo 3: Conectar ao PostgreSQL
Você pode se conectar ao PostgreSQL utilizando um cliente PostgreSQL, como dbeaver, psql, ou qualquer ferramenta de gerenciamento de banco de dados que suporte PostgreSQL. Utilize as seguintes credenciais:
```
Host: localhost
Porta: 5432
Banco de Dados: mydatabase
Usuário: myuser
Senha: mypassword
```
### Passo 4: Personalizar
Você pode personalizar o banco de dados, usuário e senha alterando as variáveis de ambiente no Dockerfile. Além disso, você pode adicionar scripts SQL adicionais ao diretório docker-entrypoint-initdb.d/ para serem executados na inicialização do contêiner.
