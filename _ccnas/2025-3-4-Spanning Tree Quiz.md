---
title: 'Spanning Tree Quiz'
date: 2024-10-14 00:00:00
description: Command Line Practice for Spanning Tree.
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

    <div class="question">
        <label for="q0">Setup Portfast:</label>
        <input type="text" id="q0" oninput="checkAnswer('q0', this)">
        <div class="checkbox" id="q0-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q0">?</button>
    </div>

    <div class="question">
        <label for="q1">Setup UpLinkFast:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q1">?</button>
    </div>

    <div class="question">
        <label for="q2">Setup Loop Guard:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q2">?</button>
    </div>

    <div class="question">
        <label for="q3">Setup Root Guard:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q3">?</button>
    </div>

    <div class="question">
        <label for="q4">Setup BPDU Guard:</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q4">?</button>
    </div>

    <div class="question">
        <label for="q5">Setup BPDU Filter:</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q5">?</button>
    </div>

    <div class="question">
        <label for="q6">Setup Backbonefast:</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q6">?</button>
    </div>

    <div class="question">
        <label for="q7">How to view the Root?</label>
        <input type="text" id="q7" oninput="checkAnswer('q7', this)">
        <div class="checkbox" id="q7-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q7">?</button>
    </div>

    <div class="question">
        <label for="q8">Setup the Link Type as Shared:</label>
        <input type="text" id="q8" oninput="checkAnswer('q8', this)">
        <div class="checkbox" id="q8-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q8">?</button>
    </div>

    <div class="question">
        <label for="q9">How to view the Root of Vlan 10?</label>
        <input type="text" id="q9" oninput="checkAnswer('q9', this)">
        <div class="checkbox" id="q9-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q9">?</button>
    </div>

    <div class="question">
        <label for="q10">Set Vlan 1's port priority to 128:</label>
        <input type="text" id="q10" oninput="checkAnswer('q10', this)">
        <div class="checkbox" id="q10-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q10">?</button>
    </div>

    <div class="question">
        <label for="q11">How to show the Spanning Tree mode?</label>
        <input type="text" id="q11" oninput="checkAnswer('q11', this)">
        <div class="checkbox" id="q11-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q11">?</button>
    </div>

    <div class="question">
        <label for="q12">Set the spanning-tree mode as: PVST:</label>
        <input type="text" id="q12" oninput="checkAnswer('q12', this)">
        <div class="checkbox" id="q12-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q12">?</button>
    </div>

    <div class="question">
        <label for="q13">How to view the Spanning-tree roles?</label>
        <input type="text" id="q13" oninput="checkAnswer('q13', this)">
        <div class="checkbox" id="q13-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q13">?</button>
    </div>

    <div class="question">
        <label for="q14">Setup the Link Type as Point to Point:</label>
        <input type="text" id="q14" oninput="checkAnswer('q14', this)">
        <div class="checkbox" id="q14-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q14">?</button>
    </div>

    <div class="question">
        <label for="q15">How to view the Spanning-tree of Vlan 10?</label>
        <input type="text" id="q15" oninput="checkAnswer('q15', this)">
        <div class="checkbox" id="q15-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q15">?</button>
    </div>

    <div class="question">
        <label for="q16">Set the spanning-tree mode as: Rapid PVST:</label>
        <input type="text" id="q16" oninput="checkAnswer('q16', this)">
        <div class="checkbox" id="q16-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q16">?</button>
    </div>

    <div class="question">
        <label for="q17">Set the bridge priority of all vlans to 32768:</label>
        <input type="text" id="q17" oninput="checkAnswer('q17', this)">
        <div class="checkbox" id="q17-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q17">?</button>
    </div>

    <div class="question">
        <label for="q18">How to view the Spanning-tree of Vlan 10 in more detail?</label>
        <input type="text" id="q18" oninput="checkAnswer('q18', this)">
        <div class="checkbox" id="q18-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q18">?</button>
    </div>

    <div class="question">
        <label for="q19">In spanning tree 802.1D, what is the Hello time in seconds?</label>
        <input type="text" id="q19" oninput="checkAnswer('q19', this)">
        <div class="checkbox" id="q19-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q19">?</button>
    </div>

    <div class="question">
        <label for="q20">In spanning tree 802.1D, what is the Forward time in seconds?</label>
        <input type="text" id="q20" oninput="checkAnswer('q20', this)">
        <div class="checkbox" id="q20-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q20">?</button>
    </div>

    <div class="question">
        <label for="q21">In spanning tree 802.1D, what is the Max Age time in seconds?</label>
        <input type="text" id="q21" oninput="checkAnswer('q21', this)">
        <div class="checkbox" id="q21-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q21">?</button>
    </div>

    <div class="question">
        <label for="q22">How to view a summarised view of spanning tree for all Vlans?</label>
        <input type="text" id="q22" oninput="checkAnswer('q22', this)">
        <div class="checkbox" id="q22-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q22">?</button>
    </div>

    <div class="question">
        <label for="q23">How to view a high-level overview of the overall Spanning-tree?</label>
        <input type="text" id="q23" oninput="checkAnswer('q23', this)">
        <div class="checkbox" id="q23-checkbox"></div>
        <button class="hint-btn" tabindex="-1" data-question="q23">?</button>
    </div>

    <script>
        const answers = {
            'q0':  'spanning-tree portfast',
            'q1':  'spanning-tree uplinkfast',
            'q2':  'spanning-tree guard loop',
            'q3':  'spanning-tree rootguard',
            'q4':  'spanning-tree bpduguard enable',
            'q5':  'spanning-tree bpdufilter enable',
            'q6':  'spanning-tree backbonefast',
            'q7':  'show spanning-tree root',
            'q8':  'spanning-tree link-type shared',
            'q9':  'show spanning-tree vlan 10 root',
            'q10': 'spanning-tree vlan 1 port-priority 128',
            'q11': 'show spanning-tree mode',
            'q12': 'spanning-tree mode pvst',
            'q13': 'show spanning-tree',
            'q14': 'spanning-tree link-type point-to-point',
            'q15': 'show spanning-tree vlan 10',
            'q16': 'spanning-tree mode rapid-pvst',
            'q17': 'spanning-tree vlan 1-4094 priority 32768',
            'q18': 'show spanning-tree vlan 10 detail',
            'q19': '2',
            'q20': '15',
            'q21': '20',
            'q22': 'show spanning-tree brief',
            'q23': 'show spanning-tree summary',
        };

        const inputOrder = ['q0','q1','q2','q3','q4','q5','q6','q7','q8','q9','q10','q11','q12','q13','q14','q15','q16','q17','q18','q19','q20','q21','q22','q23'];
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