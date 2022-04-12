# Сценарии взаимодействия

В результате структурирования которых должны оформится [требования к продуктовым ресурсам](product_resources.md)

## Состояния аудитории

- **Индюк** — базовое состояние аудитории, разрабатывает игру, не знает что существует наш продукт.
- **Посетитель** — индюк посещающий ресурс связанный с нашим продуктом.
- **Пользователь** — посетитель установивший триальную версию нашего продукта.
- **Клиент** — посетитель либо пользователь купивший коммерческую лицензию

### Наследование свойств

```puml
Индюк <|-- Посетитель
Индюк <|-- Пользователь <|-- Клиент
```

## Структура сценариев

#### Обозначения для ресурсов

- **Взаимодействие желаемо**
- Взаимодействие допустимо
- ~~Взаимодействие нежелательно~~

### Осознанности сценария

- **Не прямой поиск** (решение пока не нужно) — индюк "серфит" Unity Asset Store или другой ресурс и натыкается на **потенциально полезный** продукт.
- **Прямой поиск** (решение нужно) — индюк в поиске решения для серверной проверки платежей, либо.
- **Разработка** (нужно разобраться в решении) — пользователь ищет ответ на конкретный вопрос, в попытке разобраться в работе продукта.

### Источники сценариев

- **Unity Asset Store** — основной источник сценариев прямого поиска
- **Google** (или другой поисковик) — если поиск **Unity Asset Store** "подвел"
- **Blog Post** — основной источник траффика и сценариев не прямого поиска, иногда разработки
- **Memory** (bookmark) — основной источник сценариев разработки
- **Unity Editor** — удобный источник сценариев разработки

### Точки конверсии

| Тип конверсии                    | Возможные страницы  |
|----------------------------------|---------------------|
| **Покупка коммерческой версии**  | **STORE**           |
| **Установка триально версии**    | **STORE**           |
| **Нахождение нужной информации** | **DOC**, SOFW, FDBK |

### Матрица пересечения

Нужна для того чтобы сформулировать ключевые задачи к соответсвующим типам ресурсов.

|                  | Не прямой поиск | Прямой поиск               | Разработка                     |
|------------------|-----------------|----------------------------|--------------------------------|
| **Google**       | **STORE**       | **STORE**, LAND, ~~OTHER~~ | **DOC**, BLOG, LAND, ~~OTHER~~ |
| **Asset Store**  | **STORE**       | **STORE**                  | **STORE**                      |
| **Unity Editor** | -               | -                          | **DOC**, FDBK                  |
| **Blog Post**    | **STORE**       | -                          | **DOC**                        |
| **Memory**       | -               | -                          | **LAND**                       |

### Матрица связей

- L — ссылка _возможная_ **обязательная**
- E — встраивание _возможное_


|           | **LAND** | **STORE** | **DOC** | **FDBK** | **SOFW** | **BLOG** |
|-----------|----------|-----------|---------|----------|----------|----------|
| **LAND**  | -        | **L**_E_  | **L**   | **L**    | _L_      | _L_      |
| **STORE** |          | -         | **L**   | **L**    | _L_      | _L_      |
| **DOC**   |          | **L**     | -       | _LE_     | _L_      | _L_      |
| **FDBK**  |          | **L**     | **L**   | -        | **L**    |          |
| **SOFW**  |          | **L**     | **L**   |          | -        |          |
| **BLOG**  |          | _L_       | _L_     |          |          | -        |