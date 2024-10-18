---
title: 'IEEE 802.3 Ethernet Frame Format'
date: 2024-10-14 00:00:00
description: Labelling a Ethernet Frame.
featured_image: '/images/Photo_Blog/Blank.jpg'
---

<head>
    <style>
      /* CSS for congratulations message */

        #body {
            display: flex;
            flex-direction: column;
            justify-content: center; /* Center horizontally */
            align-items: center; /* Center vertically */
            margin: 0;
            height: 80vh; /* Full height of the viewport */
            font-size: 1.25em; /* 25% larger than default size */
        }

        #body_DTP {
            font-size: 1.25em; /* 25% larger than default size */
            text-align: center; /* Center align text and content */
            margin: 0;
            padding: 0;
            justify-content: center;
            align-items: center;
                max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: min(var(--vertical-breather), 80px);
    max-width: var(--container-max-width);
    margin-left: auto;
    margin-right: auto;
    padding-left: var(--container-gutter);
    padding-right: var(--container-gutter);
    --container-outer-margin: 0px;
        }

        table {
            border-collapse: collapse;
            margin-top: 20px; /* Space between the table and the top of the page */
            width: 50%;
            table-layout: fixed; /* Ensure fixed layout for columns */
            
        }

        td {
            font-size: 1.25em; /* 25% larger than default size */
            width: 120px; /* Consistent width for each cell */
            height: 70px; /* Consistent height for each cell */
            text-align: center;
            vertical-align: middle; /* Center content vertically */
            position: relative; /* Allow positioning of droppable boxes */
            padding: 0; /* Remove padding */
            margin: 0; /* Remove margin */
            
        }

        /* Dotted border for the first row */
        tr:first-child td {
            border: 1px dotted #000; /* Dotted border for cells in the first row */
            
        }

        /* Remove left and right borders from row 2 */
        tr:nth-child(2) td {
            border: 1px dotted #000
        }

        tr:nth-child(3) td {
            background-color: #F5F7FA;
            border: none;
        }
     
        .draggable {
            cursor: grab;
            background-color: #f0f0f0;
            border: 1px solid #000;
            user-select: none; /* Prevent text selection */
            line-height: 100%; /* Center the text vertically in the cell */
            width: 120px; /* Match the droppable cell width */
            transition: background-color 0.3s; /* Smooth background transition */
        }

        .draggable:hover {
            background-color: #d9f6ff; /* Change color on hover */
        }

        .droppable {
            border: 1px dashed #000;
            background-color: #ffffff; /* White background for droppable boxes */
            transition: background-color 0.3s; /* Smooth background transition */
            line-height: 90%; /* Center the text vertically in the cell */

        }

        .correct {
            background-color: #d9f6ff; /* Light green for correct */
        }

        .incorrect {
            background-color: #ffe2d9; /* Light red for incorrect */
        }

        #restartButton {
            padding: 20px 120px;
            font-size: 1em; /* 25% larger than default size */
            cursor: pointer;
            background-color: #ffa21a; /* Button color */
            color: white; /* Button text color */
            border: none; /* Remove border */
            border-radius: 5px; /* Rounded corners */
            transition: background-color 0.3s; /* Smooth transition for hover effect */
            
        }

        #restartButton:hover {
            background-color: #e68900; /* Darker shade on hover */
        }
      #congratsMessage {
        visibility: hidden; /* Hidden initially, but space is still reserved */
        margin-top: 20px;
        font-size: 20px;
    }
            @media (max-width: 600px) {
            .button {
                width: 100%; /* Full width on smaller screens */
            }
    </style>

</head>
<body id="bodyEthernet">
    <div id="body_DTP">
 <h2>Labelling an Ethernet Frame</h2>
 <br>
 Place the correct labels in the blank spaces. 
<br>

    <table>
        <tr>
            <td class="droppable" data-correct="Preamble"></td>
            <td class="droppable" data-correct="SFD"></td>
            <td class="droppable" data-correct="Destination Mac"></td>
            <td class="droppable" data-correct="Source MAC"></td>
            <td class="droppable" data-correct="Type"></td>
            <td class="droppable" data-correct="Data and Pad"></td>
            <td class="droppable" data-correct="FCS"></td>
        </tr>
        <tr>
            <td class="droppable" data-correct="7"></td>
            <td class="droppable" data-correct="1"></td>
            <td class="droppable" data-correct="6"></td>
            <td class="droppable" data-correct="6"></td>
            <td class="droppable" data-correct="2"></td>
            <td class="droppable" data-correct="46-1500"></td>
            <td class="droppable" data-correct="4"></td>
        </tr>
        <!-- Empty row for spacing -->
        <tr>
            <td colspan="7" style="height: 10px;"></td> <!-- Adjust the height for more/less space -->
        </tr>
        <tr id="draggableRow">
            <!-- Draggable texts will be inserted here dynamically -->
        </tr>
        <tr id="numberRow">
            <!-- Draggable numbers will be inserted here dynamically -->
        </tr>
    </table>

<button id="restartButton">Restart</button>

  <!-- Congratulations message HTML -->
<div id="congratsMessage">Congratulations! You've correctly labelled the Ethernet Frame!</div>

  </div>
    <script>
    const texts = [
        "Preamble",
        "SFD",
        "Destination Mac",
        "Source MAC",
        "Type",
        "Data and Pad",
        "FCS"
    ];

    const frameSizes = [
        "7",
        "1",
        "6",
        "6",
        "2",
        "46-1500",
        "4"
    ];

    const draggableRow = document.getElementById("draggableRow");
    const numberRow = document.getElementById("numberRow");
    const droppables = document.querySelectorAll('.droppable');
    const congratsMessage = document.getElementById('congratsMessage');

    function shuffle(array) {
        for (let i = array.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]];
        }
        return array;
    }

    function placeDraggablesRandomly() {
        draggableRow.innerHTML = "";
        numberRow.innerHTML = "";
        const shuffledTexts = shuffle([...texts]);
        const shuffledNumbers = shuffle([...frameSizes]);

        shuffledTexts.forEach(text => {
            const td = document.createElement("td");
            td.className = "draggable";
            td.draggable = true;
            td.textContent = text;

            td.addEventListener('dragstart', (e) => {
                e.dataTransfer.setData('text/plain', text);
            });

            draggableRow.appendChild(td);
        });

        shuffledNumbers.forEach(number => {
            const td = document.createElement("td");
            td.className = "draggable";
            td.draggable = true;
            td.textContent = number;

            td.addEventListener('dragstart', (e) => {
                e.dataTransfer.setData('text/plain', number);
            });

            numberRow.appendChild(td);
        });
    }

    function resetDroppableCells() {
        droppables.forEach(droppable => {
            droppable.textContent = "";
            droppable.classList.remove('correct', 'incorrect');
        });
        congratsMessage.style.visibility = "hidden"; // Hide the message
    }

    function checkCompletion() {
        let allCorrect = true;
        droppables.forEach(droppable => {
            if (droppable.textContent === "" || !droppable.classList.contains('correct')) {
                allCorrect = false;
            }
        });
        if (allCorrect) {
            congratsMessage.style.visibility = "visible"; // Show the message when all are correct
        }
    }

    droppables.forEach(droppable => {
        droppable.addEventListener('dragover', (e) => {
            e.preventDefault();
        });

        droppable.addEventListener('drop', (e) => {
            const draggedText = e.dataTransfer.getData('text/plain');
            const correctId = droppable.getAttribute('data-correct');

            if (draggedText.replace(/\s/g, "") === correctId.replace(/\s/g, "")) {
                droppable.classList.add('correct');
                droppable.textContent = draggedText;
                checkCompletion(); // Check completion after a successful drop
            } else {
                droppable.classList.add('incorrect');
                setTimeout(() => {
                    droppable.classList.remove('incorrect');
                }, 1000);
            }
        });
    });

    document.getElementById("restartButton").addEventListener("click", () => {
        resetDroppableCells();
        placeDraggablesRandomly();
    });

    placeDraggablesRandomly();
</script>

</body>

