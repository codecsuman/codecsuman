<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Suman Jhanp — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --surface: #111118;
    --surface2: #16161f;
    --border: #1e1e2e;
    --accent: #7c3aed;
    --accent2: #06b6d4;
    --accent3: #10b981;
    --gold: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --dim: #334155;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 60% 40% at 20% 20%, rgba(124,58,237,0.08) 0%, transparent 60%),
      radial-gradient(ellipse 50% 50% at 80% 80%, rgba(6,182,212,0.06) 0%, transparent 60%),
      radial-gradient(ellipse 40% 60% at 50% 50%, rgba(16,185,129,0.04) 0%, transparent 70%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* HEADER */
  .header {
    text-align: center;
    padding: 60px 0 40px;
    animation: fadeUp 0.6s ease both;
  }

  .header-name {
    font-size: clamp(2.4rem, 6vw, 4rem);
    font-weight: 800;
    letter-spacing: -0.02em;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 70%, var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1.1;
    margin-bottom: 8px;
  }

  .header-role {
    font-family: 'JetBrains Mono', monospace;
    color: var(--accent2);
    font-size: 0.95rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 32px;
    opacity: 0.85;
  }

  /* BADGE LINKS */
  .badge-row {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
    margin-bottom: 16px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 8px 14px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.03em;
    text-decoration: none;
    transition: transform 0.2s, box-shadow 0.2s, opacity 0.2s;
    border: 1px solid rgba(255,255,255,0.08);
  }

  .badge:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0,0,0,0.4);
    opacity: 0.9;
  }

  .badge-netlify { background: linear-gradient(135deg, #1a1a2e, #2d1b69); color: #a78bfa; }
  .badge-vercel  { background: linear-gradient(135deg, #111111, #1e1e1e); color: #e2e8f0; }
  .badge-resume  { background: linear-gradient(135deg, #1e3a8a, #1e40af); color: #93c5fd; }
  .badge-github  { background: linear-gradient(135deg, #181717, #242424); color: #e2e8f0; }
  .badge-leetcode{ background: linear-gradient(135deg, #1a1000, #2d1f00); color: #fbbf24; }
  .badge-linkedin{ background: linear-gradient(135deg, #0a1929, #0a3d6b); color: #60a5fa; }

  .badge svg { width: 14px; height: 14px; flex-shrink: 0; }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--border), transparent);
    margin: 40px 0;
  }

  /* SECTION */
  .section {
    margin-bottom: 48px;
    animation: fadeUp 0.6s ease both;
  }

  .section-title {
    font-size: 1.3rem;
    font-weight: 700;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    color: #fff;
  }

  .section-title .emoji { font-size: 1.2rem; }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
    margin-left: 8px;
  }

  /* CODE BLOCK */
  .code-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.82rem;
    line-height: 1.7;
  }

  .code-header {
    background: var(--surface2);
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid var(--border);
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }

  .code-lang {
    margin-left: auto;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.05em;
  }

  .code-body {
    padding: 20px 24px;
    overflow-x: auto;
  }

  .kw { color: #c792ea; }
  .fn { color: #82aaff; }
  .str { color: #c3e88d; }
  .prop { color: #f78c6c; }
  .bracket { color: var(--muted); }
  .comment { color: #546e7a; font-style: italic; }
  .arr-item { color: #89ddff; }

  /* TECH GRID */
  .tech-section { margin-bottom: 28px; }

  .tech-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 12px;
    padding-left: 2px;
  }

  .tech-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .tech-pill {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 6px 12px;
    border-radius: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.73rem;
    font-weight: 600;
    border: 1px solid rgba(255,255,255,0.07);
    transition: transform 0.15s, box-shadow 0.15s;
    cursor: default;
  }

  .tech-pill:hover {
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
  }

  /* pill colors */
  .p-java     { background: #2d1700; color: #fb923c; border-color: #431e00; }
  .p-c        { background: #001a2d; color: #60a5fa; border-color: #002d4a; }
  .p-js       { background: #2d2500; color: #fde047; border-color: #433600; }
  .p-ts       { background: #001a3d; color: #60a5fa; border-color: #002d5f; }
  .p-python   { background: #001f2d; color: #4ade80; border-color: #002d3d; }
  .p-html     { background: #2d0f00; color: #f97316; border-color: #431600; }
  .p-css      { background: #00112d; color: #818cf8; border-color: #001a43; }
  .p-react    { background: #001a2d; color: #38bdf8; border-color: #002d4a; }
  .p-next     { background: #111; color: #e2e8f0; border-color: #222; }
  .p-node     { background: #001a00; color: #4ade80; border-color: #002d00; }
  .p-express  { background: #111; color: #94a3b8; border-color: #222; }
  .p-mongo    { background: #001a00; color: #4ade80; border-color: #002d00; }
  .p-mysql    { background: #001433; color: #60a5fa; border-color: #001f4d; }
  .p-pandas   { background: #08001a; color: #a78bfa; border-color: #11002b; }
  .p-numpy    { background: #001433; color: #38bdf8; border-color: #001f4d; }
  .p-plot     { background: #001433; color: #818cf8; border-color: #001f4d; }
  .p-seaborn  { background: #001433; color: #67e8f9; border-color: #001f4d; }
  .p-jupyter  { background: #2d1000; color: #fb923c; border-color: #431700; }
  .p-git      { background: #2d0000; color: #f87171; border-color: #430000; }
  .p-postman  { background: #2d1000; color: #fb923c; border-color: #431700; }
  .p-vercel   { background: #111; color: #e2e8f0; border-color: #222; }
  .p-netlify  { background: #00211d; color: #2dd4bf; border-color: #003329; }
  .p-render   { background: #00211d; color: #34d399; border-color: #003329; }

  /* PROJECTS TABLE */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 16px;
  }

  .project-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    transition: transform 0.2s, border-color 0.2s, box-shadow 0.2s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
  }

  .project-card.c1::before { background: linear-gradient(90deg, var(--accent), var(--accent2)); }
  .project-card.c2::before { background: linear-gradient(90deg, var(--accent2), var(--accent3)); }
  .project-card.c3::before { background: linear-gradient(90deg, var(--accent3), var(--gold)); }

  .project-card:hover {
    transform: translateY(-4px);
    border-color: rgba(124,58,237,0.3);
    box-shadow: 0 12px 32px rgba(0,0,0,0.4);
  }

  .project-icon { font-size: 1.8rem; margin-bottom: 10px; }
  .project-name { font-size: 1rem; font-weight: 700; color: #fff; margin-bottom: 8px; }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
    margin-bottom: 12px;
  }

  .stack-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.65rem;
    padding: 2px 7px;
    border-radius: 4px;
    background: rgba(255,255,255,0.05);
    color: var(--muted);
    border: 1px solid var(--border);
  }

  .project-features {
    list-style: none;
    margin-bottom: 16px;
  }

  .project-features li {
    font-size: 0.78rem;
    color: #94a3b8;
    padding: 2px 0;
    padding-left: 12px;
    position: relative;
    font-family: 'JetBrains Mono', monospace;
  }

  .project-features li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--accent2);
    font-size: 0.65rem;
    top: 3px;
  }

  .project-link {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent2);
    text-decoration: none;
    border: 1px solid rgba(6,182,212,0.3);
    padding: 5px 12px;
    border-radius: 6px;
    transition: background 0.15s, color 0.15s;
  }

  .project-link:hover {
    background: rgba(6,182,212,0.1);
    color: #fff;
  }

  /* DATA ANALYTICS TREE */
  .tree-block {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 24px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    line-height: 1.8;
    overflow-x: auto;
  }

  .tree-root { color: var(--accent2); font-weight: 700; }
  .tree-line { color: var(--dim); }
  .tree-icon { margin-right: 4px; }
  .tree-text { color: #94a3b8; }
  .tree-arrow { color: var(--accent3); }

  /* PROGRESS TABLE */
  .progress-table {
    width: 100%;
    border-collapse: collapse;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
  }

  .progress-table th {
    text-align: left;
    padding: 10px 16px;
    background: var(--surface2);
    color: var(--muted);
    font-size: 0.68rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    border-bottom: 1px solid var(--border);
  }

  .progress-table td {
    padding: 10px 16px;
    border-bottom: 1px solid rgba(30,30,46,0.5);
    color: #94a3b8;
  }

  .progress-table tr:last-child td { border-bottom: none; }

  .progress-table tr:hover td { background: rgba(255,255,255,0.02); }

  .status-done {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    background: rgba(16,185,129,0.1);
    color: #34d399;
    border: 1px solid rgba(16,185,129,0.25);
    padding: 2px 10px;
    border-radius: 20px;
    font-size: 0.68rem;
    font-weight: 700;
  }

  /* STATS CARDS */
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 14px;
    margin-bottom: 24px;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 18px;
    text-align: center;
    transition: transform 0.15s;
  }

  .stat-card:hover { transform: translateY(-2px); }

  .stat-num {
    font-size: 2rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 6px;
  }

  .stat-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    color: var(--muted);
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  /* LEETCODE */
  .lc-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
  }

  .lc-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
    flex-wrap: gap;
    gap: 12px;
  }

  .lc-title {
    font-size: 1rem;
    font-weight: 700;
    color: var(--gold);
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .lc-link {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--gold);
    text-decoration: none;
    border: 1px solid rgba(245,158,11,0.3);
    padding: 5px 12px;
    border-radius: 6px;
    transition: background 0.15s;
  }

  .lc-link:hover { background: rgba(245,158,11,0.1); }

  .progress-bar-wrap {
    margin-bottom: 16px;
  }

  .progress-bar-label {
    display: flex;
    justify-content: space-between;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.72rem;
    color: var(--muted);
    margin-bottom: 6px;
  }

  .progress-bar {
    height: 8px;
    background: var(--surface2);
    border-radius: 4px;
    overflow: hidden;
    border: 1px solid var(--border);
  }

  .progress-fill {
    height: 100%;
    border-radius: 4px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    animation: fillBar 1.2s ease both 0.3s;
    transform-origin: left;
  }

  @keyframes fillBar {
    from { width: 0 !important; }
  }

  .topics-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
  }

  .topic-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.68rem;
    padding: 4px 10px;
    border-radius: 5px;
    background: rgba(124,58,237,0.12);
    color: #a78bfa;
    border: 1px solid rgba(124,58,237,0.2);
  }

  /* CONNECT */
  .connect-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    justify-content: center;
  }

  .connect-btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.78rem;
    font-weight: 600;
    text-decoration: none;
    border: 1px solid rgba(255,255,255,0.1);
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .connect-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.4);
  }

  .btn-gh   { background: #181717; color: #e2e8f0; border-color: #333; }
  .btn-lc   { background: #1a1000; color: #fbbf24; border-color: #2d1f00; }
  .btn-li   { background: #0a1929; color: #60a5fa; border-color: #0a3d6b; }
  .btn-port { background: #1a0a2e; color: #a78bfa; border-color: #2d1b69; }

  /* FOOTER */
  .footer {
    text-align: center;
    padding: 32px 0 0;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.75rem;
    color: var(--dim);
    border-top: 1px solid var(--border);
    margin-top: 48px;
  }

  .star-note {
    text-align: center;
    font-family: 'JetBrains Mono', monospace;
    font-size: 0.8rem;
    color: var(--gold);
    margin-top: 32px;
    padding: 12px 24px;
    border: 1px solid rgba(245,158,11,0.2);
    border-radius: 8px;
    background: rgba(245,158,11,0.05);
    display: inline-block;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .section:nth-child(1) { animation-delay: 0.1s; }
  .section:nth-child(2) { animation-delay: 0.2s; }
  .section:nth-child(3) { animation-delay: 0.3s; }
  .section:nth-child(4) { animation-delay: 0.4s; }
  .section:nth-child(5) { animation-delay: 0.5s; }
  .section:nth-child(6) { animation-delay: 0.6s; }

  /* SVG ICONS */
  .ico { display: inline-block; vertical-align: middle; }

  @media (max-width: 600px) {
    .badge-row { gap: 7px; }
    .badge { font-size: 0.68rem; padding: 6px 10px; }
    .projects-grid { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: repeat(2,1fr); }
  }
</style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="header">
    <div class="header-name">Suman Jhanp</div>
    <div class="header-role">💼 Backend-Focused Full Stack Developer · Kolkata, India</div>

    <div class="badge-row">
      <a href="https://sumanjhanp.netlify.app/" target="_blank" class="badge badge-netlify">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M16.934 8.519a1.044 1.044 0 0 1 .303.23l2.349-1.045-2.192-2.171-.46 2.986zM12.06 6.546a1.305 1.305 0 0 1 .209.574l3.497 1.068 .46-2.985-2.549-.507-1.617 1.85zM21.57 15.772l-4.928-1.105a1.33 1.33 0 0 1-.26.41l1.258 4.787 3.93-4.092zm-1.798-4.952l-2.385 1.06a1.315 1.315 0 0 1-.107.44l3.042 1.589.776-1.055-1.326-2.034zM9.548 6.786l-3.43-.681 1.806 3.29 2.12-1.545a1.293 1.293 0 0 1-.496-1.064zm-5.646 8.82l1.364 5.19L8.58 16.9a1.327 1.327 0 0 1-.08-.658l-4.598-1.636zm6.39 4.436L6.98 23.83l4.555-1.437-.576-2.35zm-3.464-1.54l-3.81 3.906 5.322-1.679-.61-1.8a1.318 1.318 0 0 1-.902-.427zm6.39.44l1.814 2.33 3.535-3.679-3.502-.785a1.33 1.33 0 0 1-1.847 2.133zm-2.144.935l.617 2.52 2.066-2.65-1.292-1.66a1.315 1.315 0 0 1-1.39 1.79z"/></svg>
        🌐 Portfolio · Netlify
      </a>
      <a href="https://portfolio-codecsumans-projects.vercel.app" target="_blank" class="badge badge-vercel">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M24 22.525H0l12-21.05 12 21.05z"/></svg>
        🚀 Portfolio · Vercel
      </a>
      <a href="resume.pdf" class="badge badge-resume">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8l-6-6zm-1 1.5L18.5 9H13V3.5zM6 20V4h5v7h7v9H6z"/></svg>
        📄 Resume
      </a>
      <a href="https://github.com/codecsuman" target="_blank" class="badge badge-github">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
        codecsuman
      </a>
      <a href="https://leetcode.com/u/sumanjhanp1/" target="_blank" class="badge badge-leetcode">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
        sumanjhanp1
      </a>
      <a href="https://www.linkedin.com/" target="_blank" class="badge badge-linkedin">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
    </div>
  </div>

  <div class="divider"></div>

  <!-- ABOUT ME -->
  <div class="section">
    <div class="section-title"><span class="emoji">🌟</span> About Me</div>
    <div class="code-block">
      <div class="code-header">
        <span class="dot dot-r"></span><span class="dot dot-y"></span><span class="dot dot-g"></span>
        <span class="code-lang">javascript</span>
      </div>
      <div class="code-body">
        <pre><span class="kw">const</span> <span class="fn">suman</span> <span class="bracket">= {</span>
  <span class="prop">education</span> : <span class="str">"🎓 B.Tech in Information Technology (2022–2026)"</span>,
  <span class="prop">college</span>   : <span class="str">"🏛️ RCC Institute of Information Technology, Kolkata"</span>,
  <span class="prop">cgpa</span>      : <span class="str">"📈 7.2"</span>,
  <span class="prop">location</span>  : <span class="str">"📍 Kolkata, India"</span>,
  <span class="prop">role</span>      : <span class="str">"💼 Backend-Focused Full Stack Developer"</span>,
  <span class="prop">stack</span>     : <span class="bracket">[</span><span class="arr-item">"⚙️ MERN"</span>, <span class="arr-item">"Node.js"</span>, <span class="arr-item">"Express"</span>, <span class="arr-item">"MongoDB"</span>, <span class="arr-item">"MySQL"</span><span class="bracket">]</span>,
  <span class="prop">analytics</span> : <span class="bracket">[</span><span class="arr-item">"📊 Python"</span>, <span class="arr-item">"Pandas"</span>, <span class="arr-item">"NumPy"</span>, <span class="arr-item">"Matplotlib"</span>, <span class="arr-item">"Seaborn"</span><span class="bracket">]</span>,
  <span class="prop">cs_core</span>   : <span class="bracket">[</span><span class="arr-item">"🧠 DSA"</span>, <span class="arr-item">"DBMS"</span>, <span class="arr-item">"OS"</span>, <span class="arr-item">"OOP"</span><span class="bracket">]</span>,
  <span class="prop">deployed</span>  : <span class="bracket">[</span><span class="arr-item">"☁️ Netlify"</span>, <span class="arr-item">"Vercel"</span>, <span class="arr-item">"Render"</span><span class="bracket">]</span>,
  <span class="prop">goal</span>      : <span class="str">"🎯 Build scalable systems &amp; turn raw data into meaningful insights"</span>
<span class="bracket">};</span></pre>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="section-title"><span class="emoji">🛠️</span> Tech Stack &amp; Skills</div>

    <div class="tech-section">
      <div class="tech-label">⚡ Languages</div>
      <div class="tech-grid">
        <span class="tech-pill p-java">☕ Java</span>
        <span class="tech-pill p-c">© C</span>
        <span class="tech-pill p-js">JS JavaScript</span>
        <span class="tech-pill p-ts">TS TypeScript</span>
        <span class="tech-pill p-python">🐍 Python</span>
        <span class="tech-pill p-html">HTML5</span>
        <span class="tech-pill p-css">CSS3</span>
      </div>
    </div>

    <div class="tech-section">
      <div class="tech-label">🔥 Frontend &amp; Backend</div>
      <div class="tech-grid">
        <span class="tech-pill p-react">⚛ React</span>
        <span class="tech-pill p-next">▲ Next.js</span>
        <span class="tech-pill p-node">🟢 Node.js</span>
        <span class="tech-pill p-express">Express.js</span>
      </div>
    </div>

    <div class="tech-section">
      <div class="tech-label">🗄️ Databases</div>
      <div class="tech-grid">
        <span class="tech-pill p-mongo">🍃 MongoDB</span>
        <span class="tech-pill p-mysql">🐬 MySQL</span>
      </div>
    </div>

    <div class="tech-section">
      <div class="tech-label">📊 Data Analytics</div>
      <div class="tech-grid">
        <span class="tech-pill p-pandas">🐼 Pandas</span>
        <span class="tech-pill p-numpy">🔢 NumPy</span>
        <span class="tech-pill p-plot">📈 Matplotlib</span>
        <span class="tech-pill p-seaborn">🎨 Seaborn</span>
        <span class="tech-pill p-jupyter">📓 Jupyter</span>
      </div>
    </div>

    <div class="tech-section">
      <div class="tech-label">🔧 Tools &amp; Deployment</div>
      <div class="tech-grid">
        <span class="tech-pill p-git">🔀 Git</span>
        <span class="tech-pill p-git">🐙 GitHub</span>
        <span class="tech-pill p-postman">📮 Postman</span>
        <span class="tech-pill p-vercel">▲ Vercel</span>
        <span class="tech-pill p-netlify">🌐 Netlify</span>
        <span class="tech-pill p-render">☁️ Render</span>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- PROJECTS -->
  <div class="section">
    <div class="section-title"><span class="emoji">🚀</span> Featured Projects</div>
    <div class="projects-grid">
      <div class="project-card c1">
        <div class="project-icon">🏥</div>
        <div class="project-name">Doctor Appointment System</div>
        <div class="project-stack">
          <span class="stack-tag">MERN</span><span class="stack-tag">JWT</span>
          <span class="stack-tag">Stripe</span><span class="stack-tag">Razorpay</span>
        </div>
        <ul class="project-features">
          <li>Role-based auth (Patient / Doctor / Admin)</li>
          <li>Secure payment integration</li>
          <li>Full appointment lifecycle</li>
        </ul>
        <a href="https://github.com/codecsuman/Doctor-Appointment-Booking" target="_blank" class="project-link">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          View Repo
        </a>
      </div>

      <div class="project-card c2">
        <div class="project-icon">💼</div>
        <div class="project-name">Job Portal</div>
        <div class="project-stack">
          <span class="stack-tag">MERN</span><span class="stack-tag">Auth</span>
        </div>
        <ul class="project-features">
          <li>Resume upload &amp; authentication</li>
          <li>Job search functionality</li>
          <li>Employer dashboard</li>
        </ul>
        <a href="https://github.com/codecsuman/project-jobportal" target="_blank" class="project-link">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          View Repo
        </a>
      </div>

      <div class="project-card c3">
        <div class="project-icon">📸</div>
        <div class="project-name">Instagram Clone</div>
        <div class="project-stack">
          <span class="stack-tag">MERN</span><span class="stack-tag">Socket.IO</span>
        </div>
        <ul class="project-features">
          <li>Real-time chat &amp; notifications</li>
          <li>Fully responsive UI</li>
          <li>Post &amp; story features</li>
        </ul>
        <a href="https://github.com/codecsuman/instragram_clone" target="_blank" class="project-link">
          <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
          View Repo
        </a>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- DATA ANALYTICS -->
  <div class="section">
    <div class="section-title"><span class="emoji">📊</span> Data Analytics Portfolio</div>

    <div style="margin-bottom:16px;">
      <a href="https://github.com/codecsuman/DATA_ANALYTICS" target="_blank" class="badge badge-github" style="font-size:0.78rem; padding:10px 18px;">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
        📂 DATA_ANALYTICS — Repository
      </a>
    </div>

    <div class="tree-block">
      <div><span class="tree-root">📁 DATA_ANALYTICS/</span></div>
      <div><span class="tree-line">│</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">🐍</span><span class="tree-text">python/</span>          <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> Core Python for Analytics</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">📊</span><span class="tree-text">pandas/</span>          <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> DataFrames, Series &amp; Operations</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">🔢</span><span class="tree-text">Numpy and Data/</span>  <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> Arrays, Broadcasting &amp; Math</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">📈</span><span class="tree-text">matplotlib/</span>      <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> Charts, Plots &amp; Graphs</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">🎨</span><span class="tree-text">Seaborn/</span>         <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> Statistical Visualizations</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">📓</span><span class="tree-text">jupyternotebook/</span> <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> Interactive Notebooks</span></div>
      <div><span class="tree-line">├── </span><span class="tree-icon">🗄️</span><span class="tree-text">mysql/</span>           <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> SQL Queries &amp; Analysis</span></div>
      <div><span class="tree-line">└── </span><span class="tree-icon">📑</span><span class="tree-text">ALL_xl/</span>          <span class="tree-arrow">→</span> <span style="color:#546e7a;font-size:0.75rem;"> CSV &amp; Excel File Handling</span></div>
    </div>

    <div style="margin-top:20px;">
      <div class="section-title" style="font-size:1rem; margin-bottom:12px;"><span class="emoji">📚</span> Learning Progress</div>
      <div class="code-block">
        <div class="code-header">
          <span class="dot dot-r"></span><span class="dot dot-y"></span><span class="dot dot-g"></span>
          <span class="code-lang">progress tracker</span>
        </div>
        <table class="progress-table" style="width:100%;">
          <thead>
            <tr>
              <th>#</th>
              <th>📌 Topic</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr><td>01</td><td>Python Basics for Data Analytics</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>02</td><td>NumPy Arrays (1D &amp; 2D)</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>03</td><td>Pandas Series &amp; DataFrames</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>04</td><td>Data Cleaning &amp; Preprocessing</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>05</td><td>Handling Missing &amp; Duplicate Data</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>06</td><td>Sorting, Filtering &amp; Aggregation</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>07</td><td>Data Visualization Techniques</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>08</td><td>CSV &amp; Excel File Handling</td><td><span class="status-done">✅ Done</span></td></tr>
            <tr><td>09</td><td>SQL Queries for Analysis</td><td><span class="status-done">✅ Done</span></td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- GITHUB STATS -->
  <div class="section">
    <div class="section-title"><span class="emoji">📈</span> GitHub Stats</div>
    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-num">3+</div>
        <div class="stat-label">Featured Projects</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">7.2</div>
        <div class="stat-label">CGPA</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">9</div>
        <div class="stat-label">Analytics Modules</div>
      </div>
      <div class="stat-card">
        <div class="stat-num">5+</div>
        <div class="stat-label">Tech Stacks</div>
      </div>
    </div>
    <div style="text-align:center; padding: 20px; background: var(--surface); border: 1px solid var(--border); border-radius:12px;">
      <img src="https://github-readme-stats.vercel.app/api?username=codecsuman&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0a0a0f&title_color=7c3aed&text_color=94a3b8&icon_color=06b6d4" 
           alt="GitHub Stats" 
           style="max-width:100%; border-radius:8px;"
           onerror="this.style.display='none'; this.nextElementSibling.style.display='block'">
      <div style="display:none; font-family:'JetBrains Mono',monospace; font-size:0.8rem; color:var(--muted); padding:12px;">
        📊 Visit <a href="https://github.com/codecsuman" target="_blank" style="color:var(--accent2);">github.com/codecsuman</a> to see full stats
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- LEETCODE -->
  <div class="section">
    <div class="section-title"><span class="emoji">🧩</span> LeetCode Progress</div>
    <div class="lc-section">
      <div class="lc-header">
        <div class="lc-title">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="#f59e0b"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
          sumanjhanp1
        </div>
        <a href="https://leetcode.com/u/sumanjhanp1/" target="_blank" class="lc-link">🔗 View Profile</a>
      </div>

      <div class="progress-bar-wrap">
        <div class="progress-bar-label">
          <span>DSA Progress</span>
          <span style="color: var(--accent2);">65%</span>
        </div>
        <div class="progress-bar">
          <div class="progress-fill" style="width:65%"></div>
        </div>
      </div>

      <div style="margin-bottom:16px; font-family:'JetBrains Mono',monospace; font-size:0.72rem; color:var(--muted);">
        📅 Consistent daily problem-solving on LeetCode
      </div>

      <div class="tech-label" style="margin-bottom:10px;">🎯 Focus Areas</div>
      <div class="topics-grid">
        <span class="topic-tag">Arrays</span>
        <span class="topic-tag">Strings</span>
        <span class="topic-tag">Linked List</span>
        <span class="topic-tag">Stack</span>
        <span class="topic-tag">Queue</span>
        <span class="topic-tag">Trees</span>
        <span class="topic-tag">Graphs</span>
        <span class="topic-tag">Dynamic Programming</span>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- CONNECT -->
  <div class="section">
    <div class="section-title"><span class="emoji">🤝</span> Connect With Me</div>
    <div class="connect-grid">
      <a href="https://github.com/codecsuman" target="_blank" class="connect-btn btn-gh">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/></svg>
        GitHub
      </a>
      <a href="https://leetcode.com/u/sumanjhanp1/" target="_blank" class="connect-btn btn-lc">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M13.483 0a1.374 1.374 0 0 0-.961.438L7.116 6.226l-3.854 4.126a5.266 5.266 0 0 0-1.209 2.104 5.35 5.35 0 0 0-.125.513 5.527 5.527 0 0 0 .062 2.362 5.83 5.83 0 0 0 .349 1.017 5.938 5.938 0 0 0 1.271 1.818l4.277 4.193.039.038c2.248 2.165 5.852 2.133 8.063-.074l2.396-2.392c.54-.54.54-1.414.003-1.955a1.378 1.378 0 0 0-1.951-.003l-2.396 2.392a3.021 3.021 0 0 1-4.205.038l-.02-.019-4.276-4.193c-.652-.64-.972-1.469-.948-2.263a2.68 2.68 0 0 1 .066-.523 2.545 2.545 0 0 1 .619-1.164L9.13 8.114c1.058-1.134 3.204-1.27 4.43-.278l3.501 2.831c.593.48 1.461.387 1.94-.207a1.384 1.384 0 0 0-.207-1.943l-3.5-2.831c-.8-.647-1.766-1.045-2.774-1.202l2.015-2.158A1.384 1.384 0 0 0 13.483 0zm-2.866 12.815a1.38 1.38 0 0 0-1.38 1.382 1.38 1.38 0 0 0 1.38 1.382H20.79a1.38 1.38 0 0 0 1.38-1.382 1.38 1.38 0 0 0-1.38-1.382z"/></svg>
        LeetCode
      </a>
      <a href="https://www.linkedin.com/" target="_blank" class="connect-btn btn-li">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 0 1-2.063-2.065 2.064 2.064 0 1 1 2.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="https://sumanjhanp.netlify.app/" target="_blank" class="connect-btn btn-port">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M16.934 8.519a1.044 1.044 0 0 1 .303.23l2.349-1.045-2.192-2.171-.46 2.986zM12.06 6.546a1.305 1.305 0 0 1 .209.574l3.497 1.068 .46-2.985-2.549-.507-1.617 1.85zM21.57 15.772l-4.928-1.105a1.33 1.33 0 0 1-.26.41l1.258 4.787 3.93-4.092z"/></svg>
        Portfolio
      </a>
    </div>

    <div style="text-align:center; margin-top:32px;">
      <span class="star-note">⭐ If you find my work useful, consider giving it a star! ⭐</span>
    </div>
  </div>

  <div class="footer">
    <p>Built with ❤️ by Suman Jhanp · Kolkata, India · 2026</p>
  </div>

</div>
</body>
</html>
