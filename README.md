<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>THE RESET — CONTRA INTELLIGENCE</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@300;400;600;700&family=Orbitron:wght@400;700;900&display=swap');

:root {
–bg: #050608;
–surface: #0a0c10;
–border: #1a1f2e;
–accent: #f7931a;
–accent2: #00d4aa;
–red: #ff3a3a;
–muted: #3a4055;
–text: #c8cfe8;
–dim: #6b7494;
–grid: rgba(247,147,26,0.04);
}

- { box-sizing: border-box; margin: 0; padding: 0; }

body {
background: var(–bg);
color: var(–text);
font-family: ‘Rajdhani’, sans-serif;
min-height: 100vh;
overflow-x: hidden;
}

/* Animated grid background */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image:
linear-gradient(rgba(247,147,26,0.03) 1px, transparent 1px),
linear-gradient(90deg, rgba(247,147,26,0.03) 1px, transparent 1px);
background-size: 40px 40px;
pointer-events: none;
z-index: 0;
}

.wrapper {
position: relative;
z-index: 1;
max-width: 900px;
margin: 0 auto;
padding: 40px 20px 60px;
}

/* HEADER */
.header {
text-align: center;
margin-bottom: 48px;
animation: fadeSlide 0.8s ease both;
}

.brand {
font-family: ‘Share Tech Mono’, monospace;
font-size: 11px;
letter-spacing: 4px;
color: var(–accent);
text-transform: uppercase;
margin-bottom: 12px;
opacity: 0.8;
}

.title {
font-family: ‘Orbitron’, monospace;
font-size: clamp(32px, 7vw, 64px);
font-weight: 900;
letter-spacing: -1px;
line-height: 1;
background: linear-gradient(135deg, #ffffff 0%, var(–accent) 60%, #ff6b00 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
margin-bottom: 10px;
}

.subtitle {
font-family: ‘Share Tech Mono’, monospace;
font-size: 12px;
letter-spacing: 3px;
color: var(–dim);
text-transform: uppercase;
}

.divider {
display: flex;
align-items: center;
gap: 12px;
margin: 20px 0;
}
.divider::before, .divider::after {
content: ‘’;
flex: 1;
height: 1px;
background: linear-gradient(90deg, transparent, var(–accent), transparent);
}
.divider span {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–accent);
letter-spacing: 2px;
}

/* CARDS GRID */
.cards {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
gap: 16px;
margin-bottom: 24px;
}

.card {
background: var(–surface);
border: 1px solid var(–border);
border-top: 2px solid var(–accent);
padding: 24px;
position: relative;
overflow: hidden;
animation: fadeSlide 0.6s ease both;
}

.card::before {
content: ‘’;
position: absolute;
top: 0; right: 0;
width: 60px; height: 60px;
background: radial-gradient(circle at top right, rgba(247,147,26,0.08), transparent 70%);
}

.card-label {
font-family: ‘Share Tech Mono’, monospace;
font-size: 9px;
letter-spacing: 3px;
color: var(–dim);
text-transform: uppercase;
margin-bottom: 8px;
}

.card-value {
font-family: ‘Orbitron’, monospace;
font-size: clamp(28px, 5vw, 42px);
font-weight: 700;
color: var(–accent);
line-height: 1;
margin-bottom: 6px;
}

.card-value.red { color: var(–red); }
.card-value.teal { color: var(–accent2); }

.card-desc {
font-size: 13px;
color: var(–dim);
line-height: 1.5;
font-weight: 300;
}

.card-source {
font-family: ‘Share Tech Mono’, monospace;
font-size: 9px;
color: var(–muted);
margin-top: 12px;
letter-spacing: 1px;
}

/* CHART SECTION */
.chart-section {
background: var(–surface);
border: 1px solid var(–border);
padding: 28px;
margin-bottom: 24px;
animation: fadeSlide 0.7s ease both;
}

.section-title {
font-family: ‘Orbitron’, monospace;
font-size: 13px;
font-weight: 700;
letter-spacing: 2px;
color: var(–accent);
text-transform: uppercase;
margin-bottom: 6px;
}

