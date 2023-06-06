## Tema 3: Develop event-based solutions

Preguntas:

1. ¿Qué son las soluciones basadas en eventos y cómo se diferencian de las arquitecturas
   tradicionales basadas en solicitudes y respuestas?

Son un enfoque arquitectónico en el cual los componentes del sistema interactúan y se comunican a través del intercambio de eventos. En este contexto, un evento representa un suceso significativo o una notificación de algo que ha ocurrido en el sistema.

A diferencia de las arquitecturas tradicionales basadas en solicitudes y respuestas, en las soluciones basadas en eventos:

- **Comunicación asíncrona**: En lugar de utilizar comunicación síncrona, donde una solicitud se envía y se espera una respuesta inmediata, las soluciones basadas en eventos permiten la comunicación asíncrona. Los componentes emiten eventos y no esperan respuestas inmediatas, lo que permite una mayor escalabilidad y flexibilidad.

- **Desacoplamiento**: Los componentes en una arquitectura basada en eventos están desacoplados entre sí. Un componente emite un evento y no necesita conocer ni depender de los otros componentes que puedan recibirlo. Esto permite una mayor modularidad y facilita la evolución independiente de los componentes.

- **Escalabilidad y flexibilidad**: Al utilizar eventos, es posible escalar y adaptar los componentes de manera más flexible. Los eventos se pueden procesar y enrutar según las necesidades, lo que facilita la distribución de la carga de trabajo y la implementación de cambios o mejoras sin afectar a otros componentes.

- **Reactividad**: Las soluciones basadas en eventos son altamente reactivas, ya que los componentes pueden responder a los eventos en tiempo real. Esto es especialmente útil en aplicaciones en las que la actualización rápida y la toma de decisiones en tiempo real son fundamentales.

- **Modelado de flujos de trabajo**: Los eventos pueden utilizarse para modelar y orquestar flujos de trabajo complejos. Cada evento puede desencadenar una serie de acciones y decisiones, permitiendo la automatización de procesos y la coordinación entre diferentes componentes.



2. ¿Cuál es el papel de Azure Event Grid en la implementación de soluciones basadas en
   eventos y cómo se integra con otros servicios de Azure?

Desempeña un papel clave en la implementación de soluciones basadas en eventos al proporcionar un servicio de enrutamiento y entrega confiable de eventos en la nube. Actúa como un bus de eventos que permite la comunicación entre los distintos componentes de una arquitectura basada en eventos.

Algunas de las formas en que Azure Event Grid se integra con otros servicios de Azure son:

- **Integración con servicios de origen**: Azure Event Grid puede recibir eventos de una amplia gama de servicios de origen, como Azure Storage, Azure Blob Storage, Azure Functions, Azure IoT Hub y más. Esto permite capturar eventos de estos servicios y enrutarlos a los suscriptores adecuados.

- **Enrutamiento de eventos**: Event Grid proporciona reglas de enrutamiento flexibles que permiten definir qué eventos deben ser enviados a qué suscriptores. Puedes filtrar eventos según su tipo, origen, datos o cualquier otro atributo, lo que permite una entrega selectiva y eficiente de eventos a los interesados.

- **Integración con servicios de destino**: Event Grid también puede entregar eventos a diversos servicios de destino en Azure, como Azure Functions, Azure Logic Apps, Azure Event Hubs y más. Esto permite que los eventos desencadenen acciones y flujos de trabajo en respuesta a su llegada.

- **Escalabilidad y disponibilidad**: Azure Event Grid es altamente escalable y admite eventos a gran escala, lo que garantiza que los eventos sean entregados de manera confiable y eficiente. También ofrece una alta disponibilidad con replicación automática y manejo de fallas.

- **Personalización y extensibilidad**: Puedes crear endpoints personalizados para recibir eventos de Event Grid y personalizar el procesamiento de los mismos según tus necesidades. Además, Event Grid también permite la creación de eventos personalizados para escenarios específicos.

  

3. ¿Cuáles son los beneficios y casos de uso comunes de Azure Event Hub en el procesamiento y análisis de flujos masivos de eventos en tiempo real?

Beneficios de Azure Event Hub:

