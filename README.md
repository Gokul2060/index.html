index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Harbor – Simple Website with Login and Enquiry</title>
<style>
  :root {
    --bg: #f3f6f8;
    --surface: #ffffff;
    --ink: #14232e;
    --muted: #5b6b77;
    --line: #d7e0e6;
    --accent: #0b6e8a;
    --accent-ink: #ffffff;
    --danger: #b3261e;
    --success: #1c6b3a;
  }
  @media (prefers-color-scheme: dark) {
    :root {
      --bg: #0f1b23;
      --surface: #16262f;
      --ink: #e8f0f5;
      --muted: #9db0bc;
      --line: #27404d;
      --accent: #4cb8d6;
      --accent-ink: #072029;
      --danger: #ff8a80;
      --success: #7bd39a;
    }
  }
  * { box-sizing: border-box; }
  html, body { margin: 0; }
  body {
    font-family: "Trebuchet MS", "Segoe UI", system-ui, sans-serif;
    background: var(--bg);
    color: var(--ink);
    line-height: 1.6;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
  }
  a { color: var(--accent); }
  :focus-visible { outline: 3px solid var(--accent); outline-offset: 2px; }

  header { background: var(--surface); border-bottom: 1px solid var(--line); }
  .bar {
    max-width: 960px; margin: 0 auto; padding: 14px 20px;
    display: flex; align-items: center; justify-content: space-between; gap: 16px;
  }
  .brand {
    font-family: Georgia, "Times New Roman", serif;
    font-size: 1.5rem; font-weight: 700; color: var(--ink);
    text-decoration: none; letter-spacing: 0.01em;
  }
  nav { display: flex; gap: 8px; align-items: center; flex-wrap: wrap; }
  nav a, nav button {
    font: inherit; color: var(--ink); background: none; border: 0;
    padding: 8px 12px; border-radius: 6px; text-decoration: none; cursor: pointer;
  }
  nav a:hover, nav button:hover { background: var(--bg); }
  nav a.primary { background: var(--accent); color: var(--accent-ink); }
  nav a.primary:hover { filter: brightness(1.08); }

  main { flex: 1; }
  .wrap { max-width: 960px; margin: 0 auto; padding: 48px 20px; }
  .view[hidden] { display: none; }

  .hero h1 {
    font-family: Georgia, "Times New Roman", serif;
    font-size: clamp(2rem, 5vw, 3.2rem); line-height: 1.15;
    margin: 0 0 16px; max-width: 18ch;
  }
  .hero p { color: var(--muted); font-size: 1.1rem; max-width: 52ch; margin: 0 0 28px; }
  .btn {
    display: inline-block; font: inherit; font-weight: 600;
    background: var(--accent); color: var(--accent-ink);
    border: 0; border-radius: 8px; padding: 12px 22px;
    cursor: pointer; text-decoration: none;
  }
  .btn:hover { filter: brightness(1.08); }
  .btn:disabled { opacity: .6; cursor: wait; }
  .btn.block { width: 100%; }
  .btn.ghost {
    background: transparent; color: var(--accent);
    border: 1px solid var(--accent); margin-left: 8px;
  }
  .features {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 20px; margin-top: 56px;
  }
  .feature { border-top: 3px solid var(--accent); padding-top: 12px; }
  .feature h3 { margin: 0 0 6px; font-size: 1.05rem; }
  .feature p { margin: 0; color: var(--muted); }

  .card {
    max-width: 440px; margin: 0 auto; background: var(--surface);
    border: 1px solid var(--line); border-radius: 12px; padding: 32px 28px;
  }
  .card h2 {
    font-family: Georgia, "Times New Roman", serif; margin: 0 0 4px; font-size: 1.7rem;
  }
  .card .sub { color: var(--muted); margin: 0 0 22px; }
  label { display: block; font-weight: 600; margin: 16px 0 6px; font-size: 0.95rem; }
  input[type="email"], input[type="password"], input[type="text"], textarea {
    width: 100%; font: inherit; color: var(--ink); background: var(--bg);
    border: 1px solid var(--line); border-radius: 8px; padding: 11px 12px;
  }
  textarea { min-height: 130px; resize: vertical; }
  .pw-row { position: relative; }
  .pw-row input { padding-right: 70px; }
  .pw-toggle {
    position: absolute; right: 6px; top: 50%; transform: translateY(-50%);
    font: inherit; font-size: 0.85rem; color: var(--accent);
    background: none; border: 0; padding: 6px 8px; cursor: pointer;
  }
  .row { display: flex; justify-content: space-between; align-items: center; margin: 14px 0 22px; font-size: 0.92rem; }
  .row label { display: flex; align-items: center; gap: 8px; margin: 0; font-weight: 400; }
  .msg { font-size: 0.92rem; min-height: 1.4em; margin: 12px 0 0; }
  .msg.error { color: var(--danger); }
  .msg.ok { color: var(--success); }
  .hint {
    margin-top: 20px; padding: 12px; border: 1px dashed var(--line);
    border-radius: 8px; font-size: 0.88rem; color: var(--muted);
  }
  .hint code { color: var(--ink); }
  .hp { position: absolute; left: -9999px; opacity: 0; height: 0; width: 0; }

  .welcome h2 { font-family: Georgia, "Times New Roman", serif; font-size: 2rem; margin: 0 0 6px; }
  .welcome p { color: var(--muted); margin: 0 0 32px; }
  .stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; }
  .stat { background: var(--surface); border: 1px solid var(--line); border-radius: 10px; padding: 18px; }
  .stat b { display: block; font-size: 1.8rem; }
  .stat span { color: var(--muted); font-size: 0.92rem; }
  .notice { color: var(--success); font-weight: 600; margin-top: 24px; }

  footer {
    border-top: 1px solid var(--line); text-align: center;
    color: var(--muted); font-size: 0.88rem; padding: 20px;
  }
