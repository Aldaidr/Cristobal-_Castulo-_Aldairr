<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Arbol genealogico</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>

<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

---

<div>

---

## Introducción

El documento presenta la construcción de una pequeña base de conocimiento que describe atributos generales de varios individuos utilizando dos lenguajes pertenecientes a paradigmas distintos:

- **LISP** → lenguaje simbólico orientado al procesamiento de listas.  
- **Prolog** → lenguaje declarativo especializado en la representación de conocimiento y razonamiento lógico.

En ambas implementaciones se registran características como el nombre, apellidos, estatura, complexión, tipo de cabello, color de ojos y tonalidad de piel.  
El propósito es mostrar cómo la misma información puede representarse desde perspectivas muy diferentes según el paradigma de programación.

---

## Código en Lisp

### Definición de la base de datos

En Lisp se emplea `defparameter` para almacenar la base de datos dentro de la variable global `personas`.  
Cada elemento es una lista que contiene el nombre de la persona seguido de sus atributos.

```lisp
(defparameter *personas* '(
  (Leonardo
   (apellidos (Soto Ramirez))
   (altura (alto))
   (complexion (delgado))
   (ojos (verdes))
   (cabello (castaño))
   (color_piel (claro)))

  (Daniela
   (apellidos (Gomez Rivera))
   (altura (baja))
   (complexion (atlética))
   (ojos (miel))
   (cabello (negro))
   (color_piel (morena)))

  (Bruno
   (apellidos (Perez Luna))
   (altura (mediano))
   (complexion (robusto))
   (ojos (oscuros))
   (cabello (negro))
   (color_piel (trigueño)))
))

```

formato general de cada nodo
```lisp

(Nombre
  (apellidos (...))
  (altura (...))
  (complexion (...))
  (ojos (...))
  (cabello (...))
  (color_piel (...)))
```

Ejemplo:
```lisp
(Arianna
 (apellidos (Lopez Aguilar))
 (altura (mediana))
 (complexion (esbelta))
 (ojos (azules))
 (cabello (rubio))
 (color_piel (clara)))
```

### Definición de hechos
En Prolog, cada característica se representa como un hecho independiente, utilizando predicados para cada atributo.

```prolog
apellidos(leonardo, [soto, ramirez]).
altura(leonardo, alto).
complexion(leonardo, delgado).
ojos(leonardo, verdes).
cabello(leonardo, castanio).
color_piel(leonardo, claro).

apellidos(daniela, [gomez, rivera]).
altura(daniela, baja).
complexion(daniela, atletica).
ojos(daniela, miel).
cabello(daniela, negro).
color_piel(daniela, morena).

apellidos(bruno, [perez, luna]).
altura(bruno, mediano).
complexion(bruno, robusto).
ojos(bruno, oscuros).
cabello(bruno, negro).
color_piel(bruno, trigueno).
```

### Clasificacion por genero 
```prolog
male(leonardo).
male(bruno).
female(daniela).
female(arianna).

```

### Estructura general

Cada persona se define mediante hechos de este estilo:

```prolog
atributo(persona, valor).
```

### Consulta de ejemplo

```prolog

?- color_piel(Persona, morena).
Persona = daniela ;
false.
```