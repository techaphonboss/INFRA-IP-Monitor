
<!doctype html>
<html lang="th">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>INFRA IP Monitor — Interlink Telecom</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&family=Sarabun:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
:root {
  --bg-base: #0a0d12;
  --bg-side: #070a0f;
  --bg-panel: #10141c;
  --bg-panel-2: #161b26;
  --grid-line: #1f2532;
  --text-primary: #e6e9ef;
  --text-dim: #66707f;
  --accent: #3b82f6;
  --orange: #f0862c;
  --up: #22c55e;
  --down: #ef4444;
  --warn: #f59e0b;
  --radius: 8px;
  --font-display: 'Space Grotesk', system-ui, sans-serif;
  --font-body: 'Inter', 'Sarabun', system-ui, sans-serif;
  --font-mono: 'JetBrains Mono', ui-monospace, monospace;
}
html[data-theme="light"] {
  --bg-base: #eef1f6;
  --bg-side: #ffffff;
  --bg-panel: #ffffff;
  --bg-panel-2: #f1f4f9;
  --grid-line: #dde3ec;
  --text-primary: #1c2430;
  --text-dim: #6b7686;
}
* { box-sizing: border-box; }
html, body { margin: 0; background: var(--bg-base); color: var(--text-primary); font-family: var(--font-body); font-size: 13px; transition: background 0.25s ease, color 0.25s ease; }
.theme-btn { font-size: 15px; padding: 6px 11px; border-radius: 999px; line-height: 1; }

