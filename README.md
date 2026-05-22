<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>Anan的英语有声互动阅读特训 (7天多题超级豪华版)</title>
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
    <h1>🇬🇧 英语互动阅读 7天多题超级强化版</h1>
    <div class="subtitle">有趣的故事 · 3-4题深度强化 · 答对触发全屏彩带特效</div>
    
    <div class="notice">
        <strong>💡 挑战指南：</strong>每天完成一个关卡，点击短文听标准发音。题目从3道扩充到了4道，能够帮孩子更牢固地记住单词并练习阅读理解逻辑！
    </div>

    <div class="control-panel">
        <label><strong>🔊 调整英语朗读速度:</strong></label>
        <input type="range" id="rate" min="0.5" max="1.5" value="0.8" step="0.1">
        <span id="rate-value">0.8x (最适合跟读语速)</span>
    </div>

    <div class="day-section day1-theme">
        <div class="day-header"><div class="day-title">🌟 Day 1: Max and His Clever Dog</div><div class="badge-animation">🐶</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Leo is a clever dog. He lives with a young boy named Max in a small town. Every morning, Leo waits by the front door. When Max puts on his shoes, Leo wags his tail happily because he knows it is time for a walk. Today, instead of going to the park, Max takes Leo to a new place. There are many trees, a beautiful lake, and three little ducks swimming quietly. Leo looks at the ducks curiously, but he does not bark. He just sits by the lake and enjoys the warm sunshine with Max.</div>
        
        <div class="question-block" id="d1q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Why does Leo wag his tail happily every morning?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">A. Because he sees three little ducks.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q1')">B. Because he knows it is time for a walk.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q1')">C. Because Max gives him a nice shoe.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到 Leo 看到 Max 穿鞋就知道要去散步了，所以高兴地摇尾巴。</div>
        </div>

        <div class="question-block" id="d1q2">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 2: Where do Max and Leo usually go for a walk on other days?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q2')">A. To the park.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q2')">B. To a school.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q2')">C. To a busy store.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“Today, instead of going to the park...”（今天，而不是去公园），说明平时习惯去公园。</div>
        </div>

        <div class="question-block" id="d1q3">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 3: What does the word "curiously" mean in the story?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q3')">A. In a very angry way.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q3')">B. Wanting to know or see something.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q3')">C. Feeling very tired.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>“curiously” 意思是“好奇地”。看到新见到的鸭子，小狗感到很好奇。</div>
        </div>

        <div class="question-block" id="d1q4">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 4: What is True about Leo when he sees the ducks?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q4')">A. He jumps into the water to chase them.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd1q4')">B. He barks very loudly at them.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd1q4')">C. He stays quiet and sits down by Max.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>最后提到“but he does not bark. He just sits by the lake”（但他没有叫，只是坐在湖边）。</div>
        </div>
    </div>

    <div class="day-section day2-theme">
        <div class="day-header"><div class="day-title">🌟 Day 2: The Secret of the Forest</div><div class="badge-animation">🌳</div></div>
        <div class="story-box" onclick="speak(this.innerText)">Mia loves spending time outdoors. On a sunny afternoon, she walks into a deep forest behind her grandmother's house. The forest is quiet, and the air smells like fresh rain. Suddenly, Mia spots something shiny hidden under a large, old oak tree. She runs closer and discovers a small, wooden box wrapped in a green ribbon. With exciting hands, she opens it slowly. Inside the box, there is a beautiful stone that glows with a soft blue light and a short note that says: "To the person who loves nature." Mia smiles warmly and decides to keep this wonderful secret in her heart.</div>
        
        <div class="question-block" id="d2q1">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 1: Where is the deep forest located?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">A. Next to Mia's school.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q1')">B. Behind her grandmother's house.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q1')">C. Inside a big city park.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>开头明确写到“she walks into a deep forest behind her grandmother's house”。</div>
        </div>

        <div class="question-block" id="d2q2">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 2: What does Mia discover under the large oak tree?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q2')">A. A small wooden box with a ribbon.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q2')">B. A golden key to a house.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q2')">C. A little bird that cannot fly.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中提到“discovers a small, wooden box wrapped in a green ribbon”。</div>
        </div>

        <div class="question-block" id="d2q3">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 3: What is special about the stone inside the box?</div>
            <div class="options-list">
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q3')">A. It is very heavy and dark.</div>
                <div class="option-item" onclick="checkAnswer(this, true, 'd2q3')">B. It glows with a soft blue light.</div>
                <div class="option-item" onclick="checkAnswer(this, false, 'd2q3')">C. It is made of sweet chocolate.</div>
            </div>
            <div class="explanation"><strong>解析：</strong>文中描述石头是“a beautiful stone that glows with a soft blue light”（发着柔和蓝光的漂亮石头）。</div>
        </div>

        <div class="question-block" id="d2q4">
            <div class="question-text" onclick="speak(this.innerText)">❓ Question 4: What does the note in
