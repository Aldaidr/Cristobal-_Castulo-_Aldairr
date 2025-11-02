<div align="center">
<h2>INSTITUTO TECNOLÓGICO DE MORELIA </h2>

<h3>Programación Lógica y Funcional </h3>

<h3>Template (Bienvenida y Despedida)</h3>

<h3>Ingeniería en Sistemas Computacionales</h3>

<h3>Aldair Cristobal Castulo</h3>

<h3>Profesor: Alcaraz Chavez Jesus Eduardo</h3>
</div>

---

<div align="center">
<h2>Implementación de 20 plantillas de bienvenida y 20 de despedida en Eliza</h2>
</div>

<div align="justify">
<p>
En esta actualización del programa <strong>Eliza</strong>, se integraron un total de cuarenta plantillas (templates) diseñadas para mejorar la interacción con el usuario. Estas plantillas incluyen veinte respuestas de bienvenida y veinte de despedida, lo que permite que el chatbot mantenga un diálogo más natural y variado.
</p>

<p>
El objetivo principal de este commit fue ampliar el repertorio de frases con las que Eliza puede saludar o despedirse, de manera que las conversaciones no sean repetitivas y se perciba una mayor personalización en las respuestas. Cada plantilla fue construida a partir de un patrón de entrada que reconoce distintas formas en que el usuario puede iniciar o finalizar una conversación, como “hola”, “buenas tardes”, “adiós” o “hasta pronto”.
</p>

<p>
Estas nuevas reglas se implementaron utilizando el predicado <code>template</code>, donde se especifican tres parámetros: la lista de palabras que activan el patrón, la lista que contiene la respuesta que Eliza mostrará, y un tercer parámetro que indica los índices de sustitución cuando se requiere procesar información adicional. De esta forma, Eliza puede detectar las palabras clave del usuario y devolver una respuesta acorde.
</p>

<p>
El conjunto de plantillas se encuentra dividido en dos secciones principales: las de bienvenida, que buscan iniciar una conversación amigable, y las de despedida, que permiten concluir la interacción de forma cordial. Además, se mantiene una respuesta genérica por defecto para entradas que no coinciden con ningún patrón predefinido.
</p>

<p>
Eliza se vuelve más expresiva y empática al inicio y final de las conversaciones, mejorando la experiencia del usuario e incrementando la naturalidad de la comunicación.
</p>

<div align="center">
<h2>Plantillas de Bienvenida de Eliza</h2>
</div>

<div align="justify">

<ul>
  <li><strong>Usuario:</strong> hola → <em>¡Hola! ¿Cómo te sientes hoy?</em></li>
  <li><strong>Usuario:</strong> buenos días → <em>¡Buenos días! ¿Cómo puedo ayudarte hoy?</em></li>
  <li><strong>Usuario:</strong> buenas tardes → <em>¡Buenas tardes! Cuéntame, ¿qué te preocupa?</em></li>
  <li><strong>Usuario:</strong> buenas noches → <em>¡Buenas noches! Estoy aquí para escucharte.</em></li>
  <li><strong>Usuario:</strong> que onda → <em>¡Qué onda! ¿Cómo va tu día?</em></li>
  <li><strong>Usuario:</strong> hey → <em>¡Hey! Me alegra verte por aquí.</em></li>
  <li><strong>Usuario:</strong> saludos → <em>Saludos, humano curioso.</em></li>
  <li><strong>Usuario:</strong> eliza → <em>Sí, soy Eliza. ¿En qué piensas?</em></li>
  <li><strong>Usuario:</strong> como estás → <em>Estoy lista para conversar, ¿y tú?</em></li>
  <li><strong>Usuario:</strong> hola eliza → <em>¡Hola! Siempre es un gusto saludarte.</em></li>
  <li><strong>Usuario:</strong> buen día → <em>Buen día, ¿qué te trae por aquí?</em></li>
  <li><strong>Usuario:</strong> hey eliza → <em>¡Hey! Aquí estoy, lista para hablar.</em></li>
  <li><strong>Usuario:</strong> saludos eliza → <em>Saludos, ¿en qué puedo ayudarte?</em></li>
  <li><strong>Usuario:</strong> que tal → <em>Todo bien por aquí, ¿y tú?</em></li>
  <li><strong>Usuario:</strong> hola que tal → <em>¡Hola! Me alegra verte conectado.</em></li>
  <li><strong>Usuario:</strong> como va → <em>Todo va bien. ¿Qué tal contigo?</em></li>
  <li><strong>Usuario:</strong> hola amiga → <em>¡Hola! Me gusta cuando me llamas así.</em></li>
  <li><strong>Usuario:</strong> buenas → <em>¡Buenas! Dime, ¿cómo puedo ayudarte hoy?</em></li>
  <li><strong>Usuario:</strong> eliza estás ahí → <em>Aquí estoy, atenta como siempre.</em></li>
  <li><strong>Usuario:</strong> hey bot → <em>Prefiero Eliza, pero hola igualmente.</em></li>
