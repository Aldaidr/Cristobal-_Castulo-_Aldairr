<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Explicación Código ELIZA en Prolog</title>
</head>
<body>

<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA</h2>
<h3>Programación Lógica y Funcional</h3>
<h3>Sistema Experto Proyecto</h3>
<h3>Ingeniería en Sistemas Computacionales</h3>
<h3>Aldair Cristobal Castulo</h3>
<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

<hr>

<div align="center">
<h3>Introducción</h3>
<p>El presente documento explica el funcionamiento del sistema experto ELIZA desarrollado en Prolog, el cual integra una base de conocimiento sobre enfermedades, síntomas, tratamientos, médicos y centros de atención, permitiendo realizar diagnósticos automáticos y consultas sobre relaciones familiares y jugadores del Club América. ELIZA simula interacción con el usuario y utiliza reglas lógicas para inferir información.</p>
</div>


<hr>

<ul>
<li>Diagnóstico médico basado en síntomas.</li>
<li>Consultas de relaciones familiares (padre, madre, abuelo).</li>
<li>Un juego tipo Akinator para adivinar jugadores del Club América.</li>
<li>Simulación de interacción con el usuario, procesamiento de reglas lógicas y generación de reportes.</li>
</ul>
<p>Se explican los predicados, reglas de inferencia, base de conocimiento y ejemplos de consultas para demostrar el funcionamiento del sistema.</p>
</div>

<hr>

<div align="center">
<h3>Base de Conocimiento</h3>
<p>La base de conocimiento incluye:</p>
<ul>
<li>Enfermedades y sus síntomas.</li>
<li>Tratamientos y medicamentos asociados.</li>
<li>Médicos especializados y centros médicos.</li>
<li>Jugadores del Club América y árbol genealógico.</li>
<li>Reglas para diagnóstico exclusivo, por probabilidad, preventivo, y combinación de tratamientos.</li>
<li>Relaciones familiares: padre, madre, abuelo.</li>
<li>Detección de síntomas contradictorios.</li>
</ul>
</div>

<hr>

<div align="center">
<h3>Predicados principales en Prolog</h3>
<pre>
% --- Enfermedades ---
enfermedad(covid).
enfermedad(sinusitis).
enfermedad(bronquitis).
enfermedad(otitis).
enfermedad(gastritis).

% --- Síntomas ---
sintoma(fiebre).
sintoma(tos).
sintoma(dolor_garganta).
sintoma(dificultad_respirar).

% --- Relación enfermedad ↔ síntomas ---
tiene_sintoma(covid, fiebre).
tiene_sintoma(covid, tos).
tiene_sintoma(covid, dificultad_respirar).

% --- Tratamientos ---
tratamiento(covid, reposo).
tratamiento(covid, paracetamol).
</pre>
</div>

<hr>

<div align="center">
<h3>Jugadores del Club América y Árbol Genealógico</h3>
<pre>
jugador(henry_martin).
jugador(luis_malagon).
jugador(alvaro_fidalgo).
jugador(diego_valdes).
jugador(julian_quinones).
jugador(jonathan_dos_santos).
jugador(alex_zendejas).
jugador(brian_rodriguez).
jugador(sebastian_caceres).
jugador(igor_lichnovsky).
jugador(kevin_alvarez).

% Árbol familiar de ejemplo
padre(juan, alvaro_fidalgo).
madre(maria, alvaro_fidalgo).
abuelo(jorge, alvaro_fidalgo).

padre(ricardo, diego_valdes).
madre(laura, diego_valdes).
abuelo(carlos, diego_valdes).
</pre>
</div>

<hr>

<div align="center">
<h3>Diagnósticos y Reglas</h3>
<pre>
% Diagnóstico exclusivo
diagnostico_exclusivo(Paciente, Enfermedad) :-
  tiene_sintoma(Paciente, Sintoma),
  tiene_sintoma(Enfermedad, Sintoma),
  \+ (tiene_sintoma(Otra, Sintoma), Otra \= Enfermedad).

