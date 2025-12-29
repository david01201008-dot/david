<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>房不熟 FANG BU SHU - 試用夥伴申請表單</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .loading-spinner {
            border: 3px solid rgba(255,255,255,.3);
            border-radius: 50%;
            border-top-color: #fff;
            width: 20px;
            height: 20px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin { to { transform: rotate(360deg); } }
    </style>
</head>
<body class="bg-gray-100 min-h-screen flex items-center justify-center py-12 px-4 font-sans">
    <div class="max-w-xl w-full bg-white rounded-2xl shadow-2xl overflow-hidden">
        <!-- 表單標題區 -->
        <div class="bg-emerald-700 p-8 text-white relative">
            <h1 class="text-3xl font-bold mb-1 text-center tracking-wider">房不熟</h1>
            <p class="text-emerald-200 text-center text-xs mb-4">FANG BU SHU</p>
            <div class="h-px bg-emerald-500 w-16 mx-auto mb-4"></div>
            <p class="text-emerald-100 text-center text-sm">2026 領航試用計畫：正式招募中</p>
        </div>

        <form id="applicationForm" class="p-8 space-y-5">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-1">公司名稱</label>
                    <input type="text" name="company" required placeholder="請輸入公司名稱" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none transition-all">
                </div>
                <div>
                    <label class="block text-sm font-semibold text-gray-700 mb-1">聯絡人姓名</label>
                    <input type="text" name="name" required placeholder="請輸入姓名" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none transition-all">
                </div>
            </div>

            <div>
                <label class="block text-sm font-semibold text-gray-700 mb-1">聯絡電話</label>
                <input type="tel" name="phone" required placeholder="09XX-XXX-XXX" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none transition-all">
            </div>

            <div>
                <label class="block text-sm font-semibold text-gray-700 mb-1">服務區域</label>
                <select name="region" required class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none bg-white transition-all">
                    <option value="">請選擇區域</option>
                    <option>台北市</option><option>新北市</option><option>桃園市</option>
                    <option>台中市</option><option>台南市</option><option>高雄市</option>
                </select>
            </div>

            <div>
                <label class="block text-sm font-semibold text-gray-700 mb-1">物件規模 (預計導入數量)</label>
                <div class="grid grid-cols-2 sm:grid-cols-3 gap-3 text-xs">
                    <label class="flex items-center space-x-2 border p-2.5 rounded-lg cursor-pointer hover:bg-emerald-50 transition-colors">
                        <input type="radio" name="scale" value="100以下" required> <span>100 以下</span>
                    </label>
                    <label class="flex items-center space-x-2 border p-2.5 rounded-lg cursor-pointer hover:bg-emerald-50 transition-colors">
                        <input type="radio" name="scale" value="100-200"> <span>100-200</span>
                    </label>
                    <label class="flex items-center space-x-2 border p-2.5 rounded-lg cursor-pointer hover:bg-emerald-50 transition-colors">
                        <input type="radio" name="scale" value="200-300"> <span>200-300</span>
                    </label>
                    <label class="flex items-center space-x-2 border p-2.5 rounded-lg cursor-pointer hover:bg-emerald-50 transition-colors">
                        <input type="radio" name="scale" value="300-500"> <span>300-500</span>
                    </label>
                    <label class="flex items-center space-x-2 border p-2.5 rounded-lg cursor-pointer hover:bg-emerald-50 transition-colors">
                        <input type="radio" name="scale" value="500以上"> <span>500 以上</span>
                    </label>
                </div>
            </div>

            <div>
                <label class="block text-sm font-semibold text-gray-700 mb-1">備註 (選填)</label>
                <textarea name="note" rows="2" placeholder="對功能的需求或期待..." class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none transition-all"></textarea>
            </div>

            <button type="submit" id="submitBtn" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-4 px-6 rounded-xl shadow-lg flex items-center justify-center transition-all">
                <span id="btnText">送出申請</span>
                <div id="btnLoading" class="hidden loading-spinner"></div>
            </button>
            
            <p id="errorMsg" class="hidden text-red-500 text-[10px] text-center mt-2 font-medium">連線發生問題，請稍後再試</p>
        </form>

        <!-- 成功訊息 -->
        <div id="successMessage" class="hidden p-12 text-center">
            <div class="w-20 h-20 bg-emerald-100 text-emerald-600 rounded-full flex items-center justify-center mx-auto mb-6 shadow-inner">
                <svg class="w-10 h-10" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
            </div>
            <h2 class="text-2xl font-bold text-gray-800 mb-3 text-center">申請已送出！</h2>
            <p class="text-gray-600 mb-8 text-sm leading-relaxed">
                感謝您的參與。房不熟專員將於 48 小時內聯絡您，<br>
                協助您完成後續的導入流程。
            </p>
            <button onclick="location.reload()" class="text-emerald-600 font-semibold text-sm hover:underline">返回</button>
        </div>
    </div>

    <script>
        // --- 務必確認此處已填入您的 Google Apps Script URL ---
        const scriptURL = 'https://script.google.com/macros/s/AKfycbz9NWaORwWAo_PONJFAoqyQ7LCWalYJ6HyyNNoOyqenh6c1jkTtEaK3YP8o2Y_Z-6ypOQ/exec'; 
        
        const form = document.getElementById('applicationForm');
        const submitBtn = document.getElementById('submitBtn');
        const btnText = document.getElementById('btnText');
        const btnLoading = document.getElementById('btnLoading');
        const successMessage = document.getElementById('successMessage');
        const errorMsg = document.getElementById('errorMsg');

        form.addEventListener('submit', e => {
            e.preventDefault();
            
            if (scriptURL.includes('YOUR_GOOGLE') || scriptURL === '') {
                alert('請先填入您的 Google Script URL！');
                return;
            }

            btnText.classList.add('hidden');
            btnLoading.classList.remove('hidden');
            submitBtn.disabled = true;
            errorMsg.classList.add('hidden');

            fetch(scriptURL, { 
                method: 'POST', 
                body: new FormData(form),
                mode: 'no-cors' 
            })
            .then(() => {
                form.classList.add('hidden');
                successMessage.classList.remove('hidden');
            })
            .catch(error => {
                console.error('Error!', error.message);
                btnText.classList.remove('hidden');
                btnLoading.classList.add('hidden');
                submitBtn.disabled = false;
                errorMsg.classList.remove('hidden');
                // 即使 fetch 失敗（有時因 CORS），資料可能已寫入，若您想保險起見也可直接跳轉成功
            });
        });
    </script>
</body>
</html>
