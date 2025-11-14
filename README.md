# 🎬 Projeto Cinema MySQL

![Projeto Cinema](image.png)

Banco de dados para gerenciamento de cinemas, filmes, sessões, promoções, usuários, ingressos e avaliações.  
Todas as tabelas e consultas foram implementadas e testadas no **[DB Fiddle](https://www.db-fiddle.com/f/ejPtkA85edVn8gdDdewoRU/51)**.

---

## 🗄️ Tabelas

- `distributors`, `genres`, `movies`, `movie_restrictions`  
- `cinema`, `halls`, `showings`  
- `promotions`, `showing_promotions`  
- `users`, `employees`, `tickets`, `payments`, `reviews`  
- `movie_genres`  

---

## 🔗 Relacionamentos

- **1:1**  
  - `payments` ↔ `tickets`  
  - `movie_restrictions` ↔ `movies`  

- **1:n**  
  - `distributors` → `movies`  
  - `cinema` → `halls`  
  - `halls` → `showings`  
  - `users` → `tickets`  
  - `movies` → `showings`  

- **n:n**  
  - `showings` ↔ `promotions` (tabela `showing_promotions`)  
  - `movies` ↔ `genres` (tabela `movie_genres`)  

---

## 💻 Consultas de Exemplo

### 1. Filmes com distribuidor e restrição de idade
```sql
SELECT m.title AS filme, d.name AS distribuidor, mr.age_limit, mr.explanation
FROM movies m
JOIN distributors d ON m.distributor_id = d.distributor_id
JOIN movie_restrictions mr ON m.movie_id = mr.movie_id
ORDER BY m.title;