</ul>

<p>
Cada una de estas plantillas fue implementada mediante el predicado <code>template/3</code> en Prolog, donde el primer argumento corresponde al patrón de palabras que el usuario puede escribir, y el segundo contiene la respuesta que Eliza mostrará en pantalla.
</p>
</div>


<div align="center">
<h2>Plantillas de Despedida de Eliza</h2>
</div>

<div align="justify">

<ul>
  <li><strong>Usuario:</strong> adiós → <em>Adiós. Espero haberte ayudado.</em></li>
  <li><strong>Usuario:</strong> chao → <em>Chao. Cuídate mucho.</em></li>
  <li><strong>Usuario:</strong> hasta luego → <em>Hasta luego, ¡no tardes en volver!</em></li>
  <li><strong>Usuario:</strong> nos vemos → <em>Nos vemos pronto.</em></li>
  <li><strong>Usuario:</strong> me voy → <em>Está bien, que tengas un buen día.</em></li>
  <li><strong>Usuario:</strong> gracias → <em>De nada. ¡Fue un placer hablar contigo!</em></li>
  <li><strong>Usuario:</strong> bye → <em>Bye bye.</em></li>
  <li><strong>Usuario:</strong> hasta mañana → <em>Hasta mañana, descansa bien.</em></li>
  <li><strong>Usuario:</strong> hasta pronto → <em>Hasta pronto. ¡Te esperaré!</em></li>
  <li><strong>Usuario:</strong> cuídate → <em>Tú también, cuídate mucho.</em></li>
  <li><strong>Usuario:</strong> nos hablamos → <em>Nos hablamos luego.</em></li>
  <li><strong>Usuario:</strong> salgo → <em>Está bien, nos vemos.</em></li>
  <li><strong>Usuario:</strong> ya me voy → <em>Ok, ¡nos vemos la próxima!</em></li>
  <li><strong>Usuario:</strong> hasta la próxima → <em>Hasta la próxima conversación.</em></li>
  <li><strong>Usuario:</strong> nos vemos luego → <em>Nos vemos luego, ¡suerte!</em></li>
  <li><strong>Usuario:</strong> ya es todo → <em>Perfecto. Que tengas un excelente día.</em></li>
  <li><strong>Usuario:</strong> eso es todo → <em>Entendido. ¡Cuídate!</em></li>
  <li><strong>Usuario:</strong> me despido → <em>Gracias por tu tiempo, ¡adiós!</em></li>
  <li><strong>Usuario:</strong> nos vemos mañana → <em>Nos vemos mañana si quieres charlar más.</em></li>
  <li><strong>Usuario:</strong> cierro sesión → <em>Ok, cerrando sesión mental 🤖 Adiós.</em></li>
</ul>

<p>
Estas plantillas se definen mediante el predicado <code>template/3</code> en Prolog, donde el primer parámetro corresponde a las palabras clave que el usuario puede escribir y el segundo contiene la respuesta textual de Eliza. Gracias a esta implementación, el chatbot puede despedirse de diversas maneras, generando una conversación más humana y menos repetitiva.
</p>
</div>



</div>















