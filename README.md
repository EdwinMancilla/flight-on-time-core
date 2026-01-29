# ✈️ Flight On Time Core

> 🏆 **Proyecto desarrollado durante el Hackathon ONE - Alura Latam & No Country (Enero 2025)**

[![Java](https://img.shields.io/badge/Java-17-orange)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green)](https://spring.io/projects/spring-boot)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue)](https://www.postgresql.org/)

API REST para la predicción de puntualidad de vuelos utilizando modelos de Machine Learning (ONNX). Este microservicio es el núcleo de inferencia que procesa datos de vuelos y determina la probabilidad de retraso en tiempo real.

---

## 📋 Descripción

**Flight On Time Core** es una aplicación desarrollada en Java con Spring Boot que expone endpoints para consumir un modelo de inteligencia artificial pre-entrenado. Su función principal es recibir los detalles de un vuelo (aerolínea, origen, destino, fecha, etc.), transformarlos en vectores numéricos y ejecutar una inferencia utilizando **ONNX Runtime**.

---

## 🚀 Mi Contribución al Proyecto

Como **Backend Developer** en este proyecto, mis responsabilidades incluyeron:

- ✅ **Desarrollo de API REST** con Spring Boot para exponer endpoints de predicción
- ✅ **Integración de modelo de IA** utilizando ONNX Runtime para inferencia en tiempo real
- ✅ **Transformación de datos** de vuelos (aerolínea, origen, destino, fecha) en vectores numéricos
- ✅ **Implementación de persistencia** con Spring Data JPA y PostgreSQL
- ✅ **Aplicación de principios SOLID** y patrones de diseño para código mantenible y escalable
- ✅ **Configuración de seguridad** utilizando variables de entorno para credenciales

---

## 💻 Tecnologías Utilizadas

### Backend
- **Java 17**: Lenguaje principal del proyecto
- **Spring Boot 3.x**: Framework para la creación de la API REST
- **Spring Data JPA**: Abstracción de persistencia
- **Hibernate**: ORM para mapeo objeto-relacional

### Inteligencia Artificial
- **Microsoft ONNX Runtime**: Motor de alto rendimiento para ejecutar el modelo de ML

### Base de Datos
- **PostgreSQL**: Base de datos relacional
- **Flyway**: Control de versiones de base de datos

### Herramientas
- **Maven**: Gestión de dependencias y construcción
- **Lombok**: Reducción de código repetitivo

---

## 🛠️ Instalación y Configuración

### Prerrequisitos

- JDK 17 instalado
- Maven instalado
- PostgreSQL instalado y corriendo

### Variables de Entorno

Configura las siguientes variables de entorno antes de ejecutar la aplicación:

```bash
export DB_HOST=localhost
export DB_PORT=5432
export DB_NAME=flight_on_time
export DB_USER=postgres
export DB_PASSWORD=tu_password
```

O crea un archivo `.env` en la raíz del proyecto (no incluido en el repositorio por seguridad):

```env
DB_HOST=localhost
DB_PORT=5432
DB_NAME=flight_on_time
DB_USER=postgres
DB_PASSWORD=tu_password
```

### Construcción

Para compilar el proyecto y descargar las dependencias:

```bash
./mvnw clean install
```

### Ejecución

Inicia la aplicación con:

```bash
./mvnw spring-boot:run
```

La aplicación se iniciará en el puerto `8081`.

---

## 🔌 API Endpoints

### Predecir Puntualidad de Vuelo

Envía los datos de un vuelo para obtener una predicción.

**Endpoint:** `POST /internal/predict`

**Content-Type:** `application/json`

#### Request Body

```json
{
    "aerolinea": "AA",
    "origen": "JFK",
    "destino": "LAX",
    "fecha_partida": "2026-11-10T14:30:00",
    "distancia_km": 1200.5
}
```

#### Response (200 OK)

```json
{
    "prevision": "Puntual ✅",
    "probabilidad": 0.24
}
```

---

## 📂 Estructura del Proyecto

```
src/main/java/com/flightontime/core
├── CoreApplication.java          # Clase principal de arranque
├── controller/                   # Controladores REST
│   └── FlightController.java
├── service/                      # Lógica de negocio
│   ├── FlightPredictionServiceImpl.java
│   └── FeatureEngineeringService.java
├── model/                        # Clases de dominio
│   └── Flight.java
└── dto/                          # Data Transfer Objects
    ├── FlightRequestDTO.java
    └── PredictionResponseDTO.java
```

---

## 🧠 Lógica de Predicción

El proceso de inferencia sigue estos pasos:

1. **Recepción**: El `FlightController` recibe el JSON y lo valida
2. **Transformación**: `FeatureEngineeringService` convierte las variables en un vector `float[]`
3. **Inferencia**: `FlightPredictionServiceImpl` utiliza ONNX Runtime para procesar el vector
4. **Interpretación**: Se analiza la probabilidad; si es > 0.5, se clasifica como retraso

---

## 👥 Equipo de Desarrollo

Este proyecto fue desarrollado colaborativamente durante el Hackathon ONE:

- **Luisa Valencia** - Líder del proyecto
- **Edwin Mancilla** - Backend Developer (Java/Spring Boot)
- **Marco Hernández** - Colaborador
- **Eliana Méndez** - Colaboradora
- Y más colaboradores

---

## 🔗 Repositorio Original

Este es un fork del proyecto original desarrollado durante el hackathon:
- **Repositorio original**: [luvalenciaq/flight-on-time-core](https://github.com/luvalenciaq/flight-on-time-core)

---

## 📫 Contacto

**Edwin Javier Mancilla Rios**
- 📧 Email: edwinmancilla1017@gmail.com
- 💼 LinkedIn: [linkedin.com/in/edwin-mancilla-rios-79b051346](https://www.linkedin.com/in/edwin-mancilla-rios-79b051346/)
- 🐙 GitHub: [github.com/EdwinMancilla](https://github.com/EdwinMancilla)

---

## 📄 Licencia

Este proyecto fue desarrollado con fines educativos durante el Hackathon ONE de Alura Latam & No Country.
