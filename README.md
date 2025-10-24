<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clipz - The Creator's Growth Engine</title>
    <!-- Memuat Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Memuat Font Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        /* Mengatur font default */
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Menambahkan efek gradien pada teks */
        .text-gradient {
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
        }
        /* Efek hover pada tombol */
        .cta-button {
            transition: all 0.3s ease;
        }
        .cta-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(59, 130, 246, 0.3), 0 4px 6px -2px rgba(59, 130, 246, 0.2);
        }
        /* Smooth scroll */
        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body class="bg-slate-900 text-gray-200">

    <!-- Header / Navigasi -->
    <header class="fixed w-full bg-slate-900/80 backdrop-blur-sm z-50 border-b border-slate-700">
        <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
            <!-- Logo -->
            <a href="#" class="text-3xl font-extrabold">
                <span class="text-gradient bg-gradient-to-r from-blue-400 to-cyan-300">Clipz</span>
            </a>
            
            <!-- Menu Navigasi -->
            <div class="hidden md:flex space-x-8 items-center">
                <a href="#what-is-clipz" class="text-gray-300 hover:text-blue-400 transition-colors">Apa itu Clipz?</a>
                <a href="#target-audience" class="text-gray-300 hover:text-blue-400 transition-colors">Untuk Siapa?</a>
                <a href="#pricing" class="text-gray-300 hover:text-blue-400 transition-colors">Harga</a>
                <a href="#" class="cta-button bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-5 rounded-lg">
                    Mulai Gratis
                </a>
            </div>
            
            <!-- Tombol Menu Mobile -->
            <button id="mobile-menu-button" class="md:hidden text-gray-300">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
                </svg>
            </button>
        </nav>
        
        <!-- Menu Mobile (Tampil/Sembunyi) -->
        <div id="mobile-menu" class="hidden md:hidden bg-slate-800 p-4">
            <a href="#what-is-clipz" class="block py-2 px-3 rounded hover:bg-slate-700">Apa itu Clipz?</a>
            <a href="#target-audience" class="block py-2 px-3 rounded hover:bg-slate-700">Untuk Siapa?</a>
            <a href="#pricing" class="block py-2 px-3 rounded hover:bg-slate-700">Harga</a>
            <a href="#" class="block w-full text-center mt-2 cta-button bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 px-5 rounded-lg">
                Mulai Gratis
            </a>
        </div>
    </header>

    <main>
        <!-- Bagian Hero (Judul Utama) -->
        <section class="pt-32 pb-24 container mx-auto px-6 text-center">
            <h1 class="text-5xl md:text-7xl font-extrabold mb-6 leading-tight">
                <span class="block">The Creator's</span>
                <span class="text-gradient bg-gradient-to-r from-blue-400 to-cyan-300">Growth Engine</span>
            </h1>
            <p class="text-xl md:text-2xl text-gray-300 max-w-3xl mx-auto mb-10">
                Ubah konten panjang Anda (video atau podcast) menjadi puluhan aset klip pendek yang siap viral di media sosial.
            </p>
            <a href="#" class="cta-button bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 px-10 text-lg rounded-lg">
                Mulai Gratis Sekarang
            </a>

            <!-- Mockup UI (berdasarkan PPT hal 2) -->
            <div class="max-w-4xl mx-auto mt-20 bg-slate-800 rounded-xl shadow-2xl p-4 border border-slate-700">
                <div class="flex items-center pb-3 border-b border-slate-600">
                    <div class="flex space-x-1.5">
                        <div class="w-3 h-3 rounded-full bg-red-500"></div>
                        <div class="w-3 h-3 rounded-full bg-yellow-500"></div>
                        <div class="w-3 h-3 rounded-full bg-green-500"></div>
                    </div>
                    <span class="ml-3 text-sm text-gray-400">Clipz - Genfour Dashboard</span>
                </div>
                <div class="flex flex-col md:flex-row gap-4 mt-4">
                    <!-- Kolom Utama (Video) -->
                    <div class="flex-grow bg-slate-700 rounded-lg p-4">
                        <div class="w-full h-48 md:h-72 bg-gray-900 rounded-md flex items-center justify-center">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-16 h-16 text-slate-500">
                                <path stroke-linecap="round" stroke-linejoin="round" d="m15.75 10.5 4.72-4.72a.75.75 0 0 1 1.28.53v11.38a.75.75 0 0 1-1.28.53l-4.72-4.72M4.5 18.75h9a2.25 2.25 0 0 0 2.25-2.25v-9A2.25 2.25 0 0 0 13.5 5.25h-9A2.25 2.25 0 0 0 2.25 7.5v9A2.25 2.25 0 0 0 4.5 18.75Z" />
                            </svg>
                        </div>
                        <div class="mt-4 flex flex-col md:flex-row gap-3">
                            <input type="text" placeholder="Tempelkan link YouTube..." class="flex-grow bg-slate-800 border border-slate-600 rounded-md p-2 text-sm text-gray-200 focus:outline-none focus:ring-2 focus:ring-blue-500">
                            <button class="bg-blue-600 text-white px-4 py-2 rounded-md text-sm font-semibold hover:bg-blue-700 transition-colors">Muat Video</button>
                        </div>
                    </div>
                    <!-- Sidebar (Rekomendasi) -->
                    <div class="w-full md:w-64 bg-slate-700 rounded-lg p-4">
                        <h4 class="font-semibold text-white mb-3">Rekomendasi Klip</h4>
                        <p class="text-xs text-gray-400 mb-4">Momen penting yang ditemukan oleh AI kami akan muncul di sini.</p>
                        <div class="bg-gray-900 rounded-md p-3 mb-2">
                            <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-slate-500 mr-2">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M15.91 11.672a.375.375 0 0 1 0 .656l-5.603 3.113a.375.375 0 0 1-.557-.328V8.887c0-.286.307-.466.557-.327l5.603 3.112Z" />
                                </svg>
                                <span class="text-sm text-gray-300">Belum ada klip</span>
                            </div>
                        </div>
                        <div class="bg-gray-900/50 rounded-md p-3 mb-2 opacity-50">
                             <div class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-slate-600 mr-2">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M15.91 11.672a.375.375 0 0 1 0 .656l-5.603 3.113a.375.375 0 0 1-.557-.328V8.887c0-.286.307-.466.557-.327l5.603 3.112Z" />
                                </svg>
                                <span class="text-sm text-slate-500">Menunggu video...</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Bagian "Apa itu Clipz?" -->
        <section id="what-is-clipz" class="py-20 bg-slate-800">
            <div class="container mx-auto px-6">
                <div class="max-w-3xl mx-auto text-center">
                    <h2 class="text-base font-semibold text-blue-400 tracking-wide uppercase">Apa itu Clipz?</h2>
                    <p class="mt-2 text-3xl md:text-4xl font-extrabold text-white">
                        Bukan Sekadar Alat, Ini Adalah Studio Konten Video Pendek Anda.
                    </p>
                    <p class="mt-4 text-lg text-gray-300">
                        Clipz adalah solusi SaaS (Software as a Service) berbasis AI yang dibuat untuk memecahkan masalah utama kreator: <strong class="text-white">Creator Burnout</strong>. Kami menggabungkan kecepatan AI untuk menemukan momen terbaik dengan kontrol kreatif manusia untuk hasil yang sempurna.
                    </p>
                </div>
            </div>
        </section>

        <!-- Bagian Target Audience (Untuk Siapa?) -->
        <section id="target-audience" class="py-24">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto mb-16">
                    <h2 class="text-base font-semibold text-blue-400 tracking-wide uppercase">Untuk Siapa?</h2>
                    <p class="mt-2 text-3xl md:text-4xl font-extrabold text-white">
                        Dibuat untuk Setiap Tipe Kreator
                    </p>
                </div>
                
                <!-- Grid Target Audience -->
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                    
                    <!-- Card 1: Podcaster -->
                    <div class="bg-slate-800 p-8 rounded-xl shadow-lg border border-slate-700">
                        <div class="bg-blue-600/20 text-blue-300 w-12 h-12 rounded-lg flex items-center justify-center mb-4">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 18.75a6 6 0 0 0 6-6v-1.5m-6 7.5a6 6 0 0 1-6-6v-1.5m6 7.5v3.75m-3.75 0h7.5M12 15.75a3 3 0 0 1-3-3V4.5a3 3 0 1 1 6 0v8.25a3 3 0 0 1-3 3Z" />
                            </svg>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-2">Podcaster</h3>
                        <p class="text-gray-300">Mengubah audio panjang menjadi klip video dinamis, lengkap dengan subtitle & audiogram yang menarik.</p>
                    </div>
                    
                    <!-- Card 2: Youtuber Edukasi -->
                    <div class="bg-slate-800 p-8 rounded-xl shadow-lg border border-slate-700">
                        <div class="bg-blue-600/20 text-blue-300 w-12 h-12 rounded-lg flex items-center justify-center mb-4">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.042A8.967 8.967 0 0 0 6 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 0 1 6 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 0 1 6-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0 0 18 18c-2.305 0-4.408.867-6 2.292m0-14.25v14.25" />
                            </svg>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-2">Youtuber Edukasi</h3>
                        <p class="text-gray-300">Mengekstrak "daging" dan insight penting secara otomatis untuk teaser media sosial yang padat informasi.</p>
                    </div>

                    <!-- Card 3: Gamer -->
                    <div class="bg-slate-800 p-8 rounded-xl shadow-lg border border-slate-700">
                        <div class="bg-blue-600/20 text-blue-300 w-12 h-12 rounded-lg flex items-center justify-center mb-4">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 12a9 9 0 1 1 18 0 9 9 0 0 1-18 0ZM12 15.75a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm.002-3a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm-3.752.002a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm3.75.75a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm-3.75 0a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm0 3a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm3.75 0a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm-3.75 3a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Zm3.75 0a.75.75 0 0 1 .75.75v.008a.75.75 0 0 1-1.5 0v-.008a.75.75 0 0 1 .75-.75Z" />
                            </svg>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-2">Gamer</h3>
                        <p class="text-gray-300">Menemukan momen *killstreak* epik atau komedi dari VOD berjam-jam tanpa perlu *scrolling* manual.</p>
                    </div>

                    <!-- Card 4: Agensi & Bisnis -->
                    <div class="bg-slate-800 p-8 rounded-xl shadow-lg border border-slate-700">
                        <div class="bg-blue-600/20 text-blue-300 w-12 h-12 rounded-lg flex items-center justify-center mb-4">
                            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                                <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 14.15v4.07a2.25 2.25 0 0 1-2.25 2.25h-13.5A2.25 2.25 0 0 1 2.25 18.22V10.18a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 20.25 10.18v4.07ZM12 12.75a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M12 15a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M15 12.75a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M15 15a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M9 15a.75.75 0 1 1 0-1.5.75.75 0 0 1 0 1.5Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 8.63c.09-.436.434-.78.865-.865l.38.083c.06.012.122.012.183 0l.38-.083a1.12 1.12 0 0 1 .866.865l.083.38a.998.998 0 0 0 0 .183l-.083.38a1.12 1.12 0 0 1-.866.865l-.38-.083a.998.998 0 0 0-.183 0l-.38.083a1.12 1.12 0 0 1-.865-.865l-.083-.38a.998.998 0 0 0 0-.183l.083-.38Z" />
                                <path stroke-linecap="round" stroke-linejoin="round" d="M20.25 8.63c.09-.436.434-.78.865-.865l.38.083c.06.012.122.012.183 0l.38-.083a1.12 1.12 0 0 1 .866.865l.083.38a.998.998 0 0 0 0 .183l-.083.38a1.12 1.12 0 0 1-.866.865l-.38-.083a.998.998 0 0 0-.183 0l-.38.083a1.12 1.12 0 0 1-.865-.865l-.083-.38a.998.998 0 0 0 0-.183l.083-.38Z" />
                            </svg>
                        </div>
                        <h3 class="text-2xl font-bold text-white mb-2">Agensi & Bisnis</h3>
                        <p class="text-gray-300">Menghemat ratusan jam kerja produksi tim Anda dan meningkatkan volume konten klien secara drastis.</p>
                    </div>

                </div>
            </div>
        </section>

        <!-- Bagian Harga (Pricing) -->
        <section id="pricing" class="py-24 bg-slate-800">
            <div class="container mx-auto px-6">
                <div class="text-center max-w-3xl mx-auto mb-16">
                    <h2 class="text-base font-semibold text-blue-400 tracking-wide uppercase">Model Bisnis</h2>
                    <p class="mt-2 text-3xl md:text-4xl font-extrabold text-white">
                        Harga Transparan untuk Semua Kebutuhan
                    </p>
                </div>
                
                <!-- Grid Harga -->
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 max-w-5xl mx-auto">

                    <!-- Paket 1: Gratis -->
                    <div class="bg-slate-900 p-8 rounded-xl shadow-lg border border-slate-700 flex flex-col">
                        <h3 class="text-2xl font-bold text-white mb-2">Paket Gratis</h3>
                        <p class="text-gray-400 mb-6 h-12">Target: Akuisisi pengguna masif untuk mencoba platform.</p>
                        <div class="mb-6">
                            <span class="text-5xl font-extrabold text-white">Gratis</span>
                            <span class="text-gray-400">Selamanya</span>
                        </div>
                        <ul class="space-y-3 text-gray-300 mb-8 flex-grow">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                30 Menit Video / Bulan
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Fitur Edit Dasar
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-yellow-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v3.75m0-10.036A11.959 11.959 0 0 1 3.598 6 11.99 11.99 0 0 0 3 9.75c0 5.592 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.57-.598-3.75h-.152c-3.196 0-6.1-1.25-8.25-3.286Zm0 13.036h.008v.008H12v-.008Z" />
                                </svg>
                                Dengan Watermark CLIPZ
                            </li>
                        </ul>
                        <a href="#" class="w-full text-center cta-button bg-slate-700 hover:bg-slate-600 text-white font-semibold py-3 px-5 rounded-lg transition-colors">
                            Mulai Gratis
                        </a>
                    </div>
                    
                    <!-- Paket 2: Pro (Paling Populer) -->
                    <div class="bg-blue-600 p-8 rounded-xl shadow-2xl relative flex flex-col">
                        <span class="absolute top-0 right-0 -mt-3 mr-6 bg-cyan-300 text-blue-900 text-xs font-bold px-3 py-1 rounded-full uppercase">Paling Populer</span>
                        <h3 class="text-2xl font-bold text-white mb-2">Paket Pro</h3>
                        <p class="text-blue-100 mb-6 h-12">Target: Kreator Serius & Profesional yang butuh hasil maksimal.</p>
                        <div class="mb-6">
                            <span class="text-5xl font-extrabold text-white">Rp 199k</span>
                            <span class="text-blue-100">/ Bulan</span>
                        </div>
                        <ul class="space-y-3 text-white mb-8 flex-grow">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-cyan-300 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Kuota Jauh Lebih Besar
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-cyan-300 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Tanpa Watermark
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-cyan-300 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Branding Kit Otomatis
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-cyan-300 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Akses Penuh Studio Editor
                            </li>
                        </ul>
                        <a href="#" class="w-full text-center cta-button bg-white hover:bg-gray-100 text-blue-700 font-semibold py-3 px-5 rounded-lg transition-colors">
                            Pilih Paket Pro
                        </a>
                    </div>
                    
                    <!-- Paket 3: Team -->
                    <div class="bg-slate-900 p-8 rounded-xl shadow-lg border border-slate-700 flex flex-col">
                        <h3 class="text-2xl font-bold text-white mb-2">Clipz Team</h3>
                        <p class="text-gray-400 mb-6 h-12">Target: Sultan, Brand, & Agensi yang ingin terima beres A-Z.</p>
                        <div class="mb-6">
                            <span class="text-5xl font-extrabold text-white">Custom</span>
                            <span class="text-gray-400">/ Bulan</span>
                        </div>
                        <ul class="space-y-3 text-gray-300 mb-8 flex-grow">
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Kuota Unlimited
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Dedicated Content Strategist
                            </li>
                            <li class="flex items-center">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 text-green-400 mr-2 shrink-0">
                                    <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
                                </svg>
                                Layanan Penuh A sampai Z
                            </li>
                        </ul>
                        <a href="#" class="w-full text-center cta-button bg-slate-700 hover:bg-slate-600 text-white font-semibold py-3 px-5 rounded-lg transition-colors">
                            Hubungi Sales
                        </a>
                    </div>

                </div>
            </div>
        </section>

        <!-- Bagian CTA Terakhir -->
        <section class="py-24 container mx-auto px-6 text-center">
            <h2 class="text-4xl md:text-5xl font-extrabold mb-6">
                Siap Mengubah Konten Anda Menjadi <span class="text-gradient bg-gradient-to-r from-blue-400 to-cyan-300">Aset Viral</span>?
            </h2>
            <p class="text-xl text-gray-300 max-w-2xl mx-auto mb-10">
                Hentikan *creator burnout* dan biarkan AI kami bekerja untuk Anda. Coba Clipz gratis hari ini.
            </p>
            <a href="#" class="cta-button bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 px-10 text-lg rounded-lg">
                Mulai Gratis Sekarang
            </a>
        </section>
    </main>

    <!-- Footer -->
    <footer class="border-t border-slate-700 mt-16">
        <div class="container mx-auto px-6 py-8 text-center text-gray-400">
            <p>&copy; 2025 Clipz. Dibuat berdasarkan Business Plan Anda. www.clipz.com</p>
        </div>
    </footer>

    <!-- Script untuk Menu Mobile -->
    <script>
        document.getElementById('mobile-menu-button').addEventListener('click', function() {
            var menu = document.getElementById('mobile-menu');
            if (menu.classList.contains('hidden')) {
                menu.classList.remove('hidden');
            } else {
                menu.classList.add('hidden');
            }
        });

        // Menutup menu mobile jika link di-klik
        document.querySelectorAll('#mobile-menu a').forEach(function(link) {
            link.addEventListener('click', function() {
                document.getElementById('mobile-menu').classList.add('hidden');
            });
        });
    </script>

</body>
</html>
