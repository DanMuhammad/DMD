<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Tap to Collect Coins</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #f0f0f0;
      margin: 0;
      padding: 0;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    h1 {
      margin-bottom: 20px;
    }
    button {
      font-size: 22px;
      padding: 15px 40px;
      margin: 20px;
      cursor: pointer;
      border: none;
      border-radius: 12px;
      background: gold;
      box-shadow: 0px 4px 6px rgba(0,0,0,0.2);
    }
    .stats {
      font-size: 20px;
      margin-top: 10px;
      background: #fff;
      padding: 15px;
      border-radius: 10px;
      box-shadow: 0px 4px 8px rgba(0,0,0,0.2);
    }
  </style>
</head>
<body>
  <h1>Tap Me!</h1>
  <button onclick="tap()">👉 Tap</button>
  <div class="stats">
    <p>Total Taps: <span id="taps">0</span></p>
    <p>Gold Coins 🟡: <span id="gold">0</span></p>
    <p>Blue Coins 🔵: <span id="blue">0</span></p>
  </div>

  <script>
    // Load saved progress
    let taps = parseInt(localStorage.getItem("taps")) || 0;
    let gold = parseInt(localStorage.getItem("gold")) || 0;
    let blue = parseInt(localStorage.getItem("blue")) || 0;

    // Update UI
    function updateUI() {
      document.getElementById("taps").innerText = taps;
      document.getElementById("gold").innerText = gold;
      document.getElementById("blue").innerText = blue;
    }

    // Save progress
    function saveGame() {
      localStorage.setItem("taps", taps);
      localStorage.setItem("gold", gold);
      localStorage.setItem("blue", blue);
    }

    // Tap logic
    function tap() {
      taps++;

      // Every 1000 taps → 1 Gold
      if (taps % 1000 === 0) {
        gold++;
      }

      // Every 5000 taps → 1 Blue
      if (taps % 5000 === 0) {
        blue++;
      }

      updateUI();
      saveGame();
    }

    // Initialize
    updateUI();
  </script>
</body>
</html>
