# Data-Cleaning-SQL-Project
En este proyecto, transformé datos crudos de despidos mundiales (World Layoffs) en un dataset limpio y listo para el análisis. El objetivo fue aumentar la calidad de los datos para asegurar insights precisos, manejando valores nulos, duplicados y estandarización de formatos.

Herramientas Utilizadas:

*MySQL Workbench

*SQL Avanzado: Window Functions, CTEs, Self-Joins, Type Casting.

Pasos de Limpieza Realizados
1. Eliminación de Duplicados

*Se identificaron registros duplicados basándose en todas las columnas clave (company, location, industry, date, etc.).

*Técnica: Uso de ROW_NUMBER() y PARTITION BY para identificar duplicados exactos y eliminarlos mediante una tabla de staging intermedia.

2. Estandarización de Datos

*Corrección de Strings: Se eliminaron espacios en blanco (TRIM) y se corrigieron errores tipográficos (ej: convertir "Crypto Currency" y "CryptoCurrency" a un estándar "Crypto").

*Limpieza de Países: Se corrigieron entradas como "United States." (con punto final) para unificarlas.

*Formato de Fechas: Conversión de la columna date de formato texto (str) a objeto de fecha (DATE) para permitir análisis de series temporales.

3. Manejo de Valores Nulos y en Blanco
   
*Lógica de Población de Datos: Se utilizó un Self-Join para rellenar datos faltantes en la columna Industry. Si una empresa (ej: Airbnb) tenía un registro con la industria correcta y otro nulo, se pobló automáticamente el nulo basándose en el registro existente.

*Eliminación de Datos Irrelevantes: Se eliminaron filas donde tanto total_laid_off como percentage_laid_off eran nulos, ya que no aportaban valor analítico.
