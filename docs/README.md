# Passo a Passo

## Passo 1 - Inicialização do Aplicativo:
Inicie seu aplicativo Flask em `app.py`.

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
