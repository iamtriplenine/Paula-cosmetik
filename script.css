// ===========================
// CONFIG
// ===========================
const WHATSAPP_NUMBER = "2250700000000"; // <-- remplace par le vrai numéro

const products = [
  {
    id: 1,
    name: "Lait éclat intense",
    price: "10 000 FCFA",
    desc: "Hydrate et illumine la peau. Texture légère, fini glow.",
    tags: ["Glow", "Hydratation"],
    image: "https://images.unsplash.com/photo-1611930022073-b7a4ba5fcccd?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: true
  },
  {
    id: 2,
    name: "Crème visage douceur",
    price: "7 500 FCFA",
    desc: "Confort immédiat, peau plus souple et plus lisse.",
    tags: ["Visage", "Daily"],
    image: "https://images.unsplash.com/photo-1616394584738-fc6e612e71b9?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: true
  },
  {
    id: 3,
    name: "Sérum réparateur",
    price: "12 000 FCFA",
    desc: "Aide à réparer, unifie et booste l’éclat.",
    tags: ["Sérum", "Éclat"],
    image: "https://images.unsplash.com/photo-1620916566393-e7c5a7e15f4e?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: false
  },
  {
    id: 4,
    name: "Huile nourrissante",
    price: "8 500 FCFA",
    desc: "Nourrit en profondeur, parfum doux, fini soyeux.",
    tags: ["Huile", "Corps"],
    image: "https://images.unsplash.com/photo-1612810436541-336d6fcd0c68?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: false
  },
  {
    id: 5,
    name: "Savon clarifiant",
    price: "3 000 FCFA",
    desc: "Nettoie sans agresser, peau nette et fraîche.",
    tags: ["Nettoyant", "Peau"],
    image: "https://images.unsplash.com/photo-1608248543803-ba4f8c70ae0b?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: true
  },
  {
    id: 6,
    name: "Brume parfumée",
    price: "6 000 FCFA",
    desc: "Un voile léger et chic pour la journée.",
    tags: ["Parfum", "Brume"],
    image: "https://images.unsplash.com/photo-1619994403073-2cec844b8e63?q=80&w=1200&auto=format&fit=crop",
    desc: "Peau sensible et délicate ? Ce combo hydrate en profondeur, agit en douceur et aide à uniformiser progressivement le teint...",
    best: false
  }
];

// ===========================
// HELPERS
// ===========================
function whatsappLink(message) {
  const encoded = encodeURIComponent(message);
  return `https://wa.me/${WHATSAPP_NUMBER}?text=${encoded}`;
}

function formatMeta(count, total) {
  if (count === total) return `${total} produit(s) affiché(s)`;
  return `${count} résultat(s) sur ${total}`;
}

function normalize(str) {
  return (str || "")
    .toString()
    .toLowerCase()
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g, "");
}

// ===========================
// THEME (dark mode + save)
// ===========================
const themeBtn = document.getElementById("themeBtn");
const savedTheme = localStorage.getItem("theme"); // "light" | "dark" | null

if (savedTheme === "light") document.body.classList.add("light");
if (savedTheme === "dark") document.body.classList.remove("light"); // dark par défaut

function toggleTheme() {
  // dark = default (no class), light = body.light
  document.body.classList.toggle("light");
  localStorage.setItem("theme", document.body.classList.contains("light") ? "light" : "dark");
}

themeBtn?.addEventListener("click", toggleTheme);

// ===========================
// WhatsApp global buttons
// ===========================
const whatsHeader = document.getElementById("whatsHeader");
const whatsHero = document.getElementById("whatsHero");
const whatsFloat = document.getElementById("whatsFloat");

const globalMsg = "Bonjour Paula Cosmetik, je veux passer une commande. Pouvez-vous m’aider ?";

[whatsHeader, whatsHero, whatsFloat].forEach(el => {
  if (!el) return;
  el.href = whatsappLink(globalMsg);
});

// ===========================
// RENDER
// ===========================
const grid = document.getElementById("productGrid");
const bestSellers = document.getElementById("bestSellers");
const resultsMeta = document.getElementById("resultsMeta");
const emptyState = document.getElementById("emptyState");
const searchInput = document.getElementById("searchInput");

