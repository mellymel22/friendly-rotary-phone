<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TaxPro CPA — Tax Filing Platform</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d1117;
    --surface: #161b22;
    --surface2: #1e2530;
    --border: #2a3344;
    --accent: #e8c547;
    --accent2: #4da8da;
    --success: #3fb950;
    --danger: #f85149;
    --warn: #e3b341;
    --text: #e6edf3;
    --muted: #7d8590;
    --dim: #3d4555;
  }
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    display: flex;
    overflow: hidden;
  }

/* SIDEBAR */
.sidebar {
width: 240px;
min-width: 240px;
background: var(–surface);
border-right: 1px solid var(–border);
display: flex;
flex-direction: column;
padding: 0;
height: 100vh;
position: sticky;
top: 0;
}
.logo {
padding: 24px 20px 20px;
border-bottom: 1px solid var(–border);
}
.logo-title {
font-family: ‘DM Serif Display’, serif;
font-size: 22px;
color: var(–accent);
letter-spacing: -0.5px;
}
.logo-sub {
font-size: 11px;
color: var(–muted);
letter-spacing: 2px;
text-transform: uppercase;
margin-top: 2px;
font-family: ‘DM Mono’, monospace;
}
.nav {
padding: 16px 12px;
flex: 1;
overflow-y: auto;
}
.nav-section {
font-size: 10px;
text-transform: uppercase;
letter-spacing: 1.5px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
padding: 8px 8px 6px;
margin-top: 8px;
}
.nav-item {
display: flex;
align-items: center;
gap: 10px;
padding: 9px 10px;
border-radius: 6px;
cursor: pointer;
font-size: 13.5px;
color: var(–muted);
transition: all 0.15s;
margin-bottom: 2px;
font-weight: 400;
}
.nav-item:hover { background: var(–surface2); color: var(–text); }
.nav-item.active { background: rgba(232,197,71,0.12); color: var(–accent); font-weight: 500; }
.nav-item .icon { width: 16px; text-align: center; font-size: 14px; }
.nav-badge {
margin-left: auto;
background: var(–accent);
color: #000;
font-size: 10px;
font-weight: 600;
padding: 1px 6px;
border-radius: 20px;
font-family: ‘DM Mono’, monospace;
}
.sidebar-footer {
padding: 16px;
border-top: 1px solid var(–border);
font-size: 12px;
color: var(–muted);
}
.year-badge {
display: inline-flex;
align-items: center;
gap: 6px;
background: rgba(232,197,71,0.1);
border: 1px solid rgba(232,197,71,0.3);
color: var(–accent);
padding: 4px 10px;
border-radius: 4px;
font-family: ‘DM Mono’, monospace;
font-size: 12px;
font-weight: 500;
margin-bottom: 8px;
cursor: pointer;
}

/* MAIN */
.main {
flex: 1;
display: flex;
flex-direction: column;
height: 100vh;
overflow: hidden;
}
.topbar {
background: var(–surface);
border-bottom: 1px solid var(–border);
padding: 14px 28px;
display: flex;
align-items: center;
justify-content: space-between;
min-height: 60px;
}
.topbar-title {
font-family: ‘DM Serif Display’, serif;
font-size: 19px;
color: var(–text);
}
.topbar-actions { display: flex; gap: 10px; align-items: center; }
.btn {
padding: 8px 16px;
border-radius: 6px;
font-size: 13px;
font-weight: 500;
cursor: pointer;
border: none;
transition: all 0.15s;
font-family: ‘DM Sans’, sans-serif;
}
.btn-primary {
background: var(–accent);
color: #000;
}
.btn-primary:hover { background: #f0cf5a; }
.btn-ghost {
background: transparent;
color: var(–muted);
border: 1px solid var(–border);
}
.btn-ghost:hover { color: var(–text); border-color: var(–dim); background: var(–surface2); }
.btn-sm { padding: 5px 12px; font-size: 12px; }
.btn-danger { background: rgba(248,81,73,0.15); color: var(–danger); border: 1px solid rgba(248,81,73,0.3); }
.btn-success { background: rgba(63,185,80,0.15); color: var(–success); border: 1px solid rgba(63,185,80,0.3); }

.content {
flex: 1;
overflow-y: auto;
padding: 28px;
}

/* PAGES */
.page { display: none; }
.page.active { display: block; }

/* DASHBOARD */
.stats-grid {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 16px;
margin-bottom: 28px;
}
.stat-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 20px;
position: relative;
overflow: hidden;
}
.stat-card::before {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0;
height: 2px;
background: var(–accent);
opacity: 0.5;
}
.stat-label { font-size: 11px; color: var(–muted); text-transform: uppercase; letter-spacing: 1px; font-family: ‘DM Mono’, monospace; }
.stat-value { font-family: ‘DM Serif Display’, serif; font-size: 32px; color: var(–text); margin: 6px 0 4px; }
.stat-change { font-size: 12px; color: var(–success); }
.stat-change.neg { color: var(–danger); }
.stat-icon { position: absolute; right: 16px; top: 16px; font-size: 22px; opacity: 0.3; }

.dashboard-grid {
display: grid;
grid-template-columns: 1.5fr 1fr;
gap: 20px;
}
.card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 20px;
}
.card-header {
display: flex;
justify-content: space-between;
align-items: center;
margin-bottom: 16px;
}
.card-title {
font-size: 14px;
font-weight: 600;
color: var(–text);
}
.card-muted { font-size: 12px; color: var(–muted); }

.recent-table { width: 100%; border-collapse: collapse; }
.recent-table th {
text-align: left;
font-size: 10px;
text-transform: uppercase;
letter-spacing: 1px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
padding: 6px 8px;
border-bottom: 1px solid var(–border);
}
.recent-table td {
padding: 10px 8px;
font-size: 13px;
border-bottom: 1px solid rgba(42,51,68,0.5);
}
.recent-table tr:last-child td { border-bottom: none; }
.status-pill {
display: inline-block;
padding: 2px 9px;
border-radius: 20px;
font-size: 11px;
font-weight: 500;
font-family: ‘DM Mono’, monospace;
}
.status-filed { background: rgba(63,185,80,0.15); color: var(–success); }
.status-review { background: rgba(232,197,71,0.15); color: var(–warn); }
.status-draft { background: rgba(125,133,144,0.15); color: var(–muted); }
.status-urgent { background: rgba(248,81,73,0.15); color: var(–danger); }

.deadline-item {
display: flex;
align-items: center;
justify-content: space-between;
padding: 10px 0;
border-bottom: 1px solid rgba(42,51,68,0.5);
font-size: 13px;
}
.deadline-item:last-child { border-bottom: none; }
.deadline-days {
font-family: ‘DM Mono’, monospace;
font-size: 12px;
padding: 2px 8px;
border-radius: 4px;
}
.days-red { background: rgba(248,81,73,0.15); color: var(–danger); }
.days-yellow { background: rgba(227,179,65,0.15); color: var(–warn); }
.days-green { background: rgba(63,185,80,0.15); color: var(–success); }

