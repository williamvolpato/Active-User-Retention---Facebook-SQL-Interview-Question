# Active User Retention

## Problem Statement (English)

### Description
This is the same question as problem #23 in the SQL Chapter of **Ace the Data Science Interview**!

Assume you're given a table containing information on Facebook user actions. Write a query to obtain the number of monthly active users (MAUs) in July 2022, including the month in numerical format "1, 2, 3".

### Hint:
- An active user is defined as a user who has performed actions such as 'sign-in', 'like', or 'comment' in both the current month and the previous month.

### Table Schema
**user_actions Table**:
| Column Name | Type     |
|-------------|----------|
| user_id     | integer  |
| event_id    | integer  |
| event_type  | string ("sign-in", "like", "comment") |
| event_date  | datetime |

### Example Input:
| user_id | event_id | event_type | event_date          |
|---------|----------|------------|---------------------|
| 445     | 7765     | sign-in    | 05/31/2022 12:00:00 |
| 742     | 6458     | sign-in    | 06/03/2022 12:00:00 |
| 445     | 3634     | like       | 06/05/2022 12:00:00 |
| 742     | 1374     | comment    | 06/05/2022 12:00:00 |
| 648     | 3124     | like       | 06/18/2022 12:00:00 |

### Example Output for June 2022:
| month | monthly_active_users |
|-------|-----------------------|
| 6     | 1                     |

### Example Explanation
In June 2022, there was only one monthly active user (MAU) with the `user_id` 445.

Please note that the output provided is for June 2022 as the `user_actions` table only contains event dates for that month. You should adapt the solution accordingly for July 2022.

---

## Enunciado do Problema (Português)

### Descrição
Esta é a mesma questão do problema #23 no capítulo de SQL do **Ace the Data Science Interview**!

Considere que você recebeu uma tabela contendo informações sobre ações de usuários no Facebook. Escreva uma consulta para obter o número de usuários ativos mensais (MAUs) em julho de 2022, incluindo o mês no formato numérico "1, 2, 3".

### Dica:
- Um usuário ativo é definido como um usuário que realizou ações como 'sign-in', 'like' ou 'comment' tanto no mês atual quanto no mês anterior.

### Esquema da Tabela
**Tabela `user_actions`**:
| Nome da Coluna | Tipo     |
|----------------|----------|
| user_id        | integer  |
| event_id       | integer  |
| event_type     | string ("sign-in", "like", "comment") |
| event_date     | datetime |

### Exemplo de Entrada:
| user_id | event_id | event_type | event_date          |
|---------|----------|------------|---------------------|
| 445     | 7765     | sign-in    | 31/05/2022 12:00:00 |
| 742     | 6458     | sign-in    | 03/06/2022 12:00:00 |
| 445     | 3634     | like       | 05/06/2022 12:00:00 |
| 742     | 1374     | comment    | 05/06/2022 12:00:00 |
| 648     | 3124     | like       | 18/06/2022 12:00:00 |

### Exemplo de Saída para Junho de 2022:
| month | monthly_active_users |
|-------|-----------------------|
| 6     | 1                     |

### Explicação do Exemplo
Em junho de 2022, houve apenas um usuário ativo mensalmente (MAU) com o `user_id` 445.

Observe que o resultado fornecido é para junho de 2022, já que a tabela `user_actions` contém apenas datas de eventos para aquele mês. Você deve adaptar a solução para julho de 2022.
