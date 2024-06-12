# Ejercicio CiberKillChain - Defensa

## Alumno

Yunes, Juan Ignacio

## Enunciado

Desarrollar la defensa en función del ataque planteado en orden inverso. No es una respuesta a un incidente, hay que detectar el ataque independientemente de la etapa.

Para cada etapa elegir una sola defensa, la más importante, considerar recursos limitados.

## Resolución
 
 * Acciones sobre los Objetivos (Actions on Objectives)

  * Que las credenciales estén hasheadas en la base de datos. De esa manera, aunque llegue hasta donde se alojan las mismas, no podrán ser utilizadas.

* Comando y Control (Command and Control)

  * Network Traffic Flow (DS0029): Supervisar el tráfico web. Proceder a bloquear usuario detectado como malisioso.

* Instalación (Installation)

  * Limitar el acceso a recursos a través de la red (M1035): evitar que cualquiera pueda acceder a la instancia donde se gestionan los usuarios.
  * Autenticación de 2 factores (M1032): se busca que para realizar cambios en configuraciones sensibles sea necesario tener algo más que las ceredenciales de usuario.

* Explotación (Exploitation)

  * Autenticación multifactorial (M1032): implementar autenticación multifactor para evitar que el atacante pueda acceder a las plataformas simplemente con el de usuario y contraseña.
  * Que sea necesario estar conectado a una VPN para acceder al sistema de la empresa.

* Entrega (Delivery)
    
  * Entrenamiento de integrantes de la empresa (M1017): capacitar a los usuarios para que identifiquen técnicas de ingeniería social, haciendo foco en correos electrónicos de phishing.
 
 * Armamento (Weaponization)

  * DS0037: utilizar servicios que puedan ayudar en el seguimiento de los certificados en uso en sitios de Internet. En algunos casos, es posible aprovechar piezas conocidas de información de certificados para descubrir otra infraestructura adversaria.

* Reconocimiento (Reconnaissance)

  * Internet scan (DS0035): para saber que están tratando de reconocer como es la infraestructura. Esta técnica sólo sirve para saber que es probable que seamos el objetivo de un ataque. Se pueden dar falsos positivos.
