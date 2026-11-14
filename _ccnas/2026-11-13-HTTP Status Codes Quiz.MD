---
title: 'HTTP Status Codes Quiz'
date: 2026-11-13 00:00:00
description: HTTP status codes for REST APIs and web sessions practice.
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
            min-width: 150px;
            font-family: monospace;
            font-size: 1.6em;
            font-weight: bold;
        }
        .desc {
            flex: 1 1 100%;
            font-size: 1.15em;
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
        .question input[type="text"] {
            padding: 5px;
            font-family: monospace;
            font-size: 0.95em;
        }
        .question input.name { width: 400px; }
        .question input.code { width: 140px; }
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
<div class="Bold">HTTP Status Codes</div>
<p>Type the name of each status code or class.</p>
<div id="typing"></div>

<div class="Bold">Which Code Matches?</div>
<p>Read each description and type the matching status code, or the class for a range of codes (for example 6xx).</p>
<div id="matching"></div>

<div class="shuffle-row">
<button id="shuffle-btn" type="button">Randomise</button>
</div>

<script>
const items = [
    { code: '2xx', name: 'Success', desc: 'Class of codes: the session or API request succeeded.' },
    { code: '3xx', name: 'Redirection', desc: 'Class of codes: the resource moved to another URL.' },
    { code: '4xx', name: 'Client Error', desc: 'Class of codes: the browser or API client sent a bad request or lacks permission.' },
    { code: '5xx', name: 'Server Error', desc: 'Class of codes: the request was valid, but the web server failed to fulfil it.' },
    { code: '200', name: 'OK', desc: 'The request succeeded and the server returned the response.' },
    { code: '201', name: 'Created', desc: 'The request succeeded and a new resource was created, such as after a POST to an API.' },
    { code: '301', name: 'Moved Permanently', desc: 'The resource has permanently moved to a new URL.' },
    { code: '302', name: 'Found', desc: 'The resource has temporarily moved to a different URL.' },
    { code: '400', name: 'Bad Request', desc: 'Malformed syntax or invalid JSON formatting in the request.' },
    { code: '401', name: 'Unauthorized', desc: 'Authentication failed or credentials/API token are missing.' },
    { code: '403', name: 'Forbidden', desc: 'The server understood the credentials, but the user lacks permission to access the resource.' },
    { code: '404', name: 'Not Found', desc: 'The requested URL or API endpoint does not exist on the server.' },
    { code: '500', name: 'Internal Server Error', desc: 'A generic crash or unhandled exception on the server side.' },
    { code: '502', name: 'Bad Gateway', desc: 'A proxy or gateway server received an invalid response from an upstream server.' },
    { code: '503', name: 'Service Unavailable', desc: 'The server is overloaded or down for maintenance.' },
    { code: '504', name: 'Gateway Timeout', desc: 'An upstream server failed to respond in time.' }
];

const typingBox = document.getElementById('typing');
const matchBox = document.getElementById('matching');
const rows = {};
const savedAnswers = {};

function norm(s) {
    return s.toLowerCase().replace(/\s+/g, ' ').trim();
}

function rowTail(id) {
    return '<div class="checkbox" id="' + id + '-checkbox"></div>' +
           '<button class="hint-btn" tabindex="-1" data-question="' + id + '">?</button>';
}

items.forEach(function(it, i) {
    // Section 1: see the code, type the name
    const tid = 't' + i;
    const trow = document.createElement('div');
    trow.className = 'question';
    trow.innerHTML =
        '<label for="' + tid + 'a">' + it.code + '</label>' +
        '<input type="text" class="name" id="' + tid + 'a" autocomplete="off" spellcheck="false">' +
        rowTail(tid);
    typingBox.appendChild(trow);
    rows[tid] = { fields: [ { el: tid + 'a', answers: [it.name] } ] };

    // Section 2: read the description, type the code
    const did = 'd' + i;
    const drow = document.createElement('div');
    drow.className = 'question';
    drow.innerHTML =
        '<div class="desc">' + it.desc + '</div>' +
        '<input type="text" class="code" id="' + did + 'a" placeholder="Code" autocomplete="off" spellcheck="false">' +
        rowTail(did);
    matchBox.appendChild(drow);
    rows[did] = { fields: [ { el: did + 'a', answers: [it.code] } ] };
});

function checkRow(id) {
    const r = rows[id];
    const values = r.fields.map(function(f) { return document.getElementById(f.el).value; });
    const anyTyped = values.some(function(v) { return v.length > 0; });
    const correct = r.fields.every(function(f, i) {
        return f.answers.some(function(a) { return norm(a) === norm(values[i]); });
    });
    const onTrack = r.fields.every(function(f, i) {
        const v = norm(values[i]);
        return v === '' || f.answers.some(function(a) { return norm(a).startsWith(v); });
    });
    const partial = !correct && anyTyped && onTrack;
    const cb = document.getElementById(id + '-checkbox');
    cb.classList.toggle('correct', correct);
    cb.classList.toggle('partial', partial);
    cb.classList.toggle('incorrect', !correct && anyTyped && !partial);
}

function showHint(id) {
    const r = rows[id];
    savedAnswers[id] = r.fields.map(function(f) { return document.getElementById(f.el).value; });
    r.fields.forEach(function(f) { document.getElementById(f.el).value = f.answers[0]; });
}

function clearHint(id) {
    const saved = savedAnswers[id] || [];
    rows[id].fields.forEach(function(f, i) { document.getElementById(f.el).value = saved[i] || ''; });
}

function focusNext(input) {
    const inputs = Array.from(document.querySelectorAll('#typing input, #matching input'));
    const next = inputs[inputs.indexOf(input) + 1];
    if (next) next.focus();
}

function tabComplete(e, id, f) {
    if (e.key !== 'Tab' || e.shiftKey) return;
    e.preventDefault();
    const input = document.getElementById(f.el);
    const typed = input.value;

    if (f.answers.some(function(a) { return norm(a) === norm(typed); })) {
        focusNext(input);
        return;
    }

    if (!typed || typed[typed.length - 1] === ' ') return;
    const answer = f.answers.find(function(a) { return a.toLowerCase().startsWith(typed.toLowerCase()); });
    if (!answer) return;
    const rest = answer.slice(typed.length);
    if (!rest) return;
    const spaceIdx = rest.indexOf(' ');
    input.value = spaceIdx === -1 ? answer : typed + rest.slice(0, spaceIdx + 1);
    checkRow(id);
}

function shuffleRows(container) {
    const list = Array.from(container.querySelectorAll('.question'));
    for (let i = list.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [list[i], list[j]] = [list[j], list[i]];
    }
    list.forEach(function(row) {
        const id = row.querySelector('.hint-btn').getAttribute('data-question');
        rows[id].fields.forEach(function(f) { document.getElementById(f.el).value = ''; });
        document.getElementById(id + '-checkbox').classList.remove('correct', 'partial', 'incorrect');
        delete savedAnswers[id];
        container.appendChild(row);
    });
}

function shuffleAll() {
    shuffleRows(typingBox);
    shuffleRows(matchBox);
}

document.addEventListener('DOMContentLoaded', function() {
    Object.keys(rows).forEach(function(id) {
        rows[id].fields.forEach(function(f) {
            const input = document.getElementById(f.el);
            input.addEventListener('input', function() { checkRow(id); });
            input.addEventListener('keydown', function(e) { tabComplete(e, id, f); });
        });
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

    document.getElementById('shuffle-btn').addEventListener('click', shuffleAll);
    shuffleAll();
});
</script>
</body>