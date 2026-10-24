<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Graphic World | Portfolio</title>
  <style>
    :root {
      --bg: #0f1115;
      --card-bg: #181b22;
      --accent: #ff4b4b;
      --text: #f0f2f5;
      --text-muted: #9aa0a6;
      --border: #2d3139;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      line-height: 1.6;
    }

    header {
      position: sticky;
      top: 0;
      background: rgba(15, 17, 21, 0.9);
      backdrop-filter: blur(10px);
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.2rem 8%;
      border-bottom: 1px solid var(--border);
      z-index: 100;
    }

    .logo {
      font-size: 1.5rem;
      font-weight: 800;
      letter-spacing: -0.5px;
      color: var(--text);
      text-decoration: none;
    }

    .logo span {
      color: var(--accent);
    }

    nav a {
      color: var(--text-muted);
      text-decoration: none;
      margin-left: 2rem;
      font-weight: 500;
      transition: color 0.2s ease;
    }

    nav a:hover {
      color: var(--text);
    }

    .hero {
      text-align: center;
      padding: 5rem 1rem 3rem;
      max-width: 800px;
      margin: 0 auto;
    }

    .hero h1 {
      font-size: 3rem;
      line-height: 1.1;
      margin-bottom: 1rem;
      font-weight: 800;
    }

    .hero p {
      color: var(--text-muted);
      font-size: 1.15rem;
      margin-bottom: 2rem;
    }

    .filter-buttons {
      display: flex;
      justify-content: center;
      gap: 0.75rem;
      margin-bottom: 3rem;
      flex-wrap: wrap;
    }

    .btn-filter {
      background: var(--card-bg);
      border: 1px solid var(--border);
      color: var(--text-muted);
      padding: 0.5rem 1.25rem;
      border-radius: 20px;
      cursor: pointer;
      font-weight: 500;
      transition: all 0.2s ease;
    }

    .btn-filter.active, .btn-filter:hover {
      background: var(--accent);
      color: #fff;
      border-color: var(--accent);
    }

    .portfolio {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 1.5rem 5rem;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 1.75rem;
    }

    .project-card {
      background: var(--card-bg);
      border-radius: 12px;
      overflow: hidden;
      border: 1px solid var(--border);
      transition: transform 0.25s ease, border-color 0.25s ease;
      cursor: pointer;
    }

    .project-card:hover {
      transform: translateY(-4px);
      border-color: var(--accent);
    }

    .project-card img {
      width: 100%;
      height: 240px;
      object-fit: cover;
      display: block;
      background: #252932;
    }

    .card-info {
      padding: 1.25rem;
    }

    .card-info span {
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      color: var(--accent);
      font-weight: 700;
    }

    .card-info h3 {
      font-size: 1.2rem;
      margin: 0.3rem 0;
    }

    .contact {
      background: var(--card-bg);
      border-top: 1px solid var(--border);
      padding: 4rem 1rem;
      text-align: center;
    }

    .contact h2 {
      margin-bottom: 1rem;
    }

    .contact a.btn-cta {
      display: inline-block;
      margin-top: 1.5rem;
      background: var(--accent);
      color: white;
      text-decoration: none;
      padding: 0.85rem 2rem;
      border-radius: 30px;
      font-weight: 600;
      transition: opacity 0.2s ease;
    }

    .contact a.btn-cta:hover {
      opacity: 0.9;
    }

    /* Modal Viewer */
    .modal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.85);
      z-index: 200;
      justify-content: center;
      align-items: center;
      padding: 1rem;
    }

    .modal.active {
      display: flex;
    }

    .modal-content {
      background: var(--card-bg);
      border-radius: 12px;
      max-width: 700px;
      width: 100%;
      overflow: hidden;
      position: relative;
      border: 1px solid var(--border);
    }

    .modal-content img {
      width: 100%;
      max-height: 400px;
      object-fit: cover;
    }

    .modal-text {
      padding: 1.5rem;
    }

    .close-btn {
      position: absolute;
      top: 10px;
      right: 15px;
      font-size: 2rem;
      color: #fff;
      cursor: pointer;
      line-height: 1;
    }
  </style>
