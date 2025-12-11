# Desenvolvimento da Solução

## Aplicação em Produção

A aplicação desenvolvida está publicada e disponível para acesso:

**🌐 Acesse a aplicação:** [https://racha-do-mes-fe.vercel.app/](https://racha-do-mes-fe.vercel.app/)

Todas as funcionalidades descritas abaixo estão implementadas e funcionais na versão em produção.

Para mais detalhes sobre deploy e infraestrutura, consulte: [Deploy e Publicação](deploy-publicacao.md)

---

## Protótipos de Alta Fidelidade

Durante o desenvolvimento do Racha do Mês, foram criadas interfaces funcionais que servem como protótipos de alta fidelidade. As principais telas desenvolvidas incluem:

### Tela de Login e Cadastro

A tela de autenticação permite que usuários façam login com email e senha ou criem uma nova conta. A interface foi desenvolvida com foco em simplicidade e usabilidade.

**Funcionalidades:**

- Validação de campos em tempo real
- Feedback visual de erros
- Redirecionamento automático após login bem-sucedido
- Persistência de sessão através de tokens JWT

---

### Dashboard Principal (Home)

A tela principal oferece uma visão geral das contas do mês atual, permitindo que o usuário navegue entre meses e visualize rapidamente sua situação financeira.

**Componentes principais:**

- **MonthSelector**: Seletor de mês/ano para navegação temporal
- **SummaryCard**: Cards com resumo (Total do Mês, Pendentes, Pagas)
- **BillCard**: Cards individuais para cada conta com informações detalhadas
- **InvitesDropdown**: Dropdown para gerenciar convites pendentes
- **Notificação de Dívidas**: Banner destacando dívidas pendentes

**Funcionalidades:**

- Visualização de todas as contas do mês selecionado
- Indicadores visuais de status (paga/pendente)
- Navegação rápida para outras seções (Dívidas, Créditos)
- Acesso rápido para criar nova conta

---

### Tela de Criação de Conta

Interface para cadastrar novas contas fixas (recorrentes ou parceladas).

**Funcionalidades:**

- Seleção do tipo de conta (Recorrente ou Parcelada)
- Definição de descrição e dia de vencimento
- Adição de participantes com porcentagens de divisão
- Validação automática de que a soma das porcentagens é 100%
- Para contas parceladas: configuração de valor total, número de parcelas e data de início

---

### Tela de Dívidas (Eu Devo)

Lista todas as pessoas que o usuário deve, com valores totais e opção de ver detalhamento.

**Funcionalidades:**

- Lista de credores com valores totais
- Navegação para detalhamento de cada dívida
- Geração de mensagem de cobrança personalizada
- Visualização de histórico de movimentações

---

### Tela de Créditos (Me Deve)

Lista todas as pessoas que devem ao usuário, permitindo gerenciamento e confirmação de pagamentos.

**Funcionalidades:**

- Lista de devedores com valores totais
- Detalhamento de cada dívida com histórico
- Confirmação de pagamentos recebidos
- Tratamento de pagamentos parciais e excessos

---

### Tela de Pagamentos

Interface para registrar pagamentos de contas, incluindo upload de comprovantes.

**Funcionalidades:**

- Seleção da conta e parcela a pagar
- Informação de valor e data do pagamento
- Upload de comprovante (opcional)
- Atualização automática de saldos após registro

---

### Tela de Edição de Valores

Permite ao dono da conta atualizar ou criar valores mensais para contas específicas.

**Funcionalidades:**

- Edição de valor de conta para mês/ano específico
- Criação automática de BillValue se não existir
- Atualização de data de vencimento
- Validação de permissões (apenas dono pode editar)

---

## Estrutura de Componentes Frontend

### Componentes Reutilizáveis

#### BillCard

Componente que exibe informações de uma conta individual, incluindo:

- Descrição da conta
- Valor do usuário e valor total
- Status de pagamento
- Data de vencimento
- Ações (editar, pagar, deletar)

#### SummaryCard

Card de resumo com:

- Label descritivo
- Valor numérico ou monetário
- Variantes visuais (paid/unpaid)

#### MonthSelector

Seletor de mês/ano com:

- Navegação anterior/próximo
- Exibição do mês/ano atual
- Callback para mudanças

#### InvitesDropdown

Dropdown para gerenciar convites:

- Lista de convites pendentes
- Ações de aceitar/rejeitar
- Notificação visual de novos convites

#### CreateBillModal / EditBillValueModal / CreatePaymentModal

Modais reutilizáveis para:

- Criação de contas
- Edição de valores
- Registro de pagamentos

---

## Estrutura de Módulos Backend

### AuthModule

**Responsabilidades:**

- Autenticação de usuários (login)
- Geração e validação de tokens JWT
- Proteção de rotas através de Guards

**Endpoints principais:**

- `POST /auth/register` - Cadastro de novo usuário
- `POST /auth/login` - Login e obtenção de token

---

### UsersModule

**Responsabilidades:**

- Gerenciamento de perfis de usuários
- Consulta de informações de usuários

**Endpoints principais:**

- `GET /users/me` - Obter informações do usuário autenticado
- `GET /users/:id` - Obter informações de um usuário específico

---

### BillsModule

**Responsabilidades:**

- CRUD de contas fixas
- Gerenciamento de participantes e convites
- Gerenciamento de valores mensais (BillValue)

**Endpoints principais:**

- `POST /bills` - Criar nova conta
- `GET /bills/my-bills/monthly` - Listar contas do mês
- `GET /bills/invites/pending` - Listar convites pendentes
- `PATCH /bills/:billId/invite` - Aceitar/rejeitar convite
- `PATCH /bills/:billId/values/:month/:year` - Atualizar valor mensal
- `DELETE /bills/:billId` - Deletar conta

---

### PaymentsModule

**Responsabilidades:**

- Registro de pagamentos
- Upload de comprovantes
- Histórico de pagamentos

**Endpoints principais:**

- `POST /payments` - Registrar pagamento
- `GET /payments` - Listar pagamentos do usuário
- `GET /payments/:id` - Obter detalhes de um pagamento

---

### BalanceModule

**Responsabilidades:**

- Cálculo e consulta de saldos entre usuários
- Gerenciamento de histórico de movimentações
- Geração de mensagens de cobrança
- Confirmação de pagamentos

**Endpoints principais:**

- `GET /balance/my-balance` - Obter saldo do usuário
- `GET /balance/debts` - Listar dívidas do usuário
- `GET /balance/credits` - Listar créditos do usuário
- `GET /balance/debts/:creditorId` - Detalhar dívida com credor específico
- `GET /balance/credits/:debtorId` - Detalhar crédito com devedor específico
- `POST /balance/confirm-payment/:debtorId` - Confirmar pagamento recebido
- `GET /balance/charge-message` - Gerar mensagem de cobrança

---

## Fluxos Principais Implementados

### Fluxo 1: Criação de Conta e Convite

1. Usuário cria uma conta fixa
2. Sistema define o criador como dono e participante
3. Dono adiciona outros participantes com porcentagens
4. Sistema cria registros UserBill com status PENDING
5. Usuários convidados recebem notificação
6. Usuários podem aceitar ou rejeitar convites
7. Sistema atualiza status dos convites

### Fluxo 2: Registro de Valor Mensal e Pagamento

1. Dono da conta registra valor para um mês/ano
2. Sistema cria BillValue se não existir
3. Sistema calcula valor de cada participante baseado na porcentagem
4. Participante registra pagamento
5. Sistema cria registro Payment
6. Sistema atualiza ActualBalance entre pagador e outros participantes
7. Sistema cria registros HistoryBalance para auditoria
8. Sistema atualiza is_paid do BillValue quando todos pagaram

### Fluxo 3: Confirmação de Pagamento e Quitação

1. Credor visualiza lista de devedores
2. Credor acessa detalhamento de uma dívida específica
3. Credor confirma pagamento recebido (total ou parcial)
4. Sistema marca itens do histórico como pagos (do mais antigo)
5. Sistema atualiza ActualBalance (reduz ou remove)
6. Se houver excesso de pagamento, sistema cria dívida invertida
7. Sistema atualiza todos os saldos relacionados

---

## Tecnologias e Bibliotecas Utilizadas

### Frontend

- **React 18**: Biblioteca para construção de interfaces
- **Vite**: Build tool e dev server
- **React Router**: Roteamento de páginas
- **Axios**: Cliente HTTP para chamadas à API
- **CSS Modules**: Estilização com escopo local

### Backend

- **NestJS**: Framework Node.js com TypeScript
- **TypeORM**: ORM para PostgreSQL
- **Passport + JWT**: Autenticação e autorização
- **class-validator**: Validação de DTOs
- **Swagger/OpenAPI**: Documentação da API

### Banco de Dados

- **PostgreSQL**: SGBD relacional
- **TypeORM Migrations**: Controle de versão do schema

---

## Decisões de Design

### 1. Separação entre Bill e BillValue

**Decisão:** Criar entidade separada para valores mensais  
**Justificativa:** Permite que contas tenham valores diferentes a cada mês sem duplicar a estrutura da conta. Facilita consultas por período e histórico.

### 2. ActualBalance vs HistoryBalance

**Decisão:** Manter duas tabelas separadas  
**Justificativa:**

- ActualBalance: Consultas rápidas de saldo atual (otimização)
- HistoryBalance: Auditoria completa e rastreabilidade (compliance)

### 3. Chave Primária Composta em ActualBalance

**Decisão:** Usar (debtor_user_id, borrower_user_id) como chave primária  
**Justificativa:** Garante unicidade do relacionamento entre cada par de usuários e facilita consultas de saldo.

### 4. Status de Convites (PENDING, ACCEPTED, REJECTED)

**Decisão:** Implementar sistema de convites com estados  
**Justificativa:** Permite que usuários decidam se querem participar de uma conta antes de serem incluídos nos cálculos.

### 5. Upload de Comprovantes como Binary

**Decisão:** Armazenar comprovantes como bytea no PostgreSQL  
**Justificativa:** Simplifica a arquitetura evitando serviço de armazenamento separado. Para produção, poderia migrar para S3 ou similar.

---

## Melhorias Futuras de Interface

1. **Dashboard com Gráficos**: Visualização de gastos ao longo do tempo
2. **Notificações Push**: Alertas de vencimento e novos convites
3. **Tema Escuro**: Opção de interface dark mode
4. **Filtros Avançados**: Filtros por tipo de conta, status, período
5. **Exportação de Relatórios**: Geração de PDFs com resumo mensal
6. **Integração com Calendário**: Sincronização de vencimentos
