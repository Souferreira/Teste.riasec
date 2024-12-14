# Teste.ancora
Este é um teste interativo sobre Âncoras de Carreira, composto por 40 perguntas que avaliam preferências profissionais e prioridades pessoais. Após responder, os resultados são apresentados em um gráfico de barras, destacando categorias como autonomia, segurança e criatividade, com opção de download em PDF.
qui está a estrutura do seu projeto com os arquivos necessários e o código para que o site funcione no GitHub Pages:

##Estrutura do Projeto

```plaintext
carreira-ancoras/
├── assets/
│   └── index.html
├── styles.css
└── script.js
```

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Teste: Âncoras de Carreira</title>
    <link rel="stylesheet" href="styles.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
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
            padding: 10px;
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
        table th, table td {
            border: 2px solid #e1d9d9;
            background: linear-gradient(90deg, #edeef0, #93afe6, #467cdf);
            padding: 1px;
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
    border-radius: 15px;
    cursor: pointer;
    font-size: 13px;
    transition: background-color 0.3s, transform 0.3s;
}

button:hover {
    background: linear-gradient(90deg, #bbc8b8, #82d755, #3deb11);
    transform: scale(1.1);
}

.error-message {
    color: rgb(234, 11, 11);
    margin-top: 10px;
}

/* Responsividade */
@media (max-width: 768px) {
    .container {
        max-width: 100%;
        padding: 20px;
    }

    .questions {
        flex-direction: column;
        gap: 15px;
    }

    .question {
        padding: 10px;
    }

    .circle {
        width: 35px;
        height: 35px;
        font-size: 16px;
    }

    button {
        padding: 8px 16px;
        font-size: 18px;
    }

    table th, table td {
        font-size: 14px;
        padding: 5px;
    }
}

@media (max-width: 480px) {
    h1 {
        font-size: 24px;
    }

    .question {
        padding: 8px;
    }

    .circle {
        width: 30px;
        height: 30px;
        font-size: 14px;
    }

    button {
        padding: 6px 12px;
        font-size: 16px;
    }

    table th, table td {
        font-size: 12px;
        padding: 4px;
    }
}
</style>
</head>
<body>
<div class="container">
<h1>Teste: Âncoras de Carreira</h1>
<form id="career-anchors-form">
    <p>Leia atentamente as questões abaixo e clique na resposta que mais se aplica a você, em cada uma das afirmativas.</p>
    <div class="questions">
        <div class="question">
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
const questions = [
    { question: "1. Sonho em ser tão bom no que faço que minha opinião de especialista seja sempre solicitada.", category: "COMPETÊNCIA TÉCNICA" },
    { question: "2. Me sinto mais realizado em meu trabalho quando sou capaz de integrar e gerenciar o trabalho dos outros.", category: "COMPETÊNCIA ADMINISTRATIVA" },
    { question: "3. Sonho em ter uma carreira que me dê a liberdade de fazer o trabalho do meu jeito e no tempo por mim programado.", category: "AUTONOMIA" },
    { question: "4. Segurança e estabilidade são mais importantes para mim do que liberdade e autonomia.", category: "SEGURANÇA" },
    { question: "5. Estou sempre procurando ideias que me permitam iniciar meu próprio negócio.", category: "CRIATIVIDADE EMPREENDEDORA" },
    { question: "6. Sentirei sucesso na minha carreira se sentir que contribuí verdadeiramente para o bem-estar da sociedade.", category: "DEDICAÇÃO A UMA CAUSA" },
    { question: "7. Sonho com uma carreira na qual eu possa solucionar problemas ou vencer em situações extremamente desafiadoras.", category: "DESAFIO PURO" },
    { question: "8. Prefiro deixar meu emprego a ser colocado em um trabalho que comprometa minha capacidade de satisfazer meus interesses pessoais e familiares.", category: "ESTILO DE VIDA" },
    { question: "9. Só me sentirei bem-sucedido em minha carreira se puder desenvolver minhas habilidades técnicas e funcionais até o mais alto nível de competência.", category: "COMPETÊNCIA TÉCNICA" },
    { question: "10. Sonho em dirigir uma organização complexa e tomar decisões que afetem muitas pessoas.", category: "COMPETÊNCIA ADMINISTRATIVA" },
    { question: "11. Me sinto mais realizado em meu trabalho quando tenho total liberdade de definir minhas próprias tarefas, horários e procedimentos.", category: "AUTONOMIA" },
    { question: "12. Prefiro manter minha atividade atual a aceitar outra tarefa que possa colocar em risco minha segurança na empresa.", category: "SEGURANÇA" },
    { question: "13. Montar meu próprio negócio é mais importante para mim do que atingir uma alta posição gerencial como funcionário.", category: "CRIATIVIDADE EMPREENDEDORA" },
    { question: "14. Me sinto mais realizado em minha carreira quando posso utilizar meus talentos a serviço dos outros.", category: "DEDICAÇÃO A UMA CAUSA" },
    { question: "15. Me sinto realizado em minha carreira apenas quando enfrento e supero desafios extremamente difíceis.", category: "DESAFIO PURO" },
    { question: "16. Sonho com uma carreira que me permita integrar minhas necessidades pessoais, familiares e de trabalho.", category: "ESTILO DE VIDA" },
    { question: "17. Me tornar um gerente técnico em minha área de especialização é mais atraente para mim do que me tornar um gerente geral em alguma organização.", category: "COMPETÊNCIA TÉCNICA" },
    { question: "18. Me sentirei bem-sucedido em minha carreira apenas quando me tornar um gerente geral em alguma organização.", category: "COMPETÊNCIA ADMINISTRATIVA" },
    { question: "19. Me sentirei bem-sucedido em minha carreira apenas quando alcançar total autonomia e liberdade.", category: "AUTONOMIA" },
    { question: "20. Procuro trabalhos em organizações que me deem senso de segurança e estabilidade.", category: "SEGURANÇA" },
    { question: "21. Me sinto realizado em minha carreira quando sou capaz de construir alguma coisa que seja inteiramente resultado de minhas ideias e esforços.", category: "CRIATIVIDADE EMPREENDEDORA" },
    { question: "22. Utilizar minhas habilidades para tornar o mundo um lugar melhor para se viver e trabalhar é mais importante para mim do que alcançar uma posição gerencial de alto nível.", category: "DEDICAÇÃO A UMA CAUSA" },
    { question: "23. Me sinto bem-sucedido na vida apenas quando sou capaz de equilibrar minhas necessidades pessoais, familiares e de carreira.", category: "ESTILO DE VIDA" },
    { question: "24. Prefiro sair da empresa onde estou a aceitar uma tarefa em esquema rotativo que me afaste da minha área de experiência.", category: "SEGURANÇA" },
    { question: "25. Me tornar um diretor geral é mais atraente para mim do que me tornar um diretor técnico em minha área de especialização.", category: "COMPETÊNCIA ADMINISTRATIVA" },
    { question: "26. Para mim, poder fazer um trabalho do meu jeito, livre de regras e restrições, é mais importante do que segurança.", category: "AUTONOMIA" },
    { question: "27. Me sinto mais realizado em meu trabalho quando percebo que tenho total segurança financeira e estabilidade no trabalho.", category: "SEGURANÇA" },
    { question: "28. Me sinto bem-sucedido em meu trabalho apenas quando posso criar ou construir alguma coisa que seja inteiramente de minha autoria.", category: "CRIATIVIDADE EMPREENDEDORA" },
    { question: "29. Sonho em ter uma carreira que faça uma real contribuição à humanidade e à sociedade.", category: "DEDICAÇÃO A UMA CAUSA" },
    { question: "30. Procuro oportunidades de trabalho que desafiem fortemente minhas habilidades para solucionar problemas.", category: "DESAFIO PURO" },
    { question: "31. Equilibrar as exigências da minha vida pessoal e profissional é mais importante do que alcançar alta posição gerencial.", category: "ESTILO DE VIDA" },
    { question: "32. Me sinto plenamente realizado em meu trabalho quando sou capaz de empregar minhas habilidades e talentos especiais.", category: "COMPETÊNCIA TÉCNICA" },
    { question: "33. Prefiro sair da empresa onde estou a aceitar um cargo que me afaste do caminho da diretoria geral.", category: "SEGURANÇA" },
    { question: "34. Prefiro sair da empresa onde estou a aceitar um cargo que reduza minha autonomia e liberdade.", category: "AUTONOMIA" },
    { question: "35. Sonho em ter uma carreira que me dê senso de segurança e estabilidade.", category: "SEGURANÇA" },
    { question: "36. Sonho em iniciar e montar meu próprio negócio.", category: "CRIATIVIDADE EMPREENDEDORA" },
    { question: "37. Prefiro sair da empresa onde estou a aceitar um cargo que prejudique minha capacidade de ser útil aos outros.", category: "DEDICAÇÃO A UMA CAUSA" },
    { question: "38. Trabalhar em problemas praticamente insolúveis para mim é mais importante do que alcançar uma posição gerencial de alto nível.", category: "DESAFIO PURO" },
    { question: "39. Sempre procurei oportunidades de trabalho que minimizassem interferências com assuntos pessoais e familiares.", category: "ESTILO DE VIDA" },
    { question: "40. Me sinto mais realizado em meu trabalho quando posso ajudar outras pessoas a alcançarem seus objetivos.", category: "DEDICAÇÃO A UMA CAUSA" }
        ];

        const form = document.getElementById('career-anchors-form');
        const errorMessage = document.getElementById('error-message');
        const downloadButton = document.getElementById('download-pdf');
        const chartContainer = document.querySelector('.results');
        const chartCanvas = document.getElementById('career-anchors-chart');
        let answers = {};

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
                        ${[1, 2, 3, 4, 5].map(value => `
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

        function generateChart() {
            const categories = Object.keys(answers);
            const data = categories.map(category => answers[category]);

            new Chart(chartCanvas, {
                type: 'bar',
                data: {
                    labels: categories,
                    datasets: [{
                        label: 'Pontuação por categoria',
                        data: data,
                        backgroundColor: ['#ff6384', '#36a2eb', '#cc65fe', '#ffce56', '#ffbb33', '#2d8e3f', '#e745d3'],
                        borderColor: '#ffffff',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    scales: {
                        y: {
                            beginAtZero: true,
                            max: Math.max(...data) + 10
                        }
                    }
                }
            });
        }

        downloadButton.addEventListener('click', () => {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            doc.text('Resultado do Teste: Âncoras de Carreira', 20, 10);
            doc.text('Pontuação por categoria:', 20, 20);
            Object.entries(answers).forEach(([category, score], index) => {
                doc.text(`${category}: ${score}`, 20, 30 + (index * 10));
            });
            doc.save('resultado_ancoras_carreira.pdf');
        });
    </script>
</body>
</html>
```
