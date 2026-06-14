<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>VAIBHAV SAINI // FULL STACK DEVELOPER</title>
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Orbitron:wght@400;700;900&family=Courier+Prime:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet"/>
<style>
:root {
  --bg:       #0a0a0a;
  --bg2:      #0d0f14;
  --bg3:      #111520;
  --cyan:     #00ffcc;
  --amber:    #ffd700;
  --red:      #ff3333;
  --lime:     #7ffe00;
  --white:    #e8e8e8;
  --dim:      #666;
  --border:   #1e2430;
  --mono:     'Share Tech Mono', monospace;
  --orb:      'Orbitron', monospace;
  --courier:  'Courier Prime', monospace;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--white);
  font-family: var(--mono);
  cursor: none;
  overflow-x: hidden;
}

/* ── CURSOR ── */
#cursor {
  position: fixed;
  width: 12px; height: 12px;
  background: var(--cyan);
  border-radius: 50%;
  pointer-events: none;
  z-index: 9999;
  transform: translate(-50%, -50%);
  box-shadow: 0 0 10px var(--cyan), 0 0 30px var(--cyan);
  transition: width .15s, height .15s, background .15s;
  mix-blend-mode: screen;
}
#cursor.hover {
  width: 28px; height: 28px;
  background: transparent;
  border: 2px solid var(--cyan);
}
.trail-dot {
  position: fixed;
  border-radius: 50%;
  pointer-events: none;
  z-index: 9998;
  transform: translate(-50%, -50%);
  mix-blend-mode: screen;
}

/* ── CRT OVERLAY ── */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0,0,0,0.08) 2px,
    rgba(0,0,0,0.08) 4px
  );
  pointer-events: none;
  z-index: 9000;
}
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background: radial-gradient(ellipse at center, transparent 60%, rgba(0,0,0,0.5) 100%);
  pointer-events: none;
  z-index: 9001;
}

/* ── NAV ── */
nav {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 8000;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 3rem;
  height: 56px;
  background: rgba(10,10,10,0.92);
  border-bottom: 1px solid var(--cyan);
  backdrop-filter: blur(8px);
}
.nav-logo {
  font-family: var(--orb);
  font-size: .75rem;
  font-weight: 900;
  letter-spacing: .25em;
  color: var(--cyan);
  text-shadow: 0 0 12px var(--cyan);
}
.nav-links { display: flex; gap: 2.5rem; list-style: none; }
.nav-links a {
  font-family: var(--mono);
  font-size: .72rem;
  letter-spacing: .15em;
  color: var(--dim);
  text-decoration: none;
  text-transform: uppercase;
  transition: color .2s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px; left: 0; right: 0;
  height: 1px;
  background: var(--cyan);
  transform: scaleX(0);
  transition: transform .2s;
}
.nav-links a:hover { color: var(--cyan); }
.nav-links a:hover::after { transform: scaleX(1); }
.nav-status {
  display: flex; align-items: center; gap: .6rem;
  font-size: .65rem; color: var(--lime); letter-spacing: .12em;
}
.pulse {
  width: 8px; height: 8px;
  background: var(--lime);
  border-radius: 50%;
  animation: pulse 1.4s ease-in-out infinite;
  box-shadow: 0 0 6px var(--lime);
}
@keyframes pulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50%      { opacity: .4; transform: scale(.8); }
}

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex; flex-direction: column;
  justify-content: center; align-items: flex-start;
  padding: 0 6rem;
  position: relative;
  overflow: hidden;
}
.hero-grid-bg {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(0,255,204,.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,255,204,.04) 1px, transparent 1px);
  background-size: 60px 60px;
  pointer-events: none;
}
.hero-tag {
  font-family: var(--mono);
  font-size: .7rem;
  letter-spacing: .3em;
  color: var(--amber);
  margin-bottom: 1.5rem;
  display: flex; align-items: center; gap: .8rem;
}
.hero-tag::before {
  content: '';
  display: inline-block;
  width: 3rem; height: 1px;
  background: var(--amber);
  box-shadow: 0 0 8px var(--amber);
}
.hero-name {
  font-family: var(--orb);
  font-size: clamp(3.5rem, 9vw, 8rem);
  font-weight: 900;
  line-height: .9;
  letter-spacing: -.02em;
  color: var(--white);
  text-shadow: 0 0 60px rgba(0,255,204,.15);
  position: relative;
}
.hero-name .line1 { display: block; }
.hero-name .line2 {
  display: block;
  color: transparent;
  -webkit-text-stroke: 1px var(--cyan);
  text-shadow: none;
}
.hero-name .glitch {
  position: relative;
  display: inline-block;
  animation: glitch-base 4s infinite;
}
.hero-name .glitch::before,
.hero-name .glitch::after {
  content: attr(data-text);
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  font-family: var(--orb);
  font-weight: 900;
}
.hero-name .glitch::before {
  color: var(--red);
  clip-path: polygon(0 30%, 100% 30%, 100% 55%, 0 55%);
  animation: glitch-1 4s infinite;
}
.hero-name .glitch::after {
  color: var(--cyan);
  clip-path: polygon(0 60%, 100% 60%, 100% 80%, 0 80%);
  animation: glitch-2 4s infinite;
}
@keyframes glitch-base {
  0%,94%,100% { transform: none; }
  95% { transform: skewX(-1deg); }
}
@keyframes glitch-1 {
  0%,94%,100% { transform: none; opacity: 0; }
  95% { transform: translate(-4px, 2px); opacity: 1; }
  97% { transform: translate(3px, -1px); opacity: 1; }
}
@keyframes glitch-2 {
  0%,94%,100% { transform: none; opacity: 0; }
  96% { transform: translate(4px, -2px); opacity: 1; }
  98% { transform: translate(-2px, 1px); opacity: 1; }
}
.hero-sub {
  margin-top: 1.8rem;
  font-family: var(--mono);
  font-size: 1rem;
  color: var(--dim);
  letter-spacing: .05em;
  display: flex; align-items: center; gap: .6rem;
}
.hero-sub .sep { color: var(--cyan); }
.hero-typed {
  color: var(--cyan);
  text-shadow: 0 0 10px var(--cyan);
  border-right: 2px solid var(--cyan);
  animation: blink .75s step-end infinite;
  min-width: 1ch;
}
@keyframes blink { 50% { border-color: transparent; } }
.hero-stats {
  margin-top: 3.5rem;
  display: flex; gap: 3rem;
}
.stat-box {
  display: flex; flex-direction: column;
  border-left: 2px solid var(--amber);
  padding-left: 1rem;
  gap: .3rem;
}
.stat-num {
  font-family: var(--orb);
  font-size: 2rem;
  font-weight: 900;
  color: var(--amber);
  text-shadow: 0 0 20px rgba(255,215,0,.5);
  line-height: 1;
}
.stat-label {
  font-family: var(--mono);
  font-size: .62rem;
  letter-spacing: .2em;
  color: var(--dim);
  text-transform: uppercase;
}
.hero-cta {
  margin-top: 3rem;
  display: flex; gap: 1rem;
}
.btn {
  font-family: var(--orb);
  font-size: .65rem;
  font-weight: 700;
  letter-spacing: .2em;
  text-transform: uppercase;
  padding: .9rem 2rem;
  border: 1px solid;
  text-decoration: none;
  transition: all .25s;
  position: relative;
  overflow: hidden;
}
.btn::before {
  content: '';
  position: absolute;
  inset: 0;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .25s;
  z-index: -1;
}
.btn-primary { color: var(--bg); background: var(--cyan); border-color: var(--cyan); }
.btn-primary:hover { box-shadow: 0 0 30px var(--cyan); transform: translateY(-2px); }
.btn-outline { color: var(--cyan); background: transparent; border-color: var(--cyan); }
.btn-outline::before { background: var(--cyan); }
.btn-outline:hover { color: var(--bg); }
.btn-outline:hover::before { transform: scaleX(1); }

