<!DOCTYPE html>
<html>
<head>
<title>KIIN - Game Website</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" integrity="sha512-9usAa10IRO0HhonpyAIVpjrylPvoDwiPUiKdWk5t3PyolY1cOd4DSE0Ga+ri4AuTroPR5aQvXU9xC6qOPnzFeg==" crossorigin="anonymous" referrerpolicy="no-referrer" />
<style>
body {
  font-family: sans-serif;
  margin: 0;
  background-color: #228B22;
  overflow-x: hidden;
}

.container {
  display: flex;
  min-height: 100vh;
  margin: 0;
}

.sidebar {
  width: 130px;
  background-color: #8BC34A;
  padding: 20px;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  position: relative;
}

.sidebar button {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #fff;
  border: 1px solid #ccc;
  margin: 10px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.sidebar button i {
  font-size: 1.5em;
  color: #333;
}

.menu-options {
  display: none;
  flex-direction: column;
  position: absolute;
  left: 130px;
  top: 0;
  background-color: #8BC34A;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 2px 2px 5px rgba(0,0,0,0.3);
}

.menu-options.show {
  display: flex;
}

.menu-options button {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #fff;
  border: 1px solid #ccc;
  margin: 5px auto;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.menu-options button i {
  font-size: 1.5em;
  color: #333;
}

.main-content {
  flex: 1;
  padding: 0;
  box-sizing: border-box;
}

.header {
  background-color: #4CAF50;
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
}

.header-inner {
  display: flex;
  align-items: center;
  width: 100%;
  justify-content: space-between;
  margin-bottom: 20px;
}

.header-logo {
  margin-right: 20px;
}

.header img {
  max-width: 130px;
  height: auto;
}

.header-content {
  display: flex;
  align-items: center;
  width: 100%;
  position: relative; /* Untuk search results */
}

.header-content input[type="text"] {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: white;
  color: black;
  margin-right: 10px;
  flex-grow: 1;
  width: 100%;
}

.header-content button {
  padding: 5px 10px;
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  cursor: pointer;
  color: black;
  margin-left: 10px;
}

.header-content .profile-button {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: #fff;
  border: 1px solid #ccc;
  margin-left: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.header-content .profile-button i {
  font-size: 1.5em;
  color: #333;
}

.ad-banners {
  display: flex;
  overflow-x: auto;
  overflow-y: hidden;
  width: 100%;
  scroll-behavior: smooth;
}

.ad-banner {
  max-width: 300px;
  max-height: 200px;
  margin-right: 5px;
  flex-shrink: 0;
}

.ad-banner img {
  width: 100%;
  height: auto;
  max-width: 100%;
  min-width: 100%;
}

.game-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.game-card {
  width: 20%;
  margin-bottom: 10px;
  box-sizing: border-box;
  padding: 10px;
  cursor: pointer; /* Add cursor: pointer for better UX */
}

.game-card img {
  width: 100%;
  height: auto;
}

#search-results {
  position: absolute;
  top: calc(100% + 10px);
  left: 0;
  background-color: white;
  border: 1px solid #ccc;
  padding: 10px;
  display: none;
  z-index: 10;
}

#search-results ul {
  list-style: none;
  padding: 0;
}

#search-results li {
  padding: 5px;
  cursor: pointer;
}

#search-results li:hover {
  background-color: #f0f0f0;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
  }
  .sidebar {
    width: 100%;
  }
  .main-content {
    width: 100%;
  }
  .ad-banner {
    flex-basis: 100%;
    flex-grow: 0;
    margin-right: 0;
  }
  .game-cards {
    justify-content: center;
  }
  .game-card {
    width: 48%;
  }
  .header {
    grid-template-rows: auto auto;
    min-height: auto;
  }
  .header-inner {
    flex-direction: column;
    align-items: center;
  }
  .header-content {
    flex-direction: column;
    align-items: center;
    margin-top: 10px;
    width: 100%;
  }
  .header-content input[type="text"] {
    width: calc(100% - 20px);
    margin-bottom: 10px;
  }
  .header-content button {
    margin-left: 0;
    width: 100px;
  }
  .header-content .profile-button {
    margin-top: 10px;
  }
  .menu-options {
    left: 0;
    top: 40px;
  }
}
</style>
</head>
<body>
<div class="container">
  <div class="sidebar">
    <button id="menu-button"><i class="fas fa-bars"></i></button>
    <button id="home-button"><i class="fas fa-home"></i></button>
    <button id="game-button"><i class="fas fa-gamepad"></i></button>
    <div class="menu-options" id="menu-options">
      <button id="database-button"><i class="fas fa-database"></i></button>
      <button id="customer-service"><i class="fas fa-headset"></i></button>
    </div>
  </div>
  <div class="main-content">
    <div class="header">
      <div class="header-inner">
        <div class="header-logo">
          <img src="LOGO.png" alt="Logo">
        </div>
        <div class="header-content">
          <input type="text" id="search-input" placeholder="Search">
          <button id="login-button">Login</button>
          <button id="register-button">Daftar</button>
          <button id="profile-button" class="profile-button"><i class="fas fa-user"></i></button>
          <div id="search-results"></div>
        </div>
      </div>
      <div class="ad-banners">
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 1"></div>
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 2"></div>
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 1"></div>
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 2"></div>
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 3"></div>
        <div class="ad-banner"><img src="ml.jpeg" alt="Ad 3"></div>
      </div>
    </div>
    <div class="game-cards">
      <div class="game-card" id="dota-card-1"><img src="dota.jpeg" alt="Game 1"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-2"><img src="dota.jpeg" alt="Game 2"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-3"><img src="dota.jpeg" alt="Game 3"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-4"><img src="dota.jpeg" alt="Game 4"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-5"><img src="dota.jpeg" alt="Game 5"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-6"><img src="dota.jpeg" alt="Game 1"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-7"><img src="dota.jpeg" alt="Game 2"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-8"><img src="dota.jpeg" alt="Game 3"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-9"><img src="dota.jpeg" alt="Game 4"><p>DOTA 2</p></div>
      <div class="game-card" id="dota-card-10"><img src="dota.jpeg" alt="Game 5"><p>DOTA 2</p></div>
    </div>
  </div>
