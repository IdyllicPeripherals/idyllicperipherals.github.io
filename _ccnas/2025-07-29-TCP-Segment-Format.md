---
title: 'TCP Segment Format'
date: 2024-10-14 00:00:00
description: Labelling a TCP Packet.
featured_image: '/images/Photo_Blog/Blank.jpg'
---

 <head>
  <style>
    body {
      font-family: Arial, sans-serif;
      font-size: 1.1em;
    }

    #body_DTP {
      text-align: center;
      max-width: 900px;
      margin: auto;
    }

    table {
      border-collapse: collapse;
      margin: 20px auto;
      table-layout: fixed;
      width: 100%;
    }

    td {
      border: 1px dashed #000;
      width: auto;
      height: 60px;
      text-align: center;
      vertical-align: middle;
      padding: 6px;
    }

    .droppable {
      background-color: #f9f9f9;
      overflow: hidden;
      white-space: nowrap;
    }

    .droppable:hover {
      background-color: #e6f7ff;
    }

    .draggable {
      width: auto;
      min-width: 100px;
      background-color: #f0f0f0;
      border: 1px solid #000;
      padding: 6px;
      cursor: grab;
      margin: 5px;
      display: inline-block;
      white-space: nowrap;
    }

    .draggable:hover {
      background-color: #d9f6ff;
    }

    .correct {
      background-color: #d9f6ff;
    }

    .incorrect {
      background-color: #ffe2d9;
    }

    #restartButton {
      padding: 10px 40px;
      font-size: 1em;
      background-color: #ffa21a;
      color: white;
      border: none;
      border-radius: 5px;
      margin-top: 20px;
    }

    #restartButton:hover {
      background-color: #e68900;
    }

    #congratsMessage {
      visibility: hidden;
      margin-top: 20px;
      font-size: 18px;
    }
  </style>
</head>

<body>
  <div id="body_DTP">
    <h2>Label the TCP Segment</h2>
    <p>Drag the labels into the correct parts of the TCP segment.</p>

    <table>
      <tr>
        <td class="droppable" data-correct="Source Port"></td>
        <td class="droppable" data-correct="Destination Port"></td>
      </tr>
      <tr>
        <td colspan="2" class="droppable" data-correct="Sequence Number"></td>
      </tr>
      <tr>
        <td colspan="2" class="droppable" data-correct="Acknowledgment Number"></td>
      </tr>
      <tr>
        <td class="droppable" data-correct="Data Offset / Reserved / Flags"></td>
        <td class="droppable" data-correct="Window Size"></td>
      </tr>
      <tr>
        <td class="droppable" data-correct="Checksum"></td>
        <td class="droppable" data-correct="Urgent Pointer"></td>
      </tr>
      <tr>
        <td class="droppable" data-correct="Options"></td>
        <td class="droppable" data-correct="Padding"></td>
      </tr>
      <tr>
        <td colspan="2" class="droppable" data-correct="Data (Payload)"></td>
      </tr>
    </table>

    <div id="draggableContainer"></div>
    <button id="restartButton">Restart</button>
    <div id="congratsMessage">✅ All correct! You've labelled the TCP segment!</div>
  </div>

  <script>
    const labels = [
      "Source Port",
      "Destination Port",
      "Sequence Number",
      "Acknowledgment Number",
      "Data Offset / Reserved / Flags",
      "Window Size",
      "Checksum",
      "Urgent Pointer",
      "Options",
      "Padding",
      "Data (Payload)"
    ];

    const droppables = document.querySelectorAll('.droppable');
    const container = document.getElementById("draggableContainer");
    const congratsMessage = document.getElementById('congratsMessage');

    function shuffle(array) {
      for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
      }
      return array;
    }

    function setupDraggables() {
      container.innerHTML = "";
      const shuffled = shuffle([...labels]);
      shuffled.forEach(label => {
        const div = document.createElement("div");
        div.className = "draggable";
        div.textContent = label;
        div.draggable = true;

        div.addEventListener("dragstart", (e) => {
          e.dataTransfer.setData("text/plain", label);
        });

        container.appendChild(div);
      });
    }

    function reset() {
      droppables.forEach(d => {
        d.textContent = "";
        d.classList.remove("correct", "incorrect");
      });
      congratsMessage.style.visibility = "hidden";
      setupDraggables();
    }

    function checkAllCorrect() {
      const allCorrect = [...droppables].every(d => d.classList.contains("correct"));
      if (allCorrect) congratsMessage.style.visibility = "visible";
    }

    droppables.forEach(d => {
      d.addEventListener("dragover", e => e.preventDefault());
      d.addEventListener("drop", e => {
        const data = e.dataTransfer.getData("text/plain");
        const expected = d.getAttribute("data-correct");

        if (data === expected) {
          d.textContent = data;
          d.classList.add("correct");
          d.classList.remove("incorrect");
          checkAllCorrect();
        } else {
          d.classList.add("incorrect");
          setTimeout(() => d.classList.remove("incorrect"), 800);
        }
      });
    });

    document.getElementById("restartButton").addEventListener("click", reset);
    setupDraggables();
  </script>
</body>
