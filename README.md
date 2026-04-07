# Meu-site
Site
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
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      text-align: center;
      width: 350px;
    }
    input {
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
    }
    button:disabled {
      background: #aaa;
    }
    .loader {
      margin: 20px 0;
      font-size: 18px;
      color: #555;
    }
    .result {
      margin-top: 20px;
      font-weight: bold;
      color: green;
    }
    iframe {
      margin-top: 20px;
      width: 100%;
      height: 200px;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>Leitura ao Vivo</h2>

    <input type="text" id="urlInput" placeholder="Digite o link do site (https://...)" />
    <button id="loadSiteBtn">Carregar Site</button>

    <button id="startBtn">Iniciar Leitura</button>

    <div class="loader" id="loader"></div>
    <div class="result" id="result"></div>

    <iframe id="siteFrame"></iframe>
  </div>

  <script>
    const button = document.getElementById('startBtn');
    const loader = document.getElementById('loader');
    const result = document.getElementById('result');
    const loadSiteBtn = document.getElementById('loadSiteBtn');
    const urlInput = document.getElementById('urlInput');
    const siteFrame = document.getElementById('siteFrame');

    loadSiteBtn.addEventListener('click', () => {
      let url = urlInput.value.trim();
      if (!url.startsWith('http')) {
        url = 'https://' + url;
      }
      siteFrame.src = url;
    });

    button.addEventListener('click', () => {
      result.textContent = '';
      loader.textContent = 'Carregando leitura...';
      button.disabled = true;

      setTimeout(() => {
        loader.textContent = '';
        result.textContent = 'Resultado atualizado ao vivo!';
        button.disabled = false;
      }, 5000);
    });
  </script>
</body>
</html>
