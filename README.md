[index.html](https://github.com/user-attachments/files/35206636/index.html)
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LifeHub — Персональное пространство</title>
    <style>
        :root {
            --bg-main: #f8f9fa;
            --bg-surface: #ffffff;
            --text-primary: #1a1d20;
            --text-secondary: #6c757d;
            --accent: #2563eb;
            --accent-light: #eff6ff;
            --border: #e9ecef;
            --radius: 12px;
            --shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-main);
            color: var(--text-primary);
            display: flex;
            height: 100vh;
            overflow: hidden;
        }

        /* Сайдбар */
        aside {
            width: 250px;
            background: var(--bg-surface);
            border-right: 1px solid var(--border);
            padding: 20px 16px;
            display: flex;
            flex-direction: column;
            gap: 6px;
            overflow-y: auto;
        }

        .logo {
            font-size: 20px;
            font-weight: 700;
            padding: 0 12px 16px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-item {
            padding: 9px 14px;
            border-radius: 8px;
            cursor: pointer;
            color: var(--text-secondary);
            font-weight: 500;
            font-size: 14px;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .nav-item:hover {
            background: var(--bg-main);
            color: var(--text-primary);
        }

        .nav-item.active {
            background: var(--accent-light);
            color: var(--accent);
        }

        /* Блок резервного копирования в сайдбаре */
        .backup-box {
            margin-top: auto;
            padding-top: 14px;
            border-top: 1px solid var(--border);
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .backup-title {
            font-size: 12px;
            font-weight: 600;
            color: var(--text-secondary);
            padding: 0 4px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .backup-btn {
            width: 100%;
            padding: 8px 12px;
            font-size: 13px;
            text-align: left;
            display: flex;
            align-items: center;
            gap: 8px;
            background: var(--bg-main);
            color: var(--text-primary);
            border: 1px solid var(--border);
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.2s;
        }

        .backup-btn:hover {
            border-color: var(--accent);
            color: var(--accent);
            background: var(--accent-light);
        }

        /* Основная область */
        main {
            flex: 1;
            padding: 32px 40px;
            overflow-y: auto;
        }

        .section {
            display: none;
            animation: fadeIn 0.25s ease;
        }

        .section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-size: 28px;
            margin-bottom: 8px;
        }

        .subtitle {
            color: var(--text-secondary);
            margin-bottom: 28px;
            font-size: 15px;
        }

        /* Карточки и сетки */
        .grid-2 { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
        .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 20px; }

        .card {
            background: var(--bg-surface);
            border: 1px solid var(--border);
            border-radius: var(--radius);
            padding: 20px;
            box-shadow: var(--shadow);
        }

        .card h3 {
            font-size: 17px;
            margin-bottom: 14px;
        }

        /* Элементы форм */
        input, textarea, select {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 14px;
            outline: none;
            transition: border-color 0.2s;
            background: var(--bg-main);
        }

        input:focus, textarea:focus {
            border-color: var(--accent);
            background: var(--bg-surface);
        }

        button.primary {
            background: var(--accent);
            color: white;
            border: none;
            padding: 10px 16px;
            border-radius: 8px;
            font-weight: 500;
            cursor: pointer;
            font-size: 14px;
            transition: opacity 0.2s;
        }

        button.primary:hover { opacity: 0.9; }
        button.secondary { background: var(--bg-main); color: var(--text-primary); border: 1px solid var(--border); padding: 8px 14px; border-radius: 8px; cursor: pointer; font-size: 13px; }

        /* Планер */
        .input-group { display: flex; gap: 10px; margin-bottom: 16px; }
        .task-list { list-style: none; display: flex; flex-direction: column; gap: 8px; }
        .task-item {
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 12px;
            background: var(--bg-main);
            border-radius: 8px;
        }
        .task-item.done span { text-decoration: line-through; color: var(--text-secondary); }

        /* Калькулятор */
        .calc-wrapper { max-width: 320px; }
        .calc-display {
            width: 100%;
            height: 60px;
            font-size: 26px;
            text-align: right;
            padding: 10px 15px;
            margin-bottom: 12px;
            background: var(--bg-main);
            border-radius: 8px;
            border: 1px solid var(--border);
        }
        .calc-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px; }
        .calc-btn {
            padding: 16px;
            font-size: 18px;
            background: var(--bg-main);
            color: var(--text-primary);
            border: 1px solid var(--border);
            border-radius: 8px;
            cursor: pointer;
        }
        .calc-btn.op { background: var(--accent-light); color: var(--accent); }
        .calc-btn.eq { background: var(--accent); color: white; grid-column: span 2; }

        /* Календарь */
        .cal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px; }
        .cal-grid { display: grid; grid-template-columns: repeat(7, 1fr); gap: 8px; text-align: center; }
        .cal-day-name { font-weight: 600; color: var(--text-secondary); font-size: 13px; padding-bottom: 8px; }
        .cal-day {
            padding: 14px 8px;
            background: var(--bg-main);
            border-radius: 8px;
            font-size: 14px;
        }
        .cal-day.today { background: var(--accent); color: white; font-weight: 700; }
        .cal-day.empty { background: transparent; }

        /* Дневник и Блокнот */
        .entry-card { border-left: 3px solid var(--accent); padding-left: 14px; margin-bottom: 14px; }
        .entry-date { font-size: 12px; color: var(--text-secondary); margin-bottom: 4px; }

        /* Медиа и Новости */
        .media-thumb {
            height: 140px;
            background: var(--bg-main);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            margin-bottom: 12px;
            color: var(--text-secondary);
        }
        .tag {
            display: inline-block;
            padding: 4px 8px;
            background: var(--accent-light);
            color: var(--accent);
            border-radius: 6px;
            font-size: 12px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        /* Уведомление (Toast) */
        .toast {
            position: fixed;
            bottom: 24px;
            right: 24px;
            background: #1a1d20;
            color: white;
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 14px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
            pointer-events: none;
            z-index: 1000;
        }
        .toast.show {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>

    <!-- Боковое меню -->
    <aside>
        <div class="logo">⚡ LifeHub</div>
        <div class="nav-item active" onclick="switchTab('dashboard', this)">🏠 Обзор</div>
        <div class="nav-item" onclick="switchTab('planner', this)">✅ Планер</div>
        <div class="nav-item" onclick="switchTab('calendar', this)">📅 Календарь</div>
        <div class="nav-item" onclick="switchTab('notes', this)">📝 Блокнот</div>
        <div class="nav-item" onclick="switchTab('diary', this)">📖 Дневник</div>
        <div class="nav-item" onclick="switchTab('calc', this)">🧮 Калькулятор</div>
        <div class="nav-item" onclick="switchTab('news', this)">📰 Новости</div>
        <div class="nav-item" onclick="switchTab('library', this)">📚 Библиотека</div>
