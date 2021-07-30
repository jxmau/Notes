# Thymeleaf's HTML5 Doctype 

```html

<html  xmlns:th="http://www.thymeleaf.org" lang="en">
<head>
    <meta charset="UTF-8">
    <title> </title>
</head>
<body>
    <header>

    </header>

    <main>

    </main>

    <footer>

    </footer>

</body>
</html>

```


# Spring Security and Thymeleaf

```html

 <!-- Show only if the user is authenticated  -->
 <div sec:authorize="isAuthenticated()" > </div>

 <!-- Show only if the user is not authenticated  -->
<div sec:authorize="isAnonymous()"> </div>

```

# Show a dynamic number of object

```html

<!-- Will iterate through a list of article object -->
<div th:each="article = ${articles}">
    <div classe="title" th:text="${article.getTitle}"> This title will be overwrited by thymeleaf </div>
    <div classe="image-container">  
        <!-- By default, you'll need the relative path from the static directory in the resources folder.
        If you're using Spring Security you'll need to whitelist the directory in the Confid Class. -->
        <img th:src="${article.getImageSource}" alt="${article.getTitle}"> 
    </div>
    <p th:text="${article.getDescription}"> This description will be overwrited by thymeleaf </p>
    <a th:href="'/article/' + article.getId"> See the article </a> 
</div>

```

# Form

```html
    <!--  When using a POST request with thymeleaf, you might get an error when using a plain action. -->
    <form th:action="@{/regsiter}" method="POST">

    </form>
```

# Statements

```html

<!-- If Statement -->
<div th:if="{article.getLanguage} == 'fr'" > French </div>

```
