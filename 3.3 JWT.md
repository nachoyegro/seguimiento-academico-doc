# JSON Web Token (JWT)
## Introducción

Un JSON Web Token es un token compuesto por tres partes separadas por un punto. Tiene la siguiente forma:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.
eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNTgyMDU5ODUzLCJqdGkiOiJmYWQ0NWQ1MzExZmM0NjRlYWQ1MjhmNGI2Yjc4OGVjZSIsInVzZXJfaWQiOjEsImNhcnJlcmFzIjpbIlciXSwidXNlcm5hbWUiOiJhZG1pbiJ9.LLrL5DM3Q0odd9b7poTG928Tlf_3L9-rrovxrXX1eMk
```

Aunque parece que no tenga sentido, es en realidad una forma muy compacta de representar una serie de pedidos, junto con una firma para verificar su autenticidad.

La primer parte se denomina "header", e indica cuál es el algoritmo usado para desencriptar la tercer parte del token

```json
{
"typ": "JWT",
"alg": "HS256"
}
```

La segunda parte se denomina "payload" y tiene los datos que quieren ser transportados entre el cliente y el servidor.
En el caso de SADI, es importante saber cuáles son las carreras que el usuario puede ver.

```json
{
  "token_type": "refresh",
  "exp": 1582059853,
  "jti": "e9b85778f3f44decba69a611e4e1c700",
  "user_id": 1,
  "carreras": [
    "W"
  ],
  "username": "admin"
}
```

```
HMACSHA256(
    base64UrlEncode(header) + "." +
    base64UrlEncode(payload),
    clave-secreta
)
```

## Problemas que resuelve

A pesar de que el principal propósito de JWTs es transferir demandas entre dos partes, el aspecto más importante es el de estandarizar una estructura de datos de forma simple y encriptada. 
Los principales problemas que resuelve son:
- Autenticación
- Autorización
- Identidad Federada
- Sesiones del lado del cliente

## Client-side/Stateless Sessions

Las llamadas sesiones sin estado (stateless sessions) son en realidad datos del lado del cliente (client-side). El aspecto fundamental de esta aplicación reside en el uso de firmas y posiblemente encriptación para proteger el contenido de la sesion. Como los datos del lado del cliente pueden ser manipulados con facilidad. Por esta razón, se tiene que tener mucho cuidado desde el backend.

JWTs, en virtud de JWS y JWE, puede proveer distintos tipos de firmas y encriptación. Las firmas son útiles para validar los datos contra posibles manipulaciones. La encriptación es útil para proteger los datos de ser leídos por terceros.

### ¿Es útil tener una sesión del lado del cliente?

Existen pros y contras a cualquier decisión, y las sesiones client-side no son la excepción. Algunas aplicaciones pueden requerir sesiones muy grandes. Enviando este estado ida y vuelta hacia el backend por cada request (o grupo de requests) puede vencer rápidamente los beneficios que trae JWT. Es necesario un buen balance entre los datos del lado del cliente y las búsquedas a la base de datos del backend.
En el caso del SADI, resulta útil saber qué carreras tiene permiso de ver un Director. O qué materias puede ver un alumno, por ejemplo.
Teniendo estos datos en el payload, no es necesario hacer búsquedas en la base de datos para chequear por cada request, que el usuario tiene permisos de ver lo que esta requiriendo.

## Tokens de acceso y refresh

Los tokens de acceso (access) y refresh son dos tipos de tokens que ayudan en el contexto de autenticación y autorización.

Los tokens de acceso son tokens que dan a aquel que lo tenga, el acceso a recursos protegidos. Éstos tokens son de corta vida y tienen una fecha de expiración como dato. Tienen, además, otra información que puede ser de ayuda para identificar al cliente. Esta información adicional está definida en la implementación.

Por el contrario, los tokens de refresh le da permiso a los clientes que pidan un nuevo acceso. Por ejemplo, luego de que un token de acceso expiró, un cliente puede hacer un pedido de un nuevo acceso al servidor de autorización. Para que ésto pueda suceder, es requerido un token de refresh.
A diferencia de los tokens de acceso, el tiempo de vida del token de refresh suele ser largo.

# Gráfico de access y refresh token

La principal diferencia entre el token de acceso y el de refresh, está en la posibilidad de hacer los tokens de acceso fáciles de validar. Un token de acceso que tiene una firma, no hace falta que sea validado por un servidor de autorización.
Los tokens de refresh, por el contrario, necesita que se acceda al servidor de autorizaciones. Manteniendo la validación separada de las queries al servidor de autorización, es posible obtener una mejor latencia.
Para asegurar que la pérdida o robo de tokens no sea determinante, se debería poner un tiempo de vida corto.
Los tokens de refresh, al ser de vida prolongada, tienen que ser protegidos contra estas incidencias. 
Una opción es agregarlo a una lista negra y cuando alguien pida un access token, éste es expirado automáticamente.


## JSON Web Tokens en detalle

Todos los JWTs son construidos a partir de tres elementos diferentes: el encabezado (header), los datos (payload) y la firma. Los primeros dos elementos son objetos JSON de una estructura determinada. El tercero es dependiente del algoritmo usado para encriptar y, en el caso de un JWT desencriptado, éste es ignorado.
Los JWTs pueden ser encodeados en una representación compacta conocida como JWS/JWE Compact Serialization.
Las especificaciones JWS y JWE definen un tercer formato de serialización conocido como JSON Serialization, una representación no compacta que permite múltiples firmas en el mismo JWT.

La serialización compacta es una codificación Base64 segura para URL de los 2 bytes UTF-8 de los dos primeros elementos JSON (el header y el payload) y los datos, como requeridos, para firmar o encriptar. Estos datos también son encodeados como Base64. 
Estos tres elementos están separados por puntos (".").
JWT usa una variante de Base64 que es segura para URLs. Este encoding basicamente sustituye los caracteres "+" y "/" por los caracteres "-" y "_" respectivamente.
Los caracteres que se usan como relleno también son removidos.
Esta variante es conocida como base64url.

