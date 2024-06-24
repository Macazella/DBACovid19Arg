# DBACovid19Arg
DB creada a partir de bases de datos del Ministerio de Salud de Argentina
# DBACovid19Arg

Este repositorio contiene el modelo de base de datos para el seguimiento del COVID-19 en Argentina. El modelo ha sido creado y gestionado utilizando Oracle Apex. A continuación, se presenta una descripción detallada del proyecto y sus componentes.

## Descripción del Proyecto

El objetivo de este proyecto es consolidar y analizar datos relacionados con la pandemia de COVID-19 en Argentina. Las principales áreas de enfoque incluyen:

- *Vacunación*: Información sobre las dosis aplicadas.
- *Casos Ambulatorios*: Datos de casos que no requirieron hospitalización.
- *Casos Internados y Fallecidos*: Información sobre casos severos que resultaron en hospitalización o fallecimiento.
- *Total de Casos Confirmados*: Contabilización de todos los casos confirmados de COVID-19.

## Modelo de Base de Datos

El modelo de base de datos incluye las siguientes tablas principales:

### 1. 1ra_y_2da_dosis_aplicadas_cuenta

Esta tabla unifica la información sobre las dosis de vacunación aplicadas:

- *ID*: Identificador único de la entrada.
- *Fecha*: Fecha de la aplicación de la dosis.
- *Primera_Dosis*: Cuenta de primeras dosis aplicadas.
- *Segunda_Dosis*: Cuenta de segundas dosis aplicadas.
- *Ubicación*: Lugar donde se aplicaron las dosis.

### 2. Casos_Ambulatorio

Esta tabla almacena datos sobre los casos ambulatorios:

- *ID*: Identificador único del caso.
- *Fecha_Diagnostico*: Fecha del diagnóstico.
- *Edad*: Edad del paciente.
- *Sexo*: Sexo del paciente.
- *Ubicación*: Ubicación del caso.
- *Estado*: Estado actual del caso (recuperado, activo).

### 3. Casos_Internados_y_Fallecidos

Esta tabla incluye información sobre los casos más severos:

- *ID*: Identificador único del caso.
- *Fecha_Ingreso*: Fecha de ingreso al hospital.
- *Fecha_Fallecimiento*: Fecha de fallecimiento (si aplica).
- *Edad*: Edad del paciente.
- *Sexo*: Sexo del paciente.
- *Ubicación*: Ubicación del caso.
- *Estado*: Estado actual del caso (internado, fallecido).

### 4. Total_Casos_confirmados

Esta tabla registra el total de casos confirmados:

- *ID*: Identificador único del registro.
- *Fecha_Reporte*: Fecha del reporte de casos.
- *Total_Casos*: Número total de casos confirmados hasta esa fecha.
- *Ubicación*: Ubicación de los casos reportados.

## Herramientas Utilizadas

- *Oracle Apex*: Para la creación y gestión del modelo de base de datos.
- *SQL*: Para la consulta y manipulación de datos.
- *PL/SQL*: Para procedimientos almacenados y funciones.

## Cómo Empezar

1. *Clonar el Repositorio*:
    sh
    git clone https://github.com/tuusuario/DBACovid19Arg.git
    

2. *Importar el Modelo de Base de Datos*:
    - Inicia sesión en Oracle Apex.
    - Crea una nueva aplicación e importa el modelo de base de datos:
      Aquí tienes una guía paso a paso sobre cómo generar un usuario en Oracle Apex:

## Cómo Crear un Usuario en Oracle Apex

### Prerrequisitos

Antes de comenzar, asegúrate de que tienes acceso de administrador a tu instancia de Oracle Apex.

### Pasos para Crear un Usuario

1. *Iniciar Sesión en Oracle Apex*:
   - Abre tu navegador y accede a la URL de tu instancia de Oracle Apex.
   - Inicia sesión con tu usuario de administrador.

