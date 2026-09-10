# Projeto Integrador — Gestão de Produtos e Fornecedores

Sistema full stack desenvolvido para a disciplina **Projeto Integrador** da [Faculdade Gran](https://faculdade.grancursosonline.com.br/). A aplicação permite cadastrar produtos, cadastrar fornecedores e gerenciar a associação muitos-para-muitos entre eles.

## Funcionalidades

- Cadastro, edição, listagem e exclusão de produtos.
- Cadastro, edição, listagem e exclusão de fornecedores.
- Associação de produtos a fornecedores com preço praticado e prazo de entrega.
- Consulta das associações existentes.
- Persistência local em SQLite.
- API REST consumida por uma interface React.

## Tecnologias

| Camada | Tecnologias |
| --- | --- |
| Backend | Node.js, Express, SQLite3, CORS |
| Frontend | React 18, React Router, Axios, React Scripts |
| Desenvolvimento | Nodemon, npm, Git |

## Estrutura do projeto

```text
projeto-integrador/
├── .github/workflows/ci.yml
├── .editorconfig
├── .gitignore
├── README.md
├── backend/
│   ├── .env.example
│   ├── .gitignore
│   ├── data/.gitkeep
│   ├── package.json
│   └── src/
│       ├── controllers/
│       ├── database/db.js
│       ├── routes/index.js
│       └── server.js
└── frontend/
    ├── .env.example
    ├── .gitignore
    ├── package.json
    ├── public/index.html
    └── src/
        ├── pages/
        ├── services/api.js
        ├── App.css
        ├── App.js
        └── index.js
```

## Pré-requisitos

- [Node.js](https://nodejs.org/) 18 ou superior, preferencialmente a versão LTS.
- npm instalado junto com o Node.js.
- Git, caso deseje versionar e publicar o projeto.

## Execução local

### 1. Backend

Abra um terminal na raiz do projeto e execute:

```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

A API ficará disponível em `http://localhost:3001`.

### 2. Frontend

Abra outro terminal e execute:

```bash
cd frontend
cp .env.example .env
npm install
npm start
```

A aplicação será aberta em `http://localhost:3000`.

> No Windows, crie os arquivos `.env` copiando manualmente o conteúdo de `.env.example` caso o comando `cp` não esteja disponível.

## Variáveis de ambiente

### Backend — `backend/.env`

| Variável | Padrão | Descrição |
| --- | --- | --- |
| `PORT` | `3001` | Porta da API |
| `DB_PATH` | `backend/data/database.sqlite` | Caminho opcional do arquivo SQLite |

### Frontend — `frontend/.env`

| Variável | Padrão | Descrição |
| --- | --- | --- |
| `REACT_APP_API_URL` | `http://localhost:3001/api` | URL base da API |

Os arquivos `.env` não devem ser enviados ao GitHub. Os arquivos `.env.example` servem apenas como modelo.

## Rotas da API

A API usa o prefixo `/api`.

| Método | Endpoint | Descrição |
| --- | --- | --- |
| `GET` | `/api/produtos` | Lista produtos |
| `GET` | `/api/produtos/:id` | Busca um produto |
| `POST` | `/api/produtos` | Cadastra produto |
| `PUT` | `/api/produtos/:id` | Atualiza produto |
| `DELETE` | `/api/produtos/:id` | Remove produto |
| `GET` | `/api/fornecedores` | Lista fornecedores |
| `GET` | `/api/fornecedores/:id` | Busca um fornecedor |
| `POST` | `/api/fornecedores` | Cadastra fornecedor |
| `PUT` | `/api/fornecedores/:id` | Atualiza fornecedor |
| `DELETE` | `/api/fornecedores/:id` | Remove fornecedor |
| `GET` | `/api/associacoes` | Lista associações |
| `POST` | `/api/associacoes` | Associa produto e fornecedor |
| `DELETE` | `/api/associacoes/:id` | Remove uma associação |
| `GET` | `/api/produtos/:id/fornecedores` | Lista fornecedores de um produto |
| `GET` | `/api/fornecedores/:id/produtos` | Lista produtos de um fornecedor |

## Banco de dados

O banco SQLite é criado automaticamente na primeira execução do backend. O arquivo fica em `backend/data/database.sqlite` e é ignorado pelo Git para que dados locais não sejam publicados acidentalmente.

## Verificações

Depois de instalar as dependências, use os comandos abaixo:

```bash
# Verificar a sintaxe dos arquivos JavaScript do backend
cd backend
npm run check

# Gerar a build de produção do frontend
cd ../frontend
npm run build
```

## Publicação no GitHub

Na raiz do projeto:

```bash
git init
git add .
git commit -m "feat: organiza projeto integrador"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/SEU_REPOSITORIO.git
git push -u origin main
```

Antes do primeiro `git add`, confirme que arquivos como `.env`, `node_modules` e `backend/data/database.sqlite` aparecem ignorados:

```bash
git status --ignored
