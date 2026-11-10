# FocusFlow

**FocusFlow** é uma plataforma de produtividade pessoal em desenvolvimento, projetada para integrar organização de tarefas, hábitos, objetivos, gamificação e, futuramente, recursos inteligentes baseados em inteligência artificial.

O projeto também funciona como um laboratório de engenharia de software, com foco em desenvolvimento Backend Java, arquitetura, segurança, qualidade de código e infraestrutura.

## Status do projeto

**Fase atual:** Fase 1 — Setup e estrutura inicial  
**Status:** Planejada — Não iniciada

O projeto ainda não possui funcionalidades de produto implementadas. A prioridade atual é estabelecer uma base técnica consistente para o desenvolvimento do backend.

## Stack tecnológica

| Tecnologia | Finalidade |
|---|---|
| Java 25 LTS | Linguagem principal |
| Spring Boot | Framework backend |
| Maven | Gerenciamento de dependências e build |
| PostgreSQL | Banco de dados relacional |
| Spring Data JPA / Hibernate | Persistência de dados |
| Flyway | Versionamento de banco de dados |
| JUnit / Mockito | Testes automatizados |
| Docker / Docker Compose | Ambiente de desenvolvimento |

As versões específicas das dependências serão definidas e validadas durante a configuração inicial.

## Arquitetura

O projeto seguirá a arquitetura **Monólito Modular**, mantendo responsabilidades organizadas e separação de domínios dentro de uma única aplicação backend.

A API será organizada sob o prefixo `/api/v1`.

A estrutura será construída progressivamente, evitando abstrações prematuras e módulos sem implementação real.

## Direção do produto

Os principais domínios planejados incluem:

- **Tarefas:** organização e acompanhamento de atividades.
- **Hábitos:** acompanhamento de comportamentos recorrentes.
- **Objetivos:** planejamento e acompanhamento de metas.
- **Gamificação:** progressão, recompensas e indicadores de evolução.
- **Finanças:** organização e acompanhamento financeiro.
- **Inteligência artificial:** assistência e automações inteligentes em etapas futuras.

Esses domínios representam a visão do produto, não funcionalidades já disponíveis.

## Engenharia e qualidade

O desenvolvimento priorizará:

- Princípios SOLID e boas práticas de orientação a objetos.
- Separação de responsabilidades e organização modular.
- APIs REST e validação de dados.
- Segurança desde a concepção (*Security by Design*).
- Testes automatizados.
- Integridade e consistência dos dados.
- Documentação técnica.
- Versionamento com Git e integração contínua em etapas futuras.

## Estrutura de documentação

- `AGENTS.md`: instruções técnicas e arquiteturais para agentes de IA.
- `docs/learning/MENTORING.md`: metodologia de aprendizagem e autonomia técnica.
- `docs/`: documentação técnica e arquitetural do projeto.

## Objetivos de desenvolvimento

1. Configurar a estrutura Java com Spring Boot e Maven.
2. Integrar PostgreSQL e Flyway.
3. Estabelecer a estrutura inicial do Monólito Modular.
4. Implementar e testar os primeiros recursos backend.
5. Desenvolver autenticação e autorização.
6. Evoluir segurança, infraestrutura, observabilidade e deploy.
7. Incorporar recursos de inteligência artificial quando houver justificativa funcional.

---

**FocusFlow** — Engenharia de software aplicada à construção de uma plataforma de produtividade.