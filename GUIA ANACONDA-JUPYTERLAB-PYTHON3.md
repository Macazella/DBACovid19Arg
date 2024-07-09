Guía de Instalación y Uso de Anaconda y JupyterLab para Manipulación de Base de Datos 

  

Esta guía proporciona los pasos necesarios para instalar Anaconda, configurar JupyterLab y manipular una base de datos utilizando Pandas en Python, con un ejemplo utilizando el archivo `Covid19Casos.csv`. 

  

## Instalación de Anaconda 

  

1. **Descarga de Anaconda:** 

   - Visita [Anaconda.com](https://www.anaconda.com/products/distribution) y descarga la versión adecuada de Anaconda para tu sistema operativo (Windows, macOS, Linux). 

    

2. **Instalación:** 

   - Sigue las instrucciones de instalación proporcionadas por Anaconda. Asegúrate de marcar la opción "Add Anaconda to my PATH environment variable" durante la instalación si estás en Windows, o ajustar la configuración según tu sistema operativo. 

  

3. **Verificación de la Instalación:** 

   - Abre una terminal (en Windows, puedes usar Anaconda Prompt) y verifica que Anaconda esté instalado correctamente ejecutando: 

     ```bash 

     conda --version 

     ``` 

  

## Configuración y Uso de JupyterLab 

  

1. **Entorno Virtual (Opcional pero recomendado):** 

   - Crea un nuevo entorno virtual para este proyecto (recomendado): 

     ```bash 

     conda create --name mi_entorno python=3.8 

     conda activate mi_entorno 

     ``` 

  

2. **Instalación de JupyterLab:** 

   - Instala JupyterLab dentro de tu entorno virtual ejecutando: 

     ```bash 

     conda install jupyterlab 

     ``` 

  

3. **Ejecución de JupyterLab:** 

   - Inicia JupyterLab desde tu terminal ejecutando: 

     ```bash 

     jupyter lab 

     ``` 

   - Se abrirá automáticamente en tu navegador web predeterminado. 

  

4. **Manipulación de la Base de Datos** 

  

   A continuación se muestra un ejemplo básico de cómo cargar y manipular el archivo `Covid19Casos.csv` utilizando Pandas en JupyterLab: 

  

   ```python 

   import pandas as pd 

  

   # Cargar el archivo CSV en un DataFrame 

   df = pd.read_csv('Database_csv/Covid19Casos.csv') 

  

   # Visualizar las primeras filas del DataFrame 

   print(df.head()) 

  

   # Realizar manipulaciones y análisis de datos con Pandas 

   # Ejemplo: Calcular estadísticas descriptivas 

   print("\nEstadísticas descriptivas de la columna 'edad':") 

   print(df['edad'].describe()) 

  

   # Ejemplo: Filtrar datos por alguna condición 

   df_filtrado = df[df['clasificacion_resumen'] == 'Confirmado'] 

  

   # Guardar cambios en un nuevo archivo CSV (opcional) 

   df_filtrado.to_csv('Database_csv/Covid19Casos_filtrado.csv', index=False) 

  

   # Mostrar el DataFrame filtrado 

   print("\nPrimeras filas del DataFrame filtrado:") 

   print(df_filtrado.head()) 

   ``` 

  

   Asegúrate de adaptar y expandir este ejemplo según las necesidades específicas de tu proyecto y los análisis que desees realizar con los datos del archivo `Covid19Casos.csv`. 

  

--- 