2. *Navegar a la Administración de Usuarios*:
   - Una vez que hayas iniciado sesión, selecciona el ícono de "App Builder" si no te encuentras ya allí.
   - En la parte superior derecha, haz clic en el menú desplegable (con tu nombre de usuario) y selecciona "Administration" (Administración).

3. *Crear un Usuario Nuevo*:
   - En la página de administración, selecciona "Manage Users and Groups" (Gestionar Usuarios y Grupos).
   - Haz clic en el botón "Create User" (Crear Usuario).

4. *Rellenar los Detalles del Usuario*:
   - Completa los campos necesarios para el nuevo usuario:
     - *Username*: Nombre de usuario.
     - *Email*: Correo electrónico del usuario.
     - *Password*: Contraseña (puedes generar una contraseña temporal que el usuario deberá cambiar al iniciar sesión).
     - *Confirm Password*: Confirmar la contraseña.
     - *User is an administrator*: Selecciona esta opción si el usuario debe tener permisos de administrador.
     - *Account Availability*: Asegúrate de que la opción "Account is unlocked" (Cuenta desbloqueada) esté seleccionada para que el usuario pueda iniciar sesión.
   - Configura los roles y privilegios según las necesidades del usuario.

5. *Guardar el Nuevo Usuario*:
   - Una vez que hayas rellenado todos los campos necesarios, haz clic en el botón "Create User" (Crear Usuario).

6. *Notificar al Usuario*:
   - Informa al nuevo usuario sobre sus credenciales y cómo iniciar sesión en Oracle Apex.

### Ejemplo de Detalles para el Usuario

Supongamos que estás creando un usuario para Magalí Julieta Cazella Méndez:

- *Username*: m.j.cazella
- *Email*: magali@example.com
- *Password*: (configura una contraseña temporal que Magalí deberá cambiar al iniciar sesión)
- *User is an administrator*: Selecciona si debe tener permisos de administrador.
- *Account Availability*: Asegúrate de que la cuenta esté desbloqueada.

### Nota Adicional

Si deseas crear un usuario directamente mediante un script SQL, puedes hacerlo así:

sql
BEGIN
   APEX_UTIL.CREATE_USER(
       p_user_name        => 'm.j.cazella',
       p_email_address    => 'magali@example.com',
       p_web_password     => 'temporalPassword123',
       p_developer_privs  => 'ADMIN',
       p_change_password_on_first_use => 'Y'
   );
   COMMIT;
END;


Este script crea un usuario con el nombre de usuario m.j.cazella, un correo electrónico magali@example.com y una contraseña temporal temporalPassword123. El usuario deberá cambiar la contraseña la primera vez que inicie sesión y se le otorgan privilegios de administrador.

Siguiendo estos pasos, podrás crear y gestionar usuarios en tu instancia de Oracle Apex de manera efectiva.

2. 
3. *Configurar la Base de Datos*:
    - Ejecuta los scripts SQL proporcionados en el repositorio para crear las tablas y cargar los datos iniciales. (IN PROGRESS)
  
4.  4. Procedimientos Almacenados y Triggers
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

6.  Respaldo y Restauración
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
- Tablas: http://datos.salud.gob.ar/dataset/vacunas-contra-covid-19-dosis-aplicadas-en-la-republica-argentina
http://datos.salud.gob.ar/dataset/vacunas-contra-covid19-dosis-aplicadas-en-la-republica-argentina
http://datos.salud.gob.ar/dataset/covid-19-casos-registrados-en-la-republica-argentina
http://datos.salud.gob.ar/dataset/dosis-aplicadas-a-nivel-nacional


## Contribuciones

Las contribuciones son bienvenidas. Si deseas contribuir, por favor abre un issue o envía un pull request con tus cambios.

## Contacto

Para cualquier consulta o colaboración, puedes contactarme a través de:

- *Email*: magalicazellam@GMAIL.COM.com
- *LinkedIn*: https://www.linkedin.com/in/magali-cazella-mendez/
- *Instagram*: https://www.instagram.com/magali.cm22?igsh=NTRrdTUzZzhhaHM1 

¡Gracias por tu interés en el proyecto!
