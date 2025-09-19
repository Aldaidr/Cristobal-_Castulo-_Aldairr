## Ejercicios Clisp
## Enunciado

Un trabajador cobra **40,000 euros anuales**. Calcular el sueldo que le corresponde según los años trabajados y las reglas:

* 10 años -> aumento 10%
* 6..10 años -> aumento 7%
* 4..5 años -> aumento 5%
* 0..3 años -> aumento 3%
---

## Código

```
```(setq *sueldo-base* 40000)
(defun calcular-sueldo (anios)
  (let ((sueldo *sueldo-base*))
    (cond
      ((> anios 10) (+ sueldo (* sueldo 0.10)))
      ((>= anios 6) (+ sueldo (* sueldo 0.07)))
      ((>= anios 4) (+ sueldo (* sueldo 0.05)))
      (t (+ sueldo (* sueldo 0.03)))))))


---
## Explicacion 
  Definimos el sueldo base
  (setq *sueldo-base* 40000)

  Función que calcula el aumento según los años
  (defun calcular-sueldo (anios)
  (let ((sueldo *sueldo-base*))
    (cond
      Más de 10 años → 10%
      ((> anios 10) (+ sueldo (* sueldo 0.10)))

      Entre 6 y 10 años → 7%
      ((>= anios 6) (+ sueldo (* sueldo 0.07)))

      Entre 4 y 5 años → 5%
      ((>= anios 4) (+ sueldo (* sueldo 0.05)))

      Entre 0 y 3 años → 3%
      (t (+ sueldo (* sueldo 0.03)))))))


---

## Ejecucion 

```lisp
(calcular-sueldo 12)   ; => 44000.0  (10% de 40000)
(calcular-sueldo 7)    ; => 42800.0  (7% de 40000)
(calcular-sueldo 4)    ; => 42000.0  (5% de 40000)
(calcular-sueldo 2)    ; => 41200.0  (3% de 40000)
```

---
 ## Enunciado 2
2.- Hacer un algortimo que tome el peso en libras de una cantidad de
ropa a lavar en una lavadora y nos devuelva el nivel dependiendo del
peso; además nos informe la cantidad de litros de agua que
necesitamos. Se sabe que con más de 30 libras la lavadora no funcionara
ya que es demasiado peso. Si la ropa pesa 22 ó más libras, el nivel será
de máximo; si pesa 15 ó más nivel será de alto; si pesa 8 ó más será un
nivel medio o de lo contrario el nivel será minimo

## Código
---
```
(defun nivel-lavadora (peso)
  (cond
    ((> peso 30)
     (format t "Error: La lavadora no puede con más de 30 libras.~%"))
    ((>= peso 22)
     (format t "Nivel: Máximo~%Agua: 40 litros~%"))
    ((>= peso 15)
     (format t "Nivel: Alto~%Agua: 30 litros~%"))
    ((>= peso 8)
     (format t "Nivel: Medio~%Agua: 20 litros~%"))
    (t
     (format t "Nivel: Mínimo~%Agua: 10 litros~%"))))
     
---     

## Explicacion 
 ;; Definimos la función principal que recibe el peso en libras
(defun nivel-lavadora (peso)

  ;; Usamos cond para evaluar las condiciones por orden
  (cond

    ;; 1. Si el peso es mayor a 30, mostramos un error
    ((> peso 30)
     ;; format t imprime en pantalla (como printf en C)
     (format t "Error: La lavadora no puede con más de 30 libras.~%"))

    ;; 2. Si el peso es mayor o igual a 22 → nivel máximo
    ((>= peso 22)
     (format t "Nivel: Máximo~%Agua: 40 litros~%"))

    ;; 3. Si el peso es mayor o igual a 15 → nivel alto
    ((>= peso 15)
     (format t "Nivel: Alto~%Agua: 30 litros~%"))

    ;; 4. Si el peso es mayor o igual a 8 → nivel medio
    ((>= peso 8)
     (format t "Nivel: Medio~%Agua: 20 litros~%"))

    ;; 5. Si no cumple ninguno de los anteriores → nivel mínimo
    (t
     (format t "Nivel: Mínimo~%Agua: 10 litros~%")))))
     
##Ejemplo de uso    
  (nivel-lavadora 5)
  ;; → Nivel: Mínimo
  ;;   Agua: 10 litros

  (nivel-lavadora 12)
  ;; → Nivel: Medio
  ;;   Agua: 20 litros

  (nivel-lavadora 18)
  ;; → Nivel: Alto
  ;;   Agua: 30 litros

  (nivel-lavadora 25)
  ;; → Nivel: Máximo
  ;;   Agua: 40 litros

  (nivel-lavadora 35)
  ;; → Error: La lavadora no puede con más de 30 libras.

 

```
## Enunciado 3
3-. Invitado a una gran cantidad de personas. Pero también ha decidido
algunas reglas: Que todas las personas con edades mayores a los quince
años, sólo pueden entrar si traen regalos; que jóvenes con los quince
años cumplidos entra totalmente gratis pero los de menos de quince años
no pueden entrar a la fiesta. Hacer un algoritmo donde se tome la edad
de una persona y que requisito de los anteriores le toca cumplir si
quiere entrar.

## Código
```
(defun entrada-fiesta (edad regalo)
  (cond
    ((< edad 15)
     (format t "No puede entrar a la fiesta.~%"))
    ((= edad 15)
     (format t "Puede entrar gratis.~%"))
    ((> edad 15)
     (if regalo
         (format t "Puede entrar con su regalo.~%")
         (format t "No puede entrar sin regalo.~%")))))
         
##Explicacion
  ;; Definimos la función entrada-fiesta
  ;; Recibe dos parámetros:
  ;;   edad   → número (años de la persona)
  ;;   regalo → booleano (T si trae regalo, NIL si no)
  (defun entrada-fiesta (edad regalo)

  ;; Usamos cond para evaluar las condiciones por orden
  (cond
    ;; 1. Si la edad es menor de 15
    ((< edad 15)
     (format t "No puede entrar a la fiesta.~%"))

    ;; 2. Si la edad es exactamente 15
    ((= edad 15)
     (format t "Puede entrar gratis.~%"))

    ;; 3. Si la edad es mayor de 15
    ((> edad 15)
     ;; Aquí usamos if porque depende de si trae regalo
     (if regalo
         (format t "Puede entrar con su regalo.~%")
         (format t "No puede entrar sin regalo.~%")))))
         
##Ejemplo de uso
(entrada-fiesta 12 t)
;; → No puede entrar a la fiesta.

(entrada-fiesta 15 nil)
;; → Puede entrar gratis.

(entrada-fiesta 20 nil)
;; → No puede entrar sin regalo.

(entrada-fiesta 25 t)
;; → Puede entrar con su regalo.



```

