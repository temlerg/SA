# CRUD: Create, Read, Update, Delete

CRUD — это базовая модель управления данными, которая включает в себя четыре основные операции: создание, чтение, обновление и удаление данных. Эти действия лежат в основе взаимодействия с базами данных и API.

## 1. Create (Создание)

Создание новой записи в базе данных или системе.

**SQL-пример:**

```sql
INSERT INTO users (name, email) VALUES ('Ivan', 'ivan@example.com');
```

**REST API (HTTP POST):**

```http
POST /users
{
  "name": "Ivan",
  "email": "ivan@example.com"
}
```

## 2. Read (Чтение)

Извлечение данных из системы.

**SQL-пример:**

```sql
SELECT * FROM users WHERE id = 1;
```

**REST API (HTTP GET):**

```http
GET /users/1
```

## 3. Update (Обновление)

Изменение существующих данных.

**SQL-пример:**

```sql
UPDATE users SET email = 'new_email@example.com' WHERE id = 1;
```

**REST API (HTTP PUT):**

```http
PUT /users/1
{
  "email": "new_email@example.com"
}
```

## 4. Delete (Удаление)

Удаление существующих данных.

**SQL-пример:**

```sql
DELETE FROM users WHERE id = 1;
```

**REST API (HTTP DELETE):**

```http
DELETE /users/1
```

---

## CRUD в контексте архитектуры

### REST API

- `POST` → Create
    
- `GET` → Read
    
- `PUT` / `PATCH` → Update
    
- `DELETE` → Delete
    

### MVC (Model-View-Controller)

- **Model** — реализует CRUD-операции
    
- **Controller** — управляет логикой обработки данных
    
- **View** — отображает результат CRUD-действий
    

---

## CRUD в разных технологиях

- **SQL / NoSQL** — независимо от типа СУБД, CRUD актуален
    
- **ORM (Object-Relational Mapping)** — упрощает реализацию CRUD (например, SQLAlchemy, Hibernate, Django ORM)
    
- **Frontend (React, Vue, Flutter)** — отправляет запросы на backend для выполнения CRUD
    
- **Mobile (например, Flutter)** — может использовать локальные базы (SQLite, Hive) или удалённые API