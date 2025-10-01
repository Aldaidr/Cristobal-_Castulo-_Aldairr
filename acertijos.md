---

# INSTITUTO TECNOLÓGICO DE MORELIA  

### Programación Lógica y Funcional

## Acertijos

### Ingeniería en Sistemas Computacionales


**Aldair Cristobal Castulo**


**Profesor:** Alcaraz Chavez Jesus Eduardo

### Ejercicio 1

---
```text
Cuatro personas necesitan cruzar un puente de noche con un sola
linterna. El puente es frágil y solo puede soportar a dos personas a
la vez. Cada persona tarda diferentes tiempos en cruzar (1, 2 5 y 10
minutos).  Cuando dos personas cruzan, lo hacen al ritmo del más lento
¿Cómo pueden todos cruzar el puente en 17 minutos?


Estrategia Óptima (17 minutos)

1. **Cruzan 1 y 2** → tiempo = 2  
   Estado: izquierda {5,10} — derecha {1,2}  
   Acumulado = 2

2. **Regresa 1** → tiempo = 1  
   Estado: izquierda {1,5,10} — derecha {2}  
   Acumulado = 3

3. **Cruzan 5 y 10** → tiempo = 10  
   Estado: izquierda {1} — derecha {2,5,10}  
   Acumulado = 13

4. **Regresa 2** → tiempo = 2  
   Estado: izquierda {1,2} — derecha {5,10}  
   Acumulado = 15

5. **Cruzan 1 y 2** → tiempo = 2  
   Estado: izquierda {} — derecha {1,2,5,10}  
   Acumulado = 17

Resultado final: todos cruzan en **17 minutos**.

Justificación de Optimalidad
- Si los dos más lentos cruzan por separado, el tiempo mínimo sería ≥ 19.  
- La única forma de reducir es que crucen juntos (5 y 10).  
- Usando a los más rápidos (1 y 2) para regresar la linterna, se obtiene el mínimo posible.  
- Comparando estrategias, ninguna puede dar menos de 17 minutos.  

```
---

### Ejercicio 2
---
```text

En una calle hay cinco casas, cada una de un color distinto.  En cada
casa vive una persona de distinta nacionalidad.  Cada dueño bebe un
único tipo de bebida, fuma una sola marca de cigarrillos y tiene una
mascota diferente a sus vecinos.  A partir de las 15 pistas
presentadas a continuación, la consigna que hay que responder es:
"¿Quién es el dueño del pez?".


1. El británico vive en la casa roja.  
2. El sueco tiene un perro como mascota.  
3. El danés toma té.  
4. El noruego vive en la primera casa.  
5. El alemán fuma Prince.  
6. La casa verde está inmediatamente a la izquierda de la blanca.  
7. El dueño de la casa verde bebe café.  
8. El propietario que fuma Pall Mall cría pájaros.  
9. El dueño de la casa amarilla fuma Dunhill.  
10. El hombre que vive en la casa del centro bebe leche.  
11. El vecino que fuma Blends vive al lado del que tiene un gato.  
12. El hombre que tiene un caballo vive al lado del que fuma Dunhill.  
13. El propietario que fuma Bluemaster toma cerveza.  
14. El vecino que fuma Blends vive al lado del que toma agua.  
15. El noruego vive al lado de la casa azul. 

Paso 1: Nacionalidades y posiciones iniciales
- Pista (4): El **noruego** vive en la **primera casa**.  
- Pista (10): El del **centro (3ª casa)** bebe **leche**.  

Paso 2: Colores de las casas
- Pista (9): La **primera casa** es **amarilla** y allí se fuma **Dunhill**.  
- Pista (15): El **noruego** (1ª casa) vive junto a la **azul** (→ la 2ª casa es azul).  
- Pista (6): La **verde** está a la izquierda de la **blanca** → (casas 4 y 5).  
- Pista (7): El dueño de la verde toma **café** → casa 4 = verde, café; casa 5 = blanca.  
- Pista (1): El **británico** vive en la casa **roja** → queda la 3ª casa.  

Paso 3: Bebidas
- Casa 3 (roja, británico) → ya sabemos que bebe **leche**.  
- Casa 4 (verde) → café.  
- Pista (3): El **danés** toma **té** → única opción = casa 2.  
- Pista (13): Quien fuma **Bluemaster** toma **cerveza**. Más adelante lo ubicamos.  

Paso 4: Mascotas y cigarros
- Pista (2): El **sueco** tiene **perro** → aún libre, será casa 5.  
- Pista (8): Quien fuma **Pall Mall** cría **pájaros**.  
- Pista (5): El **alemán** fuma **Prince** → queda en casa 4.  
- Casa 1 ya fuma Dunhill.  
- Pista (12): El hombre con **caballo** vive al lado de quien fuma **Dunhill** → Casa 2 tiene el caballo.  
- Pista (11): Quien fuma **Blends** vive al lado de quien tiene **gato**.  
- Pista (14): Quien fuma **Blends** vive al lado de quien toma **agua**.  

Paso 5: Distribución final
- Casa 1: Noruego, Amarilla, Agua, Dunhill, Gato.  
- Casa 2: Danés, Azul, Té, Blends, Caballo.  
- Casa 3: Británico, Roja, Leche, Pall Mall, Pájaros.  
- Casa 4: Alemán, Verde, Café, Prince, **Pez**.  
- Casa 5: Sueco, Blanca, Cerveza, Bluemaster, Perro.  

 Respuesta
El **alemán** (casa verde, nº4) es el dueño del **pez**.

```