.hero-scroll {
  position: absolute;
  bottom: 2.5rem; left: 6rem;
  display: flex; align-items: center; gap: .8rem;
  font-size: .62rem; letter-spacing: .25em; color: var(--dim);
  text-transform: uppercase;
}
.scroll-line {
  width: 3rem; height: 1px;
  background: var(--dim);
  position: relative;
  overflow: hidden;
}
.scroll-line::after {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 100%; height: 100%;
  background: var(--cyan);
  animation: scroll-anim 2s ease-in-out infinite;
}
@keyframes scroll-anim {
  0% { left: -100%; }
  100% { left: 100%; }
}

/* ── SECTIONS ── */
section {
  padding: 7rem 6rem;
  position: relative;
}
section:nth-child(even) { background: var(--bg2); }

.section-tag {
  font-family: var(--mono);
  font-size: .65rem;
  letter-spacing: .35em;
  color: var(--amber);
  text-transform: uppercase;
  display: flex; align-items: center; gap: .8rem;
  margin-bottom: .8rem;
}
.section-tag::before {
  content: '';
  display: inline-block;
  width: 2rem; height: 1px;
  background: var(--amber);
}
.section-title {
  font-family: var(--orb);
  font-size: clamp(1.6rem, 3vw, 2.5rem);
  font-weight: 900;
  letter-spacing: -.02em;
  color: var(--white);
  margin-bottom: 3.5rem;
  position: relative;
}
.section-title span { color: var(--cyan); }
.section-title::after {
  content: '';
  display: block;
  width: 4rem; height: 2px;
  background: linear-gradient(90deg, var(--cyan), transparent);
  margin-top: .8rem;
}

