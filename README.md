<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>iPod Music</title>

<style>
* {
    box-sizing: border-box;
    -webkit-tap-highlight-color: transparent;
}

body {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", Arial, sans-serif;
    background: #111;
    color: #222;
    overflow: hidden;
}

.app {
    width: 100vw;
    height: 100vh;
    max-width: 520px;
    margin: auto;
    background: #f7f7f7;
    display: flex;
    flex-direction: column;
}

/* TOP BAR */

.topbar {
    height: 50px;
    flex-shrink: 0;
    background: linear-gradient(#fafafa, #d8d8d8);
    border-bottom: 1px solid #aaa;
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    box-shadow: 0 1px 3px #777;
    z-index: 5;
}

.topbar h1 {
    font-size: 20px;
    margin: 0;
    font-weight: 600;
}

.back {
    position: absolute;
    left: 10px;
    border: 1px solid #888;
    border-radius: 5px;
    padding: 6px 11px;
    color: #333;
    background: linear-gradient(#fff,#ccc);
    font-weight: bold;
    display: none;
}

/* CONTENT */

.content {
    flex: 1;
    overflow-y: auto;
    padding-bottom: 75px;
}

.search {
    margin: 10px;
    width: calc(100% - 20px);
    border-radius: 9px;
    border: 1px solid #aaa;
    padding: 9px 12px;
    font-size: 16px;
    background: white;
}

.section {
    padding: 8px 12px;
    font-size: 13px;
    color: #777;
    font-weight: bold;
    text-transform: uppercase;
}

/* SONG LIST */

.song {
    height: 62px;
    display: flex;
    align-items: center;
    padding: 7px 12px;
    border-top: 1px solid #ddd;
    background: linear-gradient(#fff,#eeeeee);
    cursor: pointer;
}

.song:active {
    background: #d5d5d5;
}

.cover-small {
    width: 48px;
    height: 48px;
    object-fit: cover;
    border-radius: 4px;
    margin-right: 12px;
    background: #ccc;
    box-shadow: 0 1px 3px #777;
}

.song-info {
    min-width: 0;
    flex: 1;
}

.song-title {
    font-size: 16px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.song-artist {
    color: #777;
    font-size: 13px;
    margin-top: 3px;
}

.playing {
    color: #1674c8;
    font-weight: bold;
}

/* ALBUM GRID */

.grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
    padding: 15px;
}

.album {
    cursor: pointer;
}

.album img {
    width: 100%;
    aspect-ratio: 1;
    object-fit: cover;
    border-radius: 4px;
    box-shadow: 0 2px 5px #777;
}

.album-name {
    font-size: 14px;
    font-weight: bold;
    margin-top: 6px;
}

.album-artist {
    font-size: 12px;
    color: #777;
}

/* NOW PLAYING */

.now-playing {
    position: absolute;
    inset: 0;
    background: linear-gradient(#f8f8f8,#d9d9d9);
    z-index: 10;
    display: none;
    flex-direction: column;
}

.now-header {
    height: 50px;
    background: linear-gradient(#fafafa,#d1d1d1);
    border-bottom: 1px solid #aaa;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
}

.close-player {
    position: absolute;
    left: 10px;
    border: 1px solid #888;
    border-radius: 5px;
    padding: 6px 12px;
    background: linear-gradient(#fff,#ccc);
}

.player-body {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 30px 25px;
}

.big-cover {
    width: min(75vw, 330px);
    height: min(75vw, 330px);
    object-fit: cover;
    border-radius: 5px;
    box-shadow: 0 5px 15px #777;
    background: #bbb;
}

.track-title {
    margin-top: 25px;
    font-size: 22px;
    font-weight: bold;
    text-align: center;
}

.track-artist {
    color: #777;
    margin-top: 5px;
    font-size: 16px;
}

.progress {
    width: 100%;
    margin-top: 25px;
}

.time {
    display: flex;
    justify-content: space-between;
    font-size: 12px;
    color: #666;
}

input[type=range] {
    width: 100%;
    accent-color: #777;
}

.controls {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin-top: 20px;
}

.control {
    border: 0;
    background: transparent;
    font-size: 30px;
    cursor: pointer;
}

.play {
    width: 65px;
    height: 65px;
    border-radius: 50%;
    border: 1px solid #888;
    background: linear-gradient(#fff,#ccc);
    box-shadow: 0 2px 4px #888;
    font-size: 28px;
}

.extra-controls {
    display: flex;
    justify-content: space-around;
    width: 100%;
    margin-top: 20px;
}

.extra-controls button {
    border: 0;
    background: transparent;
    font-size: 20px;
    color: #666;
}

.active {
    color: #1674c8 !important;
}

/* BOTTOM NAV */

.bottom {
    height: 62px;
    flex-shrink: 0;
    position: fixed;
    bottom: 0;
    width: min(100vw,520px);
    display: flex;
    background: linear-gradient(#444,#111);
    border-top: 1px solid #666;
    z-index: 6;
}

.nav {
    flex: 1;
    border: 0;
    background: transparent;
    color: #ddd;
    font-size: 11px;
    cursor: pointer;
}

.nav span {
    display: block;
    font-size: 23px;
    margin-bottom: 3px;
}

.nav.active-nav {
    color: white;
    background: rgba(255,255,255,.12);
}

/* LOAD */

.load {
    margin: 15px;
    border: 1px solid #999;
    border-radius: 6px;
    background: linear-gradient(#fff,#ccc);
    padding: 10px;
    width: calc(100% - 30px);
    font-weight: bold;
}
</style>
</head>

<body>

<div class="app">

    <div class="topbar">
        <button class="back" id="backBtn">‹ Atrás</button>
        <h1 id="pageTitle">Canciones</h1>
    </div>

    <main class="content" id="content">

        <input
            class="search"
            id="search"
            placeholder="Buscar"
            type="search"
        >

        <button class="load" onclick="fileInput.click()">
            ＋ Agregar archivos MP3
        </button>

        <input
            id="fileInput"
            type="file"
            accept="audio/*"
            multiple
            hidden
        >

        <div id="library"></div>

    </main>

    <nav class="bottom">

        <button class="nav active-nav" onclick="showPage('songs',this)">
            <span>♫</span>
            Canciones
        </button>

        <button class="nav" onclick="showPage('albums',this)">
            <span>▦</span>
            Álbumes
        </button>

        <button class="nav" onclick="showPage('artists',this)">
            <span>♟</span>
            Artistas
        </button>

        <button class="nav" onclick="showPage('favorites',this)">
            <span>♥</span>
            Favoritos
        </button>

    </nav>

</div>


<!-- NOW PLAYING -->

<div class="now-playing" id="player">

    <div class="now-header">
        <button class="close-player" onclick="closePlayer()">‹ Biblioteca</button>
        Ahora suena
    </div>

    <div class="player-body">

        <img
            id="bigCover"
            class="big-cover"
            src=""
            alt="Portada"
        >

        <div class="track-title" id="trackTitle">
            Ninguna canción
        </div>

        <div class="track-artist" id="trackArtist">
            ---
        </div>

        <div class="progress">

            <input
                id="seek"
                type="range"
                min="0"
                max="100"
                value="0"
            >

            <div class="time">
                <span id="currentTime">0:00</span>
                <span id="duration">0:00</span>
            </div>

        </div>

        <div class="controls">

            <button class="control" onclick="previous()">⏮</button>

            <button class="control play" id="playButton" onclick="togglePlay()">
                ▶
            </button>

            <button class="control" onclick="next()">⏭</button>

        </div>

        <div class="extra-controls">

            <button id="shuffleBtn" onclick="toggleShuffle()">
                🔀
            </button>

            <button id="repeatBtn" onclick="toggleRepeat()">
                🔁
            </button>

            <button onclick="audio.volume = Math.min(1,audio.volume+.1)">
                🔊
            </button>

            <button onclick="audio.volume = Math.max(0,audio.volume-.1)">
                🔉
            </button>

        </div>

    </div>

</div>


<audio id="audio"></audio>


<script>

/* =========================
   DATABASE
========================= */

let songs = JSON.parse(localStorage.getItem("ipodSongs") || "[]");

let currentIndex = -1;
let shuffle = false;
let repeat = false;

const audio = document.getElementById("audio");

const defaultCover =
"https://dummyimage.com/600x600/cccccc/555555.png&text=♪";


/* =========================
   SAVE
========================= */

function save() {
    localStorage.setItem(
        "ipodSongs",
        JSON.stringify(songs)
    );
}


/* =========================
   ADD MP3
========================= */

fileInput.addEventListener("change", e => {

    const files = [...e.target.files];

    files.forEach(file => {

        const url = URL.createObjectURL(file);

        songs.push({

            title: file.name
                .replace(/\.[^/.]+$/, ""),

            artist: "Artista desconocido",

            album: "Álbum desconocido",

            cover: defaultCover,

            url: url,

            favorite: false

        });

    });

    save();
    renderSongs();

});


/* =========================
   FORMAT TIME
========================= */

function formatTime(seconds) {

    if (!seconds || isNaN(seconds))
        return "0:00";

    const min = Math.floor(seconds / 60);
    const sec = Math.floor(seconds % 60)
        .toString()
        .padStart(2,"0");

    return `${min}:${sec}`;

}


/* =========================
   SONG LIST
========================= */

function renderSongs(list = songs) {

    const library =
        document.getElementById("library");

    library.innerHTML = "";

    if (!list.length) {

        library.innerHTML = `
            <div style="
                text-align:center;
                padding:50px 20px;
                color:#888;
            ">
                No hay canciones todavía.
                <br><br>
                Agrega algunos MP3.
            </div>
        `;

        return;
    }

    list.forEach((song,index) => {

        const realIndex =
            songs.indexOf(song);

        const div =
            document.createElement("div");

        div.className = "song";

        div.innerHTML = `

            <img
                class="cover-small"
                src="${song.cover}"
            >

            <div class="song-info">

                <div class="song-title
                    ${realIndex === currentIndex ? "playing":""}">
                    ${escapeHTML(song.title)}
                </div>

                <div class="song-artist">
                    ${escapeHTML(song.artist)}
                </div>

            </div>

            <div style="font-size:20px">
                ${song.favorite ? "♥" : "♡"}
            </div>

        `;

        div.onclick = () =>
            playSong(realIndex);

        library.appendChild(div);

    });

}


/* =========================
   PLAY
========================= */

function playSong(index) {

    if (!songs[index])
        return;

    currentIndex = index;

    const song = songs[index];

    audio.src = song.url;

    document.getElementById("bigCover")
        .src = song.cover;

    document.getElementById("trackTitle")
        .textContent = song.title;

    document.getElementById("trackArtist")
        .textContent = song.artist;

    document.getElementById("player")
        .style.display = "flex";

    audio.play();

    document.getElementById("playButton")
        .textContent = "Ⅱ";

    renderSongs();

}


/* =========================
   PLAY / PAUSE
========================= */

function togglePlay() {

    if (currentIndex === -1) {

        if (songs.length)
            playSong(0);

        return;
    }

    if (audio.paused) {

        audio.play();

        playButton.textContent = "Ⅱ";

    } else {

        audio.pause();

        playButton.textContent = "▶";

    }

}


/* =========================
   NEXT
========================= */

function next() {

    if (!songs.length)
        return;

    let index;

    if (shuffle) {

        index =
            Math.floor(Math.random()*songs.length);

    } else {

        index =
            currentIndex + 1;

        if (index >= songs.length)
            index = 0;

    }

    playSong(index);

}


/* =========================
   PREVIOUS
========================= */

function previous() {

    if (!songs.length)
        return;

    let index =
        currentIndex - 1;

    if (index < 0)
        index = songs.length - 1;

    playSong(index);

}


/* =========================
   AUDIO EVENTS
========================= */

audio.addEventListener("timeupdate", () => {

    if (!audio.duration)
        return;

    seek.value =
        (audio.currentTime /
        audio.duration) * 100;

    currentTime.textContent =
        formatTime(audio.currentTime);

});

audio.addEventListener("loadedmetadata", () => {

    duration.textContent =
        formatTime(audio.duration);

});

audio.addEventListener("ended", () => {

    if (repeat) {

        audio.currentTime = 0;
        audio.play();

    } else {

        next();

    }

});


/* =========================
   SEEK
========================= */

seek.addEventListener("input", () => {

    if (!audio.duration)
        return;

    audio.currentTime =
        (seek.value / 100) *
        audio.duration;

});


/* =========================
   SHUFFLE
========================= */

function toggleShuffle() {

    shuffle = !shuffle;

    shuffleBtn.classList.toggle(
        "active",
        shuffle
    );

}


/* =========================
   REPEAT
========================= */

function toggleRepeat() {

    repeat = !repeat;

    repeatBtn.classList.toggle(
        "active",
        repeat
    );

}


/* =========================
   CLOSE
========================= */

function closePlayer() {

    document.getElementById("player")
        .style.display = "none";

}


/* =========================
   SEARCH
========================= */

search.addEventListener("input", () => {

    const query =
        search.value.toLowerCase();

    const filtered =
        songs.filter(song =>
            song.title.toLowerCase()
                .includes(query) ||
            song.artist.toLowerCase()
                .includes(query) ||
            song.album.toLowerCase()
                .includes(query)
        );

    renderSongs(filtered);

});


/* =========================
   NAVIGATION
========================= */

function showPage(page,button) {

    document
        .querySelectorAll(".nav")
        .forEach(x =>
            x.classList.remove("active-nav")
        );

    button.classList.add("active-nav");

    const title =
        document.getElementById("pageTitle");

    if (page === "songs") {

        title.textContent = "Canciones";
        search.style.display = "block";
        renderSongs();

    }

    if (page === "albums") {

        title.textContent = "Álbumes";
        search.style.display = "none";
        renderAlbums();

    }

    if (page === "artists") {

        title.textContent = "Artistas";
        search.style.display = "none";
        renderArtists();

    }

    if (page === "favorites") {

        title.textContent = "Favoritos";
        search.style.display = "none";

        renderSongs(
            songs.filter(x => x.favorite)
        );

    }

}


/* =========================
   ALBUMS
========================= */

function renderAlbums() {

    const library =
        document.getElementById("library");

    library.innerHTML =
        `<div class="grid"></div>`;

    const grid =
        library.querySelector(".grid");

    const albums = {};

    songs.forEach(song => {

        if (!albums[song.album])
            albums[song.album] = song;

    });

    Object.entries(albums)
        .forEach(([name,song]) => {

        const div =
            document.createElement("div");

        div.className = "album";

        div.innerHTML = `

            <img src="${song.cover}">

            <div class="album-name">
                ${escapeHTML(name)}
            </div>

            <div class="album-artist">
                ${escapeHTML(song.artist)}
            </div>

        `;

        div.onclick = () => {

            renderSongs(
                songs.filter(x =>
                    x.album === name
                )
            );

            document.getElementById("pageTitle")
                .textContent = name;

        };

        grid.appendChild(div);

    });

}


/* =========================
   ARTISTS
========================= */

function renderArtists() {

    const library =
        document.getElementById("library");

    library.innerHTML = "";

    const artists = {};

    songs.forEach(song => {

        artists[song.artist] =
            (artists[song.artist] || 0) + 1;

    });

    Object.entries(artists)
        .forEach(([artist,count]) => {

        const div =
            document.createElement("div");

        div.className = "song";

        div.innerHTML = `

            <div style="
                width:48px;
                height:48px;
                border-radius:50%;
                background:#ccc;
                display:flex;
                align-items:center;
                justify-content:center;
                font-size:25px;
                margin-right:12px;
            ">
                ♫
            </div>

            <div class="song-info">

                <div class="song-title">
                    ${escapeHTML(artist)}
                </div>

                <div class="song-artist">
                    ${count} canción${count !== 1 ? "es":""}
                </div>

            </div>

        `;

        div.onclick = () => {

            renderSongs(
                songs.filter(x =>
                    x.artist === artist
                )
            );

            pageTitle.textContent = artist;

        };

        library.appendChild(div);

    });

}


/* =========================
   HTML SECURITY
========================= */

function escapeHTML(text) {

    return String(text)
        .replace(/&/g,"&amp;")
        .replace(/</g,"&lt;")
        .replace(/>/g,"&gt;")
        .replace(/"/g,"&quot;")
        .replace(/'/g,"&#039;");

}


/* =========================
   START
========================= */

renderSongs();

</script>

</body>
</html>
