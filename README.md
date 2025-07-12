<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <title>🍎 Apple Signal Viewer</title>
  <style>
    body { background: #111; color: white; text-align: center; font-family: sans-serif; padding: 20px; }
    .grid { display: grid; grid-template-columns: repeat(5, 60px); gap: 10px; justify-content: center; margin-top: 20px; }
    .cell { width: 60px; height: 60px; line-height: 60px; border-radius: 10px; font-size: 24px; background-color: #333; }
    .apple { background-color: green; }
    .bomb { background-color: red; }
    .sure { border: 3px solid gold; }
    button { margin-top: 20px; padding: 10px 20px; background: #28a745; color: white; font-size: 16px; border: none; border-radius: 8px; }
  </style>
</head>
<body>
  <h1>🍎 Apple of Fortune Signal Viewer</h1>
  <p>সিওর ঘর দেখতে নিচে টিপ দাও</p>
  <div class="grid" id="grid"></div>
  <button onclick="reveal()">🔍 সিগন্যাল দেখাও</button>

  <script>
    const grid = document.getElementById('grid');
    let data = Array.from({ length: 50 }, () => Math.random() > 0.3 ? 1 : 0);

    function draw() {
      grid.innerHTML = '';
      data.forEach((v, i) => {
        let d = document.createElement('div');
        d.className = 'cell ' + (v ? 'apple' : 'bomb');
        d.innerText = v ? '🍎' : '💣';
        grid.appendChild(d);
      });
    }

    function reveal() {
      document.querySelectorAll('.cell').forEach((c, i) => {
        if (data[i] === 1 && i % 5 === 2) c.classList.add('sure');
      });
    }

    draw();
  </script>
</body>
</html>
