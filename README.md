# 🍕 Pizzaria Leo - Sistema de Gerenciamento de Pedidos

## 📋 Índice
- [Visão Geral](#visão-geral)
- [Objetivos do Projeto](#objetivos-do-projeto)
- [Funcionalidades](#funcionalidades)
- [Requisitos](#requisitos)
- [Instalação](#instalação)
- [Estrutura do Banco de Dados](#estrutura-do-banco-de-dados)
- [Como Usar](#como-usar)
- [Documentação das Funções](#documentação-das-funções)

---

## 🎯 Visão Geral

**Pizzaria Leo** é um sistema de gerenciamento de pedidos desenvolvido em Python como trabalho acadêmico de Fundamentos em Python. O sistema permite que clientes façam pedidos de pizzas personalizadas através de um menu interativo, enquanto funcionários podem gerenciar e acompanhar esses pedidos.

### Tipo de Projeto
- **Linguagem:** Python 3.8+
- **Banco de Dados:** PostgreSQL
- **Tipo:** Aplicação Console/CLI
- **Contexto:** Trabalho Acadêmico - Fundamentos em Python

---

## 🎓 Objetivos do Projeto

1. **Praticar Conceitos Fundamentais de Python:**
   - Funções e variáveis globais
   - Dicionários e listas
   - Estruturas de controle (if/elif/else, while, match)
   - Entrada/Saída de dados

2. **Integração com Banco de Dados:**
   - Conexão com PostgreSQL via `psycopg2`
   - Operações CRUD (Create, Read, Update, Delete)
   - Transações e cursores

3. **Autenticação e Segurança:**
   - Sistema de login para clientes e funcionários
   - Cadastro de novos usuários
   - Diferenciação de tipos de usuário

4. **Lógica de Negócio:**
   - Cálculo de preços dinâmico
   - Gerenciamento de pedidos
   - Rastreamento de status de entrega

---

## ✨ Funcionalidades

### 🔐 Sistema de Autenticação
- **Login:** Clientes e funcionários fazem login com email e senha
- **Cadastro:** Novos usuários podem se registrar no sistema
- **Dois tipos de usuário:**
  - **Cliente:** Faz pedidos de pizzas
  - **Funcionário:** Gerencia e acompanha pedidos

### 🍔 Criar Pedido
- Selecionar tamanho da pizza (Pequena, Média, Grande)
- Escolher até 3 recheios
- Adicionar complementos opcionais
- Atualizar pedido antes de finalizar
- Escolher entre Retirada ou Entrega
- Inserir dados do cliente (nome, telefone, email, endereço se entrega)
- **Cálculo automático de valores**

### 📊 Listar Pedidos
- Visualizar todos os pedidos registrados no banco
- Informações exibidas:
  - ID do pedido
  - Tipo de pizza
  - Status atual
  - Nome do cliente
  - Telefone
  - Valor total em R$

### 🔍 Buscar Pedido
- Pesquisar pedido específico por ID
- Exibe todas as informações completas do pedido

### ✏️ Editar Pedido
- Atualizar status do pedido (Pendente → Pronto → A caminho → Entregue)
- Editar dados do cliente (nome, telefone, email, endereço)

### 🗑️ Deletar Pedido
- Remover pedido do banco de dados

### 💰 Sistema de Preços

#### Pizzas
- Pequena: R$ 50,00
- Média: R$ 70,00
- Grande: R$ 90,00

#### Recheios (adicionar até 3)
- Calabresa: R$ 10,00
- Frango: R$ 12,00
- Queijo: R$ 8,00
- Pepperoni: R$ 15,00
- Bacon: R$ 14,00
- Atum: R$ 13,00
- Legumes: R$ 9,00

#### Complementos (opcionais)
- Borda Recheada: R$ 10,00
- Refrigerante: R$ 5,00
- Sobremesa: R$ 15,00
- Molho Extra: R$ 7,00
- Queijo Extra: R$ 8,00
- Calabresa Extra: R$ 9,00
- Azeitona Extra: R$ 6,00

---

## 📋 Requisitos

### Sistema
- Python 3.8+
- PostgreSQL 10+

### Dependências Python
```
psycopg2-binary==2.9.x
python-dotenv==0.x
```

### Arquivo de Configuração
Crie um arquivo `.env` na raiz do projeto:
```env
ENV_DB_USER=seu_usuario
ENV_DB_PASSWORD=sua_senha
ENV_DB_HOST=localhost
ENV_DB_PORT=5432
ENV_DB_NAME=pizzaria_leo
```

---

## 🚀 Instalação

### 1. Clonar/Preparar o Projeto
```bash
cd /Users/leonardopires/Workspace/Projects/university/FEP\ -\ Job/
```

### 2. Instalar Dependências
```bash
pip install psycopg2-binary python-dotenv
```

### 3. Criar Banco de Dados
```bash
psycopg2 -U seu_usuario -d seu_banco -f database_schema.sql
```

### 4. Configurar Variáveis de Ambiente
Crie arquivo `.env` com suas credenciais de banco

### 5. Executar o Sistema
```bash
python app.ipynb
```

---

## 🗄️ Estrutura do Banco de Dados

### Tabela: `users_client`
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | Identificador único |
| nome | VARCHAR(100) | Nome do cliente |
| email | VARCHAR(100) UNIQUE | Email único |
| senha | VARCHAR(100) | Senha de acesso |
| data_criacao | TIMESTAMP | Data de cadastro |

### Tabela: `users_employee`
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | Identificador único |
| nome | VARCHAR(100) | Nome do funcionário |
| email | VARCHAR(100) UNIQUE | Email único |
| senha | VARCHAR(100) | Senha de acesso |
| data_criacao | TIMESTAMP | Data de cadastro |

### Tabela: `orders`
| Coluna | Tipo | Descrição |
|--------|------|-----------|
| id | SERIAL PK | ID do pedido |
| pizza | VARCHAR(50) | Tamanho da pizza |
| status | VARCHAR(100) | Status atual do pedido |
| recheios | TEXT[] | Array de recheios |
| complementos | TEXT[] | Array de complementos |
| nome_cliente | VARCHAR(100) | Nome do cliente |
| telefone | VARCHAR(20) | Telefone para contato |
| email | VARCHAR(100) | Email do cliente |
| endereco | VARCHAR(255) | Endereço para entrega |
| total | DECIMAL(10,2) | Valor total do pedido |
| id_cliente | INTEGER FK | ID do cliente (referência) |
| data_criacao | TIMESTAMP | Data do pedido |

---

## 💻 Como Usar

### Fluxo de Cliente

1. **Iniciar Aplicação**
   ```
   ====== Pizzaria Leo ======
   ```

2. **Login/Cadastro**
   - Responda se já tem conta (s/n)
   - Se não, será feito cadastro automático
   - Informar tipo de usuário (c/f)
   - Inserir email e senha

3. **Menu Principal**
   ```
   1. Fazer Pedido
   2. Listar Pedidos
   3. Buscar Pedido
   4. Editar Pedido
   5. Remover Pedido
   6. Sair
   ```

4. **Fazer Pedido**
   - Escolher tamanho da pizza (1-3)
   - Escolher recheios (máximo 3)
   - Escolher complementos
   - Revisar e confirmar
   - Escolher retirada ou entrega
   - Inserir dados de contato
   - Pedido salvo com ID único

5. **Gerenciar Pedidos**
   - Listar: Ver todos os pedidos
   - Buscar: Encontrar pedido específico
   - Editar: Atualizar status ou dados
   - Deletar: Remover pedido

---

## 🔧 Documentação das Funções

### Autenticação

#### `login(id_employee, id_cliente)`
Realiza login de clientes ou funcionários no sistema.

```python
def login(id_employee, id_cliente):
    """
    Parâmetros:
        id_employee: ID do funcionário (global)
        id_cliente: ID do cliente (global)
    
    Retorna:
        "client" - login bem-sucedido como cliente
        "employee" - login bem-sucedido como funcionário
        None - credenciais incorretas
    """
```

#### `user_cadaster()`
Cadastra novo usuário (cliente ou funcionário).

```python
def user_cadaster():
    """
    Solicita informações do usuário e insere no banco.
    Define automaticamente tabela baseado na resposta.
    """
```

### Gerenciamento de Pedidos

#### `create_order(order_list)`
Inicia novo pedido solicitando tamanho da pizza.

```python
def create_order(order_list):
    """
    Parâmetros:
        order_list: Dicionário do pedido (modificado in-place)
    """
```

#### `add_filling(order_list)`
Gerencia seleção de recheios (máximo 3).

#### `add_complement(order_list)`
Gerencia seleção de complementos opcionais.

#### `checkout_order(order_list)`
Finaliza pedido com opção de atualizar antes.

#### `save_order(order_list)`
Salva pedido no banco de dados com total calculado.

#### `list_orders_db()`
Exibe lista de todos os pedidos.

#### `search_order_db()`
Busca pedido específico por ID.

#### `edit_order_db()`
Permite editar status ou dados do cliente.

#### `delete_order_db()`
Remove pedido do banco.

### Cálculos

#### `calculate_order_total(order_list)`
Calcula valor total do pedido automáticamente.

```python
def calculate_order_total(order_list):
    """
    Retorna:
        float: Total em reais (R$)
    
    Fórmula:
        Total = Preço Pizza + (Preços Recheios) + (Preços Complementos)
    """
```

### Coleta de Dados

#### `collect_customer_data(order_list)`
Coleta informações do cliente (nome, telefone, email, endereço).

---

## 📊 Fluxograma do Sistema

```
INICIAR
  ↓
LOGIN/CADASTRO
  ↓
MENU PRINCIPAL
  ├─→ FAZER PEDIDO
  │   ├─→ Escolher Pizza
  │   ├─→ Escolher Recheios
  │   ├─→ Escolher Complementos
  │   ├─→ Revisar Pedido
  │   ├─→ Escolher Entrega/Retirada
  │   ├─→ Inserir Dados Cliente
  │   ├─→ SALVAR (Total Calculado)
  │   └─→ MENU PRINCIPAL
  │
  ├─→ LISTAR PEDIDOS → Exibir Todos → MENU PRINCIPAL
  │
  ├─→ BUSCAR PEDIDO → ID → Exibir Dados → MENU PRINCIPAL
  │
  ├─→ EDITAR PEDIDO
  │   ├─→ Buscar por ID
  │   ├─→ Escolher Campo (Status/Dados)
  │   ├─→ ATUALIZAR
  │   └─→ MENU PRINCIPAL
  │
  ├─→ REMOVER PEDIDO → ID → DELETAR → MENU PRINCIPAL
  │
  └─→ SAIR
      ↓
      FIM
```

---

## 🐛 Tratamento de Erros

O sistema trata os seguintes casos:

- ✅ Entrada inválida do usuário
- ✅ Credentials incorretas no login
- ✅ Pedido não encontrado
- ✅ Email duplicado em cadastro
- ✅ Conexão com banco de dados

---

## 🎨 Features Principais

| Feature | Status | Descrição |
|---------|--------|-----------|
| Autenticação | ✅ | Login/Cadastro de clientes e funcionários |
| Criar Pedido | ✅ | Montagem customizável de pizzas |
| Cálculo de Preço | ✅ | Cálculo automático e dinâmico |
| Dados Cliente | ✅ | Coleta completa de informações |
| Editar Pedido | ✅ | Atualizar status e dados |
| Buscar Pedido | ✅ | Consulta por ID |
| Listar Pedidos | ✅ | Visualizar todos os pedidos |
| Deletar Pedido | ✅ | Remover pedidos |

---

## 📝 Exemplo de Fluxo Completo

```
1. Sistema inicia
2. Usuário faz login (ou cadastra)
3. Menu aparece
4. Usuário escolhe "1 - Fazer Pedido"
5. Sistema exibe catálogo
6. Usuário escolhe Pizza Média (2)
7. Sistema pede recheios - usuário escolhe 3
8. Sistema pede complementos - usuário escolhe 2
9. Sistema calcula total: R$ 70,00 + R$ 30,00 + R$ 15,00 = R$ 115,00
10. Usuário confirma pedido
11. Usuário escolhe Entrega (2)
12. Sistema pede dados do cliente
13. Pedido salvo com ID #1
14. Volta ao menu
15. Usuário pode listar, buscar ou editar
16. Usuário escolhe "6 - Sair"
7. Sistema encerra
```

---

## 👨🏾‍💻 Autor

**Leonardo Pires**  
Trabalho de: Fundamentos em Python  
Data: Abril de 2026

---

**© 2026 - Pizzaria Leo. Todos os direitos reservados.** 🍕
