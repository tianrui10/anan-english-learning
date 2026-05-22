<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>五年级英语有声互动阅读特训 (动画特效豪华版)</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
            background-color: #f0f4f8;
            color: #2d3748;
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }
        .container {
            max-width: 950px;
            margin: 0 auto;
            background: #fff;
            padding: 35px;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
        }
        h1 {
            color: #2b6cb0;
            text-align: center;
            margin-bottom: 5px;
            font-size: 30px;
            font-weight: 800;
        }
        .subtitle {
            text-align: center;
            color: #718096;
            margin-bottom: 30px;
            font-size: 15px;
        }
        .notice {
            background: linear-gradient(135deg, #ebf8ff 0%, #e6fffa 100%);
            border-left: 5px solid #3182ce;
            padding: 15px 20px;
            margin-bottom: 25px;
            font-size: 14px;
            color: #2b6cb0;
            border-radius: 8px;
            box-shadow: inset 0 1px 3px rgba(0,0,0,0.02);
        }
        .control-panel {
            background: #edf2f7;
            padding: 12px 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 14px;
            position: sticky;
            top: 10px;
            z-index: 100;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }
        
        /* ===== 天数大关卡卡片 (加入专属故事底色) ===== */
        .day-section {
            margin-top: 40px;
            padding: 30px;
            border-radius: 14px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.03);
            transition: transform 0.2s;
        }
        .day-section:hover {
            transform: translateY(-2px);
        }
        
        /* Day 1: 阳光暖黄底色 */
        .day1-theme {
            background: linear-gradient(180deg, #fffdf0 0%, #ffffff 100%);
            border: 2px solid #fef3c7;
        }
        /* Day 2: 神秘森林绿底色 */
        .day2-theme {
            background: linear-gradient(180deg, #f0fdf4 0%, #ffffff 100%);
            border: 2px solid #bbf7d0;
        }
        /* Day 3: 星空科技蓝底色 */
        .day3-theme {
            background: linear-gradient(180deg, #f0f9ff 0%, #ffffff 100%);
            border: 2px solid #bae6fd;
        }

        .day-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
        }
        .day-title {
            color: white;
            display: inline-block;
            padding: 6px 20px;
            border-radius: 20px;
            font-size: 16px;
            font-weight: bold;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .day1-theme .day-title { background-color: #d97706; }
        .day2-theme .day-title { background-color: #16a34a; }
        .day3-theme .day-title { background-color: #2563eb; }

        /* 关卡微型动画徽章 */
        .badge-animation {
            font-size: 28px;
            animation: float 2.5s ease-in-out infinite;
        }
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-6px) rotate(5deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

        /* 文章方框样式 */
        .story-box {
            background-color: rgba(255, 255, 255, 0.9);
            border: 1px solid #e2e8f0;
            padding: 25px;
            border-radius: 10px;
            font-size: 18px;
            color: #1a202c;
            margin-bottom: 30px;
            cursor: pointer;
            transition: all 0.2s;
            position: relative;
            box-shadow: 0 2px 8px rgba(0,0,0,0.02);
        }
        .day1-theme .story-box:hover { background-color: #fffbeb; border-color: #fde68a; }
        .day2-theme .story-box:hover { background-color: #f0fdf4; border-color: #bbf7d0; }
        .day3-theme .story-box:hover { background-color: #f0f9ff; border-color: #bae6fd; }

        .story-box::after {
            content: "🔊 Click to Listen";
            position: absolute;
            bottom: 8px;
            right: 12px;
            font-size: 11px;
            color: #718096;
            background: rgba(0,0,0,0.05);
            padding: 3px 10px;
            border-radius: 20px;
            font-weight: bold;
        }

        /* 题目样式 */
        .question-block {
            background: #fff;
            border: 1px solid #e2e8f0;
            padding: 22px;
            border-radius: 10px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.01);
        }
        .question-text {
            font-size: 16px;
            font-weight: bold;
            color: #2d3748;
            margin-bottom: 15px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .question-text:hover {
            color: #2b6cb0;
        }
        .options-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        .option-item {
            padding: 12px 18px;
            border: 1px solid #cbd5e0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 15px;
            background-color: #fff;
        }
        .option-item:hover {
            background-color: #f7fafc;
            transform: translateX(3px);
        }
        
        /* 答题状态 */
        .option-item.correct {
            background-color: #dcfce7 !important;
            border-color: #22c55e !important;
            color: #14532d !important;
            font-weight: bold;
            box-shadow: 0 0 10px rgba(34, 197, 94, 0.2);
        }
        .option-item.wrong {
            background-color: #fee2e2 !important;
            border-color: #ef4444 !important;
            color: #7f1d1d !important;
        }
        .explanation {
            margin-top: 15px;
            padding: 15px;
            background-color: #f8fafc;
            border-left: 4px solid #3b82f6;
            font-size: 14px;
            color: #475569;
            display: none;
            border-radius: 0 8px 8px 0;
            animation: fadeIn 0.3s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

<div class="container">
    <h1>🇬🇧 五年级英语有声互动阅读特训</h1>
    <div class="subtitle">有趣的故事 · 智能互动答题 · 答对触发缤纷彩带特效</div>
    
    <div class="notice">
        <strong>💡 快乐大满贯指南：</strong><br>
        1. 鼠标点击各关卡的<strong>短文方框</strong>，聆听整篇故事的英文标准朗读。<br>
        2. 认真阅读后点击选项，<strong>如果答对了，会有惊喜动画奖励哦！</strong> 答错也不要紧，仔细阅读自动弹出的中文解析。
    </div>

    <div class="control-panel">
        <label><strong>🔊 调整英语朗读速度:</strong></label>
        <input type="range" id="rate" min="0.5" max="1.5" value="0.8" step="0.1">
        <span id="rate-value">0.8x (最适合五年级跟读听力语速)</span>
    </div>

    <div class="day-section day1-theme">
        <div class="day-header">
            <div class="day-title">🌟 Day 1: Max and His Clever Dog</div>
            <div class="badge-animation">🐶</div>
        </div>
        <div class="story-box" onclick="speak(this.innerText)">
Leo is a clever dog. He lives with a young boy named Max in a small town. Every morning, Leo waits by the front door. When Max puts on his shoes, Leo wags his tail happily because he knows it is time for a walk. Today, instead of going to the park, Max takes Leo to a new place. There are many trees, a beautiful lake, and three little ducks swimming quietly. Leo looks at the ducks curiously, but he does not bark. He just sits by the lake and enjoys the warm sunshine with Max.
        </div>

        <div class="question-block" id="d1q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Why does Leo wag his tail happily every morning?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">A. Because he sees three little ducks.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q1')">B. Because he knows it is time for a walk.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">C. Because Max gives him a nice shoe.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">D. Because he wants to sleep in the sun.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中明确提到 Leo 看到 Max 穿鞋就知道要去散步了，所以高兴地摇尾巴（wags his tail happily because he knows it is time for a walk）。</div>
        </div>

        <div class="question-block" id="d1q2">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 2: Based on the story, where do Max and Leo usually go for a walk?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q2')">A. To a big school</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q2')">B. To the park</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q2')">C. To a shoe shop</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q2')">D. To a small forest</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“Today, instead of going to the park...”，这里的 instead of 意为“代替/而不是”，说明他们平时通常是去公园（park）的。</div>
        </div>
    </div>


    <div class="day-section day2-theme">
        <div class="day-header">
            <div class="day-title">🌟 Day 2: The Secret of the Forest</div>
            <div class="badge-animation">🌳</div>
        </div>
        <div class="story-box" onclick="speak(this.innerText)">
Mia loves spending time outdoors. On a sunny afternoon, she walks into a deep forest behind her grandmother's house. The forest is quiet, and the air smells like fresh rain. Suddenly, Mia spots something shiny hidden under a large, old oak tree. She runs closer and discovers a small, wooden box wrapped in a green ribbon. With exciting hands, she opens it slowly. Inside the box, there is no gold or silver, but a beautiful stone that glows with a soft blue light and a short note that says: "To the person who loves nature." Mia smiles warmly and decides to keep this wonderful secret in her heart.
        </div>

        <div class="question-block" id="d2q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Where is the deep forest located?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">A. Next to Mia's school.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">B. In the middle of a big city.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q1')">C. Behind her grandmother's house.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">D. Far away on a high mountain.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文章开头提到“she walks into a deep forest behind her grandmother's house”，说明森林就在外婆/奶奶家房子后面。</div>
        </div>

        <div class="question-block" id="d2q2">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 2: What does Mia discover under the large oak tree?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q2')">A. A small wooden box with a ribbon.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q2')">B. A little bird that cannot fly.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q2')">C. A bag full of gold coins.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q2')">D. A lost key to her house.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到她在树下发现了一个用绿丝带包裹的小木盒（discovers a small, wooden box wrapped in a green ribbon）。</div>
        </div>
    </div>


    <div class="day-section day3-theme">
        <div class="day-header">
            <div class="day-title">🌟 Day 3: Ben's Special Star Project</div>
            <div class="badge-animation">🚀</div>
        </div>
        <div class="story-box" onclick="speak(this.innerText)">
Ben is eleven years old and loves science very much. This week, his school has a special project about space. Ben decides to make a model of the solar system. He uses colorful paper, small plastic balls, and a lot of silver glue to make the stars shine. His younger sister, Lily, wants to help him, so Ben asks her to paint the planet Mars bright red. They work together at the kitchen table for three evenings. On Friday morning, Ben carries his beautiful project safely to school. His teacher is very proud of his hard work and gives him a big shiny gold star on his homework book.
        </div>

        <div class="question-block" id="d3q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: What subject does Ben love very much?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q1')">A. History</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q1')">B. Art and Music</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd3q1')">C. Science</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q1')">D. German language</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“loves science very much”，说明他非常喜欢科学课。</div>
        </div>

        <div class="question-block" id="d3q2">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 2: What reward did Ben get from his teacher?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q2')">A. A book about space animals.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q2')">B. A box of new chocolate.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd3q2')">C. A big shiny gold star on his homework book.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q2')">D. A beautiful red ball.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文章最后一句写道，老师在全班面前表扬了他，并在他的作业本上奖励了一颗亮晶晶的大金色五角星（gives him a big shiny gold star on his homework book）。</div>
        </div>
    </div>

</div>

<script>
    const rateInput = document.getElementById('rate');
    const rateValue = document.getElementById('rate-value');
    
    rateInput.addEventListener('input', () => {
        rateValue.textContent = rateInput.value + 'x' + (rateInput.value <= 0.8 ? ' (最适合五年级跟读听力语速)' : '');
    });

    function speak(text) {
        window.speechSynthesis.cancel(); 
        let cleanText = text.replace("🔊 Click to Listen", ""); 
        const utterance = new SpeechSynthesisUtterance(cleanText);
        utterance.lang = 'en-US'; 
        utterance.rate = parseFloat(rateInput.value); 
        window.speechSynthesis.speak(utterance);
    }

    // 庆祝撒花动画效果
    function celebrate() {
        confetti({
            particleCount: 100,
            spread: 70,
            origin: { y: 0.6 }
        });
    }

    function checkAnswer(element, isCorrect, questionId) {
        const questionBlock = document.getElementById(questionId);
        const options = questionBlock.getElementsByClassName('option-item');
        
        for (let option of options) {
            option.classList.remove('correct', 'wrong');
        }
        
        speak(element.innerText);

        if (isCorrect) {
            element.classList.add('correct');
            celebrate(); // 触发全屏撒花！
        } else {
            element.classList.add('wrong');
            for (let option of options) {
                if (option.getAttribute('onclick').includes('true')) {
                    option.classList.add('correct');
                }
            }
        }
        
        const exp = questionBlock.getElementsByClassName('explanation')[0];
        exp.style.display = 'block';
    }
</script>

</body>
</html>
