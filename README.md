# **IMPACTO DE EMERGENCIA SANITARIA EN CERTIFICACIONES POR PATOLOGÍAS RESPIRATORIAS**

*Daniela Elola - EAD2*

## Índice

    Introducción 
    Objetivo general y objetivos específicos
    Datos
    Metodología
    Resultados
    Conclusión
    Anécdotario
    

## Introducción 

En el año 2020 con la llegada al país del virus SARS-COV2 (COVID-19) se decretó a partir del 13/03 la emergencia sanitaria por pandemia.
Con el decreto y dada la incertidumbre que esto generó por el desconocimiento de los riesgos, tanto en los servicios de salud como en las personas, pudo haber aumentado la cantidad de consultas médicas por patologias respiratorias que derivaron en certificaciones médicas laborales.
Con este análisis se pretende verificar si hubo impacto en el ingreso de certificaciones médicas laborales por afecciones respiratorias.
    
    
## Objetivo general y objetivos específicos

*Intención del análisis: Verificar si la Emergencia Sanitaria tuvo incidencia registrándose un aumento de certificaciones laborales.

* Se registraron más certificaciones vinculadas a afecciones respiratorias?
* Qué porcentaje representan las certificaciones por afecciones respiratorias respecto al total de certificaciones?
* De qué sexo predominan las certificaciones? cuál es la relación entre ellos?
* Se puede identificar una franja etárea con mayor cantidad de certificaciones?
* Qué departamento de Uruguay registró mayor registro de certificaciones y cómo es la relación con los demás?


## Datos

Los datos para el análisis fueron extraidos de la base de certificaciones médicas ingresadas por los prestadores de salud en el portal de BPS.

El dataset está compuesto por 3 archivos csv con la información bimensual del registo, completando así el primer semestre del año 2020.
Por temas de confidencialidad de la información, fueron eliminadas de los csv datos relativos a los profesionales que actuaron en cada acto médico, y los números de documento de las personas fueron encriptados para no ser identificadas.

Las patologías consideradas para el análisis, son aquellas de afecciones respiratorias sin especificar: 

|Código Patología | Descripción | 
|---:|---:|
| J00   |  RINOFARINGITIS AGUDA (RESFRIADO COMUN)  | 
| J22 | INFECCION AGUDA NO ESPECIFICADA DE LAS VIAS RESPIRATORIAS INFERIORES |  
| J069   |  INFECCION AGUDA NO ESPECIFICADA DE LAS VIAS RESPIRATORIAS INFERIORES  |  
| J111   |  INFLUENZA CON OTRAS MANIFESTACIONES RESPIRATORIAS, VIRUS NO IDENTIFICADO  |  
| J209    |  BRONQUITIS AGUDA, NO ESPECIFICADA  |  
| J989   |  TRASTORNO RESPIRATORIO, NO ESPECIFICADO  |  


## Metodología

- Se genera un único data frame a partir de los 3 archivos csv con la data.
- Se realiza una primer exploración de los datos con el métodos head(). 
- Se eliminan las columnas que no aportan y se renombran utlizando formato snake_case aquellas columnas que sirven al análisis.
- Se aplica el método info() para conocer la cantidad de datos y su tipo.
- Aplicando drop_duplicates se eliminan los registros de certificaciones duplicadas.
- Se definen funciones para ajustar el formato fecha de acuerdo con las necesidades y se agrega una columna al data frame con el dato mes.
- Se generan estructuras auxiliares (diccionarios, data frames) para guardar información parcial y poder analizarla y graficar los resultados obtenidos.


## Resultados

### Para las preguntas planteadas en los objetivos, luego del análisis de los datos, se obtiene:


* _**Se registraron más certificaciones vinculadas a afecciones respiratorias?**_


    - Durante marzo y a partir de ese mes se indentifica un aumento en le registro de certificaciones por afecciones respiratorias.
    

|Mes/2020 | Cantidad de cert patologias respiratorias |
|---:|---:|
| Enero | 1657 |
| Febrero | 1643 |
| Marzo | 18300 |
| Abril | 8701 |
| Mayo | 3878 | 
| Junio | 6603 | 




* _**Qué porcentaje representan las certificaciones por afecciones respiratorias respecto al total de certificaciones?**_


    - La tendencia es al aumento, luego del pico de marzo baja el porcentaje pero se mantiene mayor a los valores antes de la emergencia sanitaria.
    
    
|Mes/2020 | Total_Cert | Cert_J | Porcentaje |
|---:|---:|---:|---:|
| Enero   |  72385  |  1657  |  2.28  |
| Febrero |  66634  |  1643  |  2.46  |
| Marzo   |  107018  |  18300  |  17.09  |
| Abril   |  79312  |  8701  |  10.97  |
| Mayo    |  63227  |  3878  |  6.13  |
| Junio   |  76296  |  6603  |  8.65  |




* _**De que sexo predominan las certificaciones? cuál es la relación entre ellos?**_


    - En todos los meses analizados predominan las certificaciones de mujeres que representan 62.85 % de las certificaciones por patologías respiratorias registradas en el semestre. La relación es de 1.69 en el promedio del semestre, es decir que por cada hombre certificado se certifican casi 2 mujeres. La diferencia más grande se visualiza en el mes de marzo cuando la relación pasa a ser de 1.8.

|Total_J | Mujer | Hombre | Relación |
|---:|---:|---:|---:|
| 40782   |  25632  |  15150  |  1.69  

* _**Se puede identificar una franja etárea con mayor cantidad de certificaciones?**_


    - Esta distribución es muy dispersa. Pre pandemia se ubica entre los 20 y los 80 años, y post pandemia se identifica una ampliación de las franjas etáreas con registro de certificaciones que va de los 3 a los 115 años de edad.
    
|Edad mínima Cert| Edad máxima Cert | Promedio |
|---:|---:|---:|
| 3   |  115  |  49  | 



* _**Qué departamento de Uruguay registró mayor registro de certificaciones y cómo es la relación con los demás?**_


    - Los registros en Montevideo son más del doble de las certificacioens ingresadas en el país por afecciones respiratorias con el 54,12%. La distribución de las certificacioens médicas por departamento es acorde con la población. Se presenta el top 5.
    
|Departamento | Cantidad Cert
|---:|---:|
|MONTEVIDEO | 22073
|CANELONES | 7024
|MALDONADO |  2095
|SAN JOSE  | 1169
|COLONIA   | 885


        
## Conclusión

Si bien al inicio de la emergencia sanitaria se registró un aumento sustantivo en el ingreso de certificaciones totales y en particular de certificaciones por afecciones respiratorias, esta tendencia disminuye en los siguientes 3 meses. A pesar de la baja identificada en la tendencia, las cantidades de certificaciones por patologías respiratorias se mantienen por encima de valores pre pandemia. 

--> Se podría profundizar este análisis e incluso ampliar el período considerado pero se haría inmanejable el volumen de datos dado la cantidad de informacion que surje de los registos mensuales de certificaciones médico laborales de todo el país.


## Anécdotas 

Al comienzo del análisis se pretendía identificar si hubo un incremento en el registro de certificaciones por estrés laboral a partir del decreto de la emergencia sanitaria, no habiéndose encontrado diferencias significativas que pudieran representarse gráficamente, se optó por cambiar el enfoque.


