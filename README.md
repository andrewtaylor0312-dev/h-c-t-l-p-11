<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang Web Học Từ Vựng Tiếng Anh THPT</title>
    <style>
        :root {
            --primary: #4f46e5;
            --primary-hover: #4338ca;
            --success: #10b981;
            --danger: #ef4444;
            --bg-color: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #1e293b;
            --text-secondary: #64748b;
            --border-radius: 12px;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 24px;
        }

        header h1 {
            color: var(--primary);
            font-size: 1.8rem;
            margin-bottom: 6px;
        }

        header p {
            color: var(--text-secondary);
            font-size: 0.95rem;
        }

        .container {
            width: 100%;
            max-width: 900px;
            background: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 24px;
            margin-bottom: 20px;
        }

        .nav-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: 600;
            transition: background 0.2s, transform 0.1s;
        }

        .btn:hover {
            background-color: var(--primary-hover);
        }

        .btn:active {
            transform: scale(0.98);
        }

        .btn-secondary {
            background-color: #64748b;
        }
        .btn-secondary:hover {
            background-color: #475569;
        }

        .btn-success {
            background-color: var(--success);
        }
        .btn-success:hover {
            background-color: #059669;
        }

        /* Unit Grid Selection */
        .unit-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 12px;
        }

        .unit-card {
            background: #f1f5f9;
            border: 2px solid #e2e8f0;
            border-radius: var(--border-radius);
            padding: 16px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s;
        }

        .unit-card:hover {
            border-color: var(--primary);
            background: #eef2ff;
            transform: translateY(-2px);
        }

        .unit-card h3 {
            font-size: 1.1rem;
            color: var(--primary);
            margin-bottom: 4px;
        }

        .unit-card p {
            font-size: 0.8rem;
            color: var(--text-secondary);
        }

        /* Game Menu inside a Unit (Chỉ có 2 trò chơi duy nhất) */
        .game-menu {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
            margin-top: 20px;
        }

        @media (max-width: 600px) {
            .game-menu {
                grid-template-columns: 1fr;
            }
        }

        .game-option-card {
            background: #f8fafc;
            border: 2px dashed #cbd5e1;
            border-radius: var(--border-radius);
            padding: 24px;
            text-align: center;
            cursor: pointer;
            transition: all 0.2s;
        }

        .game-option-card:hover {
            border-color: var(--primary);
            background: #f0fdf4;
        }

        .game-option-card h3 {
            color: var(--primary);
            margin-bottom: 8px;
        }

        /* Game 1: Matching Meaning Styles */
        .matching-board {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 12px;
            margin-top: 15px;
        }

        @media (max-width: 700px) {
            .matching-board {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        .match-card {
            background: #e2e8f0;
            border-radius: 8px;
            padding: 16px 10px;
            min-height: 90px;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            cursor: pointer;
            font-weight: 600;
            font-size: 0.95rem;
            user-select: none;
            transition: all 0.2s;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .match-card:hover {
            background: #cbd5e1;
        }

        .match-card.selected {
            background: #c7d2fe;
            border: 2px solid var(--primary);
            color: var(--primary-hover);
        }

        .match-card.matched {
            background: #d1fae5;
            color: #065f46;
            border: 2px solid var(--success);
            cursor: default;
            opacity: 0.7;
        }

        .match-card.wrong {
            background: #fee2e2;
            color: #991b1b;
            border: 2px solid var(--danger);
        }

        /* Game 2: Write Correct Word Styles */
        .write-game-container {
            text-align: center;
            max-width: 500px;
            margin: 0 auto;
            padding: 20px;
        }

        .word-prompt {
            font-size: 2rem;
            letter-spacing: 2px;
            font-weight: bold;
            color: var(--primary);
            margin: 15px 0;
            background: #f1f5f9;
            padding: 15px;
            border-radius: 8px;
        }

        .word-meaning {
            font-size: 1.2rem;
            color: var(--text-main);
            margin-bottom: 20px;
            font-weight: 500;
        }

        .input-group {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-bottom: 15px;
        }

        .input-group input {
            padding: 10px 16px;
            font-size: 1.1rem;
            border: 2px solid #cbd5e1;
            border-radius: 8px;
            width: 250px;
            outline: none;
            transition: border-color 0.2s;
        }

        .input-group input:focus {
            border-color: var(--primary);
        }

        .feedback-msg {
            font-weight: 600;
            font-size: 1.1rem;
            margin-top: 15px;
            min-height: 30px;
        }

        .hidden {
            display: none !important;
        }

        .score-board {
            font-size: 1.1rem;
            font-weight: bold;
            color: var(--text-secondary);
        }
    </style>
</head>
<body>

    <header>
        <h1>English Vocabulary Practice - THPT</h1>
        <p>Hệ thống học và ôn tập từ vựng Unit 1 đến Unit 10 tương tác cao</p>
    </header>

    <div class="container" id="app-container">
        <!-- Nội dung sẽ được render tự động qua JavaScript -->
    </div>

    <script>
        const vocabData = {
            1: [
                { word: "antibiotic", meaning: "thuốc kháng sinh" },
                { word: "bacteria", meaning: "vi khuẩn" },
                { word: "balanced", meaning: "cân đối, cân bằng" },
                { word: "cut down on", meaning: "cắt giảm" },
                { word: "diameter", meaning: "đường kính" },
                { word: "disease", meaning: "bệnh" },
                { word: "energy", meaning: "năng lượng" },
                { word: "examine", meaning: "kiểm tra, khám (sức khoẻ)" },
                { word: "fitness", meaning: "sự khoẻ khoắn" },
                { word: "food poisoning", meaning: "ngộ độc thức ăn" },
                { word: "germ", meaning: "vi trùng" },
                { word: "give up", meaning: "từ bỏ" },
                { word: "illness", meaning: "sự ốm đau" },
                { word: "infection", meaning: "sự lây nhiễm" },
                { word: "ingredient", meaning: "thành phần, nguyên liệu" }
            ],
            2: [
                { word: "adapt", meaning: "thích nghi, thay đổi cho phù hợp" },
                { word: "argument", meaning: "tranh luận, tranh cãi" },
                { word: "characteristic", meaning: "đặc tính, đặc điểm" },
                { word: "conflict", meaning: "sự xung đột, va chạm" },
                { word: "curious", meaning: "tò mò, muốn tìm hiểu" },
                { word: "digital native", meaning: "người sinh ra ở thời đại công nghệ" },
                { word: "experience", meaning: "trải nghiệm" },
                { word: "extended family", meaning: "gia đình đa thế hệ, đại gia đình" },
                { word: "freedom", meaning: "sự tự do" },
                { word: "generation gap", meaning: "khoảng cách giữa các thế hệ" },
                { word: "hire", meaning: "thuê nhân công, thuê người làm" },
                { word: "honesty", meaning: "tính trung thực, chân thật" },
                { word: "influence", meaning: "gây ảnh hưởng" },
                { word: "limit", meaning: "giới hạn, hạn chế" },
                { word: "nuclear family", meaning: "gia đình hạt nhân" }
            ],
            3: [
                { word: "article", meaning: "bài báo" },
                { word: "card reader", meaning: "thiết bị đọc thẻ" },
                { word: "city dweller", meaning: "người dân thành phố" },
                { word: "cycle path", meaning: "làn đường dành cho xe đạp" },
                { word: "electric bus", meaning: "xe buýt điện" },
                { word: "exhibition", meaning: "cuộc triển lãm" },
                { word: "impact", meaning: "tác động, ảnh hưởng" },
                { word: "model", meaning: "mô hình" },
                { word: "negative", meaning: "tiêu cực" },
                { word: "public transport", meaning: "phương tiện giao thông công cộng" },
                { word: "tram", meaning: "xe điện, tàu điện" },
                { word: "traffic jam", meaning: "sự tắc nghẽn giao thông" }
            ],
            4: [
                { word: "apply", meaning: "xin việc, ứng cử" },
                { word: "celebration", meaning: "lễ kỉ niệm, lễ tổ chức" },
                { word: "community", meaning: "cộng đồng" },
                { word: "compliment", meaning: "lời khen" },
                { word: "contribution", meaning: "sự đóng góp, cống hiến" },
                { word: "cultural exchange", meaning: "sự trao đổi văn hoá" },
                { word: "current", meaning: "hiện tại, đương đại" },
                { word: "development", meaning: "sự phát triển" },
                { word: "efficiently", meaning: "có hiệu quả" },
                { word: "eye-opening", meaning: "mở mang tầm mắt" },
                { word: "high-rise", meaning: "cao tầng, có nhiều tầng" },
                { word: "honour", meaning: "thể hiện sự kính trọng" }
            ],
            5: [
                { word: "atmosphere", meaning: "khí quyển" },
                { word: "balance", meaning: "sự cân bằng" },
                { word: "carbon dioxide", meaning: "khí cacbonic (CO2)" },
                { word: "coal", meaning: "than đá" },
                { word: "consequence", meaning: "hậu quả, kết quả" },
                { word: "deforestation", meaning: "sự phá rừng" },
                { word: "emission", meaning: "sự phát thải" },
                { word: "fossil fuel", meaning: "nhiên liệu hoá thạch" },
                { word: "global warming", meaning: "sự nóng lên toàn cầu" },
                { word: "heat-trapping", meaning: "giữ nhiệt" },
                { word: "methane", meaning: "khí mêtân (CH4)" },
                { word: "renewable", meaning: "tái tạo" }
            ],
            6: [
                { word: "ancient", meaning: "cổ kính" },
                { word: "appreciate", meaning: "hiểu rõ giá trị, đánh giá cao" },
                { word: "citadel", meaning: "thành trì" },
                { word: "complex", meaning: "quần thể, tổ hợp" },
                { word: "crowdfunding", meaning: "quyên góp, huy động vốn từ cộng đồng" },
                { word: "festive", meaning: "thuộc về ngày lễ" },
                { word: "fine", meaning: "tiền phạt" },
                { word: "folk", meaning: "thuộc về dân gian" },
                { word: "heritage", meaning: "di sản" },
                { word: "historic", meaning: "quan trọng, có giá trị lịch sử" },
                { word: "imperial", meaning: "thuộc về hoàng tộc" },
                { word: "landscape", meaning: "phong cảnh" }
            ],
            7: [
                { word: "academic", meaning: "có tính chất học thuật" },
                { word: "apprenticeship", meaning: "thời gian học nghề, học việc" },
                { word: "bachelor's degree", meaning: "bằng cử nhân" },
                { word: "brochure", meaning: "ấn phẩm quảng cáo, giới thiệu" },
                { word: "doctorate", meaning: "bằng tiến sĩ" },
                { word: "entrance exam", meaning: "kì thi đầu vào" },
                { word: "formal", meaning: "chính quy, có hệ thống" },
                { word: "graduation", meaning: "lễ tốt nghiệp" },
                { word: "higher education", meaning: "giáo dục đại học" },
                { word: "institution", meaning: "cơ sở, viện (đào tạo)" },
                { word: "vocational school", meaning: "trường dạy nghề" }
            ],
            8: [
                { word: "achieve", meaning: "đạt được, giành được" },
                { word: "carry out", meaning: "tiến hành" },
                { word: "combine", meaning: "kết hợp" },
                { word: "come up with", meaning: "nghĩ ra, nảy ra" },
                { word: "confidence", meaning: "sự tự tin" },
                { word: "deal with", meaning: "giải quyết, đối phó" },
                { word: "independence", meaning: "sự độc lập" },
                { word: "learner", meaning: "người học" },
                { word: "make use of", meaning: "tận dụng" },
                { word: "self-study", meaning: "sự tự học" }
            ],
            9: [
                { word: "admit", meaning: "thú nhận" },
                { word: "alcohol", meaning: "đồ uống có cồn" },
                { word: "anxiety", meaning: "sự lo lắng" },
                { word: "awareness", meaning: "nhận thức" },
                { word: "body shaming", meaning: "sự chế nhạo ngoại hình người khác" },
                { word: "bully", meaning: "bắt nạt" },
                { word: "campaign", meaning: "chiến dịch" },
                { word: "crime", meaning: "tội phạm" },
                { word: "cyberbullying", meaning: "bắt nạt trên mạng" },
                { word: "depression", meaning: "sự trầm cảm" },
                { word: "peer pressure", meaning: "áp lực từ bạn bè" }
            ],
            10: [
                { word: "biodiversity", meaning: "đa dạng sinh học" },
                { word: "conservation", meaning: "sự bảo tồn thiên nhiên" },
                { word: "coral reef", meaning: "rặng san hô" },
                { word: "delta", meaning: "đồng bằng" },
                { word: "destroy", meaning: "phá huỷ" },
                { word: "ecosystem", meaning: "hệ sinh thái" },
                { word: "endangered", meaning: "bị nguy hiểm, có nguy cơ tuyệt chủng" },
                { word: "fauna", meaning: "động vật" },
                { word: "flora", meaning: "thực vật" },
                { word: "food chain", meaning: "chuỗi thức ăn" }
            ]
        };

        const container = document.getElementById('app-container');
        let currentUnit = null;

        // 1. Màn hình trang chủ chọn Unit
        function renderHome() {
            currentUnit = null;
            let html = `
                <div class="nav-bar">
                    <h2>Danh sách các Unit (1 - 10)</h2>
                    <p>Chọn một Unit để bắt đầu luyện tập</p>
                </div>
                <div class="unit-grid">
            `;
            for (let i = 1; i <= 10; i++) {
                let count = vocabData[i] ? vocabData[i].length : 0;
                html += `
                    <div class="unit-card" onclick="selectUnit(${i})">
                        <h3>Unit ${i}</h3>
                        <p>${count} từ vựng</p>
                    </div>
                `;
            }
            html += `</div>`;
            container.innerHTML = html;
        }

        // 2. Menu chọn trò chơi (Chỉ có Matching và Write)
        function selectUnit(unitNum) {
            currentUnit = unitNum;
            container.innerHTML = `
                <div class="nav-bar">
                    <button class="btn btn-secondary" onclick="renderHome()">← Quay lại chọn Unit</button>
                    <h2>Unit ${currentUnit}</h2>
                </div>
                <p style="text-align: center; color: var(--text-secondary); margin-bottom: 20px;">Lựa chọn hình thức luyện tập:</p>
                <div class="game-menu">
                    <div class="game-option-card" onclick="startMatchingGame()">
                        <h3>Trò chơi 1</h3>
                        <p><strong>Matching Meaning</strong><br>Nối từ vựng tiếng Anh với nghĩa tiếng Việt tương ứng.</p>
                    </div>
                    <div class="game-option-card" onclick="startWriteGame()">
                        <h3>Trò chơi 2</h3>
                        <p><strong>Write the Correct Word</strong><br>Điền từ khuyết dựa trên gợi ý chữ cái đầu và nghĩa.</p>
                    </div>
                </div>
            `;
        }

        // --- TRÒ CHƠI 1: MATCHING MEANING ---
        let matchState = { cards: [], selectedCard: null, matchedCount: 0, score: 0 };

        function startMatchingGame() {
            let data = vocabData[currentUnit];
            if (!data || data.length < 4) {
                alert("Unit này chưa đủ từ vựng để chơi trò chơi này!");
                return;
            }

            let shuffledData = [...data].sort(() => 0.5 - Math.random()).slice(0, 8);
            let cardList = [];
            shuffledData.forEach((item, index) => {
                cardList.push({ id: index, type: 'word', text: item.word });
                cardList.push({ id: index, type: 'meaning', text: item.meaning });
            });

            matchState.cards = cardList.sort(() => 0.5 - Math.random());
            matchState.selectedCard = null;
            matchState.matchedCount = 0;
            matchState.score = 0;

            renderMatchingBoard();
        }

        function renderMatchingBoard() {
            let html = `
                <div class="nav-bar">
                    <button class="btn btn-secondary" onclick="selectUnit(${currentUnit})">← Menu Unit</button>
                    <div class="score-board">Điểm: <span id="match-score">${matchState.score}</span> / 8</div>
                    <button class="btn" onclick="startMatchingGame()">Chơi lại</button>
                </div>
                <div class="matching-board">
            `;

            matchState.cards.forEach((card, index) => {
                html += `<div class="match-card" id="card-${index}" onclick="handleCardClick(${index})">${card.text}</div>`;
            });

            html += `</div>`;
            container.innerHTML = html;
 