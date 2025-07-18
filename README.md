
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خاص - رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background-color: #fef9f0;
      color: #333;
      line-height: 1.6;
    }

    header {
      background-color: #fff9e5;
      padding: 20px;
      text-align: center;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    header h1 {
      font-size: 24px;
      color: #222;
    }

    .hero {
      background: url('Images/hero.png') center/cover no-repeat;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      position: relative;
    }

    .hero::after {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-color: rgba(0, 0, 0, 0.6);
    }

    .hero-content {
      position: relative;
      z-index: 2;
      color: #fff;
      padding: 20px;
    }

    .hero h2 {
      font-size: 32px;
      margin-bottom: 10px;
    }

    .hero p {
      font-size: 18px;
      margin-bottom: 20px;
    }

    .hero a.button {
      display: inline-block;
      background-color: #ffc107;
      color: #000;
      padding: 12px 30px;
      font-weight: bold;
      font-size: 18px;
      border-radius: 8px;
      text-decoration: none;
      transition: background-color 0.3s;
    }

    .hero a.button:hover {
      background-color: #e0a800;
    }

    #video {
      padding: 40px 20px;
      text-align: center;
    }

    .digital-timer {
      font-size: 36px;
      font-weight: bold;
      color: #d48806;
      background: #fff3cd;
      padding: 20px;
      border-radius: 12px;
      display: inline-block;
      box-shadow: 0 0 20px rgba(0,0,0,0.05);
      margin-bottom: 20px;
    }

    .video-container {
      position: relative;
      padding-top: 56.25%;
      margin-bottom: 20px;
    }

    .video-container iframe {
      position: absolute;
      top: 0; left: 0;
      width: 100%;
      height: 100%;
      border: 0;
      border-radius: 12px;
    }

    #expired-message {
      font-size: 22px;
      color: red;
      margin-top: 20px;
      display: none;
    }

    .subscribe-button {
      background-color: #ffc107;
      color: #000;
      font-weight: bold;
      font-size: 18px;
      padding: 14px 28px;
      border-radius: 10px;
      text-decoration: none;
      display: inline-block;
      margin-top: 20px;
      transition: background 0.3s;
      display: none;
    }

    .subscribe-button:hover {
      background-color: #e0a800;
    }

    footer {
      text-align: center;
      background-color: #fff1da;
      padding: 20px;
      font-size: 14px;
      color: #555;
      margin-top: 40px;
    }

    @media (max-width: 768px) {
      .hero h2 {
        font-size: 24px;
      }

      .hero p {
        font-size: 16px;
      }

      .hero a.button {
        font-size: 16px;
        padding: 10px 24px;
      }

      .digital-timer {
        font-size: 28px;
        padding: 16px;
      }

      .subscribe-button {
        font-size: 16px;
        padding: 12px 20px;
      }
    }
  </style>
</head>
<body>

  <header>
    <h1>رحلة المهندس المحترف</h1>
  </header>

  <section class="hero">
    <div class="hero-content">
      <h2>🎁 عرض خاص لمدة 48 ساعة فقط</h2>
      <p>شاهد المحاضرة الآن وابدأ رحلتك في احتراف الطاقة الشمسية</p>
      <a href="#video" class="button">ابدأ الآن</a>
    </div>
  </section>

  <section id="video">
    <div class="digital-timer" id="countdown">00:00:00</div>

    <div class="video-container" id="video-container">
      <iframe id="videoFrame" src="https://iframe.mediadelivery.net/embed/460802/e8b012cb-f646-4d5d-b92d-937b028bdaa2?autoplay=false&loop=false&muted=false&preload=true&responsive=true" loading="lazy" allowfullscreen allow="accelerometer; gyroscope; autoplay; encrypted-media; picture-in-picture;"></iframe>
    </div>

    <div id="expired-message">⛔ انتهى العرض، نلقاك في العرض القادم!</div>

    <a href="https://wa.me/201055690849" class="subscribe-button" id="subscribeBtn" target="_blank">اشترك الآن عبر واتساب</a>
  </section>

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

  <script>
    function startCountdown() {
      const countdownEl = document.getElementById("countdown");
      const videoContainer = document.getElementById("video-container");
      const expiredMessage = document.getElementById("expired-message");
      const subscribeBtn = document.getElementById("subscribeBtn");

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
          subscribeBtn.style.display = "none";
          return;
        }

        const hours = String(Math.floor((distance / (1000 * 60 * 60))) % 24).padStart(2, '0');
        const minutes = String(Math.floor((distance / (1000 * 60)) % 60)).padStart(2, '0');
        const seconds = String(Math.floor((distance / 1000) % 60)).padStart(2, '0');

        countdownEl.textContent = `${hours}:${minutes}:${seconds}`;
      }, 1000);
    }

    function showSubscribeAfterDelay() {
      setTimeout(() => {
        const subscribeBtn = document.getElementById("subscribeBtn");
        subscribeBtn.style.display = "inline-block";
      }, 8 * 60 * 1000); // بعد 8 دقائق
    }

    window.onload = () => {
      startCountdown();
      showSubscribeAfterDelay();
    };
  </script>

</body>
</html>
