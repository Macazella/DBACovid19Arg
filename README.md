# DBACovid19Arg
Este repositorio contiene el modelo de base de datos para el seguimiento del COVID-19 en Argentina. El modelo ha sido creado y gestionado utilizando JupyterLab a través de Anaconda y llevado a pgAdmin de PostgreSQL. A continuación, se presenta una descripción detallada del proyecto y sus componentes.

## Descripción del Proyecto

El objetivo de este proyecto es consolidar y analizar datos relacionados con la pandemia de COVID-19 en Argentina. Las principales áreas de enfoque incluyen:

- *Casos Ambulatorios*: Datos de casos que no requirieron hospitalización.
- *Casos Internados y Fallecidos*: Información sobre casos severos que resultaron en hospitalización o fallecimiento.
- *Total de Casos Confirmados*: Contabilización de todos los casos confirmados de COVID-19.

Aquí estoy gestionando un repositorio donde se indica el paso a paso sobre cómo descargar las bases de datos públicas del Ministerio de salud sobre el estado, registro y avance de casos durante el período 2020-2022 del SarsCov2 en la República Argentina.
Luego se indica cómo procesar las planillas csv en Python utilizando JupyterLab, importando NunPy y pandas para el análisis de la calidad de los datos, estadística, limpieza, unificación y modelado de las tablas a fin de luego poder ingresarlas en PostgreSQL.

Una vez realizados estos pasos, se importan en .zip los csv ya listos para incorporar a las tablas creadas en pgAdmin de PostgreSQL. Se brindan las sentencias necesarias para la creacion de usuario en Postgre, base de datos, DER, relaciones y constraints que luego de importar cada csv correspondinte a su tabla se insertarán para luego poder realizar análisis de los datos en esta gran base de datos.

Luego se utilizará Tableau para brindar en un dashbord la correspondiente visualización del análisis correspondiente a las siguientes preguntas que formarán parte de la hipótesis:

Analisis potencial de casos:
+Distribución covid por provincia
+Diferencia entre ciudades y pueblos: cantidad y fecha de registros
+Provincias con mayor cantidad de casos registrados
+Diferencias entre cantidad de casos ambulatorios e internados
+Mayor pico de casos en total (fecha)
+Provincias con menor cantidad de registros: hay bias por falta de recopilación de datos?



1) Modelo de Base de Datos

El modelo de base de datos incluye las siguientes tablas principales:


 - Casos_Ambulatorio

Esta tabla almacena datos sobre los casos ambulatorios:

- *ID*: Identificador único del caso.
- *Fecha_Diagnostico*: Fecha del diagnóstico.
- *Edad*: Edad del paciente.
- *Sexo*: Sexo del paciente.
- *Ubicación*: Ubicación del caso.
- *Estado*: Estado actual del caso (recuperado, activo).

 - Casos_Internados_y_Fallecidos

Esta tabla incluye información sobre los casos más severos:

- *ID*: Identificador único del caso.
- *Fecha_Ingreso*: Fecha de ingreso al hospital.
- *Fecha_Fallecimiento*: Fecha de fallecimiento (si aplica).
- *Edad*: Edad del paciente.
- *Sexo*: Sexo del paciente.
- *Ubicación*: Ubicación del caso.
- *Estado*: Estado actual del caso (internado, fallecido).

 - Total_Casos_confirmados

Esta tabla registra el total de casos confirmados:

- *ID*: Identificador único del registro.
- *Fecha_Reporte*: Fecha del reporte de casos.
- *Total_Casos*: Número total de casos confirmados hasta esa fecha.
- *Ubicación*: Ubicación de los casos reportados.

## Herramientas Utilizadas

- *Anaconda*: Para la creación y gestión del modelo de base de datos.
- *PostgreSQL*: Para la consulta y manipulación de datos.
- *pgAdmin.PL/SQL*: Para procedimientos almacenados y funciones.

## Cómo Empezar

1. Clonar el Repositorio:
    sh
    git clone https://github.com/Macazella/DBACovid19Arg.git
    
2. Leer 1.GUIA ANACONDA-JUPYTERLAB-PYTHON3
3. Realizar los pasos en los siguientes archivos (en orden):
   - 2. Paso a paso para carga, limpieza, modelado y guardado de Ambulatorios
   - 3. Paso a paso para carga, limpieza, modelado y guardado de Internados y fallecidos
   - 4. Paso a paso para cargar, limpiar, modelar y guardar CasosCovid19
   - 5. Descarga de archivos csv limpios

4. *Configurar la Base de Datos* PostgreSQL/pgAdmin4:
   - 0. Instalación de PostgreSQL y pgAdmin 4
     1. Tablas y relaciones
     2. SQL pgAdmin scripts para importar csv
     3. Devolver las relaciones y restricciones de las tablas
   
  
3. Procedimientos Almacenados y Triggers (IN PROGRESS)
Crea un archivo procedures_and_triggers.sql en el directorio scripts.

sql
-- procedures_and_triggers.sql

DELIMITER //

CREATE PROCEDURE obtener_prestamos_por_usuario (IN user_id INT)
BEGIN
    SELECT l.titulo, p.fecha_prestamo, p.fecha_devolucion
    FROM prestamos p
    JOIN libros l ON p.libro_id = l.id
    WHERE p.usuario_id = user_id;
END //

DELIMITER ;

CREATE TRIGGER actualizar_fecha_devolucion
AFTER UPDATE ON prestamos
FOR EACH ROW
BEGIN
    IF NEW.fecha_devolucion IS NOT NULL THEN
        INSERT INTO historial_prestamos (prestamo_id, fecha_devolucion)
        VALUES (NEW.id, NEW.fecha_devolucion);
    END IF;
END;

5. Consultas Complejas y Optimización
Agrega un archivo complex_queries.sql en el directorio scripts.

sql
-- complex_queries.sql

-- Consulta para encontrar los libros más prestados
SELECT l.titulo, COUNT(p.id) AS numero_prestamos
FROM prestamos p
JOIN libros l ON p.libro_id = l.id
GROUP BY l.titulo
ORDER BY numero_prestamos DESC
LIMIT 10;

-- Índice para optimizar las consultas de préstamos por usuario
CREATE INDEX idx_usuario_id ON prestamos(usuario_id);

4.  Respaldo y Restauración
Documenta cómo realizar un respaldo y restauración de la base de datos en el README.md.

markdown
## Respaldo y Restauración

### Respaldo
Para hacer un respaldo de la base de datos, usa el siguiente comando:

bash
mysqldump -u [usuario] -p[contraseña] nombre_base_de_datos > respaldo.sql


### Restauración
Para restaurar la base de datos desde un archivo de respaldo:

bash
mysql -u [usuario] -p[contraseña] nombre_base_de_datos < respaldo.sql
```
```

## Links de descargas de las bases de datos utilizadas:
- http://datos.salud.gob.ar/dataset?q=covid&sort=metadata_modified+desc (principal)
- DATABASES:
http://datos.salud.gob.ar/dataset/covid-19-casos-registrados-en-la-republica-argentina



## Contribuciones

Las contribuciones son bienvenidas. Si deseas contribuir, por favor abre un issue o envía un pull request con tus cambios.

## Contacto

Para cualquier consulta o colaboración, puedes contactarme a través de:

- *Email*: magalicazellam@gmail.com
- *LinkedIn*: https://www.linkedin.com/in/magali-cazella-mendez/
- *Instagram*: https://www.instagram.com/magali.cm22?igsh=NTRrdTUzZzhhaHM1 

¡Gracias por tu interés en el proyecto!
