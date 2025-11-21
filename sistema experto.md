<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Sistema Experto</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>

<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

---
<div aligne="center">
<h3>Enfermedades </3h>
<h4>
Hepatitis A

Síntomas frecuentes: fiebre, fatiga, náuseas/vómito, dolor abdominal (zona derecha superior), orina oscura, heces decoloradas, ictericia (piel/ojos amarillentos), pérdida de apetito.
(estos son los signos clásicos a vigilar). 
CDC

Complicaciones: en adultos mayores o con enfermedad hepática previa puede cursar más severo; generalmente es autolimitada. 
CDC

Especialistas a ver: médico de atención primaria / medicina familiar; si la presentación es severa o prolongada → infectólogo o hepatólogo.

Centros a acudir: clínica de urgencias si hay vómitos intensos, deshidratación o ictericia marcada; hospital con servicio de gastroenterología/hepatología para complicaciones.
<h/4>
</div>

---

<div aligne="center">
<h4>
Herpes zóster (shingles)

Síntomas frecuentes: dolor, ardor o parestesias en una banda/segmento de la piel (unilateral) seguido por erupción y ampollas; fiebre leve y malestar. Dolor puede preceder la erupción (fase prodrómica). Riesgo de neuralgia postherpética (dolor crónico) especialmente en >50 años. 

Complicaciones: afectación oftálmica (ojo) — riesgo serio; neuralgia postherpética; infecciones secundarias.

Especialistas a ver: médico de atención primaria al inicio (posible inicio de antivirales), dermatólogo; si hay afectación ocular → oftalmólogo; casos severos → infectólogo/hospital. 

Centros a acudir: atención primaria o urgencias si lesión cerca del ojo, dolor severo, o inmunosupresión.
</h4>
</div>

---

<div aligne="center">
<h4>
Enfermedad de Kawasaki

Síntomas frecuentes (niños, especialmente <5 años): fiebre alta persistente (>5 días), conjuntivitis bilateral no purulenta, labios/lingua enrojecidos y grietas, enantema (lengua de fresa), erupción cutánea, hinchazón/eritema de manos y pies (desprendimiento de piel después), adenopatía cervical (ganglios). Es una vasculitis que puede afectar coronarias. 

Complicaciones: aneurismas coronarios si no se trata de forma oportuna.

Especialistas a ver: pediatra inmediatamente; si sospecha → derivación a cardiología pediátrica y hospital para tratamiento (IVIG + aspirina como protocolo inicial en la mayoría de casos). 

Centros a acudir: urgencias pediátricas o consulta pediátrica con posibilidad de hospitalización; seguimiento con ecocardiograma.
</h4>
</div>

---
<div aligne="center">
<h4>
Enfermedad de Kawasaki

Síntomas frecuentes (niños, especialmente <5 años): fiebre alta persistente (>5 días), conjuntivitis bilateral no purulenta, labios/lingua enrojecidos y grietas, enantema (lengua de fresa), erupción cutánea, hinchazón/eritema de manos y pies (desprendimiento de piel después), adenopatía cervical (ganglios). Es una vasculitis que puede afectar coronarias. 

Complicaciones: aneurismas coronarios si no se trata de forma oportuna.

Especialistas a ver: pediatra inmediatamente; si sospecha → derivación a cardiología pediátrica y hospital para tratamiento (IVIG + aspirina como protocolo inicial en la mayoría de casos). 

Centros a acudir: urgencias pediátricas o consulta pediátrica con posibilidad de hospitalización; seguimiento con ecocardiograma.
</h4>
</div>


## Predicados del sistema experto en Prolog

```prolog
% --- Enfermedades ---
enfermedad(hepatitis_a).
enfermedad(herpes_zoster).
enfermedad(kawasaki).

% --- Síntomas ---
sintoma(fiebre).
sintoma(ictericia).
sintoma(cansancio).
sintoma(nauseas).
sintoma(dolor_abdominal).
sintoma(sarpullido).
sintoma(ampollas_dolorosas).
sintoma(dolor_nervioso).
sintoma(labios_agrietados).
sintoma(conjuntivitis).
sintoma(inflamacion_ganglios).
sintoma(descamacion_manos_pies).

% --- Relación enfermedad ↔ síntomas ---
presenta_sintoma(hepatitis_a, fiebre).
presenta_sintoma(hepatitis_a, ictericia).
presenta_sintoma(hepatitis_a, nauseas).
presenta_sintoma(hepatitis_a, cansancio).
presenta_sintoma(hepatitis_a, dolor_abdominal).

presenta_sintoma(herpes_zoster, sarpullido).
presenta_sintoma(herpes_zoster, ampollas_dolorosas).
presenta_sintoma(herpes_zoster, dolor_nervioso).
presenta_sintoma(herpes_zoster, fiebre).

presenta_sintoma(kawasaki, fiebre).
presenta_sintoma(kawasaki, labios_agrietados).
presenta_sintoma(kawasaki, conjuntivitis).
presenta_sintoma(kawasaki, inflamacion_ganglios).
presenta_sintoma(kawasaki, descamacion_manos_pies).

% --- Médicos ---
medico(infectologo).
medico(pediatra).
medico(dermatologo).
medico(cardiologo).
medico(reumatologo).

% --- Relación médico ↔ enfermedad ---
trata(infectologo, hepatitis_a).
trata(pediatra, hepatitis_a).
trata(dermatologo, herpes_zoster).
trata(infectologo, herpes_zoster).
trata(pediatra, kawasaki).
trata(cardiologo, kawasaki).
trata(reumatologo, kawasaki).

% --- Centros médicos ---
centro(hospital_general).
centro(clinica_dermatologica).
centro(centro_pediatrico).
centro(hospital_infectologia).
centro(unidad_cardiologia).

% --- Relación centro ↔ enfermedad ---
atiende_en(hospital_general, hepatitis_a).
atiende_en(hospital_infectologia, hepatitis_a).
atiende_en(clinica_dermatologica, herpes_zoster).
atiende_en(hospital_general, herpes_zoster).
atiende_en(centro_pediatrico, kawasaki).
atiende_en(unidad_cardiologia, kawasaki).
atiende_en(hospital_general, kawasaki).

% --- Medicamentos ---
medicamento(paracetamol).
medicamento(aciclovir).
medicamento(inmunoglobulina).
medicamento(aspirina).

% --- Relación medicamento ↔ enfermedad ---
medicamento_para(paracetamol, hepatitis_a).
medicamento_para(aciclovir, herpes_zoster).
medicamento_para(inmunoglobulina, kawasaki).
medicamento_para(aspirina, kawasaki).
```



