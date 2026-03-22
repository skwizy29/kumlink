# kumlink
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

        ::-webkit-scrollbar { width: 8px; height: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-input); border-radius: 10px; }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 10px; }

        .app {
            min-height: 100vh;
            padding-bottom: 100px;
        }

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
            font-size: 26px;
            font-weight: 800;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            cursor: pointer;
        }

        .tabs {
            display: flex;
            gap: 10px;
            padding: 15px 20px;
            background: var(--bg-secondary);
            border-bottom: 1px solid var(--border);
            overflow-x: auto;
            scrollbar-width: thin;
        }

        .tab-btn {
            padding: 10px 24px;
            background: var(--bg-input);
            border: none;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-weight: 600;
            font-size: 14px;
            white-space: nowrap;
            transition: all 0.2s;
        }
        .tab-btn.active { background: var(--gradient); }

        .upload-section, .playlist-section, .tracks-section, .favorites-section, .artists-section {
            margin: 20px;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 12px;
        }

        .section-header h2 {
            font-size: 22px;
            font-weight: 700;
            background: var(--gradient);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .create-playlist-btn, .add-fav-btn {
            background: var(--gradient);
            border: none;
            padding: 8px 20px;
            border-radius: 40px;
            color: white;
            cursor: pointer;
            font-weight: 600;
            font-size: 14px;
        }

Kudrick234, [23.03.2026 01:40]
.upload-area {
            border: 2px dashed var(--accent);
            border-radius: 24px;
            padding: 40px 20px;
            text-align: center;
            cursor: pointer;
            background: var(--bg-card);
            transition: all 0.3s;
        }
        .upload-area:hover { background: var(--bg-input); border-color: var(--accent-blue); }

        .playlists-grid, .artists-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 20px;
        }

        .playlist-card, .artist-card {
            background: var(--bg-card);
            border-radius: 20px;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s;
            border: 1px solid var(--border);
        }
        .playlist-card:hover, .artist-card:hover { transform: translateY(-4px); border-color: var(--accent); }

        .playlist-cover, .artist-cover {
            width: 100%;
            height: 140px;
            background: var(--gradient);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 44px;
            margin-bottom: 12px;
        }

        .playlist-title, .artist-name { font-size: 17px; font-weight: 700; margin-bottom: 4px; }
        .playlist-count, .artist-tracks { font-size: 12px; color: var(--text-secondary); }

        .track-item {
            background: var(--bg-card);
            border-radius: 16px;
            padding: 14px 18px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            border: 1px solid var(--border);
            transition: all 0.2s;
        }
        .track-item:hover { border-color: var(--accent); }

        .track-info { flex: 1; min-width: 150px; }
        .track-name { font-weight: 700; font-size: 15px; margin-bottom: 4px; }
        .track-artist { font-size: 12px; color: var(--text-secondary); }

        .track-actions { display: flex; gap: 8px; flex-wrap: wrap; }
        .play-track-btn, .fav-track-btn, .delete-track-btn {
            background: var(--bg-input);
            border: none;
            padding: 6px 16px;
            border-radius: 30px;
            color: white;
            cursor: pointer;
            font-size: 13px;
            transition: all 0.2s;
        }
        .play-track-btn { background: var(--accent); }
        .fav-track-btn.active { background: var(--accent); }
        .delete-track-btn { background: #ff4444; }

        .music-player {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(15,15,23,0.98);
            backdrop-filter: blur(10px);
            border-top: 1px solid var(--accent);
            padding: 12px 20px;
            display: flex;
            align-items: center;
            gap: 15px;
            flex-wrap: wrap;
            z-index: 100;
        }

        .player-info { flex: 1; min-width: 150px; }
        .player-title { font-weight: 700; font-size: 14px; }
        .player-artist { font-size: 11px; color: var(--text-secondary); }

        .player-controls { display: flex; gap: 12px; }
        .player-btn {
            background: var(--bg-input);
            border: none;
            width: 38px;
            height: 38px;
            border-radius: 50%;
            font-size: 18px;
            cursor: pointer;
            color: white;
            transition: all 0.2s;
        }
        .player-btn:hover { background: var(--accent); }

        .player-progress { flex: 2; min-width: 180px; }
        .progress-bar { width: 100%; height: 4px; background: var(--bg-input); border-radius: 3px; cursor: pointer; }

Kudrick234, [23.03.2026 01:40]
.progress-fill { width: 0%; height: 100%; background: var(--accent); border-radius: 3px; }
        .time-info { display: flex; justify-content: space-between; font-size: 10px; margin-top: 4px; color: var(--text-secondary); }

        @media (min-width: 1200px) {
            .upload-section, .playlist-section, .tracks-section, .favorites-section, .artists-section {
                max-width: 1400px;
                margin: 25px auto;
            }
            .playlists-grid, .artists-grid { grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); }
        }

        @media (max-width: 768px) {
            .header { padding: 12px 18px; }
            .logo { font-size: 22px; }
            .tabs { padding: 12px 15px; gap: 8px; }
            .tab-btn { padding: 8px 18px; font-size: 13px; }
            .section-header h2 { font-size: 18px; }
            .playlist-cover, .artist-cover { height: 120px; font-size: 36px; }
            .track-item { padding: 12px 15px; }
        }

        @media (max-width: 480px) {
            .playlists-grid, .artists-grid { grid-template-columns: 1fr; }
            .track-actions { width: 100%; justify-content: flex-end; }
        }
    </style>