% Diagnóstico por probabilidad
probabilidad(Paciente, Enfermedad, Porcentaje) :-
  findall(S, tiene_sintoma(Enfermedad, S), ListaSintomas),
  findall(S, (tiene_sintoma(Paciente, S), member(S, ListaSintomas)), Confirmados),
  length(ListaSintomas, Totales),
  length(Confirmados, Cont),
  Porcentaje is (Cont / Totales) * 100.

% Diagnóstico preventivo
diagnostico_preventivo(Paciente, Enfermedad) :-
  findall(S, tiene_sintoma(Enfermedad, S), Sintomas),
  findall(S, (tiene_sintoma(Paciente, S), member(S, Sintomas)), Confirmados),
  Confirmados \= [],
  length(Confirmados, Lc),
  length(Sintomas, Lt),
  Lc < Lt.
</pre>
</div>

<hr>

<div align="center">
<h3>Ejemplos de Consultas</h3>
<pre>
?- tiene_sintoma(alvaro_fidalgo, fiebre).
?- diagnostico_exclusivo(alvaro_fidalgo, covid).
?- probabilidad(alvaro_fidalgo, covid, P).
?- diagnostico_preventivo(alvaro_fidalgo, covid).
?- padre(juan, alvaro_fidalgo).
?- jugador(alvaro_fidalgo).
</pre>
</div>

<hr>

<div align="center">
<h3>Funcionamiento Interno</h3>
<p>ELIZA funciona mediante un ciclo de interacción con el usuario:</p>
<ul>
<li>El usuario ingresa síntomas con el comando <code>tengo(Sintoma)</code>.</li>
<li>ELIZA registra los síntomas y genera un reporte con probabilidades de enfermedades.</li>
<li>Permite jugar al Akinator con <code>quiero_jugar</code>, filtrando jugadores por posición y nacionalidad.</li>
<li>Consulta relaciones familiares usando <code>padre(X,Y)</code>, <code>madre(X,Y)</code> o <code>abuelo(X,Y)</code>.</li>
<li>Si el comando no es reconocido, ELIZA responde con un mensaje de error.</li>
</ul>
</div>

<hr>

<div align="center">
<h3>Base de Conocimiento</h3>
<p>La base de conocimiento contiene:</p>
<ul>
<li>Enfermedades y sus síntomas (ej. fiebre, dolor de cabeza, ictericia)</li>
<li>Tratamientos y medicamentos asociados</li>
<li>Médicos especializados</li>
<li>Centros médicos</li>
<li>Jugadores del Club América y árbol genealógico</li>
<li>Reglas para diagnóstico exclusivo, por probabilidad, preventivo, y combinación de tratamientos</li>
<li>Relaciones familiares: padre, madre, abuelo, etc.</li>
<li>Detección de síntomas contradictorios</li>
</ul>
</div>

<hr>

<div align="center">
<h3>Predicados principales en Prolog</h3>
<pre>
% --- Enfermedades ---
enfermedad(covid).
enfermedad(sinusitis).
enfermedad(bronquitis).
enfermedad(otitis).
enfermedad(gastritis).

% --- Síntomas ---
sintoma(fiebre).
sintoma(tos).
sintoma(dolor_garganta).
sintoma(dificultad_respirar).

% --- Relación enfermedad ↔ síntomas ---
tiene_sintoma(covid, fiebre).
tiene_sintoma(covid, tos).
tiene_sintoma(covid, dificultad_respirar).

% --- Tratamientos ---
tratamiento(covid, reposo).
tratamiento(covid, paracetamol).
</pre>
</div>

<hr>

<div align="center">
<h3>Jugadores del Club América y Árbol Genealógico</h3>
<pre>
jugador(henry_martin).
jugador(luis_malagon).
jugador(alvaro_fidalgo).
jugador(diego_valdes).
jugador(julian_quinones).
jugador(jonathan_dos_santos).
jugador(alex_zendejas).
jugador(brian_rodriguez).
jugador(sebastian_caceres).
jugador(igor_lichnovsky).
jugador(kevin_alvarez).

% Árbol familiar de ejemplo
padre(juan, alvaro_fidalgo).
madre(maria, alvaro_fidalgo).
abuelo(jorge, alvaro_fidalgo).

padre(ricardo, diego_valdes).
madre(laura, diego_valdes).
abuelo(carlos, diego_valdes).
</pre>
</div>


<hr>