/* CLIENTS PAGE */
.search-bar {
display: flex;
gap: 10px;
margin-bottom: 20px;
}
.search-input {
flex: 1;
background: var(–surface);
border: 1px solid var(–border);
border-radius: 6px;
padding: 9px 14px;
font-size: 13px;
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
outline: none;
transition: border-color 0.15s;
}
.search-input:focus { border-color: var(–accent); }
.search-input::placeholder { color: var(–muted); }

.clients-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 16px;
}
.client-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 18px;
cursor: pointer;
transition: all 0.15s;
}
.client-card:hover { border-color: var(–accent); transform: translateY(-1px); }
.client-avatar {
width: 40px; height: 40px;
border-radius: 50%;
display: flex; align-items: center; justify-content: center;
font-weight: 700;
font-size: 15px;
margin-bottom: 12px;
color: #000;
}
.client-name { font-size: 14px; font-weight: 600; margin-bottom: 2px; }
.client-type { font-size: 11px; color: var(–muted); font-family: ‘DM Mono’, monospace; text-transform: uppercase; letter-spacing: 0.5px; }
.client-meta { margin-top: 12px; display: flex; justify-content: space-between; align-items: center; }
.client-ein { font-size: 11px; font-family: ‘DM Mono’, monospace; color: var(–muted); }

/* MODAL */
.modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(0,0,0,0.7);
z-index: 100;
align-items: center;
justify-content: center;
backdrop-filter: blur(4px);
}
.modal-overlay.open { display: flex; }
.modal {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 12px;
width: 560px;
max-height: 85vh;
overflow-y: auto;
padding: 28px;
position: relative;
}
.modal-title {
font-family: ‘DM Serif Display’, serif;
font-size: 20px;
margin-bottom: 4px;
}
.modal-sub { font-size: 12px; color: var(–muted); margin-bottom: 22px; }
.modal-close {
position: absolute;
right: 18px; top: 18px;
background: transparent;
border: none;
color: var(–muted);
font-size: 20px;
cursor: pointer;
width: 28px; height: 28px;
display: flex; align-items: center; justify-content: center;
border-radius: 4px;
}
.modal-close:hover { background: var(–surface2); color: var(–text); }

.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; margin-bottom: 14px; }
.form-group { margin-bottom: 14px; }
.form-label { font-size: 11px; color: var(–muted); text-transform: uppercase; letter-spacing: 0.8px; margin-bottom: 5px; display: block; font-family: ‘DM Mono’, monospace; }
.form-input, .form-select {
width: 100%;
background: var(–bg);
border: 1px solid var(–border);
border-radius: 6px;
padding: 9px 12px;
font-size: 13px;
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
outline: none;
transition: border-color 0.15s;
}
.form-input:focus, .form-select:focus { border-color: var(–accent); }
.form-select option { background: var(–bg); }
.form-actions { display: flex; gap: 10px; justify-content: flex-end; margin-top: 20px; }

/* TAX FORMS PAGE */
.forms-list { display: flex; flex-direction: column; gap: 12px; }
.form-item {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 10px;
padding: 16px 20px;
display: flex;
align-items: center;
gap: 16px;
cursor: pointer;
transition: all 0.15s;
}
.form-item:hover { border-color: var(–accent2); }
.form-number {
font-family: ‘DM Serif Display’, serif;
font-size: 20px;
color: var(–accent);
min-width: 60px;
}
.form-desc { flex: 1; }
.form-desc-title { font-size: 14px; font-weight: 500; }
.form-desc-sub { font-size: 12px; color: var(–muted); margin-top: 2px; }
.form-action-area { display: flex; gap: 8px; align-items: center; }

/* CALCULATIONS */
.calc-layout {
display: grid;
grid-template-columns: 1.2fr 0.8fr;
gap: 20px;
}
.calc-section-title {
font-size: 11px;
text-transform: uppercase;
letter-spacing: 1.5px;
color: var(–muted);
font-family: ‘DM Mono’, monospace;
margin-bottom: 12px;
}
.calc-line {
display: flex;
align-items: center;
justify-content: space-between;
padding: 8px 0;
border-bottom: 1px solid rgba(42,51,68,0.5);
font-size: 13px;
}
.calc-line:last-child { border-bottom: none; }
.calc-line-label { color: var(–muted); }
.calc-line-value {
font-family: ‘DM Mono’, monospace;
font-size: 13px;
color: var(–text);
}
.calc-line-value input {
background: var(–bg);
border: 1px solid var(–border);
border-radius: 4px;
padding: 4px 8px;
font-size: 13px;
font-family: ‘DM Mono’, monospace;
color: var(–text);
width: 140px;
text-align: right;
outline: none;
}
.calc-line-value input:focus { border-color: var(–accent); }
.calc-total {
display: flex;
justify-content: space-between;
padding: 12px 0;
border-top: 2px solid var(–accent);
margin-top: 4px;
}
.calc-total-label { font-size: 14px; font-weight: 600; }
.calc-total-value {
font-family: ‘DM Serif Display’, serif;
font-size: 24px;
color: var(–accent);
}
.tax-bracket-row {
display: flex;
align-items: center;
padding: 8px 0;
font-size: 12px;
border-bottom: 1px solid rgba(42,51,68,0.4);
}
.bracket-rate {
font-family: ‘DM Mono’, monospace;
font-weight: 600;
width: 50px;
color: var(–accent2);
}
.bracket-range { color: var(–muted); flex: 1; }
.bracket-bar-wrap { width: 60px; height: 5px; background: var(–bg); border-radius: 3px; overflow: hidden; }
.bracket-bar { height: 100%; background: var(–accent2); border-radius: 3px; }

/* DOCUMENTS */
.doc-upload-area {
border: 2px dashed var(–border);
border-radius: 10px;
padding: 40px;
text-align: center;
cursor: pointer;
transition: all 0.15s;
margin-bottom: 20px;
}
.doc-upload-area:hover { border-color: var(–accent); background: rgba(232,197,71,0.03); }
.doc-upload-icon { font-size: 36px; margin-bottom: 10px; }
.doc-upload-text { font-size: 14px; font-weight: 500; margin-bottom: 4px; }
.doc-upload-sub { font-size: 12px; color: var(–muted); }
.doc-list { display: flex; flex-direction: column; gap: 10px; }
.doc-item {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 8px;
padding: 14px 16px;
display: flex;
align-items: center;
gap: 14px;
}
.doc-icon { font-size: 22px; }
.doc-info { flex: 1; }
.doc-name { font-size: 13px; font-weight: 500; }
.doc-meta { font-size: 11px; color: var(–muted); font-family: ‘DM Mono’, monospace; margin-top: 2px; }
.doc-actions { display: flex; gap: 6px; }

/* MISC */
.section-header {
display: flex;
justify-content: space-between;
align-items: flex-end;
margin-bottom: 20px;
}
.section-title {
font-family: ‘DM Serif Display’, serif;
font-size: 22px;
}
.section-sub { font-size: 12px; color: var(–muted); margin-top: 2px; }

