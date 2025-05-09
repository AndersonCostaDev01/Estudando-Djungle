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
- [Views](#views)

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

---

### 📌 Configurando um novo app

Para que o Django reconheça seu app, é necessário adicioná-lo ao arquivo `settings.py`, na lista `INSTALLED_APPS`.

Após o último app listado, adicione uma vírgula e insira o nome do seu app entre aspas simples.

---

### 📌 Iniciando as migrações

Para aplicar as migrações padrão do Django, execute:

```bash
python manage.py migrate
```

---

## 📦 Models e Admin

### 📌 O que é `models`?

O `models` é um componente fundamental do Django, responsável por definir a estrutura das tabelas no banco de dados através de classes em Python.

```python
from django.db import models
```

### 📌 Organizando os models

```python
class Produto(models.Model):
    nome = models.CharField(max_length=200, unique=True)
```

Após criar o model, rode:

```bash
python manage.py makemigrations
python manage.py migrate
```

### 📌 Ativando o painel `/admin`

```python
from django.contrib import admin
from .models import Produto

admin.site.register(Produto)
```

Crie um superusuário:

```bash
python manage.py createsuperuser
```

---

## 🚀 Views

### 📌 O que são as Views?

As **views** fazem a ponte entre **URLs**, **templates** e **models**.

### 🗂️ Organização das Views

```text
seu_app/
├── views/
│   ├── home.py
│   ├── posts.py
│   └── __init__.py
```

### 🧱 Exemplo de View com Classe

```python
from django.http import HttpResponse
from django.views import View

class PostView(View):
    def get(self, request, *args, **kwargs):
        return HttpResponse("Olá, esta é a página de postagens!")
```

---

## 🚀 Django Templates

### O que são templates no Django?

**Templates** no Django são a forma de **misturar HTML com dados do Python** para gerar páginas dinâmicas.  
Eles permitem que você exiba conteúdo de forma interativa, utilizando dados vindos do backend.

---

### 🛠️ Configuração dos templates

Para configurar os templates no Django, siga os passos abaixo:

1. Crie uma pasta chamada `templates` na raiz do projeto (no mesmo nível do `manage.py`).
2. Vá até o arquivo `settings.py` e adicione a seguinte linha:

```python
import os  # Certifique-se de ter essa importação no topo

TEMPLATES_DIR = os.path.join(BASE_DIR, 'templates')
```

3. localize a variavel `TEMPLATES` no mesmo arquivo e altere o valor da chave `DIRS` para incluir `TEMPLATES_DIR`:

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [TEMPLATES_DIR],  # Aqui você adiciona a pasta de templates
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                # Processadores de contexto padrão
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

Com essa configuração, o Django poderá reconhecer e renderizar os arquivos `.html` da pasta `templates` para gerar páginas dinâmicas.

### Como utilizar na pratica

Inicialmente crie os arquivos `.html` normalmente para uso na aplicação, a diferença de um `.html` normal para um do `django` são algumas tags adicionais que o django disponibiliza para pegarmos informaçoes de certos campos ou adicionarmos informaçoes em certos campos alem de tags que extendem outros arquivos `.html` para podermos reaproveitar codigo estas `tags` são

```html
{% block content %}
<!-- Content Goes here -->
{% endblock content %} e {% for post in post_list %}
<div class="card mb-4">
  <div class="card-body">
    <h2 class="card-title">{{ post.title }}</h2>
    <p class="card-text text-muted h6">
      {{ post.author }} | {{ post.created_on}}
    </p>
    <p class="card-text">{{post.content|slice:":200" }}</p>
    <a href="{% url 'post_detail' post.slug  %}" class="btn btn-primary"
      >Read More &rarr;</a
    >
  </div>
</div>
{% endfor %}
```

estas tags permitem como dito acima reaproveitar conteudos e adicionar conteudo de forma dinamica na pagina

### Onde utilizalos

Utilizamos nas `viws` para renderizar apartir de uma função `get` que ira retornar alguma junto ao template

```python
class PostView(generic.ListView): 

    # pega os posts publicados com status de 'publish' e ordena eles de acordo com a data de criacao, armazena eles na variavel queryset
    queryset = Post.objects.filter(status=1).order_by('-created_on')
    template_name = 'index.html' # renderiza o template 
```

---

### 📌 Dica extra: Arquivo `.gitignore`

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
