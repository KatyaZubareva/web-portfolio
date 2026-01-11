---
title: "HTTP Protocol. Client–Server Interaction"
description: "Практическая работа по изучению HTTP-запросов и инструментов взаимодействия с API"
---

## Цель работы

Изучить структуру HTTP-запросов и ответов, освоить отправку запросов различными инструментами и получить практический опыт работы с публичными API.

---

## Ход работы

### Отправка GET-запроса через Telnet / netcat
**Описание:** ручная отправка HTTP-запроса на публичный веб-сервер через CLI.  
**Задачи:** изучить низкоуровневую структуру HTTP-запроса и ответа.  
**Инструменты:** Telnet, netcat.  

**Пример запроса через netcat:**

```bash
nc jsonplaceholder.typicode.com 80
````

```
GET /posts/1 HTTP/1.1
Host: jsonplaceholder.typicode.com

```

**Результат:** получен JSON с данными поста:

```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit..."
}
```

**Скриншот:**
![GET через netcat](screenshots/get_netcat.png)

---

### Отправка POST-запроса через netcat

**Описание:** отправка POST-запроса с JSON-телом на публичный API.
**Задачи:** передача данных в теле HTTP-запроса, работа с заголовками.
**Инструменты:** netcat.

** Пример запроса через netcat: **

```
nc jsonplaceholder.typicode.com 80
```

**После подключения вводим вручную HTTP-запрос:**

```
POST /posts HTTP/1.1
Host: jsonplaceholder.typicode.com
Content-Type: application/json
Content-Length: 59

{"title":"Моя первая статья","body":"Текст статьи","userId":1}
```

**Пример данных:**

```json
{
  "title": "Моя первая статья",
  "body": "Текст статьи",
  "userId": 1
}
```

**Результат:** сервер принял данные и вернул JSON с присвоенным ID:

```json
{
  "title": "Моя первая статья",
  "body": "Текст статьи",
  "userId": 1,
  "id": 101
}
```

**Скриншот:**
![POST через netcat](screenshots/post_netcat.png)

---

### Отправка запросов с помощью cURL

**Описание:** выполнение GET и POST запросов к API через CLI.
**Задачи:** освоить синтаксис cURL, работу с заголовками и JSON.
**Инструменты:** cURL.

**GET-запрос:**

```bash
curl https://jsonplaceholder.typicode.com/posts/1
```

**Скриншот:**
![GET через cURL](screenshots/get_curl.png)

**POST-запрос:**

```bash
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -d '{"title":"Моя первая статья","body":"Текст статьи","userId":1}'
```

**Скриншот:**
![POST через cURL](screenshots/post_curl.png)

---

## Использование GUI-инструмента

### Получение курса валют через API Банка России

**Описание:** выполнение GET-запроса к XML API Банка России для получения курса валюты за выбранный период.
**Задачи:** работа с публичным API, параметрами запроса и XML-ответом.
**Инструменты:** Postman / Insomnia / HTTPie Desktop.

**Пример запроса:**

```
GET https://www.cbr.ru/scripts/XML_daily.asp?date_req=11/01/2026
```

**Пример XML-ответа:**

```xml
<ValCurs Date="11.01.2026" name="Foreign Currency Market">
  <Valute ID="R01235">
    <NumCode>840</NumCode>
    <CharCode>USD</CharCode>
    <Nominal>1</Nominal>
    <Name>Доллар США</Name>
    <Value>74,32</Value>
  </Valute>
</ValCurs>
```

**Скриншот:**
![GET курс валют через Postman](screenshots/get_currency_postman.png)

---

## Выводы

В ходе работы были изучены основы протокола HTTP и реализованы GET и POST запросы с использованием различных инструментов.
Работа позволила на практике увидеть различия между низкоуровневым и высокоуровневым взаимодействием с HTTP, освоить синтаксис cURL и работу с GUI-инструментами, а также закрепить понимание клиент–серверной архитектуры.


