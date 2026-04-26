<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Ajaya Kumar Pradhan — Data Analyst & BI Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg:        #0d0d0f;
    --surface:   #13131a;
    --border:    #1e1e2e;
    --gold:      #c9a96e;
    --gold-dim:  #8a6c40;
    --text:      #e8e4dc;
    --muted:     #6b6778;
    --accent:    #4fc3a1;
    --radius:    14px;
  }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── NOISE TEXTURE ── */
  body::before {
    content: '';
    position: fixed; inset: 0; z-index: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
    pointer-events: none;
  }

  /* ── GLOW ── */
  .glow-orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    pointer-events: none;
    z-index: 0;
  }
  .orb1 { width: 600px; height: 600px; background: rgba(201,169,110,.07); top: -200px; right: -150px; }
  .orb2 { width: 400px; height: 400px; background: rgba(79,195,161,.05); bottom: 10%; left: -100px; }

  /* ── LAYOUT ── */
  .container {
    position: relative; z-index: 1;
    max-width: 900px;
    margin: 0 auto;
    padding: 0 28px 80px;
  }

  /* ── HEADER ── */
  header {
    padding: 80px 0 60px;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 40px;
    align-items: end;
    border-bottom: 1px solid var(--border);
    animation: fadeUp .8s ease both;
  }

  .header-left {}
  .eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: .25em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 18px;
  }

  h1 {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.4rem, 5vw, 3.6rem);
    font-weight: 700;
    line-height: 1.1;
    color: var(--text);
    letter-spacing: -.01em;
    margin-bottom: 16px;
  }

  .tagline {
    font-size: 15px;
    font-weight: 300;
    color: var(--muted);
    max-width: 420px;
    line-height: 1.7;
  }

  .badges {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    margin-top: 28px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 14px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 100px;
    font-size: 12px;
    font-weight: 500;
    color: var(--muted);
    transition: border-color .2s, color .2s;
  }
  .badge:hover { border-color: var(--gold-dim); color: var(--text); }
  .badge .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); }

  .contact-links {
    display: flex;
    flex-direction: column;
    gap: 12px;
    align-items: flex-end;
  }

  .contact-links a {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: .05em;
    color: var(--muted);
    text-decoration: none;
    padding: 8px 16px;
    border: 1px solid var(--border);
    border-radius: 8px;
    transition: all .2s;
    white-space: nowrap;
  }
  .contact-links a:hover { border-color: var(--gold); color: var(--gold); }

  /* ── SECTION ── */
  section {
    margin-top: 64px;
    animation: fadeUp .8s ease both;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: .3em;
    text-transform: uppercase;
    color: var(--gold-dim);
    margin-bottom: 28px;
    display: flex;
    align-items: center;
    gap: 14px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── ABOUT GRID ── */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .about-cell {
    background: var(--surface);
    padding: 24px;
  }
  .about-cell .label {
    font-size: 10px;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 6px;
  }
  .about-cell .value {
    font-size: 14px;
    font-weight: 500;
    color: var(--text);
    line-height: 1.5;
  }

  /* ── SKILLS ── */
  .skill-groups {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2px;
    background: var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }

  .skill-group {
    background: var(--surface);
    padding: 24px 28px;
  }

  .skill-group-title {
    font-size: 11px;
    letter-spacing: .15em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 16px;
    font-weight: 600;
  }

  .skill-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .pill {
    padding: 5px 12px;
    background: rgba(201,169,110,.06);
    border: 1px solid rgba(201,169,110,.15);
    border-radius: 6px;
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: #b8a47a;
    transition: background .2s, border-color .2s;
  }
  .pill:hover { background: rgba(201,169,110,.12); border-color: rgba(201,169,110,.35); }

  .pill.accent {
    background: rgba(79,195,161,.06);
    border-color: rgba(79,195,161,.18);
    color: #4fc3a1;
  }
  .pill.accent:hover { background: rgba(79,195,161,.12); }

  /* ── PROJECTS ── */
  .project-list {
    display: flex;
    flex-direction: column;
    gap: 2px;
    background: var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }

  .project-card {
    background: var(--surface);
    padding: 28px 32px;
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 24px;
    align-items: start;
    transition: background .2s;
    cursor: default;
  }
  .project-card:hover { background: #16161f; }

  .project-index {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--gold-dim);
    letter-spacing: .1em;
    margin-bottom: 10px;
  }

  .project-name {
    font-family: 'Playfair Display', serif;
    font-size: 1.15rem;
    font-weight: 600;
    color: var(--text);
    margin-bottom: 8px;
    line-height: 1.3;
  }

  .project-desc {
    font-size: 13.5px;
    color: var(--muted);
    line-height: 1.65;
    margin-bottom: 16px;
    max-width: 500px;
  }

  .project-highlights {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-bottom: 18px;
  }

  .highlight-tag {
    font-size: 11px;
    font-family: 'DM Mono', monospace;
    color: var(--muted);
    padding: 3px 9px;
    border-radius: 4px;
    background: rgba(255,255,255,.03);
    border: 1px solid var(--border);
  }

  .project-stack {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--gold-dim);
  }

  .project-links {
    display: flex;
    flex-direction: column;
    gap: 8px;
    flex-shrink: 0;
  }

  .plink {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 14px;
    border-radius: 8px;
    font-size: 11px;
    font-weight: 600;
    font-family: 'DM Mono', monospace;
    letter-spacing: .04em;
    text-decoration: none;
    border: 1px solid;
    transition: all .2s;
    white-space: nowrap;
  }

  .plink-live {
    border-color: rgba(201,169,110,.3);
    color: var(--gold);
    background: rgba(201,169,110,.05);
  }
  .plink-live:hover { background: rgba(201,169,110,.12); border-color: var(--gold); }

  .plink-code {
    border-color: var(--border);
    color: var(--muted);
    background: transparent;
  }
  .plink-code:hover { border-color: var(--muted); color: var(--text); }

  /* ── DIVIDER ── */
  hr.divider {
    border: none;
    height: 1px;
    background: var(--border);
    margin: 60px 0;
  }

  /* ── FOOTER ── */
  footer {
    margin-top: 80px;
    padding-top: 32px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 16px;
  }

  .footer-quote {
    font-family: 'Playfair Display', serif;
    font-size: 13px;
    font-style: italic;
    color: var(--muted);
    max-width: 380px;
    line-height: 1.6;
  }

  .footer-links {
    display: flex;
    gap: 16px;
  }
  .footer-links a {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: .1em;
    text-transform: uppercase;
    color: var(--muted);
    text-decoration: none;
    transition: color .2s;
  }
  .footer-links a:hover { color: var(--gold); }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  section:nth-child(2) { animation-delay: .1s; }
  section:nth-child(3) { animation-delay: .2s; }
  section:nth-child(4) { animation-delay: .3s; }
  section:nth-child(5) { animation-delay: .4s; }

  /* ── RESPONSIVE ── */
  @media (max-width: 640px) {
    header { grid-template-columns: 1fr; }
    .contact-links { flex-direction: row; align-items: flex-start; flex-wrap: wrap; }
    .about-grid, .skill-groups { grid-template-columns: 1fr; }
    .project-card { grid-template-columns: 1fr; }
    .project-links { flex-direction: row; flex-wrap: wrap; }
  }
