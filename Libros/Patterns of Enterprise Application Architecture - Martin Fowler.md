Recomendado por David Heinemeier Hanson (DHH) en [The five programming books that meant most to me](https://signalvnoise.com/posts/3375-the-five-programming-books-that-meant-most-to-me)

> Great inventory of many of the patterns that underpin Rails itself, as well as descriptions of many of the “new” approaches that people advocate today (like [transaction scripts](http://martinfowler.com/eaaCatalog/transactionScript.html) and [service layers](http://martinfowler.com/eaaCatalog/serviceLayer.html)). You won’t necessarily implement most of these patterns yourself, but it’s an invaluable resource to understanding the differences in architectures and why framework work the way they do. (Funny anecdote: before I created Rails, [I redrew many of the diagrams](http://martinfowler.com/eaaCatalog/) in OmniGraffle for Martin Fowler because I liked the book so much.)


## 1 - Introduction
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
- Martin Fowler recomienda desarmar una gran aplicación en varias para que los cambios sean fáciles.
	