# ClubApp
Proyecto gestion club deportivo

Laboratorio de Programación y Lenguajes 2023
Trabajo Práctico Obligatorio
Lenguaje de programación C#
Facultad de Ingeniería
Universidad Nacional de la Patagonia San Juan Bosco
2
Especificación de los trabajos finales de lenguajes de programación unificados por
el uso de una base de datos PostgreSQL.
Los trabajos finales de lenguajes utilizan una base relacional PostgreSQL, de esta forma
se deberá interactuar de una forma ordenada y organizada para lograr la ejecución
correcta de las consultas, ya que el motor procesa en forma de consultas las interacciones
que se programen para dar solución a lo que indique en los requerimientos del sistema.
Sistema de gestión del club deportivo
El Club deportivo la "Vuelta Olímpica" es un club que requiere un sistema de
gestión que permita el registro de la información de sus socios, en el club se
cuentan con diversas actividades para realizar, información de las cuotas cobradas
y los horarios de las actividades que realizan los socios, guiados por profesores
registrados para ello. Del registro de toda la información se pretende obtener una serie
de listados.
Funcionalidad necesaria del sistema (aspectos generales).
 A nivel funcional el sistema deberá realizar registro de todas las entidades
indicadas,
actualización de información (No ha eliminación de datos).
 Se va a requerir que cada ingreso de información o interacción con el usuario sea
validado, por ejemplo, no ingresar nombres de localidades sin texto, socios, profesores,
con
datos completos, si se debe leer un dato numérico o fecha se deben validar, ... etc.
 El registro de los horarios, deben validar que exista la actividad, el profesor, y el día
/ lugar sin previa asignación.
Un ejemplo de actividades es:
 - fútbol
 - basketball
 - volleyball
 - tenis
 - natación
 - gimnasio y musculación
 - etc...
Los datos requeridos para cualquier socio que se registra en el sistema son:
 - Dni
 - Apellido
 - Nombres
 - Domicilio
 - Localidad a la que pertenece
 - Teléfono de contacto
 - Observaciones, agregadas por si requiere algún tratamiento especial en las rutinas
asignadas.
 - activo sirve para marcar si el socio está habilitado para acceder a hacer actividades.
 - moroso, si está marcado como moroso por atraso en pagos de las cuotas.
Una vez que el socio está registrado, éste debe pagar mensualmente las
cuotas de membresía por actividad que realiza, puestas al cobro del 1 al 10 de cada
mes, si hubiera retrasos en el pago, se marcará el campo "moroso" del socio para
que figure en listado del sistema que verifica esta situación.
El socio si no continua por alguna cuestión, se deja marcado como inactivo,
3
por si vuelve a retomar las actividades en el club, no se elimina.
Mensualmente los días 20 o 21 se procesa con los socios activos la
generación mensual de las cuotas que deben abonar del 1 al 10 del próximo mes, es
decir existe un padrón o listado de cuotas creadas mes a mes, año a año por cada
socio / actividad donde esté inscripto.
Cuando se crean quedan con una fecha de vencimiento, siempre será el 10
del mes siguiente del que se está generando, también un estado de la cuota I:
Impaga, importe según el tipo de actividad y su valor de cuota vigente, cuando se
registra el pago de la cuota se registra el estado en P: Pagada y la fecha del pago.
Si un socio decide dejar de asistir y se le generaron cuotas, que están pendientes
de cobro, esas cuotas al momento de indicar (funcionalidad) el abandono, se marcan
las cuotas como A: Anuladas.
Respecto de las actividades, en el sistema se debe reflejar el profesor que
guía y dirige la actividad, la información disponible de los profes es Legajo, Dni,
Apellido, Nombres, Domicilio, Telefono.
Se ha decidido registrar los historiales de los importes al cobro por actividad,
es decir hay información año a año de lo que ha costado cada actividad, esta
información se usa para el cálculo de lo que debe abonar el socio, si el socio tiene
más de una actividad donde está inscripto éste tendrá varias instancias de cuotas
según el nro de actividades.
El sistema registrará los diferentes importes a aplicar en el año, mes a mes,
este historial podrá dar una noción de la evolución de los valores. Esta operación se
aplicará antes de gestionar las cuotas.
4
Desarrollo en lenguaje C #
Objetivos
Desarrollo de una aplicación interactiva que sea robusta y valide las diferentes
acciones dadas por el usuario, que sea amigable y fácil de utilizar.
Requerimientos

