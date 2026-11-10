GA1-220501094-01-AA1-EV04 – Fundamentos en Pandas Explorando Instacart: descubre
patrones de compra
Descripción de la actividad:
Las plataformas de comercio electrónico recopilan información sobre los pedidos realizados por sus
clientes, los productos seleccionados, los horarios de compra y la frecuencia con la que los usuarios
realizan nuevas compras. Esta información constituye una fuente importante para comprender el
comportamiento de los consumidores y reconocer patrones de consumo.
En esta actividad, el aprendiz asumirá individualmente el rol de analista de datos de Instacart, una
plataforma de compras de supermercado, y deberá resolver una situación problemática mediante la
exploración de cinco conjuntos de datos suministrados.
El propósito es fortalecer los conocimientos relacionados con la importación de archivos CSV, la
estructura de los DataFrames, la inspección de registros, la indexación, el filtrado lógico y las
operaciones estadísticas básicas utilizando Python y Pandas.
Situación problemática
El equipo encargado de analizar las operaciones de Instacart necesita conocer las características de
los datos registrados en su plataforma. Aunque dispone de información sobre pedidos, productos,
departamentos, pasillos y artículos incluidos en las compras, requiere identificar qué información
contienen los archivos y cómo puede consultarse para responder preguntas relacionadas con el
comportamiento de los clientes.
Para ello, se solicita al aprendiz realizar una exploración inicial de los conjuntos de datos,
identificar su estructura, consultar registros específicos y obtener indicadores básicos que permitan
comprender la información disponible.
Pregunta orientadora del problema:
¿Cómo utilizar Python y la librería Pandas para explorar los datos de Instacart, identificar las
características de los pedidos y productos, y obtener información relevante sobre los hábitos de
compra de sus clientes?

GFPI-F-135 V04

Archivos de trabajo
Para desarrollar la actividad «Explorando Instacart: descubre patrones de compra con Python y
Pandas», el aprendiz utilizará los siguientes archivos CSV:
N.o Archivo Descripción Registros Columnas
1 instacart_orders.csv

Información de los pedidos realizados por los clientes,
incluyendo identificadores de usuarios, días, horarios
y frecuencia de compra.

478.967 6

2 products.csv

Catálogo de productos disponibles, con sus
identificadores y clasificación por pasillos y
departamentos.

49.694 4

3 aisles.csv Información de los pasillos utilizados para clasificar

los productos. 134 2

4 departments.csv Información de los departamentos o categorías

generales de productos. 21 2

5 order_products.csv

Relación de los productos incluidos en los pedidos,
posición de incorporación al carrito e información de
recompra.

4.545.007 4

Nota: Los archivos se encuentran en formato CSV y utilizan el punto y coma (;) como separador.
Para importarlos correctamente mediante Pandas, se debe utilizar el parámetro sep=";" en la función
pd.read_csv().

2. Secuencia didáctica e instrucciones para el aprendiz
Momento 1. Comprensión del problema y reconocimiento de los datos
Instrucciones:
1. Lea la situación problemática presentada.
2. Revise los materiales de formación relacionados con la estructura de los DataFrames y el
uso de Pandas.
3. Identifique los cinco archivos suministrados y explique qué información considera que
almacena cada uno.
4. Reconozca qué columnas podrían utilizarse para identificar pedidos, usuarios y productos.
5. Formule tres preguntas de análisis relacionadas con los hábitos de compra que puedan
responderse mediante las operaciones básicas estudiadas.
Registre en su Notebook la descripción del problema, las preguntas y una explicación sobre la
importancia de explorar los datos antes de analizarlos.

