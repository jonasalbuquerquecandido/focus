# AGENTS.md

## Visão geral

Este repositório representa a base inicial do projeto FocusFlow. A implementação funcional ainda não foi iniciada.

O objetivo desta documentação é orientar todas as futuras alterações e manter consistência entre a arquitetura, a convenção de código e o processo de entrega.

## Regras de trabalho

- Trabalhar sempre com o mínimo necessário para cumprir a tarefa.
- Não implementar funcionalidades que ainda não tenham sido aprovadas na arquitetura.
- Preservar o padrão de organização do repositório e manter a estrutura simples e previsível.
- Priorizar clareza, manutenção, testabilidade e documentação.
- Documentar decisões relevantes quando houver mudança de escopo, arquitetura ou padrões.

## Estrutura inicial esperada

A organização ideal do projeto será a seguinte, conforme a evolução do desenvolvimento:

- `apps/`: aplicações executáveis do projeto.
- `packages/`: bibliotecas compartilhadas reutilizáveis.
- `docs/`: documentação técnica e de produto.
- `scripts/`: utilitários e automações.
- `infra/`: infraestrutura e configuração operacional.
- `tests/`: testes de integração e regressão.

Até que a estrutura completa seja criada, este arquivo serve como fonte de referência para todos os agentes e colaboradores.

## Convenções

- Use nomes em inglês para código e arquivos, salvo quando a convenção do produto exigir outra linguagem.
- Prefira TypeScript para aplicações e módulos compartilhados.
- Evite código duplicado e mantenha a lógica separada por responsabilidade.
- Sempre que o projeto crescer, mantenha a divisão por camadas e módulos claros.
- A documentação deve acompanhar mudanças relevantes de comportamento ou arquitetura.

## Processo recomendado

1. Validar o estado atual do repositório antes de qualquer alteração.
2. Entender a tarefa e os impactos esperados.
3. Fazer a menor mudança necessária.
4. Validar com testes ou checagens mínimas disponíveis.
5. Registrar documentação quando a alteração afetar fluxos, contratos ou regras de negócio.

## Estado atual

Este repositório está em fase inicial de scaffolding. Não há implementação funcional de produto ainda.
