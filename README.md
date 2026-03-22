# kumlink
Kudrick234, [23.03.2026 01:23]
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>🎵 KudriLink | Музыкальный сервис</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        :root {
            --bg-primary: #0a0a0f;
            --bg-secondary: #0f0f17;
            --bg-card: #1a1a24;
            --bg-input: #2a2a34;
            --accent: #e83e8c;
            --accent-blue: #3a86ff;
            --text-primary: #ffffff;
            --text-secondary: #a0a0b0;
            --border: #2a2a34;
            --gradient: linear-gradient(135deg, #e83e8c, #3a86ff);
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            overflow-x: hidden;
        }

        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: var(--bg-input); }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 10px; }

        /* Login Screen */
        .login-screen {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: radial-gradient(circle at 30% 10%, #1a1a2a, #0a0a0f);
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            gap: 20px;
        }

        .login-card {
            background: rgba(26, 26, 36, 0.95);
            backdrop-filter: blur(20px);
            border-radius: 48px;
            padding: 40px 35px;
            width: 90%;
            max-width: 420px;
            text-align: center;
            border: 1px solid rgba(232, 62, 140, 0.3);
            box-shadow: 0 25px 50px -12px rgba(0,0,0,0.5);
        }

        .login-card h2 {
            background: linear-gradient(135deg, #e83e8c, #3a86ff);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-size: 36px;
            font-weight: 800;
            margin-bottom: 25px;
        }

        .invite-info {
            background: rgba(0,0,0,0.3);
            border-radius: 30px;
            padding: 12px;
            margin-bottom: 20px;
            font-size: 13px;
            color: #ffd700;
        }

        .login-card input {
            width: 100%;
            padding: 16px 20px;
            margin: 12px 0;
            background: var(--bg-input);
            border: 1px solid var(--border);
            border-radius: 40px;
            color: white;
            font-size: 16px;
            transition: all 0.3s;
        }

        .login-card input:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 2px rgba(232, 62, 140, 0.2);
        }

        .login-card button {
            width: 100%;
            padding: 16px;
            background: var(--gradient);
            border: none;
            border-radius: 40px;
            color: white;
            font-weight: bold;
            cursor: pointer;
            font-size: 16px;
            margin-top: 15px;
            transition: transform 0.2s;
        }

        .login-card button:active { transform: scale(0.98); }

        .hidden { display: none; }

        /* Main App */
        .app {
            display: none;
            min-height: 100vh;
            padding-bottom: 100px;
        }

Kudrick234, [23.03.2026 01:23]
/* Header */
        .header {
            background: rgba(15, 15, 23, 0.95);
            backdrop-filter: blur(10px);
            padding: 15px 25px;
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(232, 62, 140, 0.2);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            font-size: 28px;
            font-weight: 800;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            cursor: pointer;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .user-avatar {
            width: 45px;
            height: 45px;
            background: var(--gradient);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 22px;
        }

        .user-nick { font-weight: 600; }
        .creator-badge { background: var(--accent); font-size: 10px; padding: 2px 8px; border-radius: 20px; margin-left: 8px; }
        .logout-btn { background: rgba(255,68,68,0.8); border: none; padding: 8px 20px; border-radius: 30px; color: white; cursor: pointer; }

        /* Tabs */
        .tabs {
            display: flex;
            gap: 12px;
            padding: 20px 25px;
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--border);
            overflow-x: auto;
        }

        .tab-btn {
            padding: 12px 28px;
            background: var(--bg-input);
            border: none;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-weight: 600;
            white-space: nowrap;
        }
        .tab-btn.active { background: var(--gradient); }

        .upload-section, .playlist-section, .tracks-section, .favorites-section, .artists-section {
            margin: 20px 25px;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            flex-wrap: wrap;
            gap: 15px;
        }

        .section-header h2 {
            font-size: 24px;
            font-weight: 700;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .create-playlist-btn, .add-fav-btn {
            background: var(--gradient);
            border: none;
            padding: 10px 24px;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-weight: 600;
        }

        .upload-area {
            border: 2px dashed var(--accent);
            border-radius: 24px;
            padding: 50px;
            text-align: center;
            cursor: pointer;
            background: var(--bg-card);
        }
        .upload-area:hover { background: var(--bg-input); }

        .playlists-grid, .artists-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
        }

        .playlist-card, .artist-card {
            background: var(--bg-card);
            border-radius: 24px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s;
            border: 1px solid var(--border);
        }
        .playlist-card:hover, .artist-card:hover { transform: translateY(-5px); border-color: var(--accent); }

        .playlist-cover, .artist-cover {

Kudrick234, [23.03.2026 01:23]
width: 100%;
            height: 150px;
            background: var(--gradient);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            margin-bottom: 15px;
        }

        .playlist-title, .artist-name { font-size: 18px; font-weight: 700; margin-bottom: 5px; }
        .playlist-count, .artist-tracks { font-size: 12px; color: var(--text-secondary); }

        /* Track Items */
        .track-item {
            background: var(--bg-card);
            border-radius: 20px;
            padding: 15px 20px;
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            border: 1px solid var(--border);
        }
        .track-item:hover { border-color: var(--accent); }

        .track-info { flex: 1; }
        .track-name { font-weight: 700; font-size: 16px; margin-bottom: 4px; }
        .track-artist { font-size: 12px; color: var(--text-secondary); }

        .track-actions { display: flex; gap: 10px; }
        .play-track-btn, .fav-track-btn, .delete-track-btn {
            background: var(--bg-input);
            border: none;
            padding: 8px 20px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
        }
        .play-track-btn { background: var(--accent); }
        .fav-track-btn.active { background: var(--accent); }
        .delete-track-btn { background: #ff4444; }

        /* Music Player */
        .music-player {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(15,15,23,0.98);
            backdrop-filter: blur(10px);
            border-top: 1px solid var(--accent);
            padding: 15px 25px;
            display: flex;
            align-items: center;
            gap: 20px;
            flex-wrap: wrap;
            z-index: 100;
        }

        .player-info { flex: 1; min-width: 180px; }
        .player-title { font-weight: 700; font-size: 16px; }
        .player-artist { font-size: 12px; color: var(--text-secondary); }

        .player-controls { display: flex; gap: 15px; }
        .player-btn {
            background: var(--bg-input);
            border: none;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            font-size: 20px;
            cursor: pointer;
            color: white;
        }

        .player-progress { flex: 2; min-width: 200px; }
        .progress-bar { width: 100%; height: 5px; background: var(--bg-input); border-radius: 3px; cursor: pointer; }
        .progress-fill { width: 0%; height: 100%; background: var(--accent); border-radius: 3px; }
        .time-info { display: flex; justify-content: space-between; font-size: 11px; margin-top: 6px; color: var(--text-secondary); }

        @media (max-width: 600px) {
            .music-player { flex-direction: column; text-align: center; }
            .player-progress { width: 100%; }
            .playlists-grid, .artists-grid { grid-template-columns: 1fr; }
            .tabs { padding: 15px; }
            .tab-btn { padding: 8px 20px; font-size: 14px; }
        }
    </style>
</head>
<body>
    <!-- Login Screen -->
    <div class="login-screen" id="loginScreen">
        <div class="login-card">
            <h2>🎵 KudriLink</h2>
            <div class="invite-info">
                🔑 Введите инвайт-код для регистрации<br>
                <span style="color:#e83e8c;">KUDRIK2025</span> — код создателя<br>
                <span style="color:#3a86ff;">KUDRIK2026</span> — обычный код
            </div>
            <div id="inviteStep">

Kudrick234, [23.03.2026 01:23]
<input type="text" id="inviteCodeInput" placeholder="Инвайт-код" autocomplete="off">
                <button id="checkInviteBtn">🔑 Войти по коду</button>
            </div>
            <div id="regStep" class="hidden">
                <input type="email" id="emailInput" placeholder="Ваш email" autocomplete="off">
                <input type="text" id="nickInput" placeholder="Ваш ник (уникальный)" autocomplete="off">
                <input type="text" id="userNameInput" placeholder="Ваше имя">
                <button id="registerBtn">🚀 Зарегистрироваться</button>
                <button id="backToInviteBtn" style="background:#333;">← Назад</button>
            </div>
        </div>
    </div>

    <!-- Main App -->
    <div class="app" id="app">
        <div class="header">
            <div class="logo" onclick="location.reload()">🎵 KudriLink</div>
            <div class="user-info">
                <div class="user-avatar" id="userAvatar">🎧</div>
                <div>
                    <span class="user-nick" id="displayNick"></span>
                    <span id="creatorBadge" style="display:none;" class="creator-badge">👑 Создатель</span>
                </div>
                <button class="logout-btn" id="logoutBtn">Выйти</button>
            </div>
        </div>

        <div class="tabs">
            <button class="tab-btn active" data-tab="playlists">📀 Плейлисты</button>
            <button class="tab-btn" data-tab="tracks">🎵 Все треки</button>
            <button class="tab-btn" data-tab="favorites">❤️ Избранное</button>
            <button class="tab-btn" data-tab="artists">⭐ Исполнители</button>
            <button class="tab-btn" data-tab="upload">⬆️ Загрузить</button>
        </div>

        <!-- Upload Section -->
        <div class="upload-section" id="uploadTab" style="display: none;">
            <div class="upload-area" id="uploadArea">
                <div style="font-size: 56px;">🎵</div>
                <div style="margin: 20px 0; font-size: 18px;">Нажми или перетащи файл</div>
                <div style="font-size: 13px; color: var(--text-secondary);">MP3, WAV, OGG до 20MB</div>
                <input type="file" id="musicFileInput" accept="audio/*" style="display: none;">
            </div>
            <div style="margin-top: 20px;">
                <input type="text" id="trackArtist" placeholder="Исполнитель" style="width: 100%; padding: 14px; background: var(--bg-input); border: none; border-radius: 40px; color: white; margin-bottom: 12px;">
                <button id="uploadBtn" style="width: 100%; padding: 14px; background: var(--gradient); border: none; border-radius: 40px; color: white; font-weight: bold;">Загрузить трек</button>
            </div>
        </div>

        <!-- Playlists Section -->
        <div class="playlist-section" id="playlistsTab">
            <div class="section-header">
                <h2>📀 Мои плейлисты</h2>
                <button class="create-playlist-btn" id="createPlaylistBtn">➕ Создать плейлист</button>
            </div>
            <div class="playlists-grid" id="playlistsGrid"></div>
        </div>

        <!-- Tracks Section -->
        <div class="tracks-section" id="tracksTab" style="display: none;">
            <div class="section-header">
                <h2>🎵 Все треки</h2>
                <button class="add-fav-btn" id="showAllFavBtn">❤️ Мои любимые</button>
            </div>
            <div id="tracksList"></div>
        </div>

        <!-- Favorites Section -->
        <div class="favorites-section" id="favoritesTab" style="display: none;">
            <div class="section-header">
                <h2>❤️ Избранные треки</h2>
                <button class="add-fav-btn" id="clearFavBtn">🗑️ Очистить</button>
            </div>
            <div id="favoritesList"></div>
        </div>

Kudrick234, [23.03.2026 01:23]
<!-- Artists Section -->
        <div class="artists-section" id="artistsTab" style="display: none;">
            <div class="section-header">
                <h2>⭐ Популярные исполнители</h2>
            </div>
            <div class="artists-grid" id="artistsGrid"></div>
        </div>

        <!-- Music Player -->
        <div class="music-player" id="musicPlayer">
            <div class="player-info">
                <div class="player-title" id="currentTrackName">Выберите трек</div>
                <div class="player-artist" id="currentTrackArtist">-</div>
            </div>
            <div class="player-controls">
                <button class="player-btn" id="prevBtn">⏮</button>
                <button class="player-btn" id="playPauseBtn">▶️</button>
                <button class="player-btn" id="nextBtn">⏭</button>
            </div>
            <div class="player-progress">
                <div class="progress-bar" id="progressBar">
                    <div class="progress-fill" id="progressFill"></div>
                </div>
                <div class="time-info">
                    <span id="currentTime">0:00</span>
                    <span id="durationTime">0:00</span>
                </div>
            </div>
        </div>
    </div>

    <script>
        // ============= ДОПУСТИМЫЕ ИНВАЙТ-КОДЫ =============
        const VALID_INVITES = {
            "KUDRIK2025": { role: "creator", name: "Создатель" },
            "KUDRIK2026": { role: "user", name: "Пользователь" }
        };

        // ============= СИСТЕМА АККАУНТОВ =============
        let currentUser = null;
        let allUsers = JSON.parse(localStorage.getItem('kudrilink_users') || '[]');
        let allTracks = JSON.parse(localStorage.getItem('kudrilink_global_tracks') || '[]');
        let playlists = [];
        let favorites = [];
        let currentTrackIndex = 0;
        let audio = new Audio();
        let isPlaying = false;
        let currentInviteRole = null;

        // Проверка уникальности ника
        function isNickUnique(nick, excludeEmail = null) {
            return !allUsers.some(u => u.nick === nick && u.email !== excludeEmail);
        }

        // ============= ГЕНЕРАЦИЯ 200+ ТРЕКОВ =============
        const artists = [
            "Моргенштерн", "Кишлак", "Скриптонит", "Face", "Oxxxymiron", "Баста", "Noize MC", "ATL", "Хаски", 
            "GONE.Fludd", "LSP", "Фараон", "Дора", "Майот", "SALUKI", "Kai Angel", "SEEMEE", "White Punk",
            "Big Baby Tape", "Kizaru", "ЛСП", "Элджей", "Feduk", "Макс Корж", "T-Fest", "JONY", "Rauf & Faik"
        ];
        
        const trackNames = [
            "Дует", "Новый Мерин", "Розовое вино", "Плачу на техно", "Пушка", "Я хочу", "Грустная сука", 
            "Хавчик", "Кисонька", "Виражи", "Кредо", "Трап", "Космос", "Феникс", "Девочка с каре", "Малышка",
            "Красный флаг", "Бумеранг", "Патрон", "Москва любит", "Кино", "Без тебя", "На чиле", "Прованс"
        ];

        function generateTracks() {
            const tracks = [];
            for (let i = 0; i < 220; i++) {
                const artist = artists[Math.floor(Math.random() * artists.length)];
                const track = trackNames[Math.floor(Math.random() * trackNames.length)];
                tracks.push({
                    id: Date.now() + i,
                    name: ${track},
                    artist: artist,
                    url: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3",
                    duration: ${Math.floor(2 + Math.random() * 3)}:${Math.floor(10 + Math.random() * 50)},
                    addedBy: "system",
                    addedByNick: "Система"
                });
            }
            return tracks;
        }

        // Загрузка данных пользователя

Kudrick234, [23.03.2026 01:23]
function loadUserData() {
            if (!currentUser) return;
            
            const userData = JSON.parse(localStorage.getItem(kudrilink_user_${currentUser.email}) || '{"playlists":[],"favorites":[]}');
            playlists = userData.playlists || [];
            favorites = userData.favorites || [];
            
            if (playlists.length === 0) {
                playlists = [
                    { id: Date.now(), name: "🔥 Мой плейлист", tracks: allTracks.slice(0, 15).map(t => t.id), cover: "🔥" },
                    { id: Date.now()+1, name: "🎸 Любимое", tracks: allTracks.slice(10, 25).map(t => t.id), cover: "🎸" }
                ];
                saveUserData();
            }
            
            renderPlaylists();
            renderFavorites();
        }

        function saveUserData() {
            if (!currentUser) return;
            localStorage.setItem(kudrilink_user_${currentUser.email}, JSON.stringify({
                playlists: playlists,
                favorites: favorites
            }));
        }

        function saveGlobalTracks() {
            localStorage.setItem('kudrilink_global_tracks', JSON.stringify(allTracks));
        }

        // Инициализация глобальных треков
        if (allTracks.length === 0) {
            allTracks = generateTracks();
            saveGlobalTracks();
        }

        // UI Рендер
        function renderPlaylists() {
            const grid = document.getElementById('playlistsGrid');
            if (!grid) return;
            grid.innerHTML = playlists.map(playlist => {
                const trackCount = playlist.tracks.filter(id => allTracks.find(t => t.id === id)).length;
                return 
                    <div class="playlist-card" onclick="openPlaylist(${playlist.id})">
                        <div class="playlist-cover">${playlist.cover || '🎵'}</div>
                        <div class="playlist-title">${escapeHtml(playlist.name)}</div>
                        <div class="playlist-count">${trackCount} треков</div>
                    </div>
                ;
            }).join('');
        }

        function renderTracks(tracks = allTracks) {
            const container = document.getElementById('tracksList');
            if (!container) return;
            container.innerHTML = tracks.map((track, idx) => 
                <div class="track-item">
                    <div class="track-info">
                        <div class="track-name">${escapeHtml(track.name)}</div>
                        <div class="track-artist">${escapeHtml(track.artist)}</div>
                        <div class="track-duration">${track.duration}</div>
                        <div style="font-size:10px; color:var(--text-secondary); margin-top:4px;">📌 Добавил: ${track.addedByNick || 'Система'}</div>
                    </div>
                    <div class="track-actions">
                        <button class="play-track-btn" onclick="playTrack(${allTracks.indexOf(track)})">▶️</button>
                        <button class="fav-track-btn ${favorites.includes(track.id) ? 'active' : ''}" onclick="toggleFavorite(${track.id})">❤️</button>
                        ${currentUser && (currentUser.role === "creator" || track.addedBy === currentUser.email) ? <button class="delete-track-btn" onclick="deleteTrack(${track.id})">🗑️</button> : ''}
                    </div>
                </div>
            ).join('');
        }

        function renderFavorites() {
            const container = document.getElementById('favoritesList');
            if (!container) return;
            const favTracks = allTracks.filter(t => favorites.includes(t.id));
            if (favTracks.length === 0) {
                container.innerHTML = '<div style="text-align:center; padding:40px; color:var(--text-secondary);">❤️ Нет избранных треков</div>';

Kudrick234, [23.03.2026 01:23]
return;
            }
            container.innerHTML = favTracks.map((track, idx) => 
                <div class="track-item">
                    <div class="track-info">
                        <div class="track-name">${escapeHtml(track.name)}</div>
                        <div class="track-artist">${escapeHtml(track.artist)}</div>
                        <div class="track-duration">${track.duration}</div>
                    </div>
                    <div class="track-actions">
                        <button class="play-track-btn" onclick="playTrack(${allTracks.indexOf(track)})">▶️</button>
                        <button class="fav-track-btn active" onclick="toggleFavorite(${track.id})">❤️</button>
                    </div>
                </div>
            ).join('');
        }

        function renderArtists() {
            const container = document.getElementById('artistsGrid');
            if (!container) return;
            const artistStats = {};
            allTracks.forEach(t => {
                artistStats[t.artist] = (artistStats[t.artist] || 0) + 1;
            });
            const topArtists = Object.entries(artistStats).sort((a, b) => b[1] - a[1]).slice(0, 18);
            container.innerHTML = topArtists.map(([artist, count]) => 
                <div class="artist-card" onclick="filterByArtist('${escapeHtml(artist)}')">
                    <div class="artist-cover">🎤</div>
                    <div class="artist-name">${escapeHtml(artist)}</div>
                    <div class="artist-tracks">${count} треков</div>
                </div>
            ).join('');
        }

        window.filterByArtist = (artist) => {
            const filtered = allTracks.filter(t => t.artist === artist);
            renderTracks(filtered);
            document.querySelector('.tab-btn[data-tab="tracks"]').click();
        };

        window.openPlaylist = (playlistId) => {
            const playlist = playlists.find(p => p.id === playlistId);
            if (!playlist) return;
            const tracksInPlaylist = allTracks.filter(t => playlist.tracks.includes(t.id));
            renderTracks(tracksInPlaylist);
            document.querySelector('.tab-btn[data-tab="tracks"]').click();
        };

        window.playTrack = (index) => {
            const track = allTracks[index];
            if (!track) return;
            currentTrackIndex = index;
            audio.src = track.url;
            audio.play();
            isPlaying = true;
            document.getElementById('playPauseBtn').innerHTML = '⏸';
            document.getElementById('currentTrackName').innerText = track.name;
            document.getElementById('currentTrackArtist').innerText = track.artist;
            
            audio.addEventListener('timeupdate', updateProgress);
            audio.addEventListener('loadedmetadata', () => {
                const minutes = Math.floor(audio.duration / 60);
                const seconds = Math.floor(audio.duration % 60);
                document.getElementById('durationTime').innerText = ${minutes}:${seconds.toString().padStart(2, '0')};
            });
        };

        function updateProgress() {
            const percent = (audio.currentTime / audio.duration) * 100;
            document.getElementById('progressFill').style.width = percent + '%';
            const minutes = Math.floor(audio.currentTime / 60);
            const seconds = Math.floor(audio.currentTime % 60);
            document.getElementById('currentTime').innerText = ${minutes}:${seconds.toString().padStart(2, '0')};
        }

        window.toggleFavorite = (trackId) => {
            const index = favorites.indexOf(trackId);
            if (index === -1) {
                favorites.push(trackId);
            } else {
                favorites.splice(index, 1);
            }
            saveUserData();
            renderTracks();
            renderFavorites();
        };

Kudrick234, [23.03.2026 01:23]
window.deleteTrack = (trackId) => {
            if (confirm('Удалить трек?')) {
                allTracks = allTracks.filter(t => t.id !== trackId);
                playlists.forEach(p => {
                    p.tracks = p.tracks.filter(id => id !== trackId);
                });
                favorites = favorites.filter(id => id !== trackId);
                saveGlobalTracks();
                saveUserData();
                renderTracks();
                renderPlaylists();
                renderFavorites();
                renderArtists();
            }
        };

        function addTrack(name, artist, url, duration) {
            const newTrack = {
                id: Date.now(),
                name: name,
                artist: artist || 'Неизвестен',
                url: url,
                duration: duration || '3:00',
                addedBy: currentUser.email,
                addedByNick: currentUser.nick
            };
            allTracks.unshift(newTrack);
            saveGlobalTracks();
            renderTracks();
            renderPlaylists();
            renderArtists();
            alert(✅ "${name}" добавлен в библиотеку!);
        }

        function addPlaylist(name) {
            const newPlaylist = {
                id: Date.now(),
                name: name,
                tracks: [],
                cover: '🎵'
            };
            playlists.push(newPlaylist);
            saveUserData();
            renderPlaylists();
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        // ============= РЕГИСТРАЦИЯ ПО ИНВАЙТ-КОДУ =============
        document.getElementById('checkInviteBtn').onclick = () => {
            const code = document.getElementById('inviteCodeInput').value.trim().toUpperCase();
            
            if (!VALID_INVITES[code]) {
                alert('❌ Неверный инвайт-код! Доступ запрещён.');
                return;
            }
            
            currentInviteRole = VALID_INVITES[code].role;
            document.getElementById('inviteStep').classList.add('hidden');
            document.getElementById('regStep').classList.remove('hidden');
        };

        document.getElementById('backToInviteBtn').onclick = () => {
            document.getElementById('regStep').classList.add('hidden');
            document.getElementById('inviteStep').classList.remove('hidden');
            document.getElementById('emailInput').value = '';
            document.getElementById('nickInput').value = '';
            document.getElementById('userNameInput').value = '';
        };

        document.getElementById('registerBtn').onclick = () => {
            const email = document.getElementById('emailInput').value.trim();
            const nick = document.getElementById('nickInput').value.trim();
            const name = document.getElementById('userNameInput').value.trim() || nick;
            
            if (!email || !email.includes('@')) {
                alert('❌ Введите корректный email');
                return;
            }
            if (!nick) {
                alert('❌ Введите ник');
                return;
            }
            if (!isNickUnique(nick)) {
                alert('❌ Этот ник уже занят! Выберите другой');
                return;
            }
            if (!currentInviteRole) {
                alert('❌ Ошибка: нет инвайт-кода');
                return;
            }
            
            currentUser = { 
                email: email, 
                nick: nick,
                name: name,
                avatar: '🎧',
                role: currentInviteRole
            };
            
            allUsers.push({ email: email, nick: nick, name: name, role: currentInviteRole });

Kudrick234, [23.03.2026 01:23]
localStorage.setItem('kudrilink_users', JSON.stringify(allUsers));
            localStorage.setItem('kudrilink_current_user', JSON.stringify(currentUser));
            
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('app').style.display = 'block';
            document.getElementById('displayNick').innerText = currentUser.nick;
            document.getElementById('userAvatar').innerText = currentUser.avatar;
            
            if (currentUser.role === 'creator') {
                document.getElementById('creatorBadge').style.display = 'inline';
            }
            
            loadUserData();
            renderTracks();
            renderArtists();
        };

        // ============= ЗАГРУЗКА МУЗЫКИ =============
        let pendingFile = null;
        document.getElementById('uploadArea').onclick = () => document.getElementById('musicFileInput').click();
        document.getElementById('musicFileInput').onchange = (e) => {
            pendingFile = e.target.files[0];
            if (pendingFile) {
                document.getElementById('uploadArea').innerHTML = <div style="font-size: 56px;">✅</div><div style="margin: 20px 0;">${pendingFile.name}</div>;
            }
        };
        
        document.getElementById('uploadBtn').onclick = () => {
            if (!pendingFile) {
                alert('❌ Выберите файл');
                return;
            }
            const artist = document.getElementById('trackArtist').value.trim() || 'Неизвестен';
            const reader = new FileReader();
            reader.onload = (e) => {
                const url = e.target.result;
                addTrack(pendingFile.name.replace('.mp3', '').replace('.wav', ''), artist, url, '3:00');
                document.getElementById('uploadArea').innerHTML = <div style="font-size: 56px;">🎵</div><div style="margin: 20px 0;">Нажми или перетащи файл</div><div style="font-size: 13px;">MP3, WAV, OGG до 20MB</div>;
                document.getElementById('trackArtist').value = '';
                pendingFile = null;
            };
            reader.readAsDataURL(pendingFile);
        };

        // ============= ПЛЕЙЛИСТЫ =============
        document.getElementById('createPlaylistBtn').onclick = () => {
            const name = prompt('Название плейлиста:');
            if (name) addPlaylist(name);
        };

        document.getElementById('clearFavBtn').onclick = () => {
            if (confirm('Удалить все избранные треки?')) {
                favorites = [];
                saveUserData();
                renderTracks();
                renderFavorites();
            }
        };

        document.getElementById('showAllFavBtn').onclick = () => {
            document.querySelector('.tab-btn[data-tab="favorites"]').click();
        };

        // ============= ПЛЕЕР =============
        document.getElementById('playPauseBtn').onclick = () => {
            if (isPlaying) {
                audio.pause();
                document.getElementById('playPauseBtn').innerHTML = '▶️';
            } else {
                audio.play();
                document.getElementById('playPauseBtn').innerHTML = '⏸';
            }
            isPlaying = !isPlaying;
        };

        document.getElementById('prevBtn').onclick = () => {
            if (currentTrackIndex > 0) playTrack(currentTrackIndex - 1);
        };

        document.getElementById('nextBtn').onclick = () => {
            if (currentTrackIndex < allTracks.length - 1) playTrack(currentTrackIndex + 1);
        };

        document.getElementById('progressBar').onclick = (e) => {
            const rect = e.target.getBoundingClientRect();
            const percent = (e.clientX - rect.left) / rect.width;
            audio.currentTime = percent * audio.duration;
        };

Kudrick234, [23.03.2026 01:23]
// ============= ТАБЫ =============
        document.querySelectorAll('.tab-btn').forEach(btn => {
            btn.onclick = () => {
                document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                const tab = btn.dataset.tab;
                document.getElementById('uploadTab').style.display = tab === 'upload' ? 'block' : 'none';
                document.getElementById('playlistsTab').style.display = tab === 'playlists' ? 'block' : 'none';
                document.getElementById('tracksTab').style.display = tab === 'tracks' ? 'block' : 'none';
                document.getElementById('favoritesTab').style.display = tab === 'favorites' ? 'block' : 'none';
                document.getElementById('artistsTab').style.display = tab === 'artists' ? 'block' : 'none';
                if (tab === 'tracks') renderTracks();
                if (tab === 'playlists') renderPlaylists();
                if (tab === 'favorites') renderFavorites();
                if (tab === 'artists') renderArtists();
            };
        });

        document.getElementById('logoutBtn').onclick = () => {
            localStorage.removeItem('kudrilink_current_user');
            location.reload();
        };

        // Автовход
        const savedUser = localStorage.getItem('kudrilink_current_user');
        if (savedUser) {
            currentUser = JSON.parse(savedUser);
            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('app').style.display = 'block';
            document.getElementById('displayNick').innerText = currentUser.nick;
            document.getElementById('userAvatar').innerText = currentUser.avatar || '🎧';
            
            if (currentUser.role === 'creator') {
                document.getElementById('creatorBadge').style.display = 'inline';
            }
            
            loadUserData();
            renderTracks();
            renderArtists();
        }
    </script>
</body>
</html>
