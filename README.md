## Дипломный проект профессии "Тестировщик"
___

1. [План тестирования](https://github.com/IgorPyak/DIPLOM/blob/main/Plan.md)
2. [Отчет по итогам автоматизированного тестирования](https://github.com/IgorPyak/DIPLOM/blob/main/Report.md)
3. [Отчет по итогам автоматизации]

### Запуск приложения

Для запуска приложения необходимо следующее ПО:
* IntelliJ IDEA
* Docker

* склонировать репозиторий на свой ПК командой ```git clone https://github.com/IgorPyak/DIPLOM```
* В терминале IntelliJ IDEA с помощью команды ```docker-compose up```  разворачиваем контейнер, необходимый для дальнейшей работы (настройки для запуска контейнера прописаны в файле docker-compose.yml)
* в терминале IntelliJ IDEA запустить SUT: с помощью команды ```java -jar .\artifacts\aqa-shop.jar```
* запустить тесты командой ```./gradlew clean test```