/* ── ABOUT ── */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}
.terminal-box {
  background: var(--bg3);
  border: 1px solid var(--border);
  border-top: 2px solid var(--cyan);
  position: relative;
  overflow: hidden;
}
.terminal-box::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, var(--cyan), transparent);
}
.terminal-header {
  display: flex; align-items: center; gap: .5rem;
  padding: .7rem 1rem;
  border-bottom: 1px solid var(--border);
  font-size: .65rem;
  color: var(--dim);
  letter-spacing: .1em;
}
.dot { width: 10px; height: 10px; border-radius: 50%; }
.dot-r { background: #ff5f56; }
.dot-y { background: #ffbd2e; }
.dot-g { background: #27c93f; }
.terminal-body { padding: 1.5rem; font-size: .82rem; line-height: 1.9; }
.t-key { color: var(--cyan); }
.t-val { color: var(--white); }
.t-str { color: var(--amber); }
.t-comment { color: #444; font-style: italic; }
.t-arr { color: var(--lime); }

.identity-table { width: 100%; }
.identity-table tr { border-bottom: 1px solid var(--border); }
.identity-table tr:last-child { border-bottom: none; }
.identity-table td {
  padding: .9rem 0;
  font-size: .78rem;
  vertical-align: top;
}
.id-key {
  color: var(--amber);
  letter-spacing: .1em;
  width: 30%;
  font-family: var(--mono);
}
.id-val { color: var(--white); font-family: var(--courier); }
.id-arrow { color: var(--dim); padding: 0 .8rem; }

/* ── EXPERIENCE ── */
.exp-list { display: flex; flex-direction: column; gap: 0; }
.exp-item {
  display: grid;
  grid-template-columns: 120px 1fr;
  gap: 0 2.5rem;
  position: relative;
}
.exp-item + .exp-item { margin-top: 0; }
.exp-line {
  display: flex; flex-direction: column;
  align-items: center;
  padding-top: .4rem;
}
.exp-dot {
  width: 14px; height: 14px;
  border: 2px solid var(--cyan);
  border-radius: 50%;
  background: var(--bg);
  flex-shrink: 0;
  position: relative;
  z-index: 1;
  box-shadow: 0 0 10px var(--cyan);
}
.exp-connector {
  width: 1px;
  flex: 1;
  background: linear-gradient(to bottom, var(--cyan), var(--border));
  margin-top: 4px;
}
.exp-item:last-child .exp-connector { background: transparent; }
.exp-date {
  font-size: .65rem;
  letter-spacing: .1em;
  color: var(--amber);
  text-align: right;
  padding-top: .1rem;
  line-height: 1.4;
  font-family: var(--mono);
}
.exp-card {
  background: var(--bg3);
  border: 1px solid var(--border);
  border-left: 3px solid var(--cyan);
  padding: 1.5rem 1.8rem;
  margin-bottom: 2rem;
  transition: border-color .2s, box-shadow .2s;
}
.exp-card:hover {
  border-left-color: var(--amber);
  box-shadow: -4px 0 20px rgba(255,215,0,.1);
}
.exp-company {
  font-family: var(--orb);
  font-size: .85rem;
  font-weight: 700;
  color: var(--white);
  letter-spacing: .08em;
}
.exp-role {
  font-size: .72rem;
  color: var(--cyan);
  letter-spacing: .12em;
  text-transform: uppercase;
  margin-top: .3rem;
  margin-bottom: 1rem;
}
.exp-bullets { list-style: none; display: flex; flex-direction: column; gap: .5rem; }
.exp-bullets li {
  font-family: var(--courier);
  font-size: .82rem;
  color: #aaa;
  padding-left: 1.2rem;
  position: relative;
  line-height: 1.5;
}
.exp-bullets li::before {
  content: '◈';
  position: absolute;
  left: 0;
  color: var(--cyan);
  font-size: .7rem;
}
.exp-bullets li strong { color: var(--white); font-weight: 700; }

/* ── PROJECTS ── */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
}
.project-card {
  background: var(--bg3);
  border: 1px solid var(--border);
  position: relative;
  overflow: hidden;
  transition: transform .25s, box-shadow .25s;
  group: true;
}
.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 60px rgba(0,0,0,.5), 0 0 40px rgba(0,255,204,.06);
}
.project-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--cyan), var(--amber));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .3s;
}
.project-card:hover::before { transform: scaleX(1); }
.project-accent {
  position: absolute;
  top: 0; right: 0;
  width: 80px; height: 80px;
  background: radial-gradient(circle at top right, rgba(0,255,204,.06), transparent);
  pointer-events: none;
}
.project-num {
  position: absolute;
  top: 1.2rem; right: 1.5rem;
  font-family: var(--orb);
  font-size: 3rem;
  font-weight: 900;
  color: rgba(255,255,255,.03);
  line-height: 1;
  user-select: none;
}
.project-inner { padding: 2rem; }
.project-emoji {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  display: block;
  filter: drop-shadow(0 0 8px rgba(0,255,204,.4));
}
.project-name {
  font-family: var(--orb);
  font-size: 1rem;
  font-weight: 700;
  color: var(--white);
  letter-spacing: .05em;
  margin-bottom: .3rem;
}
.project-desc {
  font-family: var(--mono);
  font-size: .65rem;
  color: var(--dim);
  letter-spacing: .1em;
  text-transform: uppercase;
  margin-bottom: 1.2rem;
}
.project-metrics {
  display: flex; flex-wrap: wrap; gap: .5rem;
  margin-bottom: 1.2rem;
}
.metric-pill {
  font-family: var(--mono);
  font-size: .6rem;
  letter-spacing: .08em;
  padding: .3rem .7rem;
  border: 1px solid;
  text-transform: uppercase;
}
.metric-pill.cyan  { color: var(--cyan);  border-color: rgba(0,255,204,.3);  background: rgba(0,255,204,.06); }
.metric-pill.amber { color: var(--amber); border-color: rgba(255,215,0,.3);  background: rgba(255,215,0,.06); }
.metric-pill.lime  { color: var(--lime);  border-color: rgba(127,254,0,.3);  background: rgba(127,254,0,.06); }
.metric-pill.red   { color: var(--red);   border-color: rgba(255,51,51,.3);  background: rgba(255,51,51,.06); }
.project-stack {
  font-family: var(--mono);
  font-size: .68rem;
  color: #555;
  line-height: 1.7;
  border-top: 1px solid var(--border);
  padding-top: 1rem;
  margin-bottom: 1rem;
}
.project-links { display: flex; gap: .7rem; }
.project-link {
  font-family: var(--orb);
  font-size: .58rem;
  font-weight: 700;
  letter-spacing: .2em;
  padding: .5rem 1.1rem;
  text-decoration: none;
  border: 1px solid;
  transition: all .2s;
  text-transform: uppercase;
}
.pl-code { color: var(--white); border-color: var(--border); }
.pl-code:hover { color: var(--cyan); border-color: var(--cyan); box-shadow: 0 0 12px rgba(0,255,204,.2); }
.pl-live { color: var(--bg); background: var(--cyan); border-color: var(--cyan); }
.pl-live:hover { box-shadow: 0 0 20px var(--cyan); }