.progress-wrap { background: var(–bg); border-radius: 4px; height: 6px; overflow: hidden; margin-top: 6px; }
.progress-bar { height: 100%; border-radius: 4px; background: var(–accent); transition: width 0.3s; }

.tab-bar {
display: flex;
gap: 0;
border-bottom: 1px solid var(–border);
margin-bottom: 20px;
}
.tab {
padding: 10px 18px;
font-size: 13px;
cursor: pointer;
color: var(–muted);
border-bottom: 2px solid transparent;
margin-bottom: -1px;
transition: all 0.15s;
}
.tab:hover { color: var(–text); }
.tab.active { color: var(–accent); border-bottom-color: var(–accent); }

.chip {
display: inline-block;
padding: 2px 8px;
border-radius: 4px;
font-size: 11px;
font-family: ‘DM Mono’, monospace;
background: var(–surface2);
color: var(–muted);
border: 1px solid var(–border);
}

/* Scrollbar */
::-webkit-scrollbar { width: 5px; height: 5px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: var(–dim); border-radius: 3px; }

.accent-line {
width: 3px; height: 14px;
background: var(–accent);
border-radius: 2px;
display: inline-block;
margin-right: 8px;
vertical-align: middle;
}

.notification {
position: fixed;
bottom: 24px;
right: 24px;
background: var(–surface);
border: 1px solid var(–success);
border-radius: 8px;
padding: 12px 18px;
font-size: 13px;
color: var(–success);
z-index: 200;
display: none;
box-shadow: 0 8px 24px rgba(0,0,0,0.4);
}
.notification.show { display: block; animation: slideIn 0.2s ease; }
@keyframes slideIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }
</style>

</head>
<body>

<!-- SIDEBAR -->

<div class="sidebar">
  <div class="logo">
    <div class="logo-title">TaxPro</div>
    <div class="logo-sub">CPA Platform · 2025</div>
  </div>
  <nav class="nav">
    <div class="nav-section">Workspace</div>
    <div class="nav-item active" onclick="navigate('dashboard', this)">
      <span class="icon">⊞</span> Dashboard
    </div>
    <div class="nav-item" onclick="navigate('clients', this)">
      <span class="icon">👥</span> Clients
      <span class="nav-badge">12</span>
    </div>
    <div class="nav-section">Filing</div>
    <div class="nav-item" onclick="navigate('forms', this)">
      <span class="icon">📋</span> Tax Forms
    </div>
    <div class="nav-item" onclick="navigate('calculations', this)">
      <span class="icon">🧮</span> Calculations
    </div>
    <div class="nav-item" onclick="navigate('documents', this)">
      <span class="icon">📁</span> Documents
    </div>
    <div class="nav-section">Compliance</div>
    <div class="nav-item" onclick="navigate('deadlines', this)">
      <span class="icon">📅</span> Deadlines
    </div>
    <div class="nav-item" onclick="navigate('reports', this)">
      <span class="icon">📊</span> Reports
    </div>
  </nav>
  <div class="sidebar-footer">
    <div class="year-badge" onclick="showYearPicker()">📆 Tax Year 2024 ▾</div>
    <div style="font-size:12px; color: var(--muted);">Sarah Chen, CPA</div>
    <div style="font-size:11px; color: var(--dim); margin-top:2px;">PTIN: P01234567</div>
  </div>
</div>

<!-- MAIN -->

<div class="main">
  <div class="topbar">
    <div class="topbar-title" id="page-title">Dashboard</div>
    <div class="topbar-actions">
      <span style="font-size:12px; color: var(--muted); font-family: 'DM Mono', monospace;">IRS e-File: <span style="color: var(--success);">● Online</span></span>
      <button class="btn btn-ghost btn-sm" onclick="showModal('new-client')">+ New Client</button>
      <button class="btn btn-primary btn-sm" onclick="showModal('new-return')">+ New Return</button>
    </div>
  </div>

  <div class="content">

