<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>Anan的英语有声互动阅读特训 (一周大满贯版)</title>
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
        
        /* ===== 天数大关卡卡片渐变底色 ===== */
        .day-section {
            margin-top: 40px;
            padding: 30px;
            border-radius: 14px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.03);
            transition: transform 0.2s;
        }
        .day-section:hover { transform: translateY(-2px); }
        
        .day1-theme { background: linear-gradient(180deg, #fffdf0 0%, #ffffff 100%); border: 2px solid #fef3c7; }
        .day2-theme { background: linear-gradient(180deg, #f0fdf4 0%, #ffffff 100%); border: 2px solid #bbf7d0; }
        .day3-theme { background: linear-gradient(180deg, #f0f9ff 0%, #ffffff 100%); border: 2px solid #bae6fd; }
        .day4-theme { background: linear-gradient(180deg, #faf5ff 0%, #ffffff 100%); border: 2px solid #e9d5ff; }
        .day5-theme { background: linear-gradient(180deg, #fff7ed 0%, #ffffff 100%); border: 2px solid #ffedd5; }
        .day6-theme { background: linear-gradient(180deg, #f5f3ff 0%, #ffffff 100%); border: 2px solid #ddd6fe; }
        .day7-theme { background: linear-gradient(180deg, #fff1f2 0%, #ffffff 100%); border: 2px solid #fecdd3; }

        .day-header { display: flex; align-items: center; gap: 12px; margin-bottom: 20px; }
        .day-title { color: white; display: inline-block; padding: 6px 20px; border-radius: 20px; font-size: 16px; font-weight: bold; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
        
        .day1-theme .day-title { background-color: #d97706; }
        .day2-theme .day-title { background-color: #16a34a; }
        .day3-theme .day-title { background-color: #2563eb; }
        .day4-theme .day-title { background-color: #7c3aed; }
        .day5-theme .day-title { background-color: #ea580c; }
        .day6-theme .day-title { background-color: #6d28d9; }
        .day7-theme .day-title { background-color: #be123c; }

        .badge-animation { font-size: 28px; animation: float 2.5s ease-in-out infinite; }
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-6px) rotate(5deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

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
        }
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

        .question-block { background: #fff; border: 1px solid #e2e8f0; padding: 22px; border-radius: 10px; margin-bottom: 25px; }
        .question-text { font-size: 16px; font-weight: bold; color: #2d3748; margin-bottom: 15px; cursor: pointer; }
        .question-text:hover { color: #2b6cb0; }
        .options-list { display: flex; flex-direction: column; gap: 10px; }
        .option-item { padding: 12px 18px; border: 1px solid #cbd5e0; border-radius: 8px; cursor: pointer; transition: all 0.2s; font-size: 15px; background-color: #fff; }
        .option-item:hover { background-color: #f7fafc; transform: translateX(3px); }
        
        .option-item.correct { background-color: #dcfce7 !important; border-color: #22c55e !important; color: #14532d !important; font-weight: bold; }
        .option-item.wrong { background-color: #fee2e2 !important; border-color: #ef4444 !important; color: #7f1d1d !important; }
        .explanation { margin-top: 15px; padding: 15px; background-color: #f8fafc; border-left: 4px solid #3b82f6; font-size: 14px; color: #475569; display: none; border-radius: 0 8px 8px 0; }
    </style>
</head>
<body>

<div class="container">
    <h1>🇬🇧 英语互动阅读 7天特训大满贯</h1>
    <div class="subtitle">有趣的故事 · 智能互动答题 · 答对触发缤纷彩带特效</div>
    
    <div class="notice">
        <strong>💡 挑战指南：</strong>每天完成一个关卡，点击短文听标准发音，点击选项答题，答对有彩带雨哦！
    </div>

    <div class="control-panel">
        <label><strong>🔊 调整英语朗读速度:</strong></label>
        <input type="range" id="rate" min="0.5" max="1.5" value="0.8" step="0.1">
        <span id="rate-value">0.8x (最适合五年级跟读听力语速)</span>
    </div>

    <div class="day-section day1-theme">
        <div class="day-header"><div class="day-title">🌟 Day 1: Max and His Clever Dog</div><div class="badge-animation">🐶</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Leo is a clever dog. He lives with a young boy named Max in a small town. Every morning, Leo waits by the front door. When Max puts on his shoes, Leo wags his tail happily because he knows it is time for a walk. Today, instead of going to the park, Max takes Leo to a new place. There are many trees, a beautiful lake, and three little ducks swimming quietly. Leo looks at the ducks curiously, but he does not bark. He just sits by the lake and enjoys the warm sunshine with Max.</div>
        <div class="question-block" id="d1q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Why does Leo wag his tail happily every morning?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">A. Because he sees three little ducks.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q1')">B. Because he knows it is time for a walk.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到 Leo 看到 Max 穿鞋就知道要去散步了，所以高兴地摇尾巴。</div>
        </div>
    </div>

    <div class="day-section day2-theme">
        <div class="day-header"><div class="day-title">🌟 Day 2: The Secret of the Forest</div><div class="badge-animation">🌳</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Mia loves spending time outdoors. On a sunny afternoon, she walks into a deep forest behind her grandmother's house. The forest is quiet, and the air smells like fresh rain. Suddenly, Mia spots something shiny hidden under a large, old oak tree. She runs closer and discovers a small, wooden box wrapped in a green ribbon. With exciting hands, she opens it slowly. Inside the box, there is a beautiful stone that glows with a soft blue light and a short note that says: "To the person who loves nature."</div>
        <div class="question-block" id="d2q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: What does Mia discover under the large oak tree?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q1')">A. A small wooden box with a ribbon.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">B. A bag full of gold coins.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中明确提到他在老橡树下发现了一个用绿丝带包裹的小木盒。</div>
        </div>
    </div>

    <div class="day-section day3-theme">
        <div class="day-header"><div class="day-title">🌟 Day 3: Ben's Special Star Project</div><div class="badge-animation">🚀</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Ben is eleven years old and loves science very much. This week, his school has a special project about space. Ben decides to make a model of the solar system. He uses colorful paper, small plastic balls, and a lot of silver glue to make the stars shine. His younger sister, Lily, wants to help him, so Ben asks her to paint the planet Mars bright red. They work together at the kitchen table for three evenings. On Friday morning, Ben carries his beautiful project safely to school.</div>
        <div class="question-block" id="d3q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: What subject does Ben love very much?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd3q1')">A. History and Art</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd3q1')">B. Science</div>
            </div>
            <div class="explanation"><strong>解析：</strong>开篇提到“loves science very much”，说明他最喜欢科学课。</div>
        </div>
    </div>

    <div class="day-section day4-theme">
        <div class="day-header"><div class="day-title">🌟 Day 4: The Lost Kitten in the Garden</div><div class="badge-animation">🐱</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Emma was reading a comic book in the garden when she heard a tiny sound. "Meow, meow." She looked behind the big rose bush and found a very small white kitten. It looked scared and its fur was dirty. Emma gently picked it up and brought it some warm milk from the kitchen. The kitten drank the milk fast and started to purr happily. Emma named the kitten "Snowy" because its fur was as white as snow, and her parents allowed her to keep it.</div>
        <div class="question-block" id="d4q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Why did Emma name the kitten "Snowy"?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd4q1')">A. Because its fur was as white as snow.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd4q1')">B. Because she found it on a snowy day.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>最后一句提到，因为小猫的毛像雪一样白（as white as snow），所以起名叫 Snowy。</div>
        </div>
    </div>

    <div class="day-section day5-theme">
        <div class="day-header"><div class="day-title">🌟 Day 5: Grandfather's Magic Pocket Watch</div><div class="badge-animation">⌚</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Tom's grandfather has a beautiful golden pocket watch. It does not use batteries, but needs to be turned with a small key every night. Grandfather tells Tom that this watch is eighty years old and has traveled across many countries. When you put the watch close to your ear, it makes a steady "tick-tock" sound. To Tom, it sounds like a tiny heart beating. Grandfather promises to give this special watch to Tom on his twelfth birthday next year.</div>
        <div class="question-block" id="d5q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: How does the pocket watch get its power to run?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd5q1')">A. It uses a small solar battery.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd5q1')">B. It needs to be turned with a small key every night.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“needs to be turned with a small key every night”，说明这块老怀表每晚需要用小钥匙上弦提供动力。</div>
        </div>
    </div>

    <div class="day-section day6-theme">
        <div class="day-header"><div class="day-title">🌟 Day 6: The Great Pancake Saturday</div><div class="badge-animation">🥞</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Saturday morning is the favorite time for the Taylor family. Every Saturday, they make delicious pancakes together. Mr. Taylor mixes the flour, eggs, and milk in a large bowl. Lily and Sam are responsible for flipping the pancakes in the pan with a plastic tool. Finally, they put sweet honey and fresh strawberries on top. They sit around the dining table, share funny school stories, and enjoy their warm breakfast together.</div>
        <div class="question-block" id="d6q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: What do Lily and Sam do during the cooking process?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd6q1')">A. They mix the flour and eggs in the bowl.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd6q1')">B. They flip the pancakes in the pan.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“Lily and Sam are responsible for flipping the pancakes”，负责在平底锅里翻面。</div>
        </div>
    </div>

    <div class="day-section day7-theme">
        <div class="day-header"><div class="day-title">🌟 Day 7: A Trip to the Science Museum</div><div class="badge-animation">🏛️</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Today, Noah's class went on a field trip to the big Science Museum. There were many cool things to see, but Noah's favorite part was the Robot Zone. He saw a metal robot that could play chess with people and another robot that could draw beautiful pictures in two minutes. Noah even held hands with a small companion robot, and it said "Hello, welcome!" in a funny electronic voice. Noah decided that he wants to be a robot engineer when he grows up.</div>
        <div class="question-block" id="d7q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: What did the robot do when Noah held its hand?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd7q1')">A. It said "Hello, welcome!" to him.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd7q1')">B. It played chess with him quickly.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文末提到当 Noah 握住机器人的手时，机器人用电子音对他说了“Hello, welcome!”。</div>
        </div>
    </div>

</div>

<script>
    const rateInput = document.getElementById('rate');
    const rateValue = document.getElementById('rate-value');
    
    rateInput.addEventListener('input', () => {
        rateValue.textContent = rateInput.value + 'x' + (rateInput.value <= 0.8 ? ' (最适合跟读语速)' : '');
    });

    function speak(text) {
        window.speechSynthesis.cancel(); 
        let cleanText = text.replace("🔊 Click to Listen", ""); 
        const utterance = new SpeechSynthesisUtterance(cleanText);
        utterance.lang = 'en-US'; 
        utterance.rate = parseFloat(rateInput.value); 
        window.speechSynthesis.speak(utterance);
    }

    function celebrate() {
        confetti({ particleCount: 100, spread: 70, origin: { y: 0.6 } });
    }

    function checkAnswer(element, isCorrect, questionId) {
        const questionBlock = document.getElementById(questionId);
        const options = questionBlock.getElementsByClassName('option-item');
        
        for (let option of options) { option.classList.remove('correct', 'wrong'); }
        speak(element.innerText);

        if (isCorrect) {
            element.classList.add('correct');
            celebrate();
        } else {
            element.classList.add('wrong');
            for (let option of options) {
                if (option.getAttribute('onclick').includes('true')) { option.classList.add('correct'); }
            }
        }
        questionBlock.getElementsByClassName('explanation')[0].style.display = 'block';
    }
</script>

</body>
</html>
