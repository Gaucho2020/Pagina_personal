#  🫧 Versión Orientada a Objetos (POO)

<img width="1300" height="804" alt="image" src="https://github.com/user-attachments/assets/a694f47a-d033-48b5-9921-8ab5f449e812" />

El objetivo es refactorizar el paquete anterior utilizando **Clases y Objetos**. Eliminando las variables globales y aplicando Encapsulamiento.

## ⚙️ Requerimientos funcionales

### Clase `tortuga`

Toda la lógica debe estar dentro de una clase. 

### Encapsulamiento

* Antes: `alineación` era una variable global.
* Ahora: `self.alineacion` es un **atributo de instancia**, inicializado en el constructor (`__init__`).
* Prohibido usar `global`.

### Interfaz de objetos `__init__.py`

El usuario debe importar la clase `Tortuga` desde la carpeta.

Desde `__init__.py` debemos colocar:

```
from .turtle_class import Tortuga
```
Y el usuario podrá importar desde `main.py` así:

```
from mini_turtle_oo import Tortuga
```
## 📁 Estructura de archivos

<img width="168" height="181" alt="image" src="https://github.com/user-attachments/assets/0f036db1-820a-4709-b2cf-b3a677b30b9f" />

## 📋 Pasos de implementación

### ☑️ 1. Creamos la clase `Tortuga`

* Definimos `class Tortuga`
* Usamos `__init__` para inicializar `self.alineacion = 0`

```
# Creación de la clase tortuga

class Tortuga:
    def __init__(self):                    # Constructor de la clase tortuga
                self.alineacion = 0        # Estado inicial de la tortuga
```

### 🚀 Métodos de la clase `Tortuga`

Convertimos las funciones en **métodos**. Usando `self`

🔩 `adelante(self, ancho):`

```
 def adelante(self, ancho):                                      # Mover la tortuga delante
        print(" " * self.alineacion + " —" * ancho + "┐")
        self.alineacion += ancho * 2                             # Actualiza posición
```
* **Propósito:** Mueve la tortuga hacia adelante en el eje horizontal.
* **Cómo funciona:**
    * Usa `self.alineacion` para calcular la cantidad de espacios antes de dibujar.
    * Imprime una línea horizontal (—) repetida según el parámetro ancho.
    * Actualiza la posición sumando `ancho * 2`, lo que simula el avance.
* Importancia: Permite que la tortuga “camine” hacia adelante manteniendo su propio estado interno.


🔩 `abajo(self, alto):`

```
 def abajo(self, alto):                            # Mover la tortuga hacia abajo
     for _ in range(alto):
         print(" " * self.alineacion + "|")
     print(" " * self.alineacion + "🐢")
```
* **Propósito:** Mueve la tortuga hacia abajo en el eje vertical.
* **Cómo funciona:**
    * Repite el símbolo "|" tantas veces como indique `alto`, alineado con la posición actual (`self.alineacion`).
    * Finalmente imprime el ícono de la tortuga "🐢" en la nueva posición.
* Importancia: Representa el descenso de la tortuga en la “pantalla” de texto, manteniendo la alineación horizontal.

🔩 `reinicio(self):`

```
def reinicio(self):                     # Reinicia la posición a 0
        self.alineacion = 0
```
* **Propósito:** Devuelve la tortuga a la posición inicial.
* **Cómo funciona:**
    * Asigna `0` al atributo `self.alineacion`.
* Importancia: Permite reiniciar el recorrido y empezar un nuevo dibujo desde el inicio, sin necesidad de crear otro objeto.

> [!NOTA]
>
> * Cada método usa el estado interno (`self.alineacion`) en lugar de variables globales.
> * Esto asegura que cada objeto `Tortuga` tenga su propio recorrido independiente.
> * La interfaz es intuitiva: `adelante(ancho)`, `abajo(alto)` y `reinicio()` son comandos simples que simulan el movimiento de una tortuga en texto.

### 🎲 2. Interfaz `__init__`

En el paquete `mini_turtle_oo`, el archivo `__init__.py` expone la clase `Tortuga` para que el usuario pueda importarla directamente, sin necesidad de conocer la estructura interna del paquete.

<img width="401" height="116" alt="image" src="https://github.com/user-attachments/assets/9b7c3968-9204-4b68-a2b1-ed9a26fe914d" />

Gracias a `__init__.py`, el usuario puede escribir:

```
from mini_turtle_oo import Tortuga

t = Tortuga()
t.adelante(10)
t.abajo(3)
```

➡️ El usuario no necesita saber que la clase está en `turtle_class.py`. La interfaz pública del paquete se simplifica

### 🎯 3. Prueba `main.py`

* **Ejemplo 1**

```
# Importación de clase
from mini_turtle_oo import Tortuga

# Uso de la clase
t = Tortuga()

t.adelante(5)
t.abajo(3)

t.adelante(5)
t.abajo(3)

t.reinicio()

t.adelante(5)
t.abajo(3)

t.adelante(5)
t.abajo(3)
```

 * La clase `Tortuga ` es importada desde el módulo `mini_turtle_oo`
 * Se crea una instancia de la clase `Tortuga`
 * Al ejecutarse el constructor `__init__`, el atributo `alineacion` se inicializa en `0`.
 * Esto significa que la tortuga empieza en la posición inicial.
 
```
# Resultado
 — — — — —┐
          |
          |
          |
          🐢
           — — — — —┐
                    |
                    |
                    |
                    🐢
 — — — — —┐
          |
          |
          |
          🐢
           — — — — —┐
                    |
                    |
                    |
                    🐢
 ```
  
* **Ejemplo 2**
*Independencia de objetos*
Creamos dos objetos `Tortuga` y cada uno mantiene su propia posición.
Aquí `t1` y `t2` tienen **estados distintos** `alineacion` independiente.

```
# Importación de clase
from mini_turtle_oo import Tortuga

# Uso de la clase
t1 = Tortuga()
t2 = Tortuga()

t1.adelante(5)
t1.abajo(3)

t1.adelante(5)
t1.abajo(3)

t2.adelante(10)
t2.abajo(5)

t2.adelante(10)
t2.abajo(5)

```


```
# Resultado
 — — — — —┐
          |
          |
          |
          🐢
           — — — — —┐
                    |
                    |
                    |
                    🐢
 — — — — — — — — — —┐
                    |
                    |
                    |
                    |
                    |
                    🐢
                     — — — — — — — — — —┐
                                        |
                                        |
                                        |
                                        |
                                        |
                                        🐢

```
## 📄 Documentación de la transformación

|   **Requerimiento**|    **Antes (Código Funcional)**    |    **Depués (Clase `Tortuga`**     |
|---------------|-----------------|---------------------|
| Clase Tortuga | No existía | Se crea `turtle_class`  |
| Encapsulamiento | `alineacion` como variable global | `self.alineacion` como atributo de instancia  |
| Interfaz de objetos | Funciones sueltas | Métodos dentro de la clase importados con `from_mini_turtle_oo import Tortuga` |
| Independencia | Una sola posición global compartida | Cada objeto `Tortuga` mantiene su propia posición  |

# Referencias IA
- Copilot: conversación en versión de escritorio docuemtación de clases. https://copilot.microsoft.com/shares/RDucbCDCSN8K9281BLJSa
- Copilot: conversación en versión de escritorio tabla comparativa entre el antes y después del proyecto. https://copilot.microsoft.com/shares/Q32un9GK4iD5aWp8aBBy1

# Referencias web
- Experience league. Como utilizar Markdown para escribir documentación técnica. https://experienceleague.adobe.com/es/docs/contributor/contributor-guide/writing-essentials/markdown

  








   

