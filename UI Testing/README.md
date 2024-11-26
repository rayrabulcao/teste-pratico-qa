# **Plano de Testes - UI Testing: Sauce Demo**

## **1. Objetivo**
Este documento detalha o plano de testes para validar a plataforma de e-commerce **Sauce Demo**. 
O principal objetivo deste plano de testes é garantir que a interface de usuário (UI) da plataforma **Sauce Demo** funcione de maneira eficiente, intuitiva e estável, atendendo aos requisitos funcionais e não funcionais esperados. Isso inclui validar os fluxos principais de interação do usuário, identificar problemas que possam impactar negativamente a experiência do cliente (UX/UI) e assegurar que a aplicação esteja pronta para ser lançada em produção sem problemas críticos.

Adicionalmente, será avaliada a acessibilidade, a responsividade e a possibilidade de automação de testes para fluxos recorrentes, visando melhorias contínuas e escalabilidade no processo de qualidade.

## **2. Escopo**
O escopo do plano de testes cobre a validação completa da interface de usuário (UI) da plataforma **Sauce Demo**, com foco nos seguintes aspectos:

1.  **Fluxos principais da aplicação**:
    
    -   Login com diferentes tipos de usuários.
    -   Adicionar, remover e gerenciar itens no carrinho.
    -   Ordenação e filtragem de produtos.
    -   Finalização de compras, incluindo preenchimento de formulários.
2.  **Navegação entre páginas**:
    
    -   Garantir que a transição entre páginas seja fluida, intuitiva e sem erros, como links quebrados ou carregamento incorreto.
3.  **Logout**:
    
    -   Verificar o comportamento do sistema ao realizar logout e se o usuário é redirecionado corretamente para a página de login.
4.  **Validação de UX/UI**:
    
    -   Identificar problemas visuais ou de usabilidade, como botões desalinhados, mensagens de erro não informativas ou inconsistências na interface.
5.  **Critérios de responsividade**:
    
    -   Testar o comportamento do layout em diferentes dispositivos (desktop, tablet e mobile) e tamanhos de tela.
6.  **Critérios de acessibilidade**:
    
    -   Avaliar a compatibilidade com padrões de acessibilidade, como o uso de teclado para navegação, atributos ARIA e contraste adequado de cores.
7.  **Documentação e entrega**:
    
    -   Documentar resultados dos testes, sugestões de melhoria, bugs encontrados e uma análise de riscos para suporte na tomada de decisões antes do lançamento.

**Limitações**:

-   Não estão incluídos no escopo testes de performance, carga ou segurança, que deverão ser tratados em etapas separadas.

## **3. Casos de Teste**

### **3.1 Login**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC01 | Login com credenciais válidas            | 1. Acessar o site. <br> 2. Inserir `standard_user` / `secret_sauce`. <br> 3. Clicar em "Login".  | Redirecionar para a página de produtos.                                           |
| TC02 | Login com credenciais inválidas          | 1. Inserir `admin` / `admin`. <br> 2. Clicar em "Login".                    | Exibir mensagem de erro clara e não permitir login.                              |
| TC03 | Login com usuário bloqueado              | 1. Inserir `locked_out_user` / `secret_sauce`. <br> 2. Clicar em "Login".                       | Exibir mensagem informando que o usuário está bloqueado.                         |
| TC04 | Login com usuário com problema              | 1. Inserir `problem_user` / `secret_sauce`. <br> 2. Clicar em "Login".                       | Exibir mensagem informando que o usuário está bloqueado.                         |
| TC05 | Login com usuário com problema de desempenho              | 1. Inserir `performance_glitch_user` / `secret_sauce`. <br> 2. Clicar em "Login".                       | Redirecionar para a página de produtos.                         |
| TC06 | Login com usuário com erro              | 1. Inserir `error_user` / `secret_sauce`. <br> 2. Clicar em "Login".                       | Redirecionar para a página de produtos.                         |
| TC07 | Login com usuário visual              | 1. Inserir `visual_user` / `secret_sauce`. <br> 2. Clicar em "Login".                       | Redirecionar para a página de produtos.                         |
| TC08 | Login com campos vazios                  | 1. Deixar os campos de usuário e senha em branco. <br> 2. Clicar em "Login".                    | Exibir mensagem de erro pedindo preenchimento dos campos obrigatórios.           |

