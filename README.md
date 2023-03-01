## El camino del ‘Zen’ en Python: cómo mejorar tus habilidades como programador
---

El [Zen de Python](https://github.com/python/peps/blob/main/pep-0020.txt) es un conjunto de filosofías y buenas prácticas para escribir código en Python. Estas filosofías fueron escritas por Tim Peters, uno de los primeros desarrolladores de Python, y se han convertido en una guía importante para la comunidad de Python.

El Zen de Python se centra en la legibilidad, la simplicidad y la claridad del código, y se basa en la idea de que el código debe ser fácil de leer y comprender para otros programadores, así como para ti mismo en el futuro.

Puedes ver el Zen de Python ejecutando el siguiente código en Python:

```python 
import this
```

[![Youtube.jpg](https://i.postimg.cc/h4TW0jzg/Youtube.jpg)]([https://postimg.cc/dDsxsJjS](https://youtu.be/AuRT9DmJocA))

---

1.  **Bonito es mejor que feo**: La estética y la presentación de código son importantes para la legibilidad. Un código bien formateado y estructurado es más fácil de leer y mantener que uno feo y desordenado.

*Ejemplo*:

```python
# Mal
for i in range(len([1,2,3,4,5])):
    print(i*2)

# Bien
numeros = [1, 2, 3, 4, 5]
for numero in numeros:
    print(numero * 2)
``` 
---
2.  **Explícito es mejor que implícito**: El código debería ser claro y explícito en su intención como en su funcionamiento. Las abreviaturas y acrónimos pueden ser confusos para otros programadores por tanto deben evitarse en la medida de lo posible.

*Ejemplo*:

```python
# Mal
def f(x):
    return x**2

# Bien
def calcular_cuadrado(x):
    return x ** 2
``` 
---
3.  **Simple es mejor que complejo**: Un código simple es más fácil de entender y mantener que uno complejo. Es importante buscar la simplicidad en la solución a un problema.

*Ejemplo*:

```python
# Mal
def sumar_números_pares(numbers):
    result = 0
    for i in range(len(numbers)):
        if numbers[i] % 2 == 0:
            result += numbers[i]
    return result

# Bien
def sumar_números_pares(numbers):
    return sum(n for n in numbers if n % 2 == 0)
```

---

4.  **Complejo es mejor que complicado**: Un código complejo puede ser necesario para resolver un problema complejo, pero debe ser claro y fácil de entender. Un código complicado es difícil de entender y mantener.

Ejemplo:

```python
# Mal
def es_primo(n):
    if n <= 1:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

# Bien
def es_primo(n):
    if n <= 1:
        return False
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False
    return True
```

La función "es_primo" comprueba si un número dado es primo o no. En la primera implementación de la función, se utiliza un bucle "for" para iterar a través de todos los números entre 2 y "n-1" para verificar si "n" es divisible por cualquiera de estos números. Esto es una solución complicada, porque es necesario iterar a través de todos estos números, lo que puede ser ineficiente y aumentar el tiempo de ejecución de la función.

La segunda implementación de la función utiliza una solución más compleja pero más eficiente. En lugar de iterar a través de todos los números, solo se necesita iterar hasta la raíz cuadrada de "n", lo que disminuye el número de iteraciones necesarias. En otras palabras, si "n" es divisible por un número mayor que la raíz cuadrada de "n", entonces también sería divisible por un número menor que la raíz cuadrada de "n", y este número ya habría sido comprobado en una iteración anterior.

Por lo tanto, la segunda implementación de la función es más compleja pero más eficiente, ya que utiliza un enfoque matemático avanzado para reducir la cantidad de iteraciones necesarias para verificar si un número es primo. La solución es más fácil de entender y mantener en el futuro, lo que la hace más escalable y eficiente.

---
[-]
5.  **Plano es mejor que anidado**: Un código con una profundidad de anidamiento limitada es más fácil de entender y mantener que uno con una profundidad de anidamiento excesiva.

*Ejemplo*:

```python
# Mal 
def b():
    numeros = range(10)
    for i in numeros:
        for j in numeros:
            for k in numeros:
                for l in numeros:
                    for m in numeros:
                        for n in numeros:
                            for o in numeros:
                                for p in numeros:
                                    for q in numeros:
                                        print(i, j, k, l, m, n, o, p, q)

# Bien
from itertools import product

def b():
    for tupla in product(range(10), repeat=9):
        print(tupla)
```

---
[-]
6. **Disperso es mejor que denso**: Un código con una alta densidad de información es difícil de entender y mantener. Es mejor tener un código disperso con líneas separadas para cada concepto.

Ejemplo:

```python
# Mal
print('\n'.join("%i bytes = %i bits which has %i possible values." % (j, j*8, 256**j-1) for j in (1 << i for i in range(8))))

# Bien
for i in range(8):
    j = 1 << i
    bytes = j
    bits = j * 8
    possible_values = 256 ** j - 1
    result = f"{bytes} bytes = {bits} bits which has {possible_values} possible values."
    print(result)
```

---

7. **La legibilidad importa**: Esto significa que es importante escribir código que sea fácil de leer y comprender para otros programadores, así como para ti mismo en el futuro. Un código legible es más fácil de mantener y solucionar problemas, lo que reduce el tiempo y los costos de desarrollo. 

*Ejemplo*: 

```python
# Mal
def c(a,b):
 return a+b

# Bien
def calcular_suma(operando_1, operando_2):
    return operando_1 + operando_2
```

En el primer ejemplo, la función "c" no es claramente descriptiva y es difícil de entender qué hace.

En el segundo ejemplo, la función "calcular_suma" es clara y descriptiva, lo que facilita la comprensión de lo que hace. Además, los nombres de variables "operando_1" y "operando_2" son claros y descriptivos.

---

8. **Los casos especiales no son lo suficientemente especiales para romper reglas.**: 

Aunque pueda haber casos especiales que requieran un tratamiento especial, no deben ser una excepción a las buenas prácticas de codificación. 



*Ejemplo*:

```python
# Mal
def divisible_por_tres(numero):
    if numero == 9:
        return "Nueve es especial"
    elif numero % 3 == 0:
        return "Divisible por tres"
    else:
        return "No divisible por tres"

# Bien
def divisible_por_tres(numero):
    if numero % 3 == 0:
        return "Divisible por tres"
    else:
        return "No divisible por tres"
```
En el primer ejemplo, la función crea una excepción especial para el número 9 que no sigue la regla general de divisibilidad por 3. En lugar de simplemente verificar si el número es divisible por 3, la función crea una excepción para el caso específico del número 9, lo que dificulta el mantenimiento y la escalabilidad del código.

En el segundo ejemplo, la función sigue la regla general de divisibilidad por 3 y no crea excepciones especiales para casos específicos. De esta manera, el código es más práctico, fácil de entender y fácil de mantener, lo que lo hace más escalable y eficiente.

---

9. **Practicidad vence a la pureza:** La funcionalidad y la utilidad del código son más importantes que la pureza matemática o teórica. Es mejor una solución práctica y funcional aunque no sea pura.: 

*Ejemplo*:

```python
# Mal
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)
    
# Bien
def factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
```

La primera implementación utiliza un enfoque recursivo, mientras que la segunda utiliza un enfoque iterativo. 

La segunda solución es más eficiente y fácil de entender porque utiliza un enfoque iterativo simple y eficiente para calcular el factorial de un número, lo que la hace más rápida en términos de tiempo de ejecución y menos propensa a causar desbordamiento de pila.

---

 10. **Los errores nunca deberían de ocurrir silenciosamente. A no ser que se silencien explícitamente**: Es importante que los errores sean manejados y notificados de manera adecuada para evitar problemas en la ejecución del código.

*Ejemplo*: 

```python
# Mal
def dividir(a, b): return a / b

# Bien
def dividir(a, b): 
    try: 
        return a / b 
    except ZeroDivisionError: 
        print("Error: no se puede dividir por cero")
```

-----

 11.   **En el caso de ambigüedad, rechaza la tentación de adivinar**: A menudo, cuando nos encontramos con una parte del código que no está clara o ambigua, podemos sentir la tentación de hacer una suposición sobre lo que el autor del código intentaba hacer. Sin embargo, esto puede llevar a errores y malinterpretaciones en el futuro, especialmente si otras personas trabajan en el mismo código.
   
Por lo tanto, en lugar de adivinar, se recomienda buscar una explicación clara y detallada sobre lo que el código está tratando de hacer. Si no está claro, es mejor preguntar al autor original del código o a otros miembros del equipo para obtener una aclaración antes de continuar.

-----
 12.  **Debería haber una, y preferiblemente solo una, forma obvia de hacerlo**: Debe buscarse la simplicidad y claridad en el código y evitar soluciones confusas o con múltiples formas de hacer lo mismo.

-----
 13.  **Aunque esa forma puede no ser obvia al principio a menos que seas Holandés**: Se refiere a que a veces es necesario pensar fuera de la caja para encontrar la solución más simple y eficiente. La frase "a no ser que seas Holandés" se refiere al creador de Python, Guido van Rossum, que es holandés. Obviamente, recordar y comprender cualquier regla en Python sería más fácil para él que para cualquier otra persona.

Un ejemplo que ilustra los principios 11, 12 y 13 podría ser un programa que genera una contraseña aleatoria. Si se utiliza una implementación ambigua o poco clara, puede ser difícil para el usuario entender cómo se generó la contraseña o cómo deben usarla. Por ejemplo, un código que genera una contraseña de forma ambigua podría ser el siguiente:

*Ejemplo*: 

```python
# Mal
import random
import string

def generar_password():
    letras = string.ascii_letters
    simbolos = string.punctuation
    numeros = string.digits

    password = random.sample(letras, 2) + random.sample(simbolos, 2) + random.sample(numeros, 4)
    random.shuffle(password)

    return ''.join(password)

# Bien
import random
import string

def generar_password():
    caracteres = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choices(caracteres, k=8))

    return password
```

En el primer ejemplo, la función genera una contraseña aleatoria combinando dos letras, dos símbolos y cuatro números, y luego baraja los caracteres. Aunque esto genera una contraseña aleatoria, el código no es claro y puede ser difícil para el usuario entender cómo funciona.

En el segundo ejemplo, la función utiliza un solo conjunto de caracteres para generar la contraseña en lugar de tres diferentes. También utiliza la función "choices" del módulo "random" para elegir aleatoriamente los caracteres en lugar de hacerlo con tres llamadas separadas a "random.sample". Además, la función genera una contraseña de ocho caracteres de longitud en lugar de seis, lo que la hace más segura.

-----

14. **Ahora es mejor que nunca**: Es importante comenzar a implementar buenas prácticas de codificación desde el principio, aunque no se hayan implementado antes.

-----

15.  **Aunque nunca es a menudo mejor que ahora mismo**: Es importante no posponer la implementación de buenas prácticas de codificación, pero también es importante tener en cuenta el contexto y asegurarse de que la implementación se haga en el momento adecuado.

-----

16.  **Si la implementación es difícil de explicar, es una mala idea**: Si una solución es difícil de explicar, probablemente sea complicada y difícil de entender y mantener. Es importante buscar soluciones claras y fáciles de explicar.

-----

17.  **Si la implementación es fácil de explicar, puede ser una buena idea**: Esto significa que la claridad y la simplicidad son factores importantes en la escritura de código. Un código claro y fácil de explicar es más fácil de comprender para otros programadores, lo que facilita la colaboración y el mantenimiento del código a largo plazo. Además, un código claro es más fácil de depurar y solucionar problemas, lo que reduce el tiempo y los costos de desarrollo.


---

18.   **Los espacios de nombres son una buena idea, ¡usemos más de ellos!**: Los espacios de nombres son una buena manera de organizar y separar el código en diferentes módulos y componentes, lo que facilita la legibilidad y la mantenibilidad del código. La modularización es un mecanismo que permite organizar y distinguir entre diferentes conjuntos de nombres (variables, funciones, clases, módulos, etc.) en un programa de Python.

*Ejemplo*:

```python
# Mal
def sumar(a, b):
    return a + b

def restar(a, b):
    return a - b

# Bien
def matematicas.sumar(a, b):
    return a + b

def matematicas.restar(a, b):
    return a - b
```

En este ejemplo, se crea un espacio de nombres llamado "matemáticas" que contiene las funciones "sumar" y "restar". De esta manera, se evita la posibilidad de tener nombres de funciones duplicados y se hace más fácil identificar de qué módulo provienen las funciones.
