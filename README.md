# Ventas_Tech_DB

Base de datos relacional para el proyecto de certificación **Data Analyst**, correspondiente al módulo de Ingeniería de Datos.

## Objetivo del proyecto

Construir el back-end de datos de **TechStore**, una cadena de tiendas de tecnología, que servirá como fuente para el Dashboard de Inteligencia de Negocios del proyecto final. El script `ventas_tech_db.sql` crea un esquema normalizado (3FN) y lo carga con datos iniciales de ventas, productos, categorías y clientes.

Este esquema es la base sobre la que, en módulos posteriores, se construirán:
- Conexión y transformación de datos en **Power BI** (Módulo 6).
- Modelo analítico y medidas **DAX** (Módulo 8).

## Motor de base de datos

**SQL Server**

## Modelo de datos

```
categorias (1) ──── (N) productos (1) ──── (N) ventas (N) ──── (1) clientes
```

| Tabla | Descripción |
|---|---|
| `categorias` | Dimensión con las categorías de productos |
| `clientes` | Dimensión con los datos de los clientes |
| `productos` | Dimensión con los productos, referenciando su categoría |
| `ventas` | Tabla de hechos, referencia a clientes y productos |

## Contenido del script (`ventas_tech_db.sql`)

1. **DROP TABLES**: elimina las tablas en orden inverso de dependencias, para permitir una ejecución repetible.
2. **CREATE TABLES**: define las 4 tablas con sus tipos de datos, `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL` y `UNIQUE` según corresponde.
3. **INSERT DATA**: carga inicial con 4 categorías, 5 clientes, 6 productos y 10 ventas.
4. **Validación**: consultas `SELECT` finales para confirmar que las 4 tablas se cargaron correctamente.

## Cómo ejecutarlo

1. Abrí el archivo `ventas_tech_db.sql` en SQL Server Management Studio (SSMS) o Azure Data Studio.
2. Ejecutá el script completo (`CREATE DATABASE` incluido).
3. Corré las consultas de validación al final para confirmar que las tablas tienen datos.

## Próximos pasos

- Conectar esta base de datos a Power BI.
- Explorar el uso de **schemas** de SQL Server (por ejemplo, separar objetos en `dbo`, `ventas`, `catalogo`) para organizar mejor los objetos a medida que el proyecto crezca.
