## Requerimientos funcionales

Los usuarios deben poder ingresar una URL larga. Nuestro servicio debería guardar esa URL y generar un enlace corto.

Al hacer clic en el enlace corto, se debe redirigir al usuario a la URL larga original.

Los usuarios deben tener la opción de ingresar la fecha de vencimiento. Una vez que haya pasado esa fecha, el enlace corto debería ser inválido.

Los usuarios deben crear una cuenta para utilizar el servicio. Los servicios pueden tener un límite de uso por usuario (opcional)

El usuario puede crear su propio enlace corto: el servicio debe tener métricas, por ejemplo, los enlaces más visitados (opcional)

## Requerimientos no funcionales

El servicio debe estar en funcionamiento el 100% del tiempo

La redirección no debe durar más de dos segundos

## Conversión de URL

 La opción sería convertir números de base 10 a base 62.
 La conversión de URL se puede implementar de varias formas diferentes, y cada forma tiene sus pros y sus contras.

 El uso de la base 62 en la conversión de URL con una longitud máxima de siete caracteres nos permite tener 62^7 valores únicos para enlaces cortos.

 Vamos a utilizar la función de incremento automático de nuestra base de datos. El número de incremento automático se utilizará para la conversión de base 62. Se puede usar cualquier otra base de datos que tenga una función de incremento automático.

## Estructura

 Dependecias Spring Web y MySql Driver.

 













(https://desarrolloweb.com/articulos/trabajar-ramas-git.html)