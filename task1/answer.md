## Этап 1: Теоретические вопросы

### Frontend

**Virtual DOM vs Real DOM**

- **Real DOM** – прямое представление HTML-структуры в браузере. Изменения в Real DOM дорогие, так как вызывают перерисовку и рефлоу.
- **Virtual DOM** – легковесная копия Real DOM, которая обновляется быстрее. React сравнивает изменения (diffing) и обновляет только нужные части Real DOM (reconciliation).
- **Почему React использует Virtual DOM?** Для оптимизации производительности, минимизации прямых манипуляций с DOM.

**== vs === в JavaScript**

- `==` – нестрогое сравнение (с приведением типов).
  ```js
  "5" == 5; // true (строка приводится к числу)
  null == undefined; // true
  ```
- `===` – строгое сравнение (без приведения типов).
  ```js
  "5" === 5; // false
  null === undefined; // false
  ```

**Контекст (this) в JavaScript**

- Контекст – значение `this`, зависящее от вызова функции.
- Изменение контекста:
  ```js
  const user = { name: "Tim" };
  function greet() { console.log(this.name); }

  greet.call(user); // "Tim"
  greet.apply(user); // "Tim"
  const boundGreet = greet.bind(user);
  boundGreet(); // "Tim"
  ```

**Promises и async/await**

  ```js
  async function fetchData() {
    try {
      const res = await fetch('https://api.example.com/data');
      const data = await res.json();
      return data;
    } catch (err) {
      console.error("Error:", err);
    }
  }
  ```

### Backend

**Безопасность API**

- SQL-инъекции: Использовать ORM (Sequelize, TypeORM) или параметризованные запросы.
- Другие атаки: XSS, CSRF (защита — CORS, токены), DDoS (лимиты запросов).

**RESTful API**

- Методы HTTP:  
  GET (Read), POST (Create), PUT/PATCH (Update), DELETE (Delete).
- CRUD:  
  POST /tasks → Create, GET /tasks → Read и т.д.

**Реляционные (SQL) vs Нереляционные (NoSQL)**

- SQL (PostgreSQL, MySQL): Сложные связи, транзакции.
- NoSQL (MongoDB): Гибкость, масштабируемость, быстрые записи.

**Логирование и мониторинг**

- Логи: Winston, Morgan.
- Мониторинг: Prometheus + Grafana, Sentry.

### Базы данных

**Индексация vs Нормализация**

- Индексация – ускорение поиска (например, индекс по user_id).
- Нормализация – устранение дублирования (разделение на таблицы).
- Избыточность полезна: Денормализация для ускорения чтения (например, кэширование username в нескольких таблицах).

**JOIN vs UNION**

- JOIN – объединение таблиц по условию  
  `SELECT * FROM users JOIN orders ON users.id = orders.user_id`
- UNION – объединение результатов запросов  
  `SELECT name FROM users UNION SELECT title FROM posts`