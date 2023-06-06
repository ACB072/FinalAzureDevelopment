# Tema 5: Implement API Management



### Preguntas:

- ¿Qué es Azure API Management y cuál es su propósito en el desarrollo de aplicaciones?

   

   La gestión de API proporciona funciones básicas para garantizar el éxito de un programa de API a través        de la participación de los desarrolladores, información empresarial, análisis, seguridad y protección.

   Cada API consta de una o más operaciones, y cada API puede agregarse a uno o más productos.

  

- ¿Cuáles son los beneficios de utilizar Azure API Management para gestionar APIs en una
  arquitectura de microservicios?

  

  Azure API Management ofrece varios beneficios al gestionar APIs en una arquitectura de microservicios. Algunos de los beneficios principales son:

   

  1. Simplificación de la complejidad de las APIs: Azure API Management actúa como una puerta de enlace (API gateway) que se coloca entre los microservicios y los consumidores de la API. Esto permite que los clientes interactúen con una única interfaz simplificada, en lugar de tener que comunicarse directamente con cada uno de los microservicios por separado.
  2. Seguridad mejorada: Azure API Management proporciona capacidades de seguridad avanzadas para proteger las APIs en una arquitectura de microservicios. Permite implementar políticas de seguridad como autenticación y autorización, control de acceso, limitación de velocidad (throttling), y protección contra ataques mediante Web Application Firewall (WAF).
  3. Escalabilidad y rendimiento: Con Azure API Management, cada microservicio puede escalar de forma independiente según sus necesidades, lo que permite una granularidad en la escalabilidad. Esto significa que los microservicios pueden aumentar o disminuir su capacidad de manera individual, lo que optimiza los recursos y reduce los costos generales. Además, el API gateway puede implementar estrategias de almacenamiento en caché y optimización del rendimiento para mejorar la eficiencia y la velocidad de respuesta de las APIs.
  4. Gestión del ciclo de vida de las APIs: Azure API Management ofrece capacidades completas de gestión del ciclo de vida de las APIs. Esto incluye la creación, documentación, versión, implementación y monitorización de las APIs.

   

   En resumen, Azure API Management simplifica la gestión de APIs en una arquitectura de microservicios al proporcionar un API gateway centralizado, seguridad avanzada, escalabilidad granular y herramientas de gestión del ciclo de vida de las APIs. Estos beneficios ayudan a mejorar la eficiencia, la seguridad y la experiencia de desarrollo al trabajar con microservicios y APIs.

  

- ¿Cómo se configura y se utiliza Azure API Management para controlar el acceso y la
  seguridad de las APIs?

  

  Para configurar y utilizar Azure API Management para controlar el acceso y la seguridad de las APIs, puedes seguir los siguientes pasos:

  1. Crear una instancia de Azure API Management: Comienza creando una instancia de Azure API Management en el portal de Azure. Esta instancia será el punto central para administrar y controlar tus APIs.
  2. Configurar la autenticación y autorización: Azure API Management proporciona un conjunto de características para admitir la autenticación y autorización de las APIs. Puedes usar Azure Active Directory (Azure AD) para autenticar a los usuarios y controlar su acceso a las APIs. Azure AD permite habilitar características como la autenticación multifactor (MFA) y el control de acceso basado en roles (RBAC) para proteger el acceso al servicio API Management y sus entidades, como las APIs y las directivas.
  3. Configurar el portal para desarrolladores: Azure API Management proporciona un portal para desarrolladores totalmente personalizable que puedes utilizar para permitir que los usuarios desarrolladores descubran y se conecten a las APIs publicadas a través de API Management. El portal para desarrolladores tiene opciones para facilitar el registro y el inicio de sesión de los usuarios de manera segura.
  4. Gestionar el acceso basado en roles: Azure API Management utiliza el control de acceso basado en roles (RBAC) de Azure para administrar los roles y permisos de los usuarios en el servicio. Puedes asignar roles integrados, como el "Colaborador de servicio de administración de API" y el "Rol de lector de servicios de API Management", para controlar el acceso a las APIs y las entidades de API Management. Estos roles pueden asignarse en diferentes ámbitos, como la suscripción, el grupo de recursos y la instancia específica de API Management.
  5. Aplicar las recomendaciones de seguridad: Para garantizar la seguridad de tus APIs, es recomendable seguir las mejores prácticas y las recomendaciones de seguridad proporcionadas por Microsoft. La línea de base de seguridad de Azure para API Management ofrece instrucciones basadas en el banco de pruebas de seguridad en la nube de Microsoft. Puedes utilizar Microsoft Defender for Cloud y Azure Policy para supervisar y aplicar estas recomendaciones de seguridad.

  

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



