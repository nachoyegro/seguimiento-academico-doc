## Crecimiento exponencial de los datos.

La humanidad, hasta el año 2005, creó 130 ExaBytes de datos (un exabyte son 1.073.741.824 GB). Para el año 2010, la cantidad de datos subió a 1200 exabytes. Para el año 2015, la cantidad de datos subió a 7900 exabytes. Y para el año 2020, se estima que esa cantidad llegó a los 40900 exabytes. [[14]]

En resumen, la cantidad de datos que producimos los humanos está creciendo exponencialmente, y las universidades no son la excepción.


## El papel de las universidades con respecto a los datos
Hoy en dia, se está transformando más en una norma que en una excepción para las universidades del mundo utilizar los datos que tienen sobre los estudiantes para propósitos académicos. Hay universidades que usan estos datos para ayudar a los estudiantes a tener éxito, o para ofrecerles ayuda cuando se considera que no están rindiendo, o bien para mantenerlos cursando y seguir recibiendo ingresos, en el caso de las privadas.
El análisis de los datos se hace cada vez más frecuentementemente, y de manera más eficiente ya que las herramientas de análisis fueron mejorando.


### Universidad de San Francisco
En la Universidad de San Frascisco (USF), los datos de los estudiantes tales como asistencia, notas, y materias son usados para determinar su progreso [[12]]. Cuando ven que un alumno está teniendo dificultades, usando la tecnología desarrollada por el departamento de sistemas de USF, alertan a los tutores para que hablen con el estudiante [[12]].
Además, usan una aplicación móvil llamada USFMobile, que consulta datos de sus sistemas y generan alertas.
Eventualmente, esos datos serán usados para "entender qué hacen los alumnos, y tratar de ayudarlos" [[12]].


### Universidad de Missouri
La Universidad de Missouri arma cuestionarios de 12 preguntas para los alumnos. El propósito es conocer cómo los estudiantes se desenvuelven en términos académicos, sociales y financieros. En caso que un alumno indique alguna inquietud, esa información es utilizada para tener un mayor impacto [[13]]. Los datos son almacenados en los sitemas de la universidad.
Los tres temas principales que mostró la encuesta, estan relacionados con las dificultades de algunos cursos, la asistencia y las dificultades financieras de los alumnos. Estos datos le dieron a la Universidad un panorama y pudo actuar rápidamente en consecuencia. [[13]]


### Universidad Estatal de Georgia 
La Universidad Estatal de Georgia se convirtió en un ejemplo a nivel nacional en Estados Unidos, por el papel que adaptó para ayudar a los estudiantes de bajos recursos y los de primera generación. 
Esta universidad usa análisis predictivos para identificar a los alumnos que podrían abandonar o no llegar a recibirse. Esto lo logran usando información pasada, la cual es utilizada para predecir futuros eventos. 
La Universidad de Georgia analizó 2 millones y medio de calificaciones obtenidas por los estudiantes a lo largo de 10 años para crear una lista de factores que predecían qué alumnos son menos probables a graduarse. Este sistema tiene más de 800 alertas, apuntadas a indicarle a los tutores acerca de sus estudiantes y así poder ayudarlos. Por ejemplo, un tutor recibe un alerta cuando un estudiante no recibe una nota satisfactoria en una materia que es fundamental. 


## Trabajos relacionados

### eCoach
ECoach es una aplicación diseñada en la Universidad de Michigan para estudiantes de primer año que toman clases de ciencia, tecnología, ingeniería o matemática. Esta aplicación toma datos que las universidades ya tienen, como las materias que cursó un alumno, las notas, etc.
Otro aspecto importante de esta aplicación, es que se recibe *feedback* de parte de los alumnos con respecto a materias, profesores, horarios, etc.


## El papel de la Universidad Nacional de Quilmes

La Universidad Nacional de Quilmes tiene en la actualidad alrededor de >>Alumnos<<, y a lo largo de su historia tuvo >>Alumnos<<. Esos alumnos cursaron materias, tuvieron notas, y dejaron información que no está siendo explotada.
Si un director de una carrera determinada, quisiera tener los datos de sus alumnos, tiene que hacer un pedido formal y esos datos se les son entregados en forma de planilla. Esos datos no están normalizados, y no existe un estándar. Es decir, un año vienen de una forma, y otro año de otra forma diferente.

### Planillas de datos

Las planillas de datos que se le son 
>> Como guarani no tiene datos, las carreras analizan con planillas

#### Planes de estudio