</div>

<script>
const menuButton = document.getElementById('menu-button');
const menuOptions = document.getElementById('menu-options');
const adBanners = document.querySelector('.ad-banners');
let scrollInterval;
let scrollAmount = 1;
let isScrolling = true;

// Data game (GANTI DENGAN DATA GAME SEBENARNYA!!!)
const gameData = [
  { name: "DOTA 2", image: "dota.jpeg" },
  { name: "Mobile Legends", image: "ml.jpeg" },
  { name: "PUBG Mobile", image: "pubg.jpg" }
];

const searchInput = document.getElementById('search-input');
const searchResults = document.getElementById('search-results');

searchInput.addEventListener('input', () => {
  const searchTerm = searchInput.value.toLowerCase();
  const results = gameData.filter(game => game.name.toLowerCase().includes(searchTerm));

  searchResults.innerHTML = '';
  if (results.length > 0) {
    const ul = document.createElement('ul');
    results.forEach(game => {
      const li = document.createElement('li');
      li.textContent = game.name;
      li.addEventListener('click', () => {
        alert(`Anda memilih game: ${game.name}`);
        searchResults.style.display = 'none';
      });
      ul.appendChild(li);
    });
    searchResults.appendChild(ul);
    searchResults.style.display = 'block';
  } else {
    searchResults.innerHTML = '<p>Search not found</p>';
    searchResults.style.display = 'block';
  }
});


function autoScroll() {
  if (isScrolling) {
    adBanners.scrollBy({left: scrollAmount, behavior: 'smooth'});
  }
}

function startAutoScroll() {
  scrollInterval = setInterval(autoScroll, 50);
}

function stopAutoScroll() {
  clearInterval(scrollInterval);
}

function handleAdBannerInteraction() {
  isScrolling = false;
}

function resumeAutoScroll() {
  isScrolling = true;
  startAutoScroll();
}


startAutoScroll();

adBanners.addEventListener('mouseover', stopAutoScroll);
adBanners.addEventListener('mouseout', resumeAutoScroll);
adBanners.addEventListener('mousedown', handleAdBannerInteraction);
adBanners.addEventListener('mouseup', resumeAutoScroll);
adBanners.addEventListener('touchstart', handleAdBannerInteraction);
adBanners.addEventListener('touchend', resumeAutoScroll);

menuButton.addEventListener('click', () => {
  menuOptions.classList.toggle('show');
});

document.getElementById('profile-button').addEventListener('click', () => {
  window.location.href = 'profil.html';
});

document.getElementById('register-button').addEventListener('click', () => {
  window.location.href = 'daftar.html';
});

document.getElementById('login-button').addEventListener('click', () => {
  window.location.href = 'login.html';
});

document.getElementById('database-button').addEventListener('click', () => {
  window.location.href = 'Database.html';
});

document.getElementById('customer-service').addEventListener('click', () => {
  let gameId = prompt("Masukkan ID Anda:");
  let gameName = prompt("Masukkan Nama Game:");
  let mailtoLink = `mailto:maulanakitarikarin@gmail.com?subject=Customer Service Request&body=ID: ${gameId}\nGame Name: ${gameName}\n`;
  window.location.href = mailtoLink;
});

document.getElementById('home-button').addEventListener('click', () => {
  // Do nothing
});

document.getElementById('game-button').addEventListener('click', () => {
  window.location.href = 'Game.html';
});

//Corrected DOTA 2 redirection - using IDs
const dotaCards = document.querySelectorAll('.game-card[id^="dota-card-"]');
dotaCards.forEach(card => {
  card.addEventListener('click', () => {
    window.location.href = 'index.html';
  });
});
</script>

</body>
</html>
