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

**Plataforma:** Google Cloud Platform  
**Status:** ✅ Online e funcional

O backend foi deployado no Google Cloud, utilizando:

- Containerização com Docker
- Banco de dados PostgreSQL gerenciado
- API REST acessível via HTTPS

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
│   Backend (Google Cloud)            │
│   - NestJS API                      │
│   - Docker Container                │
│   - Load Balancer                   │
└──────────────┬──────────────────────┘
               │ TypeORM
               ▼
┌─────────────────────────────────────┐
│   PostgreSQL (Google Cloud SQL)     │
│   - Database Gerenciado             │
│   - Backups Automáticos             │
└─────────────────────────────────────┘
```

## Processo de Deploy

### Frontend (Vercel)

1. **Integração com Git**: Push para branch principal dispara deploy automático
2. **Build**: Vercel executa `npm run build` automaticamente
3. **Deploy**: Build otimizado é distribuído via CDN global
4. **Rollback**: Possibilidade de reverter para versões anteriores

### Backend (Google Cloud)

1. **Build da Imagem Docker**: Criação da imagem containerizada
2. **Push para Container Registry**: Upload da imagem
3. **Deploy no Cloud Run**: Deploy automático ou manual
4. **Configuração de Variáveis**: Variáveis de ambiente configuradas
5. **Health Checks**: Monitoramento automático de saúde da aplicação

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

- Logs de aplicação disponíveis no Google Cloud Console
- Logs de acesso e erros monitorados
- Alertas configurados para problemas críticos

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

- **Backups Automáticos**: Google Cloud SQL realiza backups diários
- **Retenção**: Backups mantidos por período configurado
- **Point-in-Time Recovery**: Possibilidade de restaurar para momento específico

### Código

- **Versionamento**: Código versionado no Git
- **Tags de Release**: Versões marcadas para rollback
- **Documentação**: Documentação versionada junto com código

## Custos

### Vercel (Frontend)

- Plano Hobby: Gratuito para projetos pessoais
- Inclui: 100GB de bandwidth, deploys ilimitados

### Google Cloud (Backend + Database)

- Cloud Run: Cobrança por uso (CPU, memória, requisições)
- Cloud SQL: Cobrança por instância e armazenamento
- Estimativa mensal: Variável conforme uso

## Acesso e Credenciais

### Para Desenvolvedores

- Acesso ao repositório Git para deploy
- Acesso ao Google Cloud Console para gerenciamento
- Acesso ao Vercel Dashboard para frontend

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