/* ── TECH STACK ── */
.stack-groups { display: flex; flex-direction: column; gap: 2rem; }
.stack-group-label {
  font-family: var(--mono);
  font-size: .65rem;
  letter-spacing: .25em;
  color: var(--amber);
  text-transform: uppercase;
  margin-bottom: 1rem;
  display: flex; align-items: center; gap: .7rem;
}
.stack-group-label::before {
  content: '';
  display: inline-block;
  width: 1.5rem; height: 1px;
  background: var(--amber);
}
.stack-pills { display: flex; flex-wrap: wrap; gap: .6rem; }
.stack-pill {
  font-family: var(--mono);
  font-size: .72rem;
  letter-spacing: .08em;
  padding: .55rem 1.1rem;
  border: 1px solid var(--border);
  color: #aaa;
  background: var(--bg3);
  transition: all .2s;
  position: relative;
  overflow: hidden;
}
.stack-pill::before {
  content: '';
  position: absolute;
  bottom: 0; left: 0;
  width: 100%; height: 1px;
  background: var(--cyan);
  transform: scaleX(0);
  transition: transform .2s;
}
.stack-pill:hover {
  color: var(--cyan);
  border-color: var(--cyan);
  box-shadow: 0 0 16px rgba(0,255,204,.12);
}
.stack-pill:hover::before { transform: scaleX(1); }
.stack-pill.hot { color: var(--cyan); border-color: rgba(0,255,204,.4); }

/* ── ACHIEVEMENTS ── */
.ach-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1px;
  border: 1px solid var(--border);
  overflow: hidden;
}
.ach-cell {
  background: var(--bg3);
  padding: 2rem 1.5rem;
  text-align: center;
  border: none;
  transition: background .2s;
  position: relative;
  overflow: hidden;
}
.ach-cell::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, rgba(0,255,204,.04), transparent);
  opacity: 0;
  transition: opacity .2s;
}
.ach-cell:hover { background: var(--bg2); }
.ach-cell:hover::after { opacity: 1; }
.ach-cell + .ach-cell { border-left: 1px solid var(--border); }
.ach-grid .ach-row:first-child .ach-cell,
.ach-row + .ach-row .ach-cell { border-top: 1px solid var(--border); }
.ach-big {
  font-family: var(--orb);
  font-size: 2.8rem;
  font-weight: 900;
  color: var(--cyan);
  text-shadow: 0 0 30px rgba(0,255,204,.4);
  line-height: 1;
  display: block;
  margin-bottom: .5rem;
}
.ach-big.amber { color: var(--amber); text-shadow: 0 0 30px rgba(255,215,0,.4); }
.ach-big.lime  { color: var(--lime);  text-shadow: 0 0 30px rgba(127,254,0,.4); }
.ach-big.red   { color: var(--red);   text-shadow: 0 0 30px rgba(255,51,51,.4); }
.ach-label {
  font-family: var(--mono);
  font-size: .62rem;
  letter-spacing: .18em;
  color: var(--dim);
  text-transform: uppercase;
  line-height: 1.5;
}

/* ── CONTACT ── */
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}
.contact-ascii {
  font-family: var(--mono);
  font-size: .72rem;
  line-height: 1.9;
  color: #555;
  white-space: pre;
}
.contact-ascii .c-hl { color: var(--cyan); }
.contact-ascii .c-am { color: var(--amber); }
.contact-ascii .c-lm { color: var(--lime); }
.contact-links { display: flex; flex-direction: column; gap: .9rem; }
.contact-link {
  display: flex; align-items: center; gap: 1.2rem;
  padding: 1rem 1.5rem;
  border: 1px solid var(--border);
  background: var(--bg3);
  text-decoration: none;
  transition: all .2s;
  group: true;
}
.contact-link:hover {
  border-color: var(--cyan);
  box-shadow: 0 0 20px rgba(0,255,204,.08);
  transform: translateX(4px);
}
.contact-link-icon {
  font-size: 1.2rem;
  width: 2.5rem; text-align: center;
  filter: grayscale(1);
  transition: filter .2s;
}
.contact-link:hover .contact-link-icon { filter: none; }
.contact-link-info { flex: 1; }
.contact-link-label {
  font-family: var(--orb);
  font-size: .6rem;
  font-weight: 700;
  letter-spacing: .2em;
  color: var(--dim);
  text-transform: uppercase;
}
.contact-link-val {
  font-family: var(--mono);
  font-size: .78rem;
  color: var(--white);
  margin-top: .2rem;
}
.contact-link-arrow {
  font-size: .8rem;
  color: var(--dim);
  transition: color .2s, transform .2s;
}
.contact-link:hover .contact-link-arrow {
  color: var(--cyan);
  transform: translateX(4px);
}

/* ── FOOTER ── */
footer {
  padding: 2rem 6rem;
  border-top: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-family: var(--mono);
  font-size: .65rem;
  color: var(--dim);
  letter-spacing: .1em;
  background: var(--bg);
}
.footer-logo { color: var(--cyan); text-shadow: 0 0 8px var(--cyan); }
.footer-quote { color: #333; font-style: italic; }

/* ── SCROLL REVEAL ── */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity .7s ease, transform .7s ease;
}
.reveal.visible {
  opacity: 1;
  transform: none;
}

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: var(--cyan); }

