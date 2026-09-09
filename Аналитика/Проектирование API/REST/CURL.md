# cURL — инструмент командной строки для HTTP-запросов

`cURL` (Client URL) — это мощный инструмент командной строки для выполнения HTTP-запросов и взаимодействия с веб-серверами. Он используется для тестирования API, скачивания файлов, отправки форм и многого другого.

---

## 📌 Основной синтаксис

```bash
curl [опции] [URL]
```

---

## 🔹 Примеры запросов

### GET-запрос (получение данных)

```bash
curl https://api.example.com/users
```

### POST-запрос (отправка данных)

```bash
curl -X POST https://api.example.com/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Ivan", "email": "ivan@example.com"}'
```

### PUT-запрос (обновление данных)

```bash
curl -X PUT https://api.example.com/users/1 \
  -H "Content-Type: application/json" \
  -d '{"email": "new_email@example.com"}'
```

### DELETE-запрос (удаление данных)

```bash
curl -X DELETE https://api.example.com/users/1
```

---

## 🔐 Авторизация

### Basic Auth:

```bash
curl -u username:password https://api.example.com/secure-data
```

### Bearer Token (OAuth2):

```bash
curl -H "Authorization: Bearer <token>" https://api.example.com/me
```

---

## ⚙️ Полезные опции

- `-X` — метод запроса (GET, POST, PUT, DELETE и т.д.)
    
- `-H` — заголовки (например, `Content-Type` или `Authorization`)
    
- `-d` — тело запроса
    
- `-i` — показать HTTP-заголовки ответа
    
- `-s` — "тихий" режим (скрыть прогресс-бар)
    
- `-o file` — сохранить ответ в файл
    

---

## 🛠 Примеры продвинутого использования

### Отправка формы (x-www-form-urlencoded):

```bash
curl -X POST https://example.com/form \
  -d "username=test&password=1234"
```

### Загрузка файла:

```bash
curl -O https://example.com/file.zip
```

### Загрузка с именем файла:

```bash
curl -o custom_name.zip https://example.com/file.zip
```

---

## ✅ Полезное

- `curl` есть практически на всех Unix-подобных системах (Linux, macOS)
    
- Для Windows доступен через PowerShell, Git Bash или WSL
    
- Часто используется вместе с `jq` для обработки JSON-ответов
    

---

## 📚 Ссылки

- Официальный сайт: [https://curl.se](https://curl.se/)
    
- Документация: `man curl` или `curl --help`
    
