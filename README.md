<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
<title>The Mathrix: a Staircase-Themed Puzzle</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
<style>
  body {
    margin: 0;
    font-family: "Press Start 2P", monospace, Arial, sans-serif;
    background: radial-gradient(circle at top, #2a003f, #0d001a);
    color: #e0b3ff;
    text-align: center;
    padding: 8px;
    max-width: 480px;
    margin: auto;
  }
  h1 {
    color: #ff66ff;
    font-size: clamp(16px, 4vw, 28px);
    text-shadow: 0 0 5px #ff00ff, 0 0 10px #cc00cc;
    margin-bottom: 10px;
    line-height: 1.3;
  }
  p {
    font-size: clamp(12px, 3.2vw, 18px);
    margin-bottom: 12px;
    color: #80ffff;
    text-shadow: 0 0 5px #00ffff;
  }
  .sentence {
    margin: 10px auto;
    font-size: clamp(12px, 3vw, 18px);
    background: rgba(20, 0, 40, 0.9);
    padding: 10px;
    border: 2px solid #ff00cc;
    border-radius: 12px;
    display: block;
    max-width: 95%;
    box-shadow: 0 0 12px #ff00cc, 0 0 18px #800080;
    color: #ffffff;
  }
  input {
    padding: 6px;
    font-size: clamp(12px, 3vw, 18px);
    border-radius: 6px;
    border: 2px solid #00ffff;
    outline: none;
    margin: 5px auto;
    background: #1a0033;
    color: #fff;
    width: 85%;
    display: block;
    box-shadow: 0 0 8px #00ffff, 0 0 12px #0088ff inset;
    text-align: center;
  }
  input::placeholder { color: #ccccff; }
  .result {
    display: block;
    font-weight: bold;
    font-size: clamp(12px, 3vw, 18px);
    margin-top: 3px;
  }
  button {
    background: linear-gradient(135deg, #ff00cc, #6600ff);
    color: #fff;
    font-size: clamp(14px, 3.5vw, 22px);
    padding: 10px 18px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    margin-top: 14px;
    text-transform: uppercase;
    font-weight: bold;
    box-shadow: 0 0 12px #ff00ff, 0 0 16px #6600ff;
  }
  button:hover {
    background: linear-gradient(135deg, #ff33ff, #8000ff);
    box-shadow: 0 0 16px #ff33ff, 0 0 20px #8000ff;
  }
  #score {
    margin-top: 14px;
    font-size: clamp(14px, 3.5vw, 22px);
    color: #80ffff;
    text-shadow: 0 0 6px #00ffff;
  }

  /* --- Terminal Section --- */
  .terminal-container {
    margin-top: 20px;
    text-align: left;
  }
  .terminal {
    background: #000;
    border: 2px solid #00ffcc;
    padding: 0.6rem;
    overflow-y: auto;
    height: 220px;
    box-shadow: 0 0 8px #00ffcc;
    font-size: 0.9rem;
    line-height: 1.4;
    white-space: pre-wrap;
    color: #00ffcc;
  }
  .term-input {
    display: flex;
    gap: 0.4rem;
    margin-top: 5px;
  }
  .term-input input {
    flex: 1;
    background: black;
    color: #fff;
    border: 2px solid #ff00ff;
    padding: 0.4rem;
    font-size: 0.9rem;
  }
  .term-input button {
    background: black;
    color: #fff;
    border: 2px solid #ff00ff;
    padding: 0.4rem;
    cursor: pointer;
    font-size: 0.9rem;
  }
  .term-input button:hover {
    background: #ff00ff;
    color: black;
  }
</style>
</head>
<body>
  <h1>The Mathrix: a Staircase-Themed Puzzle</h1>

  <!-- Terminal Game FIRST -->
  <p>🎮 Step 1: Enter the <b>Mathrix Terminal</b> to solve equations & functions 🎮</p>
  <div class="terminal-container">
    <div class="terminal" id="terminal"></div>
    <div class="term-input">
      <input id="termInput" placeholder="Type card number first" autocomplete="off" />
      <button id="okBtn" type="button">OK</button>
    </div>
  </div>

  <!-- Fill in the Blank SECOND -->
  <p>🎮 Step 2: Climb the staircase by filling in the blanks! 🎮</p>
  <div class="sentence">
    Math makes 
    <input type="text" id="blank0" placeholder="Noun (math)"> <span id="result0" class="result"></span>
    <input type="text" id="blank1" placeholder="Adjective"> <span id="result1" class="result"></span>, 
    so keep 
    <input type="text" id="blank2" placeholder="Verb-ing (action)"> <span id="result2" class="result"></span> 
    and you will 
    <input type="text" id="blank3" placeholder="Verb"> <span id="result3" class="result"></span> 
    the 
    <input type="text" id="blank4" placeholder="Noun (arcade/math)"> <span id="result4" class="result"></span>!
  </div>
  <button onclick="checkAnswers()">Check Answers</button>
  <div id="score"></div>

<script>
/* --- Terminal Game --- */
function normalize(s) {
  return s.toLowerCase()
          .replace(/\s+/g,'')
          .replace(/−/g,'-')
          .replace(/\u200b/g,'')
          .replace(/\bor\b/g,'');
}
...
</script>
</body>
</html>
