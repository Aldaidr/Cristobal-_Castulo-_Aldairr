
<center>
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Descomposicion de numeros</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>


<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</center>

---

<center><h2>Introduccion  </h2></center>

<p align="justify">
La descomposición de unidades representa uno de los retos más interesantes dentro del estudio de las matemáticas discretas y la computación. Este problema busca determinar todas las combinaciones posibles de valores que, al sumarse, generen un número específico. Su relevancia se extiende a múltiples áreas, como la optimización, la teoría combinatoria y la distribución eficiente de recursos.

Dentro del paradigma de la programación funcional, el uso de la recursión en CLISP se presenta como una estrategia elegante y eficaz para abordar este tipo de problemas. Gracias a su estructura simbólica y a su enfoque basado en funciones, LISP permite desarrollar soluciones precisas y compactas, demostrando por qué sigue siendo un lenguaje clave en el ámbito académico y en la exploración de algoritmos lógicos y matemáticos
</p>

<center><h2>Desarrollo</h2></center>
<p align="justify">
En este programa se implementa un método recursivo que permite descomponer un número ingresado por el usuario. Para ello, se utiliza una lista auxiliar que almacena los valores que forman parte del proceso de descomposición. A través de condiciones lógicas, el algoritmo compara el valor actual de la lista con el número que se desea descomponer, realizando este procedimiento de forma iterativa mediante un ciclo. De esta manera, se obtienen todas las posibles combinaciones que conforman el número inicial.
</p>

```lisp

(defun descomponer (n &optional (inicio 1) (actual '()))
  (cond
    ((= n 0) (list (reverse actual)))
    ((< n inicio) '())
    (t
     (mapcan
      (lambda (x)
        (descomponer (- n x) x (cons x actual)))
      (remove-if
       (lambda (x) (> x n))
       (number-sequence inicio n))))))











