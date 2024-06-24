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

3. *Configurar la Base de Datos*:
    - Ejecuta los scripts SQL proporcionados en el repositorio para crear las tablas y cargar los datos iniciales.

## Contribuciones

Las contribuciones son bienvenidas. Si deseas contribuir, por favor abre un issue o envía un pull request con tus cambios.

## Contacto

Para cualquier consulta o colaboración, puedes contactarme a través de:

- *Email*: magalicazellam@GMAIL.COM.com
- *LinkedIn*: https://www.linkedin.com/in/magali-cazella-mendez/
- *Instagram*: https://www.instagram.com/magali.cm22?igsh=NTRrdTUzZzhhaHM1 

¡Gracias por tu interés en el proyecto!
