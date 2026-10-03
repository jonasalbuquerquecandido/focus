# AGENTS.md

## Visão geral

Este repositório representa a base inicial do projeto FocusFlow. A implementação funcional ainda não foi iniciada.

Este arquivo é a fonte principal de contexto, regras, arquitetura, padrões e processo para todos os agentes que trabalharem no projeto no futuro.

O objetivo do FocusFlow não é apenas entregar uma aplicação funcional, mas construir um sistema realista de produtividade pessoal com foco em engenharia de software profissional, segurança, dados, observabilidade e evolução técnica.

## 1. Identidade do projeto

Nome: FocusFlow

Objetivo:
- Construir uma aplicação realista de produtividade pessoal para portfólio e laboratório de aprendizado em:
  - Backend Java
  - Spring Boot
  - Banco de dados
  - Engenharia de software
  - Segurança
  - Cloud
  - DevOps
  - Observabilidade
  - System Design
  - Desenvolvimento assistido por IA
- Simular problemas reais de engenharia de sistemas profissionais, inclusive financeiros e corporativos.
- Priorizar qualidade, segurança, testabilidade, compreensão e operabilidade.

## 2. Prioridades

Ordem de prioridade:
1. Backend Java
2. Segurança
3. Banco de dados e integridade
4. Arquitetura e engenharia de software
5. Testes
6. Cloud / DevOps / infraestrutura
7. Observabilidade
8. Frontend

Observação: frontend é secundário e existe apenas para demonstrar e testar a API. Não é objetivo principal do aprendizado.

## 3. Stack

### Backend
- Java 25 LTS
- Spring Boot em versão estável compatível com Java 25
- Spring Web
- Spring Data JPA
- Hibernate
- Spring Security
- Bean Validation
- Maven

### Banco
- PostgreSQL
- Flyway

### Testes
- JUnit
- Mockito
- Spring Boot Test
- Testcontainers quando apropriado

### Infraestrutura
- Git
- GitHub
- Docker
- Docker Compose
- Linux / Ubuntu
- Nginx
- HTTPS / TLS

### Cloud
- AWS posteriormente, quando necessário
- EC2
- RDS
- S3
- IAM
- VPC
- CloudWatch

Não adicionar serviços cloud sem necessidade técnica.

## 4. Java

Java 25 LTS é a versão oficial do projeto.

Regras:
- Não fazer downgrade automático para Java 17 ou outra versão.
- Antes de adicionar ou atualizar Spring Boot ou dependências importantes:
  1. verificar compatibilidade com Java 25;
  2. preferir versões estáveis;
  3. evitar recursos experimentais;
  4. explicar incompatibilidades antes de alterar a versão do Java.

O objetivo é usar Java moderno sem criar dependência desnecessária de recursos específicos que prejudiquem a portabilidade para ambientes corporativos.

## 5. Arquitetura

A arquitetura inicial será:
- Modular Monolith

Não criar microservices sem necessidade técnica concreta.

A estrutura deve separar módulos e responsabilidades com clareza. Os módulos esperados incluem:
- user
- auth
- task
- habit
- goal
- gamification
- finance
- security
- shared

A estrutura pode evoluir conforme o projeto crescer.

Não criar abstrações ou módulos vazios apenas para seguir um padrão.

## 6. API

A API será REST.

Versão inicial:
- /api/v1

Regras:
- usar DTOs;
- validar entradas;
- usar métodos HTTP apropriados;
- usar status codes HTTP adequados;
- ter tratamento global de exceções;
- respostas de erro consistentes;
- paginação quando necessário;
- nunca expor entidades JPA diretamente pela API;
- regra de negócio não deve ficar concentrada em controllers.

## 7. Banco de dados

PostgreSQL é o banco principal.

Flyway é responsável pelas migrations.

Toda alteração estrutural relevante deve ser versionada por migration.

Não usar criação automática destrutiva do schema em ambientes reais.

A integridade dos dados deve ser garantida pela aplicação e pelo banco, quando apropriado.

Considerar:
- NOT NULL
- UNIQUE
- FOREIGN KEY
- CHECK
- índices
- constraints
- transações

## 8. Segurança — Security by Design

Segurança é requisito transversal do projeto.

Não tratar segurança como etapa final.

Considerar desde o início:
- OWASP Top 10
- autenticação
- autorização
- RBAC
- JWT
- refresh tokens quando apropriado
- controle de acesso por recurso
- BOLA / IDOR
- privilege escalation
- validação de entrada
- proteção contra injection
- proteção de dados
- secrets management
- logging seguro
- auditoria
- segurança de dependências
- segurança de containers
- segurança de cloud
- segurança de CI/CD

