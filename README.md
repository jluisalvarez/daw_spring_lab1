# Intro Spring Framework

## Requisitos

- Java 21
- IDE: Visual Code

## Crea un proyecto desde Spring Boot Initializr

http://start.spring.io/

Completa el asistente, seleccionando:

- Gestor Proyecto: Maven
- Lenguaje: Java
- Versión de Spring Boot: 3.2.0
- Project Metadata
    - Group: daw.example.helloworld
    - Artifact: helloworld
    - Name: helloworld
    - Description: HelloWorld project for Spring Boot
    - Package name: daw.example.helloworld
    - Packaging: Jar
    - Java: 21
- Dependencias
    - Spring Boot DevTools
    - Spring Web
    - Thymeleaf

Genera el contenido, descárgalo y descomprime. Utiliza el IDE para abrir el proyecto.

## Analiza la estructura y el contenido generado

- src: código fuente
    - main: código de la aplicación
        - java\daw\example\helloworld
            - HelloworldApplication.java: Clase principal de la aplicación
        - resources: Recursos
            - static: ficheros estáticos (html, css, js, etc)
            - templates: vistas
        - application.properties: fichero de configración
    - test: código para test
- pom.xml: fichero para gestión del proyecto y dependencias

## Crea un controlador

Crea una carpeta controlles en src/main/java/daw/example/helloworld y crea un fichero AppController.java dentro con el siguiente código:

```java
package daw.example.helloworld.controllers;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class AppController {

    @GetMapping("/hola")
    public String hola(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
		model.addAttribute("name", name);
		return "hola";
	}
    
}
```

## Crea una vista

En la carpeta src/main/resources/template crea el fichero hola.html con el siguiente contenido:

```html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head> 
    <title>Getting Started: Serving Web Content</title> 
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
    <p>Hello <span th:text="${name}">NOMBRE</span>!</p>
</body>
</html>
```

## Compila el proyecto

```
mvnw clean package
```

## Ejecuta el proyecto

```
mvnw spring-boot:run
```

## Comprueba el funcionamiento

```
http://localhost:8080/hola
```

```
http://localhost:8080/hola?name=Pepe
```

## Fichero de configuración: application.properties

Cambiar el puerto: server.port=80

```
http://localhost/hola?name=Pepe
```