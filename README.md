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
      padding: 10px;
    }
    h1 {
      color: #ffcc00;
      font-size: 4vw; /* responsive heading */
      text-shadow: 2px 2px #000;
      margin-bottom: 10px;
      line-height: 1.4;
    }
    p {
      font-size: 3.5vw;
      margin-bottom: 15px;
    }
    .sentence {
      margin: 10px auto;
      font-size: 3.5vw;
      background: #111;
      padding: 10px;
      border: 3px solid #00ffcc;
      border-radius: 10px;
      display: block;
      max-width: 95%;
      box-shadow: 0 0 10px #00ffcc;
      word-wrap: break-word;
    }
    input {
      padding: 6px;
      font-size: 3.2vw;
      border-radius: 6px;
      border: 2px solid #ffcc00;
      outline: none;
      margin: 4px 0;
      background: #000;
      color: #fff;
      width: 80%; /* inputs fit mobile screen */
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    .result {
      margin-left: 4px;
      font-weight: bold;
      font-size: 3.5vw;
    }
    button {
      background: #ff0066;
      color: #fff;
      font-size: 4vw;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin-top: 15px;
      text-transform: uppercase;
      font-weight: bold;
      box-shadow: 0 0 12px #ff0066;
    }
    button:hover {
      background: #ff3399;
      box-shadow: 0 0 16px #ff3399;
    }
    #score {
      margin-top: 15px;
      font-size: 4vw;
      color: #00ffcc;
      text-shadow: 1px 1px #000;
    }

    /* Mobile optimization */
    @media (min-width: 600px) {
      h1 { font-size: 22px; }
      p, .sentence, input, button, #score { font-size: 16px; }
      input { width: auto; display: inline-block; }
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

        input = input.replace(/\s+/g, " "); // normalize spaces

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
