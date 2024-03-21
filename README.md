# Spring Boot Refresh Token with JWT example

Build JWT Refresh Token in the Java Spring Boot Application. You can know how to expire the JWT, then renew the Access Token with Refresh Token.

The instruction can be found at:
[Spring Boot Refresh Token with JWT example](https://bezkoder.com/spring-boot-refresh-token-jwt/)

## User Registration, User Login and Authorization process.
The diagram shows flow of how we implement User Registration, User Login and Authorization process.

![spring-boot-spring-security-jwt-authentication-flow](spring-boot-spring-security-jwt-authentication-flow.png)

And this is for Refresh Token:

![spring-boot-refresh-token-jwt-example-flow](spring-boot-refresh-token-jwt-example-flow.png)

## Spring Boot Server Architecture with Spring Security
You can have an overview of our Spring Boot Server with the diagram below:

![spring-boot-jwt-authentication-spring-security-architecture](spring-boot-jwt-authentication-spring-security-architecture.png)

## Configure Spring Datasource, JPA, App properties
Open `src/main/resources/application.properties`

```properties
spring.datasource.url= jdbc:mysql://localhost:3306/testdb?useSSL=false
spring.datasource.username= root
spring.datasource.password= 123456

spring.jpa.properties.hibernate.dialect= org.hibernate.dialect.MySQL5InnoDBDialect
spring.jpa.hibernate.ddl-auto= update

# App Properties
bezkoder.app.jwtSecret= bezKoderSecretKey
bezkoder.app.jwtExpirationMs= 3600000
bezkoder.app.jwtRefreshExpirationMs= 86400000
```

## Run Spring Boot application
```
mvn spring-boot:run
```

## Run following SQL insert statements
```
INSERT INTO roles(name) VALUES('ROLE_USER');
INSERT INTO roles(name) VALUES('ROLE_MODERATOR');
INSERT INTO roles(name) VALUES('ROLE_ADMIN');
```


POST API : http://localhost:9090/api/auth/signup

{
    "username": "test1",
    "email": "springsecurity@gmail.com",
    "password": "123456",
    "role": ["user","mod"]
}

GET API http://localhost:9090/api/auth/signin

{
    "username": "test1",
    "password": "123456"
}

Related Posts:
> [Spring Boot JWT Refresh Token using HttpOnly Cookies](https://www.bezkoder.com/spring-security-refresh-token/)

> [Spring Boot, Spring Security, MySQL: JWT Authentication & Authorization example](https://bezkoder.com/spring-boot-jwt-authentication/)

> [For PostgreSQL](https://bezkoder.com/spring-boot-security-postgresql-jwt-authentication/)

> [For MongoDB](https://bezkoder.com/spring-boot-jwt-auth-mongodb/)

## More Practice:
> [Spring Boot File upload example with Multipart File](https://bezkoder.com/spring-boot-file-upload/)
