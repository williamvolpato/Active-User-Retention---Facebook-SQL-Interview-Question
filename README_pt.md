# Ações de Usuários no Facebook - Consulta SQL para Usuários Ativos Mensais (MAUs)

## Descrição do Projeto
Este projeto fornece uma consulta SQL para calcular o número de Usuários Ativos Mensais (MAUs) com base nas ações de usuários no Facebook em julho de 2022. Um usuário ativo é definido como alguém que realizou ações como 'sign-in', 'like' ou 'comment' tanto no mês atual quanto no mês anterior.

## Estrutura da Tabela
A tabela `user_actions` contém os seguintes campos:
- `user_id` (integer): Identificador único de cada usuário.
- `event_id` (integer): Identificador único de cada evento.
- `event_type` (string): Tipo de evento (`sign-in`, `like`, `comment`, etc.).
- `event_date` (datetime): Data e hora do evento.

## Consulta
A consulta identifica usuários ativos em julho de 2022 que também estavam ativos em junho de 2022. O resultado inclui:
- `month`: Representação numérica do mês (ex.: 7 para julho).
- `monthly_active_users`: Contagem de usuários distintos.

### Consulta SQL:
```sql
SELECT 
  7 AS month, -- Representa julho
  COUNT(DISTINCT curr_month.user_id) AS monthly_active_users
FROM user_actions AS curr_month
WHERE EXTRACT(MONTH FROM curr_month.event_date) = 7
  AND EXTRACT(YEAR FROM curr_month.event_date) = 2022
  AND EXISTS (
    SELECT 1
    FROM user_actions AS last_month
    WHERE last_month.user_id = curr_month.user_id
      AND EXTRACT(MONTH FROM last_month.event_date) = 6
      AND EXTRACT(YEAR FROM last_month.event_date) = 2022
  );
