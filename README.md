<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>全家多语言互动学习中心 (德语宝典 + 英语7天多题强化版)</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
            background-color: #f4f6f9;
            color: #333;
            margin: 0;
            padding: 20px;
            line-height: 1.6;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: #fff;
            padding: 35px;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
        }
        
        /* ===== 顶部分语言切换导航大厅 ===== */
        .language-switcher {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 35px;
            background: #edf2f7;
            padding: 10px;
            border-radius: 12px;
        }
        .switch-btn {
            flex: 1;
            padding: 15px 20px;
            font-size: 18px;
            font-weight: bold;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        .btn-de { background-color: #e2e8f0; color: #4a5568; }
        .btn-en { background-color: #e2e8f0; color: #4a5568; }
        .switch-btn.active-de { background-color: #ffb900; color: #000; box-shadow: 0 4px 12px rgba(255,185,0,0.3); }
        .switch-btn.active-en { background-color: #3182ce; color: #fff; box-shadow: 0 4px 12px rgba(49,130,206,0.3); }

        .lang-section { display: none; }
        .lang-section.active { display: block; animation: fadeIn 0.4s ease-in-out; }

        h1 { text-align: center; margin-bottom: 5px; font-size: 30px; font-weight: 800; color: #1a365d; }
        .subtitle { text-align: center; color: #4a5568; margin-bottom: 25px; font-size: 15px; }
        
        .notice { padding: 15px 20px; margin-bottom: 25px; font-size: 14px; border-radius: 8px; }
        .notice-de { background: #ebf8ff; border-left: 5px solid #3182ce; color: #2b6cb0; }
        .notice-en { background: linear-gradient(135deg, #e6fffa 0%, #ebf8ff 100%); border-left: 5px solid #23c55e; color: #14532d; }
        
        .control-panel {
            background: #edf2f7; padding: 15px; border-radius: 6px; margin-bottom: 25px;
            display: flex; align-items: center; gap: 15px; font-size: 14px; position: sticky; top: 10px; z-index: 100; box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }
        
        /* 德语专业表格样式 */
        h2 { color: #2c5282; margin-top: 40px; border-left: 5px solid #4299e1; padding-left: 12px; }
        table { width: 100%; border-collapse: collapse; margin-bottom: 25px; background: #fff; }
        th, td { border: 1px solid #e2e8f0; padding: 12px; text-align: left; vertical-align: top; }
        th { background-color: #ebf8ff; color: #2d3748; font-weight: bold; }
        
        .speakable { cursor: pointer; color: #2b6cb0; font-weight: bold; display: inline-block; padding: 2px 6px; border-radius: 4px; transition: all 0.2s; }
        .speakable:hover { background-color: #bee3f8; color: #1a365d; text-decoration: underline; }
        
        .word-grid { display: grid; grid-template-columns: 1fr; gap: 6px; }
        .sentence-box { margin-bottom: 12px; padding-bottom: 8px; border-bottom: 1px dashed #edf2f7; }
        .sentence-box:last-child { border-bottom: none; }
        .translation { color: #718096; font-size: 13px; display: block; margin-top: 2px; font-weight: normal; }
        .letter-cell { text-align: center; font-size: 26px; font-weight: bold; color: #2b6cb0; background-color: #fafauto; }

        /* 英语卡片样式 */
        .day-section { margin-top: 35px; padding: 30px; border-radius: 14px; box-shadow: 0 4px 15px rgba(0,0,0,0.03); }
        .day1-theme { background: linear-gradient(180deg, #fffdf0 0%, #ffffff 100%); border: 2px solid #fef3c7; }
        .day2-theme { background: linear-gradient(180deg, #f0fdf4 0%, #ffffff 100%); border: 2px solid #bbf7d0; }
        .day3-theme { background: linear-gradient(180deg, #f0f9ff 0%, #ffffff 100%); border: 2px solid #bae6fd; }
        .day4-theme { background: linear-gradient(180deg, #faf5ff 0%, #ffffff 100%); border: 2px solid #e9d5ff; }
        .day5-theme { background: linear-gradient(180deg, #fff7ed 0%, #ffffff 100%); border: 2px solid #ffedd5; }
        .day6-theme { background: linear-gradient(180deg, #f5f3ff 0%, #ffffff 100%); border: 2px solid #ddd6fe; }
        .day7-theme { background: linear-gradient(180deg, #fff1f2 0%, #ffffff 100%); border: 2px solid #fecdd3; }
        .day-header { display: flex; align-items: center; gap: 12px; margin-bottom: 20px; }
        .day-title { color: white; display: inline-block; padding: 6px 20px; border-radius: 20px; font-size: 16px; font-weight: bold; }
        .day1-theme .day-title { background-color: #d97706; }
        .day2-theme .day-title { background-color: #16a34a; }
        .day3-theme .day-title { background-color: #2563eb; }
        .day4-theme .day-title { background-color: #7c3aed; }
        .day5-theme .day-title { background-color: #ea580c; }
        .day6-theme .day-title { background-color: #6d28d9; }
        .day7-theme .day-title { background-color: #be123c; }
        .badge-animation { font-size: 28px; animation: float 2.5s ease-in-out infinite; }
        @keyframes float { 0% { transform: translateY(0px) rotate(0deg); } 50% { transform: translateY(-6px) rotate(5deg); } 100% { transform: translateY(0px) rotate(0deg); } }
        
        .story-box { background-color: rgba(255, 255, 255, 0.9); border: 1px solid #e2e8f0; padding: 25px; border-radius: 10px; font-size: 18px; color: #1a202c; margin-bottom: 30px; cursor: pointer; position: relative; }
        .story-box::after { content: "🔊 Click to Listen / 点击听朗读"; position: absolute; bottom: 8px; right: 12px; font-size: 11px; color: #718096; background: rgba(0,0,0,0.05); padding: 3px 10px; border-radius: 20px; font-weight: bold; }
        
        .question-block { background: #fff; border: 1px solid #e2e8f0; padding: 22px; border-radius: 10px; margin-bottom: 25px; }
        .question-text { font-size: 16px; font-weight: bold; color: #2d3748; margin-bottom: 15px; cursor: pointer; }
        .options-list { display: flex; flex-direction: column; gap: 10px; }
        .option-item { padding: 12px 18px; border: 1px solid #cbd5e0; border-radius: 8px; cursor: pointer; transition: all 0.2s; font-size: 15px; background-color: #fff; }
        .option-item:hover { background-color: #f7fafc; transform: translateX(3px); }
        .option-item.correct { background-color: #dcfce7 !important; border-color: #22c55e !important; color: #14532d !important; font-weight: bold; }
        .option-item.wrong { background-color: #fee2e2 !important; border-color: #ef4444 !important; color: #7f1d1d !important; }
        .explanation { margin-top: 15px; padding: 15px; background-color: #f8fafc; border-left: 4px solid #3b82f6; font-size: 14px; color: #475569; display: none; border-radius: 0 8px 8px 0; }
        
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
    </style>
</head>
<body>

<div class="container">
    
    <div class="language-switcher">
        <button class="switch-btn btn-de active-de" onclick="switchLanguage('de')">🇩🇪 爸爸的德语通关宝典</button>
        <button class="switch-btn btn-en" onclick="switchLanguage('en')">🇬🇧 Anan的英语特训营</button>
    </div>

    <div class="control-panel">
        <label><strong>🔊 智能语速调节器:</strong></label>
        <input type="range" id="rate" min="0.4" max="1.5" value="0.7" step="0.1">
        <span id="rate-value">0.7x (当前推荐模仿语速)</span>
    </div>

    <div id="section-de" class="lang-section active">
        <h1>🇩🇪 德语发音通关宝典 (全套完整互动版)</h1>
        <div class="subtitle">10词10句高强度强化训练 · 点击即可大声朗读</div>
        
        <div class="notice notice-de">
            <strong>💡 完美跟读特训法：</strong> 鼠标直接点击下方的<strong>蓝色单词或整行德语长句</strong>，即可聆听纯正发音。建议先将语速拉慢到 0.7x 模仿基础口型，熟练后调至 1.0x 感受真实的德语语调节奏！
        </div>

        <h2>一、单元音与变元音 (Vokale & Umlaute)</h2>
        <table>
            <thead>
                <tr>
                    <th width="10%">字母</th>
                    <th width="22%">发音核心规律</th>
                    <th width="30%">10个高频强化单词 (点击发音)</th>
                    <th width="38%">10个经典实用句子 (点击发音)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="letter-cell">a</td>
                    <td>长音口张大，舌平放。<br>短音短促有力，干净利落。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Abend')">1. Abend (晚上 - 长)</div>
                            <div class="speakable" onclick="sayDE('Apfel')">2. Apfel (苹果 - 短)</div>
                            <div class="speakable" onclick="sayDE('Name')">3. Name (名字)</div>
                            <div class="speakable" onclick="sayDE('Tag')">4. Tag (白天)</div>
                            <div class="speakable" onclick="sayDE('alt')">5. alt (老的)</div>
                            <div class="speakable" onclick="sayDE('antworten')">6. antworten (回答)</div>
                            <div class="speakable" onclick="sayDE('acht')">7. acht (数字八)</div>
                            <div class="speakable" onclick="sayDE('arbeiten')">8. arbeiten (工作)</div>
                            <div class="speakable" onclick="sayDE('Kaffee')">9. Kaffee (咖啡)</div>
                            <div class="speakable" onclick="sayDE('was')">10. was (什么)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Guten Abend!')">Guten Abend!</span><span class="translation">晚上好！</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Apfel ist süß.')">Der Apfel ist süß.</span><span class="translation">这个苹果很甜。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Mein Name ist Anna.')">Mein Name ist Anna.</span><span class="translation">我的名字叫 Anna。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ein schöner Tag.')">Ein schöner Tag.</span><span class="translation">美好的一天。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Haus ist alt.')">Das Haus ist alt.</span><span class="translation">这栋房子很老。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Bitte antworten Sie mir.')">Bitte antworten Sie mir.</span><span class="translation">请回答我。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Es ist acht Uhr.')">Es ist acht Uhr.</span><span class="translation">现在是八点整。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich arbeite heute.')">Ich arbeite heute.</span><span class="translation">我今天工作。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich trinke Kaffee.')">Ich trinke Kaffee.</span><span class="translation">我喝咖啡。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Was ist das?')">Was ist das?</span><span class="translation">这是什么？</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="letter-cell">e</td>
                    <td>长音嘴角用力向两边咧开。<br>短音开口稍大。<br>词尾不重读时发极轻的“呃”。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Leben')">1. Leben (生活 - 长)</div>
                            <div class="speakable" onclick="sayDE('Bett')">2. Bett (床 - 短)</div>
                            <div class="speakable" onclick="sayDE('bitte')">3. bitte (请 - 弱尾音)</div>
                            <div class="speakable" onclick="sayDE('geben')">4. geben (给)</div>
                            <div class="speakable" onclick="sayDE('essen')">5. essen (吃)</div>
                            <div class="speakable" onclick="sayDE('gehen')">6. gehen (走/去)</div>
                            <div class="speakable" onclick="sayDE('lernen')">7. lernen (学习)</div>
                            <div class="speakable" onclick="sayDE('mehr')">8. mehr (更多)</div>
                            <div class="speakable" onclick="sayDE('nett')">9. nett (友善的)</div>
                            <div class="speakable" onclick="sayDE('sehen')">10. sehen (看)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Leben ist schön.')">Das Leben ist schön.</span><span class="translation">生活是美好的。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Bett ist bequem.')">Das Bett ist bequem.</span><span class="translation">这张床很舒服。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ein Bier, bitte.')">Ein Bier, bitte.</span><span class="translation">请来一杯啤酒。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Geben Sie mir das Buch.')">Geben Sie mir das Buch.</span><span class="translation">请把那本书给我。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Was möchten Sie essen?')">Was möchten Sie essen?</span><span class="translation">您想吃点什么？</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Wir gehen nach Hause.')">Wir gehen nach Hause.</span><span class="translation">我们回家吧。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich lerne Deutsch.')">Ich lerne Deutsch.</span><span class="translation">我在学德语。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich brauche mehr Zeit.')">Ich brauche mehr Zeit.</span><span class="translation">我需要更多时间。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Sie ist sehr nett.')">Sie ist sehr nett.</span><span class="translation">她人非常友善。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich sehe einen Film.')">Ich sehe einen Film.</span><span class="translation">我在看一部电影。</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="letter-cell">ö</td>
                    <td><strong>圆唇发 e</strong><br>双唇摆出拼音 "o" 的圆唇，固定不动，口腔内发 “哎(e)” 的音。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('schön')">1. schön (美丽的)</div>
                            <div class="speakable" onclick="sayDE('öffnen')">2. öffnen (打开)</div>
                            <div class="speakable" onclick="sayDE('hören')">3. hören (听)</div>
                            <div class="speakable" onclick="sayDE('können')">4. können (能够)</div>
                            <div class="speakable" onclick="sayDE('möchte')">5. möchte (想要)</div>
                            <div class="speakable" onclick="sayDE('Brötchen')">6. Brötchen (小面包)</div>
                            <div class="speakable" onclick="sayDE('Köln')">7. Köln (科隆)</div>
                            <div class="speakable" onclick="sayDE('Löffel')">8. Löffel (勺子)</div>
                            <div class="speakable" onclick="sayDE('Öl')">9. Öl (油)</div>
                            <div class="speakable" onclick="sayDE('zwölf')">10. zwölf (十二)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das ist sehr schön.')">Das ist sehr schön.</span><span class="translation">这太漂亮了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Bitte öffnen Sie die Tür.')">Bitte öffnen Sie die Tür.</span><span class="translation">请开门。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich höre Musik.')">Ich höre Musik.</span><span class="translation">我在听音乐。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Wir können Deutsch sprechen.')">Wir können Deutsch sprechen.</span><span class="translation">我们会说德语。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich möchte einen Tee.')">Ich möchte einen Tee.</span><span class="translation">我想来杯茶。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Brötchen schmeckt gut.')">Das Brötchen schmeckt gut.</span><span class="translation">这个小面包很好吃。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Köln ist eine große Stadt.')">Köln ist eine große Stadt.</span><span class="translation">科隆是一座大城市。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Löffel liegt hier.')">Der Löffel liegt hier.</span><span class="translation">勺子躺在这儿。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Öl ist in der Küche.')">Das Öl ist in der Küche.</span><span class="translation">油在厨房里。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Es ist zwölf Uhr.')">Es ist zwölf Uhr.</span><span class="translation">现在是12点。</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="letter-cell">ü</td>
                    <td><strong>憋嘴发 i</strong><br>双唇噘起成小圆（拼音 u 的口型），固定住，舌尖顶住下齿发“衣(i)”。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Tür')">1. Tür (门)</div>
                            <div class="speakable" onclick="sayDE('Küche')">2. Küche (厨房)</div>
                            <div class="speakable" onclick="sayDE('Glück')">3. Glück (运气)</div>
                            <div class="speakable" onclick="sayDE('müde')">4. müde (疲劳的)</div>
                            <div class="speakable" onclick="sayDE('Übung')">5. Übung (练习)</div>
                            <div class="speakable" onclick="sayDE('Gemüse')">6. Gemüse (蔬菜)</div>
                            <div class="speakable" onclick="sayDE('süß')">7. süß (甜的)</div>
                            <div class="speakable" onclick="sayDE('Frühstück')">8. Frühstück (早餐)</div>
                            <div class="speakable" onclick="sayDE('Züge')">9. Züge (火车-复数)</div>
                            <div class="speakable" onclick="sayDE('fünf')">10. fünf (五)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Tür ist zu.')">Die Tür ist zu.</span><span class="translation">门关着。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Sie arbeitet in der Küche.')">Sie arbeitet in der Küche.</span><span class="translation">她在厨房工作。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Viel Glück im neuen Jahr!')">Viel Glück im neuen Jahr!</span><span class="translation">新的一年祝你好运！</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich bin heute so müde.')">Ich bin heute so müde.</span><span class="translation">我今天太累了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Übung macht den Meister.')">Die Übung macht den Meister.</span><span class="translation">熟能生巧（大师皆由练习造就）。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Gemüse ist sehr gesund.')">Gemüse ist sehr gesund.</span><span class="translation">蔬菜对健康很有益。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Kuchen is sehr süß.')">Der Kuchen is sehr süß.</span><span class="translation">这个蛋糕非常甜。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Frühstück ist fertig.')">Das Frühstück ist fertig.</span><span class="translation">早餐准备好了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Züge kommen pünktlich.')">Die Züge kommen pünktlich.</span><span class="translation">火车准时到达。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Es kostet fünf Euro.')">Es kostet fünf Euro.</span><span class="translation">这个花费5欧元。</span></div>
                    </td>
                </tr>
            </tbody>
        </table>

        <h2>二、复合元音 (Diphthonge)</h2>
        <table>
            <thead>
                <tr>
                    <th width="10%">组合</th>
                    <th width="22%">发音核心规律</th>
                    <th width="30%">10个高频强化单词 (点击发音)</th>
                    <th width="38%">10个经典实用句子 (点击发音)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="letter-cell">ei</td>
                    <td>发类似英文单词 “I” 的音（从“啊”滑向“依”）。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('nein')">1. nein (不)</div>
                            <div class="speakable" onclick="sayDE('mein')">2. mein (我的)</div>
                            <div class="speakable" onclick="sayDE('Zeit')">3. Zeit (时间)</div>
                            <div class="speakable" onclick="sayDE('zwei')">4. zwei (二)</div>
                            <div class="speakable" onclick="sayDE('Fleisch')">5. Fleisch (肉)</div>
                            <div class="speakable" onclick="sayDE('Ei')">6. Ei (鸡蛋)</div>
                            <div class="speakable" onclick="sayDE('heiß')">7. heiß (热的)</div>
                            <div class="speakable" onclick="sayDE('schreiben')">8. schreiben (写)</div>
                            <div class="speakable" onclick="sayDE('Wein')">9. Wein (葡萄酒)</div>
                            <div class="speakable" onclick="sayDE('frei')">10. frei (自由/空闲)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Nein, danke.')">Nein, danke.</span><span class="translation">不，谢谢。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das ist mein Buch.')">Das ist mein Buch.</span><span class="translation">这是我的书。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich habe keine Zeit.')">Ich habe keine Zeit.</span><span class="translation">我没有时间。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich habe zwei Kinder.')">Ich habe zwei Kinder.</span><span class="translation">我有两个孩子。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich esse kein Fleisch.')">Ich esse kein Fleisch.</span><span class="translation">我不吃肉。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Möchten Sie ein Ei?')">Möchten Sie ein Ei?</span><span class="translation">你想来个鸡蛋吗？</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Tee ist sehr heiß.')">Der Tee ist sehr heiß.</span><span class="translation">这个茶非常烫。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich schreibe eine E-Mail.')">Ich schreibe eine E-Mail.</span><span class="translation">我在写一封邮件。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ein Glas Wein, bitte.')">Ein Glas Wein, bitte.</span><span class="translation">请来一杯葡萄酒。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Am Sonntag habe ich frei.')">Am Sonntag habe ich frei.</span><span class="translation">我周日休息。</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="letter-cell">eu / äu</td>
                    <td>发“奥-伊”的连读音（双唇扁圆由大变小）。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('neu')">1. neu (新的)</div>
                            <div class="speakable" onclick="sayDE('heute')">2. heute (今天)</div>
                            <div class="speakable" onclick="sayDE('Euro')">3. Euro (欧元)</div>
                            <div class="speakable" onclick="sayDE('Freund')">4. Freund (朋友)</div>
                            <div class="speakable" onclick="sayDE('Deutsch')">5. Deutsch (德语)</div>
                            <div class="speakable" onclick="sayDE('Häuser')">6. Häuser (房子-复数)</div>
                            <div class="speakable" onclick="sayDE('Bäume')">7. Bäume (树木-复数)</div>
                            <div class="speakable" onclick="sayDE('teuer')">8. teuer (贵的)</div>
                            <div class="speakable" onclick="sayDE('Leute')">9. Leute (人们)</div>
                            <div class="speakable" onclick="sayDE('Feuer')">10. Feuer (火)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Auto ist ganz neu.')">Das Auto ist ganz neu.</span><span class="translation">这辆车是崭新的。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Heute ist das Wetter gut.')">Heute ist das Wetter gut.</span><span class="translation">今天天气很好。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das kostet zehn Euro.')">Das kostet zehn Euro.</span><span class="translation">这个花费10欧元。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Er ist ein guter Freund.')">Er ist ein guter Freund.</span><span class="translation">他是一个好朋友。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Wir lernen alle Deutsch.')">Wir lernen alle Deutsch.</span><span class="translation">我们都在学德语。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Häuser hier sind alt.')">Die Häuser hier sind alt.</span><span class="translation">这里的房子很旧了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Bäume sind grün.')">Die Bäume sind grün.</span><span class="translation">树木全变绿了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Restaurant ist teuer.')">Das Restaurant ist teuer.</span><span class="translation">这家餐厅很贵。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Viele Leute sind im Park.')">Viele Leute sind im Park.</span><span class="translation">公园里有很多人。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Haben Sie Feuer?')">Haben Sie Feuer?</span><span class="translation">（借火）您有打火机吗？</span></div>
                    </td>
                </tr>
            </tbody>
        </table>

        <h2>三、核心辅音组合 (Konsonantenverbindungen)</h2>
        <table>
            <thead>
                <tr>
                    <th width="10%">组合</th>
                    <th width="22%">发音核心规律</th>
                    <th width="30%">10个高频强化单词 (点击发音)</th>
                    <th width="38%">10个经典实用句子 (点击发音)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="letter-cell">sch</td>
                    <td>发类似拼音 "sh"（师）的急促嘘气送气音。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Schule')">1. Schule (学校)</div>
                            <div class="speakable" onclick="sayDE('schnell')">2. schnell (快的)</div>
                            <div class="speakable" onclick="sayDE('schreiben')">3. schreiben (写)</div>
                            <div class="speakable" onclick="sayDE('Fleisch')">4. Fleisch (肉)</div>
                            <div class="speakable" onclick="sayDE('Schiff')">5. Schiff (船)</div>
                            <div class="speakable" onclick="sayDE('Schrank')">6. Schrank (柜子)</div>
                            <div class="speakable" onclick="sayDE('schlafen')">7. schlafen (睡觉)</div>
                            <div class="speakable" onclick="sayDE('schwarz')">8. schwarz (黑色的)</div>
                            <div class="speakable" onclick="sayDE('Schlüssel')">9. Schlüssel (钥匙)</div>
                            <div class="speakable" onclick="sayDE('Tisch')">10. Tisch (桌子)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Schule ist groß.')">Die Schule ist groß.</span><span class="translation">这所学校很大。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Fahr bitte nicht so schnell.')">Fahr bitte nicht so schnell.</span><span class="translation">请别开得那么快。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Er schreibt ein neues Buch.')">Er schreibt ein neues Buch.</span><span class="translation">他正在写一本新书。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich kaufe frisches Fleisch.')">Ich kaufe frisches Fleisch.</span><span class="translation">我买新鲜的肉。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Schiff fährt nach Hamburg.')">Das Schiff fährt nach Hamburg.</span><span class="translation">这艘船驶往汉堡。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Schrank steht im Zimmer.')">Der Schrank steht im Zimmer.</span><span class="translation">柜子在房间里放着。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Baby schläft ruhig.')">Das Baby schläft ruhig.</span><span class="translation">婴儿正在安静地睡觉。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich trinke schwarzen Tee.')">Ich trinke schwarzen Tee.</span><span class="translation">我喝红茶（黑茶）。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Wo ist mein Schlüssel?')">Wo ist mein Schlüssel?</span><span class="translation">我的钥匙在哪儿？</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Das Essen steht auf dem Tisch.')">Das Essen steht auf dem Tisch.</span><span class="translation">饭菜已经在桌上了。</span></div>
                    </td>
                </tr>
                <tr>
                    <td class="letter-cell">st / sp</td>
                    <td><strong>在词首或前缀后时</strong>：发成 **scht** 和 **schp**（“施特”和“施普”）。</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Straße')">1. Straße (街道)</div>
                            <div class="speakable" onclick="sayDE('Sport')">2. Sport (运动)</div>
                            <div class="speakable" onclick="sayDE('Stadt')">3. Stadt (城市)</div>
                            <div class="speakable" onclick="sayDE('sprechen')">4. sprechen (说话)</div>
                            <div class="speakable" onclick="sayDE('stehen')">5. stehen (站立/停)</div>
                            <div class="speakable" onclick="sayDE('spielen')">6. spielen (玩/踢)</div>
                            <div class="speakable" onclick="sayDE('Stift')">7. Stift (钢笔/笔)</div>
                            <div class="speakable" onclick="sayDE('spät')">8. spät (晚的)</div>
                            <div class="speakable" onclick="sayDE('Stunde')">9. Stunde (小时)</div>
                            <div class="speakable" onclick="sayDE('Sprache')">10. Sprache (语言)</div>
                        </div>
                    </td>
                    <td>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Straße ist sehr lang.')">Die Straße ist sehr lang.</span><span class="translation">这条街非常长。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Sport hält uns fit.')">Sport hält uns fit.</span><span class="translation">运动让我们保持健康。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Hannover ist eine grüne Stadt.')">Hannover ist eine grüne Stadt.</span><span class="translation">汉诺威是一座绿化很好的城市。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Sprechen Sie Englisch?')">Sprechen Sie Englisch?</span><span class="translation">您说英语吗？</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Der Bus steht an der Haltestelle.')">Der Bus steht an der Haltestelle.</span><span class="translation">公交车停在车站。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Die Kinder spielen im Garten.')">Die Kinder spielen im Garten.</span><span class="translation">孩子们在花园里玩。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Kann ich einen Stift haben?')">Kann ich einen Stift haben?</span><span class="translation">我可以借用一支笔吗？</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Es ist schon sehr spät.')">Es ist schon sehr spät.</span><span class="translation">时间已经很晚了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Ich warte seit einer Stunde.')">Ich warte seit einer Stunde.</span><span class="translation">我已经等了一个小时了。</span></div>
                        <div class="sentence-box"><span class="speakable" onclick="sayDE('Deutsch ist eine schöne Sprache.')">Deutsch ist eine schöne Sprache.</span><span class="translation">德语是一门美丽的语言。</span></div>
                    </td>
                </tr>
            </tbody>
        </table>

        <h2>四、词尾变音与特殊字母 (Besonderheiten)</h2>
        <table>
            <thead>
                <tr>
                    <th width="10%">组合</th>
                    <th width="22%">发音核心规律</th>
                    <th width="30%">10个高频强化单词 (点击发音)</th>
                    <th width="38%">10个经典实用句子 (点击发音)</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="letter-cell">b / d / g</td>
                    <td><strong>位于词尾或音节末时清化</strong>：<br>b $\rightarrow$ p | d $\rightarrow$ t | g $\rightarrow$ k</td>
                    <td>
                        <div class="word-grid">
                            <div class="speakable" onclick="sayDE('Tag')">1. Tag (白天 -