---

## Código LISP



````markdown
## Sistema Experto Médico en LISP

```lisp
;;; ============================
;;; SISTEMA EXPERTO MÉDICO — LISP
;;; ============================

;;; ---------- Enfermedades ----------
(defun enfermedad (x)
  (member x '(hepatitis-a herpes-zoster kawasaki)))

;;; ---------- Síntomas ----------
(defun sintoma (x)
  (member x '(fiebre ictericia cansancio nauseas dolor-abdominal
                sarpullido ampollas-dolorosas dolor-nervioso
                labios-agrietados conjuntivitis
                inflamacion-ganglios descamacion-manos-pies)))

;;; ---------- Médicos ----------
(defun medico (m)
  (member m '(infectologo pediatra dermatologo cardiologo reumatologo)))

;;; ---------- Centros ----------
(defun centro-medico (c)
  (member c '(hospital-general clinica-dermatologica centro-pediatrico
               hospital-infectologia unidad-cardiologia)))

;;; ---------- Medicamentos ----------
(defun medicamento (m)
  (member m '(paracetamol aciclovir inmunoglobulina aspirina)))

;;; ======================================
;;;          RELACIONES BINARIAS
;;; ======================================

;;; --- sintomas de cada enfermedad ---
(defun presenta-sintoma (enf sint)
  (member (list enf sint)
          '((hepatitis-a fiebre)
            (hepatitis-a ictericia)
            (hepatitis-a nauseas)
            (hepatitis-a cansancio)
            (hepatitis-a dolor-abdominal)

            (herpes-zoster sarpullido)
            (herpes-zoster ampollas-dolorosas)
            (herpes-zoster dolor-nervioso)
            (herpes-zoster fiebre)

            (kawasaki fiebre)
            (kawasaki labios-agrietados)
            (kawasaki conjuntivitis)
            (kawasaki inflamacion-ganglios)
            (kawasaki descamacion-manos-pies))))

;;; --- médicos que tratan cada enfermedad ---
(defun trata (med enf)
  (member (list med enf)
          '((infectologo hepatitis-a)
            (pediatra hepatitis-a)
            (dermatologo herpes-zoster)
            (infectologo herpes-zoster)
            (pediatra kawasaki)
            (cardiologo kawasaki)
            (reumatologo kawasaki))))

;;; --- centros donde atenderse ---
(defun atiende-en (centro enf)
  (member (list centro enf)
          '((hospital-general hepatitis-a)
            (hospital-infectologia hepatitis-a)

            (clinica-dermatologica herpes-zoster)
            (hospital-general herpes-zoster)

            (centro-pediatrico kawasaki)
            (unidad-cardiologia kawasaki)
            (hospital-general kawasaki))))

;;; --- medicamentos recomendados ---
(defun medicamento-para (med enf)
  (member (list med enf)
          '((paracetamol hepatitis-a)
            (aciclovir herpes-zoster)
            (inmunoglobulina kawasaki)
            (aspirina kawasaki))))

;;; ======================================
;;;         CONSULTAS / REGLAS
;;; ======================================

(defun sintomas-de (enf)
  (remove-if-not (lambda (s) (presenta-sintoma enf s))
                 '(fiebre ictericia cansancio nauseas dolor-abdominal
                   sarpullido ampollas-dolorosas dolor-nervioso
                   labios-agrietados conjuntivitis
                   inflamacion-ganglios descamacion-manos-pies)))

(defun medicos-para (enf)
  (remove-if-not (lambda (m) (trata m enf))
                 '(infectologo pediatra dermatologo cardiologo reumatologo)))

(defun centros-para (enf)
  (remove-if-not (lambda (c) (atiende-en c enf))
                 '(hospital-general clinica-dermatologica centro-pediatrico
                   hospital-infectologia unidad-cardiologia)))

(defun medicamentos-para (enf)
  (remove-if-not (lambda (m) (medicamento-para m enf))
                 '(paracetamol aciclovir inmunoglobulina aspirina)))













