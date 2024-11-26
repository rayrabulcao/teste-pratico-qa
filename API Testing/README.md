# Plano de testes - API Testing: Restful Booker

## **1. Objetivo**

O objetivo deste projeto é testar a API do **Restful-Booker**, um sistema de reservas de hotel, garantindo que todos os endpoints principais estejam funcionando corretamente e de acordo com os requisitos estabelecidos. Os testes incluem validação de autenticação, gestão de reservas, e a capacidade de realizar buscas e aplicar filtros para encontrar reservas específicas. Além disso, a documentação completa será criada para registrar os resultados, comportamentos encontrados e sugestões de melhorias.

## **2. Escopo**

O escopo do teste de API abrange os seguintes pontos:

1. **Autenticação**: Garantir que a API permita a autenticação de usuários e retorne um token válido. Testar também a falha de autenticação com credenciais inválidas.
  
2. **Gestão de Reservas**: Testar os fluxos de criação, leitura, atualização e exclusão de reservas. Validar o retorno adequado para tentativas de modificar ou deletar reservas inexistentes.
  
3. **Filtros e Buscas**: Verificar a funcionalidade dos filtros de pesquisa de reservas por nome, data de check-in e data de check-out. Incluir cenários com formatos inválidos e falhas esperadas.
  
4. **Validação de Erros**: Avaliar o tratamento de erros para cenários com entradas inválidas, como dados ausentes ou mal formatados.

5. **Testes Funcionais**: Garantir que a API responda de forma esperada a todas as requisições, com as respostas adequadas para cada tipo de operação.

6. **Documentação**: Criar e manter uma documentação completa com os testes realizados, resultados obtidos, bugs encontrados e sugestões de melhorias.

---


## 3. Cenários Testados

### 3.1 Autenticação
- **Gerar token de autenticação**  
  Testa se a API gera um token válido ao enviar credenciais corretas.  
  **Endpoint**: `POST /auth`  
  **Parâmetros**:
  ```json
  {
    "username": "admin",
    "password": "password123"
  }

**Expectativa**: Código de resposta `200` com o token gerado.

**Cenário de Falha**:

-   **Tentar gerar token com credenciais inválidas**  
    Testa o comportamento da API ao enviar credenciais inválidas.  
    **Expectativa**: Código de resposta `403` com mensagem de erro relevante.

### 3.2 Gestão de Reservas

-   **Criar uma nova reserva**  
    Envia uma requisição para criar uma reserva com dados válidos.  
    **Endpoint**: `POST /booking`  
    **Parâmetros**:
    
    ```json        
    {
      "firstname": "John",
      "lastname": "Doe",
      "totalprice": 123,
      "depositpaid": true,
      "bookingdates": {
        "checkin": "2024-11-01",
        "checkout": "2024-11-05"
      },
      "additionalneeds": "Breakfast"
    } 
    
  **Expectativa**: Código de resposta `200` com os dados da reserva criada.
    
  **Cenário de Falha**:
    
  - **Tentar criar uma reserva sem dados obrigatórios**  
        Envia uma requisição para criar uma reserva sem o campo obrigatório "firstname".  
        **Expectativa**: Código de resposta `400` com mensagem de erro informando o campo ausente.
-   **Buscar uma reserva específica**  
    Testa se é possível buscar uma reserva existente pelo ID.  
    **Endpoint**: `GET /booking/{id}`  
    **Cenário de Falha**:
    
    -   **Buscar uma reserva com ID inexistente**  
        Testa a resposta da API quando um ID de reserva inválido é fornecido.  
        **Expectativa**: Código de resposta `404` com mensagem de erro indicando que a reserva não foi encontrada.
-   **Listar todas as reservas**  
    Verifica se a API retorna todas as reservas.  
    **Endpoint**: `GET /booking`  
    **Cenário de Falha**:
    
    -   **Listar reservas com parâmetros de filtro inválidos**  
        Testa a resposta da API ao fornecer parâmetros inválidos, como um filtro de data mal formatado.  
        **Expectativa**: Código de resposta `400` com mensagem de erro sobre o formato inválido.
-   **Atualizar uma reserva existente**  
    Testa se é possível atualizar uma reserva existente com dados válidos.  
    **Endpoint**: `PUT /booking/{id}`  
    **Expectativa**: Código de resposta `200` com os dados atualizados.
    
    **Cenário de Falha**:
    
    -   **Tentar atualizar uma reserva inexistente**  
        Testa a resposta da API ao tentar atualizar uma reserva que não existe.  
        **Expectativa**: Código de resposta `404` com mensagem de erro indicando que a reserva não foi encontrada.
