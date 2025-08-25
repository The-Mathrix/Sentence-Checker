<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Word Check Activity</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #0d0d0d;
      color: #f0f0f0;
      text-align: center;
      padding: 20px;
    }
    h1 {
      color: #00ffcc;
    }
    .blank {
      margin: 15px 0;
    }
    input {
      padding: 6px;
      font-size: 16px;
      border-radius: 6px;
      border: none;
      outline: none;
      margin-left: 8px;
    }
    .result {
      margin-left: 10px;
      font-weight: bold;
    }
    button {
      background: #00ffcc;
      color: #000;
      font-size: 16px;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
    }
    button:hover {
      background: #00cc99;
    }
    #score {
      margin-top: 20px;
      font-size: 18px;
      color: #ffcc00;
    }
  </style>
</head>
<body>
  <h1>Word Type Checker</h1>
  <p>Fill in each blank with the correct type of word.</p>

  <div id="blanks"></div>

  <button onclick="checkAnswers()">Check Answers</button>
  <div id="score"></div>

  <script>
    // Define valid words for each blank
    const answers = [
      ["equation", "variable", "function"],      // 1: math noun
      ["complex", "difficult", "simple"],        // 2: adjective
      ["calculate", "solve", "compute"],         // 3: action
      ["derive", "add", "subtract"],             // 4: verb
      ["arcade", "matrix", "algorithm"],         // 5: math/arcade noun
      ["geometry", "algebra"],                   // 6: math noun
      ["challenging", "fun"],                    // 7: adjective
      ["analyze", "graph"],                      // 8: action
      ["play", "explore"],                       // 9: verb
      ["puzzle", "staircase"]                    // 10: noun (arcade/math)
    ];

    // Render input boxes
    const blanksDiv = document.getElementById("blanks");
    for (let i = 0; i < answers.length; i++) {
      blanksDiv.innerHTML += `
        <div class="blank">
          ${i + 1}. <input type="text" id="blank${i}" /> 
          <span class="result" id="result${i}"></span>
        </div>
      `;
    }

    // Check answers function
    function checkAnswers() {
      let score = 0;
      for (let i = 0; i < answers.length; i++) {
        const input = document.getElementById("blank" + i).value.trim().toLowerCase();
        const resultSpan = document.getElementById("result" + i);

        if (answers[i].includes(input)) {
          resultSpan.textContent = "✅";
          resultSpan.style.color = "lime";
          score++;
        } else {
          resultSpan.textContent = "❌";
          resultSpan.style.color = "red";
        }
      }
      document.getElementById("score").textContent = `You got ${score}/10 correct.`;
    }
  </script>
</body>
</html>
