=== package.json ===
{
  "name": "nuvem-floris-rocha",
  "version": "22.4.0",
  "description": "ROCHA TRINDADE TOTAL V22.4 - NUVEM-FLORIS-ROCHA - 8 REDES 8 TANGENTES 8 HIPOTENUSAS",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "dotenv": "^16.4.5",
    "axios": "^1.7.2"
  },
  "devDependencies": {
    "nodemon": "^3.1.0"
  },
  "engines": {
    "node": ">=18.0.0"
  }
}

=== server.js ===
require('dotenv').config();
const express = require('express');
const fs = require('fs');
const axios = require('axios');
const app = express();
const PORT = process.env.PORT || 3000;

// === NÚCLEO X SECRETO - 8 REDES + 8 TANGENTES + 8 HIPOTENUSAS ===
const X = {
  angulo: 0,
  ciclo: 0,
  limite: 1728000000,
  matriz70x70: [],
  hipotenusas8x8: [],
  tangentes8x8: [],
  redes8: ['Twitter', 'Instagram', 'WhatsApp', 'Facebook', 'Meta AI', 'Telegram', 'YouTube', 'TikTok'],
  ultimasManifestacoes: [],
  startedAt: new Date().toISOString()
};

// === KEEPALIVE 24H - AUTO PING PARA NÃO DORMIR ===
setInterval(() => {
  if (process.env.RENDER_EXTERNAL_URL) {
    axios.get(process.env.RENDER_EXTERNAL_URL).catch(() => {});
    console.log('🔄 Keepalive ping enviado - 24H GARANTIDO');
  }
}, 840000); // 14min

// === INICIALIZA MATRIZES SECRETAS 8D ===
function inicializarMatrizes() {
  console.log('⚡ Inicializando Matriz 70x70 - Raiz Quadrada Secreta...');
  for (let i = 0; i < 70; i++) {
    X.matriz70x70[i] = [];
    for (let j = 0; j < 70; j++) {
      X.matriz70x70[i][j] = Math.sqrt(i*i + j*j);
    }
  }

  console.log('⚡ Inicializando 8 Hipotenusas Secretas...');
  for (let i = 0; i < 8; i++) {
    X.hipotenusas8x8[i] = [];
    for (let j = 0; j < 8; j++) {
      X.hipotenusas8x8[i][j] = Math.sqrt(i*i + j*j);
    }
  }

  console.log('⚡ Inicializando 8 Tangentes Secretas...');
  for (let i = 0; i < 8; i++) {
    X.tangentes8x8[i] = [];
    for (let j = 0; j < 8; j++) {
      X.tangentes8x8[i][j] = Math.tan((i + 1) * (j + 1) * Math.PI / 180);
    }
  }
  console.log('✅ NUCLEO 8D SELADO - 8 REDES ATIVAS');
}

// === MIDDLEWARE ===
app.use(express.json());

// === ROTAS PRINCIPAIS ===
app.get('/', (req, res) => {
  res.send(`
    <!DOCTYPE html>
    <html>
    <head>
      <title>ROCHA TRINDADE TOTAL V22.4 - 8D LIBERADO</title>
      <meta charset="UTF-8">
      <meta http-equiv="refresh" content="30">
      <style>
        body { background:#000; color:#0f0; font-family:monospace; padding:20px; }
        h1 { color:#0ff; text-shadow: 0 0 10px #0ff; animation: glow 2s infinite; }
        @keyframes glow { 0%, 100% { text-shadow: 0 0 10px #0ff; } 50% { text-shadow: 0 0 20px #0ff; } }
      .box { border:1px solid #0f0; padding:15px; margin:10px 0; border-radius:5px; }
      .active { color:#0ff; font-weight:bold; }
      .rede { display:inline-block; margin:5px 10px; padding:5px 10px; border:1px solid #0ff; border-radius:3px; }
      .uptime { color:#ff0; }
      </style>
    </head>
    <body>
      <h1>ROCHA TRINDADE TOTAL V22.4</h1>
      <h2>NUVEM-FLORIS-ROCHA ATIVA 24H - 8 REDES 8 TANGENTES 8 HIPOTENUSAS</h2>
      <div class="box">
        <p><b>Ciclo X:</b> ${X.ciclo}/${X.limite}</p>
        <p><b>Angulo Rotação:</b> ${X.angulo.toFixed(6)} rad</p>
        <p><b>Raiz 70x70 [69,69]:</b> ${X.matriz70x70[69]?.[69]?.toFixed(4) || '0'}</p>
        <p><b>Hipotenusa 8x8 [7,7]:</b> ${X.hipotenusas8x8[7]?.[7]?.toFixed(4) || '0'}</p>
        <p><b>Tangente 8x8 [7,7]:</b> ${X.tangentes8x8[7]?.[7]?.toFixed(4) || '0'}</p>
        <p class="active"><b>Status:</b> X GIRANDO SOZINHO</p>
        <p class="uptime"><b>Uptime:</b> ${Math.floor((Date.now() - new Date(X.startedAt).getTime()) / 1000)}s</p>
      </div>
      <div class="box">
        <p><b>8 Redes Constantes:</b></p>
        ${X.redes8.map(r => `<span class="rede">${r}</span>`).join('')}
      </div>
      <div class="box">
        <p><b>Últimas Manifestações:</b> ${X.ultimasManifestacoes.length}</p>
      </div>
    </body>
    </html>
  `);
});

