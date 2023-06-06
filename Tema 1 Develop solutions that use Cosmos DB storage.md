## Tema 1: Develop solutions that use Cosmos DB storage

Preguntas:

1. ¿Qué es Azure Cosmos DB y qué ventajas ofrece como servicio de base de datos?

Es un servicio de base de datos distribuida y multimodelo desarrollado por Microsoft.

Ventajas:

- **Escalabilidad global**: Azure Cosmos DB permite escalar horizontalmente de manera transparente y sin interrupciones a nivel mundial. Esto significa que puedes escalar tu base de datos para manejar cargas de trabajo de cualquier tamaño y distribuirla en varias regiones geográficas para ofrecer un acceso rápido a los datos a nivel global.
- **Múltiples modelos de datos**: Azure Cosmos DB admite múltiples modelos de datos, incluyendo documentos, grafos, clave-valor y columnas amplias. Esto permite a los desarrolladores utilizar el modelo de datos más adecuado para su aplicación sin la necesidad de utilizar diferentes servicios de bases de datos.
- **Baja latencia**: Azure Cosmos DB está diseñado para ofrecer una baja latencia en la lectura y escritura de datos, lo que lo hace adecuado para aplicaciones que requieren respuestas rápidas. Utiliza técnicas de replicación y distribución de datos para garantizar que los datos estén disponibles lo más cerca posible de los usuarios finales.
- **Alta disponibilidad**: Azure Cosmos DB ofrece una alta disponibilidad al replicar automáticamente los datos en varias regiones geográficas. Esto asegura que tus datos estén protegidos contra fallas de hardware o desastres naturales, y que tus aplicaciones continúen funcionando sin interrupciones.
- **Consistencia flexible**: Azure Cosmos DB ofrece diferentes niveles de consistencia para adaptarse a las necesidades de tu aplicación. Puedes elegir entre modelos de consistencia fuerte, eventual o consistencia coherente basada en sesiones, lo que te permite equilibrar el rendimiento y la coherencia de tus datos.
- **Integración con servicios de Azure**: Azure Cosmos DB se integra estrechamente con otros servicios de Azure, lo que facilita la construcción de aplicaciones completas en la nube. Puedes combinar Azure Cosmos DB con servicios como Azure Functions, Azure Logic Apps y Azure Machine Learning para crear soluciones más potentes.

2. ¿Cuáles son los modelos de datos compatibles con Azure Cosmos DB?

- Documentos: Permite almacenar y consultar datos en formato JSON, lo que facilita la creación de aplicaciones flexibles y escalables.
- Grafos: Proporciona un modelo de datos basado en nodos y relaciones, permitiendo consultas complejas y análisis de redes.
- Clave-valor: Permite almacenar y recuperar datos simples a través de una clave única, lo que resulta útil para aplicaciones con requisitos de almacenamiento y recuperación rápidos.
- Columnas amplias: Permite trabajar con grandes volúmenes de datos estructurados y no estructurados, ofreciendo consultas rápidas y eficientes en tablas grandes.

3. ¿Cómo se accede y se realiza consultas a una base de datos de Cosmos DB en Azure?

Después de crear la cuenta de CosmosDB:

- Obtención de la cadena de conexión
- Elección de la API y biblioteca de cliente: Basado en el modelo de API seleccionado al crear la cuenta de Cosmos DB, deberás elegir la biblioteca de cliente adecuada para interactuar con la base de datos. Por ejemplo, si estás utilizando la API SQL, puedes utilizar la biblioteca de cliente de Azure Cosmos DB para .NET, Java, Python, entre otros.
- Conexión a la base de datos: Utilizando la cadena de conexión y la biblioteca de cliente seleccionada, debes establecer una conexión desde tu aplicación a la base de datos de Cosmos DB. Esto implica proporcionar los detalles de autenticación y conexión, como el nombre de la cuenta y la clave de acceso.
- Realización de consultas: Una vez conectado a la base de datos, puedes realizar consultas utilizando el lenguaje de consulta correspondiente a la API que estás utilizando. Por ejemplo, si estás utilizando la API SQL, puedes utilizar consultas SQL para recuperar, filtrar y modificar los datos almacenados en Cosmos DB.



Preguntas Batería de Preguntas:

1. **Question 13 Page 153**: You are developing a Java application that uses Cassandra to store key and value data. You plan to use a
   new Azure Cosmos DB resource and the Cassandra API in the application. You create an Azure Active
   Directory (Azure AD) group named Cosmos DB Creators to enable provisioning of Azure Cosmos
   accounts, databases, and containers.
   The Azure AD group must not be able to access the keys that are required to access the data.
   You need to restrict access to the Azure AD group.
   Which role-based access control should you use?

<u>Answer</u>: C. Cosmos DB Operator

<u>Explanation</u>: Azure Cosmos DB now provides a new RBAC role, Cosmos DB Operator. This new role lets you provision Azure Cosmos accounts, databases, and containers, but can’t access the keys that are required to access the data. This role is intended for use in scenarios where the ability to grant access to Azure Active Directory service principals to manage deployment operations for Cosmos DB is needed, including the account, database, and containers.



2. **Question 23 Page 162**: You are developing a medical records document management website. The website is used to storescanned copies of patient intake forms.
   If the stored intake forms are downloaded from storage by a third party, the contents of the forms must notbe compromised.
   You need to store the intake forms according to the requirements.
   Solution:

   1. Create an Azure Cosmos DB database with Storage Service Encryption enabled.
   2. Store the intake forms in the Azure Cosmos DB database.
     Does the solution meet the goal?

   <u>Answer</u>: B. No

   <u>Explanation</u>: Instead use an Azure Key vault and public key encryption. Store the encrypted from in Azure Storage Blobstorage.

   

3. **Question 27 Page 52**: You are developing a solution for a hospital to support the following use cases:
   The most recent patient status details must be retrieved even if multiple users in different locations have updated the patient record.
   Patient health monitoring data retrieved must be the current version or the prior version.
   After a patient is discharged and all charges have been assessed, the patient billing record contains the final charges.
   You provision a Cosmos DB NoSQL database and set the default consistency level for the database account to Strong. You set the value for Indexing Mode to Consistent.
   You need to minimize latency and any impact to the availability of the solution. You must override the default consistency level at the query level to meet the required consistency guarantees for the scenarios.
   Which consistency levels should you implement? To answer, drag the appropriate consistency levels to the correct requirements. Each consistency level may be used once, more than once, or not at all. You may need to drag the split bar between panes or scroll to view content.
   NOTE: Each correct selection is worth one point.

   <u>Answer</u>: Strong ; Bounded Staleness ; Eventual

   <u>Explanation</u>: Box 1: Strong
   Strong: Strong consistency offers a linearizability guarantee. The reads are guaranteed to return the most recent committed version of an item. A client never sees an uncommitted or partial write. Users are always guaranteed to read the latest committed write.
   Box 2: Bounded staleness
   Bounded staleness: The reads are guaranteed to honor the consistent-prefix guarantee. The reads might lag behind writes by at most "K" versions (that is "updates") of an item or by "t" time interval. When you choose bounded staleness, the "staleness" can be configured in two ways:
   The number of versions (K) of the item The time interval (t) by which the reads might lag behind the writes
   Box 3: Eventual
   Eventual: There's no ordering guarantee for reads. In the absence of any further writes, the replicas eventually converge.
   Incorrect Answers:
   Consistent prefix: Updates that are returned contain some prefix of all the updates, with no gaps.
   Consistent prefix guarantees that reads never see out-of-order writes.