</style>
</head>
<body>

<div class="glow-orb orb1"></div>
<div class="glow-orb orb2"></div>

<div class="container">

  <!-- HEADER -->
  <header>
    <div class="header-left">
      <div class="eyebrow">Portfolio · 2025</div>
      <h1>Ajaya Kumar<br>Pradhan</h1>
      <p class="tagline">Power BI Developer & Data Analyst — turning raw data into decisions through BI, SQL, Python, and predictive analytics.</p>
      <div class="badges">
        <span class="badge"><span class="dot"></span>Open to Analyst & BI Roles</span>
        <span class="badge">Bhubaneswar, India</span>
        <span class="badge">AlmaBetter Certified</span>
      </div>
    </div>
    <div class="contact-links">
      <a href="https://www.linkedin.com/in/ajayakumarpradhan/" target="_blank">↗ LinkedIn</a>
      <a href="mailto:ajayapradhan.connect@gmail.com">✉ Email</a>
      <a href="https://github.com/ajaya-kumar-pradhan" target="_blank">⌥ GitHub</a>
    </div>
  </header>

  <!-- ABOUT -->
  <section>
    <div class="section-label">Profile</div>
    <div class="about-grid">
      <div class="about-cell">
        <div class="label">Education</div>
        <div class="value">B.A. Economics Honours<br><span style="color:var(--muted);font-size:13px;">Rajdhani College, Bhubaneswar · 2017</span></div>
      </div>
      <div class="about-cell">
        <div class="label">Certification</div>
        <div class="value">Full Stack Data Science<br><span style="color:var(--muted);font-size:13px;">AlmaBetter · 2023–2024</span></div>
      </div>
      <div class="about-cell">
        <div class="label">Core Specialisation</div>
        <div class="value">End-to-end BI: ETL → Star Schema → DAX → Deployment</div>
      </div>
      <div class="about-cell">
        <div class="label">Domain Exposure</div>
        <div class="value">FinTech · Logistics · Healthcare · Retail · Banking</div>
      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section>
    <div class="section-label">Tech Stack</div>
    <div class="skill-groups">
      <div class="skill-group">
        <div class="skill-group-title">BI & Visualisation</div>
        <div class="skill-pills">
          <span class="pill">Power BI</span>
          <span class="pill">DAX</span>
          <span class="pill">Tableau</span>
          <span class="pill">Excel</span>
          <span class="pill">RLS</span>
          <span class="pill">Incremental Refresh</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Database & SQL</div>
        <div class="skill-pills">
          <span class="pill">SQL Server</span>
          <span class="pill">PostgreSQL</span>
          <span class="pill">MySQL</span>
          <span class="pill">ETL Pipelines</span>
          <span class="pill">Star Schema</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Machine Learning</div>
        <div class="skill-pills">
          <span class="pill accent">Python</span>
          <span class="pill accent">Scikit-Learn</span>
          <span class="pill accent">XGBoost</span>
          <span class="pill accent">Pandas</span>
          <span class="pill accent">NumPy</span>
          <span class="pill accent">SHAP</span>
        </div>
      </div>
      <div class="skill-group">
        <div class="skill-group-title">Deployment & Tools</div>
        <div class="skill-pills">
          <span class="pill accent">Streamlit</span>
          <span class="pill accent">FastAPI</span>
          <span class="pill accent">Hugging Face</span>
          <span class="pill">Git</span>
          <span class="pill">Jupyter</span>
          <span class="pill">VS Code</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section>
    <div class="section-label">Featured Projects</div>
    <div class="project-list">

      <div class="project-card">
        <div>
          <div class="project-index">01 / FinTech</div>
          <div class="project-name">Loan Approval & Credit Risk Analytics System</div>
          <div class="project-desc">Full-stack credit risk platform combining SQL BI, Power BI reporting, and Random Forest predictions — from schema design to live deployment.</div>
          <div class="project-highlights">
            <span class="highlight-tag">Daily-grain Star Schema</span>
            <span class="highlight-tag">20+ DAX Measures</span>
            <span class="highlight-tag">YoY Risk Concentration</span>
            <span class="highlight-tag">Dual-pane Streamlit App</span>
          </div>
          <div class="project-stack">Power BI · SQL · Python · Scikit-Learn · Streamlit · Hugging Face</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://huggingface.co/spaces/ajayapradhanconnect/loan-default-predictor" target="_blank">↗ Live App</a>
          <a class="plink plink-live" href="https://app.powerbi.com/view?r=eyJrIjoiNGYzMTM1ZDItODQ3Mi00ZWVhLWE3MjQtOGYxYmZjOGRmZDYyIiwidCI6IjdlMzEwODQ1LTg0ZTEtNGRiOC1hZjk4LTcwNDA0MTkwZDhkZSJ9" target="_blank">↗ Dashboard</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/Loan-Approval-Credit-Risk-Analytics-System" target="_blank">⌥ Code</a>
        </div>
      </div>

      <div class="project-card">
        <div>
          <div class="project-index">02 / E-Commerce</div>
          <div class="project-name">E-Commerce Analytics Intelligence Dashboard</div>
          <div class="project-desc">Enterprise-grade Power BI solution for global performance monitoring with customer segmentation and dynamic KPI design.</div>
          <div class="project-highlights">
            <span class="highlight-tag">YTD / YOY Growth</span>
            <span class="highlight-tag">AOV Tracking</span>
            <span class="highlight-tag">Geo Analysis</span>
            <span class="highlight-tag">Star Schema Model</span>
          </div>
          <div class="project-stack">Power BI · DAX · SQL · Excel</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://app.powerbi.com/view?r=eyJrIjoiZDA0M2E1YWUtMGU2NC00NDk2LTg1MjUtOTRhNmM5MDk5OTEzIiwidCI6IjdlMzEwODQ1LTg0ZTEtNGRiOC1hZjk4LTcwNDA0MTkwZDhkZSJ9" target="_blank">↗ Dashboard</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/E-Commerce-Analytics-Intelligence-Dashboard" target="_blank">⌥ Code</a>
        </div>
      </div>

      <div class="project-card">
        <div>
          <div class="project-index">03 / Banking</div>
          <div class="project-name">Banking Analytics Dashboard</div>
          <div class="project-desc">Financial analytics platform for loan portfolio management, NPL monitoring, and automated ETL pipelines with SQL Server.</div>
          <div class="project-highlights">
            <span class="highlight-tag">NPL Monitoring</span>
            <span class="highlight-tag">Delinquency %</span>
            <span class="highlight-tag">Auto ETL</span>
            <span class="highlight-tag">Customer Segmentation</span>
          </div>
          <div class="project-stack">Power BI · SQL Server · ETL</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://app.powerbi.com/view?r=eyJrIjoiOTQ5Y2UyY2UtNWM2NC00NGYyLTllNWUtYmU1ZDhkM2YwYzg5IiwidCI6IjdlMzEwODQ1LTg0ZTEtNGRiOC1hZjk4LTcwNDA0MTkwZDhkZSJ9" target="_blank">↗ Dashboard</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/Banking-Analytics-Dashboard" target="_blank">⌥ Code</a>
        </div>
      </div>

      <div class="project-card">
        <div>
          <div class="project-index">04 / Risk · ML</div>
          <div class="project-name">Fraud Detection Risk Intelligence System</div>
          <div class="project-desc">XGBoost-powered real-time fraud detection with SHAP explainability and an interactive risk monitoring dashboard.</div>
          <div class="project-highlights">
            <span class="highlight-tag">94%+ Recall</span>
            <span class="highlight-tag">SHAP Explainability</span>
            <span class="highlight-tag">Real-time Detection</span>
          </div>
          <div class="project-stack">Python · XGBoost · Streamlit · Hugging Face</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://huggingface.co/spaces/ajayapradhanconnect/Fraud-Detection-Risk-Intelligence-System" target="_blank">↗ Live App</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/fraud-detection-risk-intelligence-system" target="_blank">⌥ Code</a>
        </div>
      </div>

      <div class="project-card">
        <div>
          <div class="project-index">05 / Airline · ML</div>
          <div class="project-name">Airline Passenger Referral Prediction</div>
          <div class="project-desc">ML classifier predicting customer recommendation likelihood from 10K+ reviews with feature engineering and EDA.</div>
          <div class="project-highlights">
            <span class="highlight-tag">10K+ Reviews</span>
            <span class="highlight-tag">Feature Engineering</span>
            <span class="highlight-tag">Deployed on HF</span>
          </div>
          <div class="project-stack">Python · Scikit-Learn · Streamlit</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://huggingface.co/spaces/ajayapradhanconnect/Airline-Passenger-Referral-Prediction" target="_blank">↗ Live App</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/Airline-Passenger-Referral-Prediction" target="_blank">⌥ Code</a>
        </div>
      </div>

      <div class="project-card">
        <div>
          <div class="project-index">06 / RecSys</div>
          <div class="project-name">Book Recommendation System</div>
          <div class="project-desc">Collaborative filtering engine using KNN for personalised book recommendations with an interactive Streamlit UI.</div>
          <div class="project-highlights">
            <span class="highlight-tag">KNN Model</span>
            <span class="highlight-tag">Collaborative Filtering</span>
            <span class="highlight-tag">Interactive UI</span>
          </div>
          <div class="project-stack">Python · Scikit-Learn · Flask · Streamlit</div>
        </div>
        <div class="project-links">
          <a class="plink plink-live" href="https://huggingface.co/spaces/ajayapradhanconnect/Book-Recommendation-System" target="_blank">↗ Live App</a>
          <a class="plink plink-code" href="https://github.com/ajaya-kumar-pradhan/Book-Recommendation-System" target="_blank">⌥ Code</a>
        </div>
      </div>

    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <p class="footer-quote">"In God we trust; all others must bring data." — W. Edwards Deming</p>
    <div class="footer-links">
      <a href="https://www.linkedin.com/in/ajayakumarpradhan/" target="_blank">LinkedIn</a>
      <a href="https://github.com/ajaya-kumar-pradhan" target="_blank">GitHub</a>
      <a href="mailto:ajayapradhan.connect@gmail.com">Email</a>
    </div>
  </footer>

</div>
</body>
</html>