/* ================== LOGIN ================== */
.login-screen {
  position: fixed; inset: 0; z-index: 1000;
  background: #f2f5fa;
  display: flex; align-items: center; justify-content: center;
  padding: 20px;
}
.login-card { box-shadow: 0 24px 70px rgba(15,30,60,0.18); border: 1px solid #e2e8f2; }
.login-screen.hidden { display: none; }
.login-card {
  display: flex; width: min(980px, 100%); min-height: 560px;
  border-radius: 14px; overflow: hidden;
  box-shadow: 0 30px 80px rgba(0,0,0,0.55);
}
.login-left {
  flex: 0 0 42%;
  background: linear-gradient(160deg, #0d1526 0%, #0a101f 60%, #080d19 100%);
  padding: 42px 38px;
  display: flex; flex-direction: column;
  border-right: 1px solid rgba(255,255,255,0.05);
}
.logo-card {
  background: #fff; border-radius: 12px; padding: 16px 18px;
  display: inline-block; align-self: flex-start;
  box-shadow: 0 8px 24px rgba(0,0,0,0.35);
}
.logo-card img { display: block; width: 200px; height: auto; }
.login-left .brand { margin-top: 26px; font-family: var(--font-display); font-size: 26px; font-weight: 700; letter-spacing: 0.02em; }
.login-left .brand .o { color: var(--orange); }
.login-left .brand-sub { font-family: var(--font-mono); font-size: 11px; letter-spacing: 0.3em; color: #93a0b5; margin-top: 2px; }
.login-left .rule { width: 44px; height: 3px; background: var(--orange); border-radius: 2px; margin: 18px 0 22px; }
.login-left .sys-name { font-size: 17px; font-weight: 700; color: #dbe3f0; }
.login-left .sys-desc { font-family: 'Sarabun', sans-serif; font-size: 13.5px; color: #8b98ad; line-height: 1.7; margin-top: 6px; }
.login-stats { display: flex; gap: 12px; margin-top: auto; padding-top: 26px; }
.login-stats .stat {
  background: rgba(255,255,255,0.04); border: 1px solid rgba(255,255,255,0.07);
  border-radius: 10px; padding: 14px 18px; min-width: 110px;
}
.login-stats .stat .n { font-family: var(--font-mono); font-size: 22px; font-weight: 600; color: var(--orange); }
.login-stats .stat .n.blue { color: var(--accent); }
.login-stats .stat .l { font-family: 'Sarabun', sans-serif; font-size: 12px; color: #8b98ad; margin-top: 3px; }

.login-right { flex: 1; background: #fff; color: #1c2430; padding: 52px 56px; display: flex; flex-direction: column; }
.login-right .team { font-family: var(--font-mono); font-size: 12px; font-weight: 600; letter-spacing: 0.12em; color: var(--orange); text-transform: uppercase; }
.login-right h1 { font-family: 'Sarabun', sans-serif; font-size: 30px; font-weight: 700; margin: 8px 0 4px; }
.login-right .sub { font-family: 'Sarabun', sans-serif; font-size: 14px; color: #6b7686; margin-bottom: 34px; }
.login-right label { font-family: var(--font-mono); font-size: 11px; font-weight: 600; letter-spacing: 0.08em; color: #4a5568; display: block; margin-bottom: 7px; }
.login-right .field { position: relative; margin-bottom: 20px; }
.login-right input {
  width: 100%; font-family: var(--font-body); font-size: 14.5px;
  padding: 13px 44px 13px 15px; border: 1.5px solid #dde3ec; border-radius: 10px;
  background: #f8fafc; color: #1c2430; outline: none;
}
.login-right input:focus { border-color: var(--accent); background: #fff; }
.eye-btn { position: absolute; right: 12px; top: 50%; transform: translateY(-50%); background: none; border: none; cursor: pointer; color: #8b98ad; font-size: 16px; padding: 4px; }
.login-btn {
  width: 100%; font-family: 'Sarabun', sans-serif; font-size: 16px; font-weight: 600;
  background: var(--accent); color: #fff; border: none; border-radius: 10px;
  padding: 14px; cursor: pointer; margin-top: 8px;
}
.login-btn:hover { background: #2f6fe0; }
.login-err { font-family: 'Sarabun', sans-serif; font-size: 13px; color: var(--down); min-height: 18px; margin-top: 12px; }
.login-foot { margin-top: auto; text-align: center; font-size: 12px; color: #9aa5b5; padding-top: 30px; }
@media (max-width: 820px) { .login-left { display: none; } .login-right { padding: 40px 30px; } }

/* ================== APP ================== */
.app { display: none; }
.app.authed { display: flex; min-height: 100vh; }

.sidebar { width: 210px; flex-shrink: 0; background: var(--bg-side); border-right: 1px solid var(--grid-line); display: flex; flex-direction: column; position: sticky; top: 0; height: 100vh; }
.logo { display: flex; align-items: center; gap: 10px; padding: 14px 14px 8px; }
.logo .logo-chip { background: #fff; border-radius: 8px; padding: 6px 8px; }
.logo .logo-chip img { display: block; width: 130px; height: auto; }
.logo-sub { font-family: var(--font-mono); font-size: 9px; color: var(--text-dim); letter-spacing: 0.13em; text-transform: uppercase; padding: 0 16px 10px; border-bottom: 1px solid var(--grid-line); }

.nav { padding: 10px; flex: 1; }
.nav a { display: flex; align-items: center; gap: 10px; padding: 9px 12px; margin-bottom: 2px; border-radius: 7px; color: var(--text-dim); text-decoration: none; font-weight: 500; font-size: 13px; }
.nav a:hover { background: var(--bg-panel); color: var(--text-primary); }
.nav a.active { background: rgba(59,130,246,0.14); color: var(--accent); }
.nav a .ico { font-family: var(--font-mono); width: 16px; text-align: center; }
.nav a .pill { margin-left: auto; font-family: var(--font-mono); font-size: 10px; background: var(--down); color: #fff; border-radius: 999px; padding: 1px 7px; font-weight: 600; }
.nav a .pill.zero { background: var(--grid-line); color: var(--text-dim); }
.logout-row { padding: 10px; border-top: 1px solid var(--grid-line); }
.logout-row button { width: 100%; }
.side-clock { padding: 14px 18px; border-top: 1px solid var(--grid-line); font-family: var(--font-mono); }
.side-clock .time { font-size: 20px; font-weight: 600; }
.side-clock .date { font-size: 11px; color: var(--text-dim); margin-top: 2px; }

.main { flex: 1; min-width: 0; }
.topbar { display: flex; align-items: center; gap: 14px; padding: 12px 22px; border-bottom: 1px solid var(--grid-line); background: var(--bg-side); position: sticky; top: 0; z-index: 50; }
.topbar .crumb { font-size: 13px; color: var(--text-dim); font-weight: 500; }
.topbar .crumb strong { color: var(--text-primary); }
.search-box { flex: 1; max-width: 420px; margin-left: auto; position: relative; }
.search-box input { width: 100%; font-size: 13px; color: var(--text-primary); background: var(--bg-panel-2); border: 1px solid var(--grid-line); border-radius: 999px; padding: 8px 14px 8px 34px; }
.search-box::before { content: '⌕'; position: absolute; left: 13px; top: 6px; color: var(--text-dim); font-size: 15px; }

/* ---- Pages ---- */
.page { display: none; }
.page.active { display: block; }

/* ---- Excel-style IP grid ---- */
.ipa-tabs { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 12px; }
.ipa-tab { font-family: var(--font-body); font-weight: 600; font-size: 12.5px; padding: 8px 16px; border-radius: 8px 8px 0 0; border: 1px solid var(--grid-line); border-bottom: none; background: var(--bg-panel-2); color: var(--text-dim); cursor: pointer; }
.ipa-tab.active { background: var(--accent); color: #fff; border-color: var(--accent); }
.ipa-sub { display: flex; gap: 6px; align-items: center; margin-bottom: 12px; flex-wrap: wrap; }
.ipa-legend { display: flex; gap: 16px; font-size: 11.5px; color: var(--text-dim); margin-left: auto; flex-wrap: wrap; }
.ipa-legend .sw { display: inline-block; width: 11px; height: 11px; border-radius: 3px; margin-right: 5px; vertical-align: -1px; border: 1px solid var(--grid-line); }
/* สีแยกตามอุปกรณ์ในแท็บรวม STS/Tele/INV */
.ipa-table td.eq-STS { background: rgba(59,130,246,0.18); }
.ipa-table td.eq-TeleAlarm { background: rgba(245,158,11,0.20); }
.ipa-table td.eq-Inverter { background: rgba(168,85,247,0.20); }
html[data-theme="light"] .ipa-table td.eq-STS { background: #d8e6fb; }
html[data-theme="light"] .ipa-table td.eq-TeleAlarm { background: #fbecd0; }
html[data-theme="light"] .ipa-table td.eq-Inverter { background: #ecdcfa; }
.st-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; margin-right: 5px; vertical-align: 1px; }
.st-dot.up { background: var(--up); box-shadow: 0 0 4px var(--up); }
.st-dot.down { background: var(--down); box-shadow: 0 0 4px var(--down); }
.st-dot.unknown { background: var(--warn); opacity: 0.7; }
.ipa-wrap { overflow-x: auto; border: 1px solid var(--grid-line); border-radius: var(--radius); max-height: calc(100vh - 300px); overflow-y: auto; }
.ipa-table { border-collapse: collapse; width: 100%; min-width: 1150px; }
.ipa-table th.region { font-family: var(--font-display); font-size: 12.5px; color: var(--text-primary); background: var(--bg-panel-2); border: 1px solid var(--grid-line); padding: 8px; text-align: center; position: sticky; top: 0; z-index: 3; }
.ipa-table th.sub { font-family: var(--font-mono); font-size: 9.5px; letter-spacing: 0.05em; color: var(--text-dim); background: var(--bg-panel-2); border: 1px solid var(--grid-line); padding: 4px 8px; text-align: left; position: sticky; top: 33px; z-index: 3; }
.ipa-table td { border: 1px solid var(--grid-line); padding: 3px 7px; font-size: 11px; height: 26px; }
.ipa-table td.ipa-ip { font-family: var(--font-mono); white-space: nowrap; cursor: pointer; color: var(--text-dim); position: relative; }
.ipa-table td.ipa-ip:hover { color: var(--accent); }
.ipa-table td.ipa-node { font-family: var(--font-body); color: var(--text-dim); min-width: 90px; max-width: 150px; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.ipa-table td.used { background: rgba(34,197,94,0.16); }
.ipa-table td.used.ipa-ip { color: var(--up); font-weight: 600; }
.ipa-table td.used.ipa-node { color: var(--text-primary); }
html[data-theme="light"] .ipa-table td.used { background: #d7f5e2; }
.ipa-table td.blocked { background: rgba(107,114,128,0.22); }
.ipa-table td.blocked.ipa-ip { color: var(--text-dim); text-decoration: line-through; }
html[data-theme="light"] .ipa-table td.blocked { background: #e3e6eb; }
.blk-btn { position: absolute; right: 3px; top: 50%; transform: translateY(-50%); font-size: 10px; border: none; background: transparent; cursor: pointer; opacity: 0; padding: 1px 3px; }
.ipa-table td.ipa-ip:hover .blk-btn { opacity: 0.85; }
.ipa-table td.blocked .blk-btn { opacity: 0.85; }
.status-pill { display: flex; align-items: center; gap: 7px; font-family: var(--font-mono); font-size: 11px; font-weight: 600; padding: 6px 13px; border-radius: 999px; border: 1px solid var(--grid-line); background: var(--bg-panel-2); }
.status-pill .sdot { width: 8px; height: 8px; border-radius: 50%; }

.content { padding: 20px 22px 60px; }
.panel { background: var(--bg-panel); border: 1px solid var(--grid-line); border-radius: var(--radius); padding: 15px 16px; }
.panel h3 { margin: 0 0 10px; font-size: 12px; font-weight: 600; color: var(--text-dim); text-transform: uppercase; letter-spacing: 0.05em; }
.panel h2 { font-family: var(--font-display); font-size: 14px; margin: 0 0 12px; display: flex; align-items: center; gap: 8px; flex-wrap: wrap; }
.panel h2 .badge { font-family: var(--font-mono); font-size: 11px; font-weight: 400; color: var(--text-dim); margin-left: auto; }

.poll-strip { display: flex; align-items: center; gap: 18px; flex-wrap: wrap; font-family: var(--font-mono); font-size: 11px; color: var(--text-dim); background: var(--bg-panel); border: 1px solid var(--grid-line); border-radius: var(--radius); padding: 9px 14px; margin-bottom: 14px; }
.poll-strip b { color: var(--text-primary); font-weight: 600; }
.poll-strip .prog { flex: 1; min-width: 140px; height: 4px; background: var(--grid-line); border-radius: 2px; overflow: hidden; }
.poll-strip .prog .fill { height: 100%; width: 0%; background: var(--accent); transition: width 0.3s ease; }
.poll-strip .run { color: var(--up); }

.kpi-row { display: grid; grid-template-columns: 1.3fr 1fr 1fr 1fr 1.3fr; gap: 12px; margin-bottom: 14px; }
.net-status .word { font-family: var(--font-display); font-size: 24px; font-weight: 700; }
.net-status .word.healthy { color: var(--up); }
.net-status .word.degraded { color: var(--warn); }
.net-status .word.critical { color: var(--down); }
.net-status .desc { font-size: 11px; color: var(--text-dim); margin-top: 3px; }
.net-status svg { display: block; margin-top: 8px; }
.kpi .big { font-family: var(--font-mono); font-size: 26px; font-weight: 600; }
.kpi .sub-row { display: flex; gap: 14px; margin-top: 9px; padding-top: 9px; border-top: 1px solid var(--grid-line); }
.kpi .sub-row div { font-family: var(--font-mono); font-size: 13px; font-weight: 600; }
.kpi .sub-row span { display: block; font-size: 10px; font-weight: 400; color: var(--text-dim); text-transform: uppercase; margin-top: 1px; }
.kpi .c-up { color: var(--up); } .kpi .c-down { color: var(--down); } .kpi .c-unk { color: var(--warn); }
.donut-wrap { display: flex; align-items: center; gap: 14px; }
.donut-legend { font-size: 12px; }
.donut-legend div { display: flex; align-items: center; gap: 7px; margin-bottom: 5px; color: var(--text-dim); }
.donut-legend .sw { width: 9px; height: 9px; border-radius: 2px; }
.donut-legend b { color: var(--text-primary); font-family: var(--font-mono); margin-left: auto; }

.mid-grid { display: grid; grid-template-columns: 1.6fr 1fr; gap: 12px; margin-bottom: 14px; }
.eq-row { display: grid; grid-template-columns: 92px 1fr 170px; gap: 12px; align-items: center; margin-bottom: 9px; }
.eq-row:last-child { margin-bottom: 0; }
.eq-name { font-family: var(--font-mono); font-size: 12px; }
.eq-bar { height: 18px; border-radius: 4px; overflow: hidden; display: flex; background: var(--bg-panel-2); border: 1px solid var(--grid-line); }
.eq-bar .seg-up { background: var(--up); height: 100%; opacity: 0.85; transition: width 0.4s ease; }
.eq-bar .seg-down { background: var(--down); height: 100%; opacity: 0.9; transition: width 0.4s ease; }
.eq-bar .seg-unknown { background: var(--warn); height: 100%; opacity: 0.4; transition: width 0.4s ease; }
.eq-stats { font-family: var(--font-mono); font-size: 11px; color: var(--text-dim); text-align: right; white-space: nowrap; }
.eq-stats .u { color: var(--up); } .eq-stats .d { color: var(--down); }
.legend { display: flex; gap: 14px; font-family: var(--font-mono); font-size: 10px; color: var(--text-dim); margin-top: 12px; }
.legend .sw { display: inline-block; width: 9px; height: 9px; border-radius: 2px; margin-right: 5px; vertical-align: middle; }

/* Zabbix-style per-equipment alarm grid */
.alarm-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 14px; }
.alarm-grid .panel { padding-bottom: 8px; }
.alarm-scroll { max-height: 240px; overflow-y: auto; }
.count-pill { font-family: var(--font-mono); font-size: 11px; background: var(--down); color: #fff; border-radius: 999px; padding: 1px 9px; font-weight: 600; }
.count-pill.zero { background: var(--grid-line); color: var(--text-dim); }

table { width: 100%; border-collapse: collapse; }
th { text-align: left; font-family: var(--font-mono); font-size: 10px; letter-spacing: 0.06em; text-transform: uppercase; color: var(--text-dim); padding: 8px 10px; border-bottom: 1px solid var(--grid-line); position: sticky; top: 0; background: var(--bg-panel); z-index: 2; }
td { padding: 7px 10px; border-bottom: 1px solid var(--grid-line); font-size: 12.5px; }
tr:last-child td { border-bottom: none; }
td.t { font-family: var(--font-mono); font-size: 11.5px; color: var(--accent); white-space: nowrap; }
td.dur { font-family: var(--font-mono); font-size: 11.5px; white-space: nowrap; }
.problem-tag { background: rgba(239,68,68,0.13); color: var(--down); border: 1px solid rgba(239,68,68,0.35); border-radius: 4px; padding: 2px 8px; font-size: 11.5px; font-family: var(--font-mono); white-space: nowrap; }
.alarm-empty { color: var(--text-dim); text-align: center; padding: 16px 0; font-size: 12.5px; }

.ev-badge { font-family: var(--font-mono); font-size: 11px; border-radius: 4px; padding: 2px 8px; white-space: nowrap; }
.ev-badge.down { background: rgba(239,68,68,0.13); color: var(--down); border: 1px solid rgba(239,68,68,0.35); }
.ev-badge.up { background: rgba(34,197,94,0.12); color: var(--up); border: 1px solid rgba(34,197,94,0.35); }

.filters { display: flex; gap: 8px; flex-wrap: wrap; align-items: center; margin-bottom: 12px; }
input[type="text"], input[type="password"], select { font-family: var(--font-body); font-size: 12.5px; color: var(--text-primary); background: var(--bg-panel-2); border: 1px solid var(--grid-line); border-radius: 7px; padding: 7px 10px; }
button { font-family: var(--font-body); font-weight: 600; font-size: 12.5px; color: var(--text-primary); background: var(--bg-panel-2); border: 1px solid var(--grid-line); border-radius: 7px; padding: 7px 13px; cursor: pointer; }
button:hover { border-color: var(--accent); }
button:disabled { opacity: 0.5; cursor: default; }
button.primary { background: var(--accent); color: #fff; border-color: var(--accent); }
button.danger-outline { border-color: var(--down); color: var(--down); }
.chip { font-family: var(--font-mono); font-size: 11px; padding: 6px 12px; border-radius: 999px; border: 1px solid var(--grid-line); background: var(--bg-panel-2); color: var(--text-dim); cursor: pointer; user-select: none; }
.chip.active { color: #fff; background: var(--accent); border-color: var(--accent); font-weight: 600; }
.spacer { flex: 1; }

.add-form { display: none; background: var(--bg-panel-2); border: 1px solid var(--grid-line); border-radius: var(--radius); padding: 13px; margin-bottom: 13px; gap: 8px; flex-wrap: wrap; align-items: center; }
.add-form.open { display: flex; }
.add-form input, .add-form select { background: var(--bg-base); }
.add-form .hint { font-size: 11.5px; color: var(--text-dim); width: 100%; }
.add-form .mode-tag { font-family: var(--font-mono); font-size: 10px; background: var(--warn); color: #0b0e14; border-radius: 4px; padding: 2px 8px; font-weight: 600; display: none; }
.add-form.editing .mode-tag { display: inline-block; }

.dot { display: inline-block; width: 8px; height: 8px; border-radius: 50%; margin-right: 7px; vertical-align: middle; }
.dot.up { background: var(--up); box-shadow: 0 0 5px var(--up); }
.dot.down { background: var(--down); box-shadow: 0 0 5px var(--down); }
.dot.unknown { background: var(--warn); }
td.ip, td.ms { font-family: var(--font-mono); color: var(--text-dim); font-size: 11.5px; }
td.ip a { color: var(--accent); text-decoration: none; border-bottom: 1px dotted var(--accent); }
td.ip a:hover { border-bottom-style: solid; }
td.downdur { font-family: var(--font-mono); font-size: 11.5px; color: var(--down); }
.open-btn, .edit-btn { font-family: var(--font-mono); font-size: 10.5px; padding: 3px 9px; border: 1px solid var(--grid-line); border-radius: 5px; background: transparent; color: var(--text-dim); cursor: pointer; }
.open-btn:hover { border-color: var(--accent); color: var(--accent); }
.edit-btn:hover { border-color: var(--warn); color: var(--warn); }
.del-btn { font-family: var(--font-mono); font-size: 10.5px; padding: 3px 7px; border: 1px solid transparent; border-radius: 5px; background: transparent; color: var(--text-dim); cursor: pointer; }
.del-btn:hover { border-color: var(--down); color: var(--down); }
.empty { text-align: center; color: var(--text-dim); padding: 34px 0; }

/* Users management */
.perm-badge { font-family: var(--font-mono); font-size: 10.5px; border-radius: 4px; padding: 2px 8px; }
.perm-badge.yes { background: rgba(34,197,94,0.12); color: var(--up); border: 1px solid rgba(34,197,94,0.35); }
.perm-badge.no { background: var(--bg-panel-2); color: var(--text-dim); border: 1px solid var(--grid-line); }
.perm-badge.admin { background: rgba(240,134,44,0.14); color: var(--orange); border: 1px solid rgba(240,134,44,0.4); }
.user-form { display: none; background: var(--bg-panel-2); border: 1px solid var(--grid-line); border-radius: var(--radius); padding: 13px; margin-bottom: 13px; gap: 8px; flex-wrap: wrap; align-items: center; }
.user-form.open { display: flex; }
.user-form input { background: var(--bg-base); }
.user-form label.chk { display: flex; align-items: center; gap: 6px; font-size: 12.5px; color: var(--text-primary); cursor: pointer; }
.req::after { content: ' *'; color: var(--down); }

/* IP allocation */
.ip-chip { font-family: var(--font-mono); font-size: 11.5px; padding: 5px 10px; border-radius: 6px; border: 1px solid var(--grid-line); background: var(--bg-panel-2); color: var(--text-primary); cursor: pointer; }
.ip-chip:hover { border-color: var(--up); color: var(--up); }
.ip-chips { display: flex; flex-wrap: wrap; gap: 6px; margin-top: 10px; }
.subnet-sum { font-family: var(--font-mono); font-size: 11.5px; color: var(--text-dim); margin-top: 10px; }
.subnet-sum b { color: var(--text-primary); }
.subnet-sum .free { color: var(--up); }

.toast { position: fixed; bottom: 22px; left: 50%; transform: translateX(-50%) translateY(90px); background: var(--bg-panel-2); border: 1px solid var(--accent); border-radius: var(--radius); padding: 10px 18px; font-size: 12.5px; transition: transform 0.25s ease; z-index: 2000; max-width: 90vw; }
.toast.show { transform: translateX(-50%) translateY(0); }
.toast.alert { border-color: var(--down); }

@media (max-width: 1100px) { .kpi-row { grid-template-columns: repeat(2, 1fr); } .mid-grid, .alarm-grid { grid-template-columns: 1fr; } }
@media (max-width: 760px) { .sidebar { display: none; } .kpi-row { grid-template-columns: 1fr; } }
</style>
</head>
<body>

<!-- ================== LOGIN SCREEN ================== -->
<div class="login-screen" id="loginScreen">
  <div class="login-card">
    <div class="login-left">
      <div class="logo-card"><img src="data:image/png;base64,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" alt="Interlink Telecom" /></div>
      <div class="brand">INTER<span class="o">LINK</span></div>
      <div class="brand-sub">TELECOM</div>
      <div class="rule"></div>
      <div class="sys-name">INFRA IP Monitor</div>
      <div class="sys-desc">ระบบตรวจสอบสถานะอุปกรณ์<br/>โครงสร้างพื้นฐานเครือข่าย<br/>ทั่วประเทศ</div>
      <div class="login-stats">
        <div class="stat"><div class="n" id="loginNodeCount">—</div><div class="l">Node ทั่วประเทศ</div></div>
        <div class="stat"><div class="n blue" id="loginGroupCount">—</div><div class="l">ประเภทอุปกรณ์</div></div>
      </div>
    </div>
    <div class="login-right">
      <div class="team">Infrastructure Team</div>
      <h1>เข้าสู่ระบบ</h1>
      <div class="sub">กรุณายืนยันตัวตนเพื่อเข้าใช้งาน</div>
      <label>USERNAME</label>
      <div class="field"><input type="text" id="loginUser" placeholder="กรอก username" autocomplete="off" /></div>
      <label>PASSWORD</label>
      <div class="field">
        <input type="password" id="loginPass" placeholder="••••••••" />
        <button class="eye-btn" id="eyeBtn" type="button">👁</button>
      </div>
      <button class="login-btn" id="loginBtn">เข้าสู่ระบบ</button>
      <div class="login-err" id="loginErr"></div>
      <div class="login-foot">© 2026 INFRA ITEL · Interlink Telecom PCL</div>
    </div>
  </div>
</div>

<!-- ================== APP ================== -->
<div class="app" id="app">

  <aside class="sidebar">
    <div class="logo"><div class="logo-chip"><img src="data:image/png;base64,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" alt="Interlink" /></div></div>
    <div class="logo-sub">INFRA · IP Monitor</div>
    <nav class="nav">
      <a href="javascript:void(0)" class="active" data-nav data-page="overview"><span class="ico">◈</span> Overview</a>
      <a href="javascript:void(0)" data-nav data-page="overview" data-scroll="#alarms"><span class="ico">⚠</span> Alarms <span class="pill zero" id="navAlarmPill">0</span></a>
      <a href="javascript:void(0)" data-nav data-page="overview" data-scroll="#report"><span class="ico">▤</span> Report</a>
      <a href="javascript:void(0)" data-nav data-page="overview" data-scroll="#devices"><span class="ico">▣</span> Devices</a>
      <a href="javascript:void(0)" data-nav data-page="ipalloc" id="ipNavLink"><span class="ico">⊞</span> IP Allocation</a>
      <a href="javascript:void(0)" data-nav data-page="eventlog"><span class="ico">≡</span> Event Log</a>
      <a href="javascript:void(0)" data-nav data-page="users" id="usersNavLink" style="display:none"><span class="ico">👤</span> Users</a>
    </nav>
    <div class="logout-row">
      <div style="font-size:11.5px; color:var(--text-dim); padding: 0 6px 8px;" id="whoAmI"></div>
      <button id="logoutBtn">ออกจากระบบ</button>
    </div>
    <div class="side-clock">
      <div class="time" id="clockTime">--:--:--</div>
      <div class="date" id="clockDate"></div>
    </div>
  </aside>

  <div class="main" id="top">
    <div class="topbar">
      <span class="crumb"><strong>NOC Dashboard</strong> · Interlink Telecom · Infrastructure</span>
      <div class="spacer"></div>
      <div class="status-pill"><span class="sdot" id="pillDot" style="background:var(--warn)"></span><span id="pillText">STANDBY</span></div>
      <button class="theme-btn" id="themeBtn" title="สลับโหมดสว่าง/มืด">🌙</button>
    </div>

    <div class="content">

      <!-- ==================== PAGE: OVERVIEW ==================== -->
      <div class="page active" id="page-overview">

      <div class="poll-strip">
        <span>Polling: <b id="pollState">standby</b></span>
        <span>Interval: <b>2 min</b></span>
        <span>Last sweep: <b id="lastScan">—</b> <span id="scanDuration"></span></span>
        <span>Next sweep: <b id="nextSweep">—</b></span>
        <div class="prog"><div class="fill" id="progressFill"></div></div>
        <span id="progressLabel"></span>
      </div>

      <div class="kpi-row">
        <div class="panel net-status">
          <h3>Network Status</h3>
          <div class="word" id="netWord">—</div>
          <div class="desc" id="netDesc">รอผล sweep แรก</div>
          <svg id="sparkline" width="100%" height="34" viewBox="0 0 200 34" preserveAspectRatio="none"></svg>
        </div>
        <div class="panel kpi">
          <h3>Nodes</h3>
          <div class="big" id="statTotal">0</div>
          <div class="sub-row">
            <div class="c-up" id="statUp">0<span>Up</span></div>
            <div class="c-down" id="statDown">0<span>Down</span></div>
            <div class="c-unk" id="statUnknown">0<span>Unchecked</span></div>
          </div>
        </div>
        <div class="panel kpi">
          <h3>Equipment Types</h3>
          <div class="big" id="statGroups">0</div>
          <div class="sub-row"><div id="statGroupTop" style="font-size:11.5px; font-weight:500; color:var(--text-dim)"></div></div>
        </div>
        <div class="panel kpi">
          <h3>Availability</h3>
          <div class="big" id="statAvail">—</div>
          <div class="sub-row"><div style="font-size:11.5px; font-weight:500; color:var(--text-dim)">ของ nodes ที่เช็คแล้วในรอบล่าสุด</div></div>
        </div>
        <div class="panel">
          <h3>Active Alerts</h3>
          <div class="donut-wrap">
            <svg id="alertDonut" width="86" height="86" viewBox="0 0 86 86"></svg>
            <div class="donut-legend">
              <div><span class="sw" style="background:var(--down)"></span>Down <b id="dlDown">0</b></div>
              <div><span class="sw" style="background:var(--up)"></span>Online <b id="dlUp">0</b></div>
              <div><span class="sw" style="background:var(--warn); opacity:0.6"></span>Unchecked <b id="dlUnk">0</b></div>
            </div>
          </div>
        </div>
      </div>

      <div class="mid-grid" id="report">
        <div class="panel">
          <h2>Equipment Status Report <span class="badge" id="reportBadge"></span></h2>
          <div id="eqReport"></div>
          <div class="legend">
            <span><span class="sw" style="background:var(--up)"></span>ONLINE</span>
            <span><span class="sw" style="background:var(--down)"></span>DOWN</span>
            <span><span class="sw" style="background:var(--warn); opacity:0.5"></span>UNCHECKED</span>
          </div>
        </div>
        <div class="panel">
          <h2>Device Health</h2>
          <div class="donut-wrap" style="justify-content:center; padding: 8px 0;">
            <svg id="healthDonut" width="150" height="150" viewBox="0 0 150 150"></svg>
          </div>
        </div>
      </div>

      <!-- ===== Per-equipment alarm panels (Zabbix-style) ===== -->
      <div id="alarms" class="alarm-grid"><!-- filled by JS --></div>

      <!-- ===== Devices ===== -->
      <div class="panel" id="devices">
        <h2>Devices <span class="badge" id="countNote"></span></h2>
        <div class="filters">
          <input type="text" id="search" placeholder="ค้นหา Node, IP, site..." style="min-width:210px;" />
          <select id="groupFilter"><option value="">ทุกประเภทอุปกรณ์</option></select>
          <div class="chip active" data-status="">All</div>
          <div class="chip" data-status="up">Online</div>
          <div class="chip" data-status="down">Down</div>
          <div class="chip" data-status="unknown">Unchecked</div>
          <div class="spacer"></div>
          <button id="exportBtn">Export CSV</button>
          <button id="addBtn">+ Add Device</button>
          <button id="stopBtn" style="display:none" class="danger-outline">หยุด sweep</button>
          <button id="scanNowBtn" class="primary">Scan now</button>
        </div>

        <div class="add-form" id="addForm">
          <span class="mode-tag">แก้ไข</span>
          <input type="text" id="fName" placeholder="ชื่อ Node เช่น REC BKK-XXX-1" style="flex:2; min-width:180px;" />
          <input type="text" id="fIp" placeholder="IP เช่น 172.20.6.10" style="flex:1; min-width:140px;" />
          <input type="text" id="fSite" placeholder="Site เช่น BKK-XXX" style="flex:1; min-width:110px;" />
          <select id="fGroup">
            <option>Rectifier</option><option>STS</option><option>CCTV</option>
            <option>Inverter</option><option>TeleAlarm</option><option>Other</option>
          </select>
          <input type="text" id="fOtherGroup" placeholder="พิมพ์ชื่ออุปกรณ์ใหม่ เช่น UPS" style="display:none; flex:1; min-width:150px;" />
          <button id="fSave" class="primary">บันทึก</button>
          <button id="fCancel">ยกเลิก</button>
          <span class="hint">อุปกรณ์ที่เพิ่ม/แก้ไขอยู่จนกว่าจะปิดหน้านี้ — กด Export CSV เพื่อเก็บรายการล่าสุด (ใช้ import เข้าระบบ server จริงได้)</span>
        </div>

        <table>
          <thead>
            <tr><th>Status</th><th>Node</th><th>IP</th><th>Equipment</th><th>Response</th><th>Down for</th><th style="width:170px"></th></tr>
          </thead>
          <tbody id="deviceRows"></tbody>
        </table>
        <div class="empty" id="emptyState" style="display:none">ไม่มีอุปกรณ์ตรงกับ filter นี้</div>
      </div>

      </div><!-- /page-overview -->

      <!-- ==================== PAGE: IP ALLOCATION ==================== -->
      <div class="page" id="page-ipalloc">
        <div class="panel">
          <h2>IP Allocation — ผัง IP ทุกอุปกรณ์ <span class="badge">Region 1-6 · เริ่ม .2 เว้นทีละ 4 (.2, .6, .10 ... .254)</span></h2>
          <div class="ipa-tabs" id="ipaTabs"></div>
          <div class="ipa-sub">
            <span style="font-size:12px; color:var(--text-dim);">วง:</span>
            <div id="ipaSubnets" style="display:flex; gap:6px;"></div>
            <div class="ipa-legend" id="ipaLegend"></div>
          </div>
          <div class="ipa-wrap">
            <table class="ipa-table" id="ipaTable"></table>
          </div>
          <div style="font-size:11px; color:var(--text-dim); margin-top:8px;" id="ipaFoot"></div>
        </div>
      </div><!-- /page-ipalloc -->

      <!-- ==================== PAGE: EVENT LOG ==================== -->
      <div class="page" id="page-eventlog">
        <div class="panel" id="eventlog">
          <h2>Event Log — ประวัติ Down/Up
            <span class="badge" id="evBadge">0 events</span>
            <input type="text" id="evSearch" placeholder="ค้นหา IP, Node, อุปกรณ์..." style="min-width:220px; margin-left:8px;" />
            <button id="exportLogBtn">Export Log CSV</button>
          </h2>
          <div class="alarm-scroll" style="max-height:calc(100vh - 260px);">
            <table>
              <thead><tr><th>Time</th><th>Node</th><th>Equipment</th><th>IP</th><th>Event</th><th>อยู่สถานะเดิมนาน</th></tr></thead>
              <tbody id="eventRows"></tbody>
            </table>
            <div class="alarm-empty" id="eventEmpty">ยังไม่มีเหตุการณ์ — event จะถูกบันทึกเมื่อสถานะอุปกรณ์เปลี่ยน (Down/Up)</div>
          </div>
          <div style="font-size:11px; color:var(--text-dim); margin-top:8px;">
            ⚠ Log เก็บในหน้านี้เท่านั้น — ปิดหน้าแล้วหาย กด Export Log CSV เพื่อเก็บไว้วิเคราะห์ · เวอร์ชัน server จริงเก็บลง database ถาวร
          </div>
        </div>
      </div><!-- /page-eventlog -->

      <!-- ==================== PAGE: USERS ==================== -->
      <div class="page" id="page-users">
      <div class="panel" id="users">
        <h2>Users — จัดการผู้ใช้งาน
          <span class="badge" id="userCount"></span>
          <button id="addUserBtn" style="margin-left:8px;">+ เพิ่มผู้ใช้</button>
        </h2>

        <div class="user-form" id="userForm">
          <span class="mode-tag" style="display:none;" id="userModeTag">แก้ไข</span>
          <input type="text" id="uFirst" placeholder="ชื่อ *" style="flex:1; min-width:120px;" />
          <input type="text" id="uLast" placeholder="นามสกุล *" style="flex:1; min-width:120px;" />
          <input type="text" id="uEmail" placeholder="Email *" style="flex:1.4; min-width:170px;" />
          <input type="text" id="uUser" placeholder="Username *" style="flex:1; min-width:110px;" autocomplete="off" />
          <input type="password" id="uPass" placeholder="Password *" style="flex:1; min-width:110px;" autocomplete="new-password" />
          <label class="chk"><input type="checkbox" id="uCanEdit" /> ให้สิทธิ์เพิ่ม/แก้ไข IP</label>
          <button id="uSave" class="primary">บันทึก</button>
          <button id="uCancel">ยกเลิก</button>
          <span class="hint">ทุกช่องที่มี * ต้องกรอก · ⚠ รายชื่อผู้ใช้เก็บในหน้านี้เท่านั้น ปิดหน้าแล้วหาย (ยกเว้นบัญชีผู้พัฒนาที่ฝังในไฟล์) — เวอร์ชัน server จริงเก็บถาวร</span>
        </div>

        <table>
          <thead><tr><th>ชื่อ-นามสกุล</th><th>Email</th><th>Username</th><th>สิทธิ์เพิ่ม/แก้ไข IP</th><th style="width:130px"></th></tr></thead>
          <tbody id="userRows"></tbody>
        </table>
      </div>
      </div><!-- /page-users -->

    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
(() => {
  // ============ CONFIG ============
  // บัญชีผู้พัฒนา (ฝังในไฟล์ — แก้ตรงนี้ได้) เช็คฝั่ง client เท่านั้น ไม่ใช่ความปลอดภัยจริง
  // เวอร์ชัน server จริงมี auth แท้ที่ตรวจฝั่ง server
  const users = [
    { username: 'infra', password: 'infraadmin', first: 'ผู้พัฒนา', last: 'ระบบ', email: 'infra@interlinktelecom.co.th', canEdit: true, admin: true, builtin: true },
  ];
  let currentUser = null;

  // ผังวง IP ตามประเภทอุปกรณ์ (Region 1-6 = octet ที่ 3, host = octet ที่ 4: 1-254)
  const SUBNET_PLAN = {
    CCTV: ['172.19'],
    Rectifier: ['172.20', '172.21'],
    STS: ['172.30', '172.31'],
    TeleAlarm: ['172.30', '172.31'],
    Inverter: ['172.30', '172.31'],
  };

  const PROBE_TIMEOUT_MS = 4000;
  const CONCURRENCY = 40;
  const SCAN_INTERVAL_MS = 2 * 60 * 1000;
  const MAX_EVENTS = 5000;

  // [name, ip, site, group]
  const RAW = [["REC ACR-ACR-1","172.20.2.14","ACR-ACR","Rectifier"],["REC ACR-ACR-2","172.21.2.10","ACR-ACR","Rectifier"],["REC ATG-ATG","172.21.1.10","ATG-ATG","Rectifier"],["REC AYA-AYA-1","172.20.1.86","AYA-AYA","Rectifier"],["REC AYA-AYA-2","172.20.1.226","AYA-AYA","Rectifier"],["REC AYA-BPC-1","172.20.1.90","AYA-BPC","Rectifier"],["REC AYA-BPC-2","172.20.1.210","AYA-BPC","Rectifier"],["REC AYA-BPN","172.20.1.26","AYA-BPN","Rectifier"],["REC AYA-LBL","172.20.1.10","AYA-LBL","Rectifier"],["REC AYA-PRA","172.21.1.2","AYA-PRA","Rectifier"],["REC AYA-SNA","172.20.1.238","AYA-SNA","Rectifier"],["REC AYA-WNI","172.20.1.42","AYA-WNI","Rectifier"],["REC BKK-ADM","172.20.6.242","BKK-ADM","Rectifier"],["REC BKK-BBR-1","172.20.6.222","BKK-BBR","Rectifier"],["REC BKK-BBR-2","172.21.6.22","BKK-BBR","Rectifier"],["REC BKK-BKE","172.21.6.2","BKK-BKE","Rectifier"],["REC BKK-CEV","172.20.6.230","BKK-CEV","Rectifier"],["REC BKK-CRK","172.20.6.82","BKK-CRK","Rectifier"],["REC BKK-CTW","172.20.6.42","BKK-CTW","Rectifier"],["REC BKK-IDC","172.21.6.18","BKK-IDC","Rectifier"],["REC BKK-ITEL-Fl 5","172.20.6.198","BKK-ITEL","Rectifier"],["REC BKK-ITM","172.20.6.62","BKK-ITM","Rectifier"],["REC BKK-KTI-1","172.20.6.178","BKK-KTI","Rectifier"],["REC BKK-LKB","172.20.6.94","BKK-LKB","Rectifier"],["REC BKK-LPA","172.20.6.74","BKK-LPA","Rectifier"],["REC BKK-MBI","172.20.6.174","BKK-MBI","Rectifier"],["REC BKK-MKS-CON1-1","172.20.6.86","BKK-MKS","Rectifier"],["REC BKK-MKS-CON2-1","172.20.6.142","BKK-MKS","Rectifier"],["REC BKK-MKS-CON2-2","172.20.6.146","BKK-MKS","Rectifier"],["REC BKK-NCK","172.20.6.114","BKK-NCK","Rectifier"],["REC BKK-NCN","172.20.6.210","BKK-NCN","Rectifier"],["REC BKK-NLK","172.20.6.190","BKK-NLK","Rectifier"],["REC BKK-NOC","172.20.6.78","BKK-NOC","Rectifier"],["REC BKK-ONT","172.20.6.182","BKK-ONT","Rectifier"],["REC BKK-PBM","172.20.6.246","BKK-PBM","Rectifier"],["REC BKK-PWT","172.21.6.14","BKK-PWT","Rectifier"],["REC BKK-RCD-1","172.20.0.42","BKK-RCD","Rectifier"],["REC BKK-RCD-2","172.20.6.186","BKK-RCD","Rectifier"],["REC BKK-RCD-3","172.21.6.26","BKK-RCD","Rectifier"],["REC BKK-RIT","172.20.6.46","BKK-RIT","Rectifier"],["REC BKK-RM2","172.20.6.50","BKK-RM2","Rectifier"],["REC BKK-RM4-1","172.20.6.70","BKK-RM4","Rectifier"],["REC BKK-RM4-2","172.20.6.26","BKK-RM4","Rectifier"],["REC BKK-RM9","172.20.6.214","BKK-RM9","Rectifier"],["REC BKK-SIAM","172.20.6.206","BKK-SIAM","Rectifier"],["REC BKK-SLG-1","172.20.6.34","BKK-SLG","Rectifier"],["REC BKK-SLG-2","172.20.6.54","BKK-SLG","Rectifier"],["REC BKK-SLM","172.20.6.218","BKK-SLM","Rectifier"],["REC BKK-SMI","172.20.6.10","BKK-SMI","Rectifier"],["REC BKK-SSW","172.20.6.66","BKK-SSW","Rectifier"],["REC BKK-STD","172.20.6.98","BKK-STD","Rectifier"],["REC BKK-TDR","172.20.6.102","BKK-TDR","Rectifier"],["REC BKK-TPN-1","172.20.6.162","BKK-TPN","Rectifier"],["REC BKK-TPN-2","172.20.6.166","BKK-TPN","Rectifier"],["REC BKK-TRN","172.20.6.158","BKK-TRN","Rectifier"],["REC BKK-UPS_RCD","172.20.6.250","BKK-UPS","Rectifier"],["REC BRM-BRM-1","172.20.2.122","BRM-BRM","Rectifier"],["REC BRM-BRM-2","172.20.2.234","BRM-BRM","Rectifier"],["REC BRM-KKD","172.20.2.182","BRM-KKD","Rectifier"],["REC BRM-STK","172.20.2.178","BRM-STK","Rectifier"],["REC CBI-ANK","172.20.5.74","CBI-ANK","Rectifier"],["REC CBI-BBG","172.20.5.154","CBI-BBG","Rectifier"],["REC CBI-BLG","172.20.5.130","CBI-BLG","Rectifier"],["REC CBI-BPS","172.20.5.158","CBI-BPS","Rectifier"],["REC CBI-BSN","172.20.5.86","CBI-BSN","Rectifier"],["REC CBI-BTG","172.20.5.138","CBI-BTG","Rectifier"],["REC CBI-BWN","172.20.5.26","CBI-BWN","Rectifier"],["REC CBI-CBI-1","172.20.5.54","CBI-CBI","Rectifier"],["REC CBI-CBI-2","172.20.5.170","CBI-CBI","Rectifier"],["REC CBI-HKP","172.20.5.82","CBI-HKP","Rectifier"],["REC CBI-LCB","172.20.5.14","CBI-LCB","Rectifier"],["REC CBI-NPR","172.20.5.10","CBI-NPR","Rectifier"],["REC CBI-PIT","172.20.5.106","CBI-PIT","Rectifier"],["REC CBI-PNM","172.20.5.150","CBI-PNM","Rectifier"],["REC CBI-PTL","172.20.5.102","CBI-PTL","Rectifier"],["REC CBI-PTY-1","172.20.5.50","CBI-PTY","Rectifier"],["REC CBI-PTY-2","172.20.5.114","CBI-PTY","Rectifier"],["REC CBI-TPR","172.20.5.18","CBI-TPR","Rectifier"],["REC CBI-TSL","172.20.5.90","CBI-TSL","Rectifier"],["REC CCO-BWA-1","172.20.5.46","CCO-BWA","Rectifier"],["REC CCO-CCO-1","172.20.5.42","CCO-CCO","Rectifier"],["REC CCO-CCO-2","172.20.5.174","CCO-CCO","Rectifier"],["REC CCO-DTG","172.20.5.126","CCO-DTG","Rectifier"],["REC CCO-PKM","172.20.5.162","CCO-PKM","Rectifier"],["REC CCO-SCK","172.20.5.94","CCO-SCK","Rectifier"],["REC CCO-WGO","172.20.5.98","CCO-WGO","Rectifier"],["REC CMI-CKN","172.20.3.134","CMI-CKN","Rectifier"],["REC CMI-CMI","172.20.3.74","CMI-CMI","Rectifier"],["REC CMI-CTG","172.21.3.22","CMI-CTG","Rectifier"],["REC CMI-DSK","172.20.3.2","CMI-DSK","Rectifier"],["REC CMI-FNG","172.21.3.10","CMI-FNG","Rectifier"],["REC CMI-MRM","172.20.3.222","CMI-MRM","Rectifier"],["REC CMI-SPT","172.20.3.202","CMI-SPT","Rectifier"],["REC CMI-SRP","172.21.3.14","CMI-SRP","Rectifier"],["REC CNT-CNT-1","172.20.3.86","CNT-CNT","Rectifier"],["REC CNT-CNT-2","172.20.3.254","CNT-CNT","Rectifier"],["REC CPM-BNR","172.20.2.6","CPM-BNR","Rectifier"],["REC CPM-CPM","172.20.2.26","CPM-CPM","Rectifier"],["REC CPM-KKO","172.20.2.142","CPM-KKO","Rectifier"],["REC CPN-CPN-1","172.21.4.22","CPN-CPN","Rectifier"],["REC CPN-CPN-2","172.21.4.26","CPN-CPN","Rectifier"],["REC CPN-LME-1","172.20.4.94","CPN-LME","Rectifier"],["REC CPN-LME-2","172.20.4.210","CPN-LME","Rectifier"],["REC CPN-LSN-1","172.20.4.90","CPN-LSN","Rectifier"],["REC CPN-LSN-2","172.21.4.42","CPN-LSN","Rectifier"],["REC CPN-MAR-1","172.20.4.10","CPN-MAR","Rectifier"],["REC CPN-MAR-2","172.20.4.14","CPN-MAR","Rectifier"],["REC CPN-SWE-1","172.20.4.2","CPN-SWE","Rectifier"],["REC CPN-SWE-2","172.20.4.6","CPN-SWE","Rectifier"],["REC CPN-TSE-1","172.20.4.86","CPN-TSE","Rectifier"],["REC CRI-CRI","172.20.3.6","CRI-CRI","Rectifier"],["REC CRI-MCN","172.20.3.246","CRI-MCN","Rectifier"],["REC CRI-MSI","172.20.3.198","CRI-MSI","Rectifier"],["REC CRI-SSM","172.20.3.230","CRI-SSM","Rectifier"],["REC CRI-WPP","172.20.3.10","CRI-WPP","Rectifier"],["REC CTI-CTI","172.20.5.34","CTI-CTI","Rectifier"],["REC CTI-SDO","172.20.5.2","CTI-SDO","Rectifier"],["REC KBI-KBI-1","172.20.4.118","KBI-KBI","Rectifier"],["REC KBI-KBI-2","172.21.4.38","KBI-KBI","Rectifier"],["REC KCB-BKO","172.20.5.190","KCB-BKO","Rectifier"],["REC KCB-KCB-1","172.20.1.134","KCB-KCB","Rectifier"],["REC KCB-KCB-2","172.20.1.202","KCB-KCB","Rectifier"],["REC KCB-PNT","172.20.1.174","KCB-PNT","Rectifier"],["REC KCB-SYK","172.21.1.14","KCB-SYK","Rectifier"],["REC KCB-TAM","172.20.1.222","KCB-TAM","Rectifier"],["REC KCB-TPP","172.21.1.18","KCB-TPP","Rectifier"],["REC KKN-BPD","172.20.2.138","KKN-BPD","Rectifier"],["REC KKN-CPR","172.20.2.2","KKN-CPR","Rectifier"],["REC KKN-KKN-1","172.20.2.150","KKN-KKN","Rectifier"],["REC KKN-KKN-2","172.21.2.22","KKN-KKN","Rectifier"],["REC KKN-KSK","172.20.2.86","KKN-KSK","Rectifier"],["REC KKN-MPN-1","172.20.2.106","KKN-MPN","Rectifier"],["REC KKN-MPN-2","172.21.2.14","KKN-MPN","Rectifier"],["REC KKN-NPG","172.20.2.202","KKN-NPG","Rectifier"],["REC KPT-KPT-1","172.20.3.126","KPT-KPT","Rectifier"],["REC KPT-KPT-2","172.20.3.174","KPT-KPT","Rectifier"],["REC KPT-SLB-1","172.20.3.122","KPT-SLB","Rectifier"],["REC KPT-SLB-2","172.20.3.190","KPT-SLB","Rectifier"],["REC KSN-KNR-1","172.20.2.54","KSN-KNR","Rectifier"],["REC KSN-KNR-2","172.20.2.254","KSN-KNR","Rectifier"],["REC KSN-KSN","172.20.2.246","KSN-KSN","Rectifier"],["REC LEI-CKN","172.20.2.98","LEI-CKN","Rectifier"],["REC LEI-LEI","172.20.2.170","LEI-LEI","Rectifier"],["REC LPG-HVG","172.20.3.82","LPG-HVG","Rectifier"],["REC LPG-KKA","172.20.3.214","LPG-KKA","Rectifier"],["REC LPG-LPG-1","172.20.3.102","LPG-LPG","Rectifier"],["REC LPG-LPG-2","172.20.3.154","LPG-LPG","Rectifier"],["REC LPG-MMO-1","172.20.3.138","LPG-MMO","Rectifier"],["REC LPG-MMO-2","172.21.3.34","LPG-MMO","Rectifier"],["REC LPG-NGO","172.20.3.78","LPG-NGO","Rectifier"],["REC LPG-THN","172.20.3.54","LPG-THN","Rectifier"],["REC LPN-LPN-1","172.20.3.70","LPN-LPN","Rectifier"],["REC LPN-LPN-2","172.21.3.30","LPN-LPN","Rectifier"],["REC LRI-CBD","172.20.1.234","LRI-CBD","Rectifier"],["REC LRI-KSR","172.20.1.46","LRI-KSR","Rectifier"],["REC LRI-LRI-1","172.20.1.94","LRI-LRI","Rectifier"],["REC LRI-LRI-2","172.20.1.214","LRI-LRI","Rectifier"],["REC LRI-PNK","172.20.1.162","LRI-PNK","Rectifier"],["REC LRI-STA","172.20.1.178","LRI-STA","Rectifier"],["REC MDH-MDH-1","172.20.2.130","MDH-MDH","Rectifier"],["REC MDH-MDH-2","172.21.2.18","MDH-MDH","Rectifier"],["REC MKM-KSI","172.20.2.250","MKM-KSI","Rectifier"],["REC MKM-MKM-1","172.20.2.62","MKM-MKM","Rectifier"],["REC MKM-MKM-2","172.21.2.2","MKM-MKM","Rectifier"],["REC MKM-TKY","172.20.2.174","MKM-TKY","Rectifier"],["REC NAN-NAN","172.20.3.26","NAN-NAN","Rectifier"],["REC NAN-WSA","172.21.3.6","NAN-WSA","Rectifier"],["REC NBI-BBT-1","172.20.6.126","NBI-BBT","Rectifier"],["REC NBI-BBT-2","172.20.6.150","NBI-BBT","Rectifier"],["REC NBI-CWG","172.20.6.22","NBI-CWG","Rectifier"],["REC NBI-CWN-1","172.20.6.110","NBI-CWN","Rectifier"],["REC NBI-CWN-2","172.20.6.106","NBI-CWN","Rectifier"],["REC NBI-KER","172.20.6.18","NBI-KER","Rectifier"],["REC NBI-KPP","172.20.6.238","NBI-KPP","Rectifier"],["REC NBI-SMK","172.20.6.226","NBI-SMK","Rectifier"],["REC NKI-NKI","172.20.2.94","NKI-NKI","Rectifier"],["REC NKI-SCM","172.20.2.226","NKI-SCM","Rectifier"],["REC NLP-NKG","172.20.2.218","NLP-NKG","Rectifier"],["REC NMA-BYI-1","172.20.2.102","NMA-BYI","Rectifier"],["REC NMA-BYI-2","172.20.2.154","NMA-BYI","Rectifier"],["REC NMA-DKT","172.20.2.190","NMA-DKT","Rectifier"],["REC NMA-HTL-1","172.20.2.82","NMA-HTL","Rectifier"],["REC NMA-HTL-2","172.20.2.126","NMA-HTL","Rectifier"],["REC NMA-JHO","172.20.2.78","NMA-JHO","Rectifier"],["REC NMA-KNP-1","172.21.1.26","NMA-KNP","Rectifier"],["REC NMA-KNP-2","172.21.1.30","NMA-KNP","Rectifier"],["REC NMA-NMA-1","172.20.2.134","NMA-NMA","Rectifier"],["REC NMA-NMA-2","172.21.2.26","NMA-NMA","Rectifier"],["REC NMA-PCG-1","172.20.2.30","NMA-PCG","Rectifier"],["REC NMA-PCG-2","172.20.2.162","NMA-PCG","Rectifier"],["REC NMA-PTC","172.20.2.186","NMA-PTC","Rectifier"],["REC NMA-SIK","172.20.2.10","NMA-SIK","Rectifier"],["REC NMA-SNN-1","172.20.2.42","NMA-SNN","Rectifier"],["REC NMA-SNN-2","172.21.2.30","NMA-SNN","Rectifier"],["REC NMA-TCR-1","172.20.2.110","NMA-TCR","Rectifier"],["REC NMA-TCR-2","172.20.2.158","NMA-TCR","Rectifier"],["REC NPM-NPM","172.20.2.46","NPM-NPM","Rectifier"],["REC NPM-TPM","172.20.2.50","NPM-TPM","Rectifier"],["REC NPT-DTM","172.20.1.246","NPT-DTM","Rectifier"],["REC NPT-KPS","172.20.1.98","NPT-KPS","Rectifier"],["REC NPT-NCS","172.20.1.74","NPT-NCS","Rectifier"],["REC NPT-NPT","172.20.1.30","NPT-NPT","Rectifier"],["REC NPT-PM5","172.20.1.182","NPT-PM5","Rectifier"],["REC NPT-WNR-1","172.20.1.138","NPT-WNR","Rectifier"],["REC NPT-WNR-2","172.20.1.142","NPT-WNR","Rectifier"],["REC NRT-CHT-1","172.20.4.42","NRT-CHT","Rectifier"],["REC NRT-CHT-2","172.20.4.46","NRT-CHT","Rectifier"],["REC NRT-CHW-1","172.20.4.34","NRT-CHW","Rectifier"],["REC NRT-CHW-2","172.20.4.38","NRT-CHW","Rectifier"],["REC NRT-KCT-1","172.20.4.138","NRT-KCT","Rectifier"],["REC NRT-NRT-1","172.20.4.110","NRT-NRT","Rectifier"],["REC NRT-SCI","172.21.4.14","NRT-SCI","Rectifier"],["REC NRT-TSG-1","172.20.4.150","NRT-TSG","Rectifier"],["REC NRT-TSG-2","172.20.4.186","NRT-TSG","Rectifier"],["REC NSN-CSN-1","172.20.3.118","NSN-CSN","Rectifier"],["REC NSN-CSN-2","172.20.3.234","NSN-CSN","Rectifier"],["REC NSN-NBN","172.20.3.226","NSN-NBN","Rectifier"],["REC NSN-NSN-1","172.20.3.22","NSN-NSN","Rectifier"],["REC NSN-NSN-2","172.20.3.194","NSN-NSN","Rectifier"],["REC NSN-PNP-1","172.20.3.114","NSN-PNP","Rectifier"],["REC NSN-PNP-2","172.20.3.146","NSN-PNP","Rectifier"],["REC NSN-TKE","172.21.3.26","NSN-TKE","Rectifier"],["REC NWT-NWT","172.20.4.234","NWT-NWT","Rectifier"],["REC NWT-SKL","172.20.4.178","NWT-SKL","Rectifier"],["REC NWT-TYM","172.20.4.174","NWT-TYM","Rectifier"],["REC NYK-TBN","172.20.5.134","NYK-TBN","Rectifier"],["REC PBI-CHM-1","172.20.1.22","PBI-CHM","Rectifier"],["REC PBI-CHM-2","172.20.1.54","PBI-CHM","Rectifier"],["REC PBI-PBI-1","172.20.1.62","PBI-PBI","Rectifier"],["REC PBI-PBI-2","172.20.1.106","PBI-PBI","Rectifier"],["REC PBI-WMN-1","172.20.1.118","PBI-WMN","Rectifier"],["REC PBN-LKO","172.20.3.46","PBN-LKO","Rectifier"],["REC PBN-LSK","172.20.3.218","PBN-LSK","Rectifier"],["REC PBN-NNO","172.20.3.58","PBN-NNO","Rectifier"],["REC PBN-NPI","172.20.3.250","PBN-NPI","Rectifier"],["REC PBN-PBN","172.20.3.42","PBN-PBN","Rectifier"],["REC PBN-WBI","172.20.3.34","PBN-WBI","Rectifier"],["REC PCT-BMN","172.20.3.110","PCT-BMN","Rectifier"],["REC PCT-PCT-1","172.20.3.94","PCT-PCT","Rectifier"],["REC PCT-PCT-2","172.21.3.2","PCT-PCT","Rectifier"],["REC PCT-TKO","172.20.3.50","PCT-TKO","Rectifier"],["REC PCT-TPH","172.20.3.238","PCT-TPH","Rectifier"],["REC PKN-BSY-1","172.20.1.14","PKN-BSY","Rectifier"],["REC PKN-BSY-2","172.20.1.114","PKN-BSY","Rectifier"],["REC PKN-HHN-1","172.20.1.34","PKN-HHN","Rectifier"],["REC PKN-HHN-2","172.20.1.110","PKN-HHN","Rectifier"],["REC PKN-KBR-1","172.20.1.146","PKN-KBR","Rectifier"],["REC PKN-KBR-2","172.20.1.150","PKN-KBR","Rectifier"],["REC PKN-KLK-1","172.20.1.66","PKN-KLK","Rectifier"],["REC PKN-KLK-2","172.21.1.34","PKN-KLK","Rectifier"],["REC PKN-PBR-1","172.20.1.38","PKN-PBR","Rectifier"],["REC PKN-PBR-2","172.21.1.38","PKN-PBR","Rectifier"],["REC PKN-PKN-1","172.20.1.18","PKN-PKN","Rectifier"],["REC PKN-PKN-2","172.20.1.166","PKN-PKN","Rectifier"],["REC PKN-RTG-1","172.20.1.6","PKN-RTG","Rectifier"],["REC PKN-TSK-1","172.20.1.154","PKN-TSK","Rectifier"],["REC PKN-TSK-2","172.20.1.158","PKN-TSK","Rectifier"],["REC PKT-CLG","172.20.4.78","PKT-CLG","Rectifier"],["REC PKT-KRN","172.20.4.74","PKT-KRN","Rectifier"],["REC PKT-PKT","172.20.4.142","PKT-PKT","Rectifier"],["REC PKT-PTG","172.20.4.82","PKT-PTG","Rectifier"],["REC PKT-SST","172.20.4.242","PKT-SST","Rectifier"],["REC PKT-TKT","172.20.4.250","PKT-TKT","Rectifier"],["REC PLG-BKW-1","172.20.4.50","PLG-BKW","Rectifier"],["REC PLG-BKW-2","172.20.4.54","PLG-BKW","Rectifier"],["REC PLG-NND-1","172.20.4.98","PLG-NND","Rectifier"],["REC PLG-PLG-1","172.20.4.154","PLG-PLG","Rectifier"],["REC PLG-PLG-2","172.20.4.222","PLG-PLG","Rectifier"],["REC PLK-PLK-1","172.20.3.98","PLK-PLK","Rectifier"],["REC PLK-PLK-2","172.20.3.162","PLK-PLK","Rectifier"],["REC PLK-WCN","172.20.3.38","PLK-WCN","Rectifier"],["REC PNA-PNA-1","172.20.4.198","PNA-PNA","Rectifier"],["REC PNA-PNA-2","172.21.4.58","PNA-PNA","Rectifier"],["REC PNA-TKP","172.20.4.158","PNA-TKP","Rectifier"],["REC PNA-TMG","172.20.4.114","PNA-TMG","Rectifier"],["REC PRE-DCI-1","172.20.3.106","PRE-DCI","Rectifier"],["REC PRE-DCI-2","172.20.3.158","PRE-DCI","Rectifier"],["REC PRE-PRE","172.20.3.90","PRE-PRE","Rectifier"],["REC PRE-RKG","172.20.3.30","PRE-RKG","Rectifier"],["REC PRI-KBB","172.20.5.66","PRI-KBB","Rectifier"],["REC PRI-PRI","172.20.5.62","PRI-PRI","Rectifier"],["REC PTE-DTAC-RST","172.20.6.30","PTE-DTAC","Rectifier"],["REC PTE-KL4","172.20.6.58","PTE-KL4","Rectifier"],["REC PTE-KLL","172.20.6.154","PTE-KLL","Rectifier"],["REC PTE-PTE","172.20.6.234","PTE-PTE","Rectifier"],["REC PTE-RST-1","172.20.6.6","PTE-RST","Rectifier"],["REC PTE-RST-2","172.20.6.202","PTE-RST","Rectifier"],["REC PTN-KPO-1","172.20.4.166","PTN-KPO","Rectifier"],["REC PTN-KPO-2","172.21.4.2","PTN-KPO","Rectifier"],["REC PTN-SBR","172.20.4.246","PTN-SBR","Rectifier"],["REC PYO-PYO","172.20.3.18","PYO-PYO","Rectifier"],["REC RBI-CBG","172.21.1.6","RBI-CBG","Rectifier"],["REC RBI-NPD-1","172.20.0.26","RBI-NPD","Rectifier"],["REC RBI-NPD-2","172.20.1.2","RBI-NPD","Rectifier"],["REC RBI-NPD-3","172.20.1.194","RBI-NPD","Rectifier"],["REC RBI-NPD-4","172.20.1.198","RBI-NPD","Rectifier"],["REC RBI-RBI-1","172.20.0.22","RBI-RBI","Rectifier"],["REC RBI-RBI-2","172.20.1.126","RBI-RBI","Rectifier"],["REC RBI-SPG","172.20.1.218","RBI-SPG","Rectifier"],["REC RET-RET-1","172.20.2.58","RET-RET","Rectifier"],["REC RET-RET-2","172.21.2.6","RET-RET","Rectifier"],["REC RET-SWP","172.20.2.22","RET-SWP","Rectifier"],["REC RYG-BNL","172.20.5.178","RYG-BNL","Rectifier"],["REC RYG-EST","172.20.5.78","RYG-EST","Rectifier"],["REC RYG-KLG","172.20.5.38","RYG-KLG","Rectifier"],["REC RYG-MTP","172.20.5.182","RYG-MTP","Rectifier"],["REC RYG-NPA","172.20.5.110","RYG-NPA","Rectifier"],["REC RYG-NPN","172.20.5.118","RYG-NPN","Rectifier"],["REC RYG-PDG","172.20.5.70","RYG-PDG","Rectifier"],["REC RYG-RYG","172.20.5.22","RYG-RYG","Rectifier"],["REC SBR-SBR","172.20.1.50","SBR-SBR","Rectifier"],["REC SKA-HYI-1","172.20.4.106","SKA-HYI","Rectifier"],["REC SKA-HYI-2","172.20.4.190","SKA-HYI","Rectifier"],["REC SKA-HYN-1","172.21.4.6","SKA-HYN","Rectifier"],["REC SKA-HYN-2","172.21.4.10","SKA-HYN","Rectifier"],["REC SKA-KGE-1","172.20.4.66","SKA-KGE","Rectifier"],["REC SKA-KGE-2","172.20.4.70","SKA-KGE","Rectifier"],["REC SKA-KLG","172.21.4.18","SKA-KLG","Rectifier"],["REC SKA-KNG-1","172.20.4.58","SKA-KNG","Rectifier"],["REC SKA-KNG-2","172.20.4.62","SKA-KNG","Rectifier"],["REC SKA-NTW","172.20.4.230","SKA-NTW","Rectifier"],["REC SKA-PDB-1","172.20.0.10","SKA-PDB","Rectifier"],["REC SKA-PDB-2","172.20.0.14","SKA-PDB","Rectifier"],["REC SKA-SKA","172.20.4.162","SKA-SKA","Rectifier"],["REC SKM-SKM-1","172.20.0.18","SKM-SKM","Rectifier"],["REC SKM-SKM-2","172.21.1.46","SKM-SKM","Rectifier"],["REC SKN-ECI","172.20.1.170","SKN-ECI","Rectifier"],["REC SKN-SKN-1","172.20.1.70","SKN-SKN","Rectifier"],["REC SKW-AYT-1","172.20.0.2","SKW-AYT","Rectifier"],["REC SKW-AYT-2","172.20.0.6","SKW-AYT","Rectifier"],["REC SKW-KCN","172.20.5.6","SKW-KCN","Rectifier"],["REC SKW-SKW","172.20.5.58","SKW-SKW","Rectifier"],["REC SKW-TKW","172.20.5.166","SKW-TKW","Rectifier"],["REC SKW-WNY","172.20.5.142","SKW-WNY","Rectifier"],["REC SNI-BNN-1","172.20.4.26","SNI-BNN","Rectifier"],["REC SNI-BNN-2","172.20.4.30","SNI-BNN","Rectifier"],["REC SNI-BSG-1","172.20.4.130","SNI-BSG","Rectifier"],["REC SNI-BSG-2","172.20.4.182","SNI-BSG","Rectifier"],["REC SNI-CKM","172.20.4.194","SNI-CKM","Rectifier"],["REC SNI-CYA-1","172.20.4.18","SNI-CYA","Rectifier"],["REC SNI-CYA-2","172.20.4.22","SNI-CYA","Rectifier"],["REC SNI-KSK","172.21.4.30","SNI-KSK","Rectifier"],["REC SNI-SNI-1","172.20.4.146","SNI-SNI","Rectifier"],["REC SNI-SNI-2","172.20.4.202","SNI-SNI","Rectifier"],["REC SNI-TCG-1","172.20.4.122","SNI-TCG","Rectifier"],["REC SNI-TCG-2","172.20.4.218","SNI-TCG","Rectifier"],["REC SNI-TKB","172.20.4.238","SNI-TKB","Rectifier"],["REC SNK-PAK","172.20.2.222","SNK-PAK","Rectifier"],["REC SNK-SNK","172.20.2.38","SNK-SNK","Rectifier"],["REC SNK-SWD","172.20.2.114","SNK-SWD","Rectifier"],["REC SPB-SMK","172.20.1.78","SPB-SMK","Rectifier"],["REC SPB-SPB-1","172.20.1.130","SPB-SPB","Rectifier"],["REC SPB-SPB-2","172.20.1.206","SPB-SPB","Rectifier"],["REC SPB-UTG","172.20.1.230","SPB-UTG","Rectifier"],["REC SPK-BNA","172.20.6.14","SPK-BNA","Rectifier"],["REC SPK-DTAC-SN","172.20.6.2","SPK-DTAC","Rectifier"],["REC SPK-PKS","172.20.6.122","SPK-PKS","Rectifier"],["REC SPK-SDN","172.20.6.134","SPK-SDN","Rectifier"],["REC SRI-HBG","172.20.1.102","SRI-HBG","Rectifier"],["REC SRI-HKG-1","172.20.1.122","SRI-HKG","Rectifier"],["REC SRI-KKI-1","172.20.1.82","SRI-KKI","Rectifier"],["REC SRI-MLK","172.20.1.250","SRI-MLK","Rectifier"],["REC SRI-SRI","172.21.1.22","SRI-SRI","Rectifier"],["REC SRN-SRN-1","172.20.2.66","SRN-SRN","Rectifier"],["REC SRN-SRN-2","172.20.2.230","SRN-SRN","Rectifier"],["REC SRN-SRT-1","172.20.2.34","SRN-SRT","Rectifier"],["REC SRN-TTM","172.20.2.146","SRN-TTM","Rectifier"],["REC SSK-KTL","172.20.2.214","SSK-KTL","Rectifier"],["REC SSK-SSK-1","172.20.2.70","SSK-SSK","Rectifier"],["REC SSK-SSK-2","172.20.2.238","SSK-SSK","Rectifier"],["REC STI-STI-1","172.20.3.14","STI-STI","Rectifier"],["REC STI-STI-2","172.20.3.186","STI-STI","Rectifier"],["REC STI-SWK","172.20.3.206","STI-SWK","Rectifier"],["REC STN-STN-1","172.20.4.214","STN-STN","Rectifier"],["REC TAK-MST-1","172.20.3.178","TAK-MST","Rectifier"],["REC TAK-MST-2","172.20.3.182","TAK-MST","Rectifier"],["REC TAK-SMN-1","172.20.3.242","TAK-SMN","Rectifier"],["REC TAK-SMN-2","172.21.3.18","TAK-SMN","Rectifier"],["REC TAK-TAK-1","172.20.3.130","TAK-TAK","Rectifier"],["REC TAK-TAK-2","172.20.3.170","TAK-TAK","Rectifier"],["REC TRD-TRD","172.20.5.146","TRD-TRD","Rectifier"],["REC TRG-HYT-1","172.20.4.134","TRG-HYT","Rectifier"],["REC TRG-TRG-1","172.20.4.126","TRG-TRG","Rectifier"],["REC UBN-DUM","172.20.2.166","UBN-DUM","Rectifier"],["REC UBN-PSH","172.20.2.210","UBN-PSH","Rectifier"],["REC UBN-UBN","172.20.2.118","UBN-UBN","Rectifier"],["REC UBN-WCR-1","172.20.2.74","UBN-WCR","Rectifier"],["REC UBN-WCR-2","172.20.2.242","UBN-WCR","Rectifier"],["REC UDN-BDG","172.20.2.198","UDN-BDG","Rectifier"],["REC UDN-BLM","172.20.2.194","UDN-BLM","Rectifier"],["REC UDN-UDN","172.20.2.90","UDN-UDN","Rectifier"],["REC UTI-UTI","172.20.3.150","UTI-UTI","Rectifier"],["REC UTT-BKN-1","172.20.3.62","UTT-BKN","Rectifier"],["REC UTT-BKN-2","172.20.3.210","UTT-BKN","Rectifier"],["REC UTT-UTT","172.20.6.38","UTT-UTT","Rectifier"],["REC UTT-WKP-1","172.20.3.66","UTT-WKP","Rectifier"],["REC UTT-WKP-2","172.20.3.166","UTT-WKP","Rectifier"],["REC YLA-YLA","172.20.4.170","YLA-YLA","Rectifier"],["REC YST-LNT","172.20.2.206","YST-LNT","Rectifier"],["REC YST-YST","172.20.2.18","YST-YST","Rectifier"],["REC CBI-NPR-2","172.20.5.30","CBI-NPR","Rectifier"],["REC AYA-HIT","172.20.1.58","AYA-HIT","Rectifier"],["REC BKK-HMK-4","172.20.6.90","BKK-HMK","Rectifier"],["REC KBI-ALK-1","172.20.4.102","KBI-ALK","Rectifier"],["REC PRI-304-1","172.20.5.122","PRI-304","Rectifier"],["REC BKK-BKE","172.20.6.130","BKK-BKE","Rectifier"],["REC BKK-HMK06","172.20.6.138","BKK-HMK0","Rectifier"],["REC CRI-BMI","172.20.3.142","CRI-BMI","Rectifier"],["REC CBI-BPS","172.21.4.98","CBI-BPS","Rectifier"],["REC Test Rectifier Cyber world","172.20.6.170","","Rectifier"],["REC KCB-BKO","172.20.1.186","KCB-BKO","Rectifier"],["REC CBI-SRC-1","172.20.5.186","CBI-SRC","Rectifier"],["REC KCB-BKO","172.20.1.190","KCB-BKO","Rectifier"],["REC CCO-BWA-2","172.20.5.194","CCO-BWA","Rectifier"],["REC BKK-TLH-2","172.20.6.194","BKK-TLH","Rectifier"],["REC CCO-BPK-1","172.20.5.198","CCO-BPK","Rectifier"],["REC CCO-BPK-2","172.20.5.202","CCO-BPK","Rectifier"],["REC SNI-BTK","172.20.4.206","SNI-BTK","Rectifier"],["REC CBI-SRC-2","172.20.5.206","CBI-SRC","Rectifier"],["REC CCO-BWA-3","172.20.5.210","CCO-BWA","Rectifier"],["REC CCO-BWA-4","172.20.5.214","CCO-BWA","Rectifier"],["REC PTN-PTN-1","172.20.4.226","PTN-PTN","Rectifier"],["REC PBI-PBI-3 New Con2","172.20.1.242","PBI-PBI","Rectifier"],["REC KBI-KPN-1","172.20.4.254","KBI-KPN","Rectifier"],["REC GLO-1","172.21.6.6","","Rectifier"],["REC GLO-2","172.21.6.10","","Rectifier"],["REC BKK-TCC-1","172.21.6.30","BKK-TCC","Rectifier"],["REC SRN-SRT-2","172.21.2.34","SRN-SRT","Rectifier"],["REC SNI-BTK-2","172.21.4.34","SNI-BTK","Rectifier"],["REC BKK-KTI-2","172.21.6.38","BKK-KTI","Rectifier"],["REC PKN-RTG-2","172.21.1.42","PKN-RTG","Rectifier"],["REC CPN-TSE-2","172.21.4.46","CPN-TSE","Rectifier"],["REC SRI-HKG-2","172.21.1.50","SRI-HKG","Rectifier"],["REC TRG-HYT-2","172.21.4.50","TRG-HYT","Rectifier"],["REC SRI-KKI-2","172.21.1.54","SRI-KKI","Rectifier"],["REC TRG-TRG-2","172.21.4.54","TRG-TRG","Rectifier"],["REC PKN-BSY-3 New Con2","172.21.1.58","PKN-BSY","Rectifier"],["REC PKN-BSY-4 New Con2","172.21.1.62","PKN-BSY","Rectifier"],["REC PLG-NND-2","172.21.4.62","PLG-NND","Rectifier"],["REC PBI-PBI-4  New Con2","172.21.1.66","PBI-PBI","Rectifier"],["REC SKA-HYN-3","172.21.4.66","SKA-HYN","Rectifier"],["REC SKN-SKN-2","172.21.1.70","SKN-SKN","Rectifier"],["REC SKA-HYN-4","172.21.4.70","SKA-HYN","Rectifier"],["REC PBI-WMN-2","172.21.1.74","PBI-WMN","Rectifier"],["REC LME03 New Con2","172.21.4.74","","Rectifier"],["REC SKM-APW","172.21.1.78","SKM-APW","Rectifier"],["REC LME04 New Con2","172.21.4.78","","Rectifier"],["REC SKM-APW","172.21.1.82","SKM-APW","Rectifier"],["REC New KBI-ALK-1","172.21.4.82","KBI-ALK","Rectifier"],["REC PBI-HCS-1","172.21.1.86","PBI-HCS","Rectifier"],["REC New KBI-ALK-2","172.21.4.86","KBI-ALK","Rectifier"],["REC PBI-HCS-2","172.21.1.90","PBI-HCS","Rectifier"],["REC New KBI-KPB-1","172.21.4.90","KBI-KPB","Rectifier"],["REC PKN-TTI-1","172.21.1.94","PKN-TTI","Rectifier"],["REC New KBI-KPB-2","172.21.4.94","KBI-KPB","Rectifier"],["REC PKN-TTI-2","172.21.1.98","PKN-TTI","Rectifier"],["REC PKN-TBR-1","172.21.1.102","PKN-TBR","Rectifier"],["REC CPN-CPN-3","172.21.4.102","CPN-CPN","Rectifier"],["REC PKN-TBR-2","172.21.1.106","PKN-TBR","Rectifier"],["REC NRT-KCT-2","172.21.4.106","NRT-KCT","Rectifier"],["REC PKN-TPD-1","172.21.1.110","PKN-TPD","Rectifier"],["REC CPN-PTO-1","172.21.4.110","CPN-PTO","Rectifier"],["REC PKN-TPD-2","172.21.1.114","PKN-TPD","Rectifier"],["REC CPN-PTO-2","172.21.4.114","CPN-PTO","Rectifier"],["REC PKN-DLH-1","172.21.1.118","PKN-DLH","Rectifier"],["REC CPN-NPO-1","172.21.4.118","CPN-NPO","Rectifier"],["REC PKN-DLH-2","172.21.1.122","PKN-DLH","Rectifier"],["REC CPN-NPO-2","172.21.4.122","CPN-NPO","Rectifier"],["REC PKN-KLK-3","172.21.1.126","PKN-KLK","Rectifier"],["REC SNI-NBK","172.21.4.126","SNI-NBK","Rectifier"],["REC PKN-KLK-4","172.21.1.130","PKN-KLK","Rectifier"],["REC SNI-NBK","172.21.4.130","SNI-NBK","Rectifier"],["REC SNI-BBL","172.21.4.134","SNI-BBL","Rectifier"],["REC SNI-BBL","172.21.4.138","SNI-BBL","Rectifier"],["REC SNI-KCD","172.21.4.142","SNI-KCD","Rectifier"],["REC SNI-KCD","172.21.4.146","SNI-KCD","Rectifier"],["REC NRT-SCN","172.21.4.150","NRT-SCN","Rectifier"],["REC NRT-SCN","172.21.4.154","NRT-SCN","Rectifier"],["REC PLG-NTM","172.21.4.158","PLG-NTM","Rectifier"],["REC PLG-NTM","172.21.4.162","PLG-NTM","Rectifier"],["REC SKA-RTP","172.21.4.166","SKA-RTP","Rectifier"],["REC SKA-RTP","172.21.4.170","SKA-RTP","Rectifier"],["REC SKA-PDB-3","172.21.4.174","SKA-PDB","Rectifier"],["REC SKA-PDB-4","172.21.4.178","SKA-PDB","Rectifier"],["STS ACR-ACR","172.30.2.150","ACR-ACR","STS"],["STS ATG-ATG","172.30.1.194","ATG-ATG","STS"],["STS AYA-BPN","172.30.1.174","AYA-BPN","STS"],["STS AYA-LBL","172.30.1.14","AYA-LBL","STS"],["STS AYA-PRA","172.30.1.50","AYA-PRA","STS"],["STS AYA-SNA","172.30.1.46","AYA-SNA","STS"],["STS AYA-WNI","172.30.1.198","AYA-WNI","STS"],["STS BKK-BBR","172.30.6.166","BKK-BBR","STS"],["STS BKK-BKE-1","172.30.6.98","BKK-BKE","STS"],["STS BKK-CRK","172.30.6.54","BKK-CRK","STS"],["STS BKK-HMK","172.30.6.58","BKK-HMK","STS"],["STS BKK-KPP","172.30.6.214","BKK-KPP","STS"],["STS BKK-KTI","172.30.6.78","BKK-KTI","STS"],["STS BKK-LKB","172.30.6.86","BKK-LKB","STS"],["STS BKK-LKB-2","172.30.6.254","BKK-LKB","STS"],["STS BKK-LPA","172.30.6.14","BKK-LPA","STS"],["STS BKK-MBI-1","172.30.6.122","BKK-MBI","STS"],["STS BKK-MBI-2","172.30.6.198","BKK-MBI","STS"],["STS BKK-MKS-1","172.30.6.6","BKK-MKS","STS"],["STS BKK-MKS-2","172.30.6.142","BKK-MKS","STS"],["STS BKK-NCK","172.30.6.66","BKK-NCK","STS"],["STS BKK-NCN","172.30.6.178","BKK-NCN","STS"],["STS BKK-NLK","172.30.6.222","BKK-NLK","STS"],["STS BKK-ONT","172.30.6.74","BKK-ONT","STS"],["STS BKK-PBM","172.31.6.18","BKK-PBM","STS"],["STS BKK-RIT-1","172.30.6.18","BKK-RIT","STS"],["STS BKK-RIT-2","172.30.6.230","BKK-RIT","STS"],["STS BKK-RM4","172.30.6.126","BKK-RM4","STS"],["STS BKK-RM9","172.30.6.174","BKK-RM9","STS"],["STS BKK-RM2-1","172.31.6.22","BKK-RM2","STS"],["STS BKK-RM2-2","172.30.6.82","BKK-RM2","STS"],["STS BKK-SLG-1","172.30.6.110","BKK-SLG","STS"],["STS BKK-SLG-2","172.30.6.118","BKK-SLG","STS"],["STS BKK-SLM","172.30.6.190","BKK-SLM","STS"],["STS BKK-SMI","172.31.6.30","BKK-SMI","STS"],["STS BKK-SSW","172.30.6.70","BKK-SSW","STS"],["STS BKK-STD","172.30.6.134","BKK-STD","STS"],["STS BKK-TDR","172.31.6.38","BKK-TDR","STS"],["STS BKK-TPN","172.30.6.114","BKK-TPN","STS"],["STS BKK-TRN","172.31.6.6","BKK-TRN","STS"],["STS BRM-BRM","172.30.2.90","BRM-BRM","STS"],["STS BRM-KKD","172.30.2.210","BRM-KKD","STS"],["STS BRM-STK","172.30.2.42","BRM-STK","STS"],["STS CBI-ANK","172.30.5.58","CBI-ANK","STS"],["STS CBI-BBG","172.30.5.174","CBI-BBG","STS"],["STS CBI-BLG","172.30.5.150","CBI-BLG","STS"],["STS CBI-BPS","172.30.5.178","CBI-BPS","STS"],["STS CBI-BSN","172.30.5.62","CBI-BSN","STS"],["STS CBI-BTG","172.30.5.162","CBI-BTG","STS"],["STS CBI-BWN","172.30.5.26","CBI-BWN","STS"],["STS CBI-CBI-1","172.30.5.6","CBI-CBI","STS"],["STS CBI-HKP","172.30.5.2","CBI-HKP","STS"],["STS CBI-LCB","172.30.5.38","CBI-LCB","STS"],["STS CBI-NPR","172.30.5.46","CBI-NPR","STS"],["STS CBI-PIT","172.30.5.70","CBI-PIT","STS"],["STS CBI-PNM","172.30.5.166","CBI-PNM","STS"],["STS CBI-PTL","172.30.5.170","CBI-PTL","STS"],["STS CBI-PTY","172.30.5.10","CBI-PTY","STS"],["STS CBi-SRC","172.30.5.202","","STS"],["STS CBI-TPR","172.30.5.42","CBI-TPR","STS"],["STS CBI-TSL","172.30.5.66","CBI-TSL","STS"],["STS CCO-BWA","172.30.5.126","CCO-BWA","STS"],["STS CCO-CCO","172.30.5.118","CCO-CCO","STS"],["STS CCO-DTG","172.30.5.90","CCO-DTG","STS"],["STS CCO-PKM","172.30.5.154","CCO-PKM","STS"],["STS CCO-SCK","172.30.5.130","CCO-SCK","STS"],["STS CMI-CKN","172.30.3.26","CMI-CKN","STS"],["STS CMI-CMI","172.30.3.42","CMI-CMI","STS"],["STS CMI-CTG","172.30.3.254","CMI-CTG","STS"],["STS CMI-DSK","172.30.3.58","CMI-DSK","STS"],["STS CMI-FNG","172.30.3.238","CMI-FNG","STS"],["STS CMI-MRM","172.30.3.170","CMI-MRM","STS"],["STS CMI-SPT","172.30.3.38","CMI-SPT","STS"],["STS CMI-SRP","172.30.3.246","CMI-SRP","STS"],["STS CNT-CNT","172.30.3.186","CNT-CNT","STS"],["STS CPM-BNR","172.30.2.110","CPM-BNR","STS"],["STS CPM-CPM","172.30.2.102","CPM-CPM","STS"],["STS CPM-KKO","172.30.2.26","CPM-KKO","STS"],["STS CPN-CPN","172.30.4.190","CPN-CPN","STS"],["STS CPN-LSN","172.30.4.110","CPN-LSN","STS"],["STS CPN-SWE","172.30.4.106","CPN-SWE","STS"],["STS CPN-TSE","172.30.4.118","CPN-TSE","STS"],["STS CRI-CRI","172.30.3.50","CRI-CRI","STS"],["STS CRI-MCN","172.30.3.218","CRI-MCN","STS"],["STS CRI-MSI","172.30.3.34","CRI-MSI","STS"],["STS CRI-SSM","172.30.3.226","CRI-SSM","STS"],["STS CRI-WPP","172.30.3.62","CRI-WPP","STS"],["STS CTI-CTI","172.30.5.34","CTI-CTI","STS"],["STS KBI-ALK","172.30.4.194","KBI-ALK","STS"],["STS KBI-KBI","172.30.4.86","KBI-KBI","STS"],["STS KCB-BKO","172.30.1.166","KCB-BKO","STS"],["STS KCB-KCB","172.30.1.150","KCB-KCB","STS"],["STS KCB-PNT","172.30.1.66","KCB-PNT","STS"],["STS KCB-TAM","172.30.1.90","KCB-TAM","STS"],["STS KKN-BPD","172.30.2.46","KKN-BPD","STS"],["STS KKN-CPR","172.30.2.134","KKN-CPR","STS"],["STS KKN-KKN","172.30.2.38","KKN-KKN","STS"],["STS KKN-KKN No.2","172.30.2.238","KKN-KKN","STS"],["STS KKN-KSK","172.30.2.130","KKN-KSK","STS"],["STS KKN-MPN","172.30.2.126","KKN-MPN","STS"],["STS KKN-NPG","172.30.2.214","KKN-NPG","STS"],["STS KPT-KPT","172.30.3.82","KPT-KPT","STS"],["STS KPT-SLB","172.30.3.102","KPT-SLB","STS"],["STS KSN-KNR","172.30.2.142","KSN-KNR","STS"],["STS KSN-KSN-1","172.30.2.138","KSN-KSN","STS"],["STS LEI-LEI","172.30.2.54","LEI-LEI","STS"],["STS LPG-HVG","172.30.3.190","LPG-HVG","STS"],["STS LPG-KKA","172.30.3.214","LPG-KKA","STS"],["STS LPG-LPG","172.30.3.178","LPG-LPG","STS"],["STS LPG-NGO","172.30.3.206","LPG-NGO","STS"],["STS LPG-THN","172.30.3.182","LPG-THN","STS"],["STS LPN-LPN","172.30.3.54","LPN-LPN","STS"],["STS LRI-CBD","172.30.2.206","LRI-CBD","STS"],["STS LRI-KSR","172.30.2.182","LRI-KSR","STS"],["STS LRI-LRI","172.30.1.102","LRI-LRI","STS"],["STS LRI-PNK","172.30.1.54","LRI-PNK","STS"],["STS LRI-STA","172.30.1.106","LRI-STA","STS"],["STS MDH-MDH","172.30.2.6","MDH-MDH","STS"],["STS MKM-KSI","172.30.2.250","MKM-KSI","STS"],["STS MKM-MKM","172.30.2.122","MKM-MKM","STS"],["STS MKM-TKY","172.30.2.58","MKM-TKY","STS"],["STS NAN-NAN","172.30.3.66","NAN-NAN","STS"],["STS NAN-WSA","172.30.3.242","NAN-WSA","STS"],["STS NBI-BBT","172.30.6.30","NBI-BBT","STS"],["STS NBI-CWN-1","172.30.6.2","NBI-CWN","STS"],["STS NBI-CWN-2","172.30.6.102","NBI-CWN","STS"],["STS NBI-KER","172.30.6.26","NBI-KER","STS"],["STS NBI-SMK","172.30.6.170","NBI-SMK","STS"],["STS NKI-NKI","172.30.2.114","NKI-NKI","STS"],["STS NKI-SCM","172.30.2.246","NKI-SCM","STS"],["STS NLP-NKG","172.30.2.34","NLP-NKG","STS"],["STS NMA-BYI","172.30.2.82","NMA-BYI","STS"],["STS NMA-DKT","172.30.2.174","NMA-DKT","STS"],["STS NMA-HTL","172.30.2.86","NMA-HTL","STS"],["STS NMA-JHO","172.30.2.30","NMA-JHO","STS"],["STS NMA-NMA","172.30.2.62","NMA-NMA","STS"],["STS NMA-PCG","172.30.1.26","NMA-PCG","STS"],["STS NMA-PTC","172.30.2.178","NMA-PTC","STS"],["STS NMA-SNN","172.30.2.78","NMA-SNN","STS"],["STS NMA-TCR-1","172.30.2.74","NMA-TCR","STS"],["STS NMA-TCR-2","172.30.2.70","NMA-TCR","STS"],["STS NPM-NPM","172.30.2.194","NPM-NPM","STS"],["STS NPM-TPM","172.30.2.10","NPM-TPM","STS"],["STS NPT-DTM","172.30.1.122","NPT-DTM","STS"],["STS NPT-KPS","172.30.1.22","NPT-KPS","STS"],["STS NPT-NCS","172.30.1.34","NPT-NCS","STS"],["STS NPT-NPT","172.30.1.38","NPT-NPT","STS"],["STS NPT-PM5","172.30.1.158","NPT-PM5","STS"],["STS NRT-KCT","172.30.4.94","NRT-KCT","STS"],["STS NRT-NRT","172.30.4.90","NRT-NRT","STS"],["STS NRT-SCI","172.30.4.186","NRT-SCI","STS"],["STS NRT-TSG","172.30.4.158","NRT-TSG","STS"],["STS NSN-NBN","172.30.3.174","NSN-NBN","STS"],["STS NSN-NSN","172.30.3.94","NSN-NSN","STS"],["STS NSN-PNP","172.30.3.106","NSN-PNP","STS"],["STS NSN-TKE","172.31.3.6","NSN-TKE","STS"],["STS NWT-NWT","172.30.4.54","NWT-NWT","STS"],["STS NWT-SKL","172.30.4.26","NWT-SKL","STS"],["STS NWT-TYM","172.30.4.14","NWT-TYM","STS"],["STS NYK-TBN","172.30.5.94","NYK-TBN","STS"],["STS PBI-CHM","172.30.1.138","PBI-CHM","STS"],["STS PBI-PBI","172.30.1.142","PBI-PBI","STS"],["STS PBN-LKO","172.30.3.110","PBN-LKO","STS"],["STS PBN-LSK","172.30.3.74","PBN-LSK","STS"],["STS PBN-NNO","172.30.3.114","PBN-NNO","STS"],["STS PBN-NPI","172.30.3.78","PBN-NPI","STS"],["STS PBN-PBN","172.30.3.118","PBN-PBN","STS"],["STS PBN-WBI","172.31.3.10","PBN-WBI","STS"],["STS PCT-BMN","172.30.3.126","PCT-BMN","STS"],["STS PCT-PCT","172.30.3.2","PCT-PCT","STS"],["STS PCT-TKO","172.30.3.122","PCT-TKO","STS"],["STS PCT-TPH","172.30.3.130","PCT-TPH","STS"],["STS PKN-BSY","172.30.1.126","PKN-BSY","STS"],["STS PKN-HHN","172.30.1.118","PKN-HHN","STS"],["STS PKN-KBR","172.30.1.58","PKN-KBR","STS"],["STS PKN-KLK","172.30.1.114","PKN-KLK","STS"],["STS PKN-PBR","172.30.1.154","PKN-PBR","STS"],["STS PKN-PKN","172.30.1.134","PKN-PKN","STS"],["STS PKN-RTG","172.30.1.130","PKN-RTG","STS"],["STS PKN-TSK","172.30.1.62","PKN-TSK","STS"],["STS PKT-CLG","172.30.4.162","PKT-CLG","STS"],["STS PKT-PKT","172.30.4.74","PKT-PKT","STS"],["STS PKT-PTG","172.30.6.246","PKT-PTG","STS"],["STS PKT-SST","172.30.4.134","PKT-SST","STS"],["STS PKT-TKT","172.30.4.146","PKT-TKT","STS"],["STS PLG-NND","172.30.4.2","PLG-NND","STS"],["STS PLG-PLG","172.30.4.46","PLG-PLG","STS"],["STS PLK-PLK","172.30.3.134","PLK-PLK","STS"],["STS PLK-WCN","172.30.3.230","PLK-WCN","STS"],["STS PNA-PNA","172.30.4.58","PNA-PNA","STS"],["STS PNA-TKP","172.30.4.82","PNA-TKP","STS"],["STS PNA-TMG","172.30.4.78","PNA-TMG","STS"],["STS PRE-DCI","172.30.3.194","PRE-DCI","STS"],["STS PRE-PRE","172.30.3.198","PRE-PRE","STS"],["STS PRE-RKG","172.30.3.202","PRE-RKG","STS"],["STS PRI-3-4","172.30.5.82","","STS"],["STS PRI-KBB","172.30.5.142","PRI-KBB","STS"],["STS PRI-PRI","172.30.5.138","PRI-PRI","STS"],["STS PTE-KL4","172.30.6.106","PTE-KL4","STS"],["STS PTE-PTE","172.30.6.186","PTE-PTE","STS"],["STS PTE-RST-1","172.30.6.34","PTE-RST","STS"],["STS PTE-RST-2","172.30.6.146","PTE-RST","STS"],["STS PTN-KPO","172.30.4.22","PTN-KPO","STS"],["STS PTN-PTN","172.30.4.42","PTN-PTN","STS"],["STS PTN-SBR","172.30.4.138","PTN-SBR","STS"],["STS PYO-PYO","172.30.3.210","PYO-PYO","STS"],["STS RBI-CBG","172.30.1.190","RBI-CBG","STS"],["STS RBI-NPD-1","172.30.1.86","RBI-NPD","STS"],["STS RBI-NPD-2","172.30.1.70","RBI-NPD","STS"],["STS RBI-RBI","172.30.1.18","RBI-RBI","STS"],["STS RBI-SPG","172.30.1.82","RBI-SPG","STS"],["STS RET-RET","172.30.2.50","RET-RET","STS"],["STS RET-SWP","172.30.2.146","RET-SWP","STS"],["STS RYG-BNL","172.30.5.74","RYG-BNL","STS"],["STS RYG-EST","172.30.5.18","RYG-EST","STS"],["STS RYG-KLG","172.30.5.54","RYG-KLG","STS"],["STS RYG-MTP","172.30.5.14","RYG-MTP","STS"],["STS RYG-NPA","172.30.5.190","RYG-NPA","STS"],["STS RYG-NPN","172.30.5.194","RYG-NPN","STS"],["STS RYG-PDG","172.30.5.22","RYG-PDG","STS"],["STS RYG-RYG","172.30.5.50","RYG-RYG","STS"],["STS SBR-SBR","172.30.1.6","SBR-SBR","STS"],["STS SKA-HYI","172.30.4.34","SKA-HYI","STS"],["STS SKA-HYN","172.30.4.182","SKA-HYN","STS"],["STS SKA-KLG","172.30.4.170","SKA-KLG","STS"],["STS SKA-NTW","172.30.4.50","SKA-NTW","STS"],["STS SKA-PDB","172.30.4.178","SKA-PDB","STS"],["STS SKA-SKA","172.30.4.10","SKA-SKA","STS"],["STS SKM-SKM","172.30.1.2","SKM-SKM","STS"],["STS SKN-ECI","172.30.1.94","SKN-ECI","STS"],["STS SKN-SKN","172.30.1.162","SKN-SKN","STS"],["STS SKW-AYT","172.30.5.102","SKW-AYT","STS"],["STS SKW-KCN","172.30.5.110","SKW-KCN","STS"],["STS SKW-SKW","172.30.5.106","SKW-SKW","STS"],["STS SKW-TKW","172.30.5.158","SKW-TKW","STS"],["STS SKW-WNY","172.30.5.78","SKW-WNY","STS"],["STS SNI-BSG","172.30.4.122","SNI-BSG","STS"],["STS SNI-BTK","172.30.4.246","SNI-BTK","STS"],["STS SNI-CKM","172.30.4.30","SNI-CKM","STS"],["STS SNI-SNI","172.30.4.166","SNI-SNI","STS"],["STS SNI-TCG","172.30.4.70","SNI-TCG","STS"],["STS SNI-TKB","172.30.4.62","SNI-TKB","STS"],["STS SNK-PAK","172.30.2.218","SNK-PAK","STS"],["STS SNK-SNK","172.30.2.18","SNK-SNK","STS"],["STS SNK-SWD","172.30.2.22","SNK-SWD","STS"],["STS SPB-SMK","172.30.1.178","SPB-SMK","STS"],["STS SPB-SPB","172.30.1.182","SPB-SPB","STS"],["STS SPB-UTG","172.30.1.78","SPB-UTG","STS"],["STS SPK-BNA","172.30.6.62","SPK-BNA","STS"],["STS SPK-BNA-2","172.30.6.150","SPK-BNA","STS"],["STS SPK-PKS","172.30.6.94","SPK-PKS","STS"],["STS SPK-SDN-1","172.30.6.154","SPK-SDN","STS"],["STS SPK-SDN-2","172.30.6.22","SPK-SDN","STS"],["STS SRI-HBG","172.30.1.202","SRI-HBG","STS"],["STS SRI-HKG","172.30.1.42","SRI-HKG","STS"],["STS SRI-KKI","172.30.1.30","SRI-KKI","STS"],["STS SRI-MLK","172.30.1.10","SRI-MLK","STS"],["STS SRI-SRI","172.30.2.186","SRI-SRI","STS"],["STS SRN-SRN","172.30.2.94","SRN-SRN","STS"],["STS SRN-SRT","172.30.2.98","SRN-SRT","STS"],["STS SRN-TTM","172.30.2.14","SRN-TTM","STS"],["STS SSK-KTL","172.30.2.230","SSK-KTL","STS"],["STS SSK-SSK","172.30.2.170","SSK-SSK","STS"],["STS STI-STI","172.30.3.222","STI-STI","STS"],["STS STI-SWK","172.30.3.70","STI-SWK","STS"],["STS STN-STN","172.30.4.6","STN-STN","STS"],["STS TAK-MST","172.30.3.90","TAK-MST","STS"],["STS TAK-SMN","172.30.3.234","TAK-SMN","STS"],["STS TAK-TAK","172.30.3.6","TAK-TAK","STS"],["STS TRD-TRD","172.30.5.98","TRD-TRD","STS"],["STS TRG-HYT","172.30.4.102","TRG-HYT","STS"],["STS TRG-TRG","172.30.4.114","TRG-TRG","STS"],["STS UBN-DUM","172.30.2.166","UBN-DUM","STS"],["STS UBN-PSH","172.30.2.234","UBN-PSH","STS"],["STS UBN-UBN","172.30.2.222","UBN-UBN","STS"],["STS UBN-WCR","172.30.2.162","UBN-WCR","STS"],["STS UDN-BDG","172.30.2.202","UDN-BDG","STS"],["STS UDN-BLM","172.30.2.118","UDN-BLM","STS"],["STS UDN-UDN-1","172.30.2.106","UDN-UDN","STS"],["STS UDN-UDN-2","172.30.2.190","UDN-UDN","STS"],["STS UTI-UTI","172.30.3.154","UTI-UTI","STS"],["STS UTT-BKN","172.30.3.146","UTT-BKN","STS"],["STS UTT-UTT","172.31.3.2","UTT-UTT","STS"],["STS UTT-WKP","172.30.3.150","UTT-WKP","STS"],["STS YLA-YLA","172.30.4.18","YLA-YLA","STS"],["STS YST-LNT","172.30.2.226","YST-LNT","STS"],["STS YST-YST","172.30.2.154","YST-YST","STS"],["STS BKK-MKS-3","172.30.6.10","BKK-MKS","STS"],["STS CRI-BMI","172.30.3.14","CRI-BMI","STS"],["STS CMI-CKN-1","172.30.3.30","CMI-CKN","STS"],["STS CBI-SRC-2","172.30.5.30","CBI-SRC","STS"],["STS PKT-PTG","172.30.4.38","PKT-PTG","STS"],["STS BKK-BKE-2","172.30.6.38","BKK-BKE","STS"],["STS ThaiPBS1","172.30.6.42","","STS"],["STS CMI-CMI-1","172.30.3.46","CMI-CMI","STS"],["STS ThaiPBS2","172.30.6.46","","STS"],["STS BKK-HMK-3","172.30.6.50","BKK-HMK","STS"],["STS SNI-BTK","172.30.4.66","SNI-BTK","STS"],["STS BKK-HMK-3","172.30.6.90","BKK-HMK","STS"],["STS PKT-PKT-1","172.30.4.130","PKT-PKT","STS"],["STS BKK-RM4-2","172.30.6.130","BKK-RM4","STS"],["STS SKN-SKN-1","172.30.1.146","SKN-SKN","STS"],["STS CBI-PTY-1","172.30.5.146","CBI-PTY","STS"],["STS KBI-KPN-1","172.30.4.150","KBI-KPN","STS"],["STS CPN-LME Con2","172.30.4.154","CPN-LME","STS"],["STS ATG-ATG-1","172.30.1.170","ATG-ATG","STS"],["STS SKA-SKA-1","172.30.4.174","SKA-SKA","STS"],["STS CBI-CBI-2","172.30.5.182","CBI-CBI","STS"],["STS CCO-CCO","172.30.5.186","CCO-CCO","STS"],["STS BKK-LPA-1","172.30.6.194","BKK-LPA","STS"],["STS PBI-PBI Con2","172.30.1.234","PBI-PBI","STS"],["STS BKK-BBR-2","172.30.6.234","BKK-BBR","STS"],["STS PKN-BSY Con2","172.30.1.238","PKN-BSY","STS"],["STS LEI-CKN","172.30.2.242","LEI-CKN","STS"],["STS BKK-LPA-3","172.30.6.242","BKK-LPA","STS"],["STS BKK-CRK-3","172.30.6.250","BKK-CRK","STS"],["STS BKK-ITM-1","172.31.6.2","BKK-ITM","STS"],["STS BKK-PWT-1","172.31.6.34","BKK-PWT","STS"],["TeleAlarm BKW","172.30.4.230","","TeleAlarm"],["TeleAlarm BNN","172.30.4.218","","TeleAlarm"],["TeleAlarm BSY","172.30.1.230","","TeleAlarm"],["TeleAlarm BWA","172.30.4.238","","TeleAlarm"],["TeleAlarm BWA Room 2","172.30.5.198","","TeleAlarm"],["TeleAlarm CHT","172.30.4.226","","TeleAlarm"],["TeleAlarm CHW","172.30.4.126","","TeleAlarm"],["TeleAlarm CPN","172.30.4.202","","TeleAlarm"],["TeleAlarm CYA","172.30.4.214","","TeleAlarm"],["TeleAlarm HHN","172.30.1.218","","TeleAlarm"],["TeleAlarm HYN","172.30.4.142","","TeleAlarm"],["TeleAlarm KBR","172.30.1.222","","TeleAlarm"],["TeleAlarm LME","172.30.4.210","","TeleAlarm"],["TeleAlarm MAR","172.30.4.198","","TeleAlarm"],["TeleAlarm PBI","172.30.1.214","","TeleAlarm"],["TeleAlarm PDB","172.30.4.234","","TeleAlarm"],["TeleAlarm RBI","172.30.1.210","","TeleAlarm"],["TeleAlarm SWE","172.30.4.206","","TeleAlarm"],["TeleAlarm TSG","172.30.4.222","","TeleAlarm"],["TeleAlarm TSK","172.30.1.226","","TeleAlarm"],["TeleAlarm WNR","172.30.1.206","","TeleAlarm"],["CCTV ACR-ACR","172.19.2.86","ACR-ACR","CCTV"],["CCTV ATG-ATG","172.19.4.254","ATG-ATG","CCTV"],["CCTV AYA-AYA","172.19.2.118","AYA-AYA","CCTV"],["CCTV AYA-BPC","172.19.1.78","AYA-BPC","CCTV"],["CCTV AYA-WNI","172.19.3.30","AYA-WNI","CCTV"],["CCTV BKK-BBR","172.19.4.150","BKK-BBR","CCTV"],["CCTV BKK-BKE","172.19.5.10","BKK-BKE","CCTV"],["CCTV BKK-CRK","172.19.1.30","BKK-CRK","CCTV"],["CCTV BKK-ITEL","172.19.5.26","BKK-ITEL","CCTV"],["CCTV BKK-ITM","172.19.4.246","BKK-ITM","CCTV"],["CCTV BKK-KTI","172.19.4.66","BKK-KTI","CCTV"],["CCTV BKK-LKB","172.19.3.150","BKK-LKB","CCTV"],["CCTV BKK-LPA","172.19.1.6","BKK-LPA","CCTV"],["CCTV BKK-MBI","172.19.4.226","BKK-MBI","CCTV"],["CCTV BKK-MKS-1","172.19.3.190","BKK-MKS","CCTV"],["CCTV BKK-MKS-2","172.19.1.2","BKK-MKS","CCTV"],["CCTV BKK-NCN","172.19.4.182","BKK-NCN","CCTV"],["CCTV BKK-ONT","172.19.4.70","BKK-ONT","CCTV"],["CCTV BKK-PBM","172.19.5.2","BKK-PBM","CCTV"],["CCTV BKK-RCD-1","172.19.1.38","BKK-RCD","CCTV"],["CCTV BKK-RCD-2","172.19.1.255","BKK-RCD","CCTV"],["CCTV BKK-RCD-3","172.19.4.10","BKK-RCD","CCTV"],["CCTV BKK-RIT","172.19.2.250","BKK-RIT","CCTV"],["CCTV BKK-RM2","172.19.4.158","BKK-RM2","CCTV"],["CCTV BKK-RM4-1","172.19.1.18","BKK-RM4","CCTV"],["CCTV BKK-RM9","172.19.4.186","BKK-RM9","CCTV"],["CCTV BKK-SLG","172.19.5.34","BKK-SLG","CCTV"],["CCTV BKK-SLM","172.19.4.206","BKK-SLM","CCTV"],["CCTV BKK-SSW","172.19.1.34","BKK-SSW","CCTV"],["CCTV BKK-STD","172.19.3.158","BKK-STD","CCTV"],["CCTV BKK-TPN","172.19.4.34","BKK-TPN","CCTV"],["CCTV BKK-TRN","172.19.3.34","BKK-TRN","CCTV"],["CCTV BRM-BRM","172.19.1.98","BRM-BRM","CCTV"],["CCTV BRM-KKD","172.19.4.78","BRM-KKD","CCTV"],["CCTV BRM-STK","172.19.4.14","BRM-STK","CCTV"],["CCTV CBI-BLG","172.19.4.42","CBI-BLG","CCTV"],["CCTV CBI-CBI","172.19.1.170","CBI-CBI","CCTV"],["CCTV CBI-HKP","172.19.4.22","CBI-HKP","CCTV"],["CCTV CBI-NPR","172.19.3.146","CBI-NPR","CCTV"],["CCTV CBI-PTL","172.19.4.162","CBI-PTL","CCTV"],["CCTV CBI-PTY","172.19.1.174","CBI-PTY","CCTV"],["CCTV CCO-BPK","172.19.5.78","CCO-BPK","CCTV"],["CCTV CCO-BWA","172.19.1.162","CCO-BWA","CCTV"],["CCTV CCO-BWA Room 2","172.19.5.182","CCO-BWA","CCTV"],["CCTV CCO-CCO","172.19.1.166","CCO-CCO","CCTV"],["CCTV CCO-DTG","172.19.4.94","CCO-DTG","CCTV"],["CCTV CCO-SCK","172.19.2.142","CCO-SCK","CCTV"],["CCTV CMI-CKN","172.19.3.74","CMI-CKN","CCTV"],["CCTV CMI-CMI","172.19.1.158","CMI-CMI","CCTV"],["CCTV CMI-CTG","172.19.4.210","CMI-CTG","CCTV"],["CCTV CMI-DSK","172.19.3.114","CMI-DSK","CCTV"],["CCTV CMI-MRM","172.19.4.74","CMI-MRM","CCTV"],["CCTV CMI-SPT","172.19.2.34","CMI-SPT","CCTV"],["CCTV CMI-SRP","172.19.4.166","CMI-SRP","CCTV"],["CCTV CNT-CNT","172.19.2.138","CNT-CNT","CCTV"],["CCTV CPM-CPM","172.19.3.6","CPM-CPM","CCTV"],["CCTV CPN-CPN","172.19.4.194","CPN-CPN","CCTV"],["CCTV CPN-LME-1","172.19.2.18","CPN-LME","CCTV"],["CCTV CPN-LME-2","172.19.5.50","CPN-LME","CCTV"],["CCTV CPN-LSN","172.19.2.14","CPN-LSN","CCTV"],["CCTV CPN-MAR","172.19.3.206","CPN-MAR","CCTV"],["CCTV CPN-SWE","172.19.3.210","CPN-SWE","CCTV"],["CCTV CPN-TSE","172.19.2.6","CPN-TSE","CCTV"],["CCTV CRI-CRI","172.19.3.106","CRI-CRI","CCTV"],["CCTV CRI-MSI","172.19.4.126","CRI-MSI","CCTV"],["CCTV CRI-SSM","172.19.4.110","CRI-SSM","CCTV"],["CCTV CRI-WPP","172.19.3.110","CRI-WPP","CCTV"],["CCTV CTI-CTI","172.19.1.182","CTI-CTI","CCTV"],["CCTV CTI-SDO","172.19.1.206","CTI-SDO","CCTV"],["CCTV KBI-KBI","172.19.2.78","KBI-KBI","CCTV"],["CCTV KCB-KCB","172.19.1.222","KCB-KCB","CCTV"],["CCTV KCB-TAM","172.19.4.62","KCB-TAM","CCTV"],["CCTV KKN-BPD-1","172.19.3.154","KKN-BPD","CCTV"],["CCTV KKN-BPD-2","172.19.4.198","KKN-BPD","CCTV"],["CCTV KKN-CPR","172.19.3.70","KKN-CPR","CCTV"],["CCTV KKN-KKN","172.19.3.254","KKN-KKN","CCTV"],["CCTV KKN-KSK","172.19.1.58","KKN-KSK","CCTV"],["CCTV KKN-MPN","172.19.1.54","KKN-MPN","CCTV"],["CCTV KPT-KPT","172.19.2.130","KPT-KPT","CCTV"],["CCTV KPT-SLB","172.19.2.134","KPT-SLB","CCTV"],["CCTV KSN-KNR","172.19.4.214","KSN-KNR","CCTV"],["CCTV KSN-KSN","172.19.4.242","KSN-KSN","CCTV"],["CCTV LPG-HVG","172.19.3.22","LPG-HVG","CCTV"],["CCTV LPG-LPG","172.19.1.150","LPG-LPG","CCTV"],["CCTV LPG-MMO","172.19.1.146","LPG-MMO","CCTV"],["CCTV LPG-NGO","172.19.3.102","LPG-NGO","CCTV"],["CCTV LPG-THN","172.19.2.122","LPG-THN","CCTV"],["CCTV LPN-LPN","172.19.1.154","LPN-LPN","CCTV"],["CCTV LRI-LRI","172.19.4.142","LRI-LRI","CCTV"],["CCTV LRI-STA","172.19.4.218","LRI-STA","CCTV"],["CCTV MDH-MDH","172.19.3.14","MDH-MDH","CCTV"],["CCTV MKM-MKM","172.19.2.94","MKM-MKM","CCTV"],["CCTV NAN-NAN","172.19.3.126","NAN-NAN","CCTV"],["CCTV NBI-BBT-1","172.19.4.26","NBI-BBT","CCTV"],["CCTV NBI-BBT-2","172.19.4.190","NBI-BBT","CCTV"],["CCTV NBI-CWN","172.19.1.22","NBI-CWN","CCTV"],["CCTV NBI-KER","172.19.3.134","NBI-KER","CCTV"],["CCTV NBI-KPP","172.19.2.114","NBI-KPP","CCTV"],["CCTV NBI-SMK","172.19.4.146","NBI-SMK","CCTV"],["CCTV NKI-NKI","172.19.1.62","NKI-NKI","CCTV"],["CCTV NMA-BYI","172.19.1.46","NMA-BYI","CCTV"],["CCTV NMA-HTL","172.19.1.94","NMA-HTL","CCTV"],["CCTV NMA-JHO","172.19.3.186","NMA-JHO","CCTV"],["CCTV NMA-KNP","172.19.5.166","NMA-KNP","CCTV"],["CCTV NMA-NMA","172.19.3.10","NMA-NMA","CCTV"],["CCTV NMA-PCG","172.19.2.198","NMA-PCG","CCTV"],["CCTV NMA-SNN","172.19.3.58","NMA-SNN","CCTV"],["CCTV NMA-TCR","172.19.1.42","NMA-TCR","CCTV"],["CCTV NPM-NPM","172.19.3.66","NPM-NPM","CCTV"],["CCTV NPM-TPM","172.19.3.26","NPM-TPM","CCTV"],["CCTV NPT-WNR","172.19.4.250","NPT-WNR","CCTV"],["CCTV NRT-CHT","172.19.4.174","NRT-CHT","CCTV"],["CCTV NRT-CHW","172.19.4.170","NRT-CHW","CCTV"],["CCTV NRT-KCT","172.19.2.58","NRT-KCT","CCTV"],["CCTV NRT-NRT","172.19.2.62","NRT-NRT","CCTV"],["CCTV NRT-TSG","172.19.2.46","NRT-TSG","CCTV"],["CCTV NSN-CSN","172.19.1.90","NSN-CSN","CCTV"],["CCTV NSN-NSN","172.19.2.254","NSN-NSN","CCTV"],["CCTV NSN-PNP","172.19.1.118","NSN-PNP","CCTV"],["CCTV NWT-NWT","172.19.4.82","NWT-NWT","CCTV"],["CCTV CCTVNWT-SKL","172.19.3.178","VNWT-SKL","CCTV"],["CCTV NWT-TYM","172.19.3.170","NWT-TYM","CCTV"],["CCTV NYK-TBN","172.19.4.98","NYK-TBN","CCTV"],["CCTV PBI-CHM","172.19.1.234","PBI-CHM","CCTV"],["CCTV PBI-HCS No Sevice","172.19.5.98","PBI-HCS","CCTV"],["CCTV PBI-PBI-1","172.19.1.230","PBI-PBI","CCTV"],["CCTV PBI-PBI-2","172.19.5.42","PBI-PBI","CCTV"],["CCTV PBI-WMN","172.19.5.70","PBI-WMN","CCTV"],["CCTV PBN-LKO","172.19.3.78","PBN-LKO","CCTV"],["CCTV PBN-LSK","172.19.4.58","PBN-LSK","CCTV"],["CCTV PBN-NNO","172.19.3.162","PBN-NNO","CCTV"],["CCTV PBN-NPI","172.19.4.54","PBN-NPI","CCTV"],["CCTV PBN-PBN","172.19.2.90","PBN-PBN","CCTV"],["CCTV PCT-BMN","172.19.1.122","PCT-BMN","CCTV"],["CCTV PCT-TKO","172.19.3.54","PCT-TKO","CCTV"],["CCTV PCT-TPH","172.19.4.46","PCT-TPH","CCTV"],["CCTV PKN-BSY-1","172.19.2.2","PKN-BSY","CCTV"],["CCTV PKN-BSY-2","172.19.5.46","PKN-BSY","CCTV"],["CCTV PKN-HHN","172.19.4.102","PKN-HHN","CCTV"],["CCTV PKN-KBR","172.19.3.198","PKN-KBR","CCTV"],["CCTV PKN-KLK","172.19.2.110","PKN-KLK","CCTV"],["CCTV PKN-PBR","172.19.1.238","PKN-PBR","CCTV"],["CCTV PKN-PKN","172.19.1.246","PKN-PKN","CCTV"],["CCTV PKN-RTG","172.19.2.106","PKN-RTG","CCTV"],["CCTV PKN-TSK","172.19.3.202","PKN-TSK","CCTV"],["CCTV PKT-PKT","172.19.2.38","PKT-PKT","CCTV"],["CCTV PKT-SST","172.19.4.134","PKT-SST","CCTV"],["CCTV PKT-TKT","172.19.4.138","PKT-TKT","CCTV"],["CCTV PLG-BKW","172.19.3.234","PLG-BKW","CCTV"],["CCTV PLG-NND","172.19.2.206","PLG-NND","CCTV"],["CCTV PLG-PLG","172.19.2.66","PLG-PLG","CCTV"],["CCTV PLK-PLK","172.19.1.130","PLK-PLK","CCTV"],["CCTV PLK-WCN","172.19.3.138","PLK-WCN","CCTV"],["CCTV PNA-PNA","172.19.4.90","PNA-PNA","CCTV"],["CCTV PNA-TMG","172.19.2.246","PNA-TMG","CCTV"],["CCTV PRE-DCI","172.19.1.142","PRE-DCI","CCTV"],["CCTV PRE-PRE","172.19.3.182","PRE-PRE","CCTV"],["CCTV PRE-RKG","172.19.3.98","PRE-RKG","CCTV"],["CCTV PRI-KBB-1","172.19.1.190","PRI-KBB","CCTV"],["CCTV PRI-KBB-2","172.19.1.194","PRI-KBB","CCTV"],["CCTV PRI-KBB-3","172.19.1.198","PRI-KBB","CCTV"],["CCTV PRI-PRI","172.19.1.186","PRI-PRI","CCTV"],["CCTV PTE-KL4","172.19.1.14","PTE-KL4","CCTV"],["CCTV PTE-PTE","172.19.4.202","PTE-PTE","CCTV"],["CCTV PTE-RST","172.19.3.118","PTE-RST","CCTV"],["CCTV PTN-KPO","172.19.3.166","PTN-KPO","CCTV"],["CCTV PTN-PTN","172.19.4.154","PTN-PTN","CCTV"],["CCTV PYO-PYO","172.19.3.94","PYO-PYO","CCTV"],["CCTV RBI-NPD-1","172.19.1.214","RBI-NPD","CCTV"],["CCTV RBI-NPD-2","172.19.4.118","RBI-NPD","CCTV"],["CCTV RBI-RBI","172.19.1.218","RBI-RBI","CCTV"],["CCTV RET-RET","172.19.2.82","RET-RET","CCTV"],["CCTV RYG-KLG","172.19.1.210","RYG-KLG","CCTV"],["CCTV RYG-MTP","172.19.1.178","RYG-MTP","CCTV"],["CCTV RYG-RYG","172.19.3.142","RYG-RYG","CCTV"],["CCTV SKA-HYI-1","172.19.2.70","SKA-HYI","CCTV"],["CCTV SKA-HYN-1","172.19.4.222","SKA-HYN","CCTV"],["CCTV SKA-HYN-2","172.19.5.158","SKA-HYN","CCTV"],["CCTV SKA-HYN-3","172.19.5.162","SKA-HYN","CCTV"],["CCTV SKA-HYN-4","172.19.5.154","SKA-HYN","CCTV"],["CCTV SKA-KGE","172.19.3.238","SKA-KGE","CCTV"],["CCTV SKA-PDB","172.19.2.146","SKA-PDB","CCTV"],["CCTV SKA-PDB No Sevice","172.19.5.150","SKA-PDB","CCTV"],["CCTV SKA-RTP No Sevice","172.19.5.146","SKA-RTP","CCTV"],["CCTV SKM-APW No Sevice","172.19.5.94","SKM-APW","CCTV"],["CCTV SKM-SKM","172.19.1.226","SKM-SKM","CCTV"],["CCTV SKN-SKN","172.19.3.90","SKN-SKN","CCTV"],["CCTV SKW-AYT-2","172.19.5.22","SKW-AYT","CCTV"],["CCTV SKW-KCN","172.19.1.202","SKW-KCN","CCTV"],["CCTV SNI-BNN","172.19.3.218","SNI-BNN","CCTV"],["CCTV SNI-BSG","172.19.2.42","SNI-BSG","CCTV"],["CCTV SNI-BTK","172.19.2.30","SNI-BTK","CCTV"],["CCTV SNI-CYA","172.19.3.214","SNI-CYA","CCTV"],["CCTV SNI-SNI","172.19.2.22","SNI-SNI","CCTV"],["CCTV SNI-TCG","172.19.2.26","SNI-TCG","CCTV"],["CCTV SNK-SNK","172.19.3.62","SNK-SNK","CCTV"],["CCTV SNK-SWD","172.19.3.18","SNK-SWD","CCTV"],["CCTV SPB-SPB","172.19.1.82","SPB-SPB","CCTV"],["CCTV SPK-BNA","172.19.3.86","SPK-BNA","CCTV"],["CCTV SPK-PKS-1","172.19.5.30","SPK-PKS","CCTV"],["CCTV SPK-PKS-2","172.19.4.86","SPK-PKS","CCTV"],["CCTV SPK-SDN","172.19.4.6","SPK-SDN","CCTV"],["CCTV SRI-KKI","172.19.1.74","SRI-KKI","CCTV"],["CCTV SRI-SRI","172.19.1.242","SRI-SRI","CCTV"],["CCTV SRN-SRN","172.19.1.106","SRN-SRN","CCTV"],["CCTV SSK-SSK","172.19.1.110","SSK-SSK","CCTV"],["CCTV STI-STI","172.19.3.82","STI-STI","CCTV"],["CCTV STI-SWK","172.19.4.50","STI-SWK","CCTV"],["CCTV STN-STN","172.19.4.18","STN-STN","CCTV"],["CCTV TAK-MST","172.19.4.30","TAK-MST","CCTV"],["CCTV TAK-SMN","172.19.4.130","TAK-SMN","CCTV"],["CCTV TAK-TAK","172.19.2.126","TAK-TAK","CCTV"],["CCTV TRD-TRD","172.19.5.38","TRD-TRD","CCTV"],["CCTV TRG-HYT","172.19.2.50","TRG-HYT","CCTV"],["CCTV TRG-TRG","172.19.2.54","TRG-TRG","CCTV"],["CCTV UBN-UBN","172.19.3.122","UBN-UBN","CCTV"],["CCTV UBN-WCR","172.19.1.114","UBN-WCR","CCTV"],["CCTV UDN-BLM","172.19.4.2","UDN-BLM","CCTV"],["CCTV UDN-UDN","172.19.1.66","UDN-UDN","CCTV"],["CCTV UTT-BKN","172.19.1.134","UTT-BKN","CCTV"],["CCTV UTT-WKP","172.19.1.138","UTT-WKP","CCTV"],["CCTV YLA-YLA","172.19.3.174","YLA-YLA","CCTV"],["CCTV SRN-SRN","172.19.1.102","SRN-SRN","CCTV"],["CCTV PCT-PCT","172.19.1.126","PCT-PCT","CCTV"],["CCTV LRI-LRI","172.19.1.86","LRI-LRI","CCTV"],["CCTV PTE-KLL","172.19.3.194","PTE-KLL","CCTV"],["CCTV SRI-SRI","172.19.3.2","SRI-SRI","CCTV"],["CCTV SKA-KNG","172.19.3.230","SKA-KNG","CCTV"],["CCTV KSN-KSN","172.19.4.234","KSN-KSN","CCTV"],["CCTV PKN-TTI","172.19.5.102","PKN-TTI","CCTV"],["CCTV PKN-TBR","172.19.5.106","PKN-TBR","CCTV"],["CCTV CPN-PTO","172.19.5.118","CPN-PTO","CCTV"],["CCTV CPN-NPO","172.19.5.122","CPN-NPO","CCTV"],["CCTV SNI-NBK","172.19.5.126","SNI-NBK","CCTV"],["CCTV SNI-BBL","172.19.5.130","SNI-BBL","CCTV"],["CCTV SNI-KCD","172.19.5.134","SNI-KCD","CCTV"],["CCTV NRT-SCN","172.19.5.138","NRT-SCN","CCTV"],["CCTV CBI-SRC","172.19.5.14","CBI-SRC","CCTV"],["CCTV PLG-NTM","172.19.5.142","PLG-NTM","CCTV"],["CCTV BRM-KKD","172.19.5.170","BRM-KKD","CCTV"],["CCTV AYA-WNI","172.19.5.174","AYA-WNI","CCTV"],["CCTV PKN-TPD","172.19.5.194","PKN-TPD","CCTV"],["CCTV PKN-DLH","172.19.5.198","PKN-DLH","CCTV"],["CCTV CBI-PNM","172.19.5.54","CBI-PNM","CCTV"],["CCTV KBI-ALK","172.19.5.58","KBI-ALK","CCTV"],["CCTV KBI-KPN","172.19.5.62","KBI-KPN","CCTV"],["CCTV CBI-SRC","172.19.5.66","CBI-SRC","CCTV"],["CCTV PKN-KLK Room2","172.19.5.74","PKN-KLK","CCTV"],["CCTV SNI-TCN","172.19.5.82","SNI-TCN","CCTV"],["CCTV BKK-RIT","172.19.5.86","BKK-RIT","CCTV"],["CCTV BKK-BKE","172.19.5.90","BKK-BKE","CCTV"],["INV CCO-BPK","172.30.5.86","CCO-BPK","Inverter"],["INV CPN-LME","172.30.4.242","CPN-LME","Inverter"],["INV KBI-KPN","172.30.4.98","KBI-KPN","Inverter"],["INV PBI-HCS No Sevice","172.30.1.246","PBI-HCS","Inverter"],["INV PBI-WMN","172.30.1.74","PBI-WMN","Inverter"],["INV SKA-PDB No Sevice","172.31.1.26","SKA-PDB","Inverter"],["INV SKA-RTP No Sevice","172.31.1.22","SKA-RTP","Inverter"],["INV SKM-APW No Sevice","172.30.1.242","SKM-APW","Inverter"],["INV PKN-KLK Room2","172.31.1.10","PKN-KLK","Inverter"],["INV CBI-SRC","172.30.5.114","CBI-SRC","Inverter"],["INV PKN-TTI","172.30.1.250","PKN-TTI","Inverter"],["INV CPN-PTO","172.30.4.250","CPN-PTO","Inverter"],["INV PKN-TBR","172.30.1.254","PKN-TBR","Inverter"],["INV CPN-NPO","172.30.4.254","CPN-NPO","Inverter"],["INV PKN-TPD","172.31.1.2","PKN-TPD","Inverter"],["INV SNI-NBK","172.31.4.2","SNI-NBK","Inverter"],["INV PKN-DLH","172.31.1.6","PKN-DLH","Inverter"],["INV SNI-BBL","172.31.4.6","SNI-BBL","Inverter"],["INV SNI-KCD","172.31.4.10","SNI-KCD","Inverter"],["INV NRT-SCN","172.31.4.14","NRT-SCN","Inverter"],["INV PLG-NTM","172.31.4.18","PLG-NTM","Inverter"],["INV SKA-RTP","172.31.4.22","SKA-RTP","Inverter"],["INV SKA-PDB Con2","172.31.4.26","SKA-PDB","Inverter"],["INV BKK-RIT","172.31.6.42","BKK-RIT","Inverter"],["INV BKK-BKE","172.31.6.46","BKK-BKE","Inverter"]];
  const devices = RAW.map(([name, ip, site, group], i) => ({
    id: i, name, ip, site, group,
    state: 'unknown', ms: null, downSince: null, stateSince: null,
  }));
  let nextId = devices.length;

  const GROUP_LABEL = { Rectifier: 'REC Alarm', STS: 'STS Alarm', Inverter: 'INV Alarm', TeleAlarm: 'Tele Alarm', CCTV: 'CCTV Alarm', Other: 'Other Alarm' };
  const GROUP_ORDER = ['Rectifier', 'STS', 'Inverter', 'TeleAlarm', 'CCTV', 'Other'];

  const events = []; // {t, name, ip, group, from, to, prevDurMs}
  let scanning = false, stopRequested = false;
  let nextSweepAt = null, autoTimer = null, lastScanAt = null, lastScanMs = null;
  const history = [];

  const el = (id) => document.getElementById(id);

  // ============ LOGIN ============
  el('loginNodeCount').textContent = devices.length.toLocaleString();
  el('loginGroupCount').textContent = [...new Set(devices.map((d) => d.group))].length;

  function tryLogin() {
    const u = el('loginUser').value.trim();
    const p = el('loginPass').value;
    const found = users.find((x) => x.username === u && x.password === p);
    if (found) {
      currentUser = found;
      el('loginScreen').classList.add('hidden');
      el('app').classList.add('authed');
      el('loginErr').textContent = '';
      applyPermissions();
      renderUsers();
      if (!lastScanAt && !scanning) setTimeout(runScan, 600);
    } else {
      el('loginErr').textContent = 'Username หรือ Password ไม่ถูกต้อง';
    }
  }

  function applyPermissions() {
    if (!currentUser) return;
    const canEdit = !!currentUser.canEdit;
    el('whoAmI').textContent = `${currentUser.first} ${currentUser.last} (${currentUser.username})${currentUser.admin ? ' · Admin' : canEdit ? ' · แก้ไขได้' : ' · ดูอย่างเดียว'}`;
    el('addBtn').style.display = canEdit ? '' : 'none';
    el('usersNavLink').style.display = currentUser.admin ? '' : 'none';
    showPage('overview');
    renderTable(); // redraw so edit/delete buttons appear/disappear
  }
  el('loginBtn').addEventListener('click', tryLogin);
  el('loginPass').addEventListener('keydown', (e) => { if (e.key === 'Enter') tryLogin(); });
  el('loginUser').addEventListener('keydown', (e) => { if (e.key === 'Enter') el('loginPass').focus(); });
  el('eyeBtn').addEventListener('click', () => {
    const p = el('loginPass');
    p.type = p.type === 'password' ? 'text' : 'password';
  });
  el('logoutBtn').addEventListener('click', () => {
    currentUser = null;
    el('app').classList.remove('authed');
    el('loginScreen').classList.remove('hidden');
    el('loginPass').value = '';
  });

  // ============ THEME TOGGLE ============
  el('themeBtn').addEventListener('click', () => {
    const root = document.documentElement;
    const light = root.getAttribute('data-theme') === 'light';
    root.setAttribute('data-theme', light ? 'dark' : 'light');
    el('themeBtn').textContent = light ? '🌙' : '☀️';
  });

  // ============ PROBE / SWEEP ============
  async function probe(d) {
    const ctrl = new AbortController();
    const timer = setTimeout(() => ctrl.abort(), PROBE_TIMEOUT_MS);
    const started = performance.now();
    try {
      await fetch(`http://${d.ip}/`, { mode: 'no-cors', cache: 'no-store', signal: ctrl.signal });
      applyResult(d, true, Math.round(performance.now() - started));
    } catch (e) {
      applyResult(d, false, null);
    } finally { clearTimeout(timer); }
  }

  function applyResult(d, ok, ms) {
    const was = d.state;
    const newState = ok ? 'up' : 'down';
    d.ms = ms;
    if (was !== newState) {
      const now = new Date();
      const prevDurMs = d.stateSince ? now - d.stateSince : null;
      // บันทึกทุก transition ที่มีความหมาย (unknown→up ของรอบแรกไม่บันทึก เพื่อไม่ให้ log ท่วม)
      if (!(was === 'unknown' && newState === 'up')) {
        events.unshift({ t: now, name: d.name, ip: d.ip, group: d.group, from: was, to: newState, prevDurMs });
        if (events.length > MAX_EVENTS) events.pop();
      }
      if (newState === 'down') {
        d.downSince = now;
        if (was === 'up') showToast(`🔴 ${d.name} (${d.ip}) Down!`, true);
      } else {
        if (was === 'down' && d.downSince) showToast(`✅ ${d.name} กลับมา Online (down ไป ${fmtDuration(now - d.downSince)})`);
        d.downSince = null;
      }
      d.state = newState;
      d.stateSince = now;
    }
  }

  async function runScan() {
    if (scanning) return;
    scanning = true; stopRequested = false;
    clearTimeout(autoTimer);
    nextSweepAt = new Date(Date.now() + SCAN_INTERVAL_MS);
    setPollUI(true);
    const started = Date.now();
    let done = 0, next = 0;
    async function worker() {
      while (!stopRequested) {
        const i = next++;
        if (i >= devices.length) return;
        await probe(devices[i]);
        done++;
        el('progressFill').style.width = `${(done / devices.length) * 100}%`;
        el('progressLabel').textContent = `${done}/${devices.length}`;
      }
    }
    await Promise.all(Array.from({ length: Math.min(CONCURRENCY, devices.length) }, worker));
    scanning = false;
    lastScanAt = new Date();
    lastScanMs = Date.now() - started;
    history.push({ t: lastScanAt, down: devices.filter((d) => d.state === 'down').length });
    if (history.length > 40) history.shift();
    el('progressFill').style.width = '0%';
    el('progressLabel').textContent = '';
    setPollUI(false);
    render();
    if (!stopRequested) {
      const wait = Math.max(3000, SCAN_INTERVAL_MS - lastScanMs);
      nextSweepAt = new Date(Date.now() + wait);
      autoTimer = setTimeout(runScan, wait);
    } else nextSweepAt = null;
  }

  function setPollUI(active) {
    el('pollState').textContent = active ? 'sweeping...' : 'idle';
    el('pollState').className = active ? 'run' : '';
    el('scanNowBtn').disabled = active;
    el('stopBtn').style.display = active ? '' : 'none';
    el('pillDot').style.background = active ? 'var(--accent)' : 'var(--up)';
    el('pillText').textContent = active ? 'SWEEPING' : 'MONITORING';
  }
  el('stopBtn').addEventListener('click', () => { stopRequested = true; });
  el('scanNowBtn').addEventListener('click', runScan);

  // ============ FORMAT ============
  function fmtDuration(ms) {
    let s = Math.floor(ms / 1000);
    const d = Math.floor(s / 86400); s -= d * 86400;
    const h = Math.floor(s / 3600); s -= h * 3600;
    const m = Math.floor(s / 60); s -= m * 60;
    const parts = [];
    if (d) parts.push(d + 'd');
    if (h || d) parts.push(h + 'h');
    if (m || h || d) parts.push(m + 'm');
    parts.push(s + 's');
    return parts.slice(0, 3).join(' ');
  }
  function fmtClock(dt) { return dt ? dt.toLocaleTimeString('th-TH', { hour: '2-digit', minute: '2-digit', second: '2-digit' }) : '—'; }
  function fmtFull(dt) { return dt.toLocaleDateString('th-TH', { day: '2-digit', month: '2-digit' }) + ' ' + fmtClock(dt); }
  function escapeHtml(s) { return String(s).replace(/[&<>"']/g, (c) => ({ '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;' }[c])); }

  function donutSVG(size, segments, centerText, centerSub) {
    const r = size / 2 - 8, cx = size / 2, cy = size / 2, C = 2 * Math.PI * r;
    const total = segments.reduce((a, s) => a + s.v, 0) || 1;
    let offset = 0, rings = '';
    for (const s of segments) {
      const len = (s.v / total) * C;
      rings += `<circle cx="${cx}" cy="${cy}" r="${r}" fill="none" stroke="${s.c}" stroke-width="11" stroke-dasharray="${len} ${C - len}" stroke-dashoffset="${-offset}" transform="rotate(-90 ${cx} ${cy})" opacity="${s.o || 1}"/>`;
      offset += len;
    }
    return rings + `<text x="${cx}" y="${cy - (centerSub ? 2 : -4)}" text-anchor="middle" fill="var(--text-primary)" font-family="var(--font-mono)" font-size="${size > 100 ? 22 : 15}" font-weight="600">${centerText}</text>` +
      (centerSub ? `<text x="${cx}" y="${cy + 16}" text-anchor="middle" fill="var(--text-dim)" font-size="10">${centerSub}</text>` : '');
  }
  function renderSparkline() {
    const svg = el('sparkline');
    if (history.length < 2) { svg.innerHTML = ''; return; }
    const max = Math.max(...history.map((h) => h.down), 1);
    const pts = history.map((h, i) => `${((i / (history.length - 1)) * 200).toFixed(1)},${(30 - (h.down / max) * 26).toFixed(1)}`).join(' ');
    svg.innerHTML = `<polyline points="${pts}" fill="none" stroke="var(--down)" stroke-width="1.6" opacity="0.9"/>`;
  }

  // ============ RENDER ============
  let statusFilter = '', groupFilter = '', searchTerm = '';

  function render() {
    let up = 0, down = 0, unknown = 0;
    for (const d of devices) {
      if (d.state === 'up') up++;
      else if (d.state === 'down') down++;
      else unknown++;
    }
    el('statTotal').textContent = devices.length.toLocaleString();
    el('statUp').innerHTML = `${up.toLocaleString()}<span>Up</span>`;
    el('statDown').innerHTML = `${down.toLocaleString()}<span>Down</span>`;
    el('statUnknown').innerHTML = `${unknown.toLocaleString()}<span>Unchecked</span>`;
    el('lastScan').textContent = fmtClock(lastScanAt);
    el('scanDuration').textContent = lastScanMs ? `(${(lastScanMs / 1000).toFixed(0)}s)` : '';
    el('dlDown').textContent = down; el('dlUp').textContent = up; el('dlUnk').textContent = unknown;

    const checked = up + down;
    const avail = checked ? (up / checked) * 100 : null;
    el('statAvail').textContent = avail != null ? avail.toFixed(1) + '%' : '—';
    const word = el('netWord');
    if (avail == null) { word.textContent = '—'; word.className = 'word'; el('netDesc').textContent = 'รอผล sweep แรก'; }
    else if (avail >= 98) { word.textContent = 'Healthy'; word.className = 'word healthy'; el('netDesc').textContent = 'All systems operational'; }
    else if (avail >= 90) { word.textContent = 'Degraded'; word.className = 'word degraded'; el('netDesc').textContent = `${down} nodes down — ควรตรวจสอบ`; }
    else { word.textContent = 'Critical'; word.className = 'word critical'; el('netDesc').textContent = `${down} nodes down — ต้องตรวจสอบด่วน`; }
    renderSparkline();

    el('alertDonut').innerHTML = donutSVG(86, [
      { v: down, c: 'var(--down)' }, { v: up, c: 'var(--up)' }, { v: unknown, c: 'var(--warn)', o: 0.45 },
    ], down.toLocaleString(), 'down');
    el('healthDonut').innerHTML = donutSVG(150, [
      { v: up, c: 'var(--up)' }, { v: down, c: 'var(--down)' }, { v: unknown, c: 'var(--warn)', o: 0.4 },
    ], avail != null ? avail.toFixed(1) + '%' : '—', 'availability');

    const groups = {};
    for (const d of devices) {
      if (!groups[d.group]) groups[d.group] = { up: 0, down: 0, unknown: 0, total: 0 };
      const g = groups[d.group];
      g.total++;
      if (d.state === 'up') g.up++;
      else if (d.state === 'down') g.down++;
      else g.unknown++;
    }
    const names = Object.keys(groups);
    el('statGroups').textContent = names.length;
    const top = [...names].sort((a, b) => groups[b].total - groups[a].total)[0];
    el('statGroupTop').textContent = top ? `มากสุด: ${top} (${groups[top].total})` : '';
    el('reportBadge').textContent = `${names.length} ประเภท · ${devices.length.toLocaleString()} nodes`;
    el('eqReport').innerHTML = Object.entries(groups).sort((a, b) => b[1].total - a[1].total).map(([name, g]) => {
      const pu = (g.up / g.total) * 100, pd = (g.down / g.total) * 100, pk = (g.unknown / g.total) * 100;
      return `<div class="eq-row">
        <div class="eq-name">${escapeHtml(name)}</div>
        <div class="eq-bar"><div class="seg-up" style="width:${pu}%"></div><div class="seg-down" style="width:${pd}%"></div><div class="seg-unknown" style="width:${pk}%"></div></div>
        <div class="eq-stats"><span class="u">▲ ${g.up}</span> · <span class="d">▼ ${g.down}</span> · ${g.total} total</div>
      </div>`;
    }).join('');

    renderAlarmPanels();
    renderEventLog();
    renderTable();
  }

  // ---- Zabbix-style: one alarm panel per equipment group ----
  function renderAlarmPanels() {
    const container = el('alarms');
    const downs = devices.filter((d) => d.state === 'down' && d.downSince);
    el('navAlarmPill').textContent = downs.length.toLocaleString();
    el('navAlarmPill').classList.toggle('zero', downs.length === 0);

    const presentGroups = GROUP_ORDER.filter((g) => devices.some((d) => d.group === g));
    for (const g of [...new Set(devices.map((d) => d.group))]) {
      if (!presentGroups.includes(g)) presentGroups.push(g);
    }

    container.innerHTML = presentGroups.map((g) => {
      const gDowns = downs.filter((d) => d.group === g).sort((a, b) => b.downSince - a.downSince);
      const rows = gDowns.slice(0, 100).map((d) => `<tr>
        <td class="t">${fmtClock(d.downSince)}</td>
        <td>${escapeHtml(d.name)}</td>
        <td><span class="problem-tag">is ${d.ip} - Down</span></td>
        <td class="dur" data-since="${d.downSince.getTime()}">${fmtDuration(Date.now() - d.downSince.getTime())}</td>
        <td><button class="open-btn" onclick="window.open('http://${d.ip}/', '_blank')">เปิด ↗</button></td>
      </tr>`).join('');
      return `<div class="panel">
        <h2>${GROUP_LABEL[g] || g + ' Alarm'} <span class="count-pill ${gDowns.length ? '' : 'zero'}">${gDowns.length}</span></h2>
        <div class="alarm-scroll">
          ${gDowns.length
            ? `<table><thead><tr><th>Time</th><th>Node</th><th>Problem · Severity</th><th>Duration</th><th></th></tr></thead><tbody>${rows}</tbody></table>`
            : `<div class="alarm-empty">No data found.</div>`}
        </div>
      </div>`;
    }).join('');
  }

  // ---- Event log ----
  let evSearchTerm = '';
  function renderEventLog() {
    const term = evSearchTerm.trim().toLowerCase();
    const filtered = term
      ? events.filter((e) => `${e.name} ${e.ip} ${e.group}`.toLowerCase().includes(term))
      : events;
    el('evBadge').textContent = term
      ? `พบ ${filtered.length.toLocaleString()} จาก ${events.length.toLocaleString()} events`
      : `${events.length.toLocaleString()} events (แสดง 200 ล่าสุด)`;
    el('eventEmpty').style.display = filtered.length ? 'none' : 'block';
    el('eventEmpty').textContent = term
      ? 'ไม่พบ event ที่ตรงกับคำค้น'
      : 'ยังไม่มีเหตุการณ์ — event จะถูกบันทึกเมื่อสถานะอุปกรณ์เปลี่ยน (Down/Up)';
    el('eventRows').innerHTML = filtered.slice(0, 200).map((e) => `<tr>
      <td class="t">${fmtFull(e.t)}</td>
      <td>${escapeHtml(e.name)}</td>
      <td>${escapeHtml(e.group)}</td>
      <td class="ip">${e.ip}</td>
      <td><span class="ev-badge ${e.to}">${e.from} → ${e.to}</span></td>
      <td class="dur">${e.prevDurMs != null ? fmtDuration(e.prevDurMs) : '—'}</td>
    </tr>`).join('');
  }
  el('evSearch').addEventListener('input', (e) => { evSearchTerm = e.target.value; renderEventLog(); });

  el('exportLogBtn').addEventListener('click', () => {
    if (!events.length) { showToast('ยังไม่มี event ให้ export'); return; }
    const lines = ['timestamp,node,equipment,ip,from_state,to_state,previous_state_duration_sec'];
    for (const e of [...events].reverse()) {
      lines.push(`${e.t.toISOString()},"${e.name.replace(/"/g, '""')}",${e.group},${e.ip},${e.from},${e.to},${e.prevDurMs != null ? Math.round(e.prevDurMs / 1000) : ''}`);
    }
    downloadCSV(lines.join('\n'), 'event_log.csv');
    showToast(`Export ${events.length} events แล้ว`);
  });

  // ---- Device table ----
  function renderTable() {
    const select = el('groupFilter');
    const groups = [...new Set(devices.map((d) => d.group))];
    if (select.options.length !== groups.length + 1) {
      const current = select.value;
      select.innerHTML = '<option value="">ทุกประเภทอุปกรณ์</option>' + groups.map((g) => `<option value="${escapeHtml(g)}">${escapeHtml(g)}</option>`).join('');
      select.value = groups.includes(current) ? current : '';
    }
    const term = searchTerm.trim().toLowerCase();
    const rows = devices.filter((d) => {
      if (statusFilter === 'up' && d.state !== 'up') return false;
      if (statusFilter === 'down' && d.state !== 'down') return false;
      if (statusFilter === 'unknown' && d.state !== 'unknown') return false;
      if (groupFilter && d.group !== groupFilter) return false;
      if (term && !(`${d.name} ${d.ip} ${d.site}`.toLowerCase().includes(term))) return false;
      return true;
    });
    el('countNote').textContent = `แสดง ${rows.length.toLocaleString()} จาก ${devices.length.toLocaleString()} nodes`;
    el('emptyState').style.display = rows.length ? 'none' : 'block';
    const MAX_ROWS = 500;
    el('deviceRows').innerHTML = rows.slice(0, MAX_ROWS).map((d) => `<tr>
        <td><span class="dot ${d.state}"></span>${d.state}</td>
        <td>${escapeHtml(d.name)}</td>
        <td class="ip"><a href="http://${d.ip}/" target="_blank" rel="noopener noreferrer">${d.ip}</a></td>
        <td>${escapeHtml(d.group)}${d.site ? ' · ' + escapeHtml(d.site) : ''}</td>
        <td class="ms">${d.ms != null ? d.ms + ' ms' : '—'}</td>
        <td class="downdur" data-since="${d.downSince ? d.downSince.getTime() : ''}">${d.downSince ? fmtDuration(Date.now() - d.downSince.getTime()) : '—'}</td>
        <td>
          <button class="open-btn" onclick="window.open('http://${d.ip}/', '_blank')">เปิด ↗</button>
          ${currentUser && currentUser.canEdit ? `<button class="edit-btn" data-edit="${d.id}">แก้ไข</button> <button class="del-btn" data-del="${d.id}">✕</button>` : ''}
        </td>
      </tr>`).join('') +
      (rows.length > MAX_ROWS ? `<tr><td colspan="7" class="empty">แสดง ${MAX_ROWS} แถวแรก — ใช้ค้นหา/filter เพื่อดูที่เหลือ</td></tr>` : '');
  }

  // ============ 1s TICKER ============
  setInterval(() => {
    const now = new Date();
    el('clockTime').textContent = now.toLocaleTimeString('th-TH', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
    el('clockDate').textContent = now.toLocaleDateString('th-TH', { weekday: 'long', day: 'numeric', month: 'long', year: 'numeric' });
    document.querySelectorAll('[data-since]').forEach((cell) => {
      const since = parseInt(cell.dataset.since, 10);
      if (since) cell.textContent = fmtDuration(Date.now() - since);
    });
    if (nextSweepAt && !scanning) {
      const remain = nextSweepAt.getTime() - Date.now();
      el('nextSweep').textContent = remain > 0 ? fmtDuration(remain) : 'เริ่มแล้ว...';
    } else if (scanning) el('nextSweep').textContent = '(กำลัง sweep)';
  }, 1000);

  // ============ ADD / EDIT / DELETE / EXPORT ============
  let editingId = null;
  const BASE_GROUPS = ['Rectifier', 'STS', 'CCTV', 'Inverter', 'TeleAlarm'];
  const customGroups = []; // ประเภทอุปกรณ์ที่ผู้ใช้เพิ่มเอง (เก็บในหน้า)

  function rebuildGroupSelect(selected) {
    const opts = [...BASE_GROUPS, ...customGroups];
    el('fGroup').innerHTML = opts.map((g) => `<option>${escapeHtml(g)}</option>`).join('') + '<option>Other</option>';
    if (selected && (opts.includes(selected))) el('fGroup').value = selected;
  }
  el('fGroup').addEventListener('change', () => {
    el('fOtherGroup').style.display = el('fGroup').value === 'Other' ? '' : 'none';
    if (el('fGroup').value === 'Other') el('fOtherGroup').focus();
  });

  function openForm(device) {
    const form = el('addForm');
    form.classList.add('open');
    if (device) {
      editingId = device.id;
      form.classList.add('editing');
      el('fName').value = device.name;
      el('fIp').value = device.ip;
      el('fSite').value = device.site;
      // ถ้าเป็นประเภทใหม่ที่ยังไม่อยู่ในลิสต์ ให้เพิ่มเข้า customGroups ก่อน
      if (!BASE_GROUPS.includes(device.group) && !customGroups.includes(device.group) && device.group !== 'Other') customGroups.push(device.group);
      rebuildGroupSelect(device.group);
      el('fSave').textContent = 'อัปเดต';
    } else {
      editingId = null;
      form.classList.remove('editing');
      el('fName').value = ''; el('fIp').value = ''; el('fSite').value = '';
      rebuildGroupSelect(BASE_GROUPS[0]);
      el('fSave').textContent = 'บันทึก';
    }
    el('fOtherGroup').value = '';
    el('fOtherGroup').style.display = el('fGroup').value === 'Other' ? '' : 'none';
    el('fName').focus();
  }

  el('addBtn').addEventListener('click', () => {
    if (el('addForm').classList.contains('open') && editingId == null) el('addForm').classList.remove('open');
    else openForm(null);
  });
  el('fCancel').addEventListener('click', () => { el('addForm').classList.remove('open'); editingId = null; });

  el('fSave').addEventListener('click', () => {
    const name = el('fName').value.trim();
    const ip = el('fIp').value.trim();
    if (!name || !ip) { showToast('กรุณากรอกชื่อ Node และ IP'); return; }
    if (!/^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}$/.test(ip)) { showToast('รูปแบบ IP ไม่ถูกต้อง'); return; }
    if (blockedIPs.has(ip)) { showToast('IP นี้ถูก block ห้ามใช้ — ปลด block ในหน้า IP Allocation ก่อน'); return; }
    if (devices.some((d) => d.ip === ip && d.id !== editingId)) { showToast('IP นี้มีอยู่แล้วในระบบ'); return; }

    // ประเภทอุปกรณ์: ถ้าเลือก Other ต้องพิมพ์ชื่ออุปกรณ์ใหม่
    let group = el('fGroup').value;
    if (group === 'Other') {
      const custom = el('fOtherGroup').value.trim();
      if (!custom) { showToast('กรุณาพิมพ์ชื่ออุปกรณ์ใหม่ในช่อง Other'); return; }
      group = custom;
      if (!BASE_GROUPS.includes(group) && !customGroups.includes(group)) {
        customGroups.push(group);
        showToast(`เพิ่มประเภทอุปกรณ์ใหม่: ${group}`);
      }
    }

    if (editingId != null) {
      const d = devices.find((x) => x.id === editingId);
      if (d) {
        const ipChanged = d.ip !== ip;
        d.name = name; d.ip = ip;
        d.site = el('fSite').value.trim(); d.group = group;
        if (ipChanged) { d.state = 'unknown'; d.ms = null; d.downSince = null; d.stateSince = null; }
        showToast(`อัปเดต ${name} แล้ว${ipChanged ? ' — IP เปลี่ยน จะเช็คใหม่ในรอบถัดไป' : ''}`);
      }
    } else {
      devices.push({ id: nextId++, name, ip, site: el('fSite').value.trim(), group, state: 'unknown', ms: null, downSince: null, stateSince: null });
      showToast(`เพิ่ม ${name} แล้ว — จะถูกเช็คในรอบ sweep ถัดไป`);
    }
    editingId = null;
    el('addForm').classList.remove('open');
    render();
  });

  el('deviceRows').addEventListener('click', (e) => {
    const editBtn = e.target.closest('[data-edit]');
    if (editBtn) {
      const d = devices.find((x) => x.id === parseInt(editBtn.dataset.edit, 10));
      if (d) openForm(d);
      return;
    }
    const delBtn = e.target.closest('[data-del]');
    if (delBtn) {
      const id = parseInt(delBtn.dataset.del, 10);
      const d = devices.find((x) => x.id === id);
      if (d && confirm(`ลบ ${d.name} (${d.ip}) ออกจากรายการ?`)) {
        devices.splice(devices.findIndex((x) => x.id === id), 1);
        render();
        showToast('ลบแล้ว');
      }
    }
  });

  function downloadCSV(text, filename) {
    const blob = new Blob(['\ufeff' + text], { type: 'text/csv;charset=utf-8' });
    const a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = filename;
    a.click();
    URL.revokeObjectURL(a.href);
  }
  el('exportBtn').addEventListener('click', () => {
    const lines = ['name,ip,site,region,check_method,tcp_port'];
    for (const d of devices) lines.push(`${d.name},${d.ip},${d.site},${d.group},icmp,`);
    downloadCSV(lines.join('\n'), 'devices_export.csv');
    showToast(`Export ${devices.length} nodes เป็น CSV แล้ว`);
  });

  // ============ FILTERS / NAV ============
  el('search').addEventListener('input', (e) => { searchTerm = e.target.value; renderTable(); });
  el('groupFilter').addEventListener('change', (e) => { groupFilter = e.target.value; renderTable(); });
  document.querySelectorAll('.chip').forEach((chip) => {
    chip.addEventListener('click', () => {
      document.querySelectorAll('.chip').forEach((c) => c.classList.remove('active'));
      chip.classList.add('active');
      statusFilter = chip.dataset.status;
      renderTable();
    });
  });
  // ---- Page navigation ----
  function showPage(name) {
    document.querySelectorAll('.page').forEach((p) => p.classList.toggle('active', p.id === 'page-' + name));
    document.querySelectorAll('[data-nav]').forEach((a) => a.classList.toggle('active', a.dataset.page === name && !a.dataset.scroll));
    if (name === 'ipalloc') renderIpGrid();
    if (name === 'users') renderUsers();
    if (name === 'eventlog') renderEventLog();
  }
  document.querySelectorAll('[data-nav]').forEach((a) => {
    a.addEventListener('click', () => {
      showPage(a.dataset.page);
      document.querySelectorAll('[data-nav]').forEach((x) => x.classList.remove('active'));
      a.classList.add('active');
      if (a.dataset.scroll) {
        const target = document.querySelector(a.dataset.scroll);
        if (target) setTimeout(() => target.scrollIntoView({ behavior: 'smooth', block: 'start' }), 50);
      } else {
        window.scrollTo({ top: 0 });
      }
    });
  });

  // ============ USER MANAGEMENT (admin only) ============
  let editingUsername = null;

  function renderUsers() {
    if (!currentUser || !currentUser.admin) return;
    el('userCount').textContent = `${users.length} ผู้ใช้`;
    el('userRows').innerHTML = users.map((u) => `<tr>
      <td>${escapeHtml(u.first)} ${escapeHtml(u.last)}</td>
      <td class="ip">${escapeHtml(u.email)}</td>
      <td class="ip">${escapeHtml(u.username)}</td>
      <td>${u.admin
        ? '<span class="perm-badge admin">Admin</span>'
        : u.canEdit
          ? '<span class="perm-badge yes">เพิ่ม/แก้ไขได้</span>'
          : '<span class="perm-badge no">ดูอย่างเดียว</span>'}</td>
      <td>
        <button class="edit-btn" data-uedit="${escapeHtml(u.username)}">แก้ไข</button>
        ${u.builtin ? '' : `<button class="del-btn" data-udel="${escapeHtml(u.username)}">✕</button>`}
      </td>
    </tr>`).join('');
  }

  function openUserForm(user) {
    const form = el('userForm');
    form.classList.add('open');
    if (user) {
      editingUsername = user.username;
      el('userModeTag').style.display = 'inline-block';
      el('uFirst').value = user.first; el('uLast').value = user.last;
      el('uEmail').value = user.email; el('uUser').value = user.username;
      el('uPass').value = user.password;
      el('uCanEdit').checked = !!user.canEdit;
      el('uUser').disabled = !!user.builtin; // เปลี่ยน username บัญชีผู้พัฒนาไม่ได้
      el('uSave').textContent = 'อัปเดต';
    } else {
      editingUsername = null;
      el('userModeTag').style.display = 'none';
      ['uFirst','uLast','uEmail','uUser','uPass'].forEach((id) => { el(id).value = ''; });
      el('uCanEdit').checked = false;
      el('uUser').disabled = false;
      el('uSave').textContent = 'บันทึก';
    }
    el('uFirst').focus();
  }

  el('addUserBtn').addEventListener('click', () => openUserForm(null));
  el('uCancel').addEventListener('click', () => { el('userForm').classList.remove('open'); editingUsername = null; });

  el('uSave').addEventListener('click', () => {
    const first = el('uFirst').value.trim();
    const last = el('uLast').value.trim();
    const email = el('uEmail').value.trim();
    const username = el('uUser').value.trim();
    const password = el('uPass').value;
    // บังคับกรอกทุกช่อง
    if (!first || !last || !email || !username || !password) { showToast('กรุณากรอกให้ครบ: ชื่อ นามสกุล Email Username Password'); return; }
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) { showToast('รูปแบบ Email ไม่ถูกต้อง'); return; }
    if (users.some((u) => u.username === username && u.username !== editingUsername)) { showToast('Username นี้มีอยู่แล้ว'); return; }

    if (editingUsername != null) {
      const u = users.find((x) => x.username === editingUsername);
      if (u) {
        u.first = first; u.last = last; u.email = email; u.password = password;
        if (!u.builtin) { u.username = username; u.canEdit = el('uCanEdit').checked; }
        showToast(`อัปเดตผู้ใช้ ${username} แล้ว`);
        if (currentUser === u) applyPermissions();
      }
    } else {
      users.push({ username, password, first, last, email, canEdit: el('uCanEdit').checked, admin: false, builtin: false });
      showToast(`เพิ่มผู้ใช้ ${username} แล้ว`);
    }
    editingUsername = null;
    el('userForm').classList.remove('open');
    renderUsers();
  });

  el('userRows').addEventListener('click', (e) => {
    const editBtn = e.target.closest('[data-uedit]');
    if (editBtn) { const u = users.find((x) => x.username === editBtn.dataset.uedit); if (u) openUserForm(u); return; }
    const delBtn = e.target.closest('[data-udel]');
    if (delBtn) {
      const uname = delBtn.dataset.udel;
      if (uname === currentUser.username) { showToast('ลบบัญชีที่กำลังใช้งานอยู่ไม่ได้'); return; }
      if (confirm(`ลบผู้ใช้ ${uname}?`)) {
        users.splice(users.findIndex((x) => x.username === uname), 1);
        renderUsers();
        showToast('ลบผู้ใช้แล้ว');
      }
    }
  });

  // ============ IP ALLOCATION (Excel-style grid) ============
  const blockedIPs = new Set(); // IP ที่กด block ห้ามใช้ (เก็บในหน้า — ปิดแล้วหาย)
  let ipaGroup = 'CCTV';
  let ipaSubnet = SUBNET_PLAN.CCTV[0];
  const IPA_GROUPS = [
    { key: 'CCTV', label: 'IP Camera (CCTV)' },
    { key: 'Rectifier', label: 'Rectifier' },
    { key: 'STSGRP', label: 'STS, Tele Alarm, Inverter' }, // ใช้วง 172.30/172.31 ร่วมกัน
  ];
  const IPA_SUBNETS = { CCTV: SUBNET_PLAN.CCTV, Rectifier: SUBNET_PLAN.Rectifier, STSGRP: SUBNET_PLAN.STS };
  // สีแยกอุปกรณ์ในแท็บรวม
  const EQ_COLOR_CLASS = { STS: 'eq-STS', TeleAlarm: 'eq-TeleAlarm', Inverter: 'eq-Inverter' };

  function ipaHosts() {
    // เริ่ม .2 เว้นทีละ 4: .2, .6, .10 ... .254
    const hosts = [];
    for (let x = 2; x <= 254; x += 4) hosts.push(x);
    return hosts;
  }

  function renderIpGrid() {
    // tabs
    el('ipaTabs').innerHTML = IPA_GROUPS.map((g) =>
      `<div class="ipa-tab ${g.key === ipaGroup ? 'active' : ''}" data-ipagroup="${g.key}">${g.label}</div>`).join('');
    // subnet chips
    const subnets = IPA_SUBNETS[ipaGroup] || [];
    if (!subnets.includes(ipaSubnet)) ipaSubnet = subnets[0];
    el('ipaSubnets').innerHTML = subnets.map((s) =>
      `<div class="chip ${s === ipaSubnet ? 'active' : ''}" data-ipasubnet="${s}">${s}.x.x</div>`).join('');

    // legend — แท็บรวมแสดงสีแยกอุปกรณ์
    const baseLegend = `
      <span><span class="sw" style="background:rgba(107,114,128,0.35)"></span>Block ห้ามใช้</span>
      <span><span class="sw"></span>ว่าง</span>
      <span><span class="st-dot up"></span>Up · <span class="st-dot down"></span>Down · <span class="st-dot unknown"></span>ยังไม่เช็ค</span>
      <span>🚫 = block/ปลด block (ชี้ที่ IP)</span>`;
    el('ipaLegend').innerHTML = (ipaGroup === 'STSGRP'
      ? `<span><span class="sw" style="background:rgba(59,130,246,0.45)"></span>STS</span>
         <span><span class="sw" style="background:rgba(245,158,11,0.5)"></span>Tele Alarm</span>
         <span><span class="sw" style="background:rgba(168,85,247,0.5)"></span>Inverter</span>`
      : `<span><span class="sw" style="background:rgba(34,197,94,0.35)"></span>ใช้แล้ว</span>`) + baseLegend;

    // map ip -> device (ทุกประเภท กันชนข้ามวง)
    const byIp = new Map(devices.map((d) => [d.ip, d]));
    const hosts = ipaHosts();
    const canEdit = currentUser && currentUser.canEdit;

    let usedCount = 0, blockedCount = 0;
    let html = '<thead><tr>' + [1,2,3,4,5,6].map((r) => `<th class="region" colspan="2">Region ${r}</th>`).join('') + '</tr>';
    html += '<tr>' + [1,2,3,4,5,6].map(() => `<th class="sub">IP</th><th class="sub">Node</th>`).join('') + '</tr></thead><tbody>';

    for (const host of hosts) {
      html += '<tr>';
      for (let r = 1; r <= 6; r++) {
        const ip = `${ipaSubnet}.${r}.${host}`;
        const dev = byIp.get(ip);
        const isBlocked = blockedIPs.has(ip);
        if (dev) usedCount++;
        if (isBlocked) blockedCount++;
        // สีพื้น: แท็บรวมใช้สีตามอุปกรณ์, แท็บอื่นใช้เขียว
        let cls = '';
        if (dev) cls = (ipaGroup === 'STSGRP' && EQ_COLOR_CLASS[dev.group]) ? `used ${EQ_COLOR_CLASS[dev.group]}` : 'used';
        else if (isBlocked) cls = 'blocked';
        const stDot = dev ? `<span class="st-dot ${dev.state}"></span>` : '';
        const blkBtn = canEdit && !dev ? `<button class="blk-btn" data-blk="${ip}" title="${isBlocked ? 'ปลด block' : 'block ห้ามใช้'}">🚫</button>` : '';
        const nodeText = dev ? escapeHtml(dev.site || dev.name) : isBlocked ? 'BLOCKED' : '';
        html += `<td class="ipa-ip ${cls}" data-openip="${ip}">${stDot}${ip}${blkBtn}</td><td class="ipa-node ${cls}" title="${dev ? escapeHtml(dev.name) + ' — ' + dev.state : ''}">${nodeText}</td>`;
      }
      html += '</tr>';
    }
    html += '</tbody>';
    el('ipaTable').innerHTML = html;
    const totalSlots = hosts.length * 6;
    el('ipaFoot').textContent = `วง ${ipaSubnet}.x.x — ช่องทั้งหมด ${totalSlots} (${hosts.length} ต่อ region) · ใช้แล้ว ${usedCount} · block ${blockedCount} · ว่าง ${totalSlots - usedCount - blockedCount} · คลิก IP เพื่อเปิดหน้าเว็บอุปกรณ์ · หมายเหตุ: IP ที่ไม่อยู่ในช่วง .2 เว้น 4 จะไม่แสดงในผังนี้ · รายการ block เก็บในหน้านี้เท่านั้น`;
  }

  el('ipaTabs').addEventListener('click', (e) => {
    const tab = e.target.closest('[data-ipagroup]');
    if (!tab) return;
    ipaGroup = tab.dataset.ipagroup;
    ipaSubnet = (IPA_SUBNETS[ipaGroup] || [])[0];
    renderIpGrid();
  });
  el('ipaSubnets').addEventListener('click', (e) => {
    const chip = e.target.closest('[data-ipasubnet]');
    if (!chip) return;
    ipaSubnet = chip.dataset.ipasubnet;
    renderIpGrid();
  });
  el('ipaTable').addEventListener('click', (e) => {
    const blk = e.target.closest('[data-blk]');
    if (blk) {
      const ip = blk.dataset.blk;
      if (blockedIPs.has(ip)) { blockedIPs.delete(ip); showToast(`ปลด block ${ip} แล้ว`); }
      else { blockedIPs.add(ip); showToast(`Block ${ip} — ห้ามใช้`); }
      renderIpGrid();
      return;
    }
    const cell = e.target.closest('[data-openip]');
    if (cell) window.open(`http://${cell.dataset.openip}/`, '_blank');
  });

  let toastTimer = null;
  function showToast(msg, alert) {
    const t = el('toast');
    t.textContent = msg;
    t.classList.toggle('alert', !!alert);
    t.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => t.classList.remove('show'), 3600);
  }

  // ============ BOOT ============
  render();
  // sweep จะเริ่มหลัง login สำเร็จ (ดูใน tryLogin)
})();
</script>
</body>
</html>
