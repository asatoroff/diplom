# Дипломный проект профессии «Тестировщик»
В рамках дипломного проекта требовалось автоматизировать тестирование комплексного сервиса покупки тура, взаимодействующего с СУБД и API Банка.

База данных хранит информацию о заказах, платежах, статусах карт, способах оплаты.

Для покупки тура есть два способа: с помощью карты и в кредит. В приложении используются два отдельных сервиса оплаты: Payment Gate и Credit Gate.

[Ссылка на Дипломное задание](https://github.com/netology-code/qa-diploma).

## Тестовая документация
1. [План тестирования](https://github.com/asatoroff/diplom/blob/master/Documentation/Plan.md);
1. [Отчёт по итогам тестирования](https://github.com/asatoroff/diplom/blob/master/Documentation/%D0%9E%D1%82%D1%87%D1%91%D1%82%20%D0%BE%20%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D0%B4%D1%91%D0%BD%D0%BD%D0%BE%D0%BC%20%D1%82%D0%B5%D1%81%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B8.md);
1. [Отчет по итогам автоматизации](https://github.com/asatoroff/diplom/blob/master/Documentation/%D0%9E%D1%82%D1%87%D1%91%D1%82%20%D0%BE%20%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D0%B4%D1%91%D0%BD%D0%BD%D0%BE%D0%B9%20%D0%B0%D0%B2%D1%82%D0%BE%D0%BC%D0%B0%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8.md)

## Запуск приложения
### Подготовительный этап
1. Установить и запустить IntelliJ IDEA;
1. Установать и запустить Docker Desktop;
1. Скопировать репозиторий с Github [по ссылке](https://github.com/asatoroff/diplom.git).
1. Открыть проект в IntelliJ IDEA.

### Запуск тестового приложения
1. Запустить MySQL, PostgreSQL, NodeJS через терминал командой:
   ```
   docker-compose up
   ```
1. В новой вкладке терминала запустить тестируемое приложение:
   * Для MySQL: 
   ```
   java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar artifacts/aqa-shop.jar
   ```
   * Для PostgreSQL: 
   ```
   java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar artifacts/aqa-shop.jar
   ```
   .
1. Убедиться в готовности системы. Приложение должно быть доступно по адресу:
```
http://localhost:8080/
```

### Запуск тестов
В новой вкладке терминала запустить тесты:
1. Для MySQL: 
   ```
   gradlew clean test -Ddb.url=jdbc:mysql://localhost:3306/app
   ```
1. Для PostgreSQL: 
   ```
   gradlew clean test -Ddb.url=jdbc:postgresql://localhost:5432/app
   ```
### Перезапуск приложения, тестов и/или отчёта
Для перезапуска приложения, тестов и/или отчёта (например, для использования другой БД) необходимо выполнить остановку их работы, нажав в соответствующих вкладках терминала Ctrl+С

## Формирование отчёта о тестировании
В новой вкладке терминала ввести команду:
```
gradlew allureServe
```
Отчёт откроется в браузере автоматически.
