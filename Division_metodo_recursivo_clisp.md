<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3></h3>Division de metodo recursivo clisp

<h3>Ingeniería en Sistemas Computacionales</h3>

<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

---

<div align="center"> 
<h2>Introduccion  
</h2>
</div>

<div align="justify">
<p>
El propósito de esta práctica es explorar el uso de la recursión para calcular una división mediante un proceso repetitivo de restas. El algoritmo opera restando sucesivamente el divisor del dividendo hasta que el valor restante sea menor que el divisor, momento en el cual se detiene y se presenta el resultado al usuario. Esta metodología permite comprender cómo se puede implementar la división de forma iterativa a través de funciones recursivas.
</p>
</div>

<div align="center">
<h2>Desarrollo  </h2>
</div>

<div align="justify">
<p>
En este programa desarrollado en Common Lisp se emplea la recursión para efectuar una división entera, sin considerar los decimales. El usuario ingresa un dividendo y un divisor, y la función recursiva se encarga de restar repetidamente el divisor del dividendo hasta que el valor restante sea menor que el divisor. Cada resta se contabiliza como una unidad en el resultado, obteniéndose así el cociente entero de la operación.
</p>

</div>

```lisp

(defun division-recursiva (dividendo divisor &optional (cociente 0))
  (if (< dividendo divisor)
      cociente
      (division-recursiva (- dividendo divisor) divisor (+ cociente 1))))

(defun inicio ()
  (format t "Ingrese el divisor: ")
  (let ((divisor (read)))
    (format t "Ingrese el dividendo: ")
    (let ((dividendo (read)))
      (format t "El resultado de la division es: ~a"
              (division-recursiva dividendo divisor)))))


(inicio)













```
