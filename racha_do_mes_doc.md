# Documentação do Projeto Final - Racha do Mês

**Curso:** Análise e Desenvolvimento de Sistemas  
**Unidade Curricular:** Projeto de Desenvolvimento II  
**Professor:** Luciano Zanuz  
**Ano/Semestre:** 2025/2  
**Participante:** João Luís Rosa de Moura  

---

## Resumo do Projeto

O controle e divisão de despesas compartilhadas atualmente é realizado de forma manual através de planilhas Excel, gerando processos demorados, erros de cálculo e constrangimento social na cobrança entre amigos e familiares. O problema é significativo porque afeta grupos que compartilham despesas fixas regularmente, causando perda de tempo, conflitos interpessoais e falta de transparência financeira. O Racha do Mês é um aplicativo web e mobile que automatiza a divisão de valores, registra pagamentos, gera cobranças personalizadas e organiza o histórico em um dashboard centralizado. A solução elimina a necessidade de planilhas manuais, reduz erros de cálculo e facilita a gestão transparente de finanças coletivas, resultando em economia de tempo e melhoria nas relações interpessoais dos grupos.

## Definição do Problema

### Contexto do Problema

O gerenciamento de despesas compartilhadas é uma necessidade recorrente em diversos contextos sociais, desde repúblicas estudantis até famílias e grupos de amigos que dividem custos fixos como aluguel, contas domésticas e gastos em viagens. Segundo pesquisas sobre gestão financeira pessoal, aproximadamente 67% dos brasileiros enfrentam dificuldades no controle de suas finanças, sendo que 23% desses problemas estão relacionados à divisão de despesas em grupos (FGV, 2023).

### Problemas Identificados

Atualmente, o controle e divisão de despesas compartilhadas é realizado de forma manual através de planilhas Excel, gerando diversos problemas que impactam significativamente a experiência dos usuários:

- **Processo demorado e repetitivo**: Realizado todo início de mês, consumindo tempo valioso dos participantes
- **Dificuldade no acompanhamento**: Débitos acumulados de cada pessoa não são facilmente visualizados
- **Trabalho manual intensivo**: Cálculos manuais para divisão de valores e geração de mensagens de cobrança
- **Alto risco de erros**: Cálculos manuais propensos a falhas humanas
- **Falta de organização**: Ausência de histórico organizado e visualização clara das dívidas
- **Constrangimento social**: Dificuldade e desconforto na hora de cobrar amigos e familiares

### Público-Alvo

O problema afeta diretamente grupos que compartilham despesas fixas como:
- Repúblicas estudantis
- Famílias que dividem custos domésticos
- Grupos de amigos em viagens
- Colegas de trabalho que compartilham aluguel
- Qualquer situação onde múltiplas pessoas precisam dividir custos de forma recorrente

### Projetos Correlatos

| Sistema | Funcionalidades | Diferenciais do Racha do Mês |
|---------|----------------|------------------------------|
| Splitwise | Divisão de despesas, histórico, notificações | Foco em contas fixas recorrentes, templates de cobrança personalizados |
| Tricount | Controle de gastos em grupo, relatórios | Interface mais simples, geração automática de mensagens de cobrança |
| Settle Up | Divisão de contas, múltiplas moedas | Especialização em contas fixas mensais, dashboard otimizado para recorrência |

## Visão do Produto

**Para** pessoas que compartilham despesas fixas (como aluguel, internet, contas domésticas ou entre amigos)  
**Que** hoje perdem tempo com planilhas manuais, cálculos repetitivos e cobranças constrangedoras  
**O Racha do Mês é** um aplicativo web e mobile para gerenciamento de contas compartilhadas  
**Que** automatiza divisão de valores, registra pagamentos, envia cobranças personalizadas e organiza o histórico em um dashboard simples  
**Diferente de** planilhas de Excel e controles manuais,  
**Nosso produto** centraliza tudo em um só lugar, reduz erros, economiza tempo e traz mais transparência às finanças coletivas.

### É, Não é, Faz, Não faz

