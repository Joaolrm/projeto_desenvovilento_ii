# Planejamento da Release

## Product Backlog

O Product Backlog foi organizado utilizando a técnica de Histórias de Usuário, priorizadas através do método MoSCoW (Must have, Should have, Could have, Won't have) e ordenadas por valor de negócio e dependências técnicas.

### Técnica de Levantamento de Histórias de Usuário

As histórias foram levantadas através de:
1. **Análise do problema**: Identificação das dores dos usuários que utilizam planilhas manuais
2. **Pesquisa com usuários potenciais**: Entrevistas informais com estudantes e pessoas que dividem despesas
3. **Análise de produtos similares**: Estudo de aplicativos como Splitwise, Tricount e Settle Up
4. **Brainstorming de funcionalidades**: Identificação de necessidades não atendidas pelos concorrentes

### Histórias de Usuário - MVP (Must Have)

#### US01 - Autenticação de Usuário
**Como** um usuário  
**Eu quero** criar uma conta e fazer login  
**Para que** eu possa acessar o sistema e gerenciar minhas contas compartilhadas

**Critérios de Aceite:**
- Usuário pode se cadastrar com nome, email e senha
- Usuário pode fazer login com email e senha
- Sistema valida credenciais e mantém sessão autenticada
- Usuário pode fazer logout

**Prioridade:** Alta  
**Estimativa:** 5 pontos

---

#### US02 - Cadastro de Contas Fixas
**Como** um usuário  
**Eu quero** cadastrar contas fixas recorrentes (aluguel, luz, internet, etc.)  
**Para que** o sistema possa calcular automaticamente as divisões mensais

**Critérios de Aceite:**
- Usuário pode criar uma conta com descrição, tipo (recorrente/parcelada) e dia de vencimento
- Usuário pode definir participantes e suas porcentagens de divisão
- Sistema valida que a soma das porcentagens é 100%
- Contas parceladas permitem definir valor total, número de parcelas e data de início

**Prioridade:** Alta  
**Estimativa:** 8 pontos

---

#### US03 - Convite de Participantes
**Como** um dono de conta  
**Eu quero** convidar outros usuários para participar de uma conta  
**Para que** eles possam visualizar e gerenciar suas partes da conta

**Critérios de Aceite:**
- Dono pode convidar usuários por email
- Usuário convidado recebe notificação de convite pendente
- Usuário pode aceitar ou rejeitar convite
- Sistema atualiza status do convite

**Prioridade:** Alta  
**Estimativa:** 5 pontos

---

#### US04 - Registro de Valores Mensais
**Como** um dono de conta  
**Eu quero** registrar o valor da conta para cada mês  
**Para que** o sistema possa calcular quanto cada participante deve pagar

**Critérios de Aceite:**
- Dono pode informar o valor da conta para um mês/ano específico
- Sistema cria automaticamente o registro (BillValue) se não existir
- Sistema calcula automaticamente a parte de cada participante baseado na porcentagem
- Dono pode editar valores já registrados

**Prioridade:** Alta  
**Estimativa:** 5 pontos

---

#### US05 - Registro de Pagamentos
**Como** um usuário  
**Eu quero** registrar quando paguei uma conta  
**Para que** o sistema atualize os saldos e histórico

**Critérios de Aceite:**
- Usuário pode marcar uma conta como paga informando valor e data
- Sistema permite upload de comprovante (opcional)
- Sistema atualiza automaticamente os saldos entre usuários
- Histórico de pagamentos é mantido

**Prioridade:** Alta  
**Estimativa:** 8 pontos

---

#### US06 - Cálculo Automático de Dívidas
**Como** o sistema  
**Eu quero** calcular automaticamente quanto cada pessoa deve  
**Para que** os usuários tenham visibilidade clara de suas obrigações

**Critérios de Aceite:**
- Sistema calcula dívidas quando uma conta é paga
- Sistema mantém saldo atualizado entre cada par de usuários (ActualBalance)
- Sistema registra histórico de movimentações (HistoryBalance)
- Cálculos consideram porcentagens e valores pagos

**Prioridade:** Alta  
**Estimativa:** 13 pontos

---

#### US07 - Visualização de Dívidas e Créditos
**Como** um usuário  
**Eu quero** visualizar minhas dívidas e quem me deve  
**Para que** eu saiba exatamente minha situação financeira

**Critérios de Aceite:**
- Usuário pode ver lista de pessoas que deve (dívidas)
- Usuário pode ver lista de pessoas que devem a ele (créditos)
- Sistema mostra valor total e detalhamento por pessoa
- Usuário pode ver histórico detalhado de cada dívida/crédito

**Prioridade:** Alta  
**Estimativa:** 8 pontos

---

#### US08 - Dashboard Mensal
**Como** um usuário  
**Eu quero** visualizar um resumo das minhas contas do mês  
**Para que** eu tenha uma visão geral rápida da minha situação

**Critérios de Aceite:**
- Dashboard mostra contas do mês atual
- Sistema exibe total do mês, quantidade de contas pagas e pendentes
- Usuário pode navegar entre meses
- Cards mostram informações resumidas de cada conta

**Prioridade:** Alta  
**Estimativa:** 5 pontos

---

#### US09 - Geração de Mensagem de Cobrança
**Como** um usuário  
**Eu quero** gerar uma mensagem personalizada com minhas dívidas  
**Para que** eu possa enviar via WhatsApp ou Email

**Critérios de Aceite:**
- Sistema gera mensagem formatada com todas as dívidas
- Mensagem inclui valores, credores e total a pagar
- Mensagem está formatada para WhatsApp (com emojis)
- Usuário pode copiar mensagem para área de transferência

**Prioridade:** Média  
**Estimativa:** 3 pontos

---

### Histórias de Usuário - Should Have (Futuras)

- **US10**: Notificações push para lembretes de vencimento
- **US11**: Relatórios mensais com gráficos
- **US12**: Exportação de dados para Excel/PDF
- **US13**: Integração com calendário para lembretes
- **US14**: Suporte a múltiplas moedas

## Roadmap

### Sprint 1 (Semanas 1-2) - Fundação
**Objetivo:** Estrutura base do projeto e autenticação

**Sprint Backlog:**
- Setup do projeto backend (NestJS + TypeORM + PostgreSQL)
- Setup do projeto frontend (React + Vite)
- Configuração de ambiente de desenvolvimento
- US01 - Autenticação de Usuário

**Entregáveis:**
- Sistema de autenticação funcional
- Estrutura de banco de dados criada
- Ambiente de desenvolvimento configurado

---

### Sprint 2 (Semanas 3-4) - Gerenciamento de Contas
**Objetivo:** Cadastro e gerenciamento de contas fixas

**Sprint Backlog:**
- US02 - Cadastro de Contas Fixas
- US03 - Convite de Participantes
- US04 - Registro de Valores Mensais
- Interface de cadastro de contas

**Entregáveis:**
- Usuários podem criar contas fixas
- Sistema de convites implementado
- Registro de valores mensais funcional

---

### Sprint 3 (Semanas 5-6) - Sistema de Pagamentos
**Objetivo:** Registro de pagamentos e cálculos automáticos

**Sprint Backlog:**
- US05 - Registro de Pagamentos
- US06 - Cálculo Automático de Dívidas
- Interface de registro de pagamentos
- Upload de comprovantes

**Entregáveis:**
- Sistema de pagamentos funcional
- Cálculos automáticos de dívidas implementados
- Histórico de transações mantido

---

### Sprint 4 (Semanas 7-8) - Visualização e Dashboard
**Objetivo:** Interfaces de visualização e dashboard

**Sprint Backlog:**
- US07 - Visualização de Dívidas e Créditos
- US08 - Dashboard Mensal
- US09 - Geração de Mensagem de Cobrança
- Melhorias de UX/UI

**Entregáveis:**
- Dashboard funcional com resumo mensal
- Páginas de dívidas e créditos
- Geração de mensagens de cobrança

---

### Sprint 5 (Semanas 9-10) - Testes e Deploy
**Objetivo:** Validação e publicação

**Sprint Backlog:**
- Testes de integração
- Testes de usabilidade
- Correção de bugs
- Deploy em produção (Vercel + Supabase)
- Documentação final

**Entregáveis:**
- Aplicação em produção
- Documentação completa
- Relatório de testes

---

## Priorização

As histórias foram priorizadas considerando:
1. **Valor de negócio**: Funcionalidades que resolvem o problema principal primeiro
2. **Dependências técnicas**: Base (autenticação, estrutura) antes de funcionalidades complexas
3. **Risco**: Funcionalidades críticas (cálculos) implementadas cedo para validação
4. **Esforço vs. Valor**: Funcionalidades de alto valor e baixo esforço priorizadas

## Métricas de Sucesso

- **Tempo médio para cadastrar uma conta**: < 2 minutos
- **Tempo médio para registrar um pagamento**: < 30 segundos
- **Precisão dos cálculos**: 100% (sem erros)
- **Taxa de satisfação dos usuários**: > 80%
- **Tempo de resposta da API**: < 500ms (p95)

