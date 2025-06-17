<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خاص - أنظمة التخزين</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Cairo', sans-serif; }

    body {
      background: linear-gradient(to right, #0f0f0f, #1c1c1c);
      color: #ffffff; line-height: 1.6;
    }

    header {
      padding: 20px 40px; background-color: #111111d0;
      display: flex; justify-content: space-between; align-items: center;
      border-bottom: 1px solid #333;
    }

    header h1 { font-size: 24px; color: #f9f9f9; }

    .hero {
      position: relative;
      background-image: url('Images/hero.png');
      background-size: cover; background-position: center;
      height: 100vh;
      display: flex; align-items: center; justify-content: center;
      text-align: center;
    }

    .hero::after {
      content: ''; position: absolute; top: 0; left: 0;
      width: 100%; height: 100%; background-color: rgba(0,0,0,0.6); z-index: 1;
    }

    .hero-content {
      position: relative; z-index: 2;
      max-width: 800px; padding: 20px;
    }

    .hero h2 { font-size: 36px; margin-bottom: 20px; color: #ffffff; }
    .hero p { font-size: 18px; color: #dddddd; margin-bottom: 30px; }

    .hero a.button {
      padding: 12px 30px; background-color: #ffba00; color: #000;
      font-weight: bold; border: none; border-radius: 8px;
      text-decoration: none; font-size: 18px; transition: background-color 0.3s;
    }

    .hero a.button:hover { background-color: #ffaa00; }

    #video {
      padding: 60px 20px; text-align: center;
    }

    iframe { max-width: 100%; border-radius: 12px; }

    #countdown {
      font-size: 28px;
      margin-bottom: 30px;
      color: #ffba00;
      font-weight: bold;
    }
.digital-timer {
  font-size: 48px;
  font-weight: bold;
  color: #ffba00;
  background: #1f1f1f;
  padding: 20px 40px;
  border-radius: 12px;
  display: inline-block;
  margin-bottom: 30px;
  box-shadow: 0 0 20px rgba(255, 186, 0, 0.3);
}

    #expired-message {
      font-size: 24px;
      color: red;
      margin-top: 20px;
    }

    .subscribe-button {
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
      background-color: #101010;
      text-align: center;
      padding: 20px;
      color: #666;
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
<div id="countdown" class="digital-timer">00:00:00</div>

    <div id="video-container">
      <iframe width="800" height="450"
        src="https://www.youtube.com/embed/zW9ZX-SZKtE"
        frameborder="0" allowfullscreen></iframe>
    </div>

    <div id="expired-message" style="display:none;">⛔ انتهى العرض، نلقاك في العرض القادم!</div>

    <a href="https://wa.me/201234567890" class="subscribe-button" target="_blank">اشترك الآن عبر واتساب</a>
  </section>

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

<script>
  function startCountdown() {
    const countdownEl = document.getElementById("countdown");
    const videoContainer = document.getElementById("video-container");
    const expiredMessage = document.getElementById("expired-message");

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
  }

  window.onload = startCountdown;
</script>

</body>
</html>
