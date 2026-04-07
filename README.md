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
      padding: 20px;
      text-align: center;
    }
    input, select {
      width: 90%;
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
      margin-top: 5px;
      width: 90%;
    }
    .loader {
      margin: 15px 0;
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

    <button id="openSiteBtn">Abrir em Tela Cheia</button>

    <select id="zoomControl">
      <option value="1">Zoom 100%</option>
      <option value="0.75">Zoom 75%</option>
      <option value="0.5">Zoom 50%</option>
      <option value="0.25">Zoom 25%</option>
    </select>

    <button id="startBtn">Iniciar Leitura (5s delay)</button>

    <div class="l
    
