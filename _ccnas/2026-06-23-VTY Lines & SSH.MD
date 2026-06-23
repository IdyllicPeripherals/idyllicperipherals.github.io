---
title: 'VTY Lines & SSH Quiz'
date: 2026-06-23 00:00:00
description: Cisco VTY Lines, Passwords, and SSH Commands Practise.
featured_image: '/images/Photo_Blog/Blank.jpg'
---
<head>
    <style>
        .question {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 6px;
        }
        .Bold {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
            font-size: 2em;
        }
        .question label {
            margin-right: 10px;
            min-width: 200px;
        }
        .checkbox {
            width: 20px;
            height: 20px;
            border: 2px solid #000;
            margin-left: 10px;
            flex-shrink: 0;
        }
        .correct { background-color: green; }
        .incorrect { background-color: red; }
        input[type="text"] {
            padding: 5px;
            width: 400px;
            font-family: monospace;
            font-size: 0.95em;
        }
        .hint-btn {
            margin-left: 10px;
            font-size: 18px;
            background-color: #f0f0f0;
            border: 1px solid #ccc;
            padding: 5px 10px;
            cursor: pointer;
            flex-shrink: 0;
        }
        .hint-btn:active { background-color: #e0e0e0; }
    </style>
</head>

<body>
    <div class="Bold">VTY Lines & SSH</div>

    <div class="question">
        <label for="q0">Access all VTY lines:</label>
        <input type="text" id="q0" oninput="checkAnswer('q0', this)">
        <div class="checkbox" id="q0-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q0">?</button>
    </div>

    <div class="question">
        <label for="q1">Generate an RSA key pair:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q1">?</button>
    </div>

    <div class="question">
        <label for="q2">Configure local line authentication:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q2">?</button>
    </div>

    <div class="question">
        <label for="q3">Limit SSH connections to SSHv2 only:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q3">?</button>
    </div>

    <div class="question">
        <label for="q4">Configure a line password of Password1:</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q4">?</button>
    </div>

    <div class="question">
        <label for="q5">Apply ACL 10 for connections to the VTY lines:</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q5">?</button>
    </div>

    <div class="question">
        <label for="q6">Configure the exec timeout of 10 minutes 10 seconds:</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q6">?</button>
    </div>

    <div class="question">
        <label for="q7">Show information about the current SSH configuration:</label>
        <input type="text" id="q7" oninput="checkAnswer('q7', this)">
        <div class="checkbox" id="q7-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q7">?</button>
    </div>

    <div class="question">
        <label for="q8">Show information about the IOS version of the device:</label>
        <input type="text" id="q8" oninput="checkAnswer('q8', this)">
        <div class="checkbox" id="q8-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q8">?</button>
    </div>

    <div class="question">
        <label for="q9">Configure the switch's default gateway to 192.168.1.1:</label>
        <input type="text" id="q9" oninput="checkAnswer('q9', this)">
        <div class="checkbox" id="q9-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q9">?</button>
    </div>

    <div class="question">
        <label for="q10">Configure the router to authenticate using the configured line password:</label>
        <input type="text" id="q10" oninput="checkAnswer('q10', this)">
        <div class="checkbox" id="q10-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q10">?</button>
    </div>

    <div class="question">
        <label for="q11">Configure all protocols so they can be used to connect via the VTY lines:</label>
        <input type="text" id="q11" oninput="checkAnswer('q11', this)">
        <div class="checkbox" id="q11-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q11">?</button>
    </div>

    <div class="question">
        <label for="q12">Configure no protocols so they can not be used to connect via the VTY lines:</label>
        <input type="text" id="q12" oninput="checkAnswer('q12', this)">
        <div class="checkbox" id="q12-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q12">?</button>
    </div>

    <div class="question">
        <label for="q13">Configure the protocol that allows SSH to be used to connect via the VTY lines:</label>
        <input type="text" id="q13" oninput="checkAnswer('q13', this)">
        <div class="checkbox" id="q13-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q13">?</button>
    </div>

    <script>
        const answers = {
            'q0':  'line vty 0 15',
            'q1':  'crypto key generate rsa',
            'q2':  'login local',
            'q3':  'ip ssh version 2',
            'q4':  'password Password1',
            'q5':  'access-class 10 in',
            'q6':  'exec-timeout 10 10',
            'q7':  'show ip ssh',
            'q8':  'show version',
            'q9':  'ip default-gateway 192.168.1.1',
            'q10': 'login',
            'q11': 'transport input all',
            'q12': 'transport input none',
            'q13': 'transport input SSH',
        };

        const inputOrder = ['q0','q1','q2','q3','q4','q5','q6','q7','q8','q9','q10','q11','q12','q13'];
        const savedAnswers = {};

        function checkAnswer(questionId, inputElement) {
            const checkbox = document.getElementById(questionId + '-checkbox');
            const correct = inputElement.value.trim().toLowerCase() === answers[questionId].toLowerCase();
            checkbox.classList.toggle('correct', correct);
            checkbox.classList.toggle('incorrect', !correct && inputElement.value.length > 0);
        }

        function showHint(questionId) {
            savedAnswers[questionId] = document.getElementById(questionId).value;
            document.getElementById(questionId).value = answers[questionId];
        }

        function clearHint(questionId) {
            document.getElementById(questionId).value = savedAnswers[questionId] || '';
        }

        function tabComplete(e, questionId) {
            if (e.key !== 'Tab') return;
            e.preventDefault();
            const input = document.getElementById(questionId);
            const typed = input.value;
            const answer = answers[questionId];

            if (typed.trim().toLowerCase() === answer.toLowerCase()) {
                const next = inputOrder[inputOrder.indexOf(questionId) + 1];
                if (next) document.getElementById(next).focus();
                return;
            }

            if (!typed || typed[typed.length - 1] === ' ') return;
            if (!answer.toLowerCase().startsWith(typed.toLowerCase())) return;
            const rest = answer.slice(typed.length);
            if (!rest) return;
            const spaceIdx = rest.indexOf(' ');
            input.value = spaceIdx === -1 ? answer : typed + rest.slice(0, spaceIdx + 1);
            checkAnswer(questionId, input);
        }

        document.addEventListener('DOMContentLoaded', function() {
            Object.keys(answers).forEach(function(id) {
                const input = document.getElementById(id);
                if (input) input.addEventListener('keydown', function(e) { tabComplete(e, id); });
            });

            document.querySelectorAll('.hint-btn').forEach(function(btn) {
                const id = btn.getAttribute('data-question');
                btn.addEventListener('pointerdown', function(e) {
                    btn.setPointerCapture(e.pointerId);
                    showHint(id);
                });
                btn.addEventListener('pointerup', function() { clearHint(id); });
                btn.addEventListener('pointercancel', function() { clearHint(id); });
            });
        });
    </script>
</body>