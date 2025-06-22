# OneHealth

Como resultado del creciente aumento de los trastornos de ansiedad, en especial entre los jóvenes, se ha desarrollado una aplicación multiplataforma dentro de la iniciativa One Health, mediante la cual se buscará fomentar el estudio y la mejora de la salud de las personas. Para ello, la aplicación será capaz de de recopilar, procesar y analizar grandes volúmenes de datos del usuario, con el fin de poder predecir y prevenir crisis de ansiedad, gracias a la recopilación de diferentes tipologías y fuentes de datos: 
* Métricas biométricas (obtenidas mediante wearables que porta el usuario como 
pulseras, relojes o anillos inteligentes). 
* Registros del comportamiento digital (extraídos de las estadísticas internas de 
comportamiento e iteración del usuario con su teléfono móvil). 
* Estados anímicos (registrados mediante formularios dentro de la aplicación 
construida).

Toda esta información será almacenada en una base de datos propia para su posterior postprocesado, con la que se entrenarán diferentes modelos de predicción, usados 
posteriormente para acometer predicciones precisas sobre la posibilidad que tiene cada usuario de padecer un ataque de ansiedad, la cual será notificada en caso de ser elevada, con 
el objetivo de garantizar una intervención temprana que promueva el autocuidado emocional y contribuya al bienestar individual de la persona. 

Adicionalmente, se ha desarrollado una página web que facilita la descarga de la aplicación, así como un un dashboard de visualización y análisis de los datos recopilados, conformado en su conjunto una herramienta muy útil tanto para los propios usuarios como para investigadores y profesionales del ámbito de la salud mental, al ofrecer la posibilidad de visualizar y analizar en 
tiempo real las correlaciones entre los datos recogidos y su impacto en la aparición de crisis de ansiedad.

![image](https://github.com/user-attachments/assets/cac56041-2ebc-44d1-925c-4fbd76c5ed02)

## Subsistemas

### Aplicación de recogida y visualización de datos
Para poder recopilar y procesar los datos del usuario con el objetivo de detectar posibles crisis de ansiedad, se ha desarrollado una aplicación que, además, muestra recomendaciones y predicciones personalizadas. Estas pueden ser consultadas por el propio usuario, facilitando así una intervención temprana y un seguimiento continuo de su bienestar emocional.

![ededededed](https://github.com/user-attachments/assets/9e6dad02-796e-4317-9732-169edd9fb6e3)

#### Fuentes de recogida de datos de la aplicación:
Para la recolección de datos se utilizan tanto los formularios internos de la aplicación, destinados a recopilar información emocional del usuario, como herramientas nativas a través de la API de Capacitor para obtener datos sobre el comportamiento de uso del dispositivo, como el número de desbloqueos o las aplicaciones más utilizadas. Además, la integración con la API de Fitbit permite acceder directamente a datos relacionados con la actividad física y la salud del usuario. Todo esto garantiza una recolección de datos amplia y variada, ideal para su posterior análisis y predicción en el estudio.

![image](https://github.com/user-attachments/assets/878310f8-74b2-4556-9739-04a285fd1496)

#### Demo en dispositivo real:
https://github.com/user-attachments/assets/7143ac5b-6267-4d52-b078-5dd942ecbf37

### Web de descarga
La aplicación desarrollada para el estudio está disponible para descargarse en el siguiente enlace: https://onehealth-dowload.vercel.app/. El enlace contiene una página web creada específicamente para la instalación de la aplicación del estudio OneHealth, tanto en dispositivos iOS como Android. esde esta plataforma también se le asignará a cada participante un identificador único, necesario posteriormente para completar el registro en la aplicación y que permitirá identificar de forma individual a cada sujeto dentro del estudio. 

![Captura de pantalla 202d5-05-26 235141](https://github.com/user-attachments/assets/56d03e46-c6f0-4df6-a2f5-3ed763a9d0fa)

### Servidor
Para alojar y coordinar tanto la distribución de la aplicación móvil como la ejecución del script 
de procesamiento de datos, se ha configurado un servidor local sobre una Raspberry Pi 5 con 
8GB de RAM y 64GB de almacenamiento SD. 

![Captura de pantalla 2025-05-26 235141](https://github.com/user-attachments/assets/e57517a5-2457-4177-9d25-9a616cb6e088)


### Base de datos
Todos los datos recopilados, tanto los introducidos manualmente por los usuarios a través de los formularios como los obtenidos automáticamente desde el dispositivo móvil del usuario 
mediante la API de Capacitor o aquellos extraídos de los dispositivos wearables Fitbit, se almacenan de forma centralizada en Cloud Firestore, la base de datos de Firebase y del ecosistema desarrollado. 
![image](https://github.com/user-attachments/assets/8265de80-6820-4a36-9bc3-efbd02d4b304)

### Dashboard de visualización
Todos el flujo de datos de la aplicación, compuesto por los datos recopilados y las predicciones generadas, se pueden visualizar de forma conjunta desde un panel de control actualizado en tiempo real, desde el que se puede gestionar y supervisar el ecosistema desarrollado en su totalidad. Este dashboard permite consultar en tiempo real el número de usuarios registrados, número de usuarios activos, la cantidad total de datos recopilados y la distribución de estos datos a través de diferentes gráficas. Esta visualización no solo facilita la monitorización del estado general del estudio, sino que también resulta clave para detectar posibles errores en los subsistemas y analizar tendencias y correlaciones entre los datos que permitan formular nuevas hipótesis científicas. Además, se ofrece la posibilidad de exportar los datos en formato Excel.

![OneHealthDashware-05-18-2025_06_17_PM](https://github.com/user-attachments/assets/c9db221d-d69a-4217-8eed-40d055fe133b)

### Sitema de notificaciones
Una vez que el script de predicción ha sido ejecutado y las predicciones han sido generadas, se filtran aquellas cuyo valor supera el 6 dentro de una escala del 0 al 10 unidades de posibilidad de tener un ataque de ansiedad. Estas serán las que mediante el sistema de notificaciones del ecosistema desencadenarán notificaciones push al usuario mediante OneSignal, con el bjetivo de garantizar de esta forma una respuesta rápida y preventiva ante situaciones de alta posibilidad de padecer crisis inminentes de ansiedad. 

![Captura de ddpantalla 2025-05-21 105831](https://github.com/user-attachments/assets/98646c48-fbeb-4274-951e-605d5fb2723f)
