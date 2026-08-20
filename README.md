<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>꿈나무 발명 펀딩소 🚀 - 어린이 크라우드 펀딩</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Jua&family=Noto+Sans+KR:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        brand: {
                            50: '#f0fdf4',
                            100: '#dcfce7',
                            400: '#4ade80',
                            500: '#22c55e',
                            600: '#16a34a',
                            700: '#15803d',
                        },
                        kidYellow: '#FFD166',
                        kidPink: '#FF6B6B',
                        kidBlue: '#4ECDC4',
                        kidPurple: '#A06CD5'
                    },
                    fontFamily: {
                        jua: ['Jua', 'sans-serif'],
                        sans: ['Noto Sans KR', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #f8fafc;
        }
        .font-jua {
            font-family: 'Jua', sans-serif;
        }
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f5f9;
            border-radius: 8px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 8px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="text-slate-800 bg-slate-50 min-h-screen flex flex-col selection:bg-brand-100 selection:text-brand-700">

    <!-- Navigation Bar -->
    <nav class="sticky top-0 z-30 bg-white/90 backdrop-blur-md border-b border-slate-200 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center gap-3 cursor-pointer" onclick="filterCategory('ALL')">
                <div class="w-12 h-12 bg-gradient-to-tr from-emerald-400 to-teal-500 rounded-2xl flex items-center justify-center text-white text-2xl shadow-lg shadow-emerald-200 transform -rotate-3 hover:rotate-0 transition-transform">
                    💡
                </div>
                <div>
                    <h1 class="font-jua text-2xl md:text-3xl text-slate-800 tracking-wide flex items-center gap-2">
                        꿈나무 발명 펀딩소
                        <span class="text-xs font-sans font-semibold bg-emerald-100 text-emerald-800 px-2 py-0.5 rounded-full border border-emerald-300">실시간 클래스</span>
                    </h1>
                    <p class="text-xs text-slate-500 hidden sm:block">세상을 바꾸는 상상력! 우수 발명품에 투자하세요.</p>
                </div>
            </div>

            <!-- User Info & Action Buttons -->
            <div class="flex items-center gap-3">
                <button onclick="openRankingModal()" class="flex items-center gap-1.5 bg-amber-400 hover:bg-amber-500 text-amber-950 font-jua text-sm sm:text-base px-3.5 py-2.5 rounded-2xl shadow-md transition-all">
                    <i class="fa-solid fa-trophy text-amber-800"></i>
                    <span>🏆 펀딩 순위</span>
                </button>

                <button onclick="openCreateModal()" class="hidden md:flex items-center gap-2 bg-gradient-to-r from-emerald-500 to-teal-600 hover:from-emerald-600 hover:to-teal-700 text-white font-jua text-lg px-5 py-2.5 rounded-2xl shadow-md hover:shadow-lg transition-all transform hover:-translate-y-0.5">
                    <i class="fa-solid fa-wand-magic-sparkles"></i>
                    발명품 등록하기
                </button>

                <button onclick="openAdminAuthModal()" class="flex items-center gap-1.5 bg-slate-800 hover:bg-slate-900 text-white font-jua text-sm px-3.5 py-2.5 rounded-2xl shadow-md transition-all">
                    <i class="fa-solid fa-user-shield text-amber-400"></i>
                    <span>관리자</span>
                </button>

                <div id="userInfoHeader" class="flex items-center gap-3 bg-slate-100 p-1.5 pl-3 rounded-2xl border border-slate-200">
                    <!-- User Status dynamically rendered -->
                </div>
            </div>
        </div>
    </nav>

    <!-- Mobile Floating Action Button -->
    <button onclick="openCreateModal()" class="md:hidden fixed bottom-6 right-6 z-40 bg-emerald-500 text-white w-14 h-14 rounded-full shadow-2xl flex items-center justify-center text-2xl active:scale-95 transition-transform border-2 border-white">
        <i class="fa-solid fa-plus"></i>
    </button>

    <!-- Main Content Container -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-6">
        
        <!-- Hero Banner -->
        <div class="relative overflow-hidden rounded-3xl bg-gradient-to-r from-teal-500 via-emerald-500 to-amber-400 p-6 md:p-10 text-white shadow-xl mb-8">
            <div class="absolute -right-10 -bottom-10 w-64 h-64 bg-white/10 rounded-full blur-2xl pointer-events-none"></div>
            <div class="relative z-10 max-w-2xl">
                <span class="inline-block bg-white/20 backdrop-blur-md text-white font-semibold text-xs px-3 py-1 rounded-full mb-3 border border-white/30">
                    🌱 미래를 만드는 어린 발명가들의 공간
                </span>
                <h2 class="font-jua text-3xl md:text-5xl leading-tight mb-3 drop-shadow-sm">
                    내가 만든 신기한 발명품,<br/>친구들의 펀딩으로 진짜가 되어요!
                </h2>
                <p class="text-emerald-50 text-sm md:text-base mb-6 opacity-95">
                    불편했던 일상을 바꿀 기발한 아이디어가 있나요? 내 그림을 올려 친구들과 함께 싹싹포인트를 나누어 보아요!
                </p>
                <div class="flex flex-wrap gap-3">
                    <button onclick="openCreateModal()" class="bg-white text-emerald-700 font-jua text-lg px-6 py-2.5 rounded-xl hover:bg-emerald-50 shadow-md transition-all">
                        🚀 내 아이디어 올려보기
                    </button>
                    <button onclick="scrollToGrid()" class="bg-emerald-700/40 hover:bg-emerald-700/60 backdrop-blur-md text-white font-jua text-lg px-6 py-2.5 rounded-xl border border-white/20 transition-all">
                        👀 발명품 둘러보기
                    </button>
                </div>
            </div>
        </div>

        <!-- Filter & Search Section -->
        <div id="inventionGridAnchor" class="mb-8">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 bg-white p-4 rounded-2xl shadow-sm border border-slate-200/80">
                
                <!-- Category Buttons -->
                <div class="flex items-center gap-2 overflow-x-auto custom-scrollbar pb-2 md:pb-0">
                    <button onclick="filterCategory('ALL')" class="category-btn active border px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all bg-emerald-50 border-emerald-500 text-emerald-700 font-bold" data-cat="ALL">
                        🌈 전체 보기
                    </button>
                    <button onclick="filterCategory('환경/지구')" class="category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all" data-cat="환경/지구">
                        🌍 환경/지구
                    </button>
                    <button onclick="filterCategory('학교생활')" class="category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all" data-cat="학교생활">
                        🏫 학교생활
                    </button>
                    <button onclick="filterCategory('편리도구')" class="category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all" data-cat="편리도구">
                        💡 편리도구
                    </button>
                    <button onclick="filterCategory('로봇/IT')" class="category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all" data-cat="로봇/IT">
                        🤖 로봇/IT
                    </button>
                    <button onclick="filterCategory('재미/장난감')" class="category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all" data-cat="재미/장난감">
                        🎨 재미/장난감
                    </button>
                </div>

                <!-- Search Input & Sort Options -->
                <div class="flex items-center gap-3">
                    <div class="relative flex-grow md:w-64">
                        <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400"></i>
                        <input type="text" id="searchInput" oninput="handleSearch()" placeholder="발명품 또는 학생 이름 검색..." class="w-full pl-10 pr-4 py-2 text-sm bg-slate-50 border border-slate-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-emerald-400 transition-all">
                    </div>
                    <select id="sortSelect" onchange="renderProjects()" class="bg-slate-50 border border-slate-200 rounded-xl text-sm px-3 py-2 text-slate-700 font-medium focus:outline-none focus:ring-2 focus:ring-emerald-400">
                        <option value="newest">최신순</option>
                        <option value="popular">펀딩 달성높은순</option>
                        <option value="closing">목표 임박순</option>
                    </select>
                </div>
            </div>
        </div>

        <!-- Project Cards Grid -->
        <div id="projectsGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
            <!-- Dynamic Injection -->
        </div>

        <!-- Empty State -->
        <div id="emptyState" class="hidden text-center py-16 bg-white rounded-3xl border border-dashed border-slate-300 my-8">
            <div class="w-20 h-20 bg-slate-100 rounded-full flex items-center justify-center text-4xl mx-auto mb-4 text-slate-400">
                🔍
            </div>
            <h3 class="font-jua text-2xl text-slate-700 mb-2">등록된 발명품이 아직 없어요!</h3>
            <p class="text-slate-500 text-sm mb-6">첫 번째 아이디어 발명품을 직접 올려보는 건 어떨까요?</p>
            <button onclick="openCreateModal()" class="bg-emerald-500 hover:bg-emerald-600 text-white font-jua px-6 py-2.5 rounded-xl shadow-md transition-all">
                ✨ 내 발명품 등록하기
            </button>
        </div>
    </main>

    <!-- Footer -->
    <footer class="bg-white border-t border-slate-200 py-8 mt-12">
        <div class="max-w-7xl mx-auto px-4 text-center">
            <div class="flex items-center justify-center gap-2 mb-2">
                <span class="text-2xl">🌱</span>
                <span class="font-jua text-xl text-slate-700">꿈나무 발명 펀딩소</span>
            </div>
            <p class="text-slate-500 text-xs sm:text-sm max-w-lg mx-auto mb-4">
                어린이들의 톡톡 튀는 아이디어를 키워주는 실시간 가상 크라우드 펀딩 플랫폼입니다.<br/>
                서로의 생각을 존중하고 응원하는 따뜻한 창의력 놀이터가 되겠습니다.
            </p>
            <p class="text-xs text-slate-400">© 2026 Dream Sprouts Inventors Lab. All rights reserved.</p>
        </div>
    </footer>

    <!-- MODALS -->
    
    <!-- 1. USER REGISTRATION MODAL -->
    <div id="userModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden">
        <div class="bg-white w-full max-w-md rounded-3xl p-6 sm:p-8 shadow-2xl border border-slate-100">
            <div class="text-center mb-6">
                <div class="w-16 h-16 bg-amber-100 text-amber-600 rounded-full flex items-center justify-center text-3xl mx-auto mb-3 shadow-inner">
                    👋
                </div>
                <h3 class="font-jua text-3xl text-slate-800">꿈나무 발명소 입장하기</h3>
                <p class="text-sm text-slate-500 mt-1">발명품을 등록하고 펀딩하려면 이름을 알려주세요!</p>
            </div>

            <form onsubmit="handleUserSubmit(event)" class="space-y-5">
                <div>
                    <label class="block text-xs font-bold text-slate-600 uppercase tracking-wider mb-2">학생 이름 (또는 닉네임)</label>
                    <input type="text" id="userNameInput" required placeholder="예: 은여울" class="w-full px-4 py-3 bg-slate-50 border border-slate-200 rounded-2xl focus:outline-none focus:ring-2 focus:ring-emerald-400 text-slate-800 font-medium">
                </div>

                <div class="bg-emerald-50 border border-emerald-200 rounded-2xl p-3.5 text-xs text-emerald-800 flex items-start gap-2.5">
                    <i class="fa-solid fa-gift text-emerald-600 text-lg mt-0.5"></i>
                    <div>
                        <span class="font-bold">입장 선물!</span> 발명품에 후원할 수 있는 <strong class="text-emerald-700">100,000 싹싹포인트(P)</strong>를 무료로 드려요.
                    </div>
                </div>

                <button type="submit" class="w-full bg-gradient-to-r from-emerald-500 to-teal-600 text-white font-jua text-xl py-3.5 rounded-2xl shadow-lg hover:shadow-emerald-200 hover:scale-[1.02] active:scale-95 transition-all">
                    시작하기 🎉
                </button>
            </form>
        </div>
    </div>

    <!-- 2. CREATE INVENTION MODAL -->
    <div id="createModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden overflow-y-auto">
        <div class="bg-white w-full max-w-2xl rounded-3xl p-6 sm:p-8 shadow-2xl border border-slate-100 my-8">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100 mb-6">
                <div class="flex items-center gap-3">
                    <span class="text-3xl">✨</span>
                    <div>
                        <h3 class="font-jua text-2xl text-slate-800">새 발명품 등록하기</h3>
                        <p class="text-xs text-slate-500">멋진 아이디어를 친구들에게 보여주세요!</p>
                    </div>
                </div>
                <button onclick="closeCreateModal()" class="w-10 h-10 rounded-full bg-slate-100 hover:bg-slate-200 text-slate-500 flex items-center justify-center transition-all">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <form onsubmit="handleInventionSubmit(event)" class="space-y-5">
                <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                    <div class="sm:col-span-2">
                        <label class="block text-xs font-bold text-slate-600 mb-1.5">발명품 이름 *</label>
                        <input type="text" id="invTitle" required placeholder="예: 비 오면 자동으로 접히는 스마트 우산" class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400">
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-600 mb-1.5">카테고리 *</label>
                        <select id="invCategory" required class="w-full px-3 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400">
                            <option value="환경/지구">🌍 환경/지구</option>
                            <option value="학교생활">🏫 학교생활</option>
                            <option value="편리도구">💡 편리도구</option>
                            <option value="로봇/IT">🤖 로봇/IT</option>
                            <option value="재미/장난감">🎨 재미/장난감</option>
                        </select>
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-bold text-slate-600 mb-1.5">이 발명품이 해결하는 문제와 설명 *</label>
                    <textarea id="invDescription" required rows="3" placeholder="어떤 점이 불편해서 이 발명품을 만들게 되었나요? 어떻게 동작하는지 설명해보세요." class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400 resize-none"></textarea>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-bold text-slate-600 mb-1.5">목표 펀딩 금액 (싹싹포인트) *</label>
                        <div class="relative">
                            <input type="number" id="invGoal" min="10000" step="5000" value="50000" required class="w-full pl-4 pr-10 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400 font-bold text-emerald-700">
                            <span class="absolute right-3 top-1/2 -translate-y-1/2 text-xs font-bold text-slate-400">P</span>
                        </div>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-600 mb-1.5">펀딩 성공 시 보상(리워드/약속)</label>
                        <input type="text" id="invReward" placeholder="예: 시제품 만들기 과정 영상 공개!" class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400">
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-bold text-slate-600 mb-1.5">발명품 그림/사진 업로드 *</label>
                    <input type="file" id="invImgFile" accept="image/*" onchange="handleImagePreview(event)" required class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-400 file:mr-4 file:py-1.5 file:px-3 file:rounded-lg file:border-0 file:text-xs file:font-bold file:bg-emerald-100 file:text-emerald-700 hover:file:bg-emerald-200 cursor-pointer">
                    <p class="text-xs text-slate-400 mt-1">내 컴퓨터나 스마트폰에서 발명품 이미지 파일을 직접 업로드해 주세요.</p>
                    
                    <div id="imgPreviewContainer" class="mt-3 hidden">
                        <p class="text-xs font-bold text-slate-500 mb-1">📷 이미지 미리보기:</p>
                        <img id="imgPreview" class="w-full h-48 object-cover rounded-2xl border border-slate-200 shadow-sm">
                    </div>
                </div>

                <div class="pt-2">
                    <button type="submit" id="submitInventionBtn" class="w-full bg-gradient-to-r from-emerald-500 to-teal-600 text-white font-jua text-xl py-3.5 rounded-2xl shadow-lg hover:shadow-emerald-200 transition-all">
                        🚀 펀딩 신청하고 공유하기
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- 3. PROJECT DETAIL & FUNDING MODAL -->
    <div id="detailModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden overflow-y-auto">
        <div class="bg-white w-full max-w-3xl rounded-3xl overflow-hidden shadow-2xl border border-slate-100 my-8">
            <div id="detailContent">
                <!-- Dynamically Rendered -->
            </div>
        </div>
    </div>

    <!-- 4. ADMIN AUTH MODAL -->
    <div id="adminAuthModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden">
        <div class="bg-white w-full max-w-sm rounded-3xl p-6 shadow-2xl border border-slate-100 text-center">
            <div class="w-14 h-14 bg-slate-100 text-slate-800 rounded-full flex items-center justify-center text-2xl mx-auto mb-3 shadow-inner">
                🔐
            </div>
            <h3 class="font-jua text-2xl text-slate-800 mb-1">관리자 인증</h3>
            <p class="text-xs text-slate-500 mb-4">비밀번호를 입력하세요. (기본: 0115)</p>
            
            <form onsubmit="verifyAdminPassword(event)" class="space-y-4">
                <input type="password" id="adminPasswordInput" placeholder="비밀번호 입력" required class="w-full px-4 py-2.5 bg-slate-50 border border-slate-200 rounded-xl text-center text-lg font-bold tracking-widest focus:outline-none focus:ring-2 focus:ring-slate-800">
                <div class="flex gap-2">
                    <button type="button" onclick="closeAdminAuthModal()" class="w-1/2 bg-slate-100 hover:bg-slate-200 text-slate-600 font-jua py-2.5 rounded-xl transition-all">
                        취소
                    </button>
                    <button type="submit" class="w-1/2 bg-slate-800 hover:bg-slate-900 text-white font-jua py-2.5 rounded-xl shadow-md transition-all">
                        로그인
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- 5. ADMIN DASHBOARD MODAL -->
    <div id="adminDashboardModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden overflow-y-auto">
        <div class="bg-white w-full max-w-4xl rounded-3xl p-6 sm:p-8 shadow-2xl border border-slate-100 my-8">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100 mb-6">
                <div class="flex items-center gap-3">
                    <span class="text-3xl">⚙️</span>
                    <div>
                        <h3 class="font-jua text-2xl text-slate-800">관리자 대시보드</h3>
                        <p class="text-xs text-slate-500">발명품 펀딩 목표 달성 여부를 공개 설정하고 관리합니다.</p>
                    </div>
                </div>
                <button onclick="closeAdminDashboardModal()" class="w-10 h-10 rounded-full bg-slate-100 hover:bg-slate-200 text-slate-500 flex items-center justify-center transition-all">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <div class="flex flex-wrap items-center justify-between gap-3 mb-4 bg-slate-50 p-3.5 rounded-2xl border border-slate-200">
                <span class="text-xs font-bold text-slate-600">⚡ 일괄 처리 기능</span>
                <div class="flex items-center gap-2">
                    <button onclick="setAllPublishResults(true)" class="bg-emerald-600 hover:bg-emerald-700 text-white font-jua text-xs px-3.5 py-2 rounded-xl shadow-sm transition-all flex items-center gap-1.5">
                        <i class="fa-solid fa-bullhorn"></i> 전체 결과 공개하기
                    </button>
                    <button onclick="setAllPublishResults(false)" class="bg-slate-700 hover:bg-slate-800 text-white font-jua text-xs px-3.5 py-2 rounded-xl shadow-sm transition-all flex items-center gap-1.5">
                        <i class="fa-solid fa-lock"></i> 전체 결과 비공개하기
                    </button>
                </div>
            </div>

            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse text-sm">
                    <thead>
                        <tr class="bg-slate-50 border-b border-slate-200 text-slate-600 font-bold">
                            <th class="p-3.5 rounded-l-xl">발명품명</th>
                            <th class="p-3.5">작성자</th>
                            <th class="p-3.5">모인 포인트 / 목표</th>
                            <th class="p-3.5">현재 달성률</th>
                            <th class="p-3.5 text-center">결과 공개 상태</th>
                            <th class="p-3.5 rounded-r-xl text-center">설정</th>
                        </tr>
                    </thead>
                    <tbody id="adminProjectList" class="divide-y divide-slate-100">
                        <!-- Dynamic render -->
                    </tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- 6. RANKING MODAL -->
    <div id="rankingModal" class="fixed inset-0 z-50 flex items-center justify-center bg-slate-900/60 backdrop-blur-sm p-4 hidden overflow-y-auto">
        <div class="bg-white w-full max-w-2xl rounded-3xl p-6 sm:p-8 shadow-2xl border border-slate-100 my-8">
            <div class="flex items-center justify-between pb-4 border-b border-slate-100 mb-6">
                <div class="flex items-center gap-3">
                    <span class="text-3xl">🏆</span>
                    <div>
                        <h3 class="font-jua text-2xl text-slate-800">꿈나무 발명품 펀딩 순위</h3>
                        <p class="text-xs text-slate-500">관리자가 결과를 공개한 발명품들의 최종 펀딩 순위입니다.</p>
                    </div>
                </div>
                <button onclick="closeRankingModal()" class="w-10 h-10 rounded-full bg-slate-100 hover:bg-slate-200 text-slate-500 flex items-center justify-center transition-all">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <div id="rankingList" class="space-y-4 max-h-[60vh] overflow-y-auto pr-1 custom-scrollbar">
                <!-- Dynamic render -->
            </div>
        </div>
    </div>

    <!-- REAL-TIME CLOUD DATA SYNC SCRIPT -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, setDoc, updateDoc, onSnapshot, collection } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Firebase Configuration setup with fallbacks
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'kids-invent-class-app';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
            apiKey: "AIzaSyDemoKeyOnlyForDevelopment",
            authDomain: "demo-app.firebaseapp.com",
            projectId: "demo-app",
            storageBucket: "demo-app.appspot.com",
            messagingSenderId: "1234567890",
            appId: "1:1234567890:web:abcdef123456"
        };

        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        // App State
        let dbUser = null;
        let currentUser = null;
        let currentFilter = 'ALL';
        let searchQuery = '';
        let uploadedImageData = '';
        let currentDetailProject = null;
        let projects = [];
        const ADMIN_PASSWORD = "0115";

        // Expose global methods for UI onclick bindings
        window.openCreateModal = openCreateModal;
        window.closeCreateModal = closeCreateModal;
        window.openAdminAuthModal = openAdminAuthModal;
        window.closeAdminAuthModal = closeAdminAuthModal;
        window.openAdminDashboard = openAdminDashboard;
        window.closeAdminDashboardModal = closeAdminDashboardModal;
        window.openRankingModal = openRankingModal;
        window.closeRankingModal = closeRankingModal;
        window.filterCategory = filterCategory;
        window.handleSearch = handleSearch;
        window.scrollToGrid = scrollToGrid;
        window.verifyAdminPassword = verifyAdminPassword;
        window.togglePublishResult = togglePublishResult;
        window.setAllPublishResults = setAllPublishResults;
        window.handleImagePreview = handleImagePreview;
        window.handleInventionSubmit = handleInventionSubmit;
        window.handleUserSubmit = handleUserSubmit;
        window.openDetailModal = openDetailModal;
        window.closeDetailModal = closeDetailModal;
        window.fundProject = fundProject;
        window.openProfileModal = openProfileModal;
        window.renderProjects = renderProjects;

        // Sample Projects for fallback initialization
        const defaultSampleProjects = [
            {
                id: 'p_sample_1',
                title: '비 오는 날 우산 건조 가방',
                author: '김에디슨',
                isSample: true,
                category: '학교생활',
                description: '학교 도착해서 젖은 우산을 교실 바닥에 두면 축축해져요! 가방 옆에 흡수 타월과 팬이 달린 포켓을 만들어 뽀송하게 말려줍니다.',
                goal: 100000,
                raised: 75000,
                reward: '골판지 모형 샘플 제작 및 교실 테스트 영상 공유',
                imageUrl: 'https://images.unsplash.com/photo-1517479149777-5f3b6577d54c?w=600&q=80',
                backers: 12,
                createdAt: '2026-08-18',
                isResultPublished: false
            },
            {
                id: 'p_sample_2',
                title: '급식 잔반 제로 스마트 쟁반',
                author: '이아이디어',
                isSample: true,
                category: '환경/지구',
                description: '식판 밑에 센서가 들어있어서 음식물을 남기지 않고 다 먹으면 예쁜 스마일 불빛과 신나는 칭찬 음악이 나옵니다.',
                goal: 80000,
                raised: 80000,
                reward: '직접 그린 급식 잔반 줄이기 스티커 팩 선물',
                imageUrl: 'https://images.unsplash.com/photo-1581092160607-ee22621dd758?w=600&q=80',
                backers: 16,
                createdAt: '2026-08-15',
                isResultPublished: false
            }
        ];

        // 1. Authenticate user
        async function initAuth() {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (err) {
                console.warn("Auth initialization error, using local fallback mode:", err);
            }
            
            auth.onAuthStateChanged((user) => {
                dbUser = user;
                loadLocalUser();
                listenToCloudProjects();
            });
        }

        function loadLocalUser() {
            const savedUser = localStorage.getItem('kids_invent_user');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
            }
            renderHeader();
            if (!currentUser) {
                document.getElementById('userModal').classList.remove('hidden');
            }
        }

        function saveUser() {
            if (currentUser) {
                localStorage.setItem('kids_invent_user', JSON.stringify(currentUser));
            }
            renderHeader();
        }

        function listenToCloudProjects() {
            if (!dbUser) return;

            const projectsRef = collection(db, 'artifacts', appId, 'public', 'data', 'projects');

            onSnapshot(projectsRef, (snapshot) => {
                const cloudProjects = [];
                snapshot.forEach((doc) => {
                    cloudProjects.push(doc.data());
                });

                if (cloudProjects.length === 0) {
                    // Seed initial sample projects
                    defaultSampleProjects.forEach(async (p) => {
                        const pRef = doc(db, 'artifacts', appId, 'public', 'data', 'projects', p.id);
                        await setDoc(pRef, p);
                    });
                    projects = [...defaultSampleProjects];
                } else {
                    projects = cloudProjects;
                }

                renderProjects();
                
                if (currentDetailProject) {
                    const updatedDetail = projects.find(p => p.id === currentDetailProject.id);
                    if (updatedDetail) {
                        currentDetailProject = updatedDetail;
                        openDetailModal(updatedDetail.id, false);
                    }
                }

                const adminModal = document.getElementById('adminDashboardModal');
                if (!adminModal.classList.contains('hidden')) {
                    renderAdminProjectList();
                }
            }, (error) => {
                console.error("Cloud database synchronization error:", error);
                // Fallback to local array
                if (projects.length === 0) {
                    projects = [...defaultSampleProjects];
                    renderProjects();
                }
            });
        }

        function renderHeader() {
            const headerContainer = document.getElementById('userInfoHeader');
            if (currentUser) {
                headerContainer.innerHTML = `
                    <div class="flex items-center gap-2 cursor-pointer" onclick="openProfileModal()">
                        <div class="w-8 h-8 rounded-full bg-emerald-500 text-white flex items-center justify-center font-bold text-xs shadow-sm">
                            ${currentUser.name.substring(0, 1)}
                        </div>
                        <div class="text-left">
                            <div class="text-xs font-bold text-slate-800">${currentUser.name}</div>
                            <div class="text-[11px] font-bold text-emerald-600 flex items-center gap-1">
                                <i class="fa-solid fa-coins text-amber-500"></i> ${currentUser.points.toLocaleString()} P
                            </div>
                        </div>
                    </div>
                `;
            } else {
                headerContainer.innerHTML = `
                    <button onclick="document.getElementById('userModal').classList.remove('hidden')" class="text-xs font-jua text-emerald-600 bg-emerald-50 px-3 py-1.5 rounded-xl border border-emerald-200">
                        🔑 학생 등록하기
                    </button>
                `;
            }
        }

        function openProfileModal() {
            if (!currentUser) return;
            currentUser.points += 20000;
            saveUser();
            showToast('🎁 보너스 출석 선물로 20,000P를 더 받았어요!');
        }

        function handleUserSubmit(e) {
            e.preventDefault();
            const nameInput = document.getElementById('userNameInput').value.trim();
            if (!nameInput) return;

            currentUser = {
                id: 'user_' + Date.now(),
                name: nameInput,
                points: 100000,
                backedList: []
            };

            saveUser();
            document.getElementById('userModal').classList.add('hidden');
            showToast(`반가워요, ${currentUser.name} 학생! 100,000 포인트가 지급되었습니다! 🎉`);
        }

        function filterCategory(cat) {
            currentFilter = cat;
            document.querySelectorAll('.category-btn').forEach(btn => {
                if (btn.dataset.cat === cat) {
                    btn.className = "category-btn active border px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all bg-emerald-50 border-emerald-500 text-emerald-700 font-bold shadow-sm";
                } else {
                    btn.className = "category-btn border border-slate-200 text-slate-600 hover:bg-slate-50 px-4 py-2 rounded-xl text-sm font-medium whitespace-nowrap transition-all";
                }
            });
            renderProjects();
        }

        function handleSearch() {
            searchQuery = document.getElementById('searchInput').value.trim().toLowerCase();
            renderProjects();
        }

        function scrollToGrid() {
            document.getElementById('inventionGridAnchor').scrollIntoView({ behavior: 'smooth' });
        }

        function openAdminAuthModal() {
            document.getElementById('adminPasswordInput').value = '';
            document.getElementById('adminAuthModal').classList.remove('hidden');
        }

        function closeAdminAuthModal() {
            document.getElementById('adminAuthModal').classList.add('hidden');
        }

        function verifyAdminPassword(e) {
            e.preventDefault();
            const pw = document.getElementById('adminPasswordInput').value;
            if (pw === ADMIN_PASSWORD) {
                closeAdminAuthModal();
                openAdminDashboard();
                showToast('🔑 관리자로 로그인하였습니다.');
            } else {
                showToast('❌ 비밀번호가 올바르지 않습니다.');
            }
        }

        function openAdminDashboard() {
            renderAdminProjectList();
            document.getElementById('adminDashboardModal').classList.remove('hidden');
        }

        function closeAdminDashboardModal() {
            document.getElementById('adminDashboardModal').classList.add('hidden');
        }

        function openRankingModal() {
            const rankingList = document.getElementById('rankingList');
            const publishedProjects = projects.filter(p => p.isResultPublished && !p.isSample);

            if (publishedProjects.length === 0) {
                rankingList.innerHTML = `
                    <div class="text-center py-12 bg-slate-50 rounded-2xl border border-dashed border-slate-200">
                        <div class="text-4xl mb-3">⏳</div>
                        <h4 class="font-jua text-xl text-slate-700 mb-1">아직 공개된 펀딩 결과가 없어요!</h4>
                        <p class="text-xs text-slate-500">관리자 선생님이 펀딩 결과를 공개하면 이곳에서 순위를 확인할 수 있습니다.</p>
                    </div>
                `;
            } else {
                publishedProjects.sort((a, b) => b.raised - a.raised);

                rankingList.innerHTML = publishedProjects.map((p, index) => {
                    const rank = index + 1;
                    const percent = Math.min(100, Math.round((p.raised / p.goal) * 100));
                    const isSuccess = p.raised >= p.goal;

                    let rankBadge = '';
                    if (rank === 1) rankBadge = '<span class="text-2xl">🥇 1위</span>';
                    else if (rank === 2) rankBadge = '<span class="text-2xl">🥈 2위</span>';
                    else if (rank === 3) rankBadge = '<span class="text-2xl">🥉 3위</span>';
                    else rankBadge = `<span class="font-jua text-lg text-slate-500 px-2">${rank}위</span>`;

                    return `
                        <div class="flex items-center gap-4 p-4 bg-slate-50 hover:bg-emerald-50/50 rounded-2xl border border-slate-200/80 transition-all">
                            <div class="flex-shrink-0 w-16 text-center font-jua">
                                ${rankBadge}
                            </div>
                            <img src="${p.imageUrl}" class="w-16 h-16 rounded-xl object-cover border border-slate-200 flex-shrink-0">
                            <div class="flex-grow min-w-0">
                                <div class="flex items-center gap-2 mb-0.5">
                                    <span class="text-xs font-bold text-slate-500">👤 ${p.author}</span>
                                    <span class="text-xs bg-slate-200 text-slate-700 px-2 py-0.5 rounded-full">${p.category}</span>
                                </div>
                                <h4 class="font-jua text-lg text-slate-800 truncate">${p.title}</h4>
                                <div class="text-xs text-slate-500 flex items-center gap-3 mt-1">
                                    <span class="font-bold text-emerald-600">💰 ${p.raised.toLocaleString()} P</span>
                                    <span>🎯 목표: ${p.goal.toLocaleString()} P (${percent}%)</span>
                                </div>
                            </div>
                            <div class="flex-shrink-0 text-right">
                                ${isSuccess ? `
                                    <span class="bg-emerald-100 text-emerald-800 font-jua text-xs px-3 py-1.5 rounded-xl border border-emerald-300">
                                        🎉 목표 달성
                                    </span>
                                ` : `
                                    <span class="bg-slate-200 text-slate-600 font-jua text-xs px-3 py-1.5 rounded-xl">
                                        🎯 도전 완료
                                    </span>
                                `}
                            </div>
                        </div>
                    `;
                }).join('');
            }

            document.getElementById('rankingModal').classList.remove('hidden');
        }

        function closeRankingModal() {
            document.getElementById('rankingModal').classList.add('hidden');
        }

        async function togglePublishResult(id) {
            const project = projects.find(p => p.id === id);
            if (project) {
                const nextState = !project.isResultPublished;
                if (dbUser) {
                    const pRef = doc(db, 'artifacts', appId, 'public', 'data', 'projects', id);
                    await updateDoc(pRef, { isResultPublished: nextState });
                } else {
                    project.isResultPublished = nextState;
                    renderProjects();
                }
                showToast(nextState ? '📢 결과가 학생들에게 공개되었습니다.' : '🔒 결과가 비공개로 전환되었습니다.');
            }
        }

        async function setAllPublishResults(publishState) {
            const studentProjects = projects.filter(p => !p.isSample);
            if (studentProjects.length === 0) {
                showToast('💡 공개할 학생 발명품이 없습니다.');
                return;
            }

            for (const p of studentProjects) {
                if (dbUser) {
                    const pRef = doc(db, 'artifacts', appId, 'public', 'data', 'projects', p.id);
                    await updateDoc(pRef, { isResultPublished: publishState });
                } else {
                    p.isResultPublished = publishState;
                }
            }

            renderProjects();
            showToast(publishState ? '📢 모든 학생 발명품의 결과가 공개되었습니다!' : '🔒 모든 학생 발명품의 결과가 비공개로 변경되었습니다.');
        }

        function renderAdminProjectList() {
            const tbody = document.getElementById('adminProjectList');
            const studentProjects = projects.filter(p => !p.isSample);

            if (studentProjects.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="6" class="p-8 text-center text-slate-400 font-jua">
                            등록된 학생 발명품이 아직 없습니다.
                        </td>
                    </tr>
                `;
                return;
            }

            tbody.innerHTML = studentProjects.map(p => {
                const percent = Math.min(100, Math.round((p.raised / p.goal) * 100));
                const isSuccess = p.raised >= p.goal;
                return `
                    <tr class="hover:bg-slate-50 transition-colors">
                        <td class="p-3.5 font-bold text-slate-800">${p.title}</td>
                        <td class="p-3.5 text-slate-600">${p.author}</td>
                        <td class="p-3.5 font-semibold text-slate-700">${p.raised.toLocaleString()} / ${p.goal.toLocaleString()} P</td>
                        <td class="p-3.5 font-bold ${isSuccess ? 'text-emerald-600' : 'text-amber-600'}">${percent}% (${isSuccess ? '성공' : '진행중'})</td>
                        <td class="p-3.5 text-center">
                            ${p.isResultPublished ? `
                                <span class="bg-emerald-100 text-emerald-800 font-bold px-2.5 py-1 rounded-full text-xs">📢 공개됨</span>
                            ` : `
                                <span class="bg-slate-100 text-slate-600 font-bold px-2.5 py-1 rounded-full text-xs">🔒 비공개</span>
                            `}
                        </td>
                        <td class="p-3.5 text-center">
                            <button onclick="togglePublishResult('${p.id}')" class="px-3 py-1.5 rounded-xl font-jua text-xs text-white shadow-sm transition-all ${p.isResultPublished ? 'bg-slate-700 hover:bg-slate-800' : 'bg-emerald-500 hover:bg-emerald-600'}">
                                ${p.isResultPublished ? '비공개로 변경' : '목표 달성 여부 공개하기'}
                            </button>
                        </td>
                    </tr>
                `;
            }).join('');
        }

        function renderProjects() {
            const grid = document.getElementById('projectsGrid');
            const emptyState = document.getElementById('emptyState');
            const sortBy = document.getElementById('sortSelect').value;

            let filtered = projects.filter(p => {
                const matchCat = currentFilter === 'ALL' || p.category === currentFilter;
                const matchQuery = p.title.toLowerCase().includes(searchQuery) || 
                                   p.author.toLowerCase().includes(searchQuery) ||
                                   p.description.toLowerCase().includes(searchQuery);
                return matchCat && matchQuery;
            });

            if (sortBy === 'popular') {
                filtered.sort((a, b) => (b.raised / b.goal) - (a.raised / a.goal));
            } else if (sortBy === 'closing') {
                filtered.sort((a, b) => (a.goal - a.raised) - (b.goal - b.raised));
            } else {
                filtered.sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt));
            }

            if (filtered.length === 0) {
                grid.innerHTML = '';
                emptyState.classList.remove('hidden');
                return;
            } else {
                emptyState.classList.add('hidden');
            }

            grid.innerHTML = filtered.map(p => {
                const percent = Math.min(100, Math.round((p.raised / p.goal) * 100));
                const isFunded = p.raised >= p.goal;

                return `
                    <div class="bg-white rounded-3xl border border-slate-200/80 overflow-hidden shadow-sm hover:shadow-xl transition-all duration-300 flex flex-col group cursor-pointer" onclick="openDetailModal('${p.id}')">
                        <div class="relative h-48 bg-slate-100 overflow-hidden">
                            <img src="${p.imageUrl}" alt="${p.title}" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500" onerror="this.src='https://placehold.co/600x400/e2e8f0/475569?text=Invention+Sketch'">
                            <span class="absolute top-3 left-3 bg-white/90 backdrop-blur-md text-slate-700 text-xs font-bold px-3 py-1 rounded-full border border-slate-200 shadow-sm">
                                ${p.category}
                            </span>
                            ${p.isSample ? `
                                <span class="absolute top-3 right-3 bg-slate-800/80 text-white font-sans text-xs px-2.5 py-1 rounded-full backdrop-blur-md">
                                    💡 예시 게시물
                                </span>
                            ` : p.isResultPublished && isFunded ? `
                                <span class="absolute top-3 right-3 bg-amber-400 text-amber-950 font-jua text-xs px-3 py-1 rounded-full shadow-md animate-bounce">
                                    🎉 목표 달성 성공!
                                </span>
                            ` : p.isResultPublished && !isFunded ? `
                                <span class="absolute top-3 right-3 bg-slate-200 text-slate-700 font-jua text-xs px-3 py-1 rounded-full">
                                    🎯 아쉽게 미달성
                                </span>
                            ` : ''}
                        </div>

                        <div class="p-5 flex-grow flex flex-col justify-between">
                            <div>
                                <div class="flex items-center gap-2 mb-2 text-xs text-slate-500">
                                    <span>👤 ${p.author}</span>
                                </div>
                                <h3 class="font-jua text-xl text-slate-800 line-clamp-1 group-hover:text-emerald-600 transition-colors mb-2">
                                    ${p.title}
                                </h3>
                                <p class="text-xs text-slate-600 line-clamp-2 mb-4">
                                    ${p.description}
                                </p>
                            </div>

                            <div class="pt-2 border-t border-slate-100">
                                ${p.isResultPublished ? `
                                    <div class="flex justify-between items-end mb-1">
                                        <span class="font-jua text-lg text-emerald-600">${percent}% <span class="text-xs font-sans text-slate-400">달성</span></span>
                                        <span class="text-xs font-bold text-slate-700">${p.raised.toLocaleString()} / ${p.goal.toLocaleString()} P</span>
                                    </div>
                                    <div class="w-full bg-slate-100 h-2.5 rounded-full overflow-hidden mb-3">
                                        <div class="bg-gradient-to-r from-emerald-400 to-teal-500 h-full rounded-full transition-all duration-500" style="width: ${percent}%"></div>
                                    </div>
                                ` : `
                                    <div class="bg-slate-50 rounded-xl p-2.5 mb-3 border border-slate-100 text-center">
                                        <span class="text-xs font-jua text-slate-500 flex items-center justify-center gap-1.5">
                                            🔒 펀딩 진행 중 (달성 여부 공개 전)
                                        </span>
                                    </div>
                                `}
                                <div class="flex items-center justify-between text-xs text-slate-400">
                                    <span>🤝 ${p.backers || 0}명 후원참여</span>
                                    <span class="text-emerald-600 font-semibold group-hover:underline">자세히 보기 →</span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function handleImagePreview(e) {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(event) {
                uploadedImageData = event.target.result;
                const previewImg = document.getElementById('imgPreview');
                const previewContainer = document.getElementById('imgPreviewContainer');
                previewImg.src = uploadedImageData;
                previewContainer.classList.remove('hidden');
            };
            reader.readAsDataURL(file);
        }

        function openCreateModal() {
            if (!currentUser) {
                document.getElementById('userModal').classList.remove('hidden');
                return;
            }
            document.getElementById('createModal').classList.remove('hidden');
        }

        function closeCreateModal() {
            document.getElementById('createModal').classList.add('hidden');
        }

        async function handleInventionSubmit(e) {
            e.preventDefault();
            if (!currentUser) return;

            if (!uploadedImageData) {
                showToast('❌ 발명품 이미지 파일을 선택해 주세요!');
                return;
            }

            const btn = document.getElementById('submitInventionBtn');
            btn.disabled = true;
            btn.innerText = '등록 중... ⏳';

            const title = document.getElementById('invTitle').value.trim();
            const category = document.getElementById('invCategory').value;
            const description = document.getElementById('invDescription').value.trim();
            const goal = parseInt(document.getElementById('invGoal').value);
            const reward = document.getElementById('invReward').value.trim() || '응원해 준 모든 친구들에게 감사 카드 증정!';

            const newId = 'p_' + Date.now();
            const newProject = {
                id: newId,
                title,
                author: currentUser.name,
                isSample: false,
                category,
                description,
                goal,
                raised: 0,
                reward,
                imageUrl: uploadedImageData,
                backers: 0,
                createdAt: new Date().toISOString().split('T')[0],
                isResultPublished: false
            };

            if (dbUser) {
                const pRef = doc(db, 'artifacts', appId, 'public', 'data', 'projects', newId);
                await setDoc(pRef, newProject);
            } else {
                projects.unshift(newProject);
                renderProjects();
            }

            btn.disabled = false;
            btn.innerText = '🚀 펀딩 신청하고 공유하기';

            closeCreateModal();

            uploadedImageData = '';
            document.getElementById('imgPreviewContainer').classList.add('hidden');
            e.target.reset();

            confetti({
                particleCount: 80,
                spread: 70,
                origin: { y: 0.6 }
            });

            showToast('🎉 축하합니다! 새로운 발명품이 실시간으로 공유되었습니다.');
        }

        function openDetailModal(id, showAnimation = true) {
            const project = projects.find(p => p.id === id);
            if (!project) return;
            currentDetailProject = project;

            const percent = Math.min(100, Math.round((project.raised / project.goal) * 100));
            const isSuccess = project.raised >= project.goal;

            const modalContent = document.getElementById('detailContent');
            modalContent.innerHTML = `
                <div class="relative h-64 sm:h-80 bg-slate-900">
                    <img src="${project.imageUrl}" class="w-full h-full object-cover opacity-90">
                    <button onclick="closeDetailModal()" class="absolute top-4 right-4 w-10 h-10 rounded-full bg-black/50 text-white hover:bg-black/80 flex items-center justify-center transition-all">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                    <div class="absolute bottom-4 left-4 right-4 flex justify-between items-end">
                        <span class="bg-emerald-500 text-white text-xs font-bold px-3 py-1 rounded-full shadow-md">
                            ${project.category}
                        </span>
                        ${project.isSample ? `
                            <span class="bg-amber-400 text-slate-900 font-bold text-xs px-3 py-1 rounded-full shadow-md">
                                💡 체험용 예시 게시물
                            </span>
                        ` : ''}
                    </div>
                </div>

                <div class="p-6 sm:p-8 space-y-6">
                    <div>
                        <div class="flex items-center gap-2 text-sm text-slate-500 mb-2">
                            <span>👤 ${project.author}</span>
                            <span>•</span>
                            <span>등록일: ${project.createdAt}</span>
                        </div>
                        <h2 class="font-jua text-3xl text-slate-800 mb-3">${project.title}</h2>
                        <p class="text-slate-600 text-sm leading-relaxed bg-slate-50 p-4 rounded-2xl border border-slate-100">
                            ${project.description}
                        </p>
                    </div>

                    <div class="bg-emerald-50/60 border border-emerald-200/80 rounded-2xl p-5 space-y-3">
                        ${project.isResultPublished ? `
                            <div class="flex justify-between items-end">
                                <div>
                                    <span class="text-xs font-bold text-slate-500">모인 포인트</span>
                                    <div class="font-jua text-3xl text-emerald-700">${project.raised.toLocaleString()} <span class="text-base">P</span></div>
                                </div>
                                <div class="text-right">
                                    <span class="text-xs font-bold text-slate-500">목표 달성 상태</span>
                                    <div class="text-lg font-bold ${isSuccess ? 'text-emerald-600' : 'text-slate-600'}">
                                        ${isSuccess ? '🎉 목표 달성 성공!' : '🎯 아쉽게 미달성'} (${percent}%)
                                    </div>
                                </div>
                            </div>

                            <div class="w-full bg-emerald-200/60 h-3 rounded-full overflow-hidden">
                                <div class="bg-emerald-500 h-full rounded-full transition-all duration-500" style="width: ${percent}%"></div>
                            </div>
                        ` : `
                            <div class="text-center py-2 space-y-1">
                                <div class="font-jua text-xl text-slate-800">🌱 펀딩 참여 진행 중</div>
                                <p class="text-xs text-slate-500">목표 달성 여부 및 달성률은 관리자의 결과 발표 후 공개됩니다.</p>
                            </div>
                        `}

                        <div class="flex items-center justify-between text-xs text-slate-600 pt-1 border-t border-emerald-100">
                            <span>🤝 ${(project.backers || 0)}명의 친구가 응원중</span>
                            <span>🎁 약속 리워드: ${project.reward}</span>
                        </div>
                    </div>

                    <div class="space-y-3 pt-2">
                        <h4 class="font-jua text-lg text-slate-800">🌱 싹싹포인트로 이 발명품에 펀딩하기</h4>
                        
                        ${project.isSample ? `
                            <div class="bg-slate-100 border border-slate-200 rounded-2xl p-4 text-center">
                                <p class="text-sm font-bold text-slate-500 mb-1">🔒 예시 발명품은 펀딩 참여를 할 수 없습니다.</p>
                                <p class="text-xs text-slate-400">직접 만든 발명품이나 다른 친구들이 올린 실제 발명품에 펀딩해 보세요!</p>
                            </div>
                        ` : `
                            <div class="grid grid-cols-3 gap-3">
                                <button onclick="fundProject(1000)" class="py-3 px-2 bg-emerald-100 hover:bg-emerald-200 text-emerald-800 rounded-xl font-jua text-center transition-all border border-emerald-300">
                                    + 1,000 P
                                </button>
                                <button onclick="fundProject(5000)" class="py-3 px-2 bg-emerald-500 hover:bg-emerald-600 text-white rounded-xl font-jua text-center shadow-md transition-all">
                                    + 5,000 P
                                </button>
                                <button onclick="fundProject(10000)" class="py-3 px-2 bg-teal-600 hover:bg-teal-700 text-white rounded-xl font-jua text-center shadow-md transition-all">
                                    + 10,000 P
                                </button>
                            </div>
                        `}
                    </div>
                </div>
            `;

            if (showAnimation) {
                document.getElementById('detailModal').classList.remove('hidden');
            }
        }

        function closeDetailModal() {
            currentDetailProject = null;
            document.getElementById('detailModal').classList.add('hidden');
        }

        async function fundProject(amount) {
            if (!currentUser) {
                document.getElementById('userModal').classList.remove('hidden');
                return;
            }

            if (currentDetailProject && currentDetailProject.isSample) {
                showToast('🔒 예시 발명품은 체험용이므로 펀딩할 수 없습니다.');
                return;
            }

            if (currentUser.points < amount) {
                showToast('❌ 포인트가 부족합니다!');
                return;
            }

            currentUser.points -= amount;
            let addedBacker = false;
            if (!currentUser.backedList.includes(currentDetailProject.id)) {
                currentUser.backedList.push(currentDetailProject.id);
                addedBacker = true;
            }

            const newRaised = (currentDetailProject.raised || 0) + amount;
            const newBackers = (currentDetailProject.backers || 0) + (addedBacker ? 1 : 0);

            if (dbUser) {
                const pRef = doc(db, 'artifacts', appId, 'public', 'data', 'projects', currentDetailProject.id);
                await updateDoc(pRef, {
                    raised: newRaised,
                    backers: newBackers
                });
            } else {
                currentDetailProject.raised = newRaised;
                currentDetailProject.backers = newBackers;
            }

            saveUser();

            confetti({
                particleCount: 100,
                spread: 80,
                origin: { y: 0.5 }
            });

            showToast(`🌱 ${amount.toLocaleString()}P 후원 완료! 실시간 반영되었습니다.`);
        }

        function showToast(msg) {
            const toast = document.createElement('div');
            toast.className = 'fixed bottom-6 left-1/2 -translate-x-1/2 z-50 bg-slate-900/90 text-white font-jua text-sm px-6 py-3 rounded-2xl shadow-2xl backdrop-blur-md border border-slate-700 transition-all duration-300';
            toast.innerText = msg;
            document.body.appendChild(toast);

            setTimeout(() => {
                toast.classList.add('opacity-0');
                setTimeout(() => toast.remove(), 300);
            }, 2500);
        }

        // Start initialization on window load
        window.addEventListener('load', () => {
            initAuth();
        });
    </script>
</body>
</html>
