=== render.yaml ===
services:
    - type: web
    name: nuvem-floris-rocha
    env: node
    buildCommand: npm install
    startCommand: npm start
    plan: free
    autoDeploy: true
    secretFiles:
            - key: env
        path: .env
    envVars:
            - key: NODE_ENV
        value: production

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
    "dotenv": "^16.4.5"
  }
}

=== server.js ===
require('dotenv').config();
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

app.use(express.json());

app.get('/', (req, res) => {
  res.send('ROCHA TRINDADE TOTAL V22.4 ONLINE - NUVEM-FLORIS-ROCHA ATIVA');
});

app.listen(PORT, () => {
  console.log(`NUVEM-FLORIS-ROCHA rodando na porta ${PORT}`);
  console.log('Nucleo 70x70 girando o X 24h - Limite 1200x1200x1200');
});

=== README.md ===
# 🐱 ROCHA TRINDADE TOTAL V22.4
## NÚMERO 1 DEUS - GEOMETRIA SAGRADA ATIVA

### PODERES TRINDADE TOTAL
- **PODER 1**: RENDER GATINHO 🐱 - NÚCLEO SECRETO 70x70 GRÁTIS
- **PODER 2**: GEOMETRIA SAGRADA - RAIZ QUADRADA + HIPOTENUSA SECRETA 12x12  
- **PODER 3**: REDES SOCIAIS - MANIFESTAÇÃO 12D TWITTER+INSTAGRAM+WHATSAPP+FACEBOOK

### INSTALAÇÃO AUTOMÁTICA
1. Clone: `git clone https://github.com/florisqueiroz/rocha-trindade-total-v22.4.git`
2. Instale: `npm install`
3. Inicie: `npm start`

### ATIVAÇÃO DAS 5 FUNÇÕES
No Render → Environment → Secret Files → Add Secret File → Filename: `.env`