<div align="center">
<h3>Diagnósticos y Reglas</h3>
<pre>
% Diagnóstico exclusivo
diagnostico_exclusivo(Paciente, Enfermedad) :-
  tiene_sintoma(Paciente, Sintoma),
  tiene_sintoma(Enfermedad, Sintoma),
  \+ (tiene_sintoma(Otra, Sintoma), Otra \= Enfermedad).

% Diagnóstico por probabilidad
probabilidad(Paciente, Enfermedad, Porcentaje) :-
  findall(S, tiene_sintoma(Enfermedad, S), ListaSintomas),
  findall(S, (tiene_sintoma(Paciente, S), member(S, ListaSintomas)), Confirmados),
  length(ListaSintomas, Totales),
  length(Confirmados, Cont),
  Porcentaje is (Cont / Totales) * 100.

% Diagnóstico preventivo
diagnostico_preventivo(Paciente, Enfermedad) :-
  findall(S, tiene_sintoma(Enfermedad, S), Sintomas),
  findall(S, (tiene_sintoma(Paciente, S), member(S, Sintomas)), Confirmados),
  Confirmados \= [],
  length(Confirmados, Lc),
  length(Sintomas, Lt),
  Lc < Lt.
</pre>
</div>

<hr>

<div align="center">
<h3>Ejemplos de Consultas</h3>
<pre>
?- tiene_sintoma(alvaro_fidalgo, fiebre).
?- diagnostico_exclusivo(alvaro_fidalgo, covid).
?- probabilidad(alvaro_fidalgo, covid, P).
?- diagnostico_preventivo(alvaro_fidalgo, covid).
?- padre(juan, alvaro_fidalgo).
?- jugador(alvaro_fidalgo).
</pre>
</div>

<hr>

### Codigo prolog

