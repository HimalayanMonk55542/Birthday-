<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday! 🎂</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
    }
    body {
      background-color: #fbebf2;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      overflow: hidden;
    }
    .card-container {
      width: 100%;
      max-width: 400px;
      height: 680px;
      background: #fff5f8;
      border-radius: 30px;
      box-shadow: 0 15px 35px rgba(220, 150, 180, 0.3);
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
      text-align: center;
    }

    .screen {
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      width: 100%;
      height: 100%;
      animation: fadeIn 0.5s ease-in-out;
    }
    .screen.active {
      display: flex;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Common Typography & Controls */
    h2 { color: #5a2a42; font-size: 22px; margin-bottom: 10px; }
    p { color: #8c5b75; font-size: 14px; margin-bottom: 20px; }
    
    .btn-pink {
      background: linear-gradient(135deg, #ff85a2, #e05297);
      color: white;
      border: none;
      padding: 12px 28px;
      border-radius: 25px;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 5px 15px rgba(224, 82, 151, 0.4);
      transition: transform 0.2s;
    }
    .btn-pink:active { transform: scale(0.95); }

    /* Interactive Elements */
    .gift-box {
      font-size: 80px;
      cursor: pointer;
      animation: bounce 2s infinite;
    }
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-12px); }
    }

    /* Cake Screen */
    .cake { font-size: 90px; position: relative; margin: 15px 0; }
    .candle {
      font-size: 30px;
      cursor: pointer;
      display: inline-block;
      margin: 0 4px;
    }

    /* Reasons Screen Grid */
    .reasons-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
      width: 100%;
      margin-bottom: 20px;
    }
    .reason-card {
      background: #ffffff;
      padding: 15px 10px;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.05);
      font-size: 12px;
      color: #6a3551;
      font-weight: 600;
    }

    /* Mini Game Screen */
    .game-area {
      position: relative;
      width: 100%;
      height: 250px;
      background: #ffe3ee;
      border-radius: 20px;
      overflow: hidden;
      margin-bottom: 15px;
    }
    .floating-heart {
      position: absolute;
      font-size: 28px;
      cursor: pointer;
      user-select: none;
    }

    /* Final Card Screen */
    .final-card {
      background: #fff;
      padding: 20px;
      border-radius: 20px;
      border: 2px dashed #ffb6c1;
      text-align: left;
      font-size: 13px;
      line-height: 1.6;
      color: #5a2a42;
    }
  </style>
</head>
<body>

  <div class="card-container">

    <!-- Screen 1: Welcome / Surprise Box -->
    <div class="screen active" id="screen1">
      <p>✨ YOUR SURPRISE IS WAITING ✨</p>
      <div class="gift-box" onclick="nextScreen(2)">🎁</div>
      <p style="margin-top:20px;">Tap the gift to open!</p>
    </div>

    <!-- Screen 2: Photo / Greeting -->
    <div class="screen" id="screen2">
      <h2>Happy Birthday! 🎉</h2>
      <p>Here is a little something made with love ❤️</p>
      <div style="width:180px; height:180px; background:#e8d1e0; border-radius:15px; display:flex; align-items:center; justify-content:center; margin-bottom:20px;">
        📸 <span style="font-size:12px; color:#888; margin-left:5px;">Insert Photo</span>
      </div>
      <button class="btn-pink" onclick="nextScreen(3)">Now, keep going 💕</button>
    </div>

    <!-- Screen 3: Things I Love About You -->
    <div class="screen" id="screen3">
      <h2>Things I Love About You 💕</h2>
      <div class="reasons-grid">
        <div class="reason-card">😊 Your smile</div>
        <div class="reason-card">💖 Your kindness</div>
        <div class="reason-card">🗣️ Random talks</div>
        <div class="reason-card">🌟 Your energy</div>
      </div>
      <button class="btn-pink" onclick="nextScreen(4)">My heart is full ✨</button>
    </div>

    <!-- Screen 4: Blow Out Candles -->
    <div class="screen" id="screen4">
      <h2>Blow out the candles! 🎂</h2>
      <p>Tap each candle flame to extinguish it</p>
      <div class="cake">
        <span class="candle" onclick="blowCandle(this)">🔥</span>
        <span class="candle" onclick="blowCandle(this)">🔥</span>
        <span class="candle" onclick="blowCandle(this)">🔥</span>
      </div>
      <button class="btn-pink" id="candle-btn" style="display:none;" onclick="nextScreen(5)">Candles Out! Next ✨</button>
    </div>

    <!-- Screen 5: Tiny Challenge Game -->
    <div class="screen" id="screen5">
      <h2>One Tiny Challenge 💖</h2>
      <p>Catch 3 floating hearts!</p>
      <div class="game-area" id="gameArea"></div>
      <p>Caught: <span id="score">0</span> / 3</p>
      <button class="btn-pink" id="game-btn" style="display:none;" onclick="nextScreen(6)">Yay! What's next? 👉</button>
    </div>

    <!-- Screen 6: Final Letter -->
    <div class="screen" id="screen6">
      <h2>One Last Thing... 💌</h2>
      <div class="final-card">
        Dear Birthday Star ⭐,<br/><br/>
        I hope this page brings a big smile to your face today. You deserve all the happiness, love, laughter, and beautiful moments in the world.<br/><br/>
        Keep smiling and keep shining! 💫
      </div>
      <button class="btn-pink" style="margin-top:20px;" onclick="alert('🎂 Wish sent to the universe!')">Send Wish ✨</button>
    </div>

  </div>

  <script>
    let currentScreen = 1;
    let blownCount = 0;
    let heartsCaught = 0;

    function nextScreen(screenNum) {
      document.getElementById(`screen${currentScreen}`).classList.remove('active');
      currentScreen = screenNum;
      document.getElementById(`screen${currentScreen}`).classList.add('active');

      if (screenNum === 5) {
        startHeartGame();
      }
    }

    /* Candle interaction */
    function blowCandle(element) {
      if (element.innerText === '🔥') {
        element.innerText = '💨';
        blownCount++;
        if (blownCount === 3) {
          document.getElementById('candle-btn').style.display = 'inline-block';
        }
      }
    }

    /* Mini Game interaction */
    function startHeartGame() {
      const area = document.getElementById('gameArea');
      area.innerHTML = '';
      heartsCaught = 0;
      document.getElementById('score').innerText = heartsCaught;

      for (let i = 0; i < 3; i++) {
        spawnHeart(area);
      }
    }

    function spawnHeart(container) {
      const heart = document.createElement('div');
      heart.className = 'floating-heart';
      heart.innerText = '💖';
      heart.style.top = Math.random() * 200 + 'px';
      heart.style.left = Math.random() * 320 + 'px';

      heart.onclick = function() {
        heartsCaught++;
        document.getElementById('score').innerText = heartsCaught;
        heart.remove();
        if (heartsCaught >= 3) {
          document.getElementById('game-btn').style.display = 'inline-block';
        }
      };

      container.appendChild(heart);
    }
  </script>
</body>
</html>