</style>
</head>
<body>

<header>
  <div class="bar">
    <a class="brand" href="#/home">Harbor</a>
    <nav id="nav" aria-label="Main"></nav>
  </div>
</header>

<main>
  <!-- HOME -->
  <section id="view-home" class="view wrap" hidden>
    <div class="hero">
      <h1>A quiet place to keep your work in order.</h1>
      <p>Harbor is a small example site. Sign in to see your dashboard, or send us an enquiry.</p>
      <a class="btn" href="#/login">Sign in</a>
      <a class="btn ghost" href="#/enquiry">Send an enquiry</a>
    </div>
    <div class="features">
      <div class="feature"><h3>Simple</h3><p>One HTML file. No build step, no dependencies.</p></div>
      <div class="feature"><h3>Responsive</h3><p>Works on phones, tablets and desktops, in light or dark mode.</p></div>
      <div class="feature"><h3>Enquiries by email</h3><p>Every enquiry is sent straight to your inbox.</p></div>
    </div>
  </section>

  <!-- ENQUIRY -->
  <section id="view-enquiry" class="view wrap" hidden>
    <div class="card">
      <h2>Send an enquiry</h2>
      <p class="sub">Tell us what you need and we'll reply by email.</p>
      <form id="enquiry-form" novalidate>
        <label for="enq-name">Your name</label>
        <input id="enq-name" name="name" type="text" autocomplete="name" required>

        <label for="enq-email">Your email</label>
        <input id="enq-email" name="email" type="email" autocomplete="email" placeholder="you@example.com" required>

        <label for="enq-message">Message</label>
        <textarea id="enq-message" name="message" required></textarea>

        <!-- Spam trap: real users never see or fill this -->
        <input class="hp" type="text" name="_honey" tabindex="-1" autocomplete="off" aria-hidden="true">

        <button class="btn block" type="submit" id="enq-btn" style="margin-top:20px">Send enquiry</button>
        <p class="msg" id="enq-msg" role="alert" aria-live="polite"></p>
      </form>
    </div>
  </section>

  <!-- LOGIN -->
  <section id="view-login" class="view wrap" hidden>
    <div class="card">
      <h2>Sign in</h2>
      <p class="sub">Use your email and password to continue.</p>
      <form id="login-form" novalidate>
        <label for="email">Email</label>
        <input id="email" type="email" autocomplete="username" placeholder="you@example.com" required>

        <label for="password">Password</label>
        <div class="pw-row">
          <input id="password" type="password" autocomplete="current-password" required>
          <button type="button" class="pw-toggle" id="pw-toggle" aria-label="Show password">Show</button>
        </div>

        <div class="row">
          <label><input type="checkbox" id="remember"> Remember me</label>
          <a href="#/login" id="forgot">Forgot password?</a>
        </div>

        <button class="btn block" type="submit">Sign in</button>
        <p class="msg error" id="error" role="alert" aria-live="polite"></p>
      </form>
      <div class="hint">
        Demo account: <code>demo@example.com</code> / <code>password123</code>
      </div>
    </div>
  </section>

  <!-- DASHBOARD -->
  <section id="view-dashboard" class="view wrap" hidden>
    <div class="welcome">
      <h2 id="greeting">Welcome back</h2>
      <p>Here's a quick look at your account.</p>
    </div>
    <div class="stats">
      <div class="stat"><b>12</b><span>Open tasks</span></div>
      <div class="stat"><b>4</b><span>Due this week</span></div>
      <div class="stat"><b>38</b><span>Completed this month</span></div>
    </div>
    <p class="notice">You're signed in.</p>
  </section>
