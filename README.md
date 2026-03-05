**Задача 1**

**Сделайте модель в нотации BPMN 2.0 по описанию рабочего потока ниже.**
<img width="3035" height="1696" alt="Screenshot 2026-03-05 183035" src="https://github.com/user-attachments/assets/86a68021-6a16-4abc-acf4-bdc4520197f5" />

**Противоречия и логические нестыковки**

**Синхронизация данных между системами и службами:**

Как происходит синхронизация данных между системами №1, №2 и №3?

Нет взаимодействия между системами

Нет автоматической синхронизации, всё делается вручную?

Почему поддержка закрывает заявку в системе №2 (заявка снабжения)? Обычно закрывает заявку тот отдел, который ее исполнял, подтверждая факт передачи. Если закрывает поддержка, как они узнают, что снабжение реально передало оборудование в логистику?

Вызов логистики происходит по телефону. Где фиксируется задача для логистики? Нет номера накладной, нет заявки в системе логистики. Если груз потеряется, найти крайнего будет невозможно?

**Время обработки заявок:**

Какое время может затратить любая из служб на создание или закрытие заявок ?

Срок обработки заявок на каждом этапе? Это важно для оценки эффективности процесса.

**Обработка неудачных доставок:**

Что происходит, если оборудование не может быть доставлено пользователю? Есть ли процесс обработки таких случаев?

**Процесс согласования:**

Кто согласует заявку на оборудование пользователю(например руководитель отдела)?

Согласование на уровне отдела закупок ?

Нет описания отказов/отклонений: что если заявка пользователя некорректна

**Коммуникация с пользователем:**

Как пользователь получает уведомления о статусе своей заявки? Есть ли уведомления по почте или телефону?

Возможность для пользователя получить обратную связь на промежуточных этапах процесса и отслеживать статус своей заявки.

Почему пользователь не имеет возможность сделать заявку на оборудование через систему N, где может отслеживать статус заявку, а также выполнить оценку выполненных работ?

**Процесс оценки сервиса:**

Пользователь ставит оценку по телефону или пишет письмо с оценкой сервиса, как происходит процесс оценки сервиса технической поддержки? Где и как пользователь может выставить оценку?

**Задача 2**

- Сделать верхнеуровневую постановку в формате User story и описать требования к новой функциональности в формате вариантов использования (Use Case).
- Опционально: нарисовать диаграмму процесса в удобной нотации.

**1\. User Story (верхнеуровневая постановка)**

User Story (продавец):

Как продавец, я хочу опубликовать новый товар в Личном кабинете, чтобы он стал доступен для покупки на маркетплейсе (витрине товаров).

Краткое описание :

Продавец заполняет карточку товара (название, описание, цена, категория, фото, атрибуты), проходит валидацию данных и публикацию, после чего товар появляется в каталоге маркетплейса и доступен для отображения покупателям.

1: Создание карточки товара

- Кнопка "Создать карточку товара" доступна в личном кабинете
- Открывается форма с полями: категория, атрибуты, описание, фото
- Все обязательные поля помечены (\*)
- При сохранении валидируются обязательные поля

1.2: Выбор категории товара

- Доступен поиск по категориям
- Поддерживается многоуровневая навигация (Категория → Подкатегория)
- После выбора категории отображаются соответствующие атрибуты

1.3: Загрузка фотографий

- Поддерживается загрузка нескольких фото (drag & drop и через проводник)
- Отображается прогресс загрузки
- Фото можно удалить или поменять местами
- Первая фотография становится обложкой
- Проверяется формат (JPG, PNG) и размер файла

1.4: Заполнение атрибутов и описания

- Атрибуты отображаются в зависимости от выбранной категории
- Обязательные атрибуты помечены (\*)
- Есть подсказки к полям
- Поддерживается форматирование описания (жирный, списки)
- Автоматическое сохранение черновика каждые 30 сек

2: Управление черновиками

2.1: Сохранение черновика

- Кнопка "Сохранить черновик" доступна на любом этапе заполнения
- Черновик сохраняется без валидации обязательных полей
- Черновик отображается в разделе "Черновики"
- Присваивается статус "Черновик"

2.2: Редактирование черновика

- В разделе "Черновики" отображается список всех черновиков
- Показываются: название, дата изменения, статус
- Кнопка "Редактировать" открывает форму с сохраненными данными
- Можно удалить черновик

3: Отправка на модерацию

3.1: Отправка карточки на модерацию

- Кнопка "Отправить на модерацию" активна только при заполненных обязательных полях
- Перед отправкой показывается превью карточки
- После отправки блокируется редактирование
- Статус меняется на "На модерации"
- Приходит уведомление "Товар отправлен на модерацию"

3.2: Повторная отправка после редактирования

- Доступна для товаров со статусом "Отклонен" и черновиков
- После редактирования обязательна повторная отправка
- Статус меняется на "На модерации"
- Модератор получает уведомление о новой проверке

