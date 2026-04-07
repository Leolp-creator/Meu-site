<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Controle de Sites</title>
  <style>
    body { font-family: Arial; margin:0; background:#f5f5f5; }
    .tabs { display:flex; background:#007bff; }
    .tab { flex:1; padding:12px; color:white; text-align:center; cursor:pointer; }
    .tab.active { background:#0056b3; }
    .content { display:none; padding:15px; }
    .content.active { display:block; }
    input { width:100%; padding:10px; margin:10px 0; border-radius:8px; border:1px solid #ccc; }
    button { width:100%; padding:10px; border:none; border-radius:8px; background:#007bff; color:white; margin-bottom:10px; }
    .viewer { height:70vh; overflow:auto; border-top:2px solid #ccc; }
    iframe { width:100%; height:100%; border:none; }
  </style>
</head>
<body>

<div class="tabs">
  <div class="tab active" onclick="openTab('busca')">Buscar Site</div>
  <div class="tab" onclick="openTab('visualizar')">Visualizar</div>
</div>

<div id="busca" class="content active">
  <h3>Buscar e acessar site</h3>
  <input type="text" id="urlInput" placeholder="Digite o link (ex: example.com)">
  <button onclick="carregarSite()">Acessar Site</button>
</div>

<div id="visualizar" class="content">
  <h3>Visualização</h3>
  <div class="viewer">
    <iframe id="siteFrame"></iframe>
  </div>
</div>

<script>
function openTab(tabId){
  document.querySelectorAll('.content').forEach(c=>c.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  document.getElementById(tabId).classList.add('active');
  event.target.classList.add('active');
}

function carregarSite(){
  let url = document.getElementById('urlInput').value.trim();
  if(!url.startsWith('http')) url = 'https://' + url;
  document.getElementById('siteFrame').src = url;

  // muda automaticamente pra aba visualizar
  document.querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.content').forEach(c=>c.classList.remove('active'));
  document.querySelector('[onclick="openTab(\'visualizar\')"]').classList.add('active');
  document.getElementById('visualizar').classList.add('active');
}
</script>

</body>
</html>