.section-sub {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–dim);
letter-spacing: 2px;
margin-bottom: 24px;
}

/* BAR CHART */
.bar-chart { width: 100%; }

.bar-row {
display: flex;
align-items: center;
margin-bottom: 14px;
gap: 12px;
}

.bar-label {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–text);
width: 130px;
flex-shrink: 0;
letter-spacing: 1px;
}

.bar-track {
flex: 1;
height: 22px;
background: rgba(255,255,255,0.03);
border: 1px solid var(–border);
position: relative;
overflow: hidden;
}

.bar-fill {
height: 100%;
position: relative;
display: flex;
align-items: center;
justify-content: flex-end;
padding-right: 8px;
transition: width 1.5s cubic-bezier(0.25, 1, 0.5, 1);
}

.bar-fill::after {
content: ‘’;
position: absolute;
top: 0; left: 0; right: 0; bottom: 0;
background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1));
}

.bar-val {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
font-weight: 700;
color: rgba(255,255,255,0.9);
position: relative;
z-index: 1;
}

.bar-extra {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–dim);
width: 60px;
text-align: right;
flex-shrink: 0;
}

/* LINE CHART */
.line-chart-container {
position: relative;
width: 100%;
height: 200px;
}

.line-chart-container svg {
width: 100%;
height: 100%;
overflow: visible;
}

/* TRUST TIMELINE */
.trust-chart { margin-top: 8px; }

.trust-row {
display: flex;
align-items: center;
gap: 12px;
margin-bottom: 12px;
}

.trust-label {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–text);
width: 140px;
flex-shrink: 0;
}

.trust-bar-wrap {
flex: 1;
display: flex;
flex-direction: column;
gap: 3px;
}

.trust-bar-track {
height: 10px;
background: rgba(255,255,255,0.03);
border: 1px solid var(–border);
position: relative;
}

.trust-bar-fill {
height: 100%;
transition: width 1.5s cubic-bezier(0.25, 1, 0.5, 1);
}

.trust-era {
font-family: ‘Share Tech Mono’, monospace;
font-size: 8px;
color: var(–muted);
letter-spacing: 1px;
}

/* TIMELINE */
.timeline {
background: var(–surface);
border: 1px solid var(–border);
padding: 28px;
margin-bottom: 24px;
animation: fadeSlide 0.8s ease both;
}

.timeline-items {
display: flex;
gap: 0;
margin-top: 20px;
position: relative;
}

.timeline-items::before {
content: ‘’;
position: absolute;
top: 16px;
left: 0; right: 0;
height: 2px;
background: linear-gradient(90deg, var(–muted), var(–accent), var(–accent2));
}

.tl-item {
flex: 1;
padding-top: 36px;
position: relative;
text-align: center;
padding-left: 4px;
padding-right: 4px;
}

.tl-dot {
position: absolute;
top: 9px;
left: 50%;
transform: translateX(-50%);
width: 14px;
height: 14px;
border-radius: 50%;
border: 2px solid var(–bg);
}

.tl-year {
font-family: ‘Orbitron’, monospace;
font-size: 11px;
font-weight: 700;
margin-bottom: 4px;
letter-spacing: 1px;
}

.tl-event {
font-family: ‘Share Tech Mono’, monospace;
font-size: 8px;
color: var(–dim);
line-height: 1.5;
letter-spacing: 0.5px;
}

/* BOTTOM POST */
.post-block {
background: var(–surface);
border: 1px solid var(–border);
border-left: 3px solid var(–accent);
padding: 28px;
margin-bottom: 24px;
animation: fadeSlide 0.9s ease both;
}

.post-tag {
font-family: ‘Share Tech Mono’, monospace;
font-size: 9px;
letter-spacing: 3px;
color: var(–accent);
text-transform: uppercase;
margin-bottom: 14px;
display: flex;
align-items: center;
gap: 8px;
}

.post-tag::before {
content: ‘//’;
color: var(–muted);
}