function renderBestSellers() {
  const best = products.filter(p => p.best).slice(0, 3);

  bestSellers.innerHTML = best.map(p => `
    <div class="mini">
      <img src="${p.image}" alt="${p.name}">
      <div>
        <div class="mini__name">${p.name}</div>
        <div class="mini__price">${p.price}</div>
      </div>
    </div>
  `).join("");
}

function productCard(p) {
  const tags = (p.tags || []).slice(0, 2).map(t => `<span class="badge">${t}</span>`).join("");

  return `
    <article class="card product-card" data-id="${p.id}" tabindex="0" role="button" aria-label="Voir ${p.name}">
      <img class="card__img" src="${p.image}" alt="${p.name}">
      <div class="card__body">
        <div class="card__top">
          <div class="card__name">${p.name}</div>
          <div class="card__price">${p.price}</div>
        </div>
        <div class="card__desc">${p.desc}</div>
        <div class="card__row">
          ${tags}
          <span class="btn btn--ghost" style="pointer-events:none;">Voir détails</span>
        </div>
      </div>
    </article>
  `;
}

function renderProducts(list) {
  grid.innerHTML = list.map(productCard).join("");

  resultsMeta.textContent = formatMeta(list.length, products.length);

  if (list.length === 0) emptyState.classList.remove("hidden");
  else emptyState.classList.add("hidden");
}

function applySearch() {
  const q = normalize(searchInput.value).trim();
  if (!q) return renderProducts(products);

  const filtered = products.filter(p => {
    const hay = normalize(`${p.name} ${p.desc} ${(p.tags || []).join(" ")}`);
    return hay.includes(q);
  });

  renderProducts(filtered);
}

searchInput?.addEventListener("input", applySearch);

// Init
renderBestSellers();
renderProducts(products);









// ===========================
// MODAL PRODUIT (popup + blur)
// ===========================
const modalOverlay = document.getElementById("modalOverlay");
const modalClose = document.getElementById("modalClose");

const modalImg = document.getElementById("modalImg");
const modalName = document.getElementById("modalName");
const modalPrice = document.getElementById("modalPrice");
const modalTags = document.getElementById("modalTags");
const modalDesc = document.getElementById("modalDesc");
const modalWhats = document.getElementById("modalWhats");
const modalCopy = document.getElementById("modalCopy");

function openModal(product) {
  // Remplir contenu
  modalImg.src = product.image;
  modalImg.alt = product.name;
  modalName.textContent = product.name;
  modalPrice.textContent = product.price;

  modalTags.innerHTML = (product.tags || [])
    .map(t => `<span class="badge">${t}</span>`)
    .join("");

  modalDesc.textContent = product.desc || "";

  const msg = `Bonjour Paula Cosmetik, je veux commander : ${product.name} (${product.price}).`;
  modalWhats.href = whatsappLink(msg);

  // Afficher
  modalOverlay.classList.remove("hidden");
  document.body.classList.add("modal-open");
  modalOverlay.setAttribute("aria-hidden", "false");

  // Empêcher scroll page derrière
  document.body.style.overflow = "hidden";
}

function closeModal() {
  modalOverlay.classList.add("hidden");
  document.body.classList.remove("modal-open");
  modalOverlay.setAttribute("aria-hidden", "true");
  document.body.style.overflow = "";
}

// Délégation de clic : chaque carte produit ouvre le modal
document.addEventListener("click", (e) => {
  const card = e.target.closest(".product-card");
  if (!card) return;

  const id = Number(card.dataset.id);
  const product = products.find(p => p.id === id);
  if (!product) return;

  openModal(product);
});

// Fermer : bouton X
modalClose?.addEventListener("click", closeModal);

// Fermer : clic sur overlay (en dehors de la boîte)
modalOverlay?.addEventListener("click", (e) => {
  if (e.target === modalOverlay) closeModal();
});

// Fermer : touche ESC
document.addEventListener("keydown", (e) => {
  if (e.key === "Escape" && !modalOverlay.classList.contains("hidden")) {
    closeModal();
  }
});

// Copier le nom du produit
modalCopy?.addEventListener("click", async () => {
  try {
    await navigator.clipboard.writeText(modalName.textContent || "");
    modalCopy.textContent = "Copié ✅";
    setTimeout(() => (modalCopy.textContent = "Copier le nom"), 1200);
  } catch {
    modalCopy.textContent = "Impossible";
    setTimeout(() => (modalCopy.textContent = "Copier le nom"), 1200);
  }
});