| **É** | **Não é** | **Faz** | **Não faz** |
|-------|-----------|---------|-------------|
| Um aplicativo web e mobile para controle de despesas compartilhadas | Não é uma planilha manual ou sistema financeiro corporativo | Automatiza cálculos de divisão de despesas entre participantes | Não substitui sistemas contábeis completos |
| Uma solução colaborativa, acessível via celular e computador | Não é exclusivo para uso individual | Gera cobranças automáticas via WhatsApp/Email | Não realiza cobrança direta em meios de pagamento (ex: cartão, Pix) |
| Uma ferramenta para organização centralizada de contas fixas e variáveis | Não é apenas um lembrete de vencimento | Oferece dashboard, relatórios e histórico de pagamentos | Não faz gestão bancária ou integração direta com instituições financeiras |
| Uma forma simples de reduzir conflitos e erros em finanças coletivas | Não é um aplicativo de investimento | Envia alertas e notificações de vencimento | Não gera relatórios fiscais ou declarações de imposto |

## Objetivos

### Objetivo Geral

Desenvolver uma aplicação web e mobile que automatize e simplifique o gerenciamento de despesas compartilhadas, eliminando a necessidade de planilhas manuais e facilitando o processo de divisão e cobrança entre grupos.

### Objetivos Específicos

1. **Automatizar o cadastro de contas fixas**: Permitir o registro de contas recorrentes com definição de participantes e valores
2. **Implementar sistema de registro de pagamentos**: Facilitar a marcação de contas como pagas com controle de quem pagou e quando
3. **Desenvolver cálculo automático de dívidas**: Sistema que calcula automaticamente quanto cada pessoa deve, mantendo histórico
4. **Criar geração de cobranças automáticas**: Desenvolver sistema de mensagens personalizadas para WhatsApp/Email
5. **Implementar dashboard básico**: Fornecer visão geral das contas do mês atual e status de pagamentos
6. **Garantir interface responsiva**: Desenvolver aplicação acessível via web e mobile
7. **Validar a solução**: Testar com usuários reais e coletar feedback para melhorias

## Stack Tecnológico

### Frontend

**React.js com Vite**
- **Justificativa**: React oferece uma biblioteca robusta para desenvolvimento de interfaces de usuário, com grande comunidade e ecossistema. O Vite proporciona desenvolvimento rápido com hot module replacement e build otimizado.
- **Referência**: REACT TEAM. React Documentation. Disponível em: https://react.dev/

**Interface Responsiva**
- **Justificativa**: Necessária para garantir acesso tanto via dispositivos móveis quanto desktop, atendendo às necessidades dos usuários que precisam acessar o sistema em diferentes contextos.

### Backend

**NestJS**
- **Justificativa**: Framework Node.js que oferece arquitetura escalável, decorators para organização do código, injeção de dependências e suporte nativo ao TypeScript, facilitando o desenvolvimento de APIs robustas.
- **Referência**: NESTJS TEAM. NestJS Documentation. Disponível em: https://docs.nestjs.com/

**TypeORM**
- **Justificativa**: ORM (Object-Relational Mapping) que facilita a interação com banco de dados, oferecendo type safety com TypeScript e migrações automáticas.
- **Referência**: TYPEORM TEAM. TypeORM Documentation. Disponível em: https://typeorm.io/

**API RESTful**
- **Justificativa**: Padrão arquitetural que facilita a comunicação entre frontend e backend, oferecendo endpoints bem definidos e seguindo convenções HTTP.

### Banco de Dados

**PostgreSQL**
- **Justificativa**: Sistema gerenciador de banco de dados relacional robusto, com suporte a transações ACID, extensibilidade e performance adequada para aplicações web.
- **Referência**: POSTGRESQL GLOBAL DEVELOPMENT GROUP. PostgreSQL Documentation. Disponível em: https://www.postgresql.org/docs/

### Hospedagem e Deploy

