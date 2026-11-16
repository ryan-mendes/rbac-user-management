<h1 align="center">🖥️ Gerenciamento de TI</h1>

<p align="center">
  Sistema full stack de gestão de usuários com autenticação JWT e controle de acesso por perfil (Admin, Gestor e Usuário).
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white"/>
  <img src="https://img.shields.io/badge/Sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/styled--components-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white"/>
</p>

## Sobre

Aplicação dividida em **API REST (Node.js + Express)** e **front-end (Next.js 14)**. Cada usuário tem um perfil que define quais painéis e operações ele pode acessar.

### Funcionalidades
- Login com **JWT** e senhas com hash (**bcrypt**)
- Cadastro de usuários restrito a Admin/Gestor
- CRUD de usuários (Admin)
- Painéis diferentes por perfil: Dashboard, Gestor e Admin
- Rotas protegidas no front-end (`ProtectedRoute` + `AuthContext`)
- Validação de formulários com **React Hook Form + Zod**

## Arquitetura

```
Gerenciamento-de-TI/
├── backend/            # API REST
│   ├── app.js          # Entrada da aplicação (porta 5000)
│   ├── config/         # Conexão Sequelize/SQLite
│   ├── middlewares/    # Middleware de autenticação JWT
│   ├── models/         # Model Usuario
│   └── routes/         # /auth e /user
└── frontend/           # Next.js (App Router)
    └── app/
        ├── login/  register/  profile/  admin/
        ├── components/  context/  utils/
```

## Endpoints

| Método | Rota | Acesso | Descrição |
|---|---|---|---|
| POST | `/auth/login` | Público | Autentica e retorna o token |
| POST | `/auth/register` | Admin / Gestor | Cadastra usuário |
| GET | `/auth/user` | Autenticado | Dados do usuário logado |
| GET | `/user/users` | Admin | Lista usuários |
| PUT | `/user/users/:id` | Admin | Atualiza usuário |
| DELETE | `/user/users/:id` | Admin | Remove usuário |
| GET | `/user/dashboard` · `/user/gestor` · `/user/admin` | Por perfil | Painéis |

## Como rodar

**Backend**
```bash
cd backend
cp .env.example .env   # defina JWT_SECRET_KEY
npm install
npm start              # http://localhost:5000
```

**Frontend**
```bash
cd frontend
npm install
npm run dev            # http://localhost:3000
```
> Ajuste `API_BASE_URL` em `frontend/app/config/config.js` para `http://localhost:5000` ao rodar localmente.

## Autor

Feito por **Ryan Mendes** · [LinkedIn](https://www.linkedin.com/in/ryan-mendes-b7197322a/)
