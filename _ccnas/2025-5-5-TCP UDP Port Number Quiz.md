---
title: 'TCP/UDP Port Number Quiz'
date: 2025-5-5 00:00:00
description: TCP and UDP Ports Practise.
featured_image: '/images/Photo_Blog/Blank.jpg'
---
<head>
    <style>
        .question {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        .Bold {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            font-size: 2em;
        }
        .question label {
            margin-right: 10px;
        }
        .checkbox {
            width: 20px;
            height: 20px;
            border: 2px solid #000;
            margin-left: 10px;
        }
        .correct {
            background-color: green;
        }
        .incorrect {
            background-color: red;
        }
        input[type="text"] {
            padding: 5px;
            width: 100px;
        }
        .hint-btn {
            margin-left: 10px;
            font-size: 18px;
            background-color: #f0f0f0;
            border: 1px solid #ccc;
            padding: 5px 10px;
            cursor: pointer;
        }
        .hint-btn:active {
            background-color: #e0e0e0;
        }
        h1, h2 {
            text-align: center;
            font-size: 2em;
            margin-bottom: 20px;
        }
        h2 {
            font-size: 1.5em;
            margin-top: 30px;
        }
    </style>
</head>

<body>
    <!-- TCP Port Numbers Heading -->
    <div class="Bold">TCP Port Numbers</div>

    <div class="question">
        <label for="q1">FTP – File Transfer Protocol:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', '20', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q1', '20')" onmouseup="clearHint('q1')">?</button>
    </div>
    <div class="question">
        <label for="q2">FTP Control – File Transfer Protocol Control:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', '21', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q2', '21')" onmouseup="clearHint('q2')">?</button>
    </div>
    <div class="question">
        <label for="q3">SSH – Secure Shell:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', '22', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q3', '22')" onmouseup="clearHint('q3')">?</button>
    </div>
    <div class="question">
        <label for="q4">Telnet – Remote Command Line Access:</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', '23', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q4', '23')" onmouseup="clearHint('q4')">?</button>
    </div>
    <div class="question">
        <label for="q5">SMTP – Simple Mail Transfer Protocol:</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', '25', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q5', '25')" onmouseup="clearHint('q5')">?</button>
    </div>
    <div class="question">
        <label for="q6">HTTP – Hypertext Transfer Protocol:</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', '80', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q6', '80')" onmouseup="clearHint('q6')">?</button>
    </div>
    <div class="question">
        <label for="q7">POP3 – Post Office Protocol 3:</label>
        <input type="text" id="q7" oninput="checkAnswer('q7', '110', this)">
        <div class="checkbox" id="q7-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q7', '110')" onmouseup="clearHint('q7')">?</button>
    </div>
    <div class="question">
        <label for="q8">HTTPS – Hypertext Transfer Protocol Secure:</label>
        <input type="text" id="q8" oninput="checkAnswer('q8', '443', this)">
        <div class="checkbox" id="q8-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q8', '443')" onmouseup="clearHint('q8')">?</button>
    </div>

    <!-- UDP Port Numbers Heading -->
    <div class="Bold">UDP Port Numbers</div>

    <div class="question">
        <label for="q9">DHCP Server – Dynamic Host Configuration Protocol:</label>
        <input type="text" id="q9" oninput="checkAnswer('q9', '67', this)">
        <div class="checkbox" id="q9-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q9', '67')" onmouseup="clearHint('q9')">?</button>
    </div>
    <div class="question">
        <label for="q10">DHCP Client – Dynamic Host Configuration Protocol:</label>
        <input type="text" id="q10" oninput="checkAnswer('q10', '68', this)">
        <div class="checkbox" id="q10-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q10', '68')" onmouseup="clearHint('q10')">?</button>
    </div>
    <div class="question">
        <label for="q11">TFTP – Trivial File Transfer Protocol:</label>
        <input type="text" id="q11" oninput="checkAnswer('q11', '69', this)">
        <div class="checkbox" id="q11-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q11', '69')" onmouseup="clearHint('q11')">?</button>
    </div>
    <div class="question">
        <label for="q12">SNMP – Simple Network Management Protocol:</label>
        <input type="text" id="q12" oninput="checkAnswer('q12', '161', this)">
        <div class="checkbox" id="q12-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q12', '161')" onmouseup="clearHint('q12')">?</button>
    </div>
    <div class="question">
        <label for="q13">SNMP Manager – Simple Network Management Protocol:</label>
        <input type="text" id="q13" oninput="checkAnswer('q13', '162', this)">
        <div class="checkbox" id="q13-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q13', '162')" onmouseup="clearHint('q13')">?</button>
    </div>
    <div class="question">
        <label for="q14">Syslog – System Logging Protocol:</label>
        <input type="text" id="q14" oninput="checkAnswer('q14', '514', this)">
        <div class="checkbox" id="q14-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q14', '514')" onmouseup="clearHint('q14')">?</button>
    </div>

    <br>
    <!-- TCP & UDP Port Numbers Heading -->
    <div class="Bold">TCP & UDP Port Numbers</div>

    <div class="question">
        <label for="q15">DNS – Domain Name System:</label>
        <input type="text" id="q15" oninput="checkAnswer('q15', '53', this)">
        <div class="checkbox" id="q15-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q15', '53')" onmouseup="clearHint('q15')">?</button>
    </div>

    <script>
        let savedAnswers = {};

        function checkAnswer(questionId, correctAnswer, inputElement) {
            const checkbox = document.getElementById(questionId + '-checkbox');
            const answer = inputElement.value.trim();
            const correct = correctAnswer;

            if (answer === correct) {
                checkbox.classList.add('correct');
                checkbox.classList.remove('incorrect');
            } else {
                checkbox.classList.remove('correct');
                checkbox.classList.add('incorrect');
            }
        }

        function showHint(questionId, hint) {
            const inputElement = document.getElementById(questionId);
            savedAnswers[questionId] = inputElement.value;
            inputElement.value = hint;
        }

        function clearHint(questionId) {
            const inputElement = document.getElementById(questionId);
            inputElement.value = savedAnswers[questionId] || '';
        }
    </script>
</body>
