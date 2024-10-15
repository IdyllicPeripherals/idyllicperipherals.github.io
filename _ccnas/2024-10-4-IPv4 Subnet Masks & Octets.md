---
title: 'IPv4 Subnet Masks & Octets'
date: 2024-10-4 00:00:00
description: Binary converted to Numbers.
featured_image: '/images/Photo_Blog/Blank.jpg'
---

<head>
    <style>
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
        #body_MASK {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 0;
            flex-direction: column;
            font-size: 1.25em; /* 25% larger than default size */
            text-align: center; /* Center align text and content */
            margin: 0;
            padding: 0;
            justify-content: center;
            align-items: center;
        }
        h1 {
            margin-bottom: 20px;
        }
        th, td {
            padding: 12px;
            width: 50%;
        }
        th {
            background-color: #2a2f36; /* Background color for the heading */
            color: white; /* Set heading text color to white */
            border: none; /* Remove border from heading */
        }
        th:first-child {
            border-right: 1px solid #373b40; /* Add a white line to the right of the first heading */
        }
        td {
            border: none; /* Remove border from data cells */
            background-color: #fff;
        }
        /* Centering table content */
        #result {
            display: flex;
            justify-content: center;
            width: 100%;
        }
    </style>
</head>

<body>
<div id="body_MASK">
    <h1>Octet Subnet Mask Tool</h1>

    <!-- Dropdown for selecting Subnet Mask -->
    <select id="subnetSelect">
        <option value="">Select Subnet Mask</option>
        <option value="128">128</option>
        <option value="192">192</option>
        <option value="224">224</option>
        <option value="240">240</option>
        <option value="248">248</option>
        <option value="252">252</option>
        <option value="254">254</option>
        <option value="255">255</option>
    </select>

    <!-- Table will appear here -->
    <div id="result"></div>
    
</div>
    <script>
        const subnetInfo = {
            "128": { cidr: "/1", binary: "10000000" },
            "192": { cidr: "/2", binary: "11000000" },
            "224": { cidr: "/3", binary: "11100000" },
            "240": { cidr: "/4", binary: "11110000" },
            "248": { cidr: "/5", binary: "11111000" },
            "252": { cidr: "/6", binary: "11111100" },
            "254": { cidr: "/7", binary: "11111110" },
            "255": { cidr: "/8", binary: "11111111" }
        };

        function formatBinary(binary) {
            return binary.slice(0, 4) + ' ' + binary.slice(4);
        }

        document.getElementById("subnetSelect").addEventListener("change", function () {
            const subnet = subnetInfo[this.value];
            if (subnet) {
                document.getElementById("result").innerHTML = `
                    <table>
                        <tr>
                            <th>CIDR Notation</th>
                            <th>Binary</th>
                        </tr>
                        <tr>
                            <td>${subnet.cidr}</td>
                            <td>${formatBinary(subnet.binary)}</td>
                        </tr>
                    </table>
                `;
            } else {
                document.getElementById("result").innerHTML = "";
            }
        });
    </script>

</body>
