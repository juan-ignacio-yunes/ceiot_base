# Ejercicio CiberKillChain - Defensa

## Alumno

Yunes, Juan Ignacio

## Enunciado

Desarrollar la defensa en función del ataque planteado en orden inverso. No es una respuesta a un incidente, hay que detectar el ataque independientemente de la etapa.

Para cada etapa elegir una sola defensa, la más importante, considerar recursos limitados.

## Resolución

* Reconocimiento (Reconnaissance)

  * internet scan (DS0035): para saber que están tratando de reconocer como es la infraestructura. Esta técnica sólo sirve para saber que es probable que seamos el objetivo de un ataque. Se pueden dar falsos positivos.
 
* Armamento (Weaponization)

  * DS0037: utilizar servicios que puedan ayudar en el seguimiento de los certificados en uso en sitios de Internet. En algunos casos, es posible aprovechar piezas conocidas de información de certificados para descubrir otra infraestructura adversaria.

* Entrega (Delivery)

  * Uso de de softwares (M1054): utilizar mecanismos de autenticación de correo electrónico y antisuplantación de identidad (anti-spoofing) para filtrar mensajes según comprobaciones de validez del dominio del remitente (usando SPF) y la integridad de los mensajes (usando DKIM).
    
  * Entrenamiento de integrantes de la empresa (M1017): capacitar a los usuarios para que identifiquen técnicas de ingeniería social y envíen correos electrónicos de phishing.

* Explotación (Exploitation)

  * Detectar y evitar intermediarios en la autenticación de un usuario para evitar que las credenciales vengan de una página web ajena al dominio propio. En este caso también se quitarán todos los permisos al usuario vulnerado.

* Instalación (Installation)

  * Autenticación de 2 factores (M1032): se busca que para realizar cambios en configuraciones sensibles sea necesario tener algo más que las ceredenciales de usuario.

* Comando y Control (Command and Control)

  * Network Traffic Flow (DS0029): Supervisar el tráfico web 

* Acciones sobre los Objetivos (Actions on Objectives)

  * 
