<!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asrorcodex - Professional Onlayn Koder</title>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Fira+Code:wght@400;500&display=swap" rel="stylesheet">
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* --- CSS O'zgaruvchilar (Ranglar, Shrifter) --- */
        :root {
            --bg-color: #181825; /* Asosiy fon */
            --surface-color: #1e1e2e; /* Panellar foni */
            --border-color: #313244; /* Chegaralar */
            --text-primary: #cdd6f4; /* Asosiy matn */
            --text-secondary: #a6adc8; /* Ikkinchi darajali matn */
            --accent-color: #89b4fa; /* Asosiy urg'u rangi (tugmalar, havolalar) */
            --accent-hover: #b4befe; /* Urg'u rangi ustiga bosganda */
            --success-color: #a6e3a1; /* Muvaffaqiyat rangi */
            --danger-color: #f38ba8; /* Xatolik rangi */
            --font-ui: 'Inter', sans-serif; /* Interfeys shrifti */
            --font-code: 'Fira Code', monospace; /* Kod shrifti */
        }
        
        /* Kungi rejim ranglari */
        body.light-mode {
            --bg-color: #f5f5f5; /* Asosiy fon */
            --surface-color: #ffffff; /* Panellar foni */
            --border-color: #e0e0e0; /* Chegaralar */
            --text-primary: #333333; /* Asosiy matn */
            --text-secondary: #666666; /* Ikkinchi darajali matn */
            --accent-color: #4285f4; /* Asosiy urg'u rangi */
            --accent-hover: #3367d6; /* Urg'u rangi ustiga bosganda */
        }

        /* --- Umumiy Stil --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--font-ui);
            background-color: var(--bg-color);
            color: var(--text-primary);
            height: 100vh;
            display: flex;
            flex-direction: column;
            overflow: hidden;
            transition: background-color 0.3s, color 0.3s;
        }

        /* --- Header --- */
        .header {
            background-color: var(--surface-color);
            padding: 1rem 1.5rem;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-shrink: 0;
            transition: background-color 0.3s, border-color 0.3s;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 600;
            color: var(--accent-color);
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        .logo i {
            font-size: 1.8rem;
        }

        .controls {
            display: flex;
            gap: 1rem;
            align-items: center;
        }

        .btn {
            background-color: var(--accent-color);
            color: var(--bg-color);
            border: none;
            padding: 0.6rem 1.2rem;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-family: var(--font-ui);
        }
        .btn:hover {
            background-color: var(--accent-hover);
        }
        .btn:active {
            transform: scale(0.98);
        }
        .btn-secondary {
            background-color: transparent;
            color: var(--text-secondary);
            border: 1px solid var(--border-color);
        }
        .btn-secondary:hover {
            background-color: var(--border-color);
            color: var(--text-primary);
        }
        
        /* Chiroq tugmasi stili */
        .theme-toggle {
            position: relative;
            width: 60px;
            height: 30px;
            background-color: var(--border-color);
            border-radius: 30px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .theme-toggle-slider {
            position: absolute;
            top: 3px;
            left: 3px;
            width: 24px;
            height: 24px;
            background-color: var(--accent-color);
            border-radius: 50%;
            transition: transform 0.3s, background-color 0.3s;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .theme-toggle-slider i {
            color: var(--bg-color);
            font-size: 14px;
        }
        
        body.light-mode .theme-toggle-slider {
            transform: translateX(30px);
        }

        /* --- Asosiy Kontent --- */
        .main-container {
            display: flex;
            flex: 1;
            overflow: hidden;
        }

        /* --- Kod Muharriri Paneli --- */
        .editor-panel {
            flex: 1;
            display: flex;
            flex-direction: column;
            background-color: var(--surface-color);
            border-right: 1px solid var(--border-color);
            transition: background-color 0.3s, border-color 0.3s;
        }

        .tabs {
            display: flex;
            background-color: var(--bg-color);
            border-bottom: 1px solid var(--border-color);
            transition: background-color 0.3s, border-color 0.3s;
        }
        .tab {
            padding: 1rem 1.5rem;
            cursor: pointer;
            font-weight: 500;
            color: var(--text-secondary);
            border-bottom: 3px solid transparent;
            transition: all 0.2s;
        }
        .tab:hover {
            color: var(--text-primary);
            background-color: rgba(255, 255, 255, 0.05);
        }
        .tab.active {
            color: var(--accent-color);
            border-bottom-color: var(--accent-color);
        }

        .code-container {
            flex-grow: 1;
            padding: 1rem;
            overflow-y: auto;
        }
        .code-textarea {
            width: 100%;
            height: 100%;
            background-color: var(--bg-color);
            color: var(--text-primary);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 1rem;
            font-family: var(--font-code);
            font-size: 15px;
            resize: none;
            outline: none;
            line-height: 1.6;
            transition: background-color 0.3s, color 0.3s, border-color 0.3s;
        }

        /* --- Natija Paneli --- */
        .preview-panel {
            flex: 1;
            display: flex;
            flex-direction: column;
            background-color: var(--surface-color);
            transition: background-color 0.3s;
        }
        .preview-header {
            padding: 1rem 1.5rem;
            background-color: var(--bg-color);
            border-bottom: 1px solid var(--border-color);
            font-weight: 600;
            color: var(--text-secondary);
            transition: background-color 0.3s, border-color 0.3s, color 0.3s;
        }
        #preview-frame {
            flex-grow: 1;
            background-color: white;
            border: none;
        }

        /* --- Xabarlar (Notifications) --- */
        .notification-container {
            position: fixed;
            top: 80px;
            right: 20px;
            z-index: 1000;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .notification {
            background-color: var(--surface-color);
            border: 1px solid var(--border-color);
            border-left: 4px solid var(--accent-color);
            padding: 1rem 1.5rem;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            min-width: 250px;
            animation: slideIn 0.3s ease-out;
            transition: opacity 0.3s, transform 0.3s;
        }
        .notification.success { border-left-color: var(--success-color); }
        .notification.error { border-left-color: var(--danger-color); }
        .notification.hide {
            opacity: 0;
            transform: translateX(100%);
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(100%);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        /* --- Moslashuvchanlik (Responsive) --- */
        @media (max-width: 768px) {
            .main-container {
                flex-direction: column;
            }
            .editor-panel {
                border-right: none;
                border-bottom: 1px solid var(--border-color);
            }
            .controls {
                flex-wrap: wrap;
            }
            .btn {
                padding: 0.5rem 1rem;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>

    <!-- Header -->
    <header class="header">
        <div class="logo">
            <i class="fas fa-code"></i>
            <span>Asrorcodex</span>
        </div>
        <div class="controls">
            <button class="btn" id="run-btn">
                <i class="fas fa-play"></i> Ishga tushirish
            </button>
            <button class="btn btn-secondary" id="clear-btn">
                <i class="fas fa-eraser"></i> Tozalash
            </button>
            <button class="btn btn-secondary" id="save-btn">
                <i class="fas fa-save"></i> Saqlash
            </button>
            <button class="btn btn-secondary" id="load-btn">
                <i class="fas fa-folder-open"></i> Yuklash
            </button>
            <button class="btn btn-secondary" id="download-btn">
                <i class="fas fa-download"></i> Yuklab olish
            </button>
            <div class="theme-toggle" id="theme-toggle">
                <div class="theme-toggle-slider">
                    <i class="fas fa-moon" id="theme-icon"></i>
                </div>
            </div>
        </div>
    </header>

    <!-- Asosiy Kontent -->
    <main class="main-container">
        <!-- Kod Muharriri -->
        <section class="editor-panel">
            <div class="tabs">
                <div class="tab active" data-lang="html">HTML</div>
                <div class="tab" data-lang="css">CSS</div>
                <div class="tab" data-lang="js">JavaScript</div>
            </div>
            <div class="code-container">
                <textarea id="html-code" class="code-textarea" spellcheck="false"><!DOCTYPE html>
<html lang="uz">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Asrorcodex</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Asrorcodex ga xush kelibsiz!</h1>
        <p>Bu - sizning professional kod muharringiz.</p>
        <button id="myButton">Menga bosing!</button>
    </div>
    <script src="script.js"></script>
</body>
</html></textarea>
                <textarea id="css-code" class="code-textarea" style="display:none;" spellcheck="false">body {
    font-family: var(--font-ui);
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    text-align: center;
}

.container {
    background: rgba(255, 255, 255, 0.1);
    padding: 2rem 3rem;
    border-radius: 16px;
    backdrop-filter: blur(10px);
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
}

h1 {
    font-size: 2.5rem;
    margin-bottom: 0.5rem;
}

button {
    margin-top: 1rem;
    padding: 12px 24px;
    font-size: 1rem;
    font-weight: 600;
    color: #764ba2;
    background-color: white;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
}

button:hover {
    transform: translateY(-3px);
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
}</textarea>
                <textarea id="js-code" class="code-textarea" style="display:none;" spellcheck="false">document.getElementById('myButton').addEventListener('click', () => {
    alert('Asrorcodex dan salom! JavaScript muvaffaqiyatli ishlamoqda.');
});</textarea>
            </div>
        </section>

        <!-- Natija Oynasi -->
        <section class="preview-panel">
            <div class="preview-header">Natija</div>
            <iframe id="preview-frame"></iframe>
        </section>
    </main>

    <!-- Xabarlar uchun joy -->
    <div class="notification-container" id="notification-container"></div>

    <script>
        // --- Elementlarni olish ---
        const htmlCode = document.getElementById('html-code');
        const cssCode = document.getElementById('css-code');
        const jsCode = document.getElementById('js-code');
        const previewFrame = document.getElementById('preview-frame');
        const tabs = document.querySelectorAll('.tab');
        const notificationContainer = document.getElementById('notification-container');
        const themeToggle = document.getElementById('theme-toggle');
        const themeIcon = document.getElementById('theme-icon');

        // --- Tugmalar ---
        const runBtn = document.getElementById('run-btn');
        const clearBtn = document.getElementById('clear-btn');
        const saveBtn = document.getElementById('save-btn');
        const loadBtn = document.getElementById('load-btn');
        const downloadBtn = document.getElementById('download-btn');

        // --- Funksiyalar ---

        /**
         * Kodni ishga tushirish va natijani iframe'ga yozish
         */
        function runCode() {
            const html = htmlCode.value;
            const css = `<style>${cssCode.value}</style>`;
            const js = `<script>${jsCode.value}<\/script>`;
            
            const previewDocument = previewFrame.contentDocument || previewFrame.contentWindow.document;
            previewDocument.open();
            previewDocument.write(html + css + js);
            previewDocument.close();
            
            showNotification('Kod muvaffaqiyatli ishga tushirildi!', 'success');
        }

        /**
         * Barcha kodlarni tozalash
         */
        function clearCode() {
            if (confirm('Barcha kodlarni to\'g\'ri tozalashni xohlaysizmi?')) {
                htmlCode.value = '';
                cssCode.value = '';
                jsCode.value = '';
                runCode();
                showNotification('Barcha kodlar tozalandi.', 'success');
            }
        }

        /**
         * Kodni localStorage ga saqlash
         */
        function saveCode() {
            const projectName = prompt('Loyihangizga nom bering:', 'Mening Loyiham');
            if (!projectName) return;

            const project = {
                name: projectName,
                html: htmlCode.value,
                css: cssCode.value,
                js: jsCode.value
            };

            let projects = JSON.parse(localStorage.getItem('asrorcodex_projects') || '[]');
            projects.push(project);
            localStorage.setItem('asrorcodex_projects', JSON.stringify(projects));

            showNotification(`"${projectName}" nomi bilan saqlandi!`, 'success');
        }

        /**
         * Saqlangan kodlarni localStorage dan yuklash
         */
        function loadCode() {
            const projects = JSON.parse(localStorage.getItem('asrorcodex_projects') || '[]');
            if (projects.length === 0) {
                showNotification('Hech qanday saqlangan loyiha topilmadi.', 'error');
                return;
            }

            const projectNames = projects.map((p, i) => `${i + 1}. ${p.name}`).join('\n');
            const choice = prompt(`Qaysi loyihani yuklamoqchisiz? Raqamini kiriting:\n${projectNames}`);

            const index = parseInt(choice) - 1;
            if (index >= 0 && index < projects.length) {
                const project = projects[index];
                htmlCode.value = project.html;
                cssCode.value = project.css;
                jsCode.value = project.js;
                runCode();
                showNotification(`"${project.name}" yuklandi!`, 'success');
            } else {
                showNotification('Noto\'g\'ri raqam kiritildi.', 'error');
            }
        }

        /**
         * Kodni HTML fayl sifatida yuklab olish
         */
        function downloadCode() {
            const html = htmlCode.value;
            const css = `<style>\n${cssCode.value}\n</style>`;
            const js = `<script>\n${jsCode.value}\n<\/script>`;
            
            // CSS va JS ni HTML ga qo'shish
            const finalHtml = html.replace('</head>', `${css}\n</head>`).replace('</body>', `${js}\n</body>`);
            
            const blob = new Blob([finalHtml], { type: 'text/html' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'asrorcodex-project.html';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            showNotification('Kod yuklab olindi!', 'success');
        }

        /**
         * Xabar (notification) ko'rsatish
         */
        function showNotification(message, type = 'info') {
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.textContent = message;
            notificationContainer.appendChild(notification);

            setTimeout(() => {
                notification.classList.add('hide');
                setTimeout(() => notification.remove(), 300); // Animatsiya tugagandan so'ng o'chirish
            }, 3000);
        }
        
        /**
         * Mavzuni almashtirish (tungi/kungi)
         */
        function toggleTheme() {
            document.body.classList.toggle('light-mode');
            
            if (document.body.classList.contains('light-mode')) {
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
                localStorage.setItem('asrorcodex_theme', 'light');
            } else {
                themeIcon.classList.remove('fa-sun');
                themeIcon.classList.add('fa-moon');
                localStorage.setItem('asrorcodex_theme', 'dark');
            }
        }
        
        /**
         * Saqlangan mavzuni yuklash
         */
        function loadTheme() {
            const savedTheme = localStorage.getItem('asrorcodex_theme');
            if (savedTheme === 'light') {
                document.body.classList.add('light-mode');
                themeIcon.classList.remove('fa-moon');
                themeIcon.classList.add('fa-sun');
            }
        }

        // --- Event Listeners (Tugmalarga hodisalar bog'lash) ---

        runBtn.addEventListener('click', runCode);
        clearBtn.addEventListener('click', clearCode);
        saveBtn.addEventListener('click', saveCode);
        loadBtn.addEventListener('click', loadCode);
        downloadBtn.addEventListener('click', downloadCode);
        themeToggle.addEventListener('click', toggleTheme);

        // Tablarni almashtirish
        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                // Barcha tablardan 'active' klassini olib tashlash
                tabs.forEach(t => t.classList.remove('active'));
                // Bosilgan tabga 'active' klassini qo'shish
                tab.classList.add('active');

                const lang = tab.dataset.lang;

                // Barcha textarea'larni yashirish
                document.getElementById('html-code').style.display = 'none';
                document.getElementById('css-code').style.display = 'none';
                document.getElementById('js-code').style.display = 'none';

                // Kerakli textarea'ni ko'rsatish
                document.getElementById(`${lang}-code`).style.display = 'block';
            });
        });

        // Klaviatura qisqartmasi: Ctrl + Enter bilan kodni ishga tushirish
        document.addEventListener('keydown', (e) => {
            if (e.ctrlKey && e.key === 'Enter') {
                e.preventDefault(); // Standart xatti-harakatni oldini olish
                runCode();
            }
        });

        // Sahifa yuklanganda dastlabki kodni ishga tushirish
        window.addEventListener('load', () => {
            loadTheme();
            runCode();
        });
    </script>
</body>
</html>
