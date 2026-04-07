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
      width: 300px;
    }
    button {
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      background: #007bff;
      color: white;
      font-size: 16px;
      cursor: pointer;
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
  </style>
</head>
<body>
  <div class="container">
    <h2>Leitura ao Vivo</h2>
    <button id="startBtn">Iniciar Leitura</button>
    <div class="loader" id="loader"></div>
    <div class="result" id="result"></div>
  </div>

  <script>
    const button = document.getElementById('startBtn');
    const loader = document.getElementById('loader');
    const result = document.getElementById('result');

    button.addEventListener('click', () => {
      result.textContent = '';
      loader.textContent = 'Carregando leitura...';
      button.disabled = true;

      setTimeout(() => {
        loader.textContent = '';
        result.textContent = 'Resultado atualizado ao vivo!';
        button.disabled = false;
      }, 5000); // delay de 5 segundos
    });
  </script>
</body>
</html>
