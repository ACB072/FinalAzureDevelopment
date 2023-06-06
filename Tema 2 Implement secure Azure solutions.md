# Tema 2: Implement secure Azure solutions
## Preguntas:

- ¿Qué es Azure Key Vault y cómo se utiliza para proteger secretos y claves criptográficas?

		Es un servicio en la nube para el almacenamiento de los secretos y el acceso a estos de forma segura. Un secreto es todo aquello cuyo acceso desea controlar de forma estricta, como las claves API, las contraseñas, los certificados o las claves criptográficas. 
		
		Azure Key Vault aplica el protocolo Seguridad de la capa de transporte (TLS) para proteger los datos cuando viajan entre Azure Key Vault y los clientes. Los clientes negocian una conexión TLS con Azure Key Vault. TLS proporciona una autenticación sólida, privacidad de mensajes e integridad (lo que permite la detección de la manipulación, interceptación y falsificación de mensajes), interoperabilidad, flexibilidad de algoritmo, y facilidad de implementación y uso.
	
- ¿Cuál es el papel de las Identidades Administradas (Managed Identities) en la seguridad
de Azure?

		Cuando implementa una aplicación en una máquina virtual en Azure, puede asignar una identidad a la máquina virtual que tiene acceso a Key Vault. También puede asignar identidades a otros recursos de Azure . La ventaja de este enfoque es que la aplicación o el servicio no administran la rotación del primer secreto. Azure alterna automáticamente la identidad. 

- ¿Cómo se configuran y se utilizan Azure Key Vault y las Identidades Administradas?

        Cualquiera con una suscripción a Azure puede crear y usar instancias de Key Vault. Aunque Key Vault beneficia a los desarrolladores y los administradores de seguridad, el administrador de una organización que administra otros servicios de Azure puede implementarlo y administrarlo. Por ejemplo, este administrador puede iniciar sesión con una suscripción de Azure, crear un almacén para la organización en el que almacenar las claves y, después, asumir la responsabilidad de las tareas operativas, como:
        
        - Crear o importar una clave o un secreto
        - Revocar o eliminar una clave o un secreto
        - Autorizar usuarios o aplicaciones para acceder al almacén de claves para que puedan administrar o usar sus claves y secretos
        - Configurar el uso de claves (por ejemplo, para firmar o cifrar)
        - Supervisar el uso de claves
        
        A continuación, este administrador proporciona a los desarrolladores los URI para llamar desde sus aplicaciones. Este administrador también ofrece información de registro del uso de claves al administrador de seguridad.

  

## Preguntas de la Bateria:

### QUESTION 1 - Pagina 127
HOTSPOT
You need to retrieve the database connection string.
Which values should you use? To answer, select the appropriate options in the answer area.
NOTE: Each correct selection is worth one point.

![image](\imagenes\Tema1_Pregunta2.JPG)

    La conexion de la base de datos de azure recupera el REST API vault.azure.net/secrets/
    
    Box 1: cpandlkeyvault
    Especificamos el keyvault, cpandlkeyvault.
    
    Box 2: PostgreSQLConn
    Especificamos el secreto, PostgreSQLConn
    
    La cadena de conexión de la base de datos se almacena en Azure Key Vault con los siguientes atributos:
    - Azure Key Vault name: cpandlkeyvault
    - Secret name: PostgreSQLConn
    - Id: 80df3e46ffcd4f1cb187f79905e9a1e8
    
    Box 3:Querystring
    Especificamos el tipo de variable para acceder a los valores secretos del Key Vault



### QUESTION 1 - Pagina 139

HOTSPOT
You need to add code at line PC26 of Processing.cs to ensure that security policies are met.
How should you complete the code that you will add at line PC26? To answer, select the appropriate
options in the answer area.
NOTE: Each correct selection is worth one point.

![image](\imagenes\Tema1_Pregunta1.JPG)

La respuesta seria:

    Box 1: var key = await Resolver.ResolveKeyAsyn(keyBundle,KeyIdentifier.CancellationToken.None);
    Añadimos el identificador de la key
    
    Box 2: var x = new BlobEncryptionPolicy(key,resolver);
    Configuramos la encriptacion del blob
    
    Box 3: cloudblobClient. DefaultRequestOptions.EncryptionPolicy = x;
    Configuramos la politica de encriptación

### QUESTION 23
Note: This question is part of a series of questions that present the same scenario. Each question
in the series contains a unique solution that might meet the stated goals. Some question sets might
have more than one correct solution, while others might not have a correct solution.
After you answer a question in this section, you will NOT be able to return to it. As a result, these
questions will not appear in the review screen.
You are developing a medical records document management website. The website is used to store
scanned copies of patient intake forms.
If the stored intake forms are downloaded from storage by a third party, the contents of the forms must not
be compromised.
You need to store the intake forms according to the requirements.
Solution:
1. Create an Azure Cosmos DB database with Storage Service Encryption enabled.
2. Store the intake forms in the Azure Cosmos DB database.
   Does the solution meet the goal?
   A. Yes
   B. No

		La respuesta seria No, ya que seria mas conveniente crear un keyVault de Azure y una llave publica de encriptación, y dicha llave almacenarla en un Azure Storage Blob Storage