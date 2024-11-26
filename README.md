# Teste Prático para QA

Este repositório contém a documentação, planos de teste, evidências e scripts relacionados à execução de um teste prático para QA. O objetivo é validar funcionalidades de uma aplicação web e uma API, seguindo critérios de qualidade e boas práticas.

## Estrutura do Repositório

Abaixo está uma visão geral das pastas e arquivos do repositório:

- **UI Testing**:  
  Contém os planos de teste, evidências e resultados da validação da interface de usuário (UI) da aplicação *Sauce Demo*.  
  - **Plano de Teste**: Cenários para fluxos como login, ordenação, compra, e navegação.  
  - **Evidências**: Prints de tela e relatórios de bugs encontrados.

- **API Testing**:  
  Contém as coleções e resultados dos testes da API *Restful-Booker*.  
  - **Coleções Postman**: Requests configurados com variáveis de ambiente.  
  - **Relatórios de Teste**: Resultados da validação dos endpoints principais, como autenticação e gestão de reservas.

## Objetivo

O repositório foi criado para:
- Demonstrar habilidades em planejamento e execução de testes manuais e automatizados.
- Documentar descobertas de bugs e sugerir melhorias para UX/UI.
- Validar a conformidade de APIs e identificar possíveis riscos no sistema.

## Como Navegar no Repositório

1. Para acessar o plano de testes da interface de usuário, vá para a pasta `UI Testing`.  
2. Para verificar os testes de API, consulte a pasta `API Testing`.  
3. As evidências e relatórios estão organizados em subpastas dentro de cada área.

## Tecnologias Utilizadas

- **Ferramentas**: Postman, Markdown, navegadores web para testes UI.
- **Metodologias**: Testes manuais com documentação detalhada e boas práticas de QA.


## Notas Gerais

Devido a limitações de tempo e à falta de um ambiente de trabalho adequado, não foi possível realizar uma validação mais aprofundada dos testes de API. A execução dos testes foi limitada, principalmente, pela impossibilidade de configurar corretamente o ambiente de trabalho, uma vez que não disponho de um computador pessoal no momento. 

Embora todos os cenários de teste tenham sido planejados e documentados de acordo com os requisitos da API, a execução foi parcial. Alguns testes importantes, especialmente aqueles que exigem configurações específicas do ambiente ou dependências externas, não puderam ser validados de forma completa.

A recomendação é que os testes sejam executados em um ambiente de desenvolvimento controlado, onde seja possível configurar adequadamente as ferramentas necessárias para a validação dos fluxos e garantir que todas as funcionalidades da API sejam testadas de maneira profunda e eficaz.

Com isso, fica claro que a documentação fornecida serve como um guia para os testes que precisam ser realizados em um ambiente de desenvolvimento mais adequado. Uma execução mais completa dos testes poderá ser realizada assim que as condições do ambiente de trabalho forem ajustadas.
