<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Sticky Notes</title>

<style>
  body {
    font-family: Arial, sans-serif;
    background: #f2f2f2;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 40px;
    margin: 0;
  }

  .top-bar {
    display: flex;
    gap: 10px;
    margin-bottom: 30px;
  }

  #noteInput {
    width: 320px;
    padding: 12px;
    font-size: 16px;
    border-radius: 8px;
    border: 1px solid #ccc;
    outline: none;
  }

  #noteInput:focus {
    border-color: #555;
  }

  #resetBtn {
    padding: 12px 18px;
    font-size: 14px;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    background: #ff5c5c;
    color: white;
  }

  #resetBtn:hover {
    background: #e04848;
  }

  #notesContainer {
    width: 420px;
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  .note {
    padding: 20px;
    border-radius: 10px;
    color: #333;
    font-weight: 500;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    word-wrap: break-word;
  }
</style>
</head>

<body>

<div class="top-bar">
  <input type="text" id="noteInput" placeholder="Type notes">
  <button id="resetBtn">Reset</button>
</div>

<div id="notesContainer"></div>

<script>
document.addEventListener("DOMContentLoaded", function() {

  const input = document.getElementById("noteInput");
  const container = document.getElementById("notesContainer");
  const resetBtn = document.getElementById("resetBtn");

  function getRandomColor() {
    const colors = [
      "#FFADAD",
      "#FFD6A5",
      "#FDFFB6",
      "#CAFFBF",
      "#9BF6FF",
      "#A0C4FF",
      "#BDB2FF",
      "#FFC6FF"
    ];
    return colors[Math.floor(Math.random() * colors.length)];
  }

  input.addEventListener("keydown", function(event) {
    if (event.key === "Enter") {
      const text = input.value.trim();
      if (text !== "") {

        const note = document.createElement("div");
        note.className = "note";
        note.textContent = text;
        note.style.backgroundColor = getRandomColor();

        // Add newest note on TOP
        container.prepend(note);

        input.value = "";
      }
    }
  });

  resetBtn.addEventListener("click", function() {
    container.innerHTML = "";
  });

});
</script>

</body>
</html>
