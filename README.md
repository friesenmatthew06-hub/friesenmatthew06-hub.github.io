
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Always & Forever ♡</title>

<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Playfair+Display:ital,wght@0,400;0,500;0,600;1,400&display=swap" rel="stylesheet">

<style>
:root {
  --cream: #fffaf5;
  --pink: #f4dce0;
  --rose: #c77b89;
  --dark: #633d47;
  --text: #654d50;
  --white: #ffffff;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: var(--cream);
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
  min-height: 100vh;
}

header {
  text-align: center;
  padding: 35px 15px 20px;
}

header h1 {
  font-family: 'Playfair Display', serif;
  font-size: 42px;
  color: var(--dark);
  font-weight: 400;
}

header p {
  margin-top: 8px;
  font-size: 13px;
  letter-spacing: 2px;
  color: var(--rose);
}

nav {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 12px;
  padding: 20px;
}

nav button {
  border: none;
  background: transparent;
  color: var(--text);
  padding: 12px 20px;
  cursor: pointer;
  font-family: inherit;
  border-radius: 30px;
  transition: .2s;
}

nav button:hover,
nav button.active {
  background: var(--pink);
  color: var(--dark);
}


.page {
  display: none;
  max-width: 750px;
  width: 100%;
  margin: 35px auto;
  padding: 20px;
  text-align: center;
  box-sizing: border-box;
}


.page.active {
  display: block;
  animation: appear .4s ease;
}

@keyframes appear {
  from {opacity: 0; transform: translateY(10px);}
  to {opacity: 1; transform: translateY(0);}
}

h2 {
  font-family: 'Playfair Display', serif;
  font-size: 36px;
  font-weight: 400;
  color: var(--dark);
  text-align: center;
  width: 100%;
  margin: 0 auto 20px;
  line-height: 1.3;
  text-decoration: none;
}

.subtitle {
  font-size: 14px;
  color: var(--rose);
  margin-bottom: 35px;
}

.heart {
  font-size: 32px;
  color: var(--rose);
  margin-bottom: 20px;
}

.reason-card {
  background: white;
  border: 1px solid #f1dfe1;
  border-radius: 18px;
  padding: 45px 25px;
  min-height: 170px;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 8px 30px #633d470a;
  margin-bottom: 25px;
}

.reason-card p {
  font-family: 'Playfair Display', serif;
  font-size: 25px;
  line-height: 1.6;
  color: var(--dark);
  font-style: italic;
}

.main-btn {
  background: var(--rose);
  color: white;
  border: none;
  border-radius: 30px;
  padding: 15px 30px;
  font-family: inherit;
  font-size: 14px;
  cursor: pointer;
  transition: .2s;
}

.main-btn:hover {
  background: var(--dark);
  transform: translateY(-2px);
}

.add-section {
  margin-top: 55px;
  background: #f9edef;
  padding: 25px;
  border-radius: 18px;
}

.add-section h3 {
  font-family: 'Playfair Display', serif;
  color: var(--dark);
  font-size: 22px;
  font-weight: 400;
  margin-bottom: 15px;
}

input, textarea {
  width: 100%;
  border: 1px solid #ead5d9;
  border-radius: 10px;
  padding: 14px;
  margin-bottom: 12px;
  background: white;
  font-family: inherit;
  font-size: 14px;
  color: var(--text);
  outline: none;
}

input:focus, textarea:focus {
  border-color: var(--rose);
}

textarea {
  resize: vertical;
  min-height: 85px;
}

.saved-list {
  margin-top: 30px;
  text-align: left;
}

.saved-list h3 {
  font-family: 'Playfair Display', serif;
  font-weight: 400;
  margin-bottom: 15px;
  color: var(--dark);
}

.list-item {
  background: white;
  padding: 16px;
  margin-bottom: 10px;
  border: 1px solid #f1dfe1;
  border-radius: 12px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 12px;
}

.list-item span {
  line-height: 1.5;
  overflow-wrap: anywhere;
}

.delete-btn {
  border: none;
  background: transparent;
  color: #bd7d89;
  cursor: pointer;
  font-size: 18px;
  padding: 5px;
}

.tabs {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 25px;
}

.tabs button {
  padding: 12px 22px;
  border: 1px solid #e9cdd2;
  background: white;
  border-radius: 30px;
  color: var(--text);
  cursor: pointer;
  font-family: inherit;
}

.tabs button.active {
  background: var(--rose);
  color: white;
}

.completed {
  opacity: .55;
  text-decoration: line-through;
}

.check {
  accent-color: var(--rose);
  cursor: pointer;
  width: 17px;
  height: 17px;
  flex-shrink: 0;
}

footer {
  text-align: center;
  padding: 50px 15px 25px;
  color: var(--rose);
  font-family: 'Playfair Display', serif;
  font-style: italic;
}

