Lo encontre por el blog de https://martinfowler.com/ y algunas tier list de libros de software engineering.


(missing)

## Chapter 3
- Entender el scope del problema en profundo.
- "*You can't be a great programmer until you become highly skill at debugging*".
- Keep knowledge in plain text (ver Engineering Daybook)
- Si haces todo atraves de una GUI, pierdes todo el potencial que te ofrece hacer cosas con el CLI.
- Debugging es un tema emocional y sensitivo para algunos programadores. Puedes buscar quien fue el culpable del código, pero olvídalo. Mejor enfocate en resolver el problema. Al final del día, tienes que hacerlo. 
- Primera regla de debuggear: don't panic.
- Don't fold under pressure of stakeholders/users, take a step back before  finding a solution. 
- La solucion puede estar unos pasos más allá de lo que piensas.
- Trata de reproducir el bug con los mismos datos. Aisla el caso, prueba los casos bordes y como realmente el usuario usa la aplicación. No como si la estuvieras usando desde una perspectiva de dev.
- Si miras un error stack, usa binary search a partir de un frame que puede ser.
- Lee el error antes de saltar el codigo.

## Chapter 4
- Design by contract: establece quien hace que cosa, responsabilidades de cada equipo. https://en.wikipedia.org/wiki/Design_by_contract
- Design by contract es un approach para diseñar software en el cual se definen precondiciones (guard clause, debe cumplicar ciertas condiciones), postcondiciones (esta funcion deberia devolverme un output).
- Bastante deprecado ya que muchos problemas no simplemente se solucionan con un contrato. Los  requerimientos son caoticos.
- Se rescatan ideas como defensive programming, tipo agregar guard clauses donde corresponde antes que llegue a otras partes.



--- 

## Preguntas

###### Que emoción deberías tener cuidado cuando estas haciendo debugging?
A: La necesidad de echarle la culpa a alguién del error.
###### 
