<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anddie's Dilemma - The Power of Choice</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght=300;400;600;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            color: #fff;
        }
        
        .game-container {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            max-width: 700px;
            width: 100%;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }
        
        .logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .logo h1 {
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(90deg, #ff6b6b, #feca57, #48dbfb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: glow 2s ease-in-out infinite alternate;
        }
        
        @keyframes glow {
            from { filter: drop-shadow(0 0 10px rgba(255, 107, 107, 0.5)); }
            to { filter: drop-shadow(0 0 20px rgba(72, 219, 251, 0.5)); }
        }
        
        .subtitle {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.7);
            margin-top: 5px;
        }
        
        .scene {
            display: none;
        }
        
        .scene.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .character-image {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: linear-gradient(135deg, #ff6b6b, #feca57);
            margin: 0 auto 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            border: 3px solid rgba(255, 255, 255, 0.3);
        }
        
        .dialogue {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 20px;
            border-left: 4px solid #48dbfb;
        }
        
        .dialogue-text {
            font-size: 1.1rem;
            line-height: 1.6;
            color: #fff;
        }
        
        .dialogue-translation {
            font-size: 0.9rem;
            color: rgba(255, 255, 255, 0.6);
            margin-top: 10px;
            padding-top: 10px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .grammar-box {
            background: linear-gradient(135deg, rgba(255, 107, 107, 0.2), rgba(254, 202, 87, 0.2));
            border-radius: 10px;
            padding: 15px;
            margin: 20px 0;
            font-size: 0.85rem;
        }
        
        .grammar-box h3 {
            color: #feca57;
            margin-bottom: 8px;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }
        
        .option-btn {
            background: rgba(255, 255, 255, 0.1);
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-radius: 12px;
            padding: 18px 20px;
            color: #fff;
            font-family: 'Poppins', sans-serif;
            font-size: 1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: left;
        }
        
        .option-btn:hover {
            background: rgba(72, 219, 251, 0.2);
            border-color: #48dbfb;
            transform: translateX(10px);
        }
        
        .option-btn .label {
            font-weight: 700;
            color: #48dbfb;
            margin-right: 10px;
        }
        
        .option-btn .grammar-type {
            display: block;
            font-size: 0.8rem;
            color: rgba(255, 255, 255, 0.5);
            margin-top: 5px;
        }
        
        .progress-bar {
            width: 100%;
            height: 6px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 3px;
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #ff6b6b, #feca57, #48dbfb);
            border-radius: 3px;
            transition: width 0.5s ease;
        }
        
        .intro-screen, .ending-screen {
            text-align: center;
        }
        
        .start-btn {
            background: linear-gradient(135deg, #ff6b6b, #feca57);
            border: none;
            border-radius: 50px;
            padding: 18px 50px;
            color: #1a1a2e;
            font-family: 'Poppins', sans-serif;
            font-size: 1.2rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 30px;
        }
        
        .start-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(255, 107, 107, 0.4);
        }
        
        .ending-title {
            font-size: 2rem;
            margin-bottom: 20px;
        }
        
        .ending-text {
            font-size: 1.1rem;
            line-height: 1.8;
            color: rgba(255, 255, 255, 0.9);
        }
        
        .stats {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin: 20px 0;
        }
        
        .stat-item {
            text-align: center;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: #48dbfb;
        }
        
        .stat-label {
            font-size: 0.8rem;
            color: rgba(255, 255, 255, 0.6);
        }
    </style>
</head>
<body>
    <div class="game-container">
        <div class="logo">
            <h1>🎬 Anddie's Dilemma</h1>
            <p class="subtitle">The Power of Choice / O Poder da Escolha</p>
        </div>
        
        <div id="intro" class="scene active">
            <div class="character-image">👩‍🎤</div>
            <p style="font-size: 1.1rem; line-height: 1.8; margin-bottom: 20px;">
                Meet <strong>Anddie</strong>, a 20-year-old girl who lives alone for the first time. She's smart, but she has a big problem: <strong>she can't make decisions!</strong> She needs someone to tell her what to do.
            </p>
            <p style="font-size: 0.95rem; color: rgba(255,255,255,0.7); line-height: 1.8;">
                Conheça Anddie, uma garota de 20 anos que mora sozinha pela primeira vez. Ela é inteligente, mas tem um problema grave: <strong>ela não consegue tomar decisões!</strong> Ela precisa de alguém para dizer a ela o que fazer. Esse alguém é <strong>VOCÊ</strong>.
            </p>
            <p style="margin-top: 25px; font-size: 0.9rem; color: rgba(255,255,255,0.6);">
                🎯 O objetivo: Ajude Anddie a escolher entre opções com <strong>Zero Conditional</strong> (fatos/hábitos) ou <strong>First Conditional</strong> (possibilidades futuras).
            </p>
            <button class="start-btn" onclick="startGame()">START GAME / COMEÇAR</button>
        </div>
        
        <div id="scene1" class="scene">
            <div class="progress-bar"><div class="progress-fill" style="width: 25%"></div></div>
            <div class="character-image">☕</div>
            
            <div class="dialogue">
                <p class="dialogue-text">
                    <strong>LEVEL 1: The Coffee Shop</strong><br><br>
                    "I'm starving! I have only <strong>10 minutes</strong> before the class starts. I want to buy a sandwich, but the line is huge."<br><br>
                    <em>"If I <strong>wait</strong> in this line, I <strong>miss</strong> the test. If I <strong>skip</strong> lunch, I <strong>get</strong> hungry later."</em><br><br>
                    She looks at you nervously...
                </p>
                <p class="dialogue-translation">
                    <strong>NÍVEL 1: A Cafeteria</strong><br><br>
                    "Estou com fome! Só tenho <strong>10 minutes</strong> antes da aula começar. Quero comprar um sanduíche, mas a fila é enorme."<br><br>
                    <em>"Se eu <strong>esperar</strong> na fila, eu <strong>perco</strong> a prova. Se eu <strong>pular</strong> o almoço, eu <strong>fico</strong> com fome depois."</em>
                </p>
            </div>
            
            <div class="grammar-box">
                <h3>📚 Grammar Rule / Regra Gramatical:</h3>
                <p><strong>Zero Conditional:</strong> If + Present Simple, Present Simple (Fatos/Hábitos)</p>
                <p><strong>First Conditional:</strong> If + Present Simple, WILL + Verb (Possibilidade Futura)</p>
            </div>
            
            <div class="options">
                <button class="option-btn" onclick="chooseOption(1, 'first')">
                    <span class="label">A)</span> "If I <strong>buy</strong> the sandwich, I <strong>will be</strong> late for class."
                    <span class="grammar-type">→ First Conditional (Possibilidade Futura)</span>
                </button>
                <button class="option-btn" onclick="chooseOption(1, 'zero')">
                    <span class="label">B)</span> "If I <strong>skip</strong> lunch, I <strong>am</strong> grumpy all morning."
                    <span class="grammar-type">→ Zero Conditional (Fato/Hábito)</span>
                </button>
            </div>
        </div>
        
        <div id="scene2" class="scene">
            <div class="progress-bar"><div class="progress-fill" style="width: 50%"></div></div>
            <div class="character-image">📱</div>
            
            <div class="dialogue">
                <p class="dialogue-text">
                    <strong>LEVEL 2: The Invitation</strong><br><br>
                    "Oh! It's <strong>Leo</strong>. He is cute, but a bit weird."<br>
                    The message says: <em>"Hey Anddie! If you <strong>come</strong> to the party tonight, I <strong>buy</strong> you a drink."</em><br><br>
                    "I don't know him that well. And I have a Math test tomorrow!"
                </p>
                <p class="dialogue-translation">
                    <strong>NÍVEL 2: O Convite</strong><br><br>
                    "Ah! É o <strong>Leo</strong>. Ele é bonito, mas um pouco estranho."<br>
                    A mensagem diz: <em>"Eai Anddie! Se você <strong>vier</strong> para a festa hoje, eu <strong>compro</strong> uma bebida."</em><br><br>
                    "Não o conheço bem. E tenho prova de Matemática amanhã!"
                </p>
            </div>
            
            <div class="options">
                <button class="option-btn" onclick="chooseOption(2, 'first')">
                    <span class="label">A)</span> "If he <strong>messages</strong> me again, I <strong>will go</strong>."
                    <span class="grammar-type">→ First Conditional (Possibilidade Futura)</span>
                </button>
                <button class="option-btn" onclick="chooseOption(2, 'zero')">
                    <span class="label">B)</span> "If I <strong>go</strong> to a party, I <strong>always sleep</strong> until noon."
                    <span class="grammar-type">→ Zero Conditional (Hábito)</span>
                </button>
            </div>
        </div>
        
        <div id="scene3" class="scene">
            <div class="progress-bar"><div class="progress-fill" style="width: 75%"></div></div>
            <div class="character-image">👗</div>
            
            <div class="dialogue">
                <p class="dialogue-text">
                    <strong>LEVEL 3: What to Wear</strong><br><br>
                    "Okay, I decided to go! But what should I wear?"<br>
                    She holds two outfits:<br>
                    🟢 A super comfortable hoodie<br>
                    🔴 A very tight dress<br><br>
                    <em>"If I <strong>wear</strong> the hoodie, I <strong>am</strong> comfortable. But if I <strong>wear</strong> the dress, everyone <strong>looks</strong> at me."</em>
                </p>
                <p class="dialogue-translation">
                    <strong>NÍVEL 3: O Que Vestir</strong><br><br>
                    "Okay, decidi ir! Mas o que devo vestir?"<br>
                    Ela segura duas roupas:<br>
                    🟢 Um moletom bem confortável<br>
                    🔴 Um vestido bem apertado<br><br>
                    <em>"Se eu <strong>usar</strong> o moletom, eu <strong>fico</strong> confortável. Mas se eu <strong>usar</strong> o vestido, todos <strong>olham</strong> para mim."</em>
                </p>
            </div>
            
            <div class="options">
                <button class="option-btn" onclick="chooseOption(3, 'zero')">
                    <span class="label">A)</span> "If it <strong>rains</strong>, I <strong>always wear</strong> a jacket."
                    <span class="grammar-type">→ Zero Conditional (Fato)</span>
                </button>
                <button class="option-btn" onclick="chooseOption(3, 'first')">
                    <span class="label">B)</span> "If I <strong>wear</strong> the dress, I <strong>will feel</strong> confident."
                    <span class="grammar-type">→ First Conditional (Possibilidade Futura)</span>
                </button>
            </div>
        </div>

        <div id="ending" class="scene ending-screen">
            <div class="character-image">🎉</div>
            <h2 class="ending-title">Story Completed! / História Concluída!</h2>
            <p class="ending-text">You helped Anddie navigate her choices tonight. Here is how you balanced her decisions:</p>
            
            <div class="stats">
                <div class="stat-item">
                    <div id="zero-count" class="stat-number">0</div>
                    <div class="stat-label">Zero Conditionals<br>(Fatos/Hábitos)</div>
                </div>
                <div class="stat-item">
                    <div id="first-count" class="stat-number">0</div>
                    <div class="stat-label">First Conditionals<br>(Futuro)</div>
                </div>
            </div>
            
            <button class="start-btn" onclick="restartGame()">Play Again / Jogar Novamente</button>
        </div>
    </div>

    <script>
        let choices = {
            zero: 0,
            first: 0
        };

        function startGame() {
            document.getElementById('intro').classList.remove('active');
            document.getElementById('scene1').classList.add('active');
        }

        function chooseOption(currentScene, type) {
            // Contabiliza o tipo de condicional escolhida
            choices[type]++;

            // Esconde a cena atual
            document.getElementById('scene' + currentScene).classList.remove('active');

            // Define a próxima cena
            let nextScene = currentScene + 1;
            let nextSceneElement = document.getElementById('scene' + nextScene);

            if (nextSceneElement) {
                // Vai para o próximo nível
                nextSceneElement.classList.add('active');
            } else {
                // Se não houver mais níveis, mostra o final
                showEnding();
            }
        }

        function showEnding() {
            document.getElementById('zero-count').innerText = choices.zero;
            document.getElementById('first-count').innerText = choices.first;
            document.getElementById('ending').classList.add('active');
        }

        function restartGame() {
            choices.zero = 0;
            choices.first = 0;
            document.getElementById('ending').classList.remove('active');
            document.getElementById('intro').classList.add('active');
        }
    </script>
</body>
</html>
