[Ver en YouTube](https://youtu.be/ZA-tUyM_y7s?list=PLUl4u3cNGP63EdVPNLG3ToM6LaEUuStEY)


- Se define como f(x) =  I -> O
	- I: Input
	- O: Output
- Se define un problema de cómo se puede crear un algoritmo para encontrar a 2 alumnos que estén de cumpleaños el mismo día.
- Para probar que el algoritmo que definimos se usa  Inductive hypothesis[^1]  

## Inductive proof
- Sirve para probar que nuestro algoritmo es correcto teoricamente.
> **Mathematical induction** is a method for [proving](https://en.wikipedia.org/wiki/Mathematical_proof "Mathematical proof") that a statement P(n)![{\displaystyle P(n)}](https://wikimedia.org/api/rest_v1/media/math/render/svg/5e303d2c14cd399b6f52b468c9fd44a542bed422) is true for every [natural number](https://en.wikipedia.org/wiki/Natural_number "Natural number") n![{\displaystyle n}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a601995d55609f2d9f5e233e36fbe9ea26011b3b), that is, that the infinitely many cases P(0),P(1),P(2),P(3),…![{\displaystyle P(0),P(1),P(2),P(3),\dots }](https://wikimedia.org/api/rest_v1/media/math/render/svg/2b711489e1c1a6623f75d4cb531a06f8204cf65b)  all hold. (Wikipedia)
- Para usar inducción matemática necesitamos 2 proposiciones: Un proposición base que prueba P_1  (n=0 por ejemplo caso inicial) es verdader. La segunda proposición "Paso inductivo",  necesitamos para todas las proposiciones n= k, entonces tiene que ser verdad para el n= k +1. La demostración de ambas concluimos que es real para todos los numeros naturales.

### Desarrollo del ejercicio 
- Problema: se define cómo se puede crear un algoritmo para encontrar a 2 alumnos que estén de cumpleaños el mismo día.
- Siguiendo el ejercicio, se define como hipotesis inductiva: si los primeros K students tienen un match, el algoritmo retorna el match antes de entrevistar al estudiante K+1. (En otras palabras eso significa que alcanzo a encontrar un match antes que terminará el listado de estudiantes)
- Se define un base case en el cual es 0. Es decir que los primeros 0 estudiantes no tienen un match.
- La idea de usar inducción  es para aislar el problema en pequeños problemas.
- Entonces se asume que para k = k'
	- 1. Si k' contiene un match -> ya esta probado por la inducción
	- Si K'+1 contiene un match, el algoritmo revisa todas las posibilidades de todos los estudiantes (por fuerza bruta, ya que revisó todos los alumnos).


## Efficiency
- No se mide el tiempo, solamente la cantidad de operaciones (fundamentals operations or ops).
- Se espera que el performance dependa del tamaño de nuestro input.
-  $$Upperbound=O , Lower bound = \Omega, Both= \Theta $$
- O(1) = constante
- O(log n) = Logarithmic time
	- almost good as a consta nt.
- O(N) = linear
- O(n log n) = linear logarithmic
- O(n2) = exponencial

[^1]: Revisar proofs