-   **Deletar uma reserva**  
    Testa se é possível deletar uma reserva existente.  
    **Endpoint**: `DELETE /booking/{id}`  
    **Expectativa**: Código de resposta `201` indicando sucesso.
    
    **Cenário de Falha**:
    
    -   **Deletar uma reserva inexistente**  
        Testa a resposta da API ao tentar deletar uma reserva com um ID inválido.  
        **Expectativa**: Código de resposta `404` com mensagem de erro indicando que a reserva não foi encontrada.

### 3.3 Filtros e Buscas

-   **Buscar reservas por nome**  
    Testa se a API retorna as reservas correspondentes ao nome fornecido.  
    **Endpoint**: `GET /booking?firstname=John`  
    **Cenário de Falha**:
    
    -   **Buscar reservas por nome inexistente**  
        Testa a resposta da API ao buscar por um nome que não existe.  
        **Expectativa**: Código de resposta `200` com lista vazia.
-   **Buscar reservas por data de check-in**  
    Testa se a API retorna reservas a partir de uma data de check-in específica.  
    **Endpoint**: `GET /booking?checkin=2024-11-01`  
    **Cenário de Falha**:
    
    -   **Buscar reservas por data com formato inválido**  
        Testa a resposta da API ao enviar um formato de data inválido.  
        **Expectativa**: Código de resposta `400` com mensagem de erro informando o formato incorreto.
-   **Buscar reservas por data de check-out**  
    Testa se a API retorna reservas até uma data de check-out específica.  
    **Endpoint**: `GET /booking?checkout=2024-11-05`  
    **Cenário de Falha**:
    
    -   **Buscar reservas por data de check-out com formato inválido**  
        Testa a resposta da API ao enviar um formato de data inválido.  
        **Expectativa**: Código de resposta `400` com mensagem de erro informando o formato incorreto.

----------


## 4. Resultados Obtidos

### 4.1 Autenticação
| Cenário                              | Resultado | Observações                        |
|--------------------------------------|-----------|-------------------------------------|
| Gerar token de autenticação          | Sucesso   | Token gerado com credenciais válidas. |
| Tentar gerar token com credenciais inválidas| Sucesso | Erro 403 retornado corretamente.   |

### 4.2 Gestão de Reservas
| Cenário                    | Resultado | Observações                        |
|----------------------------|-----------|-------------------------------------|
| Criar uma nova reserva     | Sucesso   | Reserva criada com ID gerado.      |
| Tentar criar reserva sem dados obrigatórios | Falha | Erro 400 informando dados ausentes. |
| Buscar uma reserva específica | Sucesso   | Reserva encontrada pelo ID.        |
| Buscar uma reserva com ID inexistente | Falha | Erro 404, reserva não encontrada.  |
| Listar todas as reservas   | Sucesso   | Retornou lista completa de reservas. |
| Listar reservas com parâmetros de filtro inválidos | Falha | Erro 400, filtro inválido. |
| Atualizar uma reserva existente | Sucesso   | Dados atualizados corretamente.    |
| Tentar atualizar uma reserva inexistente | Falha | Erro 404, reserva não encontrada.  |
| Deletar uma reserva        | Sucesso   | Reserva deletada com sucesso.      |
| Deletar uma reserva inexistente | Falha | Erro 404, reserva não encontrada.  |

### 4.3 Filtros e Buscas
| Cenário                    | Resultado | Observações                        |
|----------------------------|-----------|-------------------------------------|
| Buscar reservas por nome   | Sucesso   | Resultados filtrados corretamente. |
| Buscar reservas por nome inexistente | Sucesso | Lista vazia retornada. |
| Buscar reservas por check-in | Sucesso   | Retornou reservas no intervalo especificado. |
| Buscar reservas por check-in com formato inválido | Falha | Erro 400, formato de data inválido. |
| Buscar reservas por check-out | Sucesso   | Retornou reservas no intervalo especificado. |
| Buscar reservas por check-out com formato inválido | Falha | Erro 400, formato de data inválido. |

---

## 5. Bugs Encontrados

Nenhum bug crítico foi encontrado durante a execução dos testes.

---

## 6. Sugestões de Melhorias
- Melhorar mensagens de erro para fornecer mais detalhes ao cliente, como exemplos de formato de dados válidos.
- Adicionar validação mais robusta nos campos obrigatórios (exemplo: nome, data).
- Implementar paginação para o endpoint `GET /booking` para lidar com um número grande de reservas.

---

## 7. Considerações Finais
Os testes realizados cobrem os principais fluxos da API. O sistema atende aos requisitos básicos de funcionalidade e robustez. Sugestões de melhoria foram listadas para refinar a experiência de uso e facilitar a integração com o front-end.
Estes cenários relatados foram gerados e validados com o auxílio de IA (ChatGPT), para facilitar a inclusão dos mesmos no repositório de execução dos testes de API.
