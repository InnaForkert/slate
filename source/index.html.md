---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python


toc_footers:
  - <a href='mailto:office@leadleader.com.ua'>Contact us</a>

includes:

search: false

code_clipboard: true

meta:
  - name: description
    content: Документація по сервісам API Lead Leader
---

# Вступ

Ласкаво просимо до API Lead Leader! Ви можете використовувати цим API для доступу до ендпоінтів точок API Lead Leader, які дозволяють вам керувати та аналізувати генерацію лідів, відстеження та взаємодію на різних платформах.

Ми пропонуємо підключення мовами Shell, Ruby, Python та JavaScript! Ви можете переглядати приклади коду в темній області праворуч, і ви можете перемикати мову програмування прикладів за допомогою вкладок у верхньому правому куті.

# Метод «Авторизація»

`POST https://api.leadleader.com.ua/api/partners/input/create-short-deal/`

> **Приклад валідної пари ключів розміром 1024 bit **

> **Public**

```python
  -----BEGIN PUBLIC KEY-----
  MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCNaJBWIhPU+TqSAOEZjpwLQ291N+19rmxqngI1jh5CBPe/WHhArUCs4g5x+cq/IayrjI4DVPs1LO8pNHXO0e9WuZFqP31GyAxDC2RWvdPc4AMmbpn5eFmkaZJ6zTHlbf4Nmpynk+EcORQBUcJL0ILHsNRlUg16Mavab9P78Ba9iQIDAQAB
  -----END PUBLIC KEY-----
```

> **Private**

```python
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQCNaJBWIhPU+TqSAOEZjpwLQ291N+19rmxqngI1jh5CBPe/WHhArUCs4g5x+cqIayrjI4DVPs1LO8pNHXO0e9WuZFqP31GyAxDC2RWvdPc4AMmbpn5eFmkaZJ6zTHlbf4Nmpynk+EcORQBUcJL0ILHsNRlUg16Mavab9P78Ba9iQIDAQABAoGAYLzh0Srq6k291dgoJjW7ZrExdL1YCRzkKmQCGuUoqf2ABzTcv1JG5n6XZz19iBffalRzarAeUph03Hl5Bo3z7w/IPNdm5sRRK1/3jOk5Tla6vdUyp8XH5iyMhhf8H4KIapUrNdLnfWv74crxX0RsCfSUf5tCbfzvDH1vvnrDziECQQD78iKwBH7UtPveiXsv9SCtRL4hbqNr+CjLc9VnEESg+UoUYfB2Bm7NeEgPeNLor0w0mGHV4n5honmFck9fUfKdAkEAj68UxEpS7IAygpccGFXNM8bdyi4g4t8OcNjjv6xwoMFnHeji0eeC8+W8wpgqaAS7+E8hJNb11Q4zeRVVHtG83QJADZrmuqCThML9MugzqcRP7mte5QlHc+YjtdDcfkNHoXW0xWMAjC8OvrO3GHbK1NvafqCX7+faMUWH0Gf610filQJBAIhZHbzTxvM1CDmSig+xxGPA8JE+yuhfwYVm3GD0k4CJZ4AjkrKcHlGyjjifS4agD3woIwyhjHFc442gp8DySWUCQC+nTwcE7xtjR9uVFoRfrklkhXGZMIU4nbiJ6CrqBr8o4QBD0gn5QqCARPPE+B0jBaId79/e1Jv9oxv/eYu5P54=
-----END RSA PRIVATE KEY-----
```

Алгоритм авторизації складається з наступних кроків:

- Процес генерації та обміну ключами RSA (size = 1024 bit).
  Існує дві пари ключів:

  - Lead Leader Keys (Public та Private) – ключі сервісу
  - Custom Keys (Public та Private) – ключі зовнішньої системи

Сторони генерують пари ключів RSA та обмінюються Public ключами.


- Lead Leader реєструє на своєму сервісі зовнішню систему та передає їй email/login та password. 
Зовнішня система повинна зашифрувати отримані від Lead Leader email/login та password з використанням заповнення ОАЕР за допомогою Public ключа, отриманого від сервісу на кроці 1. 

**Приклад отриманих від Lead Leader email та password:**

`
Email: «EmailExample@mail.com»
`

`
Password: «PasswordExample»
`

<div style="height: 20px;"></div>

