<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clipz - Auto Video Clipping</title>

    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/lucide@latest"></script>
    <script src="https://www.youtube.com/iframe_api"></script>

    <style>
        body { font-family: 'Inter', sans-serif; background-color: #020617; color: #f8fafc; }
        .clip-list-scrollbar::-webkit-scrollbar { width: 6px; }
        .clip-list-scrollbar::-webkit-scrollbar-track { background: #1e293b; }
        .clip-list-scrollbar::-webkit-scrollbar-thumb { background: #475569; border-radius: 3px; }
        .clip-list-scrollbar::-webkit-scrollbar-thumb:hover { background: #64748b; }
        .btn-disabled { cursor: not-allowed; opacity: 0.5; }
        .loader, .spinner {
            border: 4px solid #384252;
            border-top: 4px solid #38bdf8;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        .loader { width: 48px; height: 48px; }
        .spinner { width: 16px; height: 16px; border-width: 2px; }
        @keyframes spin { 0% { transform: rotate(0deg); } 100% { transform: rotate(360deg); } }
        .modal-content { animation: slideUp 0.3s ease-out; }
        @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
    </style>
</head>
<body class="antialiased">

    <div class="min-h-screen flex flex-col">
        <header class="bg-slate-900/50 backdrop-blur-sm border-b border-slate-800 sticky top-0 z-30">
            <div class="container mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex items-center justify-between h-16">
                    <div class="flex items-center space-x-3">
                        <div class="bg-sky-500 p-2 rounded-lg">
                            <i data-lucide="clapperboard" class="w-6 h-6 text-white"></i>
                        </div>
                        <h1 class="text-2xl font-bold text-white tracking-tight">Clipz</h1>
                        <span class="bg-emerald-700 text-emerald-300 text-xs font-medium px-2.5 py-0.5 rounded-full">Beta Z4</span>
                    </div>
                </div>
            </div>
        </header>

        <main class="flex-grow container mx-auto p-4 sm:p-6 lg:p-8">
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 h-full">
                
                <div class="lg:col-span-2 flex flex-col gap-6">
                    <div id="videoPlayerContainer" class="bg-slate-900 rounded-2xl aspect-video flex items-center justify-center border border-slate-800 overflow-hidden">
                        <div id="videoPlaceholder" class="text-center text-slate-500">
                            <i data-lucide="video" class="w-16 h-16 mx-auto"></i>
                            <p class="mt-2">Video player akan muncul di sini.</p>
                        </div>
                        <div id="youtubePlayer" class="w-full h-full hidden"></div>
                    </div>

                    <div class="bg-slate-900 p-4 rounded-2xl border border-slate-800 flex flex-col gap-4">
                        <div class="flex flex-col sm:flex-row items-center gap-3">
                            <div class="relative w-full flex items-center">
                                <i data-lucide="youtube" class="w-6 h-6 text-red-500 absolute left-3 pointer-events-none"></i>
                                <input id="ytInput" type="text" placeholder="Tempelkan link YouTube di sini..." class="w-full pl-12 pr-4 py-2 bg-slate-800 text-white rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-sky-500 transition">
                            </div>
                            <button id="loadVideoBtn" class="w-full sm:w-auto px-5 py-2 bg-blue-600 hover:bg-blue-700 text-white rounded-lg font-semibold transition whitespace-nowrap">
                                Muat Video
                            </button>
                        </div>
                        <div id="errorMessage" class="text-red-400 text-sm mt-1 hidden"></div>
                        <div class="border-t border-slate-800 my-2"></div>
                        <div class="flex flex-wrap items-center gap-3">
                            <button id="autoClipBtn" class="flex items-center gap-2 bg-sky-500 hover:bg-sky-600 text-white font-semibold px-4 py-2 rounded-lg transition btn-disabled" disabled>
                                <i data-lucide="sparkles" class="w-4 h-4"></i> Auto Clip (Simulasi)
                            </button>
                            <button id="deleteAllBtn" class="flex items-center gap-2 bg-red-500/20 hover:bg-red-500/40 text-red-300 font-semibold px-4 py-2 rounded-lg transition btn-disabled" disabled>
                                <i data-lucide="trash-2" class="w-4 h-4"></i> Hapus Semua
                            </button>
                        </div>
                    </div>
                </div>

                <div class="bg-slate-900 rounded-2xl p-6 border border-slate-800 flex flex-col h-[85vh] lg:h-auto">
                    <div class="flex-shrink-0">
                        <h2 class="text-xl font-bold text-white">Rekomendasi Klip</h2>
                        <p class="text-sm text-slate-400 mt-1 mb-4">Momen penting yang ditemukan akan muncul di sini.</p>
                    </div>
                    
                    <div id="clipListContainer" class="flex-grow overflow-y-auto clip-list-scrollbar -mr-3 pr-3 relative">
                        <div id="clipList" class="space-y-4"></div>
                        <div id="statusOverlay" class="absolute inset-0 flex flex-col items-center justify-center text-center text-slate-500 bg-slate-900/80 backdrop-blur-sm rounded-lg transition-opacity duration-300 hidden">
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>
    
    <div id="deleteModal" class="fixed inset-0 z-50 flex items-center justify-center bg-black/60 p-4 hidden">
        <div class="bg-slate-800 rounded-xl shadow-lg border border-slate-700 w-full max-w-sm modal-content">
            <div class="p-6 text-center">
                <div class="w-12 h-12 bg-red-500/10 rounded-full flex items-center justify-center mx-auto mb-4">
                    <i data-lucide="alert-triangle" class="w-6 h-6 text-red-400"></i>
                </div>
                <h3 id="modalTitle" class="text-lg font-semibold text-white"></h3>
                <p id="modalMessage" class="text-sm text-slate-400 mt-2"></p>
            </div>
            <div class="grid grid-cols-2 gap-3 p-4 bg-slate-900/50 rounded-b-xl">
                <button id="modalCancelBtn" class="px-4 py-2 bg-slate-700 hover:bg-slate-600 text-white rounded-lg font-semibold transition">Batal</button>
                <button id="modalConfirmBtn" class="px-4 py-2 bg-red-600 hover:bg-red-700 text-white rounded-lg font-semibold transition">Hapus</button>
            </div>
        </div>
    </div>

    <script>
        // --- State ---
        let currentVideoId = null;
        let currentVideoTitle = "";
        let clipsData = [];
        let deletionHandler = null;
        let player; 
        let videoDuration = 0;
        const BACKEND_URL = 'http://localhost:3000'; // URL Dapur kita

        function onYouTubeIframeAPIReady() {}

        document.addEventListener('DOMContentLoaded', () => {
            lucide.createIcons();

            const ytInput = document.getElementById('ytInput');
            const loadVideoBtn = document.getElementById('loadVideoBtn');
            const errorMessage = document.getElementById('errorMessage');
            const videoPlaceholder = document.getElementById('videoPlaceholder');
            const autoClipBtn = document.getElementById('autoClipBtn');
            const deleteAllBtn = document.getElementById('deleteAllBtn');
            const clipList = document.getElementById('clipList');
            const statusOverlay = document.getElementById('statusOverlay');
            const deleteModal = document.getElementById('deleteModal');
            const modalTitle = document.getElementById('modalTitle');
            const modalMessage = document.getElementById('modalMessage');
            const modalConfirmBtn = document.getElementById('modalConfirmBtn');
            const modalCancelBtn = document.getElementById('modalCancelBtn');

            const setStatus = (type, message = '') => {
                statusOverlay.classList.remove('hidden');
                let content = '';
                switch (type) {
                    case 'loading': content = `<div class="loader"></div><p class="mt-4 font-semibold text-sky-400">Membuat klip...</p><p class="text-sm">${message}</p>`; break;
                    case 'empty': content = `<i data-lucide="film" class="w-16 h-16"></i><p class="mt-4 font-semibold">Belum Ada Klip</p><p class="text-sm">Masukkan link YouTube untuk memulai.</p>`; break;
                    case 'error': content = `<i data-lucide="alert-circle" class="w-16 h-16 text-red-400"></i><p class="mt-4 font-semibold">Terjadi Kesalahan</p><p class="text-sm">${message}</p>`; break;
                }
                statusOverlay.innerHTML = content;
                lucide.createIcons();
            };

            const hideStatus = () => statusOverlay.classList.add('hidden');
            
            const updateButtonsState = () => {
                const hasVideo = !!currentVideoId;
                const hasClips = clipsData.length > 0;
                autoClipBtn.disabled = !hasVideo;
                deleteAllBtn.disabled = !hasClips;
                [autoClipBtn, deleteAllBtn].forEach(btn => btn.classList.toggle('btn-disabled', btn.disabled));
            };

            const showError = (message) => { errorMessage.textContent = message; errorMessage.classList.remove('hidden'); };
            const hideError = () => errorMessage.classList.add('hidden');

            const getYouTubeVideoId = (url) => {
                const patterns = [/(?:https?:\/\/)?(?:www\.)?youtube\.com\/watch\?v=([^&]+)/, /(?:https?:\/\/)?(?:www\.)?youtu\.be\/([^?]+)/];
                for (const pattern of patterns) {
                    const match = url.match(pattern);
                    if (match && match[1]) return match[1];
                }
                return null;
            };

            const createPlayer = (videoId) => {
                videoPlaceholder.classList.add('hidden');
                document.getElementById('youtubePlayer').classList.remove('hidden');
                if (player) { player.loadVideoById(videoId); } 
                else {
                    player = new YT.Player('youtubePlayer', {
                        height: '100%', width: '100%', videoId: videoId,
                        playerVars: { 'playsinline': 1 },
                        events: { 'onStateChange': onPlayerStateChange }
                    });
                }
            };

            function onPlayerStateChange(event) {
                if (event.data == YT.PlayerState.PLAYING && videoDuration === 0) {
                    videoDuration = player.getDuration();
                    currentVideoTitle = player.getVideoData().title;
                }
            }
            
            const timeStringToSeconds = (timeStr) => {
                const parts = timeStr.split(':').map(Number);
                if (parts.length === 3) return parts[0] * 3600 + parts[1] * 60 + parts[2];
                if (parts.length === 2) return parts[0] * 60 + parts[1];
                return 0;
            };

            loadVideoBtn.addEventListener('click', () => {
                const url = ytInput.value.trim();
                if (!url) { showError("Silakan masukkan link YouTube."); return; }
                hideError();
                const videoId = getYouTubeVideoId(url);
                if (videoId) {
                    currentVideoId = videoId;
                    videoDuration = 0; // Reset duration
                    createPlayer(videoId);
                    resetClips();
                } else {
                    showError("Link YouTube tidak valid. Mohon periksa kembali.");
                    currentVideoId = null;
                }
                updateButtonsState();
            });
            
            const extractKeyPhrases = (title) => {
                const separators = / dan | vs | tentang | mengenai |, |\|/i;
                return [...new Set(title.split(separators).map(s => s.trim()).filter(s => s.length > 3))];
            };
            
            const getSimulatedAIClips = (title, duration) => {
                const keyPhrases = extractKeyPhrases(title);
                const fallbackTitles = ["Poin Argumen Utama", "Fakta Penting", "Titik Balik Cerita", "Penjelasan Kompleks", "Statistik Kunci", "Momen Krusial"];
                const formatTime = (totalSeconds) => {
                    const hours = Math.floor(totalSeconds / 3600);
                    const minutes = Math.floor((totalSeconds % 3600) / 60);
                    const seconds = Math.floor(totalSeconds % 60);
                    return [hours, minutes, seconds].map(v => String(v).padStart(2, '0')).join(':');
                };

                const generatedClips = [];
                const numClips = Math.min(Math.floor(duration / 60) + 2, 8);
                const bucketSize = duration / numClips;

                for (let i = 0; i < numClips; i++) {
                    const clipTitle = keyPhrases[i] || fallbackTitles[i % fallbackTitles.length];
                    const clipDuration = Math.floor(Math.random() * 31) + 20; // 20-50 detik
                    const start = (i * bucketSize) + (Math.random() * (bucketSize - clipDuration));
                    const end = start + clipDuration;
                    generatedClips.push({ title: clipTitle, start: formatTime(start), end: formatTime(end) });
                }
                return new Promise(resolve => setTimeout(() => resolve(generatedClips), 1500));
            };

            autoClipBtn.addEventListener('click', async () => {
                if (!currentVideoId || player.getDuration() <= 0) {
                    showError("Tunggu video dimuat sepenuhnya sebelum membuat klip."); return;
                }
                hideError();
                resetClips();
                setStatus('loading');
                const suggestions = await getSimulatedAIClips(player.getVideoData().title, player.getDuration());
                clipsData = suggestions;
                renderClips();
            });

            const renderClips = () => {
                clipList.innerHTML = '';
                if (clipsData.length > 0) {
                    hideStatus();
                    clipsData.forEach((clip, index) => {
                        const clipElement = document.createElement('div');
                        clipElement.className = "bg-slate-800 p-3 rounded-xl flex items-start gap-4 border border-slate-700 transition hover:border-sky-500 cursor-pointer";
                        const startSeconds = timeStringToSeconds(clip.start);
                        
                        clipElement.innerHTML = `
                            <div class="w-24 h-14 rounded-lg overflow-hidden flex-shrink-0 bg-slate-700">
                                <img src="https://img.youtube.com/vi/${currentVideoId}/mqdefault.jpg" class="w-full h-full object-cover" alt="Video thumbnail">
                            </div>
                            <div class="flex-grow pt-1">
                                <h3 class="font-bold text-white text-sm leading-tight">${clip.title}</h3>
                                <p class="text-xs text-slate-400 mt-2">Timestamp: ${clip.start} - ${clip.end}</p>
                            </div>
                            <div class="flex flex-col gap-2 pt-1">
                                <button class="download-btn p-2 text-slate-400 hover:text-white hover:bg-slate-700 rounded-md transition" title="Download Klip">
                                    <i data-lucide="download-cloud" class="w-4 h-4"></i>
                                </button>
                                <button class="delete-btn p-2 text-slate-400 hover:text-red-400 hover:bg-red-500/10 rounded-md transition" title="Hapus Klip"><i data-lucide="trash-2" class="w-4 h-4"></i></button>
                            </div>
                        `;
                        clipElement.addEventListener('click', (e) => {
                            if (e.target.closest('button')) return;
                            player.seekTo(startSeconds, true); player.playVideo();
                        });
                        clipElement.querySelector('.delete-btn').addEventListener('click', () => openDeleteModal(index));
                        clipElement.querySelector('.download-btn').addEventListener('click', (e) => downloadClip(index, e.currentTarget));
                        clipList.appendChild(clipElement);
                    });
                } else { setStatus('empty'); }
                lucide.createIcons();
                updateButtonsState();
            };

            const resetClips = () => { clipsData = []; renderClips(); };

            async function downloadClip(index, buttonElement) {
                const clip = clipsData[index];
                const originalIcon = buttonElement.innerHTML;
                buttonElement.innerHTML = '<div class="spinner"></div>';
                buttonElement.disabled = true;

                try {
                    const response = await fetch(`${BACKEND_URL}/clip`, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({
                            videoId: currentVideoId,
                            startTime: clip.start,
                            endTime: clip.end,
                            title: clip.title
                        })
                    });

                    if (!response.ok) {
                        const errorData = await response.json();
                        throw new Error(errorData.error || `Server error: ${response.status}`);
                    }

                    const blob = await response.blob();
                    const url = window.URL.createObjectURL(blob);
                    const a = document.createElement('a');
                    a.style.display = 'none';
                    a.href = url;
                    a.download = response.headers.get('Content-Disposition').split('filename=')[1].replace(/"/g, '');
                    document.body.appendChild(a);
                    a.click();
                    window.URL.revokeObjectURL(url);
                    a.remove();

                } catch (error) {
                    console.error('Download error:', error);
                    alert(`Gagal mengunduh klip. Pastikan backend server berjalan.\n\nError: ${error.message}`);
                } finally {
                    buttonElement.innerHTML = originalIcon;
                    buttonElement.disabled = false;
                    lucide.createIcons();
                }
            }
            
            const openDeleteModal = (index) => {
                modalTitle.textContent = "Hapus Klip Ini?";
                modalMessage.textContent = "Anda yakin ingin menghapus klip ini? Tindakan ini tidak dapat diurungkan.";
                deletionHandler = () => { clipsData.splice(index, 1); renderClips(); };
                deleteModal.classList.remove('hidden');
            };
             deleteAllBtn.addEventListener('click', () => {
                modalTitle.textContent = "Hapus Semua Klip?";
                modalMessage.textContent = `Anda yakin ingin menghapus semua ${clipsData.length} klip?`;
                deletionHandler = resetClips;
                deleteModal.classList.remove('hidden');
            });
            
            const closeDeleteModal = () => { deleteModal.classList.add('hidden'); deletionHandler = null; };
            modalConfirmBtn.addEventListener('click', () => { if (deletionHandler) { deletionHandler(); } closeDeleteModal(); });
            modalCancelBtn.addEventListener('click', closeDeleteModal);
           
            setStatus('empty');
            updateButtonsState();
        });
    </script>
</body>
</html>

