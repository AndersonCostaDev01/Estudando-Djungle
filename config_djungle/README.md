# Configurando Djungle

## Oque e o Djangle

Djungle e um framework python para criação de aplicaçoes web

### Mas oque e um framework?

Um framework e um conjunto de ferramentas juntas em um so local que te auxilia no desenvolvimento, isto porque muitas funçoes ja vem prontas dentro dele para te ajudar e agilizar seu desenvolvimento

## Inicio das configuraçoes

> **obs**: A aplicação sera feita em um outro repositorio para facilitar o entendimento mas os passos serão descritos aqui

- Veja o repositorio em: [Repositorio-mysite](https://github.com/AndersonCostaDev01/mysite)

### Requisistos

Para criar um projeto em djungle e nessesario ter o python3 em sua maquina, para verificar se voce tem ele rode em seu terminal `python --version` para windols ou `python3 -- version` para mac e linux
<br><br>
e recomendado que para a criação de qualquer projeto python ele seja feito em um ambiente virtual para evitar conflitos internos, então para criar o ambiente rode

> **Obs**: e recomendado que o nome do ambiente seja .venv ou env apenas por criterio de padronização

```
<nome do ambiente>\Scripts\activate
```

agora entre dentro do ambiente vitual

```
<nome do ambiente>\Scripts\activate
```

> **obs:** Lembre de quando terminar de codar sair do ambiente virtual com "deactivate"

agora seguimos com a instalação do **Djungle**

```
pip install django
```

para iniciar realmente um projeto django e nessesario rodar

```
django-admin startproject <nome do projeto>
```

isto vai criar a pasta principal do seu projeto com o nome dela
<br><br>
agora voce ja tem sua primeira aplicação django e para rodar ela use

```
python .\manage.py runserver
```

agora sua aplicação esta rodando na porta 8000, para interromper basta apertar `ctrl + c`
<br><br>
agora para criar um app que e uma forma que o django utiliza para dividir as funçoes de sua aplicação e facilitar o desenvolvimento e manutenção rode

```
python .\manage.py startapp <nome do app>
```

então uma nova pasta ira ser criada com o nome do seu novo app
