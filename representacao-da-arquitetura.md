# Representação da Arquitetura

## Modelo de Arquitetura

O modelo de arquitetura adotado foi **MVC (Model-View-Controller)** adaptado para uma arquitetura de **camadas** com separação clara entre frontend, backend e banco de dados.

### Visão Geral da Arquitetura

```
┌─────────────────────────────────────────────────────────────┐
│                        Frontend Layer                       │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  React Components (View)                             │   │
│  │  - Pages (Home, Login, CreateBill, etc.)             │   │
│  │  - Components (BillCard, SummaryCard, etc.)          │   │
│  │  - Contexts (AuthContext)                            │   │
│  └──────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Services Layer (Controller Logic)                    │   │
│  │  - API Service (HTTP requests)                       │   │
│  │  - Auth Service                                        │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                            │
                            │ HTTP/REST API
                            │ (JSON)
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                        Backend Layer                        │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Controllers (API Endpoints)                         │   │
│  │  - AuthController, BillsController,                  │   │
│  │    PaymentsController, BalanceController             │   │
│  └──────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Services (Business Logic)                           │   │
│  │  - AuthService, BillsService,                        │   │
│  │    PaymentsService, BalanceService                    │   │
│  └──────────────────────────────────────────────────────┘   │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Entities (Models)                                    │   │
│  │  - User, Bill, Payment, UserBill,                    │   │
│  │    ActualBalance, HistoryBalance, BillValue          │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
                            │
                            │ TypeORM
                            │ (ORM Layer)
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    Database Layer (PostgreSQL)               │
│  ┌──────────────────────────────────────────────────────┐   │
│  │  Tables: users, bills, payments, user_bills,         │   │
│  │          actual_balance, history_balance, bill_values│   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Explicação das Camadas

#### Frontend Layer (React + Vite)
- **View (Componentes React)**: Responsável pela apresentação visual e interação com o usuário
- **Controller Logic (Services)**: Gerencia chamadas à API, estado da aplicação e lógica de apresentação
- **Separação de Responsabilidades**: 
  - Pages: Telas principais da aplicação
  - Components: Componentes reutilizáveis
  - Services: Comunicação com backend
  - Contexts: Gerenciamento de estado global (autenticação)

#### Backend Layer (NestJS)
- **Controllers**: Recebem requisições HTTP, validam dados de entrada e retornam respostas
- **Services**: Contêm a lógica de negócio, processamento de dados e orquestração de operações
- **Entities**: Modelos de dados que representam as tabelas do banco de dados
- **Guards**: Proteção de rotas e autenticação (JWT)
- **DTOs**: Data Transfer Objects para validação e transferência de dados

#### Database Layer (PostgreSQL)
- **Armazenamento Persistente**: Dados relacionados através de chaves estrangeiras
- **Transações ACID**: Garantia de consistência dos dados
- **Índices**: Otimização de consultas frequentes

### Fluxo de Dados

1. **Requisição do Usuário**: Usuário interage com interface React
2. **Chamada à API**: Service do frontend faz requisição HTTP ao backend
3. **Autenticação**: Guard valida token JWT
4. **Processamento**: Controller recebe, valida e delega para Service
5. **Lógica de Negócio**: Service executa regras de negócio e acessa banco via TypeORM
6. **Persistência**: TypeORM executa queries SQL no PostgreSQL
7. **Resposta**: Dados retornam através das camadas até o frontend
8. **Atualização da UI**: React atualiza interface com novos dados

## Visão Lógica

### Diagrama de Classes

```
┌─────────────┐
│    User     │
├─────────────┤
│ + id        │
│ + name      │
│ + email     │
│ + password  │
│ + phone     │
└─────────────┘
      │
      │ 1
      │
      │ *
┌─────────────┐
│  UserBill   │
├─────────────┤
│ + user_id   │
│ + bill_id   │
│ + share_%   │
│ + status    │
└─────────────┘
      │
      │ *
      │
      │ 1
