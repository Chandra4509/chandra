<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Proposal 💍</title>
    <style>
        body {
            font-family: 'Comic Sans MS', sans-serif;
            background-color: #fff0f5;
            text-align: center;
            padding: 30px;
        }
        h1 {
            color: #ff69b4;
        }
        button {
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 5px;
            background-color: #ff69b4;
            color: white;
            border: none;
            margin-top: 20px;
        }
        img {
            width: 200px;
            margin-top: 20px;
            display: none;
        }
        #proposal, #endMessage, #clue2, #clue3 {
            margin-top: 20px;
            font-size: 1.5em;
            color: #ff4500;
            display: none;
        }
        @keyframes fadeIn {
            from {opacity: 0;}
            to {opacity: 1;}
        }
    </style>
</head>
<body>
    <h1>Hey [Anamika] 👋</h1>
    <p>Are you ready for a fun little surprise? 🎁</p>
    
    <button onclick="startSpeechRecognition()">Say "show me" to begin... 🎤</button>

    <p id="listenStatus" style="display:none;">Listening for "show me"... 🎤</p>
    <img id="listeningGif" src="https://media.giphy.com/media/xT0xeJpnrWC4XWblEk/giphy.gif" alt="Listening...">

    <!-- Message Part 1 -->
    <p id="message" style="display:none;">Nice! I heard you! Wait for it... I have something important to say.</p>
    <img id="thinkingGif" src="https://media.giphy.com/media/xUPGGDNsLvqsBOhuU0/giphy.gif" alt="Thinking...">
    
    <button id="continueButton1" style="display:none;" onclick="showClue1()">Click to Continue</button>
    
    <!-- Clue Part 1 -->
    <p id="clue1" style="display:none;">Okay... it's something I've been meaning to ask you for a while...</p>
    <img id="suspenseGif1" src="https://media.giphy.com/media/26ufdipQqU2lhNA4g/giphy.gif" alt="Suspense...">
    
    <button id="continueButton2" style="display:none;" onclick="showClue2()">Ready for more? Click here</button>
    
    <!-- Clue Part 2 -->
    <p id="clue2" style="display:none;">It's a little awkward but... it’s important! 😳</p>
    <img id="suspenseGif2" src="https://media.giphy.com/media/xT9DPCU60mRbtGw7Ys/giphy.gif" alt="Awkward...">
    
    <button id="continueButton3" style="display:none;" onclick="showClue3()">Click to continue...</button>
    
    <!-- Clue Part 3 -->
    <p id="clue3" style="display:none;">I think you're gonna love this... (No spoilers! 😏)</p>
    <img id="mysteryGif" src="https://media.giphy.com/media/dsXf1yjzD6g7S/giphy.gif" alt="Mystery...">
    
    <button id="continueButton4" style="display:none;" onclick="showProposal()">Click for the big reveal</button>
    
    <!-- Proposal Part -->
    <p id="proposal" style="display:none;">Will you always be the one who saves me the last slice of pizza? 🍕😜</p>
    <img id="pizzaGif" src="https://media.giphy.com/media/l3vRkZsxMAAIFiTOc/giphy.gif" alt="Pizza Time">

    <!-- Final Message -->
    <p id="endMessage" style="display:none;">Just kidding! Thanks for being an awesome friend! 😄</p>
    
    <script>
        function startSpeechRecognition() {
            document.getElementById('listenStatus').style.display = 'block';
            document.getElementById('listeningGif').style.display = 'block';

            // Use the Web Speech API for speech recognition
            var recognition = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
            recognition.lang = 'en-US';
            recognition.interimResults = false;
            recognition.maxAlternatives = 1;

            recognition.start();

            recognition.onresult = function(event) {
                var speechResult = event.results[0][0].transcript.toLowerCase();
                if (speechResult.includes("show me")) {
                    showMessage();
                } else {
                    alert('Please say "show me" to continue.');
                }
            };

            recognition.onerror = function(event) {
                alert('Error occurred in recognition: ' + event.error);
            };
        }

        // Show the next message when "show me" is detected
        function showMessage() {
            document.getElementById('listenStatus').style.display = 'none';
            document.getElementById('listeningGif').style.display = 'none';
            document.getElementById('message').style.display = 'block';
            document.getElementById('thinkingGif').style.display = 'block';
            setTimeout(function() {
                document.getElementById('thinkingGif').style.display = 'none';
                document.getElementById('continueButton1').style.display = 'block';
            }, 3000);
        }

        function showClue1() {
            document.getElementById('continueButton1').style.display = 'none';
            document.getElementById('message').style.display = 'none';
            document.getElementById('clue1').style.display = 'block';
            document.getElementById('suspenseGif1').style.display = 'block';
            setTimeout(function() {
                document.getElementById('suspenseGif1').style.display = 'none';
                document.getElementById('continueButton2').style.display = 'block';
            }, 3000);
        }

        function showClue2() {
            document.getElementById('continueButton2').style.display = 'none';
            document.getElementById('clue1').style.display = 'none';
            document.getElementById('clue2').style.display = 'block';
            document.getElementById('suspenseGif2').style.display = 'block';
            setTimeout(function() {
                document.getElementById('suspenseGif2').style.display = 'none';
                document.getElementById('continueButton3').style.display = 'block';
            }, 3000);
        }

        function showClue3() {
            document.getElementById('continueButton3').style.display = 'none';
            document.getElementById('clue2').style.display = 'none';
            document.getElementById('clue3').style.display = 'block';
            document.getElementById('mysteryGif').style.display = 'block';
            setTimeout(function() {
                document.getElementById('mysteryGif').style.display = 'none';
                document.getElementById('continueButton4').style.display = 'block';
            }, 3000);
        }

        // Show the proposal
        function showProposal() {
            document.getElementById('continueButton4').style.display = 'none';
            document.getElementById('clue3').style.display = 'none';
            document.getElementById('proposal').style.display = 'block';
            document.getElementById('pizzaGif').style.display = 'block';
            setTimeout(function() {
                document.getElementById('endMessage').style.display = 'block';
            }, 4000);
        }
    </script>
</body>
</html>