.post-text {
font-size: 15px;
line-height: 1.8;
color: var(–text);
font-weight: 400;
}

.post-text strong {
color: #fff;
font-weight: 600;
}

.post-question {
font-family: ‘Orbitron’, monospace;
font-size: 14px;
color: var(–accent);
margin-top: 20px;
letter-spacing: 1px;
}

/* FOOTER */
.footer {
display: flex;
justify-content: space-between;
align-items: center;
border-top: 1px solid var(–border);
padding-top: 20px;
margin-top: 20px;
}

.footer-brand {
font-family: ‘Orbitron’, monospace;
font-size: 14px;
font-weight: 900;
color: var(–accent);
letter-spacing: 1px;
}

.footer-sub {
font-family: ‘Share Tech Mono’, monospace;
font-size: 9px;
color: var(–dim);
letter-spacing: 2px;
margin-top: 3px;
}

.footer-date {
font-family: ‘Share Tech Mono’, monospace;
font-size: 10px;
color: var(–muted);
letter-spacing: 2px;
text-align: right;
}

/* SCAN LINE */
.scanline {
position: fixed;
inset: 0;
pointer-events: none;
z-index: 999;
background: repeating-linear-gradient(
0deg,
transparent,
transparent 2px,
rgba(0,0,0,0.05) 2px,
rgba(0,0,0,0.05) 4px
);
}

@keyframes fadeSlide {
from { opacity: 0; transform: translateY(16px); }
to   { opacity: 1; transform: translateY(0); }
}

@keyframes barGrow {
from { width: 0 !important; }
}

.bar-fill { animation: barGrow 1.5s cubic-bezier(0.25,1,0.5,1) both; }

.blink {
animation: blink 1.2s step-end infinite;
}
@keyframes blink {
0%, 100% { opacity: 1; }
50% { opacity: 0; }
}
</style>

