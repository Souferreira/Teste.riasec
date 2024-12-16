# Teste Vocacional Riasec
Este é um teste interativo sobre Âncoras de Carreira, composto por 40 perguntas que avaliam preferências profissionais e prioridades pessoais. Após responder, os resultados são apresentados em um gráfico de barras, destacando categorias como autonomia, segurança e criatividade, com opção de download em PDF.
qui está a estrutura do seu projeto com os arquivos necessários e o código para que o site funcione no GitHub Pages:


```
Teste vocaional

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teste: Âncoras de Carreira</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.4.0/jspdf.umd.min.js"></script>
    <style>
        /* Estilos globais */
        body {
            font-family: Arial, sans-serif;
            margin: 0px;
            padding: 0px;
            background-color: #fdfdfe;
            color: #000000;
        }

        .container {
            max-width: 900px;
            margin: 15px auto;
            padding: 15px;
            background: linear-gradient(90deg, #eceded, #ced1d8, #aeb6c4);
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(184, 163, 163, 0.1);
        }

        header {
            background-color: #e1d6d6;
            color: #de5252;
            padding: 15px 0;
            text-align: center;
        }

        h1 {
            background: linear-gradient(90deg, #edeef0, #c0cbe1, #839ac5);
            border: 5px solid #8d7fd5;
            border-radius: 30px;
            padding: 15px;
            transition: background-color 0.3s ease, transform 0.3s ease;
            text-align: center;
            color: #100909;
        }
        h1:hover {
            background: linear-gradient(90deg, #88afb5, #9ec7d7, #26a5db);
            transform: scale(1.05);
        }
        p {
            background: linear-gradient(90deg, #edeef0, #c0cbe1, #839ac5);
            border: 5px solid #8d7fd5;
            border-radius: 30px;
            padding: 10px;
            transition: background-color 0.3s ease, transform 0.3s ease;
            text-align: center;
            color: #100909;
        }
        p:hover {
            background: linear-gradient(90deg, #88afb5, #9ec7d7, #26a5db);
            transform: scale(1.05);
        }

        
         th, table td {
            border: 2px solid #e1d9d9;
            background: linear-gradient(90deg, #edeef0, #93afe6, #467cdf);
            padding: 10px;
            border-radius: 10px;
            text-align: center;
        }
        table th, table td:hover {
            background: linear-gradient(90deg, #88afb5, #9ec7d7, #26a5db);
            transform: scale(1.05);
          
        }
        /* Layout da lista de perguntas */
        .questions {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .question {
            background-color: #f7f7f7;
            border: 5px solid #8d7fd5;
            border-radius: 30px;
            padding: 15px;
            transition: background-color 0.3s ease, transform 0.3s ease;
            text-align: center;
        }

        .question:hover {
            background: linear-gradient(90deg, #88afb5, #9ec7d7, #26a5db);
            transform: scale(1.05);
        }

        .question input[type="radio"] {
            display: none;
        }

        .question label {
            display: inline-block;
            margin-right: 15px;
            cursor: pointer;
            text-align: center;
        }

        .circle {
            width: 40px;
            height: 40px;
            border-radius: 100%;
            background-color: #9b59b6;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            transition: background-color 0.3s;
        }

        .circle:hover {
            background-color: #ffbb33
        }

.question input[type="radio"]:checked + label .circle {
    background-color: #18b63a;
    color: #fff;
}

/* Estilos de formulário */
form {
    display: flex;
    flex-direction: column;
    gap: 30px;
    text-align: center;
}

button {
    padding: 10px 20px;
    background: linear-gradient(90deg, #c2aea6, #bf4444, #ed410c);
    color: rgb(248, 241, 241);
    border: none;
    padding: 10px 20px; 
    border-radius: 15px;
    cursor: pointer;
    font-size: 16px;
    font-weight: bold;
    transition: background-color 0.3s, transform 0.10s;
}

button:hover {
    background: linear-gradient(90deg, #bbc8b8, #82d755, #3deb11);
    transform: scale(1.1);
}


.error-message {
    color: rgb(234, 11, 11);
    margin-top: 10px;
}

/* Responsividade para dispositivos maiores */

@media (max-width: 320px) {
    h1 {
        font-size: 20px;
        text-align: center;
    }

    .container {
        padding: 10px;
    }

    .circle {
        width: 25px;
        height: 25px;
        font-size: 12px;
    }

    button {
        padding: 4px 10px;
        font-size: 14px;
    }

    table th, table td {
        font-size: 10px;
        padding: 2px;
    }
}

/* Responsividade para imagens */
img {
    max-width: 100%;
    height: auto;
}

/* Responsividade para navegação */
@media (max-width: 768px) {
    .navbar {
        flex-direction: column;
        align-items: center;
    }

    .navbar a {
        padding: 10px;
        font-size: 16px;
    }

    table-container {
        overflow-x: auto; /* Permite rolagem horizontal */
        -webkit-overflow-scrolling: touch; /* Suaviza a rolagem em dispositivos móveis */
    }

    table {
        display: block; /* Transforma a tabela em um elemento rolável */
        overflow-x: auto; /* Adiciona barra de rolagem horizontal */
    }


    table th, table td {
        font-size: 12px; /* Reduz o tamanho da fonte */
        padding: 5px; /* Ajusta o espaçamento */
        word-wrap: break-word; /* Quebra o texto longo para evitar estouro */
    }
}

@media (max-width: 768px) {
    button {
        width: 100%; /* Botão ocupa toda a largura */
        font-size: 14px; /* Tamanho do texto reduzido */
        padding: 12px; /* Mais espaçamento interno */
    }
}
/* Responsividade para formulários */
@media (max-width: 480px) {
    form input, form textarea {
        width: 100%;
        font-size: 14px;
    }

    form button {
        width: 100%;
        padding: 10px;
    }
}

/* Ocultar elementos irrelevantes em telas pequenas */
@media (max-width: 768px) {
    .sidebar {
        display: none;
    }
}

/* Responsividade para textos longos */
@media (max-width: 480px) {
    p, span {
        font-size: 12px;
        line-height: 1.4;
    }
   Table th, table td {
        font-size: 11px;
        padding: 4px;
    }

    table {
        min-width: 100%; /* Garante que ela sempre seja visível */
    }
}

</style>
</head>
<body>
<div class="container">
<h1>Teste Vocacional RIASEC</h1>
<form id="career-anchors-form">
    <p>Leia atentamente as questões abaixo e clique na resposta que mais se aplica a você, em cada uma das afirmativas.</p>
    <table>
                    <tr>
                        <th>1</th>
                        <th>2</th>
                        <th>3</th>
                        <th>4</th>
                        <th>5</th>
                        <th>6</th>
                        <th>7</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Me desagrada muito</td>
                        <td>Me desagrada bastante</td>
                        <td>Me desagrada um pouco</td>
                        <td>Não me agrada nem me desagrada</td>
                        <td>Me agrada um pouco</td>
                        <td>Me agrada bastante</td>
                        <td>Me agrada muito</td>
                    </tr>
                </tbody>
            </table>
            <p>Responda cada pergunta com uma nota de 1 (Me desagrada muito) a 7 (Me agrada muito).</p>
    <div class="questions">
        </div>
    </div>
    <button type="button" id="calculate-btn">Ver resultado</button>
    <div class="error-message" id="error-message"></div>
    <button type="button" id="download-pdf" style="display:none;">Baixar PDF</button>
</form>
<div class="results">
    <canvas id="career-anchors-chart"></canvas>
</div>
</div>

<script>
    document.addEventListener('DOMContentLoaded', function() {
        const form = document.getElementById('career-anchors-form');
        const errorMessage = document.getElementById('error-message');
        const downloadButton = document.getElementById('download-pdf');
        const chartContainer = document.querySelector('.results');
        const chartCanvas = document.getElementById('career-anchors-chart');
        let answers = {};
    
        // Defina as questões corretamente
        const questions = [
            { question: "1-Trabalhar com ferramentas ou máquinas", category: "REALISTA" },
            { question: "2-Realizar pesquisas", category: "INVESTIGATIVO" },
            { question: "3-Desenhar ou pintar quadros", category: "ARTÍSTICO" },
            { question: "4-Trabalhar com pessoas que necessitem auxílio", category: "SOCIAL" },
            { question: "5-Investir em um negócio promissor de alto risco", category: "EMPREENDEDOR" },
            { question: "6-Controlar estoques em uma loja ou empresa", category: "CONVENCIONAL" },
            { question: "7-Montar aparelhos ou objetos", category: "REALISTA" },
             { question: "8-Estudar o modo de viver em outras culturas", category: "INVESTIGATIVO" },
                { question: "9-Fazer trabalhos que requeiram expressão das emoções", category: "ARTÍSTICO" },
                { question: "10-Desenvolver trabalhos voluntários", category: "SOCIAL" },
                { question: "11-Desempenhar tarefas em que possa comandar um grupo de pessoas", category: "EMPREENDEDOR" },
                { question: "12-Lidar com papéis em um escritório", category: "CONVENCIONAL" },
                { question: "13-Construir ou reformar coisas", category: "REALISTA" },
                { question: "14-Buscar explicações para fenômenos naturais ou sociais", category: "INVESTIGATIVO" },
                { question: "15-Criar propagandas para TV ou jornal", category: "ARTÍSTICO" },
                { question: "16-Trabalhar para promover o bem-estar das pessoas", category: "SOCIAL" },
                { question: "17-Tentar convencer as pessoas sobre alguma coisa ou ideia", category: "EMPREENDEDOR" },
                { question: "18-Organizar agenda de pessoas", category: "CONVENCIONAL" },
                { question: "19-Fazer coisas que requeiram uso de instrumento e habilidades mecânicas", category: "REALISTA" },
                { question: "20-Estudar origens do universo", category: "INVESTIGATIVO" },
                { question: "21-Trabalhar com fotografia e vídeo", category: "ARTÍSTICO" },
                { question: "22-Cuidar de pessoas", category: "SOCIAL" },
                { question: "23-Fazer coisas que exijam argumentação e debate", category: "EMPREENDEDOR" },
                { question: "24-Trabalhar com números e registros de maneira ordenada", category: "CONVENCIONAL" },
                { question: "25-Construir coisas que sejam úteis para o dia a dia", category: "REALISTA" },
                { question: "26-Descobrir como funciona a mente humana", category: "INVESTIGATIVO" },
                { question: "27-Cantar ou tocar instrumentos musicais", category: "ARTÍSTICO" },
                { question: "28-Realizar atividades que possam ensinar algo aos outros", category: "SOCIAL" },
                { question: "29-Exercer cargos de liderança", category: "EMPREENDEDOR" },
                { question: "30-Executar tarefas rotineiras", category: "CONVENCIONAL" },
                { question: "31-Fazer trabalhos que exijam atividade física", category: "REALISTA" },
                { question: "32-Examinar as causas das mudanças que ocorrem na sociedade", category: "INVESTIGATIVO" },
                { question: "33-Produzir coisas bonitas para se ver ou assistir", category: "ARTÍSTICO" },
                { question: "34-Executar tarefas que exijam contato humano", category: "SOCIAL" },
                { question: "35-Lidar com atividades que exijam negociação", category: "EMPREENDEDOR" },
                { question: "36-Organizar arquivos", category: "CONVENCIONAL" },
                { question: "37-Fazer trabalhos manuais", category: "REALISTA" },
                { question: "38-Discutir temas científicos com outras pessoas", category: "INVESTIGATIVO" },
                { question: "39-Planejar a decoração de um ambiente", category: "ARTÍSTICO" },
                { question: "40-Trabalhar com orientação de pessoas, assistência física ou mental", category: "SOCIAL" },
                { question: "41-Gerenciar um negócio próprio", category: "EMPREENDEDOR" },
                { question: "42-Trabalhar no caixa de um banco ou loja", category: "CONVENCIONAL" },
                { question: "43-Consertar utensílios domésticos", category: "REALISTA" },
                { question: "44-Ler trabalhos de filósofos ou outros intelectuais", category: "INVESTIGATIVO" },
                { question: "45-Dirigir um filme ou peça de teatro", category: "ARTÍSTICO" },
                { question: "46-Realizar atividades que ajudem a sociedade de algum modo", category: "SOCIAL" },
                { question: "47-Fazer coisas que exijam ambição", category: "EMPREENDEDOR" },
                { question: "48-Seguir uma rotina no trabalho", category: "CONVENCIONAL" }
            
        ];
    
        // Gerar as questões
        function generateQuestions() {
            const questionsContainer = document.querySelector('.questions');
            questions.forEach((q, index) => {
                const questionElement = document.createElement('div');
                questionElement.classList.add('question');
                questionElement.innerHTML = `
                    <label for="question-${index}">
                        ${q.question}
                    </label>
                    <div class="options">
                    ${[1, 2, 3, 4, 5, 6, 7].map(value => `
                            <input type="radio" name="question-${index}" id="question-${index}-${value}" value="${value}" />
                            <label for="question-${index}-${value}">
                                <div class="circle">${value}</div>
                            </label>
                        `).join('')}
                    </div>
                `;
                questionsContainer.appendChild(questionElement);
            });
        }
    
        generateQuestions();
    
        // Calcular os resultados
        document.getElementById('calculate-btn').addEventListener('click', () => {
            let isValid = true;
            answers = {}; // Reset answers for each calculation
            questions.forEach((q, index) => {
                const selectedOption = form.querySelector(`input[name="question-${index}"]:checked`);
                if (!selectedOption) {
                    isValid = false;
                } else {
                    answers[q.category] = (answers[q.category] || 0) + parseInt(selectedOption.value);
                }
            });
    
            if (!isValid) {
                errorMessage.textContent = 'Por favor, responda todas as perguntas.';
                return;
            }
    
            errorMessage.textContent = '';
            generateChart();
            downloadButton.style.display = 'inline-block';
        });
    
        // Gerar gráfico
        function generateChart() {
    const categories = Object.keys(answers);
    const totalScore = Object.values(answers).reduce((a, b) => a + b, 0); // Soma total das pontuações
    const data = categories.map(category => answers[category]);
    const percentages = data.map(value => ((value / totalScore) * 100).toFixed(2)); // Cálculo em porcentagem
            
    new Chart(chartCanvas, {
        type: 'bar',
        data: {
            labels: categories,
            datasets: [{
                label: 'Pontuação (%) por categoria',
                data: percentages, // Usar porcentagens no gráfico
                backgroundColor: ['#ff6384', '#36a2eb', '#cc65fe', '#ffce56', '#ffbb33', '#2d8e3f', '#e745d3'],
                borderColor: '#ffffff',
                borderWidth: 1
            }]
        },
        options: {
            responsive: true,
            plugins: {
                tooltip: {
                    callbacks: {
                        label: (context) => `${context.raw}%` // Exibir porcentagem no tooltip
                    }
                }
            },
            scales: {
                y: {
                    beginAtZero: true,
                    max: 100 // Escala de 0 a 100%
                }
            }
        }
    });
}
    
        // Gerar PDF
        function generatePDF(scores) {
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF();
    doc.text("Resultado do Teste Vocacional RIASEC", 20, 20);
            
    
    // Detalhes do teste
            doc.setFontSize(12);
            let yPosition = 40;
            const totalScore = Object.values(scores).reduce((a, b) => a + b, 0); // Soma total das pontuações

            Object.entries(scores).forEach(([category, score]) => {
        const percentage = ((score / totalScore) * 100).toFixed(2); // Cálculo em porcentagem
        doc.text(`${category}: ${score} (${percentage}%)`, 20, yPosition);
        yPosition += 10;
    });
            // Adicionar gráfico como imagem no PDF
            const chartImage = chartCanvas.toDataURL("image/png");
            doc.addImage(chartImage, 'PNG', 20, yPosition, 170, 100); // Adicionando imagem do gráfico
    
            doc.save('resultado_ancoras_carreira.pdf');
        }
    
        // Adicionar evento ao botão de download
        downloadButton.addEventListener("click", () => {
            generatePDF(answers); // Gerar e baixar o PDF com o resultado
        });
    });
    </script>
</body>
</html>

