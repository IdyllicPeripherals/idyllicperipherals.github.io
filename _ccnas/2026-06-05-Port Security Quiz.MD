---
title: 'Port Security Quiz'
date: 2025-5-5 00:00:00
description: Cisco Port Security Commands Practise.
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
        .part-label {
            font-size: 0.85em;
            color: #555;
            margin-right: 4px;
            flex-shrink: 0;
        }
    </style>
</head>

<body>
    <div class="Bold">Port Security</div>

    <div class="question">
        <label for="q0">Manually configure the secure MAC address of 1111 on the interface:</label>
        <input type="text" id="q0" oninput="checkAnswer('q0', this)">
        <div class="checkbox" id="q0-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q0">?</button>
    </div>

    <div class="question">
        <label for="q1">Enable sticky secure MAC address learning:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q1">?</button>
    </div>

    <div class="question">
        <label for="q2">Configure the port security protect violation mode:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q2">?</button>
    </div>

    <div class="question">
        <label for="q3">Configure the port security restrict violation mode:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q3">?</button>
    </div>

    <div class="question">
        <label for="q4">Configure the port security shutdown violation mode:</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q4">?</button>
    </div>

    <div class="question">
        <label for="q5">Configure the port security aging time to 7 minutes:</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q5">?</button>
    </div>

    <div class="question">
        <label for="q6">Configure the port security aging type to absolute:</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q6">?</button>
    </div>

    <div class="question">
        <label for="q7">Configure the port security aging type to inactivity:</label>
        <input type="text" id="q7" oninput="checkAnswer('q7', this)">
        <div class="checkbox" id="q7-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q7">?</button>
    </div>

    <div class="question">
        <label for="q8">Enable aging of static secure MAC addresses:</label>
        <input type="text" id="q8" oninput="checkAnswer('q8', this)">
        <div class="checkbox" id="q8-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q8">?</button>
    </div>

    <div class="question">
        <label for="q9">Enable errdisable recovery for port security violations:</label>
        <input type="text" id="q9" oninput="checkAnswer('q9', this)">
        <div class="checkbox" id="q9-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q9">?</button>
    </div>

    <div class="question">
        <label for="q10">Configure the errdisable recovery interval to 30 seconds:</label>
        <input type="text" id="q10" oninput="checkAnswer('q10', this)">
        <div class="checkbox" id="q10-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q10">?</button>
    </div>

    <div class="question">
        <label for="q11">Show all secure MAC addresses on the switch:</label>
        <input type="text" id="q11" oninput="checkAnswer('q11', this)">
        <div class="checkbox" id="q11-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q11">?</button>
    </div>

    <div class="question">
        <label for="q12">Show a summary of port security-enabled switchports:</label>
        <input type="text" id="q12" oninput="checkAnswer('q12', this)">
        <div class="checkbox" id="q12-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q12">?</button>
    </div>

    <div class="question">
        <label for="q13">Show port security information for the individual switchport fa 0/1:</label>
        <input type="text" id="q13" oninput="checkAnswer('q13', this)">
        <div class="checkbox" id="q13-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q13">?</button>
    </div>

    <div class="question">
        <label for="q14">Show a summary of errdisable recovery information:</label>
        <input type="text" id="q14" oninput="checkAnswer('q14', this)">
        <div class="checkbox" id="q14-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q14">?</button>
    </div>

    <!-- Q15 - two-part -->
    <div class="question" style="flex-wrap: nowrap;">
        <label style="white-space: nowrap;">Manually re-enable an interface disabled by port security:</label>
        <div style="display: flex; flex-direction: column; gap: 6px;">
            <div style="display: flex; align-items: center; gap: 6px;">
                <span class="part-label">Step 1:</span>
                <input type="text" id="q15a" style="width: 400px;" oninput="checkAnswerMulti()">
                <div class="checkbox" id="q15a-checkbox"></div>
                <button class="hint-btn" tabindex="-1" data-question="q15a">?</button>
            </div>
            <div style="display: flex; align-items: center; gap: 6px;">
                <span class="part-label">Step 2:</span>
                <input type="text" id="q15b" style="width: 400px;" oninput="checkAnswerMulti()">
                <div class="checkbox" id="q15b-checkbox"></div>
                <button class="hint-btn" tabindex="-1" data-question="q15b">?</button>
            </div>
        </div>
    </div>

    <script>
        const answers = {
            'q0':   'switchport port-security mac-address 1111',
            'q1':   'switchport port-security mac-address sticky',
            'q2':   'switchport port-security violation protect',
            'q3':   'switchport port-security violation restrict',
            'q4':   'switchport port-security violation shutdown',
            'q5':   'switchport port-security aging time 7',
            'q6':   'switchport port-security aging type absolute',
            'q7':   'switchport port-security aging type inactivity',
            'q8':   'switchport port-security aging static',
            'q9':   'errdisable recovery cause psecure-violation',
            'q10':  'errdisable recovery interval 30',
            'q11':  'show mac address-table secure',
            'q12':  'show port-security',
            'q13':  'show port-security interface fa 0/1',
            'q14':  'show errdisable recovery',
            'q15a': 'shutdown',
            'q15b': 'no shutdown',
        };

        const inputOrder = ['q0','q1','q2','q3','q4','q5','q6','q7','q8','q9','q10','q11','q12','q13','q14','q15a','q15b'];
        const savedAnswers = {};

        // --- Answer checking ---

        function checkAnswer(questionId, inputElement) {
            const checkbox = document.getElementById(questionId + '-checkbox');
            const correct = inputElement.value.trim().toLowerCase() === answers[questionId].toLowerCase();
            checkbox.classList.toggle('correct', correct);
            checkbox.classList.toggle('incorrect', !correct && inputElement.value.length > 0);
            if (!correct) checkbox.classList.remove('incorrect', !inputElement.value.length);
        }

        function checkAnswerMulti() {
            const ids = ['q15a', 'q15b'];
            ids.forEach(function(id) {
                const input = document.getElementById(id);
                const box = document.getElementById(id + '-checkbox');
                const correct = input.value.trim().toLowerCase() === answers[id].toLowerCase();
                box.classList.toggle('correct', correct);
                box.classList.toggle('incorrect', !correct && input.value.length > 0);
            });
        }

        // --- Hint buttons ---

        function showHint(questionId) {
            savedAnswers[questionId] = document.getElementById(questionId).value;
            document.getElementById(questionId).value = answers[questionId];
        }

        function clearHint(questionId) {
            document.getElementById(questionId).value = savedAnswers[questionId] || '';
        }

        // --- Tab autocomplete + navigation ---

        function tabComplete(e, questionId) {
            if (e.key !== 'Tab') return;
            e.preventDefault();
            const input = document.getElementById(questionId);
            const typed = input.value;
            const answer = answers[questionId];

            // Navigate to next box if answer is complete
            if (typed.trim().toLowerCase() === answer.toLowerCase()) {
                const next = inputOrder[inputOrder.indexOf(questionId) + 1];
                if (next) document.getElementById(next).focus();
                return;
            }

            // Autocomplete current word only if typing matches and a word has been started
            if (!typed || typed[typed.length - 1] === ' ') return;
            if (!answer.toLowerCase().startsWith(typed.toLowerCase())) return;
            const rest = answer.slice(typed.length);
            if (!rest) return;
            const spaceIdx = rest.indexOf(' ');
            input.value = spaceIdx === -1 ? answer : typed + rest.slice(0, spaceIdx + 1);
            questionId === 'q15a' || questionId === 'q15b' ? checkAnswerMulti() : checkAnswer(questionId, input);
        }

        // --- Initialise event listeners ---

        document.addEventListener('DOMContentLoaded', function() {
            // Tab behaviour on inputs
            Object.keys(answers).forEach(function(id) {
                const input = document.getElementById(id);
                if (input) input.addEventListener('keydown', function(e) { tabComplete(e, id); });
            });

            // Hint button hold-to-reveal
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