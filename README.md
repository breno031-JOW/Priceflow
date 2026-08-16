# PRICEFLOW

Sistema de precificação e orçamentos para pequenas empresas — cadastro de
produtos, fornecedores e clientes, cálculo de custo/margem e geração de
orçamentos, com controle de acesso por papel (admin/gestor/vendedor).

## Funcionalidades

- Cadastro de produtos com cálculo automático de custo e preço de venda por margem
- Cadastro de fornecedores e clientes
- Criação de orçamentos vinculando produtos, quantidades, margem e desconto por item
- Duplicação de orçamentos
- Controle de acesso por papel: `administrador`, `gestor`, `vendedor`
- Autenticação com bloqueio após tentativas de login inválidas
- Proteção CSRF em todos os formulários

## Stack

- **Backend:** Python 3 + Flask
- **Banco de dados:** SQLite
- **Segurança:** Flask-WTF (CSRF), Werkzeug (hash de senha)

## Como rodar localmente

```bash
# 1. Clonar o repositório
git clone <url-do-repo>
cd priceflow

# 2. Criar e ativar um ambiente virtual
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

# 3. Instalar dependências
pip install -r requirements.txt

# 4. Definir a chave secreta (obrigatório em produção, opcional em dev)
export PRICEFLOW_SECRET_KEY="troque-por-uma-chave-aleatoria"

# 5. Rodar
python priceflow_app.py
```

Acesse `http://127.0.0.1:5000`.

**Login inicial:**
- E-mail: `admin@priceflow.local`
- Senha: `123456` (troque assim que possível em Usuários)

## Variáveis de ambiente

| Variável               | Obrigatória | Descrição                                                                                |
|-------------------------|-------------|--------------------------------------------------------------------------------------------|
| `PRICEFLOW_SECRET_KEY`  | Em produção | Chave usada para assinar a sessão. Sem ela, gera uma aleatória a cada start (dev only).    |
| `PRICEFLOW_DEBUG`       | Não         | `true` para ligar o modo debug do Flask. **Nunca em produção.**                            |

## Estrutura do projeto

```
priceflow/
├── priceflow_app.py     # aplicação Flask (rotas, modelos, templates inline)
├── requirements.txt      # dependências Python
├── priceflow.db           # banco SQLite (gerado automaticamente)
├── AGENTS.md              # padrão de trabalho: Issues, PRs, qualidade, UI
└── README.md
```
