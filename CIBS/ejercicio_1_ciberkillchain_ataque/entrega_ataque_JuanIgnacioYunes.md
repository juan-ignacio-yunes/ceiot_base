# Ejercicio CiberKillChain - Ataque


## Enunciado

Armar una cyberkillchain usando técnicas de la matriz de Att&ck para un escenario relacionado al trabajo práctico de la carrera.


## Alumno
  Yunes, Juan Ignacio
  
## Sistema víctima
  El proyecto se llama "Estación inteligente para el cuidado y monitoreo remoto de mascotas". En una primera instancia consta de un comedero automático que además incorpora la capacidad de pesar al animal para hacer un seguimiento de este. Mientras que el hardware incorporará productos que ya están disponibles en el mercado, se desarrollará software para gestionar el equipo. Entre otras cosas, este gestionará los permisos de usuarios, registros de diferentes valores (peso de los animales, tamaño de las porciones de alimento a dispoensar, etc.), autorizaciones a terceras personas, entre otras. Se puede leer más sobre el proyecto [aquí](https://github.com/juan-ignacio-yunes/Plantilla-planificacion/blob/master/charter.pdf).
  
## Objetivo:
  Obtener las credenciales de los usuarios para ver si es posible utilizarlas en otras plataformas de servicios bancarios, servicios de email, etc. Se buscará que la empresa no detecte el ataque, con el fin de poder explotar la vulnerabilidad durante el mayor tiempo posible.

## Resolución
Se opta por atacar a los adminisradores de la aplicación para acceder a la bae de datos y extraer de ahí la información necesaria.

* Reconocimiento (Reconnaissance)

  * Identificación de empleados en LinkedIn, T1592.001 (Recopilación de información sobre el entorno de la red) y T1589.002 (Recopilación de correos electrónicos):
    Buscar empleados de la empresa desarrolladora del comedero automático en LinkedIn y otras redes profesionales.
    Recopilar información pública sobre estos empleados, incluyendo nombres, cargos, y correos electrónicos.
    Analizar las conexiones y publicaciones de los empleados para obtener más detalles sobre su rol y acceso a la aplicación.

* Armamento (Weaponization)

    * Diseño de correos electrónicos de phishing personalizados (T1589.001 - Phishing):
    Utilizar la información recopilada para personalizar correos electrónicos de phishing, haciéndolos parecer mensajes internos de la empresa, comunicaciones oficiales de la empresa o comunicaciones oficiales de la aplicación del comedero automático. Incluir detalles específicos (nombres de compañeros, proyectos en los que trabajan) para aumentar la credibilidad del correo.

  * Montar y configurar infraestrucutra, en este caso se opta por servicio serverless (T1583.007 - Adquirir infraestructura serverless):
    Será la plataforma donde se alojarán los servicios necesarios para llevar el ataque, como ser la página web, base de datos para alojar la información robada, servicios de autenticación que simularán los de la empresa, etc. A priori se elige a AWS como proveedor.

  * Adquirir servicios web (T1583.006):
    Se configurarán los servicios antes mencionados en la plataforma serverless configurada.
  
  * Crear un sitio web de phishing (T1204.002 - Phishing mediante enlaces maliciosos):
    Diseñar un sitio web que imite la interfaz de inicio de sesión de alguna aplicación que usen en la empresa.
    Incluir todos los elementos visuales y de navegación que se encuentran en el sitio legítimo, como logos, esquemas de color y mensajes de bienvenida. En el código de este sitio se contemplará que luego de que el usuario acceda con sus credenciales, se lo redigirá automáticamente a la página oficial y se lo autenticará sin que este se de cuenta.

  * Desarrollar y/u obtener certificados de seguridad para el sitio web (T1587.003 - Desarrollar certificados digitales, T1588.004 - Comprar o robar certificados digitales):
    Se usarán para dar una apariencia de seguridad.  
    
  * Instalar certificados digitales (T1608.003):
    Para simular que el sitio está alojado en un servidor seguro y a dar una apariencia de seguridad mediante el uso de protocolo HTTPS.

  * Generar cuentas en redes sociales (T1585.001 - Establecer cuentas en redes sociales):
    Estas se usarán para contactarse con los empleados de la empresa y enviarles mensajes con enlaces maliciosos.

* Entrega (Delivery)

  * Enviar correos electrónicos de phishing (T1566.001 - Phishing a través de correos electrónicos):
    Enviar los correos electrónicos personalizados a los empleados fingiendo una comunicación oficial de la propia empresa con un enlace que lo redireccione al sitio de phishing, disfrazado como un enlace a la página de inicio de sesión oficial.

* Explotación (Exploitation)

  * Interacción con el sitio de phishing (T1203 - Explotación de vulnerabilidades en software)
    Los usuarios que hacen clic en el enlace del correo de phishing son dirigidos al sitio web falso.
    Se les pide que ingresen sus credenciales como verificación.
    Las credenciales ingresadas en el sitio de phishing se envían al servidor malisioso para ser almacenadas y luego, como se mencionó en la etapa de weaponization, se redirigirá a los usuarios a la página legítima  y los autenticará sin que lo noten, reduciendo así las sospechas.

* Instalación (Installation)
Objetivo: Establecer persistencia en el sistema comprometido.

  * Cración de cuentas (T1136.001/T1136.002 - Creación de cuenta local/de dominio):
    Como estrategia de persistencia, se crea una nueva cuenta de usuario con permisos de administrador dentro del sistema afectado, en caso de que se detecte que la cuenta comprometida ha sido vulnerada y se tomen acciones sobre ella.

* Comando y Control (Command and Control): 

  * Comunicación via protocolos web de lacapa de aplicación(T1071.001): la comunicación se hará usando protocolo HTTP/HTTPS usando la interfaz propia de la aplicación a la cuál se infiltró.
    
  * Acceder a la aplicación con credenciales robadas (T1078.003 - Uso de credenciales válidas correspondientes a "local accounts")
    Utilizar las credenciales válidas comprometidas para minimizar sospechas y evitar la detección.
    Explorar las configuraciones y funcionalidades disponibles para la cuenta comprometida.

  * Recopilación de datos:
    Reconocimiento de plataforma y recopilación de datos (T1530 - Acceder a la misma mediante los servicios habilitados por el proveedor de servicios Cloud).

* Acciones sobre los Objetivos (Actions on Objectives)  

  * Exfiltración de datos (T1567.002 - Exfiltración a servicio cloud utilizando servicio web):
    Descarga y almacenamiento de las credenciales robadas en un servicio cloud alojado en el mismo proveedor. El usar el mismo proveedor cloud disminuye las probabilidades de detección ya que se evita la creación de conexiones "al exterior".
  
  * Utilizar las credenciales obtenidas para acceder a otros servicios y plataformas, como correos electrónicos y bancos.

    