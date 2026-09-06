<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport"
      content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">

<title>Music</title>

<style>
/* =========================================================
   IPOD TOUCH / IOS 6 STYLE MUSIC PLAYER
   ========================================================= */

*{
    box-sizing:border-box;
    -webkit-tap-highlight-color:transparent;
}

html,body{
    margin:0;
    width:100%;
    height:100%;
    overflow:hidden;
    font-family:
        "Helvetica Neue",
        Helvetica,
        Arial,
        sans-serif;
    background:#111;
    color:#222;
}

body{
    display:flex;
    justify-content:center;
}

/* DEVICE */

.device{
    width:100%;
    height:100%;
    max-width:520px;
    background:#eee;
    position:relative;
    overflow:hidden;
}

/* =========================================================
   TOP NAVIGATION BAR
   ========================================================= */

.navbar{
    height:44px;
    position:absolute;
    top:0;
    left:0;
    right:0;
    z-index:20;

    display:flex;
    align-items:center;
    justify-content:center;

    background:
        linear-gradient(
            #fafafa 0%,
            #eeeeee 48%,
            #d2d2d2 52%,
            #bcbcbc 100%
        );

    border-bottom:1px solid #777;
    box-shadow:
        0 1px 2px rgba(0,0,0,.45);
}

.nav-title{
    color:#222;
    font-size:20px;
    font-weight:bold;
    text-shadow:0 1px #fff;
}

.nav-button{
    position:absolute;
    top:6px;

    height:32px;
    min-width:60px;

    padding:0 10px;

    color:#222;
    font-size:13px;
    font-weight:bold;

    border:1px solid #777;
    border-radius:6px;

    background:
        linear-gradient(
            #fff,
            #ededed 48%,
            #c7c7c7 52%,
            #ddd
        );

    box-shadow:
        inset 0 1px rgba(255,255,255,.9),
        0 1px 1px rgba(0,0,0,.25);

    text-shadow:0 1px #fff;
}

.nav-button:active{
    background:#aaa;
}

.nav-left{
    left:7px;
}

.nav-right{
    right:7px;
}

/* =========================================================
   MAIN CONTENT
   ========================================================= */

.content{
    position:absolute;
    top:44px;
    bottom:49px;
    left:0;
    right:0;

    overflow-y:auto;
    overflow-x:hidden;

    background:
        linear-gradient(
            #f7f7f7,
            #e5e5e5
        );
}

/* =========================================================
   SEARCH
   ========================================================= */

.search-container{
    padding:8px 9px;
    background:#d8d8d8;
    border-bottom:1px solid #aaa;
}

.search{
    width:100%;
    height:31px;

    border-radius:7px;
    border:1px solid #999;

    padding:0 10px;

    font-size:16px;

    background:#fff;

    box-shadow:
        inset 0 1px 3px rgba(0,0,0,.2);
}

/* =========================================================
   SECTION HEADER
   ========================================================= */

.section-header{
    height:29px;

    padding:8px 10px 5px;

    font-size:13px;
    font-weight:bold;

    color:#555;

    text-shadow:0 1px #fff;

    background:
        linear-gradient(
            #eeeeee,
            #d1d1d1
        );

    border-bottom:1px solid #aaa;
}

/* =========================================================
   SONG ROW
   ========================================================= */

.song{
    min-height:59px;

    display:flex;
    align-items:center;

    padding:6px 9px;

    position:relative;

    background:
        linear-gradient(
            #fff,
            #ededed
        );

    border-bottom:1px solid #c6c6c6;
}

.song:active{
    background:#c6c6c6;
}

.song-cover{
    width:46px;
    height:46px;

    flex:none;

    object-fit:cover;

    border-radius:3px;

    box-shadow:
        0 1px 3px rgba(0,0,0,.5);

    background:#aaa;
}

.song-info{
    min-width:0;
    flex:1;
    padding-left:10px;
}