```
<!-- DASHBOARD -->
<div class="page active" id="page-dashboard">
  <div class="stats-grid">
    <div class="stat-card">
      <div class="stat-icon">📁</div>
      <div class="stat-label">Active Returns</div>
      <div class="stat-value">47</div>
      <div class="stat-change">↑ 8 from last week</div>
    </div>
    <div class="stat-card" style="--accent: #4da8da;">
      <div class="stat-icon">✅</div>
      <div class="stat-label">Filed YTD</div>
      <div class="stat-value">183</div>
      <div class="stat-change">↑ 12% vs 2023</div>
    </div>
    <div class="stat-card" style="--accent: #f85149;">
      <div class="stat-icon">⚠️</div>
      <div class="stat-label">Needs Review</div>
      <div class="stat-value">9</div>
      <div class="stat-change neg">↑ 3 newly flagged</div>
    </div>
    <div class="stat-card" style="--accent: #3fb950;">
      <div class="stat-icon">💵</div>
      <div class="stat-label">Refunds Processed</div>
      <div class="stat-value">$2.1M</div>
      <div class="stat-change">↑ 18% vs 2023</div>
    </div>
  </div>

  <div class="dashboard-grid">
    <div class="card">
      <div class="card-header">
        <div class="card-title"><span class="accent-line"></span>Recent Returns</div>
        <span class="card-muted">Last 7 days</span>
      </div>
      <table class="recent-table">
        <thead>
          <tr>
            <th>Client</th>
            <th>Form</th>
            <th>Filed</th>
            <th>Status</th>
          </tr>
        </thead>
        <tbody>
          <tr><td>Anderson, Mark</td><td><span class="chip">1040</span></td><td>Feb 26</td><td><span class="status-pill status-filed">Filed</span></td></tr>
          <tr><td>Beacon LLC</td><td><span class="chip">1120-S</span></td><td>Feb 25</td><td><span class="status-pill status-review">In Review</span></td></tr>
          <tr><td>Torres, Elena</td><td><span class="chip">1040</span></td><td>Feb 25</td><td><span class="status-pill status-filed">Filed</span></td></tr>
          <tr><td>Summit Partners</td><td><span class="chip">1065</span></td><td>Feb 24</td><td><span class="status-pill status-urgent">Needs Action</span></td></tr>
          <tr><td>Kim, David</td><td><span class="chip">1040</span></td><td>Feb 23</td><td><span class="status-pill status-draft">Draft</span></td></tr>
          <tr><td>Hartley Corp</td><td><span class="chip">1120</span></td><td>Feb 22</td><td><span class="status-pill status-filed">Filed</span></td></tr>
        </tbody>
      </table>
    </div>
    <div class="card">
      <div class="card-header">
        <div class="card-title"><span class="accent-line"></span>Upcoming Deadlines</div>
        <button class="btn btn-ghost btn-sm" onclick="navigate('deadlines', null)">View All</button>
      </div>
      <div class="deadline-item">
        <div>
          <div style="font-size:13px; font-weight:500;">Form 1040 Extension</div>
          <div style="font-size:11px; color:var(--muted); margin-top:2px;">6 clients pending</div>
        </div>
        <span class="deadline-days days-red">4 days</span>
      </div>
      <div class="deadline-item">
        <div>
          <div style="font-size:13px; font-weight:500;">Form 1065 Partnership</div>
          <div style="font-size:11px; color:var(--muted); margin-top:2px;">3 clients</div>
        </div>
        <span class="deadline-days days-yellow">11 days</span>
      </div>
      <div class="deadline-item">
        <div>
          <div style="font-size:13px; font-weight:500;">Form 1120-S S-Corp</div>
          <div style="font-size:11px; color:var(--muted); margin-top:2px;">5 clients</div>
        </div>
        <span class="deadline-days days-yellow">11 days</span>
      </div>
      <div class="deadline-item">
        <div>
          <div style="font-size:13px; font-weight:500;">Form 1120 C-Corp</div>
          <div style="font-size:11px; color:var(--muted); margin-top:2px;">2 clients</div>
        </div>
        <span class="deadline-days days-green">46 days</span>
      </div>
      <div class="deadline-item">
        <div>
          <div style="font-size:13px; font-weight:500;">FBAR FinCEN 114</div>
          <div style="font-size:11px; color:var(--muted); margin-top:2px;">1 client</div>
        </div>
        <span class="deadline-days days-green">76 days</span>
      </div>
    </div>
  </div>
</div>

<!-- CLIENTS -->
<div class="page" id="page-clients">
  <div class="section-header">
    <div>
      <div class="section-title">Client Management</div>
      <div class="section-sub">12 active clients · Tax Year 2024</div>
    </div>
    <button class="btn btn-primary" onclick="showModal('new-client')">+ Add Client</button>
  </div>
  <div class="search-bar">
    <input class="search-input" placeholder="🔍  Search clients by name, EIN, or SSN..." oninput="filterClients(this.value)">
    <select class="form-select" style="width:140px;">
      <option>All Types</option>
      <option>Individual</option>
      <option>Business</option>
      <option>Partnership</option>
    </select>
  </div>
  <div class="clients-grid" id="clients-grid">
    <!-- generated by JS -->
  </div>
</div>

<!-- FORMS -->
<div class="page" id="page-forms">
  <div class="section-header">
    <div>
      <div class="section-title">IRS Tax Forms</div>
      <div class="section-sub">Select a form to begin filing</div>
    </div>
  </div>
  <div class="tab-bar">
    <div class="tab active" onclick="switchTab(this, 'forms-individual')">Individual</div>
    <div class="tab" onclick="switchTab(this, 'forms-business')">Business</div>
    <div class="tab" onclick="switchTab(this, 'forms-other')">Informational</div>
  </div>
  <div id="forms-individual" class="forms-tab">
    <div class="forms-list">
      <div class="form-item" onclick="openForm('1040')">
        <div class="form-number">1040</div>
        <div class="form-desc">
          <div class="form-desc-title">U.S. Individual Income Tax Return</div>
          <div class="form-desc-sub">For individual taxpayers · Due April 15, 2025</div>
        </div>
        <div class="form-action-area">
          <span class="status-pill status-review">4 Open</span>
          <button class="btn btn-primary btn-sm">Start Return</button>
        </div>
      </div>
      <div class="form-item" onclick="openForm('1040-SR')">
        <div class="form-number">1040-SR</div>
        <div class="form-desc">
          <div class="form-desc-title">Tax Return for Seniors</div>
          <div class="form-desc-sub">For taxpayers 65 and older · Larger print format</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-primary btn-sm">Start Return</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">Schedule A</div>
        <div class="form-desc">
          <div class="form-desc-title">Itemized Deductions</div>
          <div class="form-desc-sub">Medical, taxes, mortgage interest, charitable contributions</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">Schedule C</div>
        <div class="form-desc">
          <div class="form-desc-title">Profit or Loss From Business</div>
          <div class="form-desc-sub">Sole proprietorship income and expenses</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">Schedule D</div>
        <div class="form-desc">
          <div class="form-desc-title">Capital Gains and Losses</div>
          <div class="form-desc-sub">Report sales of stocks, bonds, real estate</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">Schedule E</div>
        <div class="form-desc">
          <div class="form-desc-title">Supplemental Income and Loss</div>
          <div class="form-desc-sub">Rental income, royalties, S-corps, partnerships</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
    </div>
  </div>
  <div id="forms-business" class="forms-tab" style="display:none">
    <div class="forms-list">
      <div class="form-item">
        <div class="form-number">1120</div>
        <div class="form-desc">
          <div class="form-desc-title">U.S. Corporation Income Tax Return</div>
          <div class="form-desc-sub">C-Corporations · Due April 15, 2025</div>
        </div>
        <div class="form-action-area">
          <span class="status-pill status-draft">2 Draft</span>
          <button class="btn btn-primary btn-sm">Start Return</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">1120-S</div>
        <div class="form-desc">
          <div class="form-desc-title">S-Corporation Income Tax Return</div>
          <div class="form-desc-sub">S-Corporations · Due March 15, 2025</div>
        </div>
        <div class="form-action-area">
          <span class="status-pill status-urgent">Due Soon</span>
          <button class="btn btn-primary btn-sm">Start Return</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">1065</div>
        <div class="form-desc">
          <div class="form-desc-title">U.S. Return of Partnership Income</div>
          <div class="form-desc-sub">Partnerships and LLCs taxed as partnerships · Due March 15</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-primary btn-sm">Start Return</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">941</div>
        <div class="form-desc">
          <div class="form-desc-title">Employer's Quarterly Federal Tax Return</div>
          <div class="form-desc-sub">Federal income tax withholding, FICA taxes</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
    </div>
  </div>
  <div id="forms-other" class="forms-tab" style="display:none">
    <div class="forms-list">
      <div class="form-item">
        <div class="form-number">W-2</div>
        <div class="form-desc">
          <div class="form-desc-title">Wage and Tax Statement</div>
          <div class="form-desc-sub">Employer wage reporting · Due Jan 31</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">1099-NEC</div>
        <div class="form-desc">
          <div class="form-desc-title">Nonemployee Compensation</div>
          <div class="form-desc-sub">Independent contractor payments · Due Jan 31</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">1099-MISC</div>
        <div class="form-desc">
          <div class="form-desc-title">Miscellaneous Information</div>
          <div class="form-desc-sub">Rents, royalties, prizes, backup withholding</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
      <div class="form-item">
        <div class="form-number">FinCEN 114</div>
        <div class="form-desc">
          <div class="form-desc-title">FBAR — Foreign Bank Account Report</div>
          <div class="form-desc-sub">Foreign accounts > $10,000 · Due April 15</div>
        </div>
        <div class="form-action-area">
          <button class="btn btn-ghost btn-sm">Open</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- CALCULATIONS -->
<div class="page" id="page-calculations">
  <div class="section-header">
    <div>
      <div class="section-title">Tax Calculator</div>
      <div class="section-sub">2024 Federal Tax Computation</div>
    </div>
    <div style="display:flex; gap:8px;">
      <select class="form-select" style="width:160px;" onchange="updateFiling(this.value)">
        <option value="single">Single</option>
        <option value="mfj" selected>Married Filing Jointly</option>
        <option value="mfs">Married Filing Separately</option>
        <option value="hoh">Head of Household</option>
      </select>
      <button class="btn btn-primary btn-sm" onclick="recalculate()">Recalculate</button>
    </div>
  </div>
  <div class="calc-layout">
    <div>
      <div class="card" style="margin-bottom:16px;">
        <div class="calc-section-title">Income</div>
        <div class="calc-line">
          <span class="calc-line-label">W-2 Wages (Box 1)</span>
          <span class="calc-line-value"><input type="text" id="wages" value="120,000" onblur="recalculate()"></span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Business Income (Sch C)</span>
          <span class="calc-line-value"><input type="text" id="biz" value="35,000" onblur="recalculate()"></span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Capital Gains (Sch D)</span>
          <span class="calc-line-value"><input type="text" id="capgains" value="12,000" onblur="recalculate()"></span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Interest Income</span>
          <span class="calc-line-value"><input type="text" id="interest" value="1,800" onblur="recalculate()"></span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Dividend Income</span>
          <span class="calc-line-value"><input type="text" id="dividends" value="4,200" onblur="recalculate()"></span>
        </div>
      </div>
      <div class="card" style="margin-bottom:16px;">
        <div class="calc-section-title">Adjustments & Deductions</div>
        <div class="calc-line">
          <span class="calc-line-label">Self-Employment Tax Deduction</span>
          <span class="calc-line-value"><input type="text" id="setaxded" value="2,473" onblur="recalculate()"></span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Standard Deduction (MFJ 2024)</span>
          <span class="calc-line-value" style="font-family:'DM Mono',monospace;" id="std-ded">$29,200</span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">QBI Deduction (20% Sec. 199A)</span>
          <span class="calc-line-value" style="font-family:'DM Mono',monospace;" id="qbi-ded">$7,000</span>
        </div>
      </div>
      <div class="card">
        <div class="calc-section-title">Tax Summary</div>
        <div class="calc-line">
          <span class="calc-line-label">Gross Income</span>
          <span class="calc-line-value" id="r-gross" style="font-family:'DM Mono',monospace;">$173,000</span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Adjusted Gross Income (AGI)</span>
          <span class="calc-line-value" id="r-agi" style="font-family:'DM Mono',monospace;">$170,527</span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Taxable Income</span>
          <span class="calc-line-value" id="r-taxable" style="font-family:'DM Mono',monospace;">$134,327</span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Self-Employment Tax</span>
          <span class="calc-line-value" id="r-setax" style="font-family:'DM Mono',monospace;">$4,945</span>
        </div>
        <div class="calc-line">
          <span class="calc-line-label">Federal Income Tax</span>
          <span class="calc-line-value" id="r-fedtax" style="font-family:'DM Mono',monospace; color:var(--accent);">$19,867</span>
        </div>
        <div class="calc-total">
          <span class="calc-total-label">Total Tax Liability</span>
          <span class="calc-total-value" id="r-total">$24,812</span>
        </div>
      </div>
    </div>

    <div>
      <div class="card" style="margin-bottom:16px;">
        <div class="calc-section-title">2024 Tax Brackets (MFJ)</div>
        <div id="brackets-display"></div>
      </div>
      <div class="card">
        <div class="calc-section-title">Effective Rates</div>
        <div style="margin-bottom:14px;">
          <div style="display:flex; justify-content:space-between; font-size:13px; margin-bottom:4px;">
            <span style="color:var(--muted)">Effective Federal Rate</span>
            <span id="eff-rate" style="font-family:'DM Mono',monospace; font-weight:600; color:var(--accent);">14.3%</span>
          </div>
          <div class="progress-wrap"><div class="progress-bar" id="eff-bar" style="width:14.3%"></div></div>
        </div>
        <div style="margin-bottom:14px;">
          <div style="display:flex; justify-content:space-between; font-size:13px; margin-bottom:4px;">
            <span style="color:var(--muted)">Marginal Rate</span>
            <span id="marg-rate" style="font-family:'DM Mono',monospace; font-weight:600; color:var(--accent2);">22%</span>
          </div>
          <div class="progress-wrap"><div class="progress-bar" id="marg-bar" style="width:22%; background:var(--accent2)"></div></div>
        </div>
        <div>
          <div style="display:flex; justify-content:space-between; font-size:13px; margin-bottom:4px;">
            <span style="color:var(--muted)">SE Tax Rate</span>
            <span style="font-family:'DM Mono',monospace; font-weight:600; color:var(--muted);">15.3%</span>
          </div>
          <div class="progress-wrap"><div class="progress-bar" style="width:15.3%; background:var(--muted)"></div></div>
        </div>
        <div style="margin-top:16px; padding-top:14px; border-top:1px solid var(--border);">
          <div class="calc-section-title" style="margin-bottom:8px;">Withholding Check</div>
          <div class="calc-line">
            <span class="calc-line-label">W-2 Withholding</span>
            <span class="calc-line-value"><input type="text" id="withholding" value="18,000" onblur="recalculate()" style="width:110px;"></span>
          </div>
          <div style="display:flex; justify-content:space-between; align-items:center; margin-top:10px; padding:10px 12px; border-radius:6px;" id="refund-wrap">
            <span style="font-size:13px; font-weight:500;" id="refund-label">Estimated Refund</span>
            <span style="font-family:'DM Serif Display',serif; font-size:20px;" id="refund-value">$0</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- DOCUMENTS -->
<div class="page" id="page-documents">
  <div class="section-header">
    <div>
      <div class="section-title">Document Storage</div>
      <div class="section-sub">Secure client document repository</div>
    </div>
    <select class="form-select" style="width:180px;">
      <option>All Clients</option>
      <option>Anderson, Mark</option>
      <option>Beacon LLC</option>
      <option>Torres, Elena</option>
    </select>
  </div>
  <div class="doc-upload-area" onclick="simulateUpload()">
    <div class="doc-upload-icon">⬆️</div>
    <div class="doc-upload-text">Drop files here or click to upload</div>
    <div class="doc-upload-sub">Supports PDF, W-2, 1099, K-1, and other IRS documents · Max 50MB</div>
  </div>
  <div class="tab-bar">
    <div class="tab active" onclick="switchDocTab(this, 'docs-all')">All Documents</div>
    <div class="tab" onclick="switchDocTab(this, 'docs-source')">Source Docs</div>
    <div class="tab" onclick="switchDocTab(this, 'docs-returns')">Filed Returns</div>
    <div class="tab" onclick="switchDocTab(this, 'docs-engagement')">Engagement</div>
  </div>
  <div class="doc-list" id="docs-all">
    <div class="doc-item">
      <div class="doc-icon">📄</div>
      <div class="doc-info">
        <div class="doc-name">Anderson_Mark_W2_2024.pdf</div>
        <div class="doc-meta">W-2 · Uploaded Feb 14, 2025 · 124 KB · Anderson, Mark</div>
      </div>
      <div class="doc-actions">
        <button class="btn btn-ghost btn-sm">👁 View</button>
        <button class="btn btn-ghost btn-sm">⬇ Download</button>
      </div>
    </div>
    <div class="doc-item">
      <div class="doc-icon">📄</div>
      <div class="doc-info">
        <div class="doc-name">Torres_Elena_1099NEC_2024.pdf</div>
        <div class="doc-meta">1099-NEC · Uploaded Feb 12, 2025 · 89 KB · Torres, Elena</div>
      </div>
      <div class="doc-actions">
        <button class="btn btn-ghost btn-sm">👁 View</button>
        <button class="btn btn-ghost btn-sm">⬇ Download</button>
      </div>
    </div>
    <div class="doc-item">
      <div class="doc-icon">📊</div>
      <div class="doc-info">
        <div class="doc-name">BeaconLLC_BookIncome_2024.xlsx</div>
        <div class="doc-meta">Workpaper · Uploaded Feb 10, 2025 · 340 KB · Beacon LLC</div>
      </div>
      <div class="doc-actions">
        <button class="btn btn-ghost btn-sm">👁 View</button>
        <button class="btn btn-ghost btn-sm">⬇ Download</button>
      </div>
    </div>
    <div class="doc-item">
      <div class="doc-icon">📄</div>
      <div class="doc-info">
        <div class="doc-name">Anderson_Mark_1040_FILED_2023.pdf</div>
        <div class="doc-meta">Filed Return · Uploaded Jan 3, 2025 · 1.2 MB · Anderson, Mark</div>
      </div>
      <div class="doc-actions">
        <button class="btn btn-ghost btn-sm">👁 View</button>
        <button class="btn btn-ghost btn-sm">⬇ Download</button>
      </div>
    </div>
    <div class="doc-item">
      <div class="doc-icon">📝</div>
      <div class="doc-info">
        <div class="doc-name">SummitPartners_Engagement_Letter_2024.pdf</div>
        <div class="doc-meta">Engagement Letter · Signed Jan 15, 2025 · 204 KB · Summit Partners</div>
      </div>
      <div class="doc-actions">
        <button class="btn btn-ghost btn-sm">👁 View</button>
        <button class="btn btn-ghost btn-sm">⬇ Download</button>
      </div>
    </div>
  </div>
  <div class="doc-list" id="docs-source" style="display:none">
    <div style="color:var(--muted); font-size:13px; padding:20px 0;">Showing source documents only (W-2, 1099, K-1...).</div>
  </div>
  <div class="doc-list" id="docs-returns" style="display:none">
    <div style="color:var(--muted); font-size:13px; padding:20px 0;">Showing filed returns only.</div>
  </div>
  <div class="doc-list" id="docs-engagement" style="display:none">
    <div style="color:var(--muted); font-size:13px; padding:20px 0;">Showing engagement letters and contracts.</div>
  </div>
</div>

<!-- DEADLINES PAGE -->
<div class="page" id="page-deadlines">
  <div class="section-header">
    <div>
      <div class="section-title">Filing Deadlines</div>
      <div class="section-sub">2024 Tax Year · Key IRS dates</div>
    </div>
  </div>
  <div style="display:grid; grid-template-columns:1fr 1fr; gap:16px;">
    <div class="card">
      <div class="card-header"><div class="card-title" style="color:var(--danger);">🔴 Critical — Within 2 Weeks</div></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">March 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Form 1065 — Partnership Returns</div></div><span class="deadline-days days-red">15 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">March 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Form 1120-S — S-Corp Returns</div></div><span class="deadline-days days-red">15 days</span></div>
    </div>
    <div class="card">
      <div class="card-header"><div class="card-title" style="color:var(--warn);">🟡 Upcoming — Next Month</div></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">April 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Form 1040 — Individual Returns</div></div><span class="deadline-days days-yellow">46 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">April 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Form 1120 — C-Corp Returns</div></div><span class="deadline-days days-yellow">46 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">April 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Q1 Estimated Tax Payments</div></div><span class="deadline-days days-yellow">46 days</span></div>
    </div>
    <div class="card">
      <div class="card-header"><div class="card-title" style="color:var(--success);">🟢 Extended Deadlines</div></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">September 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Extended 1065 & 1120-S</div></div><span class="deadline-days days-green">199 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">October 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Extended 1040 Returns</div></div><span class="deadline-days days-green">229 days</span></div>
    </div>
    <div class="card">
      <div class="card-header"><div class="card-title">📋 Quarterly Reminders</div></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">April 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Q1 Estimated Taxes (Form 1040-ES)</div></div><span class="deadline-days days-yellow">46 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">June 16, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Q2 Estimated Taxes</div></div><span class="deadline-days days-green">108 days</span></div>
      <div class="deadline-item"><div><div style="font-size:13px;font-weight:600;">September 15, 2025</div><div style="font-size:12px;color:var(--muted);margin-top:2px;">Q3 Estimated Taxes</div></div><span class="deadline-days days-green">199 days</span></div>
    </div>
  </div>
</div>

<!-- REPORTS PAGE -->
<div class="page" id="page-reports">
  <div class="section-header">
    <div>
      <div class="section-title">Practice Reports</div>
      <div class="section-sub">Firm performance and filing statistics</div>
    </div>
    <button class="btn btn-primary btn-sm">Export PDF</button>
  </div>
  <div style="display:grid; grid-template-columns:repeat(3,1fr); gap:16px; margin-bottom:20px;">
    <div class="card" style="text-align:center; padding:24px;">
      <div style="font-family:'DM Serif Display',serif; font-size:40px; color:var(--accent);">183</div>
      <div style="font-size:12px;color:var(--muted);margin-top:4px;">Returns Filed YTD</div>
      <div class="progress-wrap" style="margin-top:10px;"><div class="progress-bar" style="width:73%"></div></div>
      <div style="font-size:11px;color:var(--muted);margin-top:4px;">73% of 250 goal</div>
    </div>
    <div class="card" style="text-align:center; padding:24px;">
      <div style="font-family:'DM Serif Display',serif; font-size:40px; color:var(--accent2);">94%</div>
      <div style="font-size:12px;color:var(--muted);margin-top:4px;">On-Time Filing Rate</div>
      <div class="progress-wrap" style="margin-top:10px;"><div class="progress-bar" style="width:94%; background:var(--accent2)"></div></div>
      <div style="font-size:11px;color:var(--muted);margin-top:4px;">Firm average: 89%</div>
    </div>
    <div class="card" style="text-align:center; padding:24px;">
      <div style="font-family:'DM Serif Display',serif; font-size:40px; color:var(--success);">$2.1M</div>
      <div style="font-size:12px;color:var(--muted);margin-top:4px;">Total Refunds Secured</div>
      <div class="progress-wrap" style="margin-top:10px;"><div class="progress-bar" style="width:84%; background:var(--success)"></div></div>
      <div style="font-size:11px;color:var(--muted);margin-top:4px;">Avg refund: $11,475</div>
    </div>
  </div>
  <div class="card">
    <div class="card-header"><div class="card-title"><span class="accent-line"></span>Returns by Status</div></div>
    <table class="recent-table">
      <thead><tr><th>Return Type</th><th>Total</th><th>Filed</th><th>In Progress</th><th>Pending Docs</th><th>Completion</th></tr></thead>
      <tbody>
        <tr><td>Form 1040 (Individual)</td><td>124</td><td>91</td><td>22</td><td>11</td><td><div class="progress-wrap" style="width:120px;"><div class="progress-bar" style="width:73%"></div></div></td></tr>
        <tr><td>Form 1120-S (S-Corp)</td><td>28</td><td>18</td><td>7</td><td>3</td><td><div class="progress-wrap" style="width:120px;"><div class="progress-bar" style="width:64%"></div></div></td></tr>
        <tr><td>Form 1065 (Partnership)</td><td>21</td><td>14</td><td>5</td><td>2</td><td><div class="progress-wrap" style="width:120px;"><div class="progress-bar" style="width:67%"></div></div></td></tr>
        <tr><td>Form 1120 (C-Corp)</td><td>10</td><td>6</td><td>4</td><td>0</td><td><div class="progress-wrap" style="width:120px;"><div class="progress-bar" style="width:60%"></div></div></td></tr>
      </tbody>
    </table>
  </div>
</div>
```

  </div><!-- /content -->
