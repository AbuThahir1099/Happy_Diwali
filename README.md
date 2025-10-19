<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fun Colorful Diwali Wish</title>
<style>
body {
    font-family: 'Arial', sans-serif;
    background: linear-gradient(120deg, #ffe29f, #ff7eb3, #8ee3ef, #a1ffce);
    background-size: 400% 400%;
    animation: gradientBG 15s ease infinite;
    color: #4b0082;
    text-align: center;
    margin: 0;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    overflow: hidden;
}

@keyframes gradientBG {
    0%{background-position:0% 50%;}
    50%{background-position:100% 50%;}
    100%{background-position:0% 50%;}
}

.poster-container {
    border: 10px double #ff6600;
    padding: 30px;
    max-width: 600px;
    background-color: rgba(255, 255, 255, 0.9);
    box-shadow: 0 0 20px rgba(0,0,0,0.5);
    border-radius: 15px;
    position: relative;
    overflow: hidden;
}

/* --- Input Screen --- */
#inputScreen h2 { font-size: 2em; color: #daaa00; margin-bottom: 25px; }
#nameInput { padding: 12px; font-size: 1.1em; border: 2px solid #ff6600; border-radius: 5px; width: 70%; max-width: 300px; margin-bottom: 20px; text-align: center; }
#nextButton { background-color: #4CAF50; color: white; padding: 10px 30px; font-size: 1.1em; border: none; border-radius: 5px; cursor: pointer; transition: background-color 0.3s; }
#nextButton:hover { background-color: #45a049; }
.error-message { color: red; font-size: 0.9em; height: 1.2em; margin-top: 5px; }

/* --- Wish Screen --- */
#wishScreen { display: none; animation: fadeIn 1.5s ease-in-out; }
@keyframes fadeIn { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }

.diya { font-size: 4em; color: #ffcc00; margin: 20px 0; text-shadow: 0 0 15px #ff8c00; }
h1 { font-size: 3.5em; color: #ff4f81; text-shadow: 2px 2px 4px #ffa500; margin-bottom: 0.1em; letter-spacing: 3px; text-transform: uppercase; }
.greeting-message { font-size: 1.5em; color: #ff69b4; margin-top: 0; margin-bottom: 1.5em; font-style: italic; }
.message-body { font-size: 1.2em; margin: 1em 0; line-height: 1.5; color: #ff4500; font-weight: bold; }
.personalized-wish { font-size: 1.8em; font-weight: bold; color: #ff0066; margin-top: 20px; }
.personalized-wish strong { font-weight: 900; color: #ff6600; }

/* --- Floating Confetti --- */
.confetti {
    position: absolute;
    width: 10px;
    height: 10px;
    background-color: red;
    opacity: 0.7;
    pointer-events: none;
    animation: floatUp 5s linear infinite;
    border-radius: 50%;
}
@keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg); opacity: 1; }
    50% { transform: translateY(-150px) rotate(180deg); opacity: 0.8; }
    100% { transform: translateY(-300px) rotate(360deg); opacity: 0; }
}
</style>
</head>
<body>

<div class="poster-container">
    <div id="inputScreen">
        <h2>What is your name?</h2>
        <input type="text" id="nameInput" placeholder="Enter your name here" autofocus>
        <br>
        <button id="nextButton">Next</button>
        <p class="error-message" id="errorMessage">&nbsp;</p>
    </div>

    <div id="wishScreen">
        <h2>A Special Diwali Wish for You!</h2>
        <p class="diya">🪔</p>
        <h1>Happy Diwali</h1>
        <p class="greeting-message">Wishing you lots of fun and happiness 🎉</p>
        <p class="message-body">May this festival be full of lights, laughter, and sweets!</p>
        <p class="personalized-wish" id="personalizer"></p>
    </div>
</div>

<script>
function proceedToWishScreen() {
    let userName = document.getElementById('nameInput').value.trim();
    const errorMessage = document.getElementById('errorMessage');

    if (userName.length < 2) {
        errorMessage.textContent = "Please enter a valid name.";
        document.getElementById('nameInput').focus();
        return;
    } else {
        errorMessage.textContent = "\u00a0";
    }

    document.getElementById('inputScreen').style.display = 'none';
    document.getElementById('wishScreen').style.display = 'block';

    document.getElementById('personalizer').innerHTML = `Abu for you, <strong>${userName}</strong>!`;

    // Add floating confetti
    for(let i=0; i<50; i++){
        const confetti = document.createElement('div');
        confetti.className = 'confetti';
        confetti.style.left = Math.random()*100 + '%';
        confetti.style.backgroundColor = `hsl(${Math.random()*360}, 100%, 60%)`;
        confetti.style.width = 5 + Math.random()*10 + 'px';
        confetti.style.height = confetti.style.width;
        confetti.style.animationDuration = 3 + Math.random()*5 + 's';
        document.querySelector('.poster-container').appendChild(confetti);
    }
}

document.getElementById('nextButton').addEventListener('click', proceedToWishScreen);
document.getElementById('nameInput').addEventListener('keydown', function(event) {
    if(event.key === 'Enter') proceedToWishScreen();
});
</script>

</body>
</html>