a { cursor: none; }
</style>
</head>
<body>

<!-- CURSOR -->
<div id="cursor"></div>

<!-- NAV -->
<nav>
  <div class="nav-logo">VS // DEV</div>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#stack">Stack</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <div class="nav-status">
    <div class="pulse"></div>
    OPEN TO WORK
  </div>
</nav>

<!-- HERO -->
<section id="hero">
  <div class="hero-grid-bg"></div>
  <div class="hero-tag">FULL STACK DEVELOPER // SYSTEM ARCHITECT // DSA GRINDER</div>
  <h1 class="hero-name">
    <span class="line1"><span class="glitch" data-text="VAIBHAV">VAIBHAV</span></span>
    <span class="line2">SAINI</span>
  </h1>
  <div class="hero-sub">
    <span class="sep">&gt;</span>
    <span class="hero-typed" id="typed"></span>
  </div>
  <div class="hero-stats">
    <div class="stat-box">
      <span class="stat-num">600+</span>
      <span class="stat-label">DSA Problems</span>
    </div>
    <div class="stat-box">
      <span class="stat-num">4</span>
      <span class="stat-label">Live Projects</span>
    </div>
    <div class="stat-box">
      <span class="stat-num">0</span>
      <span class="stat-label">Prod Outages</span>
    </div>
    <div class="stat-box">
      <span class="stat-num">10K+</span>
      <span class="stat-label">Lines of TypeScript</span>
    </div>
  </div>
  <div class="hero-cta">
    <a href="#projects" class="btn btn-primary">VIEW PROJECTS</a>
    <a href="mailto:vaibhavsaini1529@gmail.com" class="btn btn-outline">HIRE ME</a>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    SCROLL
  </div>
</section>

