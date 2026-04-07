<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Controle de Delay de Site</title>

<style>
body{
  font-family: Arial;
  margin:0;
  background:#f0f0f0;
}

.container{
  padding:15px;
  text-align:center;
}

input, select, button{
  width:95%;
  padding:10px;
  margin:5px 0;
  border-radius:8px;
  border:1px solid #ccc;
}

button{
  background:#007bff;
  color:#fff;
  border:none;
  font-weight:bold;
}

.viewer{
  margin-top:10px;
  height:70vh;
  border-top:2px solid #ccc;
}

iframe{
  width:100%;
  height:100%;
  border:none;
}

#status{
  margin-top:10px;
  font-weight:bold;
}
</style>

</head>

<body>

<div class="container">
  <h3>Controle de Delay (até 5s)</h3>

  <input 
    type="text" 
    id="urlInput" 
    placeholder="Digite o link do site (ex: example.com)"
  >

  <select id="delaySelect">
    <option value="1000">Delay 1s</option>
    <option value="2000">Delay 2s</option>
    <option value="3000">Delay 3s</option>
    <option value="4000">Delay 4s</option>
    <option value="5000">Delay 5s</option>
  </select>

  <button onclick="carregarComDelay()">
    Carregar Site com Delay
  </button>

  <div id="status"></div>

  <div class="viewer">
    <iframe id="frame"></iframe>
  </div>
</div>

<script>
function carregarComDelay(){

  let url = document.getElementById('urlInput').value.trim();
  let delay = document.getElementById('delaySelect').value;
  let status = document.getElementById('status');

  if(!url){
    alert('Digite um link');
    return;
  }

  if(!url.startsWith('http')){
    url = 'https://' + url;
  }

  status.innerText = 'Aguardando delay...';

  setTimeout(()=>{
    document.getElementById('frame').src = url;
    status.innerText = 'Site carregado!';
  }, delay);

}
</script>

</body>
</html>