Los datos de planes de estudio traen información de las materias junto con el área a la que pertenecen, el núcleo, y los créditos, entre otros.
Las columnas de la planilla es de la siguiente forma:

>> Tabla 2
- [Código de Carrera](CARRERAS.md)
- **Plan de Estudios**
- **Cuatrimestre (sólo número)**
- [Núcleo](NUCLEOS.md)
- **Área de Materia**
- **Cod. de Materia**
- **Créditos**
- **Nombre**

Con esta información, alcanzaría para tener los datos de las carreras, los planes y las materias.

#### Datos personales

La planilla de datos personales trae la siguiente información en orden: 

>> Tabla 3
- Legajo
- DNI
- Apellido
- Nombre
- Email
- Fecha (formato dd/mm/YYYY)
- [Código de Carrera](CARRERAS.md)
- Plan de Estudios

Estos datos son de ayuda para que los directores puedan identificar a los alumnos.

#### Materias cursadas

Esta es, quizás, la planilla más cargada de datos ya que trae el historial de cursadas de una carrera determinada. Cada fila representa la cursada de un alumno en una materia determinada.

>> Tabla 4
- **Legajo**
- DNI
- [Carrera](CARRERAS.md)
- Regular (?)
- Calidad (?)
- **Materia (Código de Guaraní)**
- **Nombre (de la materia)**
- **Fecha** *formato dd/mm/yyyy*
- [Resultado](RESULTADOS.md)
- **Nota**
- **Forma de Aprobación**
- Crédito
- Acta Promoción
- Acta Exámen
- **Plan**

#### Inscripciones

Esta planilla indica las inscripciones a una materia por parte de un alumno.

>> Tabla 5
- [Código de Carrera](CARRERAS.md)
- DNI
- Legajo
- Código de materia
- Comision
- Fecha (formato dd/mmm/YYY)


## Análisis de requerimientos

Luego de hacer un análisis de requerimientos con directores de las distinas carreras de la Universidad Nacional de Quilmes, se llegó a que las principales necesidade son:

- Se necesita que puedan calcularse el *avance de carrera*, *avance de diplomatura* y *avance de ciclo introductorio* en base a los créditos.
- Se necesita que puedan calcularse el porcentaje de materias aprobadas del total de la Carrera, el porcentaje de materias del Ciclo Básico, el porcentaje de materias del Ciclo Avanzado, el porcentaje de las Complementarias y el porcentaje del Ciclo Introductorio.
- Se necesita que puedan calcularse el porcentaje por área, que en el caso de la Licenciatura en Informática, estas áreas son:
    - Programación.
    - Sistemas Informáticos.
    - Procesos Informáticos.
    - Desarrollo de Software.
    - Teoría de la Computación.
aunque cada carrerá deberá tener asignadas sus áreas.
- Se necesita cumplir con los pedidos específicos de CONEAU:
    - Postulantes: cantidad de alumnos que se anotaron.
    - Ingresantes: cantidad de alumnos que cursaron al menos una materia del Ciclo Introductorio.
    - Alumnos: Los que no son ingresantes. Alumnos activos >> Buscar definicion 

    - Tabla de ingresantes por cohorte.
    - Tabla de cursantes por cohorte.
    - Tabla de graduados por cohorte.
    - Tasas de crecimiento anual y por cuatrimestre de las carreras, cursantes y solo ingresantes.
- Se necesita, con respecto a una materia determinada, conocer:
    - Cantidad de aprobados.
    - Cantidad de ausentes.
    - Cantidad de desaprobados.

- Estudiantes con una determinada materia aprobada, que distinga en: materia aprobada por equivalencia, examen libre, pendiente, acta de cursada comun.

- Poder ver de los inscriptos a una materia cuáles son recursantes, y cuántas veces.

- Análisis retrospectivos y riesgos de deserción en base al historial general de la carrera.
- Identificar cuáles son las materias que “traban” a los estudiantes en las carreras. 
- Predicción de Inscriptos.
- Análisis de cumplimientos de prerrequisitos según plan de estudios.

## Conclusión

Al implementar esta solución, los datos estarán disponibles para ser consultados por las carreras. Además, existe un potencial para que esta solucion pueda ser extendida en el futuro y que esto implique una mejor experiencia también para los alumnos.
Llevar a cabo este proyecto implicará una mejora en cuanto a decisiones que se pueden tomar con respecto a los alumnos en pos de una mejor calidad educativa. Ayudará a determinar qué alumnos estan teniendo problemas, qué materias están trabando a los alumnos, cuáles son los alumnos que corren riego de desersión, cuáles están cerca de recibirse, etc.



