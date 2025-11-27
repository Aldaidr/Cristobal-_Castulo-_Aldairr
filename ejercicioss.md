# INSTITUTO TECNOLÓGICO DE MORELIA  

### Programación Lógica y Funcional

## Ejercicios cdr y car

### Ingeniería en Sistemas Computacionales


**Aldair Cristobal Castulo**


**Profesor:** Alcaraz Chavez Jesus Eduardo

### Ejercicio 1 Problemas (car y cdr)

----

### Ejercicio 1
Dada una lista de pares clave-valor, usar ‘assoc‘ para obtener el valor de la
clave ‘’edad‘. Lista de ejemplo:
(setq persona '((nombre . "Ana") (edad . 23) (ciudad . "Morelia")))
Pregunta: ¿cómo obtener la edad con ‘assoc‘, ‘cdr‘ y ‘car‘?

```lisp 
(setq persona '((nombre . "Ana") (edad . 23) (ciudad . "Morelia")))
(cdr (assoc 'edad persona)) ; => 23
```

### Ejercicio 2
Usar ‘if‘ para escribir una función que diga si el primer elemento de una lista
es un número positivo o no. Ejemplo:
(mi-funcion '(5 3 2)) ; => "positivo"
(mi-funcion '(-2 1 4)) ; => "no positivo"

```lisp 
(defun positvio (lista)
  (if (> (car lista) 0)
      "positivo"
      "no positivo"))

```

### Ejercicio 3
Definir una función que recorra una lista de números con ‘mapcar‘ y devuelva
una nueva lista que contenga solo el doble de los números pares. Restricción:
usar ‘if‘ dentro de ‘mapcar‘.

``` lisp 
(defun doble-pares (lista)
  (mapcar (lambda (x) 
            (if (evenp x) 
                (* 2 x) 
                x)) 
          lista))
```


### Ejercicio 4
Usar ‘cond‘ para hacer una función que reciba un símbolo que puede ser
‘rojo‘, ‘azul‘ o ‘verde‘ y regrese un mensaje:
• rojo → "Color cálido"
• azul → "Color frío"
• verde → "Color neutro"
• cualquier otro → "Color desconocido"


```lisp
(defun clasificar-color (color)
  (cond
    ((eq color 'rojo) "Color cálido")
    ((eq color 'azul) "Color frío")
    ((eq color 'verde) "Color neutro")
    (t "Color desconocido")))
```

### Ejercicio 5
Escribir una función que use ‘case‘ para clasificar un día de la semana (‘lunes‘,
‘martes‘, . . . ):
• lunes a viernes → "día laboral"
• sábado, domingo → "fin de semana"

```lisp 
(defun clasificar-dia (dia)
  (case dia
    ((lunes martes miercoles jueves viernes) "día laboral")
    ((sabado domingo) "fin de semana")))
```

### Ejercicio 6
Definir una función que reciba una lista y con ‘when‘ imprima el primer
elemento si la lista no está vacía.

```lisp 
(defun imprimir-primer-elemento (lista)
  (when lista
    (print (car lista))))
```

### Ejercicio 7
Definir una función que reciba una lista y con ‘unless‘ imprima "lista vacía"
cuando la lista no tenga elementos.
```lisp 
(defun verificar-lista-vacia (lista)
  (unless lista
    (print "lista vacía")))
```

### Ejercicio 8
Dada una lista de listas, usar ‘mapcar‘, ‘car‘ y ‘cdr‘ para obtener una nueva
lista con los primeros elementos de cada sublista. Ejemplo:
(mi-funcion '((1 2) (3 4) (5 6))) ; => (1 3 5)

```lisp 
(defun primeros-elementos (lista)
  (mapcar 'car lista))

```


### Ejercicio 9
Dada una lista de asociación:
(setq alumnos '((juan . 8) (maria . 10) (ana . 9)))
Escribir una función que, dado un nombre, devuelva "Aprobado" si la calificación es >= 8, o "Reprobado" en caso contrario. Usar ‘assoc‘, ‘cdr‘ y
‘if‘.

```lisp 
(setq alumnos '((juan . 8) (maria . 10) (ana . 9)))

(defun verificar-aprobacion (nombre)
  (let ((calificacion (cdr (assoc nombre alumnos))))
    (if (>= calificacion 8)
        "Aprobado"
        "Reprobado")))
```



### Ejercicio 10
Definir una función que use ‘cond‘ para evaluar una lista de números y devolver:
• "vacía" si no hay elementos,
• "un solo elemento" si la lista tiene uno,
• "larga" si tiene más de uno


```lisp 
(defun evaluar-lista (lista)
  (cond
    ((null lista) "vacía")
    ((null (cdr lista)) "un solo elemento")
    (t "larga")))
```
</div> 