</div><!-- /main -->

<!-- MODALS -->

<div class="modal-overlay" id="modal-new-client">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('new-client')">✕</button>
    <div class="modal-title">Add New Client</div>
    <div class="modal-sub">Enter client information to create a new tax file</div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">First Name</label>
        <input class="form-input" placeholder="Jane">
      </div>
      <div class="form-group">
        <label class="form-label">Last Name</label>
        <input class="form-input" placeholder="Smith">
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Client Type</label>
      <select class="form-select">
        <option>Individual</option>
        <option>Business — S-Corp</option>
        <option>Business — C-Corp</option>
        <option>Partnership / LLC</option>
        <option>Nonprofit</option>
      </select>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">SSN / EIN</label>
        <input class="form-input" placeholder="XXX-XX-XXXX">
      </div>
      <div class="form-group">
        <label class="form-label">Filing Status</label>
        <select class="form-select">
          <option>Single</option>
          <option>Married Filing Jointly</option>
          <option>Married Filing Separately</option>
          <option>Head of Household</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Email Address</label>
      <input class="form-input" placeholder="client@email.com" type="email">
    </div>
    <div class="form-group">
      <label class="form-label">Phone</label>
      <input class="form-input" placeholder="(555) 000-0000">
    </div>
    <div class="form-group">
      <label class="form-label">Address</label>
      <input class="form-input" placeholder="Street address">
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">City</label>
        <input class="form-input" placeholder="City">
      </div>
      <div class="form-group">
        <label class="form-label">State / ZIP</label>
        <input class="form-input" placeholder="CA 90210">
      </div>
    </div>
    <div class="form-actions">
      <button class="btn btn-ghost" onclick="closeModal('new-client')">Cancel</button>
      <button class="btn btn-primary" onclick="addClient()">Create Client File</button>
    </div>
  </div>