@media(max-width: 500px) {
  header h1 {font-size: 34px;}
  nav {gap: 3px;}
  nav button {padding: 10px 12px; font-size: 12px;}
  .page {margin-top: 15px;}
  .reason-card p {font-size: 21px;}
}


/* WALKING COW */

.walking-cow {
  position: fixed;
  bottom: 8px;
  left: -70px;
  font-size: 48px;
  z-index: 9999;
  pointer-events: none;
  animation: cowWalk 35s linear infinite,
             cowBounce 0.5s ease-in-out infinite alternate;
}

@keyframes cowWalk {
  0% {
    left: -70px;
    transform: scaleX(1);
  }

  49% {
    left: calc(100vw - 60px);
    transform: scaleX(1);
  }

  50% {
    left: calc(100vw - 60px);
    transform: scaleX(-1);
  }

  99% {
    left: -70px;
    transform: scaleX(-1);
  }

  100% {
    left: -70px;
    transform: scaleX(1);
  }
}

@keyframes cowBounce {
  from {
    margin-bottom: 0;
  }

  to {
    margin-bottom: 5px;
  }
}

</style>
</head>

<body>

<header>
  <h1>♡ Always & Forever ♡</h1>
  <p>OUR PLACE FOR OUR LOVE</p>
</header>

<nav>
  <button class="active" onclick="showPage('reasons',this)">Reasons ♡</button>
  <button onclick="showPage('memories',this)">Memories ♡</button>
  <button onclick="showPage('bucket',this)">Bucket List ♡</button>
</nav>

<!-- PAGE 1: REASONS -->

<section id="reasons" class="page active">
  <div class="heart">♡</div>
  <h2>Reasons I Love You</h2>
  <p class="subtitle">A million reasons I love you.</p>

  <div class="reason-card">
    <p id="reasonDisplay">Every little thing about you makes my world better.</p>
  </div>

  <button class="main-btn" onclick="randomItem('reasons','reasonDisplay')">
    Give Me A Reason ♡
  </button>

  <div class="add-section">
    <h3>Add Another Reason</h3>
    <textarea id="reasonInput" placeholder="I love you because..."></textarea>
    <button class="main-btn" onclick="addItem('reasons','reasonInput')">
      Save Reason +
    </button>
  </div>

  <div class="saved-list">
    <h3>Our List of Reasons</h3>
    <div id="reasonsList"></div>
  </div>
</section>

<!-- PAGE 2: MEMORIES -->

<section id="memories" class="page">
  <div class="heart">♡</div>
  <h2>Our Memories</h2>
  <p class="subtitle">The moments that will last a lifetime.</p>

  <div class="reason-card">
    <p id="memoryDisplay">The first day I saw you at robotics.</p>
  </div>

  <button class="main-btn" onclick="randomItem('memories','memoryDisplay')">
    Remind Me Of A Memory ♡
  </button>

  <div class="add-section">
    <h3>Add A Memory</h3>
    <textarea id="memoryInput" placeholder="Remember when we..."></textarea>
    <button class="main-btn" onclick="addItem('memories','memoryInput')">
      Save Memory +
    </button>
  </div>

  <div class="saved-list">
    <h3>Our Memory Collection</h3>
    <div id="memoriesList"></div>
  </div>
</section>

<!-- PAGE 3: BUCKET LIST -->

<section id="bucket" class="page">
  <div class="heart">♡</div>
  <h2>Our Bucket Lists</h2>
  <p class="subtitle">All the things we WILL do.</p>

  <div class="tabs">
    <button class="active" onclick="setBucket('normal',this)">
      Normal ♡
    </button>
    <button onclick="setBucket('freaky',this)">
      Freaky ♡
    </button>
  </div>

  <div class="add-section" style="margin-top:0">
    <h3 id="bucketTitle">Our Adventures</h3>
    <input id="bucketInput" placeholder="Something we should do together...">
    <button class="main-btn" onclick="addBucketItem()">
      Add To Bucket List +
    </button>
  </div>

  <div class="saved-list">
    <h3>Things We Want To Do</h3>
    <div id="bucketList"></div>
  </div>
</section>

<div class="walking-cow">🐄</div>
<footer>
  Made by Door for the most amazing girl in the whole world. ♡
  <br><br>
  I will love you, Always & Forever.
</footer>

<script>

// PREMADE REASONS - ADD YOUR OWN HERE!

const defaultReasons = [
  "Your smile makes even my worst days better.",
  "You make me feel like the luckiest person alive.",
  "I love the way you laugh.",
  "You make ordinary moments feel special.",
  "I love spending time with you.",
  "You make me feel appreciated.",
  "I love how you always make me smile.",
  "You're my favorite person to talk to.",
  "I love your personality.",
  "You make everything more fun.",
  "I love the way you look at me.",
  "You make me want to be a better person.",
  "I love all the little things you do.",
  "You're beautiful inside and out.",
  "I wouldn't trade our moments for anything."
];

