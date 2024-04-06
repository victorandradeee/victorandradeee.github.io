# Passo a Passo

## Passo 1 - Inicialização do Aplicativo:
Primeiro, inicie  seu aplicativo Flask em `app.py`.

```python
from flask import Flask
app = Flask(__name__)
```

## Passo 2 - Configuração do Cache
Integre o Flask-Caching para caching simples no lado do servidor.

```python
from flask_caching import Cache
cache = Cache(app, config={'CACHE_TYPE': 'simple'})
```

## Passo 3 - Definição de Rota com Cache
Crie uma rota que utilize o cache para armazenar dados por 2 minutos. Imagine que esta rota retorna dados que mudam com pouca frequência, como informações de um artigo.

```python
@app.route('/article')
@cache.cached(timeout=120)  # Cache de 2 minutos
def article():
    # Aqui, inseriria a lógica para buscar dados reais, simularemos com um texto estático
    return "Aqui vai o conteúdo de um artigo."
```

## Passo 4 - Controle de Cache via Headers HTTP
Implemente uma rota que use headers HTTP para controle de cache do lado do cliente.

```python
@app.route('/news')
def news():
    response = make_response("Notícias recentes aqui")  # Deveria buscar dados reais
```

## Passo 5 - Execução e Teste:
Agora você vai executar a sua aplicação Flask (python app.py) e testar as rotas utilizando Postman ou uma ferramenta similar.

## Fontes

(https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)
(https://rapidapi.com/guides/api-caching-with-http-headers)
(https://codedamn.com/news/backend/rest-api-caching-advanced-techniques)

## Contribuições
Eduardo Trova (10265570) : Eduardo foi responsável pela implementação do cache na aplicação e pela escrita de partes do tutorial.

Victor Andrade (10390648): Victor contribuiu com a configuração do ambiente de desenvolvimento e também ajudou na escrita e formatação do tutorial.