┌─────────────┐
│    Bill     │
├─────────────┤
│ + id        │
│ + descript  │
│ + type      │
│ + owner_id  │
│ + due_day   │
└─────────────┘
      │
      │ 1
      │
      │ *
┌─────────────┐
│  BillValue  │
├─────────────┤
│ + id        │
│ + bill_id   │
│ + month     │
│ + year      │
│ + value     │
│ + due_date  │
│ + is_paid   │
└─────────────┘
      │
      │ 1
      │
      │ *
┌─────────────┐
│  Payment    │
├─────────────┤
│ + id        │
│ + user_id   │
│ + bill_id   │
│ + value     │
│ + payed_at  │
│ + receipt   │
└─────────────┘
      │
      │ *
      │
      │ 1
┌─────────────┐
│ActualBalance│
├─────────────┤
│ + debtor_id │
│ + borrower_id│
│ + value     │
└─────────────┘
      │
      │ *
      │
      │ 1
┌─────────────┐
│HistoryBalance│
├─────────────┤
│ + id        │
│ + debtor_id │
│ + borrower_id│
│ + bill_id   │
│ + value     │
│ + descript  │
│ + is_paid   │
└─────────────┘
```

### Banco de Dados

#### Modelo Entidade-Relacionamento (ER)

O banco de dados foi modelado utilizando TypeORM, seguindo os princípios de normalização e integridade referencial. Abaixo estão os fragmentos das principais entidades:

#### Entidade: User (Usuário)

```typescript
@Entity('users')
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ type: 'varchar', length: 120, nullable: false })
  name: string;

  @Column({ type: 'varchar', length: 30, nullable: true })
  phone_number: string;

  @Column({ type: 'varchar', length: 255, unique: true, nullable: true })
  email: string;

  @Column({ type: 'varchar', length: 255, nullable: false })
  password: string;

  @CreateDateColumn({ type: 'timestamptz' })
  created_at: Date;

  @OneToMany(() => UserBill, (userBill) => userBill.user)
  userBills: UserBill[];

  @OneToMany(() => Payment, (payment) => payment.user)
  payments: Payment[];

  @OneToMany(() => ActualBalance, (balance) => balance.debtorUser)
  debts: ActualBalance[];

  @OneToMany(() => ActualBalance, (balance) => balance.borrowerUser)
  credits: ActualBalance[];
}
```

**Descrição:** Representa os usuários do sistema. Cada usuário pode participar de múltiplas contas, fazer pagamentos e ter dívidas/créditos com outros usuários.

---

#### Entidade: Bill (Conta)

```typescript
@Entity('bills')
export class Bill {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ type: 'text', nullable: false })
  descript: string;

  @Column({
    type: 'enum',
    enum: BillType,
    default: BillType.RECORRENTE,
    nullable: false,
  })
  type: BillType; // RECORRENTE ou PARCELADA

  @Column({ type: 'int', nullable: false })
  owner_id: number;

  @Column({ type: 'int', nullable: false })
  due_day: number; // Dia do mês de vencimento (1-31)

  @Column({ type: 'numeric', precision: 12, scale: 2, nullable: true })
  total_value: number; // Apenas para contas parceladas

  @Column({ type: 'int', nullable: true })
  installments: number; // Apenas para contas parceladas

  @ManyToOne(() => User, { nullable: false })
  @JoinColumn({ name: 'owner_id' })
  owner: User;

  @OneToMany(() => UserBill, (userBill) => userBill.bill, { cascade: true })
  userBills: UserBill[];

  @OneToMany(() => BillValue, (billValue) => billValue.bill, { cascade: true })
  billValues: BillValue[];
}
```

**Descrição:** Representa uma conta fixa (recorrente ou parcelada). Cada conta tem um dono (owner) e pode ter múltiplos participantes através da tabela UserBill.

---

#### Entidade: UserBill (Participação)

```typescript
@Entity('user_bills')
export class UserBill {
  @PrimaryColumn()
  user_id: number;

