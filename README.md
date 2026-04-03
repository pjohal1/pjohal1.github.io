# pjohal1.github.io
notes and stuff 

<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=DM+Mono:wght@400;500&family=Instrument+Sans:wght@400;500;600&display=swap');
  :root {
    --dash-bg: var(--color-background-tertiary);
    --card: var(--color-background-primary);
    --card-border: var(--color-border-tertiary);
    --text: var(--color-text-primary);
    --muted: var(--color-text-secondary);
    --hint: var(--color-text-tertiary);
    --accent: #534AB7;
    --accent-light: #EEEDFE;
    --accent-text: #3C3489;
    --green: #1D9E75;
    --green-light: #E1F5EE;
    --amber: #BA7517;
    --amber-light: #FAEEDA;
    --coral: #993C1D;
    --coral-light: #FAECE7;
    --sans: 'Instrument Sans', sans-serif;
    --serif: 'DM Serif Display', serif;
    --mono: 'DM Mono', monospace;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: var(--sans); background: var(--dash-bg); color: var(--text); min-height: 100vh; }
  .layout { display: grid; grid-template-columns: 240px 1fr; min-height: 100vh; }
  .sidebar { background: var(--card); border-right: 0.5px solid var(--card-border); padding: 0; position: sticky; top: 0; height: 100vh; overflow-y: auto; display: flex; flex-direction: column; }
  .sidebar-header { padding: 20px 18px 14px; border-bottom: 0.5px solid var(--card-border); }
  .sidebar-header .module-tag { font-family: var(--mono); font-size: 10px; font-weight: 500; color: var(--accent); background: var(--accent-light); padding: 2px 7px; border-radius: 4px; display: inline-block; margin-bottom: 6px; letter-spacing: 0.04em; }
  .sidebar-header h1 { font-family: var(--serif); font-size: 17px; color: var(--text); line-height: 1.25; font-weight: 400; }
  .sidebar-search { padding: 10px 12px; border-bottom: 0.5px solid var(--card-border); }
  .sidebar-search input { width: 100%; padding: 6px 10px; border-radius: 6px; border: 0.5px solid var(--card-border); background: var(--color-background-secondary); font-size: 12px; font-family: var(--sans); color: var(--text); outline: none; }
  .sidebar-search input:focus { border-color: var(--accent); }
  .nav-section { padding: 8px 0; border-bottom: 0.5px solid var(--card-border); }
  .nav-section-title { font-size: 10px; font-weight: 600; color: var(--hint); letter-spacing: 0.06em; text-transform: uppercase; padding: 4px 18px 4px; }
  .nav-item { display: flex; align-items: center; gap: 8px; padding: 7px 18px; cursor: pointer; font-size: 13px; color: var(--muted); transition: all 0.12s; border-left: 2px solid transparent; }
  .nav-item:hover { color: var(--text); background: var(--color-background-secondary); }
  .nav-item.active { color: var(--accent-text); background: var(--accent-light); border-left-color: var(--accent); font-weight: 500; }
  .nav-item .dot { width: 7px; height: 7px; border-radius: 50%; flex-shrink: 0; }
  .nav-item .check { width: 14px; height: 14px; border-radius: 50%; border: 1.5px solid var(--card-border); display: flex; align-items: center; justify-content: center; flex-shrink: 0; font-size: 9px; cursor: pointer; transition: all 0.15s; }
  .nav-item .check.done { background: var(--green); border-color: var(--green); color: white; }
  .main { padding: 28px 32px 48px; max-width: 900px; }
  .page { display: none; }
  .page.active { display: block; }
  .page-title { font-family: var(--serif); font-size: 30px; font-weight: 400; margin-bottom: 4px; }
  .page-sub { font-size: 13px; color: var(--muted); margin-bottom: 24px; }
  .grid-2 { display: grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap: 14px; margin-bottom: 20px; }
  .grid-3 { display: grid; grid-template-columns: repeat(3, minmax(0,1fr)); gap: 12px; margin-bottom: 20px; }
  .stat-card { background: var(--color-background-secondary); border-radius: 10px; padding: 14px 16px; }
  .stat-card .label { font-size: 11px; color: var(--muted); margin-bottom: 4px; font-weight: 500; letter-spacing: 0.03em; }
  .stat-card .value { font-size: 26px; font-weight: 500; font-family: var(--mono); }
  .stat-card .sub { font-size: 11px; color: var(--hint); margin-top: 2px; }
  .card { background: var(--card); border: 0.5px solid var(--card-border); border-radius: 12px; padding: 18px 20px; margin-bottom: 14px; }
  .card-title { font-size: 13px; font-weight: 600; margin-bottom: 12px; display: flex; align-items: center; gap: 8px; }
  .progress-row { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; font-size: 12px; }
  .progress-row .label { width: 160px; flex-shrink: 0; color: var(--muted); }
  .progress-bar { flex: 1; height: 5px; background: var(--color-background-secondary); border-radius: 3px; overflow: hidden; }
  .progress-fill { height: 100%; border-radius: 3px; transition: width 0.5s ease; }
  .progress-row .pct { width: 30px; text-align: right; color: var(--hint); font-family: var(--mono); font-size: 11px; }
  .topic-grid { display: grid; grid-template-columns: repeat(2, minmax(0,1fr)); gap: 10px; }
  .topic-card { background: var(--card); border: 0.5px solid var(--card-border); border-radius: 10px; padding: 14px 16px; cursor: pointer; transition: all 0.15s; position: relative; }
  .topic-card:hover { border-color: var(--accent); box-shadow: 0 0 0 2px color-mix(in srgb, var(--accent) 12%, transparent); }
  .topic-card.complete { border-color: var(--green); }
  .topic-card .tc-num { font-family: var(--mono); font-size: 10px; color: var(--hint); margin-bottom: 4px; }
  .topic-card .tc-name { font-size: 13px; font-weight: 500; margin-bottom: 6px; line-height: 1.3; }
  .topic-card .tc-tags { display: flex; gap: 4px; flex-wrap: wrap; }
  .tag { font-size: 10px; padding: 2px 7px; border-radius: 4px; font-weight: 500; }
  .tag-theory { background: var(--accent-light); color: var(--accent-text); }
  .tag-exam { background: var(--coral-light); color: var(--coral); }
  .tag-r { background: var(--green-light); color: var(--green); }
  .tag-key { background: var(--amber-light); color: var(--amber); }
  .tc-status { position: absolute; top: 12px; right: 12px; width: 18px; height: 18px; border-radius: 50%; border: 1.5px solid var(--card-border); display: flex; align-items: center; justify-content: center; font-size: 10px; cursor: pointer; transition: all 0.15s; }
  .tc-status.done { background: var(--green); border-color: var(--green); color: white; }
  .exam-item { border: 0.5px solid var(--card-border); border-radius: 10px; padding: 16px 18px; margin-bottom: 12px; }
  .exam-item .q-header { display: flex; align-items: center; gap: 8px; margin-bottom: 10px; }
  .exam-item .q-num { font-family: var(--mono); font-size: 11px; color: var(--hint); }
  .exam-item .q-marks { margin-left: auto; font-family: var(--mono); font-size: 11px; color: var(--muted); background: var(--color-background-secondary); padding: 2px 8px; border-radius: 4px; }
  .exam-item .q-text { font-size: 13px; line-height: 1.6; margin-bottom: 12px; color: var(--text); }
  .exam-item .q-text .math { font-family: var(--mono); background: var(--color-background-secondary); padding: 0 4px; border-radius: 3px; font-size: 12px; }
  .reveal-btn { font-size: 12px; color: var(--accent-text); cursor: pointer; background: var(--accent-light); border: none; padding: 5px 12px; border-radius: 6px; font-family: var(--sans); font-weight: 500; transition: all 0.12s; }
  .reveal-btn:hover { background: #CECBF6; }
  .solution { display: none; margin-top: 12px; padding: 12px 14px; background: var(--green-light); border-radius: 8px; font-size: 12px; line-height: 1.7; color: #085041; border-left: 3px solid var(--green); }
  .solution.visible { display: block; }
  .ai-box { border: 0.5px solid var(--card-border); border-radius: 10px; overflow: hidden; margin-top: 16px; }
  .ai-input-row { display: flex; gap: 0; }
  .ai-input-row textarea { flex: 1; border: none; outline: none; padding: 12px 14px; font-size: 13px; font-family: var(--sans); background: var(--card); resize: none; color: var(--text); min-height: 60px; }
  .ai-send { background: var(--accent); color: white; border: none; padding: 0 16px; cursor: pointer; font-family: var(--sans); font-size: 12px; font-weight: 500; transition: background 0.12s; }
  .ai-send:hover { background: var(--accent-text); }
  .ai-response { padding: 14px; background: var(--color-background-secondary); font-size: 13px; line-height: 1.7; display: none; border-top: 0.5px solid var(--card-border); max-height: 320px; overflow-y: auto; }
  .ai-response.visible { display: block; }
  .ai-loading { color: var(--hint); font-style: italic; }
  .formula-card { background: var(--card); border: 0.5px solid var(--card-border); border-radius: 10px; padding: 14px 16px; margin-bottom: 10px; }
  .formula-card .f-name { font-size: 12px; font-weight: 600; color: var(--muted); margin-bottom: 6px; text-transform: uppercase; letter-spacing: 0.04em; }
  .formula-card .f-math { font-family: var(--mono); font-size: 13px; background: var(--color-background-secondary); padding: 8px 12px; border-radius: 6px; line-height: 1.8; }
  .formula-card .f-note { font-size: 12px; color: var(--muted); margin-top: 6px; line-height: 1.5; }
  .flashcard-area { perspective: 800px; margin-bottom: 20px; }
  .flashcard { width: 100%; height: 180px; cursor: pointer; position: relative; transform-style: preserve-3d; transition: transform 0.5s; }
  .flashcard.flipped { transform: rotateY(180deg); }
  .flashcard-face { position: absolute; inset: 0; backface-visibility: hidden; border-radius: 12px; border: 0.5px solid var(--card-border); display: flex; align-items: center; justify-content: center; padding: 24px; text-align: center; }
  .flashcard-front { background: var(--card); }
  .flashcard-back { background: var(--accent-light); transform: rotateY(180deg); }
  .flashcard-front .q { font-size: 16px; font-weight: 500; line-height: 1.4; }
  .flashcard-back .a { font-size: 14px; line-height: 1.6; color: var(--accent-text); font-weight: 400; }
  .fc-nav { display: flex; align-items: center; justify-content: space-between; font-size: 13px; color: var(--muted); }
  .fc-nav button { background: var(--color-background-secondary); border: 0.5px solid var(--card-border); border-radius: 6px; padding: 6px 14px; cursor: pointer; font-family: var(--sans); font-size: 12px; transition: all 0.12s; color: var(--text); }
  .fc-nav button:hover { background: var(--card); }
  .week-chip { display: inline-flex; align-items: center; gap: 5px; padding: 4px 10px; border-radius: 20px; font-size: 11px; font-weight: 500; cursor: pointer; transition: all 0.12s; border: 0.5px solid transparent; margin: 3px; }
  .week-chip:hover { border-color: var(--accent); }
  .week-chip.wk-done { background: var(--green-light); color: var(--green); }
  .week-chip.wk-progress { background: var(--amber-light); color: var(--amber); }
  .week-chip.wk-todo { background: var(--color-background-secondary); color: var(--muted); }
  .heatmap { display: grid; grid-template-columns: repeat(10, 1fr); gap: 4px; }
  .heat-cell { height: 24px; border-radius: 4px; cursor: pointer; transition: all 0.15s; position: relative; }
  .heat-cell:hover { transform: scale(1.15); }
  .heat-0 { background: var(--color-background-secondary); }
  .heat-1 { background: #9FE1CB; }
  .heat-2 { background: #5DCAA5; }
  .heat-3 { background: #1D9E75; }
  .heat-4 { background: #0F6E56; }
  .divider { height: 0.5px; background: var(--card-border); margin: 20px 0; }
  .badge { display: inline-block; font-size: 10px; padding: 1px 6px; border-radius: 4px; font-weight: 500; }
  .badge-new { background: var(--coral-light); color: var(--coral); }
</style>

<div class="layout">
  <aside class="sidebar">
    <div class="sidebar-header">
      <div class="module-tag">MATH3030</div>
      <h1>Multivariate<br>Analysis</h1>
    </div>
    <div class="sidebar-search">
      <input type="text" placeholder="Search topics..." id="search-inp" oninput="filterNav(this.value)">
    </div>
    <div class="nav-section">
      <div class="nav-section-title">Overview</div>
      <div class="nav-item active" onclick="goto('dashboard')">
        <span style="font-size:14px">◻</span> Dashboard
      </div>
      <div class="nav-item" onclick="goto('tracker')">
        <span style="font-size:14px">◈</span> Topic tracker
      </div>
      <div class="nav-item" onclick="goto('formulas')">
        <span style="font-size:14px">∑</span> Formula sheet
      </div>
    </div>
    <div class="nav-section" id="topics-nav">
      <div class="nav-section-title">Core topics</div>
      <div class="nav-item" onclick="goto('pca')">
        <div class="dot" style="background:#534AB7"></div>
        <span style="flex:1">PCA</span>
        <div class="check" id="chk-pca" onclick="event.stopPropagation();toggle('pca')"></div>
      </div>
      <div class="nav-item" onclick="goto('svd')">
        <div class="dot" style="background:#1D9E75"></div>
        <span style="flex:1">SVD</span>
        <div class="check" id="chk-svd" onclick="event.stopPropagation();toggle('svd')"></div>
      </div>
      <div class="nav-item" onclick="goto('mvn')">
        <div class="dot" style="background:#D85A30"></div>
        <span style="flex:1">Multivariate Normal</span>
        <div class="check" id="chk-mvn" onclick="event.stopPropagation();toggle('mvn')"></div>
      </div>
      <div class="nav-item" onclick="goto('hotelling')">
        <div class="dot" style="background:#BA7517"></div>
        <span style="flex:1">Hotelling's T²</span>
        <div class="check" id="chk-hotelling" onclick="event.stopPropagation();toggle('hotelling')"></div>
      </div>
      <div class="nav-item" onclick="goto('lda')">
        <div class="dot" style="background:#D4537E"></div>
        <span style="flex:1">Discriminant Analysis</span>
        <div class="check" id="chk-lda" onclick="event.stopPropagation();toggle('lda')"></div>
      </div>
      <div class="nav-item" onclick="goto('mds')">
        <div class="dot" style="background:#378ADD"></div>
        <span style="flex:1">MDS</span>
        <div class="check" id="chk-mds" onclick="event.stopPropagation();toggle('mds')"></div>
      </div>
      <div class="nav-item" onclick="goto('cluster')">
        <div class="dot" style="background:#639922"></div>
        <span style="flex:1">Cluster Analysis</span>
        <div class="check" id="chk-cluster" onclick="event.stopPropagation();toggle('cluster')"></div>
      </div>
      <div class="nav-item" onclick="goto('cca')">
        <div class="dot" style="background:#5DCAA5"></div>
        <span style="flex:1">Canonical Correlation</span>
        <div class="check" id="chk-cca" onclick="event.stopPropagation();toggle('cca')"></div>
      </div>
    </div>
    <div class="nav-section">
      <div class="nav-section-title">Exam prep</div>
      <div class="nav-item" onclick="goto('exam24')">
        <span style="font-size:12px">📄</span> Exam 2024–25 <span class="badge badge-new" style="margin-left:auto">new</span>
      </div>
      <div class="nav-item" onclick="goto('exam23')">
        <span style="font-size:12px">📄</span> Exam 2023–24
      </div>
      <div class="nav-item" onclick="goto('flashcards')">
        <span style="font-size:12px">🃏</span> Flashcards
      </div>
      <div class="nav-item" onclick="goto('askai')">
        <span style="font-size:12px">✦</span> Ask AI
      </div>
    </div>
  </aside>

  <main class="main" id="main-scroll">
    <!-- DASHBOARD -->
    <div class="page active" id="page-dashboard">
      <div class="page-title">Dashboard</div>
      <div class="page-sub">Spring 2024/25 · Prof. Richard Wilkinson · 20 credits</div>
      <div class="grid-3">
        <div class="stat-card">
          <div class="label">Topics mastered</div>
          <div class="value" id="stat-done">0/10</div>
          <div class="sub">mark complete in sidebar</div>
        </div>
        <div class="stat-card">
          <div class="label">Exam coverage</div>
          <div class="value">3</div>
          <div class="sub">past papers available</div>
        </div>
        <div class="stat-card">
          <div class="label">Exam weight</div>
          <div class="value">80%</div>
          <div class="sub">3 hour written exam</div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Topic progress</div>
        <div id="progress-rows"></div>
      </div>
      <div class="card">
        <div class="card-title">Syllabus weeks</div>
        <div style="display:flex;flex-wrap:wrap;margin:-3px">
          <div class="week-chip wk-done" onclick="goto('pca')">Wk 1 · Intro & Linear Algebra</div>
          <div class="week-chip wk-done" onclick="goto('pca')">Wk 2 · PCA I</div>
          <div class="week-chip wk-progress" onclick="goto('pca')">Wk 3 · PCA II + SVD</div>
          <div class="week-chip wk-progress" onclick="goto('cca')">Wk 4 · Canonical Correlation</div>
          <div class="week-chip wk-todo" onclick="goto('mds')">Wk 5 · MDS</div>
          <div class="week-chip wk-todo" onclick="goto('mvn')">Wk 6 · MVN distribution</div>
          <div class="week-chip wk-todo" onclick="goto('hotelling')">Wk 7 · Wishart + Hotelling</div>
          <div class="week-chip wk-todo" onclick="goto('mvn')">Wk 8 · Inference (1 & 2 samples)</div>
          <div class="week-chip wk-todo" onclick="goto('lda')">Wk 9 · Discriminant Analysis</div>
          <div class="week-chip wk-todo" onclick="goto('cluster')">Wk 10 · Cluster Analysis</div>
        </div>
        <div style="display:flex;gap:14px;margin-top:12px;font-size:11px;color:var(--muted)">
          <span><span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:var(--green-light);border:1px solid var(--green);margin-right:4px"></span>Done</span>
          <span><span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:var(--amber-light);border:1px solid var(--amber);margin-right:4px"></span>In progress</span>
          <span><span style="display:inline-block;width:10px;height:10px;border-radius:50%;background:var(--color-background-secondary);border:1px solid var(--card-border);margin-right:4px"></span>Upcoming</span>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Assessment</div>
        <div style="font-size:13px;line-height:1.8;color:var(--muted)">
          <div style="display:flex;justify-content:space-between;padding:6px 0;border-bottom:0.5px solid var(--card-border)"><span>3-hour written examination</span><span style="font-family:var(--mono);color:var(--text)">80%</span></div>
          <div style="display:flex;justify-content:space-between;padding:6px 0;border-bottom:0.5px solid var(--card-border)"><span>Coursework / R project report</span><span style="font-family:var(--mono);color:var(--text)">20%</span></div>
          <div style="padding:8px 0 2px;font-size:12px">Office hours: Tuesdays 3–4pm, C19 or online · <a href="mailto:richard.wilkinson@nottingham.ac.uk" style="color:var(--accent-text)">richard.wilkinson@nottingham.ac.uk</a></div>
        </div>
      </div>
    </div>

    <!-- TRACKER -->
    <div class="page" id="page-tracker">
      <div class="page-title">Topic tracker</div>
      <div class="page-sub">Click a topic to study it · tick to mark complete</div>
      <div class="topic-grid" id="topic-grid"></div>
    </div>

    <!-- FORMULAS -->
    <div class="page" id="page-formulas">
      <div class="page-title">Formula sheet</div>
      <div class="page-sub">Key results from the MATH3030 formula sheet</div>
      <div class="formula-card">
        <div class="f-name">Multivariate Normal</div>
        <div class="f-math">x ~ Nₚ(μ, Σ)<br>f(x) = (2π)^{-p/2} |Σ|^{-1/2} exp{-½(x-μ)ᵀΣ⁻¹(x-μ)}</div>
        <div class="f-note">If y = Ax + c, then y ~ Nₚ(Aμ + c, AΣAᵀ)</div>
      </div>
      <div class="formula-card">
        <div class="f-name">Sample statistics</div>
        <div class="f-math">x̄ = (1/n) Σᵢ xᵢ<br>S = (1/n) Σᵢ (xᵢ - x̄)(xᵢ - x̄)ᵀ</div>
        <div class="f-note">Also acceptable with denominator n-1</div>
      </div>
      <div class="formula-card">
        <div class="f-name">Hotelling's T² (one sample)</div>
        <div class="f-math">T² = n(x̄ - μ₀)ᵀ S⁻¹ (x̄ - μ₀) ~ T²(p, n-1)</div>
        <div class="f-note">Under H₀: μ = μ₀ with x ~ Nₚ(μ, Σ)</div>
      </div>
      <div class="formula-card">
        <div class="f-name">Hotelling's T² (two sample)</div>
        <div class="f-math">T² = (n+m-p-1)/((n+m-2)p) · nm/(n+m) · (ȳ-x̄)ᵀ Sp⁻¹ (ȳ-x̄) ~ F_{p, n+m-p-1}</div>
        <div class="f-note">Sp = pooled covariance = (n·S₁ + m·S₂)/(n+m-2)</div>
      </div>
      <div class="formula-card">
        <div class="f-name">SVD decomposition</div>
        <div class="f-math">X = UΔVᵀ where U, V orthogonal; Δ diagonal<br>(1/n) XᵀX = (1/n) VΔ²Vᵀ  →  eigenvalues λᵢ = δᵢ²/n</div>
        <div class="f-note">Left singular vectors: U = XVΔ⁻¹</div>
      </div>
      <div class="formula-card">
        <div class="f-name">PCA scores</div>
        <div class="f-math">zᵢ = vᵢᵀ(x - x̄)   (i-th PC score)</div>
        <div class="f-note">Proportion variance explained by PC i: λᵢ / Σⱼ λⱼ</div>
      </div>
      <div class="formula-card">
        <div class="f-name">LDA discriminant rule</div>
        <div class="f-math">Classify x to A if: aᵀ(x - h) > 0<br>a = Sp⁻¹(x̄A - x̄B),  h = ½(x̄A + x̄B)</div>
        <div class="f-note">Bayes rule: classify to A if aᵀ(x-h) > log(πB/πA)</div>
      </div>
      <div class="formula-card">
        <div class="f-name">Wishart distribution</div>
        <div class="f-math">nS ~ Wₚ(Σ, n-1)  (when xᵢ iid Nₚ(μ,Σ))</div>
        <div class="f-note">x̄ and S are independent</div>
      </div>
      <div class="formula-card">
        <div class="f-name">MDS stress criterion</div>
        <div class="f-math">minimize Σᵢ Σⱼ (dᵢⱼ - d(zᵢ,zⱼ))²</div>
        <div class="f-note">Classical MDS: B = -½ H D² H, take top-k eigenvectors</div>
      </div>
    </div>

    <!-- PCA -->
    <div class="page" id="page-pca">
      <div class="page-title">Principal Component Analysis</div>
      <div class="page-sub">Dimension reduction via variance maximisation</div>
      <div class="card">
        <div class="card-title"><span style="color:var(--accent)">●</span> Optimization problem</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          Find a ∈ ℝᵖ to maximize Var(aᵀx)<br>
          subject to aᵀa = 1
        </div>
        <div style="font-size:13px;margin-top:10px;color:var(--muted);line-height:1.7">Solution is the eigenvector of Σ (or S) with largest eigenvalue. The k-th PC uses the k-th eigenvector.</div>
      </div>
      <div class="card">
        <div class="card-title">Key facts</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>· PCs are uncorrelated (orthogonal loading vectors)</div>
          <div>· Proportion of variance explained by PC<sub>i</sub> = λᵢ / Σλⱼ</div>
          <div>· Usually use covariance matrix; use correlation matrix if variables are on different scales</div>
          <div>· Score for individual x: zᵢ = vᵢᵀ(x − x̄)</div>
        </div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT PCA</div>
        <div class="ai-input-row">
          <textarea id="ai-pca-q" placeholder="e.g. Why do we subtract the mean before computing PCA scores?"></textarea>
          <button class="ai-send" onclick="askAI('pca-q','pca-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-pca-r"></div>
      </div>
    </div>

    <!-- SVD -->
    <div class="page" id="page-svd">
      <div class="page-title">Singular Value Decomposition</div>
      <div class="page-sub">Factorising a data matrix X = UΔVᵀ</div>
      <div class="card">
        <div class="card-title">Structure</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          X = U Δ Vᵀ<br>
          U (n×p): left singular vectors<br>
          Δ (p×p): diagonal, entries δ₁ ≥ δ₂ ≥ ... ≥ 0<br>
          V (p×p): right singular vectors (eigenvectors of XᵀX)
        </div>
      </div>
      <div class="card">
        <div class="card-title">Connection to PCA</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>· (1/n)XᵀX = (1/n)VΔ²Vᵀ → eigenvalues of covariance matrix = δᵢ²/n</div>
          <div>· Right singular vectors V = PC loadings</div>
          <div>· Recover U via U = XVΔ⁻¹</div>
          <div>· Sign of uᵢ, vᵢ can be flipped — solution not unique</div>
        </div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT SVD</div>
        <div class="ai-input-row">
          <textarea id="ai-svd-q" placeholder="e.g. How do I find the left singular vectors from scratch?"></textarea>
          <button class="ai-send" onclick="askAI('svd-q','svd-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-svd-r"></div>
      </div>
    </div>

    <!-- MVN -->
    <div class="page" id="page-mvn">
      <div class="page-title">Multivariate Normal Distribution</div>
      <div class="page-sub">Nₚ(μ, Σ) and its properties</div>
      <div class="card">
        <div class="card-title">Definition & properties</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>· x ~ Nₚ(μ, Σ): mean vector μ, covariance matrix Σ (p.s.d.)</div>
          <div>· Linear transformation: y = Ax + c ~ Nₚ(Aμ+c, AΣAᵀ)</div>
          <div>· Standardising: set A = Σ⁻¹/², c = −Σ⁻¹/²μ → y ~ Nₚ(0, Iₚ)</div>
          <div>· Marginals and conditionals of an MVN are also MVN</div>
          <div>· x̄ ~ Nₚ(μ, Σ/n) for iid sample</div>
        </div>
      </div>
      <div class="card">
        <div class="card-title">Chi-squared result</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          n(x̄ − μ)ᵀ Σ⁻¹ (x̄ − μ) ~ χ²ₚ
        </div>
        <div style="font-size:12px;color:var(--muted);margin-top:8px;line-height:1.6">Proof: standardise → sum of squares of iid N(0,1) = χ²ₚ. Replace Σ with S to get Hotelling's T².</div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT MVN</div>
        <div class="ai-input-row">
          <textarea id="ai-mvn-q" placeholder="e.g. Explain why x̄ and S are independent for MVN data"></textarea>
          <button class="ai-send" onclick="askAI('mvn-q','mvn-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-mvn-r"></div>
      </div>
    </div>

    <!-- HOTELLING -->
    <div class="page" id="page-hotelling">
      <div class="page-title">Hotelling's T²</div>
      <div class="page-sub">Multivariate hypothesis testing</div>
      <div class="card">
        <div class="card-title">One-sample test</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          H₀: μ = μ₀<br>
          T² = n(x̄−μ₀)ᵀS⁻¹(x̄−μ₀) ~ T²(p, n−1)
        </div>
      </div>
      <div class="card">
        <div class="card-title">Two-sample test</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          H₀: μ₁ = μ₂  (assumes equal Σ)<br>
          Sp = pooled covariance<br>
          T² ~ F_{p, n₁+n₂−p−1}
        </div>
        <div style="font-size:12px;color:var(--muted);margin-top:8px">Reject H₀ at level α if T² > F_{p, n+m-p-1, α}</div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT HOTELLING</div>
        <div class="ai-input-row">
          <textarea id="ai-hotelling-q" placeholder="e.g. How do I compute the pooled covariance matrix?"></textarea>
          <button class="ai-send" onclick="askAI('hotelling-q','hotelling-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-hotelling-r"></div>
      </div>
    </div>

    <!-- LDA -->
    <div class="page" id="page-lda">
      <div class="page-title">Discriminant Analysis</div>
      <div class="page-sub">Linear (LDA) and Quadratic (QDA) rules</div>
      <div class="card">
        <div class="card-title">ML Discriminant rule (equal Σ)</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          Classify x to A if: aᵀ(x − h) &gt; 0<br>
          a = Sp⁻¹(x̄A − x̄B)<br>
          h = ½(x̄A + x̄B)
        </div>
      </div>
      <div class="card">
        <div class="card-title">Bayes rule (prior probabilities πA, πB)</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          Classify to A if: aᵀ(x−h) &gt; log(πB / πA)
        </div>
        <div style="font-size:12px;color:var(--muted);margin-top:8px">If πA = πB the Bayes rule reduces to the ML rule. If covariance matrices differ, decision boundary is quadratic (QDA).</div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT LDA</div>
        <div class="ai-input-row">
          <textarea id="ai-lda-q" placeholder="e.g. Why does LDA give linear boundaries but QDA gives quadratic?"></textarea>
          <button class="ai-send" onclick="askAI('lda-q','lda-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-lda-r"></div>
      </div>
    </div>

    <!-- MDS -->
    <div class="page" id="page-mds">
      <div class="page-title">Multidimensional Scaling</div>
      <div class="page-sub">Low-dimensional representation from distance matrices</div>
      <div class="card">
        <div class="card-title">Optimization problem</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          Find z₁,...,zₙ ∈ ℝᵏ to minimize<br>
          Σᵢ Σⱼ (dᵢⱼ − ‖zᵢ − zⱼ‖)²
        </div>
      </div>
      <div class="card">
        <div class="card-title">Classical MDS algorithm</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>1. Form A = −½D²  (elementwise squaring)</div>
          <div>2. Double-centre: B = HAH where H = I − (1/n)11ᵀ</div>
          <div>3. Eigendecompose B = VΛVᵀ</div>
          <div>4. Take top-k eigenvalues/vectors: Z = V_k Λ_k^{1/2}</div>
          <div>· Negative eigenvalues indicate distances are non-Euclidean</div>
        </div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT MDS</div>
        <div class="ai-input-row">
          <textarea id="ai-mds-q" placeholder="e.g. What does the double-centring matrix H do geometrically?"></textarea>
          <button class="ai-send" onclick="askAI('mds-q','mds-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-mds-r"></div>
      </div>
    </div>

    <!-- CLUSTER -->
    <div class="page" id="page-cluster">
      <div class="page-title">Cluster Analysis</div>
      <div class="page-sub">k-means and hierarchical methods</div>
      <div class="card">
        <div class="card-title">k-means objective</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          Minimise Σₖ Σ_{xᵢ∈Cₖ} ‖xᵢ − μ̂ₖ‖²<br>
          where μ̂ₖ = (1/|Cₖ|) Σ_{i∈Cₖ} xᵢ
        </div>
      </div>
      <div class="card">
        <div class="card-title">Hierarchical clustering linkage methods</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>· Single linkage: d(A,B) = min{d(a,b) : a∈A, b∈B}  — tends to chain</div>
          <div>· Complete linkage: d(A,B) = max{d(a,b)} — tight, compact clusters</div>
          <div>· Average linkage: d(A,B) = avg{d(a,b)} — compromise</div>
          <div>· Ward's method: minimises within-cluster variance</div>
        </div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT CLUSTERING</div>
        <div class="ai-input-row">
          <textarea id="ai-cluster-q" placeholder="e.g. How do I draw a dendrogram from a distance matrix by hand?"></textarea>
          <button class="ai-send" onclick="askAI('cluster-q','cluster-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-cluster-r"></div>
      </div>
    </div>

    <!-- CCA -->
    <div class="page" id="page-cca">
      <div class="page-title">Canonical Correlation Analysis</div>
      <div class="page-sub">Finding maximally correlated linear combinations</div>
      <div class="card">
        <div class="card-title">Optimization problem</div>
        <div style="font-family:var(--mono);font-size:13px;background:var(--color-background-secondary);padding:12px 14px;border-radius:8px;line-height:2;">
          max_{a,b} Cor(aᵀy, bᵀz)<br>
          Solution via SVD of Q = Var(y)^{-½} Cov(y,z) Var(z)^{-½}
        </div>
      </div>
      <div class="card">
        <div class="card-title">Canonical correlations from eigenvalues of Σ</div>
        <div style="font-size:13px;line-height:1.9;color:var(--muted)">
          <div>If Var(y) = RU(Λ+I)(RU)ᵀ and Var(z) = TU(Λ+I)(TU)ᵀ</div>
          <div>then canonical correlations = λᵢ/(λᵢ + 1)</div>
          <div>This result appeared in the 2023–24 exam, Q3(b).</div>
        </div>
      </div>
      <div class="ai-box">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">ASK AI ABOUT CCA</div>
        <div class="ai-input-row">
          <textarea id="ai-cca-q" placeholder="e.g. How is CCA different from PCA?"></textarea>
          <button class="ai-send" onclick="askAI('cca-q','cca-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-cca-r"></div>
      </div>
    </div>

    <!-- EXAM 2024-25 -->
    <div class="page" id="page-exam24">
      <div class="page-title">Exam 2024–25</div>
      <div class="page-sub">MATH3030-Exam1of1-V1-SPR2425 · 3 hours · Answer ALL questions</div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q1a</span><span class="q-num">Identify methods from optimization problems</span><span class="q-marks">12 marks</span></div>
        <div class="q-text">Four optimization problems are given. Identify each: (i) maximize Var(aᵀx) s.t. aᵀa=1; (ii) minimize (y−Xa)ᵀ(y−Xa) + λ‖a‖²; (iii) minimize sum of squared distance differences; (iv) minimize within-cluster sum of squares.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) PCA — find direction of maximum variance. (ii) Ridge regression — linear model with L2 regularisation. (iii) MDS — low-dimensional representation matching distance matrix. (iv) k-means clustering — partition into k groups minimising within-cluster variance.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q1b</span><span class="q-num">Compute SVD of a given data matrix X</span><span class="q-marks">10 marks</span></div>
        <div class="q-text">Given X = [[2,2],[−4,2],[2,−4]] and its covariance decomposition, find the full SVD. Clearly label singular values and left/right singular vectors.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">Right singular vectors V from eigenvectors of (1/3)XᵀX. Singular values: δ₁=6, δ₂=2√3. Left vectors U = XV Δ⁻¹. Result: U = [[0, √(2/3)], [−1/√2, −1/√6], [1/√2, −1/√6]]. Note: sign flips are valid.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q1c</span><span class="q-num">PCA on body measurements</span><span class="q-marks">10 marks</span></div>
        <div class="q-text">(i) Calculate proportion of variance explained by PC1 and PC2. Eigenvalues: 345, 89, 36, 17, 3, 2. (ii) Interpret PC1 and PC2 from the loadings. (iii) Compute PC1 score for an individual and interpret it.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) (345+89)/492 = 88.2%. (ii) PC1: all positive loadings, largest for weight/height/shoulder → measure of body size. PC2: dominated by age loading (0.98) → measure of age. (iii) v₁ᵀ(x−x̄) = 0.52(11.8)+0.2(−0.2)+0.11(2.9)+0.41(−1.1)+0.7(4.8)+0.13(4.8) = 9.948 → larger than average member.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q2a</span><span class="q-num">MVN properties and Hotelling derivation</span><span class="q-marks">19 marks</span></div>
        <div class="q-text">State distribution of y=Ax+c. Derive the distribution of n(x̄−μ)ᵀΣ⁻¹(x̄−μ). Prove that n(x−μ)ᵀM⁻¹(x−μ) ~ T²(p,ν) when M~Wₚ(Σ,ν). Derive distribution of (n−1)(x̄−μ)ᵀS⁻¹(x̄−μ).</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">y ~ Nₚ(Aμ+c, AΣAᵀ). Setting A=Σ⁻¹/², c=−Σ⁻¹/²μ gives y ~ Nₚ(0,I). Then n(x̄−μ)ᵀΣ⁻¹(x̄−μ) = sum of p squared N(0,1) rvs ~ χ²ₚ. For Hotelling: standardise x and M using Σ⁻¹/² → by definition of T². Final: nS ~ Wₚ(Σ, n−1) and √n·x̄ ~ N so (n−1)(x̄−μ)ᵀS⁻¹(x̄−μ) ~ T²(p, n−1).</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q2b</span><span class="q-num">Hotelling test: widget factory</span><span class="q-marks">15 marks</span></div>
        <div class="q-text">Sample of n=20 widgets. x̄=(12.4, 16.8)ᵀ, S=[[1.1, 0.5],[0.5, 0.74]]. Test H₀: μ=(12, 17)ᵀ at 5% and 2.5% levels.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">T² = n(x̄−μ₀)ᵀS⁻¹(x̄−μ₀). Compute S⁻¹ = [[1.312, −0.887],[−0.887, 1.950]]. x̄−μ₀ = (0.4, −0.2). T² = 20 × (0.4, −0.2) S⁻¹ (0.4, −0.2)ᵀ = 3.868. Compare to F₂,₁₈: 95th pctile = 3.55. Since 3.868 > 3.55, reject at 5%. Since 3.868 < 4.56 (97.5th pctile), do not reject at 2.5%.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q3a</span><span class="q-num">LDA for bat subspecies</span><span class="q-marks">22 marks</span></div>
        <div class="q-text">(i) Find the ML discriminant rule: classify as A if x₁ + cx₂ < d. (ii) Classify bat: wingspan=120, body=30. (iii) Find Bayes rule with πA=0.7. Does classification change?</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) Pooled S, a = Sp⁻¹(x̄A−x̄B) = (−0.0252, −0.0648), h = (122, 29.2). Rule: x₁ + 2.57x₂ &lt; 197.2. (ii) 120 + 2.57×30 = 197.1 &lt; 197.2 → barely type B. (iii) Bayes threshold: log(0.3/0.7) = −0.847. aᵀ(x−h) = −0.0015 > −0.847 → reclassify as type A.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q3b</span><span class="q-num">Dendrogram: supermarkets (single linkage)</span><span class="q-marks">12 marks</span></div>
        <div class="q-text">Plot the dendrogram for the given 6×6 distance matrix using single linkage. Use letters A, B, L, S, T, W for Aldi, Booths, Lidl, Sainsburys, Tesco, Waitrose.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">Stage 1 (h=0.05): join B & W. Stage 2 (h=0.09): join A & L. Stage 3 (h=0.30): join S & BW. Stage 4 (h=0.31): join T & BSW. Stage 5 (h=0.35): join AL & BSTW. Final clusters at h=0.3: {A,L}, {B,W,S}, {T}.</div>
      </div>
    </div>

    <!-- EXAM 2023-24 -->
    <div class="page" id="page-exam23">
      <div class="page-title">Exam 2023–24</div>
      <div class="page-sub">MATH3030-E1 · 3 hours · Answer ALL questions</div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q1a</span><span class="q-num">SVD, eigenvalues, and PCA variational result</span><span class="q-marks">18 marks</span></div>
        <div class="q-text">(i) Give covariance matrix of centred X in terms of U, Δ, V. (ii) Eigenvalues of covariance matrix. (iii) Prove λ₁ = max_{a} ‖Xa‖/‖a‖ and state which a achieves it.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) Σ = (1/n)XᵀX = (1/n)VΔ²Vᵀ. (ii) Eigenvalues = δᵢ²/n. (iii) Set b = Vᵀa (orthogonal transform, preserves norm). Then aᵀXᵀXa = bᵀΔ²b = Σ δᵢ² bᵢ². With ‖b‖=1, maximised by b=(1,0,...,0) → max = δ₁² = nλ₁. So max ‖Xa‖/‖a‖ = λ₁. Achieved at a = Vb = v₁.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q1b</span><span class="q-num">Army recruits: PCA on S</span><span class="q-marks">13 marks</span></div>
        <div class="q-text">S = [[10,0,0],[0,95,65],[0,65,95]]. Eigenvectors given. (i) Interpret PCs. (ii) Find eigenvalues; how many PCs for ≥90% variance? (iii) PC1 score for x=(60,90,70)ᵀ.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) PC1 = overall maths+English ability; PC2 = maths vs English; PC3 = driving ability. (ii) λ₁=160, λ₂=30, λ₃=10. Need PCs 1&2: 160/200=80% &lt; 90% &lt; 190/200=95%. (iii) (x−x̄)=(−10,10,10). Score = (−10)(0)+(10)(1/√2)+(10)(1/√2) = 20/√2 = 14.14.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q2a</span><span class="q-num">Hotelling two-sample: ventricular hypertrophy</span><span class="q-marks">15 marks</span></div>
        <div class="q-text">Healthy: n=40, x̄ₕ=(151,143), Sₕ given. Sick: n=55, x̄ₛ=(140,136), Sₛ given. Test H₀: μₕ=μₛ at 5% using Hotelling's two-sample T².</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">Pool: Sp = (40S₁+55S₂)/93. Compute Sp⁻¹. (ȳ−x̄)=(−11,−7). Mahalanobis distance = 0.407. T² = (92/2)×(40×55/95)×0.407 = 4.659. Compare to F₂,₉₂: 95th pctile = 3.10. Since 4.659 > 3.10, reject H₀ at 5% — populations have different means.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q2b</span><span class="q-num">Multivariate t-distribution discriminant rule</span><span class="q-marks">19 marks</span></div>
        <div class="q-text">Show that ML discriminant rule under equal-Σ multivariate-t distribution takes the form aᵀ(x−h)>0. Find a and h. Classify a patient with measurements (143, 140).</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">fₕ(x) > fₛ(x) iff (x−μₕ)ᵀΣ⁻¹(x−μₕ) &lt; (x−μₛ)ᵀΣ⁻¹(x−μₛ). Expand and cancel → a = Σ⁻¹(μₕ−μₛ) = (0.036, 0.00095), h = (145.5, 139.5). aᵀ((143,140)−h) = −0.09 &lt; 0 → classify as hypertrophy.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q3a</span><span class="q-num">MDS of Bordeaux wines</span><span class="q-marks">18 marks</span></div>
        <div class="q-text">(i) Explain MDS and its optimization. (ii) Find 2D MDS representation from R output. (iii) Dendrogram using group average linkage.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) Find z₁,...,zₙ∈ℝᵏ minimising Σ(dᵢⱼ − ‖zᵢ−zⱼ‖)². (ii) Multiply top-2 eigenvectors by √eigenvalue: Z = [v₁√λ₁, v₂√λ₂]. (iii) Join H&L at 0.2, join E&P at 0.5, join M&EP at 0.64, join HL&MEP at 1.013.</div>
      </div>
      <div class="exam-item">
        <div class="q-header"><span class="tag tag-exam">Q3b</span><span class="q-num">CCA canonical correlations from eigenvalues</span><span class="q-marks">17 marks</span></div>
        <div class="q-text">y=Rx+e₁, z=Tx+e₂ with eᵢ~N(0,I). (i) Cov(y,z). (ii) Show Var(y) = RU(Λ+I)(RU)ᵀ. (iii) Find canonical correlations in terms of λᵢ.</div>
        <button class="reveal-btn" onclick="revealSol(this)">Show solution</button>
        <div class="solution">(i) Cov(y,z) = RΣTᵀ. (ii) Var(Rx+e₁) = RΣRᵀ+I = RUΛUᵀRᵀ+I = RU(Λ+I)(RU)ᵀ — spectral form since RU orthogonal. (iii) Q = Var(y)^{−½}Cov(y,z)Var(z)^{−½} = RU(Λ+I)^{−½}Λ(Λ+I)^{−½}(TU)ᵀ → diagonal part gives canonical correlations λᵢ/(λᵢ+1).</div>
      </div>
    </div>

    <!-- FLASHCARDS -->
    <div class="page" id="page-flashcards">
      <div class="page-title">Flashcards</div>
      <div class="page-sub">Click to reveal · use arrows to navigate</div>
      <div class="flashcard-area">
        <div class="flashcard" id="fc" onclick="flipCard()">
          <div class="flashcard-front"><div class="q" id="fc-q"></div></div>
          <div class="flashcard-back"><div class="a" id="fc-a"></div></div>
        </div>
      </div>
      <div class="fc-nav">
        <button onclick="prevCard()">← Previous</button>
        <span id="fc-count"></span>
        <button onclick="nextCard()">Next →</button>
      </div>
    </div>

    <!-- ASK AI -->
    <div class="page" id="page-askai">
      <div class="page-title">Ask AI</div>
      <div class="page-sub">Ask any question about MATH3030 — get explanations tailored to the module</div>
      <div class="ai-box" style="border-radius:12px;overflow:hidden">
        <div style="padding:10px 14px;font-size:11px;font-weight:600;color:var(--hint);border-bottom:0.5px solid var(--card-border);letter-spacing:0.04em">MULTIVARIATE ANALYSIS TUTOR</div>
        <div class="ai-input-row">
          <textarea id="ai-main-q" placeholder="e.g. Derive the distribution of (n-1)(x̄-μ)ᵀS⁻¹(x̄-μ) step by step..." style="min-height:80px"></textarea>
          <button class="ai-send" onclick="askAI('main-q','main-r')">Ask ↗</button>
        </div>
        <div class="ai-response" id="ai-main-r"></div>
      </div>
      <div style="margin-top:16px">
        <div style="font-size:11px;color:var(--hint);font-weight:600;letter-spacing:0.04em;margin-bottom:8px">QUICK PROMPTS</div>
        <div style="display:flex;flex-wrap:wrap;gap:6px">
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('Explain how to compute the SVD of a data matrix step by step')">SVD step-by-step</button>
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('What is the Wishart distribution and why is it important?')">Wishart distribution</button>
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('Walk me through a complete Hotelling T² two-sample test example')">Two-sample test</button>
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('How do I interpret PC loadings in PCA?')">Interpret loadings</button>
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('Compare single, complete, and average linkage hierarchical clustering')">Linkage methods</button>
          <button style="font-size:12px;padding:6px 12px;border-radius:6px;border:0.5px solid var(--card-border);background:var(--color-background-secondary);cursor:pointer;font-family:var(--sans);color:var(--text)" onclick="setPrompt('What are the key differences between LDA and QDA?')">LDA vs QDA</button>
        </div>
      </div>
    </div>
  </main>
