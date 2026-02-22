# AI-trade-LSG
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>AI Trading Analyzer</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<!-- NAVBAR -->
<nav class="navbar">
  <h1>AI Trading Analyzer</h1>
  <ul>
    <li>Home</li>
    <li>Markets</li>
    <li>AI Insights</li>
    <li>Upload</li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <h2>Smarter Trading with AI Precision</h2>
  <p>Upload charts. Detect trends. Optimize stop loss & take profit.</p>
</section>

<!-- IMAGE SHOWCASE -->
<section class="gallery">
  <img src="https://images.unsplash.com/photo-1640161704729-cbe966a08476" alt="AI">
  <img src="https://images.unsplash.com/photo-1642543492481-44e81e3914a7" alt="Analyst">
  <img src="https://images.unsplash.com/photo-1621761191319-c6fb62004040" alt="Crypto">
  <img src="https://images.unsplash.com/photo-1611974789855-9c2a0a7236a3" alt="Stocks">
</section>

<!-- AI INFO -->
<section class="info">
  <h3>How Our AI Works</h3>
  <p>
    Our AI analyzes chart screenshots using pattern recognition,
    trend detection, and volatility modeling. It is optimized for
    scalping, day trading, and small account growth strategies.
  </p>
</section>

<!-- UPLOAD PANEL -->
<section class="upload-panel">
  <h3>Upload Chart Screenshot</h3>
  <input type="file" id="imageUpload" accept="image/*">
  <img id="preview" />
  <button onclick="analyzeChart()">Analyze Chart</button>
</section>

<!-- ANALYSIS PANEL -->
<section class="analysis-panel">
  <h3>AI Trade Analysis</h3>
  <div class="cards">
    <div class="card">
      <h4>Trend</h4>
      <p id="trend">Waiting...</p>
    </div>
    <div class="card">
      <h4>Stop Loss</h4>
      <p id="stopLoss">Waiting...</p>
    </div>
    <div class="card">
      <h4>Take Profit</h4>
      <p id="takeProfit">Waiting...</p>
    </div>
    <div class="card">
      <h4>Signal</h4>
      <p id="signal">Waiting...</p>
    </div>
  </div>
</section>

<!-- MARKETS -->
<section class="markets">
  <h3>Popular Markets</h3>
  <div class="market-grid">
    <div>📈 NASDAQ</div>
    <div>₿ Bitcoin</div>
    <div>💱 EUR/USD</div>
    <div>🪙 Ethereum</div>
    <div>📊 S&P 500</div>
    <div>💹 Gold</div>
  </div>
</section>

<footer>
  <p>© 2026 AI Trading Analyzer — Smart Tools for Smart Traders</p>
</footer>

<script src="script.js"></script>
</body>
</html>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #000;
  color: #fff;
}

/* Navbar */
.navbar {
  display: flex;
  justify-content: space-between;
  padding: 15px 30px;
  background: #0a0a0a;
}

.navbar ul {
  display: flex;
  gap: 20px;
  list-style: none;
}

/* Hero */
.hero {
  text-align: center;
  padding: 50px 20px;
  background: linear-gradient(to right, #000, #111);
}

/* Gallery */
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  padding: 20px;
  gap: 10px;
}

.gallery img {
  width: 100%;
  border-radius: 10px;
}

/* Info */
.info {
  padding: 30px;
  text-align: center;
  background: #0a0a0a;
}

/* Upload */
.upload-panel {
  text-align: center;
  padding: 30px;
}

#preview {
  display: block;
  margin: 20px auto;
  max-width: 400px;
  border-radius: 10px;
}

/* Analysis */
.analysis-panel {
  padding: 30px;
}

.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 20px;
}

.card {
  background: #0a0a0a;
  padding: 20px;
  border-radius: 10px;
  text-align: center;
}

/* Markets */
.markets {
  padding: 30px;
  text-align: center;
}

.market-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
  gap: 10px;
}

/* Footer */
footer {
  text-align: center;
  padding: 20px;
  background: #0a0a0a;
}
const upload = document.getElementById("imageUpload");
const preview = document.getElementById("preview");

upload.addEventListener("change", function () {
  const file = this.files[0];
  if (file) {
    preview.src = URL.createObjectURL(file);
  }
});

function analyzeChart() {
  // Demo AI logic (replace with real AI later)
  const trends = ["Uptrend", "Downtrend", "Sideways"];
  const signals = ["BUY", "SELL", "WAIT"];

  const trend = trends[Math.floor(Math.random() * trends.length)];
  const signal = signals[Math.floor(Math.random() * signals.length)];

  document.getElementById("trend").textContent = trend;
  document.getElementById("stopLoss").textContent = "Auto-calculated";
  document.getElementById("takeProfit").textContent = "Auto-calculated";
  document.getElementById("signal").textContent = signal;
}
