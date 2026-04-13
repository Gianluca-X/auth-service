🧠 Descripción

Auth Service es un microservicio de autenticación desarrollado con Spring Boot, diseñado para ser reutilizable en arquitecturas de microservicios.

Permite gestionar el ciclo completo de autenticación y seguridad de usuarios, incluyendo registro, login, verificación de email, manejo de tokens JWT y refresh tokens.

🚀 Características principales
🔐 Autenticación basada en JWT
♻️ Manejo de Refresh Tokens
📧 Verificación de email con SendGrid
🔄 Cambio de email y contraseña
🧠 Control de roles (USER / ADMIN)
🔔 Publicación de eventos con RabbitMQ
🛡️ Seguridad con Spring Security
🧪 Validación de credenciales y control de acceso

🏗️ Arquitectura

Este servicio forma parte de una arquitectura de microservicios y puede integrarse fácilmente con otros sistemas mediante:

Tokens JWT para autenticación
Eventos asincrónicos (RabbitMQ)
APIs REST

🛠️ Tecnologías utilizadas
☕ Java 21
🌱 Spring Boot
🔐 Spring Security
🪪 JWT (JSON Web Tokens)
🐘 PostgreSQL
🐇 RabbitMQ
📧 SendGrid
📦 Maven
📂 Estructura del proyecto

auth-service/
│
├── controller/
├── service/
├── repository/
├── entity/
├── security/
├── dto/
├── exceptions/
└── config/
🔌 Endpoints principales

🔑 Autenticación
POST /auth/register → Registro de usuario
POST /auth/login → Login y generación de JWT
POST /auth/refresh → Generación de nuevo access token

👤 Usuario
PATCH /auth/change-password → Cambiar contraseña
PATCH /auth/change-email → Cambiar email
PUT /auth/update → Actualizar usuario
DELETE /auth/delete/{id} → Eliminar usuario
📧 Verificación
GET /auth/verify?code=xxx → Verificar email
POST /auth/resend-verification → Reenviar código

🔐 Seguridad
Contraseñas encriptadas con BCrypt
Autenticación stateless con JWT
Filtro personalizado (JwtAuthFilter)
Control de acceso basado en roles

🔄 Flujo de autenticación
Usuario se registra
Recibe email de verificación
Verifica su cuenta
Realiza login
Recibe:
Access Token (JWT)
Refresh Token
Usa el token para acceder a endpoints protegidos

🔁 Refresh Token
Generación de tokens únicos
Expiración configurable
Rotación de tokens en cada refresh
Eliminación de tokens antiguos

📩 Eventos

Este servicio publica eventos mediante RabbitMQ, por ejemplo:

Cambio de email de usuario
Creación de usuario

Esto permite integración con otros microservicios (ej: user-service).

⚙️ Configuración
Variables de entorno necesarias
JWT_SECRET=your_secret_key
SENDGRID_API_KEY=your_sendgrid_key
SENDGRID_FROM=your_email
FRONTEND_URL=http://localhost:3000

▶️ Ejecución local
# Clonar repositorio
git clone https://github.com/Gianluca-X/auth-service.git

# Entrar al proyecto
cd auth-service

# Ejecutar
./mvnw spring-boot:run

🧪 Testing recomendado
Registro de usuario
Verificación de email
Login
Refresh token
Cambio de contraseña

🔗 Integración

Este microservicio está diseñado para ser utilizado por otros servicios como:

Digital Money Wallet App 💳
LexFlow ⚖️
E-commerce 🛒

💡 Autor

Desarrollado por Gianluca Fucci
Backend Developer | Java & Spring Boot

🚀 Estado del proyecto

🟢 Activo — listo para integración en arquitecturas reales
