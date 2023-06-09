# План автоматизации тестирования сервиса

## Задача:
Автоматизировать сценарии тестирования покупки тура "Путешествие дня"

## Артефакты:
SUT aqa-shop.jar

## Предусловия:
Тестируемое приложение запускается по инструкции, указанной в файле README.md

## Карты, представленные для тестирования (файл data.json):

* 4444 4444 4444 4441, status APPROVED
* 4444 4444 4444 4442, status DECLINED

## Тестируемые Базы данных:

* MySql
* PostgreSQL
## 1. Перечень автоматизируемых сценариев
### 1.1 Позитивные сценарии
### "_Успешная покупка тура картой со статусом APPROVED_"

- Нажать "Купить"
- Вввести в поля формы валидные данные
- Нажать "Отправить"

Ожидаемый результат: Оплата проходит(данные об оплате появляются в базе). Появляется сообщение об успешной покупке тура.
### "_Успешная покупка тура в кредит картой со статусом APPROVED_"

- Нажать "Купить в кредит"
- Вввести в поля формы валидные данные
- Нажать "Отправить"

Ожидаемый результат: Оплата проходит(данные об оплате появляются в базе). Появляется сообщение об успешной покупке тура.
### "_Покупка тура картой со статусом DECLINED_"

- Нажать "Купить"
- Вввести в поля формы валидные данные
- Нажать "Отправить"

Ожидаемый результат: Оплата не проходит(в базе данных появляется информация, что покупка отклонена). Появляется
сообщение об ошибке

### "_Покупка тура в кредит картой со статусом DECLINED_"

- Нажать "Купить в кредит"
- Вввести в поля формы валидные данные
- Нажать "Отправить"

Ожидаемый результат: Оплата не проходит(в базе данных появляется информация, что покупка отклонена). Появляется
сообщение об ошибке


### 1.2 Негативные тестовые сценарии
В негативных тестовых сценариях будут проведены следующие проверки:
### "_Ввод неполных данных во все поля при покупке_"

- Зайти на страницу покупки
- Нажать кнопку "купить"
- Ввести номер карты: 4444 4444 4444 444
- Ввести месяц: 1
- Ввести год: 2
- Ввести владельца: Ivan
- Ввести cvc: 12
- Нажать кнопку: "продолжить"

Ожидаемый результат: Поля подсчечиваются красным, кнопка "продолжить" не кликабельна, появляется подсказка, что не все поля заполнены Запись в БД не появляется

### "_Проверка поля номер карты_"

1. Ввести одинаковые цифры
2. Ввести нули
3. Ввести 4 цифры
4. Ввести 17 цифр
5. Ввести текст в поле

Ожидаемый результат:

1. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данных карты не существует, запись в БД не появляется
2. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данные карты введены некорректно, запись в БД не появляется
3. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
4. Поле не дает ввести 17 цифр, максимальное количество допустимых символов 16, запись в БД не появляется
5. Поле не дает ввести текст, возможен только ввод цифр, запись в БД не появляется

### "_Проверка поля владелец_"

1. Ввести 1 букву
2. Ввести невалидного владельца
3. Ввести 20 букв без пробела
4. Ввести только фамилию на английском
5. Ввести русские буквы
6. Ввести цифры
7. Ввести строчные буквы
8. Ввести ФИ слитно

Ожидаемый результат:

1. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
2. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данные введены некорректно, запись в БД не появляется
3. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данные введены некорректно, запись в БД не появляется
4. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
5. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
6. Поле не дает ввести русские буквы, ввод возможен только на английском, запись в БД не появляется
7. Поле не дает ввести цифры, возможен только ввод букв, запись в БД не появляется
8. Поле конвертирует буквы в прописные автоматически, запись в БД не появляется
9. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данные введены некорректно, запись в БД не появляется
10. Данные не проходят проверку, кнопка "продолжить" не кликабельна, система выдает ошибку, что данные введены некорректно, запись в БД не появляется

### "_Проверка поля месяц_"

1. Ввести невалидный месяц
2. Ввести буквы
3. Ввести 3 цифры
4. Ввести нули

Ожидаемый результат:

1. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется
2. Поле не дает ввести буквы, возможен только ввод цифр, запись в БД не появляется
3. Кнопка "продолжить" не кликабельна, система подсвечивае, т поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
4. Поле не дает ввести больше двух цифр, запись в БД не появляется
5. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется

### "_Проверка поля год_"

1. Ввести невалидный год
2. Ввести буквы
3. Ввести 3 цифры
4. Ввести нули

Ожидаемый результат:

1. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется
2. Поле не дает ввести буквы, возможен только ввод цифр, запись в БД не появляется
3. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены не полностью, запись в БД не появляется
4. Поле не дает ввести больше двух цифр, запись в БД не появляется
5. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется

### "_Проверка поля cvv_"

1. Ввести невалидный cvv
2. Ввести буквы
3. Ввести 4 цифры
4. Ввести нули

Ожидаемый результат:

1. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется
2. Поле не дает ввести буквы, возможен только ввод цифр, запись в БД не появляется
3. Поле не дает ввести больше четырех цифр, запись в БД не появляется
4. Кнопка "продолжить" не кликабельна, система подсвечивает поле и дает подсказку, что данные введены некорректно, запись в БД не появляется

### "_Оплата по карте при наличии одного незаполненного поля_"

предусловия:
- после каждого шага нажать кнопку "продолжить"

Шаги:
1. Ввести все данные данные кроме номера карты
2. Ввести все данные кроме владельца
3. Ввести все данные кроме года
4. Ввести все данные кроме месяца
5. Ввести все данные кроме cvv

Ожидаемый результат: кнопка "продолжить" не кликабельна после каждого шага, система подсвечивает пустое поле красным и выдает подсказку "заполните поле", запись в БД не появляется

### "_Покупка тура по карте с истекшим сроком годности_"

Шаги:
1. Ввести валидный номер карты
2. Ввести прошлый месяц
3. Ввести текуший год
4. Ввести валидного владельца
5. Ввести валидный cvv

Ожидаемый результат: Оплата отклонена, банк не одобрил операцию. Появилось уведомление с текстом "Ошибка! Банк отказал в проведении операции". В БД появилась запись со статусом DECLINED

## 2. Перечень используемых инструментов с обоснованием выбора
1. **Java 11**  
   Универсальный язык, позволяющий работать на большинстве ОС и различном оборудовании.
1. **IntelliJ IDE**  
   Многофункциональная среда разработки, бесплатная. Хорошая интеграция в GitHub, широкая поддержка расширений и плагинов для тестирования.
1. **Git**  
   Система контроля версий. Бсплатность, возможность параллельной разработки, хорошая интеграция с IntelliJ IDEA.
1. **JUnit5**  
   Тестовый фреймворк, совместимый с JVM и IntelliJ IDEA, содержит все необходимые аннотации.
1. **Gradle**  
   Система сборки проекта. Имеет простой и понятный код, небольшого объема, в сравнению с Maven. Проще подключать внешние зависимости.
1. **Lombok**  
   Плагин для создания аннотаций, заменяющих значительное количество однообразных конструкторов JAVA таких как getters, setters и пр.
1. **Selenide**  
   Фреймворк для автоматизированного тестирования веб-приложений на основе Selenium WebDriver. Подключение веб-драйвера происходит автоматически, простое написание кода тестов.
1. **JavaFaker**  
   Плагин для генерации случайных данных для тестов. Болшое количество настроек, бесплатный, достаточная локализация для России.
1. **Docker**
   Система контейризации. Будет использована для имитации работы IT-системы банка посредством развёртывания БД MySQL, PostgreSQL, запуск самого приложения через Node.js.
1. **Appveyor**  
   Система CI. Непрерывный контроль интеграции кода. Бесплатный, простое подключение и настройка, удобная интеграция с GitHub.
1. **Allure Report**  
   Система подготовки отчётов. Бесплатное решение. Хорошая информативная визуализация отчётов. Позволяет отслеживать данные на протяжении времени

## 3. Перечень и описание возможных рисков при автоматизации
### Перечень и описание возможных рисков при автоматизации:
* Возможны ошибки при написании автотестов;
* Возможны ошибки в автотестах, связанные с техническим сбоем;
* Возможны ошибки в автотестах, в связи с изменением кода;
* Неоправданная стоимость и затраты на автоматизацию тестирования;
* Возможен некорректный запуск симулятора банковских карт;
* Возможны сложности при настройке двух СУБД ("MySQL" и "PostgreSQL"), и корректном подключении к каждой из них.

## 4. Интервальная оценка с учётом рисков (в часах)
1. Планирование автоматизации тестирования - 5-7 часов
1. Написание кода тестов - 35-65 часов
1. Подготовка отчётных документов по итогам автоматизированного тестирования - 10-12 часов
1. Подготовка отчётных документов по итогам автоматизации - 4-7 часов

## 5. План сдачи Дипломной работы.
1. Готовность авто-тестов — 29.05.2023;
1. Подготовка отчетов по результатам прогона тестов — 1.06.2023;
1. Подготовка отчета по итогам автоматизации — 3.06.2023;
