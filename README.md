
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>旅遊團行程統整工具</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', 'Microsoft JhengHei', sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .container {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }
        
        header {
            text-align: center;
            padding: 20px;
            background: linear-gradient(135deg, #4b6cb7, #182848);
            color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }
        
        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 25px;
        }
        
        @media (max-width: 900px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }
        
        .form-section, .preview-section {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .section-title {
            font-size: 1.5rem;
            color: #182848;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eaeaea;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .section-title i {
            color: #4b6cb7;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }
        
        input:focus, select:focus, textarea:focus {
            border-color: #4b6cb7;
            outline: none;
        }
        
        textarea {
            min-height: 80px;
            resize: vertical;
        }
        
        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
        
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 6px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        
        .btn-primary {
            background-color: #4b6cb7;
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #3a5ca9;
        }
        
        .btn-secondary {
            background-color: #6c757d;
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #5a6268;
        }
        
        .btn-success {
            background-color: #28a745;
            color: white;
        }
        
        .btn-success:hover {
            background-color: #218838;
        }
        
        .btn-warning {
            background-color: #ffc107;
            color: #212529;
        }
        
        .btn-warning:hover {
            background-color: #e0a800;
        }
        
        .btn-danger {
            background-color: #dc3545;
            color: white;
        }
        
        .btn-danger:hover {
            background-color: #c82333;
        }
        
        .form-actions {
            display: flex;
            gap: 10px;
            margin-top: 25px;
        }
        
        .itinerary-list {
            max-height: 400px;
            overflow-y: auto;
            border: 1px solid #eee;
            border-radius: 6px;
            padding: 10px;
        }
        
        .itinerary-item {
            padding: 15px;
            margin-bottom: 12px;
            background-color: #f8f9fa;
            border-left: 4px solid #4b6cb7;
            border-radius: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .itinerary-item:hover {
            background-color: #e9ecef;
        }
        
        .item-content h4 {
            color: #182848;
            margin-bottom: 5px;
        }
        
        .item-meta {
            font-size: 0.9rem;
            color: #666;
        }
        
        .item-actions {
            display: flex;
            gap: 8px;
        }
        
        .item-actions button {
            padding: 6px 10px;
            font-size: 0.85rem;
        }
        
        .preview-container {
            background-color: #f8f9fa;
            border-radius: 8px;
            padding: 20px;
            min-height: 400px;
            max-height: 500px;
            overflow-y: auto;
        }
        
        .preview-day {
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 1px dashed #ccc;
        }
        
        .day-header {
            background-color: #182848;
            color: white;
            padding: 10px 15px;
            border-radius: 6px;
            margin-bottom: 15px;
            font-weight: 600;
        }
        
        .preview-item {
            background-color: white;
            padding: 15px;
            margin-bottom: 12px;
            border-radius: 6px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        .preview-time {
            color: #4b6cb7;
            font-weight: 600;
            margin-bottom: 5px;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .preview-activity {
            font-weight: 600;
            margin-bottom: 5px;
            color: #182848;
            font-size: 1.1rem;
        }
        
        .preview-details {
            color: #666;
            font-size: 0.95rem;
            margin-bottom: 5px;
        }
        
        .preview-cost {
            color: #28a745;
            font-weight: 600;
            margin-top: 8px;
        }
        
        .summary-section {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            margin-top: 25px;
        }
        
        @media (max-width: 768px) {
            .summary-section {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        
        .summary-box {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.05);
        }
        
        .summary-value {
            font-size: 2rem;
            font-weight: 700;
            color: #182848;
            margin: 10px 0;
        }
        
        .summary-label {
            color: #666;
            font-size: 0.9rem;
        }
        
        .cost-highlight {
            color: #28a745;
        }
        
        .export-section {
            text-align: center;
            padding: 20px;
        }
        
        .empty-message {
            text-align: center;
            padding: 40px 20px;
            color: #999;
            font-style: italic;
        }
        
        .instructions {
            background-color: #e7f1ff;
            border-left: 4px solid #4b6cb7;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 0 6px 6px 0;
        }
        
        .instructions h3 {
            color: #182848;
            margin-bottom: 10px;
        }
        
        .instructions ul {
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
        }
        
        .total-cost {
            font-size: 1.5rem;
            font-weight: 700;
            color: #28a745;
            text-align: center;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid #eee;
        }
        
        .day-group {
            margin-bottom: 30px;
        }
        
        .day-title {
            background-color: #f0f5ff;
            padding: 12px 15px;
            border-radius: 6px;
            font-weight: 600;
            color: #182848;
            margin-bottom: 15px;
            border-left: 4px solid #4b6cb7;
        }
        
        footer {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            color: #666;
            border-top: 1px solid #eee;
            font-size: 0.9rem;
        }
        
        /* 自訂天數樣式 */
        .custom-days-container {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        .custom-days-input {
            width: 80px !important;
            text-align: center;
        }
        
        .btn-sm {
            padding: 8px 16px;
            font-size: 0.9rem;
        }
        
        .day-options-container {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 10px;
        }
        
        .day-option {
            padding: 8px 12px;
            background-color: #f0f5ff;
            border: 1px solid #c5d4ff;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .day-option:hover {
            background-color: #dbe5ff;
        }
        
        .day-option.active {
            background-color: #4b6cb7;
            color: white;
            border-color: #4b6cb7;
        }
        
        /* 貨幣設定樣式 */
        .currency-settings {
            background-color: #f8f9fa;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
            border: 1px solid #e9ecef;
        }
        
        .currency-settings h3 {
            color: #182848;
            margin-bottom: 15px;
            font-size: 1.2rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .currency-toggle {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .currency-radio {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        /* 時間選擇器樣式 */
        .time-selector-container {
            position: relative;
        }
        
        .time-display {
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            background-color: white;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .time-display:hover {
            border-color: #4b6cb7;
        }
        
        .time-display.active {
            border-color: #4b6cb7;
            box-shadow: 0 0 0 3px rgba(75, 108, 183, 0.1);
        }
        
        .time-dropdown {
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 6px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            z-index: 100;
            display: none;
            max-height: 300px;
            overflow-y: auto;
        }
        
        .time-dropdown.show {
            display: block;
        }
        
        .time-period-selector {
            display: flex;
            border-bottom: 1px solid #eee;
        }
        
        .time-period-btn {
            flex: 1;
            padding: 12px;
            text-align: center;
            background: none;
            border: none;
            cursor: pointer;
            font-size: 0.9rem;
            color: #666;
        }
        
        .time-period-btn.active {
            background-color: #f0f5ff;
            color: #4b6cb7;
            font-weight: 600;
        }
        
        .time-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1px;
            background-color: #eee;
        }
        
        .time-option {
            padding: 12px 8px;
            background-color: white;
            border: none;
            cursor: pointer;
            text-align: center;
            font-size: 0.9rem;
            transition: all 0.2s;
        }
        
        .time-option:hover {
            background-color: #f0f5ff;
        }
        
        .time-option.selected {
            background-color: #4b6cb7;
            color: white;
        }
        
        .time-separator {
            padding: 12px 5px;
            background-color: white;
            text-align: center;
            font-weight: bold;
            color: #4b6cb7;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        /* 地圖連結樣式 */
        .map-link {
            color: #4b6cb7;
            text-decoration: none;
            font-size: 0.9rem;
            display: inline-flex;
            align-items: center;
            gap: 5px;
            margin-top: 5px;
        }
        
        .map-link:hover {
            text-decoration: underline;
        }
        
        .map-icon {
            color: #dc3545;
        }
        
        /* 匯出選項樣式 */
        .export-options {
            display: flex;
            gap: 10px;
            justify-content: center;
            margin-top: 15px;
        }
        
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            color: white;
            display: none;
        }
        
        .loading-spinner {
            border: 5px solid #f3f3f3;
            border-top: 5px solid #4b6cb7;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin-bottom: 20px;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* 預覽中的地圖連結 */
        .preview-location {
            display: flex;
            align-items: center;
            gap: 5px;
            margin-bottom: 5px;
        }
        
        /* 時間範圍顯示 */
        .time-range {
            font-size: 1rem;
        }
        
        .time-edit-icon {
            color: #666;
        }
        
        /* 介紹欄位樣式 */
        .intro-group {
            margin-top: 5px;
        }
        
        .intro-textarea {
            min-height: 120px;
        }
    </style>
</head>
<body>
    <div class="loading-overlay" id="loadingOverlay">
        <div class="loading-spinner"></div>
        <p>正在產生檔案，請稍候...</p>
    </div>
    
    <div class="container">
        <header>
            <h1><i class="fas fa-route"></i> 旅遊團行程統整工具</h1>
            <p class="subtitle">輕鬆規劃、管理並分享您的精彩旅程</p>
        </header>
        
        <div class="instructions">
            <h3><i class="fas fa-info-circle"></i> 使用說明</h3>
            <ul>
                <li>在左側表單中填寫行程細節，然後點擊「新增行程」</li>
                <li>點擊時間選擇器，用滑鼠選擇開始和結束時間（半小時為單位）</li>
                <li>可以在下方清單中編輯或刪除已建立的行程項目</li>
                <li>地點可輸入地址或地標，系統會自動產生地圖連結</li>
                <li>「介紹」欄位可詳細說明該地點的特色、歷史背景等資訊</li>
                <li>完成後點擊「列印行程表」獲得專業的行程手冊</li>
            </ul>
        </div>
        
        <div class="main-content">
            <div class="form-section">
                <!-- 貨幣設定 -->
                <div class="currency-settings">
                    <h3><i class="fas fa-money-bill-wave"></i> 貨幣顯示設定</h3>
                    <div class="currency-toggle">
                        <div class="currency-radio">
                            <input type="radio" id="currencyTWD" name="currency" value="TWD" checked>
                            <label for="currencyTWD">新台幣 (NTD)</label>
                        </div>
                        <div class="currency-radio">
                            <input type="radio" id="currencyAUD" name="currency" value="AUD">
                            <label for="currencyAUD">澳幣 (AUD)</label>
                        </div>
                    </div>
                </div>
                
                <h2 class="section-title"><i class="fas fa-calendar-plus"></i> 新增行程項目</h2>
                
                <div class="form-group">
                    <label for="day">旅遊天數</label>
                    <div class="custom-days-container">
                        <div style="flex: 1;">
                            <select id="day">
                                <!-- 選項將由JavaScript動態生成 -->
                            </select>
                        </div>
                        <button id="customizeDaysBtn" class="btn btn-secondary btn-sm">
                            <i class="fas fa-cog"></i> 自訂天數
                        </button>
                    </div>
                    <div id="dayOptionsContainer" class="day-options-container" style="display: none;">
                        <!-- 天數選項將由JavaScript動態生成 -->
                    </div>
                </div>
                
                <div class="form-group">
                    <label>時間</label>
                    <div class="time-selector-container">
                        <div class="time-display" id="timeDisplay">
                            <span class="time-range" id="timeRange">請選擇時間</span>
                            <i class="fas fa-chevron-down time-edit-icon"></i>
                        </div>
                        <div class="time-dropdown" id="timeDropdown">
                            <div class="time-period-selector">
                                <button class="time-period-btn active" data-period="start">開始時間</button>
                                <button class="time-period-btn" data-period="end">結束時間</button>
                            </div>
                            <div class="time-grid" id="timeGrid">
                                <!-- 時間選項將由JavaScript動態生成 -->
                            </div>
                        </div>
                    </div>
                    <input type="hidden" id="startTime" value="">
                    <input type="hidden" id="endTime" value="">
                </div>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="activity">活動名稱</label>
                        <input type="text" id="activity" placeholder="例如: 故宮博物院導覽">
                    </div>
                    <div class="form-group">
                        <label for="cost">每人費用</label>
                        <div style="display: flex; align-items: center; gap: 10px;">
                            <input type="number" id="cost" min="0" placeholder="例如: 500" value="0" style="flex: 1;">
                            <span id="costCurrency" style="color: #4b6cb7; font-weight: 600; min-width: 60px;">NTD</span>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="location">地點</label>
                    <input type="text" id="location" placeholder="例如: 台北市士林區至善路二段221號">
                    <div style="font-size: 0.8rem; color: #666; margin-top: 5px;">
                        輸入地址或地標，系統會自動產生Google地圖連結
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="description">活動說明</label>
                    <textarea id="description" placeholder="詳細說明活動內容、注意事項、攜帶物品等"></textarea>
                </div>
                
                <div class="form-group intro-group">
                    <label for="introduction">地點介紹</label>
                    <textarea id="introduction" class="intro-textarea" placeholder="詳細介紹這個地點的特色、歷史背景、參觀重點、有趣的故事等"></textarea>
                    <div style="font-size: 0.8rem; color: #666; margin-top: 5px;">
                        此介紹會出現在列印版面的詳細介紹頁面中
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="transportation">交通方式</label>
                    <select id="transportation">
                        <option value="步行">步行</option>
                        <option value="遊覽車">遊覽車</option>
                        <option value="輕軌">輕軌</option>
                        <option value="火車">火車</option>
                        <option value="高鐵">高鐵</option>
                        <option value="捷運">捷運</option>
                        <option value="計程車">計程車</option>
                        <option value="飛機">飛機</option>
                        <option value="輪船">輪船</option>
                        <option value="其他">其他</option>
                    </select>
                </div>
                
                <div class="form-actions">
                    <button id="addBtn" class="btn btn-primary"><i class="fas fa-plus"></i> 新增行程</button>
                    <button id="clearBtn" class="btn btn-secondary"><i class="fas fa-trash-alt"></i> 清除表單</button>
                </div>
                
                <h2 class="section-title" style="margin-top: 30px;"><i class="fas fa-list"></i> 行程清單</h2>
                <div id="itineraryList" class="itinerary-list">
                    <div class="empty-message">目前還沒有行程項目，請新增您的第一項行程！</div>
                </div>
            </div>
            
            <div class="preview-section">
                <h2 class="section-title"><i class="fas fa-eye"></i> 行程預覽</h2>
                <div id="preview" class="preview-container">
                    <div class="empty-message">行程預覽將在此顯示</div>
                </div>
                
                <div class="summary-section">
                    <div class="summary-box">
                        <div class="summary-label">旅遊天數</div>
                        <div id="totalDays" class="summary-value">0</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">行程項目</div>
                        <div id="totalItems" class="summary-value">0</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">總費用</div>
                        <div id="totalCost" class="summary-value cost-highlight">NT$ 0</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">主要交通</div>
                        <div id="mainTransport" class="summary-value">--</div>
                    </div>
                </div>
                
                <div class="export-section">
                    <button id="printBtn" class="btn btn-success" style="padding: 15px 30px; font-size: 1.1rem;">
                        <i class="fas fa-print"></i> 列印行程手冊
                    </button>
                    <div class="export-options">
                        <button id="exportHtmlBtn" class="btn btn-secondary">
                            <i class="fas fa-file-code"></i> 匯出為HTML
                        </button>
                        <button id="shareBtn" class="btn btn-warning">
                            <i class="fas fa-share-alt"></i> 分享行程
                        </button>
                    </div>
                    <p style="margin-top: 15px; color: #666; font-size: 0.9rem;">列印專業行程手冊，包含封面、行程總覽和詳細介紹</p>
                </div>
            </div>
        </div>
        
        <footer>
            <p>旅遊團行程統整工具 &copy; <span id="currentYear"></span> | 專為旅遊團總召設計</p>
        </footer>
    </div>

    <script>
        // 行程資料儲存
        let itineraryItems = JSON.parse(localStorage.getItem('tourItinerary')) || [];
        let totalDays = 7; // 預設天數
        let isCustomizingDays = false;
        let currentCurrency = 'TWD'; // 預設貨幣
        
        // 時間選擇相關變數
        let currentTimePeriod = 'start'; // 'start' 或 'end'
        let selectedStartTime = '';
        let selectedEndTime = '';
        
        // DOM元素
        const daySelect = document.getElementById('day');
        const timeDisplay = document.getElementById('timeDisplay');
        const timeRange = document.getElementById('timeRange');
        const timeDropdown = document.getElementById('timeDropdown');
        const timeGrid = document.getElementById('timeGrid');
        const startTimeInput = document.getElementById('startTime');
        const endTimeInput = document.getElementById('endTime');
        const activityInput = document.getElementById('activity');
        const locationInput = document.getElementById('location');
        const descriptionInput = document.getElementById('description');
        const introductionInput = document.getElementById('introduction');
        const costInput = document.getElementById('cost');
        const costCurrencySpan = document.getElementById('costCurrency');
        const transportationInput = document.getElementById('transportation');
        const currencyTWD = document.getElementById('currencyTWD');
        const currencyAUD = document.getElementById('currencyAUD');
        
        const addBtn = document.getElementById('addBtn');
        const clearBtn = document.getElementById('clearBtn');
        const exportHtmlBtn = document.getElementById('exportHtmlBtn');
        const printBtn = document.getElementById('printBtn');
        const shareBtn = document.getElementById('shareBtn');
        const customizeDaysBtn = document.getElementById('customizeDaysBtn');
        const dayOptionsContainer = document.getElementById('dayOptionsContainer');
        const itineraryList = document.getElementById('itineraryList');
        const preview = document.getElementById('preview');
        const totalDaysEl = document.getElementById('totalDays');
        const totalItemsEl = document.getElementById('totalItems');
        const totalCostEl = document.getElementById('totalCost');
        const mainTransportEl = document.getElementById('mainTransport');
        const loadingOverlay = document.getElementById('loadingOverlay');
        const currentYearEl = document.getElementById('currentYear');
        
        // 匯率常數 (簡單固定匯率)
        const EXCHANGE_RATE = 21.5; // 1 AUD = 21.5 NTD
        
        // 初始化
        document.addEventListener('DOMContentLoaded', function() {
            // 設定版權年份
            currentYearEl.textContent = new Date().getFullYear();
            
            // 載入保存的設定
            const savedDays = localStorage.getItem('tourTotalDays');
            if (savedDays) {
                totalDays = parseInt(savedDays);
            }
            
            const savedCurrency = localStorage.getItem('tourCurrency');
            if (savedCurrency) {
                currentCurrency = savedCurrency;
                if (currentCurrency === 'TWD') {
                    currencyTWD.checked = true;
                } else {
                    currencyAUD.checked = true;
                }
                updateCurrencyDisplay();
            }
            
            // 初始化時間選擇器
            initializeTimeSelector();
            
            // 初始化天數選項
            initializeDayOptions();
            
            // 更新顯示
            renderItineraryList();
            updatePreview();
            updateSummary();
            
            // 設定事件監聽器
            setupEventListeners();
        });
        
        // 初始化時間選擇器
        function initializeTimeSelector() {
            // 生成時間選項 (從 06:00 到 23:30，每半小時)
            let timeOptionsHTML = '';
            for (let hour = 6; hour < 24; hour++) {
                for (let minute of ['00', '30']) {
                    const timeString = `${hour.toString().padStart(2, '0')}:${minute}`;
                    timeOptionsHTML += `<button class="time-option" data-time="${timeString}">${timeString}</button>`;
                }
            }
            
            timeGrid.innerHTML = timeOptionsHTML;
            
            // 設定預設時間 (09:00 和 10:30)
            selectedStartTime = '09:00';
            selectedEndTime = '10:30';
            updateTimeDisplay();
            
            // 設定時間選項點擊事件
            document.querySelectorAll('.time-option').forEach(option => {
                option.addEventListener('click', function() {
                    const time = this.dataset.time;
                    
                    if (currentTimePeriod === 'start') {
                        selectedStartTime = time;
                        // 如果結束時間早於開始時間，自動調整結束時間
                        if (selectedEndTime && compareTimes(selectedEndTime, selectedStartTime) <= 0) {
                            // 增加1.5小時
                            const [hour, minute] = selectedStartTime.split(':').map(Number);
                            let newHour = hour + 1;
                            let newMinute = minute + 30;
                            
                            if (newMinute >= 60) {
                                newHour += 1;
                                newMinute -= 60;
                            }
                            
                            if (newHour >= 24) newHour = 23;
                            
                            selectedEndTime = `${newHour.toString().padStart(2, '0')}:${newMinute.toString().padStart(2, '0')}`;
                        }
                    } else {
                        selectedEndTime = time;
                        // 如果開始時間晚於結束時間，自動調整開始時間
                        if (selectedStartTime && compareTimes(selectedStartTime, selectedEndTime) >= 0) {
                            // 減少1.5小時
                            const [hour, minute] = selectedEndTime.split(':').map(Number);
                            let newHour = hour - 1;
                            let newMinute = minute - 30;
                            
                            if (newMinute < 0) {
                                newHour -= 1;
                                newMinute += 60;
                            }
                            
                            if (newHour < 6) newHour = 6;
                            
                            selectedStartTime = `${newHour.toString().padStart(2, '0')}:${newMinute.toString().padStart(2, '0')}`;
                        }
                    }
                    
                    updateTimeDisplay();
                    updateTimeSelection();
                });
            });
            
            // 設定時間段切換事件
            document.querySelectorAll('.time-period-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    currentTimePeriod = this.dataset.period;
                    
                    // 更新按鈕狀態
                    document.querySelectorAll('.time-period-btn').forEach(b => {
                        b.classList.remove('active');
                    });
                    this.classList.add('active');
                    
                    updateTimeSelection();
                });
            });
        }
        
        // 比較時間大小
        function compareTimes(time1, time2) {
            const [h1, m1] = time1.split(':').map(Number);
            const [h2, m2] = time2.split(':').map(Number);
            
            if (h1 !== h2) return h1 - h2;
            return m1 - m2;
        }
        
        // 更新時間顯示
        function updateTimeDisplay() {
            if (selectedStartTime && selectedEndTime) {
                timeRange.textContent = `${selectedStartTime} - ${selectedEndTime}`;
                startTimeInput.value = selectedStartTime;
                endTimeInput.value = selectedEndTime;
            } else if (selectedStartTime) {
                timeRange.textContent = `${selectedStartTime} - 請選擇結束時間`;
                startTimeInput.value = selectedStartTime;
            } else if (selectedEndTime) {
                timeRange.textContent = `請選擇開始時間 - ${selectedEndTime}`;
                endTimeInput.value = selectedEndTime;
            } else {
                timeRange.textContent = '請選擇時間';
            }
        }
        
        // 更新時間選擇器中的選中狀態
        function updateTimeSelection() {
            // 清除所有選中狀態
            document.querySelectorAll('.time-option').forEach(option => {
                option.classList.remove('selected');
            });
            
            // 設定選中狀態
            if (currentTimePeriod === 'start' && selectedStartTime) {
                const startOption = document.querySelector(`.time-option[data-time="${selectedStartTime}"]`);
                if (startOption) startOption.classList.add('selected');
            } else if (currentTimePeriod === 'end' && selectedEndTime) {
                const endOption = document.querySelector(`.time-option[data-time="${selectedEndTime}"]`);
                if (endOption) endOption.classList.add('selected');
            }
        }
        
        // 設定事件監聽器
        function setupEventListeners() {
            // 時間顯示點擊事件
            timeDisplay.addEventListener('click', function() {
                timeDropdown.classList.toggle('show');
                timeDisplay.classList.toggle('active');
            });
            
            // 點擊頁面其他地方關閉時間選擇器
            document.addEventListener('click', function(event) {
                if (!timeDisplay.contains(event.target) && !timeDropdown.contains(event.target)) {
                    timeDropdown.classList.remove('show');
                    timeDisplay.classList.remove('active');
                }
            });
        }
        
        // 初始化天數選項
        function initializeDayOptions() {
            // 清除現有選項
            daySelect.innerHTML = '';
            dayOptionsContainer.innerHTML = '';
            
            // 建立選項
            for (let i = 1; i <= totalDays; i++) {
                const option = document.createElement('option');
                option.value = i;
                option.textContent = `第${i}天`;
                daySelect.appendChild(option);
                
                // 建立自訂天數選項按鈕
                const dayOption = document.createElement('div');
                dayOption.className = 'day-option';
                dayOption.textContent = `第${i}天`;
                dayOption.dataset.day = i;
                
                dayOption.addEventListener('click', function() {
                    daySelect.value = i;
                    // 移除所有active類別
                    document.querySelectorAll('.day-option').forEach(opt => {
                        opt.classList.remove('active');
                    });
                    // 為當前選項添加active類別
                    this.classList.add('active');
                });
                
                dayOptionsContainer.appendChild(dayOption);
            }
            
            // 設定第一天為active
            if (dayOptionsContainer.children.length > 0) {
                dayOptionsContainer.children[0].classList.add('active');
            }
        }
        
        // 切換自訂天數模式
        customizeDaysBtn.addEventListener('click', function() {
            isCustomizingDays = !isCustomizingDays;
            
            if (isCustomizingDays) {
                // 顯示自訂天數介面
                dayOptionsContainer.style.display = 'flex';
                this.innerHTML = '<i class="fas fa-check"></i> 完成設定';
                this.classList.add('btn-primary');
                this.classList.remove('btn-secondary');
                
                // 建立天數輸入框
                const existingInput = document.querySelector('.custom-days-input-container');
                if (!existingInput) {
                    const inputContainer = document.createElement('div');
                    inputContainer.className = 'custom-days-input-container';
                    inputContainer.style.display = 'flex';
                    inputContainer.style.gap = '10px';
                    inputContainer.style.marginTop = '10px';
                    
                    const input = document.createElement('input');
                    input.type = 'number';
                    input.min = '1';
                    input.max = '30';
                    input.value = totalDays;
                    input.className = 'custom-days-input';
                    input.placeholder = '輸入天數';
                    
                    const updateBtn = document.createElement('button');
                    updateBtn.className = 'btn btn-primary btn-sm';
                    updateBtn.innerHTML = '<i class="fas fa-sync-alt"></i> 更新';
                    
                    updateBtn.addEventListener('click', function() {
                        const newTotalDays = parseInt(input.value);
                        if (newTotalDays >= 1 && newTotalDays <= 30) {
                            totalDays = newTotalDays;
                            localStorage.setItem('tourTotalDays', totalDays);
                            initializeDayOptions();
                            renderItineraryList();
                            updatePreview();
                            updateSummary();
                        } else {
                            alert('請輸入1到30之間的天數');
                        }
                    });
                    
                    inputContainer.appendChild(input);
                    inputContainer.appendChild(updateBtn);
                    dayOptionsContainer.parentNode.insertBefore(inputContainer, dayOptionsContainer.nextSibling);
                }
            } else {
                // 隱藏自訂天數介面
                dayOptionsContainer.style.display = 'none';
                this.innerHTML = '<i class="fas fa-cog"></i> 自訂天數';
                this.classList.remove('btn-primary');
                this.classList.add('btn-secondary');
                
                // 移除輸入框
                const inputContainer = document.querySelector('.custom-days-input-container');
                if (inputContainer) {
                    inputContainer.remove();
                }
            }
        });
        
        // 更新貨幣顯示
        function updateCurrencyDisplay() {
            if (currentCurrency === 'TWD') {
                costCurrencySpan.textContent = 'NTD';
            } else {
                costCurrencySpan.textContent = 'AUD';
            }
            
            // 更新預覽和統計
            renderItineraryList();
            updatePreview();
            updateSummary();
        }
        
        // 貨幣切換事件
        currencyTWD.addEventListener('change', function() {
            if (this.checked) {
                currentCurrency = 'TWD';
                localStorage.setItem('tourCurrency', currentCurrency);
                updateCurrencyDisplay();
            }
        });
        
        currencyAUD.addEventListener('change', function() {
            if (this.checked) {
                currentCurrency = 'AUD';
                localStorage.setItem('tourCurrency', currentCurrency);
                updateCurrencyDisplay();
            }
        });
        
        // 貨幣轉換函數
        function convertCurrency(amount, fromCurrency, toCurrency) {
            if (fromCurrency === toCurrency) {
                return amount;
            }
            
            if (fromCurrency === 'AUD' && toCurrency === 'TWD') {
                return amount * EXCHANGE_RATE;
            } else if (fromCurrency === 'TWD' && toCurrency === 'AUD') {
                return amount / EXCHANGE_RATE;
            }
            
            return amount;
        }
        
        // 格式化貨幣顯示
        function formatCurrency(amount, currency) {
            if (currency === 'TWD') {
                return `NT$ ${Math.round(amount).toLocaleString()}`;
            } else {
                return `A$ ${amount.toFixed(2)}`;
            }
        }
        
        // 產生地圖連結
        function generateMapLink(location) {
            if (!location || location.trim() === '') {
                return null;
            }
            
            // 編碼地點為URL格式
            const encodedLocation = encodeURIComponent(location.trim());
            return `https://www.google.com/maps/search/?api=1&query=${encodedLocation}`;
        }
        
        // 計算時間差（小時）
        function calculateDuration(startTime, endTime) {
            if (!startTime || !endTime) return 0;
            
            const [startHour, startMinute] = startTime.split(':').map(Number);
            const [endHour, endMinute] = endTime.split(':').map(Number);
            
            let durationHours = endHour - startHour;
            let durationMinutes = endMinute - startMinute;
            
            if (durationMinutes < 0) {
                durationHours -= 1;
                durationMinutes += 60;
            }
            
            // 轉換為小數（以0.5小時為單位）
            const totalMinutes = durationHours * 60 + durationMinutes;
            return Math.round(totalMinutes / 30) * 0.5;
        }
        
        // 新增行程項目
        addBtn.addEventListener('click', function() {
            // 驗證必要欄位
            if (!activityInput.value.trim()) {
                alert('請填寫活動名稱');
                activityInput.focus();
                return;
            }
            
            if (!selectedStartTime || !selectedEndTime) {
                alert('請選擇開始時間和結束時間');
                timeDisplay.click();
                return;
            }
            
            // 計算時長
            const duration = calculateDuration(selectedStartTime, selectedEndTime);
            if (duration <= 0) {
                alert('結束時間必須晚於開始時間');
                return;
            }
            
            // 建立行程項目物件
            const item = {
                id: Date.now(), // 使用時間戳記作為唯一ID
                day: parseInt(daySelect.value),
                startTime: selectedStartTime,
                endTime: selectedEndTime,
                time: `${selectedStartTime} - ${selectedEndTime}`,
                duration: duration,
                activity: activityInput.value.trim(),
                location: locationInput.value.trim(),
                description: descriptionInput.value.trim(),
                introduction: introductionInput.value.trim(), // 新增的介紹欄位
                cost: parseFloat(costInput.value),
                costCurrency: currentCurrency, // 儲存輸入時的貨幣
                transportation: transportationInput.value
            };
            
            // 加入陣列
            itineraryItems.push(item);
            
            // 儲存到localStorage
            saveToLocalStorage();
            
            // 更新顯示
            renderItineraryList();
            updatePreview();
            updateSummary();
            
            // 清除表單
            clearForm();
            
            // 提示成功
            alert('行程項目已新增！');
        });
        
        // 清除表單
        clearBtn.addEventListener('click', clearForm);
        
        function clearForm() {
            // 重置時間
            selectedStartTime = '09:00';
            selectedEndTime = '10:30';
            updateTimeDisplay();
            updateTimeSelection();
            
            activityInput.value = '';
            locationInput.value = '';
            descriptionInput.value = '';
            introductionInput.value = '';
            costInput.value = '0';
            
            activityInput.focus();
        }
        
        // 刪除行程項目
        function deleteItem(id) {
            if (confirm('確定要刪除這個行程項目嗎？')) {
                itineraryItems = itineraryItems.filter(item => item.id !== id);
                saveToLocalStorage();
                renderItineraryList();
                updatePreview();
                updateSummary();
            }
        }
        
        // 編輯行程項目
        function editItem(id) {
            const item = itineraryItems.find(item => item.id === id);
            if (!item) return;
            
            // 將資料填入表單
            daySelect.value = item.day;
            
            // 設定時間
            selectedStartTime = item.startTime || item.time.split(' - ')[0];
            selectedEndTime = item.endTime || item.time.split(' - ')[1];
            updateTimeDisplay();
            updateTimeSelection();
            
            activityInput.value = item.activity;
            locationInput.value = item.location;
            descriptionInput.value = item.description;
            introductionInput.value = item.introduction || '';
            costInput.value = item.cost;
            transportationInput.value = item.transportation;
            
            // 設定貨幣
            if (item.costCurrency) {
                currentCurrency = item.costCurrency;
                if (currentCurrency === 'TWD') {
                    currencyTWD.checked = true;
                } else {
                    currencyAUD.checked = true;
                }
                updateCurrencyDisplay();
            }
            
            // 刪除該項目，因為我們將用編輯後的版本替換它
            itineraryItems = itineraryItems.filter(item => item.id !== id);
            renderItineraryList();
            updatePreview();
            updateSummary();
            
            // 聚焦到活動名稱欄位
            activityInput.focus();
        }
        
        // 渲染行程清單
        function renderItineraryList() {
            if (itineraryItems.length === 0) {
                itineraryList.innerHTML = '<div class="empty-message">目前還沒有行程項目，請新增您的第一項行程！</div>';
                return;
            }
            
            // 依天數和時間排序行程項目
            itineraryItems.sort((a, b) => {
                if (a.day !== b.day) return a.day - b.day;
                // 比較開始時間
                const aTime = parseInt(a.startTime?.split(':')[0]) || 0;
                const bTime = parseInt(b.startTime?.split(':')[0]) || 0;
                return aTime - bTime;
            });
            
            let html = '';
            itineraryItems.forEach(item => {
                // 計算顯示的金額
                let displayCost = item.cost;
                let displayCurrency = item.costCurrency;
                
                if (currentCurrency !== item.costCurrency) {
                    displayCost = convertCurrency(item.cost, item.costCurrency, currentCurrency);
                    displayCurrency = currentCurrency;
                }
                
                html += `
                <div class="itinerary-item">
                    <div class="item-content">
                        <h4>${item.activity}</h4>
                        <div class="item-meta">
                            <span>第${item.day}天 | ${item.time} | ${item.location}</span>
                            <div>費用: ${formatCurrency(displayCost, displayCurrency)} | 交通: ${item.transportation}</div>
                        </div>
                    </div>
                    <div class="item-actions">
                        <button onclick="editItem(${item.id})" class="btn btn-secondary" style="padding: 6px 10px;">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button onclick="deleteItem(${item.id})" class="btn btn-danger" style="padding: 6px 10px;">
                            <i class="fas fa-trash-alt"></i>
                        </button>
                    </div>
                </div>
                `;
            });
            
            itineraryList.innerHTML = html;
        }
        
        // 更新預覽
        function updatePreview() {
            if (itineraryItems.length === 0) {
                preview.innerHTML = '<div class="empty-message">行程預覽將在此顯示</div>';
                return;
            }
            
            // 依天數分組
            const itemsByDay = {};
            itineraryItems.forEach(item => {
                if (!itemsByDay[item.day]) {
                    itemsByDay[item.day] = [];
                }
                itemsByDay[item.day].push(item);
            });
            
            // 依天數排序
            const sortedDays = Object.keys(itemsByDay).sort((a, b) => parseInt(a) - parseInt(b));
            
            let html = '';
            sortedDays.forEach(day => {
                html += `<div class="day-group">`;
                html += `<div class="day-title">第 ${day} 天</div>`;
                
                itemsByDay[day].forEach(item => {
                    // 計算顯示的金額
                    let displayCost = item.cost;
                    let displayCurrency = item.costCurrency;
                    
                    if (currentCurrency !== item.costCurrency) {
                        displayCost = convertCurrency(item.cost, item.costCurrency, currentCurrency);
                        displayCurrency = currentCurrency;
                    }
                    
                    // 產生地圖連結
                    const mapLink = generateMapLink(item.location);
                    
                    html += `
                    <div class="preview-item">
                        <div class="preview-time">
                            <i class="far fa-clock"></i> ${item.time}
                        </div>
                        <div class="preview-activity">${item.activity}</div>
                        <div class="preview-details">
                            <div class="preview-location">
                                <i class="fas fa-map-marker-alt" style="color: #dc3545;"></i> ${item.location}
                                ${mapLink ? `<a href="${mapLink}" target="_blank" class="map-link">查看地圖</a>` : ''}
                            </div>
                            <div><i class="fas fa-bus" style="color: #4b6cb7;"></i> ${item.transportation}</div>
                            ${item.description ? `<div><i class="far fa-comment" style="color: #666;"></i> ${item.description}</div>` : ''}
                            ${item.introduction ? `<div><i class="fas fa-info-circle" style="color: #17a2b8;"></i> ${item.introduction.substring(0, 80)}${item.introduction.length > 80 ? '...' : ''}</div>` : ''}
                        </div>
                        <div class="preview-cost">費用: ${formatCurrency(displayCost, displayCurrency)}</div>
                    </div>
                    `;
                });
                
                html += `</div>`;
            });
            
            preview.innerHTML = html;
        }
        
        // 更新統計資訊
        function updateSummary() {
            if (itineraryItems.length === 0) {
                totalDaysEl.textContent = '0';
                totalItemsEl.textContent = '0';
                totalCostEl.textContent = 'NT$ 0';
                mainTransportEl.textContent = '--';
                return;
            }
            
            // 計算總天數
            const daysSet = new Set(itineraryItems.map(item => item.day));
            totalDaysEl.textContent = daysSet.size;
            
            // 計算總項目數
            totalItemsEl.textContent = itineraryItems.length;
            
            // 計算總費用（轉換為當前貨幣）
            let totalCostValue = 0;
            itineraryItems.forEach(item => {
                if (item.costCurrency === currentCurrency) {
                    totalCostValue += item.cost;
                } else {
                    totalCostValue += convertCurrency(item.cost, item.costCurrency, currentCurrency);
                }
            });
            
            // 更新費用顯示
            if (currentCurrency === 'TWD') {
                totalCostEl.textContent = `NT$ ${Math.round(totalCostValue).toLocaleString()}`;
            } else {
                totalCostEl.textContent = `A$ ${totalCostValue.toFixed(2)}`;
            }
            
            // 找出主要交通方式
            const transportCounts = {};
            itineraryItems.forEach(item => {
                if (transportCounts[item.transportation]) {
                    transportCounts[item.transportation]++;
                } else {
                    transportCounts[item.transportation] = 1;
                }
            });
            
            let mainTransport = '--';
            let maxCount = 0;
            for (const [transport, count] of Object.entries(transportCounts)) {
                if (count > maxCount) {
                    maxCount = count;
                    mainTransport = transport;
                }
            }
            
            mainTransportEl.textContent = mainTransport;
        }
        
        // 儲存到localStorage
        function saveToLocalStorage() {
            localStorage.setItem('tourItinerary', JSON.stringify(itineraryItems));
        }
        
        // 分享行程功能
        shareBtn.addEventListener('click', function() {
            if (itineraryItems.length === 0) {
                alert('請先新增行程項目再分享！');
                return;
            }
            
            // 建立分享文字
            let shareText = `旅遊行程分享\n\n`;
            shareText += `行程天數: ${new Set(itineraryItems.map(item => item.day)).size}天\n`;
            shareText += `行程項目: ${itineraryItems.length}個\n`;
            shareText += `每人總費用: ${currentCurrency === 'TWD' ? 'NT$' : 'A$'}${itineraryItems.reduce((sum, item) => sum + (item.costCurrency === currentCurrency ? item.cost : convertCurrency(item.cost, item.costCurrency, currentCurrency)), 0).toLocaleString()}\n\n`;
            
            // 依天數分組
            const itemsByDay = {};
            itineraryItems.forEach(item => {
                if (!itemsByDay[item.day]) {
                    itemsByDay[item.day] = [];
                }
                itemsByDay[item.day].push(item);
            });
            
            // 依天數排序
            const sortedDays = Object.keys(itemsByDay).sort((a, b) => parseInt(a) - parseInt(b));
            
            sortedDays.forEach(day => {
                shareText += `==== 第${day}天 ====\n`;
                itemsByDay[day].forEach(item => {
                    shareText += `${item.time} | ${item.activity}\n`;
                    shareText += `地點: ${item.location}\n`;
                    shareText += `交通: ${item.transportation}\n`;
                    shareText += `費用: ${formatCurrency(item.cost, item.costCurrency)}\n`;
                    if (item.description) {
                        shareText += `說明: ${item.description}\n`;
                    }
                    if (item.introduction) {
                        shareText += `介紹: ${item.introduction.substring(0, 100)}${item.introduction.length > 100 ? '...' : ''}\n`;
                    }
                    shareText += `\n`;
                });
            });
            
            shareText += `\n行程由旅遊團行程統整工具產生`;
            
            // 複製到剪貼簿
            navigator.clipboard.writeText(shareText).then(() => {
                alert('行程已複製到剪貼簿！\n\n您可以貼上到Line、WhatsApp等通訊軟體與團員分享。');
            }).catch(err => {
                console.error('複製失敗:', err);
                // 備用方案
                const textarea = document.createElement('textarea');
                textarea.value = shareText;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
                alert('行程已複製到剪貼簿！\n\n您可以貼上到Line、WhatsApp等通訊軟體與團員分享。');
            });
        });
        
        // 列印功能
        printBtn.addEventListener('click', function() {
            if (itineraryItems.length === 0) {
                alert('請先新增行程項目再列印！');
                return;
            }
            
            // 建立列印內容
            const printContent = generatePrintContent();
            
            // 開啟新視窗並列印
            const printWindow = window.open('', '_blank');
            printWindow.document.write(printContent);
            printWindow.document.close();
            printWindow.focus();
            
            // 等待內容載入完成後列印
            setTimeout(() => {
                printWindow.print();
                // 列印後關閉視窗（可選）
                // printWindow.close();
            }, 500);
        });
        
        // 產生列印內容（三頁式結構：封面+行程總覽+詳細介紹）
        function generatePrintContent() {
            // 依天數分組
            const itemsByDay = {};
            itineraryItems.forEach(item => {
                if (!itemsByDay[item.day]) {
                    itemsByDay[item.day] = [];
                }
                itemsByDay[item.day].push(item);
            });
            
            // 依天數排序
            const sortedDays = Object.keys(itemsByDay).sort((a, b) => parseInt(a) - parseInt(b));
            
            // 生成第一頁：封面（簡潔版）
            const coverPage = `
            <div class="print-page cover-page">
                <div class="cover-content">
                    <h1>旅遊行程手冊</h1>
                    <div class="cover-subtitle">
                        <p>${new Date().toLocaleDateString('zh-TW', { year: 'numeric', month: 'long', day: 'numeric' })}</p>
                    </div>
                </div>
            </div>
            `;
            
            // 生成第二頁：行程總覽（緊湊版）
            let itineraryOverviewHTML = '';
            sortedDays.forEach(day => {
                itineraryOverviewHTML += `
                <div class="day-section">
                    <h2 class="day-title">第 ${day} 天</h2>
                    <div class="timeline">
                `;
                
                const dayItems = itemsByDay[day];
                // 按開始時間排序
                dayItems.sort((a, b) => compareTimes(a.startTime, b.startTime));
                
                dayItems.forEach((item, index) => {
                    itineraryOverviewHTML += `
                    <div class="timeline-item">
                        <div class="timeline-time">${item.startTime}</div>
                        <div class="timeline-content">
                            <div class="timeline-activity">${item.activity}</div>
                            <div class="timeline-location">${item.location}</div>
                            <div class="timeline-transport">${item.transportation}</div>
                        </div>
                    </div>
                    `;
                });
                
                itineraryOverviewHTML += `
                    </div>
                </div>
                `;
            });
            
            const overviewPage = `
            <div class="print-page overview-page">
                <div class="page-header">
                    <h2>行程總覽</h2>
                </div>
                ${itineraryOverviewHTML}
            </div>
            `;
            
            // 生成第三頁及以後：極簡版詳細介紹
            let detailPagesHTML = '';
            let pageCount = 3; // 從第3頁開始
            
            sortedDays.forEach(day => {
                const dayItems = itemsByDay[day];
                // 按開始時間排序
                dayItems.sort((a, b) => compareTimes(a.startTime, b.startTime));
                
                dayItems.forEach((item, index) => {
                    const mapLink = generateMapLink(item.location);
                    
                    detailPagesHTML += `
                    <div class="print-page detail-page">
                        <div class="page-header">
                            <h2>第 ${day} 天：${item.activity}</h2>
                            <div class="page-subtitle">
                                <span class="subtitle-item">${item.time}</span>
                                <span class="subtitle-item">${item.location}</span>
                            </div>
                        </div>
                        
                        <div class="detail-info">
                            <div class="info-row">
                                <span class="info-label">交通方式</span>
                                <span class="info-value">${item.transportation}</span>
                            </div>
                        </div>
                        
                        <div class="detail-content">
                            <div class="content-section">
                                <h3>活動說明</h3>
                                <div class="content-box">
                                    ${item.description ? `<p>${item.description}</p>` : '<p class="no-info">無特別說明</p>'}
                                </div>
                            </div>
                            
                            <div class="content-section">
                                <h3>地點介紹</h3>
                                <div class="content-box">
                                    ${item.introduction ? `<p>${item.introduction}</p>` : '<p class="no-info">無詳細介紹</p>'}
                                </div>
                            </div>
                        </div>
                        
                        <div class="page-footer">
                            <span class="page-number">第 ${pageCount} 頁</span>
                        </div>
                    </div>
                    `;
                    
                    pageCount++;
                });
            });
            
            return `
            <!DOCTYPE html>
            <html lang="zh-TW">
            <head>
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>旅遊行程手冊</title>
                <style>
                    body {
                        font-family: 'Microsoft JhengHei', 'Segoe UI', sans-serif;
                        line-height: 1.5;
                        color: #333;
                        margin: 0;
                        padding: 0;
                        background-color: white;
                    }
                    
                    /* 通用列印樣式 */
                    .print-page {
                        padding: 20px;
                        min-height: 297mm;
                        box-sizing: border-box;
                        page-break-after: always;
                        position: relative;
                    }
                    
                    @media print {
                        @page {
                            size: A4;
                            margin: 15mm;
                        }
                        
                        body {
                            margin: 0;
                            padding: 0;
                        }
                        
                        .no-print {
                            display: none !important;
                        }
                    }
                    
                    /* 封面樣式 - 極簡版 */
                    .cover-page {
                        background: linear-gradient(135deg, #182848 0%, #4b6cb7 100%);
                        color: white;
                        display: flex;
                        align-items: center;
                        justify-content: center;
                        text-align: center;
                    }
                    
                    .cover-content {
                        max-width: 600px;
                        padding: 20px;
                    }
                    
                    .cover-content h1 {
                        font-size: 48px;
                        font-weight: bold;
                        margin-bottom: 20px;
                        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
                    }
                    
                    .cover-subtitle {
                        font-size: 20px;
                        opacity: 0.9;
                        line-height: 1.5;
                    }
                    
                    /* 行程總覽頁樣式 - 緊湊版 */
                    .overview-page {
                        background-color: white;
                    }
                    
                    .page-header {
                        text-align: center;
                        margin-bottom: 20px;
                        padding-bottom: 10px;
                        border-bottom: 2px solid #4b6cb7;
                    }
                    
                    .page-header h2 {
                        font-size: 28px;
                        color: #182848;
                        margin-bottom: 5px;
                    }
                    
                    .day-section {
                        margin-bottom: 30px;
                    }
                    
                    .day-title {
                        font-size: 20px;
                        color: #182848;
                        margin-bottom: 15px;
                        padding-bottom: 8px;
                        border-bottom: 1px solid #dee2e6;
                    }
                    
                    .timeline {
                        position: relative;
                        max-width: 800px;
                        margin: 0 auto;
                    }
                    
                    .timeline-item {
                        display: flex;
                        align-items: center;
                        margin-bottom: 20px;
                        position: relative;
                    }
                    
                    .timeline-time {
                        flex: 0 0 100px;
                        font-weight: bold;
                        font-size: 16px;
                        color: #4b6cb7;
                        text-align: center;
                        padding: 8px;
                        background-color: white;
                        border-radius: 6px;
                        box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
                        z-index: 1;
                    }
                    
                    .timeline-content {
                        flex: 1;
                        padding: 15px;
                        margin-left: 15px;
                        background-color: white;
                        border-radius: 8px;
                        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
                    }
                    
                    .timeline-activity {
                        font-weight: bold;
                        font-size: 18px;
                        color: #182848;
                        margin-bottom: 5px;
                    }
                    
                    .timeline-location {
                        font-size: 14px;
                        color: #666;
                        margin-bottom: 5px;
                    }
                    
                    .timeline-transport {
                        font-size: 13px;
                        color: #4b6cb7;
                        font-weight: 600;
                    }
                    
                    /* 詳細介紹頁樣式 - 極簡版 */
                    .detail-page {
                        background-color: white;
                    }
                    
                    .page-header {
                        text-align: left;
                        margin-bottom: 15px;
                    }
                    
                    .page-header h2 {
                        font-size: 24px;
                        color: #182848;
                        margin-bottom: 5px;
                    }
                    
                    .page-subtitle {
                        display: flex;
                        flex-wrap: wrap;
                        gap: 10px;
                        align-items: center;
                        font-size: 14px;
                        color: #666;
                    }
                    
                    .subtitle-item {
                        padding: 4px 10px;
                        background-color: #f0f5ff;
                        border-radius: 15px;
                        color: #4b6cb7;
                    }
                    
                    .detail-info {
                        background-color: #f8f9fa;
                        padding: 15px;
                        border-radius: 8px;
                        margin-bottom: 20px;
                        border: 1px solid #e9ecef;
                    }
                    
                    .info-row {
                        display: flex;
                        justify-content: space-between;
                        align-items: center;
                    }
                    
                    .info-label {
                        font-weight: 600;
                        color: #666;
                    }
                    
                    .info-value {
                        font-weight: 500;
                        color: #333;
                    }
                    
                    .detail-content {
                        margin-top: 15px;
                    }
                    
                    .content-section {
                        margin-bottom: 20px;
                    }
                    
                    .content-section h3 {
                        font-size: 18px;
                        color: #182848;
                        margin-bottom: 10px;
                        padding-bottom: 5px;
                        border-bottom: 1px solid #4b6cb7;
                    }
                    
                    .content-box {
                        line-height: 1.6;
                        color: #555;
                        font-size: 14px;
                        padding: 10px;
                        background-color: #f8f9fa;
                        border-radius: 6px;
                        border: 1px solid #e9ecef;
                    }
                    
                    .no-info {
                        color: #999;
                        font-style: italic;
                    }
                    
                    .page-footer {
                        position: absolute;
                        bottom: 20px;
                        left: 20px;
                        right: 20px;
                        display: flex;
                        justify-content: space-between;
                        align-items: center;
                        padding-top: 15px;
                        border-top: 1px solid #dee2e6;
                        color: #666;
                        font-size: 12px;
                    }
                    
                    .page-number {
                        font-weight: 600;
                    }
                    
                    /* 控制按鈕樣式 */
                    .no-print {
                        text-align: center;
                        padding: 30px 20px;
                        background-color: #f8f9fa;
                        border-top: 1px solid #dee2e6;
                    }
                    
                    .print-btn {
                        padding: 12px 25px;
                        background-color: #4b6cb7;
                        color: white;
                        border: none;
                        border-radius: 6px;
                        cursor: pointer;
                        font-size: 16px;
                        font-weight: 600;
                        transition: background-color 0.3s;
                        margin-right: 10px;
                    }
                    
                    .print-btn:hover {
                        background-color: #3a5ca9;
                    }
                    
                    .close-btn {
                        padding: 12px 25px;
                        background-color: #6c757d;
                        color: white;
                        border: none;
                        border-radius: 6px;
                        cursor: pointer;
                        font-size: 16px;
                        font-weight: 600;
                        transition: background-color 0.3s;
                    }
                    
                    .close-btn:hover {
                        background-color: #5a6268;
                    }
                </style>
            </head>
            <body>
                ${coverPage}
                ${overviewPage}
                ${detailPagesHTML}
                
                <div class="no-print">
                    <p style="margin-bottom: 15px; font-size: 14px; color: #666;">行程手冊已準備完成，共 ${pageCount - 1} 頁</p>
                    <button onclick="window.print()" class="print-btn">
                        立即列印
                    </button>
                    <button onclick="window.close()" class="close-btn">
                        關閉視窗
                    </button>
                    <p style="margin-top: 15px; font-size: 12px; color: #666;">建議使用彩色印表機列印，以獲得最佳效果</p>
                </div>
            </body>
            </html>
            `;
        }
        
        // 匯出為HTML檔案（保留此功能作為備用）
        exportHtmlBtn.addEventListener('click', function() {
            if (itineraryItems.length === 0) {
                alert('請先新增行程項目再匯出！');
                return;
            }
            
            // 建立匯出的HTML內容
            const exportHTML = generateExportHtmlContent();
            
            // 建立下載連結
            const blob = new Blob([exportHTML], { type: 'text/html' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `旅遊行程手冊_${new Date().toISOString().slice(0,10)}.html`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            alert('行程手冊已匯出為HTML檔案！');
        });
        
        // 產生匯出的HTML內容（簡化版，用於HTML匯出）
        function generateExportHtmlContent() {
            // 計算統計資料
            const daysSet = new Set(itineraryItems.map(item => item.day));
            const totalDaysCount = daysSet.size;
            const totalItemsCount = itineraryItems.length;
            
            // 計算總費用（轉換為當前貨幣）
            let totalCostValue = 0;
            itineraryItems.forEach(item => {
                if (item.costCurrency === currentCurrency) {
                    totalCostValue += item.cost;
                } else {
                    totalCostValue += convertCurrency(item.cost, item.costCurrency, currentCurrency);
                }
            });
            
            // 貨幣標籤
            const currencyLabel = currentCurrency === 'TWD' ? '新台幣 (NTD)' : '澳幣 (AUD)';
            const totalCostFormatted = currentCurrency === 'TWD' 
                ? `NT$ ${Math.round(totalCostValue).toLocaleString()}`
                : `A$ ${totalCostValue.toFixed(2)}`;
            
            // 依天數分組
            const itemsByDay = {};
            itineraryItems.forEach(item => {
                if (!itemsByDay[item.day]) {
                    itemsByDay[item.day] = [];
                }
                itemsByDay[item.day].push(item);
            });
            
            // 依天數排序
            const sortedDays = Object.keys(itemsByDay).sort((a, b) => parseInt(a) - parseInt(b));
            
            // 建立行程項目HTML
            let itineraryHTML = '';
            sortedDays.forEach(day => {
                itineraryHTML += `<div class="day-group">`;
                itineraryHTML += `<div class="day-title">第 ${day} 天</div>`;
                
                // 按開始時間排序
                const dayItems = itemsByDay[day];
                dayItems.sort((a, b) => compareTimes(a.startTime, b.startTime));
                
                dayItems.forEach(item => {
                    // 計算顯示的金額
                    let displayCost = item.cost;
                    let displayCurrency = item.costCurrency;
                    
                    if (currentCurrency !== item.costCurrency) {
                        displayCost = convertCurrency(item.cost, item.costCurrency, currentCurrency);
                        displayCurrency = currentCurrency;
                    }
                    
                    const costFormatted = displayCurrency === 'TWD' 
                        ? `NT$ ${Math.round(displayCost).toLocaleString()}`
                        : `A$ ${displayCost.toFixed(2)}`;
                    
                    // 產生地圖連結
                    const mapLink = generateMapLink(item.location);
                    
                    itineraryHTML += `
                    <div class="itinerary-item">
                        <div class="item-time">${item.time}</div>
                        <div class="item-activity">${item.activity}</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> ${item.location} ${mapLink ? `<a href="${mapLink}" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a>` : ''}</div>
                            <div><strong>交通方式:</strong> ${item.transportation}</div>
                            ${item.description ? `<div><strong>活動說明:</strong> ${item.description}</div>` : ''}
                            ${item.introduction ? `<div><strong>地點介紹:</strong> ${item.introduction}</div>` : ''}
                        </div>
                        <div class="item-cost"><strong>費用:</strong> ${costFormatted}</div>
                    </div>
                    `;
                });
                
                itineraryHTML += `</div>`;
            });
            
            return `
            <!DOCTYPE html>
            <html lang="zh-TW">
            <head>
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>旅遊行程表</title>
                <style>
                    body {
                        font-family: 'Microsoft JhengHei', 'Segoe UI', sans-serif;
                        line-height: 1.6;
                        color: #333;
                        max-width: 1000px;
                        margin: 0 auto;
                        padding: 20px;
                        background-color: #f8f9fa;
                    }
                    .header {
                        text-align: center;
                        padding: 30px 0;
                        background-color: #182848;
                        color: white;
                        border-radius: 10px;
                        margin-bottom: 30px;
                    }
                    h1 {
                        margin: 0 0 10px 0;
                        font-size: 28px;
                    }
                    .currency-info {
                        text-align: center;
                        margin-bottom: 25px;
                        padding: 15px;
                        background-color: white;
                        border-radius: 8px;
                        border: 1px solid #e9ecef;
                        font-size: 16px;
                        color: #666;
                    }
                    .summary {
                        display: grid;
                        grid-template-columns: repeat(4, 1fr);
                        gap: 15px;
                        margin-bottom: 30px;
                    }
                    .summary-box {
                        background-color: white;
                        padding: 20px;
                        border-radius: 8px;
                        text-align: center;
                        border: 1px solid #e9ecef;
                    }
                    .summary-value {
                        font-size: 24px;
                        font-weight: bold;
                        color: #182848;
                        margin: 10px 0;
                    }
                    .summary-label {
                        color: #666;
                        font-size: 14px;
                        font-weight: 600;
                    }
                    .day-group {
                        margin-bottom: 40px;
                        page-break-inside: avoid;
                    }
                    .day-title {
                        background-color: #182848;
                        color: white;
                        padding: 15px 20px;
                        border-radius: 8px;
                        font-size: 20px;
                        font-weight: bold;
                        margin-bottom: 20px;
                    }
                    .itinerary-item {
                        background-color: white;
                        padding: 25px;
                        margin-bottom: 20px;
                        border-radius: 8px;
                        border: 1px solid #e9ecef;
                    }
                    .item-time {
                        color: #4b6cb7;
                        font-weight: bold;
                        font-size: 16px;
                        margin-bottom: 10px;
                    }
                    .item-activity {
                        font-weight: bold;
                        font-size: 20px;
                        margin-bottom: 15px;
                        color: #182848;
                        border-bottom: 1px solid #f0f5ff;
                        padding-bottom: 10px;
                    }
                    .item-details {
                        margin-bottom: 15px;
                        color: #555;
                        font-size: 16px;
                    }
                    .item-cost {
                        color: #28a745;
                        font-weight: bold;
                        margin-top: 15px;
                        font-size: 18px;
                        padding: 12px 15px;
                        background-color: #f8fff9;
                        border-radius: 6px;
                        border: 1px solid #d4edda;
                    }
                    .footer {
                        text-align: center;
                        margin-top: 40px;
                        padding-top: 20px;
                        border-top: 1px solid #dee2e6;
                        color: #666;
                        font-size: 14px;
                    }
                    @media print {
                        .summary {
                            grid-template-columns: repeat(2, 1fr);
                        }
                    }
                </style>
            </head>
            <body>
                <div class="header">
                    <h1>旅遊行程表</h1>
                    <p>行程統整工具匯出 | ${new Date().toLocaleDateString('zh-TW')}</p>
                </div>
                
                <div class="currency-info">
                    <p>貨幣顯示: <strong>${currencyLabel}</strong> ${currentCurrency === 'AUD' ? `| 匯率: 1 AUD = ${EXCHANGE_RATE} NTD` : ''}</p>
                </div>
                
                <div class="summary">
                    <div class="summary-box">
                        <div class="summary-label">旅遊天數</div>
                        <div class="summary-value">${totalDaysCount}</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">行程項目</div>
                        <div class="summary-value">${totalItemsCount}</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">每人總費用</div>
                        <div class="summary-value" style="color:#28a745;">${totalCostFormatted}</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">主要交通</div>
                        <div class="summary-value" style="color:#4b6cb7;">${Object.entries(itineraryItems.reduce((acc, item) => {
                            acc[item.transportation] = (acc[item.transportation] || 0) + 1;
                            return acc;
                        }, {})).sort((a,b) => b[1]-a[1])[0]?.[0] || '多種'}</div>
                    </div>
                </div>
                
                ${itineraryHTML}
                
                <div class="footer">
                    <p>本行程表由旅遊團行程統整工具產生 &copy; ${new Date().getFullYear()}</p>
                    <p>匯出時間: ${new Date().toLocaleString('zh-TW')}</p>
                </div>
            </body>
            </html>
            `;
        }
    </script>
</body>
</html>
