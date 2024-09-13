---
title: 'Dynamic Trunking Protocol'
date: 2024-09-13 00:00:00
description: Interactive Way To Learn DTP.
featured_image: '/images/Photo_Blog/DTP.jpg'
---

<head>
    <script>
    function LoadOnce() 
{ 
window.location.reload(); 
} 
    
    function updateFeedback() {
        const switchPort1 = document.getElementById('switchPort1').value;
        const switchPort2 = document.getElementById('switchPort2').value;
        const feedback = document.getElementById('feedback');

        let response = '';

        if (switchPort1 === 'Dynamic Auto' && switchPort2 === 'Dynamic Auto') {
            response = 'Access';
        } else if (switchPort1 === 'Dynamic Auto' && switchPort2 === 'Dynamic Desirable') {
            response = 'Trunk';
        } else if (switchPort1 === 'Dynamic Auto' && switchPort2 === 'Trunk') {
            response = 'Trunk';
        } else if (switchPort1 === 'Dynamic Auto' && switchPort2 === 'Access') {
            response = 'Access';
        } else if (switchPort1 === 'Dynamic Desirable' && switchPort2 === 'Dynamic Auto') {
            response = 'Trunk';
        } else if (switchPort1 === 'Dynamic Desirable' && switchPort2 === 'Dynamic Desirable') {
            response = 'Trunk';
        } else if (switchPort1 === 'Dynamic Desirable' && switchPort2 === 'Trunk') {
            response = 'Trunk';
        } else if (switchPort1 === 'Dynamic Desirable' && switchPort2 === 'Access') {
            response = 'Access';
        } else if (switchPort1 === 'Trunk' && switchPort2 === 'Dynamic Auto') {
            response = 'Trunk';
        } else if (switchPort1 === 'Trunk' && switchPort2 === 'Dynamic Desirable') {
            response = 'Trunk';
        } else if (switchPort1 === 'Trunk' && switchPort2 === 'Trunk') {
            response = 'Trunk';
        } else if (switchPort1 === 'Trunk' && switchPort2 === 'Access') {
            response = 'Limited Connectivity';
        } else if (switchPort1 === 'Access' && switchPort2 === 'Dynamic Auto') {
            response = 'Access';
        } else if (switchPort1 === 'Access' && switchPort2 === 'Dynamic Desirable') {
            response = 'Access';
        } else if (switchPort1 === 'Access' && switchPort2 === 'Trunk') {
            response = 'Limited Connectivity';
        } else if (switchPort1 === 'Access' && switchPort2 === 'Access') {
            response = 'Access';
        } else {
            response = '';
        }

        // Determine the prefix based on the response
        let prefix = '';
        if (response === 'Access') {
            prefix = 'The Switch Port will be an';
        } else if (response === 'Trunk') {
            prefix = 'The Switch Port will be a';
        } else if (response === 'Limited Connectivity') {
            feedback.innerHTML = `The Switch Port may experience <br><span class="bold_DTP">${response}</span>`;
            return; // Exit function early to prevent adding "Port"
        }

        feedback.innerHTML = `${prefix} <br><span class="bold_DTP">${response} Port</span>`;
    }

    // Call updateFeedback when the page loads to handle initial values
    document.addEventListener('DOMContentLoaded', function() {
        updateFeedback();
    });
</script>
    <style>
        #body_DTP {
            font-size: 1.25em; /* 25% larger than default size */
            text-align: center; /* Center align text and content */
            margin: 0;
            padding: 0;
            justify-content: center;
            align-items: center;
        }
        #optionsForm_DTP {
            display: inline-block; /* Keep form inline but easier to style as a block */
            text-align: center; /* Align form labels and selects to the center */
            justify-content: center;
            line-height: 1.15em;
        }
        select {
            font-size: 1em; /* Adjust font size for better fit */
            width: 250px; /* Increase width for better text fit */
            height: 2.5em; /* Increase height to match font size */
            padding: 5px; /* Add padding for better text alignment */
            box-sizing: border-box; /* Include padding and border in total width/height */
            justify-content: center;
            align-items: center;
            appearance: none;  /* For modern browsers */
            -webkit-appearance: none; /* For Chrome and Safari */
            -moz-appearance: none; /* For Firefox */
            border-radius: 10px; /* Rounded corners */
            text-align-last: center; /* Center the text in the dropdown */
        }
        #feedback {
            margin-top: 20px;
            display: block; /* Ensures feedback is displayed on a new line */
        }
        .bold_DTP {
            font-weight: bold;
        }
    </style>
</head>

<body>
    <div id="body_DTP">
        <div>
        <h2>Dynamic Trunking Protocol Modes</h2>
            <br>
            <form id="optionsForm_DTP">
                <label for="switchPort1">Switch Port A:</label>
                <select id="switchPort1" name="switchPort1" onchange="updateFeedback()">
                    <option value="Dynamic Auto">Dynamic Auto</option>
                    <option value="Dynamic Desirable">Dynamic Desirable</option>
                    <option value="Trunk">Trunk</option>
                    <option value="Access">Access</option>
                </select>
                <br><br>
                <label for="switchPort2">Switch Port B:</label>
                <select id="switchPort2" name="switchPort2" onchange="updateFeedback()">
                    <option value="Dynamic Auto">Dynamic Auto</option>
                    <option value="Dynamic Desirable">Dynamic Desirable</option>
                    <option value="Trunk">Trunk</option>
                    <option value="Access">Access</option>
                </select>
            </form>
    
            <div id="feedback">The Switch Port will be an <br><span class="bold_DTP"> Access Port</div>
        </div>
    </div>
</body>
