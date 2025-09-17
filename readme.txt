📊 Generador de Diagramas de Gantt
Este es un programa de línea de comandos (CLI) en Python diseñado para automatizar la creación de Diagramas de Gantt interactivos de alta calidad. Utiliza las potentes librerías Plotly y Pandas para procesar datos de tareas, aplicar validaciones robustas y generar visualizaciones dinámicas que se pueden ver en el navegador o exportar a múltiples formatos.
✨ Características Principales
* Interactividad: Genera gráficos interactivos con Plotly, permitiendo hacer zoom, desplazarse y ver detalles de las tareas al pasar el ratón (incluyendo Progreso, Categoría y Dependencias).
* Múltiples Fuentes de Datos: Soporta dos métodos de entrada de datos:
   * Manual: Ingreso de tareas a través de prompts interactivos en la consola (--manual).
   * Archivos: Carga de datos directamente desde archivos CSV o Excel (--file).
* Visualización Detallada:
   * Las tareas se colorean automáticamente por Categoría/Grupo.
   * Muestra el porcentaje de Progreso directamente sobre la barra de la tarea.
   * Identifica y marca visualmente los Hitos (Milestones) con un símbolo de diamante rojo (para tareas donde la fecha de inicio es igual a la de fin).
* Gestión de Dependencias: Dibuja flechas básicas entre tareas para representar las relaciones de dependencia (Fin-a-Inicio).
* Validación de Datos: Incluye lógica de validación para garantizar que las fechas sean válidas, que la fecha de fin sea posterior o igual a la de inicio, que los nombres de las tareas sean únicos, y que las dependencias ingresadas existan.
* Formatos de Salida Flexibles: Permite guardar el gráfico en formato HTML (interactivo), PNG, JPG o SVG (--output).
🛠️ Requisitos e Instalación
Este programa requiere Python 3.x y las siguientes librerías.
Instalación de Librerías
Utiliza pip para instalar todas las dependencias necesarias. Se incluye openpyxl para manejar archivos Excel y kaleido para la exportación de imágenes (PNG, JPG, SVG).
pip install plotly pandas openpyxl kaleido

🚀 Uso
El script principal está diseñado para ser ejecutado desde la línea de comandos utilizando el módulo argparse para gestionar los argumentos.
1. Estructura de Datos de Archivo
Si optas por la entrada de archivo, tu CSV o Excel debe contener (al menos) estas columnas. Las columnas Progress, Dependencies y Category son opcionales y se llenarán con valores predeterminados si faltan.
Columna
	Descripción
	Formato de Ejemplo
	Task
	Nombre único de la tarea
	Diseño de Interfaz
	Start
	Fecha de inicio
	2025-01-01, 1/15/2025, etc.
	Finish
	Fecha de fin
	2025-01-10
	Progress
	Porcentaje completado (opcional)
	50 (número entre 0 y 100)
	Category
	Grupo o fase del proyecto (opcional)
	Planning, Development
	Dependencies
	Nombres de tareas de las que depende, separadas por coma (opcional)
	Task A, Task B
	2. Ejecución desde la Consola
Puedes elegir entre ingresar datos manualmente o cargar un archivo. Si no se especifica el argumento --output, el gráfico se mostrará interactivamente en tu navegador.
Entrada Manual
python gantt_chart_generator.py --manual

(El programa te pedirá interactivamente el número de tareas y los detalles de cada una).
Entrada desde Archivo (CSV/Excel)
# Ejemplo con archivo CSV
python gantt_chart_generator.py --file datos_proyecto.csv

# Ejemplo con archivo Excel
python gantt_chart_generator.py --file datos_proyecto.xlsx

Guardar el Gráfico
Utiliza el argumento --output para guardar el gráfico en tu disco. El formato se infiere automáticamente por la extensión del archivo.
# Guardar como archivo HTML interactivo
python gantt_chart_generator.py --file datos_proyecto.csv --output gantt_interactivo.html

# Guardar como imagen PNG
python gantt_chart_generator.py --manual --output gantt_imagen.png