- **Escalabilidad**: Azure Event Hub permite manejar flujos masivos de eventos con facilidad, ya que puede manejar millones de eventos por segundo. Esto garantiza que no se pierdan eventos y que se puedan procesar a alta velocidad.

- **Rendimiento y baja latencia**: Event Hub ofrece un alto rendimiento y baja latencia, lo que significa que los eventos se entregan rápidamente y pueden ser procesados en tiempo real. Esto es crucial para aplicaciones que requieren respuestas inmediatas.

- **Almacenamiento duradero**: Event Hub almacena eventos durante un período configurable, lo que permite reprocesar y analizar eventos históricos. Esto es útil para análisis retrospectivos y para alimentar sistemas de análisis a largo plazo.

- **Integración con servicios de Azure**: Event Hub se integra fácilmente con otros servicios de Azure, como Azure Stream Analytics, Azure Databricks y Azure Functions. Esto permite construir soluciones de procesamiento y análisis de eventos completas en el ecosistema de Azure.

Casos de uso comunes:

- **IoT (Internet de las cosas)**: Event Hub es ampliamente utilizado en escenarios de IoT para recibir y procesar flujos de eventos generados por dispositivos conectados. Puede manejar grandes volúmenes de datos de sensores y permitir acciones en tiempo real basadas en eventos.

- **Registro de telemetría**: Event Hub es eficaz para capturar y procesar eventos de registro y telemetría generados por aplicaciones, servicios y sistemas distribuidos. Estos eventos se pueden analizar para monitoreo, detección de anomalías y solución de problemas.

- **Procesamiento de datos en tiempo real**: Event Hub se utiliza en arquitecturas de procesamiento en tiempo real, donde los eventos se capturan y se procesan en tiempo real para detectar patrones, generar alertas o alimentar sistemas de análisis en tiempo real.

- **Análisis de datos y big data**: Event Hub se integra con servicios de análisis como Azure Stream Analytics o Azure Databricks, lo que permite procesar y analizar eventos en tiempo real o realizar análisis retrospectivos en grandes volúmenes de datos.



Preguntas Batería de Preguntas: 

1. **Question 2 Page 64**: You need to store the user agreements. Where should you store the agreement after it is completed?

   <u>Answer</u>: B. Azure Event Hub

   <u>Explanation</u>: Azure Event Hub is used for telemetry and distributed data streaming.
   This service provides a single solution that enables rapid data retrieval for real-time processing as well as
   repeated replay of stored raw data. It can capture the streaming data into a file for processing and analysis.
   It has the following characteristics:
   low latency
   capable of receiving and processing millions of events per second
   at least once delivery

   

2. **Question 15 Page 104**: You are developing an Azure solution to collect point-of-sale (POS) device data from 2,000 stores located
   throughout the world. A single device can produce 2 megabytes (MB) of data every 24 hours. Each store
   location has one to five devices that send data.
   You must store the device data in Azure Blob storage. Device data must be correlated based on a device
   identifier. Additional stores are expected to open in the future.
   You need to implement a solution to receive the device data.
   Solution: Provision an Azure Event Grid. Configure the machine identifier as the partition key and enable
   capture.
   Does the solution meet the goal?

   <u>Answer</u>: A. Yes

   <u>Explanation</u>: 



3. **Question 6 Page 133**: You need to configure Azure Service Bus to Event Grid integration.
   Which Azure Service Bus settings should you use? To answer, select the appropriate options in the answer
   area.
   NOTE: Each correct selection is worth one point.

   <u>Answer</u>: Premium ; Contributor

   <u>Explanation</u>: Box 1: Premium
   Service Bus can now emit events to Event Grid when there are messages in a queue or a subscription
   when no receivers are present. You can create Event Grid subscriptions to your Service Bus namespaces,
   listen to these events, and then react to the events by starting a receiver. With this feature, you can use
   Service Bus in reactive programming models.
   A6319EC1AC83D57E5BA185C098116365
   To enable the feature, you need the following items:
   A Service Bus Premium namespace with at least one Service Bus queue or a Service Bus topic with at
   least one subscription.
   Contributor access to the Service Bus namespace.
   Box 2: Contributor