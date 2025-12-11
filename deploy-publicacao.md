# Deploy e Publicação

## Aplicação em Produção

O Racha do Mês está publicado e disponível para uso em produção através das seguintes URLs:

### Frontend (React + Vite)

**URL de Produção:** https://racha-do-mes-fe.vercel.app/

**Plataforma:** Vercel  
**Status:** ✅ Online e funcional

O frontend foi deployado na Vercel, aproveitando:

- Deploy automático via integração com Git
- CDN global para performance otimizada
- SSL/HTTPS automático
- Build otimizado do Vite

---

### Backend (NestJS)

**Plataforma:** Vercel  
**Status:** ✅ Online e funcional

O backend foi deployado na Vercel como Serverless Functions, aproveitando:

- Deploy automático via integração com Git
- Serverless Functions para API REST
- SSL/HTTPS automático
- Escalabilidade automática
- Integração nativa com frontend

---

### Banco de Dados (PostgreSQL)

**Plataforma:** Supabase  
**Status:** ✅ Online e funcional

O banco de dados PostgreSQL está hospedado no Supabase, oferecendo:

- PostgreSQL gerenciado e otimizado
- Backups automáticos
- Interface de gerenciamento web
- Conexão segura via SSL
- Pool de conexões otimizado

---

## Arquitetura de Deploy

```
┌─────────────────────────────────────┐
│   Usuários / Navegadores            │
└──────────────┬──────────────────────┘
               │ HTTPS
               ▼
┌─────────────────────────────────────┐
│   Frontend (Vercel)                 │
│   https://racha-do-mes-fe.vercel.app│
│   - React + Vite                    │
│   - CDN Global                      │
│   - SSL Automático                  │
└──────────────┬──────────────────────┘
               │ API REST (HTTPS)
               ▼
┌─────────────────────────────────────┐
│   Backend (Vercel Serverless)       │
│   - NestJS API                      │
│   - Serverless Functions            │
│   - Auto-scaling                    │
└──────────────┬──────────────────────┘
               │ TypeORM (SSL)
               ▼
┌─────────────────────────────────────┐
│   PostgreSQL (Supabase)             │
│   - Database Gerenciado             │
│   - Backups Automáticos             │
│   - Connection Pooling              │
└─────────────────────────────────────┘
```

## Processo de Deploy

### Frontend (Vercel)

1. **Integração com Git**: Push para branch principal dispara deploy automático
2. **Build**: Vercel executa `npm run build` automaticamente
3. **Deploy**: Build otimizado é distribuído via CDN global
4. **Rollback**: Possibilidade de reverter para versões anteriores

### Backend (Vercel)

1. **Integração com Git**: Push para branch principal dispara deploy automático
2. **Build**: Vercel detecta projeto NestJS e executa build automaticamente
3. **Serverless Functions**: API é convertida em Serverless Functions
4. **Deploy**: Funções são distribuídas globalmente
5. **Configuração de Variáveis**: Variáveis de ambiente configuradas no dashboard
6. **Rollback**: Possibilidade de reverter para versões anteriores

### Banco de Dados (Supabase)

1. **Criação do Projeto**: Projeto criado no Supabase
2. **Configuração do PostgreSQL**: Banco de dados PostgreSQL provisionado
3. **Migrações**: Schema aplicado através de migrações TypeORM
4. **Configuração de Conexão**: String de conexão configurada no backend
5. **Backups Automáticos**: Supabase realiza backups automáticos diários

## Variáveis de Ambiente

### Frontend

- `VITE_API_URL`: URL da API backend
- Configurações de ambiente para diferentes ambientes (dev, staging, prod)

### Backend

- `DB_HOST`: Host do banco de dados PostgreSQL
- `DB_PORT`: Porta do banco de dados
- `DB_USERNAME`: Usuário do banco de dados
- `DB_PASSWORD`: Senha do banco de dados
- `DB_DATABASE`: Nome do banco de dados
- `JWT_SECRET`: Chave secreta para tokens JWT
- `NODE_ENV`: Ambiente de execução (production)

## Monitoramento

### Métricas Monitoradas

- **Uptime**: Disponibilidade da aplicação
- **Tempo de Resposta**: Latência das requisições
- **Taxa de Erro**: Percentual de requisições com erro
- **Uso de Recursos**: CPU, memória, armazenamento

### Logs

- **Frontend e Backend**: Logs disponíveis no Vercel Dashboard
- **Banco de Dados**: Logs disponíveis no Supabase Dashboard
- Logs de acesso e erros monitorados
- Visualização em tempo real de requisições e erros

## Segurança

### Implementado

- ✅ HTTPS/SSL em todas as conexões
- ✅ Autenticação JWT com tokens seguros
- ✅ Validação de dados de entrada
- ✅ Proteção contra SQL Injection (TypeORM)
- ✅ CORS configurado adequadamente
- ✅ Variáveis sensíveis em variáveis de ambiente

### Melhorias Futuras

- Rate limiting para proteção contra DDoS
- WAF (Web Application Firewall)
- Monitoramento de segurança avançado

## Backup e Recuperação

### Banco de Dados

- **Backups Automáticos**: Supabase realiza backups diários automaticamente
- **Retenção**: Backups mantidos conforme plano do Supabase
- **Point-in-Time Recovery**: Disponível através do Supabase Dashboard
- **Exportação Manual**: Possibilidade de exportar dados via interface web

### Código

- **Versionamento**: Código versionado no Git
- **Tags de Release**: Versões marcadas para rollback
- **Documentação**: Documentação versionada junto com código

## Custos

### Vercel (Frontend + Backend)

- **Plano Hobby**: Gratuito para projetos pessoais
- **Frontend**: 100GB de bandwidth, deploys ilimitados
- **Backend**: Serverless Functions com limite generoso no plano gratuito
- **Inclui**: SSL automático, CDN global, analytics básico

### Supabase (Banco de Dados)

- **Plano Free**: Gratuito com limites generosos
- **Inclui**: 500MB de banco de dados, 2GB de bandwidth
- **Recursos**: Backups automáticos, interface web, API REST automática
- **Upgrade**: Planos pagos disponíveis para maior capacidade

## Acesso e Credenciais

### Para Desenvolvedores

- Acesso ao repositório Git para deploy
- Acesso ao Vercel Dashboard para gerenciamento de frontend e backend
- Acesso ao Supabase Dashboard para gerenciamento do banco de dados
- Logs e métricas disponíveis em ambos os dashboards

### Para Usuários Finais

- Acesso público via URL do frontend
- Cadastro e login necessários para uso
- Dados protegidos e privados por usuário

## Status da Aplicação

**Última Atualização:** Novembro 2025  
**Versão:** 1.0.0 (MVP)  
**Status Geral:** ✅ Operacional

---

## Links Úteis

- **Frontend em Produção**: https://racha-do-mes-fe.vercel.app/
- **Documentação da API**: Disponível via Swagger no backend
- **Repositório do Projeto**: [Link do GitHub - se disponível]
