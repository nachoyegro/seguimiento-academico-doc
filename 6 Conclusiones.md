# Conclusiones

>> Va plural o que?
A lo largo de esta tesis se han investigado numerosas herramientas de software para construir una solución para la centralización, disposición, análisis y visualización de datos académicos.

En primer lugar, se pensó una solución como servicios independientes, intercambiables y escalables según la necesidad. Esto facilita que si en un futuro aparece una tecnología superadora para una tarea en particular, sólo se tenga que reemplazar ese servicio.

Se ha logrado crear un Núcleo que almacena datos y los entrega a través de una API REST, la cual puede ser consmumida por usuarios que tengan los permisos correspondientes.

Se creó un servicio para el análisis de los datos consultados al núcleo, el cual también entrega el resultado del procesamiento de esos datos para que puedan ser consumidos.

Luego, se creó un servicio que facilita la visualización de los datos procesados. Éste consume los datos del módulo de análisis y muestra los resultados en forma de gráfico de columnas, gráfico de tortas, gráficos de radar, gráficos de puntos, tablas, etc.

Este conjunto de servicios les permite a las partes interesadas consultar la información, modificarla, consultar métricas sobre carreras, materias y alumnos de forma individual o colectiva y consultar datos sobre períodos en particular.
Esta solución se ajusta perfectamente a la arquitectura provista por la Universidad.

Se ha aprendido acerca de la importancia de la disposición de los datos y cómo esto puede ayudar a tomar decisiones tempranas sobre la vida académica de la Universidad Nacional de Quilmes, sus carreras, sus materias y su alumnado.


# Lineas de Trabajos futuros

Dado que el sistema se pensó de forma tal que se pueda extender fácilmente, y que sus datos puedan ser consultados por otros servicios, existen varias mejoras y puntos de extensión que se detallan a continuación:

## Aplicación para alumnos

Podría existir una aplicación para que usen los alumnos (puede ser móvil o web), donde puedan consultar su historial dentro de la Universidad. Si bien esta tarea se puede realizar en Guaraní, se podría integrar con servicios que brinda la universidad, como la consulta del saldo disponible en la tarjeta de la UNQ, notificaciones con novedades y noticias que estén relacionadas únicamente con los alumnos.
Esta aplicación, a su vez, puede tener un aspecto mas social: que los alumnos pongan tips y consejos sobre las materias.
Además, podría recibir feedback sobre los que ya cursaron, los horarios, las comodidades, la calidad de enseñanza, etc.

## Integración con Guaraní

Sería muy conveniente poder conectar el Núcleo con Guaraní a través de una API web. En la actualidad no existe dicha API, pero con el lanzamiento de Guaraní 3 debería ser posible. De esta forma, no se deberían importar más los datos a través de planillas, sino que se haría de forma automática a través del Núcleo.

## Integración con sistema de encuestas de inscripción

El sistema actual que utilizan algunas carreras de la UNQ para consultar las posibles inscripciones de los alumnos debería ser integrado al núcleo para que consuma datos, y luego debería enviar los resultado para luego con esa información mostrar métricas a los directores de carreras. 


## GraphQL en el núcleo

GraphQL es un lenguaje de queries para APIs, donde los clientes definen precisamente qué datos quieren en lugar de recibir todos los datos disponibles. Esto significaría una reducción en el tamaño de respuesta de la API del núcleo.

## Proveedor de identidad (IDP)

Dado que el potencial de extensión es amplio, una buena forma de desligarle responsabilidades al núcleo es crear un proveedor de identidad. En lugar de los usuarios identificarse ante el núcleo y que este les provea un token, debería hacerlo un servicio independiente que tenga conocimiento de todos los usuarios, y éste se encargue de validar quién puede ingresar y quién no, y qué permisos tiene.

## Acceso Centralizado

Una vez que exista el IDP, sería muy útil un acceso centralizado. Esto significa que, una vez que el usuario se identifica con el IDP, éste lo considera *logueado* en todas las aplicaciones que el usuario tiene acceso. Cuando ingrese a otra aplicación, automáticamente el IDP lo deja ingresar.



