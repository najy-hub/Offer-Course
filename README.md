<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خاص - رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0; padding: 0; box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background-color: #fff9f0;
      color: #2c2c2c;
      line-height: 1.6;
    }

    header {
      padding: 20px;
      background-color: #fff3d4;
      text-align: center;
      border-bottom: 1px solid #e0cda9;
    }

    header h1 {
      font-size: 24px;
      color: #a67c00;
    }

    .hero {
      position: relative;
      background: url('Images/hero.png') center/cover no-repeat;
      height: 90vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    .hero::after {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-color: rgba(255, 244, 220, 0.7);
      z-index: 1;
    }

    .hero-content {
      position: relative;
      z-index: 2;
      padding: 20px;
      max-width: 800px;
    }

    .hero h2 {
      font-size: 32px;
      color: #a67c00;
      margin-bottom: 15px;
    }

    .hero p {
      font-size: 18px;
      color: #4b3f2f;
      margin-bottom: 25px;
    }

    .hero a.button {
      background-color: #ffc107;
      color: #000;
      padding: 12px 30px;
      border-radius: 8px;
      font-weight: bold;
      text-decoration: none;
      font-size: 18px;
      transition: background 0.3s ease;
    }

    .hero a.button:hover {
      background-color: #e6a800;
    }

    #video {
      padding: 40px 20px;
      text-align: center;
    }

    .video-container {
      position: relative;
      width: 100%;
      max-width: 800px;
      margin: auto;
      aspect-ratio: 16 / 9;
    }

    .video-container iframe {
      width: 100%;
      height: 100%;
      border-radius: 12px;
      border: none;
    }

    .digital-timer {
      font-size: 42px;
      font-weight: bold;
      color: #a67c00;
      background: #fff3d4;
      padding: 20px 30px;
      border-radius: 12px;
      display: inline-block;
      margin-bottom: 30px;
      box-shadow: 0 0 15px rgba(166, 124, 0, 0.2);
    }

    .subscribe-button {
      margin-top: 30px;
      padding: 14px 28px;
      background-color: #ffc107;
      color: #000;
      border: none;
      border-radius: 10px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      text-decoration: none;
      display: none;
    }

    .subscribe-button:hover {
      background-color: #e6a800;
    }

    #expired-message {
      font-size: 20px;
      color: red;
      margin-top: 30px;
    }

    footer {
      background-color: #fdf3e3;
      text-align: center;
      padding: 20px;
      font-size: 14px;
      color: #666;
      margin-top: 60px;
    }

    @media (max-width: 600px) {
      .hero h2 { font-size: 24px; }
      .hero p { font-size: 16px; }
      .digital-timer { font-size: 32px; padding: 15px 20px; }
      .subscribe-button { font-size: 16px; padding: 12px 24px; }
    }
  </style>
</head>
<body>

  <header>
    <h1>رحلة المهندس المحترف</h1>
  </header>

  <section class="hero">
    <div class="hero-content">
      <h2>عرض خاص لمدة 48 ساعة</h2>
      <p>شاهد المحاضرة وابدأ رحلتك نحو احتراف الطاقة الشمسية</p>
      <a href="#video" class="button">شــاهد الآن</a>
    </div>
  </section>

  <section id="video">
    <div id="countdown" class="digital-timer">00:00:00</div>

    <div class="video-container">
      <iframe id="lectureVideo" src="https://iframe.mediadelivery.net/embed/460802/e8b012cb-f646-4d5d-b92d-937b028bdaa2?autoplay=false&muted=false" allow="autoplay; encrypted-media" allowfullscreen loading="lazy"></iframe>
    </div>

    <div id="expired-message" style="display:none;">⛔ انتهى العرض، نلقاك في العرض القادم!</div>

    <a id="whatsappButton" href="https://wa.me/201055690849" class="subscribe-button" target="_blank">اشترك الآن عبر واتساب</a>
  </section>

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

  <script>
    function startCountdown() {
      const countdownEl = document.getElementById("countdown");
      const videoContainer = document.getElementById("video-container");
      const expiredMessage = document.getElementById("expired-message");
      const subscribeBtn = document.getElementById("whatsappButton");

      let savedTime = localStorage.getItem("offer_expiry");
      if (!savedTime) {
        const expiryTime = new Date().getTime() + 48 * 60 * 60 * 1000;
        localStorage.setItem("offer_expiry", expiryTime);
        savedTime = expiryTime;
      }

      const interval = setInterval(() => {
        const now = new Date().getTime();
        const distance = savedTime - now;

        if (distance <= 0) {
          clearInterval(interval);
          countdownEl.style.display = "none";
          videoContainer.style.display = "none";
          expiredMessage.style.display = "block";
          return;
        }

        const hours = String(Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))).padStart(2, '0');
        const minutes = String(Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))).padStart(2, '0');
        const seconds = String(Math.floor((distance % (1000 * 60)) / 1000)).padStart(2, '0');

        countdownEl.textContent = `${hours}:${minutes}:${seconds}`;
      }, 1000);

      // زر الاشتراك بعد 8 دقائق من فتح الصفحة
      setTimeout(() => {
        subscribeBtn.style.display = "inline-block";
      }, 8 * 60 * 1000);
    }

    window.onload = startCountdown;
  </script>

</body>
</html>