<!-- ABOUT -->
<section id="about">
  <div class="section-tag">01 // IDENTITY</div>
  <h2 class="section-title">$ <span>whoami</span></h2>
  <div class="about-grid reveal">
    <div class="terminal-box">
      <div class="terminal-header">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
        <span style="margin-left:.4rem">vaibhav.ts</span>
      </div>
      <div class="terminal-body">
        <div><span class="t-key">const</span> <span style="color:var(--lime)">vaibhav</span><span style="color:#888">:</span> <span style="color:var(--amber)">Developer</span> = {</div>
        <div style="padding-left:1.2rem"><span class="t-key">role</span>: <span class="t-str">"Full Stack Developer"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-key">base</span>: <span class="t-str">"Moradabad, UP, India"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-key">degree</span>: <span class="t-str">"B.Tech CSE — MIT Moradabad"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-key">current</span>: <span class="t-str">"SDE Intern @ TechBuzz Ideas"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-key">obsessed_with</span>: [</div>
        <div style="padding-left:2.4rem"><span class="t-arr">"WebSockets"</span>, <span class="t-arr">"Prisma ORM"</span>,</div>
        <div style="padding-left:2.4rem"><span class="t-arr">"Next.js App Router"</span>, <span class="t-arr">"Type safety"</span></div>
        <div style="padding-left:1.2rem">],</div>
        <div style="padding-left:1.2rem"><span class="t-key">dsa_grind</span>: <span class="t-str">"600+ problems solved"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-key">superpower</span>: <span class="t-str">"Zero prod outages 🔒"</span>,</div>
        <div style="padding-left:1.2rem"><span class="t-comment">// cut API latency 30% before standup ☕</span></div>
        <div>}</div>
      </div>
    </div>
    <div>
      <table class="identity-table">
        <tr>
          <td class="id-key">NAME</td>
          <td class="id-arrow">→</td>
          <td class="id-val">Vaibhav Saini</td>
        </tr>
        <tr>
          <td class="id-key">ROLE</td>
          <td class="id-arrow">→</td>
          <td class="id-val">Full Stack Developer</td>
        </tr>
        <tr>
          <td class="id-key">DEGREE</td>
          <td class="id-arrow">→</td>
          <td class="id-val">B.Tech CSE (Data Science)<br/>MIT Moradabad / AKTU · 2026</td>
        </tr>
        <tr>
          <td class="id-key">CURRENTLY</td>
          <td class="id-arrow">→</td>
          <td class="id-val">SDE Intern @ TechBuzz Ideas LLP<br/>Apr 2026 → Present</td>
        </tr>
        <tr>
          <td class="id-key">WEAPON</td>
          <td class="id-arrow">→</td>
          <td class="id-val">Next.js + TypeScript + GraphQL + Prisma</td>
        </tr>
        <tr>
          <td class="id-key">SEEKING</td>
          <td class="id-arrow">→</td>
          <td class="id-val" style="color:var(--lime)">🟢 Full-time + Internship — Immediate</td>
        </tr>
      </table>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-tag">02 // BATTLE LOG</div>
  <h2 class="section-title">Work <span>Experience</span></h2>
  <div class="exp-list reveal">

    <div class="exp-item">
      <div style="display:flex;flex-direction:column;align-items:flex-end;padding-top:.35rem;gap:0">
        <div class="exp-date">APR 2026<br/>PRESENT</div>
        <div style="width:1px;flex:1;background:linear-gradient(to bottom, var(--cyan), var(--border));margin-top:.5rem;margin-right:0;align-self:center"></div>
      </div>
      <div>
        <div class="exp-card">
          <div class="exp-company">TECHBUZZ IDEAS LLP</div>
          <div class="exp-role">Full Stack Developer Intern</div>
          <ul class="exp-bullets">
            <li>Built <strong>3+ production full-stack apps</strong> with Next.js, TypeScript & PostgreSQL, delivering RESTful API integrations for real client workloads.</li>
            <li>Engineered reusable React component libraries with <strong>JWT authentication + SSR pipelines</strong>, cutting API response time by <strong>~30%</strong> across 5+ modules.</li>
            <li>Maintained <strong>&gt;95% on-time delivery</strong> across 4 agile sprint cycles via CI/CD, code reviews, and systematic debugging.</li>
          </ul>
        </div>
      </div>
    </div>

    <div class="exp-item">
      <div style="display:flex;flex-direction:column;align-items:flex-end;padding-top:.35rem;gap:0">
        <div class="exp-date">JUL 2025<br/>AUG 2025</div>
        <div style="width:1px;flex:1;background:linear-gradient(to bottom, var(--cyan), var(--border));margin-top:.5rem;align-self:center"></div>
      </div>
      <div>
        <div class="exp-card">
          <div class="exp-company">EXPLORIN</div>
          <div class="exp-role">Full Stack Developer Intern</div>
          <ul class="exp-bullets">
            <li>Revamped <strong>8+ React/Node.js components</strong>, implementing data-fetching patterns that reduced API latency by <strong>~25%</strong>.</li>
            <li>Boosted <strong>Core Web Vitals</strong> via memoization and React Query caching across 3 high-traffic user flows.</li>
            <li>Integrated <strong>OAuth 2.0 authentication + RBAC</strong> across 6+ protected routes; implemented SSR/SSG to reduce TTFB.</li>
          </ul>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-tag">03 // ARSENAL</div>
  <h2 class="section-title">Live <span>Projects</span></h2>
  <div class="projects-grid reveal">

    <div class="project-card">
      <div class="project-accent"></div>
      <div class="project-num">01</div>
      <div class="project-inner">
        <span class="project-emoji">⚡</span>
        <div class="project-name">AUCTIONARY</div>
        <div class="project-desc">Real-Time Auction Engine</div>
        <div class="project-metrics">
          <span class="metric-pill cyan">50+ Concurrent Bidders</span>
          <span class="metric-pill amber">sub-100ms Sync</span>
          <span class="metric-pill lime">Zero Race Conditions</span>
        </div>
        <div class="project-stack">Next.js · TypeScript · WebSocket · GraphQL Subscriptions · Prisma ORM · Supabase · TailwindCSS</div>
        <div class="project-links">
          <a class="project-link pl-code" href="https://github.com/Vaibhav-1529/Auctionary" target="_blank">[ CODE ]</a>
          <a class="project-link pl-live" href="https://auctionary-alpha.vercel.app/" target="_blank">LIVE ↗</a>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-accent"></div>
      <div class="project-num">02</div>
      <div class="project-inner">
        <span class="project-emoji">💼</span>
        <div class="project-name">JOBZZ</div>
        <div class="project-desc">Multi-Role Recruitment Platform</div>
        <div class="project-metrics">
          <span class="metric-pill cyan">3 User Roles</span>
          <span class="metric-pill amber">+35% Dashboard Perf</span>
          <span class="metric-pill lime">10+ Live States</span>
        </div>
        <div class="project-stack">Next.js · TypeScript · GraphQL · Prisma ORM · PostgreSQL · Radix UI · TailwindCSS</div>
        <div class="project-links">
          <a class="project-link pl-code" href="https://github.com/Vaibhav-1529/jobzz" target="_blank">[ CODE ]</a>
          <a class="project-link pl-live" href="https://jobzz.vercel.app/" target="_blank">LIVE ↗</a>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-accent"></div>
      <div class="project-num">03</div>
      <div class="project-inner">
        <span class="project-emoji">📄</span>
        <div class="project-name">PDF VIEWER APP</div>
        <div class="project-desc">Secure Document Management System</div>
        <div class="project-metrics">
          <span class="metric-pill cyan">3-Tier Access Control</span>
          <span class="metric-pill amber">-40% Load Time</span>
          <span class="metric-pill red">bcrypt Share Links</span>
        </div>
        <div class="project-stack">Next.js · TypeScript · GraphQL · AWS S3 · Supabase · Clerk · TailwindCSS</div>
        <div class="project-links">
          <a class="project-link pl-code" href="http://github.com/VaibhavSaini0/Pdf-Viewer" target="_blank">[ CODE ]</a>
          <a class="project-link pl-live" href="https://jobzz.vercel.app/" target="_blank">LIVE ↗</a>
        </div>
      </div>
    </div>

    <div class="project-card">
      <div class="project-accent"></div>
      <div class="project-num">04</div>
      <div class="project-inner">
        <span class="project-emoji">🗄️</span>
        <div class="project-name">SQL SANDBOX</div>
        <div class="project-desc">Multi-User SQL Execution Engine</div>
        <div class="project-metrics">
          <span class="metric-pill cyan">20+ Concurrent Users</span>
          <span class="metric-pill lime">100% Session Restore</span>
          <span class="metric-pill amber">Zero Data Leaks</span>
        </div>
        <div class="project-stack">React.js · TypeScript · Node.js · Express.js · PostgreSQL · MongoDB · Clerk</div>
        <div class="project-links">
          <a class="project-link pl-code" href="https://github.com/VaibhavSaini0/SQL-Sandbox" target="_blank">[ CODE ]</a>
          <a class="project-link pl-live" href="https://sql-sandbox-plum.vercel.app/" target="_blank">LIVE ↗</a>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- ACHIEVEMENTS -->
