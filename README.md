<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Aice Freezer Inspection</title>
    <style>
        /* ===== RESET & VARIABLES ===== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        :root {
            --primary: #e31e24;
            --primary-dark: #c41a1f;
            --bg: #f8f9fa;
            --card: #ffffff;
            --text: #1e293b;
            --text-light: #64748b;
            --border: #e2e8f0;
            --success: #10b981;
            --warning: #f59e0b;
            --danger: #ef4444;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
        }

        body {
            background: var(--bg);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        .hidden {
            display: none !important;
        }

        /* ===== LOGIN PAGE ===== */
        .login-container {
            max-width: 400px;
            width: 100%;
            margin: 0 auto;
            background: var(--card);
            border-radius: 32px;
            padding: 32px 24px;
            box-shadow: var(--shadow);
            border: 1px solid var(--border);
        }

        .logo {
            text-align: center;
            margin-bottom: 32px;
        }

        .logo h1 {
            color: var(--primary);
            font-size: 64px;
            font-weight: 700;
            font-style: italic;
            line-height: 1;
            margin-bottom: 8px;
        }

        .brand-line {
            height: 2px;
            background: linear-gradient(90deg, transparent, var(--primary), transparent);
            width: 80px;
            margin: 16px auto;
        }

        .tagline {
            font-size: 20px;
            font-weight: 500;
            color: var(--text);
            white-space: nowrap;
            margin: 20px 0 28px;
        }

        .tagline span {
            color: var(--primary);
            font-weight: 700;
            font-style: italic;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            color: var(--text-light);
            font-size: 14px;
            font-weight: 500;
            margin-bottom: 6px;
        }

        .input-group input {
            width: 100%;
            padding: 16px 14px;
            border: 1.5px solid var(--border);
            border-radius: 16px;
            font-size: 16px;
            background: var(--bg);
        }

        .input-group input:focus {
            outline: none;
            border-color: var(--primary);
        }

        .remember {
            display: flex;
            align-items: center;
            gap: 8px;
            margin: 16px 0 24px;
        }

        .remember input {
            width: 18px;
            height: 18px;
            accent-color: var(--primary);
        }

        .login-btn {
            width: 100%;
            padding: 16px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 100px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        /* ===== MAIN CONTAINER ===== */
        .main-container {
            max-width: 500px;
            width: 100%;
            margin: 0 auto;
            background: var(--card);
            min-height: 100vh;
            position: relative;
        }

        .header {
            background: var(--primary);
            padding: 16px 20px;
            color: white;
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .top-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 8px;
        }

        .lang-switch {
            display: flex;
            gap: 4px;
            background: rgba(255, 255, 255, 0.15);
            padding: 4px;
            border-radius: 40px;
        }

        .lang-btn {
            padding: 6px 16px;
            border-radius: 40px;
            font-size: 13px;
            font-weight: 500;
            cursor: pointer;
            color: white;
        }

        .lang-btn.active {
            background: white;
            color: var(--primary);
            font-weight: 600;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .user-name {
            font-size: 15px;
            font-weight: 500;
            background: rgba(255, 255, 255, 0.15);
            padding: 6px 14px;
            border-radius: 40px;
        }

        .logout-btn {
            background: rgba(255, 255, 255, 0.15);
            padding: 6px 14px;
            border-radius: 40px;
            font-size: 13px;
            cursor: pointer;
        }

        .date {
            font-size: 13px;
            opacity: 0.9;
        }

        .nav-bar {
            display: flex;
            background: var(--card);
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 76px;
            z-index: 9;
            padding: 4px;
        }

        .nav-item {
            flex: 1;
            text-align: center;
            padding: 12px 8px;
            color: var(--text-light);
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
            border-radius: 30px;
        }

        .nav-item.active {
            color: var(--primary);
            background: rgba(227, 30, 36, 0.05);
            font-weight: 600;
        }

        .content {
            padding: 16px;
            padding-bottom: 80px;
        }

        .stats-card {
            background: var(--card);
            border-radius: 24px;
            padding: 20px;
            margin-bottom: 16px;
            border: 1px solid var(--border);
        }

        .stats-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--text);
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        .stat-item {
            background: var(--bg);
            border-radius: 16px;
            padding: 16px;
            text-align: center;
        }

        .stat-value {
            font-size: 32px;
            font-weight: 700;
            color: var(--primary);
        }

        .stat-label {
            font-size: 13px;
            color: var(--text-light);
            margin-top: 4px;
        }

        .progress-bar {
            height: 8px;
            background: var(--border);
            border-radius: 100px;
            overflow: hidden;
            margin: 8px 0;
        }

        .progress-fill {
            height: 100%;
            background: var(--primary);
            border-radius: 100px;
        }

        .freezer-id {
            font-weight: 600;
            color: var(--primary);
            background: rgba(227, 30, 36, 0.05);
            padding: 4px 12px;
            border-radius: 30px;
        }

        .task-list {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .task-item {
            background: var(--card);
            border: 1px solid var(--border);
            border-radius: 20px;
            padding: 16px;
        }

        .task-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 8px;
        }

        .shop-name {
            font-weight: 600;
            font-size: 15px;
        }

        .shop-details {
            color: var(--text-light);
            font-size: 13px;
            margin-bottom: 12px;
        }

        .task-footer {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 12px;
        }

        .photo-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px 20px;
            border-radius: 40px;
            font-size: 13px;
            font-weight: 500;
            cursor: pointer;
        }

        .photo-btn.completed {
            background: var(--success);
        }

        .photo-btn:disabled {
            background: var(--border);
            cursor: not-allowed;
        }

        .sync-textarea {
            width: 100%;
            height: 100px;
            padding: 12px;
            border: 1px solid var(--border);
            border-radius: 16px;
            margin: 10px 0;
        }

        .sync-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 30px;
            width: 100%;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        .freezer-tag {
            display: inline-block;
            background: var(--bg);
            padding: 4px 12px;
            border-radius: 30px;
            margin: 4px;
            font-size: 12px;
        }

        .brand-footer {
            text-align: center;
            padding: 16px;
            font-size: 12px;
            color: var(--text-light);
            border-top: 1px solid var(--border);
            background: var(--card);
            position: fixed;
            bottom: 0;
            width: 100%;
            max-width: 500px;
        }

        .brand-footer span {
            color: var(--primary);
            font-weight: 600;
        }

        /* ===== PHOTO MODAL ===== */
        #photoModal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(4px);
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 16px;
        }

        #photoModal > div {
            background: var(--card);
            width: 100%;
            max-width: 450px;
            border-radius: 32px;
            padding: 24px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-title {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary);
            margin-bottom: 20px;
            padding-bottom: 12px;
            border-bottom: 2px solid var(--primary);
        }

        .photo-preview {
            width: 100%;
            height: 200px;
            background: var(--bg);
            border-radius: 20px;
            margin: 12px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-light);
            overflow: hidden;
            border: 1px dashed var(--border);
        }

        .photo-preview img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .camera-btn {
            background: var(--text);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 30px;
            width: 100%;
            font-size: 15px;
            cursor: pointer;
            margin: 12px 0;
        }

        .remark-section {
            background: rgba(227, 30, 36, 0.03);
            border-radius: 20px;
            padding: 16px;
            margin: 16px 0;
        }

        .remark-select {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--border);
            border-radius: 16px;
            font-size: 14px;
            margin-bottom: 12px;
        }

        .remark-input {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--border);
            border-radius: 16px;
            font-size: 14px;
        }

        .upload-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 16px;
            border-radius: 30px;
            width: 100%;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-top: 16px;
        }

        .photo-thumb {
            width: 100%;
            max-height: 150px;
            object-fit: cover;
            border-radius: 12px;
            margin-top: 10px;
            cursor: pointer;
        }

        .fullscreen-modal {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: black;
            z-index: 2000;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .fullscreen-modal img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }

        @media (max-width: 380px) {
            .logo h1 { font-size: 52px; }
            .tagline { font-size: 18px; }
            .top-bar { flex-direction: column; align-items: flex-start; }
            .user-info { width: 100%; justify-content: space-between; }
            .stats-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>
    <div id="app">
        <!-- LOGIN PAGE -->
        <div id="loginPage" class="login-container">
            <div class="logo">
                <h1>Aice</h1>
                <div class="brand-line"></div>
                <div class="tagline" id="loginTagline">
                    HAVE AN <span>AICE</span> DAY
                </div>
            </div>
            
            <div class="input-group">
                <label id="usernameLabel">编号</label>
                <input type="text" id="username" placeholder="001-005" value="001">
            </div>
            
            <div class="input-group">
                <label id="passwordLabel">密码</label>
                <input type="password" id="password" placeholder="123456" value="123456">
            </div>
            
            <div class="remember">
                <input type="checkbox" id="remember" checked>
                <label for="remember" id="rememberLabel">记住登录状态</label>
            </div>
            
            <button class="login-btn" onclick="handleLogin()" id="loginBtn">登录</button>
        </div>

        <!-- MAIN PAGE -->
        <div id="mainPage" class="main-container hidden">
            <div class="header">
                <div class="top-bar">
                    <div class="lang-switch">
                        <span class="lang-btn active" onclick="switchLanguage('zh')" id="langZhBtn">中文</span>
                        <span class="lang-btn" onclick="switchLanguage('en')" id="langEnBtn">English</span>
                    </div>
                    <div class="user-info">
                        <span class="user-name" id="displayName"></span>
                        <span class="logout-btn" onclick="logout()" id="logoutBtn">退出</span>
                    </div>
                </div>
                <div class="date" id="currentDate"></div>
            </div>

            <div class="nav-bar" id="navBar"></div>
            <div class="content" id="content"></div>
            
            <div class="brand-footer">
                <span>Aice</span> • Karachi
            </div>
        </div>

        <!-- PHOTO MODAL -->
        <div id="photoModal" class="hidden">
            <div>
                <div class="modal-title">
                    <span id="photoModalTitle">拍照上传</span> - <span id="modalFreezerId"></span>
                </div>
                
                <div>
                    <div style="font-weight: 600; margin-bottom: 10px;">
                        <span style="background: var(--primary); color: white; width: 26px; height: 26px; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; margin-right: 8px;">1</span>
                        <span id="step1Title">拍照</span>
                    </div>
                    <div id="camera-preview" class="photo-preview">相机预览区域</div>
                    <input type="file" id="camera-input" accept="image/*" capture="environment" style="display: none;">
                    <button class="camera-btn" onclick="openCamera()" id="openCameraBtn">打开相机</button>
                </div>
                
                <div class="remark-section">
                    <div style="font-weight: 600; margin-bottom: 12px;">
                        <span style="background: var(--primary); color: white; width: 26px; height: 26px; border-radius: 50%; display: inline-flex; align-items: center; justify-content: center; margin-right: 8px;">2</span>
                        <span id="step2Title">备注</span>
                    </div>
                    
                    <select class="remark-select" id="remarkType">
                        <option value="normal">冰柜正常</option>
                        <option value="unused">冰柜未使用</option>
                        <option value="dirty_inside">冰柜内部脏了</option>
                        <option value="other_ad">外部有其他广告</option>
                        <option value="temperature">温度异常</option>
                        <option value="damaged">冰柜损坏</option>
                        <option value="other">其他问题</option>
                    </select>
                    
                    <input type="text" class="remark-input" id="remarkDetail" placeholder="详细说明（选填，最多200字）" maxlength="200">
                    <div style="text-align: right; font-size: 12px; margin-top: 6px;">
                        <span id="charCount">0</span>/200
                    </div>
                </div>
                
                <button class="upload-btn" onclick="uploadPhoto()" id="uploadBtn">确认上传</button>
                <button style="background: var(--text-light); color: white; border: none; padding: 14px; border-radius: 30px; width: 100%; margin-top: 10px;" onclick="closePhotoModal()" id="cancelBtn">取消</button>
            </div>
        </div>

        <!-- FULLSCREEN IMAGE MODAL -->
        <div id="fullscreenModal" class="fullscreen-modal hidden" onclick="closeFullscreen()">
            <img id="fullscreenImage" src="">
        </div>
    </div>

    <script>
        // ===== CONFIG =====
        const CSV_URL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vRw6l0RVWFFp1KX7cJbWn9lZDHBNNWBV9Im8QEXxjRBoTKTEe5eFIMxtP8Bb8Y3WmOXEu2RIU6kAEVt/pub?output=csv';

        // ===== GLOBAL STATE =====
        let freezers = [];
        let currentUser = null;
        let currentFreezer = null;
        let currentLang = localStorage.getItem('language') || 'zh';
        let photos = JSON.parse(localStorage.getItem('photos')) || [];
        let todayTasks = { A: [], B: [], C: [] };

        // ===== USERS =====
        const users = {
            '001': { password: '123456', role: 'sales', region: 'A', name: '业务员001', nameEn: 'Sales 001' },
            '002': { password: '123456', role: 'sales', region: 'B', name: '业务员002', nameEn: 'Sales 002' },
            '003': { password: '123456', role: 'sales', region: 'C', name: '业务员003', nameEn: 'Sales 003' },
            '004': { password: '123456', role: 'office', name: '办公室', nameEn: 'Office' },
            '005': { password: '123456', role: 'boss', name: '老板', nameEn: 'Boss' }
        };

        // ===== TRANSLATIONS =====
        const translations = {
            zh: {
                usernameLabel: '编号', passwordLabel: '密码', rememberLabel: '记住登录状态',
                loginBtn: '登录', logoutBtn: '退出',
                step1Title: '拍照', step2Title: '备注', openCameraBtn: '打开相机',
                uploadBtn: '确认上传', cancelBtn: '取消', cameraPreview: '相机预览区域',
                photoModalTitle: '拍照上传',
                todayTasks: '今日任务', myRecords: '我的记录', progress: '进度',
                waiting: '待拍照', completed: '已完成', photo: '拍照',
                syncTasks: '同步任务', freezerSearch: '冰柜查询', regionStats: '区域统计', alerts: '预警',
                overview: '总览', regions: '区域详情', salesmen: '业务员',
                totalFreezers: '总冰柜', todayPhotos: '今日拍照',
                weekPhotos: '本周拍照', monthPhotos: '本月拍照',
                overdue: '超期未拍', warning: '即将超期',
                search: '搜索', sync: '解析并同步',
                remarkNormal: '冰柜正常', remarkUnused: '冰柜未使用',
                remarkDirtyInside: '冰柜内部脏了', remarkOtherAd: '外部有其他广告',
                remarkTemperature: '温度异常', remarkDamaged: '冰柜损坏',
                remarkOther: '其他问题', remarkDetailPlaceholder: '详细说明（选填，最多200字）',
                loginTagline: 'HAVE AN <span>AICE</span> DAY'
            },
            en: {
                usernameLabel: 'ID', passwordLabel: 'Password', rememberLabel: 'Remember me',
                loginBtn: 'LOGIN', logoutBtn: 'Logout',
                step1Title: 'Take Photo', step2Title: 'Remark', openCameraBtn: 'Open Camera',
                uploadBtn: 'Upload', cancelBtn: 'Cancel', cameraPreview: 'Camera Preview',
                photoModalTitle: 'Photo Upload',
                todayTasks: "Today's Tasks", myRecords: 'My Records', progress: 'Progress',
                waiting: 'Pending', completed: 'Completed', photo: 'Photo',
                syncTasks: 'Sync Tasks', freezerSearch: 'Search', regionStats: 'Region Stats', alerts: 'Alerts',
                overview: 'Overview', regions: 'Regions', salesmen: 'Salesmen',
                totalFreezers: 'Total', todayPhotos: 'Today',
                weekPhotos: 'Week', monthPhotos: 'Month',
                overdue: 'Overdue', warning: 'Warning',
                search: 'Search', sync: 'Sync',
                remarkNormal: '✅ Freezer Normal', remarkUnused: '⭕ Not in Use',
                remarkDirtyInside: '🧹 Inside Dirty', remarkOtherAd: '📢 Other Ads',
                remarkTemperature: '🌡️ Temperature', remarkDamaged: '🔧 Damaged',
                remarkOther: '❓ Other', remarkDetailPlaceholder: 'Details (max 200 chars)',
                loginTagline: 'HAVE AN <span>AICE</span> DAY'
            }
        };

        // ===== UTILS =====
        function getRegion(salesPerson) {
            const map = { '1': 'A', '2': 'B', '3': 'C' };
            return map[salesPerson?.trim()] || 'A';
        }

        function getRemarkText(type, lang) {
            const t = translations[lang];
            const map = {
                'normal': t.remarkNormal,
                'unused': t.remarkUnused,
                'dirty_inside': t.remarkDirtyInside,
                'other_ad': t.remarkOtherAd,
                'temperature': t.remarkTemperature,
                'damaged': t.remarkDamaged,
                'other': t.remarkOther
            };
            return map[type] || t.remarkNormal;
        }

        // ===== LOAD FREEZERS =====
        async function loadFreezersFromSheet() {
            try {
                const res = await fetch(CSV_URL);
                const csv = await res.text();
                const lines = csv.split('\n').slice(2).filter(l => l.includes('FZ-'));
                
                freezers = lines.map(line => {
                    const v = line.split(',');
                    return {
                        id: v[0]?.trim(),
                        region: getRegion(v[1]),
                        shop: v[2]?.trim(),
                        owner: v[3]?.trim(),
                        phone: v[4]?.trim(),
                        status: v[5]?.trim() || 'active'
                    };
                }).filter(f => f.id);
                
                console.log(`✅ Loaded ${freezers.length} freezers`);
            } catch (e) {
                console.log('Using default data');
                freezers = [
                    { id: 'FZ-A00006', region: 'A', shop: 'V.S.P STORE', owner: 'Yasmeen', phone: '0315-7022729' },
                    { id: 'FZ-A00009', region: 'A', shop: 'AL-SADDAT', owner: 'AHMED', phone: '0321-2899218' },
                    { id: 'FZ-A00012', region: 'A', shop: 'D.MART', owner: 'Rizwan', phone: '0323-3337441' },
                    { id: 'FZ-A00101', region: 'B', shop: 'Bazaar Store', owner: 'Ali', phone: '0300-1111111' },
                    { id: 'FZ-A00102', region: 'B', shop: 'Corner Mart', owner: 'Ahmed', phone: '0300-2222222' },
                    { id: 'FZ-A00201', region: 'C', shop: 'Market Shop', owner: 'Sara', phone: '0300-6666666' }
                ];
            }
        }

        // ===== LANGUAGE =====
        function updateUILanguage() {
            const t = translations[currentLang];
            
            const elements = [
                'usernameLabel', 'passwordLabel', 'rememberLabel', 'loginBtn',
                'logoutBtn', 'step1Title', 'step2Title', 'openCameraBtn',
                'uploadBtn', 'cancelBtn', 'photoModalTitle'
            ];
            
            elements.forEach(id => {
                const el = document.getElementById(id);
                if (el) el.textContent = t[id];
            });
            
            const tagline = document.getElementById('loginTagline');
            if (tagline) tagline.innerHTML = t.loginTagline;
            
            const preview = document.getElementById('camera-preview');
            if (preview && !preview.querySelector('img')) {
                preview.textContent = t.cameraPreview;
            }
            
            const select = document.getElementById('remarkType');
            if (select) {
                select.options[0].text = t.remarkNormal;
                select.options[1].text = t.remarkUnused;
                select.options[2].text = t.remarkDirtyInside;
                select.options[3].text = t.remarkOtherAd;
                select.options[4].text = t.remarkTemperature;
                select.options[5].text = t.remarkDamaged;
                select.options[6].text = t.remarkOther;
            }
            
            const detail = document.getElementById('remarkDetail');
            if (detail) detail.placeholder = t.remarkDetailPlaceholder;
        }

        window.switchLanguage = function(lang) {
            currentLang = lang;
            localStorage.setItem('language', lang);
            
            document.getElementById('langZhBtn').classList.toggle('active', lang === 'zh');
            document.getElementById('langEnBtn').classList.toggle('active', lang === 'en');
            
            updateUILanguage();
            
            if (currentUser) {
                document.getElementById('displayName').textContent = lang === 'zh' ? currentUser.name : currentUser.nameEn;
                if (currentUser.role === 'sales') showSalesView();
                else if (currentUser.role === 'office') showOfficeView();
                else showBossView();
            }
        };

        // ===== LOGIN =====
        window.handleLogin = function() {
            const uid = document.getElementById('username').value;
            const pwd = document.getElementById('password').value;
            const rem = document.getElementById('remember').checked;
            
            if (users[uid] && users[uid].password === pwd) {
                currentUser = { username: uid, ...users[uid] };
                if (rem) localStorage.setItem('aice_user', JSON.stringify(currentUser));
                
                document.getElementById('loginPage').classList.add('hidden');
                document.getElementById('mainPage').classList.remove('hidden');
                document.getElementById('displayName').textContent = currentLang === 'zh' ? currentUser.name : currentUser.nameEn;
                
                const d = new Date();
                document.getElementById('currentDate').textContent = `${d.getFullYear()}年${d.getMonth()+1}月${d.getDate()}日`;
                
                if (currentUser.role === 'sales') showSalesView();
                else if (currentUser.role === 'office') showOfficeView();
                else showBossView();
                
                alert(`Welcome ${currentUser.name}`);
            } else {
                alert('Invalid credentials. Use 001-005 / 123456');
            }
        };

        window.logout = function() {
            localStorage.removeItem('aice_user');
            currentUser = null;
            document.getElementById('loginPage').classList.remove('hidden');
            document.getElementById('mainPage').classList.add('hidden');
        };

        // ===== PHOTO FUNCTIONS =====
        window.openPhotoModal = function(id) {
            currentFreezer = id;
            document.getElementById('modalFreezerId').textContent = id;
            document.getElementById('photoModal').classList.remove('hidden');
            document.getElementById('remarkDetail').value = '';
            document.getElementById('charCount').textContent = '0';
            document.getElementById('camera-preview').innerHTML = translations[currentLang].cameraPreview;
        };

        window.closePhotoModal = function() {
            document.getElementById('photoModal').classList.add('hidden');
            currentFreezer = null;
        };

        window.openCamera = function() {
            document.getElementById('camera-input').click();
        };

        document.getElementById('camera-input').addEventListener('change', function(e) {
            if (e.target.files.length) {
                const reader = new FileReader();
                reader.onload = e => {
                    document.getElementById('camera-preview').innerHTML = `<img src="${e.target.result}" style="width:100%;height:100%;object-fit:cover;">`;
                };
                reader.readAsDataURL(e.target.files[0]);
            }
        });

        window.uploadPhoto = function() {
            if (!currentFreezer) return;
            const img = document.getElementById('camera-preview').querySelector('img');
            if (!img) {
                alert(translations[currentLang].cameraPreview === '相机预览区域' ? '请先拍照' : 'Take a photo first');
                return;
            }
            
            const remarkType = document.getElementById('remarkType').value;
            const remarkDetail = document.getElementById('remarkDetail').value;
            
            const photo = {
                freezerId: currentFreezer,
                time: new Date().toISOString(),
                sales: currentUser.username,
                photo: img.src,
                remark: {
                    type: remarkType,
                    text: getRemarkText(remarkType, currentLang),
                    detail: remarkDetail
                }
            };
            
            photos.push(photo);
            localStorage.setItem('photos', JSON.stringify(photos));
            
            closePhotoModal();
            if (currentUser.role === 'sales') {
                showSalesTasks();
            }
        };

        window.viewFullscreen = function(src) {
            document.getElementById('fullscreenImage').src = src;
            document.getElementById('fullscreenModal').classList.remove('hidden');
        };

        window.closeFullscreen = function() {
            document.getElementById('fullscreenModal').classList.add('hidden');
        };

        document.getElementById('remarkDetail').addEventListener('input', e => {
            document.getElementById('charCount').textContent = e.target.value.length;
        });

        // ===== SALES VIEW =====
        window.showSalesView = function() {
            const t = translations[currentLang];
            document.getElementById('navBar').innerHTML = `
                <div class="nav-item active" onclick="switchSalesTab('tasks')">${t.todayTasks}</div>
                <div class="nav-item" onclick="switchSalesTab('history')">${t.myRecords}</div>
                <div class="nav-item" onclick="switchSalesTab('stats')">${t.progress}</div>
            `;
            showSalesTasks();
        };

        window.switchSalesTab = function(tab) {
            document.querySelectorAll('.nav-item').forEach(i => i.classList.remove('active'));
            event.target.classList.add('active');
            if (tab === 'tasks') showSalesTasks();
            else if (tab === 'history') showSalesHistory();
            else showSalesStats();
        };

        function showSalesTasks() {
            const t = translations[currentLang];
            const tasks = (todayTasks[currentUser.region] || []).map(id => freezers.find(f => f.id === id)).filter(f => f);
            
            let html = `
                <div class="stats-card">
                    <div class="stats-title">📋 ${t.todayTasks}</div>
                    <div class="stats-grid">
                        <div class="stat-item"><div class="stat-value">${tasks.length}</div><div class="stat-label">${t.totalFreezers}</div></div>
                        <div class="stat-item"><div class="stat-value">${tasks.filter(t => hasPhotoToday(t.id)).length}</div><div class="stat-label">${t.completed}</div></div>
                    </div>
                    <div class="progress-bar"><div class="progress-fill" style="width: ${tasks.length ? (tasks.filter(t => hasPhotoToday(t.id)).length / tasks.length * 100) : 0}%"></div></div>
                </div>
                <div class="task-list">
            `;
            
            tasks.forEach(task => {
                const photo = photos.find(p => p.freezerId === task.id && isToday(p.time));
                html += `
                    <div class="task-item">
                        <div class="task-header">
                            <span class="freezer-id">${task.id}</span>
                            <span class="shop-name">${task.shop}</span>
                        </div>
                        <div class="shop-details">${task.owner} | ${task.phone}</div>
                        ${photo && photo.remark ? `<div style="font-size:12px; color:var(--text-light); margin-bottom:8px;">📝 ${photo.remark.text}</div>` : ''}
                        <div class="task-footer">
                            <span class="time">${photo ? '✅' : '⏳'}</span>
                            <button class="photo-btn ${photo ? 'completed' : ''}" onclick="openPhotoModal('${task.id}')" ${photo ? 'disabled' : ''}>
                                ${photo ? t.completed : t.photo}
                            </button>
                        </div>
                    </div>
                `;
            });
            
            document.getElementById('content').innerHTML = html + '</div>';
        }

        function showSalesHistory() {
            const t = translations[currentLang];
            const myPhotos = photos.filter(p => p.sales === currentUser.username);
            if (!myPhotos.length) {
                document.getElementById('content').innerHTML = '<div class="stats-card">暂无记录</div>';
                return;
            }
            
            let html = '<div class="task-list">';
            myPhotos.sort((a, b) => new Date(b.time) - new Date(a.time)).forEach(p => {
                const f = freezers.find(f => f.id === p.freezerId);
                html += `
                    <div class="task-item">
                        <div class="task-header">
                            <span class="freezer-id">${p.freezerId}</span>
                            <span class="shop-name">${f ? f.shop : ''}</span>
                        </div>
                        <div class="time">${new Date(p.time).toLocaleString()}</div>
                        ${p.photo ? `<img src="${p.photo}" class="photo-thumb" onclick="viewFullscreen('${p.photo}')">` : ''}
                        ${p.remark ? `<div style="margin-top:8px;">📝 ${p.remark.text} ${p.remark.detail ? '- ' + p.remark.detail : ''}</div>` : ''}
                    </div>
                `;
            });
            document.getElementById('content').innerHTML = html + '</div>';
        }

        function showSalesStats() {
            const t = translations[currentLang];
            const myPhotos = photos.filter(p => p.sales === currentUser.username);
            const today = myPhotos.filter(p => isToday(p.time)).length;
            const week = myPhotos.filter(p => isThisWeek(p.time)).length;
            const month = myPhotos.filter(p => isThisMonth(p.time)).length;
            
            document.getElementById('content').innerHTML = `
                <div class="stats-card">
                    <div class="stats-title">📊 ${t.myRecords}</div>
                    <div class="stats-grid">
                        <div class="stat-item"><div class="stat-value">${today}</div><div class="stat-label">${t.todayPhotos}</div></div>
                        <div class="stat-item"><div class="stat-value">${week}</div><div class="stat-label">${t.weekPhotos}</div></div>
                        <div class="stat-item"><div class="stat-value">${month}</div><div class="stat-label">${t.monthPhotos}</div></div>
                    </div>
                </div>
            `;
        }

        // ===== OFFICE VIEW =====
        window.showOfficeView = function() {
            const t = translations[currentLang];
            document.getElementById('navBar').innerHTML = `
                <div class="nav-item active" onclick="switchOfficeTab('sync')">${t.syncTasks}</div>
                <div class="nav-item" onclick="switchOfficeTab('stats')">${t.regionStats}</div>
                <div class="nav-item" onclick="switchOfficeTab('alerts')">${t.alerts}</div>
            `;
            showSyncView();
        };

        window.switchOfficeTab = function(tab) {
            document.querySelectorAll('.nav-item').forEach(i => i.classList.remove('active'));
            event.target.classList.add('active');
            if (tab === 'sync') showSyncView();
            else if (tab === 'stats') showRegionStats();
            else showAlerts();
        };

        window.syncTasks = function() {
            const text = document.getElementById('syncText').value;
            const lines = text.split('\n');
            
            lines.forEach(line => {
                const match = line.match(/区域([ABC])：\s*(.+)/);
                if (match) {
                    const region = match[1];
                    const ids = match[2].split(/[,，\s]+/).filter(id => id.startsWith('FZ-'));
                    if (ids.length) todayTasks[region] = ids;
                }
            });
            
            alert(`同步成功！共 ${Object.values(todayTasks).flat().length} 个任务`);
            showSyncView();
        };

        function showSyncView() {
            const t = translations[currentLang];
            let html = `
                <div class="stats-card">
                    <div class="stats-title">📱 ${t.syncTasks}</div>
                    <div style="background:#f5f5f5; padding:12px; border-radius:12px; margin-bottom:12px; font-size:13px;">
                        区域A：FZ-A00006, FZ-A00009<br>
                        区域B：FZ-A00101, FZ-A00102
                    </div>
                    <textarea class="sync-textarea" id="syncText" placeholder="区域A：FZ-A00006, FZ-A00009"></textarea>
                    <button class="sync-btn" onclick="syncTasks()">${t.sync}</button>
                </div>
            `;
            
            html += '<div class="stats-card"><div class="stats-title">今日任务</div>';
            for (let r in todayTasks) {
                if (todayTasks[r].length) {
                    html += `<div style="font-weight:600; margin-top:10px;">区域${r}</div>`;
                    todayTasks[r].forEach(id => html += `<span class="freezer-tag">${id}</span>`);
                }
            }
            document.getElementById('content').innerHTML = html + '</div>';
        }

        function showRegionStats() {
            const regions = ['A', 'B', 'C'];
            let html = '<div class="stats-card"><div class="stats-title">📍 区域统计</div>';
            regions.forEach(r => {
                const regionFreezers = freezers.filter(f => f.region === r);
                const todayCount = photos.filter(p => regionFreezers.some(f => f.id === p.freezerId) && isToday(p.time)).length;
                const percent = Math.round(todayCount / regionFreezers.length * 100) || 0;
                html += `
                    <div style="margin:15px 0;">
                        <div style="display:flex; justify-content:space-between;">区域${r} <span>${todayCount}/${regionFreezers.length}</span></div>
                        <div class="progress-bar"><div class="progress-fill" style="width:${percent}%"></div></div>
                    </div>
                `;
            });
            document.getElementById('content').innerHTML = html + '</div>';
        }

        function showAlerts() {
            const alerts = freezers.filter(f => {
                const last = photos.filter(p => p.freezerId === f.id).sort((a,b) => new Date(b.time) - new Date(a.time))[0];
                return !last || (new Date() - new Date(last.time)) > 7*24*60*60*1000;
            });
            
            let html = `<div class="stats-card"><div class="stats-title">⚠️ 预警 (${alerts.length})</div>`;
            if (!alerts.length) html += '<div>✅ 一切正常</div>';
            else alerts.slice(0,10).forEach(f => html += `<div style="padding:8px 0; border-bottom:1px solid var(--border);">${f.id} - ${f.shop}</div>`);
            document.getElementById('content').innerHTML = html + '</div>';
        }

        // ===== BOSS VIEW =====
        window.showBossView = function() {
            const t = translations[currentLang];
            document.getElementById('navBar').innerHTML = `
                <div class="nav-item active" onclick="switchBossTab('overview')">${t.overview}</div>
                <div class="nav-item" onclick="switchBossTab('regions')">${t.regions}</div>
                <div class="nav-item" onclick="switchBossTab('sales')">${t.salesmen}</div>
                <div class="nav-item" onclick="switchBossTab('alerts')">${t.alerts}</div>
            `;
            showBossOverview();
        };

        window.switchBossTab = function(tab) {
            document.querySelectorAll('.nav-item').forEach(i => i.classList.remove('active'));
            event.target.classList.add('active');
            if (tab === 'overview') showBossOverview();
            else if (tab === 'regions') showRegionStats();
            else if (tab === 'sales') showBossSales();
            else showAlerts();
        };

        function showBossOverview() {
            const t = translations[currentLang];
            const total = freezers.length;
            const today = photos.filter(p => isToday(p.time)).length;
            const week = photos.filter(p => isThisWeek(p.time)).length;
            const month = photos.filter(p => isThisMonth(p.time)).length;
            
            // 统计问题冰柜
            const problems = photos.filter(p => {
                if (!p.remark) return false;
                const text = p.remark.text || '';
                return !text.includes('正常') && !text.includes('Normal');
            }).length;
            
            let html = `
                <div class="stats-card">
                    <div class="stats-title">📊 ${t.overview}</div>
                    <div class="stats-grid">
                        <div class="stat-item"><div class="stat-value">${total}</div><div class="stat-label">${t.totalFreezers}</div></div>
                        <div class="stat-item"><div class="stat-value">${today}</div><div class="stat-label">${t.todayPhotos}</div></div>
                        <div class="stat-item"><div class="stat-value">${week}</div><div class="stat-label">${t.weekPhotos}</div></div>
                        <div class="stat-item"><div class="stat-value">${month}</div><div class="stat-label">${t.monthPhotos}</div></div>
                    </div>
                    <div style="margin-top:16px; padding:12px; background:${problems > 0 ? '#fee2e2' : '#f0fdf4'}; border-radius:12px;">
                        ${problems > 0 ? `⚠️ 问题冰柜：${problems}台` : '✅ 所有冰柜正常'}
                    </div>
                </div>
            `;
            
            document.getElementById('content').innerHTML = html;
        }

        function showBossSales() {
            const t = translations[currentLang];
            const sales = [
                { name: '业务员001', id: '001', region: 'A' },
                { name: '业务员002', id: '002', region: 'B' },
                { name: '业务员003', id: '003', region: 'C' }
            ];
            
            let html = '<div class="stats-card"><div class="stats-title">👥 ' + t.salesmen + '</div>';
            
            // 今日排名
            const todayRank = sales.map(s => ({
                name: s.name,
                count: photos.filter(p => p.sales === s.id && isToday(p.time)).length
            })).sort((a,b) => b.count - a.count);
            
            html += '<div style="margin-bottom:16px;"><div style="font-weight:600;">今日排行</div>';
            todayRank.forEach((s, i) => {
                const medal = i === 0 ? '🥇' : i === 1 ? '🥈' : i === 2 ? '🥉' : '👤';
                html += `<div style="display:flex; justify-content:space-between; padding:8px 0;">${medal} ${s.name} <span style="font-weight:600;">${s.count}张</span></div>`;
            });
            html += '</div>';
            
            // 本周总计
            html += '<div><div style="font-weight:600;">本周总计</div>';
            sales.forEach(s => {
                const week = photos.filter(p => p.sales === s.id && isThisWeek(p.time)).length;
                const month = photos.filter(p => p.sales === s.id && isThisMonth(p.time)).length;
                html += `<div style="display:flex; justify-content:space-between; padding:6px 0;">${s.name} <span>本周${week} / 本月${month}</span></div>`;
            });
            html += '</div></div>';
            
            document.getElementById('content').innerHTML = html;
        }

        // ===== UTILS =====
        function hasPhotoToday(id) {
            return photos.some(p => p.freezerId === id && isToday(p.time));
        }

        function isToday(date) {
            const d = new Date(date);
            const t = new Date();
            return d.getDate() === t.getDate() && d.getMonth() === t.getMonth() && d.getFullYear() === t.getFullYear();
        }

        function isThisWeek(date) {
            const d = new Date(date);
            const t = new Date();
            const w = new Date(t); w.setDate(t.getDate() - 7);
            return d >= w;
        }

        function isThisMonth(date) {
            const d = new Date(date);
            const t = new Date();
            return d.getMonth() === t.getMonth() && d.getFullYear() === t.getFullYear();
        }

        // ===== INIT =====
        window.onload = async function() {
            await loadFreezersFromSheet();
            updateUILanguage();
            
            const saved = localStorage.getItem('aice_user');
            if (saved) {
                try {
                    currentUser = JSON.parse(saved);
                    document.getElementById('loginPage').classList.add('hidden');
                    document.getElementById('mainPage').classList.remove('hidden');
                    document.getElementById('displayName').textContent = currentLang === 'zh' ? currentUser.name : currentUser.nameEn;
                    
                    const d = new Date();
                    document.getElementById('currentDate').textContent = `${d.getFullYear()}年${d.getMonth()+1}月${d.getDate()}日`;
                    
                    if (currentUser.role === 'sales') showSalesView();
                    else if (currentUser.role === 'office') showOfficeView();
                    else showBossView();
                } catch (e) {
                    localStorage.removeItem('aice_user');
                }
            }
        };
    </script>
</body>
</html>