</div>

<script>
const TOPICS = {
  pca: { name:'Principal Component Analysis', color:'#534AB7', tags:['theory','exam','key'], exam:['Q1a','Q1c','2023-Q1b'] },
  svd: { name:'Singular Value Decomposition', color:'#1D9E75', tags:['theory','exam'], exam:['Q1b','2023-Q1a'] },
  mvn: { name:'Multivariate Normal', color:'#D85A30', tags:['theory','key'], exam:['Q2a'] },
  hotelling: { name:"Hotelling's T²", color:'#BA7517', tags:['theory','exam','key'], exam:['Q2b','2023-Q2a'] },
  lda: { name:'Discriminant Analysis', color:'#D4537E', tags:['exam','key'], exam:['Q3a','2023-Q2b'] },
  mds: { name:'Multidimensional Scaling', color:'#378ADD', tags:['theory','exam'], exam:['Q1a-iii','2023-Q3a'] },
  cluster: { name:'Cluster Analysis', color:'#639922', tags:['exam'], exam:['Q1a-iv','Q3b'] },
  cca: { name:'Canonical Correlation Analysis', color:'#5DCAA5', tags:['theory'], exam:['2023-Q3b'] },
};

const FLASHCARDS = [
  { q:'What optimization problem does PCA solve?', a:'Maximise Var(aᵀx) subject to aᵀa=1. Solution: eigenvectors of the covariance matrix.' },
  { q:'What is the SVD decomposition of a matrix X?', a:'X = UΔVᵀ where U, V are orthogonal and Δ is diagonal with non-negative entries (singular values).' },
  { q:'What distribution does n(x̄−μ)ᵀΣ⁻¹(x̄−μ) follow?', a:'Chi-squared with p degrees of freedom: χ²ₚ. Proof: standardise using Σ⁻¹/² to get sum of squares of iid N(0,1).' },
  { q:'State the one-sample Hotelling T² test statistic', a:'T² = n(x̄−μ₀)ᵀS⁻¹(x̄−μ₀) ~ T²(p, n−1). Equivalently ~ F_{p, n-p} after scaling.' },
  { q:'How does the Bayes discriminant rule modify the ML rule?', a:'Classify to A if aᵀ(x−h) > log(πB/πA). When priors are equal, this reduces to the ML rule (threshold 0).' },
  { q:'What is the classical MDS algorithm?', a:'(1) A = −½D². (2) B = HAH (double-centre). (3) Eigendecompose B. (4) Z = V_k Λ_k^{1/2} gives k-dimensional coordinates.' },
  { q:'What linkage function does single linkage use?', a:'d(A,B) = min{d(a,b): a∈A, b∈B} — the smallest distance between any pair of points across clusters.' },
  { q:'What does nS follow when xᵢ iid Nₚ(μ,Σ)?', a:'nS ~ Wₚ(Σ, n−1) — a Wishart distribution with n−1 degrees of freedom. Crucially, x̄ and S are independent.' },
  { q:'What is the proportion of variance explained by PC_i?', a:'λᵢ / (λ₁ + λ₂ + ... + λₚ) where λᵢ are eigenvalues of the covariance matrix.' },
  { q:'What do the canonical correlations equal if y=Rx+e₁, z=Tx+e₂?', a:'λᵢ/(λᵢ+1) where λᵢ are the eigenvalues of Σ = Cov(x). Shown by SVD of Q = Var(y)^{−½}Cov(y,z)Var(z)^{−½}.' },
  { q:'What does ridge regression minimize?', a:'(y−Xa)ᵀ(y−Xa) + λ‖a‖². This adds an L2 penalty to shrink coefficients, preventing overfitting.' },
  { q:'How do you compute the PC1 score for an individual x?', a:'z₁ = v₁ᵀ(x − x̄) where v₁ is the first eigenvector of S and x̄ is the sample mean.' },
];