GFPI-F-135 V04
Momento 2. Importación y exploración inicial de los archivos
Instrucciones:
1. Cree un Notebook en Jupyter o Google Colab.
2. Importe la librería Pandas con el alias pd.
3. Cargue los cinco archivos CSV utilizando read_csv().
4. Tenga en cuenta que los archivos utilizan punto y coma (;) como separador.
5. Almacene cada conjunto de datos en un DataFrame con un nombre representativo.
6. Utilice head() y tail() para observar los primeros y últimos cinco registros de cada DataFrame.
7. Utilice shape para identificar la cantidad de filas y columnas.
Como punto de partida, puede utilizar la siguiente estructura:
import pandas as pdorders = pd.read_csv( "instacart_orders.csv", sep=";")products = pd.read_csv( "products.csv",
sep=";")aisles = pd.read_csv( "aisles.csv", sep=";")departments = pd.read_csv( "departments.csv",
sep=";")order_products = pd.read_csv( "order_products.csv", sep=";")
Ajuste las rutas de los archivos según su entorno de trabajo.
Preguntas de análisis:
• ¿Cuál de los cinco DataFrames contiene más registros?
• ¿Cuál contiene menos columnas?
• ¿Qué diferencias identifica entre los datos de pedidos y los datos de productos?
• ¿Por qué es importante conocer las dimensiones de un conjunto de datos?
Documente sus respuestas con los resultados obtenidos.
Momento 3. Reconocimiento de la estructura y calidad inicial de los datos
Instrucciones:
Utilice los atributos columns, dtypes, shape y el método info() para identificar las características de cada
DataFrame.
Desarrolle las siguientes tareas:
1. Identifique los nombres de las columnas de cada archivo.
2. Determine qué columnas contienen valores enteros, decimales o texto.
3. Identifique cuáles son los campos que permiten relacionar conceptualmente los diferentes
conjuntos de datos.
4. Examine el número de valores no nulos reportado por info().
5. Compare el número de registros con la cantidad de valores no nulos para reconocer posibles
datos ausentes.

GFPI-F-135 V04

6. Elabore una tabla de diagnóstico con el nombre del archivo, cantidad de filas, cantidad de
columnas y observaciones sobre los datos.
Preguntas de análisis:
• ¿Qué diferencias existen entre int64, float64 y object?
• ¿Qué información proporciona info() que no se obtiene directamente con shape?
• ¿En qué columnas se observan valores ausentes?
• ¿Qué posibles dificultades podrían generar estos valores en un análisis posterior?
No es necesario corregir ni eliminar registros en esta fase. El objetivo es reconocer las
características y posibles limitaciones de los datos.
Momento 4. Indexación y filtrado lógico de la información
Instrucciones:
Utilice los métodos de selección e indexación estudiados para consultar información específica de
los archivos.
Desarrolle los siguientes ejercicios:
N.o Requerimiento DataFrame
1 Seleccione únicamente product_id y product_name. products
2 Consulte los productos cuyo department_id sea igual a 1. products
3 Seleccione los pedidos realizados a las 10 horas. orders
4 Filtre los pedidos cuyo order_dow sea igual a 0. orders
5 Consulte los pedidos con order_number superior a 10. orders
6 Identifique los pedidos cuyo days_since_prior_order sea superior a 15. orders
7 Seleccione los registros cuyo valor de reordered sea igual a 1. order_products
8 Consulte los productos incorporados en la primera posición del carrito
(add_to_cart_order igual a 1). order_products
Posteriormente, aplique dos filtros con condiciones simultáneas:
• Pedidos realizados a las 10 horas y con order_number superior a 10.
• Productos que pertenezcan al departamento 1 y tengan un aisle_id superior a 50.
Preguntas de análisis:
• ¿Qué diferencia existe entre seleccionar columnas y filtrar filas?
• ¿Qué ventajas ofrece loc[] al consultar información específica?

GFPI-F-135 V04