**Vercel (Frontend)**
- **Justificativa**: Plataforma otimizada para aplicações React, oferecendo deploy automático, CDN global e integração nativa com Git.
- **Referência**: VERCEL TEAM. Vercel Documentation. Disponível em: https://vercel.com/docs

**Google Cloud (Backend)**
- **Justificativa**: Infraestrutura escalável e confiável, com suporte a containers Docker e serviços gerenciados.
- **Referência**: GOOGLE CLOUD. Google Cloud Documentation. Disponível em: https://cloud.google.com/docs

**Docker**
- **Justificativa**: Containerização que garante consistência entre ambientes de desenvolvimento e produção, facilitando o deploy e escalabilidade.

### Ferramentas de Desenvolvimento

**Git/GitHub**
- **Justificativa**: Controle de versão essencial para desenvolvimento colaborativo e histórico de mudanças.
- **Referência**: GIT TEAM. Git Documentation. Disponível em: https://git-scm.com/doc

## Descrição da Solução

O Racha do Mês é uma aplicação web e mobile desenvolvida para resolver os problemas de gerenciamento de despesas compartilhadas através de uma solução integrada e automatizada. A aplicação centraliza todas as funcionalidades necessárias para o controle eficiente de contas fixas em um ambiente único e acessível.

### Funcionalidades do MVP

#### 1. Cadastro de Contas Fixas
- Registro de contas recorrentes (aluguel, luz, internet, etc.)
- Definição de participantes e porcentagem/valor de cada um
- Configuração de datas de vencimento
- Sistema mantém registro detalhado de todas as contas

#### 2. Registro de Pagamentos
- Marcação de contas como pagas
- Controle de quem pagou e quando
- Histórico completo de transações

#### 3. Cálculo Automático de Dívidas
- Sistema calcula automaticamente quanto cada pessoa deve
- Manutenção de histórico de dívidas e pagamentos
- Atualização em tempo real dos valores

#### 4. Geração de Cobranças Automáticas
- Criação de mensagens personalizadas para WhatsApp/Email
- Templates de mensagem configuráveis
- Inclusão de informações detalhadas sobre valores devidos, datas de vencimento e histórico

#### 5. Dashboard Básico
- Visão geral das contas do mês atual
- Status de pagamentos por participante
- Valores pendentes e histórico de transações

### Características Técnicas

A solução funciona através de um sistema modular que permite aos usuários cadastrar contas fixas recorrentes, definindo participantes e suas respectivas porcentagens ou valores fixos. Quando uma conta é marcada como paga, o sistema automaticamente calcula as dívidas de cada participante, mantendo um histórico completo de transações.

O sistema implementa mecanismos de segurança através de autenticação de usuários e controle de acesso, garantindo que apenas participantes autorizados possam visualizar e modificar informações do grupo. A arquitetura modular permite futuras expansões, como integração com sistemas bancários ou notificações push.

### Funcionalidades Fora do Escopo do MVP

- Relatórios avançados com gráficos
- Notificações push
- Integração bancária direta
- Sistema de lembretes automáticos

## Arquitetura

O projeto está organizado em um repositório GitHub que contém todos os artefatos gerados durante o desenvolvimento. A arquitetura segue o padrão de separação de responsabilidades, com camadas bem definidas para frontend, backend e banco de dados.

### Visão Geral da Arquitetura

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Backend      │    │  Banco de Dados │
│   (React + Vite)│◄──►│   (NestJS)      │◄──►│  (PostgreSQL)   │
│                 │    │                 │    │                 │
│ - Interface     │    │ - API REST      │    │ - Usuários      │
│ - Componentes   │    │ - Controllers   │    │ - Contas        │
│ - Estados       │    │ - Services      │    │ - Pagamentos    │
│ - Roteamento    │    │ - Entities      │    │ - Histórico     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Artefatos Desenvolvidos

1. **Modelagem de Dados**
   - Diagrama ER do banco de dados
   - Esquemas de entidades (User, ContaFixa, Pagamento, Participante)

2. **Documentação de Requisitos**
   - Histórias de usuário detalhadas
   - Casos de uso principais
   - Backlog do produto

