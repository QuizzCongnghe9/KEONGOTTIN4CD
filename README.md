# KEONGOTTIN4CD[keongotonghop4.html](https://github.com/user-attachments/files/24116074/keongotonghop4.html)
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kẹo Ngọt -Tin học 4 CD</title>
    <style>
        /* ==================== CSS CƠ BẢN (Từ Kẹo Ngọt) ==================== */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%); 
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            color: #4a4a4a;
        }

        .candy-container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            width: 90%;
            max-width: 850px; 
            transition: transform 0.3s ease-in-out;
        }

        h1 {
            color: #e57373; 
            text-align: center;
            margin-bottom: 5px; 
            font-size: 2.5em;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.05);
        }

        .author-info {
            text-align: center;
            color: #6a1b9a;
            font-size: 1.0em;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .score-info, .question-text {
            text-align: center;
            margin-bottom: 15px;
            font-weight: bold;
            font-size: 1.1em;
            color: #6a1b9a;
        }

        .question-box {
            background-color: #fce4ec; 
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
        }
        
        .options-list {
            list-style: none;
            padding: 0;
        }

        .option-item {
            background-color: #fff3e0; 
            margin-bottom: 10px;
            padding: 15px;
            border-radius: 10px;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
            border: 2px solid transparent;
            font-weight: 500;
        }

        .option-item:hover {
            background-color: #ffe0b2;
            transform: translateY(-2px);
        }

        /* Kết quả */
        .option-item.correct {
            background-color: #c8e6c9; 
            border-color: #4caf50;
            pointer-events: none;
        }

        .option-item.incorrect {
            background-color: #ffcdd2; 
            border-color: #f44336;
            pointer-events: none;
        }

        /* Đúng/Sai Gộp */
        .true-false-group .statement-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #fff;
            padding: 15px;
            margin-bottom: 10px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
        }
        
        .true-false-group .statement-text {
            flex-grow: 1;
            text-align: left;
            margin-right: 10px;
        }

        .ds-btn {
            padding: 10px 0; 
            border: 1px solid #ccc;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: background-color 0.2s, transform 0.1s;
            margin-left: 5px;
            display: inline-block;
            min-width: 35px; 
            text-align: center; 
        }

        .ds-btn.selected {
            border-color: #ff8a65;
            background-color: #ffe0b2;
        }

        .ds-btn.correct-answer {
            background-color: #c8e6c9; 
            border-color: #4caf50;
        }

        .ds-btn.incorrect-answer {
            background-color: #ffcdd2; 
            border-color: #f44336;
        }

        .explanation {
            margin-top: 15px;
            padding: 10px;
            background-color: #f0f4c3; 
            border-radius: 10px;
            border-left: 5px solid #afb42b;
            font-style: italic;
            display: none;
        }

        .control-buttons {
            text-align: center;
        }

        #check-button, #next-button, #restart-button {
            background-color: #7986cb; 
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1.1em;
            font-weight: bold;
            transition: background-color 0.3s, transform 0.1s;
            margin: 5px;
        }
        #next-button, #restart-button {
            background-color: #ff8a65; 
        }
        
        /* Modal */
        #result-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            display: none; 
            justify-content: center;
            align-items: center;
            z-index: 100;
        }

        .modal-content {
            background-color: white;
            padding: 40px;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }

        /* ==================== CSS BỔ SUNG (Nối Cặp) ==================== */
        #matching-area {
            display: flex;
            justify-content: space-between;
            gap: 20px;
            margin: 20px 0;
            user-select: none; 
            position: relative; 
        }
        .column {
            width: 48%;
            text-align: left;
        }
        .matching-item {
            background-color: #fff;
            margin: 10px 0;
            padding: 12px;
            border-radius: 6px;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s, border 0.2s;
            border: 1px solid #ccc;
            line-height: 1.4;
            min-height: 40px; 
            display: flex;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            position: relative; 
        }
        .matching-item:not(.selected):hover { 
            background-color: #dcdcdc;
            transform: translateY(-1px);
        }
        .matching-item.selected { 
            background-color: #b0e0e6 !important; 
            border: 2px solid #008cba;
            font-weight: bold;
        }

        /* Line */
        #line-container {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none; 
            z-index: 1; 
        }
        .connection-line {
            position: absolute;
            height: 3px; 
            background-color: #6c757d; 
            transform-origin: 0 0;
            box-shadow: 0 1px 3px rgba(0, 0, 0, 0.4); 
            z-index: 2;
        }
        
        /* Kết quả */
        .matching-item.correct-match {
            background-color: #c8e6c9 !important; 
            border: 2px solid #4CAF50;
        }
        .matching-item.incorrect-match {
            background-color: #ffcdd2 !important; 
            border: 2px solid #f44336;
        }
        .matching-item.hint-match { 
            border: 2px solid orange !important;
        }

        /* Ẩn khu vực Nối/Đúng/Sai nếu không dùng (Sẽ được JS hiển thị lại khi cần) */
        #matching-area-container, #true-false-container {
            display: none;
        }
    </style>