### **3.2 Ordenação de filtro**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC09 | Ordenar produtos de A a Z            | 1. Selecionar o filtro `Name (A to Z)`.                                       | Produtos devem ser filtrados em ordem alfabética crescente.                                          |
| TC10 | Ordenar produtos de Z a A                         | 1. Selecionar o filtro `Name (Z to A)`.                                       | Produtos devem ser filtrados em ordem alfabética decrescente.                                         |
| TC11 | Ordenar produtos por maior preço            | 1. Selecionar o filtro `Price (high to low)`.                                       | Produtos devem ser filtrados em ordem do maior para o menor preço.                                          |
| TC12 | Ordenar produtos por menor preço                         | 1. Selecionar o filtro `Price (low to high)`.                                       | Produtos devem ser filtrados em ordem do menor para o maior preço.

### **3.3 Fluxo de Compra**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC13 | Adicionar produto ao carrinho            | 1. Selecionar um produto. <br> 2. Clicar em "Add to cart".                                       | Produto deve ser adicionado ao carrinho.                                          |
| TC14 | Finalizar compra                         | 1. Ir ao carrinho. <br> 2. Clicar em "Checkout". <br> 3. Preencher os dados e finalizar compra. | Exibir mensagem de confirmação de compra.                                         |

### **3.4 Carrinho**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC15 | Remover item do carrinho                 | 1. Adicionar produto ao carrinho. <br> 2. Clicar em "Remove".                                   | Produto deve ser removido do carrinho.                                            |

### **3.5 Navegação**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC16 | Logout com sucesso                       | 1. Abrir o menu lateral. <br> 2. Clicar em "Logout".                                            | Redirecionar para a página de login.                                              |
### **3.6 Logout**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC17 | Logout com sucesso                       | 1. Abrir o menu lateral. <br> 2. Clicar em "Logout".                                            | Redirecionar para a página de login.                                              |
---

## **4. Resultados dos Testes Executados**

| Caso de Teste | Resultado  | Observação                                                                                       |
|---------------|------------|-------------------------------------------------------------------------------------------------|
| TC01          | ✅ Sucesso | - O login com as credenciais informadas funcionou corretamente.              |
| TC02          | ⚠️ Falha | <br> - O elemento da mensagem de feedback está aparecendo de forma cortada, dificultando a leitura e visualização da mesma <br> - Melhorar a mensagem de feedback em casos de inserção ou não de usuário e senhas inválidos, tirar o Epic Sadface para algo mais formal. <br> - Ao inserir um usuário válido e uma senha inválida, a mensagem de feedback retorna que ambos estão incorretos quando deveria constar apenas que a senha está incorreta, o mesmo ocorre se inserir um usuário errado e a senha correta.                                     |
| TC03          | ⚠️ Falha   | - Melhorar a mensagem "Sorry, this user has been locked out" retornada, pois acaba sendo pouco amigável.                              |
| TC04          | ✅ Sucesso | - O login com as credenciais informadas funcionou corretamente.                                |
| TC05          | ✅ Sucesso* | - O login com as credenciais informadas funcionou corretamente, porém teve um certo delay para acessar e apresentar o home da página.                                                   |
| TC06          | ✅ Sucesso | - O login com as credenciais informadas funcionou corretamente.                                                                 |
| TC07          | ✅ Sucesso | - O login com as credenciais informadas funcionou corretamente.                                                        |
| TC08          | ✅ Sucesso | - Exibida mensagem pedindo preenchimento dos campos obrigatórios.
| TC09 | ✅ Sucesso | Produtos filtrados e ordenados corretamente. 
| TC10 | ✅ Sucesso | Produtos filtrados e ordenados corretamente. | 
| TC11 | ✅ Sucesso | Produtos filtrados e ordenados corretamente. 
| TC12 | ✅ Sucesso | Produtos filtrados e ordenados corretamente. | 
| TC13 | ✅ Sucesso | Produto adicionado corretamente ao carrinho. 
| TC14 | ✅ Sucesso | Compra finalizada com sucesso. | 
| TC15 | ✅ Sucesso | Item removido corretamente do carrinho. | 
| TC16 | ✅ Sucesso | Item removido corretamente do carrinho. | 
| TC17 | ✅ Sucesso | Logout redireciona corretamente para a página de login. |                                        |

---

## **5. Sugestões de Melhorias de UX/UI**

1. **Melhorar mensagens de erro**:
   - **Problema:** Mensagem de erro ao tentar login com usuário bloqueado é pouco amigável.
   - **Solução:** Reformular para "Usuário bloqueado. Entre em contato com o suporte para mais informações."

2. **Indicação de progresso no checkout**:
   - Adicionar barra de progresso no fluxo de compra para melhor orientação do usuário.

3. **Layout do carrinho**:
   - Tornar o botão "Remove" mais visível para o usuário.

4. **Acrescentar/dimunir quantidade do produto**:
	- Adicionar um botão que conceda a opção de adicionar/diminuir quantida de produto a ser adquirido, tanto no home quanto no carrinho.