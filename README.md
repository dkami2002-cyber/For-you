<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Be My Valentine 💖</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #ffb6c1, #ffe4e1);
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  .container {
    background: white;
    padding: 24px;
    border-radius: 20px;
    box-shadow: 0 15px 40px rgba(0,0,0,0.25);
    width: 90%;
    max-width: 380px;
    text-align: center;
  }

  h1 {
    color: #ff4d6d;
  }

  p {
    color: #444;
    font-size: 15px;
    line-height: 1.5;
  }

  img {
    width: 220px;
    border-radius: 16px;
    margin: 16px 0;
  }

  .buttons {
    position: relative;
    height: 140px;
  }

  button {
    padding: 12px 24px;
    font-size: 16px;
    border-radius: 30px;
    border: none;
    cursor: pointer;
  }

  #yesBtn, #confirmYes {
    background-color: #ff4d6d;
    color: white;
  }

  #noBtn {
    background-color: #ccc;
    position: absolute;
    right: 10px;
    top: 20px;
  }

  #loading {
    display: none;
    color: #ff4d6d;
    margin-top: 12px;
  }

  .heart {
    position: fixed;
    bottom: -20px;
    font-size: 20px;
    animation: floatUp 6s linear infinite;
  }

  @keyframes floatUp {
    from { transform: translateY(0); opacity: 1; }
    to { transform: translateY(-110vh); opacity: 0; }
  }
</style>
</head>

<body>

<div class="container" id="screen1">
  <h1>Jasmine, will you be my Valentine? 💘</h1>

  <p>
    I’ve been thinking about this for a while, and honestly… life is just better
    with you in it. You make ordinary days feel special, and I couldn’t imagine
    Valentine’s Day without asking you this 🥺👉👈
  </p>

  <img id="gif"
    src="https://media.giphy.com/media/v6aOjy0Qo1fIA/giphy.gif"
    alt="begging cat">

  <div class="buttons">
    <button id="yesBtn">Yes 💕</button>
    <button id="noBtn">No</button>
  </div>

  <div id="loading">Thinking really hard... 🤔💭</div>
</div>

<div class="container" id="screen2" style="display:none;">
  <h1>Are you sure? 😳💖</h1>
  <p>This is a rom-com level decision. Just checking 👀</p>
  <button id="confirmYes">Yes, I’m sure 💘</button>
</div>

<div class="container" id="screen3" style="display:none;">
  <h1>SHE SAID YES 😭💖</h1>
  <p>You just made me the happiest person alive 🥰</p>
  <img src="https://media.giphy.com/media/MDJ9IbxxvDUQM/giphy.gif" alt="happy cat">
</div>

<script>
  const noBtn = document.getElementById("noBtn");
  const yesBtn = document.getElementById("yesBtn");
  const confirmYes = document.getElementById("confirmYes");
  const loading = document.getElementById("loading");

  const screen1 = document.getElementById("screen1");
  const screen2 = document.getElementById("screen2");
  const screen3 = document.getElementById("screen3");

  function dodgeNo() {
    const x = Math.random() * 200;
    const y = Math.random() * 80;
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  }

  noBtn.addEventListener("mouseenter", dodgeNo);
  noBtn.addEventListener("touchstart", dodgeNo);

  yesBtn.onclick = () => {
    loading.style.display = "block";
    setTimeout(() => {
      screen1.style.display = "none";
      screen2.style.display = "block";
    }, 1200);
  };

  confirmYes.onclick = () => {
    screen2.style.display = "none";
    screen3.style.display = "block";
    startHearts();
  };

  function startHearts() {
    setInterval(() => {
      const heart = document.createElement("div");
      heart.className = "heart";
      heart.textContent = "💖";
      heart.style.left = Math.random() * 100 + "vw";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 6000);
    }, 350);
  }
</script>

</body>
</html>
