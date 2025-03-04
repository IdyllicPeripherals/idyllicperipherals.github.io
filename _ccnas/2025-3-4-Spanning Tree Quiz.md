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
            width: 300px;
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
    </style>
</head>
<body>
    <div class="question">
        <label for="q1">Set the spanning-tree mode as: PVST:</label>
        <input type="text" id="q1" oninput="checkAnswer('q1', 'spanning-tree mode pvst', this)">
        <div class="checkbox" id="q1-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q1', 'spanning-tree mode pvst')" onmouseup="clearHint('q1')">?</button>
    </div>
    <div class="question">
        <label for="q2">Set the spanning-tree mode as: Rapid PVST:</label>
        <input type="text" id="q2" oninput="checkAnswer('q2', 'spanning-tree mode rapid-pvst', this)">
        <div class="checkbox" id="q2-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q2', 'spanning-tree mode rapid-pvst')" onmouseup="clearHint('q2')">?</button>
    </div>

    <div class="question">
        <label for="q3">Set the bridge priority of all vlans to 32768:</label>
        <input type="text" id="q3" oninput="checkAnswer('q3', 'spanning-tree vlan 1-4094 priority 32768', this)">
        <div class="checkbox" id="q3-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q3', 'spanning-tree vlan 1-4094 priority 32768')" onmouseup="clearHint('q3')">?</button>
    </div>

    <div class="question">
        <label for="q4">In spanning tree 802.1D, what is the hello time in seconds?</label>
        <input type="text" id="q4" oninput="checkAnswer('q4', '2', this)">
        <div class="checkbox" id="q4-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q4', '2')" onmouseup="clearHint('q4')">?</button>
    </div>

    <div class="question">
        <label for="q5">In spanning tree 802.1D, what is the forward time in seconds?</label>
        <input type="text" id="q5" oninput="checkAnswer('q5', '15', this)">
        <div class="checkbox" id="q5-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q5', '15')" onmouseup="clearHint('q5')">?</button>
    </div>

    <div class="question">
        <label for="q6">In spanning tree 802.1D, what is the max age time in seconds?</label>
        <input type="text" id="q6" oninput="checkAnswer('q6', '20', this)">
        <div class="checkbox" id="q6-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q6', '20')" onmouseup="clearHint('q6')">?</button>
    </div>

    <div class="question">
        <label for="q7">Setup Portfast:</label>
        <input type="text" id="q7" oninput="checkAnswer('q7', 'spanning-tree portfast', this)">
        <div class="checkbox" id="q7-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q7', 'spanning-tree portfast')" onmouseup="clearHint('q7')">?</button>
    </div>

    <div class="question">
        <label for="q8">Setup Backbonefast:</label>
        <input type="text" id="q8" oninput="checkAnswer('q8', 'spanning-tree backbonefast', this)">
        <div class="checkbox" id="q8-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q8', 'spanning-tree backbonefast')" onmouseup="clearHint('q8')">?</button>
    </div>

    <div class="question">
        <label for="q9">Setup UpLinkFast:</label>
        <input type="text" id="q9" oninput="checkAnswer('q9', 'spanning-tree uplinkfast', this)">
        <div class="checkbox" id="q9-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q9', 'spanning-tree uplinkfast')" onmouseup="clearHint('q9')">?</button>
    </div>

    <div class="question">
        <label for="q10">Set Vlan 1’s port priority to 128:</label>
        <input type="text" id="q10" oninput="checkAnswer('q10', 'spanning-tree vlan 1 port-priority 128', this)">
        <div class="checkbox" id="q10-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q10', 'spanning-tree vlan 1 port-priority 128')" onmouseup="clearHint('q10')">?</button>
    </div>

    <div class="question">
        <label for="q11">Setup Loop Guard:</label>
        <input type="text" id="q11" oninput="checkAnswer('q11', 'spanning-tree guard loop', this)">
        <div class="checkbox" id="q11-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q11', 'spanning-tree guard loop')" onmouseup="clearHint('q11')">?</button>
    </div>

    <div class="question">
        <label for="q12">Setup Root Guard:</label>
        <input type="text" id="q12" oninput="checkAnswer('q12', 'spanning-tree loop guard', this)">
        <div class="checkbox" id="q12-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q12', 'spanning-tree loop guard')" onmouseup="clearHint('q12')">?</button>
    </div>

    <div class="question">
        <label for="q13">Setup the Link Type as Point to Point:</label>
        <input type="text" id="q13" oninput="checkAnswer('q13', 'spanning-tree link-type point-to-point', this)">
        <div class="checkbox" id="q13-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q13', 'spanning-tree link-type point-to-point')" onmouseup="clearHint('q13')">?</button>
    </div>

    <div class="question">
        <label for="q14">Setup the Link Type as Shared:</label>
        <input type="text" id="q14" oninput="checkAnswer('q14', 'spanning-tree link-type shared', this)">
        <div class="checkbox" id="q14-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q14', 'spanning-tree link-type shared')" onmouseup="clearHint('q14')">?</button>
    </div>

    <div class="question">
        <label for="q15">Setup BPDU Guard:</label>
        <input type="text" id="q15" oninput="checkAnswer('q15', 'spanning-tree bpduguard enable', this)">
        <div class="checkbox" id="q15-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q15', 'spanning-tree bpduguard enable')" onmouseup="clearHint('q15')">?</button>
    </div>

    <div class="question">
        <label for="q16">Setup BPDU Filter:</label>
        <input type="text" id="q16" oninput="checkAnswer('q16', 'spanning-tree bpdufilter enable', this)">
        <div class="checkbox" id="q16-checkbox"></div>
        <button class="hint-btn" onmousedown="showHint('q16', 'spanning-tree bpdufilter enable')" onmouseup="clearHint('q16')">?</button>
    </div>

    <script>
        let savedAnswers = {};

        function checkAnswer(questionId, correctAnswer, inputElement) {
            const checkbox = document.getElementById(questionId + '-checkbox');
            const answer = inputElement.value.trim().toLowerCase();
            const correct = correctAnswer.toLowerCase();

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


