<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Drakon Birthday Gift</title>
<style>
body {
  margin: 0;
  font-family: monospace;
  background: #000;
  color: #00ff99;
  text-align: center;
  overflow-x: hidden;
}

/* subtle stars background */
body::before {
  content: "";
  position: fixed;
  top:0;
  left:0;
  width:100%;
  height:100%;
  background: radial-gradient(white, transparent 1px) repeat;
  background-size: 50px 50px;
  opacity: 0.05;
  pointer-events:none;
}

/* Center containers */
.center {
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
  width:90%;
  max-width:600px;
}
.hidden {display:none;}

/* Input and button */
input {
  padding:12px;
  width:80%;
  border:none;
  border-radius:6px;
  text-align:center;
  font-size:18px;
  margin-top: 10px;
}
button {
  padding:12px 22px;
  margin-top:12px;
  background:#00ff99;
  border:none;
  border-radius:6px;
  cursor:pointer;
  font-size:16px;
}

/* Card */
.card {
  background: rgba(255,255,255,0.05);
  padding:30px;
  border-radius:15px;
  backdrop-filter: blur(8px);
  color:white;
  box-shadow:0 0 20px #00ff9955;
}

/* Message styling */
#message {
  white-space: pre-line;
  line-height:1.8;
  font-size:18px;
  color:#00ff99;
  opacity:0;
  transition:1s;
}

/* Dragon */
#dragon {
  font-size:50px;
  margin-bottom:10px;
  animation:dragonPulse 1.5s infinite alternate;
}
@keyframes dragonPulse {
  0%{transform:scale(1); opacity:0.7;}
  100%{transform:scale(1.2); opacity:1;}
}

/* Reward */
#reward {
  margin-top:20px;
  font-weight:bold;
  color: gold;
  font-size:18px;
  opacity:0;
  transition:1s;
}
.show {opacity:1;}

/* Sparkles */
.sparkle {
  position: absolute;
  width:4px;
  height:4px;
  background:white;
  border-radius:50%;
  pointer-events:none;
  animation:sparkleMove 1s forwards;
}
@keyframes sparkleMove {
  0% {transform:translate(0,0) scale(1); opacity:1;}
  100% {transform:translate(var(--x), var(--y)) scale(0); opacity:0;}
}
</style>
</head>
<body>

<!-- Audio -->
<audio id="music" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<!-- Login -->
<div id="login" class="center">
  <h2>System Authentication</h2>
  <input id="nameInput" placeholder="Enter Codename"><br>
  <button onclick="checkLogin()">Unlock</button>
  <p id="error"></p>
</div>

<!-- Gift -->
<div id="gift" class="center hidden">
  <div class="card">
    <div id="dragon">🐉</div>
    <h1>Welcome, Drakon</h1>
    <p id="message"></p>
    <button id="rewardBtn" class="hidden" onclick="showReward()">Accept Reward</button>
    <div id="reward">
      Wealth: <span id="wealth">0</span><br>
      Good Health: <span id="health">0</span><br>
      Happiness: <span id="happiness">0</span>
    </div>
  </div>
</div>

<script>
// check login
function checkLogin(){
  let name = document.getElementById("nameInput").value.trim().toLowerCase();
  if(name === "drakon"){
    document.getElementById("login").classList.add("hidden");
    document.getElementById("gift").classList.remove("hidden");

    // play music
    document.getElementById("music").play().catch(()=>{});

    // show message
    showMessage();
  } else {
    document.getElementById("error").innerText="Identity not recognized ❌";
  }
}

// show message with fade-in
function showMessage(){
  const msg=`Today we celebrate someone extraordinary.\n\nEmmanuel • Praise • Sunbola\n\nMay your life be filled with joy, success, and happiness.\nYour dreams will be realized.\nYour future is bright and unstoppable.\n\nKeep conquering, Drakon! 🥂✨`;
  let messageEl = document.getElementById("message");
  messageEl.innerText = msg;
  setTimeout(()=>{messageEl.style.opacity=1;},1000);
  // show reward button after delay
  setTimeout(()=>{document.getElementById("rewardBtn").classList.remove("hidden");},2000);
}

// show reward with counting and sparkles
function showReward(){
  const rewardEl = document.getElementById("reward");
  rewardEl.classList.add("show");
  document.getElementById("rewardBtn").disabled=true;

  animateValue("wealth",0,100,1000);
  animateValue("health",0,100,1000);
  animateValue("happiness",0,100,1000);

  // small sparkles
  for(let i=0;i<30;i++){
    createSparkle();
  }
}

// counting numbers
function animateValue(id, start, end, duration){
  let obj=document.getElementById(id);
  let range=end-start;
  let current=start;
  let increment=end>start?1:-1;
  let stepTime=Math.abs(Math.floor(duration/range));
  let timer=setInterval(function(){
    current+=increment;
    obj.innerText=current;
    if(current==end){clearInterval(timer);}
  },stepTime);
}

