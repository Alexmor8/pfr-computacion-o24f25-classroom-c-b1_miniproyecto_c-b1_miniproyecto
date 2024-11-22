# Mini Proyecto: Higher Order Functions
Programación funcional y reactiva
# 1. Importaciones necesarias
```scala
import scala.util.{Try, Success, Failure}
```
Importación de Try, Success, y Failure : Estas clases se utilizan para manejar excepciones de forma segura. permite encapsular el resultado de una operación que puede fallar, mientras que y son utilizados para representar el resultado exitoso o fallido respectivamente.TrySuccessFailure

# 2. Definición de Funciones de Derivación
# 2.1. Diferencias Finitas hacia Adelante
```scala
def derivadaAdelante(f: Double => Double, x: Double, h: Double): Try[Double] = {
  Try {
    if (h == 0) throw new IllegalArgumentException("El valor de h no puede ser cero.")
    f(x + h) - f(x) / h
  }
}
```
Función : derivadaAdelante
* Parámetros :
  
  f: La función a derivar (tipo ).Double => Double.
  
  x: El punto donde se evalúa la derivada.
  
  h: El incremento pequeño utilizado para la aproximación.
  
* Lógica :
 
  Se utiliza para manejar excepciones.Try
  
  Se verifica si es cero y se lanza una excepción si es así.h
  
  Calcula la derivada usando la fórmula de diferencias finitas hacia adelante:
 F"(x) ≈ f(x+h) - f(x) / h

# 2.2. Diferencias Finitas Centradas
```scala
def derivadaCentrada(f: Double => Double, x: Double, h: Double): Try[Double] = {
  Try {
    if (h == 0) throw new IllegalArgumentException("El valor de h no puede ser cero.")
    (f(x + h) - f(x - h)) / (2 * h)
  }
}
```
* Función: derivadaCentrada
* Parámetros: Igual que en la función anterior.
* Lógica:

  Verifica si h es cero y lanza una excepción si es necesario.
  
  Calcula la derivada usando la fórmula de diferencias finitas centradas: 
 f′(x)≈f(x+h)−f(x−h) / 2h

# 2.3. Diferencias Finitas hacia Atrás
```scala
def derivadaAtras(f: Double => Double, x: Double, h: Double): Try[Double] = {
  Try {
    if (h == 0) throw new IllegalArgumentException("El valor de h no puede ser cero.")
    f(x) - f(x - h) / h
  }
}
```
* Función: derivadaAtras
* Parámetros: Igual que en las funciones anteriores.
* Lógica:
  
  Verifica si h es cero y lanza una excepción si es necesario.
  
  Calcula la derivada usando la fórmula de diferencias finitas hacia atrás: 
f′(x) ≈ f(x) − f(x−h) / h

# 3. Cálculo del Error Absoluto
```scala
def calcularError(valorEsperado: Double, valorAproximado: Double): Try[Double] = {
  Try {
    Math.abs(valorEsperado - valorAproximado)
  }
}
```
* Función: calcularError
* Parámetros:
  
    valorEsperado: El valor real de la derivada (analítica).
  
    valorAproximado: El resultado obtenido mediante los métodos numéricos.
  
* Lógica:
  
    Utiliza Try para manejar excepciones al calcular el error absoluto.
  
    Devuelve el valor absoluto de la diferencia entre el valor esperado y el aproximado.
  