```prolog
:- encoding(utf8).

:- dynamic tiene_sintoma/2.
:- dynamic candidatos/1.


eliza :-
    retractall(tiene_sintoma(_,_)),
    retractall(candidatos(_)),
    writeln('Hola, soy ELIZA.'),
    writeln('Comandos disponibles:'),
    writeln('- tengo(sintoma).'),
    writeln('- reporte.'),
    writeln('- quiero_jugar.'),
    writeln('- padre(X,Y). madre(X,Y). abuelo(X,Y).'),
    writeln('- adios.'),
    ciclo.

ciclo :-
    write('|: '),
    read(Entrada),
    procesar(Entrada),
    Entrada \= adios,
    ciclo.
ciclo :- writeln('Adios.').

procesar(adios) :- !.

procesar(quiero_jugar) :-
    iniciar_akinator, !.

procesar(tengo(S)) :-
    assertz(tiene_sintoma(paciente, S)),
    writeln(['Sintoma registrado:', S]), !.

procesar(reporte) :-
    reporte(paciente), !.

procesar(X) :-
    call(X),
    writeln('Consulta realizada.'), !.

procesar(_) :-
    writeln('No te entendi.').

% ---- Base jugadores ----
jugador(henry_martin, delantero, mexicano).
jugador(luis_malagon, portero, mexicano).
jugador(alvaro_fidalgo, mediocampista, extranjero).
jugador(diego_valdes, mediocampista, extranjero).
jugador(julian_quinones, delantero, extranjero).
jugador(jonathan_dos_santos, mediocampista, mexicano).
jugador(alex_zendejas, extremo, mexicano).
jugador(brian_rodriguez, extremo, extranjero).
jugador(sebastian_caceres, defensa, extranjero).
jugador(igor_lichnovsky, defensa, extranjero).
jugador(kevin_alvarez, defensa, mexicano).

iniciar_akinator :-
    findall(N, jugador(N,_,_), Lista),
    assertz(candidatos(Lista)),
    writeln('Piensa en un jugador del Club America.'),
    preguntar_posicion.

preguntar_posicion :-
    writeln('¿Es delantero? (si/no)'),
    read(R),
    filtrar_posicion(delantero, R),
    siguiente_pregunta.

siguiente_pregunta :-
    candidatos([Unico]),
    writeln(['Estoy pensando en:', Unico]), !.

siguiente_pregunta :-
    writeln('¿Es mexicano? (si/no)'),
    read(R),
    filtrar_nacionalidad(mexicano, R),
    finalizar_akinator.

finalizar_akinator :-
    candidatos([Unico]),
    writeln(['Estoy pensando en:', Unico]), !.

finalizar_akinator :-
    candidatos(Lista),
    writeln(['No pude estar 100% segura, opciones:', Lista]).

filtrar_posicion(Pos, si) :-
    candidatos(L),
    include(es_pos(Pos), L, NL),
    retractall(candidatos(_)),
    assertz(candidatos(NL)).
filtrar_posicion(_, no).

filtrar_nacionalidad(Nac, si) :-
    candidatos(L),
    include(es_nacional(Nac), L, NL),
    retractall(candidatos(_)),
    assertz(candidatos(NL)).
filtrar_nacionalidad(_, no).

es_pos(P, J) :- jugador(J, P, _).
es_nacional(N, J) :- jugador(J, _, N).

enfermedad(anemia).
enfermedad(apendicitis).
enfermedad(covid).

tiene_sintoma_enfermedad(cansancio, anemia).
tiene_sintoma_enfermedad(palidez, anemia).

tiene_sintoma_enfermedad(dolor_abdominal, apendicitis).
tiene_sintoma_enfermedad(fiebre, apendicitis).

tiene_sintoma_enfermedad(fiebre, covid).
tiene_sintoma_enfermedad(tos_seca, covid).

tratamiento(anemia, hierro).
tratamiento(apendicitis, cirugia).
tratamiento(covid, reposo).

diagnostico_basico(P,E) :-
    enfermedad(E),
    forall(
        tiene_sintoma(P,S),
        tiene_sintoma_enfermedad(S,E)
    ).

probabilidad(P,E,Porc) :-
    findall(S,tiene_sintoma_enfermedad(S,E),T),
    findall(S,(tiene_sintoma(P,S),tiene_sintoma_enfermedad(S,E)),C),
    length(T,LT), length(C,LC),
    LT>0, Porc is LC*100//LT.

reporte(P) :-
    writeln('--- REPORTE ---'),
    findall(S,tiene_sintoma(P,S),Sx),
    writeln(['Sintomas:',Sx]),
    forall(enfermedad(E),
        (probabilidad(P,E,Pc),
         writeln([E,Pc,'%']))
    ).

padre(juan,carlos).
padre(carlos,pedro).
madre(maria,carlos).
madre(ana,pedro).

abuelo(X,Y) :- padre(X,Z), padre(Z,Y).
abuelo(X,Y) :- padre(X,Z), madre(Z,Y).
abuelo(X,Y) :- madre(X,Z), padre(Z,Y).
abuelo(X,Y) :- madre(X,Z), madre(Z,Y).


```
<div align="center">
<h2>PROYECTO FINAL – ELIZA EN LISP</h2>
</div>

---

<div align="center">
<h3>Base de Conocimiento – Jugadores del Club América</h3>
<pre>
(defparameter *jugadores*
  '((henry-martin delantero mexicano)
    (luis-malagon portero mexicano)
    (alvaro-fidalgo mediocampista extranjero)
    (diego-valdes mediocampista extranjero)
    (julian-quinones delantero extranjero)
    (jonathan-dos-santos mediocampista mexicano)
    (alex-zendejas extremo mexicano)
    (brian-rodriguez extremo extranjero)
    (sebastian-caceres defensa extranjero)
    (igor-lichnovsky defensa extranjero)
    (kevin-alvarez defensa mexicano)))
</pre>
</div>

---

<div align="center">
<h3>Base de Conocimiento – Medicina</h3>
<pre>
(defparameter *enfermedades*
  '((anemia (cansancio palidez) hierro)
    (apendicitis (dolor-abdominal fiebre) cirugia)
    (covid (fiebre tos-seca) reposo)))
</pre>
</div>

---

<div align="center">
<h3>Base de Conocimiento – Familia</h3>
<pre>
(defparameter *familia*
  '((padre juan carlos)
    (padre carlos pedro)
    (madre maria carlos)
    (madre ana pedro)))

