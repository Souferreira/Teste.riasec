# Teste.ancora
Este é um teste interativo sobre Âncoras de Carreira, composto por 40 perguntas que avaliam preferências profissionais e prioridades pessoais. Após responder, os resultados são apresentados em um gráfico de barras, destacando categorias como autonomia, segurança e criatividade, com opção de download em PDF.
qui está a estrutura do seu projeto com os arquivos necessários e o código para que o site funcione no GitHub Pages:

Estrutura do Projeto
scss
Copiar código
carreira-ancoras/
├── assets/
│   └── (coloque imagens ou ícones aqui, se necessário)
├── index.html
└── styles.css
Passo 1: Código HTML (index.html)
html
Copiar código
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teste: Âncoras de Carreira</title>
    <link rel="stylesheet" href="styles.css"> <!-- Referência ao arquivo CSS -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
</head>
<body>
<div class="container">
    <header>
        <h1>Teste: Âncoras de Carreira</h1>
    </header>
    <form id="career-anchors-form">
        <p>Leia atentamente as questões abaixo e clique na resposta que mais se aplica a você, em cada uma das afirmativas.</p>
        <div class="questions"></div>
        <button type="button" id="calculate-btn">Ver resultado</button>
        <div class="error-message" id="error-message"></div>
        <button type="button" id="download-pdf" style="display:none;">Baixar PDF</button>
    </form>
    <div class="results">
        <canvas id="career-anchors-chart"></canvas>
    </div>
</div>

<script>
// Coloque aqui o código JavaScript para funcionalidade
document.getElementById("calculate-btn").addEventListener("click", function() {
    // Exemplo simples de exibição de resultado
    alert("Calculando resultado...");
});

// Mais funções JavaScript podem ser adicionadas aqui
</script>
</body>
</html>
Passo 2: Código CSS (styles.css)
css
Copiar código
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
    line-height: 1.6;
}

.container {
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

header {
    text-align: center;
    margin-bottom: 20px;
}

h1 {
    font-size: 2em;
    color: #2c3e50;
}

form {
    display: flex;
    flex-direction: column;
}

form p {
    font-size: 1.1em;
    margin-bottom: 10px;
}

button {
    padding: 10px;
    margin-top: 10px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #2980b9;
}

.results {
    margin-top: 20px;
}

@media (max-width: 768px) {
    .container {
        width: 95%;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 1.5em;
    }
}
Passo 3: Subir os Arquivos para o GitHub
Crie o Repositório no GitHub:

Acesse o GitHub, crie um novo repositório com o nome carreira-ancoras.
Clone o Repositório no Seu Computador: Abra o terminal e execute:

bash
Copiar código
git clone https://github.com/seu-usuario/carreira-ancoras.git
Adicione os Arquivos: Copie os arquivos index.html, styles.css e a pasta assets (se necessário) para o diretório do repositório local.

Faça o Commit e Push: No terminal, dentro da pasta do repositório clonado, execute os seguintes comandos:

bash
Copiar código
git add .
git commit -m "Adicionando código inicial do teste Âncoras de Carreira"
git push origin main
Passo 4: Configurar o GitHub Pages
Ativar GitHub Pages:
Vá para a página do seu repositório no GitHub.
Clique na aba Settings.
No menu lateral, encontre a seção Pages.
Em Source, selecione a branch main e clique em Save.
O GitHub Pages gerará um link para acessar o seu site.
Passo 5: Testar
Acesse o link gerado pelo GitHub Pages, como por exemplo:

arduino
Copiar código
https://seu-usuario.github.io/carreira-ancoras/
Agora, seu projeto estará online, e as pessoas poderão interagir com o teste diretamente!
