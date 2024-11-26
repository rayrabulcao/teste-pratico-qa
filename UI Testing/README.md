
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
| TC15 | Cancelar uma compra                         | 1. Ir ao carrinho. <br> 2. Clicar em "Cancelar". <br> 3. Confirmar o cancelamento. | Exibir mensagem de confirmação de cancelamento e retornar ao home.                                         |

### **3.4 Carrinho**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC16 | Remover item do carrinho                 | 1. Adicionar produto ao carrinho. <br> 2. Clicar em "Remove".                                   | Produto deve ser removido do carrinho.                                            |

### **3.5 Navegação**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC17 | Navegar para a página About                       | 1. Abrir o menu lateral. <br> 2. Clicar em "About". <br> 3. Clicar em retornar a página anterior.                                            | Redirecionar para a página de login.                                              |
### **3.6 Logout**
| ID   | Caso de Teste                            | Passos                                                                                           | Resultado Esperado                                                                 |
|------|------------------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| TC18 | Logout com sucesso                       | 1. Abrir o menu lateral. <br> 2. Clicar em "Logout".                                            | Redirecionar para a página de login.                                              |
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
| TC09 | ✅ Sucesso | - Produtos filtrados e ordenados corretamente. 
| TC10 | ✅ Sucesso | - Produtos filtrados e ordenados corretamente. | 
| TC11 | ✅ Sucesso | - Produtos filtrados e ordenados corretamente. 
| TC12 | ✅ Sucesso | - Produtos filtrados e ordenados corretamente. | 
| TC13 | ✅ Sucesso | - Produto(s) adicionado(s) corretamente ao carrinho. 
| TC14 | ✅ Sucesso | - A compra foi finalizada com sucesso. | 
| TC15 | ⚠️ Falha | - Ao clicar em cancelar, a aplicação apenas redirecionada para a página anterior sem apresentar caixa de confirmação da ação. | 
| TC16 | ✅ Sucesso | - O item removido corretamente do carrinho. | 
| TC17 | ⚠️ Falha | - Só é possível retornar a página anterior pela opção do navegador, não tendo uma opção desta na própria aplicação. | 
| TC18 | ✅ Sucesso | Logout redireciona corretamente para a página de login. |                                        |

---

## **5. Sugestões de Melhorias de UX/UI**

1. **Melhorar mensagens de erro**:
   - **Problema:** Mensagem de erro ao tentar login com usuário bloqueado é pouco amigável.
   - **Solução:** Reformular para "Usuário bloqueado. Entre em contato com o suporte para mais informações."

2. **Indicação de progresso no checkout**:
   - Adicionar barra de progresso no fluxo de compra para melhor orientação do usuário.

3. **Layout do carrinho**:
   - Tornar o botão "Remove" mais visível para o usuário.

4. **Acrescentar/diminuir quantidade do produto**:

	- Adicionar um botão que conceda a opção de adicionar/diminuir quantidade de produto a ser adquirido, tanto no home quanto no carrinho.

---

## **6. Lista de Bugs Encontrados e Evidências**

1. **Mensagem de erro cortada ao tentar login com dados inválidos.**
![Mensagem de erro cortada ao tentar login com dados inválidos](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE01%20-%20TC02.png)
2. **Mensagem de erro ao tentar login com dados inválidos está pouco formal.**
![Mensagem de erro ao tentar login com dados inválidos porco formal](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE02%20-%20TC02.png)
3. **Mensagem de erro ao tentar login sem dados está pouco intuitiva.**
![Mensagem de erro ao tentar login sem dados está pouco intuitiva](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE03%20-%20TC02.png)
4. **Mensagem de erro ao tentar login com dados bloqueados pouco amigável.**
![Mensagem de erro ao tentar login com dados bloqueados pouco amigável.](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE04%20-%20TC03.png)
5. **Sem mensagem e opção de confirmação de cancelamento de compra.**
[Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE05-TC15.mp4)
6. **Sem opção de retornar a página anterior na página da aplicação.**
[Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE06%20-%20TC17.mp4)

### **6.1 Outros bugs encontrados em teste exploratório**
Aqui estão listados alguns problemas identificados utilizando o usuário `problem_user`.
1. Ao logar com usuário problem_user a aplicação apresenta erros como imagens dos produtos todos iguais e erradas, descrição e título dos produtos com erro e ao adicionar um item e em seguida tentar remove-lo no home, a aplicação não atende a ação. Só é possível remover se optar por ir ao carrinho. [Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE07.mp4)
2. Outro problema identificado com o referido usuário é de, quando clicamos para visualizar um produto ele acaba abrindo informações de outro produto. [Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE07.mp4)
3. O filtro com esse mesmo usuário (`problem_user`) não está funcionando, ao selecionar qualquer opção do mesmo nenhuma ação é realizada. [Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE08.mp4)
4. Ao tentar adicionar todos os produtos ao carrinho, estando logado como `problem_user`, apenas três deles são adicionados ao mesmo. [Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE09.mp4)
5. Ao clicar no carrinho e tentar finalizar a compra com o usuário `problem_user`, percebeu-se que é possível inserir o nomes mas ao inserir o sobrenome ele acaba sobrescrevendo o nome inserido anteriormente.[Assista ao vídeo do teste](https://github.com/rayrabulcao/teste-pratico-qa/blob/main/UI%20Testing/Evid%C3%AAncias/ISSUE10.mp4)



---

## **7. Análise de Riscos**

1. **Risco:** Problemas no fluxo de compra podem impactar diretamente as vendas.
   - **Mitigação:** Priorizar a validação do fluxo completo de compra.
   
2. **Risco:** Mensagens de erro pouco claras podem confundir os usuários.
   - **Mitigação:** Melhorar mensagens de erro antes do lançamento.

3. **Risco:** Carrinho não possui botão de confirmação antes de esvaziar todos os itens.
   - **Mitigação:** Adicionar mensagem de confirmação.

---

## **8. Extras**

### **8.1 Testes de Responsividade**

| Dispositivo          | Resultado  | Observação                                                                                       |
|-----------------------|------------|-------------------------------------------------------------------------------------------------|
| Mobile (iPhone 12)    | ✅ Sucesso | Layout responsivo e funcional.                                                                 |
| Tablet (iPad)         | ✅ Sucesso | Exibição de conteúdo adequada.                                                                 |
| Desktop               | ✅ Sucesso | Interface estável em diferentes resoluções.                                                    |

### **8.2 Testes de Acessibilidade**

- **Critérios Avaliados:**
  - Uso de atributos ARIA.
  - Contraste de cores.
  - Navegação por teclado.

- **Resultado:** Acessibilidade funcional, mas recomenda-se melhorias no contraste das mensagens de erro.

### **8.3 Sugestões de Automação**

- **Casos sugeridos para automação**:
  - Login com diferentes tipos de usuários.
  - Fluxo de compra completo.
  - Adicionar e remover produtos do carrinho.
  - Ordenação de filtro
  - E2E (Fluxo completo abrangendo login, adição de produtoe finalização da compra)

- **Ferramentas sugeridas**:
  - Selenium com Robot Framework ou Python.

---

