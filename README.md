<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Delay Visual de Site</title>
<style>
body{font-family:Arial;margin:0;background:#111;color:#fff}
.container{padding:10px;text-align:center}
input,select,button{width:95%;padding:10px;margin:5px 0;border-radius:8px;border:none}
button{background:#007bff;color:#fff}
.viewer{position:relative;height:75vh;margin-top:10px}
iframe{width:100%;height:100%;border:none}
.overlay{
  position:absolute;
  top:0;left:0;
  width:100%;height:100%;
  background:black;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:20px;
}
</style>
</head>
<body>
<div class="container">
<h3>Simulador de Delay (sem atualizar página)</h3>

<input type="text" id="urlInput" placeholder="Digite o site">

<select id="delaySelect">
<option value="1000">1 segundo</option>
<option value="2000">2 segundos</option>
<option value="3000">3 segundos</option>
<option value="4000">4 segundos</option>
<option value="5000">5 segundos</option>
</select>

<button onclick="iniciar()">Iniciar</button>

<div class="viewer">
  <iframe id="frame"></iframe>
  <div class="overlay" id="overlay">Aguardando...</div>
</div>
</div>

<script>
let delay = 2000;
let filaConteudo = '';

function iniciar(){
  let url = document.getElementById('urlInput').value.trim();
  delay = document.getElementById('delaySelect').value;

  if(!url.startsWith('http')) url = 'https://' + url;

  const frame = document.getElementById('frame');
  const overlay = document.getElementById('overlay');

  overlay.style.display = 'flex';
  overlay.innerText = 'Carregando...';

  // carrega site normal
  frame.src = url;

  // simula delay visual
  setInterval(()=>{
    overlay.style.display = 'flex';
    overlay.innerText = 'Delay...';

    setTimeout(()=>{
      overlay.style.display = 'none';
    }, delay);

  }, delay + 2000);
}
</script>
</body>
</html>
