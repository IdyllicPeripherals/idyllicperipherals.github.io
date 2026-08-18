<style>
    * { box-sizing: border-box; }

    body {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        margin: 0;
        padding: 20px 15px;
        color: #333;
    }

    .container { max-width: 800px; margin: 0 auto; width: 100%; }

    textarea {
        width: 100%;
        height: 150px;
        padding: 12px;
        border: 1px solid #ccc;
        border-radius: 6px;
        font-size: 16px;
        resize: vertical;
    }

    .counter-container {
        text-align: right;
        font-size: 0.85rem;
        color: #666;
        margin-top: 4px;
        margin-bottom: 10px;
        font-weight: 500;
    }

    #charCount { color: #FFA21A; font-weight: bold; }

    .chunk-size-toggle {
        display: flex;
        align-items: center;
        gap: 8px;
        margin-bottom: 10px;
        font-size: 0.9rem;
        color: #555;
    }

    .toggle-btn {
        padding: 6px 14px;
        border: 2px solid #FFA21A;
        border-radius: 6px;
        background: white;
        color: #FFA21A;
        font-weight: bold;
        cursor: pointer;
        transition: background 0.2s, color 0.2s;
    }

    .toggle-btn.active { background: #FFA21A; color: white; }
    .toggle-btn:hover:not(.active) {
        background: #FFA21A;
        color: white;
    }

    .action-btn {
        width: 100%;
        padding: 12px;
        background-color: #FFA21A;
        color: white;
        border: none;
        border-radius: 6px;
        font-size: 16px;
        font-weight: bold;
        cursor: pointer;
        margin-top: 10px;
        transition: background 0.2s;
    }

    .action-btn:hover { background-color: #d88200; }

    #output { margin-top: 20px; }

    .chunk-card {
        border: 1px solid #e1e4e8;
        border-radius: 8px;
        padding: 15px;
        margin-bottom: 15px;
        background: white;
        box-shadow: 0 2px 4px rgba(0,0,0,0.05);
    }

    .chunk-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 10px;
        font-size: 0.9rem;
        color: #555;
        flex-wrap: wrap;
        gap: 5px;
    }

    .copy-btn {
        padding: 6px 12px;
        background-color: #FFA21A;
        color: white;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        font-weight: 500;
    }

    .copy-btn:hover { background-color: #d88200; }

    .chunk-text {
        width: 100%;
        height: 120px;
        background-color: #fafafa;
        color: #4d5863;
        font-family: monospace;
        font-size: 14px;
    }
</style>

<h3 style="text-align: left;">Copy Code in 10,000 or 2,000 Character Chunks</h3>

<br>

<main class="container">
    <textarea id="inputText" placeholder="Paste your text here..."></textarea>

    <div class="counter-container">
        Characters: <span id="charCount">0</span>
    </div>

    <div class="chunk-size-toggle">
        <label>Chunk size:</label>
        <button class="toggle-btn active" id="btn10k" onclick="setChunkSize(10000, this)">10,000</button>
        <button class="toggle-btn" id="btn9k" onclick="setChunkSize(9000, this)">9,000</button>
        <button class="toggle-btn" id="btn2k" onclick="setChunkSize(2000, this)">2,000</button>
    </div>

    <button class="action-btn" onclick="splitText()">Split Text Safely</button>

    <div id="output"></div>
</main>

<script>
    let maxChunkSize = 10000;

    function setChunkSize(size, btn) {
        maxChunkSize = size;
        document.querySelectorAll('.toggle-btn').forEach(function(b) {
            b.classList.remove('active');
        });
        btn.classList.add('active');
    }

    var inputText = document.getElementById('inputText');

    inputText.addEventListener('input', updateCount);
    inputText.addEventListener('paste', function() {
        setTimeout(updateCount, 0);
    });

    function updateCount() {
        document.getElementById('charCount').textContent =
            inputText.value.length.toLocaleString();
    }

    function splitText() {
        var text = inputText.value;
        var output = document.getElementById('output');
        output.innerHTML = '';

        if (!text.trim()) {
            output.innerHTML = '<p style="color:red;">Please enter some text first.</p>';
            return;
        }

        var index = 0;
        var chunkIndex = 1;

        while (index < text.length) {
            if (text.length - index <= maxChunkSize) {
                createChunkBox(text.slice(index), chunkIndex++);
                break;
            }

            var endPoint = index + maxChunkSize;
            var lastSpace = text.lastIndexOf(' ', endPoint);
            var lastNewline = text.lastIndexOf('\n', endPoint);
            var cutPoint = Math.max(lastSpace, lastNewline);

            if (cutPoint <= index) cutPoint = endPoint;

            createChunkBox(text.slice(index, cutPoint), chunkIndex++);
            index = cutPoint + 1;
        }
    }

    function createChunkBox(chunk, number) {
        var card = document.createElement('div');
        card.className = 'chunk-card';

        var header = document.createElement('div');
        header.className = 'chunk-header';

        var label = document.createElement('span');
        label.innerHTML = '<strong>Chunk ' + number + '</strong> (' + chunk.length.toLocaleString() + ' chars)';

        var copyBtn = document.createElement('button');
        copyBtn.className = 'copy-btn';
        copyBtn.innerText = 'Copy';
        copyBtn.onclick = function() { copyChunk(copyBtn); };

        var textArea = document.createElement('textarea');
        textArea.className = 'chunk-text';
        textArea.readOnly = true;
        textArea.value = chunk;

        header.appendChild(label);
        header.appendChild(copyBtn);
        card.appendChild(header);
        card.appendChild(textArea);

        document.getElementById('output').appendChild(card);
    }

    function copyChunk(button) {
        var textarea = button.closest('.chunk-card').querySelector('.chunk-text');
        navigator.clipboard.writeText(textarea.value).then(function() {
            var originalText = button.innerText;
            button.innerText = 'Copied!';
            button.style.backgroundColor = '#FFA21A';
            setTimeout(function() {
                button.innerText = originalText;
                button.style.backgroundColor = '';
            }, 1200);
        });
    }
</script>
