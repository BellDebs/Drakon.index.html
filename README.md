<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Drakon Birthday System</title>
<style>
body{
  margin:0;
  background:black;
  font-family:monospace;
  text-align:center;
  overflow:hidden;
}

/* Stars */
.star{
  position:absolute;
  width:2px;
  height:2px;
  background:white;
  animation:twinkle 4s infinite;
}
@keyframes twinkle{
  0%,100%{opacity:0.2;}
  50%{opacity:1;}
}

/* Center containers */
.center{
  position:absolute;
  top:50%;
  left:50%;
  transform:translate(-50%,-50%);
  width:90%;
  max-width:600px;
}
.hidden{display:none;}

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