</head>
<body>
    <div class="app">
        <div class="header">
            <div class="logo" onclick="location.reload()">🎵 KudriLink</div>
        </div>

        <div class="tabs">
            <button class="tab-btn active" data-tab="playlists">📀 Плейлисты</button>
            <button class="tab-btn" data-tab="tracks">🎵 Все треки</button>
            <button class="tab-btn" data-tab="favorites">❤️ Избранное</button>
            <button class="tab-btn" data-tab="artists">⭐ Исполнители</button>
            <button class="tab-btn" data-tab="upload">⬆️ Загрузить</button>
        </div>

        <div class="upload-section" id="uploadTab" style="display: none;">
            <div class="upload-area" id="uploadArea">
                <div style="font-size: 52px;">🎵</div>
                <div style="margin: 15px 0; font-size: 16px;">Нажми или перетащи файл</div>
                <div style="font-size: 12px; color: var(--text-secondary);">MP3, WAV, OGG до 20MB</div>
                <input type="file" id="musicFileInput" accept="audio/*" style="display: none;">
            </div>
            <div style="margin-top: 18px;">
                <input type="text" id="trackArtist" placeholder="Исполнитель" style="width: 100%; padding: 12px 18px; background: var(--bg-input); border: none; border-radius: 40px; color: white; margin-bottom: 12px;">
                <button id="uploadBtn" style="width: 100%; padding: 12px; background: var(--gradient); border: none; border-radius: 40px; color: white; font-weight: bold;">Загрузить трек</button>
            </div>
        </div>

        <div class="playlist-section" id="playlistsTab">
            <div class="section-header">
                <h2>📀 Мои плейлисты</h2>
                <button class="create-playlist-btn" id="createPlaylistBtn">➕ Создать плейлист</button>
            </div>
            <div class="playlists-grid" id="playlistsGrid"></div>
        </div>

        <div class="tracks-section" id="tracksTab" style="display: none;">
            <div class="section-header">
                <h2>🎵 Все треки</h2>
                <button class="add-fav-btn" id="showAllFavBtn">❤️ Мои любимые</button>
            </div>
            <div id="tracksList"></div>
        </div>

        <div class="favorites-section" id="favoritesTab" style="display: none;">
            <div class="section-header">
                <h2>❤️ Избранное</h2>
                <button class="add-fav-btn" id="clearFavBtn">🗑️ Очистить</button>
            </div>
            <div id="favoritesList"></div>
        </div>

        <div class="artists-section" id="artistsTab" style="display: none;">
            <div class="section-header">
                <h2>⭐ Исполнители</h2>
            </div>
            <div class="artists-grid" id="artistsGrid"></div>
        </div>

