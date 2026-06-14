<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>منصة الحصون الخمسة</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts (Tajawal) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    
    <style>
        body { font-family: 'Tajawal', sans-serif; background-color: #f4f6f3; }
        .quran-theme-bg { background-color: #1e3a2f; }
        .quran-theme-text { color: #1e3a2f; }
        .quran-gold { color: #c49a45; }
        .quran-gold-bg { background-color: #c49a45; }
        .quran-gold-border { border-color: #c49a45; }
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #1e3a2f; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #11221b; }
        
        select {
            background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
            background-position: left 0.5rem center;
            background-repeat: no-repeat;
            background-size: 1.5em 1.5em;
            padding-left: 2.5rem;
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
        }
        
        .fab-hover:hover { transform: scale(1.05); }
    </style>
</head>
<body class="text-gray-800 transition-colors duration-300 relative">

    <div class="min-h-screen flex flex-col">
        <!-- Header -->
        <header class="quran-theme-bg text-white shadow-lg border-b-4 quran-gold-border sticky top-0 z-40">
            <div class="max-w-7xl mx-auto px-4 py-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div class="flex items-center gap-3">
                    <div class="w-12 h-12 rounded-full quran-gold-bg flex items-center justify-center shadow-inner text-white">
                        <i class="fa-solid fa-book-quran text-2xl"></i>
                    </div>
                    <div>
                        <h1 class="text-xl sm:text-2xl font-bold tracking-wide">منصة الحصون الخمسة</h1>
                        <p class="text-xs text-gray-300">النظام الذكي لتقسيم الأوراد وتوزيعها آلياً</p>
                    </div>
                </div>
                
                <div class="flex items-center gap-2">
                    <button onclick="resetAllProgress()" class="bg-red-700 hover:bg-red-800 text-white px-3 py-2 rounded-lg text-sm font-medium transition duration-200 flex items-center gap-2">
                        <i class="fa-solid fa-arrow-rotate-right"></i>
                        <span>تصفير الأسبوع</span>
                    </button>
                    <button onclick="openSetupModal()" class="bg-emerald-800 hover:bg-emerald-900 text-white px-3 py-2 rounded-lg text-sm font-medium transition duration-200 flex items-center gap-2 border border-emerald-600">
                        <i class="fa-solid fa-sliders"></i>
                        <span>ضبط الأوراد والبدايات</span>
                    </button>
                </div>
            </div>
        </header>

        <!-- Main Content -->
        <main class="flex-grow max-w-7xl w-full mx-auto px-4 py-6 sm:px-6 lg:px-8">
            
            <!-- Welcome Banner -->
            <div class="bg-white rounded-2xl p-6 mb-6 shadow-sm border border-emerald-100 flex flex-col md:flex-row items-center justify-between gap-6">
                <div class="flex-1">
                    <h2 class="text-2xl font-bold quran-theme-text mb-2">مرحباً بك في رحاب الحصون الخمسة 🕋</h2>
                    <p class="text-gray-600 leading-relaxed text-sm sm:text-base mb-3">
                        تم تفعيل التقسيم الذكي. يتم توزيع حصة (الحفظ والمراجعة) على أيامك النشطة بالتساوي. ويبقى ورد (التحضير) ثابتاً طوال الأسبوع للترداد، بينما ينطلق ورد (الختمة) بمقدار كامل يومياً.
                    </p>
                    <div class="flex flex-wrap gap-2">
                        <span class="bg-emerald-100 text-emerald-900 px-3 py-1 rounded-full text-xs font-bold" id="badge-week-start">تاريخ البداية: 13-06-2026</span>
                        <span class="bg-amber-100 text-amber-900 px-3 py-1 rounded-full text-xs font-bold" id="badge-active-days">الأيام النشطة: —</span>
                    </div>
                </div>
                <div class="bg-emerald-50 p-4 rounded-xl border-l-4 border-emerald-700 max-w-md w-full text-center">
                    <p class="text-emerald-950 font-medium text-lg italic">"فَاقْرَؤُوا مَا تَيَسَّرَ مِنَ الْقُرْآنِ"</p>
                    <span class="text-xs text-emerald-700 block mt-2">[سورة المزمل - آية 20]</span>
                </div>
            </div>

            <!-- Stats Overview Cards -->
            <div class="grid grid-cols-1 md:grid-cols-5 gap-4 mb-8">
                <!-- Fort 1 -->
                <div class="bg-white rounded-xl p-4 shadow-sm border-t-4 border-emerald-600 flex flex-col justify-between h-36">
                    <div class="flex justify-between items-start">
                        <div>
                            <span class="text-xs text-gray-500 block font-bold" id="title-card-1">الحصن الأول</span>
                            <span class="text-md font-bold quran-theme-text" id="stat-f1-val">0 / 0</span>
                        </div>
                        <span class="bg-emerald-50 text-emerald-800 text-[10px] px-2 py-1 rounded font-bold" id="target-badge-f1">—</span>
                    </div>
                    <div>
                        <div class="w-full bg-gray-100 rounded-full h-2 mb-1">
                            <div id="stat-f1-bar" class="bg-emerald-600 h-2 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <span class="text-xs text-gray-500" id="stat-f1-perc">0% مكتمل</span>
                    </div>
                </div>
                <!-- Fort 2 -->
                <div class="bg-white rounded-xl p-4 shadow-sm border-t-4 border-cyan-500 flex flex-col justify-between h-36">
                    <div class="flex justify-between items-start">
                        <div>
                            <span class="text-xs text-gray-500 block font-bold" id="title-card-2">الحصن الثاني</span>
                            <span class="text-md font-bold text-cyan-900" id="stat-f2-val">0 / 0</span>
                        </div>
                        <span class="bg-cyan-50 text-cyan-800 text-[10px] px-2 py-1 rounded font-bold" id="target-badge-f2">—</span>
                    </div>
                    <div>
                        <div class="w-full bg-gray-100 rounded-full h-2 mb-1">
                            <div id="stat-f2-bar" class="bg-cyan-500 h-2 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <span class="text-xs text-gray-500" id="stat-f2-perc">0% مكتمل</span>
                    </div>
                </div>
                <!-- Fort 3 -->
                <div class="bg-white rounded-xl p-4 shadow-sm border-t-4 border-indigo-500 flex flex-col justify-between h-36">
                    <div class="flex justify-between items-start">
                        <div>
                            <span class="text-xs text-gray-500 block font-bold" id="title-card-3">الحصن الثالث</span>
                            <span class="text-md font-bold text-indigo-900" id="stat-f3-val">0 / 0</span>
                        </div>
                        <span class="bg-indigo-50 text-indigo-800 text-[10px] px-2 py-1 rounded font-bold" id="target-badge-f3">—</span>
                    </div>
                    <div>
                        <div class="w-full bg-gray-100 rounded-full h-2 mb-1">
                            <div id="stat-f3-bar" class="bg-indigo-500 h-2 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <span class="text-xs text-gray-500" id="stat-f3-perc">0% مكتمل</span>
                    </div>
                </div>
                <!-- Fort 4 -->
                <div class="bg-white rounded-xl p-4 shadow-sm border-t-4 border-amber-600 flex flex-col justify-between h-36">
                    <div class="flex justify-between items-start">
                        <div>
                            <span class="text-xs text-gray-500 block font-bold" id="title-card-4">الحصن الرابع</span>
                            <span class="text-md font-bold text-amber-900" id="stat-f4-val">0 / 0</span>
                        </div>
                        <span class="bg-amber-50 text-amber-800 text-[10px] px-2 py-1 rounded font-bold" id="target-badge-f4">—</span>
                    </div>
                    <div>
                        <div class="w-full bg-gray-100 rounded-full h-2 mb-1">
                            <div id="stat-f4-bar" class="bg-amber-500 h-2 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <span class="text-xs text-gray-500" id="stat-f4-perc">0% مكتمل</span>
                    </div>
                </div>
                <!-- Fort 5 -->
                <div class="bg-white rounded-xl p-4 shadow-sm border-t-4 border-rose-500 flex flex-col justify-between h-36">
                    <div class="flex justify-between items-start">
                        <div>
                            <span class="text-xs text-gray-500 block font-bold" id="title-card-5">الحصن الخامس</span>
                            <span class="text-md font-bold text-rose-900" id="stat-f5-val">0 / 0</span>
                        </div>
                        <span class="bg-rose-50 text-rose-800 text-[10px] px-2 py-1 rounded font-bold" id="target-badge-f5">—</span>
                    </div>
                    <div>
                        <div class="w-full bg-gray-100 rounded-full h-2 mb-1">
                            <div id="stat-f5-bar" class="bg-rose-500 h-2 rounded-full transition-all duration-500" style="width: 0%"></div>
                        </div>
                        <span class="text-xs text-gray-500" id="stat-f5-perc">0% مكتمل</span>
                    </div>
                </div>
            </div>

            <!-- Main Layout Grid -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Right Column (1/3) -->
                <div class="lg:col-span-1 space-y-6">
                    
                    <!-- Logging Panel -->
                    <div class="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
                        <h3 class="text-lg font-bold quran-theme-text mb-4 pb-2 border-b border-gray-100 flex items-center gap-2">
                            <i class="fa-solid fa-pen-to-square text-emerald-700"></i>
                            <span>تسجيل الإنجاز اليومي</span>
                        </h3>
                        
                        <form id="daily-log-form" onsubmit="handleLogSubmit(event)" class="space-y-4">
                            <div>
                                <label class="block text-xs font-semibold text-gray-600 mb-1">اختر اليوم لتسجيل ورده</label>
                                <select id="log-day" class="w-full bg-gray-50 border border-gray-200 rounded-lg p-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 font-bold"></select>
                            </div>

                            <div class="space-y-3 pt-2">
                                <span class="block text-xs font-semibold text-gray-600 mb-1">الأوراد المنجزة لهذا اليوم:</span>
                                
                                <div id="container-check-f1" class="flex flex-col p-2.5 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                                    <label class="flex items-center justify-between cursor-pointer">
                                        <div class="flex items-center gap-2">
                                            <input type="checkbox" id="check-f1" class="w-5 h-5 rounded text-emerald-600 focus:ring-emerald-500 border-gray-300">
                                            <span class="text-sm font-bold" id="lbl-check-f1">الحصن الأول</span>
                                        </div>
                                    </label>
                                </div>
                                <div id="container-check-f2" class="flex flex-col p-2.5 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                                    <label class="flex items-center justify-between cursor-pointer">
                                        <div class="flex items-center gap-2">
                                            <input type="checkbox" id="check-f2" class="w-5 h-5 rounded text-cyan-600 focus:ring-cyan-500 border-gray-300">
                                            <span class="text-sm font-bold" id="lbl-check-f2">الحصن الثاني</span>
                                        </div>
                                    </label>
                                </div>
                                <div id="container-check-f3" class="flex flex-col p-2.5 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                                    <label class="flex items-center justify-between cursor-pointer">
                                        <div class="flex items-center gap-2">
                                            <input type="checkbox" id="check-f3" class="w-5 h-5 rounded text-indigo-600 focus:ring-indigo-500 border-gray-300">
                                            <span class="text-sm font-bold" id="lbl-check-f3">الحصن الثالث</span>
                                        </div>
                                    </label>
                                </div>
                                <div id="container-check-f4" class="flex flex-col p-2.5 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                                    <label class="flex items-center justify-between cursor-pointer">
                                        <div class="flex items-center gap-2">
                                            <input type="checkbox" id="check-f4" class="w-5 h-5 rounded text-amber-600 focus:ring-amber-500 border-gray-300">
                                            <span class="text-sm font-bold" id="lbl-check-f4">الحصن الرابع</span>
                                        </div>
                                    </label>
                                </div>
                                <div id="container-check-f5" class="flex flex-col p-2.5 rounded-lg hover:bg-gray-50 border border-gray-100 transition">
                                    <label class="flex items-center justify-between cursor-pointer">
                                        <div class="flex items-center gap-2">
                                            <input type="checkbox" id="check-f5" class="w-5 h-5 rounded text-rose-600 focus:ring-rose-500 border-gray-300">
                                            <span class="text-sm font-bold" id="lbl-check-f5">الحصن الخامس</span>
                                        </div>
                                    </label>
                                </div>
                            </div>
                            <button type="submit" class="w-full quran-theme-bg text-white font-bold py-3 px-4 rounded-xl shadow transition duration-200 flex items-center justify-center gap-2 hover:opacity-95">
                                <i class="fa-solid fa-cloud-arrow-up"></i>
                                <span>حفظ وتحديث الإنجاز اليومي</span>
                            </button>
                        </form>
                    </div>

                    <!-- Audio Helper -->
                    <div class="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
                        <h3 class="text-lg font-bold quran-theme-text mb-3 pb-2 border-b border-gray-100 flex items-center gap-2">
                            <i class="fa-solid fa-volume-high text-emerald-700"></i>
                            <span>تأكيد النطق والتحضير الصوتي</span>
                        </h3>
                        <div class="space-y-3">
                            <div>
                                <label class="block text-xs text-gray-600 mb-1">القارئ المستمع له:</label>
                                <select id="audio-reciter" class="w-full bg-gray-50 border border-gray-200 rounded-lg p-2 text-sm font-bold">
                                    <option value="ar.alafasy">مشاري بن راشد العفاسي</option>
                                    <option value="ar.husary">محمود خليل الحصري (مرتل)</option>
                                    <option value="ar.minshawi">محمد صديق المنشاوي</option>
                                </select>
                            </div>
                            <div class="grid grid-cols-2 gap-2">
                                <div>
                                    <label class="block text-xs text-gray-600 mb-1">اختر السورة:</label>
                                    <select id="audio-surah" class="w-full bg-gray-50 border border-gray-200 rounded-lg p-2 text-sm font-bold custom-dropdown-surah"></select>
                                </div>
                                <div>
                                    <label class="block text-xs text-gray-600 mb-1">رقم الآية:</label>
                                    <input type="number" id="audio-ayah" value="1" min="1" class="w-full bg-gray-50 border border-gray-200 rounded-lg p-2 text-sm text-center font-bold">
                                </div>
                            </div>
                            <button onclick="playAyahAudio()" class="w-full border-2 quran-gold-border text-emerald-950 hover:bg-amber-50 font-bold py-2 px-4 rounded-xl text-sm transition flex items-center justify-center gap-2">
                                <span id="audio-btn-icon"><i class="fa-solid fa-play"></i></span>
                                <span id="audio-btn-text">استمع وتأكد من الآية</span>
                            </button>
                            <audio id="quran-audio" class="hidden"></audio>
                        </div>
                    </div>

                </div>

                <!-- Left Column (2/3): Table Schedule & Notebook -->
                <div class="lg:col-span-2 space-y-6">
                    
                    <!-- Table Schedule Card -->
                    <div class="bg-white rounded-2xl shadow-sm border border-gray-100 overflow-hidden">
                        <div class="p-6 pb-4 border-b border-gray-100 flex items-center justify-between flex-wrap gap-4">
                            <div>
                                <h3 class="text-xl font-bold quran-theme-text flex items-center gap-2">
                                    <i class="fa-solid fa-calendar-days text-emerald-700"></i>
                                    <span>الجدول التفاعلي لمهام الأسبوع</span>
                                </h3>
                                <p class="text-xs text-gray-500 mt-1">يعتمد الجدول على التقسيم الذكي للمقادير (ما عدا التحضير والختمة)</p>
                            </div>
                            <div class="flex items-center gap-1.5 bg-emerald-50 px-3 py-1.5 rounded-lg text-emerald-900 text-sm font-semibold">
                                <i class="fa-solid fa-star text-amber-500"></i>
                                <span id="week-summary-percentage">معدل الإنجاز العام: 0%</span>
                            </div>
                        </div>

                        <div class="overflow-x-auto font-medium">
                            <table class="w-full text-right border-collapse">
                                <thead class="bg-gray-50 border-b border-gray-100">
                                    <tr>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase w-32">اليوم والتاريخ</th>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase" id="tbl-col-1">الحصن ١</th>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase" id="tbl-col-2">الحصن ٢</th>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase" id="tbl-col-3">الحصن ٣</th>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase" id="tbl-col-4">الحصن ٤</th>
                                        <th class="p-4 text-xs font-bold text-gray-500 uppercase" id="tbl-col-5">الحصن ٥</th>
                                    </tr>
                                </thead>
                                <tbody class="divide-y divide-gray-100" id="schedule-tbody">
                                </tbody>
                            </table>
                        </div>
                    </div>

                    <!-- Personal Notebook -->
                    <div class="bg-white rounded-2xl p-6 shadow-sm border border-gray-100">
                        <div class="flex items-center justify-between pb-3 border-b border-gray-100 mb-4">
                            <h3 class="text-lg font-bold quran-theme-text flex items-center gap-2">
                                <i class="fa-solid fa-note-sticky text-emerald-700"></i>
                                <span>مفكرة التثبيت والملاحظات الصعبة</span>
                            </h3>
                            <button onclick="clearNotes()" class="text-xs text-red-600 hover:underline">مسح المفكرة</button>
                        </div>
                        <div class="space-y-4">
                            <textarea id="user-notes" rows="4" class="w-full p-3 bg-amber-50/40 border border-amber-200/60 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 placeholder-gray-400 font-medium text-gray-800" placeholder="اكتب هنا آيات صعبة أو متشابهات لحفظها وتدوينها..."></textarea>
                            <div class="flex justify-end">
                                <button onclick="saveNotes()" class="bg-amber-600 hover:bg-amber-700 text-white text-sm font-semibold px-4 py-2 rounded-xl transition flex items-center gap-2">
                                    <i class="fa-solid fa-floppy-disk"></i>
                                    <span>حفظ الملاحظات</span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <footer class="bg-gray-900 text-gray-400 py-6 mt-12 border-t border-gray-800 text-center text-sm">
            <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row justify-between items-center gap-4">
                <p>© 2026 منصة الحصون الخمسة المتقدمة (مصحف المدينة).</p>
                <div class="flex gap-4">
                    <span class="hover:text-white transition cursor-pointer"><i class="fa-solid fa-heart text-emerald-500"></i> خادم للقرآن الكريم</span>
                </div>
            </div>
        </footer>
    </div>

    <!-- FLOATING CONTACT BUTTON -->
    <button onclick="openContactModal()" class="fixed bottom-6 right-6 z-40 bg-emerald-700 text-white rounded-full w-14 h-14 flex items-center justify-center shadow-[0_10px_25px_-5px_rgba(5,150,105,0.5)] fab-hover transition-all duration-300 focus:outline-none">
        <i class="fa-solid fa-headset text-xl"></i>
    </button>

    <!-- CONTACT US MODAL -->
    <div id="contact-modal" class="hidden fixed inset-0 z-50 overflow-y-auto bg-black bg-opacity-60 flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-md w-full overflow-hidden shadow-2xl transform transition-all">
            <div class="bg-gradient-to-r from-emerald-800 to-emerald-600 p-5 text-white flex justify-between items-center border-b-4 border-emerald-400 font-bold">
                <div class="flex items-center gap-2">
                    <i class="fa-solid fa-comment-dots text-xl"></i>
                    <h3 class="text-lg">رأيك يهمنا وتواصل معنا</h3>
                </div>
                <button onclick="closeContactModal()" class="text-white hover:text-emerald-200 text-xl font-bold">&times;</button>
            </div>
            <div class="p-6 text-center space-y-4">
                <p class="text-sm text-gray-600 leading-relaxed mb-6">
                    يسعدنا جداً استقبال مقترحاتكم، أفكاركم، واستفساراتكم لتطوير هذه المنصة وجعلها الخادم الأمثل لحفاظ كتاب الله. يمكنكم التواصل معنا عبر القنوات التالية:
                </p>
                <!-- 1. WhatsApp Button -->
                <a href="https://wa.me/201234567890" target="_blank" class="w-full flex items-center justify-center gap-3 bg-green-500 hover:bg-green-600 text-white font-bold py-3 rounded-xl transition shadow-sm">
                    <i class="fa-brands fa-whatsapp text-xl"></i>
                    <span>مراسلة عبر الواتساب</span>
                </a>
                <!-- 2. Email Button -->
                <a href="mailto:example@email.com?subject=مقترح لمنصة الحصون الخمسة" class="w-full flex items-center justify-center gap-3 bg-blue-500 hover:bg-blue-600 text-white font-bold py-3 rounded-xl transition shadow-sm">
                    <i class="fa-regular fa-envelope text-xl"></i>
                    <span>إرسال بريد إلكتروني</span>
                </a>
                <!-- 3. Google Form Button -->
                <a href="https://forms.gle/your-form-link-here" target="_blank" class="w-full flex items-center justify-center gap-3 bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 rounded-xl transition shadow-sm">
                    <i class="fa-solid fa-list-check text-xl"></i>
                    <span>تعبئة نموذج المقترحات</span>
                </a>
            </div>
        </div>
    </div>

    <!-- Configuration Modal ( ضبط ومواضع الانطلاق ) -->
    <div id="setup-modal" class="hidden fixed inset-0 z-50 overflow-y-auto bg-black bg-opacity-60 flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-5xl w-full overflow-hidden shadow-2xl transform transition-all">
            <div class="quran-theme-bg p-5 text-white flex justify-between items-center border-b-4 quran-gold-border font-bold">
                <div>
                    <h3 class="text-lg">لوحة ضبط خطة الحصون ومواضع الانطلاق التفصيلية</h3>
                    <p class="text-xs text-emerald-200 font-normal">استخدم القوائم الذكية لتعيين كميات الأوراد وموضع الانطلاق (صفحات، آيات، أرباع، أو أحزاب)</p>
                </div>
                <button onclick="closeSetupModal()" class="text-white hover:text-gray-300 text-xl font-bold">&times;</button>
            </div>
            
            <div class="p-6 space-y-6 max-h-[75vh] overflow-y-auto text-sm">
                <!-- Section 1: Dates & Days -->
                <div class="border-b border-gray-100 pb-5">
                    <h4 class="text-base font-bold text-emerald-950 mb-3 flex items-center gap-2">
                        <i class="fa-regular fa-calendar-check text-emerald-700"></i> <span>١. التواريخ وأيام الحفظ النشطة</span>
                    </h4>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div>
                            <label class="block text-xs text-gray-500 mb-1 font-bold">تاريخ بداية الأسبوع (السبت):</label>
                            <input type="date" id="setup-start-date" class="w-full bg-gray-50 border border-gray-200 rounded-lg p-2.5 font-bold">
                        </div>
                        <div>
                            <label class="block text-xs text-gray-500 mb-2 font-bold">تحديد أيام الورد النشطة:</label>
                            <div class="grid grid-cols-4 gap-2 font-bold">
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Sat" class="text-emerald-600"><span>سبت</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Sun" class="text-emerald-600"><span>أحد</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Mon" class="text-emerald-600"><span>إثن</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Tue" class="text-emerald-600"><span>ثلا</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Wed" class="text-emerald-600"><span>أرب</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Thu" class="text-emerald-600"><span>خميس</span></label>
                                <label class="flex items-center gap-1 bg-gray-50 p-1.5 rounded cursor-pointer border text-[11px]"><input type="checkbox" id="d-Fri" class="text-emerald-600"><span>جمعة</span></label>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Section 2: Units Customization -->
                <div class="border-b border-gray-100 pb-5">
                    <h4 class="text-base font-bold text-emerald-950 mb-3 flex items-center gap-2">
                        <i class="fa-solid fa-sliders text-emerald-700"></i> <span>٢. ضبط كميات ووحدات الحصون (المستهدف الأسبوعي/اليومي)</span>
                    </h4>
                    <div class="space-y-4">
                        <div class="p-4 rounded-xl border border-emerald-100 bg-emerald-50/30">
                            <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
                                <input type="text" id="setup-f1-name" placeholder="اسم الحصن" class="border rounded p-2 text-xs font-bold text-emerald-900">
                                <input type="number" step="0.5" id="setup-f1-target" placeholder="الكمية المستهدفة" class="border rounded p-2 text-xs text-center font-bold">
                                <select id="setup-f1-unit" class="border rounded p-2 text-xs font-bold bg-white">
                                    <option value="pages">صفحة/صفحات</option>
                                    <option value="ayahs">آية/آيات</option>
                                    <option value="quarters">ربع/أرباع</option>
                                    <option value="ahzab">حزب/أحزاب</option>
                                    <option value="juzs">جزء/أجزاء</option>
                                    <option value="surahs">سورة/سور</option>
                                </select>
                                <select id="setup-f1-period" class="border rounded p-2 text-xs font-bold bg-gray-100 text-gray-500" disabled>
                                    <option value="weekly">توزع المستهدف على الأيام النشطة</option>
                                </select>
                            </div>
                        </div>
                        <div class="p-4 rounded-xl border border-cyan-100 bg-cyan-50/20">
                            <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
                                <input type="text" id="setup-f2-name" placeholder="اسم الحصن" class="border rounded p-2 text-xs font-bold text-cyan-900">
                                <input type="number" step="0.5" id="setup-f2-target" placeholder="الكمية المستهدفة" class="border rounded p-2 text-xs text-center font-bold">
                                <select id="setup-f2-unit" class="border rounded p-2 text-xs font-bold bg-white">
                                    <option value="pages">صفحة/صفحات</option>
                                    <option value="ayahs">آية/آيات</option>
                                    <option value="quarters">ربع/أرباع</option>
                                    <option value="ahzab">حزب/أحزاب</option>
                                    <option value="juzs">جزء/أجزاء</option>
                                    <option value="surahs">سورة/سور</option>
                                </select>
                                <select id="setup-f2-period" class="border rounded p-2 text-xs font-bold bg-gray-100 text-gray-500" disabled>
                                    <option value="daily">ورد ثابت في كل الأيام (لا يُقسّم)</option>
                                </select>
                            </div>
                        </div>
                        <div class="p-4 rounded-xl border border-indigo-100 bg-indigo-50/20">
                            <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
                                <input type="text" id="setup-f3-name" placeholder="اسم الحصن" class="border rounded p-2 text-xs font-bold text-indigo-900">
                                <input type="number" step="0.5" id="setup-f3-target" placeholder="الكمية المستهدفة" class="border rounded p-2 text-xs text-center font-bold">
                                <select id="setup-f3-unit" class="border rounded p-2 text-xs font-bold bg-white">
                                    <option value="pages">صفحة/صفحات</option>
                                    <option value="ayahs">آية/آيات</option>
                                    <option value="quarters">ربع/أرباع</option>
                                    <option value="ahzab">حزب/أحزاب</option>
                                    <option value="juzs">جزء/أجزاء</option>
                                    <option value="surahs">سورة/سور</option>
                                </select>
                                <select id="setup-f3-period" class="border rounded p-2 text-xs font-bold bg-gray-100 text-gray-500" disabled>
                                    <option value="weekly">توزع المستهدف على الأيام النشطة</option>
                                </select>
                            </div>
                        </div>
                        <div class="p-4 rounded-xl border border-amber-100 bg-amber-50/20">
                            <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
                                <input type="text" id="setup-f4-name" placeholder="اسم الحصن" class="border rounded p-2 text-xs font-bold text-amber-900">
                                <input type="number" step="0.5" id="setup-f4-target" placeholder="الكمية المستهدفة" class="border rounded p-2 text-xs text-center font-bold">
                                <select id="setup-f4-unit" class="border rounded p-2 text-xs font-bold bg-white">
                                    <option value="quarters">ربع/أرباع</option>
                                    <option value="pages">صفحة/صفحات</option>
                                    <option value="ayahs">آية/آيات</option>
                                    <option value="ahzab">حزب/أحزاب</option>
                                    <option value="juzs">جزء/أجزاء</option>
                                    <option value="surahs">سورة/سور</option>
                                </select>
                                <select id="setup-f4-period" class="border rounded p-2 text-xs font-bold bg-gray-100 text-gray-500" disabled>
                                    <option value="weekly">توزع المستهدف على الأيام النشطة</option>
                                </select>
                            </div>
                        </div>
                        <div class="p-4 rounded-xl border border-rose-100 bg-rose-50/20">
                            <div class="grid grid-cols-1 md:grid-cols-4 gap-2">
                                <input type="text" id="setup-f5-name" placeholder="اسم الحصن" class="border rounded p-2 text-xs font-bold text-rose-900">
                                <input type="number" step="0.5" id="setup-f5-target" placeholder="الكمية المستهدفة" class="border rounded p-2 text-xs text-center font-bold">
                                <select id="setup-f5-unit" class="border rounded p-2 text-xs font-bold bg-white">
                                    <option value="juzs">جزء/أجزاء</option>
                                    <option value="surahs">سورة/سور</option>
                                    <option value="pages">صفحة/صفحات</option>
                                    <option value="quarters">ربع/أرباع</option>
                                </select>
                                <select id="setup-f5-period" class="border rounded p-2 text-xs font-bold bg-gray-100 text-gray-500" disabled>
                                    <option value="daily">ورد يومي متصاعد (لا يُقسّم)</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Section 3: INDEPENDENT START POINTS FOR ALL 5 FORTS -->
                <div>
                    <h4 class="text-base font-bold text-emerald-950 mb-3 flex items-center gap-2">
                        <i class="fa-solid fa-map-location-dot text-emerald-700"></i> <span>٣. تحديد مواضع الانطلاق المستقلة (قوائم ذكية لكل حصن)</span>
                    </h4>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        
                        <!-- Block Template for JS Injection -->
                        <div id="sp-blocks-container" class="contents"></div>

                    </div>
                </div>

            </div>

            <div class="bg-gray-50 p-4 border-t border-gray-100 flex justify-end gap-2">
                <button onclick="closeSetupModal()" class="text-gray-500 hover:bg-gray-100 font-semibold px-4 py-2 rounded-lg text-sm transition">إلغاء</button>
                <button onclick="saveConfiguration()" class="quran-theme-bg text-white hover:bg-emerald-900 font-semibold px-5 py-2 rounded-lg text-sm transition">حفظ الخطة المخصصة</button>
            </div>
        </div>
    </div>

    <!-- Alert System toast -->
    <div id="custom-alert" class="hidden fixed bottom-6 left-6 z-50 bg-emerald-900 text-white px-6 py-4 rounded-xl shadow-2xl border-l-4 quran-gold-border flex items-center gap-3 transition-all duration-300 transform translate-y-10">
        <div class="w-8 h-8 rounded-full quran-gold-bg flex items-center justify-center text-emerald-900 font-bold"><i class="fa-solid fa-bell"></i></div>
        <div>
            <h5 class="font-bold text-sm" id="alert-title">تنبيه</h5>
            <p class="text-xs text-gray-200 mt-0.5" id="alert-msg">تمت العملية بنجاح</p>
        </div>
    </div>

    <script>
        // --- OFFLINE QURAN DATABASE (MADINAH MUSHAF) ---
        const uniqueSurahs = ["الفاتحة","البقرة","آل عمران","النساء","المائدة","الأنعام","الأعراف","الأنفال","التوبة","يونس","هود","يوسف","الرعد","إبراهيم","الحجر","النحل","الإسراء","الكهف","مريم","طه","الأنبياء","الحج","المؤمنون","النور","الفرقان","الشعراء","النمل","القصص","العنكبوت","الروم","لقمان","السجدة","الأحزاب","سبأ","فاطر","يس","الصافات","ص","الزمر","غافر","فصلت","الشورى","الزخرف","الدخان","الجاثية","الأحقاف","محمد","الفتح","الحجرات","ق","الذاريات","الطور","النجم","القمر","الرحمن","الواقعة","الحديد","المجادلة","الحشر","الممتحنة","الصف","الجمعة","المنافقون","التغابن","الطلاق","التحريم","الملك","القلم","الحاقة","المعارج","نوح","الجن","المزمل","المدثر","القيامة","الإنسان","المرسلات","النبأ","النازعات","عبس","التكوير","الانفطار","المطففين","الانشقاق","البروج","الطارق","الأعلى","الغاشية","الفجر","البلد","الشمس","الليل","الضحى","الشرح","التين","العلق","القدر","البينة","الزلزلة","العاديات","القارعة","التكاثر","العصر","الهمزة","الفيل","قريش","الماعون","الكوثر","الكافرون","النصر","المسد","الإخلاص","الفلق","الناس"];

        const quranQuarters = [
            "1. ۞ بِسْمِ ٱللَّهِ (الفاتحة 1)", "2. ۞ إِنَّ ٱللَّهَ لَا يَسْتَحْيِۦ (البقرة 26)", "3. ۞ أَتَأْمُرُونَ ٱلنَّاسَ (البقرة 44)", "4. ۞ وَإِذِ ٱسْتَسْقَىٰ (البقرة 60)",
            "5. ۞ أَفَتَطْمَعُونَ (البقرة 75)", "6. ۞ وَلَقَدْ جَآءَكُم (البقرة 92)", "7. ۞ مَا نَنسَخْ (البقرة 106)", "8. ۞ وَإِذِ ٱبْتَلَىٰ (البقرة 124)",
            "9. ۞ سَيَقُولُ ٱلسُّفَهَآءُ (البقرة 142)", "10. ۞ إِنَّ ٱلصَّفَا (البقرة 158)", "11. ۞ لَّيْسَ ٱلْبِرَّ (البقرة 177)", "12. ۞ يَسْـَٔلُونَكَ عَنِ ٱلْأَهِلَّةِ (البقرة 189)",
            "13. ۞ وَٱذْكُرُوا۟ ٱللَّهَ (البقرة 203)", "14. ۞ وَمِنَ ٱلنَّاسِ (البقرة 213)", "15. ۞ ٱلْوَٰلِدَٰتُ (البقرة 233)", "16. ۞ أَلَمْ تَرَ إِلَى ٱلَّذِينَ (البقرة 243)",
            "17. ۞ تِلْكَ ٱلرُّسُلُ (البقرة 253)", "18. ۞ مَّثَلُ ٱلَّذِينَ يُنفِقُونَ (البقرة 263)", "19. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوٓا۟ أَنفِقُوا۟ (البقرة 267)", "20. ۞ لِّلْفُقَرَآءِ (البقرة 274)",
            "21. ۞ الم (آل عمران 1)", "22. ۞ قُلْ أَؤُنَبِّئُكُم (آل عمران 15)", "23. ۞ فَكَيْفَ إِذَا (آل عمران 25)", "24. ۞ قُلْ إِن تُخْفُوا۟ (آل عمران 33)",
            "25. ۞ لَن تَنَالُوا۟ ٱلْبِرَّ (آل عمران 93)", "26. ۞ لَيْسُوا۟ سَوَآءً (آل عمران 113)", "27. ۞ وَسَارِعُوٓا۟ (آل عمران 133)", "28. ۞ وَمَا مُحَمَّدٌ (آل عمران 145)",
            "29. ۞ لَقَدْ مَنَّ ٱللَّهُ (آل عمران 164)", "30. ۞ وَلَا تَحْسَبَنَّ (آل عمران 171)", "31. ۞ فَٱسْتَجَابَ لَهُمْ (آل عمران 196)", "32. ۞ وَٱلْمُحْصَنَـٰتُ (النساء 24)",
            "33. ۞ وَٱلْمُحْصَنَـٰتُ (النساء 24)", "34. ۞ وَٱعْبُدُوا۟ ٱللَّهَ (النساء 36)", "35. ۞ إِنَّ ٱللَّهَ يَأْمُرُكُمْ (النساء 58)", "36. ۞ فَمَا لَكُمْ فِى ٱلْمُنَـٰفِقِينَ (النساء 88)",
            "37. ۞ وَمَن يُهَاجِرْ (النساء 100)", "38. ۞ لَّا خَيْرَ فِى كَثِيرٍ (النساء 114)", "39. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ كُونُوا۟ (النساء 135)", "40. ۞ لَّا يُحِبُّ ٱللَّهُ (النساء 148)",
            "41. ۞ لَّا يُحِبُّ ٱللَّهُ ٱلْجَهْرَ (النساء 148)", "42. ۞ يَسْـَٔلُكَ أَهْلُ ٱلْكِتَـٰبِ (النساء 153)", "43. ۞ إِنَّ ٱلَّذِينَ كَفَرُوا۟ (النساء 167)", "44. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوٓا۟ أَوْفُوا۟ (المائدة 1)",
            "45. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ ٱذْكُرُوا۟ (المائدة 11)", "46. ۞ وَلَقَدْ أَخَذَ ٱللَّهُ (المائدة 12)", "47. ۞ إِنَّمَا جَزَٰٓؤُا۟ ٱلَّذِينَ (المائدة 33)", "48. ۞ يَـٰٓأَيُّهَا ٱلرَّسُولُ (المائدة 41)",
            "49. ۞ لَتَجِدَنَّ أَشَدَّ ٱلنَّاسِ (المائدة 82)", "50. ۞ أُحِلَّ لَكُمْ صَيْدُ ٱلْبَحْرِ (المائدة 96)", "51. ۞ وَإِذْ قَالَ ٱللَّهُ يَـٰعِيسَى (المائدة 116)", "52. ۞ ٱلْحَمْدُ لِلَّهِ ٱلَّذِى (الأنعام 1)",
            "53. ۞ وَلَهُۥ مَا سَكَنَ (الأنعام 13)", "54. ۞ قُلْ أَىُّ شَىْءٍ أَكْبَرُ (الأنعام 19)", "55. ۞ وَلَوْ تَرَىٰٓ إِذْ وُقِفُوا۟ (الأنعام 27)", "56. ۞ إِنَّمَا يَسْتَجِيبُ (الأنعام 36)",
            "57. ۞ وَإِن تَعْتَدُوا۟ (الأنعام 59)", "58. ۞ قُلْ نَدْعُوا۟ (الأنعام 71)", "59. ۞ وَمَنْ أَظْلَمُ (الأنعام 93)", "60. ۞ وَلَوْ أَنَّنَا نَزَّلْنَا (الأنعام 111)",
            "61. ۞ وَلَوْ أَنَّنَا نَزَّلْنَا (الأنعام 111)", "62. ۞ وَمَا لَكُمْ (الأنعام 119)", "63. ۞ سَيَقُولُ ٱلَّذِينَ أَشْرَكُوا۟ (الأنعام 148)", "64. ۞ إِنَّمَا ٱلسَّبِيلُ (الأعراف 1)",
            "65. ۞ إِنَّمَا ٱلسَّبِيلُ (الأعراف 1)", "66. ۞ يَـٰبَنِىٓ ءَادَمَ (الأعراف 26)", "67. ۞ قُلْ أَمَرَ رَبِّى (الأعراف 29)", "68. ۞ لَقَدْ أَرْسَلْنَا (الأعراف 59)",
            "69. ۞ قَالَ ٱلْمَلَأُ (الأعراف 88)", "70. ۞ وَمَا وَجَدْنَا (الأعراف 102)", "71. ۞ حَقِيقٌ عَلَىٰ (الأعراف 105)", "72. ۞ وَقَالَ ٱلْمَلَأُ (الأعراف 127)",
            "73. ۞ وَلَمَّا سَكَتَ (الأعراف 154)", "74. ۞ وَٱكْتُبْ لَنَا (الأعراف 156)", "75. ۞ وَإِذْ نَتَقْنَا (الأعراف 171)", "76. ۞ يَسْـَٔلُونَكَ عَنِ ٱلسَّاعَةِ (الأعراف 187)",
            "77. ۞ وَٱعْلَمُوٓا۟ أَنَّمَا (الأنفال 41)", "78. ۞ إِذْ أَنتُم (الأنفال 42)", "79. ۞ وَإِن جَنَحُوا۟ (الأنفال 61)", "80. ۞ بَرَآءَةٌ (التوبة 1)",
            "81. ۞ إِنَّمَا ٱلصَّدَقَـٰتُ (التوبة 60)", "82. ۞ أَلَمْ يَعْلَمُوٓا۟ (التوبة 63)", "83. ۞ فَرِحَ ٱلْمُخَلَّفُونَ (التوبة 81)", "84. ۞ وَمَا كَانَ ٱلْمُؤْمِنُونَ (التوبة 92)",
            "85. ۞ إِنَّ ٱللَّهَ ٱشْتَرَىٰ (التوبة 111)", "86. ۞ وَمَا كَانَ ٱسْتِغْفَارُ (التوبة 114)", "87. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ ٱتَّقُوا۟ (التوبة 119)", "88. ۞ الر (يونس 1)",
            "89. ۞ لِّلَّذِينَ أَحْسَنُوا۟ (يونس 26)", "90. ۞ وَمَا ظَنُّ (يونس 60)", "91. ۞ أَلَآ إِنَّ أَوْلِيَآءَ ٱللَّهِ (يونس 62)", "92. ۞ فَمَآ ءَامَنَ لِمُوسَىٰ (يونس 83)",
            "93. ۞ وَمَا مِن دَآبَّةٍ (هود 1)", "94. ۞ أَمْ يَقُولُونَ (هود 13)", "95. ۞ وَلَقَدْ أَرْسَلْنَا (هود 25)", "96. ۞ وَإِلَىٰ عَادٍ (هود 50)",
            "97. ۞ وَإِلَىٰ ثَمُودَ (هود 61)", "98. ۞ فَلَمَّا جَآءَ (هود 82)", "99. ۞ قَالَ يَـٰقَوْمِ (هود 88)", "100. ۞ وَمَآ أُبَرِّئُ (يوسف 53)",
            "101. ۞ وَمَآ أُبَرِّئُ نَفْسِى (يوسف 53)", "102. ۞ قَالُوٓا۟ إِن يَسْرِقْ (يوسف 77)", "103. ۞ وَلَمَّا فَصَلَتِ (يوسف 94)", "104. ۞ الر (الرعد 1)",
            "105. ۞ أَفَمَن يَعْلَمُ (الرعد 19)", "106. ۞ وَلَقَدْ أَرْسَلْنَا (الرعد 38)", "107. ۞ الر (إبراهيم 1)", "108. ۞ أَلَمْ تَرَ إِلَى ٱلَّذِينَ (إبراهيم 28)",
            "109. ۞ الر (الحجر 1)", "110. ۞ ۞ نَبِّئْ عِبَادِى (الحجر 49)", "111. ۞ قَالَ فَمَا خَطْبُكُمْ (الحجر 57)", "112. ۞ أَتَىٰٓ أَمْرُ ٱللَّهِ (النحل 1)",
            "113. ۞ وَمَا بِكُم (النحل 53)", "114. ۞ ضَرَبَ ٱللَّهُ (النحل 75)", "115. ۞ وَيَوْمَ نَبْعَثُ (النحل 84)", "116. ۞ إِنَّ ٱللَّهَ يَأْمُرُ (النحل 90)",
            "117. ۞ سُبْحَـٰنَ ٱلَّذِىٓ (الإسراء 1)", "118. ۞ وَإِذَآ أَرَدْنَا (الإسراء 16)", "119. ۞ وَقَضَىٰ رَبُّكَ (الإسراء 23)", "120. ۞ وَإِذَا قَرَأْتَ (الإسراء 45)",
            "121. ۞ قُل لَّوْ أَنتُمْ (الإسراء 100)", "122. ۞ ٱلْحَمْدُ لِلَّهِ (الكهف 1)", "123. ۞ وَٱضْرِبْ لَهُم (الكهف 32)", "124. ۞ قَالَ أَلَمْ أَقُلْ لَّكَ (الكهف 75)",
            "125. ۞ قَالَ أَلَمْ أَقُل (الكهف 75)", "126. ۞ حَتَّىٰٓ إِذَا بَلَغَ (الكهف 83)", "127. ۞ كٓهيعٓصٓ (مريم 1)", "128. ۞ فَخَلَفَ مِنۢ بَعْدِهِمْ (مريم 59)",
            "129. ۞ طه (طه 1)", "130. ۞ مِنْهَا خَلَقْنَـٰكُمْ (طه 55)", "131. ۞ إِنَّمَآ إِلَـٰهُكُمُ (طه 98)", "132. ۞ وَمَنْ أَعْرَضَ (طه 124)",
            "133. ۞ ٱقْتَرَبَ لِلنَّاسِ (الأنبياء 1)", "134. ۞ وَلَقَدْ ءَاتَيْنَا (الأنبياء 51)", "135. ۞ وَدَاوُۥدَ وَسُلَيْمَـٰنَ (الأنبياء 78)", "136. ۞ إِنَّ ٱلَّذِينَ سَبَقَتْ (الأنبياء 101)",
            "137. ۞ يَـٰٓأَيُّهَا ٱلنَّاسُ (الحج 1)", "138. ۞ هَـٰذَانِ خَصْمَانِ (الحج 19)", "139. ۞ إِنَّ ٱللَّهَ يُدَٰفِعُ (الحج 38)", "140. ۞ أَلَمْ تَرَ أَنَّ ٱللَّهَ (الحج 63)",
            "141. ۞ قَدْ أَفْلَحَ (المؤمنون 1)", "142. ۞ وَلَقَدْ أَرْسَلْنَا (المؤمنون 23)", "143. ۞ فَذَرْهُمْ فِى غَمْرَتِهِمْ (المؤمنون 54)", "144. ۞ حَتَّىٰٓ إِذَآ أَخَذْنَا (المؤمنون 64)",
            "145. ۞ سُورَةٌ أَنزَلْنَـٰهَا (النور 1)", "146. ۞ إِنَّ ٱلَّذِينَ جَآءُو (النور 11)", "147. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ لَا تَدْخُلُوا۟ (النور 27)", "148. ۞ ٱللَّهُ نُورُ ٱلسَّمَـٰوَٰتِ (النور 35)",
            "149. ۞ وَقَالَ ٱلَّذِينَ (الفرقان 21)", "150. ۞ أَلَمْ تَرَ إِلَىٰ رَبِّكَ (الفرقان 45)", "151. ۞ وَعِبَادُ ٱلرَّحْمَـٰنِ (الفرقان 63)", "152. ۞ طسم (الشعراء 1)",
            "153. ۞ قَالُوٓا۟ أَنُؤْمِنُ (الشعراء 111)", "154. ۞ كَذَّبَتْ ثَمُودُ (الشعراء 141)", "155. ۞ طس (النمل 1)", "156. ۞ وَتَفَقَّدَ ٱلطَّيْرَ (النمل 20)",
            "157. ۞ فَمَا كَانَ (النمل 56)", "158. ۞ أَمَّنْ خَلَقَ (النمل 60)", "159. ۞ طسم (القصص 1)", "160. ۞ وَلَمَّا وَرَدَ (القصص 23)",
            "161. ۞ وَقَالَ ٱلَّذِينَ أُوتُوا۟ (القصص 79)", "162. ۞ الم (العنكبوت 1)", "163. ۞ وَلَمَّآ أَن جَآءَتْ (العنكبوت 31)", "164. ۞ ٱتْلُ مَآ أُوحِىَ (العنكبوت 45)",
            "165. ۞ وَلَا تُجَٰدِلُوٓا۟ (العنكبوت 46)", "166. ۞ الم (الروم 1)", "167. ۞ ضَرَبَ لَكُم (الروم 28)", "168. ۞ الم (لقمان 1)",
            "169. ۞ وَمَن يُسْلِمْ (لقمان 22)", "170. ۞ الم (السجدة 1)", "171. ۞ يَـٰٓأَيُّهَا ٱلنَّبِىُّ (الأحزاب 1)", "172. ۞ لَّقَدْ كَانَ لَكُمْ (الأحزاب 21)",
            "173. ۞ ۞ وَمَن يَقْنُتْ (الأحزاب 31)", "174. ۞ تُرْجِى مَن تَشَآءُ (الأحزاب 51)", "175. ۞ إِنَّ ٱللَّهَ وَمَلَـٰٓئِكَتَهُۥ (الأحزاب 56)", "176. ۞ ٱلْحَمْدُ لِلَّهِ (سبأ 1)",
            "177. ۞ قُلْ مَن يَرْزُقُكُم (سبأ 24)", "178. ۞ ٱلْحَمْدُ لِلَّهِ (فاطر 1)", "179. ۞ إِنَّ ٱللَّهَ يُمْسِكُ (فاطر 41)", "180. ۞ يس (يس 1)",
            "181. ۞ وَمَآ أَنزَلْنَا (يس 28)", "182. ۞ أَوَلَمْ يَرَ ٱلْإِنسَـٰنُ (يس 77)", "183. ۞ وَٱلصَّـٰٓفَّـٰتِ (الصافات 1)", "184. ۞ فَنَبَذْنَـٰهُ (الصافات 144)",
            "185. ۞ ص (ص 1)", "186. ۞ وَٱذْكُرْ عَبْدَنَآ (ص 41)", "187. ۞ تَنزِيلُ ٱلْكِتَـٰبِ (الزمر 1)", "188. ۞ أَمَّنْ هُوَ قَـٰنِتٌ (الزمر 9)",
            "189. ۞ فَمَنْ أَظْلَمُ (الزمر 32)", "190. ۞ قُلْ يَـٰعِبَادِىَ (الزمر 53)", "191. ۞ حم (غافر 1)", "192. ۞ وَقَالَ رَجُلٌ (غافر 28)",
            "193. ۞ إِلَيْهِ يُرَدُّ (فصلت 47)", "194. ۞ وَلَئِنْ أَذَقْنَـٰهُ (فصلت 50)", "195. ۞ حم (الشورى 1)", "196. ۞ شَرَعَ لَكُم (الشورى 13)",
            "197. ۞ حم (الزخرف 1)", "198. ۞ وَلَمَّا ضُرِبَ (الزخرف 57)", "199. ۞ حم (الدخان 1)", "200. ۞ حم (الجاثية 1)",
            "201. ۞ حم (الأحقاف 1)", "202. ۞ وَٱذْكُرْ أَخَا عَادٍ (الأحقاف 21)", "203. ۞ ٱلَّذِينَ كَفَرُوا۟ (محمد 1)", "204. ۞ فَهَلْ عَسَيْتُمْ (محمد 22)",
            "205. ۞ إِنَّا فَتَحْنَا (الفتح 1)", "206. ۞ لَّقَدْ رَضِىَ ٱللَّهُ (الفتح 18)", "207. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ (الحجرات 1)", "208. ۞ ق (ق 1)",
            "209. ۞ ۞ قَالَ فَمَا خَطْبُكُمْ (الذاريات 31)", "210. ۞ وَٱلطُّورِ (الطور 1)", "211. ۞ وَٱلنَّجْمِ (النجم 1)", "212. ۞ ٱقْتَرَبَتِ ٱلسَّاعَةُ (القمر 1)",
            "213. ۞ ٱلرَّحْمَـٰنُ (الرحمن 1)", "214. ۞ إِذَا وَقَعَتِ (الواقعة 1)", "215. ۞ ۞ فَلَآ أُقْسِمُ (الواقعة 75)", "216. ۞ سَبَّحَ لِلَّهِ (الحديد 1)",
            "217. ۞ قَدْ سَمِعَ ٱللَّهُ (المجادلة 1)", "218. ۞ ۞ أَلَمْ تَرَ إِلَى ٱلَّذِينَ (المجادلة 14)", "219. ۞ سَبَّحَ لِلَّهِ (الحشر 1)", "220. ۞ لَا يَسْتَوِىٓ (الحشر 20)",
            "221. ۞ يَـٰٓأَيُّهَا ٱلَّذِينَ ءَامَنُوا۟ (الممتحنة 1)", "222. ۞ سَبَّحَ لِلَّهِ (الصف 1)", "223. ۞ يُسَبِّحُ لِلَّهِ (الجمعة 1)", "224. ۞ يُسَبِّحُ لِلَّهِ (التغابن 1)",
            "225. ۞ تَبَـٰرَكَ ٱلَّذِى (الملك 1)", "226. ۞ ن (القلم 1)", "227. ۞ ٱلْحَآقَّةُ (الحاقة 1)", "228. ۞ سَأَلَ سَآئِلٌۢ (المعارج 1)",
            "229. ۞ إِنَّآ أَرْسَلْنَا (نوح 1)", "230. ۞ قُلْ أُوحِىَ (الجن 1)", "231. ۞ يَـٰٓأَيُّهَا ٱلْمُزَّمِّلُ (المزمل 1)", "232. ۞ لَآ أُقْسِمُ (القيامة 1)",
            "233. ۞ ۞ عَمَّ يَتَسَآءَلُونَ (النبأ 1)", "234. ۞ عَبَسَ (عبس 1)", "235. ۞ وَيْلٌ لِّلْمُطَفِّفِينَ (المطففين 1)", "236. ۞ وَٱلسَّمَآءِ وَٱلطَّارِقِ (الطارق 1)",
            "237. ۞ وَٱلْفَجْرِ (الفجر 1)", "238. ۞ وَٱلضُّحَىٰ (الضحى 1)", "239. ۞ لَمْ يَكُنِ (البينة 1)", "240. ۞ أَلْهَىٰكُمُ (التكاثر 1)"
        ];

        const quranHizbs = [];
        for(let i = 0; i < 60; i++) {
            const quarterIndex = i * 4;
            const correspondingQuarter = quranQuarters[quarterIndex];
            const cleanText = correspondingQuarter.replace(/^[0-9]+\.\s*/, '');
            quranHizbs.push(`حزب ${i + 1}: ${cleanText}`);
        }

        // Generate Start Point UI blocks for 5 Forts
        function renderStartPointBlocks() {
            const container = document.getElementById('sp-blocks-container');
            let html = '';
            const fortTitles = ["الحصن الأول", "الحصن الثاني", "الحصن الثالث", "الحصن الرابع", "الحصن الخامس"];
            
            for(let i=1; i<=5; i++) {
                const fId = `f${i}`;
                html += `
                <div class="border p-4 rounded-xl bg-gray-50 flex flex-col gap-3 shadow-sm">
                    <span class="block font-bold text-emerald-900 text-xs">بداية انطلاق ${fortTitles[i-1]}</span>
                    <div class="grid grid-cols-2 gap-2">
                        <label class="block text-xs text-gray-500 mb-0.5 font-semibold">تحديد عبر:</label>
                        <select id="setup-${fId}-type" onchange="toggleFType('${fId}')" class="border rounded p-2 text-xs font-bold bg-white">
                            <option value="surah">السورة والآية</option>
                            <option value="page">رقم الصفحة</option>
                            <option value="quarter">رقم الربع</option>
                            <option value="hizb">رقم الحزب</option>
                            <option value="juz">رقم الجزء</option>
                        </select>
                    </div>
                    
                    <div id="${fId}-surah-box" class="grid grid-cols-2 gap-2">
                        <select id="setup-${fId}-surah" class="border rounded p-2 text-xs font-bold bg-white w-full custom-dropdown-surah"></select>
                        <input type="number" id="setup-${fId}-ayah" min="1" placeholder="رقم الآية" class="border rounded p-2 text-xs text-center font-bold bg-white">
                    </div>
                    <div id="${fId}-page-box" class="hidden">
                        <select id="setup-${fId}-page" class="border rounded p-2 text-xs font-bold bg-white w-full custom-dropdown-page"></select>
                    </div>
                    <div id="${fId}-quarter-box" class="hidden">
                        <select id="setup-${fId}-quarter" class="border rounded p-2 text-xs font-bold bg-white w-full custom-dropdown-quarter"></select>
                    </div>
                    <div id="${fId}-hizb-box" class="hidden">
                        <select id="setup-${fId}-hizb" class="border rounded p-2 text-xs font-bold bg-white w-full custom-dropdown-hizb"></select>
                    </div>
                    <div id="${fId}-juz-box" class="hidden">
                        <select id="setup-${fId}-juz" class="border rounded p-2 text-xs font-bold bg-white w-full custom-dropdown-juz"></select>
                    </div>
                </div>`;
            }
            container.innerHTML = html;
        }

        // Setup UI Toggles
        function toggleFType(fId) {
            const type = document.getElementById(`setup-${fId}-type`).value;
            const boxes = ['surah', 'page', 'quarter', 'hizb', 'juz'];
            boxes.forEach(b => {
                const el = document.getElementById(`${fId}-${b}-box`);
                if(el) {
                    if (b === type) el.classList.remove('hidden');
                    else el.classList.add('hidden');
                }
            });
        }

        function populateQuranDropdowns() {
            renderStartPointBlocks();

            const surahSelects = document.querySelectorAll('.custom-dropdown-surah');
            let surahOptions = "";
            uniqueSurahs.forEach((surah, index) => { surahOptions += `<option value="${index + 1}">${index + 1}. سورة ${surah}</option>`; });
            surahSelects.forEach(select => select.innerHTML = surahOptions);

            const pageSelects = document.querySelectorAll('.custom-dropdown-page');
            let pageOptions = "";
            for (let i = 1; i <= 604; i++) { pageOptions += `<option value="${i}">الصفحة ${i}</option>`; }
            pageSelects.forEach(select => select.innerHTML = pageOptions);

            const quarterSelects = document.querySelectorAll('.custom-dropdown-quarter');
            let quarterOptions = "";
            quranQuarters.forEach((quarter, index) => { quarterOptions += `<option value="${index}">${quarter}</option>`; });
            quarterSelects.forEach(select => select.innerHTML = quarterOptions);

            const hizbSelects = document.querySelectorAll('.custom-dropdown-hizb');
            let hizbOptions = "";
            quranHizbs.forEach((hizb, index) => { hizbOptions += `<option value="${index}">${hizb}</option>`; });
            hizbSelects.forEach(select => select.innerHTML = hizbOptions);

            const juzSelects = document.querySelectorAll('.custom-dropdown-juz');
            let juzOptions = "";
            for (let i = 1; i <= 30; i++) { juzOptions += `<option value="${i}">الجزء ${i}</option>`; }
            juzSelects.forEach(select => select.innerHTML = juzOptions);
        }

        // ================= STATE MANAGEMENT =================
        let state = {
            config: {
                forts: {
                    f1: { name: "الحصن الأول: حفظ جديد", target: 2, unit: "pages" },
                    f2: { name: "الحصن الثاني: تحضير قبلي", target: 2, unit: "pages" },
                    f3: { name: "الحصن الثالث: مراجعة قريب", target: 20, unit: "pages" },
                    f4: { name: "الحصن الرابع: مراجعة بعيد", target: 2, unit: "quarters" },
                    f5: { name: "الحصن الخامس: الختمة السردية", target: 1, unit: "juzs" }
                },
                startPoints: {
                    f1: { type: "page", surahNum: 2, ayahNum: 1, pageNum: 2, quarterIdx: 0, hizbIdx: 0, juzNum: 1 },
                    f2: { type: "page", surahNum: 2, ayahNum: 1, pageNum: 4, quarterIdx: 0, hizbIdx: 0, juzNum: 1 },
                    f3: { type: "page", surahNum: 78, ayahNum: 1, pageNum: 582, quarterIdx: 232, hizbIdx: 58, juzNum: 30 },
                    f4: { type: "quarter", surahNum: 1, ayahNum: 1, pageNum: 1, quarterIdx: 0, hizbIdx: 0, juzNum: 1 },
                    f5: { type: "juz", surahNum: 1, ayahNum: 1, pageNum: 1, quarterIdx: 0, hizbIdx: 0, juzNum: 1 }
                },
                startDateString: "2026-06-13", 
                activeDays: {
                    Saturday: true, Sunday: true, Monday: true, Tuesday: true, Wednesday: true, Thursday: true, Friday: true
                }
            },
            progress: {
                Saturday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Sunday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Monday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Tuesday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Wednesday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Thursday: { f1: false, f2: false, f3: false, f4: false, f5: false },
                Friday: { f1: false, f2: false, f3: false, f4: false, f5: false }
            },
            notes: ""
        };

        const unitTranslations = {
            pages: { sing: "صفحة", plur: "صفحات" },
            juzs: { sing: "جزء", plur: "أجزاء" },
            ahzab: { sing: "حزب", plur: "أحزاب" },
            surahs: { sing: "سورة", plur: "سور" },
            ayahs: { sing: "آية", plur: "آيات" },
            quarters: { sing: "ربع", plur: "أرباع" }
        };

        window.onload = function() {
            populateQuranDropdowns();
            loadSavedData();
            updateDashboard();
        }

        function loadSavedData() {
            const savedState = localStorage.getItem('five_forts_ultimate_v3');
            if (savedState) {
                try {
                    const parsed = JSON.parse(savedState);
                    state = { ...state, ...parsed };
                    if (state.config.startDateString !== "2026-06-13") {
                        state.config.startDateString = "2026-06-13";
                        saveData();
                    }
                    document.getElementById('user-notes').value = state.notes || "";
                } catch (e) {}
            } else {
                state.config.startDateString = "2026-06-13";
                saveData();
            }
        }

        function saveData() {
            state.notes = document.getElementById('user-notes').value;
            localStorage.setItem('five_forts_ultimate_v3', JSON.stringify(state));
        }

        function getArabicUnitName(unit, qty) {
            const trans = unitTranslations[unit];
            if (!trans) return unit;
            return qty <= 2 && qty > 0 ? trans.sing : trans.plur;
        }

        function getArabicDayName(day) {
            const map = { Saturday: "السبت", Sunday: "الأحد", Monday: "الإثنين", Tuesday: "الثلاثاء", Wednesday: "الأربعاء", Thursday: "الخميس", Friday: "الجمعة" };
            return map[day] || day;
        }

        // ================= CONTACT MODAL =================
        function openContactModal() { document.getElementById('contact-modal').classList.remove('hidden'); }
        function closeContactModal() { document.getElementById('contact-modal').classList.add('hidden'); }

        // ================= CORE LOGIC =================
        function calculateTargets() {
            const list = [];
            const daysOrder = ["Saturday", "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday"];
            const startOfWeekDate = new Date(state.config.startDateString);
            
            const activeDaysMap = state.config.activeDays;
            const activeDaysCount = Object.values(activeDaysMap).filter(Boolean).length || 1;

            // Deep clone tracking to prevent mutating original state during render
            let trackingValues = JSON.parse(JSON.stringify(state.config.startPoints));

            daysOrder.forEach((dayId, index) => {
                const thisDayDate = new Date(startOfWeekDate);
                thisDayDate.setDate(startOfWeekDate.getDate() + index);
                const formattedDate = thisDayDate.toLocaleDateString('ar-EG', { day: 'numeric', month: 'short' });
                
                let row = {
                    dayId: dayId,
                    dayLabel: `${getArabicDayName(dayId)} (${formattedDate})`,
                    isActive: activeDaysMap[dayId],
                    rawTargets: { f1: 0, f2: 0, f3: 0, f4: 0, f5: 0 },
                    f1Text: "—", f2Text: "—", f3Text: "—", f4Text: "—", f5Text: "—"
                };

                ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                    const fort = state.config.forts[fId];
                    let isDivided = (fId !== 'f2' && fId !== 'f5'); 
                    let dailyVal = 0;

                    if (isDivided) {
                        dailyVal = fort.target / activeDaysCount;
                    } else {
                        dailyVal = fort.target; // F2 and F5 take full target
                    }

                    let isStatic = (fId === 'f2'); // Preparation doesn't increment the tracker

                    if (row.isActive || fId === 'f5') { // F5 might be every day, or just active days
                        if (!row.isActive && fId !== 'f5') return; // Only process active days for non-F5

                        row.rawTargets[fId] = dailyVal;
                        let sp = trackingValues[fId];
                        let quantityStr = `${formatDecimal(dailyVal)} ${getArabicUnitName(fort.unit, dailyVal)}`;
                        
                        let startVal;
                        if(sp.type === 'page') startVal = sp.pageNum;
                        else if(sp.type === 'juz') startVal = sp.juzNum;
                        else if(sp.type === 'quarter') startVal = sp.quarterIdx;
                        else if(sp.type === 'hizb') startVal = sp.hizbIdx;
                        else startVal = sp.ayahNum;

                        let endVal = startVal + (isStatic ? fort.target : dailyVal);
                        let spText = "";

                        if(sp.type === 'page') {
                            spText = `من ص ${formatDecimal(startVal)} إلى ص ${formatDecimal(endVal)}`;
                        } else if(sp.type === 'juz') {
                            spText = `من الجزء ${formatDecimal(startVal)} إلى ${formatDecimal(endVal)}`;
                        } else if(sp.type === 'quarter') {
                            let qName = quranQuarters[Math.floor(startVal)] || `الربع ${startVal+1}`;
                            spText = `(${qName.replace(/^[0-9]+\.\s*/, '')})`;
                        } else if(sp.type === 'hizb') {
                            let hName = quranHizbs[Math.floor(startVal)] || `الحزب ${startVal+1}`;
                            spText = `(${hName})`;
                        } else {
                            spText = `سورة ${uniqueSurahs[sp.surahNum-1]} (آية ${formatDecimal(startVal)} إلى ${formatDecimal(endVal)})`;
                        }

                        row[`${fId}Text`] = `<span class="font-bold">${quantityStr}</span><br><span class="text-[10px] font-medium text-gray-500">${spText}</span>`;

                        if (!isStatic) {
                            if(sp.type === 'page') sp.pageNum = endVal;
                            else if(sp.type === 'juz') sp.juzNum = endVal;
                            else if(sp.type === 'quarter') sp.quarterIdx = endVal;
                            else if(sp.type === 'hizb') sp.hizbIdx = endVal;
                            else sp.ayahNum = endVal;
                        }
                    } else {
                        row[`${fId}Text`] = `<span class="text-gray-400 italic">راحة</span>`;
                    }
                });
                list.push(row);
            });
            return list;
        }

        function formatDecimal(num) { return Number(num.toFixed(2)).toString(); }

        function updateDashboard() {
            const schedule = calculateTargets();
            const tbody = document.getElementById('schedule-tbody');
            tbody.innerHTML = '';

            const forts = state.config.forts;
            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach((fId, index) => {
                document.getElementById(`tbl-col-${index+1}`).innerText = forts[fId].name;
                document.getElementById(`title-card-${index+1}`).innerText = forts[fId].name;
            });

            const logSelector = document.getElementById('log-day');
            const prevSelect = logSelector.value;
            logSelector.innerHTML = '';

            let progressCounts = { f1: 0, f2: 0, f3: 0, f4: 0, f5: 0 };
            let totalTasks = 0, completedTasks = 0;

            schedule.forEach(row => {
                const prog = state.progress[row.dayId];
                const opt = document.createElement('option');
                opt.value = row.dayId;
                opt.innerText = row.dayLabel;
                logSelector.appendChild(opt);

                ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                    const rawTarget = row.rawTargets[fId];
                    if (rawTarget > 0) {
                        totalTasks++;
                        if (prog[fId]) {
                            progressCounts[fId] += rawTarget;
                            completedTasks++;
                        }
                    }
                });

                const isDayDone = (!row.isActive || (
                    (row.rawTargets.f1 === 0 || prog.f1) &&
                    (row.rawTargets.f2 === 0 || prog.f2) &&
                    (row.rawTargets.f3 === 0 || prog.f3) &&
                    (row.rawTargets.f4 === 0 || prog.f4)
                )) && (row.rawTargets.f5 === 0 || prog.f5);

                const bgClass = isDayDone ? 'bg-emerald-50/70 hover:bg-emerald-100/70' : 'hover:bg-gray-50';

                const tr = document.createElement('tr');
                tr.className = `${bgClass} transition-colors duration-150`;
                tr.innerHTML = `
                    <td class="p-4 text-xs font-bold text-gray-900 border-b border-gray-100">
                        <span>${row.dayLabel}</span>
                        ${isDayDone ? '<span class="text-emerald-600 block text-[10px] mt-1"><i class="fa-solid fa-circle-check"></i> مكتمل</span>' : ''}
                    </td>
                    <td class="p-4 text-[11px] text-gray-700 border-b border-gray-100 ${prog.f1 && row.rawTargets.f1>0 ? 'opacity-50 line-through' : ''}">${row.f1Text}</td>
                    <td class="p-4 text-[11px] text-gray-700 border-b border-gray-100 ${prog.f2 && row.rawTargets.f2>0 ? 'opacity-50 line-through' : ''}">${row.f2Text}</td>
                    <td class="p-4 text-[11px] text-gray-700 border-b border-gray-100 ${prog.f3 && row.rawTargets.f3>0 ? 'opacity-50 line-through' : ''}">${row.f3Text}</td>
                    <td class="p-4 text-[11px] text-gray-700 border-b border-gray-100 ${prog.f4 && row.rawTargets.f4>0 ? 'opacity-50 line-through' : ''}">${row.f4Text}</td>
                    <td class="p-4 text-[11px] text-gray-700 border-b border-gray-100 ${prog.f5 && row.rawTargets.f5>0 ? 'opacity-50 line-through' : ''}">${row.f5Text}</td>
                `;
                tbody.appendChild(tr);
            });

            if (prevSelect && Array.from(logSelector.options).some(o => o.value === prevSelect)) {
                logSelector.value = prevSelect;
            }

            const overallPercentage = totalTasks > 0 ? Math.round((completedTasks / totalTasks) * 100) : 0;
            document.getElementById('week-summary-percentage').innerText = `معدل الإنجاز العام: ${overallPercentage}%`;
            
            const dStr = state.config.startDateString.split('-');
            document.getElementById('badge-week-start').innerText = `تاريخ البداية: ${dStr[2]}-${dStr[1]}-${dStr[0]}`;
            
            const activeDaysAr = Object.keys(state.config.activeDays).filter(d => state.config.activeDays[d]).map(d => getArabicDayName(d)).join('، ');
            document.getElementById('badge-active-days').innerText = `الأيام النشطة: ${activeDaysAr}`;

            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                const fort = forts[fId];
                // Display calculations for cards (just visual summaries)
                const isDaily = (fId === 'f2' || fId === 'f5');
                const totalTarget = isDaily ? fort.target * 7 : fort.target;
                const done = progressCounts[fId];
                
                const unitName = getArabicUnitName(fort.unit, totalTarget);
                const periodLabel = isDaily ? 'يومي (ثابت/متصاعد)' : 'أسبوعي (مقسم)';

                document.getElementById(`target-badge-${fId}`).innerText = `${fort.target} ${getArabicUnitName(fort.unit, fort.target)} / ${periodLabel}`;
                document.getElementById(`stat-${fId}-val`).innerText = `${formatDecimal(done)} / ${totalTarget} ${unitName}`;
                
                const pct = totalTarget > 0 ? Math.min(100, Math.round((done / totalTarget) * 100)) : 0;
                document.getElementById(`stat-${fId}-bar`).style.width = `${pct}%`;
                document.getElementById(`stat-${fId}-perc`).innerText = `${pct}% مكتمل`;
            });

            updateLoggerHelperTexts();
            syncAudioAndAIPanelDefaults();
        }

        function syncAudioAndAIPanelDefaults() {
            const sp = state.config.startPoints.f1;
            if (sp.type === 'surah') {
                document.getElementById('audio-surah').value = sp.surahNum || 1;
                document.getElementById('audio-ayah').value = sp.ayahNum || 1;
            }
        }

        function updateLoggerHelperTexts() {
            const selectedDay = document.getElementById('log-day').value;
            if (!selectedDay) return;

            const progress = state.progress[selectedDay];
            const schedule = calculateTargets();
            const dayTarget = schedule.find(r => r.dayId === selectedDay);

            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                document.getElementById(`check-${fId}`).checked = progress[fId];
                document.getElementById(`lbl-check-${fId}`).innerText = state.config.forts[fId].name;
                
                const container = document.getElementById(`container-check-${fId}`);
                const desc = document.getElementById(`desc-check-${fId}`);
                
                if (dayTarget.rawTargets[fId] > 0) {
                    container.classList.remove('hidden');
                    desc.innerHTML = dayTarget[`${fId}Text`];
                } else {
                    container.classList.add('hidden');
                }
            });
        }

        function handleLogSubmit(e) {
            e.preventDefault();
            const selectedDay = document.getElementById('log-day').value;
            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                state.progress[selectedDay][fId] = document.getElementById(`check-${fId}`).checked;
            });
            saveData();
            updateDashboard();
            showNotification("تحديث الإنجاز", `تم حفظ تقدم الحصون ليوم ${getArabicDayName(selectedDay)} بنجاح.`);
        }

        document.getElementById('log-day').addEventListener('change', updateLoggerHelperTexts);

        function saveNotes() { saveData(); showNotification("تم الحفظ", "تم حفظ الملاحظات."); }
        function clearNotes() { document.getElementById('user-notes').value = ""; saveData(); showNotification("تحديث", "تم مسح الملاحظات."); }

        function resetAllProgress() {
            if (confirm("هل أنت متأكد من تصفير تقدم الحصون بالكامل لهذا الأسبوع؟")) {
                ["Saturday", "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday"].forEach(day => {
                    state.progress[day] = { f1: false, f2: false, f3: false, f4: false, f5: false };
                });
                saveData();
                updateDashboard();
                showNotification("تم التصفير", "تم البدء من جديد للأسبوع الحالي.");
            }
        }

        // ================= SETUP MODAL =================
        function openSetupModal() {
            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                const fort = state.config.forts[fId];
                document.getElementById(`setup-${fId}-name`).value = fort.name;
                document.getElementById(`setup-${fId}-target`).value = fort.target;
                document.getElementById(`setup-${fId}-unit`).value = fort.unit;

                const sp = state.config.startPoints[fId];
                document.getElementById(`setup-${fId}-type`).value = sp.type;
                document.getElementById(`setup-${fId}-surah`).value = sp.surahNum;
                document.getElementById(`setup-${fId}-ayah`).value = sp.ayahNum;
                document.getElementById(`setup-${fId}-page`).value = sp.pageNum;
                document.getElementById(`setup-${fId}-quarter`).value = sp.quarterIdx;
                document.getElementById(`setup-${fId}-hizb`).value = sp.hizbIdx;
                document.getElementById(`setup-${fId}-juz`).value = sp.juzNum;
                
                toggleFType(fId);
            });

            document.getElementById('setup-start-date').value = state.config.startDateString;
            ['Saturday', 'Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'].forEach(day => {
                document.getElementById(`d-${day.substring(0,3)}`).checked = state.config.activeDays[day];
            });

            document.getElementById('setup-modal').classList.remove('hidden');
        }

        function closeSetupModal() { document.getElementById('setup-modal').classList.add('hidden'); }

        function saveConfiguration() {
            ['f1', 'f2', 'f3', 'f4', 'f5'].forEach(fId => {
                state.config.forts[fId].name = document.getElementById(`setup-${fId}-name`).value || `الحصن ${fId}`;
                state.config.forts[fId].target = parseFloat(document.getElementById(`setup-${fId}-target`).value) || 1;
                state.config.forts[fId].unit = document.getElementById(`setup-${fId}-unit`).value;

                const sp = state.config.startPoints[fId];
                sp.type = document.getElementById(`setup-${fId}-type`).value;
                sp.surahNum = parseInt(document.getElementById(`setup-${fId}-surah`).value) || 1;
                sp.ayahNum = parseInt(document.getElementById(`setup-${fId}-ayah`).value) || 1;
                sp.pageNum = parseInt(document.getElementById(`setup-${fId}-page`).value) || 1;
                sp.quarterIdx = parseInt(document.getElementById(`setup-${fId}-quarter`).value) || 0;
                sp.hizbIdx = parseInt(document.getElementById(`setup-${fId}-hizb`).value) || 0;
                sp.juzNum = parseInt(document.getElementById(`setup-${fId}-juz`).value) || 1;
            });

            state.config.startDateString = document.getElementById('setup-start-date').value || "2026-06-13";

            ['Saturday', 'Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'].forEach(day => {
                state.config.activeDays[day] = document.getElementById(`d-${day.substring(0,3)}`).checked;
            });

            saveData();
            updateDashboard();
            closeSetupModal();
            showNotification("تم الحفظ", "تم تحديث خطة الحصون الخمسة ومواضع الانطلاق بنجاح.");
        }

        // ================= AUDIO PLAYER & AI =================
        function playAyahAudio() {
            const reciter = document.getElementById('audio-reciter').value;
            const surah = document.getElementById('audio-surah').value;
            const ayah = document.getElementById('audio-ayah').value;
            const btnIcon = document.getElementById('audio-btn-icon');
            const btnText = document.getElementById('audio-btn-text');
            const audioPlayer = document.getElementById('quran-audio');
            
            btnText.innerText = "جاري التحميل...";
            btnIcon.innerHTML = `<i class="fa-solid fa-spinner animate-spin"></i>`;
            
            fetch(`https://api.alquran.cloud/v1/ayah/${surah}:${ayah}/${reciter}`)
                .then(res => res.json())
                .then(data => {
                    if (data && data.data && data.data.audio) {
                        audioPlayer.src = data.data.audio;
                        audioPlayer.play();
                        btnText.innerText = "التلاوة قيد التشغيل";
                        btnIcon.innerHTML = `<i class="fa-solid fa-circle-pause"></i>`;
                        audioPlayer.onended = () => { resetAudioBtn(); };
                    } else {
                        showNotification("خطأ", "لم يتم العثور على الآية، الرجاء التحقق من المدخلات.");
                        resetAudioBtn();
                    }
                })
                .catch(err => {
                    showNotification("تعذر الاتصال", "تأكد من اتصالك بالإنترنت.");
                    resetAudioBtn();
                });
        }

        function resetAudioBtn() {
            document.getElementById('audio-btn-text').innerText = "استمع وتأكد من الآية";
            document.getElementById('audio-btn-icon').innerHTML = `<i class="fa-solid fa-play"></i>`;
        }

        async function callGeminiAPI(prompt, systemInstruction) {
            const apiKey = ""; 
            const payload = {
                contents: [{ parts: [{ text: prompt }] }],
                systemInstruction: { parts: [{ text: systemInstruction }] }
            };

            let delay = 1000;
            for (let i = 0; i < 5; i++) {
                try {
                    const actualUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
                    const response = await fetch(actualUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                    if (response.ok) {
                        const data = await response.json();
                        return data.candidates?.[0]?.content?.parts?.[0]?.text;
                    }
                } catch (error) {}
                await new Promise(resolve => setTimeout(resolve, delay));
                delay *= 2;
            }
            throw new Error("فشل الاتصال بالمساعد الذكي.");
        }

        function showAIWorkingState() {
            document.getElementById('ai-output-panel').classList.remove('hidden');
            document.getElementById('ai-output-content').innerHTML = `
                <div class="flex flex-col items-center justify-center py-6 text-emerald-300">
                    <i class="fa-solid fa-spinner animate-spin text-2xl mb-2"></i>
                    <span class="text-xs">المساعد الذكي يعمل الآن ✨...</span>
                </div>`;
        }

        function formatMarkdownToHTML(text) {
            if (!text) return "";
            return text.replace(/\n/g, '<br>').replace(/\*\*(.*?)\*\*/g, '<strong class="text-amber-400 font-semibold">$1</strong>')
                .replace(/\*(.*?)\*/g, '<em class="text-amber-200">$1</em>')
                .replace(/- (.*?)(<br>|$)/g, '<div class="flex items-start gap-1.5 my-1 text-gray-200"><span class="text-amber-400">•</span><span>$1</span></div>');
        }

        function closeAIOutput() { document.getElementById('ai-output-panel').classList.add('hidden'); }

        async function generateAITafsir() {
            const surahSelect = document.getElementById('audio-surah');
            const surahName = surahSelect.options[surahSelect.selectedIndex].text;
            const ayah = document.getElementById('audio-ayah').value;
            document.getElementById('ai-output-title').innerText = `تفسير وتدبر [${surahName}: آية ${ayah}]`;
            showAIWorkingState();

            const sys = "أنت مفسر قرآن يبسط المعاني ويقدم خاطرة تدبرية تربط الألفاظ ببعضها لتيسير الحفظ في منصة الحصون الخمسة.";
            const prompt = `أحتاج تفسيراً مبسطاً للآية رقم ${ayah} من ${surahName} مع رابط معنوي وخاطرة عملية لتسهيل ربط وحفظ الآية الكريمة.`;
            try {
                const response = await callGeminiAPI(prompt, sys);
                document.getElementById('ai-output-content').innerHTML = formatMarkdownToHTML(response);
            } catch (error) { document.getElementById('ai-output-content').innerHTML = `<span class="text-rose-300 text-xs">${error.message}</span>`; }
        }

        async function generateAIMutashabihat() {
            const surahSelect = document.getElementById('audio-surah');
            const surahName = surahSelect.options[surahSelect.selectedIndex].text;
            const ayah = document.getElementById('audio-ayah').value;
            document.getElementById('ai-output-title').innerText = `متشابهات الآية [${surahName}: آية ${ayah}]`;
            showAIWorkingState();

            const sys = "أنت عالم بمتشابهات القرآن، تساعد الطلاب على تجنب اللبس اللفظي وتداخل السور والآيات المتشابهة.";
            const prompt = `الآية رقم ${ayah} من ${surahName}، اذكر المتشابهات اللفظية المرتبطة بها في كامل المصحف وكيف أضبط الفروق والروابط بينها بدقة؟`;
            try {
                const response = await callGeminiAPI(prompt, sys);
                document.getElementById('ai-output-content').innerHTML = formatMarkdownToHTML(response);
            } catch (error) { document.getElementById('ai-output-content').innerHTML = `<span class="text-rose-300 text-xs">${error.message}</span>`; }
        }

        async function generateAISurahTips() {
            const surahSelect = document.getElementById('audio-surah');
            const surahName = surahSelect.options[surahSelect.selectedIndex].text;
            document.getElementById('ai-output-title').innerText = `خطة ونقاط تثبيت ${surahName}`;
            showAIWorkingState();

            const sys = "أنت موجه حفظ قرآني خبير تعطي تقسيمات موضوعية وحيل بصرية وذهنية لتثبيت السور للأبد.";
            const prompt = `أعطني تقسيماً موضوعياً ذكياً وخطة متكاملة لتثبيت ${surahName} بصورة تمنع نسيانها وتسهل تسميعها.`;
            try {
                const response = await callGeminiAPI(prompt, sys);
                document.getElementById('ai-output-content').innerHTML = formatMarkdownToHTML(response);
            } catch (error) { document.getElementById('ai-output-content').innerHTML = `<span class="text-rose-300 text-xs">${error.message}</span>`; }
        }
    </script>
</body>
</html>
