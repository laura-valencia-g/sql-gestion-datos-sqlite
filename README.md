# Gestión y Consultas de Bases de Datos con SQL (SQLite)

Diseño, carga y consulta de una base de datos relacional para una plataforma de streaming musical, usando SQL sobre SQLite desde Python.

*Trabajo académico — Universidad EAFIT, 2024 (Curso: Integración de Datos y Prospectiva).*

## Contexto

A partir de un dataset de una plataforma de streaming musical (artistas, álbumes, canciones, usuarios, reproducciones, listas de reproducción, calificaciones), se diseñó y consultó una base de datos relacional completa en SQLite, evolucionando el modelo de datos en dos versiones (V2 y V3) a medida que se agregaban nuevas tablas y reglas de negocio.

## Estructura de la base de datos (V3)

9 tablas relacionadas: `Artistas`, `Álbumes`, `Canciones`, `Géneros`, `Usuarios`, `Calificaciones`, `Reproducciones`, `ListasReproducción`, `CancionesLista`.

## Consultas y operaciones desarrolladas

- **Carga de datos**: creación de la base de datos y carga de tablas desde Excel (`to_sql`) y desde un script `.sql` externo (`executescript`).
- **Consultas de selección con alias y ordenamiento**: por ejemplo, listar álbumes con título, fecha de lanzamiento y sello discográfico, ordenados alfabéticamente.
- **Funciones agregadas**: conteo de canciones por género (`COUNT`), suma de duración total de un álbum convirtiendo el formato de tiempo a segundos (`SUM` sobre subcadenas de texto).
- **Manipulación de fechas**: conversión de formato de fecha (`día/mes/año` → `año-mes-día`) usando funciones de cadena (`substr`), y cálculo de edad actual y edad de registro de cada usuario con `strftime`.
- **Actualización de datos**: uso de `UPDATE` para corregir formatos de fecha directamente en la base de datos.
- **Metadatos del esquema**: consulta de la estructura de tablas con `PRAGMA table_info` y listado de todas las tablas de la base con `sqlite_master`.
- **Visualización**: distribución de álbumes por sello discográfico mediante un gráfico de barras.

## Ejemplo de hallazgo

El cálculo de edad de usuarios al momento de registrarse en la plataforma mostró un rango amplio (desde usuarios de 19 años hasta uno de 101 años en el registro histórico de prueba), evidenciando cómo una sola consulta con funciones de fecha puede generar un indicador demográfico útil sin necesidad de procesar los datos fuera de la base de datos.

## Stack técnico

`SQL` (SQLite) · `Python` (librería `sqlite3`) · `Pandas` (carga y exploración de datos) · `Matplotlib`

## Acceso al notebook

Notebook original: [Gestión y manipulación de datos con SQLite](https://colab.research.google.com/drive/1Fi9FFKceiGyc_stvk3rXQmAtesgSeS57)

## Habilidades aplicadas

SQL (SELECT, WHERE, ORDER BY, UPDATE, funciones agregadas, funciones de fecha) · Diseño de bases de datos relacionales · Integración de Python con bases de datos SQL · Consulta de metadatos de esquema