</head>
<body>
    
    <audio id="background-music" loop autoplay>
        <source src="background_music.mp3" type="audio/mpeg">
        Trình duyệt của bạn không hỗ trợ thẻ audio.
    </audio>
    <div class="candy-container">
        <h1>🍬 Kẹo Ngọt 🍭</h1>
        <p class="author-info">Người tạo:GV Trần Trọng Nghĩa-GV Trường Tiểu học & THCS Số 1 Chư Đang Ya-Xã Biển Hồ</p>

        <div class="score-info">
            Điểm số: <span id="current-score">0.0</span> / <span id="max-score"></span>
            | Câu: <span id="current-question-number">0</span>  <span id="total-questions"></span>
        </div>
        
        <div id="quiz-area">
            <div class="question-box">
                <p class="question-text" id="question-text"></p>
                <div id="question-content">
                    <ul class="options-list" id="options-list"></ul>
                    
                    <div id="true-false-container" class="true-false-group"></div>
                    
                    <div id="matching-area-container">
                        <p style="text-align: center; color: #8B0000; font-weight: bold;"> </p>
                        <div id="matching-area">
                            <div id="line-container"></div> 
                            <div id="column-a" class="column"></div>
                            <div id="column-b" class="column"></div>
                        </div>
                    </div>
                </div>
                
                <div class="explanation" id="explanation-box">
                    <strong>Giải thích:</strong> <span id="explanation-text"></span>
                </div>
            </div>
            
            <div class="control-buttons">
                <button id="check-button" style="display: none;">Kiểm Tra</button>
                <button id="next-button" style="display: none;">Câu Kế Tiếp >></button>
            </div>
        </div>
    </div>

    <div id="result-modal">
        <div class="modal-content">
            <h2>🎉 HOÀN THÀNH BÀI ÔN TẬP! 🎉</h2>
            <p>Bạn đã hoàn thành tất cả các câu hỏi.</p>
            <p><strong>Tổng điểm đạt được:</strong> <span id="final-score"></span></p>
            <p id="result-message"></p>
            <button id="restart-button">Chơi Lại</button>
        </div>
    </div>

    <script>
        // Mảng màu sắc độc đáo cho từng đường nối
        const COLOR_PALETTE = [
            '#008CBA', '#FF8C00', '#8A2BE2', '#3CB371', '#FF6347', '#4682B4'
        ];
        const INCORRECT_COLOR = '#f44336';
        
        // Dữ liệu câu hỏi HỢP NHẤT TỪ CẢ HAI TỆP (9 Trắc nghiệm + 1 Nối Cặp + 1 Đúng Sai Gộp)
        const questionsData = [
            // 1.
            {
                type: 'multipleChoice',
                question: "Trong các thiết bị sau, thiết bị nào không phải là phần cứng máy tính?",
                options: ["Màn hình máy tính", "Chuột máy tính", "Microsoft Word", "Bàn phím máy tính"],
                answerIndex: 2, 
                explanation: "Microsoft Word là Phần mềm ứng dụng (chương trình), không phải phần cứng.",
                points: 0.5
            },
            // 2.
            {
                type: 'multipleChoice',
                question: "Phần mềm là chương trình máy tính được tạo ra để làm gì?",
                options: ["Để gõ văn bản và làm bài trình chiếu.", "Để điều khiển máy tính thực hiện công việc.", "Để giúp người dùng giải trí sau giờ học.", "Cả ba đáp án trên đều đúng."],
                answerIndex: 1, 
                explanation: "Phần mềm là tập hợp các chương trình, có chức năng điều khiển máy tính thực hiện công việc.",
                points: 0.5
            },
            // 3.
            {
                type: 'multipleChoice',
                question: "Khi gõ xong hàng phím số, các ngón tay cần quay về hàng phím nào sau đây?",
                options: ["Hàng phím trên.", "Hàng phím dưới.", "Hàng phím cơ sở.", "Giữ nguyên trên hàng phím số."],
                answerIndex: 2, 
                explanation: "Các ngón tay phải quay về hàng phím cơ sở sau khi gõ xong.",
                points: 0.5
            },
            // 4.
            {
                type: 'multipleChoice',
                question: "Để tạo một thư mục mới trong cửa sổ quản lí tệp và thư mục, em thực hiện thao tác nào sau đây?",
                options: ["Nháy chuột phải, chọn New rồi chọn File.", "Nháy chuột phải, chọn New rồi chọn Folder.", "Nháy đúp chuột vào vùng trống.", "Chọn tệp bất kì rồi chọn Copy."],
                answerIndex: 1, 
                explanation: "Thao tác đúng để tạo thư mục mới: Nháy chuột phải → New → Folder.",
                points: 0.5
            },
            // 5.
            {
                type: 'multipleChoice',
                question: "Thông tin trên một trang web thường được thể hiện dưới những dạng nào?",
                options: ["Chỉ có văn bản và hình ảnh tĩnh.", "Chỉ có hình ảnh, video và âm thanh.", "Văn bản, hình ảnh, âm thanh, video, và đường liên kết.", "Chỉ có văn bản và đường liên kết."],
                answerIndex: 2, 
                explanation: "Thông tin trên web đa dạng: Văn bản, Hình ảnh, Âm thanh, Video, Đường liên kết.",
                points: 0.5
            },
            // 6.
            {
                type: 'multipleChoice',
                question: "Bạn An muốn vẽ một bức tranh về trường học trên máy tính. An cần dùng loại phần mềm nào để thực hiện công việc này?",
                options: ["Phần mềm soạn thảo văn bản.", "Phần mềm hệ thống.", "Phần mềm trò chơi.", "Phần mềm ứng dụng đồ hoạ Paint."],
                answerIndex: 3, 
                explanation: "Phần mềm ứng dụng đồ hoạ Paint. dùng để vẽ tranh.",
                points: 0.5
            },
            // 7.
            {
                type: 'multipleChoice',
                question: "Trong phần mềm trình chiếu, việc chọn bố cục (Layout) cho trang chiếu ngay từ đầu có mục đích gì?",
                options: ["Giúp trang chiếu tự động thêm hình ảnh.", "Giúp định hướng vị trí của tiêu đề và nội dung.", "Giúp văn bản tự động chuyển sang tiếng Việt.", "Giúp chuyển đổi giữa chế độ làm việc và chế độ trình chiếu."],
                answerIndex: 1, 
                explanation: "Việc chọn Layout giúp định hướng vị trí các thành phần như tiêu đề, nội dung, hình ảnh.",
                points: 0.5
            },
            // 8.
            {
                type: 'multipleChoice',
                question: "Trong tìm kiếm thông tin trên Internet, 'Từ khóa' là gì?",
                options: ["Là tên của trang web mà em truy cập.", "Là từ hoặc cụm từ mô tả nội dung em muốn tìm kiếm.", "Là địa chỉ email của người gửi thông tin.", "Là kết quả cuối cùng mà máy tìm kiếm trả về."],
                answerIndex: 1, 
                explanation: "Từ khóa là từ hoặc cụm từ được nhập vào máy tìm kiếm để mô tả thông tin cần tìm.",
                points: 0.5
            },
            // 9.
            {
                type: 'multipleChoice',
                question: "Máy tìm kiếm (Search Engine) là gì?",
                options: ["Là một trang web thông thường hiển thị tin tức hàng ngày.", "Là phần mềm giúp em soạn thảo văn bản.", "Là một trang web đặc biệt giúp em tìm kiếm thông tin trên Internet.", "Là thiết bị phần cứng của máy tính."],
                answerIndex: 2, 
                explanation: "Máy tìm kiếm là một trang web (ví dụ: Google, Bing) được thiết kế chuyên biệt để tìm kiếm thông tin trên Internet.",
                points: 0.5
            },
            
            // CÂU HỎI NỐI CẶP (MATCHING) - Chủ đề Văn Miếu (1.0 điểm)
            {
                type: 'matching',
                question: "Hãy nối Từ khóa (Cột A) với Hiệu quả tìm kiếm (Cột B) phù hợp nhất.",
                points: 1.0, 
                dataA: [
                    { A: "Văn Miếu", match: "c" }, 
                    { A: "Di tích lịch sử", match: "a" }, 
                    { A: "Văn Miếu Quốc Tử Giám", match: "d" },
                    { A: "Di tích lịch sử Văn Miếu Quốc Tử Giám", match: "b" }
                ],
                dataB: [
                    { label: "a", B_text: "Không hiệu quả, kết quả quá nhiều." },
                    { label: "b", B_text: "Rất hiệu quả, kết quả chính xác nhất." },
                    { label: "c", B_text: "Tạm được, kết quả có thể chưa đủ." },
                    { label: "d", B_text: "Khá hiệu quả, kết quả đã được chọn lọc." }
                ]
            },

            // CÂU HỎI TIN HỌC ĐÚNG/SAI GỘP (1.0 điểm)
            {
                type: 'trueFalseGroup',
                question: "Hãy xác định các phát biểu sau là ĐÚNG (Đ) hay SAI (S):",
                statements: [
                    { 
                        text: "a) Chỉ có máy tính để bàn mới cần phần cứng.", 
                        correct: 'S', 
                        explanation: "Vì mọi loại máy tính (máy tính để bàn, laptop, máy tính bảng) đều cần phần cứng." 
                    },
                    { 
                        text: "b) Phần mềm là bộ não của máy tính, còn phần cứng là cơ thể.", 
                        correct: 'S', 
                        explanation: "Vì CPU (bộ vi xử lí) mới là 'bộ não' của máy tính." 
                    },
                    { 
                        text: "c) Để gõ chữ hoa, ta cần giữ phím Shift và gõ phím chữ cái đó.", 
                        correct: 'Đ', 
                        explanation: "Đây là một trong các cách gõ chữ hoa (hoặc dùng Caps Lock)." 
                    },
                    { 
                        text: "d) Gõ bàn phím đúng cách giúp tốc độ gõ chậm hơn nhưng dễ nhớ hơn.", 
                        correct: 'S', 
                        explanation: "Vì gõ đúng cách (gõ 10 ngón) giúp tốc độ gõ nhanh hơn và chuẩn xác hơn." 
                    }
                ],
                points: 1.0 
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let isAnswered = false;
        let userAnswers = {}; 
        
        // Dùng cho Nối Cặp
        let matchingState = {
            currentSelection: { A: null, B: null },
            connections: {}, // { indexA: labelB }
            connectionElements: {} // { indexA: {line: element, color: color} }
        };
        // Biến lưu trữ hàm xử lý resize
        let matchingResizeHandler = null; 

        const totalQuestions = questionsData.length;
        // TÍNH TOÁN TỔNG ĐIỂM: 9 * 0.5 + 1.0 + 1.0 = 6.5 điểm
        const maxScore = questionsData.reduce((sum, q) => sum + q.points, 0); 

        // Lấy các phần tử DOM
        const audioBackground = document.getElementById('background-music'); // Thêm phần tử Audio
        const questionTextElement = document.getElementById('question-text');
        const optionsListElement = document.getElementById('options-list'); 
        const trueFalseContainer = document.getElementById('true-false-container'); 
        const matchingAreaContainer = document.getElementById('matching-area-container');
        const matchingArea = document.getElementById('matching-area'); 
        const columnA = document.getElementById('column-a');
        const columnB = document.getElementById('column-b');
        const lineContainer = document.getElementById('line-container');

        const nextButton = document.getElementById('next-button');
        const checkButton = document.getElementById('check-button');
        const explanationBox = document.getElementById('explanation-box');
        const explanationText = document.getElementById('explanation-text');
        const currentScoreElement = document.getElementById('current-score');
        const maxScoreElement = document.getElementById('max-score');
        const currentQuestionNumberElement = document.getElementById('current-question-number');
        const resultModal = document.getElementById('result-modal');
        const finalScoreElement = document.getElementById('final-score');
        const resultMessageElement = document.getElementById('result-message');
        const restartButton = document.getElementById('restart-button');
        
        // Cố gắng tự động phát nhạc khi trang tải (có thể bị trình duyệt chặn)
        document.addEventListener('DOMContentLoaded', () => {
             // Thử phát nhạc khi người dùng tương tác lần đầu
            document.body.addEventListener('click', () => {
                if (audioBackground.paused) {
                    audioBackground.play().catch(e => {
                        console.log("Audio playback failed (usually due to browser policy).");
                    });
                }
            }, { once: true });
        });
        

        // Hàm khởi tạo game
        function initializeGame() {
            currentQuestionIndex = 0;
            score = 0;
            isAnswered = false;
            userAnswers = {};
            // Khởi tạo lại trạng thái Nối Cặp
            matchingState = { currentSelection: { A: null, B: null }, connections: {}, connectionElements: {} };

            maxScoreElement.textContent = maxScore.toFixed(1); 
            document.getElementById('total-questions').textContent = `/ ${totalQuestions}`;
            document.getElementById('quiz-area').style.display = 'block';
            resultModal.style.display = 'none';
            loadQuestion();
            
            // Cố gắng phát nhạc khi game khởi động lại (sau khi người dùng đã tương tác)
            audioBackground.play().catch(e => {}); 
        }

        // --- HÀM HỖ TRỢ CHO NỐI CẶP ---

        function getCenter(element) {
            const rect = element.getBoundingClientRect();
            // Lấy vị trí tương đối so với container chính (matchingArea)
            const containerRect = matchingArea.getBoundingClientRect(); 
            
            return {
                x: rect.left + rect.width / 2 - containerRect.left,
                y: rect.top + rect.height / 2 - containerRect.top
            };
        }

        function drawConnection(itemA, itemB, indexA, labelB, color) {
            const start = getCenter(itemA);
            const end = getCenter(itemB);
            
            const dx = end.x - start.x;
            const dy = end.y - start.y;
            const length = Math.sqrt(dx * dx + dy * dy);
            const angle = Math.atan2(dy, dx) * 180 / Math.PI;

            const line = document.createElement('div');
            line.className = 'connection-line';
            line.style.width = `${length}px`;
            line.style.top = `${start.y}px`;
            line.style.left = `${start.x}px`;
            line.style.transform = `rotate(${angle}deg)`;
            line.style.backgroundColor = color; 
            
            lineContainer.appendChild(line);
            
            matchingState.connectionElements[indexA] = { line: line, color: color };
        }

        function clearMatchingState() {
             // Dọn dẹp DOM và trạng thái JS của Nối Cặp
             lineContainer.innerHTML = '';
             matchingState = { currentSelection: { A: null, B: null }, connections: {}, connectionElements: {} };
             document.querySelectorAll('.matching-item').forEach(el => {
                el.classList.remove('correct-match', 'incorrect-match', 'hint-match', 'selected');
                el.removeAttribute('data-is-connected');
            });
        }
        
        function unconnectItemA(indexA) {
            const labelB = matchingState.connections[indexA];
            
            const itemA = document.querySelector(`.matching-item-a[data-index="${indexA}"]`);
            const itemB = document.querySelector(`.matching-item-b[data-label="${labelB}"]`);

            delete matchingState.connections[indexA];
            
            if (matchingState.connectionElements[indexA]) {
                matchingState.connectionElements[indexA].line.remove();
                delete matchingState.connectionElements[indexA];
            }

            if (itemA) itemA.removeAttribute('data-is-connected');
            // Kiểm tra item B: chỉ gỡ connected nếu nó không còn được item A nào khác nối tới
            const isBStillConnected = Object.values(matchingState.connections).includes(labelB);
            if (itemB && !isBStillConnected) itemB.removeAttribute('data-is-connected');
            
            // Xóa trạng thái lựa chọn/kết quả tạm thời
            document.querySelectorAll('.matching-item').forEach(el => {
                el.classList.remove('correct-match', 'incorrect-match', 'hint-match', 'selected');
            });
        }

        function makeConnection() {
            const itemA = matchingState.currentSelection.A;
            const itemB = matchingState.currentSelection.B;
            
            const indexA = itemA.dataset.index;
            const labelB = itemB.dataset.label;
            
            // 1. Xử lý hủy nối của Item A cũ (nếu có)
            if (itemA.dataset.isConnected) {
                unconnectItemA(indexA);
            }
            
            // 2. Xử lý hủy nối của Item B cũ (nếu có Item A khác đang nối tới B này)
            const oldIndexA = Object.keys(matchingState.connections).find(key => matchingState.connections[key] === labelB);
            if (oldIndexA) {
                unconnectItemA(oldIndexA);
            }
            
            // 3. Thực hiện nối mới
            matchingState.connections[indexA] = labelB;
            
            itemA.dataset.isConnected = 'true';
            itemB.dataset.isConnected = 'true';
            
            const color = COLOR_PALETTE[parseInt(indexA) % COLOR_PALETTE.length];
            drawConnection(itemA, itemB, indexA, labelB, color);

            // 4. Reset lựa chọn hiện tại
            document.querySelectorAll('.matching-item').forEach(el => {
                el.classList.remove('selected');
            });
            matchingState.currentSelection.A = null;
            matchingState.currentSelection.B = null;

            explanationBox.style.display = 'none';
        }
        
        function selectMatchingItem(element, column) {
            if (isAnswered) return;

            // Xử lý hủy nối nếu nhấp lại vào A đã nối
            if (column === 'A' && element.dataset.isConnected) {
                unconnectItemA(element.dataset.index);
                element.classList.add('selected');
                matchingState.currentSelection[column] = element;
                return;
            }
            
            // Không cho chọn B đã nối trừ khi A đã được chọn
            if (column === 'B' && element.dataset.isConnected && !matchingState.currentSelection.A) {
                 return;
            }

            // Bỏ chọn tất cả các item trong cột đang chọn
            document.querySelectorAll(`.matching-item-${column.toLowerCase()}`).forEach(el => {
                el.classList.remove('selected');
            });

            // Chọn item mới
            element.classList.add('selected');
            matchingState.currentSelection[column] = element;
            
            // Nếu cả A và B đều được chọn, thực hiện nối
            if (matchingState.currentSelection.A && matchingState.currentSelection.B) {
                makeConnection();
            }
        }


        // Hàm tải câu hỏi
        function loadQuestion() {
            if (currentQuestionIndex >= totalQuestions) {
                showResults();
                return;
            }

            const currentQuestion = questionsData[currentQuestionIndex];
            
            currentScoreElement.textContent = score.toFixed(1);
            currentQuestionNumberElement.textContent = currentQuestionIndex + 1;

            questionTextElement.textContent = `Câu ${currentQuestionIndex + 1}: (${currentQuestion.points.toFixed(1)} điểm) ${currentQuestion.question}`;
            
            // Xóa bộ lắng nghe resize cũ nếu có (Quan trọng để tránh lỗi khi chuyển câu)
            if (matchingResizeHandler) {
                window.removeEventListener('resize', matchingResizeHandler);
                matchingResizeHandler = null;
            }

            // Ẩn tất cả khu vực của các loại câu hỏi khác nhau để tránh xung đột
            optionsListElement.style.display = 'none';
            trueFalseContainer.style.display = 'none';
            matchingAreaContainer.style.display = 'none';
            
            optionsListElement.innerHTML = '';
            trueFalseContainer.innerHTML = '';
            clearMatchingState(); 
            columnA.innerHTML = '';
            columnB.innerHTML = '';
            
            explanationBox.style.display = 'none';
            nextButton.style.display = 'none';
            checkButton.style.display = 'none';
            isAnswered = false;

            // Xử lý hiển thị tùy theo loại câu hỏi
            if (currentQuestion.type === 'multipleChoice') {
                optionsListElement.style.display = 'block';
                // Trắc nghiệm tự động kiểm tra, không cần nút check
                
                currentQuestion.options.forEach((option, index) => {
                    const li = document.createElement('li');
                    li.className = 'option-item';
                    const optionLabel = String.fromCharCode(65 + index); 
                    li.innerHTML = `<strong>${optionLabel}.</strong> ${option}`;
                    li.setAttribute('data-index', index);
                    li.onclick = () => selectMultipleChoice(li, index, currentQuestion);
                    optionsListElement.appendChild(li);
                });

            } else if (currentQuestion.type === 'trueFalseGroup') {
                trueFalseContainer.style.display = 'block';
                checkButton.style.display = 'inline-block';
                userAnswers = {}; 
                
                currentQuestion.statements.forEach((statement, index) => {
                    const statementId = `stmt_${currentQuestionIndex}_${index}`;
                    const item = document.createElement('div');
                    item.className = 'statement-item';
                    item.innerHTML = `
                        <div class="statement-text"><strong>${statement.text.split(')')[0]})</strong> ${statement.text.split(')')[1]}</div>
                        <div>
                            <span class="ds-btn" data-id="${statementId}" data-choice="Đ">Đ</span>
                            <span class="ds-btn" data-id="${statementId}" data-choice="S">S</span>
                        </div>
                    `;
                    trueFalseContainer.appendChild(item);
                });

                document.querySelectorAll('.ds-btn').forEach(button => {
                    button.addEventListener('click', function() {
                        if(isAnswered) return;
                        const statementId = this.getAttribute('data-id');
                        const choice = this.getAttribute('data-choice');
                        
                        document.querySelectorAll(`.ds-btn[data-id="${statementId}"]`).forEach(btn => {
                            btn.classList.remove('selected');
                        });

                        this.classList.add('selected');
                        userAnswers[statementId] = choice;
                    });
                });
            } else if (currentQuestion.type === 'matching') {
                matchingAreaContainer.style.display = 'block';
                checkButton.style.display = 'inline-block';
                
                // Hiển thị các item cột A (Từ khóa)
                currentQuestion.dataA.forEach((item, index) => {
                    const div = document.createElement('div');
                    div.className = 'matching-item matching-item-a';
                    div.dataset.index = index;
                    div.dataset.match = item.match; 
                    div.textContent = (index + 1) + ". " + item.A;
                    div.addEventListener('click', () => selectMatchingItem(div, 'A'));
                    columnA.appendChild(div);
                });

                // Hiển thị các item cột B (Hiệu quả tìm kiếm)
                currentQuestion.dataB.forEach((item) => {
                    const div = document.createElement('div');
                    div.className = 'matching-item matching-item-b';
                    div.dataset.label = item.label; 
                    div.textContent = item.label + ". " + item.B_text;
                    div.addEventListener('click', () => selectMatchingItem(div, 'B'));
                    columnB.appendChild(div);
                });
                
                // Khởi tạo hàm xử lý resize riêng cho Matching (Đã tách ra khỏi global)
                matchingResizeHandler = () => {
                    // Kiểm tra nếu đang ở câu Matching VÀ đang có kết nối
                    if (questionsData[currentQuestionIndex].type === 'matching' && Object.keys(matchingState.connections).length > 0) {
                        const tempConnections = { ...matchingState.connections };
                        clearMatchingState(); 
                        
                        Object.keys(tempConnections).forEach(indexA => {
                            const labelB = tempConnections[indexA];
                            const itemA = document.querySelector(`.matching-item-a[data-index="${indexA}"]`);
                            const itemB = document.querySelector(`.matching-item-b[data-label="${labelB}"]`);
                            
                            if (itemA && itemB) {
                                // Tái tạo lại trạng thái
                                matchingState.connections[indexA] = labelB;
                                itemA.dataset.isConnected = 'true';
                                itemB.dataset.isConnected = 'true';
                                
                                const color = COLOR_PALETTE[parseInt(indexA) % COLOR_PALETTE.length];
                                drawConnection(itemA, itemB, indexA, labelB, color);
                            }
                        });
                        // Phục hồi lại kết quả nếu đã kiểm tra
                        if (isAnswered) {
                            checkMatchingResult(currentQuestion, true); 
                        }
                    }
                };
                window.addEventListener('resize', matchingResizeHandler);
            }
        }

        // Hàm xử lý khi người dùng chọn đáp án (Trắc nghiệm đơn)
        function selectMultipleChoice(selectedElement, selectedIndex, currentQuestion) {
            if (isAnswered) return;
            isAnswered = true;

            const correctIndex = currentQuestion.answerIndex;
            const allOptions = optionsListElement.children;

            if (selectedIndex === correctIndex) {
                selectedElement.classList.add('correct');
                score += currentQuestion.points;
            } else {
                selectedElement.classList.add('incorrect');
                allOptions[correctIndex].classList.add('correct'); 
            }

            Array.from(allOptions).forEach(option => option.style.pointerEvents = 'none');

            explanationText.textContent = currentQuestion.explanation;
            explanationBox.style.display = 'block';
            nextButton.style.display = 'block';
            currentScoreElement.textContent = score.toFixed(1); 
        }
        
        // Hàm kiểm tra kết quả Nối Cặp
        function checkMatchingResult(currentQuestion, isResizing = false) {
            let correctCount = 0;
            const pointsPerStatement = currentQuestion.points / currentQuestion.dataA.length; 
            let matchingExplanation = '<ul>';
            
            if (!isResizing) {
                document.querySelectorAll('.matching-item').forEach(el => {
                    el.style.pointerEvents = 'none'; 
                });
            }

            // Logic kiểm tra Nối Cặp
            currentQuestion.dataA.forEach((itemAData, indexA) => {
                const selectedLabelB = matchingState.connections[indexA];
                const correctLabelB = itemAData.match; 
                
                const itemAElement = document.querySelector(`.matching-item-a[data-index="${indexA}"]`);
                const itemBElement = document.querySelector(`.matching-item-b[data-label="${selectedLabelB}"]`);
                
                const connectionDetail = matchingState.connectionElements[indexA];
                const lineElement = connectionDetail ? connectionDetail.line : null;

                const B_Text_Correct = currentQuestion.dataB.find(b => b.label === correctLabelB).B_text;

                if (selectedLabelB === correctLabelB) {
                    correctCount++;
                    itemAElement.classList.add('correct-match');
                    if(itemBElement) itemBElement.classList.add('correct-match');

                } else {
                    itemAElement.classList.add('incorrect-match');
                    if(itemBElement) itemBElement.classList.add('incorrect-match');
                    
                    // Gợi ý đáp án đúng
                    const correctBElement = document.querySelector(`.matching-item-b[data-label="${correctLabelB}"]`);
                    if(correctBElement) correctBElement.classList.add('hint-match'); 
                    
                    if (lineElement) lineElement.style.backgroundColor = INCORRECT_COLOR; 
                }
                
                // Tạo giải thích sau khi đã tô màu
                if (selectedLabelB === correctLabelB) {
                    matchingExplanation += `<li>✅ ${itemAData.A} nối với ${B_Text_Correct} (ĐÚNG)</li>`;
                } else {
                    matchingExplanation += `<li>❌ ${itemAData.A} (Nối sai) - Đáp án đúng là: ${B_Text_Correct}</li>`;
                }
            });
            matchingExplanation += '</ul>';
            
            if (!isResizing) {
                score += correctCount * pointsPerStatement;
                
                explanationText.innerHTML = `Bạn nối đúng ${correctCount}/${currentQuestion.dataA.length} cặp. (Đạt ${ (correctCount * pointsPerStatement).toFixed(2)}/${currentQuestion.points.toFixed(1)} điểm)<br>` + matchingExplanation;
                explanationBox.style.display = 'block';

                currentScoreElement.textContent = score.toFixed(1); 
                checkButton.style.display = 'none';
                nextButton.style.display = 'inline-block';
            }
        }

        // Hàm xử lý khi nhấn "Kiểm Tra" (Đúng/Sai Gộp & Nối Cặp)
        checkButton.onclick = () => {
            if (isAnswered) return;
            
            const currentQuestion = questionsData[currentQuestionIndex];

            if (currentQuestion.type === 'trueFalseGroup') {
                const totalStatements = currentQuestion.statements.length;
                if (Object.keys(userAnswers).length !== totalStatements) {
                    alert("Bạn cần trả lời Đúng hoặc Sai cho tất cả 4 phát biểu trước khi kiểm tra!");
                    return;
                }
                
                isAnswered = true;
                let correctCount = 0;
                const pointsPerStatement = currentQuestion.points / totalStatements; 
                let fullExplanation = '';

                // Logic kiểm tra Đúng/Sai 
                currentQuestion.statements.forEach((statement, index) => {
                    const statementId = `stmt_${currentQuestionIndex}_${index}`;
                    const userChoice = userAnswers[statementId];
                    const correctChoice = statement.correct;
                    
                    const trueBtn = document.querySelector(`.ds-btn[data-id="${statementId}"][data-choice="Đ"]`);
                    const falseBtn = document.querySelector(`.ds-btn[data-id="${statementId}"][data-choice="S"]`);

                    trueBtn.style.pointerEvents = 'none';
                    falseBtn.style.pointerEvents = 'none';
                    
                    // Highlight đáp án đúng
                    if (correctChoice === 'Đ') {
                        trueBtn.classList.add('correct-answer');
                    } else {
                        falseBtn.classList.add('correct-answer');
                    }
                    
                    // Highlight đáp án người dùng chọn sai (nếu có)
                    if (userChoice === correctChoice) {
                        correctCount++;
                    } else if (userChoice) {
                        const incorrectBtn = document.querySelector(`.ds-btn[data-id="${statementId}"][data-choice="${userChoice}"]`);
                        if(incorrectBtn) {
                            incorrectBtn.classList.add('incorrect-answer');
                        }
                    }

                    const statementLabel = statement.text.split(')')[0];
                    const isCorrectText = correctChoice === 'Đ' ? 'ĐÚNG' : 'SAI';
                    fullExplanation += `${statementLabel}) Phát biểu ${statementLabel} là ${isCorrectText}. ${statement.explanation}\n`;
                });

                score += correctCount * pointsPerStatement;
                
                explanationText.innerHTML = `Bạn trả lời đúng ${correctCount}/${totalStatements} ý. (Đạt ${ (correctCount * pointsPerStatement).toFixed(2)}/${currentQuestion.points.toFixed(1)} điểm)<br><br>` + fullExplanation.replace(/\n/g, '<br>');
                explanationBox.style.display = 'block';

                currentScoreElement.textContent = score.toFixed(1); 
                checkButton.style.display = 'none';
                nextButton.style.display = 'inline-block';
            
            } else if (currentQuestion.type === 'matching') {
                if (Object.keys(matchingState.connections).length !== currentQuestion.dataA.length) {
                    alert(`Bạn cần nối đủ ${currentQuestion.dataA.length} cặp trước khi kiểm tra!`);
                    return;
                }
                isAnswered = true;
                checkMatchingResult(currentQuestion);
            }
        };


        // Hàm xử lý khi nhấn "Câu Kế Tiếp"
        nextButton.onclick = () => {
            currentQuestionIndex++;
            loadQuestion();
        };

        // Hàm hiển thị kết quả cuối cùng
        function showResults() {
            // Dừng nhạc nền khi hoàn thành
            audioBackground.pause();
            audioBackground.currentTime = 0; 
            
            document.getElementById('quiz-area').style.display = 'none';
            finalScoreElement.textContent = `${score.toFixed(1)} / ${maxScore.toFixed(1)}`;

            let message = "";
            const percentage = (score / maxScore) * 100;

            if (percentage === 100) {
                message = "Xuất sắc! Bạn đã trả lời đúng tất cả các câu hỏi. Kiến thức của bạn rất vững vàng!";
            } else if (percentage >= 70) {
                message = "Rất tốt! Bạn có kiến thức tốt. Cố gắng thêm một chút nữa nhé!";
            } else {
                message = "Cần ôn tập thêm. Hãy xem lại kiến thức Tin học và các chiến lược tìm kiếm thông tin.";
            }
            
            resultMessageElement.textContent = message;
            resultModal.style.display = 'flex';
        }

        // Hàm chơi lại
        restartButton.onclick = () => {
            initializeGame();
        };

        // Khởi động lần đầu
        initializeGame();
    </script>
</body>
</html>
