# JSON Web Token (JWT)
## Introducción

## Problemas que resuelve

## Client-side/Stateless Sessions

Las llamadas sesiones sin estado (stateless sessions) son en realidad datos del lado del cliente (client-side). El aspecto fundamental de esta aplicación reside en el uso de firmas y posiblemente encriptación para proteger el contenido de la sesion. Como los datos del lado del cliente pueden ser manipulados con facilidad. Por esta razón, se tiene que tener mucho cuidado desde el backend.

JWTs, en virtud de JWS y JWE, puede proveer distintos tipos de firmas y encriptación. Las firmas son útiles para validar los datos contra posibles manipulaciones. La encriptación es útil para proteger los datos de ser leídos por terceros.

### ¿Es útil tener una sesión del lado del cliente?

Existen pros y contras a cualquier decisión, y las sesiones client-side no son la excepción. Algunas aplicaciones pueden requerir sesiones muy grandes. Enviando este estado ida y vuelta hacia el backend por cada request (o grupo de requests) puede vencer rápidamente los beneficios que trae JWT. Es necesario un buen balance entre los datos del lado del cliente y las búsquedas a la base de datos del backend.
En el caso del SADI, resulta útil saber qué carreras tiene permiso de ver un Director. O qué materias puede ver un alumno, por ejemplo.
Teniendo estos datos en el payload, no es necesario hacer búsquedas en la base de datos para chequear por cada request, que el usuario tiene permisos de ver lo que esta requiriendo.

## Access y Refresh Tokens




### Gráfico de access y refresh token

## JSON Web Tokens en detalle

Todos los JWTs son construidos a partir de tres elementos diferentes: el encabezado (header), los datos (payload) y la firma. Los primeros dos elementos son objetos JSON de una estructura determinada. El tercero es dependiente del algoritmo usado para encriptar y, en el caso de un JWT desencriptado, éste es ignorado.
Los JWTs pueden ser encodeados en una representación compacta conocida como JWS/JWE Compact Serialization.
Las especificaciones JWS y JWE definen un tercer formato de serialización conocido como JSON Serialization, una representación no compacta que permite múltiples firmas en el mismo JWT.

La serialización compacta es una codificación Base64 segura para URL de los 2 bytes UTF-8 de los dos primeros elementos JSON (el header y el payload) y los datos, como requeridos, para firmar o encriptar. Estos datos también son encodeados como Base64. 
Estos tres elementos están separados por puntos (".").
JWT usa una variante de Base64 que es segura para URLs. Este encoding basicamente sustituye los caracteres "+" y "/" por los caracteres "-" y "_" respectivamente.
Los caracteres que se usan como relleno también son removidos.
Esta variante es conocida como base64url.