● Completar el modelo, según los ejemplos de referencia (modelo, relaciones,
configuraciones).
● Desarrollar pantallas con validaciones para ingresar y actualizar
información de las siguientes entidades:
- localidad(código postal, nombre)
- socio(nro de socio, dni, apellido, nombres, domicilio, teléfono,
activo, moroso)
- tipos de actividades(código, descripción) - futbol, basket,
tenis, natación, aparatos, baile
- importe tipo actividades(código, código tipo actividad, año,
mes, importe)
- profesores(legajo, apellido, nombre, domicilio, telefono)
- actividades(codigo, cod tipo actividad, cod profesor, fecha
desde, observaciones)
- actividades socio(codigo, codigo actividad, cod socio, fecha
inicio, fecha fin)
- cuotas(codigo, cod actividad socio, año, mes,
estado(pendiente, pagado, anulado), importe, fecha
vencimiento, fecha de pago)
- horarios(Dia(lunes, martes, miércoles, jueves, viernes), cod
actividad socio,Hora desde, hora hasta, lugar)
Lugar: salon 1, salon 2, salon 3 Lunes-1, Martes-2, Miércoles3, Jueves-4, Viernes-5
 Posibilitar la exportación a archivos la información del sistema, desde
los listados(el usuario deberá indicar el nombre del archivo).
Considerar las opciones de ordenamiento.
 Implementar la funcionalidad que permita la generación de las cuotas
 Implementar la funcionalidad que permita el registro de los diferentes
horarios y permite listarlos.
 Implementar funcionalidad de abandono de un socio, también la
activación del mismo si vuelve al club.
Configuración para acceso a la base de datos PostgreSQL, en fuente App.config
encontraran para configurar datos de servidor, usuario y Password, en la cadena de
conexión, para conectarse.
5
Se proveerá

- Proyecto de referencia para iniciar el desarrollo de la aplicación WinForms.
 En el proyecto las clases para gestión ORM
 Formularios para interacción
 Código base de validación
 Código base de inicialización de controles
Formularios
De los formularios provistos se contará con:
- Formulario para realizar operación de Alta y Modificación integrado en un solo
fuente, dependerá de la operación de las validaciones y que se permite
actualizar, lo mismo la lógica para guardar nueva información o actualizar datos
en la base de datos.
- Formulario par listar información de una entidad, con la aplicación de filtros
- Formulario para la búsqueda en una entidad.
Programación en los formularios
Cada formulario de ingreso de información cuenta con lógica para la validación de
los datos, con lo cual se programan conjuntos de eventos para que el usuario interactúe de
forma ordenada en la operación de ingreso de datos.
Se provee un archivo Script para poder generar una serie de cambios en el sistema
- Uso de Usuarios, Roles, permisos a funcionalidad, y auditoria.
Utilización del ORM
Todas las clases implementan la interface IAccessDB para implementar el acceso a la
base de datos.
Métodos:
- FindAll: Obtiene listado de instancias de un tipo de
clase
- FindbyKey: Obtiene una instancia por la clave
- SaveObj: Ingresa o actualiza información de una
instancia.
La clase ORMDB es la clase genérica que implementa los métodos antes
mencionados, se vale de la metadata de las clases y obtiene desde las
propiedades el mapeo a la tabla y columnas, que están en la base
Postgres.
Implementación Opcional
- Importes de Actividades
- Tipos de Actividades
- Horarios
Los Listados a implementar deben poder exportarse a archivo, habilitar
varios tipos de ordenamientos 2 minimo
