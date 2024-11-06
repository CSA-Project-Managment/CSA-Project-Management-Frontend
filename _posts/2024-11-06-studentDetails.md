---
layout: post
title: Student Info
type: issues
permalink: /student-info
comments: false
---

<html>
<head>
  <title>Student Details</title>
  <style>
    #details-container {
      display: grid;
      grid-template-columns: 1fr;
      gap: 10px;
      background-color: white;
      border: 1px solid #ddd;
      border-radius: 5px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      padding: 20px;
      max-width: 300px;
      text-align: left;
    }
    #details-container h2 {
      color: black;
      margin: 0;
      text-align: center;
    }
    #details-container p {
      font-size: 16px;
      color: black;
      margin: 5px 0;
    }
  </style>
</head>
<body>

<div class="details-container" id="studentDetails">
  <h2>Student Details</h2>
  <p id="studentName">Name: </p>
  <p id="studentCourse">Course: </p>
  <p id="studentTrimester">Trimester: </p>
  <p id="studentPeriod">Period: </p>
</div>

<script>
  // Function to display student details from query parameters
  function displayStudentDetails() {
    const urlParams = new URLSearchParams(window.location.search);
    document.getElementById("studentName").innerText = "Name: " + urlParams.get("name");
    document.getElementById("studentCourse").innerText = "Course: " + urlParams.get("course");
    document.getElementById("studentTrimester").innerText = "Trimester: " + urlParams.get("trimester");
    document.getElementById("studentPeriod").innerText = "Period: " + urlParams.get("period");
  }

  // Display the student details on page load
  window.onload = displayStudentDetails;
</script>

</body>
</html>
