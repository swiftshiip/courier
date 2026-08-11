<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>SwiftShip — Courier & Logistics</title>
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet" />
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0a0b;
    --bg2: #111114;
    --bg3: #18181d;
    --surface: #1e1e24;
    --surface2: #252530;
    --border: rgba(255,255,255,0.07);
    --border2: rgba(255,255,255,0.13);
    --text: #f0ede8;
    --muted: #888890;
    --accent: #e8c547;
    --accent2: #f0d470;
    --accent-dim: rgba(232,197,71,0.12);
    --red: #e85d5d;
    --green: #5de89a;
    --blue: #5da8e8;
    --font-head: 'Syne', sans-serif;
    --font-body: 'DM Sans', sans-serif;
    --r: 10px;
    --r-lg: 16px;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 48px;
    height: 68px;
    background: rgba(10,10,11,0.85);
    backdrop-filter: blur(16px);
    border-bottom: 0.5px solid var(--border);
  }
  .logo {
    font-family: var(--font-head);
    font-size: 22px; font-weight: 800;
    color: var(--text);
    letter-spacing: -0.5px;
    text-decoration: none;
  }
  .logo span { color: var(--accent); }
  .nav-links { display: flex; gap: 36px; list-style: none; }
  .nav-links a {
    font-size: 14px; font-weight: 500;
    color: var(--muted); text-decoration: none;
    transition: color 0.2s;
  }
  .nav-links a:hover { color: var(--text); }
  .nav-cta {
    background: var(--accent); color: #0a0a0b;
    border: none; padding: 10px 22px;
    border-radius: var(--r); font-family: var(--font-body);
    font-size: 14px; font-weight: 600; cursor: pointer;
    transition: background 0.2s, transform 0.15s;
    text-decoration: none;
  }
  .nav-cta:hover { background: var(--accent2); transform: translateY(-1px); }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center; align-items: flex-start;
    padding: 120px 48px 80px;
    position: relative;
    overflow: hidden;
  }
  .hero-grid {
    position: absolute; inset: 0; pointer-events: none;
    background-image:
      linear-gradient(rgba(255,255,255,0.025) 1px, transparent 1px),
      linear-gradient(90deg, rgba(255,255,255,0.025) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 0%, black 30%, transparent 100%);
  }
  .hero-badge {
    display: inline-flex; align-items: center; gap: 8px;
    background: var(--accent-dim); border: 0.5px solid rgba(232,197,71,0.3);
    color: var(--accent); padding: 6px 14px; border-radius: 100px;
    font-size: 12px; font-weight: 600; letter-spacing: 0.08em;
    text-transform: uppercase; margin-bottom: 28px;
  }
  .hero-badge::before { content: ''; width: 6px; height: 6px; border-radius: 50%; background: var(--accent); }
  h1 {
    font-family: var(--font-head);
    font-size: clamp(52px, 7vw, 96px);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -2px;
    max-width: 860px;
    margin-bottom: 24px;
  }
  h1 em { font-style: normal; color: var(--accent); }
  .hero-sub {
    font-size: 18px; font-weight: 300;
    color: var(--muted); max-width: 520px;
    line-height: 1.7; margin-bottom: 44px;
  }
  .hero-actions { display: flex; gap: 16px; flex-wrap: wrap; }
  .btn-primary {
    background: var(--accent); color: #0a0a0b;
    border: none; padding: 14px 32px;
    border-radius: var(--r); font-family: var(--font-body);
    font-size: 15px; font-weight: 600; cursor: pointer;
    transition: all 0.2s; text-decoration: none;
    display: inline-block;
  }
  .btn-primary:hover { background: var(--accent2); transform: translateY(-2px); }
  .btn-ghost {
    background: transparent; color: var(--text);
    border: 0.5px solid var(--border2); padding: 14px 32px;
    border-radius: var(--r); font-family: var(--font-body);
    font-size: 15px; font-weight: 500; cursor: pointer;
    transition: all 0.2s; text-decoration: none;
    display: inline-block;
  }
  .btn-ghost:hover { border-color: var(--accent); color: var(--accent); }
  .hero-stats {
    display: flex; gap: 48px; margin-top: 72px;
    padding-top: 40px; border-top: 0.5px solid var(--border);
  }
  .stat-num {
    font-family: var(--font-head); font-size: 36px; font-weight: 800; color: var(--text);
  }
  .stat-label { font-size: 13px; color: var(--muted); margin-top: 2px; }

  /* SECTION */
  section { padding: 96px 48px; }
  .section-label {
    font-size: 11px; font-weight: 600; letter-spacing: 0.12em;
    text-transform: uppercase; color: var(--accent); margin-bottom: 14px;
  }
  h2 {
    font-family: var(--font-head); font-size: clamp(32px, 4vw, 52px);
    font-weight: 800; line-height: 1.05; letter-spacing: -1.5px;
    margin-bottom: 16px;
  }
  .section-sub {
    font-size: 17px; color: var(--muted); font-weight: 300;
    max-width: 520px; margin-bottom: 56px; line-height: 1.65;
  }

  /* TRACKING SECTION */
  #tracking { background: var(--bg2); }
  .track-box {
    background: var(--surface);
    border: 0.5px solid var(--border2);
    border-radius: var(--r-lg);
    padding: 40px;
    max-width: 780px;
  }
  .track-input-row {
    display: flex; gap: 12px;
  }
  .track-input {
    flex: 1;
    background: var(--bg3); border: 0.5px solid var(--border2);
    border-radius: var(--r); padding: 14px 20px;
    font-family: var(--font-body); font-size: 15px;
    color: var(--text); outline: none;
    transition: border-color 0.2s;
    letter-spacing: 0.04em;
  }
  .track-input::placeholder { color: var(--muted); }
  .track-input:focus { border-color: var(--accent); }
  .track-btn {
    background: var(--accent); color: #0a0a0b;
    border: none; padding: 14px 28px;
    border-radius: var(--r); font-family: var(--font-body);
    font-size: 15px; font-weight: 600; cursor: pointer;
    transition: all 0.2s; white-space: nowrap;
  }
  .track-btn:hover { background: var(--accent2); }

  /* TRACKING RESULT */
  .track-result { display: none; margin-top: 32px; }
  .track-result.visible { display: block; animation: fadeUp 0.4s ease; }
  @keyframes fadeUp { from { opacity:0; transform: translateY(12px); } to { opacity:1; transform:translateY(0); } }

  .result-header {
    display: flex; justify-content: space-between; align-items: flex-start;
    padding-bottom: 24px; border-bottom: 0.5px solid var(--border);
    margin-bottom: 32px; flex-wrap: wrap; gap: 16px;
  }
  .result-id { font-family: var(--font-head); font-size: 20px; font-weight: 700; }
  .result-id span { color: var(--muted); font-weight: 400; font-size: 14px; margin-left: 10px; }
  .status-badge {
    display: inline-flex; align-items: center; gap: 6px;
    padding: 6px 14px; border-radius: 100px;
    font-size: 12px; font-weight: 600; letter-spacing: 0.05em;
  }
  .status-transit { background: rgba(93,168,232,0.15); color: var(--blue); }
  .status-delivered { background: rgba(93,232,154,0.15); color: var(--green); }
  .status-delayed { background: rgba(232,93,93,0.15); color: var(--red); }
  .status-dot { width: 6px; height: 6px; border-radius: 50%; background: currentColor; }

  .result-meta {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 20px; margin-bottom: 36px;
  }
  .meta-item { }
  .meta-label { font-size: 11px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); margin-bottom: 4px; }
  .meta-val { font-size: 15px; font-weight: 500; color: var(--text); }

  /* TIMELINE */
  .timeline { display: flex; flex-direction: column; gap: 0; }
  .tl-item {
    display: grid; grid-template-columns: 56px 1fr;
    gap: 0 20px; position: relative;
  }
  .tl-left { display: flex; flex-direction: column; align-items: center; }
  .tl-dot {
    width: 14px; height: 14px; border-radius: 50%;
    border: 2px solid var(--muted); background: var(--bg3);
    flex-shrink: 0; margin-top: 4px; position: relative; z-index: 1;
    transition: all 0.3s;
  }
  .tl-dot.done { background: var(--accent); border-color: var(--accent); }
  .tl-dot.active { background: var(--blue); border-color: var(--blue); box-shadow: 0 0 0 4px rgba(93,168,232,0.2); }
  .tl-line {
    flex: 1; width: 1px; background: var(--border2);
    margin: 4px 0; min-height: 40px;
  }
  .tl-item:last-child .tl-line { display: none; }
  .tl-content { padding-bottom: 32px; }
  .tl-item:last-child .tl-content { padding-bottom: 0; }
  .tl-event { font-size: 15px; font-weight: 500; margin-bottom: 4px; }
  .tl-loc { font-size: 13px; color: var(--muted); }
  .tl-time { font-size: 12px; color: var(--muted); margin-top: 4px; }
  .tl-time-col {
    display: flex; flex-direction: column; align-items: flex-end;
    padding-top: 2px;
    font-size: 11px; color: var(--muted); white-space: nowrap;
  }

  .map-placeholder {
    margin-top: 32px;
    background: var(--bg3); border: 0.5px solid var(--border);
    border-radius: var(--r); padding: 28px;
    display: flex; align-items: center; justify-content: center;
    height: 160px; position: relative; overflow: hidden;
  }
  .map-route {
    position: absolute; inset: 0;
    display: flex; align-items: center; justify-content: center;
  }
  .map-route svg { width: 100%; height: 100%; opacity: 0.5; }
  .map-label {
    position: relative; z-index: 1;
    display: flex; flex-direction: column; align-items: center; gap: 6px;
  }
  .map-cities {
    display: flex; gap: 8px; align-items: center;
    font-family: var(--font-head); font-size: 18px; font-weight: 700;
  }
  .map-arrow { color: var(--accent); font-size: 20px; }
  .map-sub { font-size: 12px; color: var(--muted); }
  .map-eta {
    position: absolute; right: 20px; bottom: 16px;
    background: var(--accent-dim); border: 0.5px solid rgba(232,197,71,0.25);
    padding: 6px 12px; border-radius: var(--r);
    font-size: 12px; color: var(--accent); font-weight: 600;
  }

  /* SERVICES */
  #services { background: var(--bg); }
  .services-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 20px;
  }
  .service-card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--r-lg);
    padding: 32px;
    transition: border-color 0.25s, transform 0.25s;
    position: relative;
    overflow: hidden;
  }
  .service-card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent), transparent);
    opacity: 0; transition: opacity 0.3s;
  }
  .service-card:hover { border-color: var(--border2); transform: translateY(-4px); }
  .service-card:hover::before { opacity: 1; }
  .service-icon {
    width: 48px; height: 48px; border-radius: var(--r);
    background: var(--accent-dim); border: 0.5px solid rgba(232,197,71,0.2);
    display: flex; align-items: center; justify-content: center;
    font-size: 22px; margin-bottom: 20px;
  }
  .service-name {
    font-family: var(--font-head); font-size: 20px; font-weight: 700;
    margin-bottom: 10px; letter-spacing: -0.3px;
  }
  .service-desc { font-size: 14px; color: var(--muted); line-height: 1.65; margin-bottom: 20px; }
  .service-feature {
    display: flex; align-items: center; gap: 8px;
    font-size: 13px; color: var(--muted); margin-bottom: 6px;
  }
  .service-feature::before { content: '✓'; color: var(--accent); font-weight: 700; }
  .service-price {
    margin-top: 24px; padding-top: 20px; border-top: 0.5px solid var(--border);
    font-family: var(--font-head);
  }
  .price-from { font-size: 11px; color: var(--muted); letter-spacing: 0.05em; text-transform: uppercase; }
  .price-val { font-size: 28px; font-weight: 800; color: var(--accent); }
  .price-unit { font-size: 13px; color: var(--muted); }

  /* HOW IT WORKS */
  #how { background: var(--bg2); }
  .steps-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 0; position: relative;
  }
  .step {
    padding: 40px 32px;
    border-right: 0.5px solid var(--border);
    position: relative;
  }
  .step:last-child { border-right: none; }
  .step-num {
    font-family: var(--font-head); font-size: 64px; font-weight: 800;
    color: rgba(232,197,71,0.08); line-height: 1; margin-bottom: 16px;
    letter-spacing: -3px;
  }
  .step-title {
    font-family: var(--font-head); font-size: 18px; font-weight: 700;
    margin-bottom: 10px; letter-spacing: -0.3px;
  }
  .step-desc { font-size: 14px; color: var(--muted); line-height: 1.65; }

  /* PRICING */
  #pricing { background: var(--bg); }
  .pricing-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px; max-width: 1000px;
  }
  .plan-card {
    background: var(--surface);
    border: 0.5px solid var(--border);
    border-radius: var(--r-lg);
    padding: 36px;
    transition: border-color 0.2s;
  }
  .plan-card.featured {
    border-color: rgba(232,197,71,0.4);
    background: linear-gradient(135deg, var(--surface) 60%, rgba(232,197,71,0.04));
    position: relative;
  }
  .plan-badge {
    position: absolute; top: -11px; left: 50%; transform: translateX(-50%);
    background: var(--accent); color: #0a0a0b;
    font-size: 10px; font-weight: 700; letter-spacing: 0.1em;
    text-transform: uppercase; padding: 4px 14px; border-radius: 100px;
    white-space: nowrap;
  }
  .plan-name {
    font-family: var(--font-head); font-size: 14px; font-weight: 700;
    letter-spacing: 0.08em; text-transform: uppercase;
    color: var(--muted); margin-bottom: 16px;
  }
  .plan-price {
    font-family: var(--font-head); font-size: 48px; font-weight: 800;
    letter-spacing: -2px; line-height: 1; margin-bottom: 6px;
  }
  .plan-price span { font-size: 22px; vertical-align: top; margin-top: 8px; display: inline-block; }
  .plan-period { font-size: 13px; color: var(--muted); margin-bottom: 28px; }
  .plan-feature {
    display: flex; align-items: flex-start; gap: 10px;
    font-size: 14px; margin-bottom: 12px; line-height: 1.5;
  }
  .pf-check { color: var(--accent); flex-shrink: 0; margin-top: 2px; }
  .pf-cross { color: var(--muted); flex-shrink: 0; margin-top: 2px; }
  .plan-feature.off { color: var(--muted); }
  .plan-cta {
    display: block; text-align: center;
    margin-top: 28px; padding: 12px;
    border-radius: var(--r); font-size: 14px; font-weight: 600;
    cursor: pointer; transition: all 0.2s; text-decoration: none;
    border: 0.5px solid var(--border2); color: var(--text);
    background: transparent;
  }
  .plan-cta:hover { border-color: var(--accent); color: var(--accent); }
  .plan-card.featured .plan-cta {
    background: var(--accent); color: #0a0a0b; border-color: var(--accent);
  }
  .plan-card.featured .plan-cta:hover { background: var(--accent2); }

  /* CALCULATOR */
  #calculator { background: var(--bg2); }
  .calc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; max-width: 900px; }
  @media (max-width: 700px) { .calc-grid { grid-template-columns: 1fr; } }
  .calc-form { display: flex; flex-direction: column; gap: 18px; }
  .form-group { display: flex; flex-direction: column; gap: 6px; }
  .form-label { font-size: 12px; letter-spacing: 0.06em; text-transform: uppercase; color: var(--muted); }
  .form-input, .form-select {
    background: var(--surface); border: 0.5px solid var(--border2);
    border-radius: var(--r); padding: 12px 16px;
    font-family: var(--font-body); font-size: 15px; color: var(--text);
    outline: none; transition: border-color 0.2s;
    appearance: none;
  }
  .form-input::placeholder { color: var(--muted); }
  .form-input:focus, .form-select:focus { border-color: var(--accent); }
  .form-select { cursor: pointer; }
  .input-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  .calc-result {
    background: var(--surface); border: 0.5px solid var(--border2);
    border-radius: var(--r-lg); padding: 32px;
    display: flex; flex-direction: column;
  }
  .calc-title { font-size: 13px; letter-spacing: 0.08em; text-transform: uppercase; color: var(--muted); margin-bottom: 24px; }
  .price-breakdown { flex: 1; }
  .pb-row {
    display: flex; justify-content: space-between; align-items: center;
    padding: 12px 0; border-bottom: 0.5px solid var(--border);
    font-size: 14px;
  }
  .pb-row:last-child { border-bottom: none; }
  .pb-label { color: var(--muted); }
  .pb-val { font-weight: 500; }
  .pb-total {
    display: flex; justify-content: space-between; align-items: center;
    margin-top: 20px; padding-top: 20px; border-top: 0.5px solid var(--border2);
    font-family: var(--font-head); font-size: 28px; font-weight: 800;
  }
  .pb-total-label { font-size: 13px; color: var(--muted); font-family: var(--font-body); font-weight: 400; }
  .pb-total-val { color: var(--accent); }
  .calc-note { font-size: 12px; color: var(--muted); margin-top: 16px; line-height: 1.6; }

  /* TESTIMONIALS */
  #testimonials { background: var(--bg); }
  .testi-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; }
  .testi-card {
    background: var(--surface); border: 0.5px solid var(--border);
    border-radius: var(--r-lg); padding: 28px;
    transition: border-color 0.2s;
  }
  .testi-card:hover { border-color: var(--border2); }
  .testi-stars { color: var(--accent); font-size: 14px; margin-bottom: 16px; letter-spacing: 2px; }
  .testi-text { font-size: 15px; color: var(--text); line-height: 1.7; margin-bottom: 20px; font-style: italic; font-weight: 300; }
  .testi-author { display: flex; align-items: center; gap: 12px; }
  .testi-avatar {
    width: 40px; height: 40px; border-radius: 50%;
    background: var(--accent-dim); border: 0.5px solid rgba(232,197,71,0.3);
    display: flex; align-items: center; justify-content: center;
    font-family: var(--font-head); font-size: 14px; font-weight: 700; color: var(--accent);
  }
  .testi-name { font-size: 14px; font-weight: 600; }
  .testi-role { font-size: 12px; color: var(--muted); }

  /* CONTACT */
  #contact { background: var(--bg2); }
  .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 64px; max-width: 1000px; }
  @media (max-width: 700px) { .contact-grid { grid-template-columns: 1fr; } }
  .contact-info { display: flex; flex-direction: column; gap: 28px; }
  .contact-item { display: flex; gap: 16px; align-items: flex-start; }
  .contact-ico {
    width: 44px; height: 44px; background: var(--accent-dim);
    border: 0.5px solid rgba(232,197,71,0.2);
    border-radius: var(--r); display: flex; align-items: center; justify-content: center;
    font-size: 18px; flex-shrink: 0;
  }
  .contact-label { font-size: 12px; color: var(--muted); letter-spacing: 0.06em; text-transform: uppercase; margin-bottom: 4px; }
  .contact-val { font-size: 15px; font-weight: 500; }
  .contact-form { display: flex; flex-direction: column; gap: 16px; }
  textarea.form-input {
    resize: vertical; min-height: 120px;
    font-family: var(--font-body);
  }
  .submit-btn {
    background: var(--accent); color: #0a0a0b;
    border: none; padding: 14px 28px;
    border-radius: var(--r); font-family: var(--font-body);
    font-size: 15px; font-weight: 600; cursor: pointer;
    transition: all 0.2s;
  }
  .submit-btn:hover { background: var(--accent2); transform: translateY(-1px); }

  /* FOOTER */
  footer {
    background: var(--bg3); border-top: 0.5px solid var(--border);
    padding: 56px 48px 36px;
  }
  .footer-top {
    display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 48px; margin-bottom: 48px;
  }
  .footer-brand .logo { font-size: 20px; display: inline-block; margin-bottom: 14px; }
  .footer-brand p { font-size: 14px; color: var(--muted); line-height: 1.7; max-width: 260px; }
  .footer-col-title {
    font-size: 12px; font-weight: 600; letter-spacing: 0.08em;
    text-transform: uppercase; color: var(--text); margin-bottom: 16px;
  }
  .footer-link {
    display: block; font-size: 14px; color: var(--muted);
    text-decoration: none; margin-bottom: 10px; transition: color 0.2s;
  }
  .footer-link:hover { color: var(--text); }
  .footer-bottom {
    display: flex; justify-content: space-between; align-items: center;
    padding-top: 28px; border-top: 0.5px solid var(--border);
    font-size: 13px; color: var(--muted); flex-wrap: wrap; gap: 12px;
  }

  /* MOBILE NAV */
  .nav-mobile-toggle { display: none; background: none; border: none; color: var(--text); font-size: 22px; cursor: pointer; }
  @media (max-width: 768px) {
    nav { padding: 0 20px; }
    .nav-links { display: none; }
    .nav-mobile-toggle { display: block; }
    .hero { padding: 100px 20px 60px; }
    section { padding: 72px 20px; }
    .hero-stats { gap: 28px; flex-wrap: wrap; }
    .steps-grid { grid-template-columns: 1fr; }
    .step { border-right: none; border-bottom: 0.5px solid var(--border); }
    .step:last-child { border-bottom: none; }
    footer { padding: 48px 20px 28px; }
    .footer-top { grid-template-columns: 1fr 1fr; gap: 28px; }
    .track-input-row { flex-direction: column; }
  }

  /* ANIMATIONS */
  .fade-in {
    opacity: 0; transform: translateY(20px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .fade-in.visible { opacity: 1; transform: translateY(0); }

  /* TOAST */
  .toast {
    position: fixed; bottom: 32px; right: 32px; z-index: 999;
    background: var(--surface); border: 0.5px solid var(--border2);
    border-radius: var(--r); padding: 14px 20px;
    font-size: 14px; box-shadow: 0 8px 32px rgba(0,0,0,0.4);
    transform: translateY(80px); opacity: 0;
    transition: all 0.3s ease;
    max-width: 320px;
  }
  .toast.show { transform: translateY(0); opacity: 1; }
  .toast.success { border-color: rgba(93,232,154,0.3); }
  .toast-title { font-weight: 600; margin-bottom: 4px; }
  .toast-msg { color: var(--muted); font-size: 13px; }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="logo">Swift<span>Ship</span></a>
  <ul class="nav-links">
    <li><a href="#tracking">Track</a></li>
    <li><a href="#services">Services</a></li>
    <li><a href="#pricing">Pricing</a></li>
    <li><a href="#calculator">Calculator</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="#tracking" class="nav-cta">Track Package</a>
  <button class="nav-mobile-toggle" onclick="this.innerHTML = this.innerHTML==='☰'?'✕':'☰'">☰</button>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-grid"></div>
  <div class="hero-badge">⚡ Express & Same-Day Delivery Available</div>
  <h1>Deliver<br/>with <em>Speed</em><br/>& Precision</h1>
  <p class="hero-sub">SwiftShip connects businesses and individuals with fast, reliable courier services across the country and worldwide. Real-time tracking, guaranteed delivery.</p>
  <div class="hero-actions">
    <a href="#tracking" class="btn-primary">Track Your Package</a>
    <a href="#services" class="btn-ghost">View Services</a>
  </div>
  <div class="hero-stats">
    <div>
      <div class="stat-num">2.4M+</div>
      <div class="stat-label">Packages Delivered</div>
    </div>
    <div>
      <div class="stat-num">98.7%</div>
      <div class="stat-label">On-Time Rate</div>
    </div>
    <div>
      <div class="stat-num">180+</div>
      <div class="stat-label">Countries Covered</div>
    </div>
    <div>
      <div class="stat-num">24/7</div>
      <div class="stat-label">Live Support</div>
    </div>
  </div>
</section>

<!-- TRACKING -->
<section id="tracking">
  <div class="section-label">📦 Real-Time Tracking</div>
  <h2>Where's Your Package?</h2>
  <p class="section-sub">Enter your tracking number to get instant, detailed updates on your shipment's location and status.</p>

  <div class="track-box fade-in">
    <div class="track-input-row">
      <input class="track-input" type="text" id="trackInput" placeholder="Enter tracking number (e.g. SW-2024-8834721)" />
      <button class="track-btn" onclick="trackPackage()">Track Now →</button>
    </div>
    <p style="font-size:12px;color:var(--muted);margin-top:10px;">Try: <span style="cursor:pointer;color:var(--accent);text-decoration:underline" onclick="document.getElementById('trackInput').value='SW-2024-8834721';trackPackage()">SW-2024-8834721</span> · <span style="cursor:pointer;color:var(--accent);text-decoration:underline" onclick="document.getElementById('trackInput').value='SW-2024-5519043';trackPackage()">SW-2024-5519043</span></p>

    <div class="track-result" id="trackResult">
      <!-- Filled by JS -->
    </div>
  </div>
</section>

<!-- SERVICES -->
<section id="services">
  <div class="section-label">🚀 Our Services</div>
  <h2>Every Delivery, Covered</h2>
  <p class="section-sub">From same-day express runs to international freight, SwiftShip has the right solution for every shipment size and speed requirement.</p>

  <div class="services-grid">
    <div class="service-card fade-in">
      <div class="service-icon">⚡</div>
      <div class="service-name">Same-Day Express</div>
      <div class="service-desc">Your package picked up and delivered within hours. Guaranteed same-day service for urgent shipments within city limits.</div>
      <div class="service-feature">Pickup within 1 hour</div>
      <div class="service-feature">Live GPS tracking</div>
      <div class="service-feature">Signature confirmation</div>
      <div class="service-feature">Dedicated courier</div>
      <div class="service-price">
        <div class="price-from">Starting from</div>
        <div><span class="price-val">$18</span> <span class="price-unit">/ delivery</span></div>
      </div>
    </div>

    <div class="service-card fade-in">
      <div class="service-icon">📦</div>
      <div class="service-name">Standard Courier</div>
      <div class="service-desc">Reliable 1-3 day delivery with full tracking. The perfect balance of speed and cost for regular business shipments.</div>
      <div class="service-feature">1-3 business days</div>
      <div class="service-feature">Door-to-door service</div>
      <div class="service-feature">Insurance included</div>
      <div class="service-feature">SMS & email alerts</div>
      <div class="service-price">
        <div class="price-from">Starting from</div>
        <div><span class="price-val">$8</span> <span class="price-unit">/ kg</span></div>
      </div>
    </div>

    <div class="service-card fade-in">
      <div class="service-icon">🌍</div>
      <div class="service-name">International Freight</div>
      <div class="service-desc">Seamless cross-border shipping to 180+ countries. Customs clearance handled by our dedicated freight specialists.</div>
      <div class="service-feature">180+ countries</div>
      <div class="service-feature">Customs assistance</div>
      <div class="service-feature">Air & sea options</div>
      <div class="service-feature">Duty & tax calculation</div>
      <div class="service-price">
        <div class="price-from">Starting from</div>
        <div><span class="price-val">$24</span> <span class="price-unit">/ kg</span></div>
      </div>
    </div>

    <div class="service-card fade-in">
      <div class="service-icon">🏢</div>
      <div class="service-name">Business Solutions</div>
      <div class="service-desc">Volume-based contracts for businesses with dedicated account managers, bulk pricing, and API integration.</div>
      <div class="service-feature">Volume discounts</div>
      <div class="service-feature">API & webhook access</div>
      <div class="service-feature">Monthly invoicing</div>
      <div class="service-feature">Dedicated account rep</div>
      <div class="service-price">
        <div class="price-from">Custom pricing</div>
        <div><span class="price-val">Contact</span> <span class="price-unit">us</span></div>
      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section id="how">
  <div class="section-label">🗺️ How It Works</div>
  <h2>Ship in 4 Simple Steps</h2>
  <p class="section-sub">From booking to delivery, SwiftShip makes logistics effortless.</p>

  <div class="steps-grid">
    <div class="step fade-in">
      <div class="step-num">01</div>
      <div class="step-title">Book Online</div>
      <div class="step-desc">Enter your shipment details, choose your service level, and get an instant quote. Book in under 2 minutes.</div>
    </div>
    <div class="step fade-in">
      <div class="step-num">02</div>
      <div class="step-title">We Pick Up</div>
      <div class="step-desc">Our courier arrives at your door at the scheduled time. Pack it, label it, and hand it over — we handle the rest.</div>
    </div>
    <div class="step fade-in">
      <div class="step-num">03</div>
      <div class="step-title">Track Live</div>
      <div class="step-desc">Follow your package in real time with GPS-level tracking, push notifications, and live ETA updates.</div>
    </div>
    <div class="step fade-in">
      <div class="step-num">04</div>
      <div class="step-title">Delivered</div>
      <div class="step-desc">Safe, confirmed delivery with photo proof and digital signature. Rate your experience and we pay attention.</div>
    </div>
  </div>
</section>

<!-- CALCULATOR -->
<section id="calculator">
  <div class="section-label">🧮 Price Calculator</div>
  <h2>Estimate Your Cost</h2>
  <p class="section-sub">Get an instant estimate for your shipment. Final pricing confirmed at booking.</p>

  <div class="calc-grid">
    <div class="calc-form fade-in">
      <div class="form-group">
        <label class="form-label">Service Type</label>
        <select class="form-select" id="calcService" onchange="calcPrice()">
          <option value="sameday">Same-Day Express</option>
          <option value="standard" selected>Standard Courier</option>
          <option value="international">International Freight</option>
        </select>
      </div>
      <div class="form-group">
        <label class="form-label">Origin City</label>
        <input class="form-input" type="text" id="calcFrom" placeholder="Lagos, Nigeria" oninput="calcPrice()" />
      </div>
      <div class="form-group">
        <label class="form-label">Destination City</label>
        <input class="form-input" type="text" id="calcTo" placeholder="Abuja, Nigeria" oninput="calcPrice()" />
      </div>
      <div class="form-group">
        <label class="form-label">Package Weight (kg)</label>
        <input class="form-input" type="number" id="calcWeight" value="2" min="0.1" step="0.1" oninput="calcPrice()" />
      </div>
      <div class="input-row">
        <div class="form-group">
          <label class="form-label">Length (cm)</label>
          <input class="form-input" type="number" id="calcL" value="30" min="1" oninput="calcPrice()" />
        </div>
        <div class="form-group">
          <label class="form-label">Width (cm)</label>
          <input class="form-input" type="number" id="calcW" value="20" min="1" oninput="calcPrice()" />
        </div>
      </div>
      <div class="form-group">
        <label class="form-label">Height (cm)</label>
        <input class="form-input" type="number" id="calcH" value="15" min="1" oninput="calcPrice()" />
      </div>
    </div>

    <div class="calc-result fade-in" id="calcResult">
      <div class="calc-title">Estimated Cost</div>
      <div class="price-breakdown" id="calcBreakdown">
        <!-- Filled by JS -->
      </div>
      <div class="calc-note" id="calcNote"></div>
    </div>
  </div>
</section>

<!-- PRICING PLANS -->
<section id="pricing">
  <div class="section-label">💳 Pricing Plans</div>
  <h2>Simple, Transparent Pricing</h2>
  <p class="section-sub">Choose the plan that fits your shipping volume. No hidden fees, ever.</p>

  <div class="pricing-grid">
    <div class="plan-card fade-in">
      <div class="plan-name">Starter</div>
      <div class="plan-price"><span>$</span>0</div>
      <div class="plan-period">Pay per shipment · No monthly fee</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Standard tracking</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Email notifications</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Online booking</div>
      <div class="plan-feature off"><span class="pf-cross">–</span> Priority support</div>
      <div class="plan-feature off"><span class="pf-cross">–</span> Bulk discounts</div>
      <div class="plan-feature off"><span class="pf-cross">–</span> API access</div>
      <a href="#contact" class="plan-cta">Get Started Free</a>
    </div>

    <div class="plan-card featured fade-in">
      <div class="plan-badge">Most Popular</div>
      <div class="plan-name">Business</div>
      <div class="plan-price"><span>$</span>49</div>
      <div class="plan-period">per month · Up to 200 shipments</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Live GPS tracking</div>
      <div class="plan-feature"><span class="pf-check">✓</span> SMS + email alerts</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Priority pickup slots</div>
      <div class="plan-feature"><span class="pf-check">✓</span> 15% bulk discount</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Phone + chat support</div>
      <div class="plan-feature off"><span class="pf-cross">–</span> API & webhooks</div>
      <a href="#contact" class="plan-cta">Start Business Plan</a>
    </div>

    <div class="plan-card fade-in">
      <div class="plan-name">Enterprise</div>
      <div class="plan-price"><span>$</span>199</div>
      <div class="plan-period">per month · Unlimited shipments</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Everything in Business</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Full API & webhooks</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Dedicated account rep</div>
      <div class="plan-feature"><span class="pf-check">✓</span> Custom integrations</div>
      <div class="plan-feature"><span class="pf-check">✓</span> 25% volume discount</div>
      <div class="plan-feature"><span class="pf-check">✓</span> 24/7 SLA support</div>
      <a href="#contact" class="plan-cta">Contact Sales</a>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section id="testimonials" style="background: var(--bg2)">
  <div class="section-label">⭐ Customer Reviews</div>
  <h2>Trusted by Thousands</h2>
  <p class="section-sub">Don't take our word for it — here's what our customers say.</p>

  <div class="testi-grid">
    <div class="testi-card fade-in">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"SwiftShip transformed our e-commerce logistics. Packages arrive faster, customers are happier, and the tracking is genuinely impressive. We switched from our old provider and never looked back."</p>
      <div class="testi-author">
        <div class="testi-avatar">AO</div>
        <div>
          <div class="testi-name">Adaeze Okonkwo</div>
          <div class="testi-role">CEO, StyleHub Nigeria</div>
        </div>
      </div>
    </div>

    <div class="testi-card fade-in">
      <div class="testi-stars">★★★★★</div>
      <p class="testi-text">"The same-day express service is a game-changer for our pharmacy. Critical medications reach patients within hours. The live tracking gives both us and patients real peace of mind."</p>
      <div class="testi-author">
        <div class="testi-avatar">KM</div>
        <div>
          <div class="testi-name">Dr. Kofi Mensah</div>
          <div class="testi-role">Operations Director, MediQuick</div>
        </div>
      </div>
    </div>

    <div class="testi-card fade-in">
      <div class="testi-stars">★★★★☆</div>
      <p class="testi-text">"International shipments used to be a nightmare. SwiftShip handles customs seamlessly and their tracking works across borders. Reliable, professional, and their support team is actually helpful."</p>
      <div class="testi-author">
        <div class="testi-avatar">RB</div>
        <div>
          <div class="testi-name">Rashida Bello</div>
          <div class="testi-role">Import Manager, TradeLink Africa</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-label">📬 Get In Touch</div>
  <h2>Let's Talk Logistics</h2>
  <p class="section-sub">Have questions or need a custom quote? Our team responds within 2 hours on business days.</p>

  <div class="contact-grid">
    <div class="contact-info fade-in">
      <div class="contact-item">
        <div class="contact-ico">📞</div>
        <div>
          <div class="contact-label">Phone</div>
          <div class="contact-val">+234 800 SWIFT 01</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-ico">✉️</div>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-val">hello@swiftship.io</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-ico">📍</div>
        <div>
          <div class="contact-label">Headquarters</div>
          <div class="contact-val">14 Marina Road, Lagos Island, Nigeria</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-ico">🕐</div>
        <div>
          <div class="contact-label">Support Hours</div>
          <div class="contact-val">24/7 Live Chat · Mon–Sat Phone</div>
        </div>
      </div>

      <div style="margin-top:8px; padding: 24px; background: var(--accent-dim); border: 0.5px solid rgba(232,197,71,0.2); border-radius: var(--r-lg);">
        <div style="font-family: var(--font-head); font-size:15px; font-weight:700; margin-bottom:8px;">New to SwiftShip?</div>
        <p style="font-size:13px; color: var(--muted); line-height:1.6; margin-bottom:16px;">Get 20% off your first 5 shipments when you sign up for a Business plan this month.</p>
        <a href="#pricing" class="btn-primary" style="font-size:13px; padding: 10px 20px;">Claim Offer →</a>
      </div>
    </div>

    <div class="fade-in">
      <div class="contact-form">
        <div class="form-group">
          <label class="form-label">Full Name</label>
          <input class="form-input" type="text" id="cName" placeholder="Your name" />
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input class="form-input" type="email" id="cEmail" placeholder="your@email.com" />
        </div>
        <div class="form-group">
          <label class="form-label">Subject</label>
          <select class="form-select" id="cSubject">
            <option>General Inquiry</option>
            <option>Get a Custom Quote</option>
            <option>Enterprise / Business Plan</option>
            <option>Support / Complaint</option>
            <option>Partnership</option>
          </select>
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-input" id="cMessage" placeholder="Tell us about your shipping needs..."></textarea>
        </div>
        <button class="submit-btn" onclick="sendContact()">Send Message →</button>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <a href="#" class="logo">Swift<span>Ship</span></a>
      <p>Fast, reliable courier and logistics services across Nigeria and worldwide. Trusted by 12,000+ businesses and individuals.</p>
    </div>
    <div>
      <div class="footer-col-title">Services</div>
      <a href="#services" class="footer-link">Same-Day Express</a>
      <a href="#services" class="footer-link">Standard Courier</a>
      <a href="#services" class="footer-link">International Freight</a>
      <a href="#services" class="footer-link">Business Solutions</a>
    </div>
    <div>
      <div class="footer-col-title">Company</div>
      <a href="#" class="footer-link">About Us</a>
      <a href="#" class="footer-link">Careers</a>
      <a href="#" class="footer-link">Press</a>
      <a href="#contact" class="footer-link">Contact</a>
    </div>
    <div>
      <div class="footer-col-title">Support</div>
      <a href="#tracking" class="footer-link">Track Package</a>
      <a href="#calculator" class="footer-link">Price Calculator</a>
      <a href="#" class="footer-link">FAQs</a>
      <a href="#" class="footer-link">Terms & Privacy</a>
    </div>
  </div>
  <div class="footer-bottom">
    <span>© 2024 SwiftShip Logistics Ltd. All rights reserved.</span>
    <span>🇳🇬 Lagos, Nigeria · Delivering nationwide & worldwide</span>
  </div>
</footer>

<!-- TOAST -->
<div class="toast" id="toast">
  <div class="toast-title" id="toastTitle"></div>
  <div class="toast-msg" id="toastMsg"></div>
</div>

<script>
// ── TRACKING DATA ──────────────────────────────────────────
const PACKAGES = {
  'SW-2024-8834721': {
    id: 'SW-2024-8834721',
    status: 'transit',
    statusLabel: 'In Transit',
    from: 'Lagos', to: 'Abuja',
    service: 'Standard Courier',
    weight: '3.2 kg',
    eta: 'Tomorrow, Dec 18',
    sender: 'Ada Stores Ltd',
    recipient: 'John Eze',
    timeline: [
      { event: 'Package delivered to SwiftShip hub', loc: 'Lagos Island Hub', time: 'Today, 06:14 AM', done: true, active: false },
      { event: 'Shipment scanned and processed', loc: 'Lagos Sorting Center', time: 'Today, 08:47 AM', done: true, active: false },
      { event: 'In transit — en route to destination', loc: 'Lokoja Junction Checkpoint', time: 'Today, 01:33 PM', done: false, active: true },
      { event: 'Arrived at destination hub', loc: 'Abuja FCT Distribution Center', time: 'Expected tomorrow 07:00 AM', done: false, active: false },
      { event: 'Out for delivery', loc: 'Abuja, FCT', time: 'Expected tomorrow 10:00 AM', done: false, active: false },
      { event: 'Delivered', loc: 'Recipient address, Abuja', time: 'Expected tomorrow by 5:00 PM', done: false, active: false },
    ]
  },
  'SW-2024-5519043': {
    id: 'SW-2024-5519043',
    status: 'delivered',
    statusLabel: 'Delivered',
    from: 'Port Harcourt', to: 'Lagos',
    service: 'Same-Day Express',
    weight: '1.1 kg',
    eta: 'Delivered Dec 15, 3:42 PM',
    sender: 'Tech Gadgets PH',
    recipient: 'Amaka Nwosu',
    timeline: [
      { event: 'Package received', loc: 'Port Harcourt Pickup Point', time: 'Dec 15, 09:00 AM', done: true },
      { event: 'Dispatched — air freight', loc: 'PH International Airport', time: 'Dec 15, 10:15 AM', done: true },
      { event: 'Arrived Lagos', loc: 'Murtala Mohammed Airport', time: 'Dec 15, 12:50 PM', done: true },
      { event: 'Out for delivery', loc: 'Victoria Island Hub', time: 'Dec 15, 01:30 PM', done: true },
      { event: 'Delivered — signed by recipient', loc: 'Victoria Island, Lagos', time: 'Dec 15, 03:42 PM', done: true, active: false },
    ]
  }
};

function trackPackage() {
  const val = document.getElementById('trackInput').value.trim().toUpperCase();
  const result = document.getElementById('trackResult');

  if (!val) { showToast('Please enter a tracking number', '', false); return; }

  const pkg = PACKAGES[val] || PACKAGES[val.replace(/\s/g, '')];

  if (!pkg) {
    result.className = 'track-result visible';
    result.innerHTML = `
      <div style="padding:32px;text-align:center;color:var(--muted);">
        <div style="font-size:40px;margin-bottom:16px;">📭</div>
        <div style="font-family:var(--font-head);font-size:18px;font-weight:700;color:var(--text);margin-bottom:8px;">No package found</div>
        <p style="font-size:14px;">We couldn't find a shipment with tracking number <strong style="color:var(--accent)">${val}</strong>.<br/>Check the number and try again, or contact support.</p>
      </div>`;
    return;
  }

  const statusClass = pkg.status === 'delivered' ? 'status-delivered' : pkg.status === 'delayed' ? 'status-delayed' : 'status-transit';

  const timelineHTML = pkg.timeline.map(t => `
    <div class="tl-item">
      <div class="tl-left">
        <div class="tl-dot ${t.done ? 'done' : ''} ${t.active ? 'active' : ''}"></div>
        <div class="tl-line"></div>
      </div>
      <div class="tl-content">
        <div class="tl-event" style="${!t.done && !t.active ? 'color:var(--muted)' : ''}">${t.event}</div>
        <div class="tl-loc">${t.loc}</div>
        <div class="tl-time">${t.time}</div>
      </div>
    </div>
  `).join('');

  result.className = 'track-result visible';
  result.innerHTML = `
    <div class="result-header">
      <div>
        <div class="result-id">${pkg.id} <span>${pkg.service}</span></div>
      </div>
      <div class="status-badge ${statusClass}">
        <div class="status-dot"></div>
        ${pkg.statusLabel}
      </div>
    </div>

    <div class="result-meta">
      <div class="meta-item"><div class="meta-label">From</div><div class="meta-val">${pkg.from}</div></div>
      <div class="meta-item"><div class="meta-label">To</div><div class="meta-val">${pkg.to}</div></div>
      <div class="meta-item"><div class="meta-label">Weight</div><div class="meta-val">${pkg.weight}</div></div>
      <div class="meta-item"><div class="meta-label">ETA / Delivery</div><div class="meta-val" style="color:var(--accent)">${pkg.eta}</div></div>
      <div class="meta-item"><div class="meta-label">Sender</div><div class="meta-val">${pkg.sender}</div></div>
      <div class="meta-item"><div class="meta-label">Recipient</div><div class="meta-val">${pkg.recipient}</div></div>
    </div>

    <div style="margin-bottom:16px;font-size:12px;letter-spacing:0.08em;text-transform:uppercase;color:var(--muted);">Shipment Timeline</div>
    <div class="timeline">${timelineHTML}</div>

    <div class="map-placeholder">
      <div class="map-route">
        <svg viewBox="0 0 700 120" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <marker id="arr" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto">
              <path d="M0,0 L0,6 L8,3 z" fill="rgba(232,197,71,0.5)" />
            </marker>
          </defs>
          <line x1="80" y1="60" x2="620" y2="60" stroke="rgba(255,255,255,0.08)" stroke-width="1" stroke-dasharray="6,8" />
          <path d="M80,60 Q300,20 500,60 Q560,80 620,60" stroke="rgba(232,197,71,0.4)" stroke-width="1.5" fill="none" stroke-dasharray="8,6" marker-end="url(#arr)" />
          <circle cx="80" cy="60" r="5" fill="rgba(232,197,71,0.6)" />
          <circle cx="620" cy="60" r="5" fill="rgba(93,168,232,0.6)" />
          <circle cx="360" cy="38" r="7" fill="rgba(232,197,71,0.9)" />
          <text x="80" y="90" fill="rgba(255,255,255,0.4)" font-size="11" text-anchor="middle">${pkg.from}</text>
          <text x="620" y="90" fill="rgba(255,255,255,0.4)" font-size="11" text-anchor="middle">${pkg.to}</text>
          <text x="360" y="25" fill="rgba(232,197,71,0.7)" font-size="10" text-anchor="middle">● Current</text>
        </svg>
      </div>
      <div class="map-eta">ETA: ${pkg.eta}</div>
    </div>
  `;
}

document.getElementById('trackInput').addEventListener('keydown', e => {
  if (e.key === 'Enter') trackPackage();
});

// ── PRICE CALCULATOR ────────────────────────────────────────
const RATES = {
  sameday:       { base: 18, perKg: 4,  dim: 0.003, label: 'Same-Day Express', days: 'Same day' },
  standard:      { base: 6,  perKg: 8,  dim: 0.002, label: 'Standard Courier', days: '1-3 business days' },
  international: { base: 24, perKg: 22, dim: 0.005, label: 'International Freight', days: '5-10 business days' },
};

function calcPrice() {
  const service  = document.getElementById('calcService').value;
  const weight   = parseFloat(document.getElementById('calcWeight').value) || 1;
  const l        = parseFloat(document.getElementById('calcL').value) || 1;
  const w        = parseFloat(document.getElementById('calcW').value) || 1;
  const h        = parseFloat(document.getElementById('calcH').value) || 1;
  const r        = RATES[service];

  const dimWeight   = (l * w * h) / 5000;
  const chargeWeight = Math.max(weight, dimWeight);
  const weightCost   = chargeWeight * r.perKg;
  const fuel         = (r.base + weightCost) * 0.08;
  const insurance    = (r.base + weightCost) * 0.02;
  const total        = r.base + weightCost + fuel + insurance;

  document.getElementById('calcBreakdown').innerHTML = `
    <div class="pb-row"><span class="pb-label">Base rate (${r.label})</span><span class="pb-val">$${r.base.toFixed(2)}</span></div>
    <div class="pb-row"><span class="pb-label">Weight charge (${chargeWeight.toFixed(1)} kg × $${r.perKg})</span><span class="pb-val">$${weightCost.toFixed(2)}</span></div>
    <div class="pb-row"><span class="pb-label">Fuel surcharge (8%)</span><span class="pb-val">$${fuel.toFixed(2)}</span></div>
    <div class="pb-row"><span class="pb-label">Insurance (2%)</span><span class="pb-val">$${insurance.toFixed(2)}</span></div>
    <div class="pb-total"><span class="pb-total-label">Estimated Total</span><span class="pb-total-val">$${total.toFixed(2)}</span></div>
  `;

  document.getElementById('calcNote').innerHTML =
    `<i>Estimated delivery: <strong>${r.days}</strong>. Final price depends on exact route and package contents. Dimensional weight (${dimWeight.toFixed(1)} kg) ${dimWeight > weight ? 'applied — larger than actual weight' : 'below actual weight'}.</i>`;
}

calcPrice();

// ── CONTACT FORM ────────────────────────────────────────────
function sendContact() {
  const name = document.getElementById('cName').value.trim();
  const email = document.getElementById('cEmail').value.trim();
  const msg = document.getElementById('cMessage').value.trim();
  if (!name || !email) { showToast('Please fill in your name and email', '', false); return; }
  showToast('Message sent!', 'We\'ll get back to you within 2 business hours.', true);
  document.getElementById('cName').value = '';
  document.getElementById('cEmail').value = '';
  document.getElementById('cMessage').value = '';
}

// ── TOAST ────────────────────────────────────────────────────
function showToast(title, msg, success) {
  const t = document.getElementById('toast');
  document.getElementById('toastTitle').textContent = title;
  document.getElementById('toastMsg').textContent = msg;
  t.className = 'toast' + (success ? ' success show' : ' show');
  setTimeout(() => { t.className = 'toast' + (success ? ' success' : ''); }, 4000);
}

// ── SCROLL ANIMATIONS ────────────────────────────────────────
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
}, { threshold: 0.1, rootMargin: '0px 0px -60px 0px' });

document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));
</script>
</body>
</html>
