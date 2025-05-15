const express = require('express');
const app = express();
const PORT = 3000;

// Middleware para JSON
app.use(express.json());

// Rota GET
app.get('/', (req, res) => {
  res.send('API funcionando! 🟢');
});

// Rota POST
app.post('/mensagem', (req, res) => {
  const { nome } = req.body;

  if (!nome) {
    return res.status(400).json({ erro: 'O campo "nome" é obrigatório.' });
  }

  res.json({ mensagem: `Olá, ${nome}! Sua mensagem foi recebida com sucesso.` });
});

// Iniciar o servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});

