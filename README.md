from pathlib import Path

html = r'''<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#050505">
<title>Zuha Maryam — Python & Machine Learning</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --font-sans:"Geist Variable",ui-sans-serif,system-ui,sans-serif;
  --font-mono:"Geist Mono Variable",ui-monospace,SFMono-Regular,Menlo,monospace;
  --font-display:"Space Grotesk Variable","Space Grotesk",ui-sans-serif,system-ui,sans-serif;
  --accent:#22c55e;--accent-light:#4ade80;--accent-dark:#16a34a;
  --accent-muted:#22c55e1f;--accent-glow:#22c55e59;
  --bg-primary:#050505;--bg-secondary:#0b0d10;--bg-card:#0f1116;
  --bg-elevated:#14171d;--bg-hover:#1a1e26;
  --border:#ffffff17;--border-subtle:#ffffff0f;--border-hover:#ffffff29;
  --border-accent:#22c55e66;
  --accent-gradient:linear-gradient(180deg,#3ee08f 0%,#21c274 100%);
  --shadow-card:0 12px 28px -18px #000000d9;
  --shadow-elevated:0 30px 70px -28px #000000d9,0 1px 0 0 #ffffff0d inset;
  --shadow-accent:0 8px 22px -8px #22c55e8c;
  --text-primary:#fafafa;--text-secondary:#a1a1a1;--text-muted:#666;--text-disabled:#404040;
  --space-1:4px;--space-2:8px;--space-3:12px;--space-4:16px;--space-5:20px;
  --space-6:24px;--space-8:32px;--space-10:40px;--space-12:48px;
  --space-16:64px;--space-20:80px;
  --radius-sm:6px;--radius-md:10px;--radius-lg:14px;--radius-xl:20px;--radius-full:9999px;
  --shadow-sm:0 1px 2px #0006;--shadow-md:0 4px 12px #00000080;--shadow-lg:0 8px 24px #0009;
  --shadow-glow:0 0 40px var(--accent-glow);
  --transition-fast:.15s cubic-bezier(.4,0,.2,1);
  --transition-base:.2s cubic-bezier(.4,0,.2,1);
  --transition-slow:.3s cubic-bezier(.4,0,.2,1);
}
*{box-sizing:border-box}
html{scroll-behavior:smooth}
body{margin:0;background:radial-gradient(ellipse at 50% -15%,#123321 0%,transparent 42%),var(--bg-primary);color:var(--text-primary);font-family:var(--font-sans);font-size:16px;line-height:1.6}
a{color:inherit;text-decoration:none}
button{font:inherit}
.wrap{width:min(1120px,calc(100% - 40px));margin:auto}
nav{height:72px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--border-subtle)}
.brand{display:flex;align-items:center;gap:11px;font-family:var(--font-display);font-weight:600;letter-spacing:-.4px}
.brand-mark{width:34px;height:34px;border-radius:10px;background:var(--accent-gradient);color:#052012;display:grid;place-items:center;font-weight:700}
.navlinks{display:flex;gap:26px;color:var(--text-secondary);font-size:13px}
.navlinks a:hover,.textlink:hover{color:var(--accent-light)}
.pill{border:1px solid var(--border);border-radius:999px;padding:6px 11px;color:#c9d1d9;font:11px var(--font-mono);letter-spacing:.04em}
.hero{padding:88px 0 64px;text-align:center;position:relative}
.eyebrow{display:inline-flex;align-items:center;gap:8px;padding:6px 12px;border:1px solid var(--border-accent);border-radius:999px;background:var(--accent-muted);color:var(--accent-light);font:11px var(--font-mono);text-transform:uppercase;letter-spacing:.08em}
.dot{width:7px;height:7px;background:var(--accent);border-radius:50%;box-shadow:0 0 12px var(--accent)}
h1{font:400 clamp(38px,6vw,62px)/1.08 var(--font-display);letter-spacing:-2.5px;margin:24px auto 18px;max-width:850px}
h1 span{background:linear-gradient(90deg,#f5f5f5 10%,#83e6a8 75%);-webkit-background-clip:text;background-clip:text;color:transparent}
.hero p{max-width:650px;margin:0 auto;color:var(--text-secondary);font-size:16px}
.actions{display:flex;justify-content:center;gap:12px;margin-top:28px;flex-wrap:wrap}
.btn{display:inline-flex;align-items:center;gap:9px;border-radius:10px;padding:11px 17px;font-size:13px;font-weight:600;transition:var(--transition-base);border:1px solid var(--border-hover)}
.btn-primary{background:var(--accent-gradient);color:#052012;border-color:transparent;box-shadow:var(--shadow-accent)}
.btn-primary:hover{transform:translateY(-2px);box-shadow:var(--shadow-glow)}
.btn-ghost{background:#ffffff08;color:var(--text-primary)}
.btn-ghost:hover{background:var(--bg-hover);border-color:var(--border-hover)}
.panel{background:linear-gradient(145deg,#121a16e8,#0e1115e8);border:1px solid var(--border);border-radius:20px;box-shadow:var(--shadow-elevated);backdrop-filter:blur(18px)}
.profile-shell{max-width:900px;margin:0 auto 78px;padding:18px}
.windowbar{display:flex;align-items:center;justify-content:space-between;padding:0 3px 14px;border-bottom:1px solid var(--border-subtle);color:var(--text-muted);font:11px var(--font-mono)}
.windowdots{display:flex;gap:6px}.windowdots i{width:7px;height:7px;border-radius:50%;background:#41464d}
.preview{display:grid;grid-template-columns:1.1fr .9fr;gap:18px;padding:20px 4px 4px}
.preview-card{background:#0a0d0c;border:1px solid var(--border-subtle);border-radius:14px;padding:20px;min-height:210px}
.profile-head{display:flex;gap:14px;align-items:center;margin-bottom:18px}
.avatar{width:52px;height:52px;border-radius:16px;background:linear-gradient(135deg,#183b29,#0b1710);border:1px solid #2e754b;display:grid;place-items:center;color:#8cf0ae;font:600 17px var(--font-display)}
.muted{color:var(--text-secondary)}
.mono{font-family:var(--font-mono)}
.tagrow{display:flex;gap:7px;flex-wrap:wrap;margin-top:14px}
.tag{font:10px var(--font-mono);color:#b5eac6;border:1px solid #245338;background:#102319;padding:5px 8px;border-radius:6px}
.mini-title{font:12px var(--font-mono);color:#e6f5eb;margin-bottom:12px}
.bar{height:7px;background:#202a24;border-radius:99px;overflow:hidden;margin:10px 0}
.bar i{display:block;height:100%;background:var(--accent-gradient);border-radius:99px}
.statgrid{display:grid;grid-template-columns:repeat(2,1fr);gap:10px}
.stat{border:1px solid var(--border-subtle);background:#ffffff04;border-radius:10px;padding:12px}
.stat strong{display:block;font:20px var(--font-display);color:var(--accent-light)}
.stat small{color:var(--text-muted);font:10px var(--font-mono)}
section.content{padding:54px 0}
.section-head{display:flex;align-items:end;justify-content:space-between;gap:20px;margin-bottom:24px}
.kicker{font:10px var(--font-mono);text-transform:uppercase;letter-spacing:.13em;color:var(--accent-light)}
h2{font:400 30px/1.2 var(--font-display);letter-spacing:-.8px;margin:8px 0 0}
.section-desc{color:var(--text-secondary);max-width:560px;margin:10px 0 0;font-size:14px}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
.card{padding:19px;border-radius:14px;background:linear-gradient(145deg,#11151a,#0c0e12);border:1px solid var(--border-subtle);box-shadow:var(--shadow-card);transition:var(--transition-base)}
.card:hover{transform:translateY(-3px);border-color:var(--border-accent);box-shadow:var(--shadow-elevated)}
.iconbox{width:35px;height:35px;border-radius:10px;display:grid;place-items:center;background:var(--accent-muted);color:var(--accent-light);font-size:16px;margin-bottom:16px}
h3{font:500 14px var(--font-display);margin:0 0 7px}
.card p{font-size:12px;color:var(--text-secondary);margin:0}
.skills{display:grid;grid-template-columns:repeat(2,1fr);gap:14px}
.skill-card{padding:18px;border:1px solid var(--border-subtle);border-radius:14px;background:#0d1014}
.skill-card h3{color:#e8f4ec;margin-bottom:13px}
.skill-list{display:flex;flex-wrap:wrap;gap:7px}
.skill-list span{padding:6px 9px;border-radius:7px;background:#ffffff08;border:1px solid var(--border-subtle);color:#c9d1d9;font:10px var(--font-mono)}
.project{display:flex;flex-direction:column;min-height:190px}
.project .project-top{display:flex;justify-content:space-between;align-items:center;margin-bottom:16px}
.project .repo{font:10px var(--font-mono);color:var(--accent-light)}
.project .arrow{color:var(--text-muted)}
.project h3{font-size:15px}
.project p{font-size:12px;line-height:1.7}
.project .tagrow{margin-top:auto;padding-top:16px}
.connect{display:grid;grid-template-columns:1.2fr .8fr;gap:16px}
.connect-main{padding:26px}
.connect-main p{color:var(--text-secondary);font-size:13px;max-width:520px}
.contact-links{display:grid;gap:10px}
.contact-link{display:flex;align-items:center;justify-content:space-between;padding:14px 16px;border:1px solid var(--border-subtle);background:#0d1014;border-radius:11px;font-size:12px;transition:var(--transition-fast)}
.contact-link:hover{border-color:var(--border-accent);background:var(--bg-hover)}
footer{border-top:1px solid var(--border-subtle);padding:24px 0 34px;color:var(--text-muted);font:10px var(--font-mono);display:flex;justify-content:space-between;gap:12px}
.fade{animation:slideUp .7s both}
@keyframes slideUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
@keyframes pulse{50%{box-shadow:0 0 0 7px #22c55e0c}}
@media(max-width:760px){.navlinks{display:none}.hero{padding:65px 0 45px}.preview,.connect{grid-template-columns:1fr}.grid{grid-template-columns:1fr 1fr}.section-head{display:block}.skills{grid-template-columns:1fr}}
@media(max-width:480px){.wrap{width:min(100% - 28px,1120px)}h1{letter-spacing:-1.5px}.grid{grid-template-columns:1fr}.profile-shell{padding:12px}.preview-card{padding:15px}.hero p{font-size:14px}footer{display:block;line-height:2.2}}
</style>
</head>
<body>
<div class="wrap">
  <nav>
    <a class="brand" href="#top"><span class="brand-mark">ZM</span><span>zuha<span style="color:var(--accent-light)">maryam</span></span></a>
    <div class="navlinks"><a href="#about">About</a><a href="#skills">Skills</a><a href="#projects">Projects</a><a href="#research">Research</a><a href="#contact">Contact</a></div>
    <a class="pill" href="https://github.com/zuhamaryam" target="_blank" rel="noreferrer">GITHUB ↗</a>
  </nav>

  <header class="hero fade" id="top">
    <div class="eyebrow"><span class="dot"></span> COMPUTER SCIENCE & ENGINEERING</div>
    <h1>Building with <span>Python</span>.<br>Learning through <span>Machine Learning.</span></h1>
    <p>I'm Zuha Maryam, a Computer Science and Engineering student interested in Python development, machine learning, and practical AI solutions.</p>
    <div class="actions">
      <a class="btn btn-primary" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer">Explore my repositories ↗</a>
      <a class="btn btn-ghost" href="#contact">Get in touch</a>
    </div>
  </header>

  <div class="profile-shell panel fade">
    <div class="windowbar"><span class="windowdots"><i></i><i></i><i></i></span><span>github.com / zuhamaryam / README.md</span><span>PROFILE PREVIEW</span></div>
    <div class="preview">
      <div class="preview-card">
        <div class="profile-head"><div class="avatar">ZM</div><div><div style="font:600 17px var(--font-display)">Zuha Maryam</div><div class="muted" style="font-size:11px">Python Developer · ML Enthusiast</div></div></div>
        <div class="mini-title"># About Me</div>
        <p class="muted" style="font-size:12px;margin:0">Final-year CSE student exploring Python, machine learning, data science and computer vision. Interested in building useful technology through experimentation and continuous learning.</p>
        <div class="tagrow"><span class="tag">Python</span><span class="tag">Machine Learning</span><span class="tag">Data Science</span><span class="tag">Computer Vision</span></div>
      </div>
      <div class="preview-card">
        <div class="mini-title"># TECHNICAL FOCUS</div>
        <div class="statgrid">
          <div class="stat"><strong>01</strong><small>PYTHON</small></div>
          <div class="stat"><strong>02</strong><small>MACHINE LEARNING</small></div>
          <div class="stat"><strong>03</strong><small>DATA SCIENCE</small></div>
          <div class="stat"><strong>04</strong><small>COMPUTER VISION</small></div>
        </div>
        <div style="margin-top:17px;font:10px var(--font-mono);color:var(--text-muted)">LEARNING · BUILDING · IMPROVING</div>
        <div class="bar"><i style="width:78%"></i></div>
      </div>
    </div>
  </div>

  <section class="content" id="about">
    <div class="section-head"><div><div class="kicker">01 / INTRODUCTION</div><h2>About Me</h2><p class="section-desc">I enjoy understanding how technology works and applying what I learn to practical projects. My current focus is strengthening my Python, machine learning and problem-solving skills.</p></div><span class="pill">OPEN TO LEARNING</span></div>
    <div class="grid">
      <article class="card"><div class="iconbox">⌘</div><h3>Python Development</h3><p>Writing Python programs, exploring libraries and developing clear, maintainable solutions.</p></article>
      <article class="card"><div class="iconbox">◈</div><h3>Machine Learning</h3><p>Learning data preprocessing, model training, evaluation and practical ML workflows.</p></article>
      <article class="card"><div class="iconbox">▥</div><h3>Problem Solving</h3><p>Building technical foundations through programming practice, experimentation and projects.</p></article>
    </div>
  </section>

  <section class="content" id="skills">
    <div class="section-head"><div><div class="kicker">02 / TOOLKIT</div><h2>Technical Skills</h2><p class="section-desc">Technologies and concepts I use, explore or am currently learning.</p></div></div>
    <div class="skills">
      <div class="skill-card"><h3>Programming</h3><div class="skill-list"><span>Python</span><span>SQL</span><span>JavaScript</span></div></div>
      <div class="skill-card"><h3>Machine Learning & AI</h3><div class="skill-list"><span>Machine Learning</span><span>Deep Learning</span><span>Computer Vision</span><span>Model Evaluation</span></div></div>
      <div class="skill-card"><h3>Python Libraries</h3><div class="skill-list"><span>NumPy</span><span>Pandas</span><span>Matplotlib</span><span>Scikit-learn</span><span>OpenCV</span></div></div>
      <div class="skill-card"><h3>Tools & Development</h3><div class="skill-list"><span>Jupyter Notebook</span><span>Google Colab</span><span>VS Code</span><span>Git</span><span>GitHub</span><span>Flask</span></div></div>
    </div>
  </section>

  <section class="content" id="projects">
    <div class="section-head"><div><div class="kicker">03 / SELECTED WORK</div><h2>Projects</h2><p class="section-desc">A selection of areas represented in my project work. Visit my repositories for the latest code, documentation and updates.</p></div><a class="pill textlink" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer">ALL REPOSITORIES ↗</a></div>
    <div class="grid">
      <a class="card project" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer"><div class="project-top"><span class="repo">RESEARCH / COMPUTER VISION</span><span class="arrow">↗</span></div><h3>Cell Segmentation Research</h3><p>Comparative exploration of Cellpose and StarDist for image-based cell segmentation and model evaluation.</p><div class="tagrow"><span class="tag">Python</span><span class="tag">Jupyter</span><span class="tag">Deep Learning</span></div></a>
      <a class="card project" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer"><div class="project-top"><span class="repo">AI / INTELLIGENT SYSTEMS</span><span class="arrow">↗</span></div><h3>AI-Powered Applications</h3><p>Exploring intelligent applications, automation and practical ways to apply AI concepts.</p><div class="tagrow"><span class="tag">Python</span><span class="tag">AI</span><span class="tag">APIs</span></div></a>
      <a class="card project" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer"><div class="project-top"><span class="repo">DATA / ANALYTICS</span><span class="arrow">↗</span></div><h3>Data Analysis & Experiments</h3><p>Working with datasets, visualizations and experiments to understand patterns and evaluate results.</p><div class="tagrow"><span class="tag">Pandas</span><span class="tag">NumPy</span><span class="tag">Matplotlib</span></div></a>
    </div>
  </section>

  <section class="content" id="research">
    <div class="section-head"><div><div class="kicker">04 / RESEARCH</div><h2>Research & Learning</h2><p class="section-desc">I am interested in research-led learning, careful experimentation and communicating technical findings clearly.</p></div></div>
    <div class="panel" style="padding:22px;display:flex;gap:18px;align-items:flex-start">
      <div class="iconbox" style="flex:none;margin:0">⌁</div><div><h3 style="font-size:15px">Cellpose vs. StarDist</h3><p class="muted" style="font-size:12px;margin:0">Research focus: cell segmentation using deep-learning-based computer vision models. Add the final paper PDF, notebook, datasets or dataset references, evaluation metrics and result visualizations to the relevant GitHub repository when ready.</p><div class="tagrow"><span class="tag">Research</span><span class="tag">Python</span><span class="tag">Computer Vision</span></div></div>
    </div>
  </section>

  <section class="content" id="contact">
    <div class="section-head"><div><div class="kicker">05 / CONNECT</div><h2>Let's connect.</h2><p class="section-desc">For technical discussions, collaboration and learning opportunities, feel free to reach out.</p></div></div>
    <div class="connect">
      <div class="panel connect-main"><div class="kicker">CURRENT GOAL</div><h2 style="font-size:25px;margin-top:12px">Growing into an AI/ML Engineer.</h2><p>Building strong foundations in Python, machine learning and data science, one project and experiment at a time.</p><a class="btn btn-primary" href="https://github.com/zuhamaryam?tab=repositories" target="_blank" rel="noreferrer">View GitHub work ↗</a></div>
      <div class="contact-links">
        <a class="contact-link" href="mailto:zuhamaryam676@gmail.com"><span>✉ &nbsp; Email</span><span>↗</span></a>
        <a class="contact-link" href="https://github.com/zuhamaryam" target="_blank" rel="noreferrer"><span>⌘ &nbsp; GitHub</span><span>↗</span></a>
        <a class="contact-link" href="https://www.linkedin.com/" target="_blank" rel="noreferrer"><span>in &nbsp; LinkedIn — add profile URL</span><span>↗</span></a>
      </div>
    </div>
  </section>
  <footer><span>© 2026 Zuha Maryam · Python / Machine Learning</span><span>LEARN · BUILD · ITERATE</span></footer>
</div>
</body>
</html>'''
path = Path("/mnt/data/zuha_github_profile.html")
path.write_text(html, encoding="utf-8")
print(f"Created {path} ({path.stat().st_size:,} bytes)")
