<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>The Mathrix: a Staircase-Themed Puzzle for Learning Rational Equations, Functions and One-to-One Functions</title>
  <style>
    body {
      font-family: "Press Start 2P", monospace, Arial, sans-serif;
      background: linear-gradient(180deg, #0d0d0d, #1a1a1a);
      color: #00ffcc;
      text-align: center;
      padding: 20px;
    }
    h1 {
      color: #ffcc00;
      font-size: 22px;
      text-shadow: 2px 2px #000;
      margin-bottom: 10px;
    }
    .sentence {
      margin: 20px auto;
      font-size: 16px;
      background: #111;
      padding: 15px;
      border: 3px solid #00ffcc;
      border-radius: 10px;
      display: inline-block;
      box-shadow: 0 0 10px #00ffcc;
    }
    input {
      padding: 8px;
      font-size: 14px;
      border-radius: 6px;
      border: 2px solid #ffcc00;
      outline: none;
      margin: 0 5px;
      background: #000;
      color: #fff;
    }
    .result {
      margin-left: 8px;
      font-weight: bold;
    }
    button {
      background: #ff0066;
      color: #fff;
      font-size: 14px;
      padding: 12px 25px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 20px;
      text-transform: uppercase;
      font-weight: bold;
      box-shadow: 0 0 12px #ff0066;
    }
    button:hover {
      background: #ff3399;
      box-shadow: 0 0 16px #ff3399;
    }
    #score {
      margin-top: 20px;
      font-size: 18px;
      color: #00ffcc;
      text-shadow: 1px 1px #000;
    }
  </style>
  <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
</head>
<body>
  <h1>The Mathrix: a Staircase-Themed Puzzle for Learning Rational Equations, Functions and One-to-One Functions</h1>
  <p>Fill in the blanks with the correct type of word to climb the staircase!</p>

  <div class="sentence">
    Math makes 
    <input type="text" id="blank0" placeholder="Noun (math)"> <span id="result0" class="result"></span> 
    <input type="text" id="blank1" placeholder="Adjective"> <span id="result1" class="result"></span>, 
    so keep 
    <input type="text" id="blank2" placeholder="Verb-ing action"> <span id="result2" class="result"></span> 
    and you will 
    <input type="text" id="blank3" placeholder="Verb"> <span id="result3" class="result"></span> 
    the 
    <input type="text" id="blank4" placeholder="Noun (arcade/math)"> <span id="result4" class="result"></span>!
  </div>

  <button onclick="checkAnswers()">Check Answers</button>
  <div id="score"></div>

  <script>
    // Word banks
    const answers = [
      ["numbers","patterns","equations","functions","logic","puzzles","solutions","formulas","sequences","graphs"],
      ["powerful","exciting","unbeatable","awesome","infinite","legendary","amazing","unstoppable","fun","supreme"],
      ["playing","solving","climbing","pressing start","leveling up","thinking","continuing","trying","calculating","exploring"],
      ["conquer","unlock","master","win","dominate","reach","clear","power up","achieve","complete"],
      ["challenge","game","function","quest","equation","puzzle","stage","level","problem","maze"]
    ];

    // Check answers
    function checkAnswers() {
      let score = 0;

      for (let i = 0; i < answers.length; i++) {
        let input = document.getElementById("blank" + i).value.trim().toLowerCase();
        const resultSpan = document.getElementById("result" + i);

        // Normalize multiple spaces in case of phrases
        input = input.replace(/\s+/g, " ");

        if (answers[i].includes(input)) {
          resultSpan.textContent = "✅";
          resultSpan.style.color = "lime";
          score++;
        } else {
          resultSpan.textContent = "❌";
          resultSpan.style.color = "red";
        }
      }

      document.getElementById("score").textContent = 
        `You got ${score}/5 correct.`;
    }
  </script>
</body>
</html>
