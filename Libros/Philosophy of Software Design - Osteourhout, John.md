

##  4 - Modules Should be Deep
- Definition of a module: is a unit of code that has an interface and an implementation
- Un dev no debería saber cómo es la implementación de un modulo (de una clase, un servicio)
	- Ejemplo:  un servicio que se llame getUser(id), solamente nos interesa cómo funciona la interfaz (el input, y el output), pero no la implementación por dentro ( que haga request HTTP, llame a supabase, oauth, etc)
- The best module are those whose interfaces are much simpler than their implementation.

### Deep Modules

- Practical examples: https://claude.ai/public/artifacts/b7d9afe3-b1f3-4faf-a727-623e3a36fe76






## Questions


Q: What is tactical tornado?
A: Just to get the feature done, leaving full of tech debt behind.

Q: What consequcens does tactical tornado leaves?
A: Technical debt and slows down other devs

Q: What is strategic programming:
A: Aquel que piensas un poco el diseño antes de programar

Q: Is it okay to invest too much designing?
A: Nope because it won't be effective. This is the waterfall method lol.

Q: What is the ideal amount of investment:
A: In bits and pieces (10-20% of your time)

Q: What it's gonna happen when you invest time designing?
A:In the beginning you will slow


Q: What is the definition of a module in the book?
A: An unit of code that has an interface and a implementation p.20

Q: What is the ideal design of a module?
A: Cuando el dev que trabaja con ella entiende su interfaz, pero no su implementación. p.20

Q: What is an abstraction?
A: a simplified view of an entity, which omits unimportant details.

Q: In what 2 ways an abstraction can go wrong?
A: When it includes details that are not important. 
And when it hides details that are.

Q: What happens when an abstraction INCLUDES details that are UNIMPORTANT?
A: makes the abstraction more complicated than necessary.  increasing the cognitive load of the devs using it.

Q: What happens when an abstraction OMITS details that are IMPORTANT?
A: : It goes wrong because it increases obscurity. Developers looking at the abstraction will not have all the necessary information to understand it.

Q: What are deep modules?
A: aquellos que otorgan mucha funcionalidad pero tienen una interfaz simple.
 https://claude.ai/public/artifacts/b7d9afe3-b1f3-4faf-a727-623e3a36fe7

Q: What are some example of deep modules?
A: Java or Go garbage collector. UNIX filesystem operations
 
Q: What are shallow modules?
A: aquellos su funcionalidad es simple pero su interfaz es compleja
 https://claude.ai/public/artifacts/b7d9afe3-b1f3-4faf-a727-623e3a36fe76


Q: What are some examples of shallow modules?
A: The method of a class that takes 10 different arguments, moving the complexity to the number of arguments instead of the overall functionality.

Java file reading operations, because you need to instantiate 3 different classes to read from a file: `FileInputStream`, `BufferedInputStream` `ObjectInputStream`
 

Q: What is better a deep module or a shallow module?
A: deep module because they hide the overall complexity.



 
 