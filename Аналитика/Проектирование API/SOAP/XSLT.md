# 🌐 Что такое XSLT простыми словами

**XSLT (Extensible Stylesheet Language Transformations)** — язык преобразования XML-документов в другие форматы (XML, HTML, текст и т.д.). Представьте, что у вас есть сырой XML с данными, а XSLT — это инструкция, как из этого «сырая» создать красивую веб-страницу или подготовить отчёт.

---

## 🔍 Зачем нужен XSLT

- **Отделение логики от данных**: данные хранятся в XML, а представление (HTML, текст, другой XML) описывается в XSLT.
    
- **Повторное использование**: одна и та же трансформация применяется к разным XML-файлам с одинаковой структурой.
    
- **Гибкая генерация**: можно формировать различные выходные форматы без изменения исходного XML.
    

---

## 🛠️ Как устроен файл XSLT

1. Файл имеет расширение **.xsl** или **.xslt** и начинается с:
    
    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <xsl:stylesheet version="1.0"
        xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
      <!-- шаблоны здесь -->
    </xsl:stylesheet>
    ```
    
2. **Шаблоны** (`<xsl:template>`) описывают, какие узлы XML обрабатывать.
    
3. **XPath** используется для навигации по XML и выборки нужных узлов.
    
4. **Инструкции** `<xsl:value-of>`, `<xsl:for-each>`, `<xsl:if>` и другие позволяют формировать выходной документ.
    

---

## ✏️ Простой пример XSLT

У нас есть XML со списком книг:

```
<!-- books.xml -->
<books>
  <book>
    <title>Мастер и Маргарита</title>
    <author>Булгаков</author>
  </book>
  <book>
    <title>Преступление и наказание</title>
    <author>Достоевский</author>
  </book>
</books>
```

Трансформация в HTML-список:

```
<!-- books.xsl -->
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="/books">
    <html><body>
      <h2>Список книг</h2>
      <ul>
        <xsl:for-each select="book">
          <li>
            <xsl:value-of select="title"/> — <xsl:value-of select="author"/>
          </li>
        </xsl:for-each>
      </ul>
    </body></html>
  </xsl:template>
</xsl:stylesheet>
```

Результат (в браузере):

```
<html><body>
  <h2>Список книг</h2>
  <ul>
    <li>Мастер и Маргарита — Булгаков</li>
    <li>Преступление и наказание — Достоевский</li>
  </ul>
</body></html>
```

---

## ✅ Как запустить XSLT-трансформацию

1. **Браузер**: открыть HTML-файл, подключив в нём XSL:
    
    ```
    <?xml-stylesheet type="text/xsl" href="books.xsl"?>
    <books>…</books>
    ```
    
2. **Командная строка**:
    
    - **xsltproc** (Linux): `xsltproc books.xsl books.xml > books.html`
        
3. **В коде**:
    
    - **Java**: `TransformerFactory.newInstance()` и `transform()`.
        
    - **Python**: библиотека **lxml** — `etree.XSLT`.
        

---

## 🚀 Где применяется XSLT

- **Веб-приложения**: динамическая генерация страниц из XML.
    
- **Отчёты и документация**: экспорт XML в PDF через XSL-FO.
    
- **Интеграция систем**: преобразование сообщений между сервисами.
    

---

# ✍️ Итог

**XSLT — это инструмент преобразования данных из XML**. С его помощью вы легко превратите XML в HTML, текст или другой XML без изменения исходного файла. Начните с простых шаблонов и изучите XPath — и вы быстро освоите мощь XSLT!