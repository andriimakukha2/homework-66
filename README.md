Express Authentication Project

📌 Опис

Цей проект є базовим веб-додатком, що використовує Express для аутентифікації користувачів за допомогою Passport.js. Він реалізує:
	•	Реєстрацію та вхід користувачів
	•	Захищені маршрути для авторизованих користувачів
	•	API для CRUD-операцій з користувачами
	•	Обробку великих даних за допомогою курсора MongoDB
	•	Агрегаційні запити для отримання статистичних даних
	1.	Клонуйте репозиторій:

📌 Використані технології
	•	Backend: Node.js, Express.js
	•	База даних: MongoDB (Mongoose)
	•	Аутентифікація: Passport.js, bcryptjs
	•	Сесії: express-session, cookie-parser, connect-flash
	•	Шаблонізатор: EJS (або Pug у деяких частинах проєкту)
	•	Оточення: dotenv

 📌 Встановлення та налаштування

1️⃣ Клонування репозиторію
```bash
git clone <посилання на репозиторій>
cd <назва_проекту>.

2️⃣ Встановлення залежностей
```bash
npm install

3️⃣ Налаштування змінних середовища

Створіть файл .env у кореневій директорії та додайте:
```bash
SESSION_SECRET=your-session-secret
MONGO_URI=your-mongodb-uri
PORT=3001

4️⃣ Запуск сервера
```bash
npm start

Сервер буде доступний за адресою: http://localhost:3001.

📌 Структура проекту

/project
  /public
    /styles
      styles.css
  /views
    layout.pug
    index.pug
  /routes
    auth.js
    settings.js
    users.js
  /models
    User.js
  server.js
  .env
  README.md

📌 Основні функції

🔹 Аутентифікація
	•	✅ Реєстрація користувача (з перевіркою email та хешуванням пароля)
	•	✅ Вхід користувача (з перевіркою пароля)
	•	✅ Захищені маршрути (доступ тільки для авторизованих користувачів)
	•	✅ Збереження стану авторизації за допомогою сесій

🔹 CRUD-операції з користувачами
	•	✅ Створення одного користувача (POST /userData/insertOne)
	•	✅ Створення кількох користувачів (POST /userData/insertMany)
	•	✅ Оновлення одного користувача (PUT /userData/updateOne/:id)
	•	✅ Оновлення кількох користувачів (PUT /userData/updateMany)
	•	✅ Заміна одного користувача (PUT /userData/replaceOne/:id)
	•	✅ Видалення одного користувача (DELETE /userData/deleteOne/:id)
	•	✅ Видалення кількох користувачів (DELETE /userData/deleteMany)
	•	✅ Пошук користувачів з проекцією (GET /userData/find)

🔹 Нові функції
	•	✅ Використання курсорів для обробки великих обсягів даних
	•	/userData/findWithCursor — передача даних через курсор
	•	✅ Агрегаційні запити
	•	/userData/aggregate — отримання статистики (середній вік, кількість унікальних email)
 	

📌 API-ендпоїнти
🏷 Маршрут	                🛠 Метод	🔍 Опис
/auth/register	                POST	        Реєстрація користувача
/auth/login	                POST	        Вхід користувача
/auth/logout	                GET	        Вихід користувача
/userData/insertOne	        POST	        Додавання одного користувача
/userData/insertMany	        POST	        Додавання кількох користувачів
/userData/updateOne/:id	        PUT	        Оновлення даних користувача
/userData/updateMany	        PUT	        Оновлення кількох користувачів
/userData/deleteOne/:id	        DELETE	        Видалення одного користувача
/userData/deleteMany	        DELETE	        Видалення кількох користувачів
/userData/find	                GET	        Пошук користувачів (із проекцією полів)
/userData/findWithCursor	GET	        Отримання користувачів через курсор
/userData/aggregate	        GET	        Агрегаційна статистика


📌 Перевірка через Postman

Для тестування API можна використовувати Postman або cURL.

📌 Приклад запиту на додавання одного користувача

Метод: POST
URL: http://localhost:3001/users/insertOne
Заголовки:
{
  "Authorization": "Bearer {ВАШ_ТОКЕН}",
  "Content-Type": "application/json"
}
Тіло запиту:
{
  "name": "John Doe",
  "email": "johndoe@example.com",
  "password": "securepassword",
  "age": 28
}
📌 Приклад отримання статистики (агрегаційний запит)

Метод: GET
URL: http://localhost:3001/userData/aggregate

Очікувана відповідь:
{
  "averageAge": 29.5,
  "uniqueEmails": 150,
  "totalUsers": 500
}

📌 Можливі помилки та їх вирішення

❌ Помилка	                 🔍 Можлива причина	                   🛠 Рішення
400 Bad Request	                 Неправильний формат JSON	           Перевірте тіло запиту
401 Unauthorize                  Відсутній або неправильний токен	   Додайте Authorization: Bearer {ВАШ_ТОКЕН}
403 Forbidden	                 Немає доступу	                           Переконайтеся, що користувач авторизований
404 Not Found	                 Користувача не знайдено	           Перевірте правильність _id
500 Internal Server Error	 Проблема із сервером або базою даних	   Перевірте логи сервера (npm start)

📌 Висновок

✅ Цей проект містить повну реалізацію аутентифікації, захищені маршрути, CRUD-операції та ефективну обробку даних через курсори та агрегаційні запити.
🚀 Використовуйте Postman або будь-який REST-клієнт для тестування API.

