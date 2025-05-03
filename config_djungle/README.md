### 📌 **Sumário**

- [Configurando Django](#configurando-django)
  - [O que é o Django?](#o-que-é-o-django)
  - [Mas o que é um framework?](#mas-o-que-é-um-framework)
- [Início das configurações](#início-das-configurações)
  - [Requisitos](#requisitos)
  - [Criando um ambiente virtual](#criando-um-ambiente-virtual)
  - [Instalando o Django](#instalando-o-django)
  - [Criando um novo projeto Django](#criando-um-novo-projeto-django)
  - [Executando o servidor de desenvolvimento](#executando-o-servidor-de-desenvolvimento)
  - [Criando um novo app Django](#criando-um-novo-app-django)
  - [Configurando um novo app](#configurando-um-novo-app)
  - [Iniciando as migrações](#iniciando-as-migrações)
- [Models e Admin](#models-e-admin)

---

# 🛠️ Configurando Django

## 📌 O que é o Django?

[Django](https://www.djangoproject.com/) é um **framework** Python para criação de aplicações web. Ele oferece uma estrutura robusta e organizada para o desenvolvimento de sistemas, permitindo que você foque mais na lógica do seu projeto e menos em detalhes repetitivos.

### 🔹 Mas o que é um framework?

Um **framework** é um conjunto de ferramentas e bibliotecas organizadas em um só local para facilitar o desenvolvimento de software. Isso porque muitas funcionalidades essenciais já vêm prontas, agilizando o processo de criação da aplicação.

---

## 🚀 Início das configurações

> **Obs:** A aplicação será feita em outro repositório para facilitar o entendimento, mas os passos serão descritos aqui.

🔗 **Veja o repositório:** [Repositorio-mysite](https://github.com/AndersonCostaDev01/mysite)

---

### 📌 Requisitos

Para criar um projeto em Django, é necessário ter o **Python 3** instalado em sua máquina. Para verificar se você já tem o Python instalado, execute no terminal:

- No **Windows**:
  ```bash
  python --version
  ```
- No **macOS e Linux**:
  ```bash
  python3 --version
  ```

Recomenda-se atualizar o `pip`:

```bash
python -m pip install --upgrade pip
```

---

### 📌 Criando um ambiente virtual

É **recomendado** que todo projeto Python seja feito dentro de um **ambiente virtual**, para evitar conflitos entre dependências de diferentes projetos.

Para criar um ambiente virtual, execute:

```bash
python -m venv <nome-do-ambiente>
```

> **Obs:** É comum usar os nomes `.venv` ou `env` por padronização.

Para **ativar** o ambiente virtual:

- No **Windows**:
  ```bash
  <nome-do-ambiente>\Scripts\activate
  ```
- No **macOS e Linux**:
  ```bash
  source <nome-do-ambiente>/bin/activate
  ```

> **Obs:** Quando terminar de codar, lembre-se de **desativar** o ambiente com:

```bash
deactivate
```

---

### 📌 Instalando o Django

Com o ambiente virtual ativado, instale o Django executando:

```bash
pip install django
```

---

### 📌 Criando um novo projeto Django

Para criar um novo projeto Django, use o comando:

```bash
django-admin startproject <nome-do-projeto>
```

Isso criará uma pasta com a estrutura inicial do seu projeto.

---

### 📌 Executando o servidor de desenvolvimento

Agora, para rodar o servidor local do Django, utilize:

```bash
python manage.py runserver
```

A aplicação será executada na **porta 8000**. Para interromper o servidor, pressione `Ctrl + C`.

---

### 📌 Criando um novo app Django

No Django, os **apps** são módulos independentes que organizam as funcionalidades da aplicação. Para criar um novo app, execute:

```bash
python manage.py startapp <nome-do-app>
```

Isso criará uma nova pasta com a estrutura do seu app dentro do projeto.

---

### 📌 Configurando um novo app

Para que o Django reconheça seu app, é necessário adicioná-lo ao arquivo `settings.py`, na lista `INSTALLED_APPS`.

Após o último app listado, adicione uma vírgula e insira o nome do seu app entre aspas simples. O Django já vem com alguns apps nativos — por enquanto, apenas mantenha-os como estão.

---

### 📌 Iniciando as migrações

Para aplicar as migrações padrão do Django, execute:

```bash
python manage.py migrate
```

Isso aplicará todas as migrações iniciais necessárias para o funcionamento básico da aplicação.

---

## 📦 Models e Admin

### 📌 O que é `models`?

O `models` é um componente fundamental do Django, responsável por definir a estrutura das tabelas no banco de dados através de classes em Python. Ele faz parte do ORM (Object-Relational Mapping) do Django, permitindo que você crie, leia, atualize e delete dados do banco de forma simples e intuitiva, sem precisar escrever SQL diretamente.

Com os `models`, você pode:

- Definir os campos de uma tabela usando atributos de classe.
- Criar relacionamentos entre tabelas com facilidade.
- Utilizar métodos prontos para consultas, filtros e ordenações.
- Integrar os dados facilmente com outras partes da aplicação, como as views e forms.

#### Exemplo de importação:

```python
from django.db import models
```

---

### 📌 Organizando os models

Para organizar melhor os _models_ no projeto, você pode criar uma pasta `models` dentro do app, e nela um arquivo `__init__.py`.

Depois, crie arquivos `.py` separados com nomes descritivos, como `usuario.py`, `produto.py` etc., contendo os modelos relacionados.

```python
from django.db import models

class Produto(models.Model):
    nome = models.CharField(max_length=200, unique=True)
```

> 🔗 Veja os tipos de campos disponíveis:  
> [Documentação oficial do Django](https://docs.djangoproject.com/en/5.2/topics/db/models/)

Após criar o model, rode:

```bash
python manage.py makemigrations
python manage.py migrate
```

---

### 📌 Ativando o painel `/admin`

O Django possui um painel administrativo embutido acessível por `/admin`.

Para registrar um modelo e permitir edição via interface administrativa, edite o arquivo `admin.py` do seu app:

```python
from django.contrib import admin
from .models import Produto

admin.site.register(Produto)
```

Depois, crie um superusuário com:

```bash
python manage.py createsuperuser
```

Preencha os campos solicitados:

- Nome de usuário
- E-mail
- Senha (e confirmação)

Com isso, acesse [http://localhost:8000/admin](http://localhost:8000/admin), faça login e comece a gerenciar os dados diretamente pelo navegador.

---

### 📌 Dica extra: Arquivo `.gitignore`

É importante criar um arquivo `.gitignore` na raiz do seu projeto contendo:

```
.venv/
__pycache__/
*.pyc
db.sqlite3
.env
```

---

## ✅ Pronto!

Agora você já tem uma base funcional com Django, pronta para evoluir com models, views, templates e muito mais.  
Se quiser continuar, recomendo explorar:

- `Views` e URLs
- `Templates` com HTML
- Sistema de autenticação (login/logout)
- APIs com Django REST Framework

🚀 Bora codar!
