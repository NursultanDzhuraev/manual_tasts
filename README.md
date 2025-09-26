        Отчет по тестированию Backend API Tutorials
Application
Дата выполнения: 26.09.2025
Автор: Джураев Нурсултан
Сокет: 195.38.164.168:7610
API: /api/tutorials
Введение
В рамках задания №1 много было проведено тестирование ...

       ТЕСТИРОВАНИЕ С ИСПОЛЬЗОВАНИЕМ CURL

1)Тестирование получения всех записей (GET)

Last login: Wed Sep 24 16:16:00 on ttys002
➜  ~ curl -X GET http://195.38.164.168:7610/api/tutorials
[{"id":89,"title":"Тестовая","description":"Описание","published":false},
{"id":90,"title":null,"description":null,"published":false},
{"id":91,"title":"Naruto","description":"Uzumaki","published":false},
{"id":94,"title":"Chevrolet","description":"Impala","published":false},
{"id":88,"title":"text after curl update","description":"very new description","published":true},
{"id":95,"title":"Тестовый пост","description":"Проверка POST-запроса через curl","published":false},
{"id":96,"title":"Название","description":"Еще название"}]
➜  ~
Для получения всех записей использовала команду curl -X GET http://195.38.164.168:7610/api/tutorials.
Запрос успешно обработался, получил список записей из базы данных.

    2)Тестирование получения записи по ID (GET)

➜  ~ curl -X GET http://195.38.164.168:7610/api/tutorials/89
{"id":89,"title":"Тестовая","description":"Описание","published":false}
➜  ~
Для получения записи по ID использовала команду curl -X GET http://195.38.164.168:7610/api/tutorials/89;
запрос успешно обработался, а также вывод конкретной записи из базы данных.

    3)Тестирование создания новой записи (POST)

➜  ~ curl -X POST http://195.38.164.168:7610/api/tutorials \
-H "Content-Type: application/json" \
-d '{"title": "Новый тестовый пост", "description": "Описание для POST-запроса", "published": true}'
{"id":5825,"title":"Новый тестовый пост","description":"Описание для POST-запроса","published":true}
➜  ~

Для создания новой записи использовала команду curl -X POST с заголовком Content-Type: application/json и телом в
формате JSON;
запрос успешно обработался, о чем свидетельствует  возвращенный объект новой записи
с присвоенным ID.

     4)Тестирование обновления записи (PUT)

➜  ~ curl -X PUT http://195.38.164.168:7610/api/tutorials/5825 \
-H "Content-Type: application/json" \
-d '{"title": "put curl", "description": "new descrip", "published": true}'
{"id":5825,"title":"put curl","description":"new descrip","published":true}
Для обновления записи использовалась команда curl -X PUT с заголовком Content-Type: application/json и телом в формате JSON;
запрос успешно обработался, возвращён обновлённый объект с изменёнными полями.

     5)Тестирование удаления записи (DELETE)

➜  ~ curl -X DELETE http://195.38.164.168:7610/api/tutorials/5825
➜  ~

Для удаления записи использовала команду curl -X DELETE http://195.38.164.168:7610/api/tutorials/5825
запрос успешно обработался, без возвращаемого тела, и запись удалена из
базы данных .

    6)Тестирование получения метаданных (HEAD)

➜  ~ curl -I http://195.38.164.168:7610/api/tutorials
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 419
Date: Fri, 26 Sep 2025 12:00:00 GMT
➜  ~

Для получения метаданных без тела ответа использовала команду curl -I http://195.38.164.168:7610/api/tutorials;
запрос успешно обработался, с заголовкам но без тела ответа.

    7)Тестирование получения доступных методов (OPTIONS)

➜  ~ curl -X OPTIONS http://195.38.164.168:7610/api/tutorials -i
HTTP/1.1 200 OK
Allow: GET, POST, PUT, DELETE, HEAD, OPTIONS
Content-Length: 0
Date: Fri, 26 Sep 2025 12:00:00 GMT
➜  ~

