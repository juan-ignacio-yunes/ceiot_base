# Ejercicio CiberKillChain - Ataque


## Enunciado

Armar una cyberkillchain usando técnicas de la matriz de Att&ck para un escenario relacionado al trabajo práctico de la carrera.


## Alumno
  Yunes, Juan Ignacio
  
## Sistema Víctima
  El proyecto se llama "Estación inteligente para el cuidado y monitoreo remoto de mascotas". En una primera instacnia consta de un comedero automático que además incorpora la capacidad de pesar al animal para hacer un seguimiento de este. Mientras que el hardware incorporará productos que ya están disponibles en el mercado, se desarrollará software para gestionar el equipo. Entre otras cosas, este gestionará los permisos de usuarios, registros de diferentes valores (peso de los animales, tamaño de las porciones de alimento a dispoensar, etc.), autorizaciones a terceras personas, entre otras. Se puede leer más sobre el proyecto [aquí](https://github.com/juan-ignacio-yunes/Plantilla-planificacion/blob/master/charter.pdf).
  
## Objetivo:
  Obtener las credenciales de los usuarios para ver si es posible utilizarlas en otras plataformas como bancos, email, etc. Se buscará que la empresa no detecte el ataque, con el fin de poder explotar la vulnerabilidad durante el mayor tiempo posible.

## Resolución

* Reconocimiento (Reconnaissance)

** Identificación de empleados en LinkedIn:

T1592.001 (Recopilación de información sobre el entorno de la red) y T1589.002 (Recopilación de correos electrónicos)
Buscar empleados de la empresa desarrolladora del comedero automático en LinkedIn y otras redes profesionales.
Recopilar información pública sobre estos empleados, incluyendo nombres, cargos, y correos electrónicos.
Analizar las conexiones y publicaciones de los empleados para obtener más detalles sobre su rol y acceso a la aplicación.

** Diseño de correos electrónicos de phishing personalizados:

T1589.001 (Phishing)
Utilizar la información recopilada para personalizar correos electrónicos de phishing, haciéndolos parecer mensajes internos de la empresa o comunicaciones oficiales de la aplicación del comedero automático.
Incluir detalles específicos (nombres de compañeros, proyectos en los que trabajan) para aumentar la credibilidad del correo.

* Armamento (Weaponization)

** Crear un sitio web de phishing:

T1204.002 (Phishing mediante enlaces maliciosos)
Diseñar un sitio web que imite la interfaz de inicio de sesión de la aplicación del comedero automático.
Incluir todos los elementos visuales y de navegación que se encuentran en el sitio legítimo, como logos, esquemas de color, y mensajes de bienvenida.

** Alojar el sitio de phishing en un servidor seguro:

T1027 (Ofuscación de archivos ejecutables y scripts)
Utilizar servicios de alojamiento que permitan el uso de HTTPS para dar una apariencia de seguridad.
Implementar medidas para ofuscar el código del sitio de phishing y evitar su detección por herramientas de seguridad.

* Entrega (Delivery)

** Enviar correos electrónicos de phishing:

T1566.001 (Phishing a través de correos electrónicos)
Enviar los correos electrónicos personalizados a los empleados y a usuarios de la aplicación fingiendo una promoción especial o que vean una actualización de alguna característica del frontend de la aplicación. Incluir un enlace al sitio de phishing, disfrazado como un enlace a la página de inicio de sesión oficial.

** Utilizar redes sociales para ampliar el alcance:

Compartir enlaces maliciosos en plataformas de redes sociales, mediante mensajes directos o publicaciones.

* Explotación (Exploitation)

** Interacción con el sitio de phishing:

T1203 (Explotación de vulnerabilidades en software)
Los usuarios que hacen clic en el enlace del correo de phishing son dirigidos al sitio web falso.
Se les pide que ingresen sus credenciales como verificación.


** Captura de credenciales:

Las credenciales ingresadas en el sitio de phishing se envían al servidor paralelo controlado por nosotros y no por la empresa.
El sitio de phishing puede redirigir a los usuarios a la página legítima después de la captura para reducir sospechas.

* Instalación (Installation)
Objetivo: Establecer persistencia en el sistema comprometido.

** Acceder a la aplicación con credenciales robadas:

T1078.001 (Uso de credenciales válidas para obtener acceso)
Utilizar las credenciales obtenidas para iniciar sesión en la aplicación del comedero automático.
Explorar las configuraciones y funcionalidades disponibles para la cuenta comprometida, especialmente para saber quienes son los contactos cercanos al usuario mendiante el nivel de acceso otorgado.
Detectar objetivos importantes, como ser veterinarios y paseadores, contando la cantidad de usuarios con los cuales tienen vínculos.


** Instalación de backdoors:

T1546.003 (Instalación de malware para persistencia)
Modificar configuraciones de la cuenta o de la aplicación para instalar scripts maliciosos que permitan el acceso continuo.
Crear accesos secundarios o usuarios con privilegios que puedan ser utilizados en caso de que la cuenta principal comprometida sea detectada y bloqueada.

* Comando y Control (Command and Control)

** Establecer un canal seguro de comunicación:

T1071.001 (Comunicación con C2 a través de HTTP/HTTPS)
Utilizar protocolos comunes y cifrados (HTTP/HTTPS) para comunicarse con el malware instalado en la aplicación.
Implementar técnicas de ofuscación y cifrado en la comunicación para evitar la detección.

** Enviar y recibir comandos:

Utilizar el canal de comunicación C2 para enviar comandos al sistema comprometido.
Monitorizar la actividad de la cuenta comprometida y realizar ajustes según sea necesario.

* Acciones sobre los Objetivos (Actions on Objectives)

** Exfiltración de credenciales:

T1530 (Robo de credenciales para uso en otros sistemas)
Descargar y almacenar las credenciales robadas en un servidor seguro controlado por el atacante.
Utilizar las credenciales para acceder a otros servicios y plataformas, como correos electrónicos y bancos.

** Mantener actividades de bajo perfil:

T1078.001 (Uso de credenciales válidas en otros servicios)
Minimizar las actividades visibles para evitar la detección.
Configurar alertas silenciosas que notifiquen al atacante sobre cualquier posible descubrimiento de la brecha sin alertar a los defensores.
Continuar explotando las credenciales robadas durante el mayor tiempo posible, realizando movimientos laterales para acceder a más información valiosa.