// PREMADE MEMORIES - CUSTOMIZE THESE!

const defaultMemories = [
  "The first time we met.",
  "One of our favorite dates together.",
  "The first time we said I love you.",
  "All of our late night conversations.",
  "The times we couldn't stop laughing.",
  "Every little adventure we've had."
];

// SAVE AND LOAD DATA

function loadData(key, defaults) {
  const saved = localStorage.getItem(key);
  return saved ? JSON.parse(saved) : defaults;
}

let reasons = loadData('af_reasons', defaultReasons);
let memories = loadData('af_memories', defaultMemories);
let normalBucket = loadData('af_normal', []);
let freakyBucket = loadData('af_freaky', []);

let currentBucket = 'normal';

function saveData(key, data) {
  localStorage.setItem(key, JSON.stringify(data));
}

// NAVIGATION

function showPage(page, button) {
  document.querySelectorAll('.page').forEach(p =>
    p.classList.remove('active')
  );

  document.getElementById(page).classList.add('active');

  document.querySelectorAll('nav button').forEach(b =>
    b.classList.remove('active')
  );

  button.classList.add('active');
}

// RANDOM GENERATOR

function randomItem(type, displayId) {
  const list = type === 'reasons' ? reasons : memories;

  if (!list.length) {
    document.getElementById(displayId).textContent =
      "Add something to your collection first! ♡";
    return;
  }

  let item;

  if (list.length > 1) {
    const previous = document.getElementById(displayId).dataset.last;
    const choices = list.filter(x => x !== previous);
    item = choices[Math.floor(Math.random() * choices.length)];
  } else {
    item = list[0];
  }

  const display = document.getElementById(displayId);
  display.textContent = item;
  display.dataset.last = item;
}

// ADD REASONS AND MEMORIES

function addItem(type, inputId) {
  const input = document.getElementById(inputId);
  const value = input.value.trim();

  if (!value) return;

  if (type === 'reasons') {
    reasons.push(value);
    saveData('af_reasons', reasons);
    renderList('reasons');
  } else {
    memories.push(value);
    saveData('af_memories', memories);
    renderList('memories');
  }

  input.value = '';
}

// RENDER REASONS AND MEMORIES

function renderList(type) {
  const list = type === 'reasons' ? reasons : memories;
  const container = document.getElementById(type + 'List');

  container.replaceChildren();

  list.forEach((item, index) => {
    const row = document.createElement('div');
    row.className = 'list-item';

    const text = document.createElement('span');
    text.textContent = item;

    const del = document.createElement('button');
    del.className = 'delete-btn';
    del.textContent = '×';
    del.setAttribute('aria-label', 'Delete item');

    del.onclick = () => {
      list.splice(index, 1);
      saveData(type === 'reasons' ? 'af_reasons' : 'af_memories', list);
      renderList(type);
    };

    row.append(text, del);
    container.appendChild(row);
  });
}

// BUCKET LISTS

function setBucket(type, button) {
  currentBucket = type;

  document.querySelectorAll('.tabs button').forEach(b =>
    b.classList.remove('active')
  );

  button.classList.add('active');

  document.getElementById('bucketTitle').textContent =
    type === 'normal' ? 'Our Adventures' : 'Our Secret List';

  renderBucket();
}

function addBucketItem() {
  const input = document.getElementById('bucketInput');
  const value = input.value.trim();

  if (!value) return;

  const list = currentBucket === 'normal'
    ? normalBucket : freakyBucket;

  list.push({
    text: value,
    done: false
  });

  saveData(
    currentBucket === 'normal' ? 'af_normal' : 'af_freaky',
    list
  );

  input.value = '';
  renderBucket();
}

function renderBucket() {
  const list = currentBucket === 'normal'
    ? normalBucket : freakyBucket;

  const container = document.getElementById('bucketList');
  container.replaceChildren();

  list.forEach((item, index) => {
    const row = document.createElement('div');
    row.className = 'list-item';

    const check = document.createElement('input');
    check.type = 'checkbox';
    check.className = 'check';
    check.checked = item.done;

    const text = document.createElement('span');
    text.textContent = item.text;

    if (item.done) text.className = 'completed';

    check.onchange = () => {
      item.done = check.checked;
      saveBucket();
      renderBucket();
    };

    const del = document.createElement('button');
    del.className = 'delete-btn';
    del.textContent = '×';
    del.setAttribute('aria-label', 'Delete item');

    del.onclick = () => {
      list.splice(index, 1);
      saveBucket();
      renderBucket();
    };

    row.append(check, text, del);
    container.appendChild(row);
  });
}

function saveBucket() {
  saveData(
    currentBucket === 'normal' ? 'af_normal' : 'af_freaky',
    currentBucket === 'normal' ? normalBucket : freakyBucket
  );
}

// INITIALIZE

renderList('reasons');
renderList('memories');
renderBucket();

</script>

</body>
</html>