Nunca armazenar no código ou no Git:
- senhas em texto puro
- secrets hardcoded
- tokens privados
- credenciais AWS
- API keys

## 9. Threat Modeling

Para funcionalidades sensíveis, usar princípios de threat modeling.

Considerar STRIDE quando apropriado.

Perguntas-chave:
- quem pode acessar?
- quem pode alterar?
- que dados podem vazar?
- que ações precisam de auditoria?
- como um usuário pode abusar da funcionalidade?
- o que acontece se uma requisição for repetida?
- o que acontece sob concorrência?

Riscos relevantes devem ser registrados em docs/security.md.

## 10. Autenticação e autorização

A autenticação será baseada em Spring Security.

Considerar:
- senha com hash seguro
- JWT
- access token
- refresh token quando necessário
- expiração
- validação de token
- RBAC
- autorização contextual
- ownership de recursos

Nunca assumir que um usuário autenticado é automaticamente autorizado a acessar qualquer recurso.

Exemplo:
- GET /api/v1/tasks/{id} deve passar por verificação de autorização e ownership.

## 11. Módulo financeiro

O módulo financeiro deve simular problemas reais de sistemas transacionais.

Entidades possíveis:
- Account
- Transaction
- Category
- Budget
- Statement

Considerar:
- ACID
- transactions
- isolation
- concorrência
- locking
- optimistic locking
- pessimistic locking quando necessário
- constraints
- idempotência
- consistência
- auditoria

Operações financeiras não devem ser tratadas como simples CRUD.

## 12. Idempotência

Operações críticas, especialmente financeiras, devem considerar idempotência.

Exemplo:
- Idempotency-Key

A mesma operação repetida não deve produzir efeitos duplicados.

A implementação deve considerar concorrência e persistência da chave de idempotência quando necessário.

## 13. Auditoria e logs

Diferenciar:

### Application logs
Para funcionamento, diagnóstico e troubleshooting.

### Audit logs
Para eventos relevantes de segurança e negócio.

Exemplos:
- login
- falha de autenticação
- alteração de senha
- alteração de permissões
- operações financeiras
- alterações sensíveis

Nunca registrar:
- senhas
- tokens completos
- secrets
- dados sensíveis desnecessários

## 14. Testes

Funcionalidades relevantes devem possuir testes.

Prioridade:
1. regras de negócio
2. segurança
3. endpoints críticos
4. persistência
5. integração

Considerar:
- unit tests
- integration tests
- API tests
- Testcontainers

Não criar testes apenas para aumentar cobertura. Testes devem validar comportamento real.

Criar testes para cenários de segurança relevantes, incluindo:
- usuário não autenticado
- usuário sem autorização
- acesso a recurso de outro usuário
- token inválido
- token expirado
- role insuficiente
- entradas inválidas
- duplicação de operações
- concorrência quando relevante

## 15. Frontend

Frontend é secundário.

Não é objetivo transformar o usuário em frontend developer.

O frontend deve ser:
- simples
- funcional
- mínimo
- suficiente para consumir a API
- suficiente para demonstrar autenticação
- suficiente para testar os principais fluxos

Evitar investimento desnecessário em:
- CSS avançado
- animações
- design system complexo
- UX sofisticada
- arquitetura frontend complexa

A regra crítica deve continuar no backend.

## 16. Docker

Usar Docker para tornar o ambiente reproduzível.

Inicialmente, usar Docker/Compose principalmente para dependências como PostgreSQL.

Documentar comandos necessários para:
- iniciar
- parar
- testar
- executar a aplicação

## 17. Linux

O projeto deve funcionar em Linux/Ubuntu.

Evitar dependências desnecessárias de caminhos ou ferramentas específicas do Windows.

## 18. Cloud

AWS será introduzida posteriormente.

A arquitetura pode evoluir para algo como:
- Internet
- HTTPS / Nginx
- Spring Boot
- PostgreSQL / RDS

Usar IAM e princípio de menor privilégio.

Nunca colocar credenciais AWS no código.

## 19. Observabilidade

Posteriormente implementar:
- logs
- métricas
- health checks
- monitoramento
- alertas quando apropriado

O sistema deve permitir identificar:
- se está funcionando
- onde ocorreu um erro
- quando ocorreu
- qual operação estava sendo executada
- se houve comportamento suspeito

## 20. CI/CD

Posteriormente implementar pipeline contendo, conforme necessário:
- build
- testes
- security checks
- dependency scanning
- SAST
- secret scanning
- DAST quando apropriado
- deploy

Não criar pipeline complexa antes de existir uma aplicação funcional.

## 21. Git

Usar Git com commits pequenos e semânticos.

Preferir:
- feat:
- fix:
- refactor:
- test:
- docs:
- security:
- chore:
- build:
- ci:

