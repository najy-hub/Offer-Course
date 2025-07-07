
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خـــاص -رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Cairo', sans-serif;
  }

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Cairo', sans-serif;
  }

  body {
    background: #fdf6e3;
    color: #222;
    line-height: 1.6;
  }

  header {
    padding: 20px 40px;
    background-color: #fff8e1;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #ddd;
  }

  header h1 {
    font-size: 24px;
    color: #7c5e10;
  }

  .hero {
    position: relative;
    background-image: url('Images/hero.png');
    background-size: cover;
    background-position: center;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }

  .hero::after {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background-color: rgba(255, 248, 225, 0.6);
    z-index: 1;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    max-width: 800px;
    padding: 20px;
  }

  .hero h2 {
    font-size: 36px;
    margin-bottom: 20px;
    color: #7c5e10;
  }

  .hero p {
    font-size: 18px;
    color: #4a3f25;
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

  .hero a.button:hover {
    background-color: #ffaa00;
  }

  #video {
    padding: 60px 20px;
    text-align: center;
    background-color: #fffdf5;
  }

  iframe {
    max-width: 100%;
    border-radius: 12px;
  }

  #countdown {
    font-size: 28px;
    margin-bottom: 30px;
    color: #aa8800;
    font-weight: bold;
  }

  .digital-timer {
    font-size: 48px;
    font-weight: bold;
    color: #aa8800;
    background: #fff3c4;
    padding: 20px 40px;
    border-radius: 12px;
    display: inline-block;
    margin-bottom: 30px;
    box-shadow: 0 0 20px rgba(170, 136, 0, 0.2);
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
    background-color: #fff3c4;
    text-align: center;
    padding: 20px;
    color: #555;
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
        src="https://www.youtube.com/embed/mNPXseyrxMU"
        frameborder="0" allowfullscreen></iframe>
    </div>

    <div id="expired-message" style="display:none;">⛔ انتهى العرض، نلقاك في العرض القادم!</div>

    <a href="https://wa.me/201055690849" class="subscribe-button" target="_blank">اشترك الآن عبر واتساب</a>
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
