<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
<title>iPod Touch - iOS Classic Experience</title>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jsmediatags/3.9.5/jsmediatags.min.js"></script>
<style>
* { box-sizing: border-box; -webkit-tap-highlight-color: transparent; user-select: none; }
html, body {
  margin: 0; padding: 0; width: 100%; height: 100%;
  background: #0d0d0d; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  display: flex; align-items: center; justify-content: center; overflow: hidden;
}

/* CARCASA IPOD TOUCH */
.ipod-frame {
  width: 360px; height: 690px;
  background: linear-gradient(135deg, #484b4f 0%, #1a1b1d 50%, #0d0e0f 100%);
  border-radius: 42px; padding: 18px 18px 22px 18px;
  box-shadow: 0 25px 60px rgba(0,0,0,0.9), inset 0 1px 2px rgba(255,255,255,0.4), inset 0 -2px 5px rgba(0,0,0,0.8);
  position: relative; display: flex; flex-direction: column; align-items: center; border: 1px solid #555;
}

.screen {
  width: 100%; height: 580px; background: #000; border-radius: 6px;
  position: relative; overflow: hidden; border: 2px solid #1a1a1a;
  box-shadow: inset 0 0 10px rgba(0,0,0,0.8);
}

.home-button {
  width: 50px; height: 50px; border-radius: 50%; margin-top: 14px;
  background: linear-gradient(180deg, #1c1d1f 0%, #101113 100%);
  border: 1px solid #333; box-shadow: inset 0 2px 4px rgba(0,0,0,0.8), 0 1px 1px rgba(255,255,255,0.1);
  display: flex; align-items: center; justify-content: center; cursor: pointer;
}
.home-button:active { background: #0d0e0f; }
.home-button-icon { width: 16px; height: 16px; border: 2px solid #777; border-radius: 5px; }

/* BARRA DE ESTADO iOS */
.status {
  height: 20px; background: linear-gradient(180deg, rgba(0,0,0,0.8) 0%, rgba(0,0,0,0.4) 100%);
  color: #d1d1d1; display: flex; align-items: center; padding: 0 8px; font-size: 11px; font-weight: bold;
  position: absolute; top: 0; left: 0; right: 0; z-index: 500; border-bottom: 1px solid rgba(255,255,255,0.05);
}
.status .time { position: absolute; left: 50%; transform: translateX(-50%); text-shadow: 0 -1px 0 rgba(0,0,0,0.8); }
.status .right { margin-left: auto; display: flex; gap: 4px; align-items: center; }
.battery { height: 10px; width: 20px; border: 1px solid #888; border-radius: 2px; padding: 1px; position: relative; }
.battery:after { content: ""; position: absolute; width: 1.5px; height: 4px; background: #888; right: -3px; top: 2px; }
.battery b { display: block; width: 85%; height: 100%; background: linear-gradient(180deg, #6ee049, #429f27); }

/* MENU PRINCIPAL (SPRINGBOARD iOS 4) */
.springboard {
  position: absolute; inset: 0; top: 20px;
  background: radial-gradient(circle at center, #2c3e50 0%, #0f171e 100%);
  background-image: radial-gradient(rgba(255, 255, 255, 0.08) 2px, transparent 0), radial-gradient(rgba(255, 255, 255, 0.05) 1px, transparent 0);
  background-size: 20px 20px, 10px 10px;
  display: flex; flex-direction: column; justify-content: space-between; padding: 18px 12px 8px 12px;
}

.grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 14px 10px; padding-top: 8px; }
.app-icon { display: flex; flex-direction: column; align-items: center; cursor: pointer; }
.icon-box {
  width: 54px; height: 54px; border-radius: 12px; position: relative;
  box-shadow: 0 4px 10px rgba(0,0,0,0.6), inset 0 1px 1px rgba(255,255,255,0.4);
  display: flex; align-items: center; justify-content: center; font-size: 24px; color: white;
  overflow: hidden; border: 1px solid rgba(0,0,0,0.3);
}
.icon-box::after {
  content: ""; position: absolute; top: 0; left: 0; right: 0; height: 50%;
  background: linear-gradient(180deg, rgba(255,255,255,0.4) 0%, rgba(255,255,255,0.08) 100%);
  border-radius: 11px 11px 0 0; pointer-events: none;
}
.app-icon label { color: #fff; font-size: 11px; margin-top: 4px; text-shadow: 0 1px 2px rgba(0,0,0,0.9); font-weight: 500; }

.icon-music { background: linear-gradient(180deg, #ff7a00 0%, #ff2d55 100%); }
.icon-photos { background: linear-gradient(180deg, #ffffff 0%, #d1d1d1 100%); color: #333; }
.icon-safari { background: linear-gradient(180deg, #2b92e4 0%, #1459a6 100%); }
.icon-videos { background: linear-gradient(180deg, #00c6ff 0%, #0072ff 100%); }
.icon-appstore { background: linear-gradient(180deg, #1d976c 0%, #93f9b9 100%); }
.icon-settings { background: linear-gradient(180deg, #8a8a8e 0%, #3a3a3c 100%); }
.icon-notes { background: linear-gradient(180deg, #f7d046 0%, #f39c12 100%); }
.icon-clock { background: linear-gradient(180deg, #2c3e50 0%, #000000 100%); }
.icon-calc { background: linear-gradient(180deg, #f39c12 0%, #d35400 100%); }
.icon-camera { background: linear-gradient(180deg, #a8a8a8 0%, #5a5a5a 100%); }
.icon-mail { background: linear-gradient(180deg, #3498db 0%, #2980b9 100%); }
.icon-maps { background: linear-gradient(180deg, #2ecc71 0%, #27ae60 100%); }

.dock-container { width: 100%; }
.dock-glass {
  background: linear-gradient(180deg, rgba(255,255,255,0.2) 0%, rgba(255,255,255,0.05) 20%, rgba(0,0,0,0.4) 100%);
  border-top: 1px solid rgba(255,255,255,0.4); border-radius: 4px;
  box-shadow: 0 -2px 10px rgba(0,0,0,0.5); padding: 6px 8px; display: flex; justify-style: space-around;
  display: flex; justify-content: space-around;
}
.page-dots { display: flex; justify-content: center; gap: 6px; margin-bottom: 6px; }
.dot { width: 6px; height: 6px; border-radius: 50%; background: rgba(255,255,255,0.4); }
.dot.active { background: #fff; }

/* APP DE MÚSICA */
.app-window {
  position: absolute; inset: 0; top: 20px; background: #000; z-index: 400;
  display: none; flex-direction: column; transform: scale(0.85); opacity: 0;
  transition: transform 0.22s ease-out, opacity 0.22s ease-out;
}
.app-window.open { display: flex; transform: scale(1); opacity: 1; }

.app-header {
  height: 42px; background: linear-gradient(180deg, #b0b8c0 0%, #828e99 50%, #687582 51%, #505c68 100%);
  border-bottom: 1px solid #2d353d; display: flex; align-items: center; justify-content: space-between; padding: 0 10px;
  color: #fff; text-shadow: 0 -1px 0 rgba(0,0,0,0.7); font-weight: bold; font-size: 15px;
}
.header-btn {
  background: linear-gradient(180deg, #7c8895 0%, #4b5663 100%); border: 1px solid #333;
  border-radius: 4px; color: #fff; font-size: 11px; padding: 4px 8px; font-weight: bold; cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.3);
}

.content-area { flex: 1; position: relative; overflow: hidden; background: #fff; }
.view { position: absolute; inset: 0; display: none; flex-direction: column; background: #fff; }
.view.active { display: flex; }

.section-title {
  background: linear-gradient(180deg, #d2d7dc 0%, #b8bec5 100%); color: #333; font-size: 12px; font-weight: bold;
  padding: 3px 10px; border-bottom: 1px solid #999; text-shadow: 0 1px 0 rgba(255,255,255,0.6);
}

.music-list { list-style: none; margin: 0; padding: 0; flex: 1; overflow-y: auto; }
.music-item {
  display: flex; align-items: center; padding: 8px 10px; border-bottom: 1px solid #e0e0e0; cursor: pointer;
}
.music-item:active { background: linear-gradient(180deg, #058bfb 0%, #015eea 100%); color: white; }
.music-item img { width: 42px; height: 42px; border-radius: 3px; object-fit: cover; margin-right: 10px; border: 1px solid #ccc; }
.music-info { flex: 1; overflow: hidden; }
.music-title { font-size: 14px; font-weight: bold; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; color: #000; }
.music-sub { font-size: 12px; color: #666; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; margin-top: 2px; }
.music-item:active .music-title, .music-item:active .music-sub { color: #fff; }

.albums-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; padding: 12px; overflow-y: auto; flex: 1; }
.album-card { display: flex; flex-direction: column; align-items: center; text-align: center; cursor: pointer; }
.album-card img { width: 110px; height: 110px; border-radius: 4px; box-shadow: 0 3px 6px rgba(0,0,0,0.3); border: 1px solid #ddd; object-fit: cover; }
.album-card span { font-size: 12px; font-weight: bold; margin-top: 4px; color: #111; max-width: 110px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }

.now-playing { background: #111; color: white; align-items: center; justify-content: space-around; padding: 10px; }
.art-container {
  width: 220px; height: 220px; border-radius: 6px; box-shadow: 0 8px 20px rgba(0,0,0,0.8);
  overflow: hidden; border: 1px solid #333; margin-top: 10px;
}
.art-container img { width: 100%; height: 100%; object-fit: cover; }

.track-meta { text-align: center; width: 100%; padding: 0 10px; margin-top: 10px; }
.track-meta .title { font-size: 16px; font-weight: bold; color: #fff; }
.track-meta .artist { font-size: 13px; color: #aaa; margin-top: 2px; }

.scrubber { width: 100%; padding: 0 15px; margin-top: 10px; }
.scrubber input { width: 100%; accent-color: #007aff; }
.time-box { display: flex; justify-content: space-between; font-size: 10px; color: #888; margin-top: 2px; }

.controls { display: flex; align-items: center; justify-content: center; gap: 30px; margin-bottom: 15px; }
.ctrl-btn { background: none; border: none; color: #fff; font-size: 26px; cursor: pointer; opacity: 0.9; }
.ctrl-btn:active { opacity: 0.5; }

.tab-bar {
  height: 48px; background: linear-gradient(180deg, #2c2c2c 0%, #111111 100%);
  border-top: 1px solid #000; display: flex; justify-content: space-around; align-items: center;
}
.tab { display: flex; flex-direction: column; align-items: center; color: #8e8e93; font-size: 10px; cursor: pointer; text-decoration: none; }
.tab.active { color: #007aff; }
.tab-icon { font-size: 18px; margin-bottom: 2px; }
</style>
</head>
<body>

<div class="ipod-frame">
  <div class="screen">
    <!-- Status Bar -->
    <div class="status">
      <span>iPod</span>
      <span class="time" id="clock">9:42 AM</span>
      <span class="right">
        <span>▶</span>
        <span class="battery"><b></b></span>
      </span>
    </div>

    <!-- Menú Home (Springboard) -->
    <div class="springboard" id="springboard">
      <div class="grid">
        <div class="app-icon" onclick="openMusicApp()">
          <div class="icon-box icon-music">♫</div>
          <label>Música</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Fotos...')">
          <div class="icon-box icon-photos">🖼</div>
          <label>Fotos</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Vídeos...')">
          <div class="icon-box icon-videos">🎬</div>
          <label>Vídeos</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Safari...')">
          <div class="icon-box icon-safari">🧭</div>
          <label>Safari</label>
        </div>

        <div class="app-icon" onclick="alert('Abriendo App Store...')">
          <div class="icon-box icon-appstore">🅰</div>
          <label>App Store</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Notas...')">
          <div class="icon-box icon-notes">📝</div>
          <label>Notas</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Reloj...')">
          <div class="icon-box icon-clock">⏰</div>
          <label>Reloj</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Calculadora...')">
          <div class="icon-box icon-calc">➕</div>
          <label>Calculadora</label>
        </div>

        <div class="app-icon" onclick="alert('Abriendo Ajustes...')">
          <div class="icon-box icon-settings">⚙</div>
          <label>Ajustes</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Cámara...')">
          <div class="icon-box icon-camera">📷</div>
          <label>Cámara</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Mail...')">
          <div class="icon-box icon-mail">✉</div>
          <label>Mail</label>
        </div>
        <div class="app-icon" onclick="alert('Abriendo Mapas...')">
          <div class="icon-box icon-maps">🗺</div>
          <label>Mapas</label>
        </div>
      </div>

      <div class="dock-container">
        <div class="page-dots">
          <div class="dot active"></div>
          <div class="dot"></div>
        </div>
        <div class="dock-glass">
          <div class="app-icon" onclick="openMusicApp()">
            <div class="icon-box icon-music">♫</div>
            <label>Música</label>
          </div>
          <div class="app-icon" onclick="alert('Abriendo Safari...')">
            <div class="icon-box icon-safari">🧭</div>
            <label>Safari</label>
          </div>
          <div class="app-icon" onclick="alert('Abriendo Vídeos...')">
            <div class="icon-box icon-videos">🎬</div>
            <label>Vídeos</label>
          </div>
          <div class="app-icon" onclick="alert('Abriendo Fotos...')">
            <div class="icon-box icon-photos">🖼</div>
            <label>Fotos</label>
          </div>
        </div>
      </div>
    </div>

    <!-- App de Música (Dentro del iPod) -->
    <div class="app-window" id="appWindow">
      <div class="app-header">
        <button class="header-btn" onclick="document.getElementById('fileInput').click()">+ Subir MP3</button>
        <span id="headerTitle">Canciones</span>
        <button class="header-btn" onclick="showView('nowPlayingView')">Reproduciendo</button>
      </div>

      <input type="file" id="fileInput" accept="audio/*" multiple style="display:none" onchange="handleFiles(this.files)">

      <div class="content-area">
        <!-- Vista Canciones -->
        <div class="view active" id="songsView">
          <div class="section-title">Todas las Canciones</div>
          <ul class="music-list" id="songsList"></ul>
        </div>

        <!-- Vista Álbumes -->
        <div class="view" id="albumsView">
          <div class="section-title">Álbumes</div>
          <div class="albums-grid" id="albumsGrid"></div>
        </div>

        <!-- Vista Reproduciendo -->
        <div class="view now-playing" id="nowPlayingView">
          <div class="art-container">
            <img id="npCover" src="data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200'><rect width='200' height='200' fill='%23222'/></svg>" alt="Cover">
          </div>
          <div class="track-meta">
            <div class="title" id="npTitle">Selecciona una canción</div>
            <div class="artist" id="npArtist">iPod Touch</div>
          </div>
          <div class="scrubber">
            <input type="range" id="progressBar" value="0" min="0" max="100" oninput="seekTrack(this.value)">
            <div class="time-box">
              <span id="currentTime">0:00</span>
              <span id="duration">0:00</span>
            </div>
          </div>
          <div class="controls">
            <button class="ctrl-btn" onclick="prevTrack()">⏮</button>
            <button class="ctrl-btn" id="playBtn" onclick="togglePlay()">▶</button>
            <button class="ctrl-btn" onclick="nextTrack()">⏭</button>
          </div>
        </div>
      </div>

      <!-- Tab Bar Inferior -->
      <div class="tab-bar">
        <div class="tab active" id="tabSongs" onclick="switchTab('songsView', this)">
          <div class="tab-icon">♫</div>
          <span>Canciones</span>
        </div>
        <div class="tab" id="tabAlbums" onclick="switchTab('albumsView', this)">
          <div class="tab-icon">💽</div>
          <span>Álbumes</span>
        </div>
        <div class="tab" id="tabNP" onclick="switchTab('nowPlayingView', this)">
          <div class="tab-icon">►</div>
          <span>Reproduciendo</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Botón Home Físico -->
  <div class="home-button" onclick="closeMusicApp()">
    <div class="home-button-icon"></div>
  </div>
</div>

<audio id="audioPlayer"></audio>

<script>
const DEFAULT_COVER = 'data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 200 200"><rect width="200" height="200" fill="%23222"/><circle cx="100" cy="100" r="60" fill="%23333"/><circle cx="100" cy="100" r="20" fill="%23111"/><text x="50%" y="54%" font-size="28" fill="%23666" text-anchor="middle" font-family="sans-serif">♫</text></svg>';

let songs = [];
let currentIndex = -1;
const audio = document.getElementById('audioPlayer');

function openMusicApp() {
  const win = document.getElementById('appWindow');
  win.style.display = 'flex';
  setTimeout(() => win.classList.add('open'), 10);
}

function closeMusicApp() {
  const win = document.getElementById('appWindow');
  win.classList.remove('open');
  setTimeout(() => win.style.display = 'none', 220);
}

function switchTab(viewId, tabEl) {
  document.querySelectorAll('.view').forEach(v => v.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById(viewId).classList.add('active');
  tabEl.classList.add('active');

  const titles = { 'songsView': 'Canciones', 'albumsView': 'Álbumes', 'nowPlayingView': 'Reproduciendo' };
  document.getElementById('headerTitle').textContent = titles[viewId];
}

function showView(viewId) {
  const tabMap = { 'songsView': 'tabSongs', 'albumsView': 'tabAlbums', 'nowPlayingView': 'tabNP' };
  switchTab(viewId, document.getElementById(tabMap[viewId]));
}

function handleFiles(files) {
  Array.from(files).forEach(file => {
    if (!file.type.startsWith('audio/')) return;

    const songObj = {
      file: file,
      url: URL.createObjectURL(file),
      title: file.name.replace(/\.[^/.]+$/, ""),
      artist: "Artista desconocido",
      album: "Álbum desconocido",
      cover: DEFAULT_COVER
    };

    jsmediatags.read(file, {
      onSuccess: function(tag) {
        const tags = tag.tags;
        if (tags.title) songObj.title = tags.title;
        if (tags.artist) songObj.artist = tags.artist;
        if (tags.album) songObj.album = tags.album;

        if (tags.picture) {
          const { data, format } = tags.picture;
          let base64String = "";
          for (let i = 0; i < data.length; i++) {
            base64String += String.fromCharCode(data[i]);
          }
          songObj.cover = `data:${format};base64,${btoa(base64String)}`;
        }
        renderSongs();
        renderAlbums();
      },
      onError: function() {
        renderSongs();
        renderAlbums();
      }
    });

    songs.push(songObj);
  });
  renderSongs();
  renderAlbums();
}

function renderSongs() {
  const list = document.getElementById('songsList');
  list.innerHTML = '';
  songs.forEach((song, index) => {
    const li = document.createElement('li');
    li.className = 'music-item';
    li.onclick = () => playSong(index);
    li.innerHTML = `
      <img src="${song.cover}">
      <div class="music-info">
        <div class="music-title">${song.title}</div>
        <div class="music-sub">${song.artist} — ${song.album}</div>
      </div>
    `;
    list.appendChild(li);
  });
}

function renderAlbums() {
  const grid = document.getElementById('albumsGrid');
  grid.innerHTML = '';
  const albums = {};

  songs.forEach(song => {
    if (!albums[song.album]) {
      albums[song.album] = { name: song.album, cover: song.cover, artist: song.artist };
    }
  });

  Object.values(albums).forEach(album => {
    const card = document.createElement('div');
    card.className = 'album-card';
    card.innerHTML = `<img src="${album.cover}"><span>${album.name}</span>`;
    grid.appendChild(card);
  });
}

function playSong(index) {
  currentIndex = index;
  const song = songs[index];
  audio.src = song.url;
  audio.play();

  document.getElementById('npTitle').textContent = song.title;
  document.getElementById('npArtist').textContent = song.artist;
  document.getElementById('npCover').src = song.cover;
  document.getElementById('playBtn').textContent = '⏸';

  showView('nowPlayingView');
}

function togglePlay() {
  if (!audio.src) return;
  if (audio.paused) {
    audio.play();
    document.getElementById('playBtn').textContent = '⏸';
  } else {
    audio.pause();
    document.getElementById('playBtn').textContent = '▶';
  }
}

function prevTrack() {
  if (currentIndex > 0) playSong(currentIndex - 1);
}

function nextTrack() {
  if (currentIndex < songs.length - 1) playSong(currentIndex + 1);
}

audio.ontimeupdate = () => {
  if (audio.duration) {
    const pct = (audio.currentTime / audio.duration) * 100;
    document.getElementById('progressBar').value = pct;
    document.getElementById('currentTime').textContent = formatTime(audio.currentTime);
    document.getElementById('duration').textContent = formatTime(audio.duration);
  }
};

function seekTrack(val) {
  if (audio.duration) {
    audio.currentTime = (val / 100) * audio.duration;
  }
}

function formatTime(sec) {
  const m = Math.floor(sec / 60);
  const s = Math.floor(sec % 60);
  return `${m}:${s < 10 ? '0' : ''}${s}`;
}

function clock() {
  let d = new Date(), h = d.getHours(), m = String(d.getMinutes()).padStart(2, '0'), ap = h >= 12 ? 'PM' : 'AM';
  h = h % 12 || 12;
  document.getElementById('clock').textContent = `${h}:${m} ${ap}`;
}
clock();
setInterval(clock, 1000);
</script>
</body>
</html>