<section>
  <div class="section-tag">04 // METRICS</div>
  <h2 class="section-title">By The <span>Numbers</span></h2>
  <div class="ach-grid reveal">
    <div class="ach-cell">
      <span class="ach-big">600+</span>
      <span class="ach-label">DSA Problems<br/>LeetCode · GFG · HackerRank</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big amber">4</span>
      <span class="ach-label">Production Apps<br/>All Live on Vercel</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big lime">0</span>
      <span class="ach-label">Production Outages<br/>Across All Projects</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big red">30%</span>
      <span class="ach-label">API Latency Cut<br/>@ TechBuzz Ideas LLP</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big amber">35%</span>
      <span class="ach-label">Dashboard Perf Boost<br/>via Prisma Query Tuning</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big">100ms</span>
      <span class="ach-label">WebSocket Sync Target<br/>50+ Concurrent Users</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big lime">5+</span>
      <span class="ach-label">Junior Devs Mentored<br/>Debugging & Agile</span>
    </div>
    <div class="ach-cell">
      <span class="ach-big red">10K+</span>
      <span class="ach-label">Lines of TypeScript<br/>Shipped to Production</span>
    </div>
  </div>
</section>

<!-- TECH STACK -->
<section id="stack">
  <div class="section-tag">05 // ARMORY</div>
  <h2 class="section-title">Tech <span>Stack</span></h2>
  <div class="stack-groups reveal">
    <div>
      <div class="stack-group-label">Languages</div>
      <div class="stack-pills">
        <span class="stack-pill hot">TypeScript</span>
        <span class="stack-pill hot">JavaScript ES6+</span>
        <span class="stack-pill">C++</span>
        <span class="stack-pill">Python</span>
        <span class="stack-pill">SQL</span>
        <span class="stack-pill">HTML5</span>
        <span class="stack-pill">CSS3</span>
      </div>
    </div>
    <div>
      <div class="stack-group-label">Frontend</div>
      <div class="stack-pills">
        <span class="stack-pill hot">React.js</span>
        <span class="stack-pill hot">Next.js</span>
        <span class="stack-pill hot">Tailwind CSS</span>
        <span class="stack-pill">Shadcn/UI</span>
        <span class="stack-pill">Radix UI</span>
        <span class="stack-pill">React Query</span>
        <span class="stack-pill">Redux</span>
      </div>
    </div>
    <div>
      <div class="stack-group-label">Backend & APIs</div>
      <div class="stack-pills">
        <span class="stack-pill hot">Node.js</span>
        <span class="stack-pill hot">Express.js</span>
        <span class="stack-pill hot">GraphQL</span>
        <span class="stack-pill hot">WebSockets</span>
        <span class="stack-pill">RESTful APIs</span>
        <span class="stack-pill">JWT</span>
        <span class="stack-pill">OAuth 2.0</span>
        <span class="stack-pill">RBAC</span>
      </div>
    </div>
    <div>
      <div class="stack-group-label">Databases & ORMs</div>
      <div class="stack-pills">
        <span class="stack-pill hot">PostgreSQL</span>
        <span class="stack-pill hot">MongoDB</span>
        <span class="stack-pill hot">Prisma ORM</span>
        <span class="stack-pill">MySQL</span>
        <span class="stack-pill">Supabase</span>
        <span class="stack-pill">Query Optimization</span>
      </div>
    </div>
    <div>
      <div class="stack-group-label">Cloud & DevOps</div>
      <div class="stack-pills">
        <span class="stack-pill hot">AWS S3</span>
        <span class="stack-pill hot">Vercel</span>
        <span class="stack-pill">Docker</span>
        <span class="stack-pill">Git</span>
        <span class="stack-pill">CI/CD</span>
        <span class="stack-pill">Postman</span>
        <span class="stack-pill">Cloudinary</span>
        <span class="stack-pill">Clerk</span>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-tag">06 // CONNECT</div>
  <h2 class="section-title">Open To <span>Work</span></h2>
  <div class="contact-grid reveal">
    <div>
      <pre class="contact-ascii"><span class="c-hl">╔══════════════════════════════════════╗</span>