Kudrick234, [23.03.2026 01:40]
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
        // ============= ПОЛНЫЙ СПИСОК ТРЕКОВ =============
        const artistsData = [
            { name: "Моргенштерн", tracks: ["Дует", "Новый Мерин", "Розовое вино", "Плачу на техно", "Пушка", "Я хочу", "Грустная сука", "Хавчик", "Кисонька", "Виражи", "Кредо", "Трап", "Космос", "Феникс", "Девочка с каре"] },
            { name: "Кишлак", tracks: ["Автомат", "Кино", "Без тебя", "На чиле", "Прованс", "Катана", "Мне пох", "Зима", "Танцы", "Ауф"] },
            { name: "Скриптонит", tracks: ["Положение", "Это любовь", "Танцуй сама", "Космос", "Звезда", "Невеста", "Сложно", "Мультибренд"] },
            { name: "Face", tracks: ["Юморист", "Бургер", "Я роняю запад", "Москва любит", "Красный флаг", "Бумеранг", "Патрон"] },
            { name: "Oxxxymiron", tracks: ["Где нас нет", "Кто убил Марка?", "Полигон", "Биполярочка", "Не с начала", "Хоп-механика"] },
            { name: "Баста", tracks: ["Сансара", "Выпускной", "Мама", "Солнцем", "Любовь", "Без тебя"] },
            { name: "Хаски", tracks: ["Пуля-дура", "Убей меня", "Черным-черно", "Глаза", "Бесы", "Пироман"] },
            { name: "GONE.Fludd", tracks: ["Кубик льда", "UFO", "Проснулся в темноте", "Чувствую", "Мамбл"] },
            { name: "Big Baby Tape", tracks: ["Gimme the Loot", "Hood", "Bandz", "Trap Luv", "Платина"] },
            { name: "Kizaru", tracks: ["Дежавю", "Черный Mercedes", "Тебя любил", "Money", "Тени"] },
            { name: "Элджей", tracks: ["Розовое вино", "Минимал", "Дикая", "Улетай", "Sayonara"] },
            { name: "Feduk", tracks: ["Розовое вино", "Моряк", "Плов", "Ой да", "Хулиган"] },
            { name: "Макс Корж", tracks: ["Малый повзрослел", "Тает дым", "Слово пацана", "Жить в кайф", "Неважно"] }
        ];

        // Генерация треков
        let allTracks = JSON.parse(localStorage.getItem('kudrilink_tracks') || '[]');
        
        if (allTracks.length === 0) {
            let id = 1;
            for (let artist of artistsData) {
                for (let track of artist.tracks) {
                    allTracks.push({
                        id: id++,
                        name: track,
                        artist: artist.name,
                        url: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3",
                        duration: ${Math.floor(2 + Math.random() * 3)}:${Math.floor(10 + Math.random() * 50)}
                    });
                }
            }
            localStorage.setItem('kudrilink_tracks', JSON.stringify(allTracks));
        }

        let playlists = JSON.parse(localStorage.getItem('kudrilink_playlists') || '[]');
        let favorites = JSON.parse(localStorage.getItem('kudrilink_favorites') || '[]');
        let currentTrackIndex = 0;
        let audio = new Audio();
        let isPlaying = false;

        if (playlists.length === 0) {

Kudrick234, [23.03.2026 01:40]
playlists = [
                { id: Date.now(), name: "🔥 Мои любимые", tracks: [], cover: "🔥" },
                { id: Date.now() + 1, name: "🎸 Хиты", tracks: allTracks.slice(0, 10).map(t => t.id), cover: "🎸" }
            ];
            localStorage.setItem('kudrilink_playlists', JSON.stringify(playlists));
        }

        function saveAll() {
            localStorage.setItem('kudrilink_tracks', JSON.stringify(allTracks));
            localStorage.setItem('kudrilink_playlists', JSON.stringify(playlists));
            localStorage.setItem('kudrilink_favorites', JSON.stringify(favorites));
        }

        function renderPlaylists() {
            const grid = document.getElementById('playlistsGrid');
            if (!grid) return;
            if (playlists.length === 0) {
                grid.innerHTML = '<div style="text-align:center; padding:40px; color:var(--text-secondary); grid-column:1/-1;">📀 Нет плейлистов. Создайте первый!</div>';
                return;
            }
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
            if (tracks.length === 0) {
                container.innerHTML = '<div style="text-align:center; padding:40px; color:var(--text-secondary);">🎵 Нет треков. Загрузите музыку!</div>';
                return;
            }
            container.innerHTML = tracks.map((track, idx) => 
                <div class="track-item">
                    <div class="track-info">
                        <div class="track-name">${escapeHtml(track.name)}</div>
                        <div class="track-artist">${escapeHtml(track.artist)}</div>
                        <div class="track-duration">${track.duration}</div>
                    </div>
                    <div class="track-actions">
                        <button class="play-track-btn" onclick="playTrack(${allTracks.indexOf(track)})">▶️</button>
                        <button class="fav-track-btn ${favorites.includes(track.id) ? 'active' : ''}" onclick="toggleFavorite(${track.id})">❤️</button>
                        <button class="delete-track-btn" onclick="deleteTrack(${track.id})">🗑️</button>
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
                return;
            }
            container.innerHTML = favTracks.map((track, idx) => `
                <div class="track-item">
                    <div class="track-info">
                        <div class="track-name">${escapeHtml(track.name)}</div>
                        <div class="track-artist">${escapeHtml(track.artist)}</div>
                        <div class="track-duration">${track.duration}</div>
                    </div>

Kudrick234, [23.03.2026 01:40]
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
            if (topArtists.length === 0) {
                container.innerHTML = '<div style="text-align:center; padding:40px; color:var(--text-secondary); grid-column:1/-1;">⭐ Нет исполнителей</div>';
                return;
            }
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
            document.getElementById('currentTime').innerText = ${minutes}:${seconds.toString().padStart(2, '0')}`;
        }

        window.toggleFavorite = (trackId) => {
            const index = favorites.indexOf(trackId);
            if (index === -1) {
                favorites.push(trackId);
            } else {
                favorites.splice(index, 1);
            }
            saveAll();
            renderTracks();
            renderFavorites();
        };

        window.deleteTrack = (trackId) => {
            if (confirm('Удалить трек?')) {

Kudrick234, [23.03.2026 01:40]
allTracks = allTracks.filter(t => t.id !== trackId);
                playlists.forEach(p => {
                    p.tracks = p.tracks.filter(id => id !== trackId);
                });
                favorites = favorites.filter(id => id !== trackId);
                saveAll();
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
                duration: duration || '3:00'
            };
            allTracks.unshift(newTrack);
            saveAll();
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
            saveAll();
            renderPlaylists();
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        // Загрузка музыки
        let pendingFile = null;
        document.getElementById('uploadArea').onclick = () => document.getElementById('musicFileInput').click();
        document.getElementById('musicFileInput').onchange = (e) => {
            pendingFile = e.target.files[0];
            if (pendingFile) {
                document.getElementById('uploadArea').innerHTML = <div style="font-size: 52px;">✅</div><div style="margin: 15px 0;">${pendingFile.name}</div>;
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
                document.getElementById('uploadArea').innerHTML = <div style="font-size: 52px;">🎵</div><div style="margin: 15px 0;">Нажми или перетащи файл</div><div style="font-size: 12px;">MP3, WAV, OGG до 20MB</div>;
                document.getElementById('trackArtist').value = '';
                pendingFile = null;
            };
            reader.readAsDataURL(pendingFile);
        };

        document.getElementById('createPlaylistBtn').onclick = () => {
            const name = prompt('Название плейлиста:');
            if (name) addPlaylist(name);
        };

        document.getElementById('clearFavBtn').onclick = () => {
            if (confirm('Удалить все избранные треки?')) {
                favorites = [];
                saveAll();
                renderTracks();
                renderFavorites();
            }
        };

        document.getElementById('showAllFavBtn').onclick = () => {
            document.querySelector('.tab-btn[data-tab="favorites"]').click();
        };

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

Kudrick234, [23.03.2026 01:40]
document.getElementById('nextBtn').onclick = () => {
            if (currentTrackIndex < allTracks.length - 1) playTrack(currentTrackIndex + 1);
        };

        document.getElementById('progressBar').onclick = (e) => {
            const rect = e.target.getBoundingClientRect();
            const percent = (e.clientX - rect.left) / rect.width;
            audio.currentTime = percent * audio.duration;
        };

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

        renderPlaylists();
        renderTracks();
        renderArtists();
        renderFavorites();
    </script>
</body>
</html>

