---
title: 'DHCP Snooping Quiz'
date: 2026-6-6 00:00:00
description: Cisco DHCP Snooping Commands Practise.
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
    <div class="Bold">DHCP Snooping</div>

    <div class="question">
        <label for="q0">Configure a DHCP snooping trusted port:</label>
        <input type="text" id="q0" oninput="checkAnswer('q0', this)">
        <div class="checkbox" id="q0-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q0">?</button>
    </div>

    <div class="question">
        <label for="q2">Enable DHCP Snooping on VLAN 1:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q2">?</button>
    </div>

    <div class="question">
        <label for="q3">Enable DHCP Snooping on the switch:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q3">?</button>
    </div>

        <div class="question">
        <label for="q6">Show the DHCP snooping binding table:</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q6">?</button>
    </div>

    <div class="question">
        <label for="q4">Enable errdisable recovery for DHCP rate limiting violations:</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q4">?</button>
    </div>

    <div class="question">
        <label for="q5">Limit the rate that DHCP messages are allowed on a DHCP snooping enabled interface to 100 mbps:</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q5">?</button>
    </div>

        <div class="question">
        <label for="q1">Configure the DHCP snooping-enabled switch to not add option 82 to DHCP messages:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q1">?</button>
    </div>



    <script>
        const answers = {
            'q0': 'ip dhcp snooping trust',
            'q1': 'no ip dhcp snooping information option',
            'q2': 'ip dhcp snooping vlan 1',
            'q3': 'ip dhcp snooping',
            'q4': 'errdisable recovery cause dhcp-rate-limit',
            'q5': 'ip dhcp snooping limit 100',
            'q6': 'show ip dhcp snooping binding',
        };

        const inputOrder = ['q0','q1','q2','q3','q4','q5','q6'];
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