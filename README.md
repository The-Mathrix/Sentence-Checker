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
    .sentence {
      margin: 20px 0;
      font-size: 20px;
    }
    input {
      padding: 6px;
      font-size: 16px;
      border-radius: 6px;
      border: none;
      outline: none;
      margin: 0 5px;
    }
    .result {
      margin-left: 8px;
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
  <p>Fill in the blanks with the correct type of word.</p>

  <div class="sentence">
    Math makes 
    <input type="text" id="blank0" placeholder="Noun (math)"> <span id="result0" class="result"></span> 
    <input type="text" id="blank1" placeholder="Adjective"> <span id="result1" class="result"></span>, 
    so keep 
    <input type="text" id="blank2" placeholder="Action"> <span id="result2" class="result"></span> 
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

      document.getElementById("score").textContent = `You got ${score}/5 correct.`;
    }
  </script>
</body>
</html>
