# Wall-street-casino
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wall Street Casino</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body class="dark-theme">
    <header>
        <h1>Wall Street Casino</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#games">Jogos</a></li>
                <li><a href="#depositos">Depósitos</a></li>
                <li><a href="#saques">Saques</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="home">
            <h2>Bem-vindo ao Wall Street Casino</h2>
            <p>Experimente os melhores jogos de cassino, com segurança e pagamentos rápidos via Pix.</p>
        </section>

        <section id="games">
            <h2>Jogos Disponíveis</h2>
            <div id="roleta">
                <h3>Roleta</h3>
                <button onclick="jogarRoleta()">Jogar Roleta</button>
                <p id="resultadoRoleta"></p>
            </div>
            <div id="tigrinho">
                <h3>Tigrinho</h3>
                <button onclick="jogarTigrinho()">Jogar Tigrinho</button>
                <p id="resultadoTigrinho"></p>
            </div>
            <div id="aviao">
                <h3>Aviãozinho</h3>
                <button onclick="jogarAviao()">Jogar Aviãozinho</button>
                <p id="resultadoAviao"></p>
            </div>
            <div id="blackjack">
                <h3>Blackjack</h3>
                <button onclick="jogarBlackjack()">Jogar Blackjack</button>
                <p id="resultadoBlackjack"></p>
            </div>
        </section>

        <section id="depositos">
            <h2>Faça seu Depósito</h2>
            <button id="depositBtn">Depositar com Pix</button>
        </section>

        <section id="saques">
            <h2>Saques</h2>
            <button id="withdrawBtn">Retirar Dinheiro</button>
        </section>
    </main>

    <footer>
        <p>&copy; 2025 Wall Street Casino</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>body {
    font-family: Arial, sans-serif;
    background-color: #1c1c1c;
    color: #fff;
    margin: 0;
    padding: 0;
}

header {
    background-color: #000;
    padding: 10px;
    text-align: center;
}

header h1 {
    color: #FFD700;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 10px;
}

nav ul li a {
    text-decoration: none;
    color: #FFD700;
}

section {
    padding: 20px;
    margin: 10px;
}

button {
    background-color: #FFD700;
    color: #000;
    padding: 10px;
    border: none;
    cursor: pointer;
}

button:hover {
    background-color: #ccac00;
}// Função para a Roleta
function roleta() {
    const numeros = [
        0, 32, 15, 19, 4, 21, 2, 25, 17, 34, 6, 27, 13, 36, 11, 30, 8, 23, 10, 5, 24, 16, 33, 1,
        20, 14, 31, 9, 22, 18, 29, 7, 28, 12, 35, 3, 26, 0
    ];
    const resultado = numeros[Math.floor(Math.random() * numeros.length)];
    return resultado;
}

// Função para Tigrinho
function tigrinho() {
    const animais = [
        'Avestruz', 'Águia', 'Búfalo', 'Burro', 'Cavalo', 'Camelo', 'Leão', 'Elefante', 'Galo', 'Gato', 
        'Cachorro', 'Jacaré', 'Cavalo', 'Tigre', 'Urso', 'Veado', 'Lobo', 'Cobra', 'Sapo', 'Arara', 'Mico', 
        'Pantera', 'Zebra', 'Elefante', 'Cavalo'
    ];
    const resultado = animais[Math.floor(Math.random() * animais.length)];
    return resultado;
}

// Função para Aviãozinho
function aviao() {
    const multiplicador = Math.random() * (10 - 1) + 1;  // Multiplicador entre 1 e 10
    const tempoDeVoo = Math.random() * 10 + 1;  // Tempo entre 1 e 10 segundos
    return {
        multiplicador: multiplicador,
        tempoDeVoo: tempoDeVoo
    };
}

// Função para Blackjack
function blackjack() {
    const cartas = [
        { nome: "2", valor: 2 }, { nome: "3", valor: 3 }, { nome: "4", valor: 4 }, { nome: "5", valor: 5 },
        { nome: "6", valor: 6 }, { nome: "7", valor: 7 }, { nome: "8", valor: 8 }, { nome: "9", valor: 9 },
        { nome: "10", valor: 10 }, { nome: "J", valor: 10 }, { nome: "Q", valor: 10 }, { nome: "K", valor: 10 },
        { nome: "A", valor: 11 }
    ];

    function sortearCarta() {
        return cartas[Math.floor(Math.random() * cartas.length)];
    }

    function calcularSoma(cartas) {
        let soma = 0;
        let ases = 0;

        cartas.forEach(carta => {
            soma += carta.valor;
            if (carta.nome === "A") ases++;
        });

        while (soma > 21 && ases > 0) {
            soma -= 10;
            ases--;
        }

        return soma;
    }

    let cartasJogador = [sortearCarta(), sortearCarta()];
    let cartasDealer = [sortearCarta(), sortearCarta()];

    let somaJogador = calcularSoma(cartasJogador);
    let somaDealer = calcularSoma(cartasDealer);

    return {
        cartasJogador: cartasJogador,
        cartasDealer: cartasDealer,
        somaJogador: somaJogador,
        somaDealer: somaDealer
    };
}

// Funções para exibir resultados na interface
function jogarRoleta() {
    const numeroGiro = roleta();
    document.getElementById("resultadoRoleta").innerText = `A roleta parou no número: ${numeroGiro}`;
}

function jogarTigrinho() {
    const animalSorteado = tigrinho();
    document.getElementById("resultadoTigrinho").innerText = `O animal sorteado foi: ${animalSorteado}`;
}

function jogarAviao() {
    const voo = aviao();
    document.getElementById("resultadoAviao").innerText = `O avião voou por ${voo.tempoDeVoo.toFixed(2)} segundos com um multiplicador de ${voo.multiplicador.toFixed(2)}x.`;
}

function jogarBlackjack() {
    const jogoBlackjack = blackjack();
    document.getElementById("resultadoBlackjack").innerText = `
        Cartas do jogador: ${jogoBlackjack.cartasJogador.map(c => c.nome).join(", ")} - Soma: ${jogoBlackjack.somaJogador}
        Cartas do dealer: ${jogoBlackjack.cartasDealer.map(c => c.nome).join(", ")} - Soma: ${jogoBlackjack.somaDealer}
    `;
}const express = require('express');
const bodyParser = require('body-parser');
const app = express();
const port = 3000;

// Middleware
app.use(bodyParser.json());
app.use(express.static('public'));

// Usuário simples para exemplo
let users = [
    { username: "admin", password: "milionario2031" }
];

// Rota de login
app.post('/login', (req, res) => {
    const { username, password } = req.body;
    const user = users.find(u => u.username === username && u.password === password);

    if (user) {
        res.json({ message: "Login bem-sucedido!" });
    } else {
        res.status(401).json({ message: "Credenciais inválidas!" });
    }
});

// Rota de pagamento via Pix (simulada)
app.post('/payment', (req, res) => {
    const { amount, paymentMethod } = req.body;

    if (paymentMethod === 'pix') {
        res.json({ message: `Pagamento de R$${amount} realizado via Pix!` });
    } else {
        res.status(400).json({ message: 'Método de pagamento inválido.' });
    }
});

// Iniciar o servidor
app.listen(port, () => {
    console.log(`Servidor rodando em http://localhost:${port}`);
});
