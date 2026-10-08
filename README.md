<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trendora — Trends, Style & Culture</title>
<style>
  :root{
    --bg:#fdfaf7; --bg2:#f6f0ea; --card:#ffffff; --text:#211d1a; --muted:#6f6a63;
    --accent:#c2476b; --accent2:#fbe9ef; --border:#ebe4dc; --shadow:0 2px 12px rgba(0,0,0,.06);
  }
  [data-theme="dark"]{
    --bg:#161314; --bg2:#1e1a1c; --card:#201c1e; --text:#f0ecea; --muted:#a39c97;
    --accent:#e78aa8; --accent2:#332028; --border:#332d30; --shadow:0 2px 12px rgba(0,0,0,.35);
  }
  *{margin:0;padding:0;box-sizing:border-box}
  html{scroll-behavior:smooth}
  body{font-family:Georgia,'Times New Roman',serif;background:var(--bg);color:var(--text);line-height:1.65;transition:background .3s,color .3s}
  .wrap{max-width:1080px;margin:0 auto;padding:0 24px}

  /* Header */
  header{position:sticky;top:0;z-index:50;background:var(--bg);border-bottom:1px solid var(--border)}
  .nav{display:flex;align-items:center;justify-content:space-between;height:64px}
  .logo{font-size:1.35rem;font-weight:700;letter-spacing:.5px;color:var(--text);text-decoration:none;font-family:Helvetica,Arial,sans-serif}
  .logo span{color:var(--accent)}
  .nav-links{display:flex;gap:26px;list-style:none;align-items:center}
  .nav-links a{color:var(--muted);text-decoration:none;font-size:.95rem;font-family:Helvetica,Arial,sans-serif;transition:color .2s}
  .nav-links a:hover{color:var(--accent)}
  .theme-btn{cursor:pointer;border:1px solid var(--border);background:var(--card);color:var(--text);border-radius:999px;padding:6px 14px;font-size:.85rem;font-family:Helvetica,Arial,sans-serif}
  #menu-toggle{display:none;background:none;border:none;color:var(--text);font-size:1.4rem;cursor:pointer}

  /* Hero */
  .hero{padding:88px 0 64px;text-align:center}
  .hero .kicker{font-family:Helvetica,Arial,sans-serif;font-size:.8rem;letter-spacing:2.5px;text-transform:uppercase;color:var(--accent)}
  .hero h1{font-size:clamp(2.2rem,5vw,3.6rem);margin:14px 0 12px;line-height:1.15}
  .hero p{color:var(--muted);max-width:560px;margin:0 auto;font-size:1.08rem}
  .search-box{margin:32px auto 0;max-width:440px;display:flex;border:1px solid var(--border);border-radius:999px;overflow:hidden;background:var(--card);box-shadow:var(--shadow)}
  .search-box input{flex:1;border:none;padding:13px 20px;font-size:.95rem;background:transparent;color:var(--text);outline:none;font-family:Helvetica,Arial,sans-serif}
  .search-box button{border:none;background:var(--accent);color:#fff;padding:0 22px;cursor:pointer;font-size:1rem}

  /* Sections */
  section{padding:40px 0}
  .section-title{font-family:Helvetica,Arial,sans-serif;font-size:.8rem;letter-spacing:2.5px;text-transform:uppercase;color:var(--accent);margin-bottom:20px;display:flex;align-items:center;gap:12px}
  .section-title::after{content:"";flex:1;height:1px;background:var(--border)}

  /* Featured */
  .featured{display:grid;grid-template-columns:1.2fr 1fr;gap:24px;background:var(--card);border:1px solid var(--border);border-radius:16px;overflow:hidden;box-shadow:var(--shadow)}
  .featured .art{background:linear-gradient(135deg,var(--accent),#e08aa5);min-height:300px;display:flex;align-items:center;justify-content:center;font-size:4rem}
  .featured .body{padding:36px 32px;display:flex;flex-direction:column;justify-content:center}
  .tag{display:inline-block;font-family:Helvetica,Arial,sans-serif;font-size:.72rem;letter-spacing:1.5px;text-transform:uppercase;background:var(--accent2);color:var(--accent);padding:4px 12px;border-radius:999px;width:fit-content}
  .featured h2{font-size:1.7rem;margin:14px 0 10px;line-height:1.25}
  .featured p{color:var(--muted);font-size:.98rem}
  .meta{font-family:Helvetica,Arial,sans-serif;font-size:.8rem;color:var(--muted);margin-top:18px}

  /* Post grid */
  .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:24px}
  .card{background:var(--card);border:1px solid var(--border);border-radius:16px;overflow:hidden;box-shadow:var(--shadow);transition:transform .25s,box-shadow .25s;display:flex;flex-direction:column}
  .card:hover{transform:translateY(-5px)}
  .card .art{height:150px;display:flex;align-items:center;justify-content:center;font-size:2.6rem}
  .card .body{padding:20px 22px 24px;display:flex;flex-direction:column;gap:10px;flex:1}
  .card h3{font-size:1.15rem;line-height:1.3}
  .card p{color:var(--muted);font-size:.92rem;flex:1}
  .card .meta{margin-top:4px}
  .a1{background:linear-gradient(135deg,#e5b8c9,#f4dfe8)}
  .a2{background:linear-gradient(135deg,#c9a8e0,#e8dbf4)}
  .a3{background:linear-gradient(135deg,#f0c9a8,#f8e8d8)}
  .a4{background:linear-gradient(135deg,#a8c9e0,#d8e8f4)}
  .a5{background:linear-gradient(135deg,#e0d3a8,#f4ecd4)}
  .a6{background:linear-gradient(135deg,#a8e0c9,#d8f4e8)}

  /* About */
  .about{background:var(--bg2);border-radius:16px;padding:48px;text-align:center}
  .about h2{font-size:1.6rem;margin-bottom:12px}
  .about p{color:var(--muted);max-width:620px;margin:0 auto}

  /* Newsletter */
  .newsletter{background:var(--accent2);border-radius:16px;padding:48px;text-align:center}
  .newsletter h2{font-size:1.5rem;margin-bottom:8px}
  .newsletter p{color:var(--muted);margin-bottom:22px}
  .newsletter form{display:flex;max-width:420px;margin:0 auto;border-radius:999px;overflow:hidden;border:1px solid var(--border)}
  .newsletter input{flex:1;border:none;padding:13px 20px;font-size:.95rem;background:var(--card);color:var(--text);outline:none;font-family:Helvetica,Arial,sans-serif}
  .newsletter button{border:none;background:var(--accent);color:#fff;padding:0 24px;cursor:pointer;font-family:Helvetica,Arial,sans-serif;font-size:.9rem}

  footer{border-top:1px solid var(--border);margin-top:48px;padding:28px 0;text-align:center;color:var(--muted);font-family:Helvetica,Arial,sans-serif;font-size:.85rem}

  /* Responsive */
  @media(max-width:820px){
    .featured{grid-template-columns:1fr}
    .grid{grid-template-columns:repeat(2,1fr)}
    .nav-links{position:fixed;inset:64px 0 auto 0;background:var(--bg);flex-direction:column;padding:20px;border-bottom:1px solid var(--border);display:none}
    .nav-links.open{display:flex}
    #menu-toggle{display:block}
  }
  @media(max-width:520px){.grid{grid-template-columns:1fr}.about,.newsletter{padding:32px 24px}}
</style>
</head>
<body>

<header>
  <div class="wrap nav">
    <a class="logo" href="#">Trend<span>ora</span></a>
    <button id="menu-toggle" aria-label="Menu">☰</button>
    <ul class="nav-links" id="nav-links">
      <li><a href="#home">Home</a></li>
      <li><a href="#posts">Posts</a></li>
      <li><a href="#about">About</a></li>
      <li><button class="theme-btn" id="theme-btn">🌙 Dark</button></li>
    </ul>
  </div>
</header>

<main class="wrap">
  <!-- Hero -->
  <div class="hero" id="home">
    <div class="kicker">Style · Culture · What's Next</div>
    <h1>Where trends are spotted before they peak</h1>
    <p>From street style to tech drops, food fads to design movements — Trendora tracks what's rising, why it matters, and what to watch next.</p>
    <div class="search-box">
      <input type="text" id="search" placeholder="Search trends…">
      <button aria-label="Search">⌕</button>
    </div>
  </div>

  <!-- Featured -->
  <section>
    <div class="section-title">Featured</div>
    <article class="featured">
      <div class="art">🕶️</div>
      <div class="body">
        <span class="tag">Style</span>
        <h2>The quiet luxury wave is over — say hello to "loud minimalism"</h2>
        <p>After years of beige and whisper-quiet logos, a new aesthetic is crashing the runway: bold shapes, single saturated colors, zero apologies. Here's why it's everywhere this season.</p>
        <div class="meta">Oct 5, 2026 · 8 min read</div>
      </div>
    </article>
  </section>

  <!-- Posts -->
  <section id="posts">
    <div class="section-title">Latest posts</div>
    <div class="grid" id="post-grid">
      <article class="card"><div class="art a1">👟</div><div class="body"><span class="tag">Fashion</span><h3>Retro runners are the only sneakers that matter in 2026</h3><p>Gorpcore had its moment. This year, it's all about vintage silhouettes, mesh, and that perfect worn-in look.</p><div class="meta">Sep 30, 2026 · 5 min read</div></div></article>
      <article class="card"><div class="art a2">🤖</div><div class="body"><span class="tag">Tech</span><h3>AI companions: the trend nobody admits they're trying</h3><p>From pocket coaches to chatty wearables — why personalized AI is quietly becoming the year's most personal gadget category.</p><div class="meta">Sep 24, 2026 · 12 min read</div></div></article>
      <article class="card"><div class="art a3">🍵</div><div class="body"><span class="tag">Food</span><h3>Swicy, meet smoky: the flavor mashup taking over menus</h3><p>Restaurants are burning, smoking, and charring everything sweet. We tasted the trend so you don't have to (but you will).</p><div class="meta">Sep 18, 2026 · 7 min read</div></div></article>
      <article class="card"><div class="art a4">🏠</div><div class="body"><span class="tag">Design</span><h3>"Cluttercore" vs. minimalism: the great home debate</h3><p>Maximalist shelves and layered textures are pushing back against empty white rooms. Which side of the shelf are you on?</p><div class="meta">Sep 11, 2026 · 9 min read</div></div></article>
      <article class="card"><div class="art a5">🎧</div><div class="body"><span class="tag">Culture</span><h3>Why everyone's listening to podcasts at 2x again</h3><p>Speed-listening is back, and it's not about impatience. A look at the attention economy's latest plot twist.</p><div class="meta">Sep 4, 2026 · 6 min read</div></div></article>
      <article class="card"><div class="art a6">🌿</div><div class="body"><span class="tag">Wellness</span><h3>The "soft hiking" movement: nature without the pain</h3><p>Slow trails, picnic breaks, and absolutely no summit selfies. The gentlest outdoor trend of the year explained.</p><div class="meta">Aug 27, 2026 · 10 min read</div></div></article>
    </div>
  </section>

  <!-- About -->
  <section id="about">
    <div class="about">
      <h2>About Trendora</h2>
      <p>Trendora is your early-warning system for culture. We track the signals — on runways, feeds, menus, and shelves — and translate them into stories you can actually use. No gatekeeping, no fluff, just what's next and why it matters.</p>
    </div>
  </section>

  <!-- Newsletter -->
  <section>
    <div class="newsletter">
      <h2>Never miss a trend</h2>
      <p>One sharp email a week. The rises, the fades, and the ones worth your money.</p>
      <form onsubmit="event.preventDefault();this.querySelector('button').textContent='Subscribed ✓';">
        <input type="email" placeholder="you@example.com" required>
        <button type="submit">Subscribe</button>
      </form>
    </div>
  </section>
</main>

<footer>© 2026 Trendora · Spot it first, wear it first</footer>

<script>
  // Dark mode toggle with persistence
  const btn = document.getElementById('theme-btn');
  const root = document.documentElement;
  if (localStorage.getItem('theme') === 'dark') root.dataset.theme = 'dark';
  const sync = () => btn.textContent = root.dataset.theme === 'dark' ? '☀️ Light' : '🌙 Dark';
  sync();
  btn.addEventListener('click', () => {
    root.dataset.theme = root.dataset.theme === 'dark' ? '' : 'dark';
    localStorage.setItem('theme', root.dataset.theme || 'light');
    sync();
  });

  // Mobile menu
  const toggle = document.getElementById('menu-toggle');
  const links = document.getElementById('nav-links');
  toggle.addEventListener('click', () => links.classList.toggle('open'));
  links.addEventListener('click', e => { if (e.target.tagName === 'A') links.classList.remove('open'); });

  // Live search filter
  const search = document.getElementById('search');
  const cards = document.querySelectorAll('#post-grid .card');
  search.addEventListener('input', () => {
    const q = search.value.toLowerCase();
    cards.forEach(c => c.style.display = c.textContent.toLowerCase().includes(q) ? '' : 'none');
  });
</script>
</body>
</html>
