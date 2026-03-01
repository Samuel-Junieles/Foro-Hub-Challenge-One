# Foro-Hub-Challenge-One

**ForoHub** es una API REST robusta que simula el ecosistema de un foro de discusión profesional. Este proyecto implementa una arquitectura **Stateless** con seguridad avanzada y una gestión de datos relacional optimizada, consolidando los pilares del desarrollo backend moderno.

---

## Arquitectura por Capas
El sistema está organizado para garantizar la escalabilidad y el desacoplamiento de responsabilidades:

1.  **Capa de API/Controller:** Maneja los endpoints REST, gestiona las peticiones HTTP y coordina las respuestas utilizando DTOs.
2.  **Capa de Seguridad (Spring Security + JWT):** Controla la autenticación y autorización mediante tokens firmados digitalmente, asegurando un entorno *Stateless*.
3.  **Capa de Servicio (Business Logic):** Ejecuta las reglas de negocio, como la validación de duplicados y la lógica de transición de estados (Tópico -> Solucionado).
4.  **Capa de Persistencia (Repository):** Utiliza Spring Data JPA para la comunicación con la base de datos, implementando consultas personalizadas y filtrado dinámico.
5.  **Capa de Modelo (Domain):** Entidades JPA que representan el núcleo del foro (Tópicos, Usuarios, Respuestas, Cursos).

---

## 🚀 Funcionalidades Principales

### 1. Seguridad y Autenticación Blindada
* **JWT (JSON Web Token):** Implementación de seguridad sin estado para proteger cada recurso de la API.
* **Control de Acceso:** Gestión de perfiles y permisos diferenciados entre autores y administradores.

### 2. Gestión Inteligente de Tópicos (CRUD)
* **Integridad de Datos:** Prevención automática de tópicos duplicados para evitar spam.
* **Mapeo Relacional:** Trazabilidad total vinculando cada tópico a un autor, curso y categoría específica.

### 3. Lógica de Solución y Estados
* **Transición Atómica:** Al marcar una respuesta como solución, el sistema actualiza automáticamente el estado del tópico padre a `SOLUCIONADO`, cerrando el ciclo de vida de la consulta.

### 4. Borrado Lógico (Soft Delete)
* **Preservación de Información:** Los registros no se eliminan físicamente. Se utiliza un flag de `activo = false` para mantener la integridad estadística y el historial de la base de conocimientos.

### 5. Filtrado Dinámico y Búsqueda
* Consultas optimizadas en JPA para segmentar información por **Nombre del Curso** y **Año de Creación**.

---

## 🛠️ Stack Tecnológico

* **Java 17+**
* **Spring Boot 3**
* **Spring Security & JWT**
* **Spring Data JPA**
* **Flyway:** Migraciones de base de datos.
* **MySQL / PostgreSQL:** Gestión de datos relacional.
* **Maven:** Gestión de dependencias.

---

## 📖 Configuración Rápida
1. Configura tus variables de entorno para la base de datos y el `secret` del JWT en `application.properties`.
2. Ejecuta las migraciones de Flyway para preparar el esquema de tablas.
3. Utiliza herramientas como **Insomnia** o **Postman** para interactuar con los endpoints protegidos.

---
Desarrollado como parte del Challenge de **Oracle Next Education** y **Alura Latam**.
