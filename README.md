**Caso práctico**

Este caso quiere representar una petición formal de un cliente para realizar un análisis de datos a
partir de una extracción de una de sus aplicaciones, algo habitual en el mercado de BI.

Es nuestra labor como especialistas en el análisis el realizar el diseño de arquitectura de todo el
sistema de análisis, modelado de base de datos, carga de la misma y explotación de los datos.

**Requerimientos del cliente**

Nuestro cliente es un departamento de una multinacional del sector de las telecomunicaciones que
gestiona las peticiones e incidencias que se producen en una serie de servicios y entornos que la
compañía da a sus empleados y clientes.

Cada vez que hay una petición de acceso o una incidencia de funcionamiento, los usuarios abren un
ticket en la herramienta de ticketing para informar y que se proceda a su solución. El cliente nos ha
hecho llegar una exportación de datos del año 2020 y hasta finales de agosto de 2021 de cara a
analizar algunas preguntas que querrían resolver en formato gráfico mediante informes o
dashboards.

**El cliente pone a nuestra disposición la siguiente arquitectura tecnológica:**

• Base de datos MySQL

• ETL Pentaho Data Integration

• Frontend analítico Microsoft PowerBI o Tableau Public


**A modo de resumen, nuestro cliente quiere saber:**

• La evolución del volumen de tickets general y diferenciado por incidencias y peticiones.

• Si ha variado la prioridad con la que se abren los tickets en los últimos meses (% de peso
por prioridad)

• Cuáles son los servicios que acumulan más tickets y de ellos cuáles son los que menos
cumplen los SLAs

• Cuáles son los servicios con más backlog acumulado (tickets abiertos en la actualidad)

• Cuáles son los entornos en que se resuelven más rápido y más lentos los tickets

• Volumetría de tickets en entornos productivos respecto a entornos no productivos

• Posibilidad de filtrar por prioridad, por tipo de ticket y por servicio.


**Nuestro cliente nos indica que le gustaría disponer de la siguiente documentación del proyecto:**

• Esquema de base de datos

• Documentación de los procesos de carga

• Comprobaciones realizadas de la exactitud de los datos

o Valores esperados según dataset de carga

o Comprobaciones en SQL (via query directa)

o Comparación con PowerBI (datos MySQL vs resultados en PowerBI/Tableau)

• Funcionalidades y visualizaciones desarrolladas en PowerBI o Tableau

• Decisiones de diseño tomadas en los diferentes pasos

**Información Dataset**

El dataset suministrado es un fichero Excel que contiene los siguientes campos.
El cliente nos ha dado un pequeño detalle de lo que hay en cada uno.

• Fecha de creación. Especifica el momento en que se crea el ticket. Servirá para hacer el
análisis temporal.

• Número de incidente. Identificador único del ticket.

• Descripción. Breve descripción de la petición o incidencia.

• Servicio. Los diferentes servicios que presta la compañía a sus usuarios y clientes.

• Tipo de servicio. Especifica si es una petición o una incidencia:

  o Incidencias: Restauración de infraestructura o restauración de servicio a usuario
  
  o Peticiones: Petición de serv. Por el usuario
  
• Prioridad. Especifica la prioridad con la que debe ser tratado el ticket.

  o Hay cuatro prioridades, ordenadas de más importante a menos: Crítica, Alta, Media
y Baja.

  o Sólo las incidencias pueden tener prioridad crítica y sólo deben considerarse en
entornos de producción.

• Estado. Indica la situación del ticket.

  o Un ticket se considera acabado si está en estado Cerrado o Resuelto.
  
  o Un ticket se considera abierto si está pendiente o asignado.
  
  o Los tickets cancelados no se computan.
  
• Torre. Es un agrupador funcional de servicios. Cada servicio pertenece a una torre de
gestión.

• Entorno. Indica el entorno en el que afecta el ticket. Los entornos productivos son todos
aquellos que contienen un PRO.

• Estado cumplimiento. Indica si el ticket se ha resuelto en los tiempos requeridos por el
cliente o no.

  o Dentro del objetivo de servicio: ticket resuelto adecuadamente

  o Objetivos de servicio incumplidos: ticket resuelto tarde.

• Duración días. Número de días que se ha tardado en resolver el ticket
