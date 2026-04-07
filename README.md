<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Leitura com Delay</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f5f5f5;
    }
    .container {
      padding: 15px;
      text-align: center;
    }
    input {
      width: 95%;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      font-size: 16px;
      cursor: pointer;
      margin: 5px 0;
      width: 95%;
    }
    .controls {
      display: flex;
      gap: 5px;
      justify-content: center;
      margin-top: 10px;
    }
    .controls button {
      width: auto;
      padding: 8px 12px;
    }
    .viewer {
      margin-top: 10px;
      width: 100%;
      height: 70vh;
      overflow: auto;
      border-top: 2px solid #ccc;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
      transform-origin: top left;
    }
    .loader {
      margin: 10px 0;
    }
    .result {
      font-weight: bold;
      color: green;
    }
  </style>
</head>
<body>
  <div class="container">
    <h3>Visualizador de Site</h3>

    <input type="text" id="urlInput" placeholder="Digite o link (ex: site.com)" />
    <button id="loadSiteBtn">Carregar Site</button>

    <div class="controls">
      <button onclick="zoomOut()">-</button>
      <button onclick="resetZoom()">100%</button>
      <button onclick="zoomIn()">+</button>
    </div>

    <button id="startBtn">Iniciar Leitura (5s)</button>

    <div class="loader" id="loader"></div>
    <div class="result" id="result"></div>

    <div class="viewer">
      <iframe id="siteFrame"></iframe>
    </div>
  </div>

  <script>
    const loadBtn = document.getElementById('loadSiteBtn');
    const urlInput = document.getElementById('urlInput');
    const frame = document.getElementById('siteFrame');
    const loader = document.getElementById('loader');
    const result = document.getElementById('result');
    const startBtn = document.getElementById('startBtn');

    let zoom = 1;

    loadBtn.addEventListener('click', () => {
      let url = urlInput.value.trim();
      if (!url.startsWith('http')) {
        url = 'https://' + url;
      }
      frame.src = url;
    });

    function applyZoom() {
      frame.style.transform = `scale(${zoom})`;
      frame.style.width = `${100 / zoom}%`;
      frame.style.height = `${100 / zoom}%`;
    }

    function zoomIn() {
      zoom += 0.2;
      applyZoom();
    }

    function zoomOut() {
      zoom -= 0.2;
      if (zoom < 0.2) zoom = 0.2;
      applyZoom();
    }

    function resetZoom() {
      zoom = 1;
      applyZoom();
    }

    startBtn.addEventListener('click', () => {
      result.textContent = '';
      loader.textContent = 'Carregando leitura...';
      startBtn.disabled = true;

      setTimeout(() => {
        loader.textContent = '';
        result.textContent = 'Leitura atualizada!';
        startBtn.disabled = false;
      }, 5000);
    });
  </script>
</body>
</html>
