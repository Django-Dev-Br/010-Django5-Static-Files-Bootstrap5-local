
# 010 Django 4 Static Files - Bootstrap5 Local 

Neste [repositório anterior](https://github.com/Django-Dev-Br/009-Django-4-static-files-Bootstrap5-CDN), o Boostrap foi adicionado via CDN que é uma rede de entrega de conteúdo através da internet. 

Neste, diferentemente, o Boostrap foi baixado via download e está sendo carregaddo localmente.

### O que é Bootstrap?

Bootstrap é um dos frameworks front-end mais populares do mundo, projetado para facilitar a criação de sites responsivos e com foco em dispositivos móveis. Criado originalmente pelo Twitter, Bootstrap fornece uma coleção de ferramentas CSS e JavaScript que ajudam os desenvolvedores a construir interfaces de usuário consistentes e atraentes rapidamente. Com Bootstrap, é possível adicionar componentes como botões, formulários, menus de navegação e muito mais, utilizando classes pré-definidas que seguem as melhores práticas de design responsivo. Além disso, o Bootstrap é facilmente integrável com outros frameworks e bibliotecas, tornando-se uma escolha popular para desenvolvedores de todos os níveis.

Documentação oficial: [https://getbootstrap.com/docs/5.3/getting-started/introduction/](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

Melhor tutorial: [https://www.w3schools.com/bootstrap5/](https://www.w3schools.com/bootstrap5/)


### Vantagens de Baixar e Rodar o Bootstrap Localmente

Independência de Conexão com a Internet: Usar uma versão local significa que seu site não depende de uma conexão com a internet para carregar o Bootstrap. Isso é particularmente útil em ambientes de desenvolvimento offline ou em ambientes onde a conexão com a internet é lenta ou instável.

Controle sobre a Versão: Ter uma cópia local do Bootstrap permite que você controle exatamente qual versão está sendo usada. Isso evita problemas com atualizações automáticas que podem ocorrer ao usar CDNs, onde novas versões podem introduzir mudanças inesperadas.

Customização: Ao baixar Bootstrap localmente, você pode personalizar os arquivos CSS e JavaScript diretamente para atender às necessidades específicas do seu projeto, eliminando código desnecessário e potencialmente reduzindo o tamanho dos arquivos.

Consistência de Desempenho: Usar arquivos locais pode oferecer tempos de carregamento mais consistentes, pois elimina a variabilidade de latência de rede que pode ocorrer ao carregar arquivos de um servidor remoto.


## COMO RODAR ESSE PROJETO EM SEU COMPUTADOR:

### Requisitos

- **Python 3.12**  
  [Baixar Python 3.12](https://www.python.org/downloads/release/python-3122/)

  Confira o vídeo para saber como trabalhar com múltiplas versões do Python e com venv (ambiente virtual): [Trabalhando com Múltiplas Versões do Python + venv](https://youtu.be/eetDeQrv0Rs?si=rAIDmLCgdeh7ouXa)

- **Virtualenv**

  Para instalar o pacote `virtualenv` no Python, utilize os seguintes comandos:

  - **Linux**:
    ```bash
    python3 -m pip install virtualenv
    ```

  - **Windows**:
    ```bash
    python -m pip install virtualenv
    ```

### Passos para Executar

1. **Clone o repositório**:
    ```bash
    git clone https://github.com/Django-Dev-Br/010-Django-4-Static-Files-Bootstrap5-local.git
    cd 010-Django-4-Static-Files-Bootstrap5-local
    ```

2. **Crie um ambiente virtual**:
   
    - **Linux**:
    ```bash
    python3 -m venv myvenv
    ```

  - **Windows**:
    ```bash
    python -m venv myvenv
    ```

3. **Ative o ambiente virtual criado**:
    ```bash
    source myvenv/bin/activate  # Linux
    myvenv\Scripts\activate  # Windows
    ```

4. **Instale o Django**:
    ```bash
    pip install django==4.2.15
    ```

5. **Execute o servidor de desenvolvimento**:
    ```bash
    python manage.py runserver
    ```

7. **Acesse a aplicação no seu navegador**:

   Vá para [http://127.0.0.1:8000/](http://127.0.0.1:8000/) e você verá a imagem `pythondjango.jpg` sendo exibida na página inicial. 

### Código HTML 

Aqui está o código HTML usado para adicionar o Boostrap 5.3.3 ao projeto:

```
 
{% load static %} <!-- Carrega a tag 'static' para uso nos caminhos dos arquivos estáticos -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">  <!-- Adiciona a meta tag para responsividade -->

    <title>Página Inicial</title>
    
    <!-- Latest compiled and minified CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Latest compiled JavaScript -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

</head>

<body>

    <div class="container">  <!-- Usa um container Bootstrap para centralizar o conteúdo -->

        <h1 class="p-2 m-2">Imagem do Python Django</h1>

        <img class="img-thumbnail"  
             src="{% static 'myapp/images/pythondjango.jpg' %}" 
             alt="Python Django"
             width="60%">
    </div>
    
</body>
</html>
```

### Estrutura de Diretórios do Projeto

```
010-Django-4-Static-Files-Bootstrap5-local/
├── manage.py
├── myapp/
│   ├── __init__.py
│   ├── apps.py
│   ├── views.py           # Contém a função 'index' para renderizar 'index.html'
│   └── templates/
│       └── index.html     # Página HTML que carrega o Boostrap local
├── myproject/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py        # Configurações de STATIC_DIRS, STATICFILES_DIRS, STATIC_ROOT
│   ├── urls.py            # URL principal direcionando para 'myapp.views.index'
│   └── wsgi.py
└── static/
    └── myapp/
        ├── bootstrap/
        │   ├── bootstrap.min.css    # Arquivo CSS do Bootstrap
        │   └── bootstrap.bundle.min.js  # Arquivo JS do Bootstrap
        └── images/
            └── pythondjango.jpg  # Imagem a ser exibida
```

### OBS: 
### Coletando Arquivos Estáticos para Produção

Quando estiver pronto para implantar seu projeto Django em produção, é necessário coletar todos os arquivos estáticos em um único diretório definido por `STATIC_ROOT`. Isso permite que o servidor web sirva esses arquivos de forma eficiente. Para coletar todos os arquivos estáticos, use o comando:

```bash
python manage.py collectstatic
```

Este comando irá procurar todos os arquivos estáticos nos diretórios especificados em `STATICFILES_DIRS` e nas pastas `static/` de cada aplicativo, e copiá-los para o diretório definido por `STATIC_ROOT`.

### O comando findstatic

O comando findstatic é uma ferramenta útil para depuração, que permite verificar se o Django consegue localizar um arquivo estático específico. Ele mostra o caminho completo para um arquivo estático se ele for encontrado nos diretórios de arquivos estáticos.

Como usar:

```bash
python manage.py findstatic <caminho/do/arquivo>
```

Por exemplo, para verificar se o Django consegue encontrar o arquivo bootstrap.min.css, você pode usar:

Exemplo:

bash
```
python manage.py findstatic myapp/bootstrap/bootstrap.min.css
```

Este comando verifica os diretórios listados em STATICFILES_DIRS e as pastas static/ dos aplicativos do Django para encontrar o caminho completo do arquivo especificado. É uma maneira rápida de garantir que seus arquivos estáticos estejam localizados corretamente e que o Django possa acessá-los.

### Sobre Nosso Treinamento Prático-Profissional com projeto real para iniciantes e avançados em web DevOps Full-stack com Python, Django, Bootstrap e Linux.

[Django Developers Brasil - Aprenda programando enquanto programa aprendendo!](https://django.dev.br/)

Nosso treinamento oferece uma experiência prática de aprendizado de programação, adequada tanto para iniciantes quanto para desenvolvedores avançados. Você participará de um projeto real de desenvolvimento de software em um ambiente corporativo autêntico, onde pessoas com diferentes níveis de conhecimento irão colaborar, aprendendo umas com as outras.

**Junte-se a nós!** E desenvolva as habilidades necessárias para o mercado de trabalho, aprimorando tanto seus conhecimentos técnicos quanto suas soft skills em um ambiente colaborativo e realista.
