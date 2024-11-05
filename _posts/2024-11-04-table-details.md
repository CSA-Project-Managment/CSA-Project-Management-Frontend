---
layout: post
title: Table Detais
type: issues
permalink: /tabledetails
comments: false
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Table Details</title>
  <style>
    h2 {
      color: white;
    }
    /* Container for the grid layout */
    #student-cards-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr); /* Two columns */
      gap: 20px;
      margin-top: 20px;
    }
    .student-card {
      background-color: #fff;
      border: 1px solid #ddd;
      border-radius: 5px;
      padding: 20px;
      width: 280px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      text-align: left;
    }
    .student-card h3 {
      margin: 0;
      font-size: 20px;
      color: black;
    }
    .student-card p {
      margin: 5px 0;
      font-size: 16px;
      color: black;
    }
  </style>
</head>
<body>

  <h2>Students in Table</h2>
  <div id="student-cards-container"></div>

  <script>
    document.addEventListener("DOMContentLoaded", function() {
      // Get the table number from the URL query parameter
      const urlParams = new URLSearchParams(window.location.search);
      const tableNumber = urlParams.get('table');

      if (tableNumber) {
        // Make the fetch request with the specified table number
        fetch("http://127.0.0.1:8181/api/students/find-team", {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify({
            "course": "CSA",
            "trimester": 1,
            "period": 3,
            "table": parseInt(tableNumber)
          })
        })
        .then(response => {
          if (!response.ok) {
            throw new Error("Network response was not ok");
          }
          return response.json();
        })
        .then(data => {
          const container = document.getElementById("student-cards-container");

          // Clear previous content and populate student cards
          container.innerHTML = "";
          data.forEach(student => {
            const card = document.createElement("div");
            card.className = "student-card";
            card.innerHTML = `
              <h3>${student.name}</h3>
              <p>Username: ${student.username}</p>
              <p>Table Number: ${student.tableNumber}</p>
              <p>Course: ${student.course}</p>
              <p>Trimester: ${student.trimester}</p>
              <p>Period: ${student.period}</p>
              <p>Tasks: ${student.tasks.join(", ")}</p>
            `;
            container.appendChild(card);
          });
        })
        .catch(error => {
          console.error("There was a problem with the fetch operation:", error);
        });
      } else {
        document.getElementById("student-cards-container").innerHTML = "<p>No table selected.</p>";
      }
    });
  </script>

</body>
</html>