```python
encrypted_email: «G3iW/QhCBK41zs+s9RaNvzDOAzvhAX2bQ4FJQoHcmLUsvhpaDWyLTnOZw5++ivrNjxoaBhu6xme3d/oCGoXe+w7nzBEf9WuR0qO0qS/UzKStWznjhPeD1DLda8lAHs2gt8e/3ZD4IgCjGPB6qOVQ46qam8SJ0rHyWN86cyDYFug=»

encrypted_password: «gSdSkqR0nzPHXiSlryKot2FuD1N2HZMsdZqqvWc7lYRcYdMMuEpQLiI079wNriZ9ECfJqYMNkKXryW8y4ahYAWF+WIplDhxv6nbA3fz3CYDD3b7eZ9V0Mk7ups6QVw4zDfr9oeY2hY2IDvSETVdpb4L4REXRCuluwXDxDQJ0cYY=»
```

Якщo зашифрувати ці дані з використанням заповнення ОАЕР за допомогою Public ключа, що наведений в якості прикладу на кроці 1, то отримаємо зашифровані дані у наступному вигляді:

<div style="height: 20px;"></div>

```python
signed_email: [110, 189, 95, 64, 198, 150, 251, 109, 222, 148, 192, 201, 150, 5, 61, 51, 198, 102, 224, 40, 132, 29, 241, 180, 77, 125, 200, 85, 3, 35, 66, 87, 64, 76, 136, 163, 99, 109, 27, 252, 184, 101, 29, 196, 72, 195, 158, 91, 239, 111, 44, 163, 113, 129, 66, 103, 140, 188, 156, 220, 221, 15, 221, 131, 0, 120, 200, 117, 129, 79, 123, 163, 249, 63, 177, 165, 99, 227, 94, 253, 55, 5, 111, 74, 28, 202, 171, 179, 45, 129, 82, 227, 22, 137, 168, 119, 182, 128, 174, 68, 83, 160, 33, 75, 210, 191, 82, 131, 223, 33, 91, 144, 216, 56, 127, 189, 114, 21, 214, 39, 65, 28, 134, 44, 211, 139, 244, 119]

signed_password: [81, 156, 58, 138, 61, 230, 99, 104, 126, 6, 201, 103, 213, 123, 62, 179, 82, 200, 83, 175, 90, 95, 138, 75, 1, 147, 71, 171, 103, 3, 169, 41, 15, 16, 210, 127, 115, 214, 16, 148, 234, 242, 84, 114, 224, 36, 120, 167, 62, 182, 19, 15, 8, 91, 111, 226, 167, 212, 231, 109, 64, 17, 161, 226, 144, 39, 86, 232, 132, 148, 226, 7, 207, 156, 130, 2, 209, 157, 140, 150, 230, 126, 161, 150, 71, 86, 27, 253, 32, 9, 147, 18, 51, 240, 7, 248, 207, 143, 239, 194, 14, 16, 204, 149, 193, 102, 221, 68, 219, 108, 231, 51, 30, 141, 250, 63, 78, 140, 56, 5, 46, 78, 74, 228, 248, 85, 182, 197]
```

Зовнішня система повинна за допомогою свого Private ключа підписати email та password, використовуючи алгоритм хешування SHA1. 
Використаємо в якості прикладу email та password з кроку 2, а ключ Private з кроку 1.

Зверніть увагу, що підписувати треба email та password, що були надані сервісом у початковому вигляді, а не зашифровані на кроці 2 encrypted_email та encrypted_password.

- Зовнішня система POST запитом відправляє на ендпоінт «Авторизація» сервісу чотири поля:
 - поле encrypted_email, що отримане на кроці 2;
 - поле encrypted_password, що отримане на кроці 2;
 - поле signed_email, що отримане на кроці 3;
 - поле signed_password, що отримане на кроці 3.

Сервіс після отримання даних спочатку розшифровує encrypted_email та encrypted_password за допомогою свого внутрішнього ключа Private, а потім перевіряє цифровий підпис signed_email та signed_password за допомогою ключа Public зовнішньої системи, отриманого сервісом під час обміну Public ключами на кроці 1.

Якщо розшифровані дані пройшли успішну звірку та підписи валідні, то сервіс генерує два токени – access_token та security_token, повертаючи їх зовнішній системі.

> Приклад Body  POST запиту:


