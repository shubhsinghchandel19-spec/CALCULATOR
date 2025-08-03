# CALCULATOR
A stylish and functional calculator built using HTML, CSS, and JavaScript. Supports basic operations like addition, subtraction, multiplication, division, percentage, and decimals. Features a modern glassmorphism UI, responsive design, and smooth button interactions for a great user experience.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Advanced Calculator</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(to right, #141e30, #243b55);
    }

    .calculator {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(15px);
      border-radius: 20px;
      box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
      padding: 20px;
      width: 320px;
    }

    #display {
      width: 100%;
      height: 60px;
      font-size: 2rem;
      text-align: right;
      padding: 10px;
      border: none;
      border-radius: 10px;
      margin-bottom: 20px;
      background: rgba(255,255,255,0.15);
      color: #fff;
      outline: none;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 15px;
    }

    button {
      padding: 20px;
      font-size: 1.3rem;
      border: none;
      border-radius: 12px;
      background: rgba(255,255,255,0.1);
      color: #fff;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background: rgba(255,255,255,0.2);
    }

    .equal {
      background-color: #00c6ff;
      color: black;
    }

    .equal:hover {
      background-color: #00d4ff;
    }

    .zero {
      grid-column: span 2;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled />
    <div class="buttons">
      <button onclick="clearDisplay()">C</button>
      <button onclick="deleteLast()">⌫</button>
      <button onclick="appendOperator('%')">%</button>
      <button onclick="appendOperator('/')">÷</button>

      <button onclick="appendNumber('7')">7</button>
      <button onclick="appendNumber('8')">8</button>
      <button onclick="appendNumber('9')">9</button>
      <button onclick="appendOperator('*')">×</button>

      <button onclick="appendNumber('4')">4</button>
      <button onclick="appendNumber('5')">5</button>
      <button onclick="appendNumber('6')">6</button>
      <button onclick="appendOperator('-')">−</button>

      <button onclick="appendNumber('1')">1</button>
      <button onclick="appendNumber('2')">2</button>
      <button onclick="appendNumber('3')">3</button>
      <button onclick="appendOperator('+')">+</button>

      <button onclick="appendNumber('0')" class="zero">0</button>
      <button onclick="appendNumber('.')">.</button>
      <button onclick="calculateResult()" class="equal">=</button>
    </div>
  </div>

  <script>
    const display = document.getElementById('display');

    function appendNumber(number) {
      display.value += number;
    }

    function appendOperator(operator) {
      const lastChar = display.value.slice(-1);
      if ("+-*/%".includes(lastChar)) return;
      display.value += operator;
    }

    function clearDisplay() {
      display.value = '';
    }

    function deleteLast() {
      display.value = display.value.slice(0, -1);
    }

    function calculateResult() {
      try {
        display.value = eval(display.value.replace('×', '*').replace('÷', '/'));
      } catch {
        display.value = 'Error';
      }
    }
  </script>
</body>
</html>
