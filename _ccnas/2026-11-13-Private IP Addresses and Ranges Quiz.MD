---
title: 'Private IP Addresses and Ranges Quiz'
date: 2026-11-13 00:00:00
description: Private and special IPv4 address range practice.
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
            min-width: 300px;
            font-family: monospace;
            font-size: 1.3em;
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
        .question input.cidr { width: 180px; }
        .question input.rng { width: 340px; }
        .question input.ans { width: 340px; }
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
<div class="Bold">Private IP Addresses and Ranges</div>
<p>Type the CIDR block and the address range for each type, in the format x.x.x.x/n and x.x.x.x - y.y.y.y</p>
<div id="typing"></div>

<div class="Bold">What Range Matches?</div>
<p>Read each description and type the matching CIDR block. The full address range is accepted too.</p>
<div id="matching"></div>

<div class="shuffle-row">
<button id="shuffle-btn" type="button">Randomise</button>
</div>

<script>
const items = [
    { name: 'Private Class A (RFC 1918)', cidr: '10.0.0.0/8', range: '10.0.0.0 - 10.255.255.255',
      desc: 'Class A private range. Used for internal enterprise LANs; must be translated via NAT/PAT to reach the internet.' },
    { name: 'Private Class B (RFC 1918)', cidr: '172.16.0.0/12', range: '172.16.0.0 - 172.31.255.255',
      desc: 'Class B private range. Often tested as a trap: the second octet stops at 31, so anything beyond that is a public IP.' },
    { name: 'Private Class C (RFC 1918)', cidr: '192.168.0.0/16', range: '192.168.0.0 - 192.168.255.255',
      desc: 'Class C private range. The standard range for small offices, branch sites, and home labs.' },
    { name: 'Loopback', cidr: '127.0.0.0/8', range: '127.0.0.1 - 127.255.255.254',
      desc: 'Tests local TCP/IP stack health (ping the loopback address); cannot be assigned to a physical interface.' },
    { name: 'APIPA / Link-Local', cidr: '169.254.0.0/16', range: '169.254.0.1 - 169.254.255.254',
      desc: 'Self-assigned by a host when it cannot reach a DHCP server; not routable beyond the local link.' }
];

const typingBox = document.getElementById('typing');
const matchBox = document.getElementById('matching');
const rows = {};
const savedAnswers = {};

function norm(s) {
    return s.toLowerCase().replace(/[\u2013\u2014]/g, '-').replace(/\s+/g, '');
}

function rowTail(id) {
    return '<div class="checkbox" id="' + id + '-checkbox"></div>' +
           '<button class="hint-btn" tabindex="-1" data-question="' + id + '">?</button>';
}

items.forEach(function(it, i) {
    // Section 1: type the CIDR and the range
    const tid = 't' + i;
    const trow = document.createElement('div');
    trow.className = 'question';
    trow.innerHTML =
        '<label for="' + tid + 'a">' + it.name + '</label>' +
        '<input type="text" class="cidr" id="' + tid + 'a" placeholder="CIDR" autocomplete="off" spellcheck="false">' +
        '<input type="text" class="rng" id="' + tid + 'b" placeholder="Address range" autocomplete="off" spellcheck="false">' +
        rowTail(tid);
    typingBox.appendChild(trow);
    rows[tid] = { fields: [
        { el: tid + 'a', answers: [it.cidr] },
        { el: tid + 'b', answers: [it.range] }
    ] };

    // Section 2: read the description, type the range
    const did = 'd' + i;
    const drow = document.createElement('div');
    drow.className = 'question';
    drow.innerHTML =
        '<div class="desc">' + it.desc + '</div>' +
        '<input type="text" class="ans" id="' + did + 'a" placeholder="Type the IP range" autocomplete="off" spellcheck="false">' +
        rowTail(did);
    matchBox.appendChild(drow);
    rows[did] = { fields: [
        { el: did + 'a', answers: [it.cidr, it.range] }
    ] };
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

    if (!typed || /[.\/ \-]$/.test(typed)) return;
    const answer = f.answers.find(function(a) { return a.toLowerCase().startsWith(typed.toLowerCase()); });
    if (!answer) return;
    const rest = answer.slice(typed.length);
    if (!rest) return;

    const delims = '. /-';
    let k = 0;
    while (k < rest.length && delims.indexOf(rest[k]) !== -1) k++;
    let m = -1;
    for (let j = k; j < rest.length; j++) {
        if (delims.indexOf(rest[j]) !== -1) { m = j; break; }
    }
    const end = m === -1 ? rest.length : m + 1;
    input.value = typed + rest.slice(0, end);
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