</div>

<div class="modal-overlay" id="modal-new-return">
  <div class="modal">
    <button class="modal-close" onclick="closeModal('new-return')">✕</button>
    <div class="modal-title">Start New Return</div>
    <div class="modal-sub">Create a new tax return for an existing client</div>
    <div class="form-group">
      <label class="form-label">Client</label>
      <select class="form-select">
        <option>Anderson, Mark</option>
        <option>Torres, Elena</option>
        <option>Beacon LLC</option>
        <option>Summit Partners</option>
        <option>Kim, David</option>
        <option>Hartley Corp</option>
      </select>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label class="form-label">Tax Form</label>
        <select class="form-select">
          <option>Form 1040</option>
          <option>Form 1040-SR</option>
          <option>Form 1120</option>
          <option>Form 1120-S</option>
          <option>Form 1065</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Tax Year</label>
        <select class="form-select">
          <option>2024</option>
          <option>2023</option>
          <option>2022</option>
        </select>
      </div>
    </div>
    <div class="form-group">
      <label class="form-label">Preparer</label>
      <select class="form-select">
        <option>Sarah Chen, CPA</option>
        <option>Michael Torres, CPA</option>
        <option>Aisha Johnson, EA</option>
      </select>
    </div>
    <div class="form-group">
      <label class="form-label">Priority</label>
      <select class="form-select">
        <option>Normal</option>
        <option>High Priority</option>
        <option>Rush</option>
      </select>
    </div>
    <div class="form-group">
      <label class="form-label">Notes</label>
      <input class="form-input" placeholder="Any notes for this return...">
    </div>
    <div class="form-actions">
      <button class="btn btn-ghost" onclick="closeModal('new-return')">Cancel</button>
      <button class="btn btn-primary" onclick="startReturn()">Create Return</button>
    </div>
  </div>
