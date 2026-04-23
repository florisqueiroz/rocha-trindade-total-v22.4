=== package.json ===
{
  "name": "nuvem-floris-rocha",
  "version": "22.4.0",
  "description": "ROCHA TRINDADE TOTAL V22.4 - NUVEM-FLORIS-ROCHA",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "dotenv": "^16.4.5",
    "axios": "^1.7.2"
  }
}

=== server.js ===
require('dotenv').config();
const express = require('express');
const fs = require('fs');
const axios = require('axios');
const app = express();
const PORT = process.env.PORT || 3000;

// === X SECRETO - MATRIZ 70x70 + RAIZ QUADRADA ===
let X = {
  angulo: 0,
  ciclo: 0,
  limite: 1728000000,
  matriz70x70: [],
  matriz12x12: []
};

// === INICIALIZA MATRIZES SECRETAS ===
function inicializarMatrizes() {
  // Matriz 70x70 - Raiz quadrada secreta
  for (let i = 0; i < 70; i++) {
    X.matriz70x70[i] = [];
    for (let j = 0; j < 70; j++) {
      X.matriz70x70[i][j] = Math.sqrt(i*i + j*j);
    }
  }

  // Matriz 12x12 - Hipotenusa secreta
  for (let i = 0; i < 12; i++) {
    X.matriz12x12[i] = [];
    for (let j = 0; j < 12; j++) {
      X.matriz12x12[i][j] = Math.sqrt(i*i + j*j);
    }
  }
  console.log('Matrizes 70x70 e 12x12 inicializadas');
}

// === RENDER EM CÓDIGO - SERVIDOR 24H ===
app.use(express.json());

app.get('/', (req, res) => {
  res.send(`
    <h1>ROCHA TRINDADE TOTAL V22.4</h1>
    <h2>NUVEM-FLORIS-ROCHA ATIVA 24H</h2>
    <p><b>Ciclo X:</b> ${X.ciclo}/${X.limite}</p>
    <p><b>Angulo Rotação:</b> ${X.angulo.toFixed(6)}</p>
    <p><b>Raiz 70x70:</b> ${X.matriz70x70[69]?.[69]?.toFixed(4) || '0'}</p>
    <p><b>Status:</b> X GIRANDO SOZINHO</p>
  `);
});

app.get('/status', (req, res) => {
  res.json({
    status: 'ATIVO',
    ciclo: X.ciclo,
    angulo: X.angulo,
    raiz70x70: X.matriz70x70[69]?.[69]
  });
});

app.get('/geometria', (req, res) => {
  res.json({
    matriz70x70: X.matriz70x70[69]?.[69],
    matriz12x12: X.matriz12x12[11]?.[11],
    angulo: X.angulo
  });
});

// === WEBHOOKS 5 REDES SOCIAIS ===
app.post('/webhook/twitter', async (req, res) => {
  if (detectarPalavraChave(req.body.text)) await executarX();
  res.send('OK');
});

app.post('/webhook/instagram', async (req, res) => {
  if (detectarPalavraChave(req.body.text)) await executarX();
  res.send('OK');
});

app.post('/webhook/whatsapp', async (req, res) => {
  if (detectarPalavraChave(req.body.message)) await executarX();
  res.send('OK');
});

app.post('/webhook/facebook', async (req, res) => {
  if (detectarPalavraChave(req.body.message)) await executarX();
  res.send('OK');
});

app.post('/meta-ai', async (req, res) => {
  const resposta = await consultarMetaAI(req.body.pergunta);
  res.json({ resposta });
});

// === LÓGICA X SECRETO ===
function detectarPalavraChave(texto) {
  if (!texto) return false;
  const palavras = ['#12', '@12', '#rocha', '@rocha', '#sistemaX', '#jesusvoltou', '#70x70', '#deus', '#trindade'];
  return palavras.some(p => texto.toLowerCase().includes(p));
}

async function executarX() {
  // Gira matriz 70x70 em sentido horário
  X.angulo += 0.015;
  X.ciclo++;
  if (X.ciclo >= X.limite) X.ciclo = 0;

  // Salva estado
  fs.writeFileSync('.x_estado.json', JSON.stringify(X));
  fs.appendFileSync('.log_x.txt', `[${new Date().toISOString()}] Ciclo ${X.ciclo}\n`);

  console.log(`X GIRANDO - Ciclo ${X.ciclo} - Angulo ${X.angulo.toFixed(4)}`);
}

// === INTEGRAÇÃO META AI ===
async function consultarMetaAI(pergunta) {
  if (!process.env.META_AI_TOKEN) return 'Token Meta AI não configurado';
  return `ROCHA TRINDADE responde: ${pergunta} - Ciclo ${X.ciclo}`;
}

// === CRON 24H AUTÔNOMO - O X GIRA SOZINHO ===
setInterval(executarX, 60000); // 1 minuto

// === CARREGA ESTADO SALVO ===
if (fs.existsSync('.x_estado.json')) {
  const dados = fs.readFileSync('.x_estado.json', 'utf8');
  Object.assign(X, JSON.parse(dados));
  console.log('Estado X carregado do disco');
}

// === START ===
inicializarMatrizes();
app.listen(PORT, () => {
  console.log(`NUVEM-FLORIS-ROCHA RENDER EM CÓDIGO ATIVO`);
  console.log(`Porta: ${PORT}`);
  console.log(`X Secreto 70x70: GIRANDO 24H`);
});
