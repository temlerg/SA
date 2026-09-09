SOAP (Simple Object Access Protocol) — это протокол обмена структурированными сообщениями в формате XML между клиентом и сервером. Это один из старейших стандартов интеграции, активно применяющийся в корпоративных системах, особенно в банковской, телеком- и страховой сферах.

---

## 📌 Общая характеристика SOAP

- Протокол передачи сообщений на основе [[XML]]
    
- Использует HTTP, SMTP, FTP в качестве транспортного уровня
    
- Чёткая структура и строгая типизация данных
    
- Поддерживает сложные сценарии безопасности и транзакций
    
- Основан на спецификации WSDL (Web Services Description Language)
    

---

## 📐 Устройство SOAP-сообщения

SOAP-сообщение состоит из 4 основных элементов:

```xml
<soap:Envelope>
  <soap:Header>
    <!-- Метаданные: авторизация, транзакции -->
  </soap:Header>
  <soap:Body>
    <!-- Основные данные запроса или ответа -->
  </soap:Body>
</soap:Envelope>
```

- `Envelope` — оболочка, обязательна
    
- `Header` — опциональный, содержит служебную информацию
    
- `Body` — обязательный, содержит полезную нагрузку (вызовы методов и ответы)
    

---

## ⚙️ WSDL (Web Services Description Language)

[[#Пример WSDL-документа|WSDL]] — это XML-документ, описывающий:

- Методы, доступные в веб-сервисе
    
- Форматы сообщений (запрос/ответ)
    
- Типы данных
    
- Протоколы и URL-адреса взаимодействия
    

Клиент может на основе WSDL:

- Сгенерировать код (прокси-клиент)
    
- Проверить правильность вызова
    

---

## 🔄 Пример SOAP-запроса и ответа

### Запрос:

```xml
POST /service HTTP/1.1
Content-Type: text/xml; charset=utf-8

<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <GetUser xmlns="http://example.com/users">
      <userId>123</userId>
    </GetUser>
  </soap:Body>
</soap:Envelope>
```

### Ответ:

```xml
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <GetUserResponse xmlns="http://example.com/users">
      <name>Ivan</name>
      <email>ivan@example.com</email>
    </GetUserResponse>
  </soap:Body>
</soap:Envelope>
```

---

## 🔐 Безопасность SOAP

SOAP поддерживает расширения безопасности (WS-Security):

- Подпись и шифрование сообщений (XML Signature, XML Encryption)
    
- Токены, логины, сертификаты
    
- Поддержка SAML
    

Безопасность внедряется на уровне `Header`, без зависимости от транспорта (в отличие от REST + HTTPS).

---

## 📚 Сравнение с REST

|Характеристика|SOAP|REST|
|---|---|---|
|Формат сообщений|XML|JSON (или XML)|
|Интерфейс|Описан в WSDL|URL + HTTP|
|Сложность|Высокая|Ниже|
|Безопасность|WS-Security|TLS + авторизация|
|Стандартизация|Очень высокая|Более свободная|
|Использование|Корпоративные системы, B2B|Веб-сервисы, микросервисы|

---

## ✅ Преимущества SOAP

- Чёткая структура, строгая спецификация
    
- Расширенные возможности безопасности
    
- Поддержка сложных операций и транзакций
    
- Подходит для формальных контрактов между организациями
    

---

## 🚫 Недостатки SOAP

- XML-переносимость хуже, чем у JSON
    
- Более громоздкий и сложный синтаксис
    
- Сложность настройки и сопровождения
    
- Менее гибкий в сравнение с REST
    

---

## 🛠 Инструменты

- **SoapUI** — тестирование SOAP-запросов
    
- **Postman** (ограниченная поддержка)
    
- **WSDL2Java, wsimport, dotnet svcutil** — генерация кода клиента
    
- **Apache CXF, JAX-WS, .NET WCF** — серверные библиотеки
    

---

###  Пример WSDL-документа

```xml
<definitions xmlns="http://schemas.xmlsoap.org/wsdl/" 
             xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" 
             xmlns:tns="http://example.com/users" 
             name="UserService" 
             targetNamespace="http://example.com/users">

  <types>
    <schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://example.com/users">
      <element name="GetUser">
        <complexType>
          <sequence>
            <element name="userId" type="xsd:int"/>
          </sequence>
        </complexType>
      </element>
      <element name="GetUserResponse">
        <complexType>
          <sequence>
            <element name="name" type="xsd:string"/>
            <element name="email" type="xsd:string"/>
          </sequence>
        </complexType>
      </element>
    </schema>
  </types>

  <message name="GetUserRequest">
    <part name="parameters" element="tns:GetUser"/>
  </message>
  <message name="GetUserResponse">
    <part name="parameters" element="tns:GetUserResponse"/>
  </message>

  <portType name="UserServicePortType">
    <operation name="GetUser">
      <input message="tns:GetUserRequest"/>
      <output message="tns:GetUserResponse"/>
    </operation>
  </portType>

  <binding name="UserServiceBinding" type="tns:UserServicePortType">
    <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
    <operation name="GetUser">
      <soap:operation soapAction="getUser"/>
      <input><soap:body use="literal"/></input>
      <output><soap:body use="literal"/></output>
    </operation>
  </binding>

  <service name="UserService">
    <port name="UserServicePort" binding="tns:UserServiceBinding">
      <soap:address location="http://example.com/users"/>
    </port>
  </service>
</definitions>
```

Этот WSDL определяет веб-сервис `UserService` с одной операцией `GetUser`. Он описывает сообщения, используемые типы данных, binding (связку) и конечную точку (endpoint).