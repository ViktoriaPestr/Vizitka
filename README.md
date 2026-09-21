<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Название команды</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: 'Segoe UI', Arial, sans-serif;
    background: #2a2a2a;
    color: #ffffff;
    line-height: 1.6;
  }

  /* ===== Шапка ===== */
  header {
    text-align: center;
    padding: 30px 20px 30px;
    font-color: #ffffff;
  }
  header h1 { font-size: 2.5rem; margin-bottom: 10px; }
  header p { color: #666; font-size: 1.1rem; }

  /* ===== Карусель ===== */
  .carousel {
    position: relative;
    max-width: 700px;
    margin: 15px auto 0;
    overflow: hidden;
    border-radius: 16px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
    background: #000;
  }

  .slides {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }

  .slides img {
    width: 100%;
    flex-shrink: 0;
    height: 450px;
    object-fit: contain;      /* вписать полностью */
    background: #000;         /* фон для пустых полос */
    display: block;
  }

  /* Кнопки влево/вправо */
  .btn {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(0,0,0,0.5);
    color: #fff;
    border: none;
    width: 45px;
    height: 45px;
    border-radius: 50%;
    font-size: 22px;
    cursor: pointer;
    transition: background 0.3s;
    z-index: 2;
  }
  .btn:hover { background: rgba(0,0,0,0.8); }
  .prev { left: 15px; }
  .next { right: 15px; }

  /* Точки-индикаторы */
  .dots {
    position: absolute;
    bottom: 15px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 10px;
    z-index: 2;
  }
  .dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background: rgba(255,255,255,0.5);
    cursor: pointer;
    transition: background 0.3s;
  }
  .dot.active { background: #fff; }

  /* ===== Миниатюры ===== */
  .thumbnails {
    display: flex;
    gap: 12px;
    justify-content: center;
    max-width: 900px;
    margin: 20px auto 0;
    padding: 0 20px;
    overflow-x: auto;
    scroll-behavior: smooth;
    scrollbar-width: thin;
  }

  .thumbnails::-webkit-scrollbar { height: 6px; }
  .thumbnails::-webkit-scrollbar-thumb {
    background: #ccc;
    border-radius: 3px;
  }

  .thumb {
    flex: 0 0 auto;
    width: 120px;
    height: 80px;
    border-radius: 10px;
    overflow: hidden;
    cursor: pointer;
    opacity: 0.55;
    border: 3px solid transparent;
    transition: opacity 0.3s, border-color 0.3s, transform 0.2s;
  }

  .thumb img {
  width: 100%;
  height: 100%;
  object-fit: contain;    /* ← вписать целиком */
  background: #eee;       /* фон для полос */
  }

  .thumb:hover {
    opacity: 0.85;
    transform: translateY(-2px);
  }

  .thumb.active {
    opacity: 1;
    border-color: #222;
  }

  /* ===== Контакты ===== */
  .contacts {
    text-align: center;
    padding: 40px 20px 60px;
  }
  .contacts h2 { margin-bottom: 20px; font-size: 1.6rem; }
  .contacts a {
    display: inline-block;
    margin: 8px 12px;
    padding: 12px 24px;
    background: #222;
    color: #fff;
    text-decoration: none;
    border-radius: 30px;
    transition: background 0.3s;
  }
  .contacts a:hover { background: #555; }

  /* ===== Мобильные ===== */
  @media (max-width: 600px) {
    header h1 { font-size: 1.8rem; }
    .slides img { height: 300px; }
    .btn { width: 38px; height: 38px; font-size: 18px; }
    .thumb { width: 80px; height: 55px; }
  }
</style>
</head>
<body>

  <header>
    <h2>Название команды</h2>
    <p>Лозунг или описание команды</br>
       Можно сделать в несколько строк   
    </p>
  </header>

  <!-- Карусель -->
  <div class="carousel">
    <div class="slides" id="slides">
      <img src="Images/photo1_1.png" alt="Фото участника 1">
      <img src="Images/photo2_1.png" alt="Фото участника 2">
      <img src="Images/photo3_1.png" alt="Фото участника 3">
      <img src="Images/photo4_1.png" alt="Фото участника 4">
      <img src="Images/photo5_1.png" alt="Фото участника 5">
    </div>

    <button class="btn prev" onclick="moveSlide(-1)">&#10094;</button>
    <button class="btn next" onclick="moveSlide(1)">&#10095;</button>

    <div class="dots" id="dots"></div>
  </div>

  <!-- Миниатюры -->
  <div class="thumbnails" id="thumbnails">
    <div class="thumb active" data-index="0">
      <img src="Images/photo1.png" alt="Фото участника 1">
    </div>
    <div class="thumb" data-index="1">
      <img src="Images/photo2.png" alt="Фото участника 2">
    </div>
    <div class="thumb" data-index="2">
      <img src="Images/photo3.png" alt="Фото участника 3">
    </div>
    <div class="thumb" data-index="3">
      <img src="Images/photo4.png" alt="Фото участника 4">
    </div>
    <div class="thumb" data-index="4">
      <img src="Images/photo5.png" alt="Фото участника 5">
    </div>
  </div>

  <!-- Контакты -->
  <section class="contacts">
    <h2>Связаться с нами</h2>
    <a href="tel:+79990000000">📞 Позвонить</a>
    <a href="mailto:mail@example.com">✉️ Написать</a>
    <a href="https://t.me/username" target="_blank">💬 Telegram</a>
  </section>

<script>
  const slides = document.getElementById('slides');
  const total = slides.children.length;
  const dotsBox = document.getElementById('dots');
  const thumbs = document.querySelectorAll('.thumb');
  let index = 0;

  // создаём точки
  for (let i = 0; i < total; i++) {
    const d = document.createElement('div');
    d.className = 'dot' + (i === 0 ? ' active' : '');
    d.onclick = () => goTo(i);
    dotsBox.appendChild(d);
  }

  // клик по миниатюре
  thumbs.forEach(t => {
    t.addEventListener('click', () => goTo(+t.dataset.index));
  });

  function update() {
    slides.style.transform = `translateX(-${index * 100}%)`;

    document.querySelectorAll('.dot').forEach((d, i) =>
      d.classList.toggle('active', i === index));

    thumbs.forEach((t, i) =>
      t.classList.toggle('active', i === index));

    // автоскролл к активной миниатюре
    thumbs[index]?.scrollIntoView({
      behavior: 'smooth',
      inline: 'center',
      block: 'nearest'
    });
  }

  function moveSlide(dir) {
    index = (index + dir + total) % total;
    update();
  }

  function goTo(i) {
    index = i;
    update();
  }

  // автопрокрутка каждые 4 секунды
  setInterval(() => moveSlide(1), 5000);

  // свайпы на мобильных
  let startX = 0;
  slides.addEventListener('touchstart', e => startX = e.touches[0].clientX);
  slides.addEventListener('touchend', e => {
    const diff = startX - e.changedTouches[0].clientX;
    if (Math.abs(diff) > 50) moveSlide(diff > 0 ? 1 : -1);
  });
</script>

</body>
</html>
это файл Readme