</head>
<body>

  <header>
    <a href="#" class="logo">Graphic<span>World</span>.</a>
    <nav>
      <a href="#work">Work</a>
      <a href="#about">About</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <section class="hero">
      <h1>Visual Identity & Graphic Design</h1>
      <p>Welcome to Graphic World. We craft brand identities, marketing collateral, packaging, and digital visuals that stand out.</p>
      
      <div class="filter-buttons">
        <button class="btn-filter active" onclick="filterSelection('all')">All</button>
        <button class="btn-filter" onclick="filterSelection('branding')">Branding</button>
        <button class="btn-filter" onclick="filterSelection('packaging')">Packaging</button>
        <button class="btn-filter" onclick="filterSelection('social')">Social Media</button>
      </div>
    </section>

    <section class="portfolio" id="work">
      <div class="grid">
        <!-- Project 1 -->
        <div class="project-card" data-category="branding" onclick="openModal('https://images.unsplash.com/photo-1626785774573-4b799315345d?auto=format&fit=crop&w=1000&q=80', 'Nordic Roast Co.', 'Complete identity, logo mark, and typography suite for an artisanal coffee roastery.')">
          <img src="https://images.unsplash.com/photo-1626785774573-4b799315345d?auto=format&fit=crop&w=600&q=80" alt="Branding Project" loading="lazy" />
          <div class="card-info">
            <span>Branding</span>
            <h3>Nordic Roast Co.</h3>
          </div>
        </div>

        <!-- Project 2 -->
        <div class="project-card" data-category="packaging" onclick="openModal('https://images.unsplash.com/photo-1547949003-9792a18a2601?auto=format&fit=crop&w=1000&q=80', 'Botanica Skincare', 'Minimalist glass bottle and carton packaging system using eco-friendly foils.')">
          <img src="https://images.unsplash.com/photo-1547949003-9792a18a2601?auto=format&fit=crop&w=600&q=80" alt="Packaging Project" loading="lazy" />
          <div class="card-info">
            <span>Packaging</span>
            <h3>Botanica Skincare</h3>
          </div>
        </div>

        <!-- Project 3 -->
        <div class="project-card" data-category="social" onclick="openModal('https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=1000&q=80', 'Synapse Tech Festival', 'High-energy social media campaign kit and billboard posters.')">
          <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=600&q=80" alt="Social Media Campaign" loading="lazy" />
          <div class="card-info">
            <span>Social Media</span>
            <h3>Synapse Tech Festival</h3>
          </div>
        </div>
      </div>
    </section>

    <!-- Modal Component -->
    <div class="modal" id="projectModal" onclick="closeModal(event)">
      <div class="modal-content" onclick="event.stopPropagation()">
        <span class="close-btn" onclick="closeModal()">&times;</span>
        <img id="modalImg" src="" alt="Project detail" />
        <div class="modal-text">
          <h2 id="modalTitle"></h2>
          <p id="modalDesc" style="color: var(--text-muted); margin-top: 0.5rem;"></p>
        </div>
      </div>
    </div>

    <!-- Contact Section -->
    <section class="contact" id="contact">
      <h2>Let’s Build Something Memorable</h2>
      <p style="color: var(--text-muted);">Available for freelance commissions and full identity overhauls.</p>
      <a href="mailto:your-email@example.com" class="btn-cta">Email Graphic World</a>
    </section>
  </main>

  <script>
    function filterSelection(category) {
      const cards = document.querySelectorAll('.project-card');
      const buttons = document.querySelectorAll('.btn-filter');

      buttons.forEach(btn => {
        btn.classList.toggle('active', btn.textContent.toLowerCase() === category || (category === 'all' && btn.textContent === 'All'));
      });

      cards.forEach(card => {
        if (category === 'all' || card.dataset.category === category) {
          card.style.display = 'block';
        } else {
          card.style.display = 'none';
        }
      });
    }

    function openModal(imgSrc, title, desc) {
      document.getElementById('modalImg').src = imgSrc;
      document.getElementById('modalTitle').textContent = title;
      document.getElementById('modalDesc').textContent = desc;
      document.getElementById('projectModal').classList.add('active');
    }

    function closeModal() {
      document.getElementById('projectModal').classList.remove('active');
    }

    window.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') closeModal();
    });
  </script>
</body>
</html>
