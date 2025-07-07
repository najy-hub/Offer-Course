<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عرض خاص - رحلة المهندس المحترف</title>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap" rel="stylesheet" />
  <script src="https://cdn.bunny.net/bunny-player/v1.0.0/bunny.player.js" defer></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Cairo', sans-serif;
    }

    body {
      background: linear-gradient(to right, #fffbe6, #fffaf0);
      color: #333;
      line-height: 1.6;
      text-align: center;
    }

    header {
      padding: 20px 40px;
      background-color: #f9f1d8;
      border-bottom: 1px solid #e5d5a3;
    }

    header h1 {
      font-size: 28px;
      color: #6a4e13;
    }

    .hero {
      padding: 60px 20px;
      background-image: url('Images/hero.png');
      background-size: cover;
      background-position: center;
      color: #4b390d;
    }

    .hero h2 {
      font-size: 36px;
      margin-bottom: 20px;
    }

    .hero p {
      font-size: 18px;
      margin-bottom: 30px;
    }

    .hero a.button {
      padding: 12px 30px;
      background-color: #e5b100;
      color: #000;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      text-decoration: none;
      font-size: 18px;
      transition: background-color 0.3s;
    }

    .hero a.button:hover {
      background-color: #d9a400;
    }

    #bunny-player {
      max-width: 800px;
      margin: 40px auto;
      aspect-ratio: 16/9;
    }

    #subscribeBtn {
      display: none;
      padding: 15px 30px;
      background-color: #e5b100;
      color: #000;
      border: none;
      border-radius: 10px;
      font-size: 18px;
      font-weight: bold;
      cursor: pointer;
      text-decoration: none;
      margin-top: 30px;
    }

    #subscribeBtn:hover {
      background-color: #d9a400;
    }

    footer {
      background-color: #f2e8c6;
      padding: 20px;
      color: #7a6b4d;
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
    <h2>🎓 عرض خاص لمدة 48 ساعة</h2>
    <p>ابدأ رحلتك الآن وشاهد المحاضرة المجانية الأولى في مجال الطاقة الشمسية</p>
    <a href="#bunny-player" class="button">شــاهد الآن</a>
  </section>

  <div id="bunny-player"></div>

  <a id="subscribeBtn" href="https://wa.me/201055690849" target="_blank">اشترك الآن عبر واتساب</a>

  <footer>
    &copy; 2025 جميع الحقوق محفوظة - رحلة المهندس المحترف
  </footer>

  <script>
    document.addEventListener("DOMContentLoaded", function () {
      const player = new BunnyPlayer("#bunny-player", {
        video: {
          id: "e8b012cb-f646-4d5d-b92d-937b028bdaa2",
          collection: "460802"
        }
      });

      let hasStarted = false;
      let showButtonTimer;

      player.on("play", () => {
        if (!hasStarted) {
          hasStarted = true;
          showButtonTimer = setTimeout(() => {
            document.getElementById("subscribeBtn").style.display = "inline-block";
          }, 8 * 60 * 1000); // 8 دقائق
        }
      });
    });
  </script>

</body>
</html>
