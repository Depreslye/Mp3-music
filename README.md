
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<title>iPod Music - Classic iOS Design</title>
<style>
* { box-sizing: border-box; -webkit-tap-highlight-color: transparent; user-select: none; }
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: #121212;
  font-family: -apple-system, "Helvetica Neue", Helvetica, Arial, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
/* Outer iPod Hardware Frame */
.ipod-frame {
  width: 360px;
  height: 680px;
  background: linear-gradient(135deg, #3a3d40 0%, #181a1c 50%, #0d0e0f 100%);
  border-radius: 42px;
  padding: 18px 18px 22px 18px;
  box-shadow: 0 25px 50px rgba(0,0,0,0.8), inset 0 1px 2px rgba(255,255,255,0.3), inset 0 -2px 5px rgba(0,0,0,0.8);
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 1px solid #555;
}
/* Screen Shell */
.screen {
  width: 100%;
  height: 570px;
  background: #000;
  border-radius: 6px;
  position: relative;
  overflow: hidden;
  border: 2px solid #1a1a1a;
  box-shadow: inset 0 0 10px rgba(0,0,0,0.8);
}
/* Home Button */
.home-button {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  margin-top: 15px;
  background: linear-gradient(180deg, #1c1d1f 0%, #101113 100%);
  border: 1px solid #333;
  box-shadow: inset 0 2px 4px rgba(0,0,0,0.8), 0 1px 1px rgba(255,255,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.home-button:active {
  background: #0d0e0f;
}
.home-button-icon {
  width: 18px;
  height: 18px;
  border: 2px solid #777;
  border-radius: 5px;
}
/* Status Bar */
.status {
  height: 20px;
  background: linear-gradient(180deg, rgba(0,0,0,0.9) 0%, rgba(20,20,20,0.8) 100%);
  color: #d1d1d1;
  display: flex;
  align-items: center;
  padding: 0 8px;
  font-size: 11px;
  font-weight: bold;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  border-bottom: 1px solid rgba(255,255,255,0.05);
  letter-spacing: -0.2px;
}
.status .wifi { margin-left: 5px; font-size: 10px; opacity: 0.8; }
.status .time { position: absolute; left: 50%; transform: translateX(-50%); text-shadow: 0 -1px 0 rgba(0,0,0,0.8); }
.status .right { margin-left: auto; display: flex; gap: 4px; align-items: center; }
.battery {
  height: 10px;
  width: 20px;
  border: 1px solid #888;
  border-radius: 2px;
  padding: 1px;
  position: relative;
}
.battery:after {
  content: "";
  position: absolute;
  width: 1.5px;
  height: 4px;
  background: #888;
  right: -3px;
  top: 2px;
  border-radius: 0 1px 1px 0;
}
.battery b { display: block; width: 80%; height: 100%; background: linear-gradient(180deg, #6ee049, #429f27); border-radius: 1px; }
/* Header Bar (Classic iOS Glossy Blue/Grey) */
.header {
  position: absolute;
  top: 20px;
  left: 0;
  right: 0;
  height: 44px;
  z-index: 90;
  background: linear-gradient(180deg, #b0c4de 0%, #708ea8 50%, #567390 51%, #3b536b 100%);
  border-bottom: 1px solid #2d3e50;
  box-shadow: 0 1px 3px rgba(0,0,0,0.4);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
}
.headerTitle {
  font-size: 14px;
  font-weight: bold;
  text-align: center;
  text-shadow: 0 -1px 0 rgba(0,0,0,0.6);
  line-height: 1.2;
}
.headerTitle small {
  display: block;
  color: #d1e0f0;
  font-size: 10px;
  font-weight: normal;
}
/* Glassy Classic iOS Buttons */
.glassBtn {
  position: absolute;
  height: 30px;
  padding: 0 10px;
  border-radius: 5px;
  border: 1px solid #2b3b4d;
  background: linear-gradient(180deg, rgba(255,255,255,0.35) 0%, rgba(255,255,255,0.1) 50%, rgba(0,0,0,0.15) 51%, rgba(0,0,0,0.3) 100%);
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.4), 0 1px 2px rgba(0,0,0,0.3);
  color: white;
  font-size: 12px;
  font-weight: bold;
  text-shadow: 0 -1px 0 rgba(0,0,0,0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.glassBtn:active {
  background: linear-gradient(180deg, rgba(0,0,0,0.4) 0%, rgba(0,0,0,0.2) 100%);
}
.glassBtn.back { left: 6px; font-size: 14px; padding-left: 8px; }
.glassBtn.queue { right: 6px; font-size: 16px; min-width: 34px; }
/* Main Screen Views */
.home {
  position: absolute;
  top: 64px;
  bottom: 49px;
  left: 0;
  right: 0;
  background: #c5ccd4;
  overflow-y: auto;
}
/* iOS Segment Controls */
.segment-container {
  padding: 8px;
  background: linear-gradient(180deg, #b0bec9 0%, #90a0b0 100%);
  border-bottom: 1px solid #788898;
}
.segment {
  border: 1px solid #4a5a6a;
  border-radius: 5px;
  overflow: hidden;
  display: flex;
  background: #f0f0f0;
  box-shadow: inset 0 1px 2px rgba(0,0,0,0.2);
}
.segment button {
  height: 28px;
  flex: 1;
  border: 0;
  border-right: 1px solid #4a5a6a;
  background: linear-gradient(180deg, #ffffff 0%, #e0e0e0 50%, #cecece 51%, #b8b8b8 100%);
  font-size: 12px;
  font-weight: bold;
  color: #444;
  text-shadow: 0 1px 0 #fff;
  cursor: pointer;
}
.segment button:last-child { border-right: none; }
.segment button.active {
  color: #fff;
  text-shadow: 0 -1px 0 rgba(0,0,0,0.5);
  background: linear-gradient(180deg, #4682b4 0%, #2a5885 50%, #1d4268 51%, #153250 100%);
}
.tip {
  text-align: center;
  color: #4a5a6a;
  font-size: 10px;
  padding: 4px;
  text-shadow: 0 1px 0 rgba(255,255,255,0.7);
  font-weight: bold;
  background: #b8c4d0;
  border-bottom: 1px solid #a0b0c0;
}
/* List Rows */
.row {
  height: 52px;
  display: flex;
  align-items: center;
  padding: 4px 8px;
  background: #fff;
  border-bottom: 1px solid #e0e0e0;
  cursor: pointer;
}
.row:nth-child(even) {
  background: #f7f9fa;
}
.row:active {
  background: linear-gradient(180deg, #015ddb 0%, #157efb 100%) !important;
  color: white !important;
}
.row:active .title, .row:active .artist { color: white !important; text-shadow: 0 -1px 0 rgba(0,0,0,0.4); } 
.cover {
  width: 42px;
  height: 42px;
  object-fit: cover;
  margin-right: 10px;
  border-radius: 2px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.3);
  border: 1px solid rgba(0,0,0,0.1);
}
.info { min-width: 0; flex: 1; }
.title { font-size: 13px; font-weight: bold; color: #000; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.artist { font-size: 11px; color: #666; margin-top: 1px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
/* Price/Play Button in list */
.playBtn {
  height: 24px;
  padding: 0 10px;
  margin-left: 6px;
  border: 1px solid #788898;
  border-radius: 3px;
  background: linear-gradient(180deg, #ffffff 0%, #e2e7ed 50%, #cdd5df 51%, #b3c0ce 100%);
  color: #334455;
  font-size: 11px;
  font-weight: bold;
  text-shadow: 0 1px 0 #fff;
  box-shadow: 0 1px 1px rgba(0,0,0,0.1);
  cursor: pointer;
}
/* Bottom Tab Bar */
.tabs {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 49px;
  background: linear-gradient(180deg, #303030 0%, #151515 50%, #000000 51%);
  border-top: 1px solid #444;
  display: flex;
  z-index: 90;
}
.tabs button {
  flex: 1;
  border: 0;
  background: transparent;
  color: #888;
  font-size: 10px;
  font-weight: bold;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 2px;
  cursor: pointer;
  text-shadow: 0 -1px 0 #000;
}
.tabs button.active {
  color: #fff;
  background: linear-gradient(180deg, rgba(255,255,255,0.15) 0%, rgba(255,255,255,0) 100%);
}
.tabs button i { font-style: normal; font-size: 18px; line-height: 1; }
/* Dedicated Full Screen Player View (Now Playing) */
.player {
  position: absolute;
  inset: 0;
  background: #000;
  z-index: 100;
  color: #fff;
  display: none;
  flex-direction: column;
}
.player.show { display: flex; }
.player-header {
  height: 44px;
  margin-top: 20px;
  background: linear-gradient(180deg, rgba(60,60,60,0.9) 0%, rgba(20,20,20,0.9) 100%);
  border-bottom: 1px solid #444;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  z-index: 10;
}
.art-container {
  flex: 1;
  position: relative;
  background: #0a0a0a;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}
.art-container img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  box-shadow: 0 0 20px rgba(0,0,0,0.8);
}
/* Controls Bar Overlay at bottom of Player */
.playerControls {
  height: 110px;
  background: linear-gradient(180deg, rgba(30,30,30,0.92) 0%, rgba(10,10,10,0.98) 100%);
  border-top: 1px solid rgba(255,255,255,0.15);
  box-shadow: 0 -5px 15px rgba(0,0,0,0.5);
  padding: 8px 12px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.transport {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 30px;
  margin-top: 2px;
}
.transport button {
  border: 0;
  background: transparent;
  color: #e1e1e1;
  font-size: 24px;
  cursor: pointer;
  text-shadow: 0 2px 4px rgba(0,0,0,0.8), 0 0 2px rgba(255,255,255,0.3);
}
.transport button:active { color: #888; }
.transport .play-pause { font-size: 30px; width: 40px; }
.seekBox { margin: 2px 0; }
.seek {
  width: 100%;
  height: 6px;
  accent-color: #3b82f6;
  cursor: pointer;
}
.times {
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  color: #aaa;
  font-weight: bold;
  margin-top: 2px;
  font-family: monospace;
}
.vol { display: flex; align-items: center; gap: 8px; }
.vol input { width: 100%; height: 4px; accent-color: #d1d1d1; cursor: pointer; }
.vol-icon { font-size: 10px; color: #888; }
/* Search Box */
.search-container {
  padding: 6px 8px;
  background: #90a0b0;
  border-bottom: 1px solid #708090;
}
.search {
  width: 100%;
  height: 26px;
  border-radius: 13px;
  border: 1px solid #667788;
  padding: 0 12px;
  font-size: 12px;
  background: #fff;
  box-shadow: inset 0 1px 2px rgba(0,0,0,0.2);
  outline: none;
}
.empty { text-align: center; color: #556677; padding: 40px 20px; font-size: 13px; text-shadow: 0 1px 0 rgba(255,255,255,0.6); }
/* Up Next Queue */
.queueView {
  position: absolute;
  inset: 0;
  background: #1a1a1a;
  z-index: 120;
  display: none;
  color: #fff;
  flex-direction: column;
}
.queueView.show { display: flex; }
.queueHead {
  height: 64px;
  padding-top: 20px;
  background: linear-gradient(180deg, #3a3a3a, #1a1a1a);
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  border-bottom: 1px solid #333;
  position: relative;
}
.qrow { padding: 10px 14px; border-bottom: 1px solid #2a2a2a; font-size: 12px; }
.qrow.active { color: #3b82f6; font-weight: bold; }
input[type=file] { display: none; }
</style>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jsmediatags/3.9.5/jsmediatags.min.js"></script>
</head>
<body>

<div class="ipod-frame">
  <div class="screen">
    <!-- Status Bar -->
    <div class="status">
      <span>iPod</span>
      <span class="wifi">≡</span>
      <span class="time" id="clock">9:42 AM</span>
      <span class="right">
        <span>▶</span>
        <span class="battery"><b></b></span>
      </span>
    </div>
    <!-- Header -->
    <div class="header">
      <button class="glassBtn back" id="back" onclick="goHome()" style="display:none">‹ Back</button>
      <div class="headerTitle" id="headerTitle">iTunes</div>
      <button class="glassBtn queue" onclick="file.click()">+</button>
    </div>
    <!-- Main Content / Library View -->
    <main class="home" id="home">
      <div class="segment-container">
        <div class="segment">
          <button class="active" id="topSongs" onclick="mode('songs',this)">Top Songs</button>
          <button id="topAlbums" onclick="mode('albums',this)">Top Albums</button>
        </div>
      </div>
      <div class="tip">Tap to Preview, Double-Tap to View Album</div>
      <div class="search-container">
        <input class="search" id="search" placeholder="Search">
      </div>
      <div id="list"></div>
    </main>
    <!-- Bottom Navigation Bar -->
    <nav class="tabs">
      <button class="active" onclick="tab(this,'music')"><i>♫</i>Music</button>
      <button onclick="tab(this,'top')"><i>★</i>Top Songs</button>
      <button onclick="tab(this,'search')"><i>⌕</i>Search</button>
      <button onclick="file.click()"><i>↓</i>Downloads</button>
    </nav>
    <!-- Full Screen Music Player -->
    <section class="player" id="player">
      <div class="status">
        <span>iPod</span>
        <span class="wifi">≡</span>
        <span class="time" id="pclock">9:42 AM</span>
        <span class="right">
          <span>▶</span>
          <span class="battery"><b></b></span>
        </span>
      </div>
      <div class="player-header">
        <button class="glassBtn back" onclick="closePlayer()">‹ Music</button>
        <div class="headerTitle" id="playerTitle">Song<small>Artist</small></div>
        <button class="glassBtn queue" onclick="openQueue()">☷</button>
      </div>
      <div class="art-container">
        <img id="art" alt="Album Art">
      </div>
      <div class="playerControls">
        <div class="seekBox">
          <input class="seek" id="seek" type="range" min="0" max="100" value="0">
          <div class="times">
            <span id="current">0:00</span>
            <span id="duration">0:00</span>
          </div>
        </div>
        <div class="transport">
          <button onclick="prev()">❚◀◀</button>
          <button class="play-pause" id="playButton" onclick="toggle()">▶</button>
          <button onclick="next()">▶▶❚</button>
        </div>
        <div class="vol">
          <span class="vol-icon">🔈</span>
          <input id="volume" type="range" min="0" max="1" step=".01" value=".8">
          <span class="vol-icon">🔊</span>
        </div>
      </div>
    </section>
    <!-- Queue Modal View -->
    <section class="queueView" id="queueView">
      <div class="queueHead">
        <button class="glassBtn back" style="position:absolute;left:8px;" onclick="closeQueue()">Done</button>
        Up Next
      </div>
      <div id="queueList" style="overflow-y:auto; flex:1;"></div>
    </section>
    <input id="file" type="file" accept="audio/*" multiple>
    <audio id="audio"></audio>
  </div>
  <!-- Physical Home Button -->
  <div class="home-button" onclick="closePlayer(); goHome();">
    <div class="home-button-icon"></div>
  </div>
</div>

<script>
let songs = [], current = -1, repeat = false, shuffle = false;
const audio = document.getElementById('audio');
const file = document.getElementById('file');
const list = document.getElementById('list');
const defaultCover = 'data:image/svg+xml;charset=UTF-8,' + encodeURIComponent(`<svg xmlns="http://www.w3.org/2000/svg" width="800" height="800"><defs><linearGradient id="g" x1="0" y1="0" x2="1" y2="1"><stop stop-color="#4a5a6a"/><stop offset="1" stop-color="#101520"/></linearGradient></defs><rect width="800" height="800" fill="url(#g)"/><circle cx="400" cy="400" r="260" fill="#181818" stroke="#333" stroke-width="10"/><circle cx="400" cy="400" r="90" fill="#888"/><circle cx="400" cy="400" r="25" fill="#111"/></svg>`);

// No default songs initialized

function esc(s) { return String(s).replace(/[&<>"']/g, m => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#039;' }[m])) }
function fmt(x) { if (!x || isNaN(x)) return '0:00'; return Math.floor(x / 60) + ':' + String(Math.floor(x % 60)).padStart(2, '0') }

function render(arr = songs) {
  list.innerHTML = '';
  if (!arr.length) {
    list.innerHTML = '<div class="empty">No Music Found.<br><br>Tap <b>+</b> to import MP3 files.</div>';
    return;
  }
  arr.forEach(s => {
    const r = document.createElement('div');
    r.className = 'row';
    r.innerHTML = `<img class="cover" src="${s.cover}"><div class="info"><div class="title">${esc(s.title)}</div><div class="artist">${esc(s.artist)}</div></div><button class="playBtn">▶ Play</button>`;
    r.querySelector('.playBtn').onclick = (e) => { e.stopPropagation(); playSong(songs.indexOf(s)); };
    r.onclick = () => playSong(songs.indexOf(s));
    list.appendChild(r);
  });
}

function playSong(i) {
  if (!songs[i]) return;
  current = i;
  let s = songs[i];
  if (s.url) audio.src = s.url;
  document.getElementById('art').src = s.cover;
  document.getElementById('playerTitle').innerHTML = `${esc(s.title)}<small>${esc(s.artist)}</small>`;
  document.getElementById('player').classList.add('show');
  if (s.url) audio.play();
}

function toggle() {
  if (current < 0) { if (songs.length) playSong(0); return; }
  audio.paused ? audio.play() : audio.pause();
}

function next() {
  if (!songs.length) return;
  let n = shuffle ? Math.floor(Math.random() * songs.length) : current + 1;
  if (n >= songs.length) n = 0;
  playSong(n);
}

function prev() {
  if (audio.currentTime > 3) { audio.currentTime = 0; return; }
  let n = current - 1;
  if (n < 0) n = songs.length - 1;
  playSong(n);
}

function closePlayer() {
  document.getElementById('player').classList.remove('show');
}

function mode(m, b) {
  document.querySelectorAll('.segment button').forEach(x => x.classList.remove('active'));
  b.classList.add('active');
  if (m === 'songs') render();
  else {
    let a = {};
    songs.forEach(s => a[s.album] = s);
    list.innerHTML = '';
    Object.entries(a).forEach(([album, s]) => {
      let r = document.createElement('div');
      r.className = 'row';
      r.innerHTML = `<img class="cover" src="${s.cover}"><div class="info"><div class="title">${esc(album)}</div><div class="artist">${esc(s.artist)}</div></div><div style="font-size:18px;color:#888">›</div>`;
      r.onclick = () => {
        document.getElementById('back').style.display = 'block';
        document.getElementById('headerTitle').textContent = album;
        render(songs.filter(x => x.album === album));
      };
      list.appendChild(r);
    });
  }
}

function tab(btn, t) {
  document.querySelectorAll('.tabs button').forEach(x => x.classList.remove('active'));
  btn.classList.add('active');
  if (t === 'search') {
    document.getElementById('search').focus();
  } else {
    render();
  }
}

function goHome() {
  document.getElementById('back').style.display = 'none';
  document.getElementById('headerTitle').textContent = 'iTunes';
  render();
}

function openQueue() {
  let q = document.getElementById('queueList');
  q.innerHTML = songs.length ? songs.map((s, i) => `<div class="qrow ${i===current?'active':''}">${i === current ? '▶ ' : ''}${i + 1}. ${esc(s.title)}<br><small style="color:#888">${esc(s.artist)}</small></div>`).join('') : '<div class="empty">Queue is empty.</div>';
  document.getElementById('queueView').classList.add('show');
}

function closeQueue() {
  document.getElementById('queueView').classList.remove('show');
}

file.onchange = e => {
  const files = [...e.target.files];
  if (!files.length) return;

  let loaded = 0;
  files.forEach(f => {
    const url = URL.createObjectURL(f);
    let song = {
      title: f.name.replace(/\.[^.]+$/, ''),
      artist: 'Unknown Artist',
      album: 'Unknown Album',
      cover: defaultCover,
      url: url
    };
    songs.push(song);

    // Read ID3 metadata and album art using jsmediatags
    if (window.jsmediatags) {
      window.jsmediatags.read(f, {
        onSuccess: function(tag) {
          const tags = tag.tags;
          if (tags.title) song.title = tags.title;
          if (tags.artist) song.artist = tags.artist;
          if (tags.album) song.album = tags.album;

          if (tags.picture) {
            const { data, format } = tags.picture;
            let base64String = "";
            for (let i = 0; i < data.length; i++) {
              base64String += String.fromCharCode(data[i]);
            }
            song.cover = `data:${format};base64,${window.btoa(base64String)}`;
          }
          render();
        },
        onError: function(error) {
          render();
        }
      });
    }
  });

  render();
  e.target.value = '';
}

audio.addEventListener('play', () => document.getElementById('playButton').textContent = '❚❚');
audio.addEventListener('pause', () => document.getElementById('playButton').textContent = '▶');
audio.addEventListener('timeupdate', () => {
  if (audio.duration) {
    document.getElementById('seek').value = audio.currentTime / audio.duration * 100;
    document.getElementById('current').textContent = fmt(audio.currentTime);
  }
});
audio.addEventListener('loadedmetadata', () => document.getElementById('duration').textContent = fmt(audio.duration));
audio.addEventListener('ended', () => next());

document.getElementById('seek').oninput = function() {
  if (audio.duration) audio.currentTime = this.value / 100 * audio.duration;
};
document.getElementById('volume').oninput = function() {
  audio.volume = this.value;
};
audio.volume = .8;

document.getElementById('search').oninput = function() {
  let q = this.value.toLowerCase();
  render(songs.filter(s => (s.title + ' ' + s.artist + ' ' + s.album).toLowerCase().includes(q)));
};

function clock() {
  let d = new Date(), h = d.getHours(), m = String(d.getMinutes()).padStart(2, '0'), ap = h >= 12 ? 'PM' : 'AM';
  h = h % 12 || 12;
  document.querySelectorAll('.time').forEach(x => x.textContent = `${h}:${m} ${ap}`);
}
clock();
setInterval(clock, 1000);

// Initialize default library demo
songs = [];
render();
</script>
</body>
</html>
