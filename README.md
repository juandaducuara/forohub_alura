Foro Hub
¡Hola! Bienvenidos y bienvenidas a un nuevo desafío. En esta oportunidad, vamos a poner en práctica los conocimientos adquiridos en Java y Spring Boot. ¿Cuál es la propuesta que les traigo en esta oportunidad? Vamos a realizar nuestra propia API REST con la temática de un foro. ¿Qué les parece, entonces, construir su propio foro? Un lugar donde las personas puedan crear sus tópicos con sus dudas o con sugerencias que otras personas puedan también responder e interactuar allí dentro de una comunidad. Suena genial, ¿verdad? ¿Qué les parece si vemos entonces lo que traigo para ustedes y la propuesta para nuestro desafío?

Índice
Introducción
Requisitos
Instalación
Uso
Endpoints
Autenticación
Contribuciones
Licencia
Introducción
En este proyecto, vamos a desarrollar una API REST para un foro utilizando Java y Spring Boot. La API permitirá a los usuarios crear, listar, actualizar y eliminar tópicos. Además, implementaremos una capa de seguridad utilizando JSON Web Tokens (JWT) para asegurar que solo los usuarios autenticados puedan interactuar con los tópicos.

Requisitos
Java 11 o superior
Spring Boot 3
MySQL
Insomnia (para pruebas)
Instalación
Clona este repositorio:

sh
Copiar código
git clone https://github.com/tuusuario/foro-hub.git
Navega al directorio del proyecto:

sh
Copiar código
cd foro-hub
Configura la base de datos en el archivo application.properties:

properties
Copiar código
spring.datasource.url=jdbc:mysql://localhost:3306/foro_hub
spring.datasource.username=tu_usuario
spring.datasource.password=tu_contraseña
spring.jpa.hibernate.ddl-auto=update
Construye y ejecuta el proyecto:

sh
Copiar código
./mvnw spring-boot:run
Uso
Para probar la API, utilizaremos Insomnia. A continuación, se detallan los pasos para realizar diferentes acciones a través de la API.

Listar Tópicos
Realiza una petición GET a:

bash
Copiar código
GET http://localhost:8080/topicos
Crear un Tópico
Realiza una petición POST a:

bash
Copiar código
POST http://localhost:8080/topicos
con el siguiente cuerpo:

json
Copiar código
{
  "usuarioId": 1,
  "mensaje": "Este es un nuevo tópico",
  "curso": "Java",
  "titulo": "Dudas sobre Spring Boot"
}
Actualizar un Tópico
Realiza una petición PUT a:

bash
Copiar código
PUT http://localhost:8080/topicos/{id}
con el siguiente cuerpo:

json
Copiar código
{
  "mensaje": "Este es un tópico actualizado",
  "curso": "Spring",
  "titulo": "Dudas resueltas sobre Spring Boot"
}
Eliminar un Tópico
Realiza una petición DELETE a:

bash
Copiar código
DELETE http://localhost:8080/topicos/{id}
Endpoints
GET /topicos: Listar todos los tópicos
POST /topicos: Crear un nuevo tópico
PUT /topicos/{id}: Actualizar un tópico existente
DELETE /topicos/{id}: Eliminar un tópico
Autenticación
Para crear, actualizar o eliminar tópicos, es necesario autenticarse. Utilizaremos JWT para manejar la autenticación.

Obtener Token
Realiza una petición POST a:

bash
Copiar código
POST http://localhost:8080/auth
con el siguiente cuerpo:

json
Copiar código
{
  "email": "usuario@example.com",
  "password": "tu_contraseña"
}
Esto devolverá un token que debe ser utilizado en las peticiones subsecuentes.

Usar Token
Incluye el token en el encabezado de tus peticiones:

makefile
Copiar código
Authorization: Bearer tu_token
