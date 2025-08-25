<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
<title>The Mathrix: a Staircase-Themed Puzzle for Learning Rational Equations, Functions and One-to-One Functions</title>
<style>
  body {
    font-family: "Press Start 2P", monospace, Arial, sans-serif;
    background: radial-gradient(circle at top, #2a003f, #0d001a);
    color: #e0b3ff;
    text-align: center;
    padding: 12px;
    max-width: 480px;
    margin: auto;
  }
  h1 {
    color: #ff66ff;
    font-size: 1rem;
    text-shadow: 0 0 5px #ff00ff, 0 0 10px #cc00cc;
    margin-bottom: 12px;
    line-height: 1.3;
  }
  p {
    font-size: 0.85rem;
    margin-bottom: 14px;
    color: #80ffff;
    text-shadow: 0 0 5px #00ffff;
  }
  .sentence {
    margin: 12px auto;
    font-size: 0.85rem;
    background: rgba(20, 0, 40, 0.9);
    padding: 12px;
    border: 2px solid #ff00cc;
    border-radius: 12px;
    max-width: 95%;
    box-shadow: 0 0 12px #ff00cc, 0 0 18px #800080;
    color: #ffffff;
  }
  input {
    padding: 6px;
    font-size: 0.85rem;
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
    font-size: 0.85rem;
    margin-top: 3px;
  }
  button {
    background: linear-gradient(135deg, #ff00cc, #6600ff);
    color: #fff;
    font-size: 1rem;
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
    font-size: 1rem;
    color: #80ffff;
    text-shadow: 0 0 6px #00ffff;
  }

  /* Terminal Section */
  .terminal-container {
    margin-top: 20px;
    background: #000;
    border: 2px solid #00ffcc;
    padding: 0.6rem;
    box-shadow: 0 0 12px #00ffcc;
    border-radius: 8px;
  }
  .terminal {
    height: 200px;
    overflow-y: auto;
    text-align: left;
    font-size: 0.7rem;
    white-space: pre-wrap;
    color: #00ffcc;
  }
  .term-input {
    display: flex;
    gap: 0.4rem;
    margin-top: 8px;
  }
  .term-input input {
    flex: 1;
    background: black;
    color: #fff;
    border: 2px solid #ff00ff;
    padding: 0.6rem;
    font-size: 0.8rem;
  }
  .term-input button {
    background: black;
    color: #fff;
    border: 2px solid #ff00ff;
    padding: 0.6rem;
    cursor: pointer;
    font-size: 0.8rem;
  }
  .term-input button:hover {
    background: #ff00ff;
    color: black;
  }
</style>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
</head>
<body>
  <h1>The Mathrix: a Staircase-Themed Puzzle for Learning Rational Equations, Functions and One-to-One Functions</h1>
  <p>Fill in the blanks with the correct type of word to climb the staircase!</p>

  <!-- Puzzle Section -->
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

  <!-- Terminal Section -->
  <div class="terminal-container">
    <div class="terminal" id="terminal"></div>
    <div class="term-input">
      <input id="termInput" placeholder="Type card number first" autocomplete="off" />
      <button id="okBtn" type="button">OK</button>
    </div>
  </div>

<script>
// ========== Part 1: Fill-in Puzzle ==========
const answers = [
  ["numbers","patterns","equations","functions","logic","puzzles","solutions","formulas","sequences","graphs"],
  ["powerful","exciting","unbeatable","awesome","infinite","legendary","amazing","unstoppable","fun","supreme"],
  ["playing","solving","climbing","leveling","thinking","continuing","trying","calculating","exploring","studying"],
  ["conquer","unlock","master","win","dominate","reach","clear","achieve","complete","overcome"],
  ["challenge","game","function","quest","equation","puzzle","stage","level","problem","maze"]
];

function checkAnswers() {
  let score = 0;
  for (let i = 0; i < answers.length; i++) {
    let input = document.getElementById("blank" + i).value.trim().toLowerCase();
    const resultSpan = document.getElementById("result" + i);

    if (answers[i].includes(input)) {
      resultSpan.textContent = "✅ Correct!";
      resultSpan.style.color = "#00ff99";
      score++;
    } else {
      resultSpan.textContent = "❌ Wrong!";
      resultSpan.style.color = "#ff3366";
    }
  }
  document.getElementById("score").textContent = `You got ${score}/5 correct.`;
}

// ========== Part 2: Terminal Q&A ==========
function normalize(s) {
  return s.toLowerCase().replace(/\s+/g, '').replace(/−/g, '-').replace(/\u200b/g,'').replace(/\bor\b/g,'').replace(/[()]/g,'');
}

// --- A FEW sample answers (you can insert all 50 here as needed) ---
const correctAnswers = {
  1:{question:"x/5 = 25",answers:["125"]},
  2:{question:"x/4 = 30",answers:["120"]},
  3:{question:"3x/2 = 180",answers:["120"]}
  // ... (add rest of 50 cards here)
};

let currentCard=null,waitingForAnswer=false,terminal,termInput,okBtn;

function appendLine(text){
  const div=document.createElement("div");
  div.textContent=text;
  terminal.appendChild(div);
  terminal.scrollTop=terminal.scrollHeight;
}
function printWelcome(){
  appendLine("Welcome to The Mathrix Terminal!");
  appendLine("Step 1: Type a card number.");
  appendLine("Step 2: Answer the question.");
  appendLine("Step 3: Retry if wrong, or pick another card.");
}
function handleCardNumber(input){
  const num=parseInt(input,10);
  if(!correctAnswers[num]){appendLine(`❌ Card ${input} not found.`);resetState();return;}
  currentCard=num;waitingForAnswer=true;
  appendLine(`📜 Card ${num}: ${correctAnswers[num].question}`);
  appendLine("Now type your answer:");
  termInput.placeholder="Type your answer";
}
function handleAnswer(input){
  if(/^\d+$/.test(input) && correctAnswers[parseInt(input,10)]){handleCardNumber(input);return;}
  if(currentCard===null){appendLine("❌ Please select a card first.");resetState();return;}
  const ans=normalize(input);
  const valid=correctAnswers[currentCard].answers.map(a=>normalize(a));
  if(valid.includes(ans)){appendLine("✅ Correct!");resetState();appendLine("Type another card number to continue.");}
  else{appendLine("❌ Wrong. Try again, or pick another card.");termInput.placeholder="Retry or new card";}
}
function sendCommand(){
  const val=termInput.value.trim();if(!val)return;
  appendLine("> "+val);
  if(!waitingForAnswer)handleCardNumber(val);else handleAnswer(val);
  termInput.value="";termInput.focus();
}
function resetState(){currentCard=null;waitingForAnswer=false;termInput.placeholder="Type card number first";}
window.onload=function(){
  terminal=document.getElementById("terminal");
  termInput=document.getElementById("termInput");
  okBtn=document.getElementById("okBtn");
  printWelcome();
  okBtn.addEventListener("click",sendCommand);
  termInput.addEventListener("keydown",e=>{if(e.key==="Enter")sendCommand();});
};
</script>
</body>
</html>
