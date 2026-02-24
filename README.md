<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Gerador de Sensibilidade RK</title>

<style>
body{
    margin:0;
    font-family:Arial, sans-serif;
    background:#0f0f0f;
    color:white;
    text-align:center;
}

.container{
    padding:20px;
}

.logo{
    width:120px;
    margin-top:20px;
}

.card{
    background:#1a1a1a;
    padding:20px;
    border-radius:15px;
    margin-top:20px;
    box-shadow:0 0 15px rgba(0,0,0,0.5);
}

input{
    width:80%;
    padding:10px;
    margin:10px 0;
    border-radius:10px;
    border:none;
    text-align:center;
    font-size:18px;
}

button{
    width:85%;
    padding:12px;
    margin-top:10px;
    border:none;
    border-radius:12px;
    font-size:16px;
    font-weight:bold;
    cursor:pointer;
}

.btn-gerar{
    background:#6a00ff;
    color:white;
}

.btn-copiar{
    background:#00c853;
    color:white;
}

.resultado{
    margin-top:15px;
    font-size:18px;
    color:#00e5ff;
    word-wrap:break-word;
}
</style>
</head>

<body>

<div class="container">

<img src="logo.png" class="logo">

<div class="card">

<h2>Gerador de Sensibilidade</h2>

<input type="number" id="geral" placeholder="Sensibilidade Geral (0-200)" min="0" max="200">

<button class="btn-gerar" onclick="gerar()">Gerar Sensibilidade Ajustada</button>

<div class="resultado" id="resultado"></div>

<button class="btn-copiar" onclick="copiar()">Copiar Sensi Ajustada</button>

</div>
</div>

<script>
function gerar(){
    let geral = parseInt(document.getElementById("geral").value);

    if(isNaN(geral)){
        alert("Digite um valor válido!");
        return;
    }

    let redDot = Math.max(0, geral - 20);
    let mira2x = Math.max(0, geral - 30);
    let mira4x = Math.max(0, geral - 40);
    let awm = Math.max(0, geral - 50);

    let texto = 
    "Geral: " + geral +
    " | Red Dot: " + redDot +
    " | 2x: " + mira2x +
    " | 4x: " + mira4x +
    " | AWM: " + awm;

    document.getElementById("resultado").innerText = texto;
}

function copiar(){
    let texto = document.getElementById("resultado").innerText;

    if(texto === ""){
        alert("Gere a sensibilidade primeiro!");
        return;
    }

    navigator.clipboard.writeText(texto);
    alert("Sensibilidade copiada!");
}
</script>

</body>
</html>