3. **Protótipos de Interface**
   - Wireframes de baixa fidelidade
   - Mockups das principais telas
   - Fluxo de navegação

4. **Documentação Técnica**
   - Arquitetura do sistema
   - Documentação da API REST
   - Guia de instalação e configuração

5. **Plano de Testes**
   - Estratégia de testes unitários
   - Casos de teste de integração
   - Plano de testes de usabilidade

**Repositório do Projeto**: [Link para o repositório GitHub]

## Cronograma de Desenvolvimento

| **Data** | **Atividades da disciplina** | **Atividades do projeto** |
|----------|------------------------------|---------------------------|
| 05/09 | **Entrega 1: Definição do projeto** | • Definição do escopo e tecnologias<br>• Criação do repositório no GitHub<br>• Montagem do ambiente de desenvolvimento |
| 12/09 | Mentoria | • Levantamento detalhado de requisitos<br>• Criação dos wireframes básicos<br>• Definição da arquitetura do sistema |
| 19/09 | Mentoria | • Modelagem do banco de dados<br>• Configuração inicial do projeto backend (NestJS)<br>• Setup do projeto frontend (React + Vite) |
| 26/09 | Mentoria | • Desenvolvimento da API - Módulo de usuários<br>• Desenvolvimento da API - Cadastro de contas<br>• Criação das primeiras telas do frontend |
| 03/10 | **Entrega 2: Documentação parcial do projeto** | • Tela de login/cadastro de usuário<br>• Tela de cadastro de contas fixas<br>• Integração frontend-backend (autenticação) |
| 10/10 | **Apresentações do seminário de andamento** | • Desenvolvimento - Módulo de participantes<br>• Tela de definição de divisão de valores<br>• Preparação da apresentação de andamento |
| 17/10 | **Apresentações do seminário de andamento** | • Desenvolvimento - Registro de pagamentos<br>• Tela de controle de pagamentos<br>• Refinamentos baseados no feedback da apresentação |
| 24/10 | Mentoria | • Desenvolvimento - Cálculo automático de dívidas<br>• Tela de resumo/dashboard básico<br>• Implementação da lógica de divisão |
| 31/10 | Mentoria | • Desenvolvimento - Geração de mensagens<br>• Tela de geração de cobranças<br>• Templates de mensagens (WhatsApp/Email) |
| 07/11 | Mentoria | • Integração completa frontend-backend<br>• Testes de funcionalidades principais<br>• Correção de bugs identificados |
| 14/11 | Mentoria | • Implementação de melhorias de UX/UI<br>• Testes de usabilidade<br>• Preparação do ambiente de produção |
| 21/11 | **Entrega 3: Documentação final do projeto** | • Deploy da aplicação (Vercel + Google Cloud)<br>• Documentação técnica completa<br>• Testes finais e validação |
| 28/11 | Mentoria | • Preparação da apresentação final<br>• Criação de demo com dados de teste<br>• Ajustes finais baseados na documentação |
| 05/12 | **Apresentação final do projeto** | • Apresentação do projeto completo<br>• Demonstração ao vivo do MVP<br>• Coleta de feedback final |
| 12/12 | **Apresentação final do projeto** | • Apresentações finais (se necessário)<br>• Entrega final do código e documentação<br>• Retrospectiva do projeto |

**Tempo estimado de desenvolvimento:** 6-8 semanas

## Validação

### Estratégia

A validação do sistema será realizada através de uma abordagem mista, combinando testes de usabilidade com simulação de cenários reais. A estratégia inclui:

1. **Testes de Usabilidade**: Realizados com 10 usuários representativos do público-alvo (estudantes, jovens profissionais, pessoas que dividem despesas)
2. **Simulação de Cenários**: Teste com dados reais de grupos que atualmente usam planilhas Excel
3. **Métricas de Performance**: Medição de tempo para completar tarefas principais
4. **Questionário de Satisfação**: Avaliação da experiência do usuário e facilidade de uso

### Contexto de Validação