  @PrimaryColumn()
  bill_id: number;

  @Column({ type: 'numeric', precision: 5, scale: 2, nullable: false })
  share_percentage: number; // Porcentagem de participação (0-100)

  @Column({
    type: 'enum',
    enum: UserBillStatus,
    default: UserBillStatus.PENDING,
    nullable: false,
  })
  status: UserBillStatus; // PENDING, ACCEPTED, REJECTED

  @ManyToOne(() => User, (user) => user.userBills)
  @JoinColumn({ name: 'user_id' })
  user: User;

  @ManyToOne(() => Bill, (bill) => bill.userBills, { onDelete: 'CASCADE' })
  @JoinColumn({ name: 'bill_id' })
  bill: Bill;
}
```

**Descrição:** Tabela de relacionamento muitos-para-muitos entre User e Bill, representando a participação de um usuário em uma conta com sua porcentagem de divisão.

---

#### Entidade: BillValue (Valor Mensal)

```typescript
@Entity('bill_values')
export class BillValue {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ type: 'int', nullable: false })
  bill_id: number;

  @Column({ type: 'int', nullable: false })
  month: number; // Mês (1-12)

  @Column({ type: 'int', nullable: false })
  year: number; // Ano (ex: 2025)

  @Column({ type: 'numeric', precision: 12, scale: 2, nullable: false })
  value: number; // Valor da conta neste mês/ano

  @Column({ type: 'date', nullable: false })
  due_date: Date; // Data de vencimento

  @Column({ type: 'boolean', nullable: false, default: false })
  is_paid: boolean; // Se a conta foi paga

  @ManyToOne(() => Bill, (bill) => bill.billValues, { onDelete: 'CASCADE' })
  @JoinColumn({ name: 'bill_id' })
  bill: Bill;

  @OneToMany(() => Payment, (payment) => payment.billValue)
  payments: Payment[];
}
```

**Descrição:** Representa o valor de uma conta em um mês/ano específico. Permite que contas tenham valores diferentes a cada mês.

---

#### Entidade: Payment (Pagamento)

```typescript
@Entity('payment')
export class Payment {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ type: 'int', nullable: false })
  user_id: number;

  @Column({ type: 'int', nullable: false })
  bill_id: number;

  @Column({ type: 'int', nullable: false })
  bill_value_id: number; // ID da parcela (BillValue)

  @Column({ type: 'numeric', precision: 12, scale: 2, nullable: false })
  payment_value: number;

  @Column({ type: 'timestamptz', nullable: false })
  payed_at: Date;

  @Column({ type: 'bytea', nullable: true })
  receipt_photo: Buffer | null; // Comprovante em formato binário

  @ManyToOne(() => User, (user) => user.payments)
  @JoinColumn({ name: 'user_id' })
  user: User;

  @ManyToOne(() => Bill, (bill) => bill.payments, { onDelete: 'CASCADE' })
  @JoinColumn({ name: 'bill_id' })
  bill: Bill;

  @ManyToOne(() => BillValue, (billValue) => billValue.payments, {
    onDelete: 'CASCADE',
  })
  @JoinColumn({ name: 'bill_value_id' })
  billValue: BillValue;
}
```

**Descrição:** Registra cada pagamento realizado por um usuário para uma conta específica. Permite upload de comprovante.

---

#### Entidade: ActualBalance (Saldo Atual)

```typescript
@Entity('actual_balance')
export class ActualBalance {
  @PrimaryColumn()
  debtor_user_id: number; // Usuário que deve

  @PrimaryColumn()
  borrower_user_id: number; // Usuário que emprestou (credor)

  @Column({ type: 'numeric', precision: 12, scale: 2, nullable: false })
  value: number; // Valor que o devedor deve ao credor

  @ManyToOne(() => User, (user) => user.debts)
  @JoinColumn({ name: 'debtor_user_id' })
  debtorUser: User;

