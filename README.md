# Exp_2_Simple-Spring-Boot-MVC-Application

## AIM

To develop a simple **Spring Boot MVC (Model-View-Controller) Application** that uses a **Controller** to handle HTTP requests, a **Model** to pass data, and a **View (Thymeleaf)** to render dynamic HTML pages.

---

## ALGORITHM

### Step 1: Create a New Spring Boot Project

Create a project using **Spring Initializr**.

### Step 2: Add Dependencies

Add the following dependencies:

* Spring Web
* Thymeleaf

### Step 3: Set Up Project Structure

* Create the main class and annotate it with `@SpringBootApplication`.
* Create a Controller class using `@Controller`.
* Add HTML templates under `src/main/resources/templates`.

### Step 4: Create a Controller

* Define a method to handle HTTP GET requests using `@GetMapping`.
* Return the view name (HTML page name) from the Controller.
* Pass data to the View using the `Model` object.

### Step 5: Create a Model

A separate POJO Model class is optional. For this application, the `Model` object provided by Spring MVC is used to pass data from the Controller to the View.

### Step 6: Create View Pages Using Thymeleaf

* Create an HTML file inside the `templates` folder.
* Use Thymeleaf syntax such as `${message}` to display dynamic content.

### Step 7: Run the Application

Run the Spring Boot application from the IDE or using the command line.

### Step 8: Access the Application

Open a web browser and navigate to:

```text
http://localhost:8080/
```

---

# PROGRAM

## Project Structure

```text
spring-mvc-demo/
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── example/
│       │           └── mvc/
│       │               ├── MvcApplication.java
│       │               └── HomeController.java
│       │
│       └── resources/
│           ├── templates/
│           │   └── index.html
│           └── application.properties
│
└── pom.xml
```

---

## pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         https://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.1.2</version>
        <relativePath/>
    </parent>

    <groupId>com.example</groupId>
    <artifactId>spring-mvc-demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <name>Spring MVC Demo</name>
    <description>Simple Spring Boot MVC Application</description>

    <properties>
        <java.version>17</java.version>
    </properties>

    <dependencies>

        <!-- Spring Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Thymeleaf for View Rendering -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>

    </dependencies>

</project>
```

---

## MvcApplication.java

**Main Class**

```java
package com.example.mvc;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MvcApplication {

    public static void main(String[] args) {
        SpringApplication.run(MvcApplication.class, args);
    }
}
```

---

## HomeController.java

**Controller**

```java
package com.example.mvc;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String homePage(Model model) {

        model.addAttribute(
            "message",
            "Welcome to Spring Boot MVC!"
        );

        return "index";
    }
}
```

The `return "index"` statement refers to:

```text
src/main/resources/templates/index.html
```

---

## index.html

**View – inside `src/main/resources/templates/`**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">

<head>
    <title>Spring MVC</title>
</head>

<body>

    <h1 th:text="${message}">
        Default Message
    </h1>

</body>

</html>
```

# OUTPUT

<img width="745" height="257" alt="image" src="https://github.com/user-attachments/assets/a4989238-ad0f-4a87-9ff6-7f28e2b3ad4c" />


# RESULT

Thus, the **Simple Spring Boot MVC Application** was successfully developed using **Spring Web, Controller, Model, and Thymeleaf View**, and the dynamic message was successfully displayed in the web browser.
