
<center>
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Multiplicación con metodo recursivo clisp</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>


<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</center>

---

<h2>Introduccion  </h2>

<p align="justify">
En esta práctica se busca comprender y aplicar el método recursivo 
como alternativa para realizar una multiplicación mediante sumas
sucesivas.El propósito es observar cómo, a través de llamadas
recursivas,se puede alcanzar el resultado final e imprimirlo al
usuario una vez concluido el proceso.
</p>

<h2>Desarrollo</h2>
<p>El código implementa una función recursiva en Lisp que simula el proceso de multiplicación mediante sumas repetidas. Tras solicitar al usuario dos números, la función recursiva ejecuta una suma acumulativa del primer número, disminuyendo el segundo parámetro en cada llamada, hasta llegar a la condición base. El resultado final corresponde al producto de ambos valores.
</p>

(defun potencia-rapida (base exponente)
  (cond
    ((= exponente 0) 1) ; caso base
    ((evenp exponente)  ; si es par
     (let ((mitad (potencia-rapida base (/ exponente 2))))
       (* mitad mitad)))
    (t                  ; si es impar
     (* base (potencia-rapida base (- exponente 1))))))

(defun inicio ()
  (format t "Ingrese la base: ")
  (let ((base (read)))
    (format t "Ingrese el exponente: ")
    (let ((exponente (read)))
      (let ((resultado (potencia-rapida base exponente)))
        (format t "El resultado de la potencia es: ~a" resultado)))))
        
(inicio)








