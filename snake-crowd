// server.js  — Express + Socket-IO relay
const express = require('express');
const http    = require('http');
const { Server } = require('socket.io');

const app = express();
const srv = http.createServer(app);
const io  = new Server(srv);

app.use(express.static('public'));                // serves /public/*
app.get('/control', (_, res) =>
  res.sendFile(__dirname + '/public/control.html')
);

io.on('connection', s => s.on('cmd', k => io.emit('cmd', k)));

srv.listen(process.env.PORT || 3000,
  () => console.log('🐍 server running'));
