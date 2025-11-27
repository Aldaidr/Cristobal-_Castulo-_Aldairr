<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Funciones definidas con defun lisp</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>

<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

---
````markdown
(defun calcular-sueldo (tiempo)
  (let ((sueldo-base 40000))
    (cond ((> tiempo 10) (* sueldo-base 1.10))  ; +10%
          ((and (> tiempo 5) (<= tiempo 10)) (* sueldo-base 1.07)) ; +7%
          ((and (> tiempo 3) (<= tiempo 5)) (* sueldo-base 1.05))  ; +5%
          ((<= tiempo 3) (* sueldo-base 1.03))))) ; +3%

(defun saludar(nombre)
        ( cond ((eq nombre 'juan)'(Hola juan))
                ((eq nombre 'maria)'(Hola maria))
                ((eq nombre 'lupe)'(Hola lupe))
                (t '(No se quien seas))



        )
)