<span class="c-hl">║</span>                                      <span class="c-hl">║</span>
<span class="c-hl">║</span>  SEEKING  <span class="c-am">→</span>  SDE / Full Stack /       <span class="c-hl">║</span>
<span class="c-hl">║</span>             Frontend / Solutions Eng  <span class="c-hl">║</span>
<span class="c-hl">║</span>                                      <span class="c-hl">║</span>
<span class="c-hl">║</span>  TYPE     <span class="c-am">→</span>  Full-time + Internship   <span class="c-hl">║</span>
<span class="c-hl">║</span>                                      <span class="c-hl">║</span>
<span class="c-hl">║</span>  WHERE    <span class="c-am">→</span>  Remote / Hybrid /         <span class="c-hl">║</span>
<span class="c-hl">║</span>             Delhi NCR / Moradabad     <span class="c-hl">║</span>
<span class="c-hl">║</span>                                      <span class="c-hl">║</span>
<span class="c-hl">║</span>  NOTICE   <span class="c-am">→</span>  <span class="c-lm">Immediate joiner ⚡</span>       <span class="c-hl">║</span>
<span class="c-hl">║</span>                                      <span class="c-hl">║</span>
<span class="c-hl">╚══════════════════════════════════════╝</span>

  <span style="color:#333">// Ship fast. Break nothing. Sleep later.</span></pre>
    </div>
    <div class="contact-links">
      <a class="contact-link" href="mailto:vaibhavsaini1529@gmail.com">
        <span class="contact-link-icon">✉️</span>
        <div class="contact-link-info">
          <div class="contact-link-label">Email</div>
          <div class="contact-link-val">vaibhavsaini1529@gmail.com</div>
        </div>
        <span class="contact-link-arrow">→</span>
      </a>
      <a class="contact-link" href="https://linkedin.com/in/vaibhav-saini1529" target="_blank">
        <span class="contact-link-icon">💼</span>
        <div class="contact-link-info">
          <div class="contact-link-label">LinkedIn</div>
          <div class="contact-link-val">vaibhav-saini1529</div>
        </div>
        <span class="contact-link-arrow">→</span>
      </a>
      <a class="contact-link" href="https://github.com/VaibhavSaini0" target="_blank">
        <span class="contact-link-icon">⌥</span>
        <div class="contact-link-info">
          <div class="contact-link-label">GitHub</div>
          <div class="contact-link-val">VaibhavSaini0</div>
        </div>
        <span class="contact-link-arrow">→</span>
      </a>
      <a class="contact-link" href="tel:+919389996780">
        <span class="contact-link-icon">📞</span>
        <div class="contact-link-info">
          <div class="contact-link-label">Phone</div>
          <div class="contact-link-val">+91 93899 96780</div>
        </div>
        <span class="contact-link-arrow">→</span>
      </a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <span class="footer-logo">VAIBHAV SAINI // VS_DEV</span>
  <span class="footer-quote">"Ship fast. Break nothing. Sleep later."</span>
  <span>© 2026 // BUILT WITH TS + OBSESSION</span>
</footer>

<script>
/* ── CURSOR TRAIL ── */
const cursor = document.getElementById('cursor');
let mouseX = 0, mouseY = 0;
const trails = [];
const TRAIL_COUNT = 18;
const colors = ['#00ffcc','#7ffe00','#ffd700','#00ffcc','#00ffcc'];

for (let i = 0; i < TRAIL_COUNT; i++) {
  const d = document.createElement('div');
  d.className = 'trail-dot';
  const size = Math.max(2, 10 - i * 0.45);
  d.style.cssText = `width:${size}px;height:${size}px;opacity:${(1 - i/TRAIL_COUNT)*0.7};background:${colors[i % colors.length]};box-shadow:0 0 ${size*2}px ${colors[i%colors.length]}`;
  document.body.appendChild(d);
  trails.push({ el: d, x: 0, y: 0 });
}

document.addEventListener('mousemove', e => {
  mouseX = e.clientX;
  mouseY = e.clientY;
  cursor.style.left = mouseX + 'px';
  cursor.style.top  = mouseY + 'px';
});

document.querySelectorAll('a, button, .project-card, .ach-cell, .stack-pill').forEach(el => {
  el.addEventListener('mouseenter', () => cursor.classList.add('hover'));
  el.addEventListener('mouseleave', () => cursor.classList.remove('hover'));
});

function animateTrails() {
  let x = mouseX, y = mouseY;
  trails.forEach((t, i) => {
    const prev = i === 0 ? { x: mouseX, y: mouseY } : trails[i - 1];
    t.x += (prev.x - t.x) * 0.35;
    t.y += (prev.y - t.y) * 0.35;
    t.el.style.left = t.x + 'px';
    t.el.style.top  = t.y + 'px';
  });
  requestAnimationFrame(animateTrails);
}
animateTrails();

/* ── TYPING EFFECT ── */
const phrases = [
  'Next.js + TypeScript + GraphQL',
  'Building systems that scale',
  '600+ DSA problems solved',
  'sub-100ms WebSocket sync',
  'Zero production outages 🔒',
  'Immediate joiner — hire me ⚡',
];
let pi = 0, ci = 0, deleting = false;
const el = document.getElementById('typed');
function type() {
  const phrase = phrases[pi];
  if (!deleting) {
    el.textContent = phrase.slice(0, ++ci);
    if (ci === phrase.length) { deleting = true; setTimeout(type, 2000); return; }
  } else {
    el.textContent = phrase.slice(0, --ci);
    if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
  }
  setTimeout(type, deleting ? 35 : 65);
}
type();

/* ── SCROLL REVEAL ── */
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.12 });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

/* ── STAT COUNTER ── */
function animateCount(el, target, suffix='') {
  let current = 0;
  const step = target / 60;
  const timer = setInterval(() => {
    current = Math.min(current + step, target);
    el.textContent = (target >= 1000 ? Math.round(current/1000)+'K' : Math.round(current)) + suffix;
    if (current >= target) clearInterval(timer);
  }, 20);
}
const statObserver = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (!e.isIntersecting) return;
    const nums = e.target.querySelectorAll('.ach-big');
    nums.forEach(n => {
      const txt = n.textContent;
      if (txt.includes('K')) animateCount(n, parseInt(txt)*1000, 'K+');
      else if (txt.includes('+')) animateCount(n, parseInt(txt), '+');
      else if (txt.includes('%')) animateCount(n, parseInt(txt), '%');
      else if (txt === '0') { /* keep */ }
    });
    statObserver.unobserve(e.target);
  });
}, { threshold: 0.3 });
document.querySelectorAll('.ach-grid').forEach(el => statObserver.observe(el));
</script>
</body>
</html>
