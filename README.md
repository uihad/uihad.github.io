<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>📚 Cuestionario COMPLETO: Primera Guerra Mundial</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 35px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 3px solid #667eea;
        }

        h1 {
            color: #667eea;
            font-size: 32px;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #666;
            font-size: 18px;
            margin-bottom: 10px;
        }

        .info-box {
            background: #f0f4ff;
            padding: 15px;
            border-radius: 10px;
            border-left: 4px solid #667eea;
            margin-bottom: 20px;
        }

        .info-box p {
            margin: 5px 0;
            color: #555;
            font-size: 14px;
        }

        .progress-container {
            margin-bottom: 25px;
        }

        .progress-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
            color: #666;
            font-weight: 600;
        }

        .progress-bar {
            width: 100%;
            height: 28px;
            background: #e0e0e0;
            border-radius: 15px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
            width: 0%;
            transition: width 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 13px;
        }

        .question-card {
            background: #f8f9fa;
            padding: 28px;
            border-radius: 15px;
            margin-bottom: 20px;
            border-left: 5px solid #667eea;
            display: none;
        }

        .question-card.active {
            display: block;
            animation: slideIn 0.5s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .question-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .question-number {
            color: #667eea;
            font-weight: bold;
            font-size: 15px;
        }

        .question-type {
            background: #667eea;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }

        .question-text {
            font-size: 19px;
            color: #333;
            margin-bottom: 22px;
            font-weight: 600;
            line-height: 1.5;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .option-btn {
            padding: 16px 20px;
            background: white;
            border: 2px solid #ddd;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 16px;
            text-align: left;
            position: relative;
        }

        .option-btn:hover {
            border-color: #667eea;
            background: #f0f4ff;
            transform: translateX(5px);
        }

        .option-btn.selected {
            background: #667eea;
            color: white;
            border-color: #667eea;
        }

        .option-btn.correct {
            background: #4caf50;
            color: white;
            border-color: #4caf50;
        }

        .option-btn.incorrect {
            background: #f44336;
            color: white;
            border-color: #f44336;
        }

        .option-btn.correct::after {
            content: "✓";
            position: absolute;
            right: 20px;
            font-size: 24px;
            font-weight: bold;
        }

        .option-btn.incorrect::after {
            content: "✗";
            position: absolute;
            right: 20px;
            font-size: 24px;
            font-weight: bold;
        }

        .input-answer {
            width: 100%;
            padding: 16px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s ease;
            font-family: inherit;
        }

        .input-answer:focus {
            outline: none;
            border-color: #667eea;
        }

        .feedback {
            margin-top: 18px;
            padding: 18px;
            border-radius: 10px;
            display: none;
            line-height: 1.6;
        }

        .feedback.show {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .feedback.correct {
            background: #e8f5e9;
            border: 2px solid #4caf50;
            color: #2e7d32;
        }

        .feedback.incorrect {
            background: #ffebee;
            border: 2px solid #f44336;
            color: #c62828;
        }

        .feedback strong {
            display: block;
            margin-bottom: 8px;
            font-size: 17px;
        }

        .button-group {
            display: flex;
            gap: 15px;
            margin-top: 22px;
        }

        .btn {
            flex: 1;
            padding: 16px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .btn-check {
            background: #667eea;
            color: white;
        }

        .btn-check:hover {
            background: #5568d3;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-next {
            background: #4caf50;
            color: white;
            display: none;
        }

        .btn-next:hover {
            background: #45a049;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(76, 175, 80, 0.4);
        }

        .btn-next.show {
            display: block;
        }

        .results {
            display: none;
            text-align: center;
            padding: 40px;
        }

        .results.show {
            display: block;
            animation: fadeIn 0.8s ease;
        }

        .score {
            font-size: 80px;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin: 20px 0;
        }

        .score-text {
            font-size: 26px;
            color: #333;
            margin-bottom: 15px;
        }

        .score-details {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
        }

        .score-details p {
            margin: 10px 0;
            font-size: 16px;
            color: #555;
        }

        .score-message {
            font-size: 18px;
            color: #666;
            margin: 25px 0;
            line-height: 1.6;
        }

        .btn-restart {
            background: #667eea;
            color: white;
            padding: 16px 45px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin: 10px;
        }

        .btn-restart:hover {
            background: #5568d3;
            transform: scale(1.05);
        }

        .lucky-checkbox {
            margin-top: 15px;
            padding: 12px;
            background: #fff3cd;
            border: 2px solid #ffc107;
            border-radius: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .lucky-checkbox:hover {
            background: #ffe69c;
            transform: translateX(3px);
        }

        .lucky-checkbox input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
        }

        .lucky-checkbox label {
            cursor: pointer;
            font-size: 15px;
            color: #856404;
            font-weight: 600;
        }

        .review-mode-banner {
            background: linear-gradient(135deg, #ff6b6b 0%, #ee5a6f 100%);
            color: white;
            padding: 15px;
            text-align: center;
            border-radius: 10px;
            margin-bottom: 20px;
            font-weight: bold;
            font-size: 18px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .emoji {
            font-size: 90px;
            margin-bottom: 20px;
        }

        .section-divider {
            text-align: center;
            margin: 30px 0;
            padding: 15px;
            background: linear-gradient(135deg, #667eea20 0%, #764ba220 100%);
            border-radius: 10px;
            font-weight: bold;
            color: #667eea;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>📚 Cuestionario COMPLETO</h1>
            <p class="subtitle">Primera Guerra Mundial - Tema 4 Completo</p>
            <div class="info-box">
                <p><strong>📋 Total de preguntas:</strong> 55 preguntas</p>
                <p><strong>🎯 Contenido:</strong> Causas, Países, Características, Desarrollo, Revolución Rusa, Consecuencias</p>
                <p><strong>⏱️ Tiempo estimado:</strong> 30-40 minutos</p>
            </div>
        </header>

        <div class="progress-container">
            <div class="progress-info">
                <span id="progressText">Pregunta 0 de 55</span>
                <span id="scoreProgress">Correctas: 0</span>
            </div>
            <div class="progress-bar">
                <div class="progress-fill" id="progressBar">0%</div>
            </div>
        </div>

        <div id="questionsContainer"></div>

        <div class="results" id="results">
            <div class="emoji" id="resultEmoji">🎉</div>
            <div class="score" id="finalScore">0%</div>
            <div class="score-text" id="scoreText">¡Puntuación Final!</div>
            <div class="score-details">
                <p><strong>Resumen de tu examen:</strong></p>
                <p id="correctCount">Respuestas correctas: 0</p>
                <p id="incorrectCount">Respuestas incorrectas: 0</p>
                <p id="percentageText">Porcentaje de acierto: 0%</p>
            </div>
            <div class="score-message" id="scoreMessage"></div>
            <div id="reviewButtonContainer"></div>
            <button class="btn-restart" onclick="restartQuiz()">🔄 Repetir Cuestionario Completo</button>
        </div>
    </div>

    <script>
        const questions = [
            // ========== SECCIÓN 1: CAUSAS DE LA GUERRA ==========
            {
                section: "CAUSAS DE LA PRIMERA GUERRA MUNDIAL",
                type: "section"
            },
            {
                id: 1,
                type: 'multiple',
                question: '¿En qué año estalló la Primera Guerra Mundial?',
                options: ['1912', '1914', '1916', '1918'],
                correct: 1,
                explanation: 'La Primera Guerra Mundial estalló en 1914, específicamente tras el asesinato del archiduque Francisco Fernando en junio de ese año.'
            },
            {
                id: 2,
                type: 'multiple',
                question: '¿Cómo se llamaba el clima de tensión en Europa antes de 1914?',
                options: ['Guerra fría', 'Paz armada', 'Belle Époque', 'Detente'],
                correct: 1,
                explanation: 'Se llamaba "paz armada" porque, aunque no había guerra abierta, todas las potencias se estaban armando y preparando para el conflicto.'
            },
            {
                id: 3,
                type: 'multiple',
                question: '¿Qué tres países formaban la Triple Alianza?',
                options: [
                    'Francia, Rusia y Reino Unido',
                    'Alemania, Austria-Hungría e Italia',
                    'Alemania, Francia e Italia',
                    'Austria-Hungría, Rusia e Italia'
                ],
                correct: 1,
                explanation: 'La Triple Alianza (1882) estaba formada por Alemania, Austria-Hungría e Italia. Aunque Italia después se mantuvo neutral al inicio.'
            },
            {
                id: 4,
                type: 'multiple',
                question: '¿Qué tres países formaban la Triple Entente?',
                options: [
                    'Alemania, Austria e Italia',
                    'Francia, Alemania y Rusia',
                    'Francia, Rusia y Reino Unido',
                    'Reino Unido, Italia y Francia'
                ],
                correct: 2,
                explanation: 'La Triple Entente (1907) estaba formada por Francia, Rusia y Reino Unido. Se unieron para hacer frente al poder de Alemania.'
            },
            {
                id: 5,
                type: 'multiple',
                question: '¿Qué dos regiones reclamaba Francia que estaban bajo control alemán?',
                options: [
                    'Normandía y Bretaña',
                    'Alsacia y Lorena',
                    'Provenza y Saboya',
                    'Flandes y Valonia'
                ],
                correct: 1,
                explanation: 'Francia reclamaba Alsacia y Lorena, territorios perdidos ante Alemania en la guerra franco-prusiana de 1871.'
            },
            {
                id: 6,
                type: 'multiple',
                question: '¿Por qué Alemania tenía rivalidad con Francia en Marruecos?',
                options: [
                    'Porque Marruecos era colonia alemana',
                    'Porque Alemania quería expandirse y llegó tarde al reparto colonial',
                    'Porque Francia había invadido Alemania',
                    'Porque Marruecos atacó a Alemania'
                ],
                correct: 1,
                explanation: 'Alemania había llegado tarde a la carrera colonial y quería expandirse en Marruecos, donde Francia ya tenía influencia.'
            },
            {
                id: 7,
                type: 'multiple',
                question: '¿En qué año se anexionó Bosnia-Herzegovina al Imperio austrohúngaro?',
                options: ['1905', '1908', '1912', '1914'],
                correct: 1,
                explanation: 'Austria-Hungría anexionó Bosnia-Herzegovina en 1908, lo que aumentó las tensiones en los Balcanes.'
            },
            {
                id: 8,
                type: 'multiple',
                question: '¿Qué país eslavo se consolidó como potencia en los Balcanes con el apoyo de Rusia?',
                options: ['Bulgaria', 'Albania', 'Serbia', 'Rumanía'],
                correct: 2,
                explanation: 'Serbia se consolidó como la principal potencia de los Balcanes tras las guerras balcánicas (1912-1913), con el apoyo de Rusia.'
            },
            {
                id: 9,
                type: 'multiple',
                question: '¿Quién fue asesinado en Sarajevo en junio de 1914?',
                options: [
                    'El emperador de Austria',
                    'El archiduque Francisco Fernando',
                    'El zar de Rusia',
                    'El káiser alemán'
                ],
                correct: 1,
                explanation: 'El archiduque Francisco Fernando, heredero de la corona austriaca, fue asesinado en Sarajevo (capital de Bosnia) en junio de 1914.'
            },
            {
                id: 10,
                type: 'multiple',
                question: '¿Qué país neutral invadió Alemania, provocando la entrada de Reino Unido en la guerra?',
                options: ['Suiza', 'Holanda', 'Bélgica', 'Dinamarca'],
                correct: 2,
                explanation: 'Alemania invadió Bélgica, un país neutral. Esta invasión hizo que el Reino Unido declarase la guerra a Alemania.'
            },
            {
                id: 11,
                type: 'truefalse',
                question: 'Italia se mantuvo neutral al inicio de la guerra a pesar de formar parte de la Triple Alianza.',
                correct: true,
                explanation: 'VERDADERO. A pesar de formar parte de la Triple Alianza, Italia se mantuvo neutral al inicio. Después se unió a la Entente en 1915.'
            },
            {
                id: 12,
                type: 'truefalse',
                question: 'Alemania llegó tarde al reparto colonial porque se unificó tardíamente en 1871.',
                correct: true,
                explanation: 'VERDADERO. Alemania se unificó en 1871 y llegó con retraso a la carrera colonial, lo que generó tensiones.'
            },
            {
                id: 13,
                type: 'truefalse',
                question: 'Reino Unido y Alemania eran aliados antes de la guerra.',
                correct: false,
                explanation: 'FALSO. Reino Unido y Alemania NO eran aliados. Existía una fuerte rivalidad entre ambos por la hegemonía de Europa.'
            },
            {
                id: 14,
                type: 'truefalse',
                question: 'Las guerras balcánicas de 1912 y 1913 empeoraron la situación en los Balcanes.',
                correct: true,
                explanation: 'VERDADERO. Las dos guerras balcánicas (1912 y 1913) consolidaron a Serbia y aumentaron las tensiones en la zona.'
            },
            
            // ========== SECCIÓN 2: CARACTERÍSTICAS DE LA GUERRA ==========
            {
                section: "CARACTERÍSTICAS DE LA GUERRA",
                type: "section"
            },
            {
                id: 15,
                type: 'multiple',
                question: '¿Por qué se llamó "La Gran Guerra" a la Primera Guerra Mundial?',
                options: [
                    'Por su larga duración',
                    'Por movilizar a toda la población y usar armas mortíferas',
                    'Por el número de países participantes',
                    'Por los tratados de paz'
                ],
                correct: 1,
                explanation: 'Se llamó "La Gran Guerra" porque movilizó a toda la población (no solo soldados) y se usaron armas muy destructivas y mortíferas.'
            },
            {
                id: 16,
                type: 'multiple',
                question: '¿Qué porcentaje de la mano de obra industrial constituían las mujeres al final de la guerra en Alemania y Gran Bretaña?',
                options: ['15%', '25%', '35%', '45%'],
                correct: 2,
                explanation: 'Al final de la guerra, las mujeres constituían el 35% de la mano de obra industrial en Alemania y Gran Bretaña.'
            },
            {
                id: 17,
                type: 'multiple',
                question: '¿Qué nuevas armas se utilizaron por primera vez en esta guerra?',
                options: [
                    'Solo rifles y cañones',
                    'Tanques, aviones y gases tóxicos',
                    'Bombas nucleares',
                    'Solo ametralladoras'
                ],
                correct: 1,
                explanation: 'Se usaron por primera vez tanques, aviones de combate, gases tóxicos, ametralladoras más potentes y bombardeos aéreos.'
            },
            {
                id: 18,
                type: 'truefalse',
                question: 'Solo los soldados participaron en la guerra, la población civil no se vio afectada.',
                correct: false,
                explanation: 'FALSO. La población civil se vio muy afectada: las mujeres trabajaron en fábricas, hubo bombardeos de ciudades y escasez de alimentos.'
            },
            {
                id: 19,
                type: 'truefalse',
                question: 'Se usó propaganda moderna para movilizar a la opinión pública y comprometerla en la guerra.',
                correct: true,
                explanation: 'VERDADERO. Se usaron técnicas modernas de propaganda para convencer a la población de apoyar la guerra.'
            },
            {
                id: 20,
                type: 'truefalse',
                question: 'Las industrias NO fueron reconvertidas para fabricar armamento durante la guerra.',
                correct: false,
                explanation: 'FALSO. Las industrias fueron reconvertidas para fabricar armamento, municiones y material bélico.'
            },

            // ========== SECCIÓN 3: DESARROLLO DE LA GUERRA ==========
            {
                section: "DESARROLLO DE LA GUERRA",
                type: "section"
            },
            {
                id: 21,
                type: 'multiple',
                question: '¿Cómo se llama la primera fase de la guerra en 1914 con ataques rápidos?',
                options: ['Guerra de trincheras', 'Guerra de movimientos', 'Guerra de desgaste', 'Guerra relámpago'],
                correct: 1,
                explanation: 'La Guerra de movimientos (1914) fue la primera fase con ataques rápidos. Alemania intentó conquistar Francia rápidamente.'
            },
            {
                id: 22,
                type: 'multiple',
                question: '¿En qué batalla se frenó el avance alemán en Francia en 1914?',
                options: ['Batalla de Verdún', 'Batalla del Marne', 'Batalla del Somme', 'Batalla de Tannenberg'],
                correct: 1,
                explanation: 'En la Batalla del Marne (1914) se frenó el avance alemán hacia París, comenzando el estancamiento de la guerra.'
            },
            {
                id: 23,
                type: 'multiple',
                question: '¿Cómo se llama la fase de la guerra donde los ejércitos luchaban desde zanjas en la tierra?',
                options: ['Guerra de movimientos', 'Guerra de trincheras', 'Guerra submarina', 'Guerra de posiciones'],
                correct: 1,
                explanation: 'La Guerra de trincheras (1915-1916) fue cuando los ejércitos se estancaron y luchaban desde zanjas excavadas en la tierra.'
            },
            {
                id: 24,
                type: 'multiple',
                question: '¿Qué características tenía la guerra de trincheras?',
                options: [
                    'Avances rápidos y victorias decisivas',
                    'Estancamiento, batallas largas y miles de muertos por pocos metros',
                    'Combates aéreos principalmente',
                    'Guerras navales exclusivamente'
                ],
                correct: 1,
                explanation: 'La guerra de trincheras se caracterizó por el estancamiento, batallas larguísimas (como Verdún y Somme) con miles de muertos por ganar solo unos metros.'
            },
            {
                id: 25,
                type: 'multiple',
                question: '¿Qué año fue crucial con la salida de Rusia y la entrada de Estados Unidos en la guerra?',
                options: ['1914', '1915', '1917', '1918'],
                correct: 2,
                explanation: '1917 fue el año crucial: Rusia se retiró tras la Revolución bolchevique y Estados Unidos entró del lado de la Entente.'
            },
            {
                id: 26,
                type: 'multiple',
                question: '¿Qué tratado firmó Rusia con Alemania para retirarse de la guerra?',
                options: [
                    'Tratado de Versalles',
                    'Tratado de Brest-Litovsk',
                    'Tratado de Saint-Germain',
                    'Tratado de Trianon'
                ],
                correct: 1,
                explanation: 'El Tratado de Brest-Litovsk (1918) fue firmado entre Rusia y Alemania. Rusia tuvo que aceptar grandes pérdidas territoriales.'
            },
            {
                id: 27,
                type: 'multiple',
                question: '¿Cuándo terminó la Primera Guerra Mundial?',
                options: [
                    '11 de noviembre de 1917',
                    '11 de noviembre de 1918',
                    '28 de junio de 1919',
                    '1 de septiembre de 1918'
                ],
                correct: 1,
                explanation: 'La Primera Guerra Mundial terminó el 11 de noviembre de 1918 cuando Alemania firmó el armisticio.'
            },
            {
                id: 28,
                type: 'truefalse',
                question: 'La guerra de movimientos duró toda la guerra hasta 1918.',
                correct: false,
                explanation: 'FALSO. La guerra de movimientos solo fue la primera fase en 1914. Después vino la guerra de trincheras (1915-1916) y el final en 1918.'
            },
            {
                id: 29,
                type: 'truefalse',
                question: 'Estados Unidos entró en la guerra en 1917 del lado de la Entente.',
                correct: true,
                explanation: 'VERDADERO. Estados Unidos entró en 1917 apoyando a Francia, Reino Unido y sus aliados, lo que fue decisivo para la victoria.'
            },
            {
                id: 30,
                type: 'truefalse',
                question: 'Verdún y Somme fueron dos de las batallas más sangrientas de la guerra de trincheras.',
                correct: true,
                explanation: 'VERDADERO. Verdún y Somme (1916) fueron batallas larguísimas con cientos de miles de muertos por avanzar apenas unos kilómetros.'
            },

            // ========== SECCIÓN 4: REVOLUCIÓN RUSA ==========
            {
                section: "REVOLUCIÓN RUSA 1917",
                type: "section"
            },
            {
                id: 31,
                type: 'multiple',
                question: '¿Quién era el zar de Rusia al inicio de la Primera Guerra Mundial?',
                options: ['Alejandro II', 'Nicolás I', 'Nicolás II', 'Alejandro III'],
                correct: 2,
                explanation: 'Nicolás II era el zar de Rusia. Tenía poder absoluto (autocrático) y gobernaba sin constitución ni parlamento.'
            },
            {
                id: 32,
                type: 'multiple',
                question: '¿En qué mes y año estalló la primera revolución que derrocó al zar?',
                options: ['Febrero de 1917', 'Octubre de 1917', 'Marzo de 1918', 'Noviembre de 1916'],
                correct: 0,
                explanation: 'En febrero de 1917 estalló la revolución que derrocó al zar Nicolás II y estableció un gobierno provisional.'
            },
            {
                id: 33,
                type: 'multiple',
                question: '¿Qué eran los sóviets?',
                options: [
                    'El ejército ruso',
                    'Organizaciones de trabajadores y soldados',
                    'Los nobles rusos',
                    'La policía secreta'
                ],
                correct: 1,
                explanation: 'Los sóviets eran organizaciones de trabajadores y soldados que pedían la retirada de la guerra y reformas sociales.'
            },
            {
                id: 34,
                type: 'multiple',
                question: '¿Quién lideró a los bolcheviques en la Revolución de Octubre de 1917?',
                options: ['Stalin', 'Trotski', 'Lenin', 'Kerenski'],
                correct: 2,
                explanation: 'Lenin lideró a los bolcheviques en la Revolución de Octubre de 1917, que derrocó al gobierno provisional.'
            },
            {
                id: 35,
                type: 'multiple',
                question: '¿Qué fecha fue la Revolución de Octubre (segunda revolución rusa)?',
                options: [
                    '25 de febrero de 1917',
                    '25 de octubre de 1917',
                    '7 de noviembre de 1917',
                    '1 de mayo de 1918'
                ],
                correct: 1,
                explanation: 'La Revolución de Octubre fue el 25 de octubre de 1917 (calendario ruso). Los bolcheviques tomaron el poder y establecieron un gobierno soviético.'
            },
            {
                id: 36,
                type: 'multiple',
                question: '¿Qué decidió el nuevo gobierno bolchevique respecto a la guerra?',
                options: [
                    'Continuar luchando',
                    'Firmar la paz con Alemania',
                    'Aliarse con Estados Unidos',
                    'Invadir Austria'
                ],
                correct: 1,
                explanation: 'El gobierno bolchevique firmó la paz con Alemania (Tratado de Brest-Litovsk, 1918) para retirarse de la guerra.'
            },
            {
                id: 37,
                type: 'multiple',
                question: '¿Qué significó la dictadura del proletariado según Lenin?',
                options: [
                    'Democracia para todos',
                    'El gobierno de la nobleza',
                    'Las fuerzas obreras imponiéndose sobre la burguesía',
                    'El gobierno de los campesinos solamente'
                ],
                correct: 2,
                explanation: 'La dictadura del proletariado, según Lenin, significaba que las fuerzas obreras debían imponerse sobre las de la burguesía.'
            },
            {
                id: 38,
                type: 'multiple',
                question: '¿Qué se creó en 1922 después de la guerra civil rusa?',
                options: [
                    'El Imperio Ruso',
                    'La República Rusa',
                    'La URSS (Unión de Repúblicas Socialistas Soviéticas)',
                    'La Federación Rusa'
                ],
                correct: 2,
                explanation: 'En 1922 se creó la URSS (Unión de Repúblicas Socialistas Soviéticas), que agrupaba las nacionalidades del viejo imperio.'
            },
            {
                id: 39,
                type: 'truefalse',
                question: 'El zar Nicolás II tenía un poder autocrático (absoluto) sin constitución ni parlamento.',
                correct: true,
                explanation: 'VERDADERO. Nicolás II gobernaba de forma autocrática: poder absoluto, sin constitución y sin rendir cuentas a un parlamento.'
            },
            {
                id: 40,
                type: 'truefalse',
                question: 'Rusia estaba bien preparada para la Primera Guerra Mundial con un ejército moderno.',
                correct: false,
                explanation: 'FALSO. Rusia NO estaba preparada: el ejército estaba mal equipado, deficientemente armado y mal dirigido.'
            },
            {
                id: 41,
                type: 'truefalse',
                question: 'La escasez de alimentos y las derrotas militares contribuyeron a la Revolución de Febrero de 1917.',
                correct: true,
                explanation: 'VERDADERO. La escasez, el hambre, las derrotas militares y el descontento popular provocaron la revolución que derrocó al zar.'
            },
            {
                id: 42,
                type: 'truefalse',
                question: 'El gobierno provisional continuó la guerra tras la Revolución de Febrero.',
                correct: true,
                explanation: 'VERDADERO. El gobierno provisional decidió mantener los compromisos con sus aliados y continuar en la guerra, lo que aumentó el descontento.'
            },
            {
                id: 43,
                type: 'truefalse',
                question: 'León Trotski dirigió el Ejército Rojo durante la guerra civil rusa.',
                correct: true,
                explanation: 'VERDADERO. Trotski organizó y dirigió el Ejército Rojo (bolchevique) que venció al Ejército Blanco en la guerra civil (1918-1921).'
            },

            // ========== SECCIÓN 5: CONSECUENCIAS DE LA GUERRA ==========
            {
                section: "CONSECUENCIAS DE LA GUERRA",
                type: "section"
            },
            {
                id: 44,
                type: 'multiple',
                question: '¿Cuántos millones de personas murieron aproximadamente en la Primera Guerra Mundial?',
                options: ['5 millones', '10 millones', '15 millones', '20 millones'],
                correct: 1,
                explanation: 'Murieron casi 10 millones de personas, sobre todo alemanes, franceses y rusos. Además hubo 6 millones de inválidos.'
            },
            {
                id: 45,
                type: 'multiple',
                question: '¿En qué porcentaje se redujo el potencial industrial de Europa tras la guerra?',
                options: ['20%', '30%', '40%', '50%'],
                correct: 2,
                explanation: 'El potencial industrial de Europa se redujo en un 40%, y el agrícola en un 30%. Europa quedó devastada.'
            },
            {
                id: 46,
                type: 'multiple',
                question: '¿Qué país se convirtió en el gran beneficiario económico de la guerra?',
                options: ['Reino Unido', 'Francia', 'Estados Unidos', 'Japón'],
                correct: 2,
                explanation: 'Estados Unidos fue el gran beneficiario. Se convirtió en líder de las finanzas mundiales mientras Europa quedaba arruinada.'
            },
            {
                id: 47,
                type: 'multiple',
                question: '¿Dónde se celebró la conferencia de paz en 1919?',
                options: ['Londres', 'París', 'Ginebra', 'Versalles'],
                correct: 1,
                explanation: 'En París se celebró en enero de 1919 la conferencia para establecer las condiciones de paz. De ahí el nombre "Paz de París".'
            },
            {
                id: 48,
                type: 'multiple',
                question: '¿Quién propuso los "14 Puntos" para una paz justa?',
                options: [
                    'El primer ministro británico',
                    'El presidente estadounidense Wilson',
                    'El primer ministro francés',
                    'El káiser alemán'
                ],
                correct: 1,
                explanation: 'El presidente estadounidense Thomas Wilson propuso los "14 Puntos", un manifiesto para una paz justa sin revancha.'
            },
            {
                id: 49,
                type: 'multiple',
                question: '¿Cuál fue el tratado de paz más importante firmado con Alemania?',
                options: [
                    'Tratado de París',
                    'Tratado de Versalles',
                    'Tratado de Saint-Germain',
                    'Tratado de Brest-Litovsk'
                ],
                correct: 1,
                explanation: 'El Tratado de Versalles (1919) fue el más importante. Declaraba a Alemania culpable y le imponía durísimas condiciones.'
            },
            {
                id: 50,
                type: 'multiple',
                question: '¿Qué le exigía el Tratado de Versalles a Alemania?',
                options: [
                    'Solo disculparse',
                    'Pagar reparaciones, desarmarse, ceder territorios y renunciar a colonias',
                    'Aliarse con Francia',
                    'Cambiar de gobierno solamente'
                ],
                correct: 1,
                explanation: 'El Tratado de Versalles exigía a Alemania: pagar reparaciones de guerra, desarmarse totalmente, ceder territorios y renunciar a todas sus colonias.'
            },
            {
                id: 51,
                type: 'multiple',
                question: '¿Cómo llamaron los alemanes al Tratado de Versalles?',
                options: ['Paz justa', 'Diktat (imposición humillante)', 'Acuerdo equitativo', 'Tratado honorable'],
                correct: 1,
                explanation: 'Los alemanes lo llamaron "diktat" (imposición humillante). Lo vieron como una humillación que exacerbó su nacionalismo.'
            },
            {
                id: 52,
                type: 'multiple',
                question: '¿Qué otros tratados se firmaron además del de Versalles?',
                options: [
                    'Saint-Germain, Trianon, Neuilly y Sèvres',
                    'Solo el de Versalles',
                    'Versalles y Brest-Litovsk',
                    'París y Londres'
                ],
                correct: 0,
                explanation: 'Además de Versalles (Alemania), se firmaron: Saint-Germain (Austria), Trianon (Hungría), Neuilly (Bulgaria) y Sèvres (Turquía).'
            },
            {
                id: 53,
                type: 'truefalse',
                question: 'Europa perdió su hegemonía económica mundial tras la Primera Guerra Mundial.',
                correct: true,
                explanation: 'VERDADERO. Europa perdió su hegemonía. Estados Unidos se convirtió en la nueva potencia mundial económica y financiera.'
            },
            {
                id: 54,
                type: 'truefalse',
                question: 'Los años posteriores a la guerra fueron de prosperidad para toda Europa.',
                correct: false,
                explanation: 'FALSO. Fueron años de penurias, hambre, subida de precios, manifestaciones y huelgas. Hubo gran malestar social.'
            },
            {
                id: 55,
                type: 'truefalse',
                question: 'Francia quería una paz suave con Alemania sin exigir compensaciones.',
                correct: false,
                explanation: 'FALSO. Francia quería recibir fuertes compensaciones de Alemania por las destrucciones y costes de la guerra. Rechazó la idea de paz sin revancha.'
            }
        ];

        let currentQuestion = 0;
        let score = 0;
        let userAnswers = [];
        let totalQuestions = questions.filter(q => q.type !== 'section').length;
        let failedQuestions = []; // Preguntas falladas o marcadas como "de casualidad"
        let markedAsLucky = {}; // Preguntas marcadas como "acerté de casualidad"
        let isReviewMode = false; // Modo de repaso de preguntas falladas
        let reviewQuestions = []; // Lista de preguntas a repasar
        let originalQuestions = []; // Respaldo de las preguntas originales

        function initQuiz() {
            renderQuestion();
            updateProgress();
        }

        function renderQuestion() {
            const q = questions[currentQuestion];
            const container = document.getElementById('questionsContainer');
            
            // Si es una sección divisoria
            if (q.type === 'section') {
                container.innerHTML = `
                    <div class="section-divider">
                        📖 ${q.section}
                    </div>
                `;
                setTimeout(() => {
                    currentQuestion++;
                    renderQuestion();
                }, 1500);
                return;
            }
            
            let optionsHTML = '';
            let typeLabel = '';
            
            if (q.type === 'multiple') {
                typeLabel = 'Opción múltiple';
                optionsHTML = '<div class="options">';
                q.options.forEach((option, index) => {
                    optionsHTML += `<button class="option-btn" onclick="selectOption(${index})">${option}</button>`;
                });
                optionsHTML += '</div>';
            } else if (q.type === 'truefalse') {
                typeLabel = 'Verdadero o Falso';
                optionsHTML = `
                    <div class="options">
                        <button class="option-btn" onclick="selectOption(true)">✅ VERDADERO</button>
                        <button class="option-btn" onclick="selectOption(false)">❌ FALSO</button>
                    </div>
                `;
            }
            
            const questionNumber = questions.slice(0, currentQuestion + 1).filter(q => q.type !== 'section').length;
            
            // Banner de modo repaso
            const reviewBanner = isReviewMode ? '<div class="review-mode-banner">🔄 MODO REPASO - Repasando preguntas falladas</div>' : '';
            
            container.innerHTML = `
                ${reviewBanner}
                <div class="question-card active">
                    <div class="question-header">
                        <div class="question-number">Pregunta ${questionNumber} de ${isReviewMode ? reviewQuestions.length : totalQuestions}</div>
                        <div class="question-type">${typeLabel}</div>
                    </div>
                    <div class="question-text">${q.question}</div>
                    ${optionsHTML}
                    <div class="lucky-checkbox" onclick="toggleLucky()">
                        <input type="checkbox" id="luckyCheck" ${markedAsLucky[currentQuestion] ? 'checked' : ''}>
                        <label for="luckyCheck">🎲 Lo acerté de casualidad (repasar después)</label>
                    </div>
                    <div class="feedback" id="feedback"></div>
                    <div class="button-group">
                        <button class="btn btn-check" onclick="checkAnswer()">✓ Comprobar Respuesta</button>
                        <button class="btn btn-next" id="btnNext" onclick="nextQuestion()">Siguiente →</button>
                    </div>
                </div>
            `;
        }

        function selectOption(value) {
            const buttons = document.querySelectorAll('.option-btn');
            buttons.forEach(btn => btn.classList.remove('selected'));
            
            if (typeof value === 'number') {
                buttons[value].classList.add('selected');
                userAnswers[currentQuestion] = value;
            } else {
                const index = value ? 0 : 1;
                buttons[index].classList.add('selected');
                userAnswers[currentQuestion] = value;
            }
        }

        function toggleLucky() {
            const checkbox = document.getElementById('luckyCheck');
            checkbox.checked = !checkbox.checked;
            markedAsLucky[currentQuestion] = checkbox.checked;
        }

        function checkAnswer() {
            const q = questions[currentQuestion];
            const userAnswer = userAnswers[currentQuestion];
            
            if (userAnswer === undefined) {
                alert('⚠️ Por favor, selecciona una respuesta antes de comprobar.');
                return;
            }
            
            const feedback = document.getElementById('feedback');
            const buttons = document.querySelectorAll('.option-btn');
            const btnCheck = document.querySelector('.btn-check');
            const btnNext = document.getElementById('btnNext');
            const luckyCheckbox = document.getElementById('luckyCheck');
            
            let isCorrect = false;
            
            if (q.type === 'multiple') {
                isCorrect = userAnswer === q.correct;
                buttons.forEach((btn, index) => {
                    btn.disabled = true;
                    if (index === q.correct) {
                        btn.classList.add('correct');
                    } else if (index === userAnswer && !isCorrect) {
                        btn.classList.add('incorrect');
                    }
                });
            } else if (q.type === 'truefalse') {
                isCorrect = userAnswer === q.correct;
                buttons.forEach((btn, index) => {
                    btn.disabled = true;
                    const btnValue = index === 0;
                    if (btnValue === q.correct) {
                        btn.classList.add('correct');
                    } else if (btnValue === userAnswer && !isCorrect) {
                        btn.classList.add('incorrect');
                    }
                });
            }
            
            // Registrar pregunta fallada o marcada como casualidad
            if (!isCorrect || markedAsLucky[currentQuestion]) {
                if (!failedQuestions.includes(currentQuestion)) {
                    failedQuestions.push(currentQuestion);
                }
            }
            
            if (isCorrect) {
                score++;
                feedback.className = 'feedback correct show';
                if (markedAsLucky[currentQuestion]) {
                    feedback.innerHTML = `<strong>✅ ¡Correcto! (Marcada para repasar)</strong><br>${q.explanation}<br><br><em style="color: #f57c00;">💡 Has marcado esta pregunta como "acertada de casualidad". La repasarás al final.</em>`;
                } else {
                    feedback.innerHTML = `<strong>✅ ¡Correcto!</strong><br>${q.explanation}`;
                }
            } else {
                feedback.className = 'feedback incorrect show';
                feedback.innerHTML = `<strong>❌ Incorrecto</strong><br>${q.explanation}<br><br><em style="color: #d32f2f;">📝 Esta pregunta será repasada al final del cuestionario.</em>`;
            }
            
            // Deshabilitar el checkbox después de comprobar
            luckyCheckbox.style.pointerEvents = 'none';
            luckyCheckbox.style.opacity = '0.6';
            
            btnCheck.style.display = 'none';
            btnNext.classList.add('show');
            updateProgress();
        }

        function nextQuestion() {
            currentQuestion++;
            
            if (currentQuestion < questions.length) {
                renderQuestion();
                updateProgress();
            } else {
                showResults();
            }
        }

        function updateProgress() {
            const answeredQuestions = questions.slice(0, currentQuestion + 1).filter(q => q.type !== 'section').length;
            const progress = (answeredQuestions / totalQuestions) * 100;
            const progressBar = document.getElementById('progressBar');
            const progressText = document.getElementById('progressText');
            const scoreProgress = document.getElementById('scoreProgress');
            
            progressBar.style.width = progress + '%';
            progressBar.textContent = Math.round(progress) + '%';
            progressText.textContent = `Pregunta ${answeredQuestions} de ${totalQuestions}`;
            scoreProgress.textContent = `Correctas: ${score}`;
        }

        function showResults() {
            const questionsContainer = document.getElementById('questionsContainer');
            const results = document.getElementById('results');
            const finalScore = document.getElementById('finalScore');
            const scoreText = document.getElementById('scoreText');
            const scoreMessage = document.getElementById('scoreMessage');
            const resultEmoji = document.getElementById('resultEmoji');
            const progressBar = document.getElementById('progressBar');
            const correctCount = document.getElementById('correctCount');
            const incorrectCount = document.getElementById('incorrectCount');
            const percentageText = document.getElementById('percentageText');
            const reviewButtonContainer = document.getElementById('reviewButtonContainer');
            
            progressBar.style.width = '100%';
            progressBar.textContent = '100%';
            
            questionsContainer.style.display = 'none';
            results.classList.add('show');
            
            const percentage = Math.round((score / totalQuestions) * 100);
            const incorrect = totalQuestions - score;
            
            finalScore.textContent = percentage + '%';
            scoreText.textContent = `Tu puntuación: ${score}/${totalQuestions}`;
            correctCount.textContent = `✅ Respuestas correctas: ${score}`;
            incorrectCount.textContent = `❌ Respuestas incorrectas: ${incorrect}`;
            percentageText.textContent = `📊 Porcentaje de acierto: ${percentage}%`;
            
            // Mostrar botón de repaso si hay preguntas falladas
            if (failedQuestions.length > 0 && !isReviewMode) {
                reviewButtonContainer.innerHTML = `
                    <div style="background: #fff3cd; padding: 15px; border-radius: 10px; margin: 20px 0; border: 2px solid #ffc107;">
                        <p style="color: #856404; margin-bottom: 10px; font-weight: 600;">
                            📝 Tienes ${failedQuestions.length} pregunta(s) para repasar
                        </p>
                        <button class="btn-restart" onclick="startReviewMode()" style="background: #ff9800;">
                            🔄 Repasar Preguntas Falladas
                        </button>
                    </div>
                `;
            } else if (isReviewMode) {
                reviewButtonContainer.innerHTML = `
                    <div style="background: #e8f5e9; padding: 15px; border-radius: 10px; margin: 20px 0; border: 2px solid #4caf50;">
                        <p style="color: #2e7d32; font-weight: 600;">
                            ✅ ¡Has completado el repaso de preguntas falladas!
                        </p>
                    </div>
                `;
            }
            
            if (percentage >= 90) {
                resultEmoji.textContent = '🏆';
                scoreMessage.innerHTML = `
                    <strong>¡EXCELENTE!</strong><br>
                    Dominas completamente el tema de la Primera Guerra Mundial. 
                    Tienes un conocimiento profundo de las causas, desarrollo, 
                    revolución rusa y consecuencias. ¡Estás más que preparado para el examen!
                `;
            } else if (percentage >= 80) {
                resultEmoji.textContent = '🎉';
                scoreMessage.innerHTML = `
                    <strong>¡MUY BIEN!</strong><br>
                    Tienes un muy buen conocimiento del tema. 
                    Repasa las ${incorrect} preguntas que fallaste prestando atención a las explicaciones, 
                    y estarás perfecto para el examen.
                `;
            } else if (percentage >= 70) {
                resultEmoji.textContent = '👍';
                scoreMessage.innerHTML = `
                    <strong>BIEN</strong><br>
                    Vas por buen camino, pero necesitas reforzar algunos conceptos. 
                    Lee de nuevo el resumen de los apartados donde fallaste y repite el cuestionario. 
                    Con un poco más de estudio estarás listo.
                `;
            } else if (percentage >= 60) {
                resultEmoji.textContent = '📖';
                scoreMessage.innerHTML = `
                    <strong>NECESITAS REPASAR</strong><br>
                    Tienes algunos conceptos claros, pero hay lagunas importantes. 
                    Vuelve a leer el temario con calma, especialmente las secciones donde más fallaste. 
                    Después repite el cuestionario. ¡Tú puedes!
                `;
            } else {
                resultEmoji.textContent = '📚';
                scoreMessage.innerHTML = `
                    <strong>DEBES ESTUDIAR MÁS</strong><br>
                    Necesitas dedicar más tiempo al estudio del tema. 
                    Lee el resumen completo varias veces, toma notas de los puntos importantes, 
                    y cuando te sientas preparado, vuelve a hacer el cuestionario. 
                    No te desanimes, con dedicación lo conseguirás.
                `;
            }
        }

        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            userAnswers = [];
            failedQuestions = [];
            markedAsLucky = {};
            isReviewMode = false;
            reviewQuestions = [];
            
            document.getElementById('questionsContainer').style.display = 'block';
            document.getElementById('results').classList.remove('show');
            document.getElementById('progressText').textContent = 'Pregunta 0 de ' + totalQuestions;
            document.getElementById('scoreProgress').textContent = 'Correctas: 0';
            
            initQuiz();
        }

        function startReviewMode() {
            // Crear lista de preguntas para repasar
            reviewQuestions = failedQuestions.map(index => questions[index]);
            
            // Guardar preguntas originales
            originalQuestions = [...questions];
            
            // Reemplazar el array de preguntas con solo las falladas
            questions.length = 0;
            questions.push(...reviewQuestions);
            
            // Resetear variables para el modo repaso
            currentQuestion = 0;
            score = 0;
            userAnswers = [];
            markedAsLucky = {};
            totalQuestions = questions.length;
            isReviewMode = true;
            
            // Ocultar resultados y mostrar preguntas
            document.getElementById('results').classList.remove('show');
            document.getElementById('questionsContainer').style.display = 'block';
            document.getElementById('progressText').textContent = 'Pregunta 0 de ' + totalQuestions;
            document.getElementById('scoreProgress').textContent = 'Correctas: 0';
            
            // Reiniciar quiz
            renderQuestion();
            updateProgress();
        }

        // Iniciar el cuestionario
        initQuiz();
    </script>
</body>
</html>
