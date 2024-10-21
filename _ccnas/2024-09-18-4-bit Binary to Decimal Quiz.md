---
title: '4-bit and 8-bit Binary to Decimal Quiz'
date: 2024-09-18 00:00:00
description: 4-bit and 8-bit Binary to Decimal.
featured_image: '/images/Photo_Blog/Blank.jpg'
---

<head>
    <style>
        #body_Binary {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
            font-size: 1.25em;
            padding: 20px; /* Added padding */
        }
        .buttons {
            display: flex; /* Use flexbox to center the buttons */
            justify-content: center; /* Center buttons horizontally */
            flex-wrap: wrap; /* Allow wrapping for smaller screens */
        }
        .button {
            margin: 5px;
            font-size: 1em;
            width: 150px;
            height: 2.5em;
            padding: 5px;
            box-sizing: border-box;
            display: flex; /* Center text */
            justify-content: center; /* Center text horizontally */
            align-items: center; /* Center text vertically */
            appearance: none;
            border-radius: 10px;
            text-align-last: center;
            background-color: #f0f0f0;
            color: black;
            border: 2px solid black;
            transition: background-color 0.3s, transform 0.2s; /* Smooth transitions */
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Add shadow */
        }
        .button:hover {
            background-color: #d9f6ff;
            transform: translateY(-2px); /* Lift effect */
            border: 2px solid black;
            color: black;
        }
        #resetButton1, #resetButton2 {
            margin-top: 10px;
            background-color: #ffa21a;
            color: white;
            border: 2px solid #ffa21a;
            transition: background-color 0.3s, transform 0.2s;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        #resetButton1:hover, #resetButton2:hover {
            background-color: #e68900;
            border: 2px solid #e68900;
        }
        @media (max-width: 600px) {
            .button {
                width: 100%; /* Full width on smaller screens */
            }
        }
        .result {
            min-height: 3em; /* Fixed height for results */
            text-align: center; /* Center align results */
            margin: 20px 0; /* Add margin for spacing */
        }
    </style>
</head>
<body>
    <main id="body_Binary">
        <h2> 4-bit Binary to Decimal</h2>
        <h3>What is <span id="binaryNumber1"></span> in decimal?</h3>
        <br>
        <div class="buttons" id="buttons1"></div>
        <br>
        <div id="resetContainer1" style="display: flex; justify-content: center;">
            <button class="button" id="resetButton1">Reset</button>
        </div>
    </main>

    <div class="result" id="resultContainer" role="alert" aria-live="assertive">
        <h2 id="resultDisplay"></h2>
    </div>
    
    <main id="body_Binary">
        <h2> 8-bit Binary to Decimal</h2>
        <h3>What is <span id="binaryNumber2"></span> in decimal?</h3>
        <br>
        <div class="buttons" id="buttons2"></div>
        <br>
        <div id="resetContainer2" style="display: flex; justify-content: center;">
            <button class="button" id="resetButton2">Reset</button>
        </div>
    </main>

    <script>
        function setupBinaryQuiz(binaryDisplayId, buttonsContainerId, resetButtonId, isEightBit = false) {
            let binaryNumber;
            const binaryDisplay = document.getElementById(binaryDisplayId);
            const buttonsContainer = document.getElementById(buttonsContainerId);
            const resetButton = document.getElementById(resetButtonId);
            const resultDisplay = document.getElementById('resultDisplay');

            function generateBinary() {
                if (isEightBit) {
                    // Generate an 8-bit binary number with last 4 bits as 0000
                    const randomPrefix = Math.floor(Math.random() * 16).toString(2).padStart(4, '0'); // 0-15
                    const randomBinary = randomPrefix + '0000'; // Last 4 bits are always 0000
                    binaryDisplay.textContent = formatEightBitBinary(randomBinary);
                    binaryNumber = parseInt(randomBinary, 2); // Convert the full 8-bit binary to decimal
                } else {
                    // Original 4-bit logic remains unchanged
                    const randomBinary = (Math.random() * 16 | 0).toString(2).padStart(4, '0');
                    binaryDisplay.textContent = randomBinary;
                    binaryNumber = parseInt(randomBinary, 2);
                }
                generateButtons();
                resultDisplay.textContent = ''; // Clear result text
            }

            function formatEightBitBinary(binary) {
                return binary.replace(/(.{4})/g, '$1 ').trim(); // Add space after every 4 digits
            }

            function generateButtons() {
                const correctAnswer = binaryNumber;
                const buttonNumbers = new Set([correctAnswer]);

                while (buttonNumbers.size < 4) {
                    const randomNum = Math.floor(Math.random() * (isEightBit ? 256 : 16));
                    buttonNumbers.add(randomNum);
                }

                const buttonArray = Array.from(buttonNumbers);
                buttonsContainer.innerHTML = '';
                buttonArray.sort(() => Math.random() - 0.5).forEach(num => {
                    const button = document.createElement('button');
                    button.className = 'button';
                    button.textContent = num;
                    button.onclick = () => checkAnswer(num);
                    buttonsContainer.appendChild(button);
                });
            }

            function checkAnswer(selectedNumber) {
                if (selectedNumber === binaryNumber) {
                    resultDisplay.textContent = 'Correct!';
                    setTimeout(generateBinary, 1000);
                } else {
                    resultDisplay.textContent = 'Incorrect. Try again!';
                }
            }

            resetButton.onclick = generateBinary;
            generateBinary();
        }

        setupBinaryQuiz('binaryNumber1', 'buttons1', 'resetButton1'); // 4-bit quiz
        setupBinaryQuiz('binaryNumber2', 'buttons2', 'resetButton2', true); // 8-bit quiz
    </script>
</body>
