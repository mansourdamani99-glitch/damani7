<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>الحقني | المساعدة العاجلة على الطريق</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background: radial-gradient(ellipse at 30% 40%, #0a0f1e, #03050b);
            color: #eef5ff;
            scroll-behavior: smooth;
            overflow-x: hidden;
            position: relative;
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            opacity: 0.8;
            box-shadow: 0 0 8px rgba(255,255,200,0.8);
            animation: floatStar linear infinite;
        }

        @keyframes floatStar {
            0% { transform: translateY(0vh) translateX(0) rotate(0deg); opacity: 0.3; }
            50% { opacity: 1; }
            100% { transform: translateY(100vh) translateX(20px) rotate(360deg); opacity: 0.2; }
        }

        .container {
            position: relative;
            z-index: 2;
            max-width: 1400px;
            margin: 0 auto;
            padding: 1rem 2rem;
        }

        .glow-text {
            text-shadow: 0 0 6px #b0f0ff, 0 0 12px #4effdc, 0 0 20px #00a6c4;
        }

        h1, h2, h3, .logo { font-weight: 700; }
        h2 {
            font-size: 2rem;
            margin-bottom: 1rem;
            border-right: 4px solid #0ff;
            padding-right: 1rem;
            display: inline-block;
            text-shadow: 0 0 5px cyan;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            background: rgba(0,0,0,0.65);
            backdrop-filter: blur(12px);
            border-radius: 60px;
            padding: 0.8rem 2rem;
            margin-bottom: 2rem;
            border: 1px solid rgba(0,255,255,0.2);
            box-shadow: 0 0 20px rgba(0,180,220,0.2);
        }

        .logo i { font-size: 2rem; color: #0ff; margin-left: 0.5rem; }
        .nav-links { display: flex; gap: 1rem; flex-wrap: wrap; align-items: center; }
        .nav-links a {
            color: #eef5ff;
            text-decoration: none;
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: 40px;
            transition: 0.2s;
        }
        .nav-links a:hover, .nav-links a.active {
            background: rgba(0, 255, 255, 0.2);
            text-shadow: 0 0 6px cyan;
            box-shadow: 0 0 10px rgba(0,255,255,0.4);
        }
        .user-badge {
            background: linear-gradient(135deg, #00b8b0, #0088aa);
            border-radius: 40px;
            padding: 0.4rem 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.9rem;
        }
        .logout-btn {
            background: rgba(255,80,80,0.3);
            border: 1px solid #ff6666;
            border-radius: 30px;
            padding: 0.3rem 0.8rem;
            cursor: pointer;
            font-size: 0.8rem;
        }

        .auth-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            backdrop-filter: blur(15px);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .auth-card {
            background: rgba(10, 20, 40, 0.95);
            border-radius: 2rem;
            padding: 2rem;
            width: 90%;
            max-width: 450px;
            border: 1px solid #0ff;
            box-shadow: 0 0 50px rgba(0,255,255,0.3);
            text-align: center;
        }
        .auth-tabs {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            border-bottom: 1px solid rgba(0,255,255,0.3);
            padding-bottom: 0.5rem;
        }
        .auth-tab {
            flex: 1;
            background: transparent;
            border: none;
            color: #ccddf8;
            font-size: 1.2rem;
            padding: 0.5rem;
            cursor: pointer;
            border-radius: 30px;
        }
        .auth-tab.active {
            background: rgba(0,255,255,0.2);
            color: #0ff;
            text-shadow: 0 0 5px cyan;
        }
        .auth-input {
            width: 100%;
            padding: 0.8rem 1.2rem;
            margin: 0.8rem 0;
            background: rgba(20, 30, 55, 0.8);
            border: 1px solid rgba(0, 255, 200, 0.6);
            border-radius: 60px;
            color: white;
            font-family: 'Cairo', sans-serif;
        }
        .auth-btn {
            background: linear-gradient(95deg, #00b8b0, #0088aa);
            width: 100%;
            padding: 0.8rem;
            border-radius: 60px;
            font-weight: bold;
            margin-top: 1rem;
            color: white;
            border: none;
            cursor: pointer;
        }
        .close-modal {
            position: absolute;
            top: 20px;
            left: 20px;
            background: rgba(255,80,80,0.5);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 1.5rem;
        }
        .page { display: none; animation: fadeSlide 0.5s ease-out; background: rgba(8, 12, 25, 0.55); backdrop-filter: blur(2px); border-radius: 2rem; padding: 2rem; margin-top: 1rem; border: 1px solid rgba(0, 255, 255, 0.25); }
        .active-page { display: block; }
        @keyframes fadeSlide { from { opacity: 0; transform: translateY(15px);} to { opacity: 1; transform: translateY(0);} }
        .services-grid, .features-grid, .faq-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 1.8rem; margin-top: 2rem; }
        .card { background: rgba(0, 0, 0, 0.65); backdrop-filter: blur(5px); border-radius: 1.5rem; padding: 1.5rem; transition: 0.25s; border: 1px solid rgba(0, 255, 255, 0.3); }
        .card i { font-size: 2.5rem; color: #0ff; margin-bottom: 1rem; }
        .card:hover { transform: translateY(-8px); border-color: #0ff; box-shadow: 0 0 25px rgba(0,255,255,0.4); }
        .btn { background: linear-gradient(95deg, #00b8b0, #0088aa); border: none; padding: 0.7rem 1.4rem; border-radius: 2rem; font-weight: bold; color: white; cursor: pointer; }
        .modern-input, .modern-textarea { width: 100%; padding: 0.9rem 1.5rem; margin: 0.8rem 0; background: rgba(20, 30, 55, 0.5); border: 1px solid rgba(0, 255, 200, 0.6); border-radius: 60px; color: white; }
        .order-item { border-bottom: 1px solid cyan; padding: 1rem; margin-bottom: 0.5rem; }
        .status-badge { display: inline-block; padding: 0.2rem 1rem; border-radius: 30px; font-size: 0.75rem; font-weight: bold; }
        .status-pending { background: #f0b400; color: #1e1a00; }
        .status-progress { background: #0a6eff; color: white; }
        .status-completed { background: #00cc88; color: #002b1a; }
        .status-cancelled { background: #aa2e4e; color: white; }
        .developers-section { display: flex; justify-content: center; gap: 2.5rem; flex-wrap: wrap; margin: 1.5rem 0; }
        .dev-card { display: flex; align-items: center; gap: 0.8rem; background: rgba(0, 20, 40, 0.6); padding: 0.6rem 1.8rem; border-radius: 3rem; border: 1px solid rgba(0,255,200,0.5); }
        .fading-star { animation: starFade 1.8s infinite; }
        @keyframes starFade { 0% { opacity: 0.2; } 50% { opacity: 1; text-shadow: 0 0 15px #ffaa33; } 100% { opacity: 0.2; } }
        .dev-name { background: linear-gradient(135deg, #aaffff, #00d4ff); -webkit-background-clip: text; background-clip: text; color: transparent; }
        .footer-social { margin-top: 3rem; background: rgba(0,0,0,0.7); border-radius: 2rem; padding: 2rem; text-align: center; }
        .social-icons { display: flex; justify-content: center; gap: 2rem; margin: 1.5rem 0; }
        .social-icons a { color: #0ff; font-size: 1.5rem; }
        .loading {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: rgba(0,0,0,0.9);
            padding: 1rem 2rem;
            border-radius: 3rem;
            z-index: 2000;
            color: #0ff;
            display: none;
            font-size: 1.2rem;
            border: 1px solid #0ff;
        }
        @media (max-width: 780px) { .container { padding: 1rem; } nav { flex-direction: column; } }
    </style>
</head>
<body>
<div class="loading" id="loadingIndicator"><i class="fas fa-spinner fa-spin"></i> جاري المعالجة...</div>
<div class="stars" id="starsContainer"></div>
<div class="container">
    <nav>
        <div class="logo glow-text"><i class="fas fa-car-crash"></i> الحقني</div>
        <div class="nav-links" id="navLinks">
            <a href="#" data-page="home" class="active">🏠 الرئيسية</a>
            <a href="#" data-page="services">🛠️ الخدمات</a>
            <a href="#" data-page="request">📢 طلب مساعدة</a>
            <a href="#" data-page="myorders">📋 طلباتي</a>
            <a href="#" data-page="features">✨ الميزات</a>
            <a href="#" data-page="faq">❓ الأسئلة</a>
            <a href="#" data-page="contact">📞 تواصل</a>
            <div id="userNavArea"></div>
        </div>
    </nav>

    <div id="home" class="page active-page">
        <h2 class="glow-text">⭐ مرحباً بك في الحقني</h2>
        <p style="font-size:1.2rem;">تطبيق المساعدة العاجلة للسيارات والشاحنات في الجزائر — 24 ساعة، سرعة فائقة.</p>
        <div class="services-grid">
            <div class="card"><i class="fas fa-wrench"></i><h3>ميكانيكي متنقل</h3><p>إصلاح عاجل في موقع العطل.</p></div>
            <div class="card"><i class="fas fa-gas-pump"></i><h3>توصيل وقود</h3><p>نوصل لك الوقود أينما كنت.</p></div>
            <div class="card"><i class="fas fa-truck"></i><h3>ديبناج (سحب)</h3><p>شاحنة رفع لنقل سيارتك.</p></div>
        </div>
        <button class="btn" id="quickRequestBtnHome">📱 اطلب المساعدة الآن</button>
    </div>
    
    <div id="services" class="page">
        <h2 class="glow-text">🚛 جميع الخدمات</h2>
        <div class="services-grid">
            <div class="card"><i class="fas fa-tools"></i><h3>إصلاح ميكانيكي</h3><p>جميع أنواع الإصلاحات الميكانيكية</p></div>
            <div class="card"><i class="fas fa-tint"></i><h3>توصيل الزيوت</h3><p>زيوت المحرك والجير</p></div>
            <div class="card"><i class="fas fa-charging-station"></i><h3>توصيل الوقود</h3><p>بنزين - غازوال</p></div>
            <div class="card"><i class="fas fa-truck-moving"></i><h3>خدمة السحب</h3><p>سحب إلى أقرب ورشة</p></div>
        </div>
    </div>
    
    <div id="request" class="page">
        <h2 class="glow-text">📢 طلب مساعدة فورية</h2>
        <div class="card" style="max-width:700px; margin:1rem auto;">
            <form id="helpRequestForm">
                <label>نوع الخدمة *</label>
                <select id="serviceType" class="modern-input">
                    <option value="ميكانيكي متنقل">🔧 ميكانيكي متنقل</option>
                    <option value="توصيل وقود">⛽ توصيل وقود</option>
                    <option value="توصيل زيوت">🛢️ توصيل زيوت</option>
                    <option value="ديبناج (سحب)">🚚 ديبناج / سحب</option>
                </select>
                <label>وصف المشكلة</label>
                <textarea id="problemDesc" class="modern-textarea" placeholder="ماذا حدث؟"></textarea>
                <label>رقم هاتفك *</label>
                <input type="tel" id="phoneReq" required class="modern-input" placeholder="0555XXXXXX">
                <div style="display:flex; gap:0.5rem;">
                    <button type="button" id="getLocationBtn" class="btn" style="flex:1">📍 تحديد موقعي</button>
                    <input type="text" id="locationLink" placeholder="رابط الخريطة" class="modern-input" style="flex:2">
                </div>
                <button type="submit" class="btn" style="width:100%; margin-top:1rem;">✨ إرسال الطلب ✨</button>
            </form>
        </div>
        <p class="glow-text" style="text-align:center;">⚡ هز هاتفك للإبلاغ السريع</p>
    </div>
    
    <div id="myorders" class="page">
        <h2 class="glow-text">📋 طلباتي</h2>
        <div id="ordersContainer" class="order-list"><p style="text-align:center;">✨ سيتم عرض طلباتك بعد تسجيل الدخول ✨</p></div>
        <button id="refreshOrdersBtn" class="btn">🔄 تحديث الطلبات</button>
    </div>
    
    <div id="features" class="page">
        <h2 class="glow-text">💎 مميزات التطبيق</h2>
        <div class="features-grid">
            <div class="card"><i class="fas fa-bolt"></i><h3>هز الهاتف للتبليغ</h3><p>هز هاتفك لطلب المساعدة</p></div>
            <div class="card"><i class="fas fa-moon"></i><h3>وضع ليلي</h3><p>تصميم مريح للعين</p></div>
            <div class="card"><i class="fas fa-shield-alt"></i><h3>أمان وخصوصية</h3><p>بياناتك آمنة</p></div>
        </div>
    </div>
    
    <div id="faq" class="page">
        <h2 class="glow-text">❓ الأسئلة الشائعة</h2>
        <div class="faq-grid">
            <div class="card"><h3>كيف أطلب المساعدة؟</h3><p>اختر الخدمة وحدد موقعك.</p></div>
            <div class="card"><h3>هل التطبيق مجاني؟</h3><p>نعم مجاني بالكامل.</p></div>
        </div>
    </div>
    
    <div id="contact" class="page">
        <h2 class="glow-text">📞 تواصل مع فريق الحقني</h2>
        <div class="card">
            <p><i class="fas fa-envelope"></i> support@alhaqni.com</p>
            <div class="developers-section">
                <div class="dev-card"><span class="fading-star">⭐</span><span class="dev-name">دماني نعيمة</span></div>
                <div class="dev-card"><span class="fading-star">⭐</span><span class="dev-name">بلعدل فاطيمة</span></div>
            </div>
            <form id="reportIssue">
                <textarea placeholder="الإبلاغ عن مشكلة..." id="reportMsg" class="modern-textarea"></textarea>
                <button type="submit" class="btn">إرسال</button>
            </form>
        </div>
    </div>
    
    <div class="footer-social">
        <div class="social-icons">
            <a href="#"><i class="fab fa-facebook-f"></i></a>
            <a href="#"><i class="fab fa-instagram"></i></a>
            <a href="#"><i class="fab fa-twitter"></i></a>
        </div>
        <p>© 2025 الحقني — مساعدة الطريق بلا حدود</p>
    </div>
</div>

<div id="authModal" class="auth-modal">
    <div class="close-modal" id="closeModalBtn">✖</div>
    <div class="auth-card">
        <div class="auth-tabs">
            <button class="auth-tab active" data-auth-tab="login">تسجيل الدخول</button>
            <button class="auth-tab" data-auth-tab="signup">إنشاء حساب</button>
        </div>
        <div id="loginForm">
            <input type="email" id="loginEmail" placeholder="البريد الإلكتروني" class="auth-input" autocomplete="email">
            <input type="password" id="loginPassword" placeholder="كلمة السر" class="auth-input" autocomplete="current-password">
            <button id="doLoginBtn" class="auth-btn">دخول</button>
        </div>
        <div id="signupForm" style="display:none;">
            <input type="email" id="signupEmail" placeholder="البريد الإلكتروني" class="auth-input" autocomplete="email">
            <input type="password" id="signupPassword" placeholder="كلمة السر (4 أحرف على الأقل)" class="auth-input" autocomplete="new-password">
            <button id="doSignupBtn" class="auth-btn">إنشاء حساب</button>
        </div>
    </div>
</div>

<script>
    // ==================== رابط Google Sheets API ====================
    const GOOGLE_SHEET_URL = 'https://script.google.com/macros/s/AKfycbz6L_Z8k9p0NDKcdC608fXbgrFEmWVIycNfsK3_iG5iaMu4-NtA9_vxdajZb5Bvw-lm_g/exec';
    
    function showLoading(show) {
        const loader = document.getElementById('loadingIndicator');
        if(loader) loader.style.display = show ? 'flex' : 'none';
    }
    
    // ==================== دوال التعامل مع Google Sheets ====================
    async function addToSheet(sheetName, values) {
        try {
            showLoading(true);
            const response = await fetch(GOOGLE_SHEET_URL, {
                method: 'POST',
                mode: 'no-cors',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ action: 'add', sheet: sheetName, values: values })
            });
            showLoading(false);
            return { success: true };
        } catch (error) {
            console.error('خطأ:', error);
            showLoading(false);
            return { success: false, error: error.message };
        }
    }
    
    async function searchInSheet(sheetName, column, searchValue) {
        try {
            showLoading(true);
            const response = await fetch(GOOGLE_SHEET_URL, {
                method: 'POST',
                mode: 'cors',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ action: 'getWhere', sheet: sheetName, column: column, searchValue: searchValue })
            });
            const data = await response.json();
            showLoading(false);
            return data;
        } catch (error) {
            console.error('خطأ في البحث:', error);
            showLoading(false);
            return { success: false, data: [] };
        }
    }
    
    // ==================== نظام المستخدمين ====================
    let currentUser = null;
    let userOrders = [];
    
    // تسجيل الدخول
    async function loginWithSheet(email, password) {
        const result = await searchInSheet('users', 1, email);
        if (result.success && result.data && result.data.length > 1) {
            for(let i = 1; i < result.data.length; i++) {
                const userRow = result.data[i];
                if(userRow[1] === email && userRow[2] === btoa(password)) {
                    return { success: true, user: { id: userRow[0], email: userRow[1], rowIndex: i } };
                }
            }
        }
        return { success: false, message: 'البريد أو كلمة السر غير صحيحة' };
    }
    
    // إنشاء حساب
    async function signupWithSheet(email, password) {
        const checkResult = await searchInSheet('users', 1, email);
        if (checkResult.success && checkResult.data && checkResult.data.length > 1) {
            for(let i = 1; i < checkResult.data.length; i++) {
                if(checkResult.data[i][1] === email) {
                    return { success: false, message: 'البريد الإلكتروني مسجل بالفعل' };
                }
            }
        }
        
        if (password.length < 4) {
            return { success: false, message: 'كلمة السر يجب أن تكون 4 أحرف على الأقل' };
        }
        
        const userId = 'user_' + Date.now() + '_' + Math.random().toString(36).substr(2, 6);
        const now = new Date().toISOString();
        const values = [userId, email, btoa(password), now, now];
        
        const addResult = await addToSheet('users', values);
        if (addResult.success) {
            return { success: true, user: { id: userId, email: email } };
        }
        return { success: false, message: 'حدث خطأ في إنشاء الحساب' };
    }
    
    // حفظ الطلب محلياً (لأننا نستخدم localStorage للطلبات)
    function addOrderForCurrentUser(service, phone, location, description) {
        if(!currentUser) { 
            alert('يرجى تسجيل الدخول أولاً'); 
            openAuthModal(); 
            return null; 
        }
        const orders = JSON.parse(localStorage.getItem('haqni_orders_' + currentUser.id)) || [];
        const newOrder = { 
            id: Date.now().toString() + Math.floor(Math.random()*1000), 
            service, 
            phone, 
            location: location || 'تم تحديد الموقع', 
            description, 
            status: 'pending', 
            timestamp: new Date().toISOString() 
        };
        orders.unshift(newOrder);
        localStorage.setItem('haqni_orders_' + currentUser.id, JSON.stringify(orders));
        userOrders = orders;
        renderOrdersForCurrentUser();
        return newOrder;
    }
    
    function renderOrdersForCurrentUser() {
        const container = document.getElementById('ordersContainer');
        if(!container) return;
        if(!currentUser) { 
            container.innerHTML = '<p style="text-align:center;">🔐 يرجى تسجيل الدخول لمشاهدة طلباتك</p>'; 
            return; 
        }
        const orders = JSON.parse(localStorage.getItem('haqni_orders_' + currentUser.id)) || [];
        if(orders.length === 0) { 
            container.innerHTML = '<p style="text-align:center;">✨ لا توجد طلبات بعد. قم بتقديم طلب جديد ✨</p>'; 
            return; 
        }
        container.innerHTML = '';
        orders.slice().reverse().forEach(order => {
            let statusClass = { pending:'status-pending', in_progress:'status-progress', completed:'status-completed', cancelled:'status-cancelled' }[order.status] || 'status-pending';
            let statusText = { pending:'قيد الانتظار', in_progress:'قيد التنفيذ', completed:'مكتمل', cancelled:'ملغي' }[order.status] || 'قيد الانتظار';
            const div = document.createElement('div'); div.className = 'order-item';
            div.innerHTML = `<strong><i class="fas fa-concierge-bell"></i> ${order.service}</strong><br>📞 ${order.phone} | 📍 ${order.location}<br>📝 ${order.description || 'لا يوجد'}<br><span class="status-badge ${statusClass}">${statusText}</span><small style="float:left;">${new Date(order.timestamp).toLocaleString('ar-DZ')}</small><div style="clear:both"></div><button class="btn" style="margin-top:6px; background:#aa2e4e;" onclick="window.cancelOrderGlobal('${order.id}')">إلغاء الطلب</button>`;
            container.appendChild(div);
        });
    }
    
    window.cancelOrderGlobal = function(orderId) {
        if(!currentUser) return;
        let orders = JSON.parse(localStorage.getItem('haqni_orders_' + currentUser.id)) || [];
        const idx = orders.findIndex(o => o.id === orderId);
        if(idx !== -1 && orders[idx].status !== 'completed' && orders[idx].status !== 'cancelled') {
            orders[idx].status = 'cancelled';
            localStorage.setItem('haqni_orders_' + currentUser.id, JSON.stringify(orders));
            renderOrdersForCurrentUser();
            alert("تم إلغاء الطلب");
        } else alert("لا يمكن إلغاء هذا الطلب");
    };
    
    // Stars background
    function generateMovingStars() { 
        const starsDiv = document.getElementById('starsContainer'); 
        starsDiv.innerHTML = ''; 
        for(let i=0;i<150;i++) { 
            let star = document.createElement('div'); 
            star.classList.add('star'); 
            let size = Math.random()*2.5+1; 
            star.style.width = size+'px'; 
            star.style.height = size+'px'; 
            star.style.left = Math.random()*100+'%'; 
            star.style.top = Math.random()*100+'%'; 
            star.style.animation = `floatStar ${8+Math.random()*15}s linear infinite`; 
            starsDiv.appendChild(star); 
        } 
    }
    generateMovingStars();
    
    function updateCurrentUserSession(user) { 
        currentUser = user; 
        if(user) localStorage.setItem('haqni_session', JSON.stringify(user)); 
        else localStorage.removeItem('haqni_session'); 
    }
    
    function loadSession() { 
        const sess = localStorage.getItem('haqni_session'); 
        if(sess) { 
            currentUser = JSON.parse(sess); 
        } else { 
            currentUser = null; 
        }
        renderUserNav(); 
        renderOrdersForCurrentUser(); 
    }
    
    function logout() { 
        currentUser = null; 
        localStorage.removeItem('haqni_session'); 
        renderUserNav(); 
        showPage('home'); 
        document.getElementById('ordersContainer').innerHTML = '<p style="text-align:center;">✨ يرجى تسجيل الدخول لعرض طلباتك ✨</p>'; 
    }
    
    function renderUserNav() {
        const navArea = document.getElementById('userNavArea');
        if(!navArea) return;
        if(currentUser) {
            navArea.innerHTML = `<div class="user-badge"><i class="fas fa-user-circle"></i> ${currentUser.email.split('@')[0]} <span class="logout-btn" id="logoutBtn">خروج</span></div>`;
            document.getElementById('logoutBtn')?.addEventListener('click', logout);
        } else {
            navArea.innerHTML = `<a href="#" id="showAuthBtn">🔐 دخول / حساب جديد</a>`;
            document.getElementById('showAuthBtn')?.addEventListener('click', (e) => { e.preventDefault(); openAuthModal(); });
        }
    }
    
    // Modal Auth
    function openAuthModal() { document.getElementById('authModal').style.display = 'flex'; }
    function closeAuthModal() { document.getElementById('authModal').style.display = 'none'; }
    function switchAuthTab(tab) { 
        document.getElementById('loginForm').style.display = tab === 'login' ? 'block' : 'none'; 
        document.getElementById('signupForm').style.display = tab === 'signup' ? 'block' : 'none'; 
        document.querySelectorAll('.auth-tab').forEach(btn => btn.classList.remove('active')); 
        document.querySelector(`.auth-tab[data-auth-tab="${tab}"]`).classList.add('active'); 
    }
    
    document.getElementById('closeModalBtn')?.addEventListener('click', closeAuthModal);
    document.querySelectorAll('.auth-tab').forEach(btn => { 
        btn.addEventListener('click', (e) => { switchAuthTab(btn.getAttribute('data-auth-tab')); }); 
    });
    
    document.getElementById('doLoginBtn')?.addEventListener('click', async () => {
        const email = document.getElementById('loginEmail').value.trim(); 
        const password = document.getElementById('loginPassword').value;
        if(!email || !password) { alert('املأ البريد وكلمة السر'); return; }
        const res = await loginWithSheet(email, password);
        if(res.success) { 
            updateCurrentUserSession(res.user); 
            closeAuthModal(); 
            renderUserNav(); 
            renderOrdersForCurrentUser(); 
            showPage('home'); 
            alert(`مرحباً ${res.user.email}`); 
        } else alert(res.message);
    });
    
    document.getElementById('doSignupBtn')?.addEventListener('click', async () => {
        const email = document.getElementById('signupEmail').value.trim(); 
        const password = document.getElementById('signupPassword').value;
        if(!email || !password) { alert('املأ جميع الحقول'); return; }
        const res = await signupWithSheet(email, password);
        if(res.success) { 
            alert('تم إنشاء الحساب بنجاح، يمكنك تسجيل الدخول الآن'); 
            switchAuthTab('login'); 
            document.getElementById('loginEmail').value = email; 
            document.getElementById('loginPassword').value = ''; 
        } else alert(res.message);
    });
    
    // ربط الصفحات
    const pages = ['home','services','request','myorders','features','faq','contact'];
    function showPage(pageId) { 
        pages.forEach(p => document.getElementById(p)?.classList.remove('active-page')); 
        document.getElementById(pageId)?.classList.add('active-page'); 
        document.querySelectorAll('.nav-links a[data-page]').forEach(link => link.classList.remove('active')); 
        const activeLink = document.querySelector(`.nav-links a[data-page="${pageId}"]`); 
        if(activeLink) activeLink.classList.add('active'); 
        window.scrollTo({ top: 0 }); 
    }
    
    document.querySelectorAll('.nav-links a[data-page]').forEach(link => link.addEventListener('click', (e) => { 
        e.preventDefault(); 
        const page = link.getAttribute('data-page'); 
        if(page && pages.includes(page)) showPage(page); 
    }));
    
    document.getElementById('quickRequestBtnHome')?.addEventListener('click', () => showPage('request'));
    document.getElementById('refreshOrdersBtn')?.addEventListener('click', () => renderOrdersForCurrentUser());
    
    const helpForm = document.getElementById('helpRequestForm');
    if(helpForm) {
        helpForm.addEventListener('submit', (e) => { 
            e.preventDefault(); 
            if(!currentUser) { 
                alert('يجب تسجيل الدخول أولاً'); 
                openAuthModal(); 
                return; 
            } 
            const service = document.getElementById('serviceType').value; 
            const desc = document.getElementById('problemDesc').value; 
            const phone = document.getElementById('phoneReq').value; 
            let loc = document.getElementById('locationLink').value; 
            if(!phone) { alert('أدخل رقم الهاتف'); return; } 
            if(!loc) loc = "لم يتم تحديد الموقع"; 
            addOrderForCurrentUser(service, phone, loc, desc); 
            helpForm.reset(); 
            alert('تم إرسال الطلب بنجاح'); 
            showPage('myorders'); 
        });
    }
    
    document.getElementById('getLocationBtn')?.addEventListener('click', () => { 
        if(navigator.geolocation) 
            navigator.geolocation.getCurrentPosition(pos => { 
                document.getElementById('locationLink').value = `https://www.google.com/maps?q=${pos.coords.latitude},${pos.coords.longitude}`; 
                alert('تم تحديد الموقع'); 
            }, () => alert('فشل تحديد الموقع')); 
        else alert('غير مدعوم'); 
    });
    
    if(window.DeviceMotionEvent) { 
        let lastShake=0; 
        window.addEventListener('devicemotion', (e) => { 
            let acc = e.accelerationIncludingGravity; 
            if(acc && (Math.abs(acc.x)>15||Math.abs(acc.y)>15||Math.abs(acc.z)>15)) { 
                let now=Date.now(); 
                if(now-lastShake>1500) { 
                    lastShake=now; 
                    if(confirm('🚨 هزاز الهاتف! طلب مساعدة عاجلة؟')) { 
                        if(!currentUser) openAuthModal(); 
                        else showPage('request'); 
                    } 
                } 
            } 
        }); 
    }
    
    document.getElementById('reportIssue')?.addEventListener('submit', (e) => { 
        e.preventDefault(); 
        const msg=document.getElementById('reportMsg').value; 
        if(msg) alert(`تم استلام بلاغك: ${msg.substring(0,50)}...`); 
        else alert('أدخل نص البلاغ'); 
        e.target.reset(); 
    });
    
    loadSession();
</script>
</body>
</html>
