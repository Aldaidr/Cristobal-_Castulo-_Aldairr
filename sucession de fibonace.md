## Sucessión de Fibonacc
<div>
La sucesión de Fibonacci es una serie infinita de números naturales que comienza con 0 y 1, y en la que cada término siguiente se obtiene sumando los dos anteriores.
</div>
<div>
La sucesión fue descrita en 1202 por Leonardo de Pisa, conocido como Fibonacci, en su libro Liber Abaci. Allí planteó un problema sobre la reproducción de conejos y, al resolverlo, obtuvo la serie.
Con el tiempo se descubrió que aparece en fenómenos naturales, estructuras matemáticas y algoritmos de programación.
</div>
<div>
En programación lógica y funcional, Fibonacci es un ejemplo clásico porque:
Permite aplicar recursión, concepto central en estas áreas.
Se relaciona con eficiencia algorítmica (existen implementaciones recursivas simples y optimizadas).
Muestra cómo la matemática se convierte en código declarativo (describiendo qué es Fibonacci y no cómo calcularlo paso a paso imperativamente).
</div>

```lisp
(defun fibonacci-iter (n)
  "Devuelve el n-ésimo número de Fibonacci usando recursión de cola."
  (labels ((aux (a b count)
             (if (= count 0)
                 a
                 (aux b (+ a b) (- count 1)))))
    (aux 0 1 n)))

(defun mostrar-fibonacci (n)
  "Imprime los primeros n números de Fibonacci."
  (dotimes (i n)
    (format t "F(~a) = ~a~%" i (fibonacci-iter i))))

(defun main ()
  (format t "Introduce la cantidad de números de Fibonacci a mostrar: ")
  (let ((n (read)))
    (if (and (integerp n) (>= n 0))
        (progn
          (format t "~%Serie de Fibonacci (~a números):~%~%" n)
          (mostrar-fibonacci n))
        (format t "~%Error: Entrada inválida. Debes escribir un número entero no negativo.~%"))))

(main)
