<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ون لايف</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      min-height: 350vh;
      background: #000;
      font-family: "Cairo", sans-serif;
      color: #fff;
      text-align: center;
      overflow-x: hidden;
    }

    .star {
      position: absolute;
      width: 2px;
      height: 2px;
      background: white;
      border-radius: 50%;
      animation: twinkle linear infinite;
    }

    @keyframes twinkle {
      0% { transform: translateY(0) translateX(0) scale(1); opacity: 0.8; }
      50% { transform: translateY(-20px) translateX(10px) scale(1.2); opacity: 1; }
      100% { transform: translateY(0) translateX(0) scale(1); opacity: 0.8; }
    }

    .container {
      position: relative;
      z-index: 1;
      max-width: 650px;
      margin: 60px auto;
      background: rgba(20, 20, 20, 0.95);
      border-radius: 20px;
      padding: 25px;
      box-shadow: 0 0 25px rgba(255, 165, 0, 0.3);
    }

    h1 {
      font-size: 28px;
      margin-bottom: 25px;
      font-weight: bold;
    }

    .btn-main, .btn-secondary {
      display: inline-block;
      padding: 14px 25px;
      margin-bottom: 25px;
      background: linear-gradient(45deg, #ff8000, #ff4d00);
      color: #fff;
      font-size: 16px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      transition: 0.3s;
      font-weight: bold;
      text-decoration: none;
    }

    .btn-main:hover, .btn-secondary:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px #ff8000;
    }

    .section {
      background: rgba(40, 40, 40, 0.8);
      border-radius: 15px;
      padding: 20px;
      margin-bottom: 30px;
      text-align: right;
    }

    label {
      display: block;
      margin-bottom: 8px;
      font-weight: bold;
    }

    input, select, textarea {
      width: 100%;
      padding: 10px;
      border-radius: 10px;
      border: none;
      outline: none;
      margin-bottom: 12px;
      background: #111;
      color: #fff;
      border: 1px solid #333;
    }

    input[type="submit"] {
      background: linear-gradient(45deg, #ff8000, #ff4d00);
      cursor: pointer;
      font-weight: bold;
    }

    input[type="submit"]:hover {
      transform: scale(1.05);
      box-shadow: 0 0 15px #ff8000;
    }

    .footer {
      font-size: 12px;
      color: #aaa;
      margin-top: 20px;
    }

    .rules {
      text-align: right;
      background: rgba(60, 60, 60, 0.85);
      padding: 15px;
      border-radius: 10px;
      margin-bottom: 30px;
    }

    .rules h3 {
      margin-bottom: 10px;
    }

    .rules ul {
      padding-right: 20px;
    }

    .rules li {
      margin-bottom: 8px;
    }

    /* الصفحات المخفية افتراضياً */
    #complaint-page, #central-page, #characters-page {
      display: none;
    }

    .character-list {
      text-align: right;
      font-size: 18px;
      line-height: 2;
    }
  </style>
