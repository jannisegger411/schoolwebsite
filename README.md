
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Meine Spieleseite</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; background:#0f172a; color:#e5e7eb; }
    header { padding:16px 24px; background:#020617; position:sticky; top:0; }
    h1 { margin:0; font-size:22px; }
    .grid { display:grid; grid-template-columns: repeat(auto-fill, minmax(180px, 1fr)); gap:16px; padding:24px; }
    .card { background:#020617; border-radius:16px; overflow:hidden; box-shadow:0 10px 30px rgba(0,0,0,.3); cursor:pointer; }
    .thumb { height:120px; background:#1f2937; display:flex; align-items:center; justify-content:center; }
    .card p { margin:12px; font-weight:bold; }
    .player { position:fixed; inset:0; background:rgba(2,6,23,.9); display:none; }
    .player iframe { width:100%; height:100%; border:0; }
    .close { position:absolute; top:12px; right:12px; padding:8px 12px; border-radius:10px; background:#020617; color:#e5e7eb; border:1px solid #334155; }
  </style>
</head>
<body>
  <header><h1>🎮 Meine Spieleseite</h1></header>

  <main class="grid" id="games"></main>

  <div class="player" id="player">
    <button class="close" onclick="closeGame()">Schließen</button>
    <iframe id="frame"></iframe>
  </div>

  <script>
    // Beispiel-Spiele (ersetze die URLs mit deinen eigenen Spielen)
    const games = [
      { title: 'Flappy Clone', url: https://hotgames.io/soflo-wheelie-life },
      { title: 'Hextris', url: 'https://hextris.io/' },
      { title: '2048', url: 'https://play2048.co/' }
    ];

    const grid = document.getElementById('games');
    const player = document.getElementById('player');
    const frame = document.getElementById('frame');

    games.forEach(g => {
      const card = document.createElement('div');
      card.className = 'card';
      card.innerHTML = `<div class="thumb">▶</div><p>${g.title}</p>`;
      card.onclick = () => openGame(g.url);
      grid.appendChild(card);
    });

    function openGame(url) {
      frame.src = url;
      player.style.display = 'block';
    }
    function closeGame() {
      frame.src = '';
      player.style.display = 'none';
    }
  </script>
</body>
</html>
