<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Nafis Mufadhal · Data, Systems and Web</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500;12..96,700;12..96,800&family=Instrument+Sans:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#F6F7FB;--surface:#FFFFFF;--ink:#1B1D2A;--muted:#5B6076;--line:#DFE2EE;
  --accent:#4F46E5;--violet:#8B5CF6;--cyan:#06B6D4;--soft:#ECEBFD;
  --display:"Bricolage Grotesque","Trebuchet MS",system-ui,sans-serif;
  --body:"Instrument Sans",system-ui,-apple-system,"Segoe UI",sans-serif;
  color-scheme:light;
  box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){--bg:#0E1018;--surface:#161926;--ink:#EDEEF6;--muted:#9A9FB8;--line:#262A3C;--accent:#A5A0FF;--soft:#1E2036;color-scheme:dark}
}
:root[data-theme="dark"]{--bg:#0E1018;--surface:#161926;--ink:#EDEEF6;--muted:#9A9FB8;--line:#262A3C;--accent:#A5A0FF;--soft:#1E2036;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px);scroll-behavior:smooth}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:400 1.0625rem/1.65 var(--body);-webkit-font-smoothing:antialiased}
a{color:inherit}
:focus-visible{outline:3px solid var(--violet);outline-offset:3px;border-radius:6px}
.wrap{max-width:1080px;margin:0 auto;padding:0 clamp(1.25rem,5vw,2.5rem)}
h1,h2,h3{font-family:var(--display);margin:0;letter-spacing:-.02em;line-height:1.05}

/* top bar */
.top{display:flex;justify-content:space-between;align-items:center;padding:1.5rem 0}
.mark{font:800 1.15rem var(--display);text-decoration:none;display:flex;align-items:center;gap:.6rem}
.mark i{width:14px;height:14px;border-radius:50%;background:conic-gradient(var(--accent),var(--violet),var(--cyan),var(--accent))}
.top nav{display:flex;gap:1.5rem;font-size:.95rem;font-weight:500}
.top nav a{text-decoration:none;color:var(--muted);transition:color .2s}
.top nav a:hover{color:var(--ink)}
@media(max-width:620px){.top nav a:not(.hire){display:none}}
.hire{color:var(--ink)!important;border-bottom:2px solid var(--cyan)}

/* hero */
.hero{display:grid;grid-template-columns:1.05fr .95fr;gap:clamp(2rem,5vw,4rem);align-items:center;padding:clamp(2.5rem,7vw,5.5rem) 0 clamp(3rem,7vw,5.5rem)}
@media(max-width:860px){.hero{grid-template-columns:1fr}}
.status{display:inline-flex;align-items:center;gap:.55rem;padding:.35rem .9rem;border:1px solid var(--line);border-radius:99px;background:var(--surface);font-size:.9rem;font-weight:500;margin-bottom:1.5rem}
.status b{width:8px;height:8px;border-radius:50%;background:#22C55E;box-shadow:0 0 0 4px rgba(34,197,94,.18)}
h1{font-size:clamp(3rem,8.5vw,6.2rem);font-weight:800}
h1 span{display:block;background:linear-gradient(90deg,var(--accent),var(--violet) 55%,var(--cyan));-webkit-background-clip:text;background-clip:text;color:transparent}
.lead{font-size:clamp(1.15rem,2.2vw,1.4rem);line-height:1.5;color:var(--muted);max-width:30em;margin:1.5rem 0 2rem}
.lead strong{color:var(--ink);font-weight:600}
.cta{display:flex;flex-wrap:wrap;gap:.8rem}
.btn{display:inline-block;padding:.85rem 1.4rem;border-radius:12px;font-weight:600;text-decoration:none;border:1.5px solid var(--line);background:var(--surface);transition:transform .2s,border-color .2s}
.btn:hover{transform:translateY(-2px);border-color:var(--accent)}
.btn.main{background:var(--accent);border-color:var(--accent);color:#fff}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]) .btn.main{color:#10111C}}

/* data moment */
.chart{background:var(--surface);border:1px solid var(--line);border-radius:22px;padding:1.25rem 1.25rem 1rem;box-shadow:0 30px 60px -35px rgba(79,70,229,.45)}
.chart header{display:flex;justify-content:space-between;align-items:center;gap:1rem;margin-bottom:.5rem}
.chart header p{margin:0;font-weight:600;font-size:.95rem}
.toggle{display:flex;background:var(--soft);border-radius:99px;padding:3px}
.toggle button{font:600 .82rem var(--body);border:0;background:transparent;color:var(--muted);padding:.4rem .85rem;border-radius:99px;cursor:pointer;transition:background .25s,color .25s}
.toggle button[aria-pressed="true"]{background:var(--accent);color:#fff}
@media(prefers-color-scheme:dark){:root:not([data-theme="light"]) .toggle button[aria-pressed="true"]{color:#10111C}}
svg{display:block;width:100%;height:auto;overflow:visible}
.bar{transition:transform 1.1s cubic-bezier(.2,.9,.25,1.05),opacity .8s;transform-box:fill-box;transform-origin:center}
.trend{fill:none;stroke:var(--cyan);stroke-width:3;stroke-linecap:round;stroke-dasharray:520;transition:stroke-dashoffset 1.4s ease .5s}
.axis{stroke:var(--line);stroke-width:1}
.chart small{display:block;color:var(--muted);font-size:.88rem;margin-top:.4rem;min-height:1.4em}

/* sections */
section{padding:clamp(3rem,7vw,5rem) 0;border-top:1px solid var(--line)}
.split{display:grid;grid-template-columns:.8fr 1.2fr;gap:clamp(1.5rem,5vw,4rem)}
@media(max-width:820px){.split{grid-template-columns:1fr}}
h2{font-size:clamp(2rem,4.5vw,3rem);font-weight:700}
.about p{margin:0 0 1.25rem;max-width:36em}
.facts{list-style:none;margin:2rem 0 0;padding:0;display:grid;gap:0}
.facts li{display:grid;grid-template-columns:7.5rem 1fr;gap:1rem;padding:1rem 0;border-top:1px solid var(--line)}
.facts li:last-child{border-bottom:1px solid var(--line)}
.facts b{font:700 1.7rem var(--display);color:var(--accent);line-height:1.1}
.facts span{color:var(--muted);align-self:center}

.roles{list-style:none;margin:0;padding:0}
.roles li{display:grid;grid-template-columns:1fr 1.4fr;gap:1.5rem;padding:1.6rem 0;border-top:1px solid var(--line);transition:padding-left .25s}
.roles li:last-child{border-bottom:1px solid var(--line)}
.roles li:hover{padding-left:.75rem}
.roles h3{font-size:1.5rem;font-weight:700}
.roles p{margin:0;color:var(--muted)}
@media(max-width:700px){.roles li{grid-template-columns:1fr;gap:.4rem}}

.stack{display:grid;gap:1.4rem}
.stack div{display:grid;grid-template-columns:9rem 1fr;gap:1rem;align-items:baseline}
@media(max-width:620px){.stack div{grid-template-columns:1fr;gap:.5rem}}
.stack h3{font-size:1.1rem;font-weight:700}
.chips{display:flex;flex-wrap:wrap;gap:.5rem}
.chips span{padding:.4rem .9rem;border-radius:99px;background:var(--surface);border:1px solid var(--line);font-weight:500;font-size:.95rem;transition:background .2s,border-color .2s,color .2s}
.chips span:hover{background:var(--accent);border-color:var(--accent);color:#fff}

.work{display:grid;grid-template-columns:repeat(3,1fr);gap:1.25rem}
@media(max-width:860px){.work{grid-template-columns:1fr}}
.proj{position:relative;display:flex;flex-direction:column;gap:.9rem;padding:1.6rem;border-radius:20px;background:var(--surface);border:1px solid var(--line);text-decoration:none;overflow:hidden;transition:transform .25s,border-color .25s}
.proj::before{content:"";position:absolute;inset:0 0 auto 0;height:5px;background:linear-gradient(90deg,var(--accent),var(--violet),var(--cyan))}
.proj:nth-child(2)::before{background:linear-gradient(90deg,var(--violet),var(--cyan))}
.proj:nth-child(3)::before{background:linear-gradient(90deg,var(--cyan),var(--accent))}
.proj:hover{transform:translateY(-4px);border-color:var(--accent)}
.proj h3{font-size:1.45rem;font-weight:700;margin-top:.4rem}
.proj p{margin:0;color:var(--muted);flex:1}
.proj em{font-style:normal;font-weight:600;color:var(--accent)}

/* contact */
.contact{text-align:left}
.contact h2{font-size:clamp(2.4rem,6vw,4.4rem);max-width:12em}
.contact p{color:var(--muted);max-width:32em;margin:1.2rem 0 2rem}
footer{padding:2rem 0 3rem;color:var(--muted);font-size:.92rem;border-top:1px solid var(--line)}

@media(prefers-reduced-motion:reduce){*{transition:none!important;scroll-behavior:auto!important}}
</style>
</head>
<body>
<div class="wrap">
  <div class="top">
    <a class="mark" href="#top"><i></i>Nafis Mufadhal</a>
    <nav>
      <a href="#about">About</a><a href="#do">What I do</a><a href="#work">Work</a>
      <a class="hire" href="#contact">Get in touch</a>
    </nav>
  </div>

  <main id="top">
    <div class="hero">
      <div>
        <div class="status"><b></b>Open to work</div>
        <h1>Nafis<span>Mufadhal</span></h1>
        <p class="lead">I turn messy operational data into something a team can actually use. <strong>Data analyst, data engineer, systems analyst</strong> and web developer.</p>
        <div class="cta">
          <a class="btn main" href="#work">See selected work</a>
          <a class="btn" href="mailto:nafismufadhal21@gmail.com">Send an email</a>
        </div>
      </div>

      <div class="chart" aria-label="A bar chart that moves between scattered raw data and a tidy trend">
        <header>
          <p>Quarterly requests resolved</p>
          <div class="toggle" role="group" aria-label="Data state">
            <button id="raw" aria-pressed="false">Raw</button>
            <button id="clean" aria-pressed="true">Cleaned</button>
          </div>
        </header>
        <svg id="svg" viewBox="0 0 420 250" role="img" aria-hidden="true">
          <defs>
            <linearGradient id="g" x1="0" y1="1" x2="0" y2="0">
              <stop offset="0" stop-color="#4F46E5"/><stop offset=".6" stop-color="#8B5CF6"/><stop offset="1" stop-color="#06B6D4"/>
            </linearGradient>
          </defs>
          <line class="axis" x1="0" y1="220" x2="420" y2="220"/>
          <g id="bars"></g>
          <path id="trend" class="trend" d=""/>
        </svg>
        <small id="cap">Cleaned, joined and ready to read.</small>
      </div>
    </div>

    <section id="about" class="about">
      <div class="split">
        <h2>Analysis, data and web systems in one person</h2>
        <div>
          <p>I’m an Information Systems graduate student at Universitas Diponegoro, with a background in Informatics Engineering. I work across analysis, data and web systems, and I like the part where a pile of records becomes a decision someone can make.</p>
          <p>I’m open to roles in data analysis, data engineering, IT, project management and operations.</p>
          <ul class="facts">
            <li><b>3.57</b><span>GPA in Informatics Engineering</span></li>
            <li><b>n = 267</b><span>Thesis combining DeLone &amp; McLean, UTAUT2 and Affordance models with PLS-SEM. Manuscript submitted to JUTIF (SINTA 2).</span></li>
            <li><b>82</b><span>Members led as Chair of HMIF, covering strategy and day-to-day operations.</span></li>
            <li><b>Cloud</b><span>Bangkit Academy x Google Cloud, Cloud Computing track.</span></li>
          </ul>
        </div>
      </div>
    </section>

    <section id="do">
      <div class="split">
        <h2>What I do</h2>
        <ul class="roles">
          <li><h3>Data Analyst</h3><p>Exploratory analysis, statistical modeling with PLS-SEM, dashboards and reports that a decision-maker can read.</p></li>
          <li><h3>Data Engineer</h3><p>Collection, cleaning, and cloud-based storage and processing on Google Cloud.</p></li>
          <li><h3>Systems Analyst</h3><p>Requirements, system modeling and IT governance with COBIT and ISO/IEC 38500.</p></li>
          <li><h3>Web Developer</h3><p>Full-stack apps from MySQL design through Laravel, PHP and JavaScript interfaces.</p></li>
        </ul>
      </div>
    </section>

    <section id="tech">
      <div class="split">
        <h2>Tools I work with</h2>
        <div class="stack">
          <div><h3>Analysis</h3><div class="chips"><span>Python</span><span>Pandas</span><span>Jupyter</span><span>Power BI</span><span>SmartPLS</span></div></div>
          <div><h3>Data and cloud</h3><div class="chips"><span>Google Cloud</span><span>MySQL</span><span>PostgreSQL</span><span>Docker</span></div></div>
          <div><h3>Web</h3><div class="chips"><span>Laravel</span><span>PHP</span><span>JavaScript</span><span>TypeScript</span><span>Git</span></div></div>
        </div>
      </div>
    </section>

    <section id="work">
      <h2 style="margin-bottom:2rem">Selected work</h2>
      <div class="work">
        <a class="proj" href="https://github.com/nafissmf/Sistem-Kependudukan-Ampel">
          <h3>Sistem Kependudukan Ampel</h3>
          <p>E-government system for population records: Laravel 12, MySQL, role-based access, GIS, QR verification and an analytics dashboard.</p>
          <em>View repository →</em>
        </a>
        <a class="proj" href="https://github.com/nafissmf/Pencatatan-Penduduk-Barcode">
          <h3>Pencatatan Penduduk</h3>
          <p>Population registration and verification with barcodes, built with Laravel and PHP.</p>
          <em>View repository →</em>
        </a>
        <a class="proj" href="https://github.com/nafissmf/RoDex">
          <h3>RoDex</h3>
          <p>Mobile app that detects and reports road damage from photos, with location tagging.</p>
          <em>View repository →</em>
        </a>
      </div>
    </section>

    <section id="contact" class="contact">
      <h2>Have messy data or a system that needs shaping?</h2>
      <p>I’m open to data, IT, project and operations roles. Write to me and I’ll reply.</p>
      <div class="cta">
        <a class="btn main" href="mailto:nafismufadhal21@gmail.com">nafismufadhal21@gmail.com</a>
        <a class="btn" href="https://www.linkedin.com/in/nafissmf">LinkedIn</a>
        <a class="btn" href="https://orcid.org/0009-0003-3306-1512">ORCID</a>
        <a class="btn" href="https://github.com/nafissmf">GitHub</a>
      </div>
    </section>
  </main>

  <footer>© 2026 Nafis Mufadhal. Semarang, Indonesia.</footer>
</div>

<script>
(function(){
  var NS="http://www.w3.org/2000/svg";
  var vals=[48,62,55,78,70,92,86,110,104,132,128,160];
  var bars=document.getElementById("bars"), trend=document.getElementById("trend");
  var cap=document.getElementById("cap"), bRaw=document.getElementById("raw"), bClean=document.getElementById("clean");
  var W=24, GAP=11, X0=6, BASE=220, items=[];
  var seed=7; function rnd(){seed=(seed*9301+49297)%233280;return seed/233280}
  var pts=[];
  vals.forEach(function(v,i){
    var x=X0+i*(W+GAP), r=document.createElementNS(NS,"rect");
    r.setAttribute("x",x);r.setAttribute("y",BASE-v);r.setAttribute("width",W);r.setAttribute("height",v);
    r.setAttribute("rx",6);r.setAttribute("fill","url(#g)");r.setAttribute("class","bar");
    bars.appendChild(r);
    items.push({el:r,dx:(rnd()-.5)*90,dy:-(rnd()*60)+10,rot:(rnd()-.5)*80,op:.35+rnd()*.35});
    pts.push([x+W/2,BASE-v-10]);
  });
  var d="M"+pts.map(function(p){return p[0]+" "+p[1]}).join(" L");
  trend.setAttribute("d",d);
  function set(clean){
    items.forEach(function(it){
      it.el.style.transform=clean?"none":"translate("+it.dx+"px,"+it.dy+"px) rotate("+it.rot+"deg)";
      it.el.style.opacity=clean?1:it.op;
    });
    trend.style.strokeDashoffset=clean?0:520;
    bClean.setAttribute("aria-pressed",clean);bRaw.setAttribute("aria-pressed",!clean);
    cap.textContent=clean?"Cleaned, joined and ready to read.":"Duplicates, gaps and typos. Hard to read.";
  }
  bRaw.addEventListener("click",function(){set(false)});
  bClean.addEventListener("click",function(){set(true)});
  set(false);
  setTimeout(function(){set(true)},700);
})();
</script>
</body>
</html>
