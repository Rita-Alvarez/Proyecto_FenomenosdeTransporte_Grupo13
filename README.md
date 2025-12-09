<img width="250" height="250" alt="uni" src="https://github.com/user-attachments/assets/0b5c2b56-014a-4dd2-bde5-61c644031df4" />

<h1 align="center"> Perfil de Temperaturas en Paneles Solares Fotovoltaicos </h1>

<h6 align="center"> Grupo 13 </h6>
<h6 align="center"> Rita Álvarez, Gonzalo Marín, Benjamín Ponce, Josefa Prieto </h6>

## Índice
* [Descripción del proyecto](#Descripción-del-proyecto)
* [Método numérico](#Método-numérico)
* [Código](#Código)
* [Resultados](#Resultados)

## Descripción del proyecto

## Método numérico

El método numérico utilizado para la modelación de transferencia de calor fue el método de discretización de Crank-Nicolson de segundo orden en las dimensiones espacial y temporal. Las ventajas de la utilización de este método es que ofrece una aproximación de alta precisión, además de que tiene una estabilidad incondicional que permite elegir pasos de tiempo relativamente grandes sin que la solución numérica se inestabilice, siendo de esta manera ideal para nuestro tipo de proyecto, dado que se eligió como paso de tiempo un día completo.

En primer lugar, se define una malla uniforme tanto para ambas dimensiones. Para el caso temporal se divide el tiempo total $D$ en $N_j$ nodos, mientras que para el caso espacial se divide el espesor total $L$ en $N_i$ nodos. Posteriormente, para la discretización del modelo, se emplean términos de temperatura evaluados en una posición $x_i$ en un tiempo $t_j$. Se discretiza la ecuación gobernante y se reordenan los términos correspondientes, para finalmente representarla de manera matricial. Finalmente, se discretizan las condiciones iniciales junto con las condiciones de borde utilizando las mismas notaciones.

## Código

El lenguaje utilizado para la elaboración de los códigos fue Python versión 3.11.4. Para los cálculos númericos y la generación de gráficos se emplearon las bibliotecas Numpy y Matplotlib respectivamente.

Se realizaron dos simulaciones para dos meses distintos del año, específicamente enero y julio, esto debido a que estos son los meses que presentan las temperaturas ambientales promedio más altas y bajas respectivamente, lo que permite analizar el comportamiento del modelo para distintas condiciones externas extremas. Los archivos se organizaron en dos carpetas distintas:

"Simulación Enero": Contiene el script correspondiente para las condiciones de enero, además de un anexo de los gráficos resultantes.

"Simulación Julio": Incluye el script correspondiente para las condiciones de julio junto con un anexo de los gráficos obtenido.

Además, en la carpeta "Anexos" se encuentra un archivo llamado "Base de datos Grupo 13.xlsx". Este archivo almacena todos los datos iniciales, parámetros y condiciones de contorno de un período de un año completo, donde se extrajeron los datos para las simulaciones de enero y julio. También, en esta misma carpeta se encuentran el esquema de la composición del panel fotovoltaico junto con el esquema de la transferencia de calor dentro del mismo para un mayor entendimiento de lo que ocurre dentro de este en las distintas capas, además del sistema de referencia utilizado. Ambos códigos se pueden correr de manera independiente y no necesitan ningún paso previo.

##Resultados
