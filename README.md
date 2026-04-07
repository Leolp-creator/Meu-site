# Meu-site
Site
<!DOCTYPE html>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Leitura com Delay</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f5f5f5;
    }
    .container {
      background: #fff;
      padding: 20px;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      text-align: center;
      width: 95%;
      max-width: 500px;
    }
    input, select {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
    }
    button {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      font-size: 16px;
      cursor: pointer;
      margin-top: 5px;
      width: 100%;
    }
    .viewer {
      margin-top: 15px;
      overflow: hidden;
      border: 1px solid #ccc;
      border-radius: 8px;
      height: 300px;
      position: relative;
    }
    iframe {
      width: 100%;
      height: 100%;
      border: none;
      transform-origin: 0 0;
    }
    .loader {
      margin: 15px 0;
      font-size: 16px;
    }
    .result {
      margin-top: 10px;
      font-weight: bold;
      color: green;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Leitura com Controle</h2>

    <input type="text" id="urlInput" placeholder="Digite o link do site" />
    <button id="loadSiteBtn">Carregar Site</button>

    <select id="zoomControl">
      <option value="1">Zoom 100%</option>
      <option value="0.75">Zoom 75%</option>
      <option value="0.5">Zoom 50%</option>
      <option value="0.25">Zoom 25%</option>
    </select>

    <button id="startBtn">Iniciar Leitura (5s delay)</button>

    <div class="loader" id="loader"></div>
    <div class="result" id="result"></div>

    <div class="viewer">
      <iframe id="siteFrame"></iframe>
    </div>
  </div>

  <script>
    const button = document.getElementById('startBtn');
    const loader = document.getElementById('loader');
    const result = document.getElementById('result');
    const loadSiteBtn = document.getElementById('loadSiteBtn');
    const urlInput = document.getElementById('urlInput');
    const siteFrame = document.getElementById('siteFrame');
    const zoomControl = document.getElementById('zoomControl');

    loadSiteBtn.addEventListener(
