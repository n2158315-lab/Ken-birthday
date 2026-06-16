<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Naruto Calculus Shinobi Dance Chronicles</title>
    <style>
        :root {
            --bg-color: #0f0c1b;
            --konoha-blue: #0984e3;
            --shinobi-green: #2e7d32;
            --neon-purple: #a55eea;
            --pastel-lavender: #e0b0ff;
            --cute-pink: #ffb8b8;
        }

        body {
            margin: 0;
            padding: 0;
            background-color: #0f0c1b;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden;
            color: #fff;
        }

        h1 {
            text-align: center;
            margin-bottom: 5px;
            font-size: 24px;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #ffeaa7;
            text-shadow: 0 0 10px rgba(255,234,167,0.5);
            z-index: 5;
        }

        /* Ambient Floating Particles */
        .particle-container {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            pointer-events: none;
            z-index: 3;
            overflow: hidden;
        }
        .particle {
            position: absolute;
            display: block;
            animation: floatUp 4s linear infinite;
        }
        @keyframes floatUp {
            0% { transform: translateY(100vh) translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-20px) translateX(50px) rotate(360deg); opacity: 0; }
        }

        .stage-container {
            width: 380px;
            height: 520px;
            border: 6px solid #444;
            border-radius: 20px;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            align-items: center;
            box-shadow: 0 20px 40px rgba(0,0,0,0.5);
            transition: all 0.8s ease;
        }

        /* Level Themes */
        .stage-container.lvl1 {
            background: linear-gradient(to bottom, #74b9ff 40%, #ffeaa7 65%, #55efc4 90%);
            border-color: #fff;
        }
        .stage-container.lvl2 {
            background: linear-gradient(to bottom, #2d142c 30%, #510a32 70%, #801336 100%);
            border-color: var(--neon-purple);
            box-shadow: 0 0 25px var(--neon-purple);
        }
        .stage-container.lvl3 {
            background: linear-gradient(to bottom, #2c1a4d 20%, #4a267a 60%, #834fa0 100%);
            border-color: var(--pastel-lavender);
            box-shadow: 0 0 30px var(--pastel-lavender), inset 0 0 20px rgba(224, 176, 255, 0.3);
        }

        /* Ichiraku Ramen Signboard Overlay for Level 3 */
        .ramen-shop-banner {
            position: absolute;
            top: 0;
            width: 100%;
            background: #e74c3c;
            color: #fff;
            text-align: center;
            font-size: 11px;
            font-weight: bold;
            padding: 3px 0;
            letter-spacing: 1px;
            border-bottom: 3px double #f1c40f;
            z-index: 4;
            display: none;
        }
        .lvl3 .ramen-shop-banner { display: block; animation: bounceIn 0.8s ease; }

        /* Cake & Ramen Reward Showcase for Lvl 3 */
        .cake-display {
            position: absolute;
            top: 95px;
            font-size: 13px;
            font-weight: bold;
            background: rgba(255, 255, 255, 0.2);
            padding: 4px 12px;
            border-radius: 20px;
            backdrop-filter: blur(5px);
            border: 1px solid var(--pastel-lavender);
            display: none;
            z-index: 5;
            animation: bounceIn 0.5s ease;
        }
        @keyframes bounceIn {
            0% { transform: scale(0); }
            80% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        /* Math UI Box */
        .jutsu-box {
            background: rgba(20, 20, 20, 0.85);
            backdrop-filter: blur(5px);
            padding: 15px;
            border-radius: 15px;
            margin-top: 28px;
            width: 85%;
            box-sizing: border-box;
            text-align: center;
            border: 3px solid #ff7675;
            z-index: 10;
            box-shadow: 0 8px 16px rgba(0,0,0,0.3);
            transition: all 0.4s;
        }
        .lvl2 .jutsu-box { border-color: var(--neon-purple); box-shadow: 0 0 15px var(--neon-purple); margin-top: 15px; }
        .lvl3 .jutsu-box { border-color: var(--pastel-lavender); box-shadow: 0 0 15px var(--pastel-lavender); margin-top: 25px; }
        
        input {
            width: 60%;
            padding: 8px;
            background: #333;
            border: 2px solid #555;
            border-radius: 8px;
            text-align: center;
            font-size: 16px;
            color: #fff;
            outline: none;
        }
        input:focus { border-color: #ffeaa7; }

        button {
            margin-top: 8px;
            background: #d63031;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            text-transform: uppercase;
        }
        .lvl2 button { background: var(--neon-purple); }
        .lvl3 button { background: #6c5ce7; color: white; border: 1px solid var(--pastel-lavender); }

        /* Gates */
        .gate-wrapper {
            position: absolute;
            bottom: 0; width: 100%; height: 260px;
            z-index: 8; display: flex;
        }
        .gate {
            width: 50%; height: 100%;
            background-color: #9e1c1c;
            border: 4px solid #2c1616;
            box-sizing: border-box;
            position: relative;
            transition: transform 1.5s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .gate-left { border-radius: 10px 0 0 0; transform-origin: left; }
        .gate-right { border-radius: 0 10px 0 0; transform-origin: right; }
        .crest {
            width: 40px; height: 40px; background: #fff; border-radius: 50%;
            position: absolute; top: 40%; border: 3px solid #2c1616;
            display: flex; align-items: center; justify-content: center; font-size: 20px;
        }
        .gate-left .crest { right: -20px; }
        .gate-right .crest { left: -20px; }

        .cleared .gate-left { transform: translateX(-100%) rotateY(-90deg); }
        .cleared .gate-right { transform: translateX(100%) rotateY(90deg); }

        /* --- CHARACTER BASE MODELS (Animated Anime Style) --- */
        .dance-floor {
            position: absolute;
            bottom: 30px; width: 100%; height: 200px;
            display: flex; justify-content: center; gap: 12px; z-index: 6;
            padding: 0 10px;
            box-sizing: border-box;
        }

        .ninja-body {
            width: 55px; height: 190px;
            flex-direction: column; align-items: center;
            position: relative;
            display: none;
        }

        .ninja-head {
            width: 34px; height: 42px; background: #ffdbac;
            border-radius: 30% 30% 50% 50%; position: relative; z-index: 4;
        }
        .ninja-hair { position: absolute; background: #2d3436; z-index: 5; }
        .ninja-eyes {
            position: absolute; top: 22px; width: 6px; height: 4px;
            background: #222; border-radius: 2px;
        }

        .ninja-torso {
            width: 36px; height: 65px; border-radius: 6px;
            position: relative; margin-top: -2px; z-index: 3;
        }
        .ninja-arm {
            width: 9px; height: 48px; position: absolute;
            top: 2px; border-radius: 5px; transform-origin: top center;
        }
        .arm-l { left: -8px; }
        .arm-r { right: -8px; }

        .ninja-legs {
            display: flex; justify-content: space-between;
            width: 30px; height: 75px; position: relative; z-index: 2;
        }
        .ninja-leg {
            width: 12px; height: 100%; background: #222;
            border-bottom: 6px solid #fff; transform-origin: top center;
        }

        /* --- CHARACTER DESIGN SPECIFICS --- */
        /* 1. Ken (Normal) */
        .char-ken-norm .ninja-hair {
            width: 100%; height: 15px; top: -10px;
            clip-path: polygon(0% 100%, 20% 0%, 40% 100%, 60% 0%, 80% 100%, 100% 10%, 100% 100%);
        }
        .char-ken-norm .ninja-torso { background: var(--konoha-blue); }
        .char-ken-norm .ninja-arm { background: var(--konoha-blue); }

        /* 2. Itachi */
        .char-itachi .ninja-hair { width: 110%; height: 20px; top: -8px; left: -5%; background: #1b1c1e; border-radius: 5px 5px 0 0; }
        .char-itachi .ninja-eyes { background: #ff7675; box-shadow: 0 0 4px red; }
        .char-itachi .ninja-torso { background: #111; border: 1px solid #d63031; }
        .char-itachi .ninja-torso::after { content: '☁️'; color: red; font-size: 12px; position: absolute; top: 15px; left: 8px; }
        .char-itachi .ninja-arm { background: #111; }

        /* 3. Ken (Shinobi/Grand Finale Cute Anime Edition) */
        .char-ken-shino .ninja-hair {
            width: 100%; height: 15px; top: -10px; background: #2d3436;
            clip-path: polygon(0% 100%, 20% 0%, 40% 100%, 60% 0%, 80% 100%, 100% 10%, 100% 100%);
        }
        .char-ken-shino .ninja-torso { background: var(--shinobi-green); border-bottom: 20px solid var(--konoha-blue); }
        .char-ken-shino .ninja-arm { background: var(--konoha-blue); }
        .char-ken-shino .ninja-leg { background: var(--konoha-blue); }

        /* Level 3 Cute Upgrade for Ken */
        .lvl3 .char-ken-shino .ninja-eyes {
            background: #487eb0; height: 6px; width: 6px; border-radius: 50%;
            box-shadow: 0 0 2px rgba(255,255,255,0.8);
        }
        .lvl3 .char-ken-shino .ninja-head::before {
            content: '〃〃'; color: rgba(255, 120, 120, 0.8); font-size: 9px;
            position: absolute; bottom: 8px; left: 2px; width: 30px; text-shadow: 18px 0 rgba(255,120,120,0.8);
            z-index: 4; font-weight: bold;
        }

        /* 4. Gaara */
        .char-gaara .ninja-hair { width: 104%; height: 16px; top: -10px; background: #9e2a2b; clip-path: polygon(0 100%, 10% 0, 30% 80%, 50% 0, 70% 80%, 90% 0, 100% 100%); }
        .char-gaara .ninja-head::after { content: '爱'; color: #d63031; font-size: 8px; position: absolute; top: 10px; left: 6px; font-weight: bold; }
        .char-gaara .ninja-torso { background: #7f1d1d; }
        .char-gaara::before { content: ''; position: absolute; top: 40px; right: 2px; width: 18px; height: 35px; background: #ddb892; border-radius: 10px; border: 2px solid #b5835a; z-index: 1; transform: rotate(15deg); }
        .char-gaara .ninja-arm { background: #7f1d1d; }

        /* 5. USER ANIME STYLE */
        .char-user .ninja-hair {
            width: 120%; height: 85px; top: -8px; left: -10%;
            background: #1e1b18; 
            border-radius: 10px 10px 20px 20px;
        }
        .char-user .ninja-hair::after {
            content: ''; position: absolute; bottom: 0; left: 0; width: 100%; height: 25px;
            background: #1e1b18;
            clip-path: polygon(0% 0%, 100% 0%, 100% 70%, 85% 65%, 70% 70%, 50% 65%, 30% 70%, 15% 65%, 0% 75%);
        }
        .char-user .ninja-eyes { background: #5c4033; height: 5px; width: 7px; border-radius: 50% 50% 0 0; }
        .char-user .ninja-head::before {
            content: '✿'; color: rgba(255, 120, 120, 0.6); font-size: 14px;
            position: absolute; bottom: 8px; left: 3px; width: 30px; text-shadow: 20px 0 rgba(255,120,120,0.6);
            z-index: 4;
        }
        .char-user .ninja-torso { background: #d6a2e8; border: 2px solid var(--pastel-lavender); } 
        .char-user .ninja-arm { background: #d6a2e8; }
        .char-user .ninja-leg { background: #4b3869; }


        /* --- DANCE ANIMATIONS --- */
        /* Level 1 Dance */
        .cleared.lvl1 .char-ken-norm { animation: danceLvl1 0.6s infinite alternate ease-in-out; }
        .cleared.lvl1 .char-itachi { animation: danceLvl1 0.6s infinite alternate ease-in-out; animation-delay: 0.15s; }
        @keyframes danceLvl1 { 0% { transform: translateY(0) rotate(-5deg); } 100% { transform: translateY(-15px) rotate(5deg); } }

        /* Level 2 Dance */
        .cleared.lvl2 .char-ken-shino { animation: newJeansDance 0.45s infinite ease-in-out; }
        .cleared.lvl2 .char-gaara { animation: newJeansDance 0.45s infinite ease-in-out; animation-delay: 0.1s; }
        @keyframes newJeansDance {
            0% { transform: translateX(-10px) scaleY(1) rotate(-3deg); }
            25% { transform: translateY(-8px) scaleY(1.05) rotate(0deg); }
            50% { transform: translateX(10px) scaleY(1) rotate(3deg); }
            75% { transform: translateY(4px) scaleY(0.95) rotate(0deg); }
            100% { transform: translateX(-10px) scaleY(1) rotate(-3deg); }
        }
        .cleared.lvl2 .ninja-arm { animation: armWave 0.45s infinite alternate; }
        @keyframes armWave { 0% { transform: rotate(40deg); } 100% { transform: rotate(-60deg); } }

        /* --- LEVEL 3: IVE TIKTOK DANCE CHALLENGE --- */
        .cleared.lvl3 .ninja-body { animation: iveTikTokDance 0.8s infinite ease-in-out; }
        .cleared.lvl3 #c-ken2 { animation-delay: 0s; }
        .cleared.lvl3 #c-user { animation-delay: 0s; }
        .cleared.lvl3 #c-itachi { animation-delay: 0.1s; }
        .cleared.lvl3 #c-gaara { animation-delay: 0.2s; }

        @keyframes iveTikTokDance {
            0% { transform: translateY(0) scale(1) rotate(0deg); }
            20% { transform: translateY(4px) scaleX(1.05) rotate(-4deg); } 
            40% { transform: translateY(-10px) scaleY(1.05) rotate(0deg); } 
            60% { transform: translateY(0) scale(1) rotate(4deg); } 
            80% { transform: translateY(-6px) scaleX(0.95) rotate(-2deg); } 
            100% { transform: translateY(0) scale(1) rotate(0deg); }
        }

        .cleared.lvl3 .ninja-arm.arm-l { animation: iveArmsL 0.8s infinite alternate ease-in-out; }
        .cleared.lvl3 .ninja-arm.arm-r { animation: iveArmsR 0.8s infinite alternate ease-in-out; }
        @keyframes iveArmsL { 
            0% { transform: rotate(40deg); } 
            50% { transform: rotate(-130deg) translateX(8px); } 
            100% { transform: rotate(-30deg); } 
        }
        @keyframes iveArmsR { 
            0% { transform: rotate(-40deg); } 
            50% { transform: rotate(130deg) translateX(-8px); } 
            100% { transform: rotate(30deg); } 
        }

        .status-msg { margin-top: 10px; font-weight: bold; height: 24px; text-shadow: 1px 1px #000; }
        
        .action-btn {
            display: none; background: #fdcb6e; color: #000; padding: 10px 20px;
            border-radius: 8px; cursor: pointer; font-weight: bold; margin-top: 10px; z-index: 5;
            text-transform: uppercase;
        }
    </style>
</head>
<body>

    <h1 id="gameTitle">Level 1: Konoha Gate Jutsu</h1>

    <div class="stage-container lvl1" id="stage">
        <div class="particle-container" id="particles"></div>

        <!-- Ichiraku Ramen Backdrop Shop Sign -->
        <div class="ramen-shop-banner">🍜 一楽ラーメン - ICHIRAKU RAMEN PARTY ZONE 🍜</div>

        <!-- Cake & Ramen Reward Counter -->
        <div class="cake-display" id="cakeDisplay">🎂 Target: 0/1 Feast Unlocked</div>

        <!-- Math Prompt Panel -->
        <div class="jutsu-box" id="jutsuBox">
            <p id="promptText" style="margin:0 0 8px 0; font-weight:bold;">Solve to bypass the Gate Keepers:</p>
            <p id="mathQuestion" style="font-size: 22px; color: #d63031; font-weight: bold; margin:5px 0;">d/dx (x²) = ?</p>
            <input type="text" id="answerInput" placeholder="Enter answer...">
            <br>
            <button onclick="checkJutsuAnswer()">Cast Formula!</button>
        </div>

        <!-- Characters Floor -->
        <div class="dance-floor">
            <!-- Ken Normal -->
            <div class="ninja-body char-ken-norm" id="c-ken1" style="display: flex;">
                <div class="ninja-head"><div class="ninja-hair"></div><div class="ninja-eyes" style="left:6px;"></div><div class="ninja-eyes" style="right:6px;"></div></div>
                <div class="ninja-torso"><div class="ninja-arm arm-l"></div><div class="ninja-arm arm-r"></div></div>
                <div class="ninja-legs"><div class="ninja-leg"></div><div class="ninja-leg"></div></div>
            </div>

            <!-- Itachi -->
            <div class="ninja-body char-itachi" id="c-itachi" style="display: flex;">
                <div class="ninja-head"><div class="ninja-hair"></div><div class="ninja-eyes" style="left:6px;"></div><div class="ninja-eyes" style="right:6px;"></div></div>
                <div class="ninja-torso"><div class="ninja-arm arm-l"></div><div class="ninja-arm arm-r"></div></div>
                <div class="ninja-legs"><div class="ninja-leg"></div><div class="ninja-leg"></div></div>
            </div>

            <!-- Ken Shinobi (Cute Anime Edition) -->
            <div class="ninja-body char-ken-shino" id="c-ken2">
                <div class="ninja-head"><div class="ninja-hair"></div><div class="ninja-eyes" style="left:6px;"></div><div class="ninja-eyes" style="right:6px;"></div></div>
                <div class="ninja-torso"><div class="ninja-arm arm-l"></div><div class="ninja-arm arm-r"></div></div>
                <div class="ninja-legs"><div class="ninja-leg"></div><div class="ninja-leg"></div></div>
            </div>

            <!-- Gaara -->
            <div class="ninja-body char-gaara" id="c-gaara">
                <div class="ninja-head"><div class="ninja-hair"></div><div class="ninja-eyes" style="left:6px; background:#487eb0;"></div><div class="ninja-eyes" style="right:6px; background:#487eb0;"></div></div>
                <div class="ninja-torso"><div class="ninja-arm arm-l"></div><div class="ninja-arm arm-r"></div></div>
                <div class="ninja-legs"><div class="ninja-leg"></div><div class="ninja-leg"></div></div>
            </div>

            <!-- User Avatar -->
            <div class="ninja-body char-user" id="c-user">
                <div class="ninja-head"><div class="ninja-hair"></div><div class="ninja-eyes" style="left:6px;"></div><div class="ninja-eyes" style="right:6px;"></div></div>
                <div class="ninja-torso"><div class="ninja-arm arm-l"></div><div class="ninja-arm arm-r"></div></div>
                <div class="ninja-legs"><div class="ninja-leg"></div><div class="ninja-leg"></div></div>
            </div>
        </div>

        <!-- Gate Layer -->
        <div class="gate-wrapper" id="gateWrapper">
            <div class="gate gate-left"><div class="crest" id="crestL">🍃</div></div>
            <div class="gate gate-right"><div class="crest" id="crestR">🍃</div></div>
        </div>
    </div>

    <div class="status-msg" id="feedback"></div>
    <div class="action-btn" id="nextLvlBtn" onclick="transitionToLevel2()">PROCEED TO LEVEL 2 ➔</div>
    <div class="action-btn" id="finalLvlBtn" onclick="transitionToLevel3()">👉 UNLOCK RAMEN & CAKE FINALE 👈</div>

    <!-- Media Elements -->
    <video id="musicLvl1" src="1000002804.mp4" style="display:none;" loop></video>
    <video id="musicLvl2" src="1000002815.mp4" style="display:none;" loop></video>
    <!-- AUTOMATIC NA NAKALAGAY YONG VIDEO FILE NAME MO DITO -->
    <video id="musicLvl3" src="1000002827.mp4" style="display:none;" loop></video>

    <script>
        let currentLevel = 1;

        function spawnParticles(itemsArray, isUpward = false) {
            const container = document.getElementById('particles');
            container.innerHTML = '';
            
            for(let i=0; i<22; i++) {
                let p = document.createElement('span');
                p.className = 'particle';
                
                const currentItem = itemsArray[Math.floor(Math.random() * itemsArray.length)];
                p.innerText = currentItem;
                
                p.style.left = Math.random() * 100 + '%';
                p.style.animationDelay = Math.random() * 4 + 's';
                p.style.fontSize = (Math.random() * 12 + 20) + 'px';
                
                if(!isUpward) {
                    p.style.animationName = 'fall';
                    p.style.top = '-20px';
                }
                container.appendChild(p);
            }
        }
        
        const style = document.createElement('style');
        style.innerHTML = `@keyframes fall { 0% { transform: translateY(-20px) translateX(0) rotate(0deg); opacity: 1; } 100% { transform: translateY(100vh) translateX(100px) rotate(360deg); opacity: 0; } }`;
        document.head.appendChild(style);

        // Start Level 1 Leaves
        spawnParticles(['🍃']); 

        function checkJutsuAnswer() {
            const ans = document.getElementById('answerInput').value.trim().toLowerCase();
            const feedback = document.getElementById('feedback');
            const stage = document.getElementById('stage');
            const jutsuBox = document.getElementById('jutsuBox');
            
            if (currentLevel === 1) {
                if (ans === '2x') {
                    feedback.innerHTML = "✨ JUTSU SUCCESS! Level 1 Dance Activated!";
                    feedback.style.color = "#2ecc71";
                    stage.classList.add('cleared');
                    jutsuBox.style.opacity = "0.2";
                    document.getElementById('musicLvl1').play().catch(e => console.log("Audio trigger ready"));
                    document.getElementById('nextLvlBtn').style.display = "block";
                } else {
                    feedback.innerHTML = "❌ Out of Chakra! Try again.";
                    feedback.style.color = "#e74c3c";
                }
            } else if (currentLevel === 2) {
                if (ans === 'cos(x)' || ans === 'cosx') {
                    feedback.innerHTML = "🔥 NEON CHAKRA UNLOCKED! New Jeans Trend Dance Mode!";
                    feedback.style.color = "#a55eea";
                    stage.classList.add('cleared');
                    jutsuBox.style.opacity = "0.2";
                    document.getElementById('musicLvl2').play().catch(e => console.log("Audio trigger ready"));
                    document.getElementById('finalLvlBtn').style.display = "block";
                } else {
                    feedback.innerHTML = "❌ Sand Shield Blocked! Incorrect formula.";
                    feedback.style.color = "#ff7675";
                }
            } else if (currentLevel === 3) {
                if (ans === 'e^x') {
                    feedback.innerHTML = "🍜🎉 FEAST ACTIVATED! Cute IVE Trend Dance Unlocked! 🎂💖";
                    feedback.style.color = "#ffb8b8";
                    stage.classList.add('cleared');
                    jutsuBox.style.opacity = "0.1";
                    
                    document.getElementById('cakeDisplay').innerText = "🍜 Feasting: 1/1 Ramen & Cake Claimed! 🎂";
                    document.getElementById('cakeDisplay').style.background = "rgba(235, 94, 40, 0.4)";

                    // EPIC FINALE CELEBRATION SHOWER
                    spawnParticles(['🍜', '🎂', '🧁', '💖', '✨'], true);
                    
                    document.getElementById('musicLvl3').play().catch(e => console.log("IVE Track playing"));
                } else {
                    feedback.innerHTML = "❌ Focus your thoughts! Try the exponential formula again.";
                    feedback.style.color = "#e0b0ff";
                }
            }
        }

        function transitionToLevel2() {
            currentLevel = 2;
            const m1 = document.getElementById('musicLvl1');
            m1.pause(); m1.currentTime = 0;

            document.getElementById('gameTitle').innerText = "Level 2: Akatsuki Desert Rave";
            document.getElementById('mathQuestion').innerText = "d/dx (sin(x)) = ?";
            document.getElementById('mathQuestion').style.color = "#a55eea";
            document.getElementById('answerInput').value = "";
            document.getElementById('feedback').innerText = "";
            document.getElementById('nextLvlBtn').style.display = "none";
            
            const stage = document.getElementById('stage');
            stage.className = "stage-container lvl2"; 
            document.getElementById('jutsuBox').style.opacity = "1";

            document.getElementById('c-ken1').style.display = "none";
            document.getElementById('c-itachi').style.display = "none";
            document.getElementById('c-ken2').style.display = "flex";
            document.getElementById('c-gaara').style.display = "flex";

            document.getElementById('crestL').innerText = "⏳";
            document.getElementById('crestR').innerText = "⏳";
            spawnParticles(['⏳']); 
        }

        function transitionToLevel3() {
            currentLevel = 3;
            const m2 = document.getElementById('musicLvl2');
            m2.pause(); m2.currentTime = 0;

            document.getElementById('gameTitle').innerText = "Level 3: Ichiraku Anime Squad Celebration! 🍜";
            document.getElementById('mathQuestion').innerText = "d/dx (e^x) = ?";
            document.getElementById('mathQuestion').style.color = "#e0b0ff";
            document.getElementById('answerInput').value = "";
            document.getElementById('feedback').innerText = "";
            document.getElementById('finalLvlBtn').style.display = "none";
            
            const stage = document.getElementById('stage');
            stage.className = "stage-container lvl3"; 
            document.getElementById('jutsuBox').style.opacity = "1";
            document.getElementById('cakeDisplay').style.display = "block";

            // ALL CHARACTERS ASSEMBLE
            document.getElementById('c-ken1').style.display = "none"; 
            document.getElementById('c-ken2').style.display = "flex"; 
            document.getElementById('c-itachi').style.display = "flex"; 
            document.getElementById('c-gaara').style.display = "flex"; 
            document.getElementById('c-user').style.display = "flex"; 

            document.getElementById('crestL').innerText = "🍜";
            document.getElementById('crestR').innerText = "🎂";
            
            spawnParticles(['✨', '🌸'], true); 
        }
    </script>
</body>
</html>
