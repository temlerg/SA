## 🌐 CORS (Cross-Origin Resource Sharing)

**CORS** — это механизм, позволяющий серверу управлять доступом к своим ресурсам с других доменов (междоменные запросы).

### 📌 Зачем нужен?

Браузеры по умолчанию **блокируют** запросы с одного домена на другой, если нет разрешения — это **механизм безопасности** (Same-Origin Policy).

### 🔧 Пример запроса с другого домена:

```http
Origin: https://frontend.com
```

Сервер должен ответить:

```http
Access-Control-Allow-Origin: https://frontend.com
```

### 📋 Ключевые заголовки:

- `Access-Control-Allow-Origin` — указывает разрешённый домен (или `*`)
    
- `Access-Control-Allow-Methods` — разрешённые HTTP-методы (`GET, POST...`)
    
- `Access-Control-Allow-Headers` — какие заголовки разрешены (`Content-Type`, `Authorization`)
    
- `Access-Control-Allow-Credentials` — можно ли передавать cookie или токены
    

### 🧪 Префлайт-запрос (OPTIONS)

При сложных запросах браузер сначала отправляет **OPTIONS**:

```http
OPTIONS /api/data
Origin: https://frontend.com
Access-Control-Request-Method: POST
```

Если сервер не ответит корректно, основной запрос будет **заблокирован**.

### ⚠️ Частые ошибки:

- Отсутствует `Access-Control-Allow-Origin` на сервере
    
- Неверные методы или заголовки
    
- Не настроена поддержка `credentials` (например, cookies)