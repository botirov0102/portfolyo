<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Uyga vazifa - DOM amaliyoti</title>
</head>
<body>

  <!-- 1-misol -->
  <p id="info">Salom!</p>
  <button onclick="changeText()">O'zgartir</button>

  <script>
    function changeText() {
      document.getElementById("info").innerText = "Xush kelibsiz!";
    }
  </script>

  <hr>

  <!-- 2-misol -->
  <h1 id="title">JavaScript</h1>
  <button onclick="changeColor()">Rangni o'zgartir</button>

  <script>
    function changeColor() {
      document.getElementById("title").style.color = "red";
    }
  </script>

  <hr>

  <!-- 3-misol -->
  <p class="text">Paragraph 1</p>
  <p class="text">Paragraph 2</p>
  <p class="text">Paragraph 3</p>
  <button onclick="makeGreen()">Yashil qil</button>

  <script>
    function makeGreen() {
      let elements = document.getElementsByClassName("text");
      for (let i = 0; i < elements.length; i++) {
        elements[i].style.color = "green";
      }
    }
  </script>

</body>
</html>
