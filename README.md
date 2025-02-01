<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Proposal</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: pink;
            font-family: Arial, sans-serif;
            text-align: center;
            overflow: hidden;
            margin: 0;
        }
        .proposal {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
            position: relative;
            z-index: 2;
            transition: opacity 1s ease;
        }
        .heart {
            color: red;
            font-size: 50px;
        }
        .buttons {
            margin-top: 20px;
        }
        button {
            padding: 10px 20px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 5px;
        }
        .yes {
            background: red;
            color: white;
        }
        .no {
            background: gray;
            color: white;
        }
        .emoji {
            position: absolute;
            font-size: 30px;
        }
        .rose {
            position: absolute;
            font-size: 30px;
            color: red;
            animation: fall 3s linear infinite;
        }
        @keyframes fall {
            from { transform: translateY(-10px); opacity: 1; }
            to { transform: translateY(100vh); opacity: 0; }
        }
    </style>
    <script>
        let noButtonPressCount = 0;  // Initialize a counter for the "No" button presses

        function acceptProposal() {
            document.getElementById('message').innerHTML = "Do you want to go to the movies together? 🎬❤️";
            document.getElementById('buttons').innerHTML = '<button class="yes" onclick="movieYes()">Yes!</button> <button class="no" onclick="movieNo()">No</button>';
        }

        function movieYes() {
            document.getElementById('message').innerHTML = "Yay! We will have so much fun! 🌹";
            document.getElementById('buttons').innerHTML = '<button class="yes" onclick="msgMe()">Message Me!</button>';
            startRoses();
        }

        function movieNo() {
            noButtonPressCount++;  // Increment the counter when "No" is pressed
            if (noButtonPressCount >= 3) {
                // If the "No" button is pressed 3 times, redirect to the YouTube link
                window.location.href = "https://youtu.be/4yZ-mn0u8NE?si=CMCoA8JxIemk_Byc";
            } else {
                document.getElementById('message').innerHTML = "Why? I just wanted to spend time with you. 😢";
                startCryingEmojis();
                setTimeout(() => {
                    window.location.href = "https://www.romantic-messages.com";  // Keep this redirection in case the user presses once or twice
                }, 3000);
            }
        }

        function msgMe() {
            window.location.href = "https://www.instagram.com/aviyanskshrestha/";
        }

        function startCryingEmojis() {
            for (let i = 0; i < 10; i++) {
                let emoji = document.createElement('div');
                emoji.className = 'emoji';
                emoji.innerHTML = '😭';
                emoji.style.left = Math.random() * window.innerWidth + 'px';
                emoji.style.top = Math.random() * window.innerHeight + 'px';
                document.body.appendChild(emoji);
            }
        }

        function startRoses() {
            for (let i = 0; i < 20; i++) {
                let rose = document.createElement('div');
                rose.className = 'rose';
                rose.innerHTML = '🌹';
                rose.style.left = Math.random() * window.innerWidth + 'px';
                rose.style.animationDuration = (Math.random() * 3 + 2) + 's';
                document.body.appendChild(rose);
            }
        }

        function moveButton() {
            let btn = document.getElementById('noBtn');
            let x = Math.random() * (window.innerWidth - 100);
            let y = Math.random() * (window.innerHeight - 50);
            btn.style.position = "absolute";
            btn.style.left = x + "px";
            btn.style.top = y + "px";
        }
    </script>
</head>
<body>
    <div class="proposal">
        <h1>Will You Be My Valentine? <span class="heart">❤️</span></h1>
        <p id="message">You make my world brighter, and I’d love to spend this special day with you.</p>
        <div class="buttons" id="buttons">
            <button class="yes" onclick="acceptProposal()">Yes!</button>
            <button class="no" id="noBtn" onmouseover="moveButton()" onclick="movieNo()">No</button>
        </div>
    </div>
</body>
</html>
