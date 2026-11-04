# ADR-001 — Arquitetura e stack tecnológica

**Situação:** Aceito

## Contexto

O Connexa é uma aplicação destinada à organização de grupos de estudo e suas atividades. A equipe precisava definir uma arquitetura e tecnologias que permitissem desenvolver, testar e manter o sistema de forma organizada.

## Decisão

Foi escolhida uma arquitetura de monólito modular para o back-end, com ASP.NET Core e .NET 10. A aplicação é centralizada no projeto Connexa.Api e dividida em módulos independentes, como Identidade, Perfil, Grupos, Encontros, Acompanhamento, Painel e Materiais.

O banco de dados escolhido foi PostgreSQL, integrado ao back-end por meio do Entity Framework Core e do Npgsql.

No front-end, foi escolhida uma aplicação SPA desenvolvida com React, TypeScript e Vite. Para gerenciamento de formulários e validações são utilizadas bibliotecas como React Hook Form e Zod. Os testes do back-end utilizam MSTest e os do front-end utilizam Vitest.

## Alternativas consideradas

| Alternativa | Por que não foi escolhida |
|---|---|
| Monólito sem divisão em módulos | Dificultaria a separação das responsabilidades e a manutenção do código conforme o sistema crescesse. |
| Arquitetura de microsserviços | Acrescentaria complexidade de comunicação, implantação e configuração desnecessária para o escopo inicial do projeto. |
| Front-end sem organização por funcionalidades | Poderia dificultar a manutenção e a evolução das funcionalidades. |

## Consequências

- **Positivas:** melhor organização do código, separação de responsabilidades, facilidade de manutenção e possibilidade de testar os módulos.
- **Negativas:** exige atenção às dependências entre módulos e à manutenção das regras de arquitetura.
- **Como verificar:** executar os testes automatizados do back-end e do front-end, além do comando `./verificar`, que valida os principais critérios do projeto.