</head>
<body>
  <!-- نجوم متحركة -->
  <script>
    const numStars = 150;
    for(let i=0; i<numStars; i++) {
      const star = document.createElement('div');
      star.classList.add('star');
      star.style.top = Math.random() * window.innerHeight + 'px';
      star.style.left = Math.random() * window.innerWidth + 'px';
      star.style.animationDuration = (Math.random() * 5 + 5) + 's';
      star.style.width = star.style.height = (Math.random() * 2 + 1) + 'px';
      document.body.appendChild(star);
    }
  </script>

  <!-- الصفحة الرئيسية -->
  <div id="main-page" class="container">
    <h1>ون لايف</h1>
    <button class="btn-main" onclick="openCentral()">إجراء مركزي</button>

    <!-- القسم الأول - نموذج تقديم إلكتروني -->
    <div class="section">
      <h3>القسم الأول</h3>
      <p>صفحة تقديم إلكترونية</p>
      <form action="https://formspree.io/f/mzzadrlv" method="POST">
        <label>اسم شخصيتك</label>
        <input type="text" name="اسم_الشخصية" required>

        <label>في أي دولة كنت؟</label>
        <input type="text" name="الدولة" required>

        <label>أقسم بعدم الخيانة</label>
        <select name="أقسم_بعدم_الخيانة" required>
          <option value="">اختر</option>
          <option value="نعم">نعم</option>
          <option value="لا">لا</option>
        </select>

        <label>ارسل جميع حساباتك بالتواصل الاجتماعي واذكر هذا لكذا وكذا</label>
        <textarea name="حسابات_التواصل" rows="4" required></textarea>

        <input type="submit" value="إرسال">
      </form>
    </div>

    <!-- القسم الثاني -->
    <div class="section">
      <h3>القسم الثاني</h3>
      <p>لتقديم شكوى ضد شخص</p>
      <button class="btn-secondary" onclick="openComplaint()">تقديم شكوى</button>
    </div>

    <!-- القسم الجديد: شخصيات الدولة -->
    <div class="section">
      <h3>القسم الثالث</h3>
      <p>لمشاهدة شخصيات الدولة</p>
      <button class="btn-secondary" onclick="openCharacters()">شخصيات الدولة</button>
    </div>

    <!-- القوانين -->
    <div class="section rules">
      <h3>قوانين الاستخدام</h3>
      <ul>
        <li>يجب احترام جميع المستخدمين وعدم الإساءة لهم.</li>
        <li>لا يسمح بنشر أي محتوى مخالف للقانون.</li>
        <li>الموقع لا يتحمل أي مسؤولية عن المحتوى المقدم.</li>
        <li>يجب استخدام النماذج بطريقة صحيحة وعدم التلاعب بها.</li>
      </ul>
    </div>

    <p class="footer">ضع بواسطة عبادي – لا ترسل أكثر من طلب.</p>
  </div>

  <!-- صفحة تقديم الشكوى -->
  <div id="complaint-page" class="container">
    <h1>تقديم شكوى</h1>
    <form action="https://formspree.io/f/mzzadrlv" method="POST">
      <label>اسمك الكامل</label>
      <input type="text" name="اسم_المشتكي" required>

      <label>البريد الإلكتروني</label>
      <input type="email" name="البريد" required>

      <label>اسم الشخص المشتكى عليه</label>
      <input type="text" name="اسم_المشتكى_عليه" required>

      <label>الشكوى</label>
      <textarea name="الشكوى" rows="4" required></textarea>

      <input type="submit" value="إرسال الشكوى">
    </form>
    <button class="btn-secondary" onclick="goBack()">العودة للرئيسية</button>
  </div>

  <!-- صفحة الإجراء المركزي -->
  <div id="central-page" class="container">
    <h1>إجراء مركزي - تسجيل بيانات المستخدم</h1>
    <form action="https://formspree.io/f/mzzadrlv" method="POST">
      <label>اسم الشخصية</label>
      <input type="text" name="اسم_الشخصية" required>

      <label>الدولة</label>
      <input type="text" name="الدولة" required>

      <label>البريد الإلكتروني</label>
      <input type="email" name="البريد" required>

      <label>ملاحظات إضافية</label>
      <textarea name="ملاحظات" rows="3"></textarea>

      <input type="submit" value="تسجيل البيانات">
    </form>
    <button class="btn-secondary" onclick="goBack()">العودة للرئيسية</button>
  </div>

  <!-- صفحة شخصيات الدولة -->
  <div id="characters-page" class="container">
    <h1>شخصيات الدولة</h1>
    <div class="character-list">
      <p>الرئيس: مرعب</p>
      <p>رئيس الوزراء: عبادي</p>
      <p>الوزير: كرم</p>
      <p>الوزير: حسنين</p>
    </div>
    <button class="btn-secondary" onclick="goBack()">العودة للرئيسية</button>
  </div>

  <script>
    function openComplaint() {
      document.getElementById('main-page').style.display = 'none';
      document.getElementById('complaint-page').style.display = 'block';
      document.getElementById('central-page').style.display = 'none';
      document.getElementById('characters-page').style.display = 'none';
    }

    function openCentral() {
      document.getElementById('main-page').style.display = 'none';
      document.getElementById('central-page').style.display = 'block';
      document.getElementById('complaint-page').style.display = 'none';
      document.getElementById('characters-page').style.display = 'none';
    }

    function openCharacters() {
      document.getElementById('main-page').style.display = 'none';
      document.getElementById('characters-page').style.display = 'block';
      document.getElementById('central-page').style.display = 'none';
      document.getElementById('complaint-page').style.display = 'none';
    }

    function goBack() {
      document.getElementById('main-page').style.display = 'block';
      document.getElementById('complaint-page').style.display = 'none';
      document.getElementById('central-page').style.display = 'none';
      document.getElementById('characters-page').style.display = 'none';
    }
  </script>
</body>
</html>      transition: 0.3s;
      font-weight: bold;
    }

    .btn-main:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px #ff8000;
    }

    .section {
      background: rgba(40, 40, 40, 0.7);
      border-radius: 15px;
      padding: 15px;
      margin-bottom: 20px;
      text-align: right;
    }

    label {
      display: block;
      margin-bottom: 8px;
      font-weight: bold;
    }

    input, select, textarea {
      width: 100%;
      padding: 10px;
      border-radius: 10px;
      border: none;
      outline: none;
      margin-bottom: 12px;
      background: #111;
      color: #fff;
      border: 1px solid #333;
    }

    input[type="submit"] {
      background: linear-gradient(45deg, #ff8000, #ff4d00);
      cursor: pointer;
      font-weight: bold;
    }

    input[type="submit"]:hover {
      transform: scale(1.05);
      box-shadow: 0 0 15px #ff8000;
    }

    .footer {
      font-size: 12px;
      color: #aaa;
      margin-top: 15px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>ون لايف</h1>

    <button class="btn-main">اضغط هنا - إجراء مركزي</button>

    <!-- القسم الأول - نموذج تقديم -->
    <div class="section">
      <h3>القسم الأول</h3>
      <p>صفحة تقديم إلكترونية</p>
      <form action="https://formspree.io/f/mzzadrlv" method="POST">
        <label>الاسم الكامل</label>
        <input type="text" name="الاسم" required>
        
        <label>البريد الإلكتروني</label>
        <input type="email" name="البريد" required>
        
        <label>رسالتك</label>
        <textarea name="الرسالة" rows="3" required></textarea>
        
        <input type="submit" value="إرسال">
      </form>
    </div>

    <!-- القسم الثاني -->
    <div class="section">
      <h3>القسم الثاني</h3>
      <p>مستقل عن الباقي</p>
      <select>
        <option>اختيار أ</option>
        <option>اختيار ب</option>
        <option>اختيار ج</option>
      </select>
    </div>

    <!-- القسم الثالث -->
    <div class="section">
      <h3>القسم الثالث</h3>
      <p>كل خانة منفصلة بذاتها</p>
      <select>
        <option>واحد</option>
        <option>اثنان</option>
        <option>ثلاثة</option>
      </select>
    </div>

    <p class="footer">ضع بواسطة عبادي – لا ترسل أكثر من طلب.</p>
  </div>
</body>
</html>
