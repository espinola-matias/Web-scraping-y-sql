# 📚 Books Scraping & SQL + API

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat&logo=python)
![SQLite](https://img.shields.io/badge/Database-SQLite3-green?style=flat&logo=sqlite)
![ETL](https://img.shields.io/badge/Process-ETL-orange)

Este proyecto es una implementación completa de un proceso **ETL (Extract, Transform, Load)**. Extrae información de libros desde una web de prueba, enriquece los datos consultando una API externa, limpia la información y la almacena en una base de datos **SQLite** completamente normalizada.

## 🚀 Características Principales

* **Web Scraping Avanzado:** Utiliza `BeautifulSoup` y `Requests` para iterar sobre 50 páginas de [Books to Scrape](https://books.toscrape.com/).
* **Enriquecimiento de Datos:** Dado que la web original no provee el nombre del autor, el script consulta dinámicamente la **API de Google Books** para obtener esta información.
* **Base de Datos Relacional (3NF):** Diseño de base de datos normalizado para evitar redundancia.
    * Separación de `Autores` y `Categorías`.
    * Implementación de relación **Muchos a Muchos (N:N)** entre Libros y Autores.
* **Consultas SQL Complejas:** El proyecto incluye scripts de análisis de datos utilizando `JOINs`, `GROUP BY` y `HAVING`.

## 🛠️ Tecnologías Utilizadas

* **Python 3.x**
* **SQLite3** (Base de datos)
* **BeautifulSoup4** (Parsing HTML)
* **Requests** (Peticiones HTTP)
* **Google Books API**

## 🗂️ Modelo de Base de Datos

```text
├── bd_evaluacion.db       # Base de datos SQLite generada
├── webscraping.ipynb      # Notebook con la lógica de extracción y carga
├── requirements.txt       # Lista de dependencias del proyecto
└── README.md              # Documentación