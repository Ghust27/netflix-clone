# Netflix Clone

Este projeto é uma aplicação web que replica a interface e funcionalidades básicas do Netflix, utilizando Python, Django e PostgreSQL no back-end, com Django Templates e CSS customizado no front-end. O objetivo é criar uma experiência de usuário semelhante à plataforma de streaming, com autenticação de usuários, exibição de filmes/séries e suporte a streaming de mídia.

## Tecnologias Utilizadas

### Back-end
- **Python 3**: Linguagem principal para o desenvolvimento.
- **Django 4.1.7**: Framework web para estruturação do back-end, organizado em apps (`core/` e `netflix_site/`).
- **Gunicorn 21.2.0**: Servidor WSGI usado para deploy (ex.: Heroku), declarado no `Procfile`.
- **Requests 2.28.2**: Biblioteca para requisições HTTP externas, como integração com APIs (ex.: TMDB API).
- **Starlette 0.26.1**: Toolkit ASGI para funcionalidades assíncronas, como streaming de vídeo.

### Banco de Dados
- **SQLite**: Usado em desenvolvimento local (`db.sqlite3`).
- **PostgreSQL**: Usado em produção, com driver `psycopg2-binary==2.9.9`.

### Front-end
- **Django Templates**: HTML puro para renderização de páginas (ex.: `login.html`, `index.html`, `movie.html`).
- **CSS Customizado**: Estilização em `static/assets/` (ex.: `style.css`, `login.css`, `profiles.css`).

### Media
- Imagens de filmes armazenadas em `media/movie_images/`.
- Vídeos de filmes armazenados em `media/movie_videos/`.

### Configuração
- **Variáveis de Ambiente**: Gerenciadas via arquivo `.env` com `python-dotenv` para configurações seguras (ex.: chaves de API, credenciais do banco de dados).

## Funcionalidades

- Interface de usuário inspirada no Netflix, com navegação por filmes e séries.
- Autenticação de usuários (login/cadastro) gerenciada pelo Django.
- Exibição de conteúdos em formato de lista ou carrossel, com suporte a imagens e vídeos.
- Integração com APIs externas para dados de filmes/séries.
- Suporte a streaming de vídeos utilizando Starlette para endpoints assíncronos.
- Gerenciamento de perfis de usuário.

## Pré-requisitos

Antes de começar, certifique-se de ter instalado:
- [Python 3.10+](https://www.python.org/)
- [Git](https://git-scm.com/)
- [PostgreSQL](https://www.postgresql.org/) (para produção)
- Opcional: Conta em uma plataforma de deploy como Heroku.

## Instalação

1. Clone o repositório:
   ```bash
   git clone https://github.com/Ghust27/netflix-clone.git
   ```

2. Navegue até o diretório do projeto:
   ```bash
   cd netflix-clone
   ```

3. Crie e ative um ambiente virtual:
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   venv\Scripts\activate     # Windows
   ```

4. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

5. Configure as variáveis de ambiente:
   - Crie um arquivo `.env` na raiz do projeto.
   - Adicione as configurações necessárias, como credenciais do banco de dados e chaves de API.
   - Exemplo de `.env`:
     ```
     SECRET_KEY=your_django_secret_key
     DATABASE_URL=postgresql://user:password@localhost:5432/dbname
     TMDB_API_KEY=your_tmdb_api_key
     DEBUG=True
     ```

6. Aplique as migrações do banco de dados:
   ```bash
   python manage.py migrate
   ```

7. Inicie o servidor de desenvolvimento:
   ```bash
   python manage.py runserver
   ```

8. Abra o navegador e acesse `http://localhost:8000`.

## Estrutura do Projeto

```
netflix-clone/
├── core/                     # App Django para lógica central
├── netflix_site/             # App Django para funcionalidades do site
├── media/                    # Diretório para arquivos de mídia
│   ├── movie_images/         # Imagens de filmes
│   ├── movie_videos/         # Vídeos de filmes
├── static/                   # Arquivos estáticos
│   ├── assets/               # CSS customizado (style.css, login.css, profiles.css)
├── templates/                # Django Templates (login.html, index.html, movie.html)
├── db.sqlite3                # Banco de dados SQLite para desenvolvimento
├── .env                      # Variáveis de ambiente (não versionado)
├── manage.py                 # Script de gerenciamento do Django
├── Procfile                  # Configuração para deploy (ex.: Heroku)
├── requirements.txt          # Dependências do projeto
└── README.md                 # Documentação do projeto
```

## Deploy

Para deploy em produção (ex.: Heroku):
1. Ascerte o `Procfile` e configure o `Gunicorn`.
2. Configure o banco de dados PostgreSQL no serviço de hospedagem.
3. Adicione as variáveis de ambiente no painel de configuração da plataforma.
4. Execute:
   ```bash
   heroku config:set SECRET_KEY=your_secret_key
   heroku config:set DATABASE_URL=your_postgres_url
   ```

