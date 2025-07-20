

##  4 - Modules Should be Deep
- Definition of a module: is a unit of code that has an interface and an implementation
- Un dev no debería saber cómo es la implementación de un modulo (de una clase, un servicio)
	- Ejemplo:  un servicio que se llame getUser(id), solamente nos interesa cómo funciona la interfaz (el input, y el output), pero no la implementación por dentro ( que haga request HTTP, llame a supabase, oauth, etc)
- The best module are those whose interfaces are much simpler than their implementation.

### Deep Modules

- Practical examples: https://claude.ai/public/artifacts/b7d9afe3-b1f3-4faf-a727-623e3a36fe76






## Information Leakage
- Cuando muchos modulos dependen de varia información entre sí, a veces es mejor hacer un modulo más grande que contenga toda la información relacionada a este proceso. Information hiding can often be improved by making a class slightly larger.
- Avoid exposing internal data structures as much as possible.
- Classes should do the right thing without being explicitly askedl. Defaults are an example of this.
- The best features are the ones you get without even knowing they exist.
- Red Flag -Overexpose: If the API for a feature forces users to learn about others implementations, this increases cognitive load.
- You can also hide information from within the class. Such as designing private methods within  a class so that each method encapsulates some information and hides it from the rest of the class.
- Information hiding hace sentido cuando la información que está siendo escondida no tiene que ser usada fuera de su modulo. 
	- If the information is needed outside of the module, then you must not hide it. 
		- An example of this is a module that accepts a configuration parameter: class UserService(apiUrl: string).fetch(id);
- Information hiding an deep modules are closely related.
- if a module doesn't hide much information, then either it doesn't have much functionality or it has a complex interface.
- When decomposing a system into modules, try not to be infleunced by the order of which operations will occur at runtime.


## Chapter 6
- Hay una discusion entre si programas los modulos de forma specialized or general purpose. El autor menciona que la specialization lleva a mayor complejidad, mientras que el general-purpose es más simple.
- El desafío común cuando diseñas una clase es hacer specialized para un caso o general purpose. 
	- Specialized: enfocarse en un problema especifico a resolver.
		- `class EmailNotifier` con metodos cómo `sendWelcomeEmail`, `sendOnboardingEmail`
	- General purpose: enfocarse en variedad de problemas a resolver, no aquellos que importan el día de hoy.
		- `class EmailNotifier` con metodos como: `sendEmail` que acepta como argumento el string del email a enviar, y un objeto de configuración.
- Make classes somewhat general-purpose
	- Somewhat general purpose means that the implementation should reflect your current needs, but it's interface should not.
- One of the most important elemnts of software design is determining who needs to know what, and when.
	- Cuando los detalles son importanes, es mejor hacerlo más explicitos aún.
- Questions to ask your self?
	- What is the simplest interface that will cover all my current needs?
	- In how many situations will this method be used?
	- Is this API easy to use for my current needs?

### 6.6 Push specialization updates (and downwards)
- Es inevitable que haya código que sea specialized. Por ejemplo, para un grupo de usuarios haya una feature especifica.
	- pero hay que dejar clara la separación del caso especifico, y el general.
- You can push specialization  upwards by making top level classes  handlingthe special cases.
	- Classes such as `EmailService`, `SMSService`, `PushNotificationService` (?)
- You can push it downwards by making the low-level class handle the special cases.
	- `NotificationService` that calls classes such as `EmailChannel SmsChannel PushChannel` . Strategy Pattern.

- Eliminate specialñ cases in code: can result in code that is riddled with "if" statements, which make the code hard to understand. Delete it wherever possible.
	- Code should handle this cases by treating it with defaults.
- Unnecesary specialization in the form of special purpose classes or code, is a significant contributor to software complexity.


# 7 - Different Layer, Different Abstraction
- Software systems are composed in layers, where higher layers  uses the facilities provided by the lower layers.
	- Such as TCP Protocol
	- Such as File System abstractions
- Redflag Passthrough methods are the ones which just call the method of another class. Ex: class TextDocument{ constructor(textArea) insertString(){ this.textArea.insertString()}}
	- Makes classes shallow.
	- Indicates that maybe there is a confusion over the division of responsibility between classes.
	- When you see passtrough methods, ask yourself "Exactly which feaures and abstractions is each of these classes responsibly for?"
	- The solution is to expose the lower level classes directly to the callers of the higher class (llama a las clases lower level nomás)



## Chapter 10 - Define Errors out of Existence
- Exception = Error 
- *developers often define exceptions without considering how they will be handled.*
- El autor argumenta que cuando los modulos tiran excepciones, aumenta la complejidad del sistema, ya que tienes que hacer código para estos casos especiales.
	- Obviamente es más díficil que un modulo que no lanza excepciones.
	- Para esto está el defensive programming, que checkea por las excepciones. Pero también aumenta la complejidad del código llenandolos  de try/except/catch
- Throwing exceptions is easy; handling them is hard.
- En conclusion: manejar o esconder excepciones depende que tan importante sean para los usuarios de tu modulo. Si es importante mostrar las exceptions, entonces levanta la exception. If not, then define errors out of existence.





## Chapter 13 - Comments should describe things that aren't obvious  from the code

- Like the title says: *Comments should describe things that aren't obvious  from the code*
- Red Flag: *Comment that Repeats code*
- Higher level comments enhance intuition
- Interface comments should explain in higher level how it works,if it has any side effects, and any exceptions that can emanate from the method.
- Red Flag: Implementation docmuentation contaminates interface
- When writing comments try toput yourself in the mindset of the reader and ask yourself what are the key things he will need to know.



## Chapter 14- Choosing names

- Selecting names for variables, methods and other entities is one of the most underrated aspects of software design.
- When choosing a name, try to create an image in the mind of the reader about the nature of the thing being named.
- Red flag: Vague name: if a variable or method name is broad enough to refer to many different things, then it doesn't convey much informaton to the developer.
- Red flag: hard to pick name: If it's hard to find a simple name for a variable or method, that's a hint that the underlying object may not have a clean design.
	- Perhaps you are trying to use a single variable to represent several things.

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


MISSING NOTES 


 
 