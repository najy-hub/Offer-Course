<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خاص - رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Cairo', sans-serif; }

    body {
      background: #fffef5;
      color: #333;
      line-height: 1.6;
    }

    header {
      padding: 20px 40px;
      background-color: #f5e9cc;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid #ddd;
    }

    header h1 { font-size: 24px; color: #2c2c2c; }

    .hero {
      position: relative;
      background: #fff8dc;
      height: 70vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .hero-content {
      max-width: 800px;
      padding: 20px;
    }

    .hero h2 {
      font-size: 36px;
      margin-bottom: 20px;
      color: #2a2a2a;
    }

    .hero p {
      font-size: 18px;
      color: #4d4d4d;
      margin-bottom: 30px;
    }

    .hero a.button {
      padding: 12px 30px;
      background-color: #ffba00;
      color: #000;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      text-decoration: none;
      font-size: 18px;
      transition: background-color 0.3s;
    }

    .hero a.button:hover { background-color: #ffaa00; }

    #video {
      padding: 60px 20px;
      text-align: center;
    }

    iframe { max-width: 100%; border-radius: 12px; }

    #countdown {
      font-size: 28px;
      margin-bottom: 30px;
      color: #ff9900;
      font-weight: bold;
    }

    .subscribe-button {
      display: none;
      margin-top: 30px;
      padding: 15px 30px;
      background-color: #ffba00;
      color: #000;
      border: none;
      border-radius: 10px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      text-decoration: none;
    }

    .subscribe-button:hover {
      background-color: #ffaa00;
    }

    footer {
      background-color: #f2f2f2;
      text-align: center;
      padding: 20px;
      color: #777;
      font-size: 14px;
      margin-top: 60px;
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
    <div id="countdown">00:00:00</div>
    <div style="position:relative;padding-top:56.25%;">
      <iframe src="https://iframe.mediadelivery.net/embed/460802/e8b012cb-f646-4d5d-b92d-937b028bdaa2?autoplay=false&loop=false&muted=false&preload=false&responsive=true"
        loading="lazy"
        style="border:0;position:absolute;top:0;height:100%;width:100%;"
        allow="accelerometer;gyroscope;autoplay;encrypted-media;picture-in-picture"
        allowfullscreen="true">
      </iframe>
    </div>

    <a href="https://wa.me/201055690849" class="subscribe-button" target="_blank" id="subscribeBtn">اشترك الآن عبر واتساب</a>
  </section>

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

  <script>
    function startCountdown() {
      const countdownEl = document.getElementById("countdown");
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
          countdownEl.textContent = "⛔ انتهى العرض!";
          return;
        }

        const hours = String(Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))).padStart(2, '0');
        const minutes = String(Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))).padStart(2, '0');
        const seconds = String(Math.floor((distance % (1000 * 60)) / 1000)).padStart(2, '0');

        countdownEl.textContent = `${hours}:${minutes}:${seconds}`;
      }, 1000);

      setTimeout(() => {
        subscribeBtn.style.display = 'inline-block';
      }, 8 * 60 * 1000); // 8 دقائق
    }

    window.onload = startCountdown;
  </script>
</body>
</html>