(defun padre-p (x y)
  (member (list 'padre x y) *familia* :test #'equal))

(defun madre-p (x y)
  (member (list 'madre x y) *familia* :test #'equal))

(defun abuelo-p (x y)
  (some (lambda (z)
          (and (or (padre-p x z) (madre-p x z))
               (or (padre-p z y) (madre-p z y))))
        '(juan carlos pedro)))
</pre>
</div>

---

<div align="center">
<h3>Medicina – Funciones</h3>
<pre>
(defparameter *sintomas-paciente* '())

(defun agregar-sintoma (s)
  (push s *sintomas-paciente*)
  (format t "Sintoma registrado: ~a~%" s))

(defun probabilidad (enfermedad)
  (let* ((datos (assoc enfermedad *enfermedades*))
         (sintomas (second datos))
         (total (length sintomas))
         (coinciden (length
                     (intersection sintomas *sintomas-paciente*))))
    (if (> total 0)
        (* 100 (/ coinciden total))
        0)))

(defun reporte-medico ()
  (format t "~%--- REPORTE MEDICO ---~%")
  (format t "Sintomas: ~a~%" *sintomas-paciente*)
  (dolist (e *enfermedades*)
    (format t "~a: ~a%%~%"
            (first e)
            (probabilidad (first e)))))
</pre>
</div>

---

<div align="center">
<h3>Akinator – Club América</h3>
<pre>
(defparameter *candidatos* '())

(defun iniciar-akinator ()
  (setf *candidatos* *jugadores*)
  (format t "~%Piensa en un jugador del Club America.~%")
  (pregunta-posicion))

(defun pregunta-posicion ()
  (format t "¿Es delantero? (si/no): ")
  (let ((r (read)))
    (when (equal r 'si)
      (setf *candidatos*
            (remove-if-not
             (lambda (j) (equal (second j) 'delantero))
             *candidatos*)))
    (pregunta-nacionalidad)))

(defun pregunta-nacionalidad ()
  (format t "¿Es mexicano? (si/no): ")
  (let ((r (read)))
    (when (equal r 'si)
      (setf *candidatos*
            (remove-if-not
             (lambda (j) (equal (third j) 'mexicano))
             *candidatos*)))
    (finalizar-akinator)))

(defun finalizar-akinator ()
  (cond
    ((= (length *candidatos*) 1)
     (format t "Estoy pensando en: ~a~%"
             (first (first *candidatos*))))
    (t
     (format t "No estoy segura, posibles opciones: ~a~%"
             (mapcar #'first *candidatos*)))))
</pre>
</div>

---

<div align="center">
<h3>ELIZA – Interacción</h3>
<pre>
(defun eliza ()
  (format t "~%Hola, soy ELIZA.~%")
  (format t "Comandos:~%")
  (format t "- (tengo sintoma)~%")
  (format t "- reporte~%")
  (format t "- quiero-jugar~%")
  (format t "- padre x y / madre x y / abuelo x y~%")
  (format t "- adios~%")
  (loop
     (format t "~%> ")
     (let ((entrada (read)))
       (cond
         ((equal entrada 'adios)
          (format t "Adios.~%")
          (return))
         ((and (listp entrada) (equal (first entrada) 'tengo))
          (agregar-sintoma (second entrada)))
         ((equal entrada 'reporte)
          (reporte-medico))
         ((equal entrada 'quiero-jugar)
          (iniciar-akinator))
         ((and (listp entrada) (equal (first entrada) 'padre))
          (format t "~a~%" (padre-p (second entrada) (third entrada))))
         ((and (listp entrada) (equal (first entrada) 'madre))
          (format t "~a~%" (madre-p (second entrada) (third entrada))))
         ((and (listp entrada) (equal (first entrada) 'abuelo))
          (format t "~a~%" (abuelo-p (second entrada) (third entrada))))
         (t
          (format t "No te entendi.~%"))))))
</pre>
</div>

<div align="center">
<h3>Conclusión</h3>
<p>El sistema experto ELIZA en Prolog permite simular una interacción similar a un asistente médico, integrando una base de conocimiento amplia y reglas de inferencia que permiten diagnosticar enfermedades, recomendar tratamientos, identificar relaciones familiares y adivinar jugadores del Club América. El uso de Prolog facilita la representación lógica de conocimientos y relaciones complejas.</p>
</div>


</body>
</html>