4: Модерация товаров

4.1: Проверка карточки модератором

- В интерфейсе модератора отображается очередь на проверку
- Показываются все заполненные поля и фото
- Доступны чек-листы соответствия правилам
- Можно оставить комментарий для продавца
- Доступны кнопки "Опубликовать" и "Отклонить"

4.2: Публикация товара

- Доступна только для товаров на модерации
- Статус меняется на "Опубликован"
- Товар появляется в каталоге маркетплейса
- Продавец получает уведомление "Товар опубликован"
- Указывается дата публикации

4.3: Отклонение товара

- Доступна только для товаров на модерации
- Обязательно указать причину отклонения (выбор из списка + комментарий)
- Статус меняется на "Отклонен"
- Продавец получает уведомление с причиной отклонения
- Товар возвращается в редактирование

  <img width="1985" height="1690" alt="Screenshot 2026-03-04 152938" src="https://github.com/user-attachments/assets/aa8677d4-ec0f-43c2-ac3f-1cf7241ccc04" />

<img width="778" height="963" alt="Sequencediagram" src="https://github.com/user-attachments/assets/a8388873-1b2e-4674-a967-50db9e57b6a3" />

&nbsp;**Задача 3**

На картинке (скачать можно по ссылке - <https://drive.google.com/file/d/1fi9JLRvO6bhS1uJJ2PUX8ZTOq0Eq_At0/view?usp=drive_link>) изображен интерфейс регистрации Пользователя (как успешный экран создания Пользователя, так и варианты с ошибками).
```json
openapi: 3.0.3
info:
  title: Book Store Registration API
  description: API для регистрации новых пользователей в системе Book Store.
  version: 1.0.0
servers:
  - url: https://api.demoqa.com/Account/v1
    description: Основной сервер (пример на основе demoqa.com)

paths:
  /users/register:
    post:
      tags:
        - Authentication
      summary: Register a new user
      description: Создает нового пользователя в системе Book Store
      operationId: registerUser
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/RegistrationRequest'
            examples:
              validRegistration:
                summary: Valid registration request
                value:
                  firstName: "Ivan"
                  lastName: "Ivanov"
                  username: "ivan"
                  password: "Password123!"
                  recaptchaToken: "03AGdBqA7Si...recaptcha_token_here..."
      responses:
        '201':
          description: User successfully registered
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RegistrationResponse'
              examples:
                successExample:
                  summary: Successful registration
                  value:
                    userId: "550e8400-e29b-41d4-a716-446655440000"
                    username: "ivan"
                    message: "User Register Successfully"
                    createdAt: "2026-03-04T10:30:00Z"
        '400':
          description: Bad request - validation error or reCAPTCHA failed
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              examples:
                passwordValidationError:
                  summary: Password validation error
                  value:
                    errorCode: "VALIDATION_ERROR"
                    message: "Passwords must have at least one non alphanumeric character, one digit ('0'-'9'), one uppercase ('A'-'Z'), one lowercase ('a'-'z'), one special character and Password must be eight characters or longer"
                    field: "password"
                    timestamp: "2026-03-04T10:30:00Z"
                recaptchaError:
                  summary: reCAPTCHA verification failed
                  value:
                    errorCode: "RECAPTCHA_VERIFICATION_FAILED"
                    message: "Please verify reCaptcha to register!"
                    field: "recaptchaToken"
                    timestamp: "2026-03-04T10:30:00Z"
        '409':
          description: Conflict - user already exists
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              examples:
                userExists:
                  summary: User already exists
                  value:
                    errorCode: "USER_ALREADY_EXISTS"
                    message: "User exists!"
                    field: "username"
                    timestamp: "2026-03-04T10:30:00Z"
        '500':
          description: Internal server error
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              examples:
                internalError:
                  summary: Internal server error
                  value:
                    errorCode: "INTERNAL_SERVER_ERROR"
                    message: "Internal server error"
                    timestamp: "2026-03-04T10:30:00Z"
        '503':
          description: Service unavailable
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              examples:
                serviceUnavailable:
                  summary: Service temporarily unavailable
                  value:
                    errorCode: "SERVICE_UNAVAILABLE"
                    message: "Service temporarily unavailable"
                    timestamp: "2026-03-04T10:30:00Z"

components:
  schemas:
    RegistrationRequest:
      type: object
      required:
        - firstName
        - lastName
        - username
        - password
        - recaptchaToken
      properties:
        firstName:
          type: string
          minLength: 2
          maxLength: 50
          pattern: '^[a-zA-Z\s]+$'
          description: "First name of the user"
          example: "Ivan"
        lastName:
          type: string
          minLength: 2
          maxLength: 50
          pattern: '^[a-zA-Z\s]+$'
          description: "Last name of the user"
          example: "Ivanov"
        username:
          type: string
          minLength: 3
          maxLength: 30
          pattern: '^[a-zA-Z0-9_-]+$'
          description: "Unique username for login"
          example: "ivan"
        password:
          type: string
          minLength: 8
          maxLength: 128
          pattern: "^(?=.*[a-z])(?=.*[A-Z])(?=.*\\d)(?=.*[@$!%*?&])[A-Za-z\\d@$!%*?&]{8,}$"
          description: "Password with complexity requirements"
          example: "Password123!"
        recaptchaToken:
          type: string
          minLength: 10
          description: "Google reCAPTCHA verification token"
          example: "03AGdBqA7Si...recaptcha_token_here..."
    
    RegistrationResponse:
      type: object
      required:
        - userId
        - username
        - message
        - createdAt
      properties:
        userId:
          type: string
          format: uuid
          description: "Unique identifier of the created user"
          example: "550e8400-e29b-41d4-a716-446655440000"
        username:
          type: string
          description: "Username of the registered user"
          example: "ivan"
        message:
          type: string
          description: "Success message"
          example: "User Register Successfully"
        createdAt:
          type: string
          format: date-time
          description: "Timestamp of user creation in ISO 8601 format"
          example: "2026-03-04T10:30:00Z"
    
    ErrorResponse:
      type: object
      required:
        - errorCode
        - message
        - timestamp
      properties:
        errorCode:
          type: string
          description: "Machine-readable error code"
          example: "VALIDATION_ERROR"
        message:
          type: string
          description: "Human-readable error message"
          example: "Passwords must have at least one non alphanumeric character..."
        field:
          type: string
          description: "Field that caused the error (if applicable)"
          example: "password"
        timestamp:
          type: string
          format: date-time
          description: "Timestamp when the error occurred"
          example: "2026-03-04T10:30:00Z"

Пример запроса
{
  "firstName": "Ivan",
  "lastName": "Ivanov",
  "username": "ivan",
  "password": "Password123!",
  "recaptchaToken": "some_token"
}

Пример ответа при успешной регистрации
{
  "status": "success",
  "userId": 123
}

Пример ответа с ошибкой
{
  "errorCode": "USER_ALREADY_EXISTS",
  "message": "User exists!",
  "field": "username",
  "timestamp": "2026-03-04T10:30:00Z"
}

{
  "userId": "550e8400-e29b-41d4-a716-446655440000",
  "username": "ivan",
  "message": "User Register Successfully",
  "createdAt": "2026-03-04T10:30:00Z"
}

{
  "errorCode": "VALIDATION_ERROR",
  "message": "Passwords must have at least one non alphanumeric character, one digit ('0'-'9'), one uppercase ('A'-'Z'), one lowercase ('a'-'z'), one special character and Password must be eight characters or longer",
  "field": "password",
  "timestamp": "2026-03-04T10:30:00Z"
}
```
**Задание 3.2**

<img width="1416" height="1882" alt="Backend" src="https://github.com/user-attachments/assets/1e0f0b0b-a560-46b6-a8c9-85fa34b0b1ec" />


Пошаговый алгоритм

1\. Получение и парсинг запроса

\- Извлечь JSON-тело запроса.

\- Проверить Content-Type на application/json.

\- Если тело пустое или неверный формат - вернуть 400 Bad Request сразу.

2\. Синтаксическая валидация по схеме

\- Проверить соответствие схеме OpenAPI (обязательные поля: username, email, password; типы, minLength/maxLength, pattern для username, format email для email).

\- Если нарушения - собрать ошибки по полям и вернуть 400 с ErrorResponse.

3\. Семантическая валидация полей

\- Username: проверить на пустоту после trim, запретить пробелы/спецсимволы (кроме \_).

\- Email: дополнительно проверить домен (не disposable, как mailinator.com).

\- Password: наличие uppercase/lowercase/цифр/символов (regex), min 8 символов.

\- Если ошибки - 400 с детальными сообщениями по полям.

4\. Проверка уникальности

\- Запрос в БД: SELECT по username и email (CASE INSENSITIVE).

\- Если найдено - 409 Conflict с указанием дублирующего поля.

5\. Дополнительные бизнес-проверки

\- Rate limiting: проверить IP/пользователя на превышение попыток (например, 5/мин).

\- Блокировка подозрительных: проверить email/username на черный список (спам, боты).

\- Если fail - 429 Too Many Requests или 400.

6\. Подготовка данных

\- Хэшировать password (bcrypt/Argon2, salt rounds 12+).

\- Сгенерировать userId (UUID).

\- Нормализовать firstName/lastName (trim, lowercase).

7\. Транзакция БД

\- Начать транзакцию.

\- INSERT в users таблицу с hashed_password, validated_email=false, email_validation_token=UUID.

\- Если OK - commit и перейти к успеху.

\- Rollback при любой ошибке.

8\. Успешный финал и пост-обработка

\- После commit: отправить email с validation token (асинхронно).

\- Вернуть 201 Created с userId и базовыми данными (без password).

\- Логировать событие для аудита.