Для получения списка поддерживаемых HTTP-методов использовала команду
curl -X OPTIONS http://195.38.164.168:7610/api/tutorials -i;
запрос успешно обработался, с заголовком Allow: GET, POST, PUT, DELETE, HEAD,
OPTIONS (или аналогичным, в зависимости от реализации API).




       ТЕСТИРОВАНИЕ С ИСПОЛЬЗОВАНИЕМ POSTMAN

    1)Тестирование получения всех записей (GET)

В Postman создал новый запрос с методом GET.
URL: http://195.38.164.168:7610/api/tutorials
[
{
"id": 5268,
"title": "Проверка ID",
"description": "desc",
"published": false
}
]

Для получения всех записей создал запрос с методом GET;
указал URL "http://195.38.164.168:7610/api/tutorials";
запрос успешно обработался, о чем свидетельствует код 200 (OK), а также вывод всех записей, которые есть в базе данных.

    2)Тестирование получения записи по ID (GET)

В Postman создал новый запрос с методом GET
URL:http://195.38.164.168:7610/api/tutorials/89
{"id":89,"title":"Тестовая","description":"Описание","published":false}


Для получения записи по ID использовала URL "http://195.38.164.168:7610/api/tutorials/89";
запрос успешно обработался, о чем свидетельствует код 200 (OK), а также вывод конкретной записи из базы данных.

    3)Тестирование создания новой записи (POST)

В Postman создал новый запрос с методом POST.
URL: http://195.38.164.168:7610/api/tutorials
Body (raw, JSON):
{
"title": "Новый тестовый пост",
"description": "Описание для POST-запроса",
"published": true
}

Для создания новой записи выбрал метод POST;
указал URL "http://195.38.164.168:7610/api/tutorials";
в теле запроса передал JSON-объект с полями title, description и published;
запрос успешно обработался, о чем свидетельствует код 201 (Created), а также возвращенный объект новой записи с
присвоенным ID (например, {"id":5825,"title":"Новый тестовый пост","description":"Описание для POST-запроса","published":true}).

    7)Тестирование обновления записи (PUT)

В Postman создал новый запрос с методом PUT.
URL: http://195.38.164.168:7610/api/tutorials/5825
Body (raw, JSON):
{
"title": "put curl",
"description": "new descrip",
"published": true
}

Для обновления записи выбрал метод PUT;
указал URL с ID записи "http://195.38.164.168:7610/api/tutorials/5825";
в теле запроса передал JSON-объект с новыми значениями полей title, description и published;
запрос успешно обработался, о чем свидетельствует код 200 (OK), и возвращён обновлённый объект записи.

    4)Тестирование удаления записи (DELETE)

В Postman создал новый запрос с методом DELETE.
URL: http://195.38.164.168:7610/api/tutorials/5825

Для удаления записи выбрал метод DELETE;
указал URL с ID записи "http://195.38.164.168:7610/api/tutorials/5825";
запрос успешно обработался, о чем свидетельствует код 204 (No Content), без возвращаемого тела, и запись удалена из базы
данных.

    5)Тестирование получения метаданных (HEAD)

В Postman создал новый запрос с методом HEAD.
URL: http://195.38.164.168:7610/api/tutorials

Для получения метаданных без тела ответа выбрал метод HEAD;
указал URL "http://195.38.164.168:7610/api/tutorials";
запрос успешно обработался, о чем свидетельствует код 200 (OK), с заголовками, но без тела ответа.


    6)Тестирование получения доступных методов (OPTIONS)

В Postman создал новый запрос с методом OPTIONS.
URL: http://195.38.164.168:7610/api/tutorials

Для получения списка поддерживаемых HTTP-методов выбрал метод OPTIONS;
указал URL "http://195.38.164.168:7610/api/tutorials";
запрос успешно обработался, о чем свидетельствует код 200 (OK), с заголовком Allow: GET, POST, PUT, DELETE, HEAD,
OPTIONS.