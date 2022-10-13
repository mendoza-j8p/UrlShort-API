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

 Crear algunas carpetas para dividir lógicamente mi código. Mis carpetas en este caso son controlador, entidad, servicio, repositorio, dto y config.

 ## Implementación

 Dentro de la carpeta de la entidad, vamos a crear una clase Url.java con cuatro atributos: id, longUrl, createdDate, expiresDate.

 A continuación, creemos un BaseService .java en la carpeta del servicio. BaseService contiene métodos para convertir de base 10 a base 62 y viceversa.

 Dentro de la carpeta del repositorio, creemos el archivo UrlRepository.java , que es solo una extensión de JpaRepository y nos brinda muchos métodos como 'findById', 'save', etc.

 Luego, creemos un archivo UrlController.java en la carpeta del controlador. El controlador debe tener un método POST para crear enlaces cortos y un método GET para redirigir a la URL original.

 El método POST tiene UrlLongRequest como cuerpo de solicitud. Es solo una clase con atributos longUrl y expiresDate.

 El método GET toma una URL corta como variable de ruta y luego obtiene y redirige a la URL original. En la parte superior del controlador, se inyecta UrlService como una dependencia

 UrlService .java es donde se encuentra la mayor parte de la lógica y es el servicio utilizado por el controlador.

 ConvertToShortUrl es utilizado por el método POST del controlador. Simplemente crea un nuevo registro en la base de datos y obtiene una identificación. Luego, la ID se convierte en un enlace corto de base 62 y se devuelve al controlador.

 GetOriginalUrl es un método utilizado por el método GET del controlador. Primero convierte una cadena a base 10, y el resultado es una identificación. Luego obtiene un registro de la base de datos con esa identificación y lanza una excepción si no existe. Después de eso, devuelve la URL original al controlador.


 Después de agregar las dependencias de Maven, es hora de agregar la configuración de Swagger. Dentro de la carpeta de configuración, necesitamos crear una nueva clase: SwaggerConfig .java













