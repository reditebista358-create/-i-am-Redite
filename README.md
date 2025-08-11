<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Redite's Retro Kitty</title>

<style>
  body {
    margin: 0;
    overflow: hidden;
    background-color: black;
    font-family: "Courier New", monospace;
    color: #00ff99;
    text-align: center;
  }

  /* CRT Screen Effect */
  body::before {
    content: "";
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    background: repeating-linear-gradient(
      rgba(255,255,255,0.03) 0px,
      rgba(255,255,255,0.03) 1px,
      transparent 1px,
      transparent 2px
    );
    z-index: 1000;
  }

  h1 {
    margin-top: 30px;
    font-size: 2.5em;
    animation: flicker 1.5s infinite;
  }

  @keyframes flicker {
    0%, 19%, 21%, 23%, 25%, 54%, 56%, 100% {
      opacity: 1;
    }
    20%, 24%, 55% {
      opacity: 0.4;
    }
  }

  p {
    font-size: 1em;
    margin-top: 5px;
    color: #aaffdd;
  }

  /* Funny Button */
  .funny-btn {
    display: inline-block;
    background: #ff4081;
    color: white;
    padding: 15px 25px;
    font-size: 1.2em;
    border: none;
    border-radius: 10px;
    margin-top: 30px;
    cursor: pointer;
    box-shadow: 0 0 10px #ff80ab;
    transition: transform 0.2s, opacity 0.3s;
  }
  .funny-btn:hover {
    transform: scale(1.1);
  }

  /* Social Icons */
  .socials {
    position: fixed;
    bottom: 15px;
    left: 0;
    right: 0;
    display: flex;
    justify-content: center;
    gap: 15px;
    z-index: 1001;
  }
  .socials a img {
    width: 40px;
    height: 40px;
  }

  /* Floating Hello Kitty Images */
  .kitty {
    position: absolute;
    width: 50px;
    height: 50px;
    pointer-events: none;
    animation: float 5s linear forwards;
  }

  @keyframes float {
    0% { transform: translateY(0) rotate(0deg); opacity: 1; }
    100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
  }
</style>
</head>

<body>
  <h1>WELCOME</h1>
  <p>Hello, my name is Redite and these are my socials:</p>

  <!-- Funny Button -->
  <button class="funny-btn" id="funnyBtn">🚫 Don't Click Me 🚫</button>

  <!-- Social Icons -->
  <div class="socials">
    <a href="https://www.facebook.com/reditebista1" target="_blank"><img src="https://cdn-icons-png.flaticon.com/512/733/733547.png"></a>
    <a href="https://www.instagram.com/reditebista11/" target="_blank"><img src="https://cdn-icons-png.flaticon.com/512/733/733558.png"></a>
    <a href="https://www.tiktok.com/@reditebista" target="_blank"><img src="https://cdn-icons-png.flaticon.com/512/3046/3046121.png"></a>
    <a href="https://www.youtube.com/@reditebista4788" target="_blank"><img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png"></a>
  </div>

<script>
  const kittyImgs = [
    "https://upload.wikimedia.org/wikipedia/en/d/d8/Hello_Kitty_character_portrait.png",
    "https://i.imgur.com/Q7iKXGq.png",
    "https://i.imgur.com/oIqpM4I.png"
  ];

  function spawnKitty() {
    const img = document.createElement("img");
    img.src = kittyImgs[Math.floor(Math.random() * kittyImgs.length)];
    img.className = "kitty";
    img.style.left = Math.random() * window.innerWidth + "px";
    img.style.top = window.innerHeight + "px";
    document.body.appendChild(img);

    setTimeout(() => {
      img.remove();
    }, 5000);
  }

  setInterval(spawnKitty, 1500);

  // Funny button disappear effect
  document.getElementById("funnyBtn").addEventListener("click", function() {
    this.style.opacity = "0";
    setTimeout(() => {
      this.remove();
      alert("😆 I told you not to click!");
    }, 300);
  });
</script>
</body>
</html>