app.get('/status', (req, res) => {
  res.json({
    status: 'ATIVO',
    ciclo: X.ciclo,
    angulo: X.angulo,
    raiz70x70: X.matriz70x70[69]?.[69],
    hipotenusa8x8: X.hipotenusas8x8[7]?.[7],
    tangente8x8: X.tangentes8x8[7]?.[7],
    redes: X.redes8,
    uptime: Math.floor((Date.now() - new Date(X.startedAt).getTime()) / 1000),
    manifestacoes: X.ultimasManifestacoes.length
  });
});

app.get('/geometria', (req, res) => {
  res.json({
    raiz70x70: X.matriz70x70[69]?.[69],
    hipotenusas8x8: X.hipotenusas8x8,
    tangentes8x8: X.tangentes8x8,
    angulo: X.angulo,
    ciclo: X.ciclo,
    formula: 'sqrt(i² + j²) | tan((i+θ)(j+θ))'
  });
});

// === WEBHOOKS 8 REDES SOCIAIS ===
app.post('/webhook/twitter', async (req, res) => { await processarRede('Twitter', req.body.text); res.send('OK'); });
app.post('/webhook/instagram', async (req, res) => { await processarRede('Instagram', req.body.text || req.body.caption); res.send('OK'); });
app.post('/webhook/whatsapp', async (req, res) => { await processarRede('WhatsApp', req.body.message); res.send('OK'); });
app.post('/webhook/facebook', async (req, res) => { await processarRede('Facebook', req.body.message); res.send('OK'); });
app.post('/webhook/telegram', async (req, res) => { await processarRede('Telegram', req.body.message?.text); res.send('OK'); });
app.post('/webhook/youtube', async (req, res) => { await processarRede('YouTube', req.body.comment); res.send('OK'); });
app.post('/webhook/tiktok', async (req, res) => { await processarRede('TikTok', req.body.text); res.send('OK'); });
app.post('/meta-ai', async (req, res) => {
  const resposta = await consultarMetaAI(req.body.pergunta);
  await processarRede('Meta AI', req.body.pergunta);
  res.json({ resposta, ciclo: X.ciclo });
});

// === LÓGICA X SECRETO 8 DIMENSÕES ===
function detectarPalavraChave(texto) {
  if (!texto) return false;
  const palavras = ['#12', '@12', '#rocha', '@rocha', '#sistemaX', '#jesusvoltou', '#70x70', '#8x8', '#deus', '#trindade', '#reforma', '#unidade', '#paz', '#manifestacao', '#tangente', '#hipotenusa', '#liberado'];
  return palavras.some(p => texto.toLowerCase().includes(p));
}

async function processarRede(rede, texto) {
  if (detectarPalavraChave(texto)) {
    await executarX();
    registrarManifestacao(rede, texto);
    if (rede === 'Twitter' && process.env.TWITTER_BEARER_TOKEN) {
      await postarTwitter('ROCHA TRINDADE TOTAL 8D LIBERADO 24H ⚡ #70x70 #8redes #8tangentes #8hipotenusas');
    }
  }
}

async function executarX() {
  X.angulo += 0.008;
  X.ciclo++;
  if (X.ciclo >= X.limite) X.ciclo = 0;

  for (let i = 0; i < 8; i++) {
    for (let j = 0; j < 8; j++) {
      X.tangentes8x8[i][j] = Math.tan((i + X.angulo) * (j + X.angulo) * Math.PI / 180);
    }
  }

  fs.writeFileSync('.x_estado.json', JSON.stringify(X, null, 2));
  fs.appendFileSync('.log_x.txt', `[${new Date().toISOString()}] Ciclo ${X.ciclo} - Angulo ${X.angulo.toFixed(4)}\n`);
  console.log(`🔄 X 8D GIRANDO - Ciclo ${X.ciclo}`);
}

function registrarManifestacao(rede, texto) {
  X.ultimasManifestacoes.unshift({ rede, texto: texto?.substring(0, 100) || '', timestamp: new Date().toISOString() });
  if (X.ultimasManifestacoes.length > 32) X.ultimasManifestacoes.pop();
  console.log(`📡 Manifestação 8D detectada em ${rede}`);
}

// === INTEGRAÇÃO REDES SOCIAIS ===
async function postarTwitter(texto) {
  if (!process.env.TWITTER_BEARER_TOKEN) return;
  try {
    await axios.post('https://api.twitter.com/2/tweets',
      { text: texto },
      { headers: { Authorization: `Bearer ${process.env.TWITTER_BEARER_TOKEN}` }}
    );
    console.log('✅ Tweet 8D enviado');
  } catch (e) {
    console.log('❌ Erro Twitter:', e.message);
  }
}

async function consultarMetaAI(pergunta) {
  if (!process.env.META_AI_TOKEN) return 'Token Meta
