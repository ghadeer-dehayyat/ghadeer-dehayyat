## Hi there 👋

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ghadeer's GitHub Banner</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;1,600&family=Cormorant+Garamond:wght@300;600&family=Raleway:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  background: #040d2a;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding: 30px;
}

.banner {
  width: 1200px;
  height: 400px;
  position: relative;
  overflow: hidden;
  border-radius: 6px;
  background: #070f35;
}

/* ── Background layers ── */
.bg-base {
  position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 700px 500px at 15% 60%, rgba(13,28,95,0.95) 0%, transparent 65%),
    radial-gradient(ellipse 500px 350px at 85% 25%, rgba(232,121,176,0.07) 0%, transparent 55%),
    radial-gradient(ellipse 400px 400px at 60% 80%, rgba(13,28,95,0.5) 0%, transparent 60%),
    linear-gradient(145deg, #06102e 0%, #0e1f72 35%, #0a1850 65%, #06102e 100%);
}

/* Dot grid */
.dot-grid {
  position: absolute; inset: 0;
  background-image: radial-gradient(circle, rgba(245,230,211,0.07) 1px, transparent 1px);
  background-size: 28px 28px;
}

/* Diagonal accent stripe */
.stripe {
  position: absolute;
  top: 0; left: 0; right: 0; bottom: 0;
  background: repeating-linear-gradient(
    -60deg,
    transparent 0px,
    transparent 60px,
    rgba(232,121,176,0.018) 60px,
    rgba(232,121,176,0.018) 61px
  );
}

/* ── Decorative circles top-right ── */
.deco-ring {
  position: absolute; border-radius: 50%;
  border: 1px solid rgba(232,121,176,0.08);
  top: -100px; right: -100px;
}
.deco-ring-1 { width: 350px; height: 350px; }
.deco-ring-2 { width: 500px; height: 500px; top: -175px; right: -175px; border-color: rgba(245,230,211,0.04); }
.deco-ring-3 { width: 200px; height: 200px; top: -50px; right: -50px; border-color: rgba(232,121,176,0.12); animation: spinSlow 40s linear infinite; }

/* ── Neural Net SVG (left side) ── */
.neural-svg {
  position: absolute; left: 0; top: 0; width: 420px; height: 400px;
}

/* ── Chess pieces floating ── */
.chess {
  position: absolute;
  font-size: 26px;
  color: #f5e6d3;
  user-select: none;
  pointer-events: none;
  opacity: 0;
  animation: floatChess ease-in-out infinite;
}

/* ── Sparkle dots ── */
.spark {
  position: absolute;
  border-radius: 50%;
  animation: twinkle ease-in-out infinite;
  pointer-events: none;
}

/* ── Main content ── */
.content {
  position: absolute;
  right: 0; top: 0;
  width: 720px; height: 400px;
  display: flex; flex-direction: column;
  justify-content: center; align-items: flex-start;
  padding: 0 65px 0 10px;
}

.eyebrow {
  font-family: 'Raleway', sans-serif;
  font-weight: 300;
  font-size: 11px;
  letter-spacing: 7px;
  text-transform: uppercase;
  color: #e879b0;
  margin-bottom: 14px;
  opacity: 0;
  animation: slideUp 0.9s cubic-bezier(0.16,1,0.3,1) forwards 0.3s;
}

.eyebrow-dot { 
  display: inline-block; 
  width: 5px; height: 5px; 
  background: #e879b0; 
  border-radius: 50%; 
  margin: 0 10px; 
  vertical-align: middle;
  animation: pulseDot 2s ease-in-out infinite 1.5s;
}

.title-line1 {
  font-family: 'Raleway', sans-serif;
  font-weight: 200;
  font-size: 20px;
  letter-spacing: 5px;
  text-transform: uppercase;
  color: rgba(245,230,211,0.65);
  margin-bottom: 4px;
  opacity: 0;
  animation: slideUp 0.9s cubic-bezier(0.16,1,0.3,1) forwards 0.55s;
}

.title-name {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
  font-size: 64px;
  color: #f5e6d3;
  line-height: 1.05;
  margin-bottom: 2px;
  opacity: 0;
  animation: slideUp 0.9s cubic-bezier(0.16,1,0.3,1) forwards 0.7s, nameGlow 4s ease-in-out infinite 2.5s;
}

