---
title: 'Spanning Tree Port States Quiz'
date: 2026-11-10 00:00:00
description: Spanning Tree Port States Practice.
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
            min-width: 260px;
            font-family: monospace;
            font-size: 1.6em;
            font-weight: bold;
        }
        .checkbox {
            width: 20px;
            height: 20px;
            border: 2px solid #000;
            margin-left: 10px;
            flex-shrink: 0;
        }
        .correct { background-color: green; }
        .partial { background-color: #ffbf00; }
        .incorrect { background-color: red; }
        input[type="text"] {
            padding: 5px;
            width: 500px;
            font-family: monospace;
            font-size: 0.95em;
        }
        input.count {
            padding: 5px;
            width: 60px;
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
        .shuffle-row { text-align: center; margin-top: 30px; }
        .shuffle-row button { padding: 12px 32px; }
    </style>
</head>

<body>
    <div class="Bold">Spanning Tree Port States</div>
    <p>How many port states are there? List them in order and separated by spaces.</p>

    <div id="questions">

    <div class="question">
        <label for="c0">Classic STP (802.1D)</label>
        <input type="text" class="count" id="c0" placeholder="#" inputmode="numeric" oninput="checkAnswer('q0')">
        <input type="text" id="s0" placeholder="List the states" oninput="checkAnswer('q0')">
        <div class="checkbox" id="q0-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q0">?</button>
    </div>

    <div class="question">
        <label for="c1">PVST+</label>
        <input type="text" class="count" id="c1" placeholder="#" inputmode="numeric" oninput="checkAnswer('q1')">
        <input type="text" id="s1" placeholder="List the states" oninput="checkAnswer('q1')">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q1">?</button>
    </div>

    <div class="question">
        <label for="c2">Rapid STP (802.1w)</label>
        <input type="text" class="count" id="c2" placeholder="#" inputmode="numeric" oninput="checkAnswer('q2')">
        <input type="text" id="s2" placeholder="List the states" oninput="checkAnswer('q2')">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q2">?</button>
    </div>

    <div class="question">
        <label for="c3">Rapid PVST+</label>
        <input type="text" class="count" id="c3" placeholder="#" inputmode="numeric" oninput="checkAnswer('q3')">
        <input type="text" id="s3" placeholder="List the states" oninput="checkAnswer('q3')">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q3">?</button>
    </div>

    <div class="question">
        <label for="c4">MSTP (802.1s)</label>
        <input type="text" class="count" id="c4" placeholder="#" inputmode="numeric" oninput="checkAnswer('q4')">
        <input type="text" id="s4" placeholder="List the states" oninput="checkAnswer('q4')">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q4">?</button>
    </div>
    </div>

    <div class="shuffle-row">
        <button id="shuffle-btn" type="button">Randomise</button>
    </div>

    <script>
        const answers = {
            'q0': { count: '5', states: 'Disabled Blocking Listening Learning Forwarding' },
            'q1': { count: '5', states: 'Disabled Blocking Listening Learning Forwarding' },
            'q2': { count: '3', states: 'Discarding Learning Forwarding' },
            'q3': { count: '3', states: 'Discarding Learning Forwarding' },
            'q4': { count: '3', states: 'Discarding Learning Forwarding' },
        };

        const savedAnswers = {};

        function currentOrder() {
            return Array.from(document.querySelectorAll('#questions .question')).map(function(q) {
                return q.querySelector('.hint-btn').getAttribute('data-question');
            });
        }

        function shuffleQuestions() {
            const container = document.getElementById('questions');
            const items = Array.from(container.querySelectorAll('.question'));
            for (let i = items.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [items[i], items[j]] = [items[j], items[i]];
            }
            items.forEach(function(item) {
                const id = item.querySelector('.hint-btn').getAttribute('data-question');
                const n = id.slice(1);
                document.getElementById('c' + n).value = '';
                document.getElementById('s' + n).value = '';
                const cb = document.getElementById(id + '-checkbox');
                cb.classList.remove('correct', 'partial', 'incorrect');
                delete savedAnswers[id];
                container.appendChild(item);
            });
        }

        function idNum(questionId) { return questionId.slice(1); }

        function normalize(list) {
            return list.split(/[\s,]+/)
                .map(function(x) { return x.trim().toLowerCase(); })
                .filter(Boolean)
                .sort()
                .join(',');
        }

        function isCorrect(questionId) {
            const n = idNum(questionId);
            const count = document.getElementById('c' + n).value.trim();
            const states = document.getElementById('s' + n).value;
            const a = answers[questionId];
            return count === a.count && normalize(states) === normalize(a.states);
        }

        // Returns true if what's typed could still become the correct answer
        function stillOnTrack(questionId) {
            const n = idNum(questionId);
            const a = answers[questionId];
            const count = document.getElementById('c' + n).value.trim();
            const states = document.getElementById('s' + n).value.toLowerCase();

            if (count && !a.count.startsWith(count)) return false;

            const expected = a.states.toLowerCase().split(/[\s,]+/).filter(Boolean);
            const parts = states.split(/[\s,]+/).filter(Boolean);
            const endsWithSep = /[\s,]$/.test(states);
            const fragment = endsWithSep ? '' : (parts.pop() || '');
            const done = parts;
            const remaining = expected.slice();

            for (let i = 0; i < done.length; i++) {
                const idx = remaining.indexOf(done[i]);
                if (idx === -1) return false;
                remaining.splice(idx, 1);
            }
            if (fragment) {
                return remaining.some(function(x) { return x.startsWith(fragment); });
            }
            return true;
        }

        function checkAnswer(questionId) {
            const n = idNum(questionId);
            const checkbox = document.getElementById(questionId + '-checkbox');
            const correct = isCorrect(questionId);
            const anyTyped = document.getElementById('c' + n).value.length > 0 ||
                             document.getElementById('s' + n).value.length > 0;
            const partial = !correct && anyTyped && stillOnTrack(questionId);
            checkbox.classList.toggle('correct', correct);
            checkbox.classList.toggle('partial', partial);
            checkbox.classList.toggle('incorrect', !correct && anyTyped && !partial);
        }

        function showHint(questionId) {
            const n = idNum(questionId);
            savedAnswers[questionId] = {
                count: document.getElementById('c' + n).value,
                states: document.getElementById('s' + n).value
            };
            document.getElementById('c' + n).value = answers[questionId].count;
            document.getElementById('s' + n).value = answers[questionId].states;
        }

        function clearHint(questionId) {
            const n = idNum(questionId);
            const saved = savedAnswers[questionId] || { count: '', states: '' };
            document.getElementById('c' + n).value = saved.count;
            document.getElementById('s' + n).value = saved.states;
        }

        function tabComplete(e, questionId) {
            if (e.key !== 'Tab' || e.shiftKey) return;
            e.preventDefault();
            const n = idNum(questionId);
            const input = document.getElementById('s' + n);
            const typed = input.value;
            const answer = answers[questionId].states;

            if (isCorrect(questionId)) {
                const order = currentOrder();
                const next = order[order.indexOf(questionId) + 1];
                if (next) document.getElementById('c' + idNum(next)).focus();
                return;
            }

            if (!typed || typed[typed.length - 1] === ' ') return;
            if (!answer.toLowerCase().startsWith(typed.toLowerCase())) return;
            const rest = answer.slice(typed.length);
            if (!rest) return;
            const spaceIdx = rest.indexOf(' ');
            input.value = spaceIdx === -1 ? answer : typed + rest.slice(0, spaceIdx + 1);
            checkAnswer(questionId);
        }

        document.addEventListener('DOMContentLoaded', function() {
            document.getElementById('shuffle-btn').addEventListener('click', shuffleQuestions);
            shuffleQuestions();

            Object.keys(answers).forEach(function(id) {
                const input = document.getElementById('s' + idNum(id));
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