## Проверка изделия на принадлежность к поставке

### POST /searchSn/

Для авторизации используются ваши текущие логин(**login**):пароль(**password**) в системе b2b.

### Параметры запроса

|Параметр|Тип|Обязательный|Описание|
|---|---|---|---|
| sn | string | да | серийный номер изделия указанный на корпусе |

### Пример запроса

```http
POST /getPrice/
Authorization: Basic
```
```json
{
    "sn": "109EXTRULIFE11"
}
```

### Ответ в случае успеха

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```json
{
    "data": {
        "sn": "109EXTRULIFE11",
        "product": "Внешний аккумулятор Defender ExtraLife",
        "partner": "ООО &quot;Корпоративный стандарт&quot;",
        "date": "09.01.2020"
    },
    "code": "ok"
}
```

### Описание полей ответа

|Параметр|Тип|Описание|
|---|---|---|
| data.sn | string | серийный номер изделия |
| data.product | string | наименование изделия |
| data.partner | string | контрагент приобретавший изделие |
| data.date | string | дата покупки |

### Ответ при отсутствии в базе серийного номера

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```json
{
    "data": "false",
    "code": "ok"
}
```

### Ответ при ошибке авторизации

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
```
```json
{"data":"Access denied","code":"error"}
```