let completed = JSON.parse(localStorage.getItem('mva-done') || '{}');
let fcIdx = 0, fcFlipped = false;

function save() { try { localStorage.setItem('mva-done', JSON.stringify(completed)); } catch(e){} }

function updateStats() {
  const done = Object.values(completed).filter(Boolean).length;
  const el = document.getElementById('stat-done');
  if(el) el.textContent = done + '/' + Object.keys(TOPICS).length;
  Object.keys(TOPICS).forEach(k => {
    const c = document.getElementById('chk-'+k);
    if(c) { c.textContent = completed[k] ? '✓' : ''; c.className = 'check' + (completed[k]?' done':''); }
  });
  renderProgress();
}

function renderProgress() {
  const el = document.getElementById('progress-rows');
  if(!el) return;
  const topics = Object.entries(TOPICS);
  el.innerHTML = topics.map(([k,t]) => {
    const pct = completed[k] ? 100 : 30;
    return `<div class="progress-row">
      <div class="label">${t.name}</div>
      <div class="progress-bar"><div class="progress-fill" style="width:${pct}%;background:${t.color}"></div></div>
      <div class="pct">${pct}%</div>
    </div>`;
  }).join('');
}

function renderTopicGrid() {
  const el = document.getElementById('topic-grid');
  if(!el) return;
  el.innerHTML = Object.entries(TOPICS).map(([k,t]) => {
    const tagMap = { theory:'tag-theory', exam:'tag-exam', r:'tag-r', key:'tag-key' };
    const tags = t.tags.map(tg => `<span class="tag ${tagMap[tg]||'tag-theory'}">${tg}</span>`).join('');
    const done = completed[k];
    return `<div class="topic-card ${done?'complete':''}" onclick="goto('${k}')">
      <div class="tc-num">MATH3030</div>
      <div class="tc-name">${t.name}</div>
      <div class="tc-tags">${tags}</div>
      <div class="tc-status ${done?'done':''}" onclick="event.stopPropagation();toggle('${k}')">${done?'✓':''}</div>
    </div>`;
  }).join('');
}