.title-name .accent { 
  color: #e879b0; 
  font-style: italic; 
}

.title-github {
  font-family: 'Cormorant Garamond', serif;
  font-weight: 300;
  font-size: 26px;
  letter-spacing: 12px;
  text-transform: uppercase;
  color: rgba(245,230,211,0.5);
  margin-bottom: 28px;
  opacity: 0;
  animation: slideUp 0.9s cubic-bezier(0.16,1,0.3,1) forwards 0.9s;
}

.divider {
  display: flex; align-items: center; gap: 10px;
  margin-bottom: 22px;
  opacity: 0;
  animation: fadeIn 1s ease forwards 1.1s;
}
.divider-line { width: 50px; height: 1px; background: linear-gradient(90deg, #e879b0, transparent); }
.divider-diamond { width: 6px; height: 6px; background: #e879b0; transform: rotate(45deg); opacity: 0.6; }

.tags {
  display: flex; gap: 10px; flex-wrap: wrap;
  opacity: 0;
  animation: slideUp 0.9s cubic-bezier(0.16,1,0.3,1) forwards 1.3s;
}
.tag {
  padding: 5px 15px;
  border: 1px solid rgba(232,121,176,0.3);
  border-radius: 30px;
  font-family: 'Raleway', sans-serif;
  font-size: 10px;
  letter-spacing: 2.5px;
  text-transform: uppercase;
  color: rgba(245,230,211,0.75);
  background: rgba(232,121,176,0.06);
  font-weight: 300;
  transition: all 0.3s;
}
.tag:hover {
  background: rgba(232,121,176,0.15);
  border-color: rgba(232,121,176,0.6);
  color: #f5e6d3;
}

/* Bottom accent bar */
.bottom-bar {
  position: absolute; bottom: 0; left: 0; right: 0; height: 2px;
  background: linear-gradient(90deg, transparent 0%, #e879b0 25%, #f5e6d3 50%, #e879b0 75%, transparent 100%);
  opacity: 0.35;
  animation: barShimmer 3s ease-in-out infinite 2s;
}

/* Left pink glow */
.left-glow {
  position: absolute;
  left: 160px; top: 50%; transform: translateY(-50%);
  width: 2px; height: 60%;
  background: linear-gradient(180deg, transparent, rgba(232,121,176,0.3) 30%, rgba(232,121,176,0.5) 50%, rgba(232,121,176,0.3) 70%, transparent);
  opacity: 0;
  animation: fadeIn 1s ease forwards 1.8s;
}

/* ── Keyframe Animations ── */
@keyframes slideUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
@keyframes floatChess {
  0%   { transform: translateY(0px) rotate(-3deg); opacity: 0.08; }
  30%  { opacity: 0.22; }
  50%  { transform: translateY(-18px) rotate(3deg); opacity: 0.15; }
  70%  { opacity: 0.22; }
  100% { transform: translateY(0px) rotate(-3deg); opacity: 0.08; }
}
@keyframes twinkle {
  0%, 100% { opacity: 0; transform: scale(0.4); }
  50%       { opacity: 1; transform: scale(1.2); }
}
@keyframes spinSlow { to { transform: rotate(360deg); } }
@keyframes pulseDot {
  0%, 100% { transform: scale(1); opacity: 1; }
  50%       { transform: scale(1.6); opacity: 0.5; }
}
@keyframes nameGlow {
  0%, 100% { text-shadow: none; }
  50%       { text-shadow: 0 0 40px rgba(232,121,176,0.25), 0 0 80px rgba(232,121,176,0.08); }
}
@keyframes barShimmer {
  0%, 100% { opacity: 0.35; }
  50%       { opacity: 0.6; }
}
@keyframes nodePulse {
  0%, 100% { r: 4; opacity: 0.7; }
  50%       { r: 6.5; opacity: 1; }
}
@keyframes nodeRipple {
  0%   { r: 4; opacity: 0.6; stroke-width: 1.5; }
  100% { r: 22; opacity: 0; stroke-width: 0.5; }
}
@keyframes flowLine {
  0%   { stroke-dashoffset: 120; opacity: 0; }
  20%  { opacity: 0.5; }
  80%  { opacity: 0.5; }
  100% { stroke-dashoffset: -120; opacity: 0; }
}
@keyframes moveParticle {
  0%   { transform: translate(0, 0) scale(1); opacity: 0; }
  10%  { opacity: 0.7; }
  90%  { opacity: 0.7; }
  100% { transform: translate(var(--dx), var(--dy)) scale(0); opacity: 0; }
}
</style>
</head>
<body>
<div class="banner">
  <!-- Background -->
  <div class="bg-base"></div>
  <div class="dot-grid"></div>
  <div class="stripe"></div>

  <!-- Decorative rings -->
  <div class="deco-ring deco-ring-1"></div>
  <div class="deco-ring deco-ring-2"></div>
  <div class="deco-ring deco-ring-3"></div>

  <!-- Left divider glow -->
  <div class="left-glow"></div>

  <!-- Neural Network SVG -->
  <svg class="neural-svg" viewBox="0 0 420 400" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <!-- Flowing gradient for lines -->
      <linearGradient id="lineGrad1" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" style="stop-color:#e879b0;stop-opacity:0"/>
        <stop offset="50%" style="stop-color:#e879b0;stop-opacity:0.5"/>
        <stop offset="100%" style="stop-color:#e879b0;stop-opacity:0"/>
      </linearGradient>
      <linearGradient id="lineGrad2" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" style="stop-color:#f5e6d3;stop-opacity:0"/>
        <stop offset="50%" style="stop-color:#f5e6d3;stop-opacity:0.3"/>
        <stop offset="100%" style="stop-color:#f5e6d3;stop-opacity:0"/>
      </linearGradient>
    </defs>

    <!-- ── Layer 1 → Layer 2 connections ── -->
    <!-- Node L1:1 (50,80) → L2:1,2,3 -->
    <line x1="50" y1="80"  x2="155" y2="60"  stroke="rgba(232,121,176,0.18)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.8s" repeatCount="indefinite"/></line>
    <line x1="50" y1="80"  x2="155" y2="140" stroke="rgba(232,121,176,0.12)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.2s" repeatCount="indefinite"/></line>
    <line x1="50" y1="80"  x2="155" y2="220" stroke="rgba(245,230,211,0.08)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.7s" repeatCount="indefinite"/></line>
    <!-- Node L1:2 (50,200) → L2:1,2,3 -->
    <line x1="50" y1="200" x2="155" y2="60"  stroke="rgba(245,230,211,0.08)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.1s" repeatCount="indefinite"/></line>
    <line x1="50" y1="200" x2="155" y2="140" stroke="rgba(232,121,176,0.15)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.6s" repeatCount="indefinite"/></line>
    <line x1="50" y1="200" x2="155" y2="220" stroke="rgba(232,121,176,0.18)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.4s" repeatCount="indefinite"/></line>
    <line x1="50" y1="200" x2="155" y2="300" stroke="rgba(245,230,211,0.08)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.9s" repeatCount="indefinite"/></line>
    <!-- Node L1:3 (50,320) → L2:2,3,4 -->
    <line x1="50" y1="320" x2="155" y2="140" stroke="rgba(245,230,211,0.06)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.6s" repeatCount="indefinite"/></line>
    <line x1="50" y1="320" x2="155" y2="220" stroke="rgba(232,121,176,0.12)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.7s" repeatCount="indefinite"/></line>
    <line x1="50" y1="320" x2="155" y2="300" stroke="rgba(232,121,176,0.18)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.0s" repeatCount="indefinite"/></line>

    <!-- ── Layer 2 → Layer 3 connections ── -->
    <line x1="155" y1="60"  x2="265" y2="100" stroke="rgba(232,121,176,0.2)"  stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.4s" repeatCount="indefinite"/></line>
    <line x1="155" y1="60"  x2="265" y2="200" stroke="rgba(245,230,211,0.08)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.3s" repeatCount="indefinite"/></line>
    <line x1="155" y1="140" x2="265" y2="100" stroke="rgba(245,230,211,0.1)"  stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.8s" repeatCount="indefinite"/></line>
    <line x1="155" y1="140" x2="265" y2="200" stroke="rgba(232,121,176,0.18)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.5s" repeatCount="indefinite"/></line>
    <line x1="155" y1="140" x2="265" y2="300" stroke="rgba(245,230,211,0.08)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.1s" repeatCount="indefinite"/></line>
    <line x1="155" y1="220" x2="265" y2="100" stroke="rgba(232,121,176,0.1)"  stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.9s" repeatCount="indefinite"/></line>
    <line x1="155" y1="220" x2="265" y2="200" stroke="rgba(232,121,176,0.22)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.2s" repeatCount="indefinite"/></line>
    <line x1="155" y1="220" x2="265" y2="300" stroke="rgba(245,230,211,0.1)"  stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.5s" repeatCount="indefinite"/></line>
    <line x1="155" y1="300" x2="265" y2="200" stroke="rgba(232,121,176,0.14)" stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="3.0s" repeatCount="indefinite"/></line>
    <line x1="155" y1="300" x2="265" y2="300" stroke="rgba(232,121,176,0.2)"  stroke-width="0.8" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.6s" repeatCount="indefinite"/></line>

    <!-- ── Layer 3 → Output ── -->
    <line x1="265" y1="100" x2="360" y2="200" stroke="rgba(232,121,176,0.25)" stroke-width="1" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.3s" repeatCount="indefinite"/></line>
    <line x1="265" y1="200" x2="360" y2="200" stroke="rgba(232,121,176,0.3)"  stroke-width="1" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.0s" repeatCount="indefinite"/></line>
    <line x1="265" y1="300" x2="360" y2="200" stroke="rgba(232,121,176,0.25)" stroke-width="1" stroke-dasharray="6,4"><animate attributeName="stroke-dashoffset" from="0" to="-20" dur="2.7s" repeatCount="indefinite"/></line>

    <!-- ── Nodes Layer 1 (input) ── -->
    <!-- Node 1,1 -->
    <circle cx="50" cy="80" r="4" fill="#e879b0" opacity="0.75">
      <animate attributeName="r" values="3.5;6;3.5" dur="3.2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.5;1;0.5" dur="3.2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="50" cy="80" r="4" fill="none" stroke="#e879b0" stroke-width="1">
      <animate attributeName="r" values="4;22" dur="3.2s" repeatCount="indefinite" begin="0s"/>
      <animate attributeName="opacity" values="0.5;0" dur="3.2s" repeatCount="indefinite" begin="0s"/>
    </circle>
    <!-- Node 1,2 -->
    <circle cx="50" cy="200" r="4" fill="#f5e6d3" opacity="0.7">
      <animate attributeName="r" values="3.5;5.5;3.5" dur="2.8s" repeatCount="indefinite" begin="0.5s"/>
      <animate attributeName="opacity" values="0.5;0.9;0.5" dur="2.8s" repeatCount="indefinite" begin="0.5s"/>
    </circle>
    <circle cx="50" cy="200" r="4" fill="none" stroke="#f5e6d3" stroke-width="0.8">
      <animate attributeName="r" values="4;20" dur="2.8s" repeatCount="indefinite" begin="0.5s"/>
      <animate attributeName="opacity" values="0.4;0" dur="2.8s" repeatCount="indefinite" begin="0.5s"/>
    </circle>
    <!-- Node 1,3 -->
    <circle cx="50" cy="320" r="4" fill="#e879b0" opacity="0.7">
      <animate attributeName="r" values="3.5;6;3.5" dur="3.5s" repeatCount="indefinite" begin="1s"/>
      <animate attributeName="opacity" values="0.5;1;0.5" dur="3.5s" repeatCount="indefinite" begin="1s"/>
    </circle>
    <circle cx="50" cy="320" r="4" fill="none" stroke="#e879b0" stroke-width="1">
      <animate attributeName="r" values="4;22" dur="3.5s" repeatCount="indefinite" begin="1s"/>
      <animate attributeName="opacity" values="0.5;0" dur="3.5s" repeatCount="indefinite" begin="1s"/>
    </circle>

    <!-- ── Nodes Layer 2 ── -->
    <circle cx="155" cy="60"  r="4" fill="#e8c9b4" opacity="0.6"><animate attributeName="r" values="3;5.5;3" dur="2.6s" repeatCount="indefinite" begin="0.3s"/></circle>
    <circle cx="155" cy="140" r="4" fill="#e879b0" opacity="0.7"><animate attributeName="r" values="3.5;6;3.5" dur="3.0s" repeatCount="indefinite" begin="0.8s"/></circle>
    <circle cx="155" cy="140" r="4" fill="none" stroke="#e879b0" stroke-width="0.8"><animate attributeName="r" values="4;20" dur="3.0s" repeatCount="indefinite" begin="0.8s"/><animate attributeName="opacity" values="0.5;0" dur="3.0s" repeatCount="indefinite" begin="0.8s"/></circle>
    <circle cx="155" cy="220" r="4" fill="#f5e6d3" opacity="0.6"><animate attributeName="r" values="3;5;3" dur="2.4s" repeatCount="indefinite" begin="1.2s"/></circle>
    <circle cx="155" cy="300" r="4" fill="#e879b0" opacity="0.65"><animate attributeName="r" values="3.5;5.5;3.5" dur="3.3s" repeatCount="indefinite" begin="0.4s"/></circle>

    <!-- ── Nodes Layer 3 ── -->
    <circle cx="265" cy="100" r="4" fill="#e8c9b4" opacity="0.65"><animate attributeName="r" values="3;5.5;3" dur="2.7s" repeatCount="indefinite" begin="0.6s"/></circle>
    <circle cx="265" cy="200" r="4" fill="#e879b0" opacity="0.8">
      <animate attributeName="r" values="4;7;4" dur="2.5s" repeatCount="indefinite" begin="0.2s"/>
      <animate attributeName="opacity" values="0.6;1;0.6" dur="2.5s" repeatCount="indefinite" begin="0.2s"/>
    </circle>
    <circle cx="265" cy="200" r="4" fill="none" stroke="#e879b0" stroke-width="1.2">
      <animate attributeName="r" values="4;24" dur="2.5s" repeatCount="indefinite" begin="0.2s"/>
      <animate attributeName="opacity" values="0.6;0" dur="2.5s" repeatCount="indefinite" begin="0.2s"/>
    </circle>
    <circle cx="265" cy="300" r="4" fill="#e8c9b4" opacity="0.6"><animate attributeName="r" values="3;5.5;3" dur="3.1s" repeatCount="indefinite" begin="0.9s"/></circle>

    <!-- ── Output node ── -->
    <circle cx="360" cy="200" r="8" fill="#e879b0" opacity="0.9">
      <animate attributeName="r" values="7;11;7" dur="2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.7;1;0.7" dur="2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="360" cy="200" r="8" fill="none" stroke="#e879b0" stroke-width="1.5">
      <animate attributeName="r" values="8;28" dur="2s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.7;0" dur="2s" repeatCount="indefinite"/>
    </circle>
    <circle cx="360" cy="200" r="8" fill="none" stroke="#e879b0" stroke-width="1">
      <animate attributeName="r" values="8;40" dur="2s" repeatCount="indefinite" begin="0.5s"/>
      <animate attributeName="opacity" values="0.4;0" dur="2s" repeatCount="indefinite" begin="0.5s"/>
    </circle>

    <!-- Label -->
    <text x="360" y="240" font-family="Raleway, sans-serif" font-size="9" fill="rgba(232,121,176,0.5)" text-anchor="middle" letter-spacing="2">OUTPUT</text>
    <text x="50" y="350" font-family="Raleway, sans-serif" font-size="9" fill="rgba(245,230,211,0.3)" text-anchor="middle" letter-spacing="2">INPUT</text>
  </svg>

  <!-- Chess Pieces -->
  <div class="chess" style="left:500px; top:30px;  font-size:22px; animation-duration:5.2s; animation-delay:0.2s;">♛</div>
  <div class="chess" style="left:560px; top:340px; font-size:18px; animation-duration:6.1s; animation-delay:1.1s; color:#e879b0;">♟</div>
  <div class="chess" style="left:450px; top:180px; font-size:30px; animation-duration:7.3s; animation-delay:0.7s; opacity:0.06;">♚</div>
  <div class="chess" style="left:620px; top:60px;  font-size:20px; animation-duration:4.8s; animation-delay:1.5s; color:#e879b0;">♝</div>
  <div class="chess" style="left:700px; top:310px; font-size:16px; animation-duration:5.7s; animation-delay:0.4s;">♞</div>
  <div class="chess" style="left:750px; top:25px;  font-size:14px; animation-duration:6.5s; animation-delay:2.0s; color:#e879b0;">♜</div>
  <div class="chess" style="left:820px; top:355px; font-size:20px; animation-duration:5.0s; animation-delay:0.9s;">♛</div>
  <div class="chess" style="left:1080px; top:40px;  font-size:18px; animation-duration:6.8s; animation-delay:1.3s; color:#e879b0;">♟</div>
  <div class="chess" style="left:1130px; top:340px; font-size:16px; animation-duration:5.4s; animation-delay:0.6s;">♝</div>
  <div class="chess" style="left:420px; top:80px;  font-size:13px; animation-duration:4.6s; animation-delay:1.8s; color:#e8c9b4;">♞</div>

  <!-- Sparkle dots -->
  <div class="spark" style="left:490px;  top:95px;  width:3px; height:3px; background:#e879b0;    animation-duration:2.1s; animation-delay:0.3s;"></div>
  <div class="spark" style="left:600px;  top:160px; width:4px; height:4px; background:#f5e6d3;    animation-duration:3.2s; animation-delay:1.1s;"></div>
  <div class="spark" style="left:680px;  top:240px; width:3px; height:3px; background:#e879b0;    animation-duration:2.8s; animation-delay:0.7s;"></div>
  <div class="spark" style="left:780px;  top:110px; width:5px; height:5px; background:#e8c9b4;    animation-duration:3.5s; animation-delay:1.5s;"></div>
  <div class="spark" style="left:860px;  top:290px; width:3px; height:3px; background:#e879b0;    animation-duration:2.4s; animation-delay:0.2s;"></div>
  <div class="spark" style="left:950px;  top:75px;  width:4px; height:4px; background:#f5e6d3;    animation-duration:3.0s; animation-delay:0.9s;"></div>
  <div class="spark" style="left:1020px; top:210px; width:3px; height:3px; background:#e879b0;    animation-duration:2.6s; animation-delay:1.7s;"></div>
  <div class="spark" style="left:1100px; top:150px; width:4px; height:4px; background:#e8c9b4;    animation-duration:3.8s; animation-delay:0.5s;"></div>
  <div class="spark" style="left:1150px; top:270px; width:3px; height:3px; background:#e879b0;    animation-duration:2.2s; animation-delay:1.3s;"></div>
  <div class="spark" style="left:530px;  top:300px; width:4px; height:4px; background:#f5e6d3;    animation-duration:3.4s; animation-delay:0.4s;"></div>
  <div class="spark" style="left:430px;  top:350px; width:3px; height:3px; background:#e879b0;    animation-duration:2.9s; animation-delay:1.9s;"></div>
  <div class="spark" style="left:660px;  top:370px; width:5px; height:5px; background:#e8c9b4;    animation-duration:4.1s; animation-delay:0.8s;"></div>

  <!-- Main content -->
  <div class="content">
    <div class="eyebrow">
      <span class="eyebrow-dot"></span>
      Creative Developer
      <span class="eyebrow-dot"></span>
    </div>
    <div class="title-line1">Welcome to</div>
    <div class="title-name"><span class="accent">Ghadeer's</span></div>
    <div class="title-github">GitHub</div>
    <div class="divider">
      <div class="divider-line"></div>
      <div class="divider-diamond"></div>
      <div class="divider-line" style="background: linear-gradient(90deg, transparent, rgba(245,230,211,0.3));"></div>
    </div>
    <div class="tags">
      <span class="tag">⚡ Artificial Intelligence</span>
      <span class="tag">♟ Chess</span>
      <span class="tag">🎮 Game Design</span>
      <span class="tag">💡 Innovation</span>
    </div>
  </div>

  <div class="bottom-bar"></div>
</div>
</body>
</html>
