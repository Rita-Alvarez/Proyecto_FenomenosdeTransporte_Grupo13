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

<h3> Contexto </h3>

Chile cuenta con una geografía excepcionalmente favorable para la generación de energías renovables, donde destaca el Desierto de Atacama por ser conocido mundialmente como el punto que recibe mayor cantidad de radiación, teniendo una radiación anual que supera los 2500 $kW/m^2$, convirtiéndose en un lugar óptimo y estratégico para la instalación de centrales energéticas de paneles solares. Actualmente, Atacama constituye más del 90% de la capacidad fotovoltaica de todo Chile, lo que favorece a la transición de energías más limpias.

Sin embargo, estas mismas condiciones extremas a su vez generan un problema: el sobrecalentamiento de las celdas fotovoltaicas provocan una disminución en la eficiencia de los mismo paneles, de modo que se termina generando menos energía que la capacidad máxima permitida. Se estima que un aumento de 1°C por sobre los 25°C en el material puede costar un 0.4% del rendimiento del panel, lo que implica una pérdida significativa de energía, puesto que no se está generando lo mismo que la capacidad máxima instalada de cada panel solar.

<h3> Proyecto </h3>

El proyecto se centra en la modelación y simulación numérica de la transferencia de calor a través de un panel solar fotovoltaico ubicado en el Desierto de Atacama. El objetivo principal es estudiar la evolución del perfil de temperatura a través de las distintas capas del panel para analizar cómo el sobrecalentamiento de las celdas fotovoltaicas afectan en la eficiencia energética. Esto permitirá que en futuro se puedan proponer mejoras en los diseños y materiales de los paneles.

<h3> Importancia </h3>

La importancia del proyecto radica en su contribución a la eficiencia y sustentabilidad de la industria energética chilena. Al determinar con precisión el perfil de temperatura de los paneles solares es posible determinar una optimización de diseño y materiales, siendo beneficiados directamente las empresas energéticas ya que implementar esto conlleva un mayor retorno de la inversión. Además, es un apoyo directo para los objetivos de transición energética a fuentes renovables y la descarbonización del país.

<h3> Modelo </h3>

Para realizar el modelamiento, se realizó un esquema de un panel solar fotovoltaico. Se consideró que este está constituído por cinco capas: vidrio, EVA superior, celdas fotovoltáicas, EVA inferior y tedlar. A continuación, se presenta un diseño representativo del mismo panel.

![Esquema panel fotovoltaico](https://github.com/user-attachments/assets/27c83a5e-6254-42db-b432-4723cb4942d0)


El modelo integra los tres mecanismos de transferencia: conducción interna, convección y radiación. A continuación, se presenta un esquema detallado de la transferencia de calor dentro de las distintas capas del panel solar fotovoltaico.

![Esquema transferencia de calor](https://github.com/user-attachments/assets/2588691b-3513-489b-b5dd-df2b737f50b7)

Los supuestos realizados para el modelo fueron:

1. Flujo unidireccional (eje x).
2. Material sólido (se eliminan términos de velocidad).
3. Propiedades termofísicas constantes k, ρ, $C_p$.
4. Largo y ancho son mucho más grandes que el espesor.
5. La temperatura del aire es menor a la temperatura del panel, por lo que la convección va en dirección hacia el aire.
6. La capa del vidrio da hacia el cielo y el tedlar hacia el suelo.
7. El efecto de la radiación angular es despreciable respecto a la global.

## Método numérico

El método numérico utilizado para la modelación de transferencia de calor fue el método de discretización de Crank-Nicolson de segundo orden en las dimensiones espacial y temporal. Las ventajas de la utilización de este método es que ofrece una aproximación de alta precisión, además de que tiene una estabilidad incondicional que permite elegir pasos de tiempo relativamente grandes sin que la solución numérica se inestabilice, siendo de esta manera ideal para nuestro tipo de proyecto, dado que se eligió como paso de tiempo un día completo.

En primer lugar, se define una malla uniforme tanto para ambas dimensiones. Para el caso temporal se divide el tiempo total $D$ en $N_j$ nodos, mientras que para el caso espacial se divide el espesor total $L$ en $N_i$ nodos. Posteriormente, para la discretización del modelo, se emplean términos de temperatura evaluados en una posición $x_i$ en un tiempo $t_j$. Se discretiza la ecuación gobernante y se reordenan los términos correspondientes, para finalmente representarla de manera matricial. Finalmente, se discretizan las condiciones iniciales junto con las condiciones de borde utilizando las mismas notaciones.

## Código 

<h3> Tecnologías utilizadas </h3>

El lenguaje utilizado para la elaboración de los códigos fue Python versión 3.11.4. Para los cálculos númericos y la generación de gráficos se emplearon las bibliotecas Numpy y Matplotlib respectivamente.

<h3> Archivos </h3>

Los archivos se organizaron en dos carpetas distintas:

"Simulación Enero": Contiene el script correspondiente para las condiciones de enero, además de un anexo de los gráficos resultantes llamados "Evolución temporal temperatura enero.png" y "Perfil temperatura enero.png"

"Simulación Julio": Incluye el script correspondiente para las condiciones de julio junto con un anexo de los gráficos obtenido llamados "Evolución temporal temperatura julio.png" y "Perfil temperatura julio.png"

Además, en la carpeta "Anexos" se encuentra un archivo llamado "Base de datos Grupo 13.xlsx". Este archivo almacena todos los datos iniciales, parámetros y condiciones de contorno de un período de un año completo, donde se extrajeron los datos para las simulaciones de enero y julio. También, en esta misma carpeta se encuentran el esquema de la composición del panel fotovoltaico junto con el esquema de la transferencia de calor dentro del mismo para un mayor entendimiento de lo que ocurre dentro de este en las distintas capas, además del sistema de referencia utilizado. Ambos códigos se pueden correr de manera independiente y no necesitan ningún paso previo.

<h3> Script </h3>

Se realizaron dos simulaciones para dos meses distintos del año, específicamente enero y julio, esto debido a que estos son los meses que presentan las temperaturas ambientales promedio más altas y bajas respectivamente, lo que permite analizar el comportamiento del modelo para distintas condiciones externas extremas. Cada simulación presenta la misma estructura, sin embargo, los únicos valores que cambian son las temperaturas ambientes por hora, irradiancia por hora y la velocidad del aire por hora. Al final de cada script es posible generar dos gráficos distintos, el primero correspondiene al perfil de temperatura en °C del panel a las 8, 12 y 16 horas; el segundo correspondiente a la evolución temporal en horas de las capas superficie frontal, centro del panel y la superficie posterior. También, al final del código se entregan los valores de temperatura mínima y temperatura máxima que alcanza el panel en °C.


## Resultados
