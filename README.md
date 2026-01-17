
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
                    <p>行程統整工具匯出 | 2026/1/17</p>
                </div>
                
                <div class="currency-info">
                    <p>貨幣顯示: <strong>新台幣 (NTD)</strong> </p>
                </div>
                
                <div class="summary">
                    <div class="summary-box">
                        <div class="summary-label">旅遊天數</div>
                        <div class="summary-value">9</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">行程項目</div>
                        <div class="summary-value">18</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">每人總費用</div>
                        <div class="summary-value" style="color:#28a745;">NT$ 56,600</div>
                    </div>
                    <div class="summary-box">
                        <div class="summary-label">主要交通</div>
                        <div class="summary-value" style="color:#4b6cb7;">輕軌</div>
                    </div>
                </div>
                
                <div class="day-group"><div class="day-title">第 1 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 10:30</div>
                        <div class="item-activity">落地布里斯本</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 布里斯本機場 <a href="https://www.google.com/maps/search/?api=1&query=%E5%B8%83%E9%87%8C%E6%96%AF%E6%9C%AC%E6%A9%9F%E5%A0%B4" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 飛機</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 28,000</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">13:00 - 18:00</div>
                        <div class="item-activity">市區晃晃+飯店</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 布里斯本市區 <a href="https://www.google.com/maps/search/?api=1&query=%E5%B8%83%E9%87%8C%E6%96%AF%E6%9C%AC%E5%B8%82%E5%8D%80" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 步行</div>
                            <div><strong>活動說明:</strong> 布里斯本市區住宿一晚估2000</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 4,000</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 2 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 18:00</div>
                        <div class="item-activity">黃金海岸+其他景點</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 黃金海岸 <a href="https://www.google.com/maps/search/?api=1&query=%E9%BB%83%E9%87%91%E6%B5%B7%E5%B2%B8" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 火車</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 3 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 18:00</div>
                        <div class="item-activity">出發陽光海岸+澳洲動物園(自駕)+飯店</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 澳洲動物園 <a href="https://www.google.com/maps/search/?api=1&query=%E6%BE%B3%E6%B4%B2%E5%8B%95%E7%89%A9%E5%9C%92" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 計程車</div>
                            <div><strong>活動說明:</strong> 從布里斯本市區移動到陽光海岸，沿路順便玩。採自駕方式。住宿一晚估2000</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 3,600</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 4 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 11:00</div>
                        <div class="item-activity">水族館看水</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> SEA LIFE Sunshine Coast <a href="https://www.google.com/maps/search/?api=1&query=SEA%20LIFE%20Sunshine%20Coast" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 火車</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 1,100</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">11:00 - 12:30</div>
                        <div class="item-activity">跟本地人吃飯</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 餐廳 <a href="https://www.google.com/maps/search/?api=1&query=%E9%A4%90%E5%BB%B3" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 捷運</div>
                            <div><strong>活動說明:</strong> 此行程還未確定時間!!!!</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">14:00 - 18:00</div>
                        <div class="item-activity">布里斯本(陽光海岸機場)飛去雪梨</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 陽光海岸機場 <a href="https://www.google.com/maps/search/?api=1&query=%E9%99%BD%E5%85%89%E6%B5%B7%E5%B2%B8%E6%A9%9F%E5%A0%B4" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 飛機</div>
                            <div><strong>活動說明:</strong> 機票未定，時間還需要調整</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 4,000</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">18:00 - 19:30</div>
                        <div class="item-activity">飯店</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 飯店 <a href="https://www.google.com/maps/search/?api=1&query=%E9%A3%AF%E5%BA%97" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 火車</div>
                            <div><strong>活動說明:</strong> 雪梨市區住宿一晚估2000，共五碗</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 10,000</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 5 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 12:00</div>
                        <div class="item-activity">雪梨市區+港灣大橋</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 港灣大橋 <a href="https://www.google.com/maps/search/?api=1&query=%E6%B8%AF%E7%81%A3%E5%A4%A7%E6%A9%8B" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 步行</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">14:00 - 18:00</div>
                        <div class="item-activity">雪梨歌劇院聽音樂</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 雪梨歌劇院 <a href="https://www.google.com/maps/search/?api=1&query=%E9%9B%AA%E6%A2%A8%E6%AD%8C%E5%8A%87%E9%99%A2" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 輕軌</div>
                            <div><strong>活動說明:</strong> 要確認演出時間和地點，目前先排在上午</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 1,500</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 6 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 18:00</div>
                        <div class="item-activity">藍山一日遊</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 藍山 <a href="https://www.google.com/maps/search/?api=1&query=%E8%97%8D%E5%B1%B1" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 遊覽車</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 3,200</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 7 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 10:30</div>
                        <div class="item-activity">聖瑪麗大教堂</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 聖瑪麗大教堂 <a href="https://www.google.com/maps/search/?api=1&query=%E8%81%96%E7%91%AA%E9%BA%97%E5%A4%A7%E6%95%99%E5%A0%82" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 輕軌</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">11:00 - 12:30</div>
                        <div class="item-activity">雪梨魚市場吃午餐</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 雪梨魚市場 <a href="https://www.google.com/maps/search/?api=1&query=%E9%9B%AA%E6%A2%A8%E9%AD%9A%E5%B8%82%E5%A0%B4" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 輕軌</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">14:00 - 18:00</div>
                        <div class="item-activity">動物園看可愛動物</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 塔龍加動物園 <a href="https://www.google.com/maps/search/?api=1&query=%E5%A1%94%E9%BE%8D%E5%8A%A0%E5%8B%95%E7%89%A9%E5%9C%92" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 輕軌</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 1,200</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 8 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 18:00</div>
                        <div class="item-activity">購買伴手禮</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 各大百貨公司 <a href="https://www.google.com/maps/search/?api=1&query=%E5%90%84%E5%A4%A7%E7%99%BE%E8%B2%A8%E5%85%AC%E5%8F%B8" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 步行</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    </div><div class="day-group"><div class="day-title">第 9 天</div>
                    <div class="itinerary-item">
                        <div class="item-time">09:00 - 12:00</div>
                        <div class="item-activity">自由安排</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 無 <a href="https://www.google.com/maps/search/?api=1&query=%E7%84%A1" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 輕軌</div>
                            <div><strong>活動說明:</strong> 目前還未確定去哪</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">14:00 - 18:00</div>
                        <div class="item-activity">雪梨飛布里斯本</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 雪梨機場國內線 <a href="https://www.google.com/maps/search/?api=1&query=%E9%9B%AA%E6%A2%A8%E6%A9%9F%E5%A0%B4%E5%9C%8B%E5%85%A7%E7%B7%9A" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 飛機</div>
                            <div><strong>活動說明:</strong> 機票未定，時間還需要調整</div>
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    
                    <div class="itinerary-item">
                        <div class="item-time">22:30 - 23:30</div>
                        <div class="item-activity">回台灣</div>
                        <div class="item-details">
                            <div><strong>地點:</strong> 布里斯本機場 <a href="https://www.google.com/maps/search/?api=1&query=%E5%B8%83%E9%87%8C%E6%96%AF%E6%9C%AC%E6%A9%9F%E5%A0%B4" target="_blank" style="color: #4b6cb7; text-decoration: none; font-size: 14px;">(查看地圖)</a></div>
                            <div><strong>交通方式:</strong> 飛機</div>
                            
                            
                        </div>
                        <div class="item-cost"><strong>費用:</strong> NT$ 0</div>
                    </div>
                    </div>
                
                <div class="footer">
                    <p>本行程表由旅遊團行程統整工具產生 &copy; 2026</p>
                    <p>匯出時間: 2026/1/17 下午11:53:05</p>
                </div>
            </body>
            </html>
            