// sparkle effect
function createSparkle(){
  let sparkle=document.createElement("div");
  sparkle.className="sparkle";
  sparkle.style.top=Math.random()*80+"%";
  sparkle.style.left=Math.random()*80+"%";
  sparkle.style.setProperty("--x",(Math.random()*200-100)+"px");
  sparkle.style.setProperty("--y",(Math.random()*-200-50)+"px");
  document.body.appendChild(sparkle);
  setTimeout(()=>{sparkle.remove();},1000);
}
</script>

</body>
</html>
/* Input and button */
input{
  padding:12px;
  width:80%;
  border:none;
  border-radius:6px;
  text-align:center;
  font-size:18px;
}
button{
  padding:12px 22px;
  margin-top:12px;
  background:#00ff99;
  border:none;
  border-radius:6px;
  cursor:pointer;
  font-size:16px;
}

/* Card */
.card{
  background:rgba(255,255,255,0.05);
  padding:30px;
  border-radius:15px;
  backdrop-filter:blur(10px);
  color:white;
  box-shadow:0 0 25px #00ff9955;
}

/* Glowing neon text */
#message{
  white-space:pre-line;
  line-height:1.7;
  font-size:18px;
  color:#00ff99;
  text-shadow:
     0 0 5px #00ff99,
     0 0 10px #00ff99,
     0 0 20px #00ff99,
     0 0 40px #00ff99;
}

/* Dragon animation */
#dragon{
  font-size:60px;
  animation:dragonPulse 1.2s infinite alternate;
}
@keyframes dragonPulse{
  0%{transform:scale(1); opacity:0.7;}
  100%{transform:scale(1.2); opacity:1;}
}

/* Reward */
#reward{
  margin-top:20px;
  font-weight:bold;
  color:gold;
  opacity:0;
  transition:1s;
  font-size:18px;
}
.show{opacity:1;}
</style>
</head>
<body>

<!-- Stars -->
<script>
for(let i=0;i<100;i++){
  let s=document.createElement("div");
  s.className="star";
  s.style.top=Math.random()*100+"%";
  s.style.left=Math.random()*100+"%";
  document.body.appendChild(s);
}
</script>

<!-- Audio -->
<audio id="music" loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<!-- Login -->
<div id="login" class="center">
<h2>System Authentication</h2>
<input id="nameInput" placeholder="Enter Codename">
<br>
<button onclick="checkLogin()">Unlock</button>
<p id="error"></p>
</div>

<!-- Gift -->
<div id="gift" class="center hidden">
<div class="card">
<div id="dragon">🐉</div>
<h1>Welcome, Drakon</h1>
<p id="message"></p>
<button id="rewardBtn" class="hidden" onclick="showReward()">Accept Reward</button>
<div id="reward">
Wealth: <span id="wealth">0</span><br>
Good Health: <span id="health">0</span><br>
Happiness: <span id="happiness">0</span>
</div>
</div>
</div>

<script>
let typed=false;

// Check codename and start music
function checkLogin(){
  let name = document.getElementById("nameInput").value.trim().toLowerCase();
  if(name === "drakon"){
    document.getElementById("login").classList.add("hidden");
    document.getElementById("gift").classList.remove("hidden");

    // Start music
    const audio = document.getElementById("music");
    audio.play().catch(()=>{});

    typeMessage();
  } else {
    document.getElementById("error").innerText = "Identity not recognized ❌";
  }
}

// Typewriter message
const msg=`Today we celebrate someone extraordinary.

Emmanuel • Praise • Sunbola

May your life be filled with joy, success, and happiness.
Your dreams will be realized.
Your future is bright and unstoppable.

Keep conquering, Drakon! 🥂✨`;

let i=0;
function typeMessage(){
  if(i<msg.length){
    document.getElementById("message").innerText += msg.charAt(i);
    i++;
    setTimeout(typeMessage,25);
  } else {
    document.getElementById("rewardBtn").classList.remove("hidden");
  }
}

// Show reward with counting animation
function showReward(){
  document.getElementById("reward").classList.add("show");
  document.getElementById("rewardBtn").disabled = true;

  animateValue("wealth",0,100,1000);
  animateValue("health",0,100,1000);
  animateValue("happiness",0,100,1000);
}

// Count up animation
function animateValue(id, start, end, duration){
  let obj=document.getElementById(id);
  let range=end-start;
  let current=start;
  let increment=end>start?1:-1;
  let stepTime=Math.abs(Math.floor(duration/range));
  let timer=setInterval(function(){
    current+=increment;
    obj.innerText=current;
    if(current==end){clearInterval(timer);}
  },stepTime);
}
</script>

</body>
</html>