• ¿Qué ocurre con la cantidad de registros cuando se aplican varias condiciones?
• ¿Por qué es importante utilizar correctamente los operadores lógicos?
Cada ejercicio deberá contener el código utilizado, la salida obtenida y una explicación breve de su
resultado.
Momento 5. Obtención e interpretación de indicadores básicos
Instrucciones:
Utilice las operaciones estadísticas básicas estudiadas en los materiales para obtener información
sobre el comportamiento de los pedidos.
Resuelva las siguientes preguntas utilizando los métodos de Pandas correspondientes:

Pregunta Operación sugerida
¿Cuántos registros de pedidos contiene el archivo? shape o count()
¿Cuántos registros de productos contiene el catálogo? shape
¿Cuál es el promedio de order_number? mean()
¿Cuál es el promedio de days_since_prior_order entre los valores disponibles? mean()
¿Cuántos registros de artículos tienen reordered igual a 1? Filtrado y conteo
¿Cuál es la suma de la columna reordered? sum()
¿Qué características estadísticas presenta order_hour_of_day? describe()
¿Qué características estadísticas presenta add_to_cart_order? describe()
Después de obtener los resultados, elabore una tabla que contenga la pregunta analizada, el valor
obtenido y su interpretación.
Importante: diferencie entre cantidad de registros, cantidad de pedidos y cantidad de usuarios. No
interprete automáticamente el número de filas como el número de clientes diferentes.
Momento 6. Resolución del problema y presentación del producto
Instrucciones:
A partir de los resultados obtenidos, elabore una síntesis individual que responda la pregunta
orientadora de la actividad.
Incluya:
1. Las tres preguntas de análisis formuladas inicialmente y sus respectivas respuestas.
2. Una descripción de los principales hallazgos sobre los pedidos y productos.

GFPI-F-135 V04

3. Una explicación de cómo la indexación y los filtros permitieron consultar información
relevante.
4. Las limitaciones identificadas en los conjuntos de datos.
5. Tres conclusiones sustentadas en los resultados de los ejercicios.
Finalmente, verifique que el Notebook ejecute correctamente las operaciones y que las respuestas
correspondan a los datos obtenidos.
Ambiente requerido
• Ambiente de formación presencial o virtual, con equipos de cómputo que permitan ejecutar
Python y la librería Pandas.
• Se requiere un entorno de desarrollo como Jupyter Notebook o Google Colab, acceso a los
cinco archivos CSV suministrados y disponibilidad de los materiales de consulta. Se
recomienda contar con memoria suficiente para procesar los archivos, especialmente
order_products.csv, debido a su volumen de registros.
Estrategias o técnicas didácticas activas
• Estrategia principal: Aprendizaje Basado en Problemas (ABP), con desarrollo individual.
Materiales de formación y Material de apoyo
Materiales de formación:
Documento «Materiales de ciencia de datos», especialmente los contenidos relacionados con la
librería Pandas, DataFrames, lectura de archivos CSV, indexación, filtrado lógico, conteos, sumas,

promedios y descripciones estadísticas. Link de los recursos: https://educated-show-
144.notion.site/Materiales-de-ciencia-de-datos-
3fe4671e02a1807aa6cae213e826c33b?source=copy_link

Material de apoyo: los cinco archivos suministrados:
• instacart_orders.csv
• products.csv
• aisles.csv
• departments.csv
• order_products.csv
Link Datasets:
https://drive.google.com/drive/folders/19vYGYdE0hI1DzvpBcCZskzJ0u2TZjwas?usp=
drive_link
Adicionalmente, los ejemplos prácticos de los materiales de formación y la documentación oficial
de Pandas servirán como recursos de consulta.

GFPI-F-135 V04

Evidencias de aprendizaje:
Producto formativo individual
El aprendiz entregará un Notebook de Jupyter (.ipynb) titulado «Exploración de datos de
Instacart con Python y Pandas», que incluya la comprensión del problema, la carga de los
archivos, la exploración de los DataFrames, los ejercicios de indexación y filtrado, el cálculo
de indicadores, la interpretación de resultados y las conclusiones individuales.