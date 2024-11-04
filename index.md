---
layout: base
title: Student Home 
description: Home Page
hide: true
---

  <title>Table Selection</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f0f0f0;
      margin: 0;
    }
    .container {
      position: relative;
      width: 300px;
      height: 300px;
    }
    .button {
      position: absolute;
      width: 60px;
      padding: 15px;
      background-color: #FFA500; /* Orange color */
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 18px;
      text-align: center;
    }
    /* Position each button based on the drawing */
    #button1 { top: 10px; left: 10px; }
    #button2 { top: 80px; left: 20px; }
    #button3 { top: 150px; left: 10px; }
    #button4 { top: 220px; left: 60px; }
    #button5 { top: 160px; right: 10px; }
    #button6 { top: 80px; right: 10px; }
  </style>
</head>
<body>

  <div class="container">
    <button id="button1" class="button" onclick="selectTable(1)">1</button>
    <button id="button2" class="button" onclick="selectTable(2)">2</button>
    <button id="button3" class="button" onclick="selectTable(3)">3</button>
    <button id="button4" class="button" onclick="selectTable(4)">4</button>
    <button id="button5" class="button" onclick="selectTable(5)">5</button>
    <button id="button6" class="button" onclick="selectTable(6)">6</button>
  </div>