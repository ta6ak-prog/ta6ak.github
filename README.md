<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#07140f">
  <title>BASTER SHOP — каталог</title>

  <style>
    :root {
      --bg: #07140f;
      --bg-soft: #0b1c14;
      --panel: #10251a;
      --panel-light: #163323;
      --green: #9be36b;
      --green-bright: #b9f58c;
      --text: #f1f7ef;
      --muted: #a3b7a7;
      --border: rgba(190, 231, 190, .13);
      --danger: #ef8f8f;
      --radius: 20px;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      min-width: 320px;
      color: var(--text);
      background:
        radial-gradient(ellipse at 15% 0%, rgba(75, 144, 83, .17), transparent 34rem),
        var(--bg);
      font-family: Arial, Helvetica, sans-serif;
    }

    body.locked {
      overflow: hidden;
    }

    button,
    a {
      font: inherit;
    }

    button {
      color: inherit;
    }

    a {
      color: inherit;
    }

    .container {
      width: min(1160px, calc(100% - 40px));
      margin: 0 auto;
    }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 10;
      border-bottom: 1px solid var(--border);
      background: rgba(7, 20, 15, .92);
      backdrop-filter: blur(12px);
    }

    .nav {
      min-height: 74px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
    }

    .logo {
      color: var(--text);
      font-size: 19px;
      font-weight: 900;
      letter-spacing: .08em;
      text-decoration: none;
    }

    .logo span {
      color: var(--green);
    }

    .nav-links {
      display: flex;
      gap: 26px;
    }

    .nav-links a {
      color: var(--muted);
      font-size: 14px;
      text-decoration: none;
      transition: color .2s;
    }

    .nav-links a:hover,
    .footer a:hover {
      color: var(--green-bright);
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      min-height: 46px;
      padding: 12px 19px;
      border: 0;
      border-radius: 999px;
      color: #102013;
      background: var(--green);
      font-weight: 800;
      text-decoration: none;
      cursor: pointer;
      transition: transform .2s, background .2s;
    }

    .button:hover {
      transform: translateY(-2px);
      background: var(--green-bright);
    }

    .button:focus-visible,
    .close-button:focus-visible,
    .qty-button:focus-visible,
    a:focus-visible {
      outline: 3px solid #e0ffc8;
      outline-offset: 3px;
    }

    .cart-open {
      white-space: nowrap;
    }

    .hero {
      position: relative;
      overflow: hidden;
      min-height: 440px;
      display: flex;
      align-items: center;
      border-bottom: 1px solid var(--border);
      background:
        radial-gradient(ellipse at 82% 45%, rgba(115, 182, 98, .2), transparent 24rem),
        linear-gradient(110deg, #0a1a12, #10291b 60%, #0a1a12);
    }

    .hero::after {
      content: "B";
      position: absolute;
      right: 9%;
      top: 50%;
      color: rgba(155, 227, 107, .07);
      font-size: clamp(240px, 42vw, 510px);
      font-weight: 900;
      line-height: .8;
      transform: translateY(-50%);
      pointer-events: none;
    }

    .hero-content {
      position: relative;
      z-index: 1;
      max-width: 670px;
      padding: 72px 0;
    }

    .eyebrow {
      display: inline-block;
      margin-bottom: 18px;
      color: var(--green);
      font-size: 12px;
      font-weight: 800;
      letter-spacing: .2em;
      text-transform: uppercase;
    }

    h1 {
      margin: 0;
      font-size: clamp(48px, 8vw, 86px);
      line-height: .98;
      letter-spacing: -.06em;
    }

    .hero-copy {
      max-width: 480px;
      margin: 22px 0 28px;
      color: #c3d2c3;
      font-size: 17px;
      line-height: 1.65;
    }

    .age-note {
      margin: 17px 0 0;
      color: var(--muted);
      font-size: 12px;
    }

    .catalog {
      padding: 76px 0 88px;
    }

    .section-heading {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 20px;
      margin-bottom: 26px;
    }

    .section-heading h2 {
      margin: 0;
      font-size: clamp(30px, 4vw, 44px);
      letter-spacing: -.04em;
    }

    .section-heading p {
      margin: 0;
      color: var(--muted);
      font-size: 14px;
    }

    .product-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 20px;
    }

    .product-card {
      overflow: hidden;
      border: 1px solid var(--border);
      border-radius: var(--radius);
      background: linear-gradient(145deg, var(--panel-light), var(--panel));
      transition: transform .22s, border-color .22s;
    }

    .product-card:hover {
      transform: translateY(-5px);
      border-color: rgba(155, 227, 107, .48);
    }

    .product-art {
      height: 190px;
      display: grid;
      place-items: center;
      background:
        radial-gradient(circle at 50% 45%, rgba(155, 227, 107, .18), transparent 43%),
        linear-gradient(135deg, #173523, #0c1c13);
      border-bottom: 1px solid var(--border);
    }

    .product-icon {
      display: grid;
      width: 92px;
      height: 92px;
      place-items: center;
      border: 1px solid rgba(190, 231, 190, .2);
      border-radius: 28px;
      color: var(--green-bright);
      background: rgba(8, 24, 15, .6);
      font-size: 40px;
      box-shadow: 0 18px 50px rgba(0, 0, 0, .2);
    }

    .product-body {
      padding: 20px;
    }

    .product-body h3 {
      margin: 0 0 9px;
      font-size: 18px;
    }

    .product-body p {
      min-height: 42px;
      margin: 0 0 18px;
      color: var(--muted);
      font-size: 14px;
      line-height: 1.5;
    }

    .product-bottom {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
    }

    .price {
      color: var(--green);
      font-size: 20px;
      font-weight: 900;
      white-space: nowrap;
    }

    .add-button {
      min-height: 40px;
      padding: 10px 15px;
      font-size: 13px;
    }

    .footer {
      padding: 28px 0;
      border-top: 1px solid var(--border);
      color: var(--muted);
      font-size: 14px;
    }

    .footer-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      flex-wrap: wrap;
    }

    .footer p {
      margin: 6px 0;
    }

    .footer a {
      color: var(--green);
      text-decoration: none;
    }

    /* Корзина */
    .backdrop {
      position: fixed;
      inset: 0;
      z-index: 19;
      visibility: hidden;
      background: rgba(0, 0, 0, .62);
      opacity: 0;
      transition: opacity .25s, visibility .25s;
    }

    .backdrop.open {
      visibility: visible;
      opacity: 1;
    }

    .cart-panel {
      position: fixed;
      top: 0;
      right: 0;
      z-index: 20;
      width: min(430px, 100%);
      height: 100%;
      height: 100dvh;
      display: flex;
      flex-direction: column;
      padding: 24px;
      border-left: 1px solid var(--border);
      background: #0c1d14;
      transform: translateX(105%);
      transition: transform .28s ease;
    }

    .cart-panel.open {
      transform: translateX(0);
    }

    .cart-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 14px;
    }

    .cart-header h2 {
      margin: 0;
      font-size: 25px;
    }

    .close-button {
      width: 40px;
      height: 40px;
      border: 1px solid var(--border);
      border-radius: 50%;
      background: transparent;
      font-size: 18px;
      cursor: pointer;
    }

    .cart-list {
      flex: 1;
      overflow-y: auto;
      margin: 0;
      padding: 0;
      list-style: none;
    }

    .cart-list li {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 15px 0;
      border-bottom: 1px solid var(--border);
      font-size: 14px;
    }

    .cart-item-name {
      display: block;
      margin-bottom: 8px;
      font-weight: 700;
    }

    .cart-item-controls {
      display: flex;
      align-items: center;
      gap: 9px;
      color: var(--muted);
    }

    .qty-button {
      width: 28px;
      height: 28px;
      border: 1px solid var(--border);
      border-radius: 50%;
      background: var(--panel-light);
      cursor: pointer;
    }

    .empty-cart {
      justify-content: flex-start !important;
      color: var(--muted);
    }

    .cart-summary {
      padding-top: 18px;
      border-top: 1px solid var(--border);
    }

    .cart-total {
      display: flex;
      justify-content: space-between;
      margin-bottom: 16px;
      font-size: 18px;
      font-weight: 800;
    }

    .checkout-button {
      width: 100%;
    }

    .checkout-note {
      margin: 12px 0 0;
      color: var(--muted);
      font-size: 12px;
      line-height: 1.5;
    }

    /* Проверка возраста */
    .age-gate {
      position: fixed;
      inset: 0;
      z-index: 50;
      display: grid;
      place-items: center;
      padding: 20px;
      background: rgba(3, 11, 7, .94);
      backdrop-filter: blur(10px);
    }

    .age-gate.hidden {
      display: none;
    }

    .age-card {
      width: min(440px, 100%);
      padding: 30px;
      border: 1px solid var(--border);
      border-radius: 24px;
      background: var(--panel);
      text-align: center;
      box-shadow: 0 24px 80px rgba(0, 0, 0, .35);
    }

    .age-symbol {
      margin-bottom: 12px;
      color: var(--green);
      font-size: 36px;
    }

    .age-card h2 {
      margin: 0 0 12px;
      font-size: 28px;
    }

    .age-card p {
      margin: 0 0 22px;
      color: var(--muted);
      line-height: 1.6;
    }

    .age-actions {
      display: flex;
      justify-content: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .age-no {
      min-height: 46px;
      padding: 12px 18px;
      border: 1px solid var(--border);
      border-radius: 999px;
      background: transparent;
      font-weight: 700;
      cursor: pointer;
    }

    .age-denied {
      display: none;
      color: var(--text);
    }

    .age-denied.show {
      display: block;
    }

    .age-card.denied .age-content {
      display: none;
    }

    @media (max-width: 800px) {
      .product-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .nav-links {
        display: none;
      }

      .hero {
        min-height: 400px;
      }
    }

    @media (max-width: 540px) {
      .container {
        width: calc(100% - 28px);
      }

      .nav {
        min-height: 66px;
      }

      .logo {
        font-size: 16px;
      }

      .cart-open {
        min-height: 40px;
        padding: 9px 12px;
        font-size: 13px;
      }

      .product-grid {
        grid-template-columns: 1fr;
      }

      .product-art {
        height: 180px;
      }

      .section-heading {
        align-items: flex-start;
        flex-direction: column;
      }

      .hero {
        min-height: 390px;
      }

      .hero-copy {
        font-size: 16px;
      }

      .cart-panel {
        padding: 20px;
      }
    }
  </style>
</head>

<body class="locked">
  <header class="site-header">
    <nav class="nav container" aria-label="Главная навигация">
      <a class="logo" href="#">TUMAN <span>SHOP</span></a>

      <div class="nav-links">
        <a href="#catalog">Каталог</a>
        <a href="#contacts">Контакты</a>
      </div>

      <button class="button cart-open" id="open-cart" type="button">
        🛒 Корзина (<span id="cart-count">0</span>)
      </button>
    </nav>
  </header>

  <main>
    <section class="hero">
      <div class="container hero-content">
        <span class="eyebrow">TUMAN SHOP · МИНСК</span>
        <h1>VAPE<br>&amp; LIQUIDS</h1>
        <p class="hero-copy">
          Каталог товаров TUMAN SHOP. Добавьте выбранные позиции в корзину
          и подготовьте заказ для отправки.
        </p>
        <a class="button" href="#catalog">Смотреть каталог <span aria-hidden="true">→</span></a>
        <p class="age-note">Только для совершеннолетних. 18+</p>
      </div>
    </section>

    <section class="catalog container" id="catalog">
      <div class="section-heading">
        <h2>Наш ассортимент</h2>
        <p>Цены указаны в белорусских рублях</p>
      </div>
      <div class="product-grid" id="product-grid"></div>
    </section>
  </main>

  <footer class="footer" id="contacts">
    <div class="container footer-inner">
      <div>
        <p><strong>TUMAN SHOP</strong> — Минск</p>
        <p>Время работы: 10:00–22:00</p>
      </div>
      <p>
        Связь:
        <a href="https://t.me/froggy_vapesh0p" target="_blank" rel="noopener noreferrer">
          @froggy_vapesh0p
        </a>
      </p>
    </div>
  </footer>

  <div class="backdrop" id="backdrop"></div>

  <aside class="cart-panel" id="cart-panel" aria-label="Корзина" aria-hidden="true">
    <div class="cart-header">
      <h2>Корзина</h2>
      <button class="close-button" id="close-cart" type="button" aria-label="Закрыть корзину">✕</button>
    </div>

    <ul class="cart-list" id="cart-list"></ul>

    <div class="cart-summary">
      <div class="cart-total">
        <span>Итого:</span>
        <span><span id="cart-total">0</span> руб.</span>
      </div>
      <button class="button checkout-button" id="checkout" type="button">Подготовить заказ</button>
      <p class="checkout-note">
        Заказ будет подготовлен для отправки в Telegram. Наличие оплаты и обработки
        заказов зависит от настроек магазина.
      </p>
    </div>
  </aside>

  <div class="age-gate" id="age-gate" role="dialog" aria-modal="true" aria-labelledby="age-title">
    <div class="age-card" id="age-card">
      <div class="age-content">
        <div class="age-symbol" aria-hidden="true">✦</div>
        <h2 id="age-title">Вам уже есть 18?</h2>
        <p>Сайт предназначен только для совершеннолетних. Подтвердите возраст, чтобы продолжить.</p>
        <div class="age-actions">
          <button class="button" id="age-yes" type="button">Да, мне есть 18</button>
          <button class="age-no" id="age-no" type="button">Нет</button>
        </div>
      </div>
      <div class="age-denied" id="age-denied">
        <h2>Доступ закрыт</h2>
        <p>Сайт предназначен только для совершеннолетних.</p>
      </div>
    </div>
  </div>

  <script>
    "use strict";

    const products = [
      {
        id: 1,
        name: "Жижа «Неон» 30 мл",
        price: 15,
        desc: "Лайм, мята, холодок.",
        icon: "◈"
      },
      {
        id: 2,
        name: "Соль «Синтез» 20 мл",
        price: 20,
        desc: "Манго, маракуйя, лёд.",
        icon: "✧"
      },
      {
        id: 3,
        name: "Под-система SYNTH-X",
        price: 90,
        desc: "Компактная модель, ёмкость 800 mAh.",
        icon: "▰"
      },
      {
        id: 4,
        name: "Картридж 0.8Ω",
        price: 10,
        desc: "Набор из 2 сменных картриджей.",
        icon: "◉"
      },
      {
        id: 5,
        name: "Жижа «Пепел» 60 мл",
        price: 25,
        desc: "Табак и карамель.",
        icon: "❖"
      },
      {
        id: 6,
        name: "Одноразка Puff 5000",
        price: 35,
        desc: "Вкус клубники и киви.",
        icon: "▥"
      }
    ];

    const CART_STORAGE_KEY = "basterShopCart";
    let cart = loadCart();

    const productGrid = document.getElementById("product-grid");
    const cartPanel = document.getElementById("cart-panel");
    const backdrop = document.getElementById("backdrop");
    const ageGate = document.getElementById("age-gate");
    const ageCard = document.getElementById("age-card");

    function loadCart() {
      try {
        const saved = JSON.parse(localStorage.getItem(CART_STORAGE_KEY) || "[]");
        if (!Array.isArray(saved)) return [];
        return saved.filter(item =>
          products.some(product => product.id === Number(item.id)) &&
          Number.isInteger(Number(item.qty)) &&
          Number(item.qty) > 0
        ).map(item => ({ id: Number(item.id), qty: Number(item.qty) }));
      } catch (error) {
        return [];
      }
    }

    function saveCart() {
      try {
        localStorage.setItem(CART_STORAGE_KEY, JSON.stringify(cart));
      } catch (error) {
        // Корзина продолжит работать до закрытия вкладки,
        // даже если браузер запретил локальное сохранение.
      }
    }

    function renderProducts() {
      productGrid.innerHTML = products.map(product => `
        <article class="product-card">
          <div class="product-art" aria-hidden="true">
            <div class="product-icon">${product.icon}</div>
          </div>
          <div class="product-body">
            <h3>${product.name}</h3>
            <p>${product.desc}</p>
            <div class="product-bottom">
              <span class="price">${product.price} руб.</span>
              <button class="button add-button" type="button" data-add="${product.id}">
                В корзину
              </button>
            </div>
          </div>
        </article>
      `).join("");
    }

    function renderCart() {
      const cartList = document.getElementById("cart-list");
      let total = 0;
      let count = 0;

      if (cart.length === 0) {
        cartList.innerHTML = '<li class="empty-cart">Корзина пока пуста</li>';
      } else {
        cartList.innerHTML = cart.map(item => {
          const product = products.find(entry => entry.id === item.id);
          const itemTotal = product.price * item.qty;
          total += itemTotal;
          count += item.qty;

          return `
            <li>
              <div>
                <span class="cart-item-name">${product.name}</span>
                <div class="cart-item-controls">
                  <button class="qty-button" type="button"
                    data-change="-1" data-id="${product.id}"
                    aria-label="Уменьшить количество">−</button>
                  <span>${item.qty} шт.</span>
                  <button class="qty-button" type="button"
                    data-change="1" data-id="${product.id}"
                    aria-label="Увеличить количество">+</button>
                </div>
              </div>
              <strong>${itemTotal} руб.</strong>
            </li>
          `;
        }).join("");
      }

      document.getElementById("cart-count").textContent = count;
      document.getElementById("cart-total").textContent = total;
      saveCart();
    }

    function addToCart(id) {
      const item = cart.find(entry => entry.id === id);

      if (item) {
        item.qty += 1;
      } else {
        cart.push({ id: id, qty: 1 });
      }

      renderCart();
      openCart();
    }

    function changeQuantity(id, amount) {
      const item = cart.find(entry => entry.id === id);
      if (!item) return;

      item.qty += amount;

      if (item.qty <= 0) {
        cart = cart.filter(entry => entry.id !== id);
      }

      renderCart();
    }

    function openCart() {
      cartPanel.classList.add("open");
      backdrop.classList.add("open");
      cartPanel.setAttribute("aria-hidden", "false");
    }

    function closeCart() {
      cartPanel.classList.remove("open");
      backdrop.classList.remove("open");
      cartPanel.setAttribute("aria-hidden", "true");
    }

    function makeOrderText() {
      let total = 0;
      let text = "Заказ в TUMAN SHOP:\\n";

      cart.forEach(item => {
        const product = products.find(entry => entry.id === item.id);
        const itemTotal = product.price * item.qty;
        total += itemTotal;
        text += `• ${product.name} × ${item.qty} — ${itemTotal} руб.\\n`;
      });

      text += `\\nИтого: ${total} руб.`;
      return text;
    }

    async function checkout() {
      if (cart.length === 0) {
        alert("Корзина пуста.");
        return;
      }

      const orderText = makeOrderText();

      // Открываем чат магазина; сам сайт не отправляет заказ автоматически.
      window.open("https://t.me/froggy_vapesh0p", "_blank", "noopener,noreferrer");

      try {
        if (navigator.clipboard && window.isSecureContext) {
          await navigator.clipboard.writeText(orderText);
          alert("Текст заказа скопирован. Вставьте его в чат Telegram с магазином.");
        } else {
          window.prompt("Скопируйте текст заказа и отправьте его в Telegram:", orderText);
        }
      } catch (error) {
        window.prompt("Скопируйте текст заказа и отправьте его в Telegram:", orderText);
      }
    }

    function confirmAge(isAdult) {
      if (isAdult) {
        try {
          localStorage.setItem("basterAgeConfirmed", "true");
        } catch (error) {
          // Подтверждение действует до закрытия страницы, если хранилище недоступно.
        }

        ageGate.classList.add("hidden");
        document.body.classList.remove("locked");
      } else {
        ageCard.classList.add("denied");
        document.getElementById("age-denied").classList.add("show");
      }
    }

    productGrid.addEventListener("click", event => {
      const button = event.target.closest("[data-add]");
      if (button) addToCart(Number(button.dataset.add));
    });

    document.getElementById("cart-list").addEventListener("click", event => {
      const button = event.target.closest("[data-change]");
      if (button) {
        changeQuantity(Number(button.dataset.id), Number(button.dataset.change));
      }
    });

    document.getElementById("open-cart").addEventListener("click", openCart);
    document.getElementById("close-cart").addEventListener("click", closeCart);
    document.getElementById("checkout").addEventListener("click", checkout);
    document.getElementById("age-yes").addEventListener("click", () => confirmAge(true));
    document.getElementById("age-no").addEventListener("click", () => confirmAge(false));
    backdrop.addEventListener("click", closeCart);

    document.addEventListener("keydown", event => {
      if (event.key === "Escape") closeCart();
    });

    try {
      if (localStorage.getItem("basterAgeConfirmed") === "true") {
        ageGate.classList.add("hidden");
        document.body.classList.remove("locked");
      }
    } catch (error) {
      // Если хранилище недоступно, возраст спрашивается при каждом открытии страницы.
    }

    renderProducts();
    renderCart();
  </script>
</body>
</html>