</main>

<footer>Harbor demo site</footer>

<script>
  // ====== Email that receives enquiries ======
  const RECEIVER_EMAIL = "gokulkuppusamy66@gmail.com";
  // ===========================================

  // Demo user (replace with a real server check in production)
  const DEMO_USER = { email: "demo@example.com", password: "password123", name: "Demo" };

  // Session helpers (fall back to memory if storage is unavailable)
  let memorySession = null;
  const session = {
    get() {
      try {
        const raw = sessionStorage.getItem("harbor-user") || localStorage.getItem("harbor-user");
        return raw ? JSON.parse(raw) : memorySession;
      } catch (e) { return memorySession; }
    },
    set(user, remember) {
      memorySession = user;
      try {
        (remember ? localStorage : sessionStorage).setItem("harbor-user", JSON.stringify(user));
      } catch (e) {}
    },
    clear() {
      memorySession = null;
      try {
        sessionStorage.removeItem("harbor-user");
        localStorage.removeItem("harbor-user");
      } catch (e) {}
    }
  };

  // Routing
  const views = ["home", "enquiry", "login", "dashboard"];

  function currentRoute() {
    const r = (location.hash.replace("#/", "") || "home");
    return views.includes(r) ? r : "home";
  }

  function render() {
    let route = currentRoute();
    const user = session.get();

    if (route === "dashboard" && !user) route = "login";
    if (route === "login" && user) route = "dashboard";

    views.forEach(v => document.getElementById("view-" + v).hidden = (v !== route));

    const nav = document.getElementById("nav");
    nav.innerHTML = "";
    nav.append(link("Home", "#/home"));
    nav.append(link("Enquiry", "#/enquiry"));
    if (user) {
      nav.append(link("Dashboard", "#/dashboard"));
      const out = document.createElement("button");
      out.textContent = "Log out";
      out.onclick = () => { session.clear(); location.hash = "#/home"; render(); };
      nav.append(out);
      document.getElementById("greeting").textContent = "Welcome back, " + user.name;
    } else {
      nav.append(link("Log in", "#/login", true));
    }
    document.title = "Harbor – " + route.charAt(0).toUpperCase() + route.slice(1);
    window.scrollTo(0, 0);
  }

  function link(text, href, primary) {
    const a = document.createElement("a");
    a.textContent = text;
    a.href = href;
    if (primary) a.className = "primary";
    return a;
  }

  window.addEventListener("hashchange", render);

  // ---------- Enquiry form (emailed via FormSubmit) ----------
  const enqForm = document.getElementById("enquiry-form");
  const enqMsg = document.getElementById("enq-msg");
  const enqBtn = document.getElementById("enq-btn");

  enqForm.addEventListener("submit", async (e) => {
    e.preventDefault();
    enqMsg.className = "msg error";

    const name = document.getElementById("enq-name").value.trim();
    const email = document.getElementById("enq-email").value.trim();
    const message = document.getElementById("enq-message").value.trim();

    if (!name || !email || !message) {
      enqMsg.textContent = "Fill in your name, email and message.";
      return;
    }
    if (!/^\S+@\S+\.\S+$/.test(email)) {
      enqMsg.textContent = "Enter a valid email address.";
      return;
    }
    if (enqForm.elements["_honey"].value) return;

    enqBtn.disabled = true;
    enqBtn.textContent = "Sending...";
    enqMsg.textContent = "";

    const payload = {
      name: name,
      email: email,
      message: message,
      _subject: "New enquiry from " + name,
      _replyto: email,
      _template: "table",
      _captcha: "false"
    };

    try {
      const res = await fetch("https://formsubmit.co/ajax/" + RECEIVER_EMAIL, {
        method: "POST",
        headers: { "Content-Type": "application/json", "Accept": "application/json" },
        body: JSON.stringify(payload)
      });

      let data = {};
      try { data = await res.json(); } catch (_) {}

      if (res.ok && (data.success === true || data.success === "true")) {
        enqMsg.className = "msg ok";
        enqMsg.textContent = "Enquiry sent. We'll reply to " + email + ".";
        enqForm.reset();
      } else {
        enqMsg.className = "msg error";
        enqMsg.textContent = data.message
          ? "Not sent: " + data.message
          : "Not sent. Check your inbox (and spam) for the FormSubmit activation email and click its link.";
      }
    } catch (err) {
      // Network/CORS failure: fall back to a normal form post in a new tab
      const f = document.createElement("form");
      f.method = "POST";
      f.action = "https://formsubmit.co/" + RECEIVER_EMAIL;
      f.target = "_blank";
      Object.entries(payload).forEach(([k, v]) => {
        const i = document.createElement("input");
        i.type = "hidden"; i.name = k; i.value = v;
        f.appendChild(i);
      });
      document.body.appendChild(f);
      f.submit();
      f.remove();
      enqMsg.className = "msg ok";
      enqMsg.textContent = "Your enquiry was submitted in a new tab. Close it when it finishes.";
      enqForm.reset();
    } finally {
      enqBtn.disabled = false;
      enqBtn.textContent = "Send enquiry";
    }
  });

  // ---------- Login form ----------
  const form = document.getElementById("login-form");
  const errorEl = document.getElementById("error");
  const pw = document.getElementById("password");

  document.getElementById("pw-toggle").addEventListener("click", (e) => {
    const show = pw.type === "password";
    pw.type = show ? "text" : "password";
    e.target.textContent = show ? "Hide" : "Show";
    e.target.setAttribute("aria-label", show ? "Hide password" : "Show password");
  });

  document.getElementById("forgot").addEventListener("click", (e) => {
    e.preventDefault();
    errorEl.style.color = "var(--muted)";
    errorEl.textContent = "Password reset isn't set up in this demo.";
  });

  form.addEventListener("submit", (e) => {
    e.preventDefault();
    errorEl.style.color = "var(--danger)";
    const email = document.getElementById("email").value.trim().toLowerCase();
    const password = pw.value;

    if (!email || !password) {
      errorEl.textContent = "Enter your email and password.";
      return;
    }
    if (!/^\S+@\S+\.\S+$/.test(email)) {
      errorEl.textContent = "Enter a valid email address.";
      return;
    }
    if (email === DEMO_USER.email && password === DEMO_USER.password) {
      errorEl.textContent = "";
      session.set({ email, name: DEMO_USER.name }, document.getElementById("remember").checked);
      form.reset();
      location.hash = "#/dashboard";
      render();
    } else {
      errorEl.textContent = "Email or password is incorrect. Check both and try again.";
      pw.value = "";
      pw.focus();
    }
  });

  render();
</script>
</body>
</html>