  @ManyToOne(() => User, (user) => user.credits)
  @JoinColumn({ name: 'borrower_user_id' })
  borrowerUser: User;
}
```

**Descrição:** Mantém o saldo atual entre cada par de usuários. Chave primária composta por (debtor_user_id, borrower_user_id). Representa quanto um usuário deve a outro no momento atual.

---

#### Entidade: HistoryBalance (Histórico de Saldos)

```typescript
@Entity('history_balance')
export class HistoryBalance {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ type: 'int', nullable: false })
  debtor_user_id: number;

  @Column({ type: 'int', nullable: false })
  borrower_user_id: number;

  @Column({ type: 'int', nullable: true })
  bill_id: number; // Opcional: relaciona com a conta que gerou a dívida

  @Column({ type: 'text', nullable: false })
  descript: string; // Descrição da movimentação

  @Column({ type: 'numeric', precision: 12, scale: 2, nullable: false })
  value: number; // Valor da movimentação

  @Column({ type: 'boolean', default: false, nullable: false })
  is_paid: boolean; // Se esta movimentação foi paga

  @CreateDateColumn({ type: 'timestamptz' })
  created_at: Date;

  @ManyToOne(() => User, (user) => user.debtHistory)
  @JoinColumn({ name: 'debtor_user_id' })
  debtorUser: User;

  @ManyToOne(() => User, (user) => user.creditHistory)
  @JoinColumn({ name: 'borrower_user_id' })
  borrowerUser: User;

  @ManyToOne(() => Bill, (bill) => bill.historyBalances, {
    nullable: true,
    onDelete: 'CASCADE',
  })
  @JoinColumn({ name: 'bill_id' })
  bill: Bill;
}
```

**Descrição:** Mantém o histórico completo de todas as movimentações financeiras entre usuários. Permite rastreabilidade e auditoria de todas as transações.

---

### Relacionamentos Principais

1. **User ↔ Bill**: Relacionamento muitos-para-muitos através de `UserBill`
   - Um usuário pode participar de múltiplas contas
   - Uma conta pode ter múltiplos participantes

2. **Bill ↔ BillValue**: Relacionamento um-para-muitos
   - Uma conta pode ter múltiplos valores (um para cada mês/ano)
   - Cada BillValue representa a instância da conta em um período específico

3. **BillValue ↔ Payment**: Relacionamento um-para-muitos
   - Um valor de conta pode ter múltiplos pagamentos (se houver divisão entre participantes)
   - Cada pagamento está vinculado a um BillValue específico

4. **User ↔ ActualBalance**: Relacionamento um-para-muitos (bidirecional)
   - Um usuário pode ser devedor em múltiplos saldos
   - Um usuário pode ser credor em múltiplos saldos

5. **User ↔ HistoryBalance**: Relacionamento um-para-muitos (bidirecional)
   - Histórico completo de todas as movimentações envolvendo o usuário

### Índices e Otimizações

- **Índices criados** para melhorar performance:
  - `user_id`, `bill_id`, `payed_at` na tabela `payment`
  - `debtor_user_id`, `borrower_user_id`, `created_at` na tabela `history_balance`
  - `email` único na tabela `users`

### Regras de Negócio Implementadas

1. **Cálculo Automático de Dívidas**: Quando um pagamento é registrado, o sistema:
   - Calcula quanto cada participante deve baseado na porcentagem
   - Atualiza `ActualBalance` entre o pagador e cada participante
   - Cria registros em `HistoryBalance` para auditoria

2. **Confirmação de Pagamento**: Quando um credor confirma um pagamento:
   - Marca itens do histórico como pagos (do mais antigo para o mais recente)
   - Atualiza ou remove `ActualBalance`
   - Trata excessos de pagamento criando dívida invertida

3. **Contas Recorrentes vs Parceladas**:
   - Recorrentes: Valor é informado mês a mês
   - Parceladas: Valor total é dividido em parcelas, criando BillValues automaticamente

