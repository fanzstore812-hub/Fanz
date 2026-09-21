<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FANZ JOKI - Clone RoxyJoki</title>
<style>
* { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', system-ui, sans-serif; }
body { background: #0B1512; color: #fff; padding-bottom: 90px; }

/* TOP BAR */
.topbar {
  background: #0F1E1C;
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px 16px;
  position: sticky;
  top: 0;
  z-index: 100;
}
.logo {
  width: 44px;
  height: 44px;
  border-radius: 50%;
  border: 2px solid #7CFB7C;
  object-fit: cover;
  background: #000814;
  flex-shrink: 0;
}
.brand { font-weight: bold; font-size: 17px; }
.ver {
  background: #1E88E5;
  border-radius: 50%;
  width: 16px;
  height: 16px;
  font-size: 10px;
  color: white;
  margin-left: 4px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

/* TICKER */
.ticker {
  background: #1A2E2A;
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 6px 12px;
  overflow: hidden;
}
.badge {
  background: #2E7D32;
  color: #fff;
  font-size: 12px;
  padding: 3px 10px;
  border-radius: 20px;
  font-weight: bold;
  flex-shrink: 0;
}
.ticker marquee { color: #D9F99D; font-size: 13px; }

/* BANNER */
.banner-wrap { padding: 12px 16px; }
.banner {
  width: 100%;
  height: 160px;
  border-radius: 18px;
  object-fit: cover;
  display: block;
}

/* GRID MENU */
.grid-menu {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
  padding: 4px 16px 16px;
}
.menu-btn {
  background: #1E332E;
  border: 1px solid #2A4A3E;
  border-radius: 14px;
  color: #fff;
  padding: 14px 6px;
  font-size: 12px;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  transition: .2s;
  line-height: 1.6;
}
.menu-btn:hover { background: #26463D; }

/* HOME */
#home {
  display: block;
  padding: 0 16px 16px;
}
.card {
  background: #1E332E;
  border: 1px solid #2A4A3E;
  border-radius: 16px;
  padding: 18px;
  margin-bottom: 14px;
}
.card h3 { margin-bottom: 8px; color: #D9F99D; }
.card p { font-size: 13px; color: #b8ccc5; margin-bottom: 14px; line-height: 1.5; }
.btn-lihat {
  background: linear-gradient(90deg, #7CFB7C, #D9F99D);
  color: #0F1E1C;
  border: none;
  padding: 10px 18px;
  border-radius: 10px;
  font-weight: bold;
  cursor: pointer;
  width: 100%;
}

/* LIST PAGE */
.listPage {
  display: none;
  pointer-events: auto !important;
  position: relative;
  z-index: 2;
  padding: 16px;
}
#joki, #digital, #csWrap {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.listPage h3 {
  margin: 12px 0 16px;
  color: #D9F99D;
  font-size: 18px;
}
.back {
  background: #1E332E;
  border: 1px solid #2A4A3E;
  color: #D9F99D;
  padding: 8px 16px;
  border-radius: 10px;
  cursor: pointer;
  font-weight: bold;
}

/* ITEM */
.item {
  background: #1E332E;
  border: 1px solid #2A4A3E;
  border-radius: 14px;
  padding: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
  z-index: 5;
}
.item b { font-size: 14px; }
.pr { color: #7CFB7C; font-size: 13px; margin-top: 4px; }
.btn-order {
  background: linear-gradient(90deg, #7CFB7C, #D9F99D) !important;
  color: #0F1E1C !important;
  border: none !important;
  padding: 10px 18px;
  border-radius: 10px;
  font-weight: bold;
  cursor: pointer !important;
  z-index: 99 !important;
  pointer-events: auto !important;
  position: relative !important;
}

/* CS CARD */
.cs-card {
  background: #1E332E;
  border: 1px solid #2A4A3E;
  border-radius: 16px;
  padding: 22px;
  text-align: center;
}
.cs-avatar {
  width: 90px;
  height: 90px;
  border-radius: 50%;
  margin: 0 auto 14px;
  background: linear-gradient(135deg, #7CFB7C, #00B0FF);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 44px;
  box-shadow: 0 0 24px rgba(124,251,124,0.4);
}
.cs-card h3 { color: #D9F99D; margin-bottom: 6px; font-size: 18px; }
.cs-card p { color: #b8ccc5; font-size: 13px; margin-bottom: 18px; line-height: 1.6; }
.cs-wa-btn {
  display: inline-block;
  background: linear-gradient(90deg, #25D366, #7CFB7C);
  color: #0F1E1C;
  text-decoration: none;
  padding: 14px 26px;
  border-radius: 12px;
  font-weight: bold;
  font-size: 15px;
  box-shadow: 0 6px 18px rgba(37,211,102,0.35);
}
.cs-wa-btn:active { transform: scale(0.98); }
.cs-info {
  margin-top: 18px;
  padding-top: 14px;
  border-top: 1px solid #2A4A3E;
  font-size: 12px;
  color: #8aa39b;
  text-align: left;
  line-height: 1.8;
}

/* NAVBAR */
.navbar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: #0F1E1C;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 8px 6px;
  z-index: 500;
  border-top: 1px solid #1E332E;
}
.nav-item {
  background: transparent;
  border: none;
  color: #b8ccc5;
  font-size: 11px;
  text-align: center;
  text-decoration: none;
  cursor: pointer;
  padding: 6px 4px;
  line-height: 1.5;
  flex: 1;
}
.nav-home {
  background: linear-gradient(135deg, #7CFB7C, #D9F99D);
  color: #0F1E1C;
  border-radius: 16px;
  margin-top: -14px;
  padding: 10px 4px;
  font-weight: bold;
}
.nav-home.active { box-shadow: 0 4px 14px rgba(124,251,124,.5); }

/* OVERLAY */
#overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.85);
  z-index: 9999;
  align-items: center;
  justify-content: center;
  padding: 16px;
}
.overlay-box {
  background: #12211D;
  border: 1px solid #2A4A3E;
  border-radius: 18px;
  padding: 20px;
  width: 100%;
  max-width: 420px;
  max-height: 90vh;
  overflow-y: auto;
}
.step { display: none; flex-direction: column; gap: 10px; }
.step h4 { color: #D9F99D; margin-bottom: 6px; }
#format, #finalFormat {
  width: 100%;
  background: #0B1512;
  border: 1px solid #2A4A3E;
  border-radius: 10px;
  color: #fff;
  padding: 10px;
  font-size: 13px;
  resize: vertical;
}
#finalFormat { height: auto; }
.timer { text-align: center; color: #D9F99D; font-weight: bold; font-size: 18px; }
.btn-lanjut, .btn-wa {
  background: linear-gradient(90deg, #7CFB7C, #D9F99D);
  color: #0F1E1C;
  border: none;
  padding: 12px;
  border-radius: 10px;
  font-weight: bold;
  cursor: pointer;
  text-align: center;
  text-decoration: none;
  display: block;
}
.btn-tutup {
  background: #2A4A3E;
  color: #fff;
  border: none;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
}

/* KARTU QRIS */
.qris-card {
  background: #FFFFFF;
  border-radius: 14px;
  padding: 16px;
  color: #111;
  text-align: center;
  box-shadow: 0 6px 20px rgba(0,0,0,0.35);
}
.qris-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 10px;
  border-bottom: 1.5px solid #eee;
}
.qris-logo { display: flex; align-items: center; gap: 8px; text-align: left; }
.qris-tag {
  background: #E53935;
  color: #fff;
  font-weight: 900;
  padding: 3px 8px;
  border-radius: 6px;
  font-size: 14px;
  letter-spacing: 1px;
}
.qris-sub b { display: block; font-size: 12px; color: #111; }
.qris-sub small { font-size: 10px; color: #666; }
.qris-gpn {
  color: #E53935;
  font-weight: 900;
  font-size: 16px;
  font-style: italic;
}
.qris-store {
  font-size: 16px;
  font-weight: bold;
  color: #111;
  margin: 12px 0 4px;
}
.qris-nmid {
  font-size: 11px;
  color: #555;
  margin-bottom: 12px;
}
.qris-qr-wrap {
  background: #fff;
  padding: 6px;
  display: flex;
  justify-content: center;
}
.qris-img {
  width: 230px;
  height: 230px;
  object-fit: contain;
  display: block;
}
.qris-footer {
  font-size: 10px;
  color: #888;
  margin-top: 10px;
  padding-top: 8px;
  border-top: 1.5px solid #eee;
}
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <img src="https://cdn.phototourl.com/free/2026-09-21-45c1d5e9-96b7-48ae-9e8b-450445e4aa4e.jpg" alt="logo" class="logo">
  <span class="brand">FANZ joki <span class="ver">✓</span></span>
</div>

<!-- TICKER -->
<div class="ticker">
  <span class="badge">Beli</span>
  <marquee behavior="scroll" direction="left" scrollamount="5">JOKI VIEW • COSTUMER SERVICE • PRODUK DIGITAL • PROSES CEPAT • AMANAH • TERPERCAYA</marquee>
</div>

<!-- BANNER -->
<div class="banner-wrap">
  <img src="https://cdn.phototourl.com/free/2026-09-21-45c1d5e9-96b7-48ae-9e8b-450445e4aa4e.jpg" alt="banner" class="banner">
</div>

<!-- GRID MENU -->
<div class="grid-menu">
  <button type="button" class="menu-btn" data-show="joki">🕹️<br>Joki</button>
  <button type="button" class="menu-btn" data-show="cs">🎧<br>Costumer Service</button>
  <button type="button" class="menu-btn" data-show="digital">📦<br>Produk Digital</button>
  <a class="menu-btn" href="https://wa.me/6283866900499" target="_blank">💬<br>WA Joki</a>
  <a class="menu-btn" href="https://wa.me/6283866900499" target="_blank">🤝<br>WA FS</a>
  <a class="menu-btn" href="https://whatsapp.com/channel/0029VbCODVb3gvWY9NrE7r22" target="_blank">🔗<br>Link SL</a>
</div>

<!-- HOME -->
<div id="home">
  <div class="card">
    <h3>🕹️ JOKI</h3>
    <p>Jasa joki view, kontak, seller, buyer & lainnya. Proses cepat, amanah, terpercaya.</p>
    <button type="button" class="btn-lihat" data-show="joki">Lihat Daftar Layanan</button>
  </div>
  <div class="card">
    <h3>🎧 COSTUMER SERVICE</h3>
    <p>Butuh bantuan? Hubungi CS kami via WhatsApp untuk konsultasi, order, atau keluhan.</p>
    <button type="button" class="btn-lihat" data-show="cs">Hubungi CS</button>
  </div>
  <div class="card">
    <h3>📦 PRODUK DIGITAL</h3>
    <p>Murid suntik, murid web AI, jasa bikin web & layanan digital lainnya.</p>
    <button type="button" class="btn-lihat" data-show="digital">Lihat Daftar Layanan</button>
  </div>
</div>

<!-- LIST JOKI -->
<div id="list-joki" class="listPage">
  <button type="button" class="back" data-back>← Kembali</button>
  <h3>Daftar Layanan Joki</h3>
  <div id="joki"></div>
</div>

<!-- LIST COSTUMER SERVICE -->
<div id="list-cs" class="listPage">
  <button type="button" class="back" data-back>← Kembali</button>
  <h3>Costumer Service</h3>
  <div id="csWrap">
    <div class="cs-card">
      <div class="cs-avatar">🎧</div>
      <h3>FANZ Costumer Service</h3>
      <p>Siap membantu kamu 24 jam<br>Order • Konsultasi • Keluhan • Info Layanan</p>
      <a class="cs-wa-btn" href="https://wa.me/6283121532193" target="_blank">💬 Chat CS via WhatsApp</a>
      <div class="cs-info">
        <b>📱 WhatsApp:</b> 0831-2153-2193<br>
        <b>⏰ Jam Operasional:</b> 08.00 - 23.00 WIB<br>
        <b>⚡ Respon cepat & ramah</b>
      </div>
    </div>
  </div>
</div>

<!-- LIST DIGITAL -->
<div id="list-digital" class="listPage">
  <button type="button" class="back" data-back>← Kembali</button>
  <h3>Daftar Layanan Produk Digital</h3>
  <div id="digital"></div>
</div>

<!-- NAVBAR -->
<nav class="navbar">
  <button type="button" class="nav-item" data-show="joki">🕹️<br>Joki</button>
  <button type="button" class="nav-item" data-show="cs">🎧<br>CS</button>
  <button type="button" class="nav-item nav-home active" data-back>🏠<br>Home</button>
  <button type="button" class="nav-item" data-show="digital">📦<br>Digital</button>
  <a class="nav-item" href="https://wa.me/6283121532193" target="_blank">👤<br>Admin</a>
</nav>

<!-- OVERLAY ORDER -->
<div id="overlay">
  <div class="overlay-box">
    <div id="step1" class="step">
      <h4>Format Order</h4>
      <textarea id="format" rows="9"></textarea>
      <button type="button" class="btn-lanjut" id="btnLanjut">Lanjut ke Pembayaran</button>
      <button type="button" class="btn-tutup" data-close>Tutup</button>
    </div>

    <div id="step2" class="step">
      <h4>Pembayaran QRIS</h4>
      <div class="qris-card">
        <div class="qris-header">
          <div class="qris-logo">
            <span class="qris-tag">QRIS</span>
            <div class="qris-sub">
              <b>QR Code Standar</b>
              <small>Pembayaran Nasional</small>
            </div>
          </div>
          <div class="qris-gpn">GPN</div>
        </div>
        <div class="qris-store">arpan store</div>
        <div class="qris-nmid">NMID : ID1026520420450</div>
        <div class="qris-qr-wrap">
          <img src="https://cdn.phototourl.com/free/2026-09-21-8f9c8103-fe30-43fb-84a9-28d5995059d7.jpg" alt="QRIS" class="qris-img">
        </div>
        <div class="qris-footer">Dicetak oleh: 93600915</div>
      </div>
      <textarea id="finalFormat" rows="5" readonly></textarea>
      <div class="timer">⏳ <span id="timer">15:00</span></div>
      <a id="waConfirm" class="btn-wa" href="#" target="_blank">Konfirmasi via WhatsApp</a>
      <button type="button" class="btn-tutup" data-close>Tutup</button>
    </div>
  </div>
</div>

<script>
// ================= DATA =================
const dataJoki = [
  ["1 HARI", "Rp 1.000"],
  ["2 HARI", "Rp 2.000"],
  ["3 HARI", "Rp 3.000"],
  ["4 HARI", "Rp 4.000"],
  ["PERMANEN TEBAR SAMPE PENSI", "Rp 50.000"]
];

const dataDigital = [
  ["MURID SUNTIK", "Rp 5.000"],
  ["MURID WEB AI", "Rp 7.000"],
  ["MURID SUNTIK + WEB", "Rp 10.000"],
  ["MURID LOGO", "Rp 7.000"]
];

// ================= RENDER LIST =================
function buatList(id, arr, tipe) {
  let html = "";
  arr.forEach(a => {
    html += `<div class="item">
      <div><b>${a[0]}</b><div class="pr">${a[1]}</div></div>
      <button type="button" class="btn-order" data-paket="${a[0]}" data-harga="${a[1]}" data-tipe="${tipe}">ORDER</button>
    </div>`;
  });
  document.getElementById(id).innerHTML = html;
}

buatList('joki', dataJoki, 'joki');
buatList('digital', dataDigital, 'digital');

// ================= NAVIGASI =================
window.showList = (t) => {
  document.getElementById('home').style.display = 'none';
  document.querySelectorAll('.listPage').forEach(e => e.style.display = 'none');
  document.getElementById('list-' + t).style.display = 'block';
  window.scrollTo(0, 0);
};

window.showHome = () => {
  document.querySelectorAll('.listPage').forEach(e => e.style.display = 'none');
  document.getElementById('home').style.display = 'block';
  window.scrollTo(0, 0);
};

// ================= DELEGATION =================
document.addEventListener('click', function(e) {
  const showEl = e.target.closest('[data-show]');
  if (showEl) {
    e.preventDefault();
    window.showList(showEl.getAttribute('data-show'));
    return;
  }

  const backEl = e.target.closest('[data-back]');
  if (backEl) {
    e.preventDefault();
    window.showHome();
    return;
  }

  const orderEl = e.target.closest('.btn-order');
  if (orderEl) {
    e.preventDefault();
    const paket = orderEl.getAttribute('data-paket');
    const harga = orderEl.getAttribute('data-harga');
    const tipe = orderEl.getAttribute('data-tipe');
    let base = "";

    if (tipe === 'joki') {
      base = "SV BUYER FRESH FANZ🔥\n\nSV ; NAMA STORE\nWa.me/62..\n\n#NAMBAH VIEW SW + KONTAK + SELLER + BUYYER + DLL 🌤️🌈";
    } else if (tipe === 'digital') {
      base = "nama:\nlayanan digital:\n";
    }

    document.getElementById('format').value = base + "\n\nPaket: " + paket + " - " + harga;
    document.getElementById('overlay').style.display = 'flex';
    document.getElementById('step1').style.display = 'flex';
    document.getElementById('step2').style.display = 'none';
    return;
  }

  const closeEl = e.target.closest('[data-close]');
  if (closeEl) {
    e.preventDefault();
    document.getElementById('overlay').style.display = 'none';
    return;
  }
});

// ================= STEP 1 -> STEP 2 =================
document.getElementById('btnLanjut').addEventListener('click', function() {
  const formatVal = document.getElementById('format').value;
  document.getElementById('finalFormat').value = formatVal;

  const waText = encodeURIComponent(formatVal + "\n\nMohon konfirmasi pembayaran QRIS.");
  document.getElementById('waConfirm').href = "https://wa.me/6283121532193?text=" + waText;

  document.getElementById('step1').style.display = 'none';
  document.getElementById('step2').style.display = 'flex';

  let waktu = 15 * 60;
  const timerEl = document.getElementById('timer');
  if (window._timerInterval) clearInterval(window._timerInterval);
  window._timerInterval = setInterval(() => {
    const m = String(Math.floor(waktu / 60)).padStart(2, '0');
    const s = String(waktu % 60).padStart(2, '0');
    timerEl.textContent = m + ":" + s;
    if (waktu <= 0) {
      clearInterval(window._timerInterval);
      timerEl.textContent = "00:00";
    }
    waktu--;
  }, 1000);
});

document.getElementById('overlay').addEventListener('click', function(e) {
  if (e.target.id === 'overlay') {
    this.style.display = 'none';
  }
});
</script>
</body>
</html>