function toggle(key) {
  completed[key] = !completed[key];
  save();
  updateStats();
  renderTopicGrid();
}

function goto(page) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  const el = document.getElementById('page-'+page);
  if(el) el.classList.add('active');
  document.getElementById('main-scroll').scrollTop = 0;
}

function revealSol(btn) {
  const sol = btn.nextElementSibling;
  sol.classList.toggle('visible');
  btn.textContent = sol.classList.contains('visible') ? 'Hide solution' : 'Show solution';
}

function renderFlashcard() {
  const fc = FLASHCARDS[fcIdx];
  document.getElementById('fc-q').textContent = fc.q;
  document.getElementById('fc-a').textContent = fc.a;
  document.getElementById('fc-count').textContent = (fcIdx+1) + ' / ' + FLASHCARDS.length;
  document.getElementById('fc').classList.remove('flipped');
  fcFlipped = false;
}
function flipCard() { document.getElementById('fc').classList.toggle('flipped'); fcFlipped = !fcFlipped; }
function nextCard() { fcIdx = (fcIdx+1) % FLASHCARDS.length; renderFlashcard(); }
function prevCard() { fcIdx = (fcIdx-1+FLASHCARDS.length) % FLASHCARDS.length; renderFlashcard(); }

async function askAI(qId, rId) {
  const q = document.getElementById('ai-'+qId).value.trim();
  if(!q) return;
  const resp = document.getElementById('ai-'+rId);
  resp.className = 'ai-response visible';
  resp.innerHTML = '<span class="ai-loading">Thinking…</span>';
  try {
    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body: JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:1000,
        system:'You are a concise tutor for MATH3030 Multivariate Analysis at the University of Nottingham (taught by Prof. Richard Wilkinson). Topics: PCA, SVD, Multivariate Normal, Wishart, Hotelling T², LDA/QDA, MDS, Cluster Analysis, CCA. Answer clearly and concisely, using mathematical notation where helpful. Assume the student knows linear algebra and basic statistics.',
        messages:[{role:'user', content:q}]
      })
    });
    const data = await res.json();
    const text = data.content?.map(c=>c.text||'').join('') || 'No response.';
    resp.innerHTML = text.replace(/\n/g,'<br>');
  } catch(e) { resp.innerHTML = 'Error: ' + e.message; }
}

function setPrompt(text) {
  document.getElementById('ai-main-q').value = text;
  document.getElementById('ai-main-q').focus();
}

function filterNav(val) {
  val = val.toLowerCase();
  document.querySelectorAll('#topics-nav .nav-item').forEach(item => {
    item.style.display = item.textContent.toLowerCase().includes(val) ? '' : 'none';
  });
}

renderFlashcard();
renderTopicGrid();
updateStats();
</script>
