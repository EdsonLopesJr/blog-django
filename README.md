# Documentação de Inicialização e Instalação do Projeto Django

## Índice

1. [Pré-requisitos](#pré-requisitos)
2. [Clonando o Repositório](#clonando-o-repositório)
3. [Configuração do Ambiente Virtual](#configuração-do-ambiente-virtual)
4. [Configuração do Banco de Dados](#configuração-do-banco-de-dados)
5. [Aplicando as Migrações](#aplicando-as-migrações)
6. [Coletando Arquivos Estáticos](#coletando-arquivos-estáticos)
7. [Criando o Superusuário](#criando-o-superusuário)
8. [Executando o Servidor de Desenvolvimento](#executando-o-servidor-de-desenvolvimento)

---

## Pré-requisitos

Antes de iniciar a instalação, certifique-se de que seu ambiente atende aos seguintes requisitos:

- **Python 3.8+**: Django 5.1.2 requer Python 3.8 ou superior.
- **pip**: Gerenciador de pacotes Python.
- **Git**: Para clonar o repositório do projeto.

## Clonando o Repositório

Primeiro, clone o repositório do projeto para sua máquina local utilizando o Git.

```bash
git clone https://github.com/EdsonLopesJr/blog-django.git
```

## Configuração do Ambiente Virtual

É recomendado utilizar um ambiente virtual para isolar as dependências do projeto.

## Criar o Ambiente Virtual

```bash
python3 -m venv venv
```

### Ativar o Ambiente Virtual

```bash
source venv/bin/activate
```

### Instalação das Dependências

Com o ambiente virtual ativado, instale as dependências listadas no arquivo requirements.txt.

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## Configuração do Banco de Dados

Este projeto utiliza SQLite como banco de dados, o que simplifica a configuração, especialmente para ambientes de desenvolvimento.

### Configuração Padrão do SQLite

No arquivo settings.py do seu projeto Django, a configuração padrão do banco de dados geralmente está definida da seguinte forma:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}
```

### Observações:

SQLite é um banco de dados leve que não requer configuração adicional.
O arquivo `db.sqlite3` será criado automaticamente na raiz do projeto quando as migrações forem aplicadas.

## Aplicando as Migrações

Após configurar o banco de dados, aplique as migrações para criar as tabelas necessárias.

```bash
python manage.py migrate
```

Se o projeto inclui migrações personalizadas ou de terceiros, certifique-se de aplicá-las também.

### Coletando Arquivos Estáticos

Para servir arquivos estáticos corretamente, especialmente em produção, execute o comando de coleta.

```bash
python manage.py collectstatic
```

Siga as instruções exibidas no terminal para confirmar a coleta dos arquivos.

## Criando o Superusuário

Para poder realizar operações de CRUD (Criar, Ler, Atualizar, Deletar) no painel administrativo do Django, é necessário criar um superusuário. Esse superusuário terá permissões administrativas, e com isso, o botão de adicionar e editar posts estará disponível no painel.

Crie o superusuário executando o seguinte comando:

```bash
python manage.py createsuperuser
````

Preencha as informações solicitadas no terminal, como nome de usuário, e-mail e senha

## Executando o Servidor de Desenvolvimento

Inicie o servidor de desenvolvimento para verificar se tudo está funcionando corretamente.

```bash
python manage.py runserver
```

Por padrão, o servidor estará acessível em http://127.0.0.1:8000/.

### Logar no Painel Administrativo

acesse o painel de administração em:
http://127.0.0.1:8000/admin

Insira as credenciais do superusuário que você criou para se autenticar.

Com isso, os botões de adicionar e editar posts estarão disponíveis.

