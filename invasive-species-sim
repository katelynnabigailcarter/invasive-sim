<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <title>Invasive Species and Ecosystem Balance — Virtual Lab</title>
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    body { font-family: 'Inter', Arial, sans-serif; margin:0; padding:20px; background:#f6fbf7; color:#15332b; }
    header { display:flex; align-items:center; gap:16px; margin-bottom:18px; }
    h1 { margin:0; font-size:1.6rem; }
    .grid { display:grid; grid-template-columns: 360px 1fr; gap:18px; align-items:start; }
    .card { background:white; border-radius:10px; padding:14px; box-shadow:0 6px 18px rgba(5,40,30,0.06); }
    label { display:block; margin:10px 0 6px; font-weight:600; font-size:0.92rem; }
    .row { display:flex; gap:8px; align-items:center; }
    .num { font-weight:600; padding:6px 10px; background:#eef7f1; border-radius:8px; min-width:70px; text-align:center; }
    input[type=range] { width:100%; }
    button { background:#2b8a5a; color:white; border:none; padding:8px 10px; border-radius:8px; cursor:pointer; font-weight:600; }
    button.secondary { background:#6aa98a; }
    .small { font-size:0.85rem; color:#3b6a59; }
    .chart-wrap { height:340px; }
    table { width:100%; border-collapse:collapse; margin-top:10px; font-size:0.9rem; }
    th,td { border:1px solid #e7efe9; padding:6px 8px; text-align:center; }
    .instructions { font-size:0.95rem; line-height:1.45; }
    footer { margin-top:18px; font-size:0.85rem; color:#2f4f42; }
    .top-controls { display:flex; gap:8px; margin-top:10px; flex-wrap:wrap; }
    .badge { background:#e9f5ee; padding:4px 8px; border-radius:6px; font-weight:600; color:#1b5b3f; }
    .export { margin-left:auto; display:flex; gap:8px; }
    .notes { margin-top:10px; font-size:0.88rem; color:#475b51; }
    .question { margin-top:12px; background:#f0fff4; padding:10px; border-radius:8px; }
    .hint { font-size:0.85rem; color:#486b5a; }
  </style>
</head>
<body>
  <header>
    <div class="badge">Lab: SES6</div>
    <div>
      <h1>Invasive Species and Ecosystem Balance — Virtual Lab</h1>
      <div class="small">Georgia Standards of Excellence — Environmental Science</div>
    </div>
  </header>

  <div class="grid">
    <!-- left controls -->
    <div class="card">
      <div>
        <label>Initial Populations</label>
        <div class="row">
          <div style="flex:1">
            <div class="small">Grass (producers)</div>
            <input id="grassRange" type="range" min="50" max="1000" value="300">
            <div class="num" id="grassDisplay">300</div>
          </div>
        </div>

        <div class="row" style="margin-top:8px">
          <div style="flex:1">
            <div class="small">Rabbits (herbivores)</div>
            <input id="rabbitRange" type="range" min="0" max="300" value="40">
            <div class="num" id="rabbitDisplay">40</div>
          </div>
        </div>

        <div class="row" style="margin-top:8px">
          <div style="flex:1">
            <div class="small">Snakes (mesopredator)</div>
            <input id="snakeRange" type="range" min="0" max="100" value="10">
            <div class="num" id="snakeDisplay">10</div>
          </div>
        </div>

        <div class="row" style="margin-top:8px">
          <div style="flex:1">
            <div class="small">Hawks (top predator)</div>
            <input id="hawkRange" type="range" min="0" max="50" value="5">
            <div class="num" id="hawkDisplay">5</div>
          </div>
        </div>

        <label>Simulation Controls</label>
        <div class="top-controls">
          <button id="runBtn">Run 1 Step</button>
          <button class="secondary" id="run10Btn">Run 10 Steps</button>
          <button class="secondary" id="autoBtn">Auto Run</button>
          <button id="resetBtn">Reset</button>
          <div class="export">
            <button id="exportCSV" title="Download table as CSV">Export CSV</button>
            <button id="saveConfig" title="Save current settings to clipboard">Copy Lab Link</button>
          </div>
        </div>

        <div class="notes">
          <div><strong>Time step:</strong> Each step simulates one week in the virtual ecosystem.</div>
          <div style="margin-top:6px" class="hint">Use Run 10 Steps to quickly reveal trends. Use Copy Lab Link to create a URL representing current settings you can paste into a browser or an email.</div>
        </div>

        <div style="margin-top:12px">
          <label>Add or Remove Species</label>
          <div class="row">
            <button id="addRabbits">Add 10 Rabbits</button>
            <button id="removeRabbits" class="secondary">Remove 10 Rabbits</button>
          </div>
          <div class="row" style="margin-top:8px">
            <button id="addHawks">Add 2 Hawks</button>
            <button id="removeHawks" class="secondary">Remove 2 Hawks</button>
          </div>
        </div>

        <div style="margin-top:12px">
          <label>Student Worksheet</label>
          <div class="instructions">
            1. Set initial populations. 2. Run simulation for at least 20 steps. 3. Record data from table. 4. Answer reflection questions at the right.
          </div>
        </div>
      </div>
    </div>

    <!-- right main -->
    <div>
      <div class="card">
        <div class="chart-wrap">
          <canvas id="popChart"></canvas>
        </div>
        <div style="display:flex; gap:12px; margin-top:10px; align-items:center;">
          <div class="small">Step: <span id="stepNum">0</span></div>
          <div class="small">Biodiversity Index: <strong id="bioIndex">0</strong></div>
          <div style="margin-left:auto;" class="small">CSV rows: <span id="csvCount">0</span></div>
        </div>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin:0 0 8px 0">Data Table</h3>
        <div style="overflow:auto; max-height:220px;">
          <table id="dataTable">
            <thead>
              <tr>
                <th>Step</th>
                <th>Grass</th>
                <th>Rabbits</th>
                <th>Snakes</th>
                <th>Hawks</th>
                <th>Biodiversity Index</th>
              </tr>
            </thead>
            <tbody></tbody>
          </table>
        </div>
        <div style="margin-top:10px" class="small">Tip: Run the simulation, then use Export CSV to save your results for analysis and graphing in Excel or Google Sheets.</div>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin:0 0 8px 0">Reflection & Questions</h3>
        <div class="question">
          <ol>
            <li>Which plant or animal addition or removal caused the largest change in biodiversity? Explain using population trends.</li>
            <li>How could human actions mimic the changes you introduced in this simulation?</li>
            <li>What limitations does this simulation have compared to field data?</li>
            <li>Propose a restoration action that could help return the system to balance.</li>
          </ol>
        </div>
        <div style="margin-top:10px" class="small">When finished, copy the CSV, paste into a spreadsheet, and create line graphs for each population. Attach graphs to your lab report.</div>
      </div>

      <div class="card" style="margin-top:12px">
        <h3 style="margin:0 0 8px 0">AI Prompt & Citation (for your submission)</h3>
        <div class="small">
          Prompt used to create this simulation:
          <pre style="background:#f4f9f1; padding:8px; border-radius:6px; overflow:auto; font-size:0.83rem;">
Create an interactive virtual laboratory simulation titled "Invasive Species and Ecosystem Balance."
Align it with Georgia Environmental Science standard SES6. Include interactive controls to add/remove species, run time steps, collect population data (grass, rabbits, snakes, hawks), compute a biodiversity index, show live graphs, provide a data table, and include reflection questions. Output as a single self-contained HTML file with comments and easy hosting instructions.
          </pre>
          AI Source: <a href="https://chat.openai.com" target="_blank">ChatGPT (OpenAI)</a> — interaction date: October 31, 2025.
        </div>
      </div>

      <footer>
        <div class="small">Developer note: Save this file as <strong>invasive_simulation.html</strong>. To create a live link, host on GitHub Pages, Netlify Drop, or any static hosting provider. See hosting instructions below.</div>
      </footer>
    </div>
  </div>

  <!-- Chart.js CDN -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script>
    // --- Model parameters and state ---
    const state = {
      step: 0,
      grass: 300,
      rabbits: 40,
      snakes: 10,
      hawks: 5,
      history: []
    };

    // DOM refs
    const grassRange = document.getElementById('grassRange');
    const rabbitRange = document.getElementById('rabbitRange');
    const snakeRange = document.getElementById('snakeRange');
    const hawkRange = document.getElementById('hawkRange');
    const grassDisplay = document.getElementById('grassDisplay');
    const rabbitDisplay = document.getElementById('rabbitDisplay');
    const snakeDisplay = document.getElementById('snakeDisplay');
    const hawkDisplay = document.getElementById('hawkDisplay');
    const stepNum = document.getElementById('stepNum');
    const bioIndex = document.getElementById('bioIndex');
    const dataTableBody = document.querySelector('#dataTable tbody');
    const csvCount = document.getElementById('csvCount');

    // update displays
    function updateControls() {
      grassDisplay.textContent = state.grass;
      rabbitDisplay.textContent = state.rabbits;
      snakeDisplay.textContent = state.snakes;
      hawkDisplay.textContent = state.hawks;
      grassRange.value = state.grass;
      rabbitRange.value = state.rabbits;
      snakeRange.value = state.snakes;
      hawkRange.value = state.hawks;
      stepNum.textContent = state.step;
    }

    // biodiversity index: simple metric based on number of species present and evenness
    function computeBiodiversityIndex(g, r, s, h) {
      const species = [g>20?1:0, r>0?1:0, s>0?1:0, h>0?1:0];
      const speciesCount = species.reduce((a,b)=>a+b,0);
      const pops = [g,r,s,h].map(x=>Math.max(0,x));
      const total = pops.reduce((a,b)=>a+b,0) || 1;
      const evenness = pops.map(p => p/total).filter(x=>x>0).reduce((a,b)=>a - (b*Math.log(b)),0);
      // normalize to 1-10
      const idx = Math.round(Math.min(10, Math.max(1, speciesCount*2 + evenness*2)));
      return idx;
    }

    // ecosystem dynamics per time step (simple deterministic + small randomness)
    function stepEcosystem() {
      let g = state.grass;
      let r = state.rabbits;
      let s = state.snakes;
      let h = state.hawks;

      // grass growth: logistic with grazing pressure
      const grassIntrinsic = 0.08;
      const grassCarry = 1200;
      const grazingEffect = Math.max(0, r * 0.03); // rabbits eat grass
      const newGrass = g + Math.round(g * grassIntrinsic * (1 - g/grassCarry) - grazingEffect + (Math.random()-0.45)*5);

      // rabbits: birth proportional to food, death from predators
      const rabbitBirthRate = 0.12 * Math.min(1, g/200);
      const rabbitDeathsFromSnakes = Math.round(Math.min(r, Math.round(s * (0.15 + Math.random()*0.05))));
      const rabbitDeathsFromHawks = Math.round(Math.min(r - rabbitDeathsFromSnakes, Math.round(h * (0.12 + Math.random()*0.05))));
      const newRabbits = Math.max(0, r + Math.round(r * rabbitBirthRate - rabbitDeathsFromSnakes - rabbitDeathsFromHawks + (Math.random()-0.45)*2));

      // snakes: feed on rabbits; reproduce based on food
      const snakeBirthRate = 0.06 * Math.min(1, newRabbits/50);
      const snakeDeaths = Math.round(s * 0.04);
      const newSnakes = Math.max(0, s + Math.round(s * snakeBirthRate - snakeDeaths + (Math.random()-0.5)*1));

      // hawks: top predator, feed on rabbits and snakes
      const hawkFood = newRabbits * 0.01 + newSnakes * 0.02;
      const hawkBirthRate = 0.03 * Math.min(1, hawkFood/2);
      const hawkDeaths = Math.round(h * 0.05);
      const newHawks = Math.max(0, h + Math.round(h * hawkBirthRate - hawkDeaths + (Math.random()-0.5)*0.6));

      // apply
      state.grass = Math.max(0, Math.round(newGrass));
      state.rabbits = Math.max(0, Math.round(newRabbits));
      state.snakes = Math.max(0, Math.round(newSnakes));
      state.hawks = Math.max(0, Math.round(newHawks));
      state.step += 1;

      // update history row
      const idx = computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks);
      state.history.push({
        step: state.step,
        grass: state.grass,
        rabbits: state.rabbits,
        snakes: state.snakes,
        hawks: state.hawks,
        bio: idx
      });
      appendRow(state.history[state.history.length-1]);
      updateChart();
      updateControls();
      bioIndex.textContent = idx;
      csvCount.textContent = state.history.length;
    }

    // --- Chart
    const ctx = document.getElementById('popChart').getContext('2d');
    const chart = new Chart(ctx, {
      type: 'line',
      data: {
        labels: [],
        datasets: [
          { label: 'Grass', data: [], borderWidth:2, fill:false, tension:0.2 },
          { label: 'Rabbits', data: [], borderWidth:2, fill:false, tension:0.2 },
          { label: 'Snakes', data: [], borderWidth:2, fill:false, tension:0.2 },
          { label: 'Hawks', data: [], borderWidth:2, fill:false, tension:0.2 }
        ]
      },
      options: {
        animation:false,
        responsive:true,
        plugins: {
          legend: { position:'top' }
        },
        scales: {
          x: { title: { display:true, text:'Time Step (weeks)' } },
          y: { title: { display:true, text:'Population' }, beginAtZero:true }
        }
      }
    });

    function updateChart() {
      chart.data.labels = state.history.map(r => r.step);
      chart.data.datasets[0].data = state.history.map(r => r.grass);
      chart.data.datasets[1].data = state.history.map(r => r.rabbits);
      chart.data.datasets[2].data = state.history.map(r => r.snakes);
      chart.data.datasets[3].data = state.history.map(r => r.hawks);
      chart.update();
    }

    function appendRow(r) {
      const tr = document.createElement('tr');
      tr.innerHTML = `<td>${r.step}</td><td>${r.grass}</td><td>${r.rabbits}</td><td>${r.snakes}</td><td>${r.hawks}</td><td>${r.bio}</td>`;
      dataTableBody.appendChild(tr);
    }

    // controls wiring
    document.getElementById('runBtn').addEventListener('click', () => stepEcosystem());
    document.getElementById('run10Btn').addEventListener('click', () => { for(let i=0;i<10;i++) stepEcosystem(); });
    let autoInterval = null;
    document.getElementById('autoBtn').addEventListener('click', (e) => {
      if (!autoInterval) {
        autoInterval = setInterval(() => stepEcosystem(), 600);
        e.target.textContent = 'Stop Auto';
        e.target.classList.remove('secondary');
      } else {
        clearInterval(autoInterval);
        autoInterval = null;
        e.target.textContent = 'Auto Run';
        e.target.classList.add('secondary');
      }
    });

    // sliders to set initial populations (only when step=0)
    function setStateFromSliders() {
      if (state.step === 0) {
        state.grass = parseInt(grassRange.value);
        state.rabbits = parseInt(rabbitRange.value);
        state.snakes = parseInt(snakeRange.value);
        state.hawks = parseInt(hawkRange.value);
        updateControls();
      }
    }
    grassRange.addEventListener('input', () => { grassDisplay.textContent = grassRange.value; setStateFromSliders(); });
    rabbitRange.addEventListener('input', () => { rabbitDisplay.textContent = rabbitRange.value; setStateFromSliders(); });
    snakeRange.addEventListener('input', () => { snakeDisplay.textContent = snakeRange.value; setStateFromSliders(); });
    hawkRange.addEventListener('input', () => { hawkDisplay.textContent = hawkRange.value; setStateFromSliders(); });

    // add/remove buttons
    document.getElementById('addRabbits').addEventListener('click', () => { state.rabbits += 10; appendManualRow(); updateChart(); updateControls(); });
    document.getElementById('removeRabbits').addEventListener('click', () => { state.rabbits = Math.max(0, state.rabbits - 10); appendManualRow(); updateChart(); updateControls(); });
    document.getElementById('addHawks').addEventListener('click', () => { state.hawks += 2; appendManualRow(); updateChart(); updateControls(); });
    document.getElementById('removeHawks').addEventListener('click', () => { state.hawks = Math.max(0, state.hawks - 2); appendManualRow(); updateChart(); updateControls(); });

    function appendManualRow() {
      // record a manual observation at current step (no increment)
      const idx = computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks);
      state.history.push({ step: state.step + 0.1, grass: state.grass, rabbits: state.rabbits, snakes: state.snakes, hawks: state.hawks, bio: idx });
      appendRow(state.history[state.history.length-1]);
      csvCount.textContent = state.history.length;
    }

    // reset
    document.getElementById('resetBtn').addEventListener('click', () => {
      if (autoInterval) { clearInterval(autoInterval); autoInterval = null; document.getElementById('autoBtn').textContent='Auto Run'; }
      state.step = 0;
      state.history = [];
      state.grass = parseInt(grassRange.value);
      state.rabbits = parseInt(rabbitRange.value);
      state.snakes = parseInt(snakeRange.value);
      state.hawks = parseInt(hawkRange.value);
      dataTableBody.innerHTML = '';
      updateChart();
      updateControls();
      bioIndex.textContent = computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks);
      csvCount.textContent = 0;
    });

    // export CSV
    document.getElementById('exportCSV').addEventListener('click', () => {
      const rows = [['Step','Grass','Rabbits','Snakes','Hawks','BiodiversityIndex']];
      for (const r of state.history) {
        rows.push([r.step, r.grass, r.rabbits, r.snakes, r.hawks, r.bio]);
      }
      const csvContent = rows.map(e => e.join(',')).join('\n');
      const blob = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'ecosystem_data.csv';
      a.style.display = 'none';
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
    });

    // copy lab link: encode settings as query string; user can paste into browser to restore
    document.getElementById('saveConfig').addEventListener('click', async () => {
      const params = new URLSearchParams({
        grass: state.grass, rabbits: state.rabbits, snakes: state.snakes, hawks: state.hawks
      });
      const url = location.href.split('#')[0].split('?')[0] + '?' + params.toString();
      await navigator.clipboard.writeText(url);
      alert('Lab link copied to clipboard. Paste it into a browser or email to share initial settings.');
    });

    // restore from query string
    function restoreFromQuery() {
      const p = new URLSearchParams(location.search);
      if (p.has('grass')) {
        state.grass = parseInt(p.get('grass') || state.grass);
        state.rabbits = parseInt(p.get('rabbits') || state.rabbits);
        state.snakes = parseInt(p.get('snakes') || state.snakes);
        state.hawks = parseInt(p.get('hawks') || state.hawks);
      }
      updateControls();
      bioIndex.textContent = computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks);
    }

    // initial setup
    restoreFromQuery();
    updateControls();
    bioIndex.textContent = computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks);

    // append initial baseline row (step 0)
    state.history.push({ step:0, grass: state.grass, rabbits: state.rabbits, snakes: state.snakes, hawks: state.hawks, bio: computeBiodiversityIndex(state.grass, state.rabbits, state.snakes, state.hawks) });
    appendRow(state.history[0]);
    csvCount.textContent = state.history.length;
  </script>
</body>
</html>
