# Tarea 2 - Ejercicios Unidad 1 📝

# Aprendiendo a programar como una tortuga 🐢

<img width="360" height="360" alt="image" src="https://github.com/user-attachments/assets/67639cc5-8a39-4c77-b2a1-b4ac6c2cd217" />

## Ejemplo base para iniciar
### Código Import Turtle

Con este importamos la librería Python llamada Turtle, que permite crear gráficos y dibujos en una ventana virtual.

```Python
import turtle

t = turtle.Turtle()   # Crea una tortuga
t.forward(100)        # Avanza 100 unidades
turtle.done()         # Mantiene la ventana abierta
```
Como salida a este código tenemos la siguiente imágen

<img width="635" height="407" alt="image" src="https://github.com/user-attachments/assets/858f32a5-e568-4e39-af09-71b2890eda93" />

## Reto 1: Simular el comportamiento de la tortuga usando solo print() e input().

Intenta recrear el movimiento de la tortuga únicamente con texto, usando funciones, print() y input() para pedir valores al usuario.

### Solución presentada

```Python
# Entrada
import turtle

t = turtle.Turtle()   # Crea una tortuga
pasos = int(input("¿Cuántos pasos quieres dar?: "))
print("-" * pasos,">")
print("Creando una tortuga simulada que da", pasos, "pasos")
t.forward(100)        # Avanza 100 unidades
turtle.done()         # Mantiene la ventana abierta
```
```
# Salida

¿Cuántos pasos quieres dar?: 50
-------------------------------------------------- >
Creando una tortuga simulada que da 50 pasos

```
## Reto 2: Tortuga bajando

Crea el rastro de una tortuga moviéndose hacia abajo usando únicamente print() e input().

### Solución presentada

```Python
# Entrada 
import turtle

t = turtle.Turtle()   # Crea una tortuga
pasos = int(input("¿Cuántos pasos quieres dar?: ")) # Usuario indica cantidad de pasos
print("Creando una tortuga simulada que da", pasos, "pasos hacia abajo") # Imprime cantidad de pasos y hacia adonde
for i in range(pasos):
    print("     |")
print("     ↓")

t.right(90)        # Avanza hacia abajo
turtle.done()         # Mantiene la ventana abierta

```

```Python
# Salida
Creando una tortuga simulada que da 5 pasos hacia abajo
     |
     |
     |
     |
     |
     ↓
```




