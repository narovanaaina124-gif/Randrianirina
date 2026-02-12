christian
html lang="mg">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Future Prediction 🔮</title>
<style>
body{
    margin:0;
    font-family: Arial, sans-serif;
    color:white;
    text-align:center;
    background: radial-gradient(circle at top, #1b2735, #090a0f);
    overflow-x:hidden;
}

/* Galaxy animation */
.stars {
    width:100%;
    height:100%;
    position:fixed;
    top:0;
    left:0;
    background:#000;
    overflow:hidden;
    z-index:-1;
}
.star{
    position:absolute;
    background:white;
    border-radius:50%;
    animation: twinkle 5s infinite;
}
@keyframes twinkle{
    0%,100%{opacity:0.3;}
    50%{opacity:1;}
}

/* Header */
header{
    font-size:2rem;
    margin-top:20px;
    color:#00d2ff;
    font-weight:bold;
}

/* Input & Button */
input, button{
    padding:10px;
    border-radius:8px;
    border:none;
    margin:5px;
    font-size:1rem;
}
input{
    width:70%;
}
button{
    background:#00d2ff;
    color:black;
    font-weight:bold;
    cursor:pointer;
}
button:hover{
    background:#3a7bd5;
    color:white;
}

/* Timer */
.timer{
    display:flex;
    justify-content:center;
    gap:15px;
    margin-top:20px;
}
.box{
    background:#16213e;
    padding:15px;
    border-radius:15px;
    width:80px;
    box-shadow:0 0 15px #00d2ff;
}
.number{
    font-size:1.5rem;
    font-weight:bold;
}

/* Prediction */
#predictionBox{
    margin-top:30px;
    padding:20px;
    width:80%;
    margin-left:auto;
    margin-right:auto;
    background:#16213e;
    border-radius:15px;
    box-shadow:0 0 20px #ffdd59;
    display:none;
    font-size:1.2rem;
    color:#ffdd59;
}
</style>
</head>
<body>

<div class="stars" id="stars"></div>

<header>🔮 FUTURE PREDICTION 🔮</header>

<p>Apetraka ny fanontanianao:</p>
<input type="text" id="question" placeholder="Soraty eto ny fanontaniana..."><br>

<p>Fidio ny fotoana:</p>
<input type="number" id="hoursInput" placeholder="Heure" min="0">
<input type="number" id="minutesInput" placeholder="Minute" min="0">
<input type="number" id="secondsInput" placeholder="Seconde"><br>

<button onclick="startPrediction()">START PREDICTION</button>

<div class="timer">
    <div class="box"><div class="number" id="hours">00</div>Heure</div>
    <div class="box"><div class="number" id="minutes">00</div>Minute</div>
    <div class="box"><div class="number" id="seconds">00</div>Seconde</div>
</div>

<div id="predictionBox">
    <h2>✨ Prediction ✨</h2>
    <p id="predictionText"></p>
</div>

<audio id="sound" src="https://www.soundjay.com/misc/sounds/magic-chime-01.mp3"></audio>

<script>
// Galaxy stars
const starCount=50;
const starsEl=document.getElementById("stars");
for(let i=0;i<starCount;i++){
    const star=document.createElement("div");
    star.className="star";
    star.style.width=star.style.height=Math.random()*3+1+"px";
    star.style.top=Math.random()*100+"%";
    star.style.left=Math.random()*100+"%";
    star.style.animationDuration=(Math.random()*5+3)+"s";
    starsEl.appendChild(star);
}

// Predictions
const predictions=[
    "Ho tanteraka tsy ho ela ny fanirianao.",
    "Misy vintana lehibe miandry anao.",
    "Mitandrema amin'ny fanapahan-kevitra raisinao.",
    "Ho avy ny fahombiazana raha mahery fo ianao.",
    "Misy fiovana tsara ho avy eo amin'ny fiainanao."
];

function startPrediction(){
    let h=parseInt(document.getElementById("hoursInput").value)||0;
    let m=parseInt(document.getElementById("minutesInput").value)||0;
    let s=parseInt(document.getElementById("secondsInput").value)||0;
    let totalSeconds=h*3600+m*60+s;
    if(totalSeconds<=0){alert("Ampidiro ny fotoana!");return;}
    document.getElementById("predictionBox").style.display="none";
    let countdown=setInterval(function(){
        if(totalSeconds<=0){
            clearInterval(countdown);
            showPrediction();
            return;
        }
        totalSeconds--;
        let hours=Math.floor(totalSeconds/3600);
        let minutes=Math.floor((totalSeconds%3600)/60);
        let seconds=totalSeconds%60;
        document.getElementById("hours").innerText=String(hours).padStart(2,'0');
        document.getElementById("minutes").innerText=String(minutes).padStart(2,'0');
        document.getElementById("seconds").innerText=String(seconds).padStart(2,'0');
    },1000);
}

function showPrediction(){
    let randomIndex=Math.floor(Math.random()*predictions.length);
    document.getElementById("predictionText").innerText=predictions[randomIndex];
    document.getElementById("predictionBox").style.display="block";
    document.getElementById("sound").play();
}
</script>

</body>
</html>