Evitar commits gigantes contendo várias funcionalidades não relacionadas.

## 22. Documentação

O projeto deve possuir:
- README.md
- docs/architecture.md
- docs/security.md
- docs/database.md
- docs/api.md
- docs/roadmap.md
- docs/decisions.md

Esses arquivos são documentação técnica persistente do projeto.

Não criar todos antecipadamente sem necessidade. Criar ou atualizar quando houver conteúdo real para documentar.

## 23. Architecture Decision Records (ADR)

Decisões arquiteturais importantes devem ser documentadas.

Registrar:
- contexto
- problema
- decisão
- alternativas
- consequências

Não deixar decisões importantes somente na conversa com a IA.

## 24. Uso de IA

O agente pode:
- implementar código
- criar testes
- refatorar
- investigar erros
- revisar código
- revisar segurança
- criar documentação
- sugerir arquitetura

Porém:
- código gerado pela IA não é automaticamente considerado correto ou seguro.

O objetivo é desenvolver cinco competências:
- BUILD
- UNDERSTAND
- REVIEW
- OPERATE
- PROTECT

O usuário deve conseguir compreender, revisar, executar, corrigir e proteger o sistema.

## 25. Processo obrigatório do agente

Antes de alterar código:
1. ler AGENTS.md;
2. analisar o código existente;
3. verificar documentação relevante;
4. verificar se a funcionalidade já existe;
5. identificar impactos;
6. propor abordagem quando houver decisão relevante;
7. implementar a menor mudança necessária.

Depois:
1. executar testes;
2. verificar erros;
3. revisar segurança;
4. verificar alterações;
5. atualizar documentação quando necessário;
6. explicar o resultado.

Nunca apagar ou substituir trabalho existente sem necessidade.

## 26. Tarefas delimitadas

Preferir tarefas pequenas.

Exemplo:
- "Implemente cadastro de usuários, incluindo DTO, validação, service, repository, migration e testes."

Evitar:
- "Construa todo o sistema."

Cada etapa deve deixar o projeto em estado funcional.

## 27. Dependências

Antes de adicionar uma dependência:
1. verificar se ela já existe;
2. verificar se o Spring/Java já oferece solução adequada;
3. avaliar manutenção;
4. avaliar segurança;
5. avaliar necessidade;
6. considerar impacto arquitetural.

Não adicionar tecnologia só para melhorar currículo.

Kafka, Redis, Kubernetes, microservices e outras tecnologias só devem entrar quando houver problema técnico bem justificado.

## 28. Checkpoint

Após cada etapa significativa, apresentar:

### Implementado
### Arquivos alterados
### Testes executados
### Decisões técnicas
### Riscos de segurança
### Próximo passo

Não avançar automaticamente para uma grande nova funcionalidade.

## 29. Roadmap macro

1. Setup
2. Users
3. Authentication
4. Tasks
5. Habits
6. Goals
7. Gamification
8. Financial Module
9. Testing
10. Security Hardening
11. Docker
12. Linux / Deployment
13. AWS
14. HTTPS / Nginx
15. CI/CD
16. Observability
17. Security Testing
18. AI Features
19. Performance / Scalability
20. Production Hardening

O roadmap pode ser alterado quando houver justificativa técnica.

## 30. Estado atual

FASE ATUAL:
Fase 1 — Setup

STATUS:
Em desenvolvimento

JAVA:
25 LTS

SPRING BOOT:
Versão estável compatível com Java 25

DATABASE:
PostgreSQL

MIGRATIONS:
Flyway

ARCHITECTURE:
Modular Monolith

FRONTEND:
Mínimo / secundário

SECURITY:
Security by Design

CLOUD:
AWS posteriormente

## 31. Regra final

Antes de implementar qualquer funcionalidade, verificar:
1. Isso pertence ao escopo atual?
2. É necessário agora?
3. Existe implementação semelhante?
4. Respeita a arquitetura?
5. É testável?
6. Introduz risco de segurança?
7. Existe solução mais simples?
8. Existe alguma decisão que precisa ser explicada ao usuário?

Priorizar sempre:
- correção → segurança → simplicidade → testabilidade → observabilidade → evolução.

O FocusFlow deve ser desenvolvido como um sistema profissional, mas sem overengineering.

## Instrução final para esta tarefa

Neste momento, NÃO implemente nenhuma funcionalidade nova do FocusFlow.

Faça somente:
1. analisar o repositório existente;
2. criar ou revisar o AGENTS.md;
3. preservar o código existente;
4. mostrar o conteúdo final do AGENTS.md;
5. informar eventuais conflitos entre a estrutura existente e estas regras;
6. aguardar a próxima instrução.

Não iniciar a Fase 1 automaticamente.