```json
{
    "encrypted_email": "G3iW/QhCBK41zs+s9RaNvzDOAzvhAX2bQ4FJQoHcmLUsvhpaDWyLTnOZw5++ivrNjxoaBhu6xme3d/oCGoXe+w7nzBEf9WuR0qO0qS/UzKStWznjhPeD1DLda8lAHs2gt8e/3ZD4IgCjGPB6qOVQ46qam8SJ0rHyWN86cyDYFug=",
    "encrypted_password":"gSdSkqR0nzPHXiSlryKot2FuD1N2HZMsdZqqvWc7lYRcYdMMuEpQLiI079wNriZ9ECfJqYMNkKXryW8y4ahYAWF+WIplDhxv6nbA3fz3CYDD3b7eZ9V0Mk7ups6QVw4zDfr9oeY2hY2IDvSETVdpb4L4REXRCuluwXDxDQJ0cYY=",
    "signed_email": [110, 189, 95, 64, 198, 150, 251, 109, 222, 148, 192, 201, 150, 5, 61, 51, 198, 102, 224, 40, 132, 29, 241, 180, 77, 125, 200, 85, 3, 35, 66, 87, 64, 76, 136, 163, 99, 109, 27, 252, 184, 101, 29, 196, 72, 195, 158, 91, 239, 111, 44, 163, 113, 129, 66, 103, 140, 188, 156, 220, 221, 15, 221, 131, 0, 120, 200, 117, 129, 79, 123, 163, 249, 63, 177, 165, 99, 227, 94, 253, 55, 5, 111, 74, 28, 202, 171, 179, 45, 129, 82, 227, 22, 137, 168, 119, 182, 128, 174, 68, 83, 160, 33, 75, 210, 191, 82, 131, 223, 33, 91, 144, 216, 56, 127, 189, 114, 21, 214, 39, 65, 28, 134, 44, 211, 139, 244, 119],
    "signed_password": [81, 156, 58, 138, 61, 230, 99, 104, 126, 6, 201, 103, 213, 123, 62, 179, 82, 200, 83, 175, 90, 95, 138, 75, 1, 147, 71, 171, 103, 3, 169, 41, 15, 16, 210, 127, 115, 214, 16, 148, 234, 242, 84, 114, 224, 36, 120, 167, 62, 182, 19, 15, 8, 91, 111, 226, 167, 212, 231, 109, 64, 17, 161, 226, 144, 39, 86, 232, 132, 148, 226, 7, 207, 156, 130, 2, 209, 157, 140, 150, 230, 126, 161, 150, 71, 86, 27, 253, 32, 9, 147, 18, 51, 240, 7, 248, 207, 143, 239, 194, 14, 16, 204, 149, 193, 102, 221, 68, 219, 108, 231, 51, 30, 141, 250, 63, 78, 140, 56, 5, 46, 78, 74, 228, 248, 85, 182, 197]
}
```

> Приклад Body відповіді у разі успіху:


```json
{
    "message": "Токени отримано",
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjgwMjcwNzc5LCJpYXQiOjE2ODAxODQzNzksImp0aSI6IjQ4NGU0ZjM0NjkxYzQwMWY5NmFhYTYwNDEwY2M2ZWQyIiwidXNlcl9pZCI6MzZ9.WrMDUfH7Tqm_sju9fjSrBSxjgG9Nvq_87gC1ZZ0pdH8",
    "security_token": "s1SjglETjq5P1TpOUsKJ7wu3yqXVvMrW"
}
```

У разі помилки повертається лише поле «error», що містить інформацію про помилку.

## Можливі помилки: 
 - Повідомлення *«Виникла помилка під час дешифрування»* може вказувати на те, що передані дані encrypted_email та/або encrypted_password надійшли в неприпустимому форматі;
 - Повідомлення *«Виникла помилка під час перевірки підпису»* може вказувати на те, що передані дані signed_email та/або signed_password надійшли в неприпустимому форматі;
 - Повідомлення *«Зашифровані та/або підписані дані надано невірно. Перевірте правильність наданих даних»* може вказувати на те, що дані розшифрувалися без помилки, але розшифровані email та password не відповідають підписаним даним;
 - Повідомлення *«Такого користувача не існує»* може вказувати на те, що після розшифрування поле email виявилося не відповідним полю email, що було надано зовнішній системі сервісом;
 - Повідомлення *«Пароль невірний»* може вказувати на те, що після розшифрування поле password виявилося не відповідним полю password, що було надано зовнішній системі сервісом.

# Метод «Створення короткої заявки»
`POST https://api.leadleader.com.ua/api/partners/input/create-short-deal/`

Для створення короткої заявки на сервісі Lead Leader потрібно надіслати наступні дані:

