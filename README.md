lab15
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title data-lang-key="appTitle">Учёт Студентов | EduTrack // FESTIVAL VIBE 🍂</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <style>
        /* -------------------------------------- */
        /* 🌈 ГЕНЕРАЦИЯ ЦВЕТОВ */
        /* -------------------------------------- */
        :root {
            /* DARK THEME (Classic Cyberpunk - Без изменений) */
            --dark-bg: #0d0d1a;
            --dark-surface: #1a1a2e;
            --dark-text: #00ffc4; /* Neon Green */
            --dark-accent: #3498db; /* Neon Blue */
            --dark-highlight: #ff00ff; /* Neon Fuchsia */
            --dark-shadow: rgba(0, 255, 196, 0.5);

            /* FESTIVAL LIGHT THEME (New Style) */
            --light-bg: #f5f7fa; /* Очень светлый фон */
            --light-surface: white;
            --light-text: #333; /* Темный текст */
            --light-accent: #ff7043; /* Coral/Orange Accent (Теплый) */
            --light-highlight: #ffc107; /* Yellow/Amber Highlight (Веселый) */
            --light-shadow: rgba(0, 0, 0, 0.15); /* Мягкая тень */
            --light-gradient: linear-gradient(135deg, #ff7043, #ff9800);
        }

        /* -------------------------------------- */
        /* 1. БАЗОВЫЕ СТИЛИ (ПО УМОЛЧАНИЮ - DARK) */
        /* -------------------------------------- */

        body {
            font-family: 'Consolas', monospace;
            margin: 0;
            padding: 0;
            background-color: var(--dark-bg);
            background-image: radial-gradient(#2c3e50 1px, transparent 0);
            background-size: 40px 40px;
            color: var(--dark-text);
            min-height: 100vh;
            transition: all 0.5s ease-in-out;
        }

        /* ... (Остальные общие стили Dark Theme) ... */

        main {
            max-width: 1100px;
            margin: 40px auto;
            padding: 20px;
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        /* Шапка и Управление */
        .app-header {
            background: var(--dark-surface);
            padding: 20px 40px;
            border-bottom: 2px solid var(--dark-highlight);
            box-shadow: 0 0 15px var(--dark-highlight);
            border-bottom-left-radius: 5px;
            border-bottom-right-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.5s ease-in-out;
        }

        .logo { display: flex; align-items: center; }

        .logo i {
            font-size: 2.8rem;
            color: var(--dark-text);
            text-shadow: 0 0 10px var(--dark-text);
            margin-right: 15px;
            transition: all 0.5s;
        }

        .logo h1 {
            margin: 0;
            font-size: 2rem;
            color: var(--dark-accent);
            letter-spacing: 2px;
            transition: all 0.5s;
        }

        .controls-panel {
            display: flex;
            gap: 10px;
            align-items: center;
        }
        
        .main-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
            margin-top: 10px;
        }
        
        .tab-group {
            display: flex;
            gap: 5px;
        }

        /* Карточки, Заголовки, и Неоновые Элементы */
        .card {
            background: var(--dark-surface);
            padding: 30px;
            border-radius: 8px; /* Увеличенное скругление */
            border: 1px solid var(--dark-accent);
            box-shadow: 0 0 20px rgba(52, 152, 219, 0.3);
            transition: all 0.5s;
        }

        h2 {
            color: var(--dark-highlight);
            padding-bottom: 10px;
            margin-top: 0;
            font-size: 1.6rem;
            border-bottom: 1px solid var(--dark-highlight);
            text-shadow: 0 0 5px var(--dark-highlight);
            animation: textshadow 1.5s infinite alternate;
            transition: all 0.5s;
        }

        h2 i {
            margin-right: 10px;
            color: var(--dark-text);
        }

        .app-text-accent { 
            color: var(--dark-text);
            text-shadow: 0 0 5px var(--dark-text);
            font-weight: bold;
            transition: all 0.5s;
        }

        /* Входные поля */
        .app-input {
            padding: 12px;
            border: 2px solid var(--dark-accent);
            border-radius: 5px;
            background: var(--dark-surface);
            color: var(--dark-text);
            box-shadow: 0 0 8px rgba(52, 152, 219, 0.5);
            resize: vertical;
            transition: all 0.5s;
        }

        .app-input:focus {
            border-color: var(--dark-highlight);
            box-shadow: 0 0 15px var(--dark-highlight);
            outline: none;
        }

        /* Кнопки */
        .app-btn {
            padding: 12px 20px;
            border: none;
            border-radius: 50px;
            background: var(--dark-accent);
            color: var(--dark-surface);
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 0 10px rgba(52, 152, 219, 0.7);
            letter-spacing: 1px;
            transition: all 0.3s;
        }
        
        .app-btn:hover {
            background: var(--dark-highlight); 
            color: black;
            box-shadow: 0 0 15px var(--dark-highlight);
        }

        .tab-btn.active {
            background: var(--dark-text);
            color: var(--dark-surface);
            box-shadow: 0 0 15px var(--dark-text);
        }

        .delete-btn {
            background-color: #e74c3c;
            box-shadow: 0 0 10px rgba(231, 76, 60, 0.7);
        }

        .delete-btn:hover {
            background-color: #c0392b;
            box-shadow: 0 0 15px rgba(231, 76, 60, 1);
        }

        /* Таблица */
        #students-table {
            background: var(--dark-surface); 
            border: 1px solid var(--dark-text);
            box-shadow: 0 0 10px var(--dark-shadow);
        }

        #students-table th {
            background-color: #2c3e50;
            color: var(--dark-accent);
        }

        #students-table tr:hover {
            background-color: #2c3e50;
            color: var(--dark-highlight);
        }


        /* -------------------------------------- */
        /* 2. ФЕСТИВАЛЬНЫЙ СТИЛЬ (ПЕРЕОПРЕДЕЛЕНИЕ LIGHT THEME) */
        /* -------------------------------------- */

        body.light-theme {
            background-color: var(--light-bg);
            color: var(--light-text);
            font-family: 'Roboto', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            
            /* 🌿 ФОН - ТРОПИЧЕСКИЕ ЛИСТЬЯ */
            background-image: 
                radial-gradient(ellipse 50% 50% at 50% 100%, rgba(255, 255, 255, 0) 0%, rgba(240, 240, 240, 0.5) 100%),
                repeating-linear-gradient(135deg, rgba(255, 255, 255, 0.1) 0, rgba(255, 255, 255, 0.1) 4px, transparent 4px, transparent 8px),
                linear-gradient(135deg, #fdfdfd 25%, #f5f7fa 25%, #f5f7fa 50%, #fdfdfd 50%, #fdfdfd 75%, #f5f7fa 75%, #f5f7fa 100%);
            background-size: 
                cover, 
                100% 100%,
                40px 40px; /* Размер "листьев" - базовый паттерн */
        }
        
        body.light-theme .app-header {
            background: var(--light-surface);
            border-bottom: 3px solid var(--light-accent);
            box-shadow: 0 4px 15px var(--light-shadow);
        }

        body.light-theme .logo i {
            color: var(--light-accent);
            text-shadow: none;
        }

        body.light-theme .card {
            background: var(--light-surface);
            border: 1px solid #ddd;
            border-radius: 12px;
            box-shadow: 0 8px 20px var(--light-shadow);
        }

        body.light-theme h2 {
            color: var(--light-accent);
            border-bottom: 2px solid var(--light-highlight);
            text-shadow: none;
            animation: none;
        }
        
        body.light-theme h2 i {
            color: var(--light-highlight);
        }
        
        body.light-theme .app-text-accent {
            color: var(--light-accent);
            font-weight: 900;
            text-shadow: 1px 1px 0px rgba(0,0,0,0.05);
        }

        body.light-theme .app-input {
            border: 1px solid #ccc;
            background: var(--light-surface);
            color: var(--light-text);
            border-radius: 8px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        body.light-theme .app-input:focus {
            border-color: var(--light-accent);
            box-shadow: 0 0 10px rgba(255, 112, 67, 0.5);
        }

        body.light-theme .app-btn {
            background: var(--light-gradient);
            color: white;
            border-radius: 50px;
            font-weight: 900;
            box-shadow: 0 5px 15px rgba(255, 112, 67, 0.4);
        }

        body.light-theme .app-btn:hover {
            background: var(--light-accent);
            transform: translateY(-2px);
            box-shadow: 0 7px 20px rgba(255, 112, 67, 0.6);
        }
        
        body.light-theme .tab-btn.active {
            background: var(--light-highlight);
            color: var(--light-text);
            box-shadow: 0 3px 10px rgba(255, 193, 7, 0.7);
        }
        
        body.light-theme .tab-btn.active:hover {
            background: var(--light-accent);
            color: white;
            box-shadow: 0 3px 10px rgba(255, 112, 67, 0.7);
        }


        body.light-theme .delete-btn {
            background-color: #e74c3c;
            box-shadow: 0 2px 5px rgba(231, 76, 60, 0.5);
        }

        /* Таблица */
        body.light-theme #students-table {
            background: var(--light-surface); 
            border: 1px solid #eee;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 4px 10px var(--light-shadow);
        }

        body.light-theme #students-table th {
            background-color: #eee;
            color: var(--light-text);
        }

        body.light-theme #students-table tr:hover {
            background-color: #fffaf0;
        }


        /* -------------------------------------- */
        /* 3. АНИМАЦИИ И УТИЛИТЫ */
        /* -------------------------------------- */
        
        @keyframes textshadow {
            0% { text-shadow: 0 0 5px var(--dark-highlight), 1px 1px 2px var(--dark-text); }
            50% { text-shadow: 0 0 5px var(--dark-text), -1px -1px 2px var(--dark-highlight); }
            100% { text-shadow: 0 0 5px var(--dark-highlight), 1px 1px 2px var(--dark-text); }
        }

        .view-section { display: none; }
        #students-table { width: 100%; border-collapse: collapse; margin-top: 15px; }
        #students-table th, #students-table td { padding: 15px; text-align: left; border: 1px solid #2c3e50; color: var(--dark-text); }
        body.light-theme #students-table th, body.light-theme #students-table td { border-color: #eee; color: var(--light-text); }
        #students-table th { text-transform: uppercase; font-size: 0.85em; letter-spacing: 2px; }
        #student-form, #profile-form { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; }
        #profile-form textarea { grid-column: 1 / -1; min-height: 100px; }
        .placeholder-content { padding: 50px; text-align: center; font-size: 1.2rem; color: var(--dark-text); }
        body.light-theme .placeholder-content { color: #777; }

        @media (max-width: 1000px) {
            .app-header { flex-direction: column; align-items: flex-start; padding: 20px; }
            .controls-panel { width: 100%; margin-top: 15px; }
            .main-tabs { justify-content: center; }
        }

        @media (max-width: 768px) {
            .controls-panel { flex-direction: column; }
            .tab-group { flex-wrap: wrap; justify-content: center; }
            .app-btn, .app-input, #lang-selector { width: 100%; }
            #student-form { grid-template-columns: 1fr; }
        }
    </style>
</head>

<body class="dark-theme">

    <header class="app-header">
        <div class="logo">
            <i class="fas fa-user-graduate"></i>
            <h1 data-lang-key="headerTitle">EduTrack // NEON ARCADE 🍂</h1>
        </div>
        
        <div class="controls-panel">
            <div class="tab-group">
                <button id="theme-toggle" class="app-btn tab-btn"><i class="fas fa-sun"></i></button>
                <select id="lang-selector" class="app-input">
                    <option value="RU">Русский (RU)</option>
                    <option value="EN">English (EN)</option>
                    <option value="JP">日本語 (JP)</option>
                </select>
            </div>
            
            <div class="main-tabs">
                <button id="tab-students" class="app-btn tab-btn active" data-lang-key="tabStudents"><i class="fas fa-users"></i> СТУДЕНТЫ</button>
                <button id="tab-subjects" class="app-btn tab-btn" data-lang-key="tabSubjects"><i class="fas fa-book"></i> ПРЕДМЕТЫ</button>
                <button id="tab-teachers" class="app-btn tab-btn" data-lang-key="tabTeachers"><i class="fas fa-chalkboard-teacher"></i> ПРЕПОДАВАТЕЛИ</button>
                <button id="tab-grades" class="app-btn tab-btn" data-lang-key="tabGrades"><i class="fas fa-graduation-cap"></i> ОЦЕНКИ</button>
                <button id="tab-reports" class="app-btn tab-btn" data-lang-key="tabReports"><i class="fas fa-chart-line"></i> ОТЧЕТЫ</button>
                <button id="tab-profile" class="app-btn tab-btn" data-lang-key="tabProfile"><i class="fas fa-user-cog"></i> ПРОФИЛЬ</button>
            </div>
        </div>
    </header>

    <main>
        
        <div id="students-view" class="view-section">
            <section class="card form-container">
                <h2 data-lang-key="h2AddStudent"><i class="fas fa-plus-circle"></i> ДОБАВИТЬ // СТУДЕНТ</h2>
                <form id="student-form">
                    <input type="text" id="student-name" data-lang-key-placeholder="phName" placeholder="[NICKNAME/ИМЯ]" required class="app-input">
                    <input type="number" id="student-course" data-lang-key-placeholder="phCourse" placeholder="[COURSE/КУРС (1-5)]" min="1" max="5" required class="app-input">
                    <select id="student-specialization" class="app-input">
                        <option value="Front-end" data-lang-key="optFrontend">[FRONT-END / КОД]</option>
                        <option value="Back-end" data-lang-key="optBackend">[BACK-END / СЕРВЕР]</option>
                        <option value="Data-Science" data-lang-key="optData">[DATA / БАЗЫ]</option>
                        <option value="Design" data-lang-key="optDesign">[DESIGN / ВИЗУАЛ]</option>
                        <option value="DevOps" data-lang-key="optDevops">[DEVOPS / СЕТЬ]</option>
                    </select>
                    <button type="submit" class="app-btn primary-btn" data-lang-key="btnSave">
                        <i class="fas fa-save"></i> СОХРАНИТЬ
                    </button>
                </form>
            </section>

            <section class="card controls-container">
                <h2 data-lang-key="h2Filter"><i class="fas fa-filter"></i> СИСТЕМА // ПОИСК</h2>
                <input type="text" id="filter-input" data-lang-key-placeholder="phFilter" placeholder="Введите [QUERY] для поиска..." class="app-input">
            </section>

            <section class="card list-container">
                <h2 data-lang-key="h2StudentList"><i class="fas fa-list"></i> ДАННЫЕ // СТУДЕНТЫ</h2>
                <div class="table-responsive">
                    <table id="students-table">
                        <thead>
                            <tr>
                                <th data-lang-key="thId">ID</th>
                                <th data-lang-key="thName">ИМЯ</th>
                                <th data-lang-key="thCourse">КУРС</th>
                                <th data-lang-key="thSpecialization">СПЕЦИАЛИЗАЦИЯ</th>
                                <th data-lang-key="thAction">ДЕЙСТВИЕ</th>
                            </tr>
                        </thead>
                        <tbody>
                            </tbody>
                    </table>
                </div>
            </section>
        </div>
        
        <div id="subjects-view" class="view-section">
            <section class="card">
                <h2 data-lang-key="h2Subjects"><i class="fas fa-book"></i> УЧЕБНЫЕ // ПРЕДМЕТЫ</h2>
                <div class="placeholder-content">
                    <p data-lang-key="placeholderSubjects">Здесь будет система управления учебными курсами и их параметрами. (Секция в разработке)</p>
                </div>
            </section>
        </div>
        
        <div id="teachers-view" class="view-section">
            <section class="card">
                <h2 data-lang-key="h2Teachers"><i class="fas fa-chalkboard-teacher"></i> ПЕРСОНАЛ // ПРЕПОДАВАТЕЛИ</h2>
                <div class="placeholder-content">
                    <p data-lang-key="placeholderTeachers">Здесь будет список преподавателей, их нагрузка и закрепленные курсы. (Секция в разработке)</p>
                </div>
            </section>
        </div>

        <div id="grades-view" class="view-section">
            <section class="card">
                <h2 data-lang-key="h2Grades"><i class="fas fa-graduation-cap"></i> ЖУРНАЛ // ОЦЕНОК</h2>
                <div class="placeholder-content">
                    <p data-lang-key="placeholderGrades">Здесь будет матрица оценок, где можно выставлять баллы студентам по разным предметам. (Секция в разработке)</p>
                </div>
            </section>
        </div>

        <div id="reports-view" class="view-section">
            <section class="card">
                <h2 data-lang-key="h2Reports"><i class="fas fa-chart-line"></i> СИСТЕМА // ОТЧЕТОВ</h2>
                <div class="placeholder-content">
                    <p data-lang-key="placeholderReports">Здесь будут графики и отчеты по успеваемости и статистике. (Секция в разработке)</p>
                </div>
            </section>
        </div>
        
        <div id="profile-view" class="view-section">
            <section class="card profile-info-card">
                <h2 data-lang-key="h2YourProfile"><i class="fas fa-id-card"></i> ТВОЙ // ПРОФИЛЬ</h2>
                <div class="profile-display">
                    <p data-lang-key="profileUsername">Никнейм: <span id="profile-name-display" class="app-text-accent"></span></p>
                    <p data-lang-key="profileLocation">Локация: <span id="profile-city-display" class="app-text-accent"></span></p>
                    <p data-lang-key="profileBio">Био: <span id="profile-bio-display" class="app-text-accent"></span></p>
                </div>
            </section>
            
            <section class="card profile-edit-card">
                <h2 data-lang-key="h2EditInfo"><i class="fas fa-edit"></i> РЕДАКТИРОВАТЬ // ИНФО</h2>
                <form id="profile-form">
                    <input type="text" id="profile-name-input" data-lang-key-placeholder="phNewName" placeholder="[NEW NICKNAME]" required class="app-input">
                    <input type="text" id="profile-city-input" data-lang-key-placeholder="phNewLocation" placeholder="[NEW LOCATION]" required class="app-input">
                    <textarea id="profile-bio-input" data-lang-key-placeholder="phNewBio" placeholder="[NEW BIO DATA]" required class="app-input"></textarea>
                    <button type="submit" class="app-btn primary-btn" data-lang-key="btnUpload"><i class="fas fa-upload"></i> ЗАГРУЗИТЬ</button>
                </form>
            </section>
        </div>
        
    </main>

    <script>
        // --- 0. БАЗА ДАННЫХ ЛОКАЛИЗАЦИИ ---
        const languageData = {
            'RU': {
                appTitle: 'Учёт Студентов | EduTrack // FESTIVAL VIBE 🍂',
                headerTitle: 'EduTrack // FESTIVAL VIBE 🍂',
                tabStudents: 'СТУДЕНТЫ',
                tabSubjects: 'ПРЕДМЕТЫ', 
                tabTeachers: 'ПРЕПОДАВАТЕЛИ', 
                tabGrades: 'ОЦЕНКИ',
                tabReports: 'ОТЧЕТЫ',
                tabProfile: 'ПРОФИЛЬ',
                h2AddStudent: 'ДОБАВИТЬ // СТУДЕНТ',
                h2Filter: 'СИСТЕМА // ПОИСК',
                h2StudentList: 'ДАННЫЕ // СТУДЕНТЫ',
                h2YourProfile: 'ТВОЙ // ПРОФИЛЬ',
                h2EditInfo: 'РЕДАКТИРОВАТЬ // ИНФО',
                h2Subjects: 'УЧЕБНЫЕ // ПРЕДМЕТЫ', 
                h2Teachers: 'ПЕРСОНАЛ // ПРЕПОДАВАТЕЛИ', 
                h2Grades: 'ЖУРНАЛ // ОЦЕНОК', 
                h2Reports: 'СИСТЕМА // ОТЧЕТОВ', 
                phName: '[NICKNAME/ИМЯ]',
                phCourse: '[COURSE/КУРС (1-5)]',
                phFilter: 'Введите [QUERY] для поиска...',
                phNewName: '[NEW NICKNAME]',
                phNewLocation: '[NEW LOCATION]',
                phNewBio: '[NEW BIO DATA]',
                optFrontend: '[FRONT-END / КОД]',
                optBackend: '[BACK-END / СЕРВЕР]',
                optData: '[DATA / БАЗЫ]',
                optDesign: '[DESIGN / ВИЗУАЛ]',
                optDevops: '[DEVOPS / СЕТЬ]',
                thId: 'ID',
                thName: 'ИМЯ',
                thCourse: 'КУРС',
                thSpecialization: 'СПЕЦИАЛИЗАЦИЯ',
                thAction: 'ДЕЙСТВИЕ',
                profileUsername: 'Никнейм:',
                profileLocation: 'Локация:',
                profileBio: 'Био:',
                btnSave: 'СОХРАНИТЬ',
                btnUpload: 'ЗАГРУЗИТЬ',
                placeholderSubjects: 'Здесь будет система управления учебными курсами и их параметрами. (Секция в разработке)',
                placeholderTeachers: 'Здесь будет список преподавателей, их нагрузка и закрепленные курсы. (Секция в разработке)',
                placeholderGrades: 'Здесь будет матрица оценок, где можно выставлять баллы студентам по разным предметам. (Секция в разработке)',
                placeholderReports: 'Здесь будут графики и отчеты по успеваемости и статистике. (Секция в разработке)',
                noStudents: '[SYSTEM] Список пуст. Добавьте студентов.',
                alertProfileUpdated: '[NOTIFICATION] Профиль обновлен!',
                alertLangSet: '[NOTIFICATION] Язык установлен на: '
            },
            'EN': {
                appTitle: 'Student Tracking | EduTrack // FESTIVAL VIBE 🍂',
                headerTitle: 'EduTrack // FESTIVAL VIBE 🍂',
                tabStudents: 'STUDENTS',
                tabSubjects: 'SUBJECTS',
                tabTeachers: 'TEACHERS',
                tabGrades: 'GRADES',
                tabReports: 'REPORTS',
                tabProfile: 'PROFILE',
                h2AddStudent: 'ADD // STUDENT',
                h2Filter: 'SYSTEM // SEARCH',
                h2StudentList: 'DATA // STUDENTS',
                h2YourProfile: 'YOUR // PROFILE',
                h2EditInfo: 'EDIT // INFO',
                h2Subjects: 'ACADEMIC // SUBJECTS',
                h2Teachers: 'STAFF // TEACHERS',
                h2Grades: 'GRADE // JOURNAL',
                h2Reports: 'SYSTEM // REPORTS',
                phName: '[NICKNAME/NAME]',
                phCourse: '[COURSE (1-5)]',
                phFilter: 'Enter [QUERY] to search...',
                phNewName: '[NEW NICKNAME]',
                phNewLocation: '[NEW LOCATION]',
                phNewBio: '[NEW BIO DATA]',
                optFrontend: '[FRONT-END / CODE]',
                optBackend: '[BACK-END / SERVER]',
                optData: '[DATA / BASES]',
                optDesign: '[DESIGN / VISUAL]',
                optDevops: '[DEVOPS / NETWORK]',
                thId: 'ID',
                thName: 'NAME',
                thCourse: 'COURSE',
                thSpecialization: 'SPECIALIZATION',
                thAction: 'ACTION',
                profileUsername: 'Nickname:',
                profileLocation: 'Location:',
                profileBio: 'Bio:',
                btnSave: 'SAVE',
                btnUpload: 'UPLOAD',
                placeholderSubjects: 'This section will manage academic courses and their parameters. (Section under development)',
                placeholderTeachers: 'This section will list teachers, their workload, and assigned courses. (Section under development)',
                placeholderGrades: 'This section will feature a grade matrix for assigning scores to students. (Section under development)',
                placeholderReports: 'This section will contain charts and reports on student performance and statistics. (Section under development)',
                noStudents: '[SYSTEM] List is empty. Add students.',
                alertProfileUpdated: '[NOTIFICATION] Profile updated!',
                alertLangSet: '[NOTIFICATION] Language set to: '
            },
            'JP': {
                appTitle: '学生追跡 | EduTrack // フェスティバルバイブ 🍂',
                headerTitle: 'EduTrack // フェスティバルバイブ 🍂',
                tabStudents: '学生',
                tabSubjects: '科目',
                tabTeachers: '先生',
                tabGrades: '成績',
                tabReports: 'レポート',
                tabProfile: 'プロフィール',
                h2AddStudent: '追加 // 学生',
                h2Filter: 'システム // 検索',
                h2StudentList: 'データ // 学生',
                h2YourProfile: 'あなたの // プロフィール',
                h2EditInfo: '編集 // 情報',
                h2Subjects: '学習 // 科目',
                h2Teachers: 'スタッフ // 先生',
                h2Grades: '成績 // ジャーナル',
                h2Reports: 'システム // レポート',
                phName: '[ニックネーム/名前]',
                phCourse: '[コース (1-5)]',
                phFilter: '検索 [QUERY] を入力...',
                phNewName: '[新しいニックネーム]',
                phNewLocation: '[新しい場所]',
                phNewBio: '[新しいバイオデータ]',
                optFrontend: '[フロントエンド / コード]',
                optBackend: '[バックエンド / サーバー]',
                optData: '[データ / ベース]',
                optDesign: '[デザイン / ビジュアル]',
                optDevops: '[デブオプス / ネットワーク]',
                thId: 'ID',
                thName: '名前',
                thCourse: 'コース',
                thSpecialization: '専門分野',
                thAction: 'アクション',
                profileUsername: 'ニックネーム:',
                profileLocation: '場所:',
                profileBio: 'バイオ:',
                btnSave: '保存',
                btnUpload: 'アップロード',
                placeholderSubjects: '学術コースとそのパラメータを管理するためのシステムがここにあります。（開発中のセクション）',
                placeholderTeachers: '教師のリスト、彼らの作業量、および割り当てられたコースがここに表示されます。（開発中のセクション）',
                placeholderGrades: '学生にスコアを割り当てるための成績マトリックスがここにあります。（開発中のセクション）',
                placeholderReports: '学生の成績と統計に関するグラフとレポートがここに表示されます。（開発中のセクション）',
                noStudents: '[システム] リストは空です。学生を追加してください。',
                alertProfileUpdated: '[NOTIFICATION] プロフィールが更新されました！',
                alertLangSet: '[NOTIFICATION] 言語が設定されました: '
            }
        };

        // --- 1. DOM Элементы и UI ---
        const elements = {
            form: document.getElementById('student-form'),
            nameInput: document.getElementById('student-name'),
            courseInput: document.getElementById('student-course'),
            specializationSelect: document.getElementById('student-specialization'),
            filterInput: document.getElementById('filter-input'),
            tableBody: document.querySelector('#students-table tbody')
        };
        
        const uiElements = {
            tabStudents: document.getElementById('tab-students'),
            tabSubjects: document.getElementById('tab-subjects'), 
            tabTeachers: document.getElementById('tab-teachers'), 
            tabGrades: document.getElementById('tab-grades'),     
            tabReports: document.getElementById('tab-reports'),   
            tabProfile: document.getElementById('tab-profile'),

            studentSection: document.getElementById('students-view'),
            subjectsSection: document.getElementById('subjects-view'), 
            teachersSection: document.getElementById('teachers-view'), 
            gradesSection: document.getElementById('grades-view'),     
            reportsSection: document.getElementById('reports-view'),   
            profileSection: document.getElementById('profile-view'),
            
            profileNameDisplay: document.getElementById('profile-name-display'),
            profileCityDisplay: document.getElementById('profile-city-display'),
            profileBioDisplay: document.getElementById('profile-bio-display'),
            profileForm: document.getElementById('profile-form'),
            profileNameInput: document.getElementById('profile-name-input'),
            profileCityInput: document.getElementById('profile-city-input'),
            profileBioInput: document.getElementById('profile-bio-input'),
            langSelector: document.getElementById('lang-selector'),
            themeToggle: document.getElementById('theme-toggle')
        };
        
        const views = {
            'students': { tab: uiElements.tabStudents, section: uiElements.studentSection },
            'subjects': { tab: uiElements.tabSubjects, section: uiElements.subjectsSection },
            'teachers': { tab: uiElements.tabTeachers, section: uiElements.teachersSection },
            'grades': { tab: uiElements.tabGrades, section: uiElements.gradesSection },
            'reports': { tab: uiElements.tabReports, section: uiElements.reportsSection },
            'profile': { tab: uiElements.tabProfile, section: uiElements.profileSection }
        };

        // --- 2. Data Manager (LocalStorage) ---
        let students = [];
        const STORAGE_KEY = 'studentsList';
        const PROFILE_KEY = 'userProfileData';
        const THEME_KEY = 'appTheme';
        
        let userProfile = {
            username: 'Ryu_Hakuno_77',
            city: 'Neo-Tokyo Sector 4',
            bio: 'Data Analyst | Seeking new network connections.',
            language: 'RU' 
        };

        const loadStudents = () => { 
            const storedStudents = localStorage.getItem(STORAGE_KEY);
            students = storedStudents ? JSON.parse(storedStudents) : [];
            return students;
        };
        const saveStudents = () => { localStorage.setItem(STORAGE_KEY, JSON.stringify(students)); };
        const addStudent = (name, course, specialization) => { 
            const newStudent = { id: Date.now(), name: name, course: Number(course), specialization: specialization };
            students.push(newStudent);
            saveStudents();
            return students;
        };
        const removeStudent = (studentId) => { 
            students = students.filter(student => student.id !== studentId);
            saveStudents();
            return students;
        };
        const filterStudents = (searchTerm) => { 
            const term = searchTerm.toLowerCase().trim();
            if (!term) return students;
            return students.filter(student => 
                student.name.toLowerCase().includes(term) ||
                String(student.course).includes(term) ||
                student.specialization.toLowerCase().includes(term)
            );
        };
        const loadProfile = () => { 
            const storedProfile = localStorage.getItem(PROFILE_KEY);
            userProfile = storedProfile ? JSON.parse(storedProfile) : userProfile;
            return userProfile;
        };
        const saveProfile = (newProfile) => { 
            userProfile = { ...userProfile, ...newProfile };
            localStorage.setItem(PROFILE_KEY, JSON.stringify(userProfile));
        };
        const updateLanguage = (lang) => { 
            saveProfile({ language: lang });
            applyLocalization(lang); 
            return userProfile;
        };
        const loadTheme = () => { return localStorage.getItem(THEME_KEY) || 'dark'; };
        const saveTheme = (theme) => { localStorage.setItem(THEME_KEY, theme); };

        // --- 3. UI Renderer Functions и Локализация ---

        const applyLocalization = (lang) => {
            const texts = languageData[lang] || languageData['RU'];
            
            document.querySelectorAll('[data-lang-key]').forEach(el => {
                const key = el.getAttribute('data-lang-key');
                if (texts[key]) {
                    if (el.tagName === 'BUTTON' || el.tagName === 'A' || el.tagName === 'H1') {
                        const icon = el.querySelector('i');
                        el.textContent = texts[key];
                        if (icon) el.prepend(icon);
                    } else if (el.tagName === 'TITLE') {
                        document.title = texts[key];
                    } else if (el.tagName === 'P') {
                        const span = el.querySelector('.app-text-accent');
                        el.textContent = texts[key];
                        if (span) el.appendChild(span);
                    } else {
                        el.textContent = texts[key];
                    }
                }
            });

            document.querySelectorAll('[data-lang-key-placeholder]').forEach(el => {
                const key = el.getAttribute('data-lang-key-placeholder');
                if (texts[key]) {
                    el.placeholder = texts[key];
                }
            });
            
            updateUI(filterStudents(elements.filterInput.value));
        };

        const createStudentRow = (student) => {
            const tr = document.createElement('tr');
            tr.dataset.studentId = student.id;

            tr.innerHTML = `
                <td>${student.id}</td>
                <td>${student.name}</td>
                <td>${student.course}</td>
                <td>${student.specialization}</td>
                <td>
                    <button class="app-btn delete-btn" data-id="${student.id}">
                        <i class="fas fa-trash-alt"></i>
                    </button>
                </td>
            `;
            
            tr.querySelector('.delete-btn').addEventListener('click', (e) => {
                const id = Number(e.currentTarget.dataset.id);
                const updatedStudents = removeStudent(id);
                updateUI(updatedStudents);
            });
            return tr;
        };

        const renderStudentsList = (currentStudents) => {
            const currentLang = uiElements.langSelector.value;
            const noStudentsText = languageData[currentLang]?.noStudents || languageData['RU'].noStudents;
            const isLightTheme = document.body.classList.contains('light-theme');
            const highlightColor = isLightTheme ? 'var(--light-accent)' : 'var(--dark-text)'; 
            
            elements.tableBody.innerHTML = '';
            
            if (currentStudents.length === 0) {
                const tr = document.createElement('tr');
                tr.innerHTML = `<td colspan="5" style="text-align: center; color: ${highlightColor}; transition: color 0.3s;">${noStudentsText}</td>`;
                elements.tableBody.appendChild(tr);
                return;
            }

            currentStudents.forEach(student => {
                const row = createStudentRow(student);
                elements.tableBody.appendChild(row);
            });
        };

        const switchSection = (sectionId) => {
            Object.values(views).forEach(view => {
                view.section.style.display = 'none';
                view.tab.classList.remove('active');
            });

            if (views[sectionId]) {
                views[sectionId].section.style.display = 'block';
                views[sectionId].tab.classList.add('active');
            }
        };

        const renderProfile = (profile) => {
            uiElements.profileNameDisplay.textContent = profile.username;
            uiElements.profileCityDisplay.textContent = profile.city;
            uiElements.profileBioDisplay.textContent = profile.bio;
            
            uiElements.profileNameInput.value = profile.username;
            uiElements.profileCityInput.value = profile.city;
            uiElements.profileBioInput.value = profile.bio;
            
            uiElements.langSelector.value = profile.language;
        };

        // --- 4. App Initialization & Handlers ---

        const updateUI = (studentsToRender) => { renderStudentsList(studentsToRender); };
        
        const handleFormSubmit = (e) => {
            e.preventDefault();
            
            const name = elements.nameInput.value.trim();
            const course = elements.courseInput.value;
            const specialization = elements.specializationSelect.value;
            
            if (name && course) {
                const updatedStudents = addStudent(name, course, specialization);
                updateUI(updatedStudents);
                elements.form.reset();
            }
        };

        const handleFilterInput = () => {
            const searchTerm = elements.filterInput.value;
            const filteredStudents = filterStudents(searchTerm);
            updateUI(filteredStudents);
        };

        const handleProfileSubmit = (e) => {
            e.preventDefault();
            const currentLang = uiElements.langSelector.value;
            const texts = languageData[currentLang] || languageData['RU'];

            const name = uiElements.profileNameInput.value.trim();
            const city = uiElements.profileCityInput.value.trim();
            const bio = uiElements.profileBioInput.value.trim();
            
            const updatedProfile = saveProfile({ username: name, city: city, bio: bio });
            renderProfile(updatedProfile);
            
            alert(texts.alertProfileUpdated);
        };

        const handleLangChange = (e) => {
            const lang = e.target.value;
            const updatedProfile = updateLanguage(lang);
            const texts = languageData[lang] || languageData['RU'];
            renderProfile(updatedProfile);
            alert(texts.alertLangSet + lang);
        };
        
        const handleThemeToggle = () => {
            const currentTheme = loadTheme();
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            
            document.body.className = newTheme + '-theme';
            
            uiElements.themeToggle.innerHTML = newTheme === 'dark' 
                ? '<i class="fas fa-sun"></i>'
                : '<i class="fas fa-moon"></i>';
                
            saveTheme(newTheme);
            updateUI(filterStudents(elements.filterInput.value)); 
        };


        const init = () => {
            // 1. Инициализация профиля и темы
            const initialProfile = loadProfile();
            const initialTheme = loadTheme();
            
            // Установка начальной темы и иконки
            document.body.className = initialTheme + '-theme';
            if (initialTheme === 'dark') {
                 uiElements.themeToggle.innerHTML = '<i class="fas fa-sun"></i>';
            } else {
                 uiElements.themeToggle.innerHTML = '<i class="fas fa-moon"></i>';
            }


            // 2. Инициализация языка и локализация
            renderProfile(initialProfile); 
            applyLocalization(initialProfile.language); 
            
            // 3. Инициализация студентов
            const initialStudents = loadStudents(); 
            updateUI(initialStudents);

            // 4. Подключение обработчиков
            elements.form.addEventListener('submit', handleFormSubmit); 
            elements.filterInput.addEventListener('input', handleFilterInput);
            
            Object.keys(views).forEach(key => {
                views[key].tab.addEventListener('click', () => switchSection(key));
            });
            
            uiElements.profileForm.addEventListener('submit', handleProfileSubmit);
            uiElements.langSelector.addEventListener('change', handleLangChange);
            uiElements.themeToggle.addEventListener('click', handleThemeToggle);

            // 5. Изначально показываем секцию студентов
            switchSection('students');
        };

        init();
    </script>
</body>
</html>




EduTrack — система учёта студентов

Современный веб-интерфейс для управления студентами, предметами, преподавателями и оценками. Поддерживает темы, мультиязычность и модульную структуру.

1. Цель проекта

Создать удобный, адаптивный и визуально выразительный интерфейс, который можно легко интегрировать с серверной частью и использовать в учебных заведениях.

2. Описание проекта

EduTrack предоставляет инструменты для базы студентов:

добавление студентов (имя, курс, специализация);

фильтрация данных;

навигация по модулям: студенты, предметы, преподаватели, оценки, отчёты, профиль;

смена темы оформления (Dark / Festival Light);

мультиязычная поддержка (RU | EN | JP);

адаптивный дизайн.

Приложение реализовано на HTML + CSS, структура готова к подключению JavaScript-логики.

3. Структура проекта
project/
│
├── index.html          # Основной интерфейс EduTrack
├── /assets
│     ├── styles.css    # Стили (или inline CSS)
│     └── scripts.js    # Логика приложения
│
├── /img                # Скриншоты интерфейса
│
├── package.json        # npm-конфигурация
└── README.md           # Текущая документация

4. Скриншоты интерфейса

![интерфейс ](https://github.com/user-attachments/assets/5300ce4a-1e4e-4e92-89dd-9ad1c6230305)


Добавьте изображения в папку /img и вставьте:

https://github.com/shal558/lab15.git


5. Примеры кода
HTML — форма добавления студента
<form id="student-form">
    <input type="text" id="student-name" placeholder="[NICKNAME/ИМЯ]" class="app-input">
    <input type="number" id="student-course" placeholder="[COURSE/КУРС (1-5)]" class="app-input">
    <select id="student-specialization" class="app-input">
        <option value="Front-end">FRONT-E![интерфейс ](https://github.com/user-attachments/assets/1e62ff56-1231-4fd1-91be-47f786fdbc96)
ND</option>
        <option value="Back-end">BACK-END</option>
    </select>
    <button class="app-btn">СОХРАНИТЬ</button>
</form>

CSS — переключение темы
body.light-theme {
    background: var(--light-bg);
    color: var(--light-text);
}

body.dark-theme {
    background: var(--dark-bg);
    color: var(--dark-text);
}

JS — базовый toggler темы
document.getElementById("theme-toggle").onclick = () => {
    document.body.classList.toggle("light-theme");
    document.body.classList.toggle("dark-theme");
};

6. Инструкция по запуску
Установка зависимостей:
npm install

Запуск приложения:
npm start

Запуск тестов:
npm test

7. Ссылка на репозиторий

Укажите вашу:

https://github.com/username/edutrack

8. Выводы

Разработан готовый интерфейс системы “EduTrack”, включающий:

модульную структуру;

формы и таблицы;

поддержку тем;

мультиязычность;

визуальную адаптивность.