</div>

<div class="notification" id="notification"></div>

<script>
// Navigation
function navigate(page, el) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page-' + page).classList.add('active');
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  if (el) el.classList.add('active');
  const titles = {
    dashboard: 'Dashboard', clients: 'Client Management',
    forms: 'Tax Forms', calculations: 'Tax Calculator',
    documents: 'Document Storage', deadlines: 'Filing Deadlines', reports: 'Practice Reports'
  };
  document.getElementById('page-title').textContent = titles[page] || page;
  if (page === 'calculations') setTimeout(recalculate, 100);
  if (page === 'clients') renderClients();
}

// Clients data
const colors = ['#e8c547','#4da8da','#3fb950','#e06c75','#c678dd','#56b6c2','#d19a66','#98c379'];
const clients = [
  {name:'Anderson, Mark', type:'Individual', ein:'SSN ···-··-4821', color: colors[0]},
  {name:'Torres, Elena', type:'Individual', ein:'SSN ···-··-9932', color: colors[1]},
  {name:'Beacon LLC', type:'S-Corporation', ein:'EIN 47-···6621', color: colors[2]},
  {name:'Summit Partners', type:'Partnership', ein:'EIN 62-···8812', color: colors[3]},
  {name:'Kim, David', type:'Individual', ein:'SSN ···-··-1144', color: colors[4]},
  {name:'Hartley Corp', type:'C-Corporation', ein:'EIN 55-···3391', color: colors[5]},
  {name:'Rivera, Sofia', type:'Individual', ein:'SSN ···-··-7723', color: colors[6]},
  {name:'GreenLeaf Inc', type:'S-Corporation', ein:'EIN 89-···4417', color: colors[7]},
  {name:'Nakamura, James', type:'Individual', ein:'SSN ···-··-5581', color: colors[0]},
  {name:'BlueStar LLC', type:'Partnership', ein:'EIN 33-···9901', color: colors[1]},
  {name:'Chen, Wei', type:'Individual', ein:'SSN ···-··-2267', color: colors[2]},
  {name:'Apex Holdings', type:'C-Corporation', ein:'EIN 71-···0043', color: colors[3]},
];

