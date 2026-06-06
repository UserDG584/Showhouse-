[index.html](https://github.com/user-attachments/files/28668502/index.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Window Cleaning Quote Request</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --navy: #0d1b2a;
    --blue: #1b4f8a;
    --sky: #4a9ede;
    --ice: #e8f4fd;
    --white: #ffffff;
    --slate: #64748b;
    --border: #d0e4f5;
    --accent: #f0a500;
    --success: #22c55e;
    --error: #ef4444;
    --text: #1e293b;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: linear-gradient(160deg, #0d1b2a 0%, #1b3a6b 60%, #0d1b2a 100%);
    min-height: 100vh;
    color: var(--text);
    padding: 40px 20px 80px;
  }

  /* Animated background bubbles */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 600px 400px at 80% 20%, rgba(74,158,222,0.15) 0%, transparent 70%),
      radial-gradient(ellipse 400px 600px at 10% 80%, rgba(27,79,138,0.2) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 760px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 48px;
    animation: fadeDown 0.6s ease both;
  }

  .logo-mark {
    width: 64px;
    height: 64px;
    background: linear-gradient(135deg, var(--sky), var(--blue));
    border-radius: 18px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 20px;
    box-shadow: 0 8px 32px rgba(74,158,222,0.4);
  }

  .logo-mark svg { width: 34px; height: 34px; fill: white; }

  h1 {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2rem, 5vw, 3rem);
    color: var(--white);
    line-height: 1.1;
    margin-bottom: 12px;
  }

  .subtitle {
    color: rgba(255,255,255,0.65);
    font-size: 1rem;
    font-weight: 300;
    letter-spacing: 0.02em;
  }

  /* Progress bar */
  .progress-wrap {
    background: rgba(255,255,255,0.1);
    border-radius: 99px;
    height: 4px;
    margin-bottom: 40px;
    overflow: hidden;
    animation: fadeDown 0.6s 0.1s ease both;
  }
  .progress-bar {
    height: 100%;
    background: linear-gradient(90deg, var(--sky), var(--accent));
    border-radius: 99px;
    transition: width 0.4s cubic-bezier(.4,0,.2,1);
    width: 0%;
  }

  /* Section cards */
  .section-card {
    background: var(--white);
    border-radius: 24px;
    padding: 36px;
    margin-bottom: 24px;
    box-shadow: 0 4px 24px rgba(0,0,0,0.18), 0 0 0 1px rgba(255,255,255,0.05);
    animation: fadeUp 0.5s ease both;
  }

  .section-card:nth-child(2) { animation-delay: 0.05s; }
  .section-card:nth-child(3) { animation-delay: 0.1s; }
  .section-card:nth-child(4) { animation-delay: 0.15s; }

  .section-label {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-size: 0.7rem;
    font-weight: 600;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--sky);
    background: var(--ice);
    padding: 5px 12px;
    border-radius: 99px;
    margin-bottom: 24px;
  }

  .section-label svg { width: 12px; height: 12px; }

  /* Question groups */
  .q-group {
    margin-bottom: 28px;
  }

  .q-group:last-child { margin-bottom: 0; }

  label.q-label {
    display: block;
    font-weight: 500;
    font-size: 0.92rem;
    color: var(--navy);
    margin-bottom: 10px;
    line-height: 1.4;
  }

  label.q-label span.num {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 24px;
    height: 24px;
    background: var(--navy);
    color: white;
    border-radius: 50%;
    font-size: 0.72rem;
    font-weight: 600;
    margin-right: 8px;
    flex-shrink: 0;
  }

  /* Inputs */
  input[type="text"],
  input[type="email"],
  input[type="tel"],
  input[type="number"],
  input[type="date"],
  select,
  textarea {
    width: 100%;
    padding: 13px 16px;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.92rem;
    color: var(--navy);
    background: #f8fbff;
    transition: border-color 0.2s, box-shadow 0.2s, background 0.2s;
    outline: none;
    -webkit-appearance: none;
    appearance: none;
  }

  input:focus, select:focus, textarea:focus {
    border-color: var(--sky);
    background: var(--white);
    box-shadow: 0 0 0 3px rgba(74,158,222,0.15);
  }

  input.error, select.error, textarea.error {
    border-color: var(--error);
    background: #fff8f8;
  }

  .field-error {
    font-size: 0.78rem;
    color: var(--error);
    margin-top: 5px;
    display: none;
  }

  .field-error.show { display: block; }

  select {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='%2364748b' viewBox='0 0 16 16'%3E%3Cpath d='M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 14px center;
    padding-right: 40px;
    cursor: pointer;
  }

  textarea { min-height: 90px; resize: vertical; }

  /* Postcode row */
  .postcode-row {
    display: grid;
    grid-template-columns: 1fr auto;
    gap: 10px;
    align-items: start;
  }

  .postcode-row input { }

  .lookup-btn {
    padding: 13px 18px;
    background: var(--navy);
    color: white;
    border: none;
    border-radius: 12px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.85rem;
    font-weight: 500;
    cursor: pointer;
    white-space: nowrap;
    transition: background 0.2s, transform 0.1s;
    margin-top: 0;
  }

  .lookup-btn:hover { background: var(--blue); }
  .lookup-btn:active { transform: scale(0.97); }

  .nearby-info {
    margin-top: 10px;
    font-size: 0.8rem;
    color: var(--slate);
    background: var(--ice);
    border-radius: 8px;
    padding: 8px 12px;
    display: none;
  }

  .nearby-info.show { display: block; }

  /* Radio / Checkbox cards */
  .options-grid {
    display: grid;
    gap: 10px;
  }

  .options-grid.cols-2 { grid-template-columns: 1fr 1fr; }

  @media (max-width: 500px) { .options-grid.cols-2 { grid-template-columns: 1fr; } }

  .opt-card {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 13px 16px;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    cursor: pointer;
    transition: border-color 0.15s, background 0.15s;
    background: #f8fbff;
    user-select: none;
    line-height: 1.35;
    font-size: 0.88rem;
    color: var(--navy);
  }

  .opt-card:hover { border-color: var(--sky); background: var(--ice); }

  .opt-card input[type="radio"],
  .opt-card input[type="checkbox"] {
    width: 18px;
    height: 18px;
    border: 2px solid var(--border);
    border-radius: 4px;
    background: white;
    flex-shrink: 0;
    appearance: none;
    -webkit-appearance: none;
    cursor: pointer;
    margin-top: 1px;
    transition: border-color 0.15s, background 0.15s;
    padding: 0;
    box-shadow: none;
  }

  .opt-card input[type="radio"] { border-radius: 50%; }

  .opt-card input[type="radio"]:checked,
  .opt-card input[type="checkbox"]:checked {
    background: var(--blue);
    border-color: var(--blue);
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='10' viewBox='0 0 10 10'%3E%3Cpath d='M8.5 2L4 7.5 1.5 5' stroke='white' stroke-width='1.8' fill='none' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: center;
  }

  .opt-card input[type="radio"]:checked {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='8' height='8' viewBox='0 0 8 8'%3E%3Ccircle cx='4' cy='4' r='3' fill='white'/%3E%3C/svg%3E");
  }

  .opt-card:has(input:checked) {
    border-color: var(--blue);
    background: #eef5ff;
  }

  /* Number input with stepper */
  .number-wrap {
    display: flex;
    align-items: center;
    gap: 0;
    border: 1.5px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    background: #f8fbff;
    width: fit-content;
    min-width: 160px;
  }

  .number-wrap button {
    width: 44px;
    height: 48px;
    border: none;
    background: transparent;
    font-size: 1.3rem;
    color: var(--navy);
    cursor: pointer;
    flex-shrink: 0;
    transition: background 0.15s;
  }

  .number-wrap button:hover { background: var(--ice); }

  .number-wrap input {
    border: none;
    border-radius: 0;
    border-left: 1px solid var(--border);
    border-right: 1px solid var(--border);
    text-align: center;
    width: 70px;
    background: white;
    box-shadow: none;
    padding: 13px 8px;
  }

  .number-wrap input:focus { box-shadow: none; border-color: var(--border); }

  /* Conditional textarea */
  .conditional-textarea {
    margin-top: 10px;
    display: none;
  }

  .conditional-textarea.show { display: block; }

  /* Submit button */
  .submit-wrap {
    text-align: center;
    margin-top: 36px;
    animation: fadeUp 0.5s 0.3s ease both;
  }

  .submit-btn {
    display: inline-flex;
    align-items: center;
    gap: 12px;
    padding: 18px 52px;
    background: linear-gradient(135deg, var(--sky) 0%, var(--blue) 100%);
    color: white;
    border: none;
    border-radius: 99px;
    font-family: 'DM Sans', sans-serif;
    font-size: 1rem;
    font-weight: 600;
    letter-spacing: 0.02em;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 8px 32px rgba(27,79,138,0.45);
  }

  .submit-btn:hover { transform: translateY(-2px); box-shadow: 0 12px 40px rgba(27,79,138,0.55); }
  .submit-btn:active { transform: scale(0.98); }

  .submit-btn svg { width: 20px; height: 20px; }

  .submit-btn.loading { opacity: 0.7; pointer-events: none; }

  /* Loading spinner */
  @keyframes spin { to { transform: rotate(360deg); } }
  .spinner { animation: spin 0.8s linear infinite; }

  /* Thank you overlay */
  #thank-you {
    display: none;
    position: fixed;
    inset: 0;
    background: linear-gradient(160deg, #0d1b2a 0%, #1b3a6b 100%);
    z-index: 1000;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    padding: 40px;
  }

  #thank-you.show { display: flex; animation: fadeIn 0.5s ease; }

  .ty-icon {
    width: 88px;
    height: 88px;
    background: linear-gradient(135deg, #22c55e, #16a34a);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto 28px;
    box-shadow: 0 8px 40px rgba(34,197,94,0.45);
    animation: popIn 0.5s 0.2s cubic-bezier(.34,1.56,.64,1) both;
  }

  .ty-icon svg { width: 44px; height: 44px; stroke: white; stroke-width: 3; fill: none; }

  .ty-title {
    font-family: 'DM Serif Display', serif;
    font-size: clamp(2rem, 6vw, 3.5rem);
    color: white;
    margin-bottom: 16px;
    animation: fadeUp 0.5s 0.3s ease both;
  }

  .ty-text {
    color: rgba(255,255,255,0.7);
    font-size: 1.05rem;
    max-width: 420px;
    line-height: 1.6;
    animation: fadeUp 0.5s 0.4s ease both;
  }

  .ty-note {
    margin-top: 28px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 16px;
    padding: 20px 28px;
    color: rgba(255,255,255,0.6);
    font-size: 0.88rem;
    max-width: 400px;
    animation: fadeUp 0.5s 0.5s ease both;
  }

  /* Animations */
  @keyframes fadeDown { from { opacity:0; transform:translateY(-18px); } to { opacity:1; transform:none; } }
  @keyframes fadeUp   { from { opacity:0; transform:translateY(18px);  } to { opacity:1; transform:none; } }
  @keyframes fadeIn   { from { opacity:0; } to { opacity:1; } }
  @keyframes popIn    { from { opacity:0; transform:scale(0.5); } to { opacity:1; transform:scale(1); } }

  /* Divider */
  .q-divider { border: none; border-top: 1px solid var(--ice); margin: 24px 0; }

  /* Helper text */
  .helper { font-size: 0.78rem; color: var(--slate); margin-top: 5px; }

  /* Responsive */
  @media (max-width: 600px) {
    .section-card { padding: 24px 20px; }
    h1 { font-size: 1.9rem; }
  }
</style>
</head>
<body>

<div class="container">

  <div class="header">
    <div class="logo-mark">
      <svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
      </svg>
    </div>
    <h1>Get Your Free Quote</h1>
    <p class="subtitle">Tell us about your property and we'll get back to you promptly</p>
  </div>

  <div class="progress-wrap">
    <div class="progress-bar" id="progressBar"></div>
  </div>

  <form id="quoteForm" novalidate>

    <!-- ── SECTION 1: YOUR DETAILS ── -->
    <div class="section-card">
      <div class="section-label">
        <svg viewBox="0 0 16 16" fill="currentColor"><path d="M8 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm4 2H4a2 2 0 0 0-2 2v1h12v-1a2 2 0 0 0-2-2z"/></svg>
        Your Details
      </div>

      <!-- Q1 Name -->
      <div class="q-group">
        <label class="q-label" for="name"><span class="num">1</span>Full Name</label>
        <input type="text" id="name" name="name" placeholder="e.g. John Smith" autocomplete="name" required>
        <div class="field-error" id="name-err">Please enter your full name.</div>
      </div>

      <!-- Q2 Telephone -->
      <div class="q-group">
        <label class="q-label" for="phone"><span class="num">2</span>Telephone Number</label>
        <input type="tel" id="phone" name="phone" placeholder="e.g. 07700 900000" autocomplete="tel" required>
        <div class="field-error" id="phone-err">Please enter a valid phone number.</div>
      </div>

      <!-- Q3 Email -->
      <div class="q-group">
        <label class="q-label" for="email"><span class="num">3</span>Email Address</label>
        <input type="email" id="email" name="email" placeholder="e.g. hello@email.com" autocomplete="email" required>
        <div class="field-error" id="email-err">Please enter a valid email address.</div>
      </div>

      <!-- Q4 Address + Postcode -->
      <div class="q-group">
        <label class="q-label" for="address"><span class="num">4</span>Full Address</label>
        <textarea id="address" name="address" placeholder="House number, Street, Town, County" required style="min-height:80px;"></textarea>
        <div class="field-error" id="address-err">Please enter your full address.</div>
        <div style="margin-top:12px;">
          <label class="q-label" for="postcode" style="margin-bottom:8px;font-size:0.85rem;color:var(--slate);">Postcode</label>
          <div class="postcode-row">
            <input type="text" id="postcode" name="postcode" placeholder="e.g. RH6 0AA" style="text-transform:uppercase;" required>
            <button type="button" class="lookup-btn" onclick="lookupPostcode()">Find Area</button>
          </div>
          <div class="field-error" id="postcode-err">Please enter a valid UK postcode.</div>
          <div class="nearby-info" id="nearbyInfo"></div>
        </div>
      </div>
    </div>

    <!-- ── SECTION 2: YOUR PROPERTY ── -->
    <div class="section-card">
      <div class="section-label">
        <svg viewBox="0 0 16 16" fill="currentColor"><path d="M6.5 14.5v-3.505c0-.245.25-.495.5-.495h2c.25 0 .5.25.5.5v3.5a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5v-7a.5.5 0 0 0-.146-.354L13 5.793V2.5a.5.5 0 0 0-.5-.5h-1a.5.5 0 0 0-.5.5v1.293L8.354 1.146a.5.5 0 0 0-.708 0l-6 6A.5.5 0 0 0 1.5 7.5v7a.5.5 0 0 0 .5.5h4a.5.5 0 0 0 .5-.5z"/></svg>
        Your Property
      </div>

      <!-- Q5 Property type -->
      <div class="q-group">
        <label class="q-label" for="propType"><span class="num">5</span>What type of property needs cleaning?</label>
        <select id="propType" name="propType" required>
          <option value="" disabled selected>Select property type…</option>
          <option value="Semi">Semi-detached</option>
          <option value="Detached">Detached</option>
          <option value="Tera">Terraced</option>
          <option value="Other">Other</option>
        </select>
        <div class="field-error" id="propType-err">Please select a property type.</div>
      </div>

      <hr class="q-divider">

      <!-- Q6 Number of windows -->
      <div class="q-group">
        <label class="q-label"><span class="num">6</span>How many windows are there?</label>
        <div class="number-wrap">
          <button type="button" onclick="stepNum('numWindows',-1)">−</button>
          <input type="number" id="numWindows" name="numWindows" value="0" min="0" max="99" required>
          <button type="button" onclick="stepNum('numWindows',1)">+</button>
        </div>
        <div class="field-error" id="numWindows-err">Please enter the number of windows.</div>
      </div>

      <hr class="q-divider">

      <!-- Q7 Window size -->
      <div class="q-group">
        <label class="q-label"><span class="num">7</span>What type of windows are they?</label>
        <div class="options-grid cols-2">
          <label class="opt-card">
            <input type="radio" name="windowSize" value="Sml" required>
            Small
          </label>
          <label class="opt-card">
            <input type="radio" name="windowSize" value="Medium">
            Medium
          </label>
          <label class="opt-card">
            <input type="radio" name="windowSize" value="LRGE">
            Large
          </label>
        </div>
        <div class="field-error" id="windowSize-err">Please select a window size.</div>
      </div>

      <hr class="q-divider">

      <!-- Q8 Clean type -->
      <div class="q-group">
        <label class="q-label"><span class="num">8</span>What needs cleaning this time?</label>
        <div class="options-grid">
          <label class="opt-card"><input type="radio" name="cleanType" value="Ext" required>Outside windows only</label>
          <label class="opt-card"><input type="radio" name="cleanType" value="Ext + Doors">Outside windows and glass doors</label>
          <label class="opt-card"><input type="radio" name="cleanType" value="Int + Ext">Inside and outside of windows</label>
          <label class="opt-card"><input type="radio" name="cleanType" value="All">Inside and outside of windows and glass doors</label>
        </div>
        <div class="field-error" id="cleanType-err">Please select what needs cleaning.</div>
      </div>

      <hr class="q-divider">

      <!-- Q9 Stories -->
      <div class="q-group">
        <label class="q-label"><span class="num">9</span>How many storeys are there?</label>
        <div class="number-wrap">
          <button type="button" onclick="stepNum('numFloors',-1)">−</button>
          <input type="number" id="numFloors" name="numFloors" value="1" min="1" max="10" required>
          <button type="button" onclick="stepNum('numFloors',1)">+</button>
        </div>
        <div class="field-error" id="numFloors-err">Please enter the number of storeys.</div>
      </div>

      <hr class="q-divider">

      <!-- Q10 Roof windows -->
      <div class="q-group">
        <label class="q-label"><span class="num">10</span>Are there any roof windows?</label>
        <div class="number-wrap">
          <button type="button" onclick="stepNum('roofWindows',-1)">−</button>
          <input type="number" id="roofWindows" name="roofWindows" value="0" min="0" max="30">
          <button type="button" onclick="stepNum('roofWindows',1)">+</button>
        </div>
        <p class="helper">Enter 0 if none</p>
      </div>

      <hr class="q-divider">

      <!-- Q11 Other glass -->
      <div class="q-group">
        <label class="q-label"><span class="num">11</span>Any other glass? (e.g. glass balcony)</label>
        <div class="options-grid cols-2">
          <label class="opt-card"><input type="radio" name="otherGlass" value="No" required onchange="toggleGlassDesc(this)">No</label>
          <label class="opt-card"><input type="radio" name="otherGlass" value="Yes" onchange="toggleGlassDesc(this)">Yes</label>
        </div>
        <div class="field-error" id="otherGlass-err">Please select an option.</div>
        <div class="conditional-textarea" id="glassDescWrap">
          <textarea id="glassDesc" name="glassDesc" placeholder="Please describe the other glass areas…"></textarea>
        </div>
      </div>

      <hr class="q-divider">

      <!-- Q12 Access -->
      <div class="q-group">
        <label class="q-label"><span class="num">12</span>Are all windows easy to access? (Will ladders / scaffold be required?)</label>
        <div class="options-grid">
          <label class="opt-card"><input type="radio" name="access" value="Yes" required>Yes – all easily accessible</label>
          <label class="opt-card"><input type="radio" name="access" value="Ladder/Scaff">No – will need a ladder / scaffold</label>
        </div>
        <div class="field-error" id="access-err">Please select an access option.</div>
      </div>

      <hr class="q-divider">

      <!-- Q13 Extras (multi-tick) -->
      <div class="q-group">
        <label class="q-label"><span class="num">13</span>Are there any extras to include?</label>
        <div class="options-grid">
          <label class="opt-card"><input type="checkbox" name="extras" value="None" onchange="handleExtras(this)">No – just standard windows / glass doors</label>
          <label class="opt-card"><input type="checkbox" name="extras" value="F" onchange="handleExtras(this)">Fascias</label>
          <label class="opt-card"><input type="checkbox" name="extras" value="S" onchange="handleExtras(this)">Soffits</label>
          <label class="opt-card"><input type="checkbox" name="extras" value="SP" onchange="handleExtras(this)">Solar panels</label>
          <label class="opt-card"><input type="checkbox" name="extras" value="xSML" onchange="handleExtras(this)">One extra area (small conservatory / up to 3 skylights / balcony panels up to 3m)</label>
          <label class="opt-card"><input type="checkbox" name="extras" value="xM/L" onchange="handleExtras(this)">Medium–large conservatory / 3+ skylights / balcony panels over 3m</label>
        </div>
        <div class="field-error" id="extras-err">Please select at least one option.</div>
      </div>
    </div>

    <!-- ── SECTION 3: CLEAN HISTORY ── -->
    <div class="section-card">
      <div class="section-label">
        <svg viewBox="0 0 16 16" fill="currentColor"><path d="M3.5 0a.5.5 0 0 1 .5.5V1h8V.5a.5.5 0 0 1 1 0V1h1a2 2 0 0 1 2 2v11a2 2 0 0 1-2 2H2a2 2 0 0 1-2-2V3a2 2 0 0 1 2-2h1V.5a.5.5 0 0 1 .5-.5z"/></svg>
        Clean History &amp; Schedule
      </div>

      <!-- Q14 Last cleaned -->
      <div class="q-group">
        <label class="q-label" for="lastCleaned"><span class="num">14</span>When was your property last cleaned?</label>
        <input type="date" id="lastCleaned" name="lastCleaned" required>
        <div class="field-error" id="lastCleaned-err">Please select a date.</div>
      </div>

      <hr class="q-divider">

      <!-- Q15 Frequency -->
      <div class="q-group">
        <label class="q-label"><span class="num">15</span>How often would you like the clean?</label>
        <div class="options-grid">
          <label class="opt-card"><input type="radio" name="frequency" value="+12mnths" required>Intensive one-off clean (previous clean was over 12 months ago)</label>
          <label class="opt-card"><input type="radio" name="frequency" value="6-12mnths">One-off clean (previous clean was 6–12 months ago)</label>
          <label class="opt-card"><input type="radio" name="frequency" value="4 weeks">Regular clean every 4 weeks</label>
          <label class="opt-card"><input type="radio" name="frequency" value="6 weeks">Regular clean every 6 weeks</label>
          <label class="opt-card"><input type="radio" name="frequency" value="8 weeks">Regular clean every 8 weeks</label>
          <label class="opt-card"><input type="radio" name="frequency" value="12 weeks">Regular clean every 12 weeks</label>
        </div>
        <div class="field-error" id="frequency-err">Please select a cleaning frequency.</div>
      </div>
    </div>

    <!-- Submit -->
    <div class="submit-wrap">
      <button type="submit" class="submit-btn" id="submitBtn">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><path d="M22 2L11 13M22 2L15 22l-4-9-9-4 20-7z"/></svg>
        Submit &amp; Get My Quote
      </button>
      <p style="color:rgba(255,255,255,0.45);font-size:0.78rem;margin-top:14px;">
        We'll send your quotation confirmation to the email address provided.
      </p>
    </div>

  </form>
</div>

<!-- Thank you page -->
<div id="thank-you">
  <div class="ty-icon">
    <svg viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12"/></svg>
  </div>
  <h2 class="ty-title">Thank You!</h2>
  <p class="ty-text">Your quote request has been received. We'll review your details and be in touch very soon.</p>
  <div class="ty-note">
    📧 A confirmation email has been sent to your inbox — please check your spam folder if you don't see it within a few minutes.
  </div>
</div>

<script>
// ── CONFIGURATION ──────────────────────────────────────────────
// Replace with your deployed Google Apps Script Web App URL:
const APPS_SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec';

// ── PROGRESS BAR ───────────────────────────────────────────────
function updateProgress() {
  const required = document.querySelectorAll('[required]');
  let filled = 0;
  required.forEach(el => {
    if (el.type === 'radio') {
      if (document.querySelector(`[name="${el.name}"]:checked`)) filled++;
    } else if (el.value.trim() !== '' && el.value !== '0') {
      filled++;
    }
  });
  // Deduplicate radio groups
  const radioGroups = new Set([...document.querySelectorAll('[type="radio"][required]')].map(r => r.name));
  const checkedGroups = [...radioGroups].filter(n => document.querySelector(`[name="${n}"]:checked`));
  const totalRadioRequired = radioGroups.size;
  const filledRadio = checkedGroups.length;
  const nonRadioRequired = [...required].filter(el => el.type !== 'radio');
  const filledNonRadio = nonRadioRequired.filter(el => el.value.trim() !== '' && el.value !== '0').length;
  const total = totalRadioRequired + nonRadioRequired.length;
  const done  = filledRadio + filledNonRadio;
  document.getElementById('progressBar').style.width = Math.round((done / total) * 100) + '%';
}

document.querySelectorAll('input,select,textarea').forEach(el => {
  el.addEventListener('change', updateProgress);
  el.addEventListener('input', updateProgress);
});

// ── NUMBER STEPPER ─────────────────────────────────────────────
function stepNum(id, delta) {
  const el = document.getElementById(id);
  const min = parseInt(el.min) || 0;
  const max = parseInt(el.max) || 999;
  el.value = Math.min(max, Math.max(min, parseInt(el.value || 0) + delta));
  updateProgress();
}

// ── TOGGLE GLASS DESCRIPTION ───────────────────────────────────
function toggleGlassDesc(radio) {
  document.getElementById('glassDescWrap').classList.toggle('show', radio.value === 'Yes');
}

// ── EXTRAS CHECKBOXES ─────────────────────────────────────────
function handleExtras(cb) {
  const allBoxes = document.querySelectorAll('[name="extras"]');
  if (cb.value === 'None' && cb.checked) {
    allBoxes.forEach(b => { if (b.value !== 'None') b.checked = false; });
  } else if (cb.value !== 'None' && cb.checked) {
    document.querySelector('[name="extras"][value="None"]').checked = false;
  }
  updateProgress();
}

function getExtrasValue() {
  const checked = [...document.querySelectorAll('[name="extras"]:checked')].map(c => c.value);
  if (!checked.length) return '';
  if (checked.includes('None')) return 'None';
  // Check if all non-None options are selected
  const allVals = ['F','S','SP','xSML','xM/L'];
  if (allVals.every(v => checked.includes(v))) return 'All';
  return checked.filter(v => v !== 'None').join(' + ');
}

// ── POSTCODE LOOKUP ────────────────────────────────────────────
function lookupPostcode() {
  const pc = document.getElementById('postcode').value.trim().toUpperCase();
  const infoDiv = document.getElementById('nearbyInfo');
  if (!pc || !/^[A-Z]{1,2}[0-9][0-9A-Z]?\s?[0-9][A-Z]{2}$/.test(pc)) {
    infoDiv.innerHTML = '⚠️ Please enter a valid UK postcode first.';
    infoDiv.classList.add('show');
    return;
  }
  infoDiv.innerHTML = '🔍 Looking up postcode area…';
  infoDiv.classList.add('show');
  fetch(`https://api.postcodes.io/postcodes/${encodeURIComponent(pc)}`)
    .then(r => r.json())
    .then(data => {
      if (data.status === 200) {
        const r = data.result;
        infoDiv.innerHTML = `📍 <strong>${r.admin_ward || r.parish || ''}</strong>, ${r.admin_district || ''}, ${r.region || ''} &mdash; Area confirmed.`;
      } else {
        infoDiv.innerHTML = '⚠️ Postcode not found. Please check and re-enter.';
      }
    })
    .catch(() => {
      infoDiv.innerHTML = '⚠️ Could not verify postcode right now &mdash; please check it is correct.';
    });
}

// Auto-uppercase postcode as typed
document.getElementById('postcode').addEventListener('input', function() {
  this.value = this.value.toUpperCase();
});

// ── VALIDATION ─────────────────────────────────────────────────
function showError(id, show) {
  const el = document.getElementById(id + '-err');
  if (el) el.classList.toggle('show', show);
}
function markField(id, isError) {
  const el = document.getElementById(id);
  if (el) el.classList.toggle('error', isError);
}

function validateForm() {
  let valid = true;

  // Text fields
  const textFields = [
    { id: 'name',     test: v => v.trim().split(' ').length >= 2 },
    { id: 'phone',    test: v => /^[\d\s\+\-\(\)]{7,15}$/.test(v.trim()) },
    { id: 'email',    test: v => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(v.trim()) },
    { id: 'address',  test: v => v.trim().length > 5 },
    { id: 'postcode', test: v => /^[A-Z]{1,2}[0-9][0-9A-Z]?\s?[0-9][A-Z]{2}$/i.test(v.trim()) },
    { id: 'numWindows', test: v => parseInt(v) >= 0 },
    { id: 'numFloors',  test: v => parseInt(v) >= 1 },
    { id: 'lastCleaned', test: v => v !== '' },
  ];

  textFields.forEach(({id, test}) => {
    const el = document.getElementById(id);
    const ok = el && test(el.value);
    markField(id, !ok);
    showError(id, !ok);
    if (!ok) valid = false;
  });

  // Select
  const propType = document.getElementById('propType').value;
  markField('propType', !propType);
  showError('propType', !propType);
  if (!propType) valid = false;

  // Radios
  const radioGroups = ['windowSize','cleanType','otherGlass','access','frequency'];
  radioGroups.forEach(name => {
    const checked = !!document.querySelector(`[name="${name}"]:checked`);
    showError(name, !checked);
    if (!checked) valid = false;
  });

  // Extras checkbox
  const extrasChecked = document.querySelectorAll('[name="extras"]:checked').length > 0;
  showError('extras', !extrasChecked);
  if (!extrasChecked) valid = false;

  return valid;
}

// ── SUBMIT ─────────────────────────────────────────────────────
document.getElementById('quoteForm').addEventListener('submit', async function(e) {
  e.preventDefault();

  if (!validateForm()) {
    document.querySelector('.error, .field-error.show')?.scrollIntoView({behavior:'smooth', block:'center'});
    return;
  }

  const btn = document.getElementById('submitBtn');
  btn.classList.add('loading');
  btn.innerHTML = `
    <svg class="spinner" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" width="20" height="20">
      <path d="M12 2v4M12 18v4M4.93 4.93l2.83 2.83M16.24 16.24l2.83 2.83M2 12h4M18 12h4M4.93 19.07l2.83-2.83M16.24 7.76l2.83-2.83"/>
    </svg>
    Sending…`;

  // Build payload
  const get = id => document.getElementById(id)?.value?.trim() || '';
  const radio = name => document.querySelector(`[name="${name}"]:checked`)?.value || '';

  const payload = {
    Initials:       get('name'),
    Phone:          get('phone'),
    Email:          get('email'),
    PostCode:       get('postcode').toUpperCase(),
    FullAddress:    get('address'),
    Style:          document.getElementById('propType').value,
    'No.Windows':   get('numWindows'),
    Size:           radio('windowSize'),
    'Clean Type':   radio('cleanType'),
    Floors:         get('numFloors'),
    'Roof Wnds':    get('roofWindows'),
    'Other Glass':  radio('otherGlass'),
    'Glass Detail': get('glassDesc'),
    Access:         radio('access'),
    Extras:         getExtrasValue(),
    Prev:           get('lastCleaned'),
    Frequency:      radio('frequency'),
  };

  try {
    await fetch(APPS_SCRIPT_URL, {
      method: 'POST',
      mode: 'no-cors',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(payload),
    });
  } catch(err) {
    console.warn('Submission note:', err);
  }

  // Show thank-you regardless (no-cors won't return readable response)
  document.getElementById('thank-you').classList.add('show');
  document.body.style.overflow = 'hidden';
});
</script>
</body>
</html>
