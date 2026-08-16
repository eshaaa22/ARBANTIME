(function () {
  const DEFAULT_WATCHES = [
    {
      id: 1,
      name: "Poedagar Leather Belt (Black)",
      price: 1000,
      offerPrice: 0,
      img: "https://img.drz.lazcdn.com/static/bd/p/78f20ea8abb9d4985742ebf10d5d054d.png_960x960q80.png_.webp"
    },
    {
      id: 2,
      name: "Poedagar Leather Belt (Green)",
      price: 1000,
      offerPrice: 0,
      img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRup8yeK8Dwbr4Nh4vSnVPoq6w0WwNaa1qbvAAxXb7_ZA&s"
    },
    {
      id: 3,
      name: "Poedagar Leather Belt (Yellow)",
      price: 1000,
      offerPrice: 0,
      img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS5xLhVIPmQTak88I-sFO1oEqY_N4eKdszb0ohSABCq-OHceTrC7Gn3-0k&s=10"
    },
    {
      id: 4,
      name: "Poedagar Leather Belt (Blue)",
      price: 1000,
      offerPrice: 0,
      img: "https://static-01.daraz.com.bd/p/c96687be74ef7d86e54fedf28b6840bc.png"
    },
    {
      id: 5,
      name: "Poedagar Chain (Green)",
      price: 1200,
      offerPrice: 0,
      img: "https://img.drz.lazcdn.com/static/bd/p/4faf7b3fa7cf16a13419668531aeb581.jpg_960x960q80.jpg_.webp"
    },
    {
      id: 6,
      name: "Poedagar Chain (blue)",
      price: 1200,
      offerPrice: 0,
      img: "https://poedagar.store/wp-content/uploads/2025/02/%E9%93%B6%E8%93%9D-1.jpg"
    },
    {
      id: 7,
      name: "Rolex magnet belt",
      price: 1600,
      offerPrice: 0,
      img: "https://static-01.daraz.com.bd/p/ccd95ee7e38d424e43aef828a71414f2.jpg"
    },
    {
      id: 8,
      name: "Foshel",
      price: 1200,
      offerPrice: 999,
      img: "https://images.meesho.com/images/products/999182818/bj4hf_512.webp?width=512"
    },
    {
      id: 9,
      name: "Universe Point",
      price: 2000,
      offerPrice: 1499,
      img: "https://voguealaska.pk/cdn/shop/files/5_3f8f8e4c-b291-4e4c-b47f-4fd6f737436f.png?v=1778749497&width=1946"
    },
    {
      id: 10,
      name: "Arabic Watch",
      price: 1500,
      offerPrice: 999,
      img: "https://img.drz.lazcdn.com/static/bd/p/905885701653e6f3ac5216f34bb3c3f9.jpg_960x960q80.jpg_.webp"
    }
  ];

  const DEFAULT_FALLBACK_IMG = "data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='300' height='240' viewBox='0 0 300 240'><rect width='100%' height='100%' fill='%231a1a1a'/><text x='50%' y='50%' dominant-baseline='middle' text-anchor='middle' fill='%23d4af37' font-family='sans-serif' font-size='14'>Timepiece Image</text></svg>";

  function processDefaultWatches(list) {
    return list.map(item => ({
      ...item,
      isOffer: item.offerPrice > 0 && item.offerPrice < item.price
    }));
  }

  let inventory = processDefaultWatches(DEFAULT_WATCHES);
  let cart = [];

  const styleSheet = document.createElement("style");
  styleSheet.type = "text/css";
  styleSheet.innerText = `
    @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Montserrat:wght@200;300;400;500;600&family=Orbitron:wght@500;700;900&display=swap');

    :root {
      --bg-dark: #0a0a0a;
      --bg-card: #121212;
      --bg-surface: #1a1a1a;
      --accent-gold: #d4af37;
      --accent-gold-light: #f3e5ab;
      --text-main: #f5f5f7;
      --text-muted: #a1a1a6;
      --border-color: rgba(212, 175, 55, 0.25);
      --font-heading: 'Cinzel', serif;
      --font-body: 'Montserrat', sans-serif;
      --font-futuristic: 'Orbitron', sans-serif;
      --transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background-color: var(--bg-dark);
      color: var(--text-main);
      font-family: var(--font-body);
      overflow-x: hidden;
      line-height: 1.6;
    }

    #auth-overlay {
      position: fixed; inset: 0;
      background: rgba(5, 5, 5, 0.95);
      backdrop-filter: blur(15px);
      z-index: 1000;
      display: flex; align-items: center; justify-content: center;
    }

    .auth-card {
      background: var(--bg-card);
      border: 1px solid var(--border-color);
      padding: 3rem; width: 100%; max-width: 440px;
      text-align: center;
      box-shadow: 0 20px 50px rgba(0,0,0,0.8);
    }

    .auth-card h1 {
      font-family: var(--font-heading);
      letter-spacing: 4px; color: var(--accent-gold);
      font-size: 2.2rem; margin-bottom: 2rem;
    }

    .auth-btn {
      width: 100%; padding: 0.9rem; margin-bottom: 1rem;
      background: transparent; border: 1px solid var(--border-color);
      color: var(--text-main); font-family: var(--font-body);
      font-size: 0.85rem; letter-spacing: 1px; cursor: pointer;
      display: flex; align-items: center; justify-content: center; gap: 10px;
      transition: var(--transition);
    }

    .auth-btn:hover {
      border-color: var(--accent-gold);
      background: rgba(212, 175, 55, 0.05);
      color: var(--accent-gold);
    }

    .auth-divider {
      margin: 1.5rem 0; display: flex; align-items: center;
      color: var(--text-muted); font-size: 0.75rem;
    }
    .auth-divider::before, .auth-divider::after {
      content: ""; flex: 1; height: 1px; background: rgba(255,255,255,0.1);
    }
    .auth-divider span { padding: 0 10px; }

    .input-field {
      width: 100%; padding: 0.9rem;
      background: var(--bg-surface);
      border: 1px solid rgba(255,255,255,0.1);
      color: #fff; margin-bottom: 1rem;
      font-family: var(--font-body); outline: none;
    }
    .input-field:focus { border-color: var(--accent-gold); }

    header {
      position: sticky; top: 0;
      background: rgba(10, 10, 10, 0.9);
      backdrop-filter: blur(10px);
      border-bottom: 1px solid var(--border-color);
      z-index: 100; padding: 0 2rem;
    }

    .nav-container {
      max-width: 1400px; margin: 0 auto; height: 80px;
      display: flex; align-items: center; justify-content: space-between;
    }

    .brand-logo {
      font-family: var(--font-heading);
      font-size: 1.6rem; letter-spacing: 3px;
      color: var(--accent-gold); text-decoration: none; font-weight: 700;
      cursor: pointer;
    }

    .nav-menu { display: flex; align-items: center; gap: 2rem; list-style: none; }
    .nav-link {
      color: var(--text-main); text-decoration: none;
      font-size: 0.8rem; letter-spacing: 2px; text-transform: uppercase;
      transition: var(--transition); cursor: pointer;
    }
    .nav-link:hover, .nav-link.active { color: var(--accent-gold); }

    .search-box { position: relative; display: flex; align-items: center; }
    .search-input {
      background: var(--bg-surface);
      border: 1px solid rgba(255,255,255,0.1);
      padding: 0.5rem 1rem; padding-right: 2.5rem;
      color: var(--text-main); font-family: var(--font-body);
      font-size: 0.8rem; width: 180px; transition: var(--transition);
    }
    .search-input:focus { width: 240px; border-color: var(--accent-gold); outline: none; }

    .cart-trigger {
      position: relative; cursor: pointer;
      font-size: 0.85rem; letter-spacing: 1.5px; color: var(--accent-gold);
    }
    .cart-badge {
      position: absolute; top: -8px; right: -12px;
      background: var(--accent-gold); color: #000;
      font-size: 0.65rem; font-weight: bold; width: 18px; height: 18px;
      border-radius: 50%; display: flex; align-items: center; justify-content: center;
    }

    main { max-width: 1400px; margin: 0 auto; padding: 2rem; }
    .page-section { display: none; animation: fadeIn 0.5s cubic-bezier(0.16, 1, 0.3, 1) forwards; }
    .page-section.active { display: block; }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .section-title {
      font-family: var(--font-heading); font-size: 2rem;
      letter-spacing: 3px; color: var(--text-main); margin-bottom: 0.5rem; text-transform: uppercase;
    }
    .section-subtitle { color: var(--text-muted); font-size: 0.85rem; letter-spacing: 1px; margin-bottom: 2.5rem; }

    .hero-banner {
      width: 100%; height: 520px; border: 1px solid var(--border-color);
      margin-bottom: 4rem; overflow: hidden; background: var(--bg-card); position: relative;
    }
    .hero-banner img {
      width: 100%; height: 100%; object-fit: cover; object-position: center;
      filter: brightness(0.75); cursor: pointer; transition: transform 0.6s ease;
    }
    .hero-banner img:hover { transform: scale(1.03); }

    .hero-overlay {
      position: absolute; inset: 0;
      background: radial-gradient(circle, rgba(10,10,10,0.2) 0%, rgba(10,10,10,0.7) 100%);
      display: flex; flex-direction: column; justify-content: center; align-items: center;
      text-align: center; padding: 2rem; pointer-events: none;
    }
    .hero-overlay h2 {
      font-family: var(--font-futuristic); font-size: 3.8rem; color: var(--accent-gold-light);
      letter-spacing: 10px; margin-bottom: 0.8rem; text-transform: uppercase;
      text-shadow: 0 0 20px rgba(0, 0, 0, 0.9), 0 0 10px rgba(212, 175, 55, 0.3);
    }
    .hero-overlay p {
      font-family: var(--font-futuristic); color: var(--text-main); font-size: 1.1rem;
      letter-spacing: 6px; text-transform: uppercase; font-weight: 500;
      text-shadow: 0 0 15px rgba(0, 0, 0, 0.9);
    }

    .product-grid {
      display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 2rem;
    }
    .empty-msg {
      grid-column: 1 / -1; text-align: center; padding: 4rem;
      background: var(--bg-card); border: 1px dashed var(--border-color); color: var(--text-muted);
    }

    .product-card {
      background: var(--bg-card); border: 1px solid rgba(255,255,255,0.05);
      padding: 1.5rem; position: relative; transition: var(--transition);
      display: flex; flex-direction: column;
    }
    .product-card:hover { border-color: var(--border-color); transform: translateY(-5px); }

    .offer-badge {
      position: absolute; top: 1rem; left: 1rem; background: var(--accent-gold);
      color: #000; font-size: 0.65rem; font-weight: bold; padding: 0.25rem 0.5rem;
      letter-spacing: 1px; text-transform: uppercase; z-index: 2;
    }

    .img-wrapper {
      position: relative; width: 100%; height: 240px; margin-bottom: 1.5rem;
      overflow: hidden; background-color: var(--bg-surface); cursor: pointer;
    }
    .img-wrapper::after {
      content: "🔍 Click to View"; position: absolute; inset: 0; background: rgba(0,0,0,0.5);
      color: var(--accent-gold-light); display: flex; align-items: center; justify-content: center;
      font-size: 0.8rem; letter-spacing: 1px; opacity: 0; transition: var(--transition);
    }
    .img-wrapper:hover::after { opacity: 1; }

    .product-img { width: 100%; height: 100%; object-fit: cover; transition: var(--transition); }
    .img-wrapper:hover .product-img { transform: scale(1.08); }

    .product-title { font-family: var(--font-heading); font-size: 1.1rem; margin-bottom: 0.5rem; color: var(--text-main); }
    .product-price { display: flex; align-items: center; gap: 10px; margin-bottom: 1rem; }
    .curr-price { color: var(--accent-gold); font-weight: 600; font-size: 1.1rem; }
    .old-price { color: var(--text-muted); text-decoration: line-through; font-size: 0.85rem; }

    .btn-action {
      margin-top: auto; padding: 0.75rem; background: transparent;
      border: 1px solid var(--border-color); color: var(--accent-gold);
      font-family: var(--font-body); font-size: 0.75rem; letter-spacing: 1.5px;
      text-transform: uppercase; cursor: pointer; transition: var(--transition);
    }
    .btn-action:hover { background: var(--accent-gold); color: #000; }

    .dashboard-panel, .inventory-panel {
      background: var(--bg-card); border: 1px solid var(--border-color);
      padding: 2.5rem; margin-bottom: 2rem;
    }
    .profile-info { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1.5rem; margin-bottom: 2rem; }
    .info-box { background: var(--bg-surface); padding: 1rem; border-left: 2px solid var(--accent-gold); }
    .info-box span { display: block; color: var(--text-muted); font-size: 0.75rem; text-transform: uppercase; }
    .info-box strong { font-size: 1rem; color: var(--text-main); }

    .inventory-form { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1rem; margin-bottom: 2rem; }
    .inventory-list { margin-top: 2rem; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 1.5rem; }
    .inventory-list-title { font-family: var(--font-heading); color: var(--accent-gold); margin-bottom: 1rem; font-size: 1.2rem; }

    .inventory-table { width: 100%; border-collapse: collapse; }
    .inventory-table th, .inventory-table td {
      padding: 0.8rem; text-align: left; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 0.85rem;
    }
    .inventory-table th { color: var(--text-muted); font-weight: 500; text-transform: uppercase; font-size: 0.75rem; }
    .inventory-item-img { width: 45px; height: 45px; object-fit: cover; cursor: pointer; border: 1px solid rgba(255,255,255,0.1); }

    .remove-btn {
      background: transparent; border: 1px solid #ff4d4d; color: #ff4d4d;
      padding: 0.4rem 0.8rem; font-size: 0.75rem; cursor: pointer; transition: var(--transition);
    }
    .remove-btn:hover { background: #ff4d4d; color: #fff; }

    .cart-drawer {
      position: fixed; top: 0; right: -450px; width: 450px; max-width: 100vw; height: 100vh;
      background: var(--bg-card); border-left: 1px solid var(--border-color);
      z-index: 500; transition: var(--transition); padding: 2rem;
      display: flex; flex-direction: column;
    }
    .cart-drawer.open { right: 0; }
    .cart-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 1.5rem; border-bottom: 1px solid rgba(255,255,255,0.1); padding-bottom: 1rem; }
    .cart-items { flex: 1; overflow-y: auto; }
    .cart-item { display: flex; align-items: center; gap: 12px; margin-bottom: 1rem; background: var(--bg-surface); padding: 0.75rem; border: 1px solid rgba(255,255,255,0.05); }
    .cart-item-img { width: 60px; height: 60px; object-fit: cover; background: var(--bg-card); cursor: pointer; }
    .cart-item-details { flex: 1; }
    .cart-item-title { font-size: 0.85rem; font-weight: 600; color: var(--text-main); margin-bottom: 4px; }
    .cart-item-price { color: var(--accent-gold); font-size: 0.8rem; }
    .qty-controls { display: flex; align-items: center; gap: 6px; margin-top: 6px; }
    .qty-btn { width: 22px; height: 22px; background: transparent; border: 1px solid var(--border-color); color: var(--accent-gold); font-size: 0.8rem; cursor: pointer; display: flex; align-items: center; justify-content: center; }
    .qty-btn:hover { background: var(--accent-gold); color: #000; }
    .qty-val { font-size: 0.8rem; font-weight: bold; width: 20px; text-align: center; }
    .delete-btn { cursor: pointer; color: var(--text-muted); font-size: 1.1rem; transition: var(--transition); padding: 0 4px; }
    .delete-btn:hover { color: #ff4d4d; }
    .cart-footer { border-top: 1px solid rgba(255,255,255,0.1); padding-top: 1rem; }

    #image-modal {
      position: fixed; inset: 0; background: rgba(0, 0, 0, 0.9); backdrop-filter: blur(10px);
      z-index: 2000; display: none; align-items: center; justify-content: center; flex-direction: column; padding: 2rem;
    }
    #image-modal.open { display: flex; animation: fadeIn 0.3s ease; }
    .modal-img-container { max-width: 90vw; max-height: 80vh; border: 1px solid var(--border-color); box-shadow: 0 0 30px rgba(212, 175, 55, 0.2); position: relative; }
    .modal-img-container img { max-width: 100%; max-height: 80vh; object-fit: contain; display: block; }
    .modal-caption { margin-top: 1rem; font-family: var(--font-heading); color: var(--accent-gold-light); font-size: 1.2rem; letter-spacing: 2px; text-align: center; }
    .close-modal { position: absolute; top: 20px; right: 30px; color: var(--accent-gold); font-size: 2.5rem; cursor: pointer; transition: var(--transition); }
    .close-modal:hover { color: #fff; }
  `;
  document.head.appendChild(styleSheet);

  const authOverlay = document.createElement("div");
  authOverlay.id = "auth-overlay";

  const authCard = document.createElement("div");
  authCard.className = "auth-card";

  const authH1 = document.createElement("h1");
  authH1.innerText = "ARBAN TIME";

  const googleBtn = document.createElement("button");
  googleBtn.className = "auth-btn";
  googleBtn.innerHTML = `<svg width="18" height="18" viewBox="0 0 24 24"><path fill="currentColor" d="M21.35 11.1h-9.17v2.73h6.51c-.33 1.76-1.82 3.08-3.79 3.08-2.3 0-4.16-1.87-4.16-4.16s1.86-4.16 4.16-4.16c1.05 0 2.01.39 2.74 1.03l2.05-2.05C18.39 6.28 16.51 5.5 14.33 5.5 9.73 5.5 6 9.23 6 13.83s3.73 8.33 8.33 8.33c4.8 0 8.01-3.37 8.01-8.15 0-.62-.06-1.22-.19-1.91z"/></svg> Continue with Gmail`;
  googleBtn.onclick = () => authenticate("Google User");

  const authDivider = document.createElement("div");
  authDivider.className = "auth-divider";
  const authSpan = document.createElement("span");
  authSpan.innerText = "OR PHONE";
  authDivider.appendChild(authSpan);

  const phoneInput = document.createElement("input");
  phoneInput.type = "tel";
  phoneInput.id = "auth-phone";
  phoneInput.className = "input-field";
  phoneInput.placeholder = "+880 1XXX XXXXXX";

  const phoneBtn = document.createElement("button");
  phoneBtn.className = "auth-btn";
  phoneBtn.innerText = "Access Store";
  phoneBtn.onclick = authenticateWithPhone;

  authCard.appendChild(authH1);
  authCard.appendChild(googleBtn);
  authCard.appendChild(authDivider);
  authCard.appendChild(phoneInput);
  authCard.appendChild(phoneBtn);
  authOverlay.appendChild(authCard);
  document.body.appendChild(authOverlay);

  const imageModal = document.createElement("div");
  imageModal.id = "image-modal";
  imageModal.onclick = closeImageModal;

  const closeModal = document.createElement("span");
  closeModal.className = "close-modal";
  closeModal.innerHTML = "&times;";

  const modalImgContainer = document.createElement("div");
  modalImgContainer.className = "modal-img-container";
  modalImgContainer.onclick = (e) => e.stopPropagation();

  const modalImgElement = document.createElement("img");
  modalImgElement.id = "modal-img-element";
  modalImgElement.src = "";
  modalImgElement.alt = "Timepiece Preview";

  const modalCaptionText = document.createElement("div");
  modalCaptionText.id = "modal-caption-text";
  modalCaptionText.className = "modal-caption";

  modalImgContainer.appendChild(modalImgElement);
  imageModal.appendChild(closeModal);
  imageModal.appendChild(modalImgContainer);
  imageModal.appendChild(modalCaptionText);
  document.body.appendChild(imageModal);

  const header = document.createElement("header");
  const navContainer = document.createElement("div");
  navContainer.className = "nav-container";

  const brandLogo = document.createElement("a");
  brandLogo.className = "brand-logo";
  brandLogo.innerText = "ARBAN TIME";
  brandLogo.onclick = () => switchSection("home");

  const navMenu = document.createElement("ul");
  navMenu.className = "nav-menu";

  const sections = ["home", "catalog", "dashboard", "inventory"];
  sections.forEach((sec, idx) => {
    const li = document.createElement("li");
    const a = document.createElement("a");
    a.className = "nav-link" + (idx === 0 ? " active" : "");
    a.innerText = sec.charAt(0).toUpperCase() + sec.slice(1);
    a.onclick = function () { switchSection(sec, this); };
    li.appendChild(a);
    navMenu.appendChild(li);
  });

  const rightNav = document.createElement("div");
  rightNav.style.display = "flex";
  rightNav.style.alignItems = "center";
  rightNav.style.gap = "1.5rem";

  const searchBox = document.createElement("div");
  searchBox.className = "search-box";

  const searchInput = document.createElement("input");
  searchInput.type = "text";
  searchInput.className = "search-input";
  searchInput.id = "search-bar";
  searchInput.placeholder = "Search timepiece...";
  searchInput.onkeyup = filterProducts;
  searchBox.appendChild(searchInput);

  const cartTrigger = document.createElement("div");
  cartTrigger.className = "cart-trigger";
  cartTrigger.onclick = toggleCart;
  cartTrigger.innerHTML = `CART <span class="cart-badge" id="cart-count">0</span>`;

  rightNav.appendChild(searchBox);
  rightNav.appendChild(cartTrigger);

  navContainer.appendChild(brandLogo);
  navContainer.appendChild(navMenu);
  navContainer.appendChild(rightNav);
  header.appendChild(navContainer);
  document.body.appendChild(header);

  const main = document.createElement("main");

  const homeSec = document.createElement("section");
  homeSec.id = "home";
  homeSec.className = "page-section active";

  const heroBanner = document.createElement("div");
  heroBanner.className = "hero-banner";

  const heroImg = document.createElement("img");
  heroImg.src = "https://img.drz.lazcdn.com/static/bd/p/78f20ea8abb9d4985742ebf10d5d054d.png_960x960q80.png_.webp";
  heroImg.alt = "Hero Watch";
  heroImg.onclick = () => openImageModal(heroImg.src, "Poedagar Leather Belt (Black)");

  const heroOverlay = document.createElement("div");
  heroOverlay.className = "hero-overlay";
  heroOverlay.innerHTML = `<h2>ARBAN TIME</h2><p>Luxury On Your Wrist</p>`;

  heroBanner.appendChild(heroImg);
  heroBanner.appendChild(heroOverlay);

  const offersTitle = document.createElement("h3");
  offersTitle.className = "section-title";
  offersTitle.innerText = "Special Offers";

  const offersSubtitle = document.createElement("p");
  offersSubtitle.className = "section-subtitle";
  offersSubtitle.innerText = "Exclusive timepieces currently with privilege discounts";

  const offersGrid = document.createElement("div");
  offersGrid.className = "product-grid";
  offersGrid.id = "offers-grid";

  homeSec.appendChild(heroBanner);
  homeSec.appendChild(offersTitle);
  homeSec.appendChild(offersSubtitle);
  homeSec.appendChild(offersGrid);

  const catalogSec = document.createElement("section");
  catalogSec.id = "catalog";
  catalogSec.className = "page-section";

  const catTitle = document.createElement("h3");
  catTitle.className = "section-title";
  catTitle.innerText = "Complete Collection";

  const catSubtitle = document.createElement("p");
  catSubtitle.className = "section-subtitle";
  catSubtitle.innerText = "Browse all available horological creations";

  const catalogGrid = document.createElement("div");
  catalogGrid.className = "product-grid";
  catalogGrid.id = "catalog-grid";

  catalogSec.appendChild(catTitle);
  catalogSec.appendChild(catSubtitle);
  catalogSec.appendChild(catalogGrid);

  const dashSec = document.createElement("section");
  dashSec.id = "dashboard";
  dashSec.className = "page-section";

  const dashTitle = document.createElement("h3");
  dashTitle.className = "section-title";
  dashTitle.innerText = "Client Dashboard";

  const dashSubtitle = document.createElement("p");
  dashSubtitle.className = "section-subtitle";
  dashSubtitle.innerText = "Personal account overview and order history";

  const dashPanel = document.createElement("div");
  dashPanel.className = "dashboard-panel";
  dashPanel.innerHTML = `
    <div class="profile-info">
      <div class="info-box"><span>Client Identification</span><strong id="user-display-id">Not Logged In</strong></div>
      <div class="info-box"><span>Membership Status</span><strong style="color: var(--accent-gold);">Patron Circle</strong></div>
      <div class="info-box"><span>Acquisitions</span><strong id="dashboard-items-count">0 Timepieces</strong></div>
    </div>
  `;

  dashSec.appendChild(dashTitle);
  dashSec.appendChild(dashSubtitle);
  dashSec.appendChild(dashPanel);

  const invSec = document.createElement("section");
  invSec.id = "inventory";
  invSec.className = "page-section";

  const invTitle = document.createElement("h3");
  invTitle.className = "section-title";
  invTitle.innerText = "Inventory Management";

  const invSubtitle = document.createElement("p");
  invSubtitle.className = "section-subtitle";
  invSubtitle.innerText = "Add new watch items (New items will stay on this device)";

  const invPanel = document.createElement("div");
  invPanel.className = "inventory-panel";

  const invForm = document.createElement("form");
  invForm.className = "inventory-form";
  invForm.onsubmit = addNewWatch;

  invForm.innerHTML = `
    <input type="text" id="watch-title" class="input-field" placeholder="Watch Title (e.g. Rolex Gold)" required>
    <input type="number" id="watch-price" class="input-field" placeholder="Regular Price (BDT ৳)" required>
    <input type="number" id="watch-offer-price" class="input-field" placeholder="Offer Price (BDT ৳ - Optional)">
    <input type="text" id="watch-img" class="input-field" placeholder="Image URL" required>
    <button type="submit" class="btn-action" style="grid-column: 1 / -1;">Save Watch</button>
  `;

  const invList = document.createElement("div");
  invList.className = "inventory-list";
  invList.innerHTML = `<h4 class="inventory-list-title">Current Inventory Items</h4><div id="inventory-table-container"></div>`;

  const resetBtn = document.createElement("button");
  resetBtn.className = "btn-action";
  resetBtn.style.borderColor = "#ff4d4d";
  resetBtn.style.color = "#ff4d4d";
  resetBtn.style.marginTop = "2rem";
  resetBtn.innerText = "Reset to Default Permanent Catalog";
  resetBtn.onclick = resetToHardcodedData;

  invPanel.appendChild(invForm);
  invPanel.appendChild(invList);
  invPanel.appendChild(resetBtn);

  invSec.appendChild(invTitle);
  invSec.appendChild(invSubtitle);
  invSec.appendChild(invPanel);

  main.appendChild(homeSec);
  main.appendChild(catalogSec);
  main.appendChild(dashSec);
  main.appendChild(invSec);

  document.body.appendChild(main);

  const cartDrawer = document.createElement("div");
  cartDrawer.className = "cart-drawer";
  cartDrawer.id = "cart-drawer";

  cartDrawer.innerHTML = `
    <div class="cart-header">
      <h4 style="font-family: var(--font-heading); color: var(--accent-gold);">YOUR SELECTION</h4>
      <span style="cursor: pointer; font-size: 1.2rem;" id="close-cart-btn">✕</span>
    </div>
    <div class="cart-items" id="cart-items"></div>
    <div class="cart-footer">
      <div style="display: flex; justify-content: space-between; margin-bottom: 1rem;">
        <span>Total Value:</span>
        <strong id="cart-total" style="color: var(--accent-gold);">৳0</strong>
      </div>
      <button class="btn-action" style="width: 100%;">Proceed to Checkout</button>
    </div>
  `;

  document.body.appendChild(cartDrawer);
  document.getElementById("close-cart-btn").onclick = toggleCart;

  function saveInventory() {
    localStorage.setItem('arban_time_inventory_v3', JSON.stringify(inventory));
  }

  function resetToHardcodedData() {
    inventory = processDefaultWatches(DEFAULT_WATCHES);
    saveInventory();
    renderProducts();
    alert('ডিফল্ট ইনভেন্টরি রিলোড হয়েছে!');
  }

  function authenticate(identity) {
    document.getElementById('auth-overlay').style.display = 'none';
    document.getElementById('user-display-id').innerText = identity;
  }

  function authenticateWithPhone() {
    const phone = document.getElementById('auth-phone').value;
    if (phone.trim()) authenticate(phone);
    else alert('Please enter a valid phone number');
  }

  function switchSection(sectionId, element) {
    document.querySelectorAll('.page-section').forEach(sec => sec.classList.remove('active'));
    document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));
    document.getElementById(sectionId).classList.add('active');
    if (element) {
      element.classList.add('active');
    } else {
      const activeNav = Array.from(document.querySelectorAll('.nav-link')).find(el => el.innerText.toLowerCase() === sectionId.toLowerCase());
      if (activeNav) activeNav.classList.add('active');
    }
  }

  function openImageModal(imgSrc, title) {
    document.getElementById('modal-img-element').src = imgSrc || DEFAULT_FALLBACK_IMG;
    document.getElementById('modal-caption-text').innerText = title || 'Timepiece Preview';
    document.getElementById('image-modal').classList.add('open');
  }

  function closeImageModal() {
    document.getElementById('image-modal').classList.remove('open');
  }

  function renderProducts() {
    const offersGrid = document.getElementById('offers-grid');
    const catalogGrid = document.getElementById('catalog-grid');

    offersGrid.innerHTML = '';
    catalogGrid.innerHTML = '';

    renderInventoryTable();

    if (inventory.length === 0) {
      catalogGrid.innerHTML = `<div class="empty-msg">No watches in inventory.</div>`;
      offersGrid.innerHTML = `<div class="empty-msg">No special offers available.</div>`;
      return;
    }

    let hasOffers = false;

    inventory.forEach(item => {
      const displayPrice = item.isOffer ? item.offerPrice : item.price;
      const cardHTML = `
        <div class="product-card">
          ${item.isOffer ? '<span class="offer-badge">Special Offer</span>' : ''}
          <div class="img-wrapper" data-img="${item.img}" data-title="${item.name.replace(/"/g, '&quot;')}">
            <img src="${item.img}" class="product-img" alt="${item.name}" onerror="this.onerror=null; this.src='${DEFAULT_FALLBACK_IMG}';">
          </div>
          <h4 class="product-title">${item.name}</h4>
          <div class="product-price">
            <span class="curr-price">৳${Number(displayPrice).toLocaleString()}</span>
            ${item.isOffer ? `<span class="old-price">৳${Number(item.price).toLocaleString()}</span>` : ''}
          </div>
          <button class="btn-action" data-add-id="${item.id}">Add to Cart</button>
        </div>
      `;

      catalogGrid.innerHTML += cardHTML;
      if (item.isOffer) {
        offersGrid.innerHTML += cardHTML;
        hasOffers = true;
      }
    });

    if (!hasOffers) {
      offersGrid.innerHTML = `<div class="empty-msg">No special offer items in current collection.</div>`;
    }

    document.querySelectorAll('.img-wrapper').forEach(wrapper => {
      wrapper.onclick = function () {
        openImageModal(this.getAttribute('data-img'), this.getAttribute('data-title'));
      };
    });

    document.querySelectorAll('button[data-add-id]').forEach(btn => {
      btn.onclick = function () {
        addToCart(Number(this.getAttribute('data-add-id')));
      };
    });
  }

  function renderInventoryTable() {
    const container = document.getElementById('inventory-table-container');
    if (inventory.length === 0) {
      container.innerHTML = `<p style="color: var(--text-muted); font-size: 0.85rem;">Inventory is currently empty.</p>`;
      return;
    }

    let tableHTML = `
      <table class="inventory-table">
        <thead>
          <tr>
            <th>Preview</th>
            <th>Watch Title</th>
            <th>Price</th>
            <th>Offer Price</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
    `;

    inventory.forEach(item => {
      tableHTML += `
        <tr>
          <td>
            <img src="${item.img}" class="inventory-item-img" alt="${item.name}" 
                 data-img="${item.img}" data-title="${item.name.replace(/"/g, '&quot;')}"
                 onerror="this.onerror=null; this.src='${DEFAULT_FALLBACK_IMG}';">
          </td>
          <td><strong>${item.name}</strong></td>
          <td>৳${Number(item.price).toLocaleString()}</td>
          <td>${item.isOffer ? '৳' + Number(item.offerPrice).toLocaleString() : 'N/A'}</td>
          <td>
            <button class="remove-btn" data-remove-id="${item.id}">🗑 Delete</button>
          </td>
        </tr>
      `;
    });

    tableHTML += `</tbody></table>`;
    container.innerHTML = tableHTML;

    container.querySelectorAll('.inventory-item-img').forEach(img => {
      img.onclick = function () {
        openImageModal(this.getAttribute('data-img'), this.getAttribute('data-title'));
      };
    });

    container.querySelectorAll('button[data-remove-id]').forEach(btn => {
      btn.onclick = function () {
        removeInventoryItem(Number(this.getAttribute('data-remove-id')));
      };
    });
  }

  function removeInventoryItem(id) {
    inventory = inventory.filter(i => i.id !== id);
    saveInventory();
    renderProducts();
  }

  function addNewWatch(e) {
    e.preventDefault();
    const name = document.getElementById('watch-title').value.trim();
    const price = parseFloat(document.getElementById('watch-price').value);
    const offerPriceInput = document.getElementById('watch-offer-price').value;
    const img = document.getElementById('watch-img').value.trim();

    const offerPrice = offerPriceInput ? parseFloat(offerPriceInput) : 0;
    const isOffer = offerPrice > 0 && offerPrice < price;

    const newItem = {
      id: Date.now(),
      name,
      price,
      offerPrice: isOffer ? offerPrice : 0,
      isOffer,
      img
    };

    inventory.push(newItem);
    saveInventory();
    renderProducts();
    e.target.reset();
    alert('Watch added successfully!');
  }

  function toggleCart() {
    document.getElementById('cart-drawer').classList.toggle('open');
  }

  function addToCart(id) {
    const item = inventory.find(i => i.id === id);
    if (!item) return;
    const existingInCart = cart.find(c => c.id === id);
    if (existingInCart) existingInCart.qty += 1;
    else cart.push({ ...item, qty: 1 });
    updateCartUI();
    toggleCart();
  }

  function changeQty(id, delta) {
    const cartItem = cart.find(c => c.id === id);
    if (cartItem) {
      cartItem.qty += delta;
      if (cartItem.qty <= 0) cart = cart.filter(c => c.id !== id);
    }
    updateCartUI();
  }

  function removeFromCart(id) {
    cart = cart.filter(c => c.id !== id);
    updateCartUI();
  }

  function updateCartUI() {
    const container = document.getElementById('cart-items');
    container.innerHTML = '';
    let totalQty = 0, totalPrice = 0;

    cart.forEach(item => {
      const itemPrice = item.isOffer ? item.offerPrice : item.price;
      const itemTotal = itemPrice * item.qty;
      totalQty += item.qty;
      totalPrice += itemTotal;

      container.innerHTML += `
        <div class="cart-item">
          <img src="${item.img}" class="cart-item-img" alt="${item.name}" onerror="this.onerror=null; this.src='${DEFAULT_FALLBACK_IMG}';">
          <div class="cart-item-details">
            <div class="cart-item-title">${item.name}</div>
            <div class="cart-item-price">৳${Number(itemPrice).toLocaleString()}</div>
            <div class="qty-controls">
              <button class="qty-btn" data-qty-id="${item.id}" data-delta="-1">-</button>
              <span class="qty-val">${item.qty}</span>
              <button class="qty-btn" data-qty-id="${item.id}" data-delta="1">+</button>
            </div>
          </div>
          <span class="delete-btn" data-cart-remove-id="${item.id}">🗑</span>
        </div>
      `;
    });

    document.getElementById('cart-count').innerText = totalQty;
    document.getElementById('cart-total').innerText = `৳${totalPrice.toLocaleString()}`;
    document.getElementById('dashboard-items-count').innerText = `${totalQty} Timepieces`;

    container.querySelectorAll('button[data-qty-id]').forEach(btn => {
      btn.onclick = function () {
        changeQty(Number(this.getAttribute('data-qty-id')), Number(this.getAttribute('data-delta')));
      };
    });

    container.querySelectorAll('.delete-btn[data-cart-remove-id]').forEach(btn => {
      btn.onclick = function () {
        removeFromCart(Number(this.getAttribute('data-cart-remove-id')));
      };
    });
  }

  function filterProducts() {
    const query = document.getElementById('search-bar').value.toLowerCase();
    const cards = document.querySelectorAll('#catalog-grid .product-card');
    cards.forEach(card => {
      const title = card.querySelector('.product-title').innerText.toLowerCase();
      card.style.display = title.includes(query) ? 'flex' : 'none';
    });
  }

  renderProducts();
})();