### Identificar y explicar (comprobar si es posible) de la batería de Preguntas 3 preguntas por cada integrante relacionadas con Azure API Management





**TESTLET 3 - CASE STUDY -  PAGINAS 129,130,131**

**QUESTION 3**

HOTSPOT
You need to configure API Management for authentication.
Which policy values should you use? To answer, select the appropriate options in the answer area.



![tema5-pregunta3](imagenes/tema5pregunta3.png)



**SOLUCION:**

![tema5-pregunta3-respuesta](imagenes/tema5pregunta3-respuesta.png)



**EXPLICACION:**

Box 1: Validate JWT

La política validate-jwt valida la existencia y validez de un JWT extraído de un encabezado HTTP especificado o un parámetro de consulta especificado. Esta política se utiliza en el contexto de la autenticación de usuarios y sigue los siguientes pasos:

1. El usuario selecciona "Iniciar sesión" en el sitio web.
2. El navegador redirige al usuario a la página de inicio de sesión de Azure Active Directory (Azure AD).
3. El usuario inicia sesión.
4. Azure AD redirige la sesión del usuario de vuelta a la aplicación web. La URL incluye un token de acceso.
5. La aplicación web llama a una API e incluye el token de acceso en el encabezado de autenticación. El ID de la aplicación se envía como la audiencia (reclamo 'aud') en el token de acceso.
6. La API de backend valida el token de acceso.

La política validate-jwt se encarga de verificar que el token de acceso sea válido y existe antes de que la aplicación pueda llamar a la API. Para ello, verifica la firma del token y otros detalles, como el reclamo de tiempo de expiración (exp). Dependiendo de la configuración, se puede requerir que el reclamo de tiempo de expiración esté presente en el token o no

Box 2: Outbound







-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------







**TESTLET 3 - CASE STUDY - PAGINA 131**

**QUESTION 4**

You need to authenticate the user to the corporate website as indicated by the architectural diagram.
Which two values should you use? Each correct answer presents part of the solution.

A. ID token signature
B. ID token claims
C. HTTP response code
D. Azure AD endpoint URI
E. Azure AD tenant ID



**SOLUCION:**

- A. ID token signature
- D. Azure AD endpoint URI





**EXPLICACION:**



A: Los reclamos en los tokens de acceso Los JWT (JSON Web Tokens) se dividen en tres partes:

- Encabezado - Proporciona información sobre cómo validar el token, incluyendo detalles sobre el tipo de token y cómo se firmó.
- Carga útil - Contiene todos los datos importantes sobre el usuario o la aplicación que intenta llamar al servicio.
- Firma - Es el material utilizado para validar el token.

D: Su cliente puede obtener un token de acceso desde el punto de conexión v1.0 o el punto de conexión v2.0 utilizando una variedad de protocolos.

Escenario: Autenticación de usuario. Los siguientes pasos detallan el proceso de autenticación del usuario:

1. El usuario selecciona "Iniciar sesión" en el sitio web.
2. El navegador redirige al usuario a la página de inicio de sesión de Azure Active Directory (Azure AD).
3. El usuario inicia sesión.
4. Azure AD redirige la sesión del usuario de vuelta a la aplicación web. La URL incluye un token de acceso.
5. La aplicación web llama a una API e incluye el token de acceso en el encabezado de autenticación. El ID de la aplicación se envía como el reclamo de audiencia ('aud') en el token de acceso.
6. La API de backend valida el token de acceso.

Durante este proceso, los tokens de acceso contienen reclamos que proporcionan información importante, como la audiencia a la que está dirigido el token. Estos reclamos se utilizan para validar y autorizar las solicitudes realizadas por la aplicación web a la API de backend.





-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------





**QUESTION SET 5 - PAGINA 148**

**QUESTION 8**

Your company is developing an Azure API.
You need to implement authentication for the Azure API. You have the following requirements:
All API calls must be secure.
Callers to the API must not send credentials to the API.
Which authentication mechanism should you use?
A. Basic
B. Anonymous
C. Managed identity
D. Client certificate



**SOLUCION:**

C. Managed Identity



**EXPLICACION:**



El uso de la política de autenticación con identidad administrada permite autenticarse con un servicio backend utilizando la identidad administrada del servicio de administración de API. Esta política utiliza la identidad administrada para obtener un token de acceso de Azure Active Directory que permite acceder al recurso especificado. Después de obtener exitosamente el token, la política establecerá el valor del token en el encabezado de autorización utilizando el esquema Bearer.