function renderClients(filter='') {
  const grid = document.getElementById('clients-grid');
  const filtered = clients.filter(c => c.name.toLowerCase().includes(filter.toLowerCase()) || c.type.toLowerCase().includes(filter.toLowerCase()));
  const statuses = ['Filed','In Review','Draft','Filed','Needs Docs','Filed','Filed','In Review','Draft','Filed','Filed','In Review'];
  const statusMap = {Filed:'status-filed','In Review':'status-review','Draft':'status-draft','Needs Docs':'status-urgent'};
  grid.innerHTML = filtered.map((c, i) => `
    <div class="client-card" onclick="showNotification('Opening file for ${c.name}...')">
      <div class="client-avatar" style="background:${c.color}">${c.name.split(',')[0][0]}${c.name.includes(',') ? c.name.split(',')[1].trim()[0] : ''}</div>
      <div class="client-name">${c.name}</div>
      <div class="client-type">${c.type}</div>
      <div class="client-meta">
        <span class="client-ein">${c.ein}</span>
        <span class="status-pill ${statusMap[statuses[i]] || 'status-draft'}">${statuses[i]}</span>
      </div>
    </div>
  `).join('');
}

function filterClients(val) { renderClients(val); }

// Modals
function showModal(id) { document.getElementById('modal-' + id).classList.add('open'); }
function closeModal(id) { document.getElementById('modal-' + id).classList.remove('open'); }

// Notifications
function showNotification(msg) {
  const n = document.getElementById('notification');
  n.textContent = '✓ ' + msg;
  n.classList.add('show');
  setTimeout(() => n.classList.remove('show'), 2500);
}

function addClient() {
  closeModal('new-client');
  showNotification('Client file created successfully');
}
function startReturn() {
  closeModal('new-return');
  showNotification('New return created and assigned');
}

// Tax calculation
const brackets2024_MFJ = [
  {rate:0.10, min:0, max:23200},
  {rate:0.12, min:23200, max:94300},
  {rate:0.22, min:94300, max:201050},
  {rate:0.24, min:201050, max:383900},
  {rate:0.32, min:383900, max:487450},
  {rate:0.35, min:487450, max:731200},
  {rate:0.37, min:731200, max:Infinity},
];

function parseNum(s) { return parseFloat((s || '0').toString().replace(/,/g,'')) || 0; }
function fmt(n) { return '$' + Math.round(n).toLocaleString(); }

function calcFedTax(taxable, brackets) {
  let tax = 0, marg = 0.10;
  for (const b of brackets) {
    if (taxable <= b.min) break;
    const taxed = Math.min(taxable, b.max) - b.min;
    tax += taxed * b.rate;
    marg = b.rate;
  }
  return {tax, marg};
}

function recalculate() {
  const wages = parseNum(document.getElementById('wages').value);
  const biz = parseNum(document.getElementById('biz').value);
  const capgains = parseNum(document.getElementById('capgains').value);
  const interest = parseNum(document.getElementById('interest').value);
  const dividends = parseNum(document.getElementById('dividends').value);
  const withholding = parseNum(document.getElementById('withholding').value);

  const gross = wages + biz + capgains + interest + dividends;
  const seTax = biz * 0.9235 * 0.153;
  const seTaxDed = seTax / 2;
  const qbiDed = biz * 0.20;
  const stdDed = 29200;
  const agi = gross - seTaxDed;
  const taxable = Math.max(0, agi - stdDed - qbiDed);
  const {tax: fedTax, marg} = calcFedTax(taxable, brackets2024_MFJ);
  const total = fedTax + seTax;
  const effRate = gross > 0 ? (total / gross * 100) : 0;
  const balance = withholding - total;

  document.getElementById('r-gross').textContent = fmt(gross);
  document.getElementById('r-agi').textContent = fmt(agi);
  document.getElementById('r-taxable').textContent = fmt(taxable);
  document.getElementById('r-setax').textContent = fmt(seTax);
  document.getElementById('r-fedtax').textContent = fmt(fedTax);
  document.getElementById('r-total').textContent = fmt(total);
  document.getElementById('qbi-ded').textContent = fmt(qbiDed);
  document.getElementById('eff-rate').textContent = effRate.toFixed(1) + '%';
  document.getElementById('eff-bar').style.width = Math.min(effRate, 40) * 2.5 + '%';
  document.getElementById('marg-rate').textContent = (marg * 100).toFixed(0) + '%';
  document.getElementById('marg-bar').style.width = marg * 100 + '%';

  const rw = document.getElementById('refund-wrap');
  const rl = document.getElementById('refund-label');
  const rv = document.getElementById('refund-value');
  if (balance >= 0) {
    rw.style.background = 'rgba(63,185,80,0.1)';
    rw.style.border = '1px solid rgba(63,185,80,0.3)';
    rl.style.color = 'var(--success)';
    rv.style.color = 'var(--success)';
    rl.textContent = '💚 Estimated Refund';
  } else {
    rw.style.background = 'rgba(248,81,73,0.1)';
    rw.style.border = '1px solid rgba(248,81,73,0.3)';
    rl.style.color = 'var(--danger)';
    rv.style.color = 'var(--danger)';
    rl.textContent = '🔴 Balance Due';
  }
  rv.textContent = fmt(Math.abs(balance));

  // Brackets display
  const bd = document.getElementById('brackets-display');
  bd.innerHTML = brackets2024_MFJ.map(b => `
    <div class="tax-bracket-row">
      <span class="bracket-rate">${(b.rate*100).toFixed(0)}%</span>
      <span class="bracket-range">${b.max === Infinity ? `Over $${(b.min/1000).toFixed(0)}k` : `$${(b.min/1000).toFixed(0)}k–$${(b.max/1000).toFixed(0)}k`}</span>
      <div class="bracket-bar-wrap"><div class="bracket-bar" style="width:${b.rate/0.37*100}%"></div></div>
    </div>
  `).join('');
}

// Tabs
function switchTab(el, tabId) {
  el.closest('.page').querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  el.classList.add('active');
  el.closest('.page').querySelectorAll('.forms-tab').forEach(t => t.style.display = 'none');
  document.getElementById(tabId).style.display = 'block';
}

function switchDocTab(el, tabId) {
  el.closest('.page').querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  el.classList.add('active');
  ['docs-all','docs-source','docs-returns','docs-engagement'].forEach(id => {
    const el2 = document.getElementById(id);
    if(el2) el2.style.display = id === tabId ? 'flex' : 'none';
  });
}

function openForm(name) { showNotification(`Opening Form ${name} — select a client to continue`); }
function simulateUpload() { showNotification('Document uploaded and linked to client file'); }
function showYearPicker() { showNotification('Tax year selector — currently set to 2024'); }
function updateFiling(v) { recalculate(); }

// Init
renderClients();
setTimeout(recalculate, 300);
</script>

</body>
</html>