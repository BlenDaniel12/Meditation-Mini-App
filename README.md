# Meditation-Mini-App
It used for meditation count down.


<html>
<head>
  <title>Meditation App</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #f5f5f5;
      font-family: Arial, sans-serif;
    }
    
    .container {
      text-align: center;
    }
    
    h1 {
      font-size: 32px;
      margin-bottom: 20px;
    }
    
    button {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
    }
    
    .timer {
      font-size: 48px;
      margin-bottom: 20px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Meditation App</h1>
    <p>Click the button below to start a 5-minute meditation session.</p>
    <button id="startButton" onclick="startMeditation()">Start Meditation</button>
    <p class="timer"></p>
  </div>

  <script>
    function startMeditation() {
      const startButton = document.getElementById('startButton');
      const timerElement = document.querySelector('.timer');
      startButton.disabled = true;
      let duration = 5 * 60; // 5 minutes in seconds

      const intervalId = setInterval(updateTimer, 1000);

      function updateTimer() {
        const minutes = Math.floor(duration / 60);
        const seconds = duration % 60;

        timerElement.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;

        if (duration <= 0) {
          clearInterval(intervalId);
          timerElement.textContent = 'Meditation Complete!';
          startButton.disabled = false;
        } else {
          duration--;
        }
      }
    }
  </script>
</body>
</html>
