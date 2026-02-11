[love_story_app.html](https://github.com/user-attachments/files/25224624/love_story_app.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <meta name="theme-color" content="#d63384">
    <title>💝 Love Story - Shaalu 💝</title>
    <link rel="manifest" href="manifest.json">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Helvetica', 'Arial', sans-serif;
            min-height: 100vh;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 25%, #f093fb 50%, #f5576c 75%, #ff6b9d 100%);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            overflow-x: hidden;
            user-select: none;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        /* Splash Screen */
        .splash-screen {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #d63384 0%, #f093fb 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            animation: fadeOut 1s ease 2.5s forwards;
        }

        @keyframes fadeOut {
            to {
                opacity: 0;
                pointer-events: none;
            }
        }

        .app-logo {
            width: 150px;
            height: 150px;
            background: white;
            border-radius: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5em;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
            animation: bounce 1s ease infinite;
            margin-bottom: 30px;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        .app-name {
            color: white;
            font-size: 2.5em;
            font-weight: 700;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .app-tagline {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.2em;
            font-weight: 300;
        }

        .loading-spinner {
            margin-top: 40px;
            width: 50px;
            height: 50px;
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-top: 4px solid white;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Main App */
        .hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .heart {
            position: absolute;
            font-size: 20px;
            animation: float 10s infinite;
            opacity: 0.6;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        .app-header {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            height: 70px;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(20px);
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            z-index: 100;
        }

        .app-header-logo {
            width: 45px;
            height: 45px;
            background: linear-gradient(135deg, #d63384 0%, #f093fb 100%);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8em;
            margin-right: 15px;
        }

        .app-header-title {
            font-size: 1.4em;
            font-weight: 700;
            color: #d63384;
        }

        .container {
            position: relative;
            z-index: 2;
            max-width: 500px;
            margin: 0 auto;
            padding: 90px 20px 100px 20px;
            min-height: 100vh;
        }

        .game-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 25px;
            padding: 30px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            animation: slideUp 0.5s ease-out;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .header {
            text-align: center;
            margin-bottom: 25px;
        }

        .header h1 {
            color: #d63384;
            font-size: 2em;
            margin-bottom: 10px;
        }

        .header p {
            color: #666;
            font-size: 1.1em;
            font-style: italic;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: #f0f0f0;
            border-radius: 10px;
            margin-bottom: 25px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #d63384 0%, #f093fb 100%);
            border-radius: 10px;
            transition: width 0.5s ease;
        }

        .question-section {
            margin: 20px 0;
        }

        .question {
            font-size: 1.3em;
            color: #333;
            margin-bottom: 20px;
            font-weight: 600;
            text-align: center;
            line-height: 1.4;
        }

        .emoji-options {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin: 20px 0;
        }

        .emoji-option {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border: 3px solid transparent;
            border-radius: 15px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-align: center;
            font-size: 1em;
            min-height: 110px;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .emoji-option:active {
            transform: scale(0.95);
        }

        .emoji-option.selected {
            background: linear-gradient(135deg, #d63384 0%, #f093fb 100%);
            color: white;
            border-color: #fff;
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(214, 51, 132, 0.4);
        }

        .emoji-option .emoji {
            font-size: 2.5em;
            margin-bottom: 8px;
            display: block;
        }

        .text-input {
            width: 100%;
            padding: 18px;
            border: 3px solid #ffecd2;
            border-radius: 15px;
            font-size: 1.1em;
            font-family: inherit;
            transition: all 0.3s ease;
            resize: vertical;
            min-height: 100px;
        }

        .text-input:focus {
            outline: none;
            border-color: #d63384;
            box-shadow: 0 0 20px rgba(214, 51, 132, 0.2);
        }

        .btn {
            background: linear-gradient(135deg, #d63384 0%, #f093fb 100%);
            color: white;
            border: none;
            padding: 16px 40px;
            font-size: 1.2em;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: block;
            margin: 30px auto;
            font-weight: 600;
            box-shadow: 0 8px 25px rgba(214, 51, 132, 0.4);
            width: 100%;
            max-width: 300px;
        }

        .btn:active {
            transform: scale(0.95);
        }

        .final-proposal {
            text-align: center;
        }

        .final-proposal h2 {
            color: #d63384;
            font-size: 1.8em;
            margin-bottom: 20px;
        }

        .final-proposal .summary {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 30%);
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
            text-align: left;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
        }

        .summary-item {
            margin: 12px 0;
            color: #333;
            font-size: 1em;
            line-height: 1.5;
            padding: 10px;
            background: rgba(255, 255, 255, 0.6);
            border-radius: 10px;
        }

        .big-question {
            font-size: 2em;
            font-weight: 900;
            color: #d63384;
            margin: 30px 0 25px 0;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 2px 2px 4px rgba(214, 51, 132, 0.3);
            animation: heartbeat 1.5s infinite;
            line-height: 1.3;
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(1); }
            10%, 30% { transform: scale(1.08); }
            20%, 40% { transform: scale(1); }
        }

        .yes-no-container {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 30px;
        }

        .answer-btn {
            padding: 22px 40px;
            font-size: 2em;
            font-weight: 900;
            border-radius: 20px;
            border: 4px solid;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 4px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            width: 100%;
        }

        .answer-btn:active {
            transform: scale(0.95);
        }

        .yes-btn {
            background: linear-gradient(135deg, #11998e 0%, #38ef7d 100%);
            color: white;
            border-color: #0d7569;
        }

        .no-btn {
            background: linear-gradient(135deg, #ee0979 0%, #ff6a00 100%);
            color: white;
            border-color: #c70763;
        }

        .celebration {
            display: none;
            text-align: center;
        }

        .celebration h2 {
            color: #11998e;
            font-size: 2.2em;
            margin-bottom: 20px;
            animation: bounce 1s infinite;
        }

        .music-control {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 50%;
            width: 60px;
            height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
            z-index: 1000;
            transition: all 0.3s ease;
            border: 3px solid #d63384;
        }

        .music-control:active {
            transform: scale(0.9);
        }

        .music-control span {
            font-size: 1.8em;
        }

        @media (min-width: 768px) {
            .app-logo {
                width: 180px;
                height: 180px;
                font-size: 6em;
            }

            .emoji-options {
                grid-template-columns: repeat(3, 1fr);
            }

            .big-question {
                font-size: 2.8em;
            }

            .yes-no-container {
                flex-direction: row;
                gap: 20px;
            }

            .answer-btn {
                font-size: 2.5em;
            }
        }
    </style>
</head>
<body>
    <!-- Splash Screen -->
    <div class="splash-screen" id="splashScreen">
        <div class="app-logo">💝</div>
        <div class="app-name">Love Story</div>
        <div class="app-tagline">For Shaalu Rajput</div>
        <div class="loading-spinner"></div>
    </div>

    <!-- App Header -->
    <div class="app-header">
        <div class="app-header-logo">💝</div>
        <div class="app-header-title">Love Story</div>
    </div>

    <div class="hearts" id="hearts"></div>
    
    <div class="music-control" id="musicControl" title="Music">
        <span id="musicIcon">🎵</span>
    </div>

    <div class="container">
        <div class="game-card">
            <div class="header">
                <h1>💝 For Shaalu Rajput 💝</h1>
                <p>A Valentine's Journey</p>
            </div>

            <div class="progress-bar">
                <div class="progress-fill" id="progressFill"></div>
            </div>

            <div id="gameContent">
                <!-- Questions will be inserted here -->
            </div>
        </div>
    </div>

    <audio id="bgMusic" loop>
        <source src="data:audio/mpeg;base64,SUQzBAAAAAAAI1RTU0UAAAAPAAADTGF2ZjU4Ljc2LjEwMAAAAAAAAAAAAAAA//tQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAWGluZwAAAA8AAAACAAADhAC7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7u7v////////////////////////////////////////////////////////////////AAAAATGF2YzU4LjEzAAAAAAAAAAAAAAAAJAAAAAAAAAAAA4T0A+BSAAAAAAAAAAAAAAAAAAAA//sQZAAP8AAAaQAAAAgAAA0gAAABAAABpAAAACAAADSAAAAETEFNRTMuMTAwVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV//sQZEYP8AAAaQAAAAgAAA0gAAABAAABpAAAACAAADSAAAAEVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV" type="audio/mpeg">
    </audio>

    <script>
        const questions = [
            {
                type: 'emoji-select',
                question: '🌸 What makes Shaalu\'s heart smile?',
                emojis: [
                    { emoji: '📚', label: 'Books' },
                    { emoji: '🎵', label: 'Music' },
                    { emoji: '🎨', label: 'Art' },
                    { emoji: '🍕', label: 'Food' },
                    { emoji: '🌸', label: 'Nature' },
                    { emoji: '✈️', label: 'Travel' },
                    { emoji: '🎬', label: 'Movies' },
                    { emoji: '💃', label: 'Dancing' },
                    { emoji: '📸', label: 'Photos' },
                    { emoji: '🎮', label: 'Gaming' },
                    { emoji: '☕', label: 'Coffee' },
                    { emoji: '🛍️', label: 'Shopping' }
                ],
                key: 'likes'
            },
            {
                type: 'emoji-select',
                question: '🙅‍♀️ What does Shaalu prefer to avoid?',
                emojis: [
                    { emoji: '🕷️', label: 'Bugs' },
                    { emoji: '😡', label: 'Rude People' },
                    { emoji: '🥦', label: 'Certain Foods' },
                    { emoji: '⏰', label: 'Being Late' },
                    { emoji: '🗣️', label: 'Loud Noises' },
                    { emoji: '❄️', label: 'Cold Weather' },
                    { emoji: '😴', label: 'Boring Things' },
                    { emoji: '📱', label: 'Too Much Screen' },
                    { emoji: '🚗', label: 'Traffic' },
                    { emoji: '💤', label: 'Early Mornings' },
                    { emoji: '😰', label: 'Stress' },
                    { emoji: '🎭', label: 'Fake People' }
                ],
                key: 'dislikes'
            },
            {
                type: 'emoji-select',
                question: '✈️ Where does Shaalu dream of going?',
                emojis: [
                    { emoji: '🗼', label: 'Paris' },
                    { emoji: '🗽', label: 'New York' },
                    { emoji: '🏔️', label: 'Switzerland' },
                    { emoji: '🏝️', label: 'Maldives' },
                    { emoji: '🏯', label: 'Japan' },
                    { emoji: '🕌', label: 'Dubai' },
                    { emoji: '🏛️', label: 'Greece' },
                    { emoji: '🏖️', label: 'Beach' },
                    { emoji: '🏰', label: 'Castles' },
                    { emoji: '🌄', label: 'Mountains' },
                    { emoji: '🌊', label: 'Islands' },
                    { emoji: '🌃', label: 'City Lights' }
                ],
                key: 'dreamDestination'
            },
            {
                type: 'emoji-select',
                question: '😊 What brings joy to Shaalu?',
                emojis: [
                    { emoji: '👨‍👩‍👧‍👦', label: 'Family' },
                    { emoji: '👯‍♀️', label: 'Friends' },
                    { emoji: '🎁', label: 'Surprises' },
                    { emoji: '💌', label: 'Messages' },
                    { emoji: '🌅', label: 'Sunsets' },
                    { emoji: '🎂', label: 'Celebrations' },
                    { emoji: '💪', label: 'Achievements' },
                    { emoji: '🤗', label: 'Hugs' },
                    { emoji: '🌟', label: 'Dreams' },
                    { emoji: '🎉', label: 'Adventures' },
                    { emoji: '💝', label: 'Love' },
                    { emoji: '🕊️', label: 'Peace' }
                ],
                key: 'happiness'
            },
            {
                type: 'emoji-select',
                question: '🎭 What\'s Shaalu\'s personality?',
                emojis: [
                    { emoji: '😊', label: 'Cheerful' },
                    { emoji: '🤔', label: 'Thoughtful' },
                    { emoji: '😎', label: 'Confident' },
                    { emoji: '🥰', label: 'Caring' },
                    { emoji: '😂', label: 'Funny' },
                    { emoji: '🌟', label: 'Ambitious' },
                    { emoji: '💭', label: 'Creative' },
                    { emoji: '🔥', label: 'Passionate' },
                    { emoji: '🦋', label: 'Free-Spirited' },
                    { emoji: '📖', label: 'Wise' },
                    { emoji: '💫', label: 'Unique' },
                    { emoji: '🌈', label: 'Positive' }
                ],
                key: 'personality'
            },
            {
                type: 'emoji-select',
                question: '🎨 What are Shaalu\'s hobbies?',
                emojis: [
                    { emoji: '✍️', label: 'Writing' },
                    { emoji: '🎤', label: 'Singing' },
                    { emoji: '🏃‍♀️', label: 'Fitness' },
                    { emoji: '🧘‍♀️', label: 'Yoga' },
                    { emoji: '🍳', label: 'Cooking' },
                    { emoji: '🎸', label: 'Music' },
                    { emoji: '💅', label: 'Self-Care' },
                    { emoji: '🌱', label: 'Gardening' },
                    { emoji: '🐕', label: 'Pets' },
                    { emoji: '🎯', label: 'Goals' },
                    { emoji: '🎨', label: 'Crafts' },
                    { emoji: '📺', label: 'Netflix' }
                ],
                key: 'hobbies'
            },
            {
                type: 'emoji-select',
                question: '💭 What matters most to Shaalu?',
                emojis: [
                    { emoji: '❤️', label: 'Love' },
                    { emoji: '👨‍👩‍👧‍👦', label: 'Family' },
                    { emoji: '🎓', label: 'Growth' },
                    { emoji: '💼', label: 'Career' },
                    { emoji: '😊', label: 'Happiness' },
                    { emoji: '🙏', label: 'Faith' },
                    { emoji: '🤝', label: 'Friendship' },
                    { emoji: '💰', label: 'Security' },
                    { emoji: '🌍', label: 'Impact' },
                    { emoji: '🎯', label: 'Goals' },
                    { emoji: '🧠', label: 'Health' },
                    { emoji: '⚖️', label: 'Balance' }
                ],
                key: 'values'
            },
            {
                type: 'text',
                question: '💭 What would you like me to know about you, Shaalu?',
                placeholder: 'Share your thoughts, dreams, anything... ✨',
                key: 'aboutHer'
            },
            {
                type: 'text',
                question: '💝 Would you feel comfortable sharing your feelings with me?',
                placeholder: 'Tell me about trust and opening up...',
                key: 'feelings'
            }
        ];

        let currentQuestion = 0;
        let answers = {};
        let musicPlaying = false;
        const bgMusic = document.getElementById('bgMusic');
        const musicControl = document.getElementById('musicControl');
        const musicIcon = document.getElementById('musicIcon');

        // Hide splash screen after loading
        setTimeout(() => {
            document.getElementById('splashScreen').style.display = 'none';
        }, 3000);

        // Create floating hearts
        function createHearts() {
            const heartsContainer = document.getElementById('hearts');
            const heartEmojis = ['❤️', '💕', '💖', '💗', '💝', '💘', '💓', '💞'];
            
            for (let i = 0; i < 20; i++) {
                const heart = document.createElement('div');
                heart.className = 'heart';
                heart.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.animationDelay = Math.random() * 10 + 's';
                heart.style.animationDuration = (Math.random() * 5 + 8) + 's';
                heart.style.fontSize = (Math.random() * 10 + 15) + 'px';
                heartsContainer.appendChild(heart);
            }
        }

        // Music control
        musicControl.addEventListener('click', () => {
            if (musicPlaying) {
                bgMusic.pause();
                musicIcon.textContent = '🔇';
                musicPlaying = false;
            } else {
                bgMusic.play().catch(e => console.log('Music play failed:', e));
                musicIcon.textContent = '🎵';
                musicPlaying = true;
            }
        });

        // Auto-play music on first interaction
        document.addEventListener('click', () => {
            if (!musicPlaying) {
                bgMusic.play().catch(e => console.log('Music play failed:', e));
                musicIcon.textContent = '🎵';
                musicPlaying = true;
            }
        }, { once: true });

        function updateProgress() {
            const progress = ((currentQuestion + 1) / (questions.length + 1)) * 100;
            document.getElementById('progressFill').style.width = progress + '%';
        }

        function renderQuestion() {
            const gameContent = document.getElementById('gameContent');
            const question = questions[currentQuestion];

            let html = `
                <div class="question-section">
                    <div class="question">${question.question}</div>
            `;

            if (question.type === 'emoji-select') {
                html += '<div class="emoji-options">';
                question.emojis.forEach((item, index) => {
                    html += `
                        <div class="emoji-option" onclick="selectEmoji(${index})">
                            <span class="emoji">${item.emoji}</span>
                            <div>${item.label}</div>
                        </div>
                    `;
                });
                html += '</div>';
            } else if (question.type === 'text') {
                html += `
                    <textarea class="text-input" id="textAnswer" placeholder="${question.placeholder}"></textarea>
                `;
            }

            html += `
                    <button class="btn" onclick="nextQuestion()">Continue 💕</button>
                </div>
            `;

            gameContent.innerHTML = html;
            updateProgress();
        }

        function selectEmoji(index) {
            const question = questions[currentQuestion];
            const options = document.querySelectorAll('.emoji-option');
            
            options[index].classList.toggle('selected');
            
            const selected = [];
            options.forEach((option, i) => {
                if (option.classList.contains('selected')) {
                    selected.push(question.emojis[i].label);
                }
            });
            
            answers[question.key] = selected;
        }

        function nextQuestion() {
            const question = questions[currentQuestion];
            
            if (question.type === 'text') {
                const textAnswer = document.getElementById('textAnswer').value.trim();
                if (!textAnswer) {
                    alert('Please share your thoughts 💕');
                    return;
                }
                answers[question.key] = textAnswer;
            } else if (!answers[question.key] || answers[question.key].length === 0) {
                alert('Please select at least one option 💕');
                return;
            }

            currentQuestion++;
            
            if (currentQuestion < questions.length) {
                renderQuestion();
            } else {
                showProposal();
            }
        }

        function showProposal() {
            updateProgress();
            const gameContent = document.getElementById('gameContent');
            
            let summaryHTML = '';
            
            if (answers.likes && answers.likes.length > 0) {
                summaryHTML += `<div class="summary-item">💖 <strong>Happy:</strong> ${answers.likes.join(', ')}</div>`;
            }
            
            if (answers.dislikes && answers.dislikes.length > 0) {
                summaryHTML += `<div class="summary-item">🙅‍♀️ <strong>Avoid:</strong> ${answers.dislikes.join(', ')}</div>`;
            }
            
            if (answers.dreamDestination && answers.dreamDestination.length > 0) {
                summaryHTML += `<div class="summary-item">✈️ <strong>Dreams:</strong> ${answers.dreamDestination.join(', ')}</div>`;
            }
            
            if (answers.happiness && answers.happiness.length > 0) {
                summaryHTML += `<div class="summary-item">😊 <strong>Joy:</strong> ${answers.happiness.join(', ')}</div>`;
            }

            if (answers.personality && answers.personality.length > 0) {
                summaryHTML += `<div class="summary-item">🎭 <strong>You:</strong> ${answers.personality.join(', ')}</div>`;
            }

            if (answers.hobbies && answers.hobbies.length > 0) {
                summaryHTML += `<div class="summary-item">🎨 <strong>Hobbies:</strong> ${answers.hobbies.join(', ')}</div>`;
            }

            if (answers.values && answers.values.length > 0) {
                summaryHTML += `<div class="summary-item">💭 <strong>Values:</strong> ${answers.values.join(', ')}</div>`;
            }
            
            if (answers.aboutHer) {
                summaryHTML += `<div class="summary-item">💝 <strong>About:</strong> "${answers.aboutHer}"</div>`;
            }

            if (answers.feelings) {
                summaryHTML += `<div class="summary-item">💭 <strong>Trust:</strong> "${answers.feelings}"</div>`;
            }

            gameContent.innerHTML = `
                <div class="final-proposal">
                    <h2>💕 I Know You Now 💕</h2>
                    <div class="summary">
                        ${summaryHTML}
                    </div>
                    <div style="margin: 25px 0; font-size: 1.15em; color: #333; line-height: 1.6;">
                        <p>Every answer touched my heart. 💓</p>
                        <p style="margin-top: 15px;">I want to create memories with you, explore the world together, and be someone you trust.</p>
                        <p style="margin-top: 15px; color: #d63384; font-weight: 600;">You're amazing! 🌟</p>
                    </div>
                    
                    <div class="big-question">
                        Will You Go On A Date With Me?
                    </div>
                    
                    <div class="yes-no-container">
                        <button class="answer-btn yes-btn" onclick="handleResponse('yes')">YES</button>
                        <button class="answer-btn no-btn" onclick="handleResponse('no')">NO</button>
                    </div>
                </div>
            `;
        }

        function handleResponse(response) {
            const gameContent = document.getElementById('gameContent');
            
            if (response === 'yes') {
                gameContent.innerHTML = `
                    <div class="celebration">
                        <h2>🎉 YES! YOU SAID YES! 🎉</h2>
                        <div style="font-size: 4em; margin: 30px 0;">
                            💕💖💗💓💝💘💞
                        </div>
                        <p style="font-size: 1.5em; color: #11998e; margin: 20px 0; font-weight: 600;">
                            Shaalu, you made me SO HAPPY!
                        </p>
                        <p style="font-size: 1.2em; color: #333; margin: 20px 0; line-height: 1.6;">
                            I promise an unforgettable date! 🌹
                        </p>
                        <p style="font-size: 1.1em; color: #d63384; margin: 25px 0; font-weight: 600;">
                            Get ready for amazing times! ✨💫
                        </p>
                        <div style="font-size: 3em; margin-top: 30px;">
                            🥰😍💑
                        </div>
                    </div>
                `;
                document.querySelector('.celebration').style.display = 'block';
                
                // Heart explosion
                for (let i = 0; i < 80; i++) {
                    setTimeout(() => {
                        const heart = document.createElement('div');
                        const hearts = ['❤️', '💕', '💖', '💗', '💝', '💘', '💓', '💞'];
                        heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                        heart.style.position = 'fixed';
                        heart.style.left = Math.random() * 100 + '%';
                        heart.style.top = Math.random() * 100 + '%';
                        heart.style.fontSize = (Math.random() * 25 + 20) + 'px';
                        heart.style.zIndex = '9999';
                        heart.style.animation = 'float 4s ease-out forwards';
                        heart.style.pointerEvents = 'none';
                        document.body.appendChild(heart);
                        setTimeout(() => heart.remove(), 4000);
                    }, i * 30);
                }
            } else {
                gameContent.innerHTML = `
                    <div class="final-proposal">
                        <h2 style="color: #666;">💭 I Understand</h2>
                        <div style="font-size: 3em; margin: 20px 0; opacity: 0.7;">
                            😔💔
                        </div>
                        <p style="font-size: 1.2em; color: #666; margin: 20px 0; line-height: 1.6;">
                            That's okay. I appreciate your honesty. 💕
                        </p>
                        <p style="font-size: 1.1em; color: #666; margin: 20px 0; line-height: 1.5;">
                            Take your time. I'll be here with an open heart. 🌸
                        </p>
                        <p style="font-size: 1em; color: #999; margin: 20px 0;">
                            No pressure - just hope. 💫
                        </p>
                    </div>
                `;
            }
        }

        // Initialize
        createHearts();
        renderQuestion();
    </script>
</body>
</html>
