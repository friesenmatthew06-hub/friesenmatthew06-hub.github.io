
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Always&Forever ♡</title>
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
  <style>
    :root {
      --pink: #e9a8b8;
      --dark-pink: #c96f89;
      --light-pink: #fff0f3;
      --cream: #fffaf2;
      --brown: #674b4b;
      --white: #ffffff;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      font-family: Georgia, "Times New Roman", serif;
      background: var(--cream);
      color: var(--brown);
      text-align: center;
    }

    button, input { font: inherit; }

    button {
      border: none;
      border-radius: 22px;
      padding: 11px 19px;
      background: var(--pink);
      color: white;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      background: var(--dark-pink);
      transform: translateY(-1px);
    }

    button:disabled {
      opacity: 0.6;
      cursor: wait;
      transform: none;
    }

    .login-screen {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 24px;
      background: linear-gradient(135deg, #fff0f3, #fffaf2);
    }

    .login-card {
      width: 100%;
      max-width: 420px;
      background: white;
      padding: 38px 28px;
      border-radius: 25px;
      box-shadow: 0 8px 30px #d9aab344;
    }

    .login-card h1 {
      color: var(--dark-pink);
      font-size: 36px;
      margin: 0 0 10px;
    }

    .login-card p { line-height: 1.6; }

    .login-card input {
      display: block;
      width: 100%;
      padding: 13px;
      margin: 12px 0;
      border: 1px solid #edcbd4;
      border-radius: 12px;
      background: #fffafc;
      color: var(--brown);
    }

    .login-card button { width: 100%; margin-top: 10px; }

    #login-message, #status-message {
      min-height: 22px;
      color: var(--dark-pink);
      font-size: 14px;
    }

    .app-shell { display: none; }
    body.logged-in .app-shell { display: block; }

    header {
      padding: 35px 18px 20px;
      background: var(--light-pink);
    }

    header h1 {
      font-size: clamp(35px, 7vw, 55px);
      color: var(--dark-pink);
      margin: 0;
    }

    header p { margin-bottom: 0; }

    .top-bar {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      padding: 12px;
      background: #fff7f5;
    }

    .top-bar span { font-size: 13px; }

    nav {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 10px;
      padding: 18px 12px;
    }

    nav button { background: #e7b4c0; }

    .page {
      display: none;
      max-width: 850px;
      margin: 0 auto;
      padding: 25px 20px 65px;
      min-height: 55vh;
    }

    .page.active { display: block; }

    h2 {
      color: var(--dark-pink);
      font-size: 32px;
      margin-bottom: 12px;
    }

    .intro { line-height: 1.6; }

    .generator {
      background: white;
      padding: 24px;
      margin: 25px auto;
      border-radius: 20px;
      box-shadow: 0 4px 15px #d9aab322;
    }

    .generated-text {
      min-height: 35px;
      font-size: 20px;
      line-height: 1.5;
      margin: 18px 0;
    }

    .add-row {
      display: flex;
      justify-content: center;
      gap: 8px;
      flex-wrap: wrap;
      margin: 20px auto;
    }

    .add-row input {
      flex: 1;
      min-width: 190px;
      max-width: 480px;
      padding: 12px;
      border: 1px solid #e8c5ce;
      border-radius: 20px;
      background: white;
      color: var(--brown);
    }

    .item-list {
      list-style: none;
      padding: 0;
      margin: 20px auto;
      max-width: 650px;
      text-align: left;
    }

    .item {
      display: flex;
      align-items: center;
      gap: 12px;
      background: white;
      padding: 14px 16px;
      margin: 10px 0;
      border-radius: 15px;
      box-shadow: 0 2px 8px #d9aab322;
      overflow-wrap: anywhere;
    }

    .item-content {
      flex: 1;
      line-height: 1.5;
    }

    .item.completed .item-content {
      text-decoration: line-through;
      opacity: 0.55;
    }

    .item input[type="checkbox"] {
      accent-color: var(--dark-pink);
      width: 18px;
      height: 18px;
      flex-shrink: 0;
    }

    .delete-button {
      background: #f1c4ce;
      padding: 7px 12px;
      flex-shrink: 0;
    }

    .empty-message {
      opacity: 0.7;
      padding: 20px;
    }

    .bucket-section {
      margin: 35px 0;
      padding: 20px;
      border-radius: 20px;
      background: #fff3f5;
    }

    .bucket-section h3 {
      color: var(--dark-pink);
      font-size: 24px;
    }

    footer {
      padding: 35px 15px 65px;
      background: var(--light-pink);
      margin-top: 30px;
    }

    .walking-cow {
      position: fixed;
      bottom: 8px;
      left: -60px;
      font-size: 35px;
      z-index: 5;
      animation: walk 18s linear infinite;
      pointer-events: none;
    }

    @keyframes walk {
      from { left: -60px; }
      to { left: calc(100% + 60px); }
    }

    @media (max-width: 500px) {
      .item { padding: 12px; }
      .delete-button { padding: 7px 10px; }
      .page { padding-left: 14px; padding-right: 14px; }
    }
  </style>
</head>

<body>
  <!-- Sign-in screen -->
  <section class="login-screen" id="login-screen">
    <div class="login-card">
      <h1>Always&Forever ♡</h1>
      <p>A little place for our memories, reasons, and dreams.</p>

      <form id="login-form">
        <input
          id="email"
          type="email"
          placeholder="Email address"
          autocomplete="username"
          required
        >
        <input
          id="password"
          type="password"
          placeholder="Password"
          autocomplete="current-password"
          required
        >
        <button id="login-button" type="submit">Sign in ♡</button>
      </form>

      <p id="login-message" aria-live="polite"></p>
    </div>
  </section>

  <!-- Main website -->
  <div class="app-shell" id="app-shell">
    <header>
      <h1>Always&Forever ♡</h1>
      <p>Our little corner of the world</p>
    </header>

    <div class="top-bar">
      <span id="signed-in-as"></span>
      <button id="logout-button">Log out</button>
    </div>

    <nav>
      <button data-page="reasons">Reasons I Love You ♡</button>
      <button data-page="memories">Our Memories 📸</button>
      <button data-page="bucket">Our Bucket Lists ✨</button>
    </nav>

    <main>
      <!-- Reasons page -->
      <section class="page active" id="reasons">
        <h2>Reasons I Love You ♡</h2>
        <p class="intro">A million little reasons, and still not enough.</p>

        <div class="generator">
          <h3>A random reason</h3>
          <p class="generated-text" id="random-reason">
            Click below for a little reminder ♡
          </p>
          <button id="random-reason-button">Give me a reason</button>
        </div>

        <h3>Add your own reason</h3>
        <form class="add-row" id="reason-form">
          <input id="reason-input" maxlength="500"
            placeholder="Something you love..." required>
          <button type="submit">Add ♡</button>
        </form>

        <ul class="item-list" id="reasons-list"></ul>
      </section>

      <!-- Memories page -->
      <section class="page" id="memories">
        <h2>Our Memories 📸</h2>
        <p class="intro">Little moments that mean everything.</p>

        <div class="generator">
          <h3>Memory jar</h3>
          <p class="generated-text" id="random-memory">
            Pick a memory to look back on ♡
          </p>
          <button id="random-memory-button">Pick a memory</button>
        </div>

        <h3>Add a memory</h3>
        <form class="add-row" id="memory-form">
          <input id="memory-input" maxlength="500"
            placeholder="A moment we'll remember..." required>
          <button type="submit">Save memory ♡</button>
        </form>

        <ul class="item-list" id="memories-list"></ul>
      </section>

      <!-- Bucket list page -->
      <section class="page" id="bucket">
        <h2>Our Bucket Lists ✨</h2>
        <p class="intro">All the little and big things we want to do together.</p>

        <div class="bucket-section">
          <h3>Normal Bucket List 🌷</h3>
          <form class="add-row" id="normal-form">
            <input id="normal-input" maxlength="500"
              placeholder="Something we want to do..." required>
            <button type="submit">Add</button>
          </form>
          <ul class="item-list" id="normal-list"></ul>
        </div>

        <div class="bucket-section">
          <h3>Freaky Bucket List 👀</h3>
          <p>For silly, surprising, and adventurous ideas.</p>
          <form class="add-row" id="freaky-form">
            <input id="freaky-input" maxlength="500"
              placeholder="Add a playful idea..." required>
            <button type="submit">Add</button>
          </form>
          <ul class="item-list" id="freaky-list"></ul>
        </div>
      </section>
    </main>

    <p id="status-message" aria-live="polite"></p>

    <footer>
      <p>Made with love, for us ♡</p>
      <p>Always&Forever</p>
    </footer>
  </div>

  <div class="walking-cow" aria-hidden="true">🐄</div>

  <script>
    // 1. SUPABASE CONNECTION
    // This is the project URL based on your project reference.
    // If Supabase shows a different Project URL under Settings > API,
    // replace this value with the one shown there.
    const SUPABASE_URL = "https://rczjkpufhbpthtvwboez.supabase.co";

    // Your publishable key goes here.
    const SUPABASE_PUBLISHABLE_KEY =
      "sb_publishable_bIc_IcIySeM2sMYGw56Nlw_U01sEsNh";

    const db = window.supabase.createClient(
      SUPABASE_URL,
      SUPABASE_PUBLISHABLE_KEY
    );

    // 2. DEFAULT REASONS AND MEMORIES
    // These are added only if their category is empty in the database.
    const defaultReasons = [
      "You make ordinary days feel special.",
      "You always make me smile.",
      "I love how we can laugh together.",
      "You make me feel appreciated.",
      "I love making memories with you."
    ];

    const defaultMemories = [
      "The first time we really talked.",
      "One of our funniest conversations.",
      "A day I wish I could relive.",
      "A little moment that made me happy."
    ];

    let currentUser = null;
    let allItems = [];
    let realtimeChannel = null;
    let refreshTimer = null;

    const $ = (id) => document.getElementById(id);

    function setLoginMessage(message) {
      $("login-message").textContent = message;
    }

    function setStatus(message) {
      $("status-message").textContent = message;
    }

    function showApp(user) {
      currentUser = user;
      document.body.classList.add("logged-in");
      $("login-screen").style.display = "none";
      $("signed-in-as").textContent = "Signed in as " + user.email;
      setLoginMessage("");
    }

    function showLogin() {
      currentUser = null;
      document.body.classList.remove("logged-in");
      $("login-screen").style.display = "flex";
      allItems = [];

      if (realtimeChannel) {
        db.removeChannel(realtimeChannel);
        realtimeChannel = null;
      }
    }

    // 3. SIGN IN AND SIGN OUT
    $("login-form").addEventListener("submit", async (event) => {
      event.preventDefault();

      const button = $("login-button");
      button.disabled = true;
      setLoginMessage("Signing in...");

      const email = $("email").value.trim();
      const password = $("password").value;

      const { data, error } = await db.auth.signInWithPassword({
        email,
        password
      });

      button.disabled = false;

      if (error) {
        setLoginMessage(error.message);
        return;
      }

      showApp(data.user);
      await startSharedWebsite();
    });

    $("logout-button").addEventListener("click", async () => {
      if (realtimeChannel) {
        await db.removeChannel(realtimeChannel);
        realtimeChannel = null;
      }

      const { error } = await db.auth.signOut();

      if (error) {
        setStatus("Couldn't log out: " + error.message);
        return;
      }

      showLogin();
      setStatus("");
    });

    // 4. LOAD SHARED DATA
    async function loadItems() {
      if (!currentUser) return;

      const { data, error } = await db
        .from("shared_items")
        .select("*")
        .order("created_at", { ascending: true });

      if (error) {
        setStatus("Couldn't load shared items: " + error.message);
        return;
      }

      allItems = data || [];
      renderAll();
      setStatus("Your shared website is up to date ♡");
    }

    // Add starter content only when a category has no items.
    async function addDefaultsIfEmpty() {
      const categories = [
        { name: "reasons", values: defaultReasons },
        { name: "memories", values: defaultMemories }
      ];

      for (const category of categories) {
        const existing = allItems.filter(
          item => item.category === category.name
        );

        if (existing.length === 0) {
          const rows = category.values.map(content => ({
            category: category.name,
            content,
            completed: false,
            created_by: currentUser.id
          }));

          const { error } = await db
            .from("shared_items")
            .insert(rows);

          if (error) {
            setStatus("Couldn't add starter items: " + error.message);
            return;
          }
        }
      }

      await loadItems();
    }

    // 5. ADD, UPDATE, AND DELETE ITEMS
    async function addItem(category, content) {
      if (!currentUser) return;

      const cleanContent = content.trim();
      if (!cleanContent) return;

      const { error } = await db
        .from("shared_items")
        .insert({
          category,
          content: cleanContent,
          completed: false,
          created_by: currentUser.id
        });

      if (error) {
        setStatus("Couldn't save that item: " + error.message);
        return;
      }

      setStatus("Saved ♡");
      await loadItems();
    }

    async function updateItem(id, completed) {
      const { error } = await db
        .from("shared_items")
        .update({ completed })
        .eq("id", id);

      if (error) {
        setStatus("Couldn't update that item: " + error.message);
        return;
      }

      await loadItems();
    }

    async function deleteItem(id) {
      if (!confirm("Are you sure you want to delete this item?")) return;

      const { error } = await db
        .from("shared_items")
        .delete()
        .eq("id", id);

      if (error) {
        setStatus("Couldn't delete that item: " + error.message);
        return;
      }

      setStatus("Item deleted.");
      await loadItems();
    }

    // 6. DISPLAY ITEMS
    function renderList(category, listId, showCheckbox) {
      const list = $(listId);
      list.innerHTML = "";

      const items = allItems.filter(item => item.category === category);

      if (items.length === 0) {
        const empty = document.createElement("li");
        empty.className = "empty-message";
        empty.textContent = "Nothing here yet. Add something ♡";
        list.appendChild(empty);
        return;
      }

      items.forEach(item => {
        const li = document.createElement("li");
        li.className = "item" + (item.completed ? " completed" : "");

        if (showCheckbox) {
          const checkbox = document.createElement("input");
          checkbox.type = "checkbox";
          checkbox.checked = item.completed;
          checkbox.setAttribute("aria-label", "Mark item complete");

          checkbox.addEventListener("change", () => {
            updateItem(item.id, checkbox.checked);
          });

          li.appendChild(checkbox);
        }

        const content = document.createElement("span");
        content.className = "item-content";
        content.textContent = item.content;
        li.appendChild(content);

        const deleteButton = document.createElement("button");
        deleteButton.className = "delete-button";
        deleteButton.textContent = "Delete";
        deleteButton.addEventListener("click", () => deleteItem(item.id));
        li.appendChild(deleteButton);

        list.appendChild(li);
      });
    }

    function renderAll() {
      renderList("reasons", "reasons-list", false);
      renderList("memories", "memories-list", false);
      renderList("normal", "normal-list", true);
      renderList("freaky", "freaky-list", true);
    }

    // 7. FORM HANDLERS
    function connectForm(formId, inputId, category) {
      $(formId).addEventListener("submit", async (event) => {
        event.preventDefault();

        const input = $(inputId);
        const content = input.value;

        await addItem(category, content);
        input.value = "";
      });
    }

    connectForm("reason-form", "reason-input", "reasons");
    connectForm("memory-form", "memory-input", "memories");
    connectForm("normal-form", "normal-input", "normal");
    connectForm("freaky-form", "freaky-input", "freaky");

    // 8. RANDOM GENERATORS
    function pickRandom(category, outputId, emptyMessage) {
      const items = allItems.filter(item => item.category === category);

      if (items.length === 0) {
        $(outputId).textContent = emptyMessage;
        return;
      }

      const choice = items[Math.floor(Math.random() * items.length)];
      $(outputId).textContent = choice.content;
    }

    $("random-reason-button").addEventListener("click", () => {
      pickRandom("reasons", "random-reason", "Add a reason first ♡");
    });

    $("random-memory-button").addEventListener("click", () => {
      pickRandom("memories", "random-memory", "Add a memory first ♡");
    });

    // 9. NAVIGATION
    document.querySelectorAll("nav button[data-page]").forEach(button => {
      button.addEventListener("click", () => {
        document.querySelectorAll(".page").forEach(page => {
          page.classList.remove("active");
        });

        $(button.dataset.page).classList.add("active");
      });
    });

    // 10. LIVE SHARED UPDATES
    function subscribeToChanges() {
      if (realtimeChannel) {
        db.removeChannel(realtimeChannel);
      }

      realtimeChannel = db
        .channel("shared-items-live")
        .on(
          "postgres_changes",
          {
            event: "*",
            schema: "public",
            table: "shared_items"
          },
          () => {
            // Small delay lets the database finish the change first.
            clearTimeout(refreshTimer);
            refreshTimer = setTimeout(loadItems, 300);
          }
        )
        .subscribe();
    }

    // 11. START THE WEBSITE AFTER SIGN-IN
    async function startSharedWebsite() {
      await loadItems();

      if (allItems.length >= 0) {
        await addDefaultsIfEmpty();
      }

      subscribeToChanges();
    }

    // 12. CHECK WHETHER A USER IS ALREADY SIGNED IN
    async function checkExistingSession() {
      const { data, error } = await db.auth.getSession();

      if (error) {
        setLoginMessage(error.message);
        return;
      }

      if (data.session) {
        showApp(data.session.user);
        await startSharedWebsite();
      } else {
        showLogin();
      }
    }

    db.auth.onAuthStateChange((event, session) => {
      if (event === "SIGNED_OUT" || !session) {
        showLogin();
      }
    });

    checkExistingSession();
  </script>
</body>
</html>
