<!DOCTYPE html>
<!--
MIT License

Copyright (c) 2025 [Ваше ім’я або назва]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
-->

<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Casino Multilang Demo</title>
  <style>
    body { margin:0; font-family:Arial, sans-serif; transition: all 0.5s ease; }
    header { padding:50px; text-align:center; }
    h1 { margin:0; font-size:3em; }
    .btn { display:inline-block; padding:15px 30px; margin-top:20px; border-radius:30px; text-decoration:none; font-weight:bold; transition:0.3s; }
    .section { padding:40px 20px; text-align:center; }
    .card { display:inline-block; margin:10px; padding:20px; border-radius:15px; min-width:200px; }

    /* ====== UA STYLE ====== */
    body.ua { background:#0c0c0c; color:#fff; }
    body.ua header { background: linear-gradient(90deg, #d4af37, #8b0000); color:#fff; }
    body.ua .btn { background:#d4af37; color:#000; }
    body.ua h2 { color:#d4af37; }
    body.ua .card { background:#1a1a1a; box-shadow:0 0 15px rgba(212,175,55,0.5); }

    /* ====== PL STYLE ====== */
    body.pl { background:#fff; color:#000; }
    body.pl header { background: linear-gradient(90deg, #ff0000, #ffffff); color:#222; }
    body.pl .btn { background:#ff0000; color:#fff; }
    body.pl h2 { color:#ff0000; }
    body.pl .card { border:2px solid #ff0000; background:#fff; }

    /* ====== EN STYLE ====== */
    body.en { background: linear-gradient(180deg, #0d0d3f, #1a1a80); color:#fff; }
    body.en header { background:rgba(0,0,0,0.3); color:#ffd700; }
    body.en .btn { background:#6a0dad; color:#fff; box-shadow:0 0 10px #6a0dad; }
    body.en h2 { color:#ffd700; }
    body.en .card { background:rgba(255,255,255,0.1); backdrop-filter:blur(5px); }

    /* language switcher */
    .lang-switcher { position:fixed; top:10px; right:10px; }
    .lang-switcher button { margin:0 5px; padding:8px 15px; border:none; border-radius:20px; font-weight:bold; cursor:pointer; }
  </style>
</head>
<body>
  <div class="lang-switcher">
    <button onclick="setLang('ua')">🇺🇦 UA</button>
    <button onclick="setLang('pl')">🇵🇱 PL</button>
    <button onclick="setLang('en')">🇬🇧 EN</button>
  </div>

  <header>
    <h1 id="title"></h1>
    <p id="subtitle"></p>
    <a href="#games" id="cta" class="btn"></a>
  </header>

  <section id="games" class="section">
    <h2 id="games-title"></h2>
    <div id="games-list">
      <div class="card"></div>
      <div class="card"></div>
      <div class="card"></div>
    </div>
  </section>

  <section class="section">
    <h2 id="bonus-title"></h2>
    <p id="bonus-text"></p>
  </section>

  <footer>
    <p id="footer-text"></p>
  </footer>

  <script>
    const content = {
      ua: {
        title: "Палац удачі",
        subtitle: "Сучасне онлайн-казино для справжніх переможців",
        cta: "🎰 Грати зараз",
        games: "Наші ігри",
        cards: ["🎲 Популярні слоти", "🃏 Живе казино з дилерами", "🏆 Турніри та джекпоти"],
        bonus: "Бонуси",
        bonusText: "Щедрі вітальні бонуси, кешбек та ексклюзивні пропозиції.",
        footer: "© 2025 Палац удачі. Усі права захищені."
      },
      pl: {
        title: "Pałac Szczęścia",
        subtitle: "Nowoczesne kasyno online dla prawdziwych zwycięzców",
        cta: "🎰 Graj teraz",
        games: "Nasze gry",
        cards: ["🎲 Popularne sloty", "🃏 Kasyno na żywo", "🏆 Turnieje i jackpoty"],
        bonus: "Bonusy",
        bonusText: "Hojne bonusy powitalne, cashback i ekskluzywne oferty.",
        footer: "© 2025 Pałac Szczęścia. Wszelkie prawa zastrzeżone."
      },
      en: {
        title: "Palace of Luck",
        subtitle: "A modern online casino for true winners",
        cta: "🎰 Play Now",
        games: "Our Games",
        cards: ["🎲 Popular Slots", "🃏 Live Casino with Dealers", "🏆 Tournaments & Jackpots"],
        bonus: "Bonuses",
        bonusText: "Generous welcome bonuses, cashback, and exclusive offers.",
        footer: "© 2025 Palace of Luck. All rights reserved."
      }
    };

    function setLang(lang) {
      document.body.className = lang;
      document.documentElement.lang = lang;
      localStorage.setItem("siteLang", lang);
      document.getElementById("title").innerText = content[lang].title;
      document.getElementById("subtitle").innerText = content[lang].subtitle;
      document.getElementById("cta").innerText = content[lang].cta;
      document.getElementById("games-title").innerText = content[lang].games;
      const cards = document.querySelectorAll("#games-list .card");
      cards.forEach((c,i)=> c.innerText = content[lang].cards[i]);
      document.getElementById("bonus-title").innerText = content[lang].bonus;
      document.getElementById("bonus-text").innerText = content[lang].bonusText;
      document.getElementById("footer-text").innerText = content[lang].footer;
    }

    // при завантаженні перевіряємо збережену мову або беремо мову браузера
    const savedLang = localStorage.getItem("siteLang");
    if (savedLang) {
      setLang(savedLang);
    } else {
      const browserLang = navigator.language.toLowerCase();
      if (browserLang.startsWith("uk") || browserLang.startsWith("ru")) {
        setLang("ua");
      } else if (browserLang.startsWith("pl")) {
        setLang("pl");
      } else {
        setLang("en");
      }
    }
  </script>
</body>
</html>
