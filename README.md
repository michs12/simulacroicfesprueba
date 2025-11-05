<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Simulacros ICFES — Pro (Temporizador 45 min + PDF)</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">
  <style>
    html { scroll-behavior:smooth; }
    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #0f172a, #1e293b);
      color: #f1f5f9;
      margin:0; padding:0;
    }
    header {
      background: linear-gradient(90deg,#1e3a8a,#0ea5e9);
      padding: 18px 22px;
      display:flex;align-items:center;justify-content:space-between;
      position:sticky;top:0;z-index:100;
      box-shadow:0 4px 14px rgba(0,0,0,0.25);
    }
    header h1 { margin:0;font-size:18px; }
    nav a { color:#fff;margin-left:14px;text-decoration:none;cursor:pointer;font-weight:600 }
    main { max-width:1100px;margin:28px auto;padding:0 18px 80px; }
    .hero { text-align:center;padding:28px 18px;border-radius:12px;background:linear-gradient(135deg,#06b6d4,#4f46e5);box-shadow:0 10px 25px rgba(0,0,0,0.2); }
    .hero h2{margin:0 0 6px;font-size:clamp(20px,3vw,30px)}
    .hero p{margin:0;color:rgba(255,255,255,0.92)}
    .controls { display:flex;gap:12px;align-items:center;justify-content:center;margin:18px 0;flex-wrap:wrap }
    .input-name { padding:10px 12px;border-radius:8px;border:0;min-width:240px }
    .btn { background:#06b6d4;color:#042f3b;padding:10px 14px;border-radius:10px;border:0;font-weight:700;cursor:pointer }
    .btn:disabled{opacity:0.6;cursor:not-allowed}
    .timer { font-weight:700;background:rgba(255,255,255,0.06);padding:8px 12px;border-radius:8px }
    .areas { display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px;margin:20px 0 }
    .card { background:rgba(255,255,255,0.04);padding:16px;border-radius:12px;box-shadow:0 6px 18px rgba(0,0,0,0.25); }
    .card h3{margin:0 0 8px;color:#a5f3fc}
    .section { background: rgba(255,255,255,0.03); padding:20px;border-radius:12px;margin-bottom:22px }
    .simulacro { display:none }
    .simulacro.active { display:block }
    .question { background: rgba(255,255,255,0.02); padding:10px;border-radius:8px;margin-bottom:10px }
    label{display:block;cursor:pointer;color:#e6eef8;margin:6px 0}
    input[type="radio"]{margin-right:8px}
    .resultado{margin-top:12px;font-weight:700;color:#34d399;white-space:pre-line}
    .footer{ text-align:center;color:rgba(255,255,255,0.7);padding:18px 0 }
    .small{font-size:13px;color:rgba(241,245,249,0.9)}
    @media(max-width:700px){ header{padding:12px} .controls{flex-direction:column} }
  </style>
</head>
<body>
  <header>
    <h1>Simulacros ICFES — Versión Pro</h1>
    <nav>
      <a onclick="mostrar('inicio')">Inicio</a>
      <a onclick="mostrar('areas')">Áreas</a>
      <a onclick="mostrar('simulacros')">Simulacros</a>
      <a onclick="mostrar('contacto')">Contacto</a>
    </nav>
  </header>

  <main>
    <section id="inicio" class="hero">
      <h2>Simulacro completo — 5 áreas • 50 preguntas</h2>
      <p>Llena tu nombre, presiona <strong>Iniciar</strong> y el temporizador de <strong>45 minutos</strong> comenzará. Cuando termine, se corregirá automáticamente y podrás exportar tu resultado a PDF.</p>

      <div class="controls" style="margin-top:18px">
        <input id="userName" class="input-name" placeholder="Escribe tu nombre aquí (ej. María Pérez)" />
        <div id="timer" class="timer">45:00</div>
        <button id="startBtn" class="btn">Iniciar simulacro</button>
        <button id="pauseBtn" class="btn" style="display:none">Pausar</button>
        <button id="finishBtn" class="btn" style="display:none">Finalizar y Calificar</button>
      </div>

      <div style="margin-top:8px" class="small">Nota: el temporizador sigue corriendo incluso si cambias de sección. Si se termina el tiempo, el simulacro se corrige automáticamente.</div>
    </section>

    <section id="areas" class="section">
      <h3 style="color:#a5f3fc;margin-top:0">Áreas</h3>
      <div class="areas">
        <div class="card"><h3>📐 Matemáticas</h3><p class="small">Razonamiento numérico y álgebra.</p><div style="text-align:right"><button class="btn" onclick="mostrarSimulacro('matematicas')">Ir</button></div></div>
        <div class="card"><h3>📘 Lectura Crítica</h3><p class="small">Comprensión e inferencia.</p><div style="text-align:right"><button class="btn" onclick="mostrarSimulacro('lectura')">Ir</button></div></div>
        <div class="card"><h3>🧪 Ciencias Naturales</h3><p class="small">Biología, física y química básicas.</p><div style="text-align:right"><button class="btn" onclick="mostrarSimulacro('naturales')">Ir</button></div></div>
        <div class="card"><h3>🌍 Sociales</h3><p class="small">Historia, geografía y ciudadanía.</p><div style="text-align:right"><button class="btn" onclick="mostrarSimulacro('sociales')">Ir</button></div></div>
        <div class="card"><h3>🇬🇧 Inglés</h3><p class="small">Gramática y comprensión básica.</p><div style="text-align:right"><button class="btn" onclick="mostrarSimulacro('ingles')">Ir</button></div></div>
      </div>
    </section>

    <section id="simulacros" class="section">
      <h3 style="color:#a5f3fc;margin-top:0">Simulacros — responde y guarda tu progreso</h3>

      <!-- MATEMÁTICAS -->
      <div id="simulacro-matematicas" class="simulacro">
        <h4>Matemáticas — 10 preguntas</h4>
        <form id="form-matematicas">
          <div class="question"><p>1. Si 3x + 2 = 14, ¿x = ?</p>
            <label><input type="radio" name="q1" value="A"> 3</label>
            <label><input type="radio" name="q1" value="B"> 4</label>
            <label><input type="radio" name="q1" value="C"> 5</label>
            <label><input type="radio" name="q1" value="D"> 6</label>
          </div>
          <div class="question"><p>2. Área de triángulo base 6 y altura 4:</p>
            <label><input type="radio" name="q2" value="A"> 12</label>
            <label><input type="radio" name="q2" value="B"> 24</label>
            <label><input type="radio" name="q2" value="C"> 10</label>
            <label><input type="radio" name="q2" value="D"> 8</label>
          </div>
          <div class="question"><p>3. ¿Raíz cuadrada de 169?</p>
            <label><input type="radio" name="q3" value="A"> 11</label>
            <label><input type="radio" name="q3" value="B"> 12</label>
            <label><input type="radio" name="q3" value="C"> 13</label>
            <label><input type="radio" name="q3" value="D"> 14</label>
          </div>
          <div class="question"><p>4. Si 5x = 35, x = ?</p>
            <label><input type="radio" name="q4" value="A"> 5</label>
            <label><input type="radio" name="q4" value="B"> 6</label>
            <label><input type="radio" name="q4" value="C"> 7</label>
            <label><input type="radio" name="q4" value="D"> 8</label>
          </div>
          <div class="question"><p>5. 25% de 200 es:</p>
            <label><input type="radio" name="q5" value="A"> 30</label>
            <label><input type="radio" name="q5" value="B"> 50</label>
            <label><input type="radio" name="q5" value="C"> 40</label>
            <label><input type="radio" name="q5" value="D"> 60</label>
          </div>
          <div class="question"><p>6. 2^6 = ?</p>
            <label><input type="radio" name="q6" value="A"> 32</label>
            <label><input type="radio" name="q6" value="B"> 64</label>
            <label><input type="radio" name="q6" value="C"> 16</label>
            <label><input type="radio" name="q6" value="D"> 8</label>
          </div>
          <div class="question"><p>7. MCM de 4 y 6:</p>
            <label><input type="radio" name="q7" value="A"> 12</label>
            <label><input type="radio" name="q7" value="B"> 10</label>
            <label><input type="radio" name="q7" value="C"> 8</label>
            <label><input type="radio" name="q7" value="D"> 6</label>
          </div>
          <div class="question"><p>8. Perímetro de un cuadrado lado 7:</p>
            <label><input type="radio" name="q8" value="A"> 14</label>
            <label><input type="radio" name="q8" value="B"> 21</label>
            <label><input type="radio" name="q8" value="C"> 28</label>
            <label><input type="radio" name="q8" value="D"> 35</label>
          </div>
          <div class="question"><p>9. 9 × 8 = ?</p>
            <label><input type="radio" name="q9" value="A"> 72</label>
            <label><input type="radio" name="q9" value="B"> 81</label>
            <label><input type="radio" name="q9" value="C"> 64</label>
            <label><input type="radio" name="q9" value="D"> 90</label>
          </div>
          <div class="question"><p>10. Velocidad media: 150 km en 3 h → ?</p>
            <label><input type="radio" name="q10" value="A"> 40 km/h</label>
            <label><input type="radio" name="q10" value="B"> 50 km/h</label>
            <label><input type="radio" name="q10" value="C"> 60 km/h</label>
            <label><input type="radio" name="q10" value="D"> 30 km/h</label>
          </div>

          <div style="text-align:center;margin-top:10px">
            <button type="button" class="btn" onclick="calificar('matematicas')">Calificar Matemáticas</button>
            <div id="resultado-matematicas" class="resultado"></div>
          </div>
        </form>
      </div>

      <!-- LECTURA -->
      <div id="simulacro-lectura" class="simulacro">
        <h4>Lectura Crítica — 10 preguntas</h4>
        <form id="form-lectura">
          <div class="question"><p>1. ¿Qué es una inferencia?</p>
            <label><input type="radio" name="q1" value="A"> Una cita literal</label>
            <label><input type="radio" name="q1" value="B"> Una conclusión basada en pistas</label>
            <label><input type="radio" name="q1" value="C"> Un dato numérico</label>
            <label><input type="radio" name="q1" value="D"> Una opinión irrelevante</label>
          </div>
          <div class="question"><p>2. ¿Para qué sirven los conectores?</p>
            <label><input type="radio" name="q2" value="A"> Para unir ideas y mostrar relaciones</label>
            <label><input type="radio" name="q2" value="B"> Para decorar el texto</label>
            <label><input type="radio" name="q2" value="C"> Para contar una historia</label>
            <label><input type="radio" name="q2" value="D"> Para indicar el autor</label>
          </div>
          <div class="question"><p>3. ¿Qué distingue un texto expositivo?</p>
            <label><input type="radio" name="q3" value="A"> Busca persuadir con emoción</label>
            <label><input type="radio" name="q3" value="B"> Expone información y conceptos</label>
            <label><input type="radio" name="q3" value="C"> Es siempre ficticio</label>
            <label><input type="radio" name="q3" value="D"> Tiene rima</label>
          </div>
          <div class="question"><p>4. ¿Qué es el tono de un texto?</p>
            <label><input type="radio" name="q4" value="A"> La estructura</label>
            <label><input type="radio" name="q4" value="B"> La actitud o emoción del autor</label>
            <label><input type="radio" name="q4" value="C"> El título</label>
            <label><input type="radio" name="q4" value="D"> El tipo de letra</label>
          </div>
          <div class="question"><p>5. ¿Qué es una idea principal?</p>
            <label><input type="radio" name="q5" value="A"> Un detalle menor</label>
            <label><input type="radio" name="q5" value="B"> El mensaje central del párrafo</label>
            <label><input type="radio" name="q5" value="C"> Una conclusión sin base</label>
            <label><input type="radio" name="q5" value="D"> Un ejemplo</label>
          </div>
          <div class="question"><p>6. ¿Qué identifica una opinión?</p>
            <label><input type="radio" name="q6" value="A"> Juicio personal</label>
            <label><input type="radio" name="q6" value="B"> Hecho comprobable</label>
            <label><input type="radio" name="q6" value="C"> Definición técnica</label>
            <label><input type="radio" name="q6" value="D"> Un número</label>
          </div>
          <div class="question"><p>7. ¿Cuál recurso ayuda a argumentar?</p>
            <label><input type="radio" name="q7" value="A"> Evidencias y ejemplos</label>
            <label><input type="radio" name="q7" value="B"> Palabras vacías</label>
            <label><input type="radio" name="q7" value="C"> Rimas</label>
            <label><input type="radio" name="q7" value="D"> Listas sin sentido</label>
          </div>
          <div class="question"><p>8. ¿Qué indica un subtítulo?</p>
            <label><input type="radio" name="q8" value="A"> Cambio de idea o sección</label>
            <label><input type="radio" name="q8" value="B"> Fin del texto</label>
            <label><input type="radio" name="q8" value="C"> Una referencia</label>
            <label><input type="radio" name="q8" value="D"> La firma del autor</label>
          </div>
          <div class="question"><p>9. ¿Qué significa “objetivo” en un texto informativo?</p>
            <label><input type="radio" name="q9" value="A"> Parcialidad</label>
            <label><input type="radio" name="q9" value="B"> Imparcialidad y precisión</label>
            <label><input type="radio" name="q9" value="C"> Ficción</label>
            <label><input type="radio" name="q9" value="D"> Subjetividad</label>
          </div>
          <div class="question"><p>10. ¿Qué es una conclusión?</p>
            <label><input type="radio" name="q10" value="A"> Una idea final que resume</label>
            <label><input type="radio" name="q10" value="B"> Un ejemplo</label>
            <label><input type="radio" name="q10" value="C"> Un párrafo inicial</label>
            <label><input type="radio" name="q10" value="D"> Una cita</label>
          </div>

          <div style="text-align:center;margin-top:10px">
            <button type="button" class="btn" onclick="calificar('lectura')">Calificar Lectura</button>
            <div id="resultado-lectura" class="resultado"></div>
          </div>
        </form>
      </div>

      <!-- NATURALES -->
      <div id="simulacro-naturales" class="simulacro">
        <h4>Ciencias Naturales — 10 preguntas</h4>
        <form id="form-naturales">
          <div class="question"><p>1. ¿Cuál es la función de los glóbulos rojos?</p>
            <label><input type="radio" name="q1" value="A"> Transportar oxígeno</label>
            <label><input type="radio" name="q1" value="B"> Defender el cuerpo</label>
            <label><input type="radio" name="q1" value="C"> Producir hormonas</label>
            <label><input type="radio" name="q1" value="D"> Filtrar sangre</label>
          </div>
          <div class="question"><p>2. ¿Qué gas necesitamos para respirar?</p>
            <label><input type="radio" name="q2" value="A"> Nitrógeno</label>
            <label><input type="radio" name="q2" value="B"> Oxígeno</label>
            <label><input type="radio" name="q2" value="C"> Dióxido de carbono</label>
            <label><input type="radio" name="q2" value="D"> Helio</label>
          </div>
          <div class="question"><p>3. ¿Cuál es la unidad básica de los seres vivos?</p>
            <label><input type="radio" name="q3" value="A"> Tejido</label>
            <label><input type="radio" name="q3" value="B"> Célula</label>
            <label><input type="radio" name="q3" value="C"> Órgano</label>
            <label><input type="radio" name="q3" value="D"> Sistema</label>
          </div>
          <div class="question"><p>4. ¿Qué proceso realizan las plantas para producir alimento?</p>
            <label><input type="radio" name="q4" value="A"> Fotosíntesis</label>
            <label><input type="radio" name="q4" value="B"> Respiración</label>
            <label><input type="radio" name="q4" value="C"> Fermentación</label>
            <label><input type="radio" name="q4" value="D"> Digestión</label>
          </div>
          <div class="question"><p>5. ¿Cuál es el símbolo químico del agua?</p>
            <label><input type="radio" name="q5" value="A"> H2O</label>
            <label><input type="radio" name="q5" value="B"> CO2</label>
            <label><input type="radio" name="q5" value="C"> O2</label>
            <label><input type="radio" name="q5" value="D"> H2</label>
          </div>
          <div class="question"><p>6. ¿Qué órgano ayuda a filtrar desechos de la sangre?</p>
            <label><input type="radio" name="q6" value="A"> Corazón</label>
            <label><input type="radio" name="q6" value="B"> Hígado</label>
            <label><input type="radio" name="q6" value="C"> Riñón</label>
            <label><input type="radio" name="q6" value="D"> Pulmón</label>
          </div>
          <div class="question"><p>7. ¿Qué partícula tiene carga negativa?</p>
            <label><input type="radio" name="q7" value="A"> Protón</label>
            <label><input type="radio" name="q7" value="B"> Neutrón</label>
            <label><input type="radio" name="q7" value="C"> Electrón</label>
            <label><input type="radio" name="q7" value="D"> Átomo</label>
          </div>
          <div class="question"><p>8. ¿Qué estructura realizan la fotosíntesis?</p>
            <label><input type="radio" name="q8" value="A"> Raíces</label>
            <label><input type="radio" name="q8" value="B"> Hojas</label>
            <label><input type="radio" name="q8" value="C"> Flores</label>
            <label><input type="radio" name="q8" value="D"> Tallos</label>
          </div>
          <div class="question"><p>9. ¿Cuál es la función principal del sistema respiratorio?</p>
            <label><input type="radio" name="q9" value="A"> Transportar nutrientes</label>
            <label><input type="radio" name="q9" value="B"> Intercambio de gases (oxígeno/dióxido de carbono)</label>
            <label><input type="radio" name="q9" value="C"> Producir hormonas</label>
            <label><input type="radio" name="q9" value="D"> Proteger contra infecciones</label>
          </div>
          <div class="question"><p>10. ¿Qué molécula almacena la información genética?</p>
            <label><input type="radio" name="q10" value="A"> ARN</label>
            <label><input type="radio" name="q10" value="B"> ADN</label>
            <label><input type="radio" name="q10" value="C"> ATP</label>
            <label><input type="radio" name="q10" value="D"> Proteína</label>
          </div>

          <div style="text-align:center;margin-top:10px">
            <button type="button" class="btn" onclick="calificar('naturales')">Calificar Naturales</button>
            <div id="resultado-naturales" class="resultado"></div>
          </div>
        </form>
      </div>

      <!-- SOCIALES -->
      <div id="simulacro-sociales" class="simulacro">
        <h4>Sociales — 10 preguntas</h4>
        <form id="form-sociales">
          <div class="question"><p>1. ¿Qué es la geografía?</p>
            <label><input type="radio" name="q1" value="A"> Estudio de procesos económicos</label>
            <label><input type="radio" name="q1" value="B"> Estudio del espacio, lugares y fenómenos del planeta</label>
            <label><input type="radio" name="q1" value="C"> Estudio de la química del suelo</label>
            <label><input type="radio" name="q1" value="D"> Estudio de la biología humana</label>
          </div>
          <div class="question"><p>2. ¿Qué es la historia?</p>
            <label><input type="radio" name="q2" value="A"> Narración y estudio de hechos pasados</label>
            <label><input type="radio" name="q2" value="B"> Ciencia de plantas</label>
            <label><input type="radio" name="q2" value="C"> Técnica de construcción</label>
            <label><input type="radio" name="q2" value="D"> Lenguaje artístico</label>
          </div>
          <div class="question"><p>3. ¿Qué representa una constitución?</p>
            <label><input type="radio" name="q3" value="A"> Conjunto de normas fundamentales de un país</label>
            <label><input type="radio" name="q3" value="B"> Un tipo de moneda</label>
            <label><input type="radio" name="q3" value="C"> Un monumento</label>
            <label><input type="radio" name="q3" value="D"> Un sistema climático</label>
          </div>
          <div class="question"><p>4. ¿Qué estudia la economía?</p>
            <label><input type="radio" name="q4" value="A"> Relaciones sociales</label>
            <label><input type="radio" name="q4" value="B"> Producción, distribución y consumo de bienes</label>
            <label><input type="radio" name="q4" value="C"> La pintura</label>
            <label><input type="radio" name="q4" value="D"> Fórmulas químicas</label>
          </div>
          <div class="question"><p>5. ¿Qué es la democracia?</p>
            <label><input type="radio" name="q5" value="A"> Gobierno de unos pocos</label>
            <label><input type="radio" name="q5" value="B"> Participación del pueblo en la toma de decisiones</label>
            <label><input type="radio" name="q5" value="C"> Ausencia de normas</label>
            <label><input type="radio" name="q5" value="D"> Sistema económico</label>
          </div>
          <div class="question"><p>6. ¿Qué es un ciudadano?</p>
            <label><input type="radio" name="q6" value="A"> Alguien que vive en el campo</label>
            <label><input type="radio" name="q6" value="B"> Miembro y sujeto de derecho de un Estado</label>
            <label><input type="radio" name="q6" value="C"> Un trabajador</label>
            <label><input type="radio" name="q6" value="D"> Un turista</label>
          </div>
          <div class="question"><p>7. ¿Qué es la globalización?</p>
            <label><input type="radio" name="q7" value="A"> Aislamiento de países</label>
            <label><input type="radio" name="q7" value="B"> Interconexión e intercambio entre países</label>
            <label><input type="radio" name="q7" value="C"> Un fenómeno climático</label>
            <label><input type="radio" name="q7" value="D"> Un tipo de gobierno</label>
          </div>
          <div class="question"><p>8. ¿Qué es la migración?</p>
            <label><input type="radio" name="q8" value="A"> Movimiento de personas entre lugares</label>
            <label><input type="radio" name="q8" value="B"> Cambio de idioma</label>
            <label><input type="radio" name="q8" value="C"> Un tratado internacional</label>
            <label><input type="radio" name="q8" value="D"> Un sistema educativo</label>
          </div>
          <div class="question"><p>9. ¿Qué función cumple el parlamento?</p>
            <label><input type="radio" name="q9" value="A"> Crear y aprobar leyes</label>
            <label><input type="radio" name="q9" value="B"> Diseñar ropa</label>
            <label><input type="radio" name="q9" value="C"> Plantar árboles</label>
            <label><input type="radio" name="q9" value="D"> Administrar empresas privadas</label>
          </div>
          <div class="question"><p>10. ¿Qué es un derecho humano?</p>
            <label><input type="radio" name="q10" value="A"> Algo que solo algunos tienen</label>
            <label><input type="radio" name="q10" value="B"> Libertades y garantías que todas las personas poseen</label>
            <label><input type="radio" name="q10" value="C"> Una ley local</label>
            <label><input type="radio" name="q10" value="D"> Un requisito educativo</label>
          </div>

          <div style="text-align:center;margin-top:10px">
            <button type="button" class="btn" onclick="calificar('sociales')">Calificar Sociales</button>
            <div id="resultado-sociales" class="resultado"></div>
          </div>
        </form>
      </div>

      <!-- INGLES -->
      <div id="simulacro-ingles" class="simulacro">
        <h4>Inglés — 10 preguntas</h4>
        <form id="form-ingles">
          <div class="question"><p>1. She ____ to school every day.</p>
            <label><input type="radio" name="q1" value="A"> go</label>
            <label><input type="radio" name="q1" value="B"> goes</label>
            <label><input type="radio" name="q1" value="C"> going</label>
            <label><input type="radio" name="q1" value="D"> gone</label>
          </div>
          <div class="question"><p>2. Opposite of "easy":</p>
            <label><input type="radio" name="q2" value="A"> hard</label>
            <label><input type="radio" name="q2" value="B"> simple</label>
            <label><input type="radio" name="q2" value="C"> difficult</label>
            <label><input type="radio" name="q2" value="D"> quick</label>
          </div>
          <div class="question"><p>3. I have been learning English ____ two years.</p>
            <label><input type="radio" name="q3" value="A"> since</label>
            <label><input type="radio" name="q3" value="B"> for</label>
            <label><input type="radio" name="q3" value="C"> from</label>
            <label><input type="radio" name="q3" value="D"> during</label>
          </div>
          <div class="question"><p>4. Past of "read" (pronounced "red") in "I ____ a book yesterday":</p>
            <label><input type="radio" name="q4" value="A"> read</label>
            <label><input type="radio" name="q4" value="B"> will read</label>
            <label><input type="radio" name="q4" value="C"> am reading</label>
            <label><input type="radio" name="q4" value="D"> reads</label>
          </div>
          <div class="question"><p>5. Which is a noun?</p>
            <label><input type="radio" name="q5" value="A"> run</label>
            <label><input type="radio" name="q5" value="B"> quickly</label>
            <label><input type="radio" name="q5" value="C"> happiness</label>
            <label><input type="radio" name="q5" value="D"> blue</label>
          </div>
          <div class="question"><p>6. They ____ going to the party tonight.</p>
            <label><input type="radio" name="q6" value="A"> is</label>
            <label><input type="radio" name="q6" value="B"> are</label>
            <label><input type="radio" name="q6" value="C"> am</label>
            <label><input type="radio" name="q6" value="D"> be</label>
          </div>
          <div class="question"><p>7. She arrived ___ the airport.</p>
            <label><input type="radio" name="q7" value="A"> in</label>
            <label><input type="radio" name="q7" value="B"> at</label>
            <label><input type="radio" name="q7" value="C"> on</label>
            <label><input type="radio" name="q7" value="D"> to</label>
          </div>
          <div class="question"><p>8. Comparative of "small":</p>
            <label><input type="radio" name="q8" value="A"> smallest</label>
            <label><input type="radio" name="q8" value="B"> more small</label>
            <label><input type="radio" name="q8" value="C"> smaller</label>
            <label><input type="radio" name="q8" value="D"> most small</label>
          </div>
          <div class="question"><p>9. I saw ___ owl.</p>
            <label><input type="radio" name="q9" value="A"> a</label>
            <label><input type="radio" name="q9" value="B"> an</label>
            <label><input type="radio" name="q9" value="C"> the</label>
            <label><input type="radio" name="q9" value="D"> that</label>
          </div>
          <div class="question"><p>10. "Casa" in English is:</p>
            <label><input type="radio" name="q10" value="A"> house</label>
            <label><input type="radio" name="q10" value="B"> car</label>
            <label><input type="radio" name="q10" value="C"> homeworks</label>
            <label><input type="radio" name="q10" value="D"> window</label>
          </div>

          <div style="text-align:center;margin-top:10px">
            <button type="button" class="btn" onclick="calificar('ingles')">Calificar Inglés</button>
            <div id="resultado-ingles" class="resultado"></div>
          </div>
        </form>
      </div>

    </section>

    <section id="contacto" class="section">
      <h3 style="color:#a5f3fc;margin-top:0">Contacto</h3>
      <p style="text-align:center">¿Quieres mejoras (temporizador por área, guardar historial o PDF más bonito)? Escríbeme: <strong>michelleflorez@example.com</strong></p>
      <div style="text-align:center;margin-top:12px">
        <button id="exportPdfBtn" class="btn" onclick="exportPDF()" style="display:none">📄 Exportar resultado a PDF</button>
      </div>
    </section>

  </main>

  <div class="footer">© 2025 Simulacros ICFES — Demo por Michelle Flórez</div>

  <script>
    // ---- Answers (A-D) for each subject (10 each) ----
    const answers = {
      matematicas: ['B','A','C','C','C','A','A','C','A','B'],
      lectura:    ['B','A','B','B','B','A','A','A','B','A'],
      naturales:  ['A','B','B','A','A','C','C','B','B','B'],
      sociales:   ['B','A','A','B','B','B','B','A','A','B'],
      ingles:     ['B','C','B','A','C','B','B','C','B','A']
    };

    // DOM elements
    const startBtn = document.getElementById('startBtn');
    const pauseBtn = document.getElementById('pauseBtn');
    const finishBtn = document.getElementById('finishBtn');
    const timerEl = document.getElementById('timer');
    const userNameEl = document.getElementById('userName');
    const exportPdfBtn = document.getElementById('exportPdfBtn');

    // Timer state
    const TOTAL_SECONDS = 45 * 60; // 45 minutes
    let remaining = TOTAL_SECONDS;
    let timerInterval = null;
    let running = false;
    let startTime = null;

    function formatTime(s) {
      const m = Math.floor(s/60).toString().padStart(2,'0');
      const sec = (s%60).toString().padStart(2,'0');
      return `${m}:${sec}`;
    }

    // Update UI timer
    function updateTimerDisplay() {
      timerEl.textContent = formatTime(remaining);
    }

    // Start timer
    startBtn.addEventListener('click', () => {
      const name = userNameEl.value.trim();
      if (!name) { alert('Por favor escribe tu nombre antes de iniciar.'); userNameEl.focus(); return; }
      if (running) return;
      running = true;
      startTime = Date.now();
      startBtn.style.display = 'none';
      pauseBtn.style.display = 'inline-block';
      finishBtn.style.display = 'inline-block';
      exportPdfBtn.style.display = 'none';
      // show simulacros section
      mostrar('simulacros');
      // begin countdown
      timerInterval = setInterval(()=>{
        remaining--;
        if (remaining <= 0) {
          remaining = 0;
          updateTimerDisplay();
          clearInterval(timerInterval);
          running = false;
          onTimeEnd();
        } else {
          updateTimerDisplay();
        }
      }, 1000);
    });

    // Pause/resume
    pauseBtn.addEventListener('click', () => {
      if (!running) {
        // resume
        running = true;
        pauseBtn.textContent = 'Pausar';
        timerInterval = setInterval(()=>{
          remaining--;
          if (remaining <= 0) { remaining = 0; updateTimerDisplay(); clearInterval(timerInterval); running=false; onTimeEnd(); }
          else updateTimerDisplay();
        },1000);
      } else {
        // pause
        running = false;
        pauseBtn.textContent = 'Reanudar';
        clearInterval(timerInterval);
      }
    });

    // Finish early
    finishBtn.addEventListener('click', () => {
      if (!confirm('¿Terminar y calificar ahora?')) return;
      clearInterval(timerInterval);
      running = false;
      onTimeEnd();
    });

    // When time ends or user finishes
    function onTimeEnd() {
      disableAllInputs();
      // grade all areas
      gradeAll();
      // show export button
      exportPdfBtn.style.display = 'inline-block';
      startBtn.style.display = 'inline-block';
      startBtn.textContent = 'Reiniciar simulacro';
      // reset start UI so the user can restart if wants (we do not auto-reset answers)
      pauseBtn.style.display = 'none';
      finishBtn.style.display = 'none';
    }

    // Disable inputs to prevent changes after time end
    function disableAllInputs(){
      document.querySelectorAll('input[type=radio]').forEach(i=>i.disabled=true);
    }

    // Enable inputs (for restart)
    function enableAllInputs(){
      document.querySelectorAll('input[type=radio]').forEach(i=>i.disabled=false);
    }

    // Reset function (clear answers and timer)
    function resetSimulacro(){
      remaining = TOTAL_SECONDS;
      updateTimerDisplay();
      clearInterval(timerInterval);
      running = false;
      startBtn.style.display = 'inline-block';
      startBtn.textContent = 'Iniciar simulacro';
      pauseBtn.style.display = 'none';
      finishBtn.style.display = 'none';
      exportPdfBtn.style.display = 'none';
      // clear results text
      ['matematicas','lectura','naturales','sociales','ingles'].forEach(k=>{
        const el = document.getElementById('resultado-' + k);
        if (el) el.textContent = '';
      });
      // enable inputs and clear selections
      document.querySelectorAll('input[type=radio]').forEach(i=>{ i.checked=false; i.disabled=false; });
    }

    // If user clicks start again after finishing, reset
    startBtn.addEventListener('click', () => {
      if (startBtn.textContent.includes('Reiniciar')) {
        if (!confirm('Se reiniciará el simulacro (se borrarán las respuestas). ¿Continuar?')) return;
        resetSimulacro();
      }
    });

    // Initialize timer display
    updateTimerDisplay();

    // Show/hide main sections
    function mostrar(id) {
      document.querySelectorAll('main > section').forEach(s => s.style.display = 'none');
      const el = document.getElementById(id);
      if (el) el.style.display = 'block';
      window.scrollTo({ top: 0, behavior: 'smooth' });
      if (id === 'simulacros') {
        setTimeout(()=> document.getElementById('simulacros').scrollIntoView({behavior:'smooth'}),120);
      }
    }
    mostrar('inicio');

    // Show specific simulacro panel
    function mostrarSimulacro(area) {
      mostrar('simulacros');
      document.querySelectorAll('.simulacro').forEach(s=>s.classList.remove('active'));
      const panel = document.getElementById('simulacro-' + area);
      if (panel) {
        panel.classList.add('active');
        setTimeout(()=> panel.scrollIntoView({behavior:'smooth',block:'start'}),120);
      }
    }

    // Grade single area and show result
    function calificar(area) {
      const key = area;
      const correct = answers[key];
      const form = document.getElementById('form-' + key);
      let acertadas = 0;
      for (let i = 0; i < correct.length; i++) {
        const q = 'q' + (i+1);
        const sel = form.querySelector(`input[name="${q}"]:checked`);
        if (sel && sel.value === correct[i]) acertadas++;
      }
      const total = correct.length;
      const porcentaje = Math.round((acertadas / total) * 100);
      const resultadoEl = document.getElementById('resultado-' + key);
      let comentario = '';
      if (porcentaje === 100) comentario = '¡Perfecto! 🎉';
      else if (porcentaje >= 80) comentario = 'Muy bien 👍';
      else if (porcentaje >= 50) comentario = 'Bien, repasa un poco más 🔎';
      else comentario = 'Necesitas estudiar más — ¡ánimo! 💪';
      resultadoEl.textContent = `Puntaje: ${acertadas} / ${total} — ${porcentaje}%\n${comentario}`;
      resultadoEl.style.whiteSpace = 'pre-line';
      return {acertadas, total, porcentaje};
    }

    // Grade all areas and collect results
    function gradeAll() {
      const areas = ['matematicas','lectura','naturales','sociales','ingles'];
      const summary = {};
      let totalAcertadas = 0, totalPreguntas = 0;
      areas.forEach(a=>{
        const res = calificar(a);
        summary[a] = res;
        totalAcertadas += res.acertadas;
        totalPreguntas += res.total;
      });
      // overall result
      const overallPct = Math.round((totalAcertadas / totalPreguntas) * 100);
      // show a modal-like alert (simple)
      setTimeout(()=> alert(`Simulacro terminado.\nResultado total: ${totalAcertadas} / ${totalPreguntas} — ${overallPct}%`), 200);
      // save last summary for export
      window.lastSummary = { name: userNameEl.value.trim() || 'Sin nombre', totalAcertadas, totalPreguntas, overallPct, byArea: summary, date: new Date().toLocaleString() };
      return window.lastSummary;
    }

    // Export the result to printable page (user can save as PDF)
    function exportPDF() {
      // ensure grading done
      if (!window.lastSummary) {
        if (!confirm('No hay resultado guardado. ¿Deseas calificar todo ahora y generar el PDF?')) return;
        gradeAll();
      }
      const s = window.lastSummary;
      // Build printable HTML
      const title = `Simulacro ICFES — Resultado de ${s.name}`;
      let body = `
        <div style="font-family:Arial,Helvetica,sans-serif;padding:20px;color:#042f3b">
          <h1 style="margin-bottom:4px">${title}</h1>
          <p style="margin-top:0;color:#555">${s.date}</p>
          <hr/>
          <h2 style="color:#0b5563">Resumen general</h2>
          <p><strong>Puntaje total:</strong> ${s.totalAcertadas} / ${s.totalPreguntas} — ${s.overallPct}%</p>
          <h3 style="color:#0b5563;margin-top:12px">Detalle por área</h3>
          <table style="width:100%;border-collapse:collapse">
            <thead><tr><th style="text-align:left;padding:6px;border-bottom:1px solid #ddd">Área</th><th style="text-align:left;padding:6px;border-bottom:1px solid #ddd">Aciertos</th><th style="text-align:left;padding:6px;border-bottom:1px solid #ddd">Total</th><th style="text-align:left;padding:6px;border-bottom:1px solid #ddd">%</th></tr></thead>
            <tbody>
      `;
      const areaNames = { matematicas:'Matemáticas', lectura:'Lectura Crítica', naturales:'Ciencias Naturales', sociales:'Sociales', ingles:'Inglés' };
      for (let k in s.byArea) {
        const v = s.byArea[k];
        body += `<tr><td style="padding:6px;border-bottom:1px solid #f0f0f0">${areaNames[k]}</td><td style="padding:6px;border-bottom:1px solid #f0f0f0">${v.acertadas}</td><td style="padding:6px;border-bottom:1px solid #f0f0f0">${v.total}</td><td style="padding:6px;border-bottom:1px solid #f0f0f0">${v.porcentaje}%</td></tr>`;
      }
      body += `
            </tbody>
          </table>
          <hr/>
          <p style="margin-top:14px;color:#666">Generado desde Simulacros ICFES — Demo por Michelle Flórez</p>
        </div>
      `;
      const w = window.open('', '_blank', 'width=800,height=900');
      w.document.write(`<!doctype html><html><head><title>${title}</title></head><body>${body}</body></html>`);
      w.document.close();
      // small delay to ensure render
      setTimeout(()=> w.print(), 500);
    }

    // Helper: call calificar for area name
    function calificar(area) {
      return window.calificarOriginal ? window.calificarOriginal(area) : (function(){
        // backwards compatibility: compute using mapping
        const map = { matematicas:'matematicas', lectura:'lectura', naturales:'naturales', sociales:'sociales', ingles:'ingles' };
        const key = map[area] || area;
        const correct = answers[key];
        const form = document.getElementById('form-' + key);
        let acertadas = 0;
        for (let i = 0; i < correct.length; i++) {
          const q = 'q' + (i+1);
          const sel = form.querySelector(`input[name="${q}"]:checked`);
          if (sel && sel.value === correct[i]) acertadas++;
        }
        const total = correct.length;
        const porcentaje = Math.round((acertadas / total) * 100);
        const resultadoEl = document.getElementById('resultado-' + key);
        let comentario = '';
        if (porcentaje === 100) comentario = '¡Perfecto! 🎉';
        else if (porcentaje >= 80) comentario = 'Muy bien 👍';
        else if (porcentaje >= 50) comentario = 'Bien, repasa un poco más 🔎';
        else comentario = 'Necesitas estudiar más — ¡ánimo! 💪';
        resultadoEl.textContent = `Puntaje: ${acertadas} / ${total} — ${porcentaje}%\n${comentario}`;
        resultadoEl.style.whiteSpace = 'pre-line';
        return {acertadas, total, porcentaje};
      })();
    }

    // Expose a stable calificarOriginal to use in gradeAll
    window.calificarOriginal = function(areaKey){
      const correct = answers[areaKey];
      const form = document.getElementById('form-' + areaKey);
      let acertadas = 0;
      for (let i = 0; i < correct.length; i++) {
        const q = 'q' + (i+1);
        const sel = form.querySelector(`input[name="${q}"]:checked`);
        if (sel && sel.value === correct[i]) acertadas++;
      }
      const total = correct.length;
      const porcentaje = Math.round((acertadas / total) * 100);
      const resultadoEl = document.getElementById('resultado-' + areaKey);
      let comentario = '';
      if (porcentaje === 100) comentario = '¡Perfecto! 🎉';
      else if (porcentaje >= 80) comentario = 'Muy bien 👍';
      else if (porcentaje >= 50) comentario = 'Bien, repasa un poco más 🔎';
      else comentario = 'Necesitas estudiar más — ¡ánimo! 💪';
      resultadoEl.textContent = `Puntaje: ${acertadas} / ${total} — ${porcentaje}%\n${comentario}`;
      resultadoEl.style.whiteSpace = 'pre-line';
      return {acertadas, total, porcentaje};
    };

    // Rebind calificar name to original impl
    calificar = function(areaKey){ return window.calificarOriginal(areaKey); };

    // Keyboard: if user changes name after finishing and clicks export, update name in export
    userNameEl.addEventListener('input', ()=> {
      if (window.lastSummary) window.lastSummary.name = userNameEl.value.trim() || window.lastSummary.name;
    });

    // Make sure export button reflects availability (it will be shown when grading done)
  </script>
</body>
</html>
