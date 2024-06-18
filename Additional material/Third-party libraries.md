```
    В данном файле приведены сторонние библиотеки java, которые могут пригодиться в работе
```

# Cодержание

- [JCommander](#jcommander) - **Обработка параметров командой строки**
- [JCDP](#jcdp) - **Цветная печать в терминале**
- [JDBC (PostgreSQL)](#jdbc-postgresql) - **Подключение к PostgreSQL через java**
    - [Основные методы JDBC](#основные-методы-jdbc)
    - [Пример использования методов JDBC](#пример-использования-методов-jdbc)

## JCommander

`JCommander` - это библиотека для обработки аргументов командной строки в Java. Она предоставляет удобные средства для определения и разбора параметров командной строки, позволяя легко создавать приложения с гибкими и понятными интерфейсами командной строки.

**Подключение для Maven:**
```xml
    <dependency>
        <groupId>com.beust</groupId>
        <artifactId>jcommander</artifactId>
        <version>1.82</version>
    </dependency>
```

**Пример использования JCommander:**

```java
import com.beust.jcommander.JCommander;
import com.beust.jcommander.Parameter;

public class MyApp {
    @Parameter(names = {"-username", "-u"}, description = "User's name")
    private String username;

    @Parameter(names = {"-password", "-p"}, description = "User's password")
    private String password;

    @Parameter(names = {"-verbose", "-v"}, description = "Enable verbose mode")
    private boolean verbose = false;

    public static void main(String[] args) {
        MyApp app = new MyApp();
        JCommander.newBuilder()
                .addObject(app)
                .build()
                .parse(args);

        app.run();
    }

    public void run() {
        System.out.println("Username: " + username);
        System.out.println("Password: " + password);
        System.out.println("Verbose mode: " + verbose);
    }
}
```

**Ссылки для скачивания**: 
* https://repo1.maven.org/maven2/com/beust/jcommander/1.72/jcommander-1.72.jar
* http://www.java2s.com/Code/Jar/j/Downloadjcommanderjar.htm

**Документация**:
* https://jcommander.org/

## JCDP

`JCDP` (Java Colored Debug Printer) — это библиотека для Java, которая позволяет разработчикам выводить на консоль цветной текст. Эта библиотека упрощает форматирование сообщений для отладки и логгирования, делая вывод более читабельным и структурированным.

**Подключение для Maven:**
```xml
    <dependency>
        <groupId>com.diogonunes</groupId>
        <artifactId>JCDP</artifactId>
        <version>2.0.3.1</version>
    </dependency>
```

**Пример использования JCDP:**
```java
import com.diogonunes.jcdp.color.api.Ansi;
import com.diogonunes.jcdp.color.ColoredPrinter;
import com.diogonunes.jcdp.color.api.Ansi.FColor;
import com.diogonunes.jcdp.color.api.Ansi.BColor;

public class JCDPExample {
    public static void main(String[] args) {
        // Создаем экземпляр ColoredPrinter с базовой конфигурацией
        ColoredPrinter cp = new ColoredPrinter.Builder(1, false)
            .foreground(FColor.WHITE).background(BColor.BLUE)   // Цвет текста и фона
            .build();

        // Печать сообщения с конфигурацией по умолчанию
        cp.println("This is a default message.");

        // Печать сообщения с измененными цветами текста и фона
        cp.print("This is a message with different colors.", Ansi.Attribute.NONE, FColor.RED, BColor.YELLOW);

        // Печать сообщения с жирным текстом
        cp.println(" This is a bold message.", Ansi.Attribute.BOLD, FColor.GREEN, BColor.NONE);
        
        // Закрываем принтер
        cp.clear();
    }
}
```

**Ссылки для скачивания**: 
* https://repo1.maven.org/maven2/com/diogonunes/JCDP/4.0.0/JCDP-4.0.0.jar
* https://mavenlibs.com/jar/file/com.diogonunes/JCDP

**Документация**:
* https://dialex.github.io/JColor/index-all.html