| Назва поля           | Тип значення                      | Обов'язкове | Опис                                |
| -------------------- | --------------------------------- | ----------- | ----------------------------------- |
| clientInfo/PIB       |	string                           | Так         |	Прізвище, ім’я та ім’я по батькові |
| clientInfo/telephone |	string	                         | Так         |	Мобільний телефон |
| clientInfo/stateCode |	string                           | Так         |	ІНН |
| clientInfo/activity  |	string                           | Так |	Вид діяльності |
| clientInfo/email     |	string                           | Ні |	Електронна пошта |
| clientInfo/city      |	string                           | Ні |	Місто |
| clientInfo/region    |	string                           | Ні |	Область |
| termin               |	int                              | Так |	Термін |
| summa                |	decimal                          | Так |	Бажана сума кредиту |
| security_token       |	string                           | Так |	Одноразовий токен, що отримується під час авторизації (див. Метод «Авторизація») |

Зовнішня система повинна надіслати дані на ендпоінт методу POST запитом. У відповідь на запит у разі успіху зовнішня система отримає повідомлення про створену заявку та ID створеної заявки на сервісі.

> Приклад Body POST запиту:

```
Headers: {
  «Authorization»: «Bearer » + access_token
}
```
```json
{
    "clientInfo": {
        "PIB": "Іваненко Іван Іванович",
        "telephone": "0996666666",
        "stateCode": "1111122222",
        "activity": "Студент",
        "email": "example@gmail.com",
        "city": "Київ"
    },
    "termin": 12,
    "summa": 6000.00,
    "security_token": "s1SjglETjq5P1TpOUsKJ7wu3yqXVvMrW"
}
```

> Приклад Body відповіді у разі успіху: 

```json
{
    "message": "Заявку було успішно створено",
    "deal_id": 24
}
```

Зверніть увагу на декілька важливих моментів:

- При надсиланні запиту зовнішній системі потрібно в Headers вказати ключ «Authorization», який потрібен для Bearer аутентифікації. JWT токен отримується полем access_token під час запиту на метод Lead Leader «Авторизація».
- Інший токен, який метод Lead Leader «Авторизація» повертає полем security_token, передається зовнішньою системою у тілі запиту разом з полями, що містять інформацію про клієнта.
- Токени є одноразовими, тобто кожен раз перед запитом на створення короткої заявки зовнішня система повинна авторизуватися в сервісі Lead Leader за допомогою методу «Авторизація», отримавши нові security_token та access_token.
- Метод «Створення короткої заявки» може повернути помилку у разі не відповідності типу значення переданих даних типам, що вказані у таблиці.
- Поле deal_id, що повертається зовнішній системі у відповідь на запит, є цілим числом типу Integer.

# Метод «Отримання поточного статусу короткої заявки»

`GET https://api.leadleader.com.ua/api/partners/input/check-status/`

За допомогою цього методу зовнішня система має змогу отримати поточний статус короткої заявки, надіславши сервісу ID заявки.

| Назва поля |	Тип значення |	Обов’язкове	| Опис |
| ---------- | ------------- | ------------ | ---- |
| deal_id	   | int	| Так	 | ID короткої заявки |
| security_token |	string	| Так |	Одноразовий токен, що отримується під час авторизації (див. Метод «Авторизація») |

Зовнішня система повинна надіслати дані на ендпоінт методу POST запитом. У відповідь на запит у разі успіху зовнішня система отримає повідомлення про успіх та поточний статус короткої заявки.

> Приклад Body POST запиту:

```
Headers: {«Authorization»: «Bearer » + access_token}
{
    "deal_id": 24,
    "security_token": "7UwDpkCAXWJzxjNG4nPm5ysvcF09uKTY"
}
```

> Приклад Body відповіді у разі успіху: 

```json
{
    "message": "Статус отримано",
    "status": "В обробці"
}
```

Зверніть увагу на декілька важливих моментів:

- При надсиланні запиту зовнішній системі потрібно в Headers вказати ключ «Authorization», який потрібен для Bearer аутентифікації. JWT токен отримується полем access_token під час запиту на метод Lead Leader «Авторизація;
- Інший токен, який метод Lead Leader «Авторизація» повертає полем security_token, передається зовнішньою системою у тілі запиту разом з полем, що містить ID короткої заявки;
- Токени є одноразовими, тобто кожен раз перед запитом на отримання поточного статусу короткої заявки зовнішня система повинна авторизуватися в сервісі Lead Leader за допомогою методу «Авторизація», отримавши нові security_token та access_token;
- Метод «Отримання поточного статусу короткої заявки» може повернути помилки у деяких випадках: у разі, якщо заявки з таким ID не існує, або при надсиланні поля deal_id іншим типом даних, або у разі внутрішнього збою сервісу. Кожен тип помилки повертається відповідним повідомленням для зовнішньої системи.
