Recomendado por David Heinemeier Hanson (DHH) en [The five programming books that meant most to me](https://signalvnoise.com/posts/3375-the-five-programming-books-that-meant-most-to-me)

> Great inventory of many of the patterns that underpin Rails itself, as well as descriptions of many of the “new” approaches that people advocate today (like [transaction scripts](http://martinfowler.com/eaaCatalog/transactionScript.html) and [service layers](http://martinfowler.com/eaaCatalog/serviceLayer.html)). You won’t necessarily implement most of these patterns yourself, but it’s an invaluable resource to understanding the differences in architectures and why framework work the way they do. (Funny anecdote: before I created Rails, [I redrew many of the diagrams](http://martinfowler.com/eaaCatalog/) in OmniGraffle for Martin Fowler because I liked the book so much.)


## Introduction
- Las enterprise application no son complicadas(ex. que no estan resolviendo problemas tipo: multihreading), solo que tienen mucha lógica de negocios que dependen entre sí. 
	- Ahí la importancia de una buena arquitectura que permita hacer cambios sin tanto costo.
	- Requieren que la data sea persistente.
		- A pesar de que hayan muchos cambios en el sistema, debe mantenerse igual.
	- Hay mucha data.
	- Usually many people access data concurrently.
	- Lots of UI screens.
	- Se integran con otras enterprise applications.
		- Siempre hay desacuerdos o malentendidos de que entiende un sistema y que el otro.
- Cuando se define la logica de negocios, no se puede cambiar. 
	- Hay casos bordes como por ej. tu sistema deposita el dinero a fin de mes, pero un cliente lo necesita 2 días antes. Haciendo que generes esta logica para esto. Se llama complex business "illogic".
- Martin Fowler recomienda desarmar una gran aplicación en varias para que los cambios sean fáciles
- La arquitectura es tradeoffs. Hay sistemas que no son complejos, pero requieren escalabilidad. Otros que tienen mucha lógica de negocios. Etc.
	- Hay que pensarla.
  ### Thinking about Performance
  - *Performance should not be treated as a fact until its measured on your configuration.*
  - Corolario: A significant change in your configuration may invalidate any facts about performance.
	  - Siempre hay que rehacer las pruebas de optimizacion a ver si son significativas en nuevas versiones
  - Terms:
	  - Response time: el tiempo que se demora un sistema en procesar una request. ex. UI Action, Server call.
	  - Responsiveness: que tan rapido el sistema se da cuenta de que una request esta siendo procesada. Ex: cuando haces una request y te muestra una progress bar que esta siendo procesada.
	  - Latency: el tiempo minimo requerido para conseguir algun tipo de response.
	  - Throughput: la cantidad de operaciones que puedes hacer en t(s). ex. Si estas copiando un archivo, a cuatnos bytes per second lo esta haciendo.
	  - Load: la cantidad de estres que un sistema está. Ex. cuando hay muchos usuarios conectados en un ecommerce.
	  - Load sensitivity: cuanto varia el response time cuando hay cierto load. Ex. con 100 usuarios las request demoran 1s, con 2000 demoran 10s.
	  - Eficiencia: performance dividido por resources. Un sistema que hace 30 tps(transaction per second) en 2 CPUs, es más eficiente que un sistema que hace 40TPS en 4 cpus.
	  - Capacity: es la medida de cuanto puede manejar de throughput o load.  Puede ser el maximo local o el punto de inflexion en cuanto el performance empieza a bajar.
	  - Scalability: es la medida de como agregar mas recursos (hardware) afecta el performance.
		  - Un sistema escalable (horizontal) permite agregar mas servidores para tener una mejor performance.
		  - Un sistema vertical upgradea el hardware para una mayor performance. [ThePrimeagen lo explica mucho mejor.](https://youtube.com/clip/UgkxtSUG4D0YReu1bqGrgy_nWtdUrjJHPiMc?si=3O23OsjgAVULcDpK)
	- Cuando se construye enterprise systems, es mejor optar por la escalabilidad mas que eficiencia o capacidad.


### Patterns
- Each pattern describes a problem which occurs over and over again in our enviroment, and then describes the core of the solution to that problem, in such a way that you can use this solution a million times over, without ever doing it the same way twice. 
- Siempre hay variaciones de los patterns, pero la mayoria se parece.



### Chapter  1 - Layering
- La tecnica mas comun para separar los sistemas.
	- Ejemplo las layas del network como TCP, IP, Ethernet.
- Benefits 
	- Permite entender un layer a la vez, sin la necesidad de saber los otros. Si quiero saber como construir un FTP server sobre TCP, no necesito saber los detalles de implementación de TCP.
	- Puedes sustituir los layers con otras alternativas, sin afecta el comportamiento de las otras. 
	- Minimizas las dependencias entre los layers.
	- Layers pueden ser estandarizados. Por ejemplo TCP/IP son ejemplos de estandares.
	- Los layers permiten hacer higher-level services. Ejemplo TCP/IP es utilizado para FTP, SSH o HTTP.
- Tradeoffs
	- No alcanzan a encapsular todo. Generando cambios en cascada. Por ejemplo tu aplicación agrega un campo en la base de datos, y tienes que mostrarla a nivel UI. Todos los layers que esten entremedios deben hacer el cambio.
	- Exra layers pueden dañar el performance. Ya que en cada layer, debe ser transformado para pasarselo a otra. 
		- Pero esto no es un problema si manejas las transformaciones/transactions correctamente.
- Anteriormente las app's tenian la business logic en la UI, causando toda causa de problemas de sincronizacion, código duplicado, entre otras.
- The three principal layers:
	- 1. Presentation: display de informacion, UI Html, handling of user request
	- Domain (Business Logic): Es la parte de la aplicación que hace el calculo, las transformaciones, validaction, etc. Recibida por la parte de la presentación
	- Data Source (comuniccation with databases):  se encarga de interactuar con la base de datos, puede ser ORM's, HTTP Clients, o la parte que hace las interacciones con la base de datos.
- Es un desastre dejar la business logic en la UI, generando toda causa de problemas.
- La recomendacion es dejar todo la business logic en las capas de Domain / Data Source. Dejando la capa de presentación lo más simple posible.
	- Por la misma razon que podemos manejar la logica en un servidor, sin necesidad de estar replicando nuestros cambios. Una fuente de la verdad (server). 
- Go all in en el server.
- El libro habla de separar la logica entre el cliente y server, pero es la peor decisión de todas. Solo hace las cosas peor. Complexity boosters.


	