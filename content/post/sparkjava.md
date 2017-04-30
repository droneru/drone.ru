+++
date = "2017-03-03T15:39:37+03:00"
description = "Spark - A micro framework for creating web applications in Java 8 with minimal effort"
title = "Java мир не обязан быть сложным"
+++

Считается, что разработка веб приложения на java очень сложна: сервлеты, web.xml, EJB сервисы или spring. Написать простую динамическую страницу может оказаться довольно сложным делом. Собрать ear, стартовать сервер, задеплоить. Это оправдано в enterprise мире. Но для очень простого приложения нет смысла использовать инструменты enterprise уровня. С удивлением понял, что многие коллеги просто не знают больше ничего другого. Один из фреймворков, который позволяет создавать простые веб приложения с минимальными усилиями - это [spark](http://sparkjava.com/). Посмотрите как просто и красиво можно написать "hello, world".

```java
import static spark.Spark.*;

public class HelloWorld {
    public static void main(String[] args) {
        port(8080); // Spark will run on port 8080
        get("/hello", (req, res) -> "Hello, world!");
    }
}
```
Теперь остаётся просто запустить и открыть http://localhost:8080/hello. Не нужно поднимать и настраивать JEE сервер. Можно довольно просто упаковать в docker. Хорошо подходит для микросервисов: создавать REST API на нём действительно просто и наглядно. Вместо get [можно было написать post, put, delete](http://sparkjava.com/documentation.html#routes).

Параметры

```java
// matches "GET /hello/foo" and "GET /hello/bar"
// request.params(":name") is 'foo' or 'bar'
get("/hello/:name", (request, response) -> {
    return "Hello: " + request.params(":name");
});
```

Для простых задачек часто имеет смысл вместо привычных, но громозких, инструментов попробовать что-то другое. Не застревать в привычной среде. Мне очень понравилась простота spark.

Сегодня 3 марта [всемирный день писателя](https://ru.wikipedia.org/wiki/%D0%92%D1%81%D0%B5%D0%BC%D0%B8%D1%80%D0%BD%D1%8B%D0%B9_%D0%B4%D0%B5%D0%BD%D1%8C_%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D0%B5%D0%BB%D1%8F). Какой способ отметить праздник может быть лучше, чем начать писать?!
