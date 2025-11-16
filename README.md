<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>☠️ My Interactive Page ☠️</title>
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      text-align: center;
      padding: 2rem;
      transition: all 0.4s ease;
      background-color: #E8D1E4;
      color: #333;
      font-size: 18px; /* Base size for text resizer */
    }

    h1 { font-size: 2.5rem; margin-bottom: 1rem; }
    button {
      padding: 1rem 2rem;
      font-size: 1.2rem;
      border: none;
      border-radius: 10px;
      background-color: #1b851b;
      cursor: pointer;
      transition: background-color 0.3s ease;
      margin: .5rem;
    }
    button:hover { background-color: #ff8400; }

    .dark {
      background-color: #222;
      color: white;
    }
  </style>
</head>
<body>
  <h1 id="welcome">Welcome! ✨</h1>
  <p id="greeting">Let's make your page come alive ✨</p>
  <button id="themeBtn">Toggle Dark Mode 🌗</button>

  <!-- NEW FEATURE 1: LIVE CLOCK -->
  <h2>Current Time ⏰</h2>
  <p id="clock" style="font-size:1.5rem; font-weight:bold;"></p>

  <hr>

  <h2>Click Counter 💥</h2>
  <p>You’ve clicked the button <span id="clickCount">0</span> times!</p>
  <button id="clickButton">Click me!</button>

  <hr>

  <h2>Quote of the Day 💬</h2>
  <p id="quote">How about some inspiration!</p>
  <button id="quoteBtn">✨ New Quote</button>

  <hr>

  <!-- NEW FEATURE 2: TEXT SIZE CONTROLLER -->
  <h2>Adjust Text Size 🔍</h2>
  <button id="increaseText">A➕ Increase</button>
  <button id="decreaseText">A➖ Decrease</button>

  <script>
    const btn = document.getElementById('themeBtn');
    const body = document.body;

    btn.addEventListener('click', () => {
      body.classList.toggle('dark');
    });

    // Ask for visitor's name
    const name = prompt("What's your name?");
    if (name) {
      document.getElementById('welcome').textContent = `Hey there, ${name}! 🙂`;
    }

    // Dynamic greeting
    const hour = new Date().getHours();
    let message;
    if (hour < 12) message = "☀️ Good morning!";
    else if (hour < 18) message = "🌤️ Good afternoon!";
    else message = "🌙 Good evening!";
    document.getElementById('greeting').textContent = message;

    // Start the counter at 0
    let count = 0;

    const button = document.getElementById("clickButton");
    const display = document.getElementById("clickCount");

    function getRandomColour() {
      const letters = '0123456789ABCDEF';
      let colour = '#';
      for (let i = 0; i < 6; i++) {
        colour += letters[Math.floor(Math.random() * 16)];
      }
      return colour;
    }

    button.addEventListener("click", function() {
      count++;
      display.textContent = count;
      document.body.style.backgroundColor = getRandomColour();
    });

    // Quotes
    const quotes = [
      "There is some good in this world, and it’s worth fighting for. — J.R.R. Tolkien",
      "Do or do not, there is no try. — Yoda",
      "What is essential is invisible to the eye. — The Little Prince",
      "Beware; for I am fearless, and therefore powerful. — Mary Shelley",
      "To thine own self be true. — William Shakespeare",
      "Who controls the past controls the future. — George Orwell"
    ];

    const quoteDisplay = document.getElementById("quote");
    const quoteBtn = document.getElementById("quoteBtn");

    quoteBtn.addEventListener("click", () => {
      const randomIndex = Math.floor(Math.random() * quotes.length);
      quoteDisplay.textContent = quotes[randomIndex];
    });

    // NEW FEATURE 1: LIVE CLOCK
    function updateClock() {
      const now = new Date();
      document.getElementById("clock").textContent =
        now.toLocaleTimeString();
    }
    setInterval(updateClock, 1000);
    updateClock();

    // NEW FEATURE 2: TEXT SIZE ADJUSTER
    const increaseText = document.getElementById("increaseText");
    const decreaseText = document.getElementById("decreaseText");

    increaseText.addEventListener("click", () => {
      const currentSize = parseFloat(window.getComputedStyle(body).fontSize);
      body.style.fontSize = (currentSize + 2) + "px";
    });

    decreaseText.addEventListener("click", () => {
      const currentSize = parseFloat(window.getComputedStyle(body).fontSize);
      if (currentSize > 10) {
        body.style.fontSize = (currentSize - 2) + "px";
      }
    });
  </script>
</body>
</html>