.song-title{
    font-size:16px;
    line-height:20px;

    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.song-artist{
    font-size:13px;
    color:#777;

    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.song-arrow{
    color:#999;
    font-size:25px;
    margin-left:7px;
}

.playing{
    color:#1674b9;
    font-weight:bold;
}

/* =========================================================
   EMPTY
   ========================================================= */

.empty{
    text-align:center;
    padding:45px 20px;

    color:#777;
    font-size:15px;
}

.add-button{
    margin:10px;

    width:calc(100% - 20px);
    height:38px;

    border:1px solid #888;
    border-radius:7px;

    font-weight:bold;
    font-size:14px;

    background:
        linear-gradient(
            #fff,
            #ddd
        );

    box-shadow:
        inset 0 1px #fff,
        0 1px 2px rgba(0,0,0,.25);
}

/* =========================================================
   ALBUM GRID
   ========================================================= */

.album-grid{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:15px;

    padding:15px 12px;
}

.album{
    min-width:0;
}

.album-cover{
    width:100%;
    aspect-ratio:1;

    object-fit:cover;

    border-radius:5px;

    box-shadow:
        0 2px 5px rgba(0,0,0,.55);
}

.album-title{
    margin-top:5px;

    font-size:13px;
    font-weight:bold;

    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

.album-artist{
    font-size:11px;
    color:#777;

    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
}

/* =========================================================
   ARTIST / PLAYLIST ROW
   ========================================================= */

.simple-row{
    height:44px;

    display:flex;
    align-items:center;

    padding:0 12px;

    background:
        linear-gradient(#fff,#eee);

    border-bottom:1px solid #ccc;
}

.simple-row-title{
    flex:1;
    font-size:16px;
}

.simple-arrow{
    font-size:23px;
    color:#aaa;
}

/* =========================================================
   BOTTOM TAB BAR
   ========================================================= */

.tabs{
    position:absolute;

    left:0;
    right:0;
    bottom:0;

    height:49px;

    z-index:20;

    display:flex;

    background:
        linear-gradient(
            #555,
            #303030
        );

    border-top:1px solid #111;

    box-shadow:
        0 -1px 3px rgba(0,0,0,.5);
}

.tab{
    flex:1;

    border:0;

    background:transparent;

    color:#aaa;

    font-size:10px;

    text-shadow:0 -1px #111;
}

.tab-icon{
    display:block;

    height:25px;

    font-size:21px;

    line-height:23px;
}

.tab.active{
    color:#fff;
}

.tab.active .tab-icon{
    text-shadow:
        0 0 7px #fff;
}

/* =========================================================
   NOW PLAYING SCREEN
   ========================================================= */

.player{
    position:absolute;

    inset:0;

    z-index:100;

    display:none;
    flex-direction:column;

    background:
        linear-gradient(
            #eeeeee,
            #cfcfcf
        );
}

.player.show{
    display:flex;
}

.player-navbar{
    height:44px;

    flex:none;

    display:flex;
    align-items:center;
    justify-content:center;

    position:relative;

    background:
        linear-gradient(
            #fafafa,
            #d0d0d0
        );

    border-bottom:1px solid #777;

    font-size:18px;
    font-weight:bold;

    text-shadow:0 1px #fff;
}

.player-close{
    position:absolute;
    left:7px;

    height:31px;

    padding:0 11px;

    border:1px solid #777;
    border-radius:6px;

    background:
        linear-gradient(
            #fff,
            #ccc
        );

    font-weight:bold;
}

.player-body{
    flex:1;

    overflow:auto;

    display:flex;
    flex-direction:column;
    align-items:center;

    padding:22px 20px;
}

.player-cover{
    width:min(75vw,330px);
    height:min(75vw,330px);

    object-fit:cover;

    border-radius:5px;

    box-shadow:
        0 4px 9px rgba(0,0,0,.55);

    background:#aaa;
}

.player-title{
    margin-top:17px;

    font-size:19px;
    font-weight:bold;

    text-align:center;

    max-width:95%;
}

.player-artist{
    margin-top:3px;

    font-size:14px;
    color:#666;
}

.player-album{
    font-size:13px;
    color:#888;

    margin-top:2px;
}

/* =========================================================
   PROGRESS
   ========================================================= */

.progress{
    width:100%;
    margin-top:22px;
}

.seek{
    width:100%;

    margin:0;

    accent-color:#777;
}

.times{
    display:flex;
    justify-content:space-between;

    color:#555;
    font-size:11px;
}

/* =========================================================
   PLAYER CONTROLS
   ========================================================= */

.controls{
    width:100%;

    display:flex;
    align-items:center;
    justify-content:space-around;

    margin-top:18px;
}

.control{
    width:50px;
    height:45px;

    border:0;

    background:transparent;

    font-size:28px;

    color:#333;
}

.play-button{
    width:61px;
    height:61px;

    border-radius:50%;

    border:1px solid #777;

    background:
        linear-gradient(
            #fff,
            #d0d0d0
        );

    box-shadow:
        0 2px 4px rgba(0,0,0,.4),
        inset 0 1px #fff;

    font-size:26px;
}

.control:active,
.play-button:active{
    transform:scale(.94);
}

/* =========================================================
   PLAYER OPTIONS
   ========================================================= */

.player-options{
    width:100%;

    display:flex;
    justify-content:space-between;

    margin-top:13px;
}

.option{
    border:0;
    background:transparent;

    color:#555;

    font-size:14px;
}

.option.active{
    color:#1674b9;
    font-weight:bold;
}

/* =========================================================
   VOLUME
   ========================================================= */

.volume{
    width:100%;
    margin-top:8px;
}

.volume input{
    width:100%;
    accent-color:#777;
}

/* =========================================================
   MINI PLAYER
   ========================================================= */

.mini-player{
    position:absolute;

    left:0;
    right:0;

    bottom:49px;

    height:48px;

    z-index:15;

    display:none;
    align-items:center;

    padding:4px 8px;

    background:
        linear-gradient(
            #fafafa,
            #d4d4d4
        );

    border-top:1px solid #999;

    box-shadow:
        0 -1px 3px rgba(0,0,0,.3);
}

.mini-player.show{
    display:flex;
}

.mini-cover{
    width:39px;
    height:39px;

    object-fit:cover;

    border-radius:3px;
}

.mini-info{
    flex:1;
    min-width:0;

    padding-left:9px;
}

.mini-title{
    font-size:13px;
    font-weight:bold;

    overflow:hidden;
    white-space:nowrap;
    text-overflow:ellipsis;
}

.mini-artist{
    font-size:11px;
    color:#777;
}

.mini-play{
    border:0;
    background:transparent;

    font-size:25px;
}

/* =========================================================
   MODAL
   ========================================================= */

.modal{
    position:absolute;

    inset:0;

    z-index:200;

    display:none;

    align-items:center;
    justify-content:center;

    background:rgba(0,0,0,.45);
}

.modal.show{
    display:flex;
}

.modal-box{
    width:85%;
    max-width:350px;

    background:#eee;

    border-radius:12px;

    box-shadow:
        0 5px 25px #000;

    overflow:hidden;
}

.modal-title{
    padding:15px;

    text-align:center;

    font-size:18px;
    font-weight:bold;

    background:
        linear-gradient(#fff,#ddd);
}

.modal-row{
    padding:13px;

    text-align:center;

    border-top:1px solid #ccc;

    background:#fff;
}

.modal-row:active{
    background:#ccc;
}
</style>
</head>


<body>

<div class="device">

    <!-- =====================================================
         TOP BAR
         ===================================================== -->

    <header class="navbar">

        <button
            class="nav-button nav-left"
            id="backButton"
            style="display:none"
            onclick="goBack()">
            ‹ Atrás
        </button>

        <div
            class="nav-title"
            id="navTitle">
            Canciones
        </div>

        <button
            class="nav-button nav-right"
            onclick="openAdd()">
            +
        </button>

    </header>


    <!-- =====================================================
         CONTENT
         ===================================================== -->

    <main class="content">

        <div
            class="search-container"
            id="searchContainer">

            <input
                class="search"
                id="search"
                type="search"
                placeholder="Buscar"
                autocomplete="off">

        </div>

        <div id="contentArea"></div>

    </main>


    <!-- =====================================================
         MINI PLAYER
         ===================================================== -->

    <div
        class="mini-player"
        id="miniPlayer"
        onclick="openPlayer()">

        <img
            class="mini-cover"
            id="miniCover">

        <div class="mini-info">

            <div
                class="mini-title"
                id="miniTitle">
                Ninguna canción
            </div>

            <div
                class="mini-artist"
                id="miniArtist">
                ---
            </div>

        </div>

        <button
            class="mini-play"
            id="miniPlay"
            onclick="event.stopPropagation();togglePlay()">
            ▶
        </button>

    </div>


    <!-- =====================================================
         BOTTOM TABS
         ===================================================== -->

    <nav class="tabs">

        <button
            class="tab active"
            onclick="changeTab('songs',this)">

            <span class="tab-icon">♫</span>
            Canciones

        </button>

        <button
            class="tab"
            onclick="changeTab('artists',this)">

            <span class="tab-icon">♟</span>
            Artistas

        </button>

        <button
            class="tab"
            onclick="changeTab('albums',this)">

            <span class="tab-icon">▦</span>
            Álbumes

        </button>

        <button
            class="tab"
            onclick="changeTab('playlists',this)">

            <span class="tab-icon">☷</span>
            Listas

        </button>

        <button
            class="tab"
            onclick="changeTab('more',this)">

            <span class="tab-icon">•••</span>
            Más

        </button>

    </nav>


    <!-- =====================================================
         NOW PLAYING
         ===================================================== -->

    <section
        class="player"
        id="player">

        <header class="player-navbar">

            <button
                class="player-close"
                onclick="closePlayer()">
                ‹ Música
            </button>

            Ahora suena

        </header>

        <div class="player-body">

            <img
                class="player-cover"
                id="playerCover">

            <div
                class="player-title"
                id="playerTitle">
                Ninguna canción
            </div>

            <div
                class="player-artist"
                id="playerArtist">
                ---
            </div>

            <div
                class="player-album"
                id="playerAlbum">
                ---
            </div>


            <div class="progress">

                <input
                    class="seek"
                    id="seek"
                    type="range"
                    min="0"
                    max="100"
                    value="0">

                <div class="times">

                    <span id="currentTime">
                        0:00
                    </span>

                    <span id="totalTime">
                        0:00
                    </span>

                </div>

            </div>


            <div class="controls">

                <button
                    class="control"
                    onclick="previous()">
                    ⏮
                </button>

                <button
                    class="play-button"
                    id="playButton"
                    onclick="togglePlay()">
                    ▶
                </button>

                <button
                    class="control"
                    onclick="next()">
                    ⏭
                </button>

            </div>


            <div class="player-options">

                <button
                    class="option"
                    id="shuffleButton"
                    onclick="toggleShuffle()">
                    🔀 Aleatorio
                </button>

                <button
                    class="option"
                    id="repeatButton"
                    onclick="toggleRepeat()">
                    🔁 Repetir
                </button>

                <button
                    class="option"
                    onclick="toggleFavorite()">
                    <span id="favoriteIcon">♡</span>
                </button>

            </div>


            <div class="volume">

                <input
                    type="range"
                    id="volume"
                    min="0"
                    max="1"
                    step=".01"
                    value=".8">

            </div>

        </div>

    </section>


    <!-- =====================================================
         MODAL
         ===================================================== -->

    <div
        class="modal"
        id="modal"
        onclick="closeModal(event)">

        <div
            class="modal-box"
            onclick="event.stopPropagation()">

            <div class="modal-title">
                Añadir música
            </div>

            <div
                class="modal-row"
                onclick="chooseFiles()">
                Seleccionar archivos MP3
            </div>

            <div
                class="modal-row"
                onclick="closeModal()">
                Cancelar
            </div>

        </div>

    </div>


    <input
        id="fileInput"
        type="file"
        accept="audio/*"
        multiple
        hidden>


    <audio id="audio"></audio>

</div>


<script>

/* =========================================================
   STATE
   ========================================================= */

let songs =
    JSON.parse(
        localStorage.getItem("ipodMusicLibrary") || "[]"
    );

let currentIndex = -1;

let shuffle = false;

let repeat = false;

let currentTab = "songs";


/* =========================================================
   ELEMENTS
   ========================================================= */

const audio =
    document.getElementById("audio");

const fileInput =
    document.getElementById("fileInput");

const contentArea =
    document.getElementById("contentArea");

const search =
    document.getElementById("search");

const defaultCover =
    createDefaultCover();


/* =========================================================
   DEFAULT COVER
   ========================================================= */

function createDefaultCover(){

    return "data:image/svg+xml," +
    encodeURIComponent(`
        <svg xmlns="http://www.w3.org/2000/svg"
             width="600"
             height="600">

            <defs>
                <linearGradient
                    id="g"
                    x1="0"
                    y1="0"
                    x2="1"
                    y2="1">

                    <stop
                        offset="0"
                        stop-color="#555"/>

                    <stop
                        offset="1"
                        stop-color="#111"/>

                </linearGradient>
            </defs>

            <rect
                width="600"
                height="600"
                fill="url(#g)"/>

            <circle
                cx="300"
                cy="300"
                r="210"
                fill="#222"/>

            <circle
                cx="300"
                cy="300"
                r="65"
                fill="#777"/>

            <circle
                cx="300"
                cy="300"
                r="20"
                fill="#222"/>

        </svg>
    `);

}


/* =========================================================
   SAVE
   ========================================================= */

function save(){

    localStorage.setItem(
        "ipodMusicLibrary",
        JSON.stringify(songs)
    );

}


/* =========================================================
   ADD FILES
   ========================================================= */

function openAdd(){

    document
        .getElementById("modal")
        .classList.add("show");

}


function chooseFiles(){

    closeModal();

    fileInput.click();

}


fileInput.addEventListener(
    "change",
    function(){

        const files =
            [...this.files];

        files.forEach(file => {

            songs.push({

                title:
                    file.name
                        .replace(/\.[^/.]+$/,""),

                artist:
                    "Artista desconocido",

                album:
                    "Álbum desconocido",

                cover:
                    defaultCover,

                url:
                    URL.createObjectURL(file),

                favorite:false

            });

        });

        save();

        renderSongs();

        this.value = "";

    }
);


/* =========================================================
   RENDER SONGS
   ========================================================= */

function renderSongs(list=songs){

    document
        .getElementById("searchContainer")
        .style.display = "block";

    contentArea.innerHTML = "";

    if(!list.length){

        contentArea.innerHTML = `

            <div class="empty">

                <div style="font-size:45px">
                    ♫
                </div>

                <br>

                Tu biblioteca está vacía.

                <br><br>

                Pulsa <b>+</b> para añadir música.

            </div>

        `;

        return;

    }


    const header =
        document.createElement("div");

    header.className =
        "section-header";

    header.textContent =
        "Canciones";

    contentArea.appendChild(header);


    list.forEach(song => {

        const index =
            songs.indexOf(song);

        const row =
            document.createElement("div");

        row.className =
            "song";

        row.innerHTML = `

            <img
                class="song-cover"
                src="${song.cover}">

            <div class="song-info">

                <div
                    class="song-title
                    ${index === currentIndex
                    ? "playing"
                    : ""}">

                    ${safe(song.title)}

                </div>

                <div class="song-artist">

                    ${safe(song.artist)}

                </div>

            </div>

            <div class="song-arrow">
                ›
            </div>
        `;

        row.onclick =
            () => playSong(index);

        contentArea.appendChild(row);

    });

}


/* =========================================================
   PLAY SONG
   ========================================================= */

function playSong(index){

    if(!songs[index])
        return;

    currentIndex = index;

    const song =
        songs[index];

    audio.src =
        song.url;

    updatePlayer(song);

    audio.play();

    updatePlayButtons();

    document
        .getElementById("miniPlayer")
        .classList.add("show");

    renderCurrent();

}


/* =========================================================
   PLAYER UI
   ========================================================= */

function updatePlayer(song){

    playerCover.src =
        song.cover;

    playerTitle.textContent =
        song.title;

    playerArtist.textContent =
        song.artist;

    playerAlbum.textContent =
        song.album;

    miniCover.src =
        song.cover;

    miniTitle.textContent =
        song.title;

    miniArtist.textContent =
        song.artist;

    favoriteIcon.textContent =
        song.favorite
        ? "♥"
        : "♡";

}


function openPlayer(){

    document
        .getElementById("player")
        .classList.add("show");

}


function closePlayer(){

    document
        .getElementById("player")
        .classList.remove("show");

}


/* =========================================================
   PLAY / PAUSE
   ========================================================= */

function togglePlay(){

    if(currentIndex === -1){

        if(songs.length)
            playSong(0);

        return;

    }


    if(audio.paused){

        audio.play();

    }else{

        audio.pause();

    }

}


function updatePlayButtons(){

    const playing =
        !audio.paused;

    playButton.textContent =
        playing ? "Ⅱ" : "▶";

    miniPlay.textContent =
        playing ? "Ⅱ" : "▶";

}


/* =========================================================
   NEXT
   ========================================================= */

function next(){

    if(!songs.length)
        return;

    let index;

    if(shuffle){

        index =
            Math.floor(
                Math.random() *
                songs.length
            );

    }else{

        index =
            currentIndex + 1;

        if(index >= songs.length)
            index = 0;

    }

    playSong(index);

}


/* =========================================================
   PREVIOUS
   ========================================================= */

function previous(){

    if(!songs.length)
        return;

    if(audio.currentTime > 3){

        audio.currentTime = 0;

        return;

    }

    let index =
        currentIndex - 1;

    if(index < 0)
        index = songs.length - 1;

    playSong(index);

}


/* =========================================================
   AUDIO EVENTS
   ========================================================= */

audio.addEventListener(
    "play",
    updatePlayButtons
);

audio.addEventListener(
    "pause",
    updatePlayButtons
);


audio.addEventListener(
    "timeupdate",
    function(){

        if(!audio.duration)
            return;

        seek.value =
            (audio.currentTime /
            audio.duration) * 100;

        currentTime.textContent =
            formatTime(
                audio.currentTime
            );

    }
);


audio.addEventListener(
    "loadedmetadata",
    function(){

        totalTime.textContent =
            formatTime(audio.duration);

    }
);


audio.addEventListener(
    "ended",
    function(){

        if(repeat){

            audio.currentTime = 0;

            audio.play();

        }else{

            next();

        }

    }
);


/* =========================================================
   SEEK
   ========================================================= */

seek.addEventListener(
    "input",
    function(){

        if(!audio.duration)
            return;

        audio.currentTime =
            (this.value / 100) *
            audio.duration;

    }
);


/* =========================================================
   VOLUME
   ========================================================= */

volume.addEventListener(
    "input",
    function(){

        audio.volume =
            this.value;

    }
);

audio.volume = .8;


/* =========================================================
   SHUFFLE
   ========================================================= */

function toggleShuffle(){

    shuffle =
        !shuffle;

    shuffleButton.classList.toggle(
        "active",
        shuffle
    );

}


/* =========================================================
   REPEAT
   ========================================================= */

function toggleRepeat(){

    repeat =
        !repeat;

    repeatButton.classList.toggle(
        "active",
        repeat
    );

}


/* =========================================================
   FAVORITE
   ========================================================= */

function toggleFavorite(){

    if(currentIndex < 0)
        return;

    songs[currentIndex].favorite =
        !songs[currentIndex].favorite;

    favoriteIcon.textContent =
        songs[currentIndex].favorite
        ? "♥"
        : "♡";

    save();

}


/* =========================================================
   TABS
   ========================================================= */

function changeTab(tab,button){

    currentTab =
        tab;

    document
        .querySelectorAll(".tab")
        .forEach(x =>
            x.classList.remove("active")
        );

    button.classList.add("active");

    document
        .getElementById("backButton")
        .style.display = "none";

    search.value = "";


    if(tab === "songs"){

        navTitle.textContent =
            "Canciones";

        renderSongs();

    }


    if(tab === "artists"){

        navTitle.textContent =
            "Artistas";

        renderArtists();

    }


    if(tab === "albums"){

        navTitle.textContent =
            "Álbumes";

        renderAlbums();

    }


    if(tab === "playlists"){

        navTitle.textContent =
            "Listas";

        renderPlaylists();

    }


    if(tab === "more"){

        navTitle.textContent =
            "Más";

        renderMore();

    }

}


/* =========================================================
   ARTISTS
   ========================================================= */

function renderArtists(){

    searchContainer.style.display =
        "none";

    contentArea.innerHTML = "";

    const artists =
        [...new Set(
            songs.map(x => x.artist)
        )];

    artists.forEach(artist => {

        const row =
            document.createElement("div");

        row.className =
            "simple-row";

        row.innerHTML = `

            <div class="simple-row-title">
                ${safe(artist)}
            </div>

            <div class="simple-arrow">
                ›
            </div>

        `;

        row.onclick = () => {

            renderSongs(
                songs.filter(
                    x => x.artist === artist
                )
            );

            navTitle.textContent =
                artist;

            backButton.style.display =
                "block";

        };

        contentArea.appendChild(row);

    });

}


/* =========================================================
   ALBUMS
   ========================================================= */

function renderAlbums(){

    searchContainer.style.display =
        "none";

    contentArea.innerHTML = "";

    const grid =
        document.createElement("div");

    grid.className =
        "album-grid";

    const albums = {};

    songs.forEach(song => {

        if(!albums[song.album])
            albums[song.album] =
                song;

    });


    Object.entries(albums)
        .forEach(([album,song]) => {

            const div =
                document.createElement("div");

            div.className =
                "album";

            div.innerHTML = `

                <img
                    class="album-cover"
                    src="${song.cover}">

                <div class="album-title">
                    ${safe(album)}
                </div>

                <div class="album-artist">
                    ${safe(song.artist)}
                </div>

            `;

            div.onclick = () => {

                renderSongs(
                    songs.filter(
                        x => x.album === album
                    )
                );

                navTitle.textContent =
                    album;

                backButton.style.display =
                    "block";

            };

            grid.appendChild(div);

        });


    contentArea.appendChild(grid);

}


/* =========================================================
   PLAYLISTS
   ========================================================= */

function renderPlaylists(){

    searchContainer.style.display =
        "none";

    contentArea.innerHTML = "";


    const lists = [

        ["Todas las canciones",songs.length],

        [
            "Añadidas recientemente",
            songs.length
        ],

        [
            "Favoritos",
            songs.filter(
                x => x.favorite
            ).length
        ]

    ];


    lists.forEach(([name,count]) => {

        const row =
            document.createElement("div");

        row.className =
            "simple-row";

        row.innerHTML = `

            <div class="simple-row-title">

                ${name}

                <span
                    style="
                    color:#999;
                    font-size:12px;
                    margin-left:6px">

                    ${count}

                </span>

            </div>

            <div class="simple-arrow">
                ›
            </div>

        `;


        row.onclick = () => {

            let list = songs;

            if(name === "Favoritos"){

                list =
                    songs.filter(
                        x => x.favorite
                    );

            }

            renderSongs(list);

            navTitle.textContent =
                name;

            backButton.style.display =
                "block";

        };


        contentArea.appendChild(row);

    });

}


/* =========================================================
   MORE
   ========================================================= */

function renderMore(){

    searchContainer.style.display =
        "none";

    contentArea.innerHTML = `

        <div class="section-header">
            Biblioteca
        </div>

        <div class="simple-row">

            <div class="simple-row-title">
                Canciones
            </div>

            <div>
                ${songs.length}
            </div>

        </div>

        <div class="section-header">
            Opciones
        </div>

        <div
            class="simple-row"
            onclick="openAdd()">

            <div class="simple-row-title">
                Añadir música
            </div>

            <div class="simple-arrow">
                ›
            </div>

        </div>

        <div
            class="simple-row"
            onclick="clearLibrary()">

            <div class="simple-row-title"
                 style="color:#c00">

                Borrar biblioteca

            </div>

            <div class="simple-arrow">
                ›
            </div>

        </div>

    `;

}


/* =========================================================
   BACK
   ========================================================= */

function goBack(){

    backButton.style.display =
        "none";

    changeTab(
        currentTab,
        document.querySelector(
            ".tab.active"
        )
    );

}


/* =========================================================
   CLEAR LIBRARY
   ========================================================= */

function clearLibrary(){

    if(
        confirm(
            "¿Borrar toda la biblioteca?"
        )
    ){

        songs = [];

        currentIndex = -1;

        audio.pause();

        audio.src = "";

        save();

        renderSongs();

    }

}


/* =========================================================
   SEARCH
   ========================================================= */

search.addEventListener(
    "input",
    function(){

        const q =
            this.value
                .toLowerCase()
                .trim();

        if(!q){

            renderSongs();

            return;

        }

        renderSongs(
            songs.filter(song =>
                song.title
                    .toLowerCase()
                    .includes(q) ||

                song.artist
                    .toLowerCase()
                    .includes(q) ||

                song.album
                    .toLowerCase()
                    .includes(q)
            )
        );

    }
);


/* =========================================================
   MODAL
   ========================================================= */

function closeModal(){

    document
        .getElementById("modal")
        .classList.remove("show");

}


/* =========================================================
   FORMAT TIME
   ========================================================= */

function formatTime(seconds){

    if(
        !seconds ||
        isNaN(seconds)
    )
        return "0:00";

    const minutes =
        Math.floor(seconds / 60);

    const secondsPart =
        Math.floor(seconds % 60)
            .toString()
            .padStart(2,"0");

    return `${minutes}:${secondsPart}`;

}


/* =========================================================
   HTML ESCAPE
   ========================================================= */

function safe(text){

    return String(text)
        .replace(/&/g,"&amp;")
        .replace(/</g,"&lt;")
        .replace(/>/g,"&gt;")
        .replace(/"/g,"&quot;")
        .replace(/'/g,"&#039;");

}


/* =========================================================
   CURRENT VIEW
   ========================================================= */

function renderCurrent(){

    if(currentTab === "songs")
        renderSongs();

}


/* =========================================================
   START
   ========================================================= */

renderSongs();

</script>

</body>
</html>
