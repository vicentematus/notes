

### 22 - Relating Elements
- Los sistemas se deberían ordenar de manera que sus elementos tienen relación entre sí.
	- Ejemplo: Atomos -> Moleculas, Cristales.
	- Tokens > expresisions > statements > functions > object/modules > systems.
- Un diseño que tenga elementos que estén bien relacionados entre sí es más fácil de modificar.
- Ejemplo
	- de una función que sea fn(): return box.width() * box.height()
	- Corresponderia refactorizar dentro de box, una función nueva que relacione ambas. class Box fn area(): return box.width() * box.height().
	  
	  Cosa de que al momento de llamarlo en una función externa, simplemente nos preocupemos de una sola cosa que sería box.area()


### 23 - Structure and Behaviour
- Los sistemas generan valor de las siguientes 2 maneraS:
	- Que hace hoy
	- La posibilidad de agregar nuevas features.
- Lo que hace hoy es el behaviour (comportamiento) del sistema. Es lo que genera las ganancias. El sistema podría quedarse así y generar ganancias por un tiempo.
- ???
- The structure of the sysmem doesnt matter to itsbehavior. One big function, a whole bunch of itty bitties, same paycheck comes out. The structure is what creates options.
- La estructura de un sistema no es legible como agregar nuevas features. Por eso es que exiten los roadmaps.
- Sabemos que mantener una buena arquitectura o behaviour es importante para el sistema. Eso implica que agregar nuevo código sea fácil, o nuevas funcionalidades. Pero no sabremos bien si realmente si tomamos las decisiones correctas(?)

# 24 - Economics: Time Value and Optionality
- En las aplicaciones es importante el dinero.
- A dollar today is worth more than a dollar tomorrow, so earn sooner and spend later.
- In a chaotic situation, options are better than things, so create options in the face of adversity.