- **Perfil dos Usuários**: Pessoas entre 18-35 anos que compartilham despesas fixas
- **Momento da Validação**: Após implementação das funcionalidades principais (semana 8)
- **Duração**: 2 semanas de testes com acompanhamento semanal
- **Ferramentas**: Google Forms para questionários, Google Analytics para métricas de uso

### Consolidação dos Dados Coletados

Os resultados serão apresentados através de:
- Gráficos de tempo médio para completar tarefas
- Percentual de satisfação dos usuários
- Análise comparativa entre método manual vs. sistema automatizado
- Identificação de pontos de melhoria baseados no feedback

## Benefícios Esperados

- Economia de tempo no controle mensal de contas
- Redução de erros nos cálculos
- Facilidade na cobrança de valores devidos
- Organização centralizada das finanças compartilhadas
- Acesso remoto via celular ou computador
- Melhoria na transparência das finanças coletivas
- Redução de conflitos interpessoais relacionados a dinheiro

## Limitações do Projeto e Perspectivas Futuras

### Limitações Identificadas

1. **Escopo do MVP**: Funcionalidades avançadas como relatórios com gráficos e notificações push foram excluídas do escopo inicial
2. **Integração Bancária**: Não há integração direta com instituições financeiras para pagamentos automáticos
3. **Multiplicidade de Moedas**: Suporte limitado a uma única moeda (Real brasileiro)
4. **Notificações**: Sistema de notificações básico, sem push notifications nativas

### Perspectivas Futuras

1. **Expansão de Funcionalidades**
   - Implementação de relatórios avançados com gráficos e análises
   - Sistema de notificações push para lembretes automáticos
   - Integração com APIs bancárias para pagamentos diretos

2. **Melhorias Técnicas**
   - Implementação de Progressive Web App (PWA)
   - Otimização de performance para grandes volumes de dados
   - Sistema de backup e sincronização em tempo real

3. **Expansão de Mercado**
   - Suporte a múltiplas moedas para usuários internacionais
   - Versão para pequenas empresas e condomínios
   - Integração com sistemas de gestão financeira existentes

4. **Recursos Avançados**
   - Inteligência artificial para sugestões de divisão otimizada
   - Sistema de pontuação de confiabilidade entre usuários
   - Marketplace de serviços relacionados a gestão financeira

## Conclusões

O projeto Racha do Mês representa uma solução inovadora para um problema recorrente na vida de muitos brasileiros. Através da automatização do processo de divisão de despesas compartilhadas, a aplicação elimina os principais pontos de dor identificados: processos manuais demorados, erros de cálculo e constrangimento social na cobrança.

A implementação das funcionalidades principais - cadastro de contas fixas, registro de pagamentos, cálculo automático de dívidas e geração de cobranças - atende diretamente aos objetivos estabelecidos. A escolha da stack tecnológica (React, NestJS, PostgreSQL) proporciona uma base sólida e escalável para o desenvolvimento.

Os resultados esperados incluem economia significativa de tempo no controle mensal de contas, redução de erros nos cálculos e melhoria na transparência das finanças coletivas. A interface responsiva garante acessibilidade tanto via dispositivos móveis quanto desktop, atendendo às necessidades dos usuários em diferentes contextos.

A validação com usuários reais permitirá identificar pontos de melhoria e confirmar a eficácia da solução proposta, contribuindo para o sucesso do projeto e sua aplicabilidade prática.

## Referências Bibliográficas

GOOGLE CLOUD. Google Cloud Documentation. Disponível em: https://cloud.google.com/docs.

NESTJS TEAM. NestJS Documentation. Disponível em: https://docs.nestjs.com/.

POSTGRESQL GLOBAL DEVELOPMENT GROUP. PostgreSQL Documentation. Disponível em: https://www.postgresql.org/docs/.

REACT TEAM. React Documentation. Disponível em: https://react.dev/.

TYPEORM TEAM. TypeORM Documentation. Disponível em: https://typeorm.io/.

VERCEL TEAM. Vercel Documentation. Disponível em: https://vercel.com/docs.
