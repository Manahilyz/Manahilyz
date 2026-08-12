<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Manahil Zahra — Aspiring Frontend Developer</title>

  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />

  <!-- AOS – Animate On Scroll -->
  <link href="https://unpkg.com/aos@2.3.4/dist/aos.css" rel="stylesheet" />

  <!-- Typed.js -->
  <script src="https://unpkg.com/typed.js@2.1.0/dist/typed.umd.js"></script>

  <!-- CountUp.js -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/countup.js/2.8.0/countUp.umd.js"></script>

  <!-- Iconify -->
  <script src="https://code.iconify.design/3/3.1.0/iconify.min.js"></script>

  <style>
    /* ═══════════════════════════════════════════
       RESET & BASE
    ═══════════════════════════════════════════ */
    *, *::before, *::after {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --bg-primary: #030304;
      --bg-secondary: #050507;
      --bg-card: rgba(255, 255, 255, 0.03);
      --bg-card-hover: rgba(255, 255, 255, 0.06);
      --text-primary: #ffffff;
      --text-secondary: #a1a1aa;
      --text-tertiary: #71717a;
      --accent: #6366f1;
      --accent-light: #818cf8;
      --accent-glow: rgba(99, 102, 241, 0.3);
      --border: rgba(255, 255, 255, 0.06);
      --border-hover: rgba(255, 255, 255, 0.12);
      --gradient-1: linear-gradient(135deg, #6366f1, #8b5cf6, #a78bfa);
      --gradient-2: linear-gradient(135deg, #6366f1, #06b6d4);
      --radius: 16px;
      --radius-sm: 12px;
      --radius-xs: 8px;
      --transition: cubic-bezier(0.16, 1, 0.3, 1);
    }

    html {
      scroll-behavior: smooth;
      scroll-padding-top: 80px;
    }

    body {
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
      background: var(--bg-primary);
      color: var(--text-primary);
      line-height: 1.7;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }

    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg-primary); }
    ::-webkit-scrollbar-thumb { background: #27272a; border-radius: 3px; }
    ::-webkit-scrollbar-thumb:hover { background: #3f3f46; }

    /* ═══════════════════════════════════════════
       ANIMATED BACKGROUND
    ═══════════════════════════════════════════ */
    .bg-effects {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
      overflow: hidden;
    }

    .bg-orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(120px);
      opacity: 0.4;
      animation: orbFloat 20s ease-in-out infinite;
    }

    .bg-orb--1 {
      width: 600px;
      height: 600px;
      background: radial-gradient(circle, rgba(99, 102, 241, 0.3), transparent 70%);
      top: -200px;
      left: -100px;
      animation-duration: 25s;
    }

    .bg-orb--2 {
      width: 500px;
      height: 500px;
      background: radial-gradient(circle, rgba(139, 92, 246, 0.2), transparent 70%);
      top: 40%;
      right: -150px;
      animation-duration: 30s;
      animation-delay: -5s;
    }

    .bg-orb--3 {
      width: 400px;
      height: 400px;
      background: radial-gradient(circle, rgba(6, 182, 212, 0.15), transparent 70%);
      bottom: -100px;
      left: 30%;
      animation-duration: 22s;
      animation-delay: -10s;
    }

    @keyframes orbFloat {
      0%, 100% { transform: translate(0, 0) scale(1); }
      25% { transform: translate(60px, -40px) scale(1.1); }
      50% { transform: translate(-30px, 50px) scale(0.95); }
      75% { transform: translate(40px, 20px) scale(1.05); }
    }

    /* Grid pattern overlay */
    .bg-grid {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
      background-image:
        linear-gradient(rgba(255, 255, 255, 0.02) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255, 255, 255, 0.02) 1px, transparent 1px);
      background-size: 60px 60px;
      mask-image: radial-gradient(ellipse 80% 60% at 50% 30%, black 20%, transparent 100%);
    }

    /* Particles canvas */
    #particles-canvas {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
    }

    /* ═══════════════════════════════════════════
       LAYOUT
    ═══════════════════════════════════════════ */
    .container {
      max-width: 960px;
      margin: 0 auto;
      padding: 0 24px;
      position: relative;
      z-index: 1;
    }

    section {
      padding: 100px 0;
      position: relative;
    }

    /* ═══════════════════════════════════════════
       NAVIGATION
    ═══════════════════════════════════════════ */
    .navbar {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 100;
      padding: 16px 24px;
      transition: all 0.4s var(--transition);
    }

    .navbar.scrolled {
      background: rgba(3, 3, 4, 0.8);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      padding: 12px 24px;
    }

    .navbar-inner {
      max-width: 960px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .nav-logo {
      font-size: 16px;
      font-weight: 600;
      color: var(--text-primary);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .nav-logo-icon {
      width: 32px;
      height: 32px;
      border-radius: 8px;
      background: var(--gradient-1);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 14px;
      font-weight: 700;
      color: white;
    }

    .nav-links {
      display: flex;
      gap: 8px;
      list-style: none;
    }

    .nav-links a {
      color: var(--text-tertiary);
      text-decoration: none;
      font-size: 13px;
      font-weight: 500;
      padding: 6px 14px;
      border-radius: 20px;
      transition: all 0.3s ease;
      letter-spacing: -0.01em;
    }

    .nav-links a:hover {
      color: var(--text-primary);
      background: rgba(255, 255, 255, 0.06);
    }

    .nav-links a.active {
      color: var(--text-primary);
      background: rgba(99, 102, 241, 0.15);
    }

    .mobile-toggle {
      display: none;
      background: none;
      border: none;
      color: var(--text-secondary);
      cursor: pointer;
      padding: 8px;
    }

    /* ═══════════════════════════════════════════
       HERO
    ═══════════════════════════════════════════ */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding-top: 80px;
      position: relative;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 6px 16px 6px 8px;
      border-radius: 100px;
      border: 1px solid var(--border);
      background: var(--bg-card);
      font-size: 12px;
      font-weight: 500;
      color: var(--text-secondary);
      margin-bottom: 32px;
      animation: fadeInUp 0.8s var(--transition) both;
    }

    .hero-badge-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: #22c55e;
      position: relative;
    }

    .hero-badge-dot::after {
      content: '';
      position: absolute;
      inset: -3px;
      border-radius: 50%;
      background: #22c55e;
      opacity: 0.4;
      animation: pulse 2s ease-in-out infinite;
    }

    @keyframes pulse {
      0%, 100% { transform: scale(1); opacity: 0.4; }
      50% { transform: scale(1.8); opacity: 0; }
    }

    .hero h1 {
      font-size: clamp(40px, 8vw, 72px);
      font-weight: 700;
      line-height: 1.05;
      letter-spacing: -0.04em;
      margin-bottom: 8px;
      animation: fadeInUp 0.8s var(--transition) 0.1s both;
    }

    .hero h1 .wave {
      display: inline-block;
      animation: wave 2.5s ease-in-out infinite;
      transform-origin: 70% 70%;
    }

    @keyframes wave {
      0%, 60%, 100% { transform: rotate(0deg); }
      10% { transform: rotate(14deg); }
      20% { transform: rotate(-8deg); }
      30% { transform: rotate(14deg); }
      40% { transform: rotate(-4deg); }
      50% { transform: rotate(10deg); }
    }

    .hero-tagline {
      font-size: clamp(14px, 2.5vw, 18px);
      font-weight: 400;
      color: var(--text-secondary);
      margin-bottom: 12px;
      min-height: 28px;
      animation: fadeInUp 0.8s var(--transition) 0.2s both;
    }

    .hero-tagline .typed-cursor {
      color: var(--accent-light);
    }

    .hero-views {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-size: 12px;
      color: var(--text-tertiary);
      animation: fadeInUp 0.8s var(--transition) 0.3s both;
    }

    .hero-views-count {
      color: var(--accent-light);
      font-weight: 600;
      font-variant-numeric: tabular-nums;
    }

    .hero-scroll-hint {
      position: absolute;
      bottom: 40px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      color: var(--text-tertiary);
      font-size: 11px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      animation: fadeInUp 0.8s var(--transition) 0.5s both;
    }

    .hero-scroll-line {
      width: 1px;
      height: 40px;
      background: linear-gradient(to bottom, var(--accent-light), transparent);
      animation: scrollLine 2s ease-in-out infinite;
    }

    @keyframes scrollLine {
      0% { transform: scaleY(0); transform-origin: top; opacity: 0; }
      50% { transform: scaleY(1); transform-origin: top; opacity: 1; }
      51% { transform: scaleY(1); transform-origin: bottom; opacity: 1; }
      100% { transform: scaleY(0); transform-origin: bottom; opacity: 0; }
    }

    /* ═══════════════════════════════════════════
       SECTION HEADERS
    ═══════════════════════════════════════════ */
    .section-label {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 11px;
      font-weight: 600;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent-light);
      margin-bottom: 16px;
    }

    .section-label::before {
      content: '';
      width: 20px;
      height: 1px;
      background: var(--accent-light);
    }

    .section-title {
      font-size: clamp(28px, 5vw, 40px);
      font-weight: 600;
      letter-spacing: -0.03em;
      line-height: 1.15;
      margin-bottom: 20px;
    }

    .section-desc {
      font-size: 16px;
      color: var(--text-secondary);
      max-width: 600px;
      line-height: 1.75;
    }

    /* ═══════════════════════════════════════════
       ABOUT
    ═══════════════════════════════════════════ */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }

    .about-visual {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .about-avatar-ring {
      width: 280px;
      height: 280px;
      border-radius: 50%;
      padding: 3px;
      background: var(--gradient-1);
      animation: ringRotate 8s linear infinite;
      position: relative;
    }

    @keyframes ringRotate {
      0% { background: var(--gradient-1); }
      25% { background: linear-gradient(135deg, #8b5cf6, #a78bfa, #6366f1); }
      50% { background: linear-gradient(135deg, #a78bfa, #6366f1, #8b5cf6); }
      75% { background: linear-gradient(135deg, #6366f1, #8b5cf6, #a78bfa); }
      100% { background: var(--gradient-1); }
    }

    .about-avatar-inner {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background: var(--bg-secondary);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 80px;
      position: relative;
      overflow: hidden;
    }

    .about-avatar-inner::after {
      content: '';
      position: absolute;
      inset: 0;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 30%, rgba(99, 102, 241, 0.1), transparent 60%);
    }

    .about-float-card {
      position: absolute;
      background: rgba(5, 5, 7, 0.9);
      backdrop-filter: blur(20px);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 12px 16px;
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 13px;
      font-weight: 500;
      white-space: nowrap;
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
    }

    .about-float-card--1 {
      top: 20px;
      right: -20px;
      animation: floatCard1 4s ease-in-out infinite;
    }

    .about-float-card--2 {
      bottom: 30px;
      left: -20px;
      animation: floatCard2 5s ease-in-out infinite;
    }

    .about-float-card--3 {
      bottom: -10px;
      right: 10px;
      animation: floatCard1 4.5s ease-in-out infinite 0.5s;
    }

    @keyframes floatCard1 {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }

    @keyframes floatCard2 {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(8px); }
    }

    .float-icon {
      width: 32px;
      height: 32px;
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      flex-shrink: 0;
    }

    .about-text p {
      color: var(--text-secondary);
      font-size: 15px;
      line-height: 1.8;
      margin-bottom: 24px;
    }

    .about-highlights {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .about-highlight-tag {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 6px 14px;
      border-radius: 100px;
      border: 1px solid var(--border);
      background: var(--bg-card);
      font-size: 12px;
      font-weight: 500;
      color: var(--text-secondary);
      transition: all 0.3s ease;
    }

    .about-highlight-tag:hover {
      border-color: var(--accent);
      color: var(--accent-light);
      background: rgba(99, 102, 241, 0.08);
    }

    /* ═══════════════════════════════════════════
       SKILLS
    ═══════════════════════════════════════════ */
    .skills-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-top: 48px;
    }

    .skill-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 28px 24px;
      text-align: center;
      transition: all 0.4s var(--transition);
      position: relative;
      overflow: hidden;
      cursor: default;
    }

    .skill-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 50% 0%, var(--accent-glow), transparent 70%);
      opacity: 0;
      transition: opacity 0.4s ease;
    }

    .skill-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-4px);
      background: var(--bg-card-hover);
    }

    .skill-card:hover::before {
      opacity: 1;
    }

    .skill-icon-wrap {
      width: 56px;
      height: 56px;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 16px;
      font-size: 28px;
      position: relative;
      z-index: 1;
      transition: transform 0.4s var(--transition);
    }

    .skill-card:hover .skill-icon-wrap {
      transform: scale(1.1);
    }

    .skill-name {
      font-size: 14px;
      font-weight: 600;
      margin-bottom: 4px;
      position: relative;
      z-index: 1;
    }

    .skill-level {
      font-size: 11px;
      color: var(--text-tertiary);
      position: relative;
      z-index: 1;
    }

    .skill-progress-bar {
      width: 100%;
      height: 3px;
      background: rgba(255, 255, 255, 0.06);
      border-radius: 2px;
      margin-top: 16px;
      overflow: hidden;
      position: relative;
      z-index: 1;
    }

    .skill-progress-fill {
      height: 100%;
      border-radius: 2px;
      width: 0%;
      transition: width 1.5s var(--transition);
    }

    .skill-card.in-view .skill-progress-fill {
      /* Width set via inline style */
    }

    /* Skill color themes */
    .skill-html .skill-icon-wrap { background: rgba(227, 79, 38, 0.15); }
    .skill-html .skill-progress-fill { background: #E34F26; }

    .skill-css .skill-icon-wrap { background: rgba(21, 114, 182, 0.15); }
    .skill-css .skill-progress-fill { background: #1572B6; }

    .skill-bootstrap .skill-icon-wrap { background: rgba(121, 82, 179, 0.15); }
    .skill-bootstrap .skill-progress-fill { background: #7952B3; }

    .skill-js .skill-icon-wrap { background: rgba(247, 223, 30, 0.12); }
    .skill-js .skill-progress-fill { background: #F7DF1E; }

    .skill-git .skill-icon-wrap { background: rgba(240, 80, 50, 0.15); }
    .skill-git .skill-progress-fill { background: #F05032; }

    .skill-github .skill-icon-wrap { background: rgba(255, 255, 255, 0.08); }
    .skill-github .skill-progress-fill { background: #ffffff; }

    /* ═══════════════════════════════════════════
       GOALS
    ═══════════════════════════════════════════ */
    .goals-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 40px;
    }

    .goal-item {
      display: flex;
      align-items: center;
      gap: 16px;
      padding: 20px 24px;
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      transition: all 0.3s ease;
      cursor: default;
    }

    .goal-item:hover {
      border-color: var(--border-hover);
      background: var(--bg-card-hover);
      transform: translateX(8px);
    }

    .goal-number {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      background: rgba(99, 102, 241, 0.1);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 13px;
      font-weight: 700;
      color: var(--accent-light);
      flex-shrink: 0;
      transition: all 0.3s ease;
    }

    .goal-item:hover .goal-number {
      background: var(--accent);
      color: white;
    }

    .goal-text {
      font-size: 15px;
      font-weight: 500;
      color: var(--text-secondary);
      transition: color 0.3s ease;
    }

    .goal-item:hover .goal-text {
      color: var(--text-primary);
    }

    /* ═══════════════════════════════════════════
       PROJECTS
    ═══════════════════════════════════════════ */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 20px;
      margin-top: 48px;
    }

    .project-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      overflow: hidden;
      transition: all 0.4s var(--transition);
      position: relative;
    }

    .project-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-6px);
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.4);
    }

    .project-thumbnail {
      width: 100%;
      height: 180px;
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.1), rgba(139, 92, 246, 0.05));
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      overflow: hidden;
    }

    .project-thumbnail::before {
      content: '';
      position: absolute;
      inset: 0;
      background-image:
        radial-gradient(circle at 20% 50%, rgba(99, 102, 241, 0.15) 0%, transparent 50%),
        radial-gradient(circle at 80% 20%, rgba(139, 92, 246, 0.1) 0%, transparent 50%);
    }

    .project-thumbnail-icon {
      font-size: 48px;
      opacity: 0.3;
      position: relative;
      z-index: 1;
    }

    .project-body {
      padding: 24px;
    }

    .project-title {
      font-size: 17px;
      font-weight: 600;
      margin-bottom: 8px;
      letter-spacing: -0.01em;
    }

    .project-desc {
      font-size: 13px;
      color: var(--text-tertiary);
      line-height: 1.6;
      margin-bottom: 16px;
    }

    .project-techs {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-bottom: 20px;
    }

    .project-tech {
      font-size: 10px;
      font-weight: 600;
      letter-spacing: 0.05em;
      text-transform: uppercase;
      color: var(--accent-light);
      background: rgba(99, 102, 241, 0.1);
      padding: 4px 10px;
      border-radius: 6px;
    }

    .project-links {
      display: flex;
      gap: 10px;
    }

    .project-link {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-size: 12px;
      font-weight: 500;
      color: var(--text-tertiary);
      text-decoration: none;
      padding: 6px 14px;
      border-radius: 8px;
      border: 1px solid var(--border);
      transition: all 0.3s ease;
    }

    .project-link:hover {
      color: var(--text-primary);
      border-color: var(--border-hover);
      background: rgba(255, 255, 255, 0.04);
    }

    .project-link--primary {
      background: var(--accent);
      border-color: var(--accent);
      color: white;
    }

    .project-link--primary:hover {
      background: var(--accent-light);
      border-color: var(--accent-light);
      color: white;
    }

    /* ═══════════════════════════════════════════
       JOURNEY TIMELINE
    ═══════════════════════════════════════════ */
    .journey-timeline {
      margin-top: 48px;
      position: relative;
      padding-left: 40px;
    }

    .journey-timeline::before {
      content: '';
      position: absolute;
      left: 15px;
      top: 0;
      bottom: 0;
      width: 1px;
      background: linear-gradient(to bottom, var(--accent), var(--border) 30%, var(--border) 70%, transparent);
    }

    .journey-item {
      position: relative;
      padding-bottom: 40px;
    }

    .journey-item:last-child {
      padding-bottom: 0;
    }

    .journey-dot {
      position: absolute;
      left: -33px;
      top: 4px;
      width: 14px;
      height: 14px;
      border-radius: 50%;
      border: 2px solid var(--accent);
      background: var(--bg-primary);
      z-index: 1;
    }

    .journey-item.active .journey-dot {
      background: var(--accent);
      box-shadow: 0 0 12px var(--accent-glow);
    }

    .journey-item.active .journey-dot::after {
      content: '';
      position: absolute;
      inset: -5px;
      border-radius: 50%;
      border: 1px solid var(--accent);
      opacity: 0.3;
      animation: journeyPulse 2s ease-in-out infinite;
    }

    @keyframes journeyPulse {
      0%, 100% { transform: scale(1); opacity: 0.3; }
      50% { transform: scale(1.5); opacity: 0; }
    }

    .journey-status {
      font-size: 10px;
      font-weight: 700;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent-light);
      margin-bottom: 4px;
    }

    .journey-item:not(.active) .journey-status {
      color: var(--text-tertiary);
    }

    .journey-title {
      font-size: 16px;
      font-weight: 600;
      margin-bottom: 6px;
    }

    .journey-desc {
      font-size: 13px;
      color: var(--text-tertiary);
      line-height: 1.6;
    }

    /* ═══════════════════════════════════════════
       STATS
    ═══════════════════════════════════════════ */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
      margin-top: 48px;
    }

    .stat-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 28px 20px;
      text-align: center;
      transition: all 0.3s ease;
    }

    .stat-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-3px);
    }

    .stat-value {
      font-size: 32px;
      font-weight: 700;
      letter-spacing: -0.03em;
      background: var(--gradient-1);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      margin-bottom: 4px;
      font-variant-numeric: tabular-nums;
    }

    .stat-label {
      font-size: 12px;
      color: var(--text-tertiary);
      font-weight: 500;
    }

    .stats-charts {
      display: grid;
      grid-template-columns: 2fr 1fr;
      gap: 20px;
      margin-top: 24px;
    }

    .stats-chart-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 24px;
    }

    .stats-chart-title {
      font-size: 13px;
      font-weight: 600;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .lang-bar {
      display: flex;
      height: 8px;
      border-radius: 4px;
      overflow: hidden;
      margin-bottom: 20px;
      background: rgba(255, 255, 255, 0.04);
    }

    .lang-segment {
      height: 100%;
      transition: width 1.5s var(--transition);
    }

    .lang-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
    }

    .lang-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 13px;
    }

    .lang-item-left {
      display: flex;
      align-items: center;
      gap: 8px;
      color: var(--text-secondary);
    }

    .lang-dot {
      width: 10px;
      height: 10px;
      border-radius: 3px;
    }

    .lang-percent {
      color: var(--text-tertiary);
      font-weight: 500;
      font-variant-numeric: tabular-nums;
    }

    .streak-grid {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 3px;
    }

    .streak-cell {
      aspect-ratio: 1;
      border-radius: 3px;
      background: rgba(255, 255, 255, 0.04);
      transition: all 0.3s ease;
    }

    .streak-cell.active {
      background: var(--accent);
      opacity: 0.7;
    }

    .streak-cell.active.high {
      opacity: 0.85;
    }

    .streak-cell.active.max {
      opacity: 1;
    }

    /* ═══════════════════════════════════════════
       CONNECT
    ═══════════════════════════════════════════ */
    .connect-cards {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-top: 48px;
    }

    .connect-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: var(--radius-sm);
      padding: 32px 24px;
      text-align: center;
      text-decoration: none;
      color: inherit;
      transition: all 0.4s var(--transition);
      position: relative;
      overflow: hidden;
    }

    .connect-card::before {
      content: '';
      position: absolute;
      inset: 0;
      opacity: 0;
      transition: opacity 0.4s ease;
    }

    .connect-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-6px);
      box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
    }

    .connect-card:hover::before {
      opacity: 1;
    }

    .connect-card--linkedin::before {
      background: radial-gradient(circle at 50% 0%, rgba(10, 102, 194, 0.15), transparent 70%);
    }
    .connect-card--github::before {
      background: radial-gradient(circle at 50% 0%, rgba(255, 255, 255, 0.08), transparent 70%);
    }
    .connect-card--email::before {
      background: radial-gradient(circle at 50% 0%, rgba(234, 67, 53, 0.12), transparent 70%);
    }

    .connect-icon {
      width: 52px;
      height: 52px;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 16px;
      font-size: 24px;
      position: relative;
      z-index: 1;
      transition: transform 0.4s var(--transition);
    }

    .connect-card:hover .connect-icon {
      transform: scale(1.1);
    }

    .connect-card--linkedin .connect-icon { background: rgba(10, 102, 194, 0.15); color: #0A66C2; }
    .connect-card--github .connect-icon { background: rgba(255, 255, 255, 0.08); color: #fff; }
    .connect-card--email .connect-icon { background: rgba(234, 67, 53, 0.12); color: #EA4335; }

    .connect-name {
      font-size: 15px;
      font-weight: 600;
      margin-bottom: 4px;
      position: relative;
      z-index: 1;
    }

    .connect-handle {
      font-size: 12px;
      color: var(--text-tertiary);
      position: relative;
      z-index: 1;
    }

    .connect-arrow {
      position: absolute;
      top: 16px;
      right: 16px;
      font-size: 16px;
      color: var(--text-tertiary);
      opacity: 0;
      transform: translate(-4px, 4px);
      transition: all 0.3s ease;
      z-index: 1;
    }

    .connect-card:hover .connect-arrow {
      opacity: 1;
      transform: translate(0, 0);
    }

    /* ═══════════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════════ */
    .footer {
      padding: 40px 0;
      text-align: center;
      border-top: 1px solid var(--border);
      position: relative;
      z-index: 1;
    }

    .footer-quote {
      font-size: 14px;
      font-style: italic;
      color: var(--text-tertiary);
      margin-bottom: 12px;
    }

    .footer-text {
      font-size: 12px;
      color: var(--text-tertiary);
    }

    .footer-text .heart {
      color: var(--accent-light);
      display: inline-block;
      animation: heartbeat 1.5s ease-in-out infinite;
    }

    @keyframes heartbeat {
      0%, 100% { transform: scale(1); }
      15% { transform: scale(1.15); }
      30% { transform: scale(1); }
      45% { transform: scale(1.1); }
    }

    /* ═══════════════════════════════════════════
       SEPARATOR
    ═══════════════════════════════════════════ */
    .section-sep {
      height: 1px;
      background: linear-gradient(to right, transparent, var(--border) 20%, var(--border) 80%, transparent);
      max-width: 600px;
      margin: 0 auto;
    }

    /* ═══════════════════════════════════════════
       ANIMATIONS
    ═══════════════════════════════════════════ */
    @keyframes fadeInUp {
      from {
        opacity: 0;
        transform: translateY(24px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    /* ═══════════════════════════════════════════
       MOBILE NAV
    ═══════════════════════════════════════════ */
    .mobile-menu {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(3, 3, 4, 0.95);
      backdrop-filter: blur(20px);
      z-index: 99;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .mobile-menu.open {
      display: flex;
    }

    .mobile-menu a {
      color: var(--text-secondary);
      text-decoration: none;
      font-size: 18px;
      font-weight: 500;
      padding: 12px 32px;
      border-radius: 12px;
      transition: all 0.3s ease;
    }

    .mobile-menu a:hover {
      color: var(--text-primary);
      background: rgba(255, 255, 255, 0.06);
    }

    .mobile-close {
      position: absolute;
      top: 20px;
      right: 24px;
      background: none;
      border: none;
      color: var(--text-secondary);
      font-size: 24px;
      cursor: pointer;
    }

    /* ═══════════════════════════════════════════
       RESPONSIVE
    ═══════════════════════════════════════════ */
    @media (max-width: 768px) {
      .nav-links { display: none; }
      .mobile-toggle { display: block; }

      .about-grid {
        grid-template-columns: 1fr;
        gap: 40px;
      }

      .about-visual { order: -1; }

      .about-avatar-ring {
        width: 200px;
        height: 200px;
      }

      .about-avatar-inner { font-size: 56px; }

      .about-float-card { display: none; }

      .skills-grid {
        grid-template-columns: repeat(2, 1fr);
      }

      .projects-grid {
        grid-template-columns: 1fr;
      }

      .stats-grid {
        grid-template-columns: repeat(2, 1fr);
      }

      .stats-charts {
        grid-template-columns: 1fr;
      }

      .connect-cards {
        grid-template-columns: 1fr;
        max-width: 360px;
        margin-left: auto;
        margin-right: auto;
        margin-top: 48px;
      }

      section {
        padding: 72px 0;
      }
    }

    @media (max-width: 480px) {
      .skills-grid {
        grid-template-columns: 1fr;
      }

      .stats-grid {
        grid-template-columns: repeat(2, 1fr);
        gap: 10px;
      }

      .stat-card {
        padding: 20px 14px;
      }

      .stat-value {
        font-size: 26px;
      }
    }
  </style>
</head>
<body>

  <!-- ════════ BACKGROUND EFFECTS ════════ -->
  <div class="bg-effects">
    <div class="bg-orb bg-orb--1"></div>
    <div class="bg-orb bg-orb--2"></div>
    <div class="bg-orb bg-orb--3"></div>
  </div>
  <div class="bg-grid"></div>
  <canvas id="particles-canvas"></canvas>

  <!-- ════════ NAVIGATION ════════ -->
  <nav class="navbar" id="navbar">
    <div class="navbar-inner">
      <a href="#hero" class="nav-logo">
        <div class="nav-logo-icon">M</div>
        Manahil
      </a>
      <ul class="nav-links">
        <li><a href="#about">About</a></li>
        <li><a href="#skills">Skills</a></li>
        <li><a href="#goals">Goals</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#journey">Journey</a></li>
        <li><a href="#stats">Stats</a></li>
        <li><a href="#connect">Connect</a></li>
      </ul>
      <button class="mobile-toggle" id="mobileToggle" aria-label="Open menu">
        <span class="iconify" data-icon="mdi:menu" data-width="24"></span>
      </button>
    </div>
  </nav>

  <!-- Mobile Menu -->
  <div class="mobile-menu" id="mobileMenu">
    <button class="mobile-close" id="mobileClose" aria-label="Close menu">
      <span class="iconify" data-icon="mdi:close" data-width="24"></span>
    </button>
    <a href="#about" class="mobile-link">About</a>
    <a href="#skills" class="mobile-link">Skills</a>
    <a href="#goals" class="mobile-link">Goals</a>
    <a href="#projects" class="mobile-link">Projects</a>
    <a href="#journey" class="mobile-link">Journey</a>
    <a href="#stats" class="mobile-link">Stats</a>
    <a href="#connect" class="mobile-link">Connect</a>
  </div>

  <!-- ════════ HERO ════════ -->
  <section class="hero" id="hero">
    <div class="container">
      <div class="hero-badge">
        <div class="hero-badge-dot"></div>
        Open to learning & collaboration
      </div>
      <h1>Hi, I'm Manahil Zahra <span class="wave">👋</span></h1>
      <div class="hero-tagline">
        <span id="typed-output"></span>
      </div>
      <div class="hero-views">
        <span class="iconify" data-icon="mdi:eye-outline" data-width="14"></span>
        <span class="hero-views-count" id="viewsCount">0</span> profile views
      </div>
      <div class="hero-scroll-hint">
        <span>Scroll</span>
        <div class="hero-scroll-line"></div>
      </div>
    </div>
  </section>

  <!-- ════════ ABOUT ════════ -->
  <section id="about">
    <div class="container">
      <div class="about-grid">
        <div class="about-visual" data-aos="fade-right" data-aos-duration="800">
          <div class="about-avatar-ring">
            <div class="about-avatar-inner">
              👩‍💻
            </div>
          </div>
          <div class="about-float-card about-float-card--1">
            <div class="float-icon" style="background: rgba(99,102,241,0.15);">
              <span class="iconify" data-icon="mdi:code-braces" data-width="18" style="color: #818cf8;"></span>
            </div>
            <span>Frontend Dev</span>
          </div>
          <div class="about-float-card about-float-card--2">
            <div class="float-icon" style="background: rgba(34,197,94,0.15);">
              <span class="iconify" data-icon="mdi:school-outline" data-width="18" style="color: #22c55e;"></span>
            </div>
            <span>SE Student</span>
          </div>
          <div class="about-float-card about-float-card--3">
            <div class="float-icon" style="background: rgba(247,223,30,0.12);">
              <span class="iconify" data-icon="mdi:lightbulb-outline" data-width="18" style="color: #F7DF1E;"></span>
            </div>
            <span>Curious Learner</span>
          </div>
        </div>
        <div data-aos="fade-left" data-aos-duration="800" data-aos-delay="200">
          <div class="section-label">About Me</div>
          <h2 class="section-title">A student building her path, one line of code at a time.</h2>
          <div class="about-text">
            <p>
              I'm a <strong style="color: var(--text-primary);">Software Engineering student</strong> with a growing passion for <strong style="color: var(--text-primary);">Frontend Web Development</strong>. I'm currently at the beginning of my coding journey — learning the fundamentals, building small projects, and improving with every line of code I write.
            </p>
            <p>
              Right now, I'm focused on exploring <strong style="color: var(--text-primary);">HTML, CSS, Bootstrap, and JavaScript</strong> to understand how the web works from the ground up. I genuinely enjoy turning ideas into visual, interactive web pages, even if they're simple ones.
            </p>
            <p>
              I believe that <strong style="color: var(--accent-light);">consistency matters more than speed</strong>. I'm not in a rush — I'm here to learn deeply, build steadily, and grow into a skilled developer over time.
            </p>
          </div>
          <div class="about-highlights">
            <span class="about-highlight-tag">
              <span class="iconify" data-icon="mdi:check-circle-outline" data-width="14" style="color: var(--accent-light);"></span>
              Consistent Learner
            </span>
            <span class="about-highlight-tag">
              <span class="iconify" data-icon="mdi:check-circle-outline" data-width="14" style="color: var(--accent-light);"></span>
              Project Builder
            </span>
            <span class="about-highlight-tag">
              <span class="iconify" data-icon="mdi:check-circle-outline" data-width="14" style="color: var(--accent-light);"></span>
              Curious Mind
            </span>
            <span class="about-highlight-tag">
              <span class="iconify" data-icon="mdi:check-circle-outline" data-width="14" style="color: var(--accent-light);"></span>
              Open to Improve
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ SKILLS ════════ -->
  <section id="skills">
    <div class="container">
      <div data-aos="fade-up" data-aos-duration="700">
        <div class="section-label">Currently Learning</div>
        <h2 class="section-title">Technologies I'm exploring right now.</h2>
        <p class="section-desc">
          I'm at the beginner stage with these technologies. Each day I practice, I get a little better. Progress, not perfection.
        </p>
      </div>
      <div class="skills-grid">
        <div class="skill-card skill-html" data-aos="fade-up" data-aos-delay="0" data-progress="70">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="logos:html-5" data-width="28"></span>
          </div>
          <div class="skill-name">HTML5</div>
          <div class="skill-level">Learning</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="70"></div>
          </div>
        </div>
        <div class="skill-card skill-css" data-aos="fade-up" data-aos-delay="80" data-progress="60">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="logos:css-3" data-width="28"></span>
          </div>
          <div class="skill-name">CSS3</div>
          <div class="skill-level">Learning</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="60"></div>
          </div>
        </div>
        <div class="skill-card skill-bootstrap" data-aos="fade-up" data-aos-delay="160" data-progress="55">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="logos:bootstrap" data-width="28"></span>
          </div>
          <div class="skill-name">Bootstrap</div>
          <div class="skill-level">Learning</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="55"></div>
          </div>
        </div>
        <div class="skill-card skill-js" data-aos="fade-up" data-aos-delay="240" data-progress="35">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="logos:javascript" data-width="28"></span>
          </div>
          <div class="skill-name">JavaScript</div>
          <div class="skill-level">Just Started</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="35"></div>
          </div>
        </div>
        <div class="skill-card skill-git" data-aos="fade-up" data-aos-delay="320" data-progress="45">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="logos:git-icon" data-width="28"></span>
          </div>
          <div class="skill-name">Git</div>
          <div class="skill-level">Learning</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="45"></div>
          </div>
        </div>
        <div class="skill-card skill-github" data-aos="fade-up" data-aos-delay="400" data-progress="50">
          <div class="skill-icon-wrap">
            <span class="iconify" data-icon="mdi:github" data-width="28" style="color: #fff;"></span>
          </div>
          <div class="skill-name">GitHub</div>
          <div class="skill-level">Learning</div>
          <div class="skill-progress-bar">
            <div class="skill-progress-fill" style="width: 0%;" data-width="50"></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ GOALS ════════ -->
  <section id="goals">
    <div class="container">
      <div data-aos="fade-up" data-aos-duration="700">
        <div class="section-label">My Goals</div>
        <h2 class="section-title">Where I'm heading.</h2>
        <p class="section-desc">
          These aren't overnight targets. They're milestones I'm working toward with patience and consistency.
        </p>
      </div>
      <div class="goals-list">
        <div class="goal-item" data-aos="fade-up" data-aos-delay="0">
          <div class="goal-number">01</div>
          <div class="goal-text">Become a skilled Frontend Developer</div>
        </div>
        <div class="goal-item" data-aos="fade-up" data-aos-delay="60">
          <div class="goal-number">02</div>
          <div class="goal-text">Build responsive and modern websites</div>
        </div>
        <div class="goal-item" data-aos="fade-up" data-aos-delay="120">
          <div class="goal-number">03</div>
          <div class="goal-text">Improve JavaScript and programming fundamentals</div>
        </div>
        <div class="goal-item" data-aos="fade-up" data-aos-delay="180">
          <div class="goal-number">04</div>
          <div class="goal-text">Learn more advanced frontend technologies</div>
        </div>
        <div class="goal-item" data-aos="fade-up" data-aos-delay="240">
          <div class="goal-number">05</div>
          <div class="goal-text">Build real-world projects that solve actual problems</div>
        </div>
        <div class="goal-item" data-aos="fade-up" data-aos-delay="300">
          <div class="goal-number">06</div>
          <div class="goal-text">Eventually explore other areas of Software Engineering</div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ PROJECTS ════════ -->
  <section id="projects">
    <div class="container">
      <div data-aos="fade-up" data-aos-duration="700">
        <div class="section-label">Projects</div>
        <h2 class="section-title">Things I'm building.</h2>
        <p class="section-desc">
          I'm currently working on my first projects. This section will grow as I build and learn more.
        </p>
      </div>
      <div class="projects-grid">
        <!-- Project 1 -->
        <div class="project-card" data-aos="fade-up" data-aos-delay="0">
          <div class="project-thumbnail">
            <div class="project-thumbnail-icon">
              <span class="iconify" data-icon="mdi:web" data-width="48" style="color: rgba(99,102,241,0.4);"></span>
            </div>
          </div>
          <div class="project-body">
            <div class="project-title">Coming Soon</div>
            <div class="project-desc">Placeholder for my first project — something simple but meaningful.</div>
            <div class="project-techs">
              <span class="project-tech">HTML</span>
              <span class="project-tech">CSS</span>
            </div>
            <div class="project-links">
              <a href="#" class="project-link project-link--primary">
                <span class="iconify" data-icon="mdi:open-in-new" data-width="14"></span>
                Live Demo
              </a>
              <a href="#" class="project-link">
                <span class="iconify" data-icon="mdi:github" data-width="14"></span>
                Code
              </a>
            </div>
          </div>
        </div>
        <!-- Project 2 -->
        <div class="project-card" data-aos="fade-up" data-aos-delay="100">
          <div class="project-thumbnail" style="background: linear-gradient(135deg, rgba(139,92,246,0.1), rgba(99,102,241,0.05));">
            <div class="project-thumbnail-icon">
              <span class="iconify" data-icon="mdi:palette-outline" data-width="48" style="color: rgba(139,92,246,0.4);"></span>
            </div>
          </div>
          <div class="project-body">
            <div class="project-title">Coming Soon</div>
            <div class="project-desc">Placeholder for my second project — experimenting with interactivity.</div>
            <div class="project-techs">
              <span class="project-tech">HTML</span>
              <span class="project-tech">CSS</span>
              <span class="project-tech">JS</span>
            </div>
            <div class="project-links">
              <a href="#" class="project-link project-link--primary">
                <span class="iconify" data-icon="mdi:open-in-new" data-width="14"></span>
                Live Demo
              </a>
              <a href="#" class="project-link">
                <span class="iconify" data-icon="mdi:github" data-width="14"></span>
                Code
              </a>
            </div>
          </div>
        </div>
        <!-- Project 3 -->
        <div class="project-card" data-aos="fade-up" data-aos-delay="200">
          <div class="project-thumbnail" style="background: linear-gradient(135deg, rgba(6,182,212,0.1), rgba(99,102,241,0.05));">
            <div class="project-thumbnail-icon">
              <span class="iconify" data-icon="mdi:cellphone" data-width="48" style="color: rgba(6,182,212,0.4);"></span>
            </div>
          </div>
          <div class="project-body">
            <div class="project-title">Coming Soon</div>
            <div class="project-desc">Placeholder for my third project — focusing on responsive design.</div>
            <div class="project-techs">
              <span class="project-tech">HTML</span>
              <span class="project-tech">Bootstrap</span>
            </div>
            <div class="project-links">
              <a href="#" class="project-link project-link--primary">
                <span class="iconify" data-icon="mdi:open-in-new" data-width="14"></span>
                Live Demo
              </a>
              <a href="#" class="project-link">
                <span class="iconify" data-icon="mdi:github" data-width="14"></span>
                Code
              </a>
            </div>
          </div>
        </div>
        <!-- Project 4 -->
        <div class="project-card" data-aos="fade-up" data-aos-delay="300">
          <div class="project-thumbnail" style="background: linear-gradient(135deg, rgba(247,223,30,0.06), rgba(99,102,241,0.04));">
            <div class="project-thumbnail-icon">
              <span class="iconify" data-icon="mdi:rocket-launch-outline" data-width="48" style="color: rgba(247,223,30,0.3);"></span>
            </div>
          </div>
          <div class="project-body">
            <div class="project-title">Coming Soon</div>
            <div class="project-desc">Placeholder for a future project — pushing my skills further.</div>
            <div class="project-techs">
              <span class="project-tech">TBD</span>
            </div>
            <div class="project-links">
              <a href="#" class="project-link project-link--primary">
                <span class="iconify" data-icon="mdi:open-in-new" data-width="14"></span>
                Live Demo
              </a>
              <a href="#" class="project-link">
                <span class="iconify" data-icon="mdi:github" data-width="14"></span>
                Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ JOURNEY ════════ -->
  <section id="journey">
    <div class="container">
      <div data-aos="fade-up" data-aos-duration="700">
        <div class="section-label">My Learning Journey</div>
        <h2 class="section-title">Step by step, no shortcuts.</h2>
        <p class="section-desc">
          My path into development is straightforward — I'm learning in public, making mistakes, fixing them, and moving forward.
        </p>
      </div>
      <div class="journey-timeline">
        <div class="journey-item active" data-aos="fade-up" data-aos-delay="0">
          <div class="journey-dot"></div>
          <div class="journey-status">Currently</div>
          <div class="journey-title">Learning HTML, CSS, Bootstrap & JavaScript</div>
          <div class="journey-desc">Building a solid foundation in web technologies. Practicing daily through small exercises and projects.</div>
        </div>
        <div class="journey-item" data-aos="fade-up" data-aos-delay="100">
          <div class="journey-dot"></div>
          <div class="journey-status">Practicing</div>
          <div class="journey-title">Building small web pages and UI components</div>
          <div class="journey-desc">Applying what I learn by creating real things — landing pages, cards, layouts, and more.</div>
        </div>
        <div class="journey-item" data-aos="fade-up" data-aos-delay="200">
          <div class="journey-dot"></div>
          <div class="journey-status">Exploring</div>
          <div class="journey-title">Git, GitHub, and developer workflows</div>
          <div class="journey-desc">Learning how to version control my code, collaborate, and present my work professionally.</div>
        </div>
        <div class="journey-item" data-aos="fade-up" data-aos-delay="300">
          <div class="journey-dot"></div>
          <div class="journey-status">Next Steps</div>
          <div class="journey-title">Deepen JavaScript, then move to frameworks</div>
          <div class="journey-desc">Once I'm comfortable with the basics, I'll level up with React or Vue and modern tooling.</div>
        </div>
        <div class="journey-item" data-aos="fade-up" data-aos-delay="400">
          <div class="journey-dot"></div>
          <div class="journey-status">Long Term</div>
          <div class="journey-title">Grow into a well-rounded Software Engineer</div>
          <div class="journey-desc">Frontend is my starting point. Over time, I plan to explore backend, databases, and beyond.</div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ STATS ════════ -->
  <section id="stats">
    <div class="container">
      <div data-aos="fade-up" data-aos-duration="700">
        <div class="section-label">GitHub Stats</div>
        <h2 class="section-title">My activity at a glance.</h2>
        <p class="section-desc">
          These numbers will grow as I code more. Every commit counts.
        </p>
      </div>
      <div class="stats-grid">
        <div class="stat-card" data-aos="fade-up" data-aos-delay="0">
          <div class="stat-value"><span class="counter" data-target="12">0</span></div>
          <div class="stat-label">Repositories</div>
        </div>
        <div class="stat-card" data-aos="fade-up" data-aos-delay="80">
          <div class="stat-value"><span class="counter" data-target="87">0</span></div>
          <div class="stat-label">Commits</div>
        </div>
        <div class="stat-card" data-aos="fade-up" data-aos-delay="160">
          <div class="stat-value"><span class="counter" data-target="15">0</span></div>
          <div class="stat-label">Streak Days</div>
        </div>
        <div class="stat-card" data-aos="fade-up" data-aos-delay="240">
          <div class="stat-value"><span class="counter" data-target="3">0</span></div>
          <div class="stat-label">PRs Merged</div>
        </div>
      </div>
      <div class="stats-charts">
        <div class="stats-chart-card" data-aos="fade-up" data-aos-delay="0">
          <div class="stats-chart-title">
            <span class="iconify" data-icon="mdi:code-tags" data-width="16" style="color: var(--accent-light);"></span>
            Top Languages
          </div>
          <div class="lang-bar">
            <div class="lang-segment" style="width: 0%; background: #E34F26;" data-width="40"></div>
            <div class="lang-segment" style="width: 0%; background: #1572B6;" data-width="30"></div>
            <div class="lang-segment" style="width: 0%; background: #F7DF1E;" data-width="15"></div>
            <div class="lang-segment" style="width: 0%; background: #7952B3;" data-width="10"></div>
            <div class="lang-segment" style="width: 0%; background: #555;" data-width="5"></div>
          </div>
          <div class="lang-list">
            <div class="lang-item">
              <div class="lang-item-left">
                <div class="lang-dot" style="background: #E34F26;"></div>
                HTML
              </div>
              <div class="lang-percent">40%</div>
            </div>
            <div class="lang-item">
              <div class="lang-item-left">
                <div class="lang-dot" style="background: #1572B6;"></div>
                CSS
              </div>
              <div class="lang-percent">30%</div>
            </div>
            <div class="lang-item">
              <div class="lang-item-left">
                <div class="lang-dot" style="background: #F7DF1E;"></div>
                JavaScript
              </div>
              <div class="lang-percent">15%</div>
            </div>
            <div class="lang-item">
              <div class="lang-item-left">
                <div class="lang-dot" style="background: #7952B3;"></div>
                Bootstrap
              </div>
              <div class="lang-percent">10%</div>
            </div>
            <div class="lang-item">
              <div class="lang-item-left">
                <div class="lang-dot" style="background: #555;"></div>
                Other
              </div>
              <div class="lang-percent">5%</div>
            </div>
          </div>
        </div>
        <div class="stats-chart-card" data-aos="fade-up" data-aos-delay="100">
          <div class="stats-chart-title">
            <span class="iconify" data-icon="mdi:fire" data-width="16" style="color: #f97316;"></span>
            Contribution Activity
          </div>
          <div class="streak-grid" id="streakGrid"></div>
        </div>
      </div>
    </div>
  </section>

  <div class="section-sep"></div>

  <!-- ════════ CONNECT ════════ -->
  <section id="connect">
    <div class="container">
      <div style="text-align: center;" data-aos="fade-up" data-aos-duration="700">
        <div class="section-label" style="justify-content: center;">Connect With Me</div>
        <h2 class="section-title">Let's stay in touch.</h2>
        <p class="section-desc" style="margin: 0 auto;">
          I'm always happy to connect with fellow learners, developers, and anyone who wants to share knowledge or collaborate.
        </p>
      </div>
      <div class="connect-cards">
        <a href="https://linkedin.com/in/your-linkedin-username" target="_blank" class="connect-card connect-card--linkedin" data-aos="fade-up" data-aos-delay="0">
          <span class="connect-arrow">
            <span class="iconify" data-icon="mdi:arrow-top-right" data-width="16"></span>
          </span>
          <div class="connect-icon">
            <span class="iconify" data-icon="mdi:linkedin" data-width="24"></span>
          </div>
          <div class="connect-name">LinkedIn</div>
          <div class="connect-handle">/your-username</div>
        </a>
        <a href="https://github.com/manahilzahra" target="_blank" class="connect-card connect-card--github" data-aos="fade-up" data-aos-delay="100">
          <span class="connect-arrow">
            <span class="iconify" data-icon="mdi:arrow-top-right" data-width="16"></span>
          </span>
          <div class="connect-icon">
            <span class="iconify" data-icon="mdi:github" data-width="24"></span>
          </div>
          <div class="connect-name">GitHub</div>
          <div class="connect-handle">@manahilzahra</div>
        </a>
        <a href="mailto:your.email@example.com" class="connect-card connect-card--email" data-aos="fade-up" data-aos-delay="200">
          <span class="connect-arrow">
            <span class="iconify" data-icon="mdi:arrow-top-right" data-width="16"></span>
          </span>
          <div class="connect-icon">
            <span class="iconify" data-icon="mdi:email-outline" data-width="24"></span>
          </div>
          <div class="connect-name">Email</div>
          <div class="connect-handle">your.email@example.com</div>
        </a>
      </div>
    </div>
  </section>

  <!-- ════════ FOOTER ════════ -->
  <footer class="footer">
    <div class="container">
      <div class="footer-quote">"Every expert was once a beginner."</div>
      <div class="footer-text">
        Made with <span class="heart">♥</span> by Manahil Zahra · Thank you for visiting!
      </div>
    </div>
  </footer>

  <!-- ════════ SCRIPTS ════════ -->
  <script src="https://unpkg.com/aos@2.3.4/dist/aos.js"></script>
  <script>
    // ─── AOS Init ───
    AOS.init({
      once: true,
      offset: 60,
      easing: 'ease-out-cubic'
    });

    // ─── Typed.js ───
    new Typed('#typed-output', {
      strings: [
        'Software Engineering Student',
        'Aspiring Frontend Developer',
        'Lifelong Learner',
        'Building things one step at a time'
      ],
      typeSpeed: 50,
      backSpeed: 30,
      backDelay: 2000,
      loop: true,
      showCursor: true,
      cursorChar: '|'
    });

    // ─── Navbar scroll effect ───
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      navbar.classList.toggle('scrolled', window.scrollY > 50);
    });

    // ─── Active nav link on scroll ───
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-links a');
    window.addEventListener('scroll', () => {
      let current = '';
      sections.forEach(section => {
        const top = section.offsetTop - 120;
        if (scrollY >= top) current = section.getAttribute('id');
      });
      navLinks.forEach(link => {
        link.classList.remove('active');
        if (link.getAttribute('href') === '#' + current) link.classList.add('active');
      });
    });

    // ─── Mobile menu ───
    const mobileToggle = document.getElementById('mobileToggle');
    const mobileMenu = document.getElementById('mobileMenu');
    const mobileClose = document.getElementById('mobileClose');
    const mobileLinks = document.querySelectorAll('.mobile-link');

    mobileToggle.addEventListener('click', () => mobileMenu.classList.add('open'));
    mobileClose.addEventListener('click', () => mobileMenu.classList.remove('open'));
    mobileLinks.forEach(link => {
      link.addEventListener('click', () => mobileMenu.classList.remove('open'));
    });

    // ─── Profile views counter animation ───
    const viewsEl = document.getElementById('viewsCount');
    const viewsTarget = 1247;
    const viewsCU = new countUp.CountUp(viewsEl, viewsTarget, {
      duration: 2.5,
      separator: ','
    });
    setTimeout(() => viewsCU.start(), 800);

    // ─── Stats counters ───
    const counters = document.querySelectorAll('.counter');
    let countersStarted = false;

    function startCounters() {
      if (countersStarted) return;
      countersStarted = true;
      counters.forEach(counter => {
        const target = parseInt(counter.dataset.target);
        const cu = new countUp.CountUp(counter, target, { duration: 2 });
        cu.start();
      });
    }

    // ─── Skill progress bars ───
    let skillsAnimated = false;

    function animateSkills() {
      if (skillsAnimated) return;
      skillsAnimated = true;
      document.querySelectorAll('.skill-progress-fill').forEach(bar => {
        const w = bar.dataset.width;
        setTimeout(() => { bar.style.width = w + '%'; }, 200);
      });
    }

    // ─── Language bar animation ───
    let langsAnimated = false;

    function animateLangs() {
      if (langsAnimated) return;
      langsAnimated = true;
      document.querySelectorAll('.lang-segment').forEach(seg => {
        const w = seg.dataset.width;
        setTimeout(() => { seg.style.width = w + '%'; }, 300);
      });
    }

    // ─── Intersection Observer for animations ───
    const statsSection = document.getElementById('stats');
    const skillsSection = document.getElementById('skills');

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          if (entry.target === statsSection) {
            startCounters();
            animateLangs();
          }
          if (entry.target === skillsSection) {
            animateSkills();
          }
        }
      });
    }, { threshold: 0.2 });

    observer.observe(statsSection);
    observer.observe(skillsSection);

    // ─── Generate streak grid ───
    const streakGrid = document.getElementById('streakGrid');
    for (let i = 0; i < 84; i++) {
      const cell = document.createElement('div');
      cell.classList.add('streak-cell');
      const rand = Math.random();
      if (rand > 0.55) {
        cell.classList.add('active');
        if (rand > 0.85) cell.classList.add('max');
        else if (rand > 0.7) cell.classList.add('high');
      }
      streakGrid.appendChild(cell);
    }

    // ─── Particles ───
    const canvas = document.getElementById('particles-canvas');
    const ctx = canvas.getContext('2d');
    let particles = [];
    let mouse = { x: -1000, y: -1000 };

    function resizeCanvas() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    }
    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);

    document.addEventListener('mousemove', e => {
      mouse.x = e.clientX;
      mouse.y = e.clientY;
    });

    class Particle {
      constructor() {
        this.reset();
      }
      reset() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 1.5 + 0.5;
        this.speedX = (Math.random() - 0.5) * 0.3;
        this.speedY = (Math.random() - 0.5) * 0.3;
        this.opacity = Math.random() * 0.4 + 0.1;
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;

        // Mouse repulsion
        const dx = this.x - mouse.x;
        const dy = this.y - mouse.y;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < 120) {
          const force = (120 - dist) / 120 * 0.8;
          this.x += (dx / dist) * force;
          this.y += (dy / dist) * force;
        }

        if (this.x < 0 || this.x > canvas.width || this.y < 0 || this.y > canvas.height) {
          this.reset();
        }
      }
      draw() {
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(129, 140, 248, ${this.opacity})`;
        ctx.fill();
      }
    }

    // Create particles
    const particleCount = Math.min(80, Math.floor(window.innerWidth / 18));
    for (let i = 0; i < particleCount; i++) {
      particles.push(new Particle());
    }

    function animateParticles() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });

      // Draw connections
      for (let i = 0; i < particles.length; i++) {
        for (let j = i + 1; j < particles.length; j++) {
          const dx = particles[i].x - particles[j].x;
          const dy = particles[i].y - particles[j].y;
          const dist = Math.sqrt(dx * dx + dy * dy);
          if (dist < 120) {
            ctx.beginPath();
            ctx.moveTo(particles[i].x, particles[i].y);
            ctx.lineTo(particles[j].x, particles[j].y);
            ctx.strokeStyle = `rgba(129, 140, 248, ${0.06 * (1 - dist / 120)})`;
            ctx.lineWidth = 0.5;
            ctx.stroke();
          }
        }
      }
      requestAnimationFrame(animateParticles);
    }
    animateParticles();

    // ─── Smooth scroll for all anchor links ───
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          target.scrollIntoView({ behavior: 'smooth' });
        }
      });
    });
  </script>
</body>
</html>
