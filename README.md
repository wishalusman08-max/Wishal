# Wishal
Happy birthday 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday</title>

<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>

<style>
*{
  box-sizing:border-box;
}
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg,#ff9a9e,#fad0c4);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Segoe UI', sans-serif;
  overflow: hidden;
}

.box {
  width: 90%;
  max-width: 400px;
  background: rgba(255,255,255,0.25);
  backdrop-filter: blur(12px);
  padding: 30px;
  border-radius: 25px;
  text-align: center;
  animation: float 3s ease-in-out infinite;
  box-shadow: 0 10px 30px rgba(0,0,0,0.25);
}

@keyframes float {
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-15px)}
}

h1{
  color:white;
  font-size:2.2rem;
}
p{
  color:white;
  font-weight:bold;
}

#countdown{
  font-size:1.1rem;
  margin-top:15px;
}

</style>
</head>

<body>

<div class="box">
  <h1>🎉 Happy Birthday <span id="name">Noreen</span> 🎉</h1>
  <p>💖 My Love | My Best Friend 💖</p>
  <p id="countdown"></p>
</div>

<audio id="music" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3">
</audio>

<script>
/* 🔧 CHANGE NAME HERE */
document.getElementById("name").innerText = "Noreen";

/* 🔧 CHANGE BIRTHDAY DATE HERE (YYYY-MM-DD) */
const birthdayDate = new Date("2026-02-10");

/* Countdown */
function updateCountdown(){
  const now = new Date();
  const diff = birthdayDate - now;

  if(diff <= 0){
    document.getElementById("countdown").innerHTML = "🎂 Today is your special day 🎂";
    startSurprise();
    clearInterval(timer);
    return;
  }

  const d = Math.floor(diff / (1000*60*60*24));
  const h = Math.floor((diff / (1000*60*60)) % 24);
  const m = Math.floor((diff / (1000*60)) % 60);

  document.getElementById("countdown").innerHTML =
    `⏳ ${d} Days ${h} Hours ${m} Minutes Left`;
}

const timer = setInterval(updateCountdown,1000);
updateCountdown();

/* Auto surprise */
function startSurprise(){
  document.getElementById("music").play();

  var duration = 10 * 1000;
  var end = Date.now() + duration;

  (function frame(){
    confetti({
      particleCount: 5,
      spread: 360,
      origin: { x: Math.random(), y: Math.random() - 0.2 }
    });
    if(Date.now() < end){
      requestAnimationFrame(frame);
    }
  })();
}
</script>

</body>
</html>