</head>
<body>
<div class="scanline"></div>
<div class="wrapper">

  <!-- HEADER -->

  <div class="header">
    <div class="brand">◈ Contra Intelligence ◈ Signal Dispatch</div>
    <div class="title">THE RESET</div>
    <div class="subtitle">Data-Driven Intelligence Brief · March 2026</div>
    <div class="divider"><span>CLASSIFIED OPEN SOURCE</span></div>
  </div>

  <!-- STAT CARDS -->

  <div class="cards">
    <div class="card" style="animation-delay:0.1s">
      <div class="card-label">// Global Total Debt</div>
      <div class="card-value">$251T</div>
      <div class="card-desc">235% of world GDP. Stabilized at an elevated level. Public debt alone sits at $99.2 trillion.</div>
      <div class="card-source">SRC: IMF Global Debt Database 2025</div>
    </div>
    <div class="card" style="animation-delay:0.2s">
      <div class="card-label">// Trust in US Gov't</div>
      <div class="card-value red">~16%</div>
      <div class="card-desc">Share of Americans who trust the federal government to do the right thing. Down from 73% in 1958.</div>
      <div class="card-source">SRC: Pew Research, Sept 2025</div>
    </div>
    <div class="card" style="animation-delay:0.3s">
      <div class="card-label">// Trust in Media</div>
      <div class="card-value red">28%</div>
      <div class="card-desc">All-time low. Among adults under 50, no age group exceeds 28% trust in mass media.</div>
      <div class="card-source">SRC: Gallup, Sept 2025</div>
    </div>
    <div class="card" style="animation-delay:0.4s">
      <div class="card-label">// Countries Over 300% Debt/GDP</div>
      <div class="card-value teal">Several</div>
      <div class="card-desc">Combined household, corporate and gov't debt exceeds 3 full years of economic output in major economies.</div>
      <div class="card-source">SRC: IIF Global Debt Monitor, Q4 2025</div>
    </div>
  </div>

  <!-- DEBT BY COUNTRY BAR CHART -->

  <div class="chart-section" style="animation-delay:0.3s">
    <div class="section-title">Government Debt to GDP by Major Economy</div>
    <div class="section-sub">// 2025 · IMF World Economic Outlook</div>
    <div class="bar-chart">
      <div class="bar-row">
        <div class="bar-label">JAPAN</div>
        <div class="bar-track">
          <div class="bar-fill" style="width:92%; background: linear-gradient(90deg, #7b2d00, var(--red));">
            <span class="bar-val">230%</span>
          </div>
        </div>
        <div class="bar-extra">of GDP</div>
      </div>
      <div class="bar-row">
        <div class="bar-label">UNITED STATES</div>
        <div class="bar-track">
          <div class="bar-fill" style="width:50%; background: linear-gradient(90deg, #7b4500, var(--accent));">
            <span class="bar-val">121%</span>
          </div>
        </div>
        <div class="bar-extra">of GDP</div>
      </div>
      <div class="bar-row">
        <div class="bar-label">FRANCE</div>
        <div class="bar-track">
          <div class="bar-fill" style="width:46%; background: linear-gradient(90deg, #7b4500, var(--accent));">
            <span class="bar-val">113%</span>
          </div>
        </div>
        <div class="bar-extra">of GDP</div>
      </div>
      <div class="bar-row">
        <div class="bar-label">CHINA</div>
        <div class="bar-track">
          <div class="bar-fill" style="width:36%; background: linear-gradient(90deg, #1a5c4a, var(--accent2));">
            <span class="bar-val">88%</span>
          </div>
        </div>
        <div class="bar-extra">of GDP</div>
      </div>
      <div class="bar-row">
        <div class="bar-label">WORLD AVG</div>
        <div class="bar-track">
          <div class="bar-fill" style="width:38%; background: linear-gradient(90deg, #1a2a5c, #4a6aff);">
            <span class="bar-val">94.7%</span>
          </div>
        </div>
        <div class="bar-extra">of GDP</div>
      </div>
    </div>
    <div style="margin-top:12px; font-family:'Share Tech Mono',monospace; font-size:9px; color:var(--muted); letter-spacing:1px;">
      ▲ Global avg up 2.3 pts YoY · 23 countries borrowing more than their entire GDP
    </div>
  </div>

  <!-- TRUST COLLAPSE CHART -->

  <div class="chart-section" style="animation-delay:0.5s">
    <div class="section-title">Institutional Trust Collapse · USA</div>
    <div class="section-sub">// % expressing high confidence across eras · Pew / Gallup composite</div>
    <div class="trust-chart">
      <div class="trust-row">
        <div class="trust-label">FED GOV'T</div>
        <div class="trust-bar-wrap">
          <div class="trust-bar-track">
            <div class="trust-bar-fill" style="width:73%; background: linear-gradient(90deg, #1a5c4a, var(--accent2));"></div>
          </div>
          <div class="trust-era">1958 · 73%</div>
          <div class="trust-bar-track" style="margin-top:4px">
            <div class="trust-bar-fill" style="width:16%; background: linear-gradient(90deg, #7b2d00, var(--red));"></div>
          </div>
          <div class="trust-era">2025 · ~16%</div>
        </div>
      </div>
      <div class="trust-row">
        <div class="trust-label">MEDIA</div>
        <div class="trust-bar-wrap">
          <div class="trust-bar-track">
            <div class="trust-bar-fill" style="width:55%; background: linear-gradient(90deg, #1a5c4a, var(--accent2));"></div>
          </div>
          <div class="trust-era">EARLY 2000s · ~55%</div>
          <div class="trust-bar-track" style="margin-top:4px">
            <div class="trust-bar-fill" style="width:28%; background: linear-gradient(90deg, #7b2d00, var(--red));"></div>
          </div>
          <div class="trust-era">2025 · 28% (all-time low)</div>
        </div>
      </div>
      <div class="trust-row">
        <div class="trust-label">CONGRESS</div>
        <div class="trust-bar-wrap">
          <div class="trust-bar-track">
            <div class="trust-bar-fill" style="width:42%; background: linear-gradient(90deg, #1a5c4a, var(--accent2));"></div>
          </div>
          <div class="trust-era">1970s · ~42%</div>
          <div class="trust-bar-track" style="margin-top:4px">
            <div class="trust-bar-fill" style="width:7%; background: linear-gradient(90deg, #7b2d00, var(--red));"></div>
          </div>
          <div class="trust-era">2025 · 7% (record low)</div>
        </div>
      </div>
      <div class="trust-row">
        <div class="trust-label">RELIGION</div>
        <div class="trust-bar-wrap">
          <div class="trust-bar-track">
            <div class="trust-bar-fill" style="width:53%; background: linear-gradient(90deg, #1a5c4a, var(--accent2));"></div>
          </div>
          <div class="trust-era">~20 YRS AGO · 53%</div>
          <div class="trust-bar-track" style="margin-top:4px">
            <div class="trust-bar-fill" style="width:32%; background: linear-gradient(90deg, #7b2d00, var(--red));"></div>
          </div>
          <div class="trust-era">2025 · 32%</div>
        </div>
      </div>
    </div>
  </div>

  <!-- RESET TIMELINE -->

  <div class="timeline">
    <div class="section-title">Historical Reset Playbook</div>
    <div class="section-sub">// Monetary system failures and the windows they opened</div>
    <div class="timeline-items">
      <div class="tl-item">
        <div class="tl-dot" style="background: #4a6aff;"></div>
        <div class="tl-year" style="color:#4a6aff;">1944</div>
        <div class="tl-event">Bretton Woods<br>USD anchored<br>to gold</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: var(--accent);"></div>
        <div class="tl-year" style="color:var(--accent);">1971</div>
        <div class="tl-event">Nixon Shock<br>gold window<br>closed</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: var(--accent);"></div>
        <div class="tl-year" style="color:var(--accent);">1974</div>
        <div class="tl-event">Petrodollar<br>deal with<br>Saudi Arabia</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: var(--red);"></div>
        <div class="tl-year" style="color:var(--red);">2008</div>
        <div class="tl-event">Credit crisis<br>$700B bailout<br>trust collapse</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: var(--accent2);"></div>
        <div class="tl-year" style="color:var(--accent2);">2009</div>
        <div class="tl-event">Bitcoin<br>genesis block<br>mined</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: var(--red);"></div>
        <div class="tl-year" style="color:var(--red);">2020</div>
        <div class="tl-event">$9T printed<br>supply chain<br>collapse</div>
      </div>
      <div class="tl-item">
        <div class="tl-dot" style="background: #fff;" style="animation: blink 1s infinite;"></div>
        <div class="tl-year" style="color:#fff;">NOW<span class="blink">_</span></div>
        <div class="tl-event">$251T debt<br>trust at<br>all-time lows</div>
      </div>
    </div>
  </div>

  <!-- POST TEXT -->

  <div class="post-block">
    <div class="post-tag">SIGNAL</div>
    <div class="post-text">
      The world isn't ending. It's settling.<br><br>
      <strong>$251 trillion in global debt.</strong> Government trust near 16%. Media trust at 28% and falling. 23 countries borrowing more than their entire economic output.<br><br>
      These aren't talking points. These are IMF and Pew numbers published this year.<br><br>
      Every reset in history created a window. Bretton Woods. The Nixon shock. The 2008 freeze. Each one punished the people holding the old assumptions and rewarded whoever had already moved.<br><br>
      Hard money. Open networks. Sovereign tools. The infrastructure for the next era is already being built by people who saw this coming years ago.<br><br>
      <strong>The noise is loud because the stakes are real.</strong>
    </div>
    <div class="post-question">What are you building while everyone else is watching the news?</div>
  </div>

  <!-- FOOTER -->

  <div class="footer">
    <div>
      <div class="footer-brand">CONTRA INTELLIGENCE</div>
      <div class="footer-sub">// Nostr · Rumble · YouTube</div>
    </div>
    <div class="footer-date">
      MARCH 2026<br>
      DATA: IMF · PEW · GALLUP · IIF
    </div>
  </div>

</div>
</body>
</html>
