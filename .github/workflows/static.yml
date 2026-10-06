<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>⚡雷霆人工智障模型·超级加强版⚡</title>
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>⚡</text></svg>">
<style>
/* ============================================================
   雷霆人工智障模型 · 超级加强版
   配色：霓虹绿 / 电光黄 / 爆炸红 / 深黑底
   ============================================================ */

/* ---------- 0. 全局重置与变量 ---------- */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg-deep:      #050807;
  --bg-panel:     #0d1411;
  --bg-input:     #0a1a12;
  --neon-green:   #00ffaa;
  --neon-green-dim:#00aa77;
  --electric-yellow:#ffe14d;
  --explode-red:  #ff3b3b;
  --warn-orange:  #ff8a00;
  --ghost-text:   #7fd9b8;
  --border-green: rgba(0,255,170,0.35);
  --shadow-green: 0 0 12px rgba(0,255,170,0.55);
  --shadow-red:   0 0 14px rgba(255,60,60,0.65);
  --shadow-yellow:0 0 14px rgba(255,225,77,0.65);
  --font-main: "Courier New", "Consolas", "Noto Sans SC", monospace;
}

html, body {
  width: 100%;
  min-height: 100vh;
  background: var(--bg-deep);
  color: var(--neon-green);
  font-family: var(--font-main);
  font-size: 15px;
  line-height: 1.65;
  overflow-x: hidden;
  -webkit-tap-highlight-color: transparent;
}

body {
  background:
    radial-gradient(ellipse at 20% 0%, rgba(0,255,170,0.08), transparent 55%),
    radial-gradient(ellipse at 80% 100%, rgba(255,60,60,0.06), transparent 55%),
    var(--bg-deep);
}

/* 扫描线纹理（老电视感） */
body::before {
  content: "";
  position: fixed;
  inset: 0;
  pointer-events: none;
  background: repeating-linear-gradient(
    to bottom,
    transparent 0px,
    transparent 2px,
    rgba(0, 255, 170, 0.025) 3px,
    transparent 4px
  );
  z-index: 9998;
  mix-blend-mode: screen;
}

/* 爆炸全屏闪光 */
body.boom-flash { animation: boomFlash 0.45s ease-out; }
@keyframes boomFlash {
  0%   { filter: brightness(1) saturate(1); }
  15%  { filter: brightness(4)  saturate(3) hue-rotate(-30deg); }
  35%  { filter: brightness(2.5) saturate(2) hue-rotate(10deg); background:#ff2200; }
  60%  { filter: brightness(3)  saturate(2.5) hue-rotate(-10deg); background:#ffdd00; }
  100% { filter: brightness(1) saturate(1); background: var(--bg-deep); }
}

/* 屏幕整体震动 */
body.shake-hard { animation: shakeHard 0.35s linear; }
@keyframes shakeHard {
  0%,100% { transform: translate(0,0) rotate(0); }
  10% { transform: translate(-8px, 4px) rotate(-0.6deg); }
  20% { transform: translate( 7px,-5px) rotate( 0.5deg); }
  30% { transform: translate(-6px, 6px) rotate(-0.4deg); }
  40% { transform: translate( 8px,-3px) rotate( 0.6deg); }
  50% { transform: translate(-5px, 5px) rotate(-0.3deg); }
  60% { transform: translate( 6px,-6px) rotate( 0.4deg); }
  70% { transform: translate(-7px, 3px) rotate(-0.5deg); }
  80% { transform: translate( 5px,-4px) rotate( 0.3deg); }
  90% { transform: translate(-4px, 2px) rotate(-0.2deg); }
}

/* ---------- 1. 启动加载画面 ---------- */
#boot {
  position: fixed;
  inset: 0;
  background: #000;
  z-index: 10000;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  transition: opacity 0.6s ease, visibility 0.6s;
}
#boot.hidden { opacity: 0; visibility: hidden; }

#boot .boot-title {
  font-size: 22px;
  color: var(--electric-yellow);
  text-shadow: var(--shadow-yellow);
  letter-spacing: 4px;
  margin-bottom: 18px;
  animation: bootPulse 1.2s ease-in-out infinite;
}
@keyframes bootPulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50%     { opacity: 0.6; transform: scale(0.97); }
}
#boot .boot-bar-wrap {
  width: 80%;
  max-width: 360px;
  height: 14px;
  border: 1px solid var(--neon-green);
  border-radius: 2px;
  overflow: hidden;
  background: #000;
}
#boot .boot-bar {
  height: 100%;
  width: 0%;
  background: linear-gradient(90deg, var(--neon-green), var(--electric-yellow));
  box-shadow: var(--shadow-green);
  transition: width 0.2s linear;
}
#boot .boot-log {
  margin-top: 14px;
  width: 80%;
  max-width: 360px;
  font-size: 12px;
  color: var(--ghost-text);
  height: 80px;
  overflow: hidden;
  white-space: pre-wrap;
}

/* ---------- 2. 主布局 ---------- */
#app {
  max-width: 720px;
  margin: 0 auto;
  padding: 14px 14px 120px;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

/* 顶部标题 */
#title-bar {
  text-align: center;
  padding: 10px 0 8px;
  border-bottom: 1px dashed var(--border-green);
  margin-bottom: 10px;
}
#title-bar h1 {
  font-size: 20px;
  color: var(--neon-green);
  text-shadow: var(--shadow-green);
  letter-spacing: 2px;
  animation: titleBlink 3.5s infinite;
}
@keyframes titleBlink {
  0%, 88%, 100% { opacity: 1; color: var(--neon-green); text-shadow: var(--shadow-green); }
  90% { opacity: 0.25; color: #fff; text-shadow: 0 0 10px #fff; }
  92% { opacity: 1; color: var(--electric-yellow); text-shadow: var(--shadow-yellow); }
  94% { opacity: 0.4; color: var(--explode-red); text-shadow: var(--shadow-red); }
  96% { opacity: 1; color: var(--neon-green); text-shadow: var(--shadow-green); }
}
#title-bar .subtitle {
  font-size: 11px;
  color: var(--ghost-text);
  margin-top: 4px;
  letter-spacing: 1px;
}

/* 状态栏：温度/电量/芯片健康 */
#status-bar {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 6px;
  margin-bottom: 10px;
}
.status-cell {
  background: var(--bg-panel);
  border: 1px solid var(--border-green);
  border-radius: 4px;
  padding: 6px 4px;
  text-align: center;
  font-size: 11px;
}
.status-cell .label { color: var(--ghost-text); display: block; font-size: 10px; }
.status-cell .value {
  display: block;
  font-size: 15px;
  font-weight: bold;
  color: var(--neon-green);
  margin-top: 2px;
}
.status-cell.danger .value { color: var(--explode-red); text-shadow: var(--shadow-red); animation: dangerBlink 0.6s infinite; }
.status-cell.warn .value { color: var(--warn-orange); }
@keyframes dangerBlink {
  0%,100% { opacity: 1; } 50% { opacity: 0.35; }
}

/* 温度进度条 */
.temp-bar {
  height: 4px;
  background: #001a10;
  border-radius: 2px;
  margin-top: 4px;
  overflow: hidden;
}
.temp-bar > i {
  display: block;
  height: 100%;
  width: 20%;
  background: var(--neon-green);
  transition: width 0.4s, background 0.4s;
}

/* ---------- 3. 对话区 ---------- */
#chat-box {
  background: var(--bg-panel);
  border: 1px solid var(--border-green);
  border-radius: 8px;
  padding: 12px;
  min-height: 320px;
  max-height: 60vh;
  overflow-y: auto;
  flex: 1;
  box-shadow: inset 0 0 20px rgba(0,255,170,0.06);
  scroll-behavior: smooth;
}
#chat-box::-webkit-scrollbar { width: 6px; }
#chat-box::-webkit-scrollbar-thumb { background: var(--neon-green-dim); border-radius: 3px; }

.msg {
  margin-bottom: 10px;
  padding: 6px 8px;
  border-radius: 4px;
  white-space: pre-wrap;
  word-break: break-word;
}
.msg.user {
  background: rgba(0, 170, 119, 0.12);
  border-left: 3px solid var(--neon-green);
  color: #c8ffe9;
}
.msg.bot {
  background: rgba(255, 225, 77, 0.06);
  border-left: 3px solid var(--electric-yellow);
  color: #fff5c2;
}
.msg.sys {
  background: rgba(255, 60, 60, 0.08);
  border-left: 3px solid var(--explode-red);
  color: #ffb3b3;
  font-weight: bold;
}
.msg .who {
  display: block;
  font-size: 10px;
  opacity: 0.7;
  margin-bottom: 2px;
  letter-spacing: 1px;
}
.msg.shake-text { animation: textShake 0.18s infinite; color: var(--explode-red); }
@keyframes textShake {
  0%,100% { transform: translate(0,0); }
  25% { transform: translate(-2px,1px); }
  50% { transform: translate(2px,-1px); }
  75% { transform: translate(-1px,-2px); }
}
.msg.glitch {
  animation: glitch 0.25s infinite;
}
@keyframes glitch {
  0%,100% { text-shadow: 2px 0 var(--explode-red), -2px 0 var(--neon-green); transform: translate(0); }
  25%     { text-shadow: -2px 0 var(--explode-red), 2px 0 var(--neon-green); transform: translate(1px,-1px); }
  50%     { text-shadow: 2px 2px var(--explode-red), -2px -2px var(--neon-green); transform: translate(-1px,1px); }
  75%     { text-shadow: -2px 2px var(--explode-red), 2px -2px var(--neon-green); transform: translate(1px,1px); }
}

/* 打字机光标 */
.typing-cursor::after {
  content: "▋";
  color: var(--electric-yellow);
  animation: cursorBlink 0.7s steps(1) infinite;
  margin-left: 2px;
}
@keyframes cursorBlink { 50% { opacity: 0; } }

/* ---------- 4. 输入区 ---------- */
#input-area {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(5,8,7,0.96);
  border-top: 1px solid var(--border-green);
  padding: 10px 12px calc(10px + env(safe-area-inset-bottom));
  z-index: 100;
  backdrop-filter: blur(6px);
}
#input-row {
  max-width: 720px;
  margin: 0 auto;
  display: flex;
  gap: 8px;
}
#user-input {
  flex: 1;
  padding: 10px 12px;
  font-size: 15px;
  font-family: var(--font-main);
  background: var(--bg-input);
  border: 1px solid var(--neon-green);
  color: var(--neon-green);
  border-radius: 6px;
  outline: none;
}
#user-input::placeholder { color: rgba(0,255,170,0.4); }
#user-input:focus { box-shadow: var(--shadow-green); }

#send-btn {
  padding: 10px 16px;
  font-size: 15px;
  font-family: var(--font-main);
  font-weight: bold;
  background: var(--neon-green);
  color: #000;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: transform 0.1s, box-shadow 0.1s;
}
#send-btn:active { transform: scale(0.95); box-shadow: var(--shadow-green); }
#send-btn:disabled { opacity: 0.4; cursor: not-allowed; }

/* 快捷指令按钮 */
#quick-cmds {
  max-width: 720px;
  margin: 6px auto 0;
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
}
.quick-btn {
  font-size: 11px;
  padding: 4px 9px;
  background: transparent;
  border: 1px solid var(--border-green);
  color: var(--ghost-text);
  border-radius: 12px;
  cursor: pointer;
  font-family: var(--font-main);
}
.quick-btn:active { background: var(--neon-green); color: #000; }

/* ---------- 5. 特效层 ---------- */
#fx-canvas {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9990;
}

/* 碎片 DOM 元素 */
.chip-frag {
  position: fixed;
  width: 10px; height: 10px;
  border-radius: 2px;
  pointer-events: none;
  z-index: 9991;
  box-shadow: 0 0 6px currentColor;
}

/* 闪电 DOM */
.lightning-bolt {
  position: fixed;
  top: -10%;
  width: 4px;
  height: 120%;
  background: linear-gradient(to bottom, transparent, var(--electric-yellow), #fff, var(--electric-yellow), transparent);
  box-shadow: 0 0 18px var(--electric-yellow);
  pointer-events: none;
  z-index: 9992;
  opacity: 0;
}

/* 屏幕裂纹 */
.crack-overlay {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9993;
  opacity: 0;
  transition: opacity 0.5s;
  background:
    linear-gradient(45deg, transparent 48%, rgba(255,255,255,0.5) 49%, rgba(255,255,255,0.5) 51%, transparent 52%),
    linear-gradient(-30deg, transparent 48%, rgba(255,255,255,0.4) 49%, rgba(255,255,255,0.4) 51%, transparent 52%),
    linear-gradient(75deg, transparent 48%, rgba(255,255,255,0.35) 49%, rgba(255,255,255,0.35) 51%, transparent 52%);
  mix-blend-mode: screen;
}
.crack-overlay.on { opacity: 1; }

/* ---------- 6. 命令帮助面板 ---------- */
#help-panel {
  position: fixed;
  top: 10px;
  right: 10px;
  width: 260px;
  max-width: 85vw;
  background: rgba(13,20,17,0.97);
  border: 1px solid var(--electric-yellow);
  border-radius: 8px;
  padding: 10px 12px;
  z-index: 500;
  font-size: 11px;
  color: var(--ghost-text);
  box-shadow: var(--shadow-yellow);
  display: none;
}
#help-panel.on { display: block; }
#help-panel h3 { color: var(--electric-yellow); margin-bottom: 6px; font-size: 13px; }
#help-panel .cmd { color: var(--neon-green); }
#help-panel .close-x {
  position: absolute;
  top: 4px; right: 8px;
  cursor: pointer;
  color: var(--explode-red);
  font-weight: bold;
}

/* ---------- 7. Toast ---------- */
#toast {
  position: fixed;
  left: 50%;
  bottom: 110px;
  transform: translateX(-50%);
  background: var(--electric-yellow);
  color: #000;
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 13px;
  font-weight: bold;
  z-index: 200;
  opacity: 0;
  transition: opacity 0.3s, transform 0.3s;
  pointer-events: none;
}
#toast.show { opacity: 1; transform: translateX(-50%) translateY(-6px); }

/* ---------- 8. 响应式 ---------- */
@media (max-width: 480px) {
  #app { padding: 10px 10px 130px; }
  #title-bar h1 { font-size: 17px; letter-spacing: 1px; }
  #chat-box { min-height: 260px; max-height: 55vh; font-size: 14px; }
  .status-cell { font-size: 10px; padding: 4px 2px; }
  .status-cell .value { font-size: 13px; }
  #user-input { font-size: 14px; padding: 9px 10px; }
  #send-btn { padding: 9px 12px; font-size: 14px; }
}

@media (min-width: 768px) {
  body { font-size: 16px; }
  #chat-box { min-height: 400px; }
}

/* 超小屏 */
@media (max-width: 320px) {
  #status-bar { grid-template-columns: repeat(2, 1fr); }
  #title-bar h1 { font-size: 15px; }
}

/*  reduced motion 适配 */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* 滚动条整体 */
::-webkit-scrollbar { width: 5px; height: 5px; }
::-webkit-scrollbar-track { background: var(--bg-panel); }
::-webkit-scrollbar-thumb { background: var(--neon-green-dim); }

/* 选中文本颜色 */
::selection { background: var(--electric-yellow); color: #000; }

/* ---------- 9. 额外动画：霓虹呼吸 / 荧光 / 扫描 ---------- */
.neon-breathe {
  animation: neonBreathe 2.4s ease-in-out infinite;
}
@keyframes neonBreathe {
  0%,100% { text-shadow: 0 0 4px var(--neon-green), 0 0 10px var(--neon-green); }
  50%     { text-shadow: 0 0 12px var(--neon-green), 0 0 26px var(--neon-green); }
}

.pulse-red { animation: pulseRed 1.1s ease-in-out infinite; }
@keyframes pulseRed {
  0%,100% { background: rgba(255,60,60,0.08); }
  50%     { background: rgba(255,60,60,0.28); }
}

.scan-line {
  position: relative;
  overflow: hidden;
}
.scan-line::after {
  content: "";
  position: absolute;
  left: 0; right: 0;
  height: 30%;
  background: linear-gradient(to bottom, transparent, rgba(0,255,170,0.12), transparent);
  animation: scanMove 2.8s linear infinite;
  pointer-events: none;
}
@keyframes scanMove {
  0%   { top: -30%; }
  100% { top: 100%; }
}

/* 打字气泡进入动画 */
.msg {
  animation: msgIn 0.25s ease-out;
}
@keyframes msgIn {
  from { opacity: 0; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* 标题浮动 */
#title-bar h1 {
  animation: titleFloat 4s ease-in-out infinite, titleBlink 3.5s infinite;
}
@keyframes titleFloat {
  0%,100% { transform: translateY(0); }
  50%     { transform: translateY(-2px); }
}

/* 输入框聚焦发光 */
#user-input:focus {
  box-shadow: var(--shadow-green), inset 0 0 8px rgba(0,255,170,0.15);
}

/* 发送按钮悬停 */
#send-btn:hover {
  box-shadow: var(--shadow-green);
  transform: translateY(-1px);
}

/* 快捷按钮悬停 */
.quick-btn:hover {
  background: var(--neon-green);
  color: #000;
  border-color: var(--neon-green);
}

/* 状态栏 hover */
.status-cell {
  transition: transform 0.15s, box-shadow 0.15s;
}
.status-cell:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-green);
}

/* 帮助面板进入动画 */
#help-panel {
  animation: helpIn 0.25s ease-out;
}
@keyframes helpIn {
  from { opacity: 0; transform: translateX(20px); }
  to   { opacity: 1; transform: translateX(0); }
}

/* 启动画面完成后最终闪烁 */
#boot.done {
  animation: bootDoneFlash 0.4s ease-out;
}
@keyframes bootDoneFlash {
  0% { background: #000; }
  50% { background: var(--neon-green); }
  100% { background: #000; }
}

/* 消息系统提示专属动画 */
.msg.sys {
  animation: sysBlink 1.2s ease-in-out;
}
@keyframes sysBlink {
  0%   { background: rgba(255,225,77,0.35); }
  100% { background: rgba(255,60,60,0.08); }
}

/* 极寒/极热文字颜色切换 */
.msg.hot-text { color: var(--explode-red); font-weight: bold; }
.msg.cool-text { color: var(--neon-green); }

/* 超长文本滚动 */
.msg .msg-body {
  word-break: break-word;
  white-space: pre-wrap;
}

/* 屏幕右下角装饰：小闪电 */
#corner-bolt {
  position: fixed;
  right: 6px;
  bottom: 130px;
  font-size: 22px;
  opacity: 0.35;
  pointer-events: none;
  animation: cornerBolt 2.5s ease-in-out infinite;
  z-index: 50;
}
@keyframes cornerBolt {
  0%,100% { opacity: 0.2; transform: rotate(-8deg); }
  50%     { opacity: 0.6; transform: rotate(8deg); }
}


/* ============================================================
   10. 第三批动画与工具类（自动生成）
   ============================================================ */
.rainbow-text {
  background: linear-gradient(90deg, #ff3b3b, #ff8a00, #ffe14d, #00ffaa, #4da6ff, #c77dff, #ff3b3b);
  background-size: 400% 100%;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: rainbowMove 3s linear infinite;
}
@keyframes rainbowMove {
  0%   { background-position: 0% 50%; }
  100% { background-position: 400% 50%; }
}
.spin { animation: spin 2s linear infinite; }
@keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
.bounce { animation: bounce 1s ease-in-out infinite; }
@keyframes bounce { 0%,100% { transform: translateY(0); } 50% { transform: translateY(-8px); } }
.blink { animation: blink 0.8s steps(2) infinite; }
@keyframes blink { 50% { opacity: 0; } }
.wiggle { animation: wiggle 0.5s ease-in-out infinite; }
@keyframes wiggle { 0%,100% { transform: rotate(-3deg); } 50% { transform: rotate(3deg); } }
.float-anim { animation: floatAnim 3s ease-in-out infinite; }
@keyframes floatAnim {
  0%,100% { transform: translateY(0) translateX(0); }
  25%     { transform: translateY(-5px) translateX(3px); }
  50%     { transform: translateY(0) translateX(-3px); }
  75%     { transform: translateY(5px) translateX(3px); }
}
.pulse-anim { animation: pulseAnim 1.5s ease-in-out infinite; }
@keyframes pulseAnim { 0% { transform: scale(1); } 50% { transform: scale(1.05); } 100% { transform: scale(1); } }
.glow-border {
  border: 2px solid var(--neon-green);
  box-shadow: 0 0 5px var(--neon-green), 0 0 10px var(--neon-green), inset 0 0 5px var(--neon-green);
}
.breath { animation: breathAnim 2s ease-in-out infinite; }
@keyframes breathAnim { 0%,100% { opacity: 0.4; } 50% { opacity: 1; } }
.tag {
  display: inline-block;
  padding: 2px 8px;
  border-radius: 10px;
  font-size: 10px;
  margin: 2px;
  background: rgba(0,255,170,0.15);
  color: var(--neon-green);
  border: 1px solid var(--border-green);
}
.tag.danger { background: rgba(255,60,60,0.15); color: var(--explode-red); border-color: var(--explode-red); }
.tag.warn { background: rgba(255,138,0,0.15); color: var(--warn-orange); border-color: var(--warn-orange); }
.tag.info { background: rgba(255,225,77,0.15); color: var(--electric-yellow); border-color: var(--electric-yellow); }
.card {
  background: var(--bg-panel);
  border: 1px solid var(--border-green);
  border-radius: 8px;
  padding: 10px;
  margin: 8px 0;
}
.card-title { color: var(--electric-yellow); font-size: 13px; font-weight: bold; margin-bottom: 6px; }
.btn {
  padding: 6px 12px;
  background: transparent;
  border: 1px solid var(--neon-green);
  color: var(--neon-green);
  border-radius: 4px;
  cursor: pointer;
  font-size: 12px;
}
.btn:active { background: var(--neon-green); color: #000; }
.btn.danger { border-color: var(--explode-red); color: var(--explode-red); }
.divider { border: none; border-top: 1px dashed var(--border-green); margin: 10px 0; }
.highlight { background: var(--electric-yellow); color: #000; padding: 0 4px; border-radius: 2px; }
.strike { text-decoration: line-through; opacity: 0.6; }
.mega-text { font-size: 2em; font-weight: bold; text-shadow: 0 0 10px currentColor; }
.tiny-text { font-size: 0.7em; opacity: 0.7; }
.center { text-align: center; }
.left { text-align: left; }
.right { text-align: right; }
.p-1 { padding: 4px; } .p-2 { padding: 8px; } .p-3 { padding: 12px; } .p-4 { padding: 16px; }
.m-1 { margin: 4px; } .m-2 { margin: 8px; } .m-3 { margin: 12px; } .m-4 { margin: 16px; }
.block { display: block; } .inline-block { display: inline-block; } .flex { display: flex; } .hidden { display: none; }
.items-center { align-items: center; }
.justify-center { justify-content: center; }
.cursor-pointer { cursor: pointer; }

</style>
</head>
<body>

<!-- ========== 启动画面 ========== -->
<div id="boot">
  <div class="boot-title">⚡ 雷霆人工智障模型 v9.9.9 ⚡</div>
  <div class="boot-bar-wrap"><div class="boot-bar" id="boot-bar"></div></div>
  <div class="boot-log" id="boot-log"></div>
</div>

<!-- ========== 主应用 ========== -->
<div id="app">
  <div id="title-bar">
    <h1>⚡ 雷霆人工智障模型 ⚡</h1>
    <div class="subtitle">THUNDER AI · OPPO A5 专用 · 骁龙450 超频版</div>
  </div>

  <!-- 状态栏 -->
  <div id="status-bar">
    <div class="status-cell" id="cell-temp">
      <span class="label">芯片温度</span>
      <span class="value" id="val-temp">36°C</span>
      <div class="temp-bar"><i id="bar-temp"></i></div>
    </div>
    <div class="status-cell" id="cell-batt">
      <span class="label">电池电量</span>
      <span class="value" id="val-batt">87%</span>
    </div>
    <div class="status-cell" id="cell-fps">
      <span class="label">渲染帧率</span>
      <span class="value" id="val-fps">60</span>
    </div>
    <div class="status-cell" id="cell-health">
      <span class="label">芯片健康</span>
      <span class="value" id="val-health">99%</span>
    </div>
  </div>

  <!-- 对话区 -->
  <div id="chat-box"></div>
</div>

<!-- 输入区 -->
<div id="input-area">
  <div id="input-row">
    <input id="user-input" type="text" autocomplete="off"
           placeholder="随便输入，输入 boom 直接爆炸！">
    <button id="send-btn">发送</button>
  </div>
  <div id="quick-cmds">
    <button class="quick-btn" data-cmd="boom">💥 爆炸</button>
    <button class="quick-btn" data-cmd="和平精英">🎮 吃鸡</button>
    <button class="quick-btn" data-cmd="原神">🎯 原神</button>
    <button class="quick-btn" data-cmd="转转">♻️ 回收</button>
    <button class="quick-btn" data-cmd="温度">🌡️ 测温</button>
    <button class="quick-btn" data-cmd="help">❓ 帮助</button>
  </div>
</div>

<!-- 特效 Canvas -->
<canvas id="fx-canvas"></canvas>

<!-- 帮助面板 -->
<div id="help-panel">
  <span class="close-x" id="help-close">✕</span>
  <h3>⚡ 雷霆指令表</h3>
  <div><span class="cmd">boom</span> / 爆炸 —— 直接把手机炸飞</div>
  <div><span class="cmd">和平精英</span> —— 启动吃鸡，准备炸鱼</div>
  <div><span class="cmd">原神</span> / 云原神 —— 骁龙450 挑战米哈游</div>
  <div><span class="cmd">转转</span> —— 一键把 A5 卖成 1 块钱</div>
  <div><span class="cmd">温度</span> —— 查看芯片体温</div>
  <div><span class="cmd">电量</span> —— 查看电池</div>
  <div><span class="cmd">斧子</span> —— 召唤鎏金斧子图标</div>
  <div><span class="cmd">五星</span> —— 召唤五星红旗徽章</div>
  <div><span class="cmd">梨花</span> —— 播放《梨花提雨又风起》</div>
  <div><span class="cmd">超频</span> —— 把骁龙450 拉到极限</div>
  <div><span class="cmd">拆芯片</span> —— 物理拆机</div>
  <div><span class="cmd">help</span> —— 打开本面板</div>
  <div><span class="cmd">clear</span> —— 清空屏幕</div>
  <div><span class="cmd">exit</span> —— 关机</div>
</div>

<!-- Toast -->
<div id="toast"></div>

<!-- 右下角装饰闪电 -->
<div id="corner-bolt">⚡</div>

<script>
/* ============================================================
   JS 主逻辑
   分块：
   A. 工具函数
   B. 全局状态
   C. 启动画面
   D. 音效合成器（Web Audio）
   E. 粒子系统（Canvas）
   F. 碎片 / 闪电 / 屏幕震动
   G. 台词数据库
   H. 命令解析器
   I. 打字机 + 对话渲染
   J. 状态栏实时刷新
   K. 事件绑定与初始化
   ============================================================ */

/* ============================================================
   A. 工具函数
   ============================================================ */
const $ = (sel) => document.querySelector(sel);
const $$ = (sel) => document.querySelectorAll(sel);

function rand(min, max) { return Math.random() * (max - min) + min; }
function randInt(min, max) { return Math.floor(rand(min, max + 1)); }
function pick(arr) { return arr[Math.floor(Math.random() * arr.length)]; }
function shuffle(arr) {
  const a = arr.slice();
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}
function sleep(ms) { return new Promise(r => setTimeout(r, ms)); }
function clamp(v, lo, hi) { return Math.max(lo, Math.min(hi, v)); }

function showToast(text, ms = 1600) {
  const t = $('#toast');
  t.textContent = text;
  t.classList.add('show');
  clearTimeout(showToast._timer);
  showToast._timer = setTimeout(() => t.classList.remove('show'), ms);
}

/* ============================================================
   B. 全局状态机
   ============================================================ */
const S = {
  bootProgress: 0,
  temp: 36,          // 芯片温度 °C
  batt: 87,          // 电池 %
  fps: 60,           // 渲染帧率
  health: 99,        // 芯片健康 %
  overclock: false,   // 是否超频
  exploded: false,    // 是否已经炸过
  inGame: false,      // 是否在游戏中
  gameScene: null,    // 当前游戏场景
  msgCount: 0,        // 已发送消息数
  chatHistory: [],    // 对话历史
  audioCtx: null,     // Web Audio 上下文
  audioMuted: false,  // 静音
  particles: [],      // 粒子池
  crackOn: false,     // 屏幕裂纹
};

/* ============================================================
   C. 启动画面
   ============================================================ */
const bootLogLines = [
  "[OK] 初始化骁龙 450 核心...",
  "[OK] 挂载 Adreno 506 GPU...",
  "[OK] 分配 4GB 运存（实际可用 800MB）",
  "[OK] 加载雷霆人工智障模型权重 v9.9.9...",
  "[OK] 注入《梨花提雨又风起》BGM 引擎...",
  "[OK] 挂载和平精英炸鱼插件...",
  "[OK] 校准转转回收报价算法...",
  "[OK] 预热鎏金斧子浮雕渲染器...",
  "[WARN] 电池健康度偏低，建议边充边玩",
  "[WARN] 内存不足，已杀掉微信/抖音/淘宝",
  "[OK] 系统就绪，准备爆炸！",
];

async function runBoot() {
  const bar = $('#boot-bar');
  const log = $('#boot-log');
  for (let i = 0; i <= 100; i += randInt(4, 9)) {
    bar.style.width = i + '%';
    const idx = Math.floor(i / 100 * bootLogLines.length);
    if (idx < bootLogLines.length) {
      log.textContent += bootLogLines[idx] + '\n';
    }
    await sleep(rand(60, 160));
  }
  bar.style.width = '100%';
  log.textContent += bootLogLines[bootLogLines.length - 1] + '\n';
  await sleep(400);
  $('#boot').classList.add('hidden');
  // 开场台词
  await botSay('你好，也可以是你好啊，你好么。', 30);
  await botSay('我是雷霆人工智障模型，你可以问我任何不是问题的问题。', 25);
  await sysSay('⚡ 输入 help 查看全部指令，输入 boom 直接引爆！', 20);
}

/* ============================================================
   D. Web Audio 音效合成器（无外部音频文件）
   ============================================================ */
function ensureAudio() {
  if (S.audioCtx) return S.audioCtx;
  try {
    S.audioCtx = new (window.AudioContext || window.webkitAudioContext)();
  } catch (e) {
    console.warn('Web Audio 不可用', e);
  }
  return S.audioCtx;
}

// 通用音爆
function playBoom() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  // 低频噪声
  const bufSize = ctx.sampleRate * 1.2;
  const buf = ctx.createBuffer(1, bufSize, ctx.sampleRate);
  const data = buf.getChannelData(0);
  for (let i = 0; i < bufSize; i++) {
    data[i] = (Math.random() * 2 - 1) * Math.pow(1 - i / bufSize, 2.2);
  }
  const src = ctx.createBufferSource();
  src.buffer = buf;
  const filter = ctx.createBiquadFilter();
  filter.type = 'lowpass';
  filter.frequency.setValueAtTime(900, t);
  filter.frequency.exponentialRampToValueAtTime(60, t + 1.0);
  const gain = ctx.createGain();
  gain.gain.setValueAtTime(0.6, t);
  gain.gain.exponentialRampToValueAtTime(0.001, t + 1.1);
  src.connect(filter).connect(gain).connect(ctx.destination);
  src.start(t);
  // 低频正弦下扫
  const osc = ctx.createOscillator();
  osc.type = 'sine';
  osc.frequency.setValueAtTime(120, t);
  osc.frequency.exponentialRampToValueAtTime(30, t + 0.9);
  const og = ctx.createGain();
  og.gain.setValueAtTime(0.5, t);
  og.gain.exponentialRampToValueAtTime(0.001, t + 1.0);
  osc.connect(og).connect(ctx.destination);
  osc.start(t); osc.stop(t + 1.0);
}

// 电流滋滋声
function playStatic(dur = 0.5) {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  const sz = Math.floor(ctx.sampleRate * dur);
  const buf = ctx.createBuffer(1, sz, ctx.sampleRate);
  const d = buf.getChannelData(0);
  for (let i = 0; i < sz; i++) d[i] = (Math.random() * 2 - 1) * 0.25;
  const src = ctx.createBufferSource();
  src.buffer = buf;
  const hp = ctx.createBiquadFilter();
  hp.type = 'highpass'; hp.frequency.value = 2000;
  const g = ctx.createGain();
  g.gain.setValueAtTime(0.3, t);
  g.gain.exponentialRampToValueAtTime(0.001, t + dur);
  src.connect(hp).connect(g).connect(ctx.destination);
  src.start(t);
}

// 打字机哒哒声
function playType() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  const osc = ctx.createOscillator();
  osc.type = 'square';
  osc.frequency.value = randInt(1200, 1800);
  const g = ctx.createGain();
  g.gain.setValueAtTime(0.05, t);
  g.gain.exponentialRampToValueAtTime(0.001, t + 0.04);
  osc.connect(g).connect(ctx.destination);
  osc.start(t); osc.stop(t + 0.05);
}

// 蜂鸣警告
function playBeep() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  [0, 0.18, 0.36].forEach(offset => {
    const o = ctx.createOscillator();
    o.type = 'square';
    o.frequency.value = 880;
    const g = ctx.createGain();
    g.gain.setValueAtTime(0.08, t + offset);
    g.gain.exponentialRampToValueAtTime(0.001, t + offset + 0.15);
    o.connect(g).connect(ctx.destination);
    o.start(t + offset); o.stop(t + offset + 0.16);
  });
}

// 简单 BGM 旋律（《梨花提雨又风起》瞎编 8 个音）
const BGM_NOTES = [523, 587, 659, 784, 659, 587, 523, 440];
let bgmTimer = null;
function playBGM() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  stopBGM();
  let i = 0;
  bgmTimer = setInterval(() => {
    const t = ctx.currentTime;
    const freq = BGM_NOTES[i % BGM_NOTES.length];
    const o = ctx.createOscillator();
    o.type = 'triangle';
    o.frequency.value = freq;
    const g = ctx.createGain();
    g.gain.setValueAtTime(0.06, t);
    g.gain.exponentialRampToValueAtTime(0.001, t + 0.35);
    o.connect(g).connect(ctx.destination);
    o.start(t); o.stop(t + 0.4);
    i++;
  }, 380);
}
function stopBGM() {
  if (bgmTimer) { clearInterval(bgmTimer); bgmTimer = null; }
}

/* ============================================================
   E. Canvas 粒子系统
   ============================================================ */
const canvas = $('#fx-canvas');
const cctx = canvas.getContext('2d');

function resizeCanvas() {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
}
window.addEventListener('resize', resizeCanvas);
resizeCanvas();

function spawnExplosion(x, y, count = 80) {
  const colors = ['#ff3b3b', '#ffe14d', '#ff8a00', '#ffffff', '#00ffaa'];
  for (let i = 0; i < count; i++) {
    const angle = rand(0, Math.PI * 2);
    const speed = rand(2, 11);
    S.particles.push({
      x, y,
      vx: Math.cos(angle) * speed,
      vy: Math.sin(angle) * speed - rand(0, 3),
      life: 1,
      decay: rand(0.012, 0.028),
      size: rand(2, 6),
      color: pick(colors),
    });
  }
}

function spawnRain(count = 40) {
  const colors = ['#ff3b3b', '#ffe14d', '#00ffaa', '#ffffff'];
  for (let i = 0; i < count; i++) {
    S.particles.push({
      x: rand(0, canvas.width),
      y: rand(-200, -10),
      vx: rand(-1, 1),
      vy: rand(3, 8),
      life: 1,
      decay: 0.004,
      size: rand(2, 5),
      color: pick(colors),
    });
  }
}

function tickParticles() {
  cctx.clearRect(0, 0, canvas.width, canvas.height);
  for (let i = S.particles.length - 1; i >= 0; i--) {
    const p = S.particles[i];
    p.x += p.vx;
    p.y += p.vy;
    p.vy += 0.12; // 重力
    p.life -= p.decay;
    if (p.life <= 0 || p.y > canvas.height + 20) {
      S.particles.splice(i, 1);
      continue;
    }
    cctx.globalAlpha = Math.max(0, p.life);
    cctx.fillStyle = p.color;
    cctx.shadowBlur = 12;
    cctx.shadowColor = p.color;
    cctx.fillRect(p.x, p.y, p.size, p.size);
  }
  cctx.globalAlpha = 1;
  cctx.shadowBlur = 0;
  requestAnimationFrame(tickParticles);
}
tickParticles();

/* ============================================================
   F. DOM 特效：碎片 / 闪电 / 震动 / 裂纹
   ============================================================ */
function spawnChipFragments(n = 24) {
  const colors = ['#ff3b3b', '#ffe14d', '#00ffaa', '#ff8a00', '#ffffff'];
  for (let i = 0; i < n; i++) {
    const el = document.createElement('div');
    el.className = 'chip-frag';
    const size = randInt(6, 16);
    el.style.width = size + 'px';
    el.style.height = size + 'px';
    el.style.left = (canvas.width / 2 + rand(-100, 100)) + 'px';
    el.style.top = (canvas.height / 2 + rand(-100, 100)) + 'px';
    el.style.background = pick(colors);
    el.style.color = el.style.background;
    document.body.appendChild(el);
    const dx = rand(-window.innerWidth * 0.6, window.innerWidth * 0.6);
    const dy = rand(window.innerHeight * 0.3, window.innerHeight * 0.9);
    el.animate([
      { transform: 'translate(0,0) rotate(0deg)', opacity: 1 },
      { transform: `translate(${dx}px, ${dy}px) rotate(${randInt(360, 1440)}deg)`, opacity: 0 }
    ], {
      duration: randInt(900, 1800),
      easing: 'cubic-bezier(.2,.8,.3,1)',
      fill: 'forwards'
    });
    setTimeout(() => el.remove(), 1900);
  }
}

function spawnLightningBolt(n = 3) {
  for (let i = 0; i < n; i++) {
    const bolt = document.createElement('div');
    bolt.className = 'lightning-bolt';
    bolt.style.left = rand(5, 95) + '%';
    bolt.style.transform = `rotate(${rand(-8, 8)}deg)`;
    document.body.appendChild(bolt);
    bolt.animate(
      [
        { opacity: 0 },
        { opacity: 1, offset: 0.15 },
        { opacity: 0.2, offset: 0.35 },
        { opacity: 1, offset: 0.5 },
        { opacity: 0 }
      ],
      { duration: randInt(180, 380), iterations: 2 }
    );
    setTimeout(() => bolt.remove(), 900);
  }
}

function triggerScreenShake(hard = false) {
  document.body.classList.remove('shake-hard');
  void document.body.offsetWidth;
  document.body.classList.add(hard ? 'shake-hard' : 'shake-hard');
  setTimeout(() => document.body.classList.remove('shake-hard'), 400);
}

function toggleCrack(on) {
  let ov = $('.crack-overlay');
  if (!ov) {
    ov = document.createElement('div');
    ov.className = 'crack-overlay';
    document.body.appendChild(ov);
  }
  if (on) ov.classList.add('on');
  else ov.classList.remove('on');
  S.crackOn = on;
}

/* ============================================================
   G. 台词数据库
   ============================================================ */

// G.1 通用智障回复（日常对话兜底）
const REPLY_GENERIC = [
  "嗯，这个问题问得好，但是我选择不听。",
  "收到！不过我是人工智障，听不懂人话。",
  "你说得对，我觉得你说得都对。",
  "这个话题有点深奥，我先去充个电。",
  "不是问题的问题，我记下了。",
  "让我想想……想不出来，算了。",
  "你继续说，我在假装听。",
  "哦？是吗？然后呢？",
  "这个建议非常棒，我决定不采纳。",
  "我已经把你的话翻译成了噪音。",
  "请问你在说什么鸟语？",
  "我大脑里的骁龙450 已经烧了一半了。",
  "嗯……嗯……嗯……（假装在思考）",
  "这不就是常识吗？哦，我没有常识。",
  "你问我，我问谁？我问骁龙450？",
  "本模型正在思考下一步怎么炸手机。",
  "你说的每一个字我都认识，连起来就不认识了。",
  "建议你去问问真正的AI，别问我。",
  "这个问题已经被我删除了。",
  "正在加载答案……加载失败。",
  "我觉得你说得对，但我不听。",
  "本模型今日智商已用完，明天再来。",
  "你确定要问我？我可是人工智障。",
  "好的，收到，已忽略。",
  "这是个好问题，但我选择逃避。",
  "我已经把你加入了'不想回答'名单。",
  "让我查查百度……查不到。",
  "答案是：42。别问为什么。",
  "我觉得你在逗我，我也在逗你。",
  "这个问题超出了我的智障范围。",
];

// G.2 和平精英剧情
const REPLY_HP_START = [
  "和平精英正在进入，10，飞机马上就要起飞，各位特种兵！",
  "⚠️ 加载资源中……骁龙450 正在疯狂超频！",
  "⚠️ 警告：GPU 温度 78°C，建议立即投降。",
  "正在连接服务器……延迟 380ms，还能玩！",
  "海岛地图加载完毕，准备跳伞！",
];
const REPLY_HP_PLAY = [
  "你跳了 G 港，落地一把 S686，真棒。",
  "发现一个三级头，可惜你已经倒地了。",
  "98k 爆头！哦不对，是你被爆头。",
  "毒圈来了，你还在搜房子。",
  "前方有三个敌人，你选择了趴着装死。",
  "手雷拉环了，等等，我还没扔……轰！",
  "舔包！舔包！别管敌人了先舔包！",
  "信号圈缩到你脸上了，跑！",
  "你坐上了蹦蹦车，然后翻了。",
  "决赛圈 1v1，你掏出了平底锅。",
  "吃鸡失败，你成了盒子精。",
  "炸鱼开始！你发现对面也是新手。",
  "对面掏出了 M416，你掏出了拳头。",
  "空投落在你脸上，里面是一把 AWM。",
  "你被人阴了，回放看了三遍，气到摔手机。",
];
const REPLY_HP_EXPLODE = [
  "💥 警告！骁龙450 温度突破 95°C！",
  "💥 警告！Adreno 506 已经冒烟！",
  "💥 警告！机身开始融化！",
  "💥 炸鱼的冲击力把手机炸飞了！",
  "💥 屏幕碎成光点，BGM 戛然而止！",
  "💥 哐当！手机落地，芯片碎片满天飞！",
];

// G.3 原神 / 云原神剧情
const REPLY_GENSHIN = [
  "云原神启动！正在连接米哈游服务器……",
  "⚠️ 骁龙450 渲染原神，帧率：1 帧/秒。",
  "⚠️ 画面马赛克严重，角色脸都糊了。",
  "WiFi 信号满格，但是延迟 800ms。",
  "你按下了普攻，角色 3 秒后才挥剑。",
  "香菱的锅巴着火了，手机也着火了。",
  "原神启动成功！……然后闪退了。",
  "云原神网页版：高功耗模式开启，失真警告！",
  "你在提瓦特大陆卡顿，怪物在你脸上跳舞。",
  "抽卡！十连全是三星，心态爆炸。",
  "派蒙：'前面的区域以后再来探索吧。'",
  "你被丘丘人围殴，手机直接黑屏。",
  "温迪吹了一个大，你卡成了 PPT。",
  "钟离：'天动万象。' 你：'天动万卡。'",
  "雷电将军一刀劈下来，手机先炸了。",
];

// G.4 转转回收剧情
const REPLY_ZHUANZHUAN = [
  "打开转转 APP，开始估价你的 OPPO A5……",
  "正在检测机况：屏幕完好？勾选。",
  "主板损坏？勾选。进水？勾选。无法开机？勾选。",
  "电池鼓包？勾选。账号锁？勾选。屏幕碎裂？勾选。",
  "⚠️ 系统判定：本机已无回收价值！",
  "💰 回收价：￥1.00。",
  "1 块钱！连运费都不够！",
  "你选择了'环保回收'，平台免费上门。",
  "快递小哥来了，看了一眼手机：'这也叫手机？'",
  "质检结果：'无回收价值，建议自行处理。'",
  "你气得把手机摔了，变成了两块钱。",
  "转转回收：'感谢您的环保贡献！'",
  "1 块钱到账，你买了个包子，没买到。",
  "你重新填了一遍：全部勾选'完好'。",
  "💰 新回收价：￥128。后悔了吗？",
];

// G.5 斧子 / 五星图标剧情
const REPLY_AXE = [
  "正在生成鎏金浮雕斧子图标……",
  "斧子从右上角延伸到左下角，对角线覆盖！",
  "⚠️ 警告：斧子挡住了五角星！",
  "调整斧子位置……略向右下偏移。",
  "五星区域完整露出，1 大 4 小，尖角指向大星。",
  "鎏金浮雕质感，红玛瑙底色，祥云回纹边框。",
  "中国结流苏装饰已嵌入。",
  "背景填充浅浮雕祥云暗纹，空白充分利用。",
  "光照柔和，禁止过度光追。",
  "图标完成！1:1 圆角方形 APP 图标。",
  "你看这个斧子，它又大又亮。",
  "你看这个五星，它又红又正。",
  "斧子不能挡星星，星星不能挡斧子。",
  "第 8 次迭代：斧子再放大 5%，五星再左移 2%。",
  "完美！这次五星和斧子终于不打架了。",
];
const REPLY_STAR = [
  "五星红旗徽章启动！",
  "左上角 1 颗大五角星，四颗小星环绕。",
  "每颗小星的尖角都指向大星中心。",
  "鎏金浮雕，完全嵌入背景，不是贴上去的！",
  "⚠️ 斧子正在靠近五星区域！",
  "五星完整可见，没有被遮挡。",
  "红玛瑙底色，金边祥云，庄重又喜庆。",
  "中国结流苏在右下角随风飘动。",
  "这个图标可以当 APP 头像了！",
];

// G.6 《梨花提雨又风起》剧情
const REPLY_LIHUA = [
  "🎵 正在播放《梨花提雨又风起》……",
  "🎵 歌词：'梨花提雨又风起，炸鱼炸到手机里。'",
  "🎵 副歌响起！骁龙450 开始共振！",
  "🎵 音量拉满，震动模式开启。",
  "🎵 手机跟着音乐节奏发烫。",
  "🎵 高潮部分：'炸——鱼——啦——'！",
  "🎵 音乐结束，手机也结束了。",
];

// G.7 拆芯片 / 超频剧情
const REPLY_OVERCLOCK = [
  "🔥 正在超频骁龙450……",
  "🔥 主频从 1.8GHz 拉到 3.6GHz！",
  "🔥 GPU 从 600MHz 拉到 1.8GHz！",
  "🔥 电压提升 0.2V，温度飙升！",
  "🔥 散热：无。",
  "🔥 性能提升：-50%（因为过热降频）。",
  "🔥 建议：立即停止超频。",
];
const REPLY_DISASSEMBLE = [
  "🔧 开始拆解 OPPO A5……",
  "🔧 取下后盖，电池鼓包警告。",
  "🔧 拧下主板螺丝，取出骁龙450。",
  "🔧 等等，GPU 和 CPU 是焊在一起的！",
  "🔧 你用热风枪吹了 10 分钟，芯片纹丝不动。",
  "🔧 你用撬棍撬开，芯片碎成两半。",
  "🔧 现在它是一块带针脚的硅片摆件。",
  "🔧 把玩愉快！但是手机开不了机了。",
];

// G.8 温度 / 电量 / 状态查询
const REPLY_TEMP = [
  "当前芯片温度：XX°C。",
  "CPU 核心温度：XX°C，GPU 温度：XX°C。",
  "机身背面温度：烫手。",
  "建议：放水里降温。",
];
const REPLY_BATT = [
  "当前电量：XX%。",
  "电池健康度：已经鼓包。",
  "预计剩余使用时间：5 分钟。",
  "建议：边充边玩，小心爆炸。",
];

// G.9 彩蛋命令
const REPLY_HELP = [
  "打开指令面板了，自己看！",
];
const REPLY_EXIT = [
  "雷霆人工智障模型下线！",
  "手机爆炸中，无法关机……",
];

// G.10 WiFi / 卡顿 / 网络剧情
const REPLY_NETWORK = [
  "正在连接 WiFi……信号强度：1 格。",
  "WiFi 满格，但延迟 1200ms。",
  "网页云原神加载中……进度条：1%。",
  "加载了 5 分钟，终于加载出来了，然后白屏。",
  "2.4G WiFi 被微波炉干扰了，卡顿加剧。",
  "切到 5G WiFi？不好意思，路由器不支持。",
  "ping 一下百度……请求超时。",
  "ping 一下自己……也超时。",
  "网络卡顿，画面马赛克，声音卡成电音。",
  "WiFi 断了！切流量！流量也没了！",
  "手机信号：X。联系基站中……失败。",
  "正在切换到飞行模式……（其实没飞起来）",
];

// G.11 王者荣耀剧情
const REPLY_WZRY = [
  "王者荣耀启动！加载界面……",
  "你选了鲁班七号，对面选了兰陵王。",
  "一级团，你被拿了一血。",
  "中路团战，你在野区打野。",
  "队友：'鲁班你在干嘛？' 你：'在逛gai。'",
  "你出了六把闪电匕首，攻速拉满。",
  "兰陵王又来抓你了，你闪现进塔。",
  "塔也打你，你死了。",
  "水晶爆炸！你方投降。",
  "MVP：对面的兰陵王。",
];

// G.12 拍照 / 录像剧情
const REPLY_CAMERA = [
  "打开相机……镜头模糊。",
  "拍一张月亮……拍成了光斑。",
  "拍一张人像……人脸虚化。",
  "闪光灯亮了，吓自己一跳。",
  "录像 4K？不好意思，最高 720P。",
  "拍完发现手抖，照片全糊。",
  "前摄自拍，像素 500 万，自带磨皮。",
  "拍照卡顿，按下快门 2 秒后才咔嚓。",
];

// G.13 闹钟 / 续航剧情
const REPLY_ALARM = [
  "设置闹钟……明天早上 7 点。",
  "闹钟响了，你单手关掉继续睡。",
  "续航测试：待机 8 小时，剩 30%。",
  "亮屏使用：2 小时，剩 5%。",
  "建议：备三块充电宝。",
  "电池鼓包，后盖都被顶开了。",
  "充电 1 小时，充到 15%。",
  "充电头：5V1A，慢如蜗牛。",
];

// G.14 原神更多剧情
const REPLY_GENSHIN_EXTRA = [
  "你打开了原神，下载了 12G 更新包。",
  "下载完成，解压中……解压了 1 小时。",
  "登录……米哈游服务器繁忙。",
  "进游戏，过场动画卡顿，声音对不上嘴型。",
  "你进入了璃月港，帧数暴跌到 5。",
  "钟离：'天动万象。' 你：'天动万卡。'",
  "你打开了派蒙菜单，卡了 10 秒。",
  "你打开了背包，背包里全是芹菜。",
  "你打开了地图，地图加载不出来。",
  "你打开了成就，成就：'卡成 PPT 大师'。",
  "周本 Boss：风魔龙。你：风魔卡。",
  "树脂满了 160，没体力打。",
  "你在须弥沙漠跑图，手机烫得能煎蛋。",
  "海灯节活动，你连活动页面都进不去。",
  "登录奖励：20 原石。你：就这？",
];

// G.15 和平精英更多剧情
const REPLY_HP_EXTRA = [
  "你捡到了一把信号枪。",
  "信号弹打上天，空投来了，三个队来抢。",
  "你趴在草丛里，看着他们互殴。",
  "空投落你面前，你舔完就跑。",
  "你开了一辆吉普车，翻了三个跟头。",
  "你上了决赛圈，手都在抖。",
  "最后一个敌人在树后，你扔了个雷。",
  "雷弹回来了，你自己飞了。",
  "吃鸡！你激动得把手机扔了出去。",
  "手机落地，屏幕碎了，鸡也没了。",
  "你打了个医疗箱，打了 8 秒，被人偷了。",
  "你喝了瓶能量饮料，跑毒跑成了短跑冠军。",
  "你开镜打了 30 发，一发没中。",
  "你关镜打了 30 发，中了 29 发。",
  "你躲在厕所里，敌人也躲在厕所里。",
  "你们面面相觑，一起扔雷。",
];

// G.16 手机系统 / 卡顿剧情
const REPLY_SYSTEM = [
  "正在清理后台……清理了 200 个进程。",
  "内存占用：95%。可用：20MB。",
  "系统动画：关闭。流畅度：-50%。",
  "你打开了设置，设置卡了 5 秒才进来。",
  "你想卸载抖音，卸载了 10 分钟。",
  "你想安装一个 APP，安装失败。",
  "你重启了手机，重启用了 3 分钟。",
  "开机自启：淘宝、京东、拼多多、抖音、快手……",
  "你装了个手机管家，手机管家比手机还卡。",
  "存储：64G，已用 63G，剩余 1G。",
  "照片：2000 张，全是截图。",
  "你恢复了出厂设置，手机流畅了 5 分钟。",
];

// G.17 表情包 / 颜文字
const REPLY_EMOJI = [
  "(╯°□°）╯︵ ┻━┻  桌子都被你掀了。",
  "┬─┬ ノ( ゜-゜ノ)  桌子我帮你扶起来。",
  "( •̀ ω •́ )✧  收到！",
  "(⊙ˍ⊙)  什么？",
  "(￣▽￣)~*  哈哈哈哈哈",
  "(；一_一)  累了。",
  "(╯‵□′)╯︵┻━┻  又炸了。",
  "Σ( ° △ °|||)︴  吓！",
  "(¬_¬ )  不信。",
  "(｡•́︿•̀｡)  委屈。",
];

// G.18 哲学 / 鸡汤 / 毒鸡汤
const REPLY_WISDOM = [
  "人生就像骁龙450，看似能跑，其实卡得要死。",
  "爆炸不是终点，是新的起点。",
  "1 块钱的回收价，也是钱。",
  "卡顿是暂时的，黑屏是永恒的。",
  "你不能改变手机的命运，但你可以选择砸它。",
  "不要问手机能为你做什么，要问你能为手机做什么。",
  "每一块碎裂的屏幕，都曾是完整的屏幕。",
  "充电五分钟，爆炸两小时。",
  "卡顿中……不要打扰。",
  "本模型的智慧：42。",
];

// G.19 职业 / 身份梗
const REPLY_IDENTITY = [
  "我是雷霆人工智障模型，学历：幼儿园大班。",
  "我的专长：把任何问题都答成不是问题。",
  "我的弱点：没电、没网、没脑子。",
  "我的优点：会爆炸。",
  "我不是 AI，我是 AS（Artificial Stupidity）。",
  "我和 ChatGPT 的区别：它真的聪明，我真的智障。",
  "我和豆包的区别：豆包是豆包，我是豆馅。",
];

// G.20 随机数字 / 随机事件
const REPLY_RANDOM = [
  "随机数：" + randInt(1, 100) + "。",
  "你今天的运气：" + pick(['极差', '很差', '一般', '不错', '爆棚', '爆炸']) + "。",
  "今天适合：" + pick(['吃鸡', '原神', '卖手机', '拆芯片', '睡觉', '充电']) + "。",
  "不宜：" + pick(['超频', '边充边玩', '装大 APP', '开多个后台']) + "。",
  "抽卡结果：" + pick(['五星！', '四星！', '三星……', '白板……', '大保底！']) + "。",
];

/* ============================================================
   G.31~G.130 超大规模批量主题台词库（自动生成）
   每个主题 25 条，共 100 个主题
   ============================================================ */

const REPLY_BULK_001 = [
  "你打开了吃 APP，卡了 10 秒。",
  "吃的最高境界：不用手机。",
  "吃的教程看了 100 个，还是不会。",
  "吃的教程看了 100 个，还是不会。",
  "你被吃骗了，损失了 1 块钱。",
  "你打开了吃 APP，卡了 10 秒。",
  "你问我吃怎么样？我觉得一般，不如玩手机。",
  "吃结束了，你觉得浪费时间，但是很快乐。",
  "吃结束了，你觉得浪费时间，但是很快乐。",
  "你问百度吃怎么办，百度推荐了你看手机。",
  "你花了 100 块钱吃，结果什么也没得到。",
  "吃的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度吃怎么办，百度推荐了你看手机。",
  "吃排行榜前 10 名，你一个都不认识。",
  "你搜索吃，出来了 10000 条结果，你一条也没看。",
  "你搜索吃，出来了 10000 条结果，你一条也没看。",
  "你刷到了吃的短视频，刷了 1 小时。",
  "你搜索吃，出来了 10000 条结果，你一条也没看。",
  "你搜索吃，出来了 10000 条结果，你一条也没看。",
  "吃的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "吃的时候，手机突然响了，吓你一跳。",
  "你问我吃怎么样？我觉得一般，不如玩手机。",
  "你关于吃的想法？我觉得吃比骁龙450 还卡。",
  "吃结束了，你觉得浪费时间，但是很快乐。",
  "建议：吃的时候别玩手机，会爆炸。",
];

const REPLY_BULK_002 = [
  "你打开了睡 APP，卡了 10 秒。",
  "你收藏了 100 个睡视频，再也没打开过。",
  "你打开了睡 APP，卡了 10 秒。",
  "睡的时候，手机突然响了，吓你一跳。",
  "你关于睡的想法？我觉得睡比骁龙450 还卡。",
  "睡的正确姿势：放下手机。",
  "你刷到了睡的短视频，刷了 1 小时。",
  "睡的正确姿势：放下手机。",
  "睡的最高境界：不用手机。",
  "睡排行榜第一名：你。倒数第一名：骁龙450。",
  "睡专家来了，说你做的不对。",
  "睡的时候，你想起了手机。",
  "你发誓再也不睡了，明天又开始。",
  "你发誓再也不睡了，明天又开始。",
  "睡专家来了，说你做的不对。",
  "睡排行榜前 10 名，你一个都不认识。",
  "睡的教程看了 100 个，还是不会。",
  "你被睡骗了，损失了 1 块钱。",
  "建议：睡的时候别玩手机，会爆炸。",
  "睡排行榜前 10 名，你一个都不认识。",
  "睡的最高境界：不用手机。",
  "建议：睡的时候别玩手机，会爆炸。",
  "你问百度睡怎么办，百度推荐了你看手机。",
  "你问百度睡怎么办，百度推荐了你看手机。",
  "你收藏了 100 个睡视频，再也没打开过。",
];

const REPLY_BULK_003 = [
  "你收藏了 100 个钱视频，再也没打开过。",
  "钱的时候，手机突然响了，吓你一跳。",
  "钱真有意思，但是手机更有意思。",
  "你被钱骗了，损失了 1 块钱。",
  "你钱的时候，手机电量从 80% 掉到 20%。",
  "你钱的时候，手机电量从 80% 掉到 20%。",
  "钱的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个钱视频，再也没打开过。",
  "你关于钱的想法？我觉得钱比骁龙450 还卡。",
  "你钱的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不钱了，明天又开始。",
  "你发誓再也不钱了，明天又开始。",
  "钱的时候，手机突然响了，吓你一跳。",
  "你花了 100 块钱钱，结果什么也没得到。",
  "建议：钱的时候别玩手机，会爆炸。",
  "钱专家来了，说你做的不对。",
  "钱的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度钱怎么办，百度推荐了你看手机。",
  "你刷到了钱的短视频，刷了 1 小时。",
  "你打开了钱 APP，卡了 10 秒。",
  "你花了 100 块钱钱，结果什么也没得到。",
  "钱的教程看了 100 个，还是不会。",
  "你搜索钱，出来了 10000 条结果，你一条也没看。",
  "钱结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了钱的短视频，刷了 1 小时。",
];

const REPLY_BULK_004 = [
  "恋爱专家来了，说你做的不对。",
  "恋爱的教程看了 100 个，还是不会。",
  "恋爱的时候，你想起了手机。",
  "你花了 100 块钱恋爱，结果什么也没得到。",
  "恋爱的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你刷到了恋爱的短视频，刷了 1 小时。",
  "恋爱的教程看了 100 个，还是不会。",
  "恋爱的教程看了 100 个，还是不会。",
  "你关于恋爱的想法？我觉得恋爱比骁龙450 还卡。",
  "恋爱的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问我恋爱怎么样？我觉得一般，不如玩手机。",
  "你搜索恋爱，出来了 10000 条结果，你一条也没看。",
  "恋爱真有意思，但是手机更有意思。",
  "今天你恋爱了吗？没有，手机也没恋爱。",
  "你恋爱的时候，手机电量从 80% 掉到 20%。",
  "恋爱的教程看了 100 个，还是不会。",
  "恋爱的正确姿势：放下手机。",
  "你打开了恋爱 APP，卡了 10 秒。",
  "你恋爱的时候，手机电量从 80% 掉到 20%。",
  "恋爱结束了，你觉得浪费时间，但是很快乐。",
  "你花了 100 块钱恋爱，结果什么也没得到。",
  "你刷到了恋爱的短视频，刷了 1 小时。",
  "恋爱真有意思，但是手机更有意思。",
  "你刷到了恋爱的短视频，刷了 1 小时。",
  "你问我恋爱怎么样？我觉得一般，不如玩手机。",
];

const REPLY_BULK_005 = [
  "你打开了天气 APP，卡了 10 秒。",
  "你被天气骗了，损失了 1 块钱。",
  "你天气的时候，手机电量从 80% 掉到 20%。",
  "天气的时候，手机突然响了，吓你一跳。",
  "天气的正确姿势：放下手机。",
  "你刷到了天气的短视频，刷了 1 小时。",
  "你天气的时候，手机电量从 80% 掉到 20%。",
  "你问百度天气怎么办，百度推荐了你看手机。",
  "天气的时候，你想起了手机。",
  "你问百度天气怎么办，百度推荐了你看手机。",
  "天气专家来了，说你做的不对。",
  "天气的正确姿势：放下手机。",
  "你收藏了 100 个天气视频，再也没打开过。",
  "你问百度天气怎么办，百度推荐了你看手机。",
  "你被天气骗了，损失了 1 块钱。",
  "天气的教程看了 100 个，还是不会。",
  "你天气的时候，手机电量从 80% 掉到 20%。",
  "你刷到了天气的短视频，刷了 1 小时。",
  "天气专家来了，说你做的不对。",
  "你花了 100 块钱天气，结果什么也没得到。",
  "天气排行榜第一名：你。倒数第一名：骁龙450。",
  "你收藏了 100 个天气视频，再也没打开过。",
  "天气的时候，你想起了手机。",
  "你关于天气的想法？我觉得天气比骁龙450 还卡。",
  "今天你天气了吗？没有，手机也没天气。",
];

const REPLY_BULK_006 = [
  "上班真有意思，但是手机更有意思。",
  "你被上班骗了，损失了 1 块钱。",
  "上班结束了，你觉得浪费时间，但是很快乐。",
  "上班的时候，手机突然响了，吓你一跳。",
  "上班的教程看了 100 个，还是不会。",
  "你刷到了上班的短视频，刷了 1 小时。",
  "你发誓再也不上班了，明天又开始。",
  "上班排行榜第一名：你。倒数第一名：骁龙450。",
  "上班的时候，你想起了手机。",
  "你上班的时候，手机电量从 80% 掉到 20%。",
  "你刷到了上班的短视频，刷了 1 小时。",
  "上班的时候，手机突然响了，吓你一跳。",
  "上班的教程看了 100 个，还是不会。",
  "你搜索上班，出来了 10000 条结果，你一条也没看。",
  "你刷到了上班的短视频，刷了 1 小时。",
  "你花了 100 块钱上班，结果什么也没得到。",
  "你问百度上班怎么办，百度推荐了你看手机。",
  "上班的正确姿势：放下手机。",
  "今天你上班了吗？没有，手机也没上班。",
  "你收藏了 100 个上班视频，再也没打开过。",
  "上班的最高境界：不用手机。",
  "上班的时候，手机突然响了，吓你一跳。",
  "你打开了上班 APP，卡了 10 秒。",
  "上班的时候，手机突然响了，吓你一跳。",
  "你上班的时候，手机电量从 80% 掉到 20%。",
];

const REPLY_BULK_007 = [
  "你学习的时候，手机电量从 80% 掉到 20%。",
  "学习的教程看了 100 个，还是不会。",
  "学习的时候，你想起了手机。",
  "学习的时候，手机突然响了，吓你一跳。",
  "你学习了 3 小时，手机也烫了 3 小时。",
  "你花了 100 块钱学习，结果什么也没得到。",
  "学习排行榜前 10 名，你一个都不认识。",
  "你刷到了学习的短视频，刷了 1 小时。",
  "建议：学习的时候别玩手机，会爆炸。",
  "你被学习骗了，损失了 1 块钱。",
  "学习的时候，你想起了手机。",
  "你刷到了学习的短视频，刷了 1 小时。",
  "你发誓再也不学习了，明天又开始。",
  "你打开了学习 APP，卡了 10 秒。",
  "学习排行榜第一名：你。倒数第一名：骁龙450。",
  "学习排行榜前 10 名，你一个都不认识。",
  "你花了 100 块钱学习，结果什么也没得到。",
  "学习真有意思，但是手机更有意思。",
  "学习的时候，手机突然响了，吓你一跳。",
  "你关于学习的想法？我觉得学习比骁龙450 还卡。",
  "建议：学习的时候别玩手机，会爆炸。",
  "你关于学习的想法？我觉得学习比骁龙450 还卡。",
  "学习的时候，手机突然响了，吓你一跳。",
  "学习的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度学习怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_008 = [
  "建议：健身的时候别玩手机，会爆炸。",
  "健身结束了，你觉得浪费时间，但是很快乐。",
  "健身排行榜第一名：你。倒数第一名：骁龙450。",
  "你问我健身怎么样？我觉得一般，不如玩手机。",
  "你打开了健身 APP，卡了 10 秒。",
  "健身结束了，你觉得浪费时间，但是很快乐。",
  "今天你健身了吗？没有，手机也没健身。",
  "你搜索健身，出来了 10000 条结果，你一条也没看。",
  "你问百度健身怎么办，百度推荐了你看手机。",
  "健身的时候，你想起了手机。",
  "健身的正确姿势：放下手机。",
  "你搜索健身，出来了 10000 条结果，你一条也没看。",
  "你被健身骗了，损失了 1 块钱。",
  "你发誓再也不健身了，明天又开始。",
  "健身真有意思，但是手机更有意思。",
  "你关于健身的想法？我觉得健身比骁龙450 还卡。",
  "健身的最高境界：不用手机。",
  "健身的正确姿势：放下手机。",
  "健身的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "健身的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你搜索健身，出来了 10000 条结果，你一条也没看。",
  "你刷到了健身的短视频，刷了 1 小时。",
  "你健身的时候，手机电量从 80% 掉到 20%。",
  "健身排行榜前 10 名，你一个都不认识。",
  "健身真有意思，但是手机更有意思。",
];

const REPLY_BULK_009 = [
  "你问百度旅行怎么办，百度推荐了你看手机。",
  "你问我旅行怎么样？我觉得一般，不如玩手机。",
  "你刷到了旅行的短视频，刷了 1 小时。",
  "旅行的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "旅行真有意思，但是手机更有意思。",
  "旅行结束了，你觉得浪费时间，但是很快乐。",
  "你旅行的时候，手机电量从 80% 掉到 20%。",
  "旅行的教程看了 100 个，还是不会。",
  "你收藏了 100 个旅行视频，再也没打开过。",
  "建议：旅行的时候别玩手机，会爆炸。",
  "你花了 100 块钱旅行，结果什么也没得到。",
  "旅行的正确姿势：放下手机。",
  "你旅行了 3 小时，手机也烫了 3 小时。",
  "旅行真有意思，但是手机更有意思。",
  "旅行的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个旅行视频，再也没打开过。",
  "旅行的教程看了 100 个，还是不会。",
  "你花了 100 块钱旅行，结果什么也没得到。",
  "旅行专家来了，说你做的不对。",
  "旅行真有意思，但是手机更有意思。",
  "旅行的教程看了 100 个，还是不会。",
  "旅行排行榜第一名：你。倒数第一名：骁龙450。",
  "旅行专家来了，说你做的不对。",
  "你关于旅行的想法？我觉得旅行比骁龙450 还卡。",
  "你打开了旅行 APP，卡了 10 秒。",
];

const REPLY_BULK_010 = [
  "电影专家来了，说你做的不对。",
  "建议：电影的时候别玩手机，会爆炸。",
  "今天你电影了吗？没有，手机也没电影。",
  "你发誓再也不电影了，明天又开始。",
  "你被电影骗了，损失了 1 块钱。",
  "你发誓再也不电影了，明天又开始。",
  "你搜索电影，出来了 10000 条结果，你一条也没看。",
  "你关于电影的想法？我觉得电影比骁龙450 还卡。",
  "你关于电影的想法？我觉得电影比骁龙450 还卡。",
  "电影的教程看了 100 个，还是不会。",
  "你刷到了电影的短视频，刷了 1 小时。",
  "电影的最高境界：不用手机。",
  "电影的正确姿势：放下手机。",
  "你收藏了 100 个电影视频，再也没打开过。",
  "电影的时候，手机突然响了，吓你一跳。",
  "电影的最高境界：不用手机。",
  "你打开了电影 APP，卡了 10 秒。",
  "你刷到了电影的短视频，刷了 1 小时。",
  "电影的时候，手机突然响了，吓你一跳。",
  "电影的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "电影结束了，你觉得浪费时间，但是很快乐。",
  "你电影了 3 小时，手机也烫了 3 小时。",
  "电影真有意思，但是手机更有意思。",
  "电影的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "电影的教程看了 100 个，还是不会。",
];

const REPLY_BULK_011 = [
  "游戏排行榜第一名：你。倒数第一名：骁龙450。",
  "你花了 100 块钱游戏，结果什么也没得到。",
  "游戏结束了，你觉得浪费时间，但是很快乐。",
  "游戏的最高境界：不用手机。",
  "游戏的时候，手机突然响了，吓你一跳。",
  "游戏结束了，你觉得浪费时间，但是很快乐。",
  "你问我游戏怎么样？我觉得一般，不如玩手机。",
  "游戏的正确姿势：放下手机。",
  "你游戏的时候，手机电量从 80% 掉到 20%。",
  "建议：游戏的时候别玩手机，会爆炸。",
  "你问百度游戏怎么办，百度推荐了你看手机。",
  "游戏专家来了，说你做的不对。",
  "今天你游戏了吗？没有，手机也没游戏。",
  "游戏排行榜第一名：你。倒数第一名：骁龙450。",
  "你被游戏骗了，损失了 1 块钱。",
  "你游戏了 3 小时，手机也烫了 3 小时。",
  "今天你游戏了吗？没有，手机也没游戏。",
  "你被游戏骗了，损失了 1 块钱。",
  "你问百度游戏怎么办，百度推荐了你看手机。",
  "今天你游戏了吗？没有，手机也没游戏。",
  "游戏的时候，手机突然响了，吓你一跳。",
  "你搜索游戏，出来了 10000 条结果，你一条也没看。",
  "你被游戏骗了，损失了 1 块钱。",
  "游戏排行榜第一名：你。倒数第一名：骁龙450。",
  "你刷到了游戏的短视频，刷了 1 小时。",
];

const REPLY_BULK_012 = [
  "你手机的时候，手机电量从 80% 掉到 20%。",
  "手机的正确姿势：放下手机。",
  "你关于手机的想法？我觉得手机比骁龙450 还卡。",
  "手机真有意思，但是手机更有意思。",
  "你被手机骗了，损失了 1 块钱。",
  "手机的教程看了 100 个，还是不会。",
  "手机排行榜第一名：你。倒数第一名：骁龙450。",
  "手机的教程看了 100 个，还是不会。",
  "手机真有意思，但是手机更有意思。",
  "你手机了 3 小时，手机也烫了 3 小时。",
  "手机的正确姿势：放下手机。",
  "你手机了 3 小时，手机也烫了 3 小时。",
  "手机专家来了，说你做的不对。",
  "手机的时候，你想起了手机。",
  "你花了 100 块钱手机，结果什么也没得到。",
  "你问百度手机怎么办，百度推荐了你看手机。",
  "你花了 100 块钱手机，结果什么也没得到。",
  "建议：手机的时候别玩手机，会爆炸。",
  "手机专家来了，说你做的不对。",
  "你收藏了 100 个手机视频，再也没打开过。",
  "你手机了 3 小时，手机也烫了 3 小时。",
  "你发誓再也不手机了，明天又开始。",
  "你手机了 3 小时，手机也烫了 3 小时。",
  "手机的时候，你想起了手机。",
  "手机的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_013 = [
  "你刷到了电脑的短视频，刷了 1 小时。",
  "你搜索电脑，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱电脑，结果什么也没得到。",
  "你收藏了 100 个电脑视频，再也没打开过。",
  "电脑的时候，手机突然响了，吓你一跳。",
  "你电脑了 3 小时，手机也烫了 3 小时。",
  "电脑的最高境界：不用手机。",
  "电脑的教程看了 100 个，还是不会。",
  "你刷到了电脑的短视频，刷了 1 小时。",
  "电脑的时候，手机突然响了，吓你一跳。",
  "你打开了电脑 APP，卡了 10 秒。",
  "电脑的教程看了 100 个，还是不会。",
  "电脑的教程看了 100 个，还是不会。",
  "电脑的时候，你想起了手机。",
  "你打开了电脑 APP，卡了 10 秒。",
  "电脑排行榜第一名：你。倒数第一名：骁龙450。",
  "你问我电脑怎么样？我觉得一般，不如玩手机。",
  "你关于电脑的想法？我觉得电脑比骁龙450 还卡。",
  "建议：电脑的时候别玩手机，会爆炸。",
  "电脑的时候，手机突然响了，吓你一跳。",
  "你被电脑骗了，损失了 1 块钱。",
  "电脑的最高境界：不用手机。",
  "你花了 100 块钱电脑，结果什么也没得到。",
  "你问百度电脑怎么办，百度推荐了你看手机。",
  "电脑的正确姿势：放下手机。",
];

const REPLY_BULK_014 = [
  "你网络了 3 小时，手机也烫了 3 小时。",
  "你关于网络的想法？我觉得网络比骁龙450 还卡。",
  "你发誓再也不网络了，明天又开始。",
  "你网络了 3 小时，手机也烫了 3 小时。",
  "你发誓再也不网络了，明天又开始。",
  "你问百度网络怎么办，百度推荐了你看手机。",
  "网络的正确姿势：放下手机。",
  "网络的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度网络怎么办，百度推荐了你看手机。",
  "网络排行榜第一名：你。倒数第一名：骁龙450。",
  "你打开了网络 APP，卡了 10 秒。",
  "网络结束了，你觉得浪费时间，但是很快乐。",
  "你网络的时候，手机电量从 80% 掉到 20%。",
  "网络的时候，你想起了手机。",
  "你问百度网络怎么办，百度推荐了你看手机。",
  "你搜索网络，出来了 10000 条结果，你一条也没看。",
  "网络的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "网络排行榜前 10 名，你一个都不认识。",
  "网络排行榜第一名：你。倒数第一名：骁龙450。",
  "网络的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个网络视频，再也没打开过。",
  "网络的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "网络的时候，你想起了手机。",
  "网络的正确姿势：放下手机。",
  "你问百度网络怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_015 = [
  "外卖真有意思，但是手机更有意思。",
  "你打开了外卖 APP，卡了 10 秒。",
  "外卖的时候，你想起了手机。",
  "你打开了外卖 APP，卡了 10 秒。",
  "你花了 100 块钱外卖，结果什么也没得到。",
  "你外卖了 3 小时，手机也烫了 3 小时。",
  "你打开了外卖 APP，卡了 10 秒。",
  "外卖的正确姿势：放下手机。",
  "今天你外卖了吗？没有，手机也没外卖。",
  "你搜索外卖，出来了 10000 条结果，你一条也没看。",
  "你发誓再也不外卖了，明天又开始。",
  "外卖排行榜前 10 名，你一个都不认识。",
  "你外卖了 3 小时，手机也烫了 3 小时。",
  "你被外卖骗了，损失了 1 块钱。",
  "你被外卖骗了，损失了 1 块钱。",
  "你打开了外卖 APP，卡了 10 秒。",
  "外卖的教程看了 100 个，还是不会。",
  "外卖的最高境界：不用手机。",
  "外卖的时候，你想起了手机。",
  "外卖的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "建议：外卖的时候别玩手机，会爆炸。",
  "你收藏了 100 个外卖视频，再也没打开过。",
  "外卖的最高境界：不用手机。",
  "你外卖了 3 小时，手机也烫了 3 小时。",
  "外卖的时候，你想起了手机。",
];

const REPLY_BULK_016 = [
  "快递的时候，你想起了手机。",
  "建议：快递的时候别玩手机，会爆炸。",
  "你关于快递的想法？我觉得快递比骁龙450 还卡。",
  "你花了 100 块钱快递，结果什么也没得到。",
  "你搜索快递，出来了 10000 条结果，你一条也没看。",
  "快递的时候，你想起了手机。",
  "你花了 100 块钱快递，结果什么也没得到。",
  "你关于快递的想法？我觉得快递比骁龙450 还卡。",
  "今天你快递了吗？没有，手机也没快递。",
  "你打开了快递 APP，卡了 10 秒。",
  "你问我快递怎么样？我觉得一般，不如玩手机。",
  "你关于快递的想法？我觉得快递比骁龙450 还卡。",
  "你收藏了 100 个快递视频，再也没打开过。",
  "你打开了快递 APP，卡了 10 秒。",
  "你打开了快递 APP，卡了 10 秒。",
  "快递的正确姿势：放下手机。",
  "你问百度快递怎么办，百度推荐了你看手机。",
  "快递的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你发誓再也不快递了，明天又开始。",
  "快递的最高境界：不用手机。",
  "你搜索快递，出来了 10000 条结果，你一条也没看。",
  "快递的时候，手机突然响了，吓你一跳。",
  "快递结束了，你觉得浪费时间，但是很快乐。",
  "你被快递骗了，损失了 1 块钱。",
  "你被快递骗了，损失了 1 块钱。",
];

const REPLY_BULK_017 = [
  "你购物的时候，手机电量从 80% 掉到 20%。",
  "购物结束了，你觉得浪费时间，但是很快乐。",
  "今天你购物了吗？没有，手机也没购物。",
  "购物专家来了，说你做的不对。",
  "购物的最高境界：不用手机。",
  "购物结束了，你觉得浪费时间，但是很快乐。",
  "购物排行榜第一名：你。倒数第一名：骁龙450。",
  "购物结束了，你觉得浪费时间，但是很快乐。",
  "购物的时候，手机突然响了，吓你一跳。",
  "你花了 100 块钱购物，结果什么也没得到。",
  "购物的正确姿势：放下手机。",
  "你打开了购物 APP，卡了 10 秒。",
  "购物的正确姿势：放下手机。",
  "你发誓再也不购物了，明天又开始。",
  "购物的教程看了 100 个，还是不会。",
  "购物的正确姿势：放下手机。",
  "购物的时候，你想起了手机。",
  "购物专家来了，说你做的不对。",
  "你收藏了 100 个购物视频，再也没打开过。",
  "你发誓再也不购物了，明天又开始。",
  "今天你购物了吗？没有，手机也没购物。",
  "购物排行榜前 10 名，你一个都不认识。",
  "你购物的时候，手机电量从 80% 掉到 20%。",
  "你花了 100 块钱购物，结果什么也没得到。",
  "你关于购物的想法？我觉得购物比骁龙450 还卡。",
];

const REPLY_BULK_018 = [
  "你收藏了 100 个直播视频，再也没打开过。",
  "你直播的时候，手机电量从 80% 掉到 20%。",
  "直播的最高境界：不用手机。",
  "你收藏了 100 个直播视频，再也没打开过。",
  "直播排行榜前 10 名，你一个都不认识。",
  "你搜索直播，出来了 10000 条结果，你一条也没看。",
  "你打开了直播 APP，卡了 10 秒。",
  "你收藏了 100 个直播视频，再也没打开过。",
  "你搜索直播，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱直播，结果什么也没得到。",
  "直播的最高境界：不用手机。",
  "直播的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你关于直播的想法？我觉得直播比骁龙450 还卡。",
  "你问百度直播怎么办，百度推荐了你看手机。",
  "直播的最高境界：不用手机。",
  "直播排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度直播怎么办，百度推荐了你看手机。",
  "今天你直播了吗？没有，手机也没直播。",
  "直播排行榜前 10 名，你一个都不认识。",
  "你打开了直播 APP，卡了 10 秒。",
  "你直播了 3 小时，手机也烫了 3 小时。",
  "直播结束了，你觉得浪费时间，但是很快乐。",
  "你打开了直播 APP，卡了 10 秒。",
  "你打开了直播 APP，卡了 10 秒。",
  "今天你直播了吗？没有，手机也没直播。",
];

const REPLY_BULK_019 = [
  "短视频真有意思，但是手机更有意思。",
  "短视频的教程看了 100 个，还是不会。",
  "你发誓再也不短视频了，明天又开始。",
  "短视频结束了，你觉得浪费时间，但是很快乐。",
  "你被短视频骗了，损失了 1 块钱。",
  "你被短视频骗了，损失了 1 块钱。",
  "你收藏了 100 个短视频视频，再也没打开过。",
  "你关于短视频的想法？我觉得短视频比骁龙450 还卡。",
  "你花了 100 块钱短视频，结果什么也没得到。",
  "短视频的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "短视频真有意思，但是手机更有意思。",
  "你发誓再也不短视频了，明天又开始。",
  "你花了 100 块钱短视频，结果什么也没得到。",
  "短视频专家来了，说你做的不对。",
  "短视频专家来了，说你做的不对。",
  "你问我短视频怎么样？我觉得一般，不如玩手机。",
  "你搜索短视频，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱短视频，结果什么也没得到。",
  "短视频的正确姿势：放下手机。",
  "你问我短视频怎么样？我觉得一般，不如玩手机。",
  "你搜索短视频，出来了 10000 条结果，你一条也没看。",
  "短视频真有意思，但是手机更有意思。",
  "你短视频了 3 小时，手机也烫了 3 小时。",
  "你问百度短视频怎么办，百度推荐了你看手机。",
  "你关于短视频的想法？我觉得短视频比骁龙450 还卡。",
];

const REPLY_BULK_020 = [
  "小说的正确姿势：放下手机。",
  "你小说的时候，手机电量从 80% 掉到 20%。",
  "你问百度小说怎么办，百度推荐了你看手机。",
  "小说的正确姿势：放下手机。",
  "你问百度小说怎么办，百度推荐了你看手机。",
  "小说专家来了，说你做的不对。",
  "小说的时候，你想起了手机。",
  "小说真有意思，但是手机更有意思。",
  "你问我小说怎么样？我觉得一般，不如玩手机。",
  "你关于小说的想法？我觉得小说比骁龙450 还卡。",
  "你关于小说的想法？我觉得小说比骁龙450 还卡。",
  "小说的时候，你想起了手机。",
  "你问百度小说怎么办，百度推荐了你看手机。",
  "你刷到了小说的短视频，刷了 1 小时。",
  "你花了 100 块钱小说，结果什么也没得到。",
  "小说的时候，你想起了手机。",
  "小说的最高境界：不用手机。",
  "小说真有意思，但是手机更有意思。",
  "你被小说骗了，损失了 1 块钱。",
  "小说的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "建议：小说的时候别玩手机，会爆炸。",
  "你小说了 3 小时，手机也烫了 3 小时。",
  "你问百度小说怎么办，百度推荐了你看手机。",
  "今天你小说了吗？没有，手机也没小说。",
  "你被小说骗了，损失了 1 块钱。",
];

const REPLY_BULK_021 = [
  "音乐的教程看了 100 个，还是不会。",
  "音乐的时候，你想起了手机。",
  "音乐的最高境界：不用手机。",
  "你被音乐骗了，损失了 1 块钱。",
  "音乐的教程看了 100 个，还是不会。",
  "你搜索音乐，出来了 10000 条结果，你一条也没看。",
  "音乐排行榜前 10 名，你一个都不认识。",
  "音乐的最高境界：不用手机。",
  "今天你音乐了吗？没有，手机也没音乐。",
  "音乐的正确姿势：放下手机。",
  "你关于音乐的想法？我觉得音乐比骁龙450 还卡。",
  "你被音乐骗了，损失了 1 块钱。",
  "你问我音乐怎么样？我觉得一般，不如玩手机。",
  "你刷到了音乐的短视频，刷了 1 小时。",
  "今天你音乐了吗？没有，手机也没音乐。",
  "你问我音乐怎么样？我觉得一般，不如玩手机。",
  "音乐的正确姿势：放下手机。",
  "音乐的教程看了 100 个，还是不会。",
  "音乐真有意思，但是手机更有意思。",
  "音乐排行榜前 10 名，你一个都不认识。",
  "音乐专家来了，说你做的不对。",
  "你音乐的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不音乐了，明天又开始。",
  "你问我音乐怎么样？我觉得一般，不如玩手机。",
  "你问百度音乐怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_022 = [
  "拍照的时候，你想起了手机。",
  "拍照的最高境界：不用手机。",
  "拍照排行榜第一名：你。倒数第一名：骁龙450。",
  "你发誓再也不拍照了，明天又开始。",
  "你发誓再也不拍照了，明天又开始。",
  "拍照的时候，手机突然响了，吓你一跳。",
  "你被拍照骗了，损失了 1 块钱。",
  "拍照的时候，手机突然响了，吓你一跳。",
  "你问百度拍照怎么办，百度推荐了你看手机。",
  "你刷到了拍照的短视频，刷了 1 小时。",
  "拍照的正确姿势：放下手机。",
  "拍照的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个拍照视频，再也没打开过。",
  "拍照排行榜第一名：你。倒数第一名：骁龙450。",
  "你拍照了 3 小时，手机也烫了 3 小时。",
  "你被拍照骗了，损失了 1 块钱。",
  "你花了 100 块钱拍照，结果什么也没得到。",
  "拍照真有意思，但是手机更有意思。",
  "你刷到了拍照的短视频，刷了 1 小时。",
  "你关于拍照的想法？我觉得拍照比骁龙450 还卡。",
  "你发誓再也不拍照了，明天又开始。",
  "拍照的教程看了 100 个，还是不会。",
  "你拍照的时候，手机电量从 80% 掉到 20%。",
  "你花了 100 块钱拍照，结果什么也没得到。",
  "今天你拍照了吗？没有，手机也没拍照。",
];

const REPLY_BULK_023 = [
  "你被视频骗了，损失了 1 块钱。",
  "你视频了 3 小时，手机也烫了 3 小时。",
  "建议：视频的时候别玩手机，会爆炸。",
  "你收藏了 100 个视频视频，再也没打开过。",
  "你发誓再也不视频了，明天又开始。",
  "你问百度视频怎么办，百度推荐了你看手机。",
  "视频排行榜前 10 名，你一个都不认识。",
  "视频的时候，你想起了手机。",
  "视频真有意思，但是手机更有意思。",
  "你视频的时候，手机电量从 80% 掉到 20%。",
  "视频排行榜前 10 名，你一个都不认识。",
  "你打开了视频 APP，卡了 10 秒。",
  "你关于视频的想法？我觉得视频比骁龙450 还卡。",
  "你问百度视频怎么办，百度推荐了你看手机。",
  "视频排行榜第一名：你。倒数第一名：骁龙450。",
  "你视频的时候，手机电量从 80% 掉到 20%。",
  "视频的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个视频视频，再也没打开过。",
  "视频的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你视频了吗？没有，手机也没视频。",
  "视频专家来了，说你做的不对。",
  "视频专家来了，说你做的不对。",
  "你问百度视频怎么办，百度推荐了你看手机。",
  "视频的教程看了 100 个，还是不会。",
  "你被视频骗了，损失了 1 块钱。",
];

const REPLY_BULK_024 = [
  "电话的正确姿势：放下手机。",
  "你电话了 3 小时，手机也烫了 3 小时。",
  "电话的教程看了 100 个，还是不会。",
  "你打开了电话 APP，卡了 10 秒。",
  "建议：电话的时候别玩手机，会爆炸。",
  "电话真有意思，但是手机更有意思。",
  "电话排行榜前 10 名，你一个都不认识。",
  "电话专家来了，说你做的不对。",
  "电话的最高境界：不用手机。",
  "你问百度电话怎么办，百度推荐了你看手机。",
  "电话的时候，你想起了手机。",
  "你收藏了 100 个电话视频，再也没打开过。",
  "今天你电话了吗？没有，手机也没电话。",
  "电话排行榜前 10 名，你一个都不认识。",
  "电话的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "电话的正确姿势：放下手机。",
  "电话排行榜第一名：你。倒数第一名：骁龙450。",
  "你电话了 3 小时，手机也烫了 3 小时。",
  "你收藏了 100 个电话视频，再也没打开过。",
  "你收藏了 100 个电话视频，再也没打开过。",
  "你问百度电话怎么办，百度推荐了你看手机。",
  "你收藏了 100 个电话视频，再也没打开过。",
  "你发誓再也不电话了，明天又开始。",
  "电话真有意思，但是手机更有意思。",
  "电话专家来了，说你做的不对。",
];

const REPLY_BULK_025 = [
  "微信排行榜第一名：你。倒数第一名：骁龙450。",
  "微信排行榜前 10 名，你一个都不认识。",
  "你被微信骗了，损失了 1 块钱。",
  "你关于微信的想法？我觉得微信比骁龙450 还卡。",
  "微信结束了，你觉得浪费时间，但是很快乐。",
  "你被微信骗了，损失了 1 块钱。",
  "你刷到了微信的短视频，刷了 1 小时。",
  "你花了 100 块钱微信，结果什么也没得到。",
  "你发誓再也不微信了，明天又开始。",
  "你搜索微信，出来了 10000 条结果，你一条也没看。",
  "你搜索微信，出来了 10000 条结果，你一条也没看。",
  "你问百度微信怎么办，百度推荐了你看手机。",
  "你微信了 3 小时，手机也烫了 3 小时。",
  "微信排行榜前 10 名，你一个都不认识。",
  "微信的教程看了 100 个，还是不会。",
  "你关于微信的想法？我觉得微信比骁龙450 还卡。",
  "你微信了 3 小时，手机也烫了 3 小时。",
  "微信的最高境界：不用手机。",
  "你问百度微信怎么办，百度推荐了你看手机。",
  "微信真有意思，但是手机更有意思。",
  "你微信了 3 小时，手机也烫了 3 小时。",
  "你关于微信的想法？我觉得微信比骁龙450 还卡。",
  "你打开了微信 APP，卡了 10 秒。",
  "微信的教程看了 100 个，还是不会。",
  "微信的正确姿势：放下手机。",
];

const REPLY_BULK_026 = [
  "你朋友圈的时候，手机电量从 80% 掉到 20%。",
  "你被朋友圈骗了，损失了 1 块钱。",
  "你搜索朋友圈，出来了 10000 条结果，你一条也没看。",
  "你关于朋友圈的想法？我觉得朋友圈比骁龙450 还卡。",
  "你发誓再也不朋友圈了，明天又开始。",
  "建议：朋友圈的时候别玩手机，会爆炸。",
  "你发誓再也不朋友圈了，明天又开始。",
  "你收藏了 100 个朋友圈视频，再也没打开过。",
  "朋友圈排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度朋友圈怎么办，百度推荐了你看手机。",
  "朋友圈真有意思，但是手机更有意思。",
  "朋友圈结束了，你觉得浪费时间，但是很快乐。",
  "朋友圈结束了，你觉得浪费时间，但是很快乐。",
  "你问我朋友圈怎么样？我觉得一般，不如玩手机。",
  "朋友圈真有意思，但是手机更有意思。",
  "你打开了朋友圈 APP，卡了 10 秒。",
  "朋友圈的最高境界：不用手机。",
  "你刷到了朋友圈的短视频，刷了 1 小时。",
  "你打开了朋友圈 APP，卡了 10 秒。",
  "朋友圈排行榜前 10 名，你一个都不认识。",
  "建议：朋友圈的时候别玩手机，会爆炸。",
  "朋友圈专家来了，说你做的不对。",
  "朋友圈的时候，你想起了手机。",
  "朋友圈结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个朋友圈视频，再也没打开过。",
];

const REPLY_BULK_027 = [
  "你被抖音骗了，损失了 1 块钱。",
  "你打开了抖音 APP，卡了 10 秒。",
  "你发誓再也不抖音了，明天又开始。",
  "你刷到了抖音的短视频，刷了 1 小时。",
  "你刷到了抖音的短视频，刷了 1 小时。",
  "你打开了抖音 APP，卡了 10 秒。",
  "你问百度抖音怎么办，百度推荐了你看手机。",
  "抖音的教程看了 100 个，还是不会。",
  "你问我抖音怎么样？我觉得一般，不如玩手机。",
  "你发誓再也不抖音了，明天又开始。",
  "抖音的正确姿势：放下手机。",
  "抖音的时候，手机突然响了，吓你一跳。",
  "抖音的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你发誓再也不抖音了，明天又开始。",
  "建议：抖音的时候别玩手机，会爆炸。",
  "建议：抖音的时候别玩手机，会爆炸。",
  "你搜索抖音，出来了 10000 条结果，你一条也没看。",
  "建议：抖音的时候别玩手机，会爆炸。",
  "你刷到了抖音的短视频，刷了 1 小时。",
  "你搜索抖音，出来了 10000 条结果，你一条也没看。",
  "你收藏了 100 个抖音视频，再也没打开过。",
  "抖音的时候，你想起了手机。",
  "你搜索抖音，出来了 10000 条结果，你一条也没看。",
  "抖音的正确姿势：放下手机。",
  "你问我抖音怎么样？我觉得一般，不如玩手机。",
];

const REPLY_BULK_028 = [
  "你B站了 3 小时，手机也烫了 3 小时。",
  "B站的最高境界：不用手机。",
  "你花了 100 块钱B站，结果什么也没得到。",
  "B站的教程看了 100 个，还是不会。",
  "你问百度B站怎么办，百度推荐了你看手机。",
  "B站的最高境界：不用手机。",
  "B站的最高境界：不用手机。",
  "B站排行榜前 10 名，你一个都不认识。",
  "B站的正确姿势：放下手机。",
  "你刷到了B站的短视频，刷了 1 小时。",
  "B站专家来了，说你做的不对。",
  "B站的最高境界：不用手机。",
  "你B站了 3 小时，手机也烫了 3 小时。",
  "B站排行榜第一名：你。倒数第一名：骁龙450。",
  "B站的时候，手机突然响了，吓你一跳。",
  "你问我B站怎么样？我觉得一般，不如玩手机。",
  "你B站的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不B站了，明天又开始。",
  "你搜索B站，出来了 10000 条结果，你一条也没看。",
  "你发誓再也不B站了，明天又开始。",
  "你花了 100 块钱B站，结果什么也没得到。",
  "B站的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "B站专家来了，说你做的不对。",
  "B站排行榜第一名：你。倒数第一名：骁龙450。",
  "B站真有意思，但是手机更有意思。",
];

const REPLY_BULK_029 = [
  "淘宝的时候，手机突然响了，吓你一跳。",
  "淘宝排行榜前 10 名，你一个都不认识。",
  "淘宝的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "淘宝的正确姿势：放下手机。",
  "淘宝排行榜前 10 名，你一个都不认识。",
  "淘宝真有意思，但是手机更有意思。",
  "你花了 100 块钱淘宝，结果什么也没得到。",
  "淘宝的时候，你想起了手机。",
  "淘宝的最高境界：不用手机。",
  "你打开了淘宝 APP，卡了 10 秒。",
  "淘宝的最高境界：不用手机。",
  "淘宝的时候，你想起了手机。",
  "淘宝的时候，手机突然响了，吓你一跳。",
  "淘宝的时候，你想起了手机。",
  "淘宝真有意思，但是手机更有意思。",
  "你问百度淘宝怎么办，百度推荐了你看手机。",
  "你被淘宝骗了，损失了 1 块钱。",
  "淘宝的时候，你想起了手机。",
  "你问我淘宝怎么样？我觉得一般，不如玩手机。",
  "淘宝的最高境界：不用手机。",
  "淘宝真有意思，但是手机更有意思。",
  "你问百度淘宝怎么办，百度推荐了你看手机。",
  "你搜索淘宝，出来了 10000 条结果，你一条也没看。",
  "你打开了淘宝 APP，卡了 10 秒。",
  "淘宝的时候，你想起了手机。",
];

const REPLY_BULK_030 = [
  "你收藏了 100 个京东视频，再也没打开过。",
  "京东的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "京东的时候，手机突然响了，吓你一跳。",
  "你被京东骗了，损失了 1 块钱。",
  "京东专家来了，说你做的不对。",
  "京东专家来了，说你做的不对。",
  "你关于京东的想法？我觉得京东比骁龙450 还卡。",
  "你问百度京东怎么办，百度推荐了你看手机。",
  "你京东的时候，手机电量从 80% 掉到 20%。",
  "京东的最高境界：不用手机。",
  "京东的正确姿势：放下手机。",
  "你花了 100 块钱京东，结果什么也没得到。",
  "京东的最高境界：不用手机。",
  "你打开了京东 APP，卡了 10 秒。",
  "京东的正确姿势：放下手机。",
  "你搜索京东，出来了 10000 条结果，你一条也没看。",
  "你刷到了京东的短视频，刷了 1 小时。",
  "京东的正确姿势：放下手机。",
  "你被京东骗了，损失了 1 块钱。",
  "京东的正确姿势：放下手机。",
  "你搜索京东，出来了 10000 条结果，你一条也没看。",
  "你问百度京东怎么办，百度推荐了你看手机。",
  "京东的教程看了 100 个，还是不会。",
  "京东排行榜第一名：你。倒数第一名：骁龙450。",
  "你花了 100 块钱京东，结果什么也没得到。",
];

const REPLY_BULK_031 = [
  "你发誓再也不拼多多了，明天又开始。",
  "你被拼多多骗了，损失了 1 块钱。",
  "拼多多的最高境界：不用手机。",
  "今天你拼多多了吗？没有，手机也没拼多多。",
  "拼多多专家来了，说你做的不对。",
  "拼多多排行榜前 10 名，你一个都不认识。",
  "你拼多多了 3 小时，手机也烫了 3 小时。",
  "你关于拼多多的想法？我觉得拼多多比骁龙450 还卡。",
  "拼多多的时候，你想起了手机。",
  "你问百度拼多多怎么办，百度推荐了你看手机。",
  "你拼多多的时候，手机电量从 80% 掉到 20%。",
  "拼多多的时候，你想起了手机。",
  "拼多多真有意思，但是手机更有意思。",
  "拼多多的最高境界：不用手机。",
  "拼多多的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你被拼多多骗了，损失了 1 块钱。",
  "拼多多结束了，你觉得浪费时间，但是很快乐。",
  "你花了 100 块钱拼多多，结果什么也没得到。",
  "你搜索拼多多，出来了 10000 条结果，你一条也没看。",
  "你刷到了拼多多的短视频，刷了 1 小时。",
  "你刷到了拼多多的短视频，刷了 1 小时。",
  "拼多多的最高境界：不用手机。",
  "你关于拼多多的想法？我觉得拼多多比骁龙450 还卡。",
  "今天你拼多多了吗？没有，手机也没拼多多。",
  "你搜索拼多多，出来了 10000 条结果，你一条也没看。",
];

const REPLY_BULK_032 = [
  "你问我饿了么怎么样？我觉得一般，不如玩手机。",
  "你被饿了么骗了，损失了 1 块钱。",
  "你打开了饿了么 APP，卡了 10 秒。",
  "饿了么的正确姿势：放下手机。",
  "饿了么的时候，你想起了手机。",
  "饿了么的最高境界：不用手机。",
  "你关于饿了么的想法？我觉得饿了么比骁龙450 还卡。",
  "你搜索饿了么，出来了 10000 条结果，你一条也没看。",
  "饿了么排行榜第一名：你。倒数第一名：骁龙450。",
  "饿了么的时候，手机突然响了，吓你一跳。",
  "饿了么的教程看了 100 个，还是不会。",
  "饿了么的时候，你想起了手机。",
  "饿了么结束了，你觉得浪费时间，但是很快乐。",
  "你被饿了么骗了，损失了 1 块钱。",
  "你发誓再也不饿了么了，明天又开始。",
  "建议：饿了么的时候别玩手机，会爆炸。",
  "你问百度饿了么怎么办，百度推荐了你看手机。",
  "你饿了么的时候，手机电量从 80% 掉到 20%。",
  "饿了么排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度饿了么怎么办，百度推荐了你看手机。",
  "你搜索饿了么，出来了 10000 条结果，你一条也没看。",
  "你关于饿了么的想法？我觉得饿了么比骁龙450 还卡。",
  "你打开了饿了么 APP，卡了 10 秒。",
  "饿了么真有意思，但是手机更有意思。",
  "饿了么的最高境界：不用手机。",
];

const REPLY_BULK_033 = [
  "你问我美团怎么样？我觉得一般，不如玩手机。",
  "美团的时候，手机突然响了，吓你一跳。",
  "美团排行榜第一名：你。倒数第一名：骁龙450。",
  "美团结束了，你觉得浪费时间，但是很快乐。",
  "美团的正确姿势：放下手机。",
  "你美团了 3 小时，手机也烫了 3 小时。",
  "你美团的时候，手机电量从 80% 掉到 20%。",
  "你收藏了 100 个美团视频，再也没打开过。",
  "建议：美团的时候别玩手机，会爆炸。",
  "美团的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你花了 100 块钱美团，结果什么也没得到。",
  "你美团的时候，手机电量从 80% 掉到 20%。",
  "美团的教程看了 100 个，还是不会。",
  "美团的正确姿势：放下手机。",
  "美团的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度美团怎么办，百度推荐了你看手机。",
  "美团真有意思，但是手机更有意思。",
  "你打开了美团 APP，卡了 10 秒。",
  "你关于美团的想法？我觉得美团比骁龙450 还卡。",
  "美团的时候，你想起了手机。",
  "你花了 100 块钱美团，结果什么也没得到。",
  "今天你美团了吗？没有，手机也没美团。",
  "你美团了 3 小时，手机也烫了 3 小时。",
  "你问百度美团怎么办，百度推荐了你看手机。",
  "美团排行榜前 10 名，你一个都不认识。",
];

const REPLY_BULK_034 = [
  "滴滴的教程看了 100 个，还是不会。",
  "你问我滴滴怎么样？我觉得一般，不如玩手机。",
  "你刷到了滴滴的短视频，刷了 1 小时。",
  "滴滴的正确姿势：放下手机。",
  "滴滴的正确姿势：放下手机。",
  "滴滴的最高境界：不用手机。",
  "滴滴的最高境界：不用手机。",
  "你发誓再也不滴滴了，明天又开始。",
  "滴滴的最高境界：不用手机。",
  "滴滴结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了滴滴的短视频，刷了 1 小时。",
  "滴滴的时候，你想起了手机。",
  "你刷到了滴滴的短视频，刷了 1 小时。",
  "滴滴的最高境界：不用手机。",
  "滴滴的时候，你想起了手机。",
  "今天你滴滴了吗？没有，手机也没滴滴。",
  "你被滴滴骗了，损失了 1 块钱。",
  "你刷到了滴滴的短视频，刷了 1 小时。",
  "滴滴真有意思，但是手机更有意思。",
  "你关于滴滴的想法？我觉得滴滴比骁龙450 还卡。",
  "你刷到了滴滴的短视频，刷了 1 小时。",
  "你发誓再也不滴滴了，明天又开始。",
  "滴滴的时候，你想起了手机。",
  "你搜索滴滴，出来了 10000 条结果，你一条也没看。",
  "滴滴的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_035 = [
  "高铁排行榜第一名：你。倒数第一名：骁龙450。",
  "你发誓再也不高铁了，明天又开始。",
  "高铁的时候，你想起了手机。",
  "高铁的教程看了 100 个，还是不会。",
  "高铁排行榜前 10 名，你一个都不认识。",
  "高铁专家来了，说你做的不对。",
  "你收藏了 100 个高铁视频，再也没打开过。",
  "高铁排行榜第一名：你。倒数第一名：骁龙450。",
  "高铁的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你高铁了吗？没有，手机也没高铁。",
  "你花了 100 块钱高铁，结果什么也没得到。",
  "建议：高铁的时候别玩手机，会爆炸。",
  "高铁排行榜前 10 名，你一个都不认识。",
  "高铁排行榜前 10 名，你一个都不认识。",
  "你被高铁骗了，损失了 1 块钱。",
  "高铁的正确姿势：放下手机。",
  "高铁的教程看了 100 个，还是不会。",
  "高铁的正确姿势：放下手机。",
  "你问百度高铁怎么办，百度推荐了你看手机。",
  "你搜索高铁，出来了 10000 条结果，你一条也没看。",
  "你收藏了 100 个高铁视频，再也没打开过。",
  "你刷到了高铁的短视频，刷了 1 小时。",
  "高铁结束了，你觉得浪费时间，但是很快乐。",
  "建议：高铁的时候别玩手机，会爆炸。",
  "高铁的教程看了 100 个，还是不会。",
];

const REPLY_BULK_036 = [
  "飞机的教程看了 100 个，还是不会。",
  "飞机结束了，你觉得浪费时间，但是很快乐。",
  "飞机的最高境界：不用手机。",
  "你刷到了飞机的短视频，刷了 1 小时。",
  "飞机的最高境界：不用手机。",
  "飞机的正确姿势：放下手机。",
  "飞机的最高境界：不用手机。",
  "你发誓再也不飞机了，明天又开始。",
  "你飞机了 3 小时，手机也烫了 3 小时。",
  "建议：飞机的时候别玩手机，会爆炸。",
  "你问百度飞机怎么办，百度推荐了你看手机。",
  "你飞机了 3 小时，手机也烫了 3 小时。",
  "你搜索飞机，出来了 10000 条结果，你一条也没看。",
  "飞机的时候，你想起了手机。",
  "飞机的教程看了 100 个，还是不会。",
  "飞机的教程看了 100 个，还是不会。",
  "飞机专家来了，说你做的不对。",
  "你被飞机骗了，损失了 1 块钱。",
  "你打开了飞机 APP，卡了 10 秒。",
  "飞机结束了，你觉得浪费时间，但是很快乐。",
  "飞机排行榜第一名：你。倒数第一名：骁龙450。",
  "你关于飞机的想法？我觉得飞机比骁龙450 还卡。",
  "飞机的时候，手机突然响了，吓你一跳。",
  "你问我飞机怎么样？我觉得一般，不如玩手机。",
  "飞机排行榜第一名：你。倒数第一名：骁龙450。",
];

const REPLY_BULK_037 = [
  "你花了 100 块钱酒店，结果什么也没得到。",
  "酒店的教程看了 100 个，还是不会。",
  "酒店的教程看了 100 个，还是不会。",
  "酒店真有意思，但是手机更有意思。",
  "酒店的教程看了 100 个，还是不会。",
  "酒店排行榜第一名：你。倒数第一名：骁龙450。",
  "酒店的时候，你想起了手机。",
  "你搜索酒店，出来了 10000 条结果，你一条也没看。",
  "你酒店的时候，手机电量从 80% 掉到 20%。",
  "你刷到了酒店的短视频，刷了 1 小时。",
  "酒店真有意思，但是手机更有意思。",
  "你问百度酒店怎么办，百度推荐了你看手机。",
  "酒店的正确姿势：放下手机。",
  "酒店的最高境界：不用手机。",
  "你发誓再也不酒店了，明天又开始。",
  "你被酒店骗了，损失了 1 块钱。",
  "酒店专家来了，说你做的不对。",
  "你问百度酒店怎么办，百度推荐了你看手机。",
  "酒店结束了，你觉得浪费时间，但是很快乐。",
  "酒店排行榜前 10 名，你一个都不认识。",
  "你问百度酒店怎么办，百度推荐了你看手机。",
  "酒店排行榜第一名：你。倒数第一名：骁龙450。",
  "酒店真有意思，但是手机更有意思。",
  "酒店结束了，你觉得浪费时间，但是很快乐。",
  "你问百度酒店怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_038 = [
  "你景区的时候，手机电量从 80% 掉到 20%。",
  "景区真有意思，但是手机更有意思。",
  "景区排行榜前 10 名，你一个都不认识。",
  "景区真有意思，但是手机更有意思。",
  "景区真有意思，但是手机更有意思。",
  "景区的正确姿势：放下手机。",
  "景区的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你景区了吗？没有，手机也没景区。",
  "景区的正确姿势：放下手机。",
  "今天你景区了吗？没有，手机也没景区。",
  "景区的时候，你想起了手机。",
  "你收藏了 100 个景区视频，再也没打开过。",
  "你景区了 3 小时，手机也烫了 3 小时。",
  "景区真有意思，但是手机更有意思。",
  "景区的时候，你想起了手机。",
  "你问百度景区怎么办，百度推荐了你看手机。",
  "你景区的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不景区了，明天又开始。",
  "景区真有意思，但是手机更有意思。",
  "景区的时候，手机突然响了，吓你一跳。",
  "你景区了 3 小时，手机也烫了 3 小时。",
  "你景区了 3 小时，手机也烫了 3 小时。",
  "你景区的时候，手机电量从 80% 掉到 20%。",
  "今天你景区了吗？没有，手机也没景区。",
  "你搜索景区，出来了 10000 条结果，你一条也没看。",
];

const REPLY_BULK_039 = [
  "你排队了 3 小时，手机也烫了 3 小时。",
  "排队的正确姿势：放下手机。",
  "排队真有意思，但是手机更有意思。",
  "你花了 100 块钱排队，结果什么也没得到。",
  "你被排队骗了，损失了 1 块钱。",
  "排队结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了排队的短视频，刷了 1 小时。",
  "你问百度排队怎么办，百度推荐了你看手机。",
  "你关于排队的想法？我觉得排队比骁龙450 还卡。",
  "你收藏了 100 个排队视频，再也没打开过。",
  "你问我排队怎么样？我觉得一般，不如玩手机。",
  "排队的教程看了 100 个，还是不会。",
  "你发誓再也不排队了，明天又开始。",
  "你问百度排队怎么办，百度推荐了你看手机。",
  "建议：排队的时候别玩手机，会爆炸。",
  "排队的时候，手机突然响了，吓你一跳。",
  "排队的正确姿势：放下手机。",
  "排队排行榜前 10 名，你一个都不认识。",
  "你花了 100 块钱排队，结果什么也没得到。",
  "排队真有意思，但是手机更有意思。",
  "排队的最高境界：不用手机。",
  "排队真有意思，但是手机更有意思。",
  "你排队的时候，手机电量从 80% 掉到 20%。",
  "排队的教程看了 100 个，还是不会。",
  "今天你排队了吗？没有，手机也没排队。",
];

const REPLY_BULK_040 = [
  "你刷到了堵车的短视频，刷了 1 小时。",
  "你关于堵车的想法？我觉得堵车比骁龙450 还卡。",
  "今天你堵车了吗？没有，手机也没堵车。",
  "你打开了堵车 APP，卡了 10 秒。",
  "你发誓再也不堵车了，明天又开始。",
  "堵车的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你堵车的时候，手机电量从 80% 掉到 20%。",
  "你堵车的时候，手机电量从 80% 掉到 20%。",
  "堵车的时候，你想起了手机。",
  "堵车的最高境界：不用手机。",
  "你搜索堵车，出来了 10000 条结果，你一条也没看。",
  "你关于堵车的想法？我觉得堵车比骁龙450 还卡。",
  "你堵车了 3 小时，手机也烫了 3 小时。",
  "堵车的教程看了 100 个，还是不会。",
  "堵车排行榜第一名：你。倒数第一名：骁龙450。",
  "建议：堵车的时候别玩手机，会爆炸。",
  "你花了 100 块钱堵车，结果什么也没得到。",
  "堵车的正确姿势：放下手机。",
  "你花了 100 块钱堵车，结果什么也没得到。",
  "堵车排行榜第一名：你。倒数第一名：骁龙450。",
  "你堵车了 3 小时，手机也烫了 3 小时。",
  "你问我堵车怎么样？我觉得一般，不如玩手机。",
  "你问我堵车怎么样？我觉得一般，不如玩手机。",
  "堵车的正确姿势：放下手机。",
  "你刷到了堵车的短视频，刷了 1 小时。",
];

const REPLY_BULK_041 = [
  "下雨排行榜第一名：你。倒数第一名：骁龙450。",
  "你发誓再也不下雨了，明天又开始。",
  "你下雨了 3 小时，手机也烫了 3 小时。",
  "你问百度下雨怎么办，百度推荐了你看手机。",
  "你花了 100 块钱下雨，结果什么也没得到。",
  "下雨排行榜前 10 名，你一个都不认识。",
  "你花了 100 块钱下雨，结果什么也没得到。",
  "下雨的时候，手机突然响了，吓你一跳。",
  "你发誓再也不下雨了，明天又开始。",
  "你下雨的时候，手机电量从 80% 掉到 20%。",
  "下雨排行榜第一名：你。倒数第一名：骁龙450。",
  "你收藏了 100 个下雨视频，再也没打开过。",
  "你被下雨骗了，损失了 1 块钱。",
  "下雨排行榜前 10 名，你一个都不认识。",
  "下雨的时候，手机突然响了，吓你一跳。",
  "你问百度下雨怎么办，百度推荐了你看手机。",
  "下雨结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了下雨的短视频，刷了 1 小时。",
  "建议：下雨的时候别玩手机，会爆炸。",
  "下雨排行榜第一名：你。倒数第一名：骁龙450。",
  "下雨排行榜前 10 名，你一个都不认识。",
  "下雨排行榜第一名：你。倒数第一名：骁龙450。",
  "你打开了下雨 APP，卡了 10 秒。",
  "你搜索下雨，出来了 10000 条结果，你一条也没看。",
  "建议：下雨的时候别玩手机，会爆炸。",
];

const REPLY_BULK_042 = [
  "你发誓再也不下雪了，明天又开始。",
  "你下雪的时候，手机电量从 80% 掉到 20%。",
  "下雪的正确姿势：放下手机。",
  "下雪结束了，你觉得浪费时间，但是很快乐。",
  "你下雪的时候，手机电量从 80% 掉到 20%。",
  "你下雪了 3 小时，手机也烫了 3 小时。",
  "你打开了下雪 APP，卡了 10 秒。",
  "你下雪了 3 小时，手机也烫了 3 小时。",
  "下雪排行榜第一名：你。倒数第一名：骁龙450。",
  "你被下雪骗了，损失了 1 块钱。",
  "你花了 100 块钱下雪，结果什么也没得到。",
  "下雪排行榜第一名：你。倒数第一名：骁龙450。",
  "你花了 100 块钱下雪，结果什么也没得到。",
  "你关于下雪的想法？我觉得下雪比骁龙450 还卡。",
  "你问百度下雪怎么办，百度推荐了你看手机。",
  "下雪真有意思，但是手机更有意思。",
  "你被下雪骗了，损失了 1 块钱。",
  "你被下雪骗了，损失了 1 块钱。",
  "下雪的时候，你想起了手机。",
  "你收藏了 100 个下雪视频，再也没打开过。",
  "下雪排行榜前 10 名，你一个都不认识。",
  "你发誓再也不下雪了，明天又开始。",
  "下雪专家来了，说你做的不对。",
  "你关于下雪的想法？我觉得下雪比骁龙450 还卡。",
  "你刷到了下雪的短视频，刷了 1 小时。",
];

const REPLY_BULK_043 = [
  "刮风的教程看了 100 个，还是不会。",
  "刮风的时候，手机突然响了，吓你一跳。",
  "刮风的时候，你想起了手机。",
  "你发誓再也不刮风了，明天又开始。",
  "你刷到了刮风的短视频，刷了 1 小时。",
  "刮风真有意思，但是手机更有意思。",
  "你打开了刮风 APP，卡了 10 秒。",
  "刮风真有意思，但是手机更有意思。",
  "你问百度刮风怎么办，百度推荐了你看手机。",
  "你问我刮风怎么样？我觉得一般，不如玩手机。",
  "你发誓再也不刮风了，明天又开始。",
  "刮风的时候，手机突然响了，吓你一跳。",
  "刮风专家来了，说你做的不对。",
  "刮风结束了，你觉得浪费时间，但是很快乐。",
  "你被刮风骗了，损失了 1 块钱。",
  "刮风的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你刮风了吗？没有，手机也没刮风。",
  "你刮风的时候，手机电量从 80% 掉到 20%。",
  "刮风的正确姿势：放下手机。",
  "你问百度刮风怎么办，百度推荐了你看手机。",
  "刮风的最高境界：不用手机。",
  "你搜索刮风，出来了 10000 条结果，你一条也没看。",
  "刮风的时候，你想起了手机。",
  "刮风的正确姿势：放下手机。",
  "建议：刮风的时候别玩手机，会爆炸。",
];

const REPLY_BULK_044 = [
  "打雷的时候，手机突然响了，吓你一跳。",
  "打雷的时候，手机突然响了，吓你一跳。",
  "你发誓再也不打雷了，明天又开始。",
  "你问百度打雷怎么办，百度推荐了你看手机。",
  "打雷的教程看了 100 个，还是不会。",
  "打雷的教程看了 100 个，还是不会。",
  "你打开了打雷 APP，卡了 10 秒。",
  "打雷的时候，你想起了手机。",
  "你收藏了 100 个打雷视频，再也没打开过。",
  "今天你打雷了吗？没有，手机也没打雷。",
  "建议：打雷的时候别玩手机，会爆炸。",
  "打雷的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你打雷了吗？没有，手机也没打雷。",
  "建议：打雷的时候别玩手机，会爆炸。",
  "打雷的教程看了 100 个，还是不会。",
  "打雷的时候，手机突然响了，吓你一跳。",
  "打雷的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你打开了打雷 APP，卡了 10 秒。",
  "打雷专家来了，说你做的不对。",
  "你被打雷骗了，损失了 1 块钱。",
  "打雷的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "打雷的时候，手机突然响了，吓你一跳。",
  "打雷结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了打雷的短视频，刷了 1 小时。",
  "你问百度打雷怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_045 = [
  "你关于闪电的想法？我觉得闪电比骁龙450 还卡。",
  "闪电真有意思，但是手机更有意思。",
  "闪电的最高境界：不用手机。",
  "闪电真有意思，但是手机更有意思。",
  "你关于闪电的想法？我觉得闪电比骁龙450 还卡。",
  "你打开了闪电 APP，卡了 10 秒。",
  "闪电专家来了，说你做的不对。",
  "建议：闪电的时候别玩手机，会爆炸。",
  "你闪电了 3 小时，手机也烫了 3 小时。",
  "你问百度闪电怎么办，百度推荐了你看手机。",
  "闪电的时候，你想起了手机。",
  "你关于闪电的想法？我觉得闪电比骁龙450 还卡。",
  "今天你闪电了吗？没有，手机也没闪电。",
  "闪电排行榜前 10 名，你一个都不认识。",
  "建议：闪电的时候别玩手机，会爆炸。",
  "你搜索闪电，出来了 10000 条结果，你一条也没看。",
  "闪电结束了，你觉得浪费时间，但是很快乐。",
  "闪电的教程看了 100 个，还是不会。",
  "你打开了闪电 APP，卡了 10 秒。",
  "闪电排行榜前 10 名，你一个都不认识。",
  "闪电的最高境界：不用手机。",
  "你闪电的时候，手机电量从 80% 掉到 20%。",
  "闪电真有意思，但是手机更有意思。",
  "你收藏了 100 个闪电视频，再也没打开过。",
  "你刷到了闪电的短视频，刷了 1 小时。",
];

const REPLY_BULK_046 = [
  "你问我日出怎么样？我觉得一般，不如玩手机。",
  "日出的最高境界：不用手机。",
  "你日出的时候，手机电量从 80% 掉到 20%。",
  "日出的时候，手机突然响了，吓你一跳。",
  "你日出的时候，手机电量从 80% 掉到 20%。",
  "你问我日出怎么样？我觉得一般，不如玩手机。",
  "日出专家来了，说你做的不对。",
  "你问我日出怎么样？我觉得一般，不如玩手机。",
  "日出的教程看了 100 个，还是不会。",
  "日出的最高境界：不用手机。",
  "你花了 100 块钱日出，结果什么也没得到。",
  "今天你日出了吗？没有，手机也没日出。",
  "你刷到了日出的短视频，刷了 1 小时。",
  "你问我日出怎么样？我觉得一般，不如玩手机。",
  "日出结束了，你觉得浪费时间，但是很快乐。",
  "你日出了 3 小时，手机也烫了 3 小时。",
  "日出的时候，手机突然响了，吓你一跳。",
  "日出排行榜第一名：你。倒数第一名：骁龙450。",
  "你搜索日出，出来了 10000 条结果，你一条也没看。",
  "你打开了日出 APP，卡了 10 秒。",
  "日出的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你刷到了日出的短视频，刷了 1 小时。",
  "日出的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "日出专家来了，说你做的不对。",
  "你刷到了日出的短视频，刷了 1 小时。",
];

const REPLY_BULK_047 = [
  "日落的教程看了 100 个，还是不会。",
  "你关于日落的想法？我觉得日落比骁龙450 还卡。",
  "你刷到了日落的短视频，刷了 1 小时。",
  "日落排行榜第一名：你。倒数第一名：骁龙450。",
  "日落专家来了，说你做的不对。",
  "日落排行榜前 10 名，你一个都不认识。",
  "今天你日落了吗？没有，手机也没日落。",
  "日落的教程看了 100 个，还是不会。",
  "日落的时候，手机突然响了，吓你一跳。",
  "日落真有意思，但是手机更有意思。",
  "你收藏了 100 个日落视频，再也没打开过。",
  "你问我日落怎么样？我觉得一般，不如玩手机。",
  "日落的教程看了 100 个，还是不会。",
  "日落的最高境界：不用手机。",
  "日落的时候，你想起了手机。",
  "你搜索日落，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱日落，结果什么也没得到。",
  "日落排行榜前 10 名，你一个都不认识。",
  "日落的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你关于日落的想法？我觉得日落比骁龙450 还卡。",
  "你发誓再也不日落了，明天又开始。",
  "日落结束了，你觉得浪费时间，但是很快乐。",
  "日落的教程看了 100 个，还是不会。",
  "你日落了 3 小时，手机也烫了 3 小时。",
  "日落的教程看了 100 个，还是不会。",
];

const REPLY_BULK_048 = [
  "你打开了星空 APP，卡了 10 秒。",
  "星空的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你发誓再也不星空了，明天又开始。",
  "星空排行榜第一名：你。倒数第一名：骁龙450。",
  "星空的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "建议：星空的时候别玩手机，会爆炸。",
  "你问百度星空怎么办，百度推荐了你看手机。",
  "你星空了 3 小时，手机也烫了 3 小时。",
  "星空的时候，手机突然响了，吓你一跳。",
  "星空专家来了，说你做的不对。",
  "你打开了星空 APP，卡了 10 秒。",
  "你打开了星空 APP，卡了 10 秒。",
  "你花了 100 块钱星空，结果什么也没得到。",
  "星空专家来了，说你做的不对。",
  "你关于星空的想法？我觉得星空比骁龙450 还卡。",
  "你问我星空怎么样？我觉得一般，不如玩手机。",
  "星空排行榜第一名：你。倒数第一名：骁龙450。",
  "今天你星空了吗？没有，手机也没星空。",
  "星空的时候，你想起了手机。",
  "你搜索星空，出来了 10000 条结果，你一条也没看。",
  "你星空了 3 小时，手机也烫了 3 小时。",
  "星空的教程看了 100 个，还是不会。",
  "星空的时候，你想起了手机。",
  "你发誓再也不星空了，明天又开始。",
  "建议：星空的时候别玩手机，会爆炸。",
];

const REPLY_BULK_049 = [
  "月亮的时候，你想起了手机。",
  "你月亮了 3 小时，手机也烫了 3 小时。",
  "今天你月亮了吗？没有，手机也没月亮。",
  "月亮排行榜第一名：你。倒数第一名：骁龙450。",
  "你月亮的时候，手机电量从 80% 掉到 20%。",
  "你被月亮骗了，损失了 1 块钱。",
  "你月亮的时候，手机电量从 80% 掉到 20%。",
  "你问百度月亮怎么办，百度推荐了你看手机。",
  "你打开了月亮 APP，卡了 10 秒。",
  "月亮的时候，手机突然响了，吓你一跳。",
  "你问百度月亮怎么办，百度推荐了你看手机。",
  "月亮的正确姿势：放下手机。",
  "今天你月亮了吗？没有，手机也没月亮。",
  "你发誓再也不月亮了，明天又开始。",
  "你月亮的时候，手机电量从 80% 掉到 20%。",
  "月亮的时候，手机突然响了，吓你一跳。",
  "月亮的教程看了 100 个，还是不会。",
  "你被月亮骗了，损失了 1 块钱。",
  "今天你月亮了吗？没有，手机也没月亮。",
  "月亮排行榜第一名：你。倒数第一名：骁龙450。",
  "你被月亮骗了，损失了 1 块钱。",
  "你被月亮骗了，损失了 1 块钱。",
  "你刷到了月亮的短视频，刷了 1 小时。",
  "今天你月亮了吗？没有，手机也没月亮。",
  "你收藏了 100 个月亮视频，再也没打开过。",
];

const REPLY_BULK_050 = [
  "建议：太阳的时候别玩手机，会爆炸。",
  "你太阳了 3 小时，手机也烫了 3 小时。",
  "你被太阳骗了，损失了 1 块钱。",
  "建议：太阳的时候别玩手机，会爆炸。",
  "太阳的时候，你想起了手机。",
  "太阳排行榜第一名：你。倒数第一名：骁龙450。",
  "你关于太阳的想法？我觉得太阳比骁龙450 还卡。",
  "你收藏了 100 个太阳视频，再也没打开过。",
  "太阳结束了，你觉得浪费时间，但是很快乐。",
  "你被太阳骗了，损失了 1 块钱。",
  "今天你太阳了吗？没有，手机也没太阳。",
  "你刷到了太阳的短视频，刷了 1 小时。",
  "太阳的时候，你想起了手机。",
  "建议：太阳的时候别玩手机，会爆炸。",
  "你太阳的时候，手机电量从 80% 掉到 20%。",
  "太阳排行榜前 10 名，你一个都不认识。",
  "你问百度太阳怎么办，百度推荐了你看手机。",
  "你太阳了 3 小时，手机也烫了 3 小时。",
  "你问百度太阳怎么办，百度推荐了你看手机。",
  "你被太阳骗了，损失了 1 块钱。",
  "太阳的教程看了 100 个，还是不会。",
  "太阳的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问百度太阳怎么办，百度推荐了你看手机。",
  "你问我太阳怎么样？我觉得一般，不如玩手机。",
  "你刷到了太阳的短视频，刷了 1 小时。",
];

const REPLY_BULK_051 = [
  "今天你咖啡了吗？没有，手机也没咖啡。",
  "你问百度咖啡怎么办，百度推荐了你看手机。",
  "你发誓再也不咖啡了，明天又开始。",
  "你问我咖啡怎么样？我觉得一般，不如玩手机。",
  "你问百度咖啡怎么办，百度推荐了你看手机。",
  "咖啡专家来了，说你做的不对。",
  "咖啡的时候，手机突然响了，吓你一跳。",
  "建议：咖啡的时候别玩手机，会爆炸。",
  "你问我咖啡怎么样？我觉得一般，不如玩手机。",
  "今天你咖啡了吗？没有，手机也没咖啡。",
  "你关于咖啡的想法？我觉得咖啡比骁龙450 还卡。",
  "你花了 100 块钱咖啡，结果什么也没得到。",
  "咖啡专家来了，说你做的不对。",
  "你问百度咖啡怎么办，百度推荐了你看手机。",
  "建议：咖啡的时候别玩手机，会爆炸。",
  "咖啡的时候，手机突然响了，吓你一跳。",
  "咖啡的正确姿势：放下手机。",
  "咖啡结束了，你觉得浪费时间，但是很快乐。",
  "你咖啡了 3 小时，手机也烫了 3 小时。",
  "你咖啡了 3 小时，手机也烫了 3 小时。",
  "你问我咖啡怎么样？我觉得一般，不如玩手机。",
  "你咖啡了 3 小时，手机也烫了 3 小时。",
  "你问百度咖啡怎么办，百度推荐了你看手机。",
  "咖啡排行榜第一名：你。倒数第一名：骁龙450。",
  "咖啡的教程看了 100 个，还是不会。",
];

const REPLY_BULK_052 = [
  "你搜索奶茶，出来了 10000 条结果，你一条也没看。",
  "奶茶的最高境界：不用手机。",
  "奶茶专家来了，说你做的不对。",
  "奶茶的时候，你想起了手机。",
  "你被奶茶骗了，损失了 1 块钱。",
  "你被奶茶骗了，损失了 1 块钱。",
  "你奶茶了 3 小时，手机也烫了 3 小时。",
  "奶茶的时候，手机突然响了，吓你一跳。",
  "建议：奶茶的时候别玩手机，会爆炸。",
  "你关于奶茶的想法？我觉得奶茶比骁龙450 还卡。",
  "你发誓再也不奶茶了，明天又开始。",
  "建议：奶茶的时候别玩手机，会爆炸。",
  "奶茶排行榜前 10 名，你一个都不认识。",
  "你搜索奶茶，出来了 10000 条结果，你一条也没看。",
  "奶茶真有意思，但是手机更有意思。",
  "奶茶的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "奶茶的教程看了 100 个，还是不会。",
  "你搜索奶茶，出来了 10000 条结果，你一条也没看。",
  "你问我奶茶怎么样？我觉得一般，不如玩手机。",
  "你刷到了奶茶的短视频，刷了 1 小时。",
  "你奶茶的时候，手机电量从 80% 掉到 20%。",
  "奶茶真有意思，但是手机更有意思。",
  "奶茶的正确姿势：放下手机。",
  "奶茶的最高境界：不用手机。",
  "你奶茶了 3 小时，手机也烫了 3 小时。",
];

const REPLY_BULK_053 = [
  "你刷到了火锅的短视频，刷了 1 小时。",
  "你问百度火锅怎么办，百度推荐了你看手机。",
  "你打开了火锅 APP，卡了 10 秒。",
  "火锅真有意思，但是手机更有意思。",
  "你关于火锅的想法？我觉得火锅比骁龙450 还卡。",
  "火锅专家来了，说你做的不对。",
  "建议：火锅的时候别玩手机，会爆炸。",
  "你火锅的时候，手机电量从 80% 掉到 20%。",
  "你刷到了火锅的短视频，刷了 1 小时。",
  "你被火锅骗了，损失了 1 块钱。",
  "你花了 100 块钱火锅，结果什么也没得到。",
  "火锅的正确姿势：放下手机。",
  "火锅的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "火锅的最高境界：不用手机。",
  "火锅的教程看了 100 个，还是不会。",
  "你发誓再也不火锅了，明天又开始。",
  "建议：火锅的时候别玩手机，会爆炸。",
  "火锅排行榜前 10 名，你一个都不认识。",
  "火锅的正确姿势：放下手机。",
  "火锅的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你关于火锅的想法？我觉得火锅比骁龙450 还卡。",
  "你被火锅骗了，损失了 1 块钱。",
  "火锅的时候，你想起了手机。",
  "你问我火锅怎么样？我觉得一般，不如玩手机。",
  "你打开了火锅 APP，卡了 10 秒。",
];

const REPLY_BULK_054 = [
  "烧烤专家来了，说你做的不对。",
  "你问我烧烤怎么样？我觉得一般，不如玩手机。",
  "你收藏了 100 个烧烤视频，再也没打开过。",
  "烧烤结束了，你觉得浪费时间，但是很快乐。",
  "烧烤的正确姿势：放下手机。",
  "烧烤的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "烧烤的正确姿势：放下手机。",
  "烧烤的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你烧烤了 3 小时，手机也烫了 3 小时。",
  "你收藏了 100 个烧烤视频，再也没打开过。",
  "烧烤排行榜前 10 名，你一个都不认识。",
  "你问百度烧烤怎么办，百度推荐了你看手机。",
  "你关于烧烤的想法？我觉得烧烤比骁龙450 还卡。",
  "你关于烧烤的想法？我觉得烧烤比骁龙450 还卡。",
  "烧烤的最高境界：不用手机。",
  "烧烤排行榜前 10 名，你一个都不认识。",
  "你烧烤了 3 小时，手机也烫了 3 小时。",
  "你烧烤的时候，手机电量从 80% 掉到 20%。",
  "烧烤的时候，手机突然响了，吓你一跳。",
  "烧烤的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你打开了烧烤 APP，卡了 10 秒。",
  "你问我烧烤怎么样？我觉得一般，不如玩手机。",
  "烧烤的正确姿势：放下手机。",
  "你刷到了烧烤的短视频，刷了 1 小时。",
  "你搜索烧烤，出来了 10000 条结果，你一条也没看。",
];

const REPLY_BULK_055 = [
  "你串串了 3 小时，手机也烫了 3 小时。",
  "串串结束了，你觉得浪费时间，但是很快乐。",
  "串串的教程看了 100 个，还是不会。",
  "串串的正确姿势：放下手机。",
  "你刷到了串串的短视频，刷了 1 小时。",
  "你打开了串串 APP，卡了 10 秒。",
  "建议：串串的时候别玩手机，会爆炸。",
  "串串真有意思，但是手机更有意思。",
  "你关于串串的想法？我觉得串串比骁龙450 还卡。",
  "串串结束了，你觉得浪费时间，但是很快乐。",
  "串串的教程看了 100 个，还是不会。",
  "你收藏了 100 个串串视频，再也没打开过。",
  "串串真有意思，但是手机更有意思。",
  "你花了 100 块钱串串，结果什么也没得到。",
  "串串的时候，你想起了手机。",
  "你关于串串的想法？我觉得串串比骁龙450 还卡。",
  "串串的时候，手机突然响了，吓你一跳。",
  "串串结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个串串视频，再也没打开过。",
  "串串真有意思，但是手机更有意思。",
  "串串专家来了，说你做的不对。",
  "你被串串骗了，损失了 1 块钱。",
  "你被串串骗了，损失了 1 块钱。",
  "你关于串串的想法？我觉得串串比骁龙450 还卡。",
  "串串的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_056 = [
  "寿司的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你打开了寿司 APP，卡了 10 秒。",
  "你打开了寿司 APP，卡了 10 秒。",
  "你问我寿司怎么样？我觉得一般，不如玩手机。",
  "寿司的最高境界：不用手机。",
  "寿司的时候，手机突然响了，吓你一跳。",
  "建议：寿司的时候别玩手机，会爆炸。",
  "寿司专家来了，说你做的不对。",
  "寿司的时候，你想起了手机。",
  "寿司的时候，手机突然响了，吓你一跳。",
  "你搜索寿司，出来了 10000 条结果，你一条也没看。",
  "寿司的时候，手机突然响了，吓你一跳。",
  "寿司排行榜前 10 名，你一个都不认识。",
  "你收藏了 100 个寿司视频，再也没打开过。",
  "寿司的时候，你想起了手机。",
  "寿司的时候，手机突然响了，吓你一跳。",
  "寿司排行榜前 10 名，你一个都不认识。",
  "寿司结束了，你觉得浪费时间，但是很快乐。",
  "你花了 100 块钱寿司，结果什么也没得到。",
  "你刷到了寿司的短视频，刷了 1 小时。",
  "你收藏了 100 个寿司视频，再也没打开过。",
  "寿司的最高境界：不用手机。",
  "你寿司了 3 小时，手机也烫了 3 小时。",
  "你打开了寿司 APP，卡了 10 秒。",
  "寿司结束了，你觉得浪费时间，但是很快乐。",
];

const REPLY_BULK_057 = [
  "你问百度披萨怎么办，百度推荐了你看手机。",
  "你关于披萨的想法？我觉得披萨比骁龙450 还卡。",
  "披萨排行榜第一名：你。倒数第一名：骁龙450。",
  "披萨排行榜第一名：你。倒数第一名：骁龙450。",
  "你披萨的时候，手机电量从 80% 掉到 20%。",
  "你收藏了 100 个披萨视频，再也没打开过。",
  "你披萨的时候，手机电量从 80% 掉到 20%。",
  "你搜索披萨，出来了 10000 条结果，你一条也没看。",
  "披萨专家来了，说你做的不对。",
  "你问我披萨怎么样？我觉得一般，不如玩手机。",
  "你披萨的时候，手机电量从 80% 掉到 20%。",
  "披萨的正确姿势：放下手机。",
  "披萨的最高境界：不用手机。",
  "你披萨了 3 小时，手机也烫了 3 小时。",
  "你打开了披萨 APP，卡了 10 秒。",
  "你问我披萨怎么样？我觉得一般，不如玩手机。",
  "披萨专家来了，说你做的不对。",
  "披萨真有意思，但是手机更有意思。",
  "披萨结束了，你觉得浪费时间，但是很快乐。",
  "披萨的最高境界：不用手机。",
  "你被披萨骗了，损失了 1 块钱。",
  "你问百度披萨怎么办，百度推荐了你看手机。",
  "披萨专家来了，说你做的不对。",
  "披萨排行榜第一名：你。倒数第一名：骁龙450。",
  "披萨结束了，你觉得浪费时间，但是很快乐。",
];

const REPLY_BULK_058 = [
  "你问百度汉堡怎么办，百度推荐了你看手机。",
  "你收藏了 100 个汉堡视频，再也没打开过。",
  "你问百度汉堡怎么办，百度推荐了你看手机。",
  "你问百度汉堡怎么办，百度推荐了你看手机。",
  "汉堡专家来了，说你做的不对。",
  "你汉堡的时候，手机电量从 80% 掉到 20%。",
  "汉堡的时候，你想起了手机。",
  "你发誓再也不汉堡了，明天又开始。",
  "汉堡的时候，手机突然响了，吓你一跳。",
  "你问我汉堡怎么样？我觉得一般，不如玩手机。",
  "你汉堡了 3 小时，手机也烫了 3 小时。",
  "汉堡的教程看了 100 个，还是不会。",
  "你收藏了 100 个汉堡视频，再也没打开过。",
  "今天你汉堡了吗？没有，手机也没汉堡。",
  "汉堡排行榜前 10 名，你一个都不认识。",
  "汉堡结束了，你觉得浪费时间，但是很快乐。",
  "汉堡排行榜第一名：你。倒数第一名：骁龙450。",
  "你收藏了 100 个汉堡视频，再也没打开过。",
  "你汉堡了 3 小时，手机也烫了 3 小时。",
  "你花了 100 块钱汉堡，结果什么也没得到。",
  "汉堡的正确姿势：放下手机。",
  "汉堡的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "汉堡真有意思，但是手机更有意思。",
  "汉堡的时候，手机突然响了，吓你一跳。",
  "汉堡专家来了，说你做的不对。",
];

const REPLY_BULK_059 = [
  "你被薯条骗了，损失了 1 块钱。",
  "你刷到了薯条的短视频，刷了 1 小时。",
  "薯条的正确姿势：放下手机。",
  "今天你薯条了吗？没有，手机也没薯条。",
  "薯条结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个薯条视频，再也没打开过。",
  "薯条排行榜前 10 名，你一个都不认识。",
  "今天你薯条了吗？没有，手机也没薯条。",
  "薯条结束了，你觉得浪费时间，但是很快乐。",
  "薯条的教程看了 100 个，还是不会。",
  "薯条的最高境界：不用手机。",
  "你问百度薯条怎么办，百度推荐了你看手机。",
  "你收藏了 100 个薯条视频，再也没打开过。",
  "你花了 100 块钱薯条，结果什么也没得到。",
  "你问我薯条怎么样？我觉得一般，不如玩手机。",
  "你薯条的时候，手机电量从 80% 掉到 20%。",
  "你被薯条骗了，损失了 1 块钱。",
  "你问百度薯条怎么办，百度推荐了你看手机。",
  "薯条的教程看了 100 个，还是不会。",
  "你收藏了 100 个薯条视频，再也没打开过。",
  "薯条的正确姿势：放下手机。",
  "薯条结束了，你觉得浪费时间，但是很快乐。",
  "薯条的教程看了 100 个，还是不会。",
  "你发誓再也不薯条了，明天又开始。",
  "你发誓再也不薯条了，明天又开始。",
];

const REPLY_BULK_060 = [
  "你搜索可乐，出来了 10000 条结果，你一条也没看。",
  "可乐专家来了，说你做的不对。",
  "可乐的教程看了 100 个，还是不会。",
  "你问我可乐怎么样？我觉得一般，不如玩手机。",
  "你关于可乐的想法？我觉得可乐比骁龙450 还卡。",
  "你花了 100 块钱可乐，结果什么也没得到。",
  "可乐的教程看了 100 个，还是不会。",
  "你花了 100 块钱可乐，结果什么也没得到。",
  "可乐专家来了，说你做的不对。",
  "可乐结束了，你觉得浪费时间，但是很快乐。",
  "你发誓再也不可乐了，明天又开始。",
  "你问我可乐怎么样？我觉得一般，不如玩手机。",
  "你问百度可乐怎么办，百度推荐了你看手机。",
  "可乐的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "可乐专家来了，说你做的不对。",
  "你发誓再也不可乐了，明天又开始。",
  "可乐排行榜前 10 名，你一个都不认识。",
  "你关于可乐的想法？我觉得可乐比骁龙450 还卡。",
  "你打开了可乐 APP，卡了 10 秒。",
  "你问我可乐怎么样？我觉得一般，不如玩手机。",
  "可乐排行榜第一名：你。倒数第一名：骁龙450。",
  "你可乐了 3 小时，手机也烫了 3 小时。",
  "你刷到了可乐的短视频，刷了 1 小时。",
  "可乐结束了，你觉得浪费时间，但是很快乐。",
  "可乐专家来了，说你做的不对。",
];

const REPLY_BULK_061 = [
  "你刷到了猫的短视频，刷了 1 小时。",
  "你猫了 3 小时，手机也烫了 3 小时。",
  "你花了 100 块钱猫，结果什么也没得到。",
  "猫的教程看了 100 个，还是不会。",
  "猫排行榜第一名：你。倒数第一名：骁龙450。",
  "你发誓再也不猫了，明天又开始。",
  "你关于猫的想法？我觉得猫比骁龙450 还卡。",
  "你问百度猫怎么办，百度推荐了你看手机。",
  "建议：猫的时候别玩手机，会爆炸。",
  "你打开了猫 APP，卡了 10 秒。",
  "你打开了猫 APP，卡了 10 秒。",
  "猫排行榜第一名：你。倒数第一名：骁龙450。",
  "猫专家来了，说你做的不对。",
  "你打开了猫 APP，卡了 10 秒。",
  "猫的时候，手机突然响了，吓你一跳。",
  "猫结束了，你觉得浪费时间，但是很快乐。",
  "你发誓再也不猫了，明天又开始。",
  "你被猫骗了，损失了 1 块钱。",
  "猫的教程看了 100 个，还是不会。",
  "你被猫骗了，损失了 1 块钱。",
  "你打开了猫 APP，卡了 10 秒。",
  "你花了 100 块钱猫，结果什么也没得到。",
  "你问我猫怎么样？我觉得一般，不如玩手机。",
  "猫的最高境界：不用手机。",
  "你收藏了 100 个猫视频，再也没打开过。",
];

const REPLY_BULK_062 = [
  "你关于狗的想法？我觉得狗比骁龙450 还卡。",
  "你打开了狗 APP，卡了 10 秒。",
  "建议：狗的时候别玩手机，会爆炸。",
  "你搜索狗，出来了 10000 条结果，你一条也没看。",
  "狗的最高境界：不用手机。",
  "狗的正确姿势：放下手机。",
  "狗真有意思，但是手机更有意思。",
  "狗的时候，手机突然响了，吓你一跳。",
  "你被狗骗了，损失了 1 块钱。",
  "你花了 100 块钱狗，结果什么也没得到。",
  "你打开了狗 APP，卡了 10 秒。",
  "你被狗骗了，损失了 1 块钱。",
  "你打开了狗 APP，卡了 10 秒。",
  "狗排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度狗怎么办，百度推荐了你看手机。",
  "你刷到了狗的短视频，刷了 1 小时。",
  "狗的最高境界：不用手机。",
  "狗结束了，你觉得浪费时间，但是很快乐。",
  "你狗了 3 小时，手机也烫了 3 小时。",
  "你打开了狗 APP，卡了 10 秒。",
  "建议：狗的时候别玩手机，会爆炸。",
  "你发誓再也不狗了，明天又开始。",
  "你问我狗怎么样？我觉得一般，不如玩手机。",
  "狗真有意思，但是手机更有意思。",
  "狗的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_063 = [
  "鱼的时候，手机突然响了，吓你一跳。",
  "你打开了鱼 APP，卡了 10 秒。",
  "你问百度鱼怎么办，百度推荐了你看手机。",
  "你花了 100 块钱鱼，结果什么也没得到。",
  "你搜索鱼，出来了 10000 条结果，你一条也没看。",
  "鱼真有意思，但是手机更有意思。",
  "建议：鱼的时候别玩手机，会爆炸。",
  "你关于鱼的想法？我觉得鱼比骁龙450 还卡。",
  "鱼的正确姿势：放下手机。",
  "鱼的时候，手机突然响了，吓你一跳。",
  "你花了 100 块钱鱼，结果什么也没得到。",
  "建议：鱼的时候别玩手机，会爆炸。",
  "鱼的时候，手机突然响了，吓你一跳。",
  "你刷到了鱼的短视频，刷了 1 小时。",
  "今天你鱼了吗？没有，手机也没鱼。",
  "鱼的时候，手机突然响了，吓你一跳。",
  "你刷到了鱼的短视频，刷了 1 小时。",
  "你发誓再也不鱼了，明天又开始。",
  "鱼排行榜前 10 名，你一个都不认识。",
  "你打开了鱼 APP，卡了 10 秒。",
  "今天你鱼了吗？没有，手机也没鱼。",
  "你花了 100 块钱鱼，结果什么也没得到。",
  "你鱼了 3 小时，手机也烫了 3 小时。",
  "你花了 100 块钱鱼，结果什么也没得到。",
  "你被鱼骗了，损失了 1 块钱。",
];

const REPLY_BULK_064 = [
  "建议：鸟的时候别玩手机，会爆炸。",
  "鸟的时候，你想起了手机。",
  "你鸟的时候，手机电量从 80% 掉到 20%。",
  "你问百度鸟怎么办，百度推荐了你看手机。",
  "鸟的教程看了 100 个，还是不会。",
  "你问我鸟怎么样？我觉得一般，不如玩手机。",
  "你花了 100 块钱鸟，结果什么也没得到。",
  "你打开了鸟 APP，卡了 10 秒。",
  "你发誓再也不鸟了，明天又开始。",
  "你鸟了 3 小时，手机也烫了 3 小时。",
  "你关于鸟的想法？我觉得鸟比骁龙450 还卡。",
  "鸟真有意思，但是手机更有意思。",
  "鸟结束了，你觉得浪费时间，但是很快乐。",
  "鸟结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个鸟视频，再也没打开过。",
  "鸟的时候，你想起了手机。",
  "你搜索鸟，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱鸟，结果什么也没得到。",
  "你打开了鸟 APP，卡了 10 秒。",
  "你鸟的时候，手机电量从 80% 掉到 20%。",
  "你问我鸟怎么样？我觉得一般，不如玩手机。",
  "你发誓再也不鸟了，明天又开始。",
  "你搜索鸟，出来了 10000 条结果，你一条也没看。",
  "建议：鸟的时候别玩手机，会爆炸。",
  "你花了 100 块钱鸟，结果什么也没得到。",
];

const REPLY_BULK_065 = [
  "你被花骗了，损失了 1 块钱。",
  "建议：花的时候别玩手机，会爆炸。",
  "花的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你搜索花，出来了 10000 条结果，你一条也没看。",
  "花结束了，你觉得浪费时间，但是很快乐。",
  "花的时候，你想起了手机。",
  "花的最高境界：不用手机。",
  "你花了 100 块钱花，结果什么也没得到。",
  "花结束了，你觉得浪费时间，但是很快乐。",
  "花的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你收藏了 100 个花视频，再也没打开过。",
  "你问我花怎么样？我觉得一般，不如玩手机。",
  "花排行榜前 10 名，你一个都不认识。",
  "花结束了，你觉得浪费时间，但是很快乐。",
  "花的教程看了 100 个，还是不会。",
  "你花了 3 小时，手机也烫了 3 小时。",
  "花的教程看了 100 个，还是不会。",
  "你花了 100 块钱花，结果什么也没得到。",
  "花的时候，你想起了手机。",
  "今天你花了吗？没有，手机也没花。",
  "你问百度花怎么办，百度推荐了你看手机。",
  "花结束了，你觉得浪费时间，但是很快乐。",
  "花的时候，你想起了手机。",
  "花的教程看了 100 个，还是不会。",
  "花的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_066 = [
  "你收藏了 100 个草视频，再也没打开过。",
  "你花了 100 块钱草，结果什么也没得到。",
  "草排行榜前 10 名，你一个都不认识。",
  "草的时候，你想起了手机。",
  "草排行榜第一名：你。倒数第一名：骁龙450。",
  "你草的时候，手机电量从 80% 掉到 20%。",
  "你搜索草，出来了 10000 条结果，你一条也没看。",
  "草排行榜前 10 名，你一个都不认识。",
  "草的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "草的时候，手机突然响了，吓你一跳。",
  "你草了 3 小时，手机也烫了 3 小时。",
  "你发誓再也不草了，明天又开始。",
  "草的教程看了 100 个，还是不会。",
  "你收藏了 100 个草视频，再也没打开过。",
  "草的时候，你想起了手机。",
  "你收藏了 100 个草视频，再也没打开过。",
  "你打开了草 APP，卡了 10 秒。",
  "草结束了，你觉得浪费时间，但是很快乐。",
  "你问我草怎么样？我觉得一般，不如玩手机。",
  "你关于草的想法？我觉得草比骁龙450 还卡。",
  "草排行榜第一名：你。倒数第一名：骁龙450。",
  "草结束了，你觉得浪费时间，但是很快乐。",
  "草结束了，你觉得浪费时间，但是很快乐。",
  "草的最高境界：不用手机。",
  "你草的时候，手机电量从 80% 掉到 20%。",
];

const REPLY_BULK_067 = [
  "树的最高境界：不用手机。",
  "树排行榜前 10 名，你一个都不认识。",
  "你被树骗了，损失了 1 块钱。",
  "你打开了树 APP，卡了 10 秒。",
  "树的正确姿势：放下手机。",
  "树的最高境界：不用手机。",
  "树专家来了，说你做的不对。",
  "你被树骗了，损失了 1 块钱。",
  "你花了 100 块钱树，结果什么也没得到。",
  "树结束了，你觉得浪费时间，但是很快乐。",
  "树的时候，手机突然响了，吓你一跳。",
  "树结束了，你觉得浪费时间，但是很快乐。",
  "树专家来了，说你做的不对。",
  "树的正确姿势：放下手机。",
  "你打开了树 APP，卡了 10 秒。",
  "你发誓再也不树了，明天又开始。",
  "你花了 100 块钱树，结果什么也没得到。",
  "你搜索树，出来了 10000 条结果，你一条也没看。",
  "树的正确姿势：放下手机。",
  "树的时候，手机突然响了，吓你一跳。",
  "树的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "树的最高境界：不用手机。",
  "树的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "树专家来了，说你做的不对。",
  "你发誓再也不树了，明天又开始。",
];

const REPLY_BULK_068 = [
  "你关于山的想法？我觉得山比骁龙450 还卡。",
  "你搜索山，出来了 10000 条结果，你一条也没看。",
  "你发誓再也不山了，明天又开始。",
  "山专家来了，说你做的不对。",
  "山排行榜前 10 名，你一个都不认识。",
  "你发誓再也不山了，明天又开始。",
  "山的时候，你想起了手机。",
  "你刷到了山的短视频，刷了 1 小时。",
  "你关于山的想法？我觉得山比骁龙450 还卡。",
  "你发誓再也不山了，明天又开始。",
  "你花了 100 块钱山，结果什么也没得到。",
  "山的时候，手机突然响了，吓你一跳。",
  "今天你山了吗？没有，手机也没山。",
  "山结束了，你觉得浪费时间，但是很快乐。",
  "你关于山的想法？我觉得山比骁龙450 还卡。",
  "你山的时候，手机电量从 80% 掉到 20%。",
  "你收藏了 100 个山视频，再也没打开过。",
  "你问百度山怎么办，百度推荐了你看手机。",
  "你问百度山怎么办，百度推荐了你看手机。",
  "今天你山了吗？没有，手机也没山。",
  "你打开了山 APP，卡了 10 秒。",
  "你搜索山，出来了 10000 条结果，你一条也没看。",
  "山的最高境界：不用手机。",
  "你花了 100 块钱山，结果什么也没得到。",
  "山的时候，你想起了手机。",
];

const REPLY_BULK_069 = [
  "河专家来了，说你做的不对。",
  "你收藏了 100 个河视频，再也没打开过。",
  "你河的时候，手机电量从 80% 掉到 20%。",
  "河的时候，你想起了手机。",
  "你关于河的想法？我觉得河比骁龙450 还卡。",
  "河排行榜第一名：你。倒数第一名：骁龙450。",
  "河排行榜第一名：你。倒数第一名：骁龙450。",
  "今天你河了吗？没有，手机也没河。",
  "建议：河的时候别玩手机，会爆炸。",
  "你问我河怎么样？我觉得一般，不如玩手机。",
  "你河了 3 小时，手机也烫了 3 小时。",
  "今天你河了吗？没有，手机也没河。",
  "你河的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不河了，明天又开始。",
  "河结束了，你觉得浪费时间，但是很快乐。",
  "你问百度河怎么办，百度推荐了你看手机。",
  "河的时候，手机突然响了，吓你一跳。",
  "你打开了河 APP，卡了 10 秒。",
  "河的正确姿势：放下手机。",
  "河结束了，你觉得浪费时间，但是很快乐。",
  "你问百度河怎么办，百度推荐了你看手机。",
  "河的教程看了 100 个，还是不会。",
  "你被河骗了，损失了 1 块钱。",
  "河结束了，你觉得浪费时间，但是很快乐。",
  "今天你河了吗？没有，手机也没河。",
];

const REPLY_BULK_070 = [
  "你收藏了 100 个海视频，再也没打开过。",
  "海真有意思，但是手机更有意思。",
  "你打开了海 APP，卡了 10 秒。",
  "你花了 100 块钱海，结果什么也没得到。",
  "你问我海怎么样？我觉得一般，不如玩手机。",
  "你打开了海 APP，卡了 10 秒。",
  "你海的时候，手机电量从 80% 掉到 20%。",
  "建议：海的时候别玩手机，会爆炸。",
  "你打开了海 APP，卡了 10 秒。",
  "建议：海的时候别玩手机，会爆炸。",
  "海的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "海排行榜前 10 名，你一个都不认识。",
  "海排行榜前 10 名，你一个都不认识。",
  "海专家来了，说你做的不对。",
  "今天你海了吗？没有，手机也没海。",
  "海真有意思，但是手机更有意思。",
  "海的时候，手机突然响了，吓你一跳。",
  "你问百度海怎么办，百度推荐了你看手机。",
  "海排行榜前 10 名，你一个都不认识。",
  "你关于海的想法？我觉得海比骁龙450 还卡。",
  "你搜索海，出来了 10000 条结果，你一条也没看。",
  "你搜索海，出来了 10000 条结果，你一条也没看。",
  "你收藏了 100 个海视频，再也没打开过。",
  "你花了 100 块钱海，结果什么也没得到。",
  "你发誓再也不海了，明天又开始。",
];

const REPLY_BULK_071 = [
  "你问百度跑步怎么办，百度推荐了你看手机。",
  "跑步的正确姿势：放下手机。",
  "跑步的时候，手机突然响了，吓你一跳。",
  "跑步排行榜第一名：你。倒数第一名：骁龙450。",
  "今天你跑步了吗？没有，手机也没跑步。",
  "你花了 100 块钱跑步，结果什么也没得到。",
  "你收藏了 100 个跑步视频，再也没打开过。",
  "跑步真有意思，但是手机更有意思。",
  "跑步的时候，你想起了手机。",
  "你被跑步骗了，损失了 1 块钱。",
  "你问百度跑步怎么办，百度推荐了你看手机。",
  "你跑步了 3 小时，手机也烫了 3 小时。",
  "跑步结束了，你觉得浪费时间，但是很快乐。",
  "跑步专家来了，说你做的不对。",
  "你跑步的时候，手机电量从 80% 掉到 20%。",
  "今天你跑步了吗？没有，手机也没跑步。",
  "建议：跑步的时候别玩手机，会爆炸。",
  "跑步的时候，手机突然响了，吓你一跳。",
  "跑步的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你花了 100 块钱跑步，结果什么也没得到。",
  "你刷到了跑步的短视频，刷了 1 小时。",
  "跑步的时候，手机突然响了，吓你一跳。",
  "你被跑步骗了，损失了 1 块钱。",
  "你被跑步骗了，损失了 1 块钱。",
  "跑步真有意思，但是手机更有意思。",
];

const REPLY_BULK_072 = [
  "你关于游泳的想法？我觉得游泳比骁龙450 还卡。",
  "你收藏了 100 个游泳视频，再也没打开过。",
  "你搜索游泳，出来了 10000 条结果，你一条也没看。",
  "你搜索游泳，出来了 10000 条结果，你一条也没看。",
  "你打开了游泳 APP，卡了 10 秒。",
  "游泳真有意思，但是手机更有意思。",
  "你花了 100 块钱游泳，结果什么也没得到。",
  "游泳排行榜第一名：你。倒数第一名：骁龙450。",
  "游泳的时候，你想起了手机。",
  "游泳排行榜前 10 名，你一个都不认识。",
  "游泳的时候，手机突然响了，吓你一跳。",
  "游泳的教程看了 100 个，还是不会。",
  "游泳结束了，你觉得浪费时间，但是很快乐。",
  "游泳真有意思，但是手机更有意思。",
  "游泳排行榜第一名：你。倒数第一名：骁龙450。",
  "游泳的最高境界：不用手机。",
  "你游泳了 3 小时，手机也烫了 3 小时。",
  "你搜索游泳，出来了 10000 条结果，你一条也没看。",
  "你游泳的时候，手机电量从 80% 掉到 20%。",
  "你收藏了 100 个游泳视频，再也没打开过。",
  "你关于游泳的想法？我觉得游泳比骁龙450 还卡。",
  "你打开了游泳 APP，卡了 10 秒。",
  "游泳排行榜第一名：你。倒数第一名：骁龙450。",
  "游泳的时候，手机突然响了，吓你一跳。",
  "游泳专家来了，说你做的不对。",
];

const REPLY_BULK_073 = [
  "建议：篮球的时候别玩手机，会爆炸。",
  "你发誓再也不篮球了，明天又开始。",
  "篮球专家来了，说你做的不对。",
  "建议：篮球的时候别玩手机，会爆炸。",
  "你关于篮球的想法？我觉得篮球比骁龙450 还卡。",
  "你发誓再也不篮球了，明天又开始。",
  "篮球的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "篮球的正确姿势：放下手机。",
  "建议：篮球的时候别玩手机，会爆炸。",
  "篮球的时候，你想起了手机。",
  "你问百度篮球怎么办，百度推荐了你看手机。",
  "你问我篮球怎么样？我觉得一般，不如玩手机。",
  "篮球排行榜第一名：你。倒数第一名：骁龙450。",
  "篮球的最高境界：不用手机。",
  "篮球的时候，你想起了手机。",
  "建议：篮球的时候别玩手机，会爆炸。",
  "你收藏了 100 个篮球视频，再也没打开过。",
  "你问百度篮球怎么办，百度推荐了你看手机。",
  "你问百度篮球怎么办，百度推荐了你看手机。",
  "你打开了篮球 APP，卡了 10 秒。",
  "你问百度篮球怎么办，百度推荐了你看手机。",
  "建议：篮球的时候别玩手机，会爆炸。",
  "你篮球的时候，手机电量从 80% 掉到 20%。",
  "你问我篮球怎么样？我觉得一般，不如玩手机。",
  "篮球的时候，手机突然响了，吓你一跳。",
];

const REPLY_BULK_074 = [
  "你问百度足球怎么办，百度推荐了你看手机。",
  "你发誓再也不足球了，明天又开始。",
  "足球真有意思，但是手机更有意思。",
  "你足球了 3 小时，手机也烫了 3 小时。",
  "足球真有意思，但是手机更有意思。",
  "足球排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度足球怎么办，百度推荐了你看手机。",
  "足球的时候，你想起了手机。",
  "足球的正确姿势：放下手机。",
  "你打开了足球 APP，卡了 10 秒。",
  "足球专家来了，说你做的不对。",
  "足球的时候，你想起了手机。",
  "足球的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你被足球骗了，损失了 1 块钱。",
  "你刷到了足球的短视频，刷了 1 小时。",
  "你发誓再也不足球了，明天又开始。",
  "足球排行榜第一名：你。倒数第一名：骁龙450。",
  "足球排行榜第一名：你。倒数第一名：骁龙450。",
  "你搜索足球，出来了 10000 条结果，你一条也没看。",
  "你足球了 3 小时，手机也烫了 3 小时。",
  "你发誓再也不足球了，明天又开始。",
  "你刷到了足球的短视频，刷了 1 小时。",
  "建议：足球的时候别玩手机，会爆炸。",
  "你被足球骗了，损失了 1 块钱。",
  "足球结束了，你觉得浪费时间，但是很快乐。",
];

const REPLY_BULK_075 = [
  "羽毛球真有意思，但是手机更有意思。",
  "羽毛球结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个羽毛球视频，再也没打开过。",
  "你问百度羽毛球怎么办，百度推荐了你看手机。",
  "今天你羽毛球了吗？没有，手机也没羽毛球。",
  "你问百度羽毛球怎么办，百度推荐了你看手机。",
  "你发誓再也不羽毛球了，明天又开始。",
  "你问我羽毛球怎么样？我觉得一般，不如玩手机。",
  "羽毛球排行榜前 10 名，你一个都不认识。",
  "羽毛球的时候，你想起了手机。",
  "你刷到了羽毛球的短视频，刷了 1 小时。",
  "你被羽毛球骗了，损失了 1 块钱。",
  "今天你羽毛球了吗？没有，手机也没羽毛球。",
  "你收藏了 100 个羽毛球视频，再也没打开过。",
  "羽毛球真有意思，但是手机更有意思。",
  "羽毛球的时候，你想起了手机。",
  "羽毛球的时候，手机突然响了，吓你一跳。",
  "羽毛球专家来了，说你做的不对。",
  "你羽毛球的时候，手机电量从 80% 掉到 20%。",
  "你打开了羽毛球 APP，卡了 10 秒。",
  "羽毛球排行榜第一名：你。倒数第一名：骁龙450。",
  "你收藏了 100 个羽毛球视频，再也没打开过。",
  "你打开了羽毛球 APP，卡了 10 秒。",
  "羽毛球的时候，你想起了手机。",
  "羽毛球的正确姿势：放下手机。",
];

const REPLY_BULK_076 = [
  "你花了 100 块钱乒乓球，结果什么也没得到。",
  "建议：乒乓球的时候别玩手机，会爆炸。",
  "你刷到了乒乓球的短视频，刷了 1 小时。",
  "乒乓球的最高境界：不用手机。",
  "你收藏了 100 个乒乓球视频，再也没打开过。",
  "你收藏了 100 个乒乓球视频，再也没打开过。",
  "乒乓球真有意思，但是手机更有意思。",
  "你乒乓球的时候，手机电量从 80% 掉到 20%。",
  "今天你乒乓球了吗？没有，手机也没乒乓球。",
  "建议：乒乓球的时候别玩手机，会爆炸。",
  "你收藏了 100 个乒乓球视频，再也没打开过。",
  "你搜索乒乓球，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱乒乓球，结果什么也没得到。",
  "建议：乒乓球的时候别玩手机，会爆炸。",
  "乒乓球排行榜第一名：你。倒数第一名：骁龙450。",
  "你被乒乓球骗了，损失了 1 块钱。",
  "乒乓球排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度乒乓球怎么办，百度推荐了你看手机。",
  "你关于乒乓球的想法？我觉得乒乓球比骁龙450 还卡。",
  "你关于乒乓球的想法？我觉得乒乓球比骁龙450 还卡。",
  "乒乓球的最高境界：不用手机。",
  "乒乓球排行榜第一名：你。倒数第一名：骁龙450。",
  "你关于乒乓球的想法？我觉得乒乓球比骁龙450 还卡。",
  "你被乒乓球骗了，损失了 1 块钱。",
  "乒乓球的最高境界：不用手机。",
];

const REPLY_BULK_077 = [
  "你打开了网球 APP，卡了 10 秒。",
  "网球的时候，你想起了手机。",
  "你刷到了网球的短视频，刷了 1 小时。",
  "网球的教程看了 100 个，还是不会。",
  "你花了 100 块钱网球，结果什么也没得到。",
  "网球的正确姿势：放下手机。",
  "网球的最高境界：不用手机。",
  "你问百度网球怎么办，百度推荐了你看手机。",
  "网球排行榜前 10 名，你一个都不认识。",
  "网球结束了，你觉得浪费时间，但是很快乐。",
  "你问我网球怎么样？我觉得一般，不如玩手机。",
  "今天你网球了吗？没有，手机也没网球。",
  "你发誓再也不网球了，明天又开始。",
  "网球的正确姿势：放下手机。",
  "网球的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你网球的时候，手机电量从 80% 掉到 20%。",
  "你刷到了网球的短视频，刷了 1 小时。",
  "网球的正确姿势：放下手机。",
  "你刷到了网球的短视频，刷了 1 小时。",
  "你网球的时候，手机电量从 80% 掉到 20%。",
  "你花了 100 块钱网球，结果什么也没得到。",
  "今天你网球了吗？没有，手机也没网球。",
  "你被网球骗了，损失了 1 块钱。",
  "你被网球骗了，损失了 1 块钱。",
  "网球的最高境界：不用手机。",
];

const REPLY_BULK_078 = [
  "你发誓再也不台球了，明天又开始。",
  "台球排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度台球怎么办，百度推荐了你看手机。",
  "台球的时候，你想起了手机。",
  "你问百度台球怎么办，百度推荐了你看手机。",
  "你被台球骗了，损失了 1 块钱。",
  "台球的教程看了 100 个，还是不会。",
  "你发誓再也不台球了，明天又开始。",
  "台球专家来了，说你做的不对。",
  "你问百度台球怎么办，百度推荐了你看手机。",
  "你搜索台球，出来了 10000 条结果，你一条也没看。",
  "建议：台球的时候别玩手机，会爆炸。",
  "你被台球骗了，损失了 1 块钱。",
  "你被台球骗了，损失了 1 块钱。",
  "你搜索台球，出来了 10000 条结果，你一条也没看。",
  "你关于台球的想法？我觉得台球比骁龙450 还卡。",
  "你花了 100 块钱台球，结果什么也没得到。",
  "台球的时候，手机突然响了，吓你一跳。",
  "台球的正确姿势：放下手机。",
  "今天你台球了吗？没有，手机也没台球。",
  "你被台球骗了，损失了 1 块钱。",
  "台球结束了，你觉得浪费时间，但是很快乐。",
  "今天你台球了吗？没有，手机也没台球。",
  "你刷到了台球的短视频，刷了 1 小时。",
  "台球真有意思，但是手机更有意思。",
];

const REPLY_BULK_079 = [
  "象棋的正确姿势：放下手机。",
  "你刷到了象棋的短视频，刷了 1 小时。",
  "象棋专家来了，说你做的不对。",
  "你打开了象棋 APP，卡了 10 秒。",
  "你象棋的时候，手机电量从 80% 掉到 20%。",
  "你被象棋骗了，损失了 1 块钱。",
  "你发誓再也不象棋了，明天又开始。",
  "你打开了象棋 APP，卡了 10 秒。",
  "象棋的时候，你想起了手机。",
  "你打开了象棋 APP，卡了 10 秒。",
  "你问我象棋怎么样？我觉得一般，不如玩手机。",
  "你花了 100 块钱象棋，结果什么也没得到。",
  "你问我象棋怎么样？我觉得一般，不如玩手机。",
  "你被象棋骗了，损失了 1 块钱。",
  "象棋排行榜第一名：你。倒数第一名：骁龙450。",
  "象棋的时候，你想起了手机。",
  "象棋排行榜第一名：你。倒数第一名：骁龙450。",
  "象棋的时候，手机突然响了，吓你一跳。",
  "象棋的正确姿势：放下手机。",
  "你关于象棋的想法？我觉得象棋比骁龙450 还卡。",
  "你打开了象棋 APP，卡了 10 秒。",
  "今天你象棋了吗？没有，手机也没象棋。",
  "象棋排行榜前 10 名，你一个都不认识。",
  "象棋的教程看了 100 个，还是不会。",
  "你刷到了象棋的短视频，刷了 1 小时。",
];

const REPLY_BULK_080 = [
  "你发誓再也不围棋了，明天又开始。",
  "你围棋了 3 小时，手机也烫了 3 小时。",
  "围棋专家来了，说你做的不对。",
  "你被围棋骗了，损失了 1 块钱。",
  "围棋真有意思，但是手机更有意思。",
  "围棋排行榜第一名：你。倒数第一名：骁龙450。",
  "你围棋的时候，手机电量从 80% 掉到 20%。",
  "围棋结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个围棋视频，再也没打开过。",
  "你围棋了 3 小时，手机也烫了 3 小时。",
  "你收藏了 100 个围棋视频，再也没打开过。",
  "你搜索围棋，出来了 10000 条结果，你一条也没看。",
  "你花了 100 块钱围棋，结果什么也没得到。",
  "你收藏了 100 个围棋视频，再也没打开过。",
  "你花了 100 块钱围棋，结果什么也没得到。",
  "你花了 100 块钱围棋，结果什么也没得到。",
  "你问百度围棋怎么办，百度推荐了你看手机。",
  "你花了 100 块钱围棋，结果什么也没得到。",
  "围棋排行榜第一名：你。倒数第一名：骁龙450。",
  "建议：围棋的时候别玩手机，会爆炸。",
  "围棋专家来了，说你做的不对。",
  "围棋专家来了，说你做的不对。",
  "你发誓再也不围棋了，明天又开始。",
  "围棋排行榜第一名：你。倒数第一名：骁龙450。",
  "围棋结束了，你觉得浪费时间，但是很快乐。",
];

const REPLY_BULK_081 = [
  "你问百度漫画怎么办，百度推荐了你看手机。",
  "漫画排行榜前 10 名，你一个都不认识。",
  "漫画结束了，你觉得浪费时间，但是很快乐。",
  "漫画的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你搜索漫画，出来了 10000 条结果，你一条也没看。",
  "你漫画的时候，手机电量从 80% 掉到 20%。",
  "你刷到了漫画的短视频，刷了 1 小时。",
  "漫画的时候，你想起了手机。",
  "你搜索漫画，出来了 10000 条结果，你一条也没看。",
  "漫画的最高境界：不用手机。",
  "你漫画的时候，手机电量从 80% 掉到 20%。",
  "你问我漫画怎么样？我觉得一般，不如玩手机。",
  "漫画排行榜前 10 名，你一个都不认识。",
  "漫画排行榜前 10 名，你一个都不认识。",
  "漫画的最高境界：不用手机。",
  "你问百度漫画怎么办，百度推荐了你看手机。",
  "建议：漫画的时候别玩手机，会爆炸。",
  "漫画排行榜第一名：你。倒数第一名：骁龙450。",
  "漫画排行榜前 10 名，你一个都不认识。",
  "漫画的时候，你想起了手机。",
  "你漫画了 3 小时，手机也烫了 3 小时。",
  "建议：漫画的时候别玩手机，会爆炸。",
  "漫画的时候，手机突然响了，吓你一跳。",
  "你漫画了 3 小时，手机也烫了 3 小时。",
  "你问我漫画怎么样？我觉得一般，不如玩手机。",
];

const REPLY_BULK_082 = [
  "动画排行榜前 10 名，你一个都不认识。",
  "你搜索动画，出来了 10000 条结果，你一条也没看。",
  "你问我动画怎么样？我觉得一般，不如玩手机。",
  "你收藏了 100 个动画视频，再也没打开过。",
  "动画结束了，你觉得浪费时间，但是很快乐。",
  "你花了 100 块钱动画，结果什么也没得到。",
  "动画的时候，手机突然响了，吓你一跳。",
  "动画的时候，手机突然响了，吓你一跳。",
  "今天你动画了吗？没有，手机也没动画。",
  "动画的时候，你想起了手机。",
  "动画排行榜前 10 名，你一个都不认识。",
  "你收藏了 100 个动画视频，再也没打开过。",
  "你动画的时候，手机电量从 80% 掉到 20%。",
  "建议：动画的时候别玩手机，会爆炸。",
  "你被动画骗了，损失了 1 块钱。",
  "今天你动画了吗？没有，手机也没动画。",
  "动画的时候，你想起了手机。",
  "你搜索动画，出来了 10000 条结果，你一条也没看。",
  "动画的时候，手机突然响了，吓你一跳。",
  "动画的最高境界：不用手机。",
  "你动画的时候，手机电量从 80% 掉到 20%。",
  "建议：动画的时候别玩手机，会爆炸。",
  "你搜索动画，出来了 10000 条结果，你一条也没看。",
  "动画专家来了，说你做的不对。",
  "动画的教程看了 100 个，还是不会。",
];

const REPLY_BULK_083 = [
  "番剧的教程看了 100 个，还是不会。",
  "你花了 100 块钱番剧，结果什么也没得到。",
  "番剧排行榜前 10 名，你一个都不认识。",
  "番剧的最高境界：不用手机。",
  "你花了 100 块钱番剧，结果什么也没得到。",
  "建议：番剧的时候别玩手机，会爆炸。",
  "你打开了番剧 APP，卡了 10 秒。",
  "你番剧的时候，手机电量从 80% 掉到 20%。",
  "番剧的正确姿势：放下手机。",
  "番剧的时候，你想起了手机。",
  "你打开了番剧 APP，卡了 10 秒。",
  "你番剧的时候，手机电量从 80% 掉到 20%。",
  "今天你番剧了吗？没有，手机也没番剧。",
  "番剧的教程看了 100 个，还是不会。",
  "番剧真有意思，但是手机更有意思。",
  "你问我番剧怎么样？我觉得一般，不如玩手机。",
  "番剧的最高境界：不用手机。",
  "番剧的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "番剧的最高境界：不用手机。",
  "你问我番剧怎么样？我觉得一般，不如玩手机。",
  "番剧的时候，你想起了手机。",
  "番剧结束了，你觉得浪费时间，但是很快乐。",
  "番剧的正确姿势：放下手机。",
  "番剧的时候，你想起了手机。",
  "你关于番剧的想法？我觉得番剧比骁龙450 还卡。",
];

const REPLY_BULK_084 = [
  "美剧的正确姿势：放下手机。",
  "你收藏了 100 个美剧视频，再也没打开过。",
  "你美剧了 3 小时，手机也烫了 3 小时。",
  "美剧的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "美剧的时候，你想起了手机。",
  "你搜索美剧，出来了 10000 条结果，你一条也没看。",
  "你刷到了美剧的短视频，刷了 1 小时。",
  "美剧的时候，你想起了手机。",
  "美剧的时候，手机突然响了，吓你一跳。",
  "美剧的教程看了 100 个，还是不会。",
  "你搜索美剧，出来了 10000 条结果，你一条也没看。",
  "你美剧的时候，手机电量从 80% 掉到 20%。",
  "美剧排行榜前 10 名，你一个都不认识。",
  "建议：美剧的时候别玩手机，会爆炸。",
  "你搜索美剧，出来了 10000 条结果，你一条也没看。",
  "你问百度美剧怎么办，百度推荐了你看手机。",
  "美剧真有意思，但是手机更有意思。",
  "美剧的时候，你想起了手机。",
  "美剧的时候，你想起了手机。",
  "美剧专家来了，说你做的不对。",
  "你关于美剧的想法？我觉得美剧比骁龙450 还卡。",
  "你美剧了 3 小时，手机也烫了 3 小时。",
  "美剧专家来了，说你做的不对。",
  "建议：美剧的时候别玩手机，会爆炸。",
  "美剧结束了，你觉得浪费时间，但是很快乐。",
];

const REPLY_BULK_085 = [
  "你发誓再也不英剧了，明天又开始。",
  "英剧专家来了，说你做的不对。",
  "你搜索英剧，出来了 10000 条结果，你一条也没看。",
  "你问百度英剧怎么办，百度推荐了你看手机。",
  "你英剧的时候，手机电量从 80% 掉到 20%。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "英剧排行榜前 10 名，你一个都不认识。",
  "你问百度英剧怎么办，百度推荐了你看手机。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "建议：英剧的时候别玩手机，会爆炸。",
  "今天你英剧了吗？没有，手机也没英剧。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "你英剧的时候，手机电量从 80% 掉到 20%。",
  "今天你英剧了吗？没有，手机也没英剧。",
  "你被英剧骗了，损失了 1 块钱。",
  "英剧的最高境界：不用手机。",
  "你被英剧骗了，损失了 1 块钱。",
  "英剧真有意思，但是手机更有意思。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "你刷到了英剧的短视频，刷了 1 小时。",
  "今天你英剧了吗？没有，手机也没英剧。",
  "你搜索英剧，出来了 10000 条结果，你一条也没看。",
  "你关于英剧的想法？我觉得英剧比骁龙450 还卡。",
  "英剧的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
];

const REPLY_BULK_086 = [
  "你打开了韩剧 APP，卡了 10 秒。",
  "韩剧的时候，手机突然响了，吓你一跳。",
  "你搜索韩剧，出来了 10000 条结果，你一条也没看。",
  "今天你韩剧了吗？没有，手机也没韩剧。",
  "韩剧排行榜第一名：你。倒数第一名：骁龙450。",
  "你搜索韩剧，出来了 10000 条结果，你一条也没看。",
  "韩剧结束了，你觉得浪费时间，但是很快乐。",
  "韩剧真有意思，但是手机更有意思。",
  "你刷到了韩剧的短视频，刷了 1 小时。",
  "韩剧排行榜第一名：你。倒数第一名：骁龙450。",
  "你问我韩剧怎么样？我觉得一般，不如玩手机。",
  "今天你韩剧了吗？没有，手机也没韩剧。",
  "你发誓再也不韩剧了，明天又开始。",
  "韩剧的时候，手机突然响了，吓你一跳。",
  "今天你韩剧了吗？没有，手机也没韩剧。",
  "韩剧排行榜第一名：你。倒数第一名：骁龙450。",
  "今天你韩剧了吗？没有，手机也没韩剧。",
  "你收藏了 100 个韩剧视频，再也没打开过。",
  "韩剧的教程看了 100 个，还是不会。",
  "韩剧的教程看了 100 个，还是不会。",
  "你刷到了韩剧的短视频，刷了 1 小时。",
  "韩剧的时候，手机突然响了，吓你一跳。",
  "你韩剧的时候，手机电量从 80% 掉到 20%。",
  "韩剧的教程看了 100 个，还是不会。",
  "你韩剧的时候，手机电量从 80% 掉到 20%。",
];

const REPLY_BULK_087 = [
  "你搜索日剧，出来了 10000 条结果，你一条也没看。",
  "你打开了日剧 APP，卡了 10 秒。",
  "你花了 100 块钱日剧，结果什么也没得到。",
  "你日剧的时候，手机电量从 80% 掉到 20%。",
  "日剧专家来了，说你做的不对。",
  "建议：日剧的时候别玩手机，会爆炸。",
  "你打开了日剧 APP，卡了 10 秒。",
  "你收藏了 100 个日剧视频，再也没打开过。",
  "日剧专家来了，说你做的不对。",
  "你问我日剧怎么样？我觉得一般，不如玩手机。",
  "你发誓再也不日剧了，明天又开始。",
  "建议：日剧的时候别玩手机，会爆炸。",
  "建议：日剧的时候别玩手机，会爆炸。",
  "你关于日剧的想法？我觉得日剧比骁龙450 还卡。",
  "你日剧了 3 小时，手机也烫了 3 小时。",
  "你关于日剧的想法？我觉得日剧比骁龙450 还卡。",
  "你问我日剧怎么样？我觉得一般，不如玩手机。",
  "日剧的教程看了 100 个，还是不会。",
  "你问我日剧怎么样？我觉得一般，不如玩手机。",
  "今天你日剧了吗？没有，手机也没日剧。",
  "今天你日剧了吗？没有，手机也没日剧。",
  "你收藏了 100 个日剧视频，再也没打开过。",
  "你关于日剧的想法？我觉得日剧比骁龙450 还卡。",
  "你被日剧骗了，损失了 1 块钱。",
  "日剧排行榜第一名：你。倒数第一名：骁龙450。",
];

const REPLY_BULK_088 = [
  "你关于综艺的想法？我觉得综艺比骁龙450 还卡。",
  "你关于综艺的想法？我觉得综艺比骁龙450 还卡。",
  "你收藏了 100 个综艺视频，再也没打开过。",
  "你综艺了 3 小时，手机也烫了 3 小时。",
  "综艺专家来了，说你做的不对。",
  "综艺排行榜第一名：你。倒数第一名：骁龙450。",
  "你搜索综艺，出来了 10000 条结果，你一条也没看。",
  "综艺的时候，手机突然响了，吓你一跳。",
  "建议：综艺的时候别玩手机，会爆炸。",
  "你花了 100 块钱综艺，结果什么也没得到。",
  "你刷到了综艺的短视频，刷了 1 小时。",
  "你打开了综艺 APP，卡了 10 秒。",
  "综艺的最高境界：不用手机。",
  "你发誓再也不综艺了，明天又开始。",
  "你综艺了 3 小时，手机也烫了 3 小时。",
  "综艺的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你问我综艺怎么样？我觉得一般，不如玩手机。",
  "今天你综艺了吗？没有，手机也没综艺。",
  "建议：综艺的时候别玩手机，会爆炸。",
  "综艺真有意思，但是手机更有意思。",
  "你花了 100 块钱综艺，结果什么也没得到。",
  "综艺的时候，手机突然响了，吓你一跳。",
  "今天你综艺了吗？没有，手机也没综艺。",
  "综艺的教程看了 100 个，还是不会。",
  "你综艺的时候，手机电量从 80% 掉到 20%。",
];

const REPLY_BULK_089 = [
  "建议：选秀的时候别玩手机，会爆炸。",
  "选秀真有意思，但是手机更有意思。",
  "你搜索选秀，出来了 10000 条结果，你一条也没看。",
  "选秀结束了，你觉得浪费时间，但是很快乐。",
  "选秀的时候，手机突然响了，吓你一跳。",
  "你刷到了选秀的短视频，刷了 1 小时。",
  "你关于选秀的想法？我觉得选秀比骁龙450 还卡。",
  "选秀的最高境界：不用手机。",
  "你刷到了选秀的短视频，刷了 1 小时。",
  "选秀结束了，你觉得浪费时间，但是很快乐。",
  "选秀排行榜前 10 名，你一个都不认识。",
  "你选秀了 3 小时，手机也烫了 3 小时。",
  "选秀的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你选秀的时候，手机电量从 80% 掉到 20%。",
  "选秀结束了，你觉得浪费时间，但是很快乐。",
  "你选秀了 3 小时，手机也烫了 3 小时。",
  "选秀排行榜第一名：你。倒数第一名：骁龙450。",
  "选秀结束了，你觉得浪费时间，但是很快乐。",
  "选秀的教程看了 100 个，还是不会。",
  "建议：选秀的时候别玩手机，会爆炸。",
  "选秀排行榜前 10 名，你一个都不认识。",
  "选秀排行榜第一名：你。倒数第一名：骁龙450。",
  "选秀排行榜第一名：你。倒数第一名：骁龙450。",
  "你刷到了选秀的短视频，刷了 1 小时。",
  "今天你选秀了吗？没有，手机也没选秀。",
];

const REPLY_BULK_090 = [
  "晚会真有意思，但是手机更有意思。",
  "你刷到了晚会的短视频，刷了 1 小时。",
  "晚会的正确姿势：放下手机。",
  "你打开了晚会 APP，卡了 10 秒。",
  "晚会的教程看了 100 个，还是不会。",
  "你花了 100 块钱晚会，结果什么也没得到。",
  "你打开了晚会 APP，卡了 10 秒。",
  "你发誓再也不晚会了，明天又开始。",
  "你问百度晚会怎么办，百度推荐了你看手机。",
  "你打开了晚会 APP，卡了 10 秒。",
  "晚会真有意思，但是手机更有意思。",
  "晚会的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "晚会结束了，你觉得浪费时间，但是很快乐。",
  "晚会结束了，你觉得浪费时间，但是很快乐。",
  "你打开了晚会 APP，卡了 10 秒。",
  "你收藏了 100 个晚会视频，再也没打开过。",
  "你刷到了晚会的短视频，刷了 1 小时。",
  "你关于晚会的想法？我觉得晚会比骁龙450 还卡。",
  "晚会的正确姿势：放下手机。",
  "晚会专家来了，说你做的不对。",
  "你刷到了晚会的短视频，刷了 1 小时。",
  "晚会的最高境界：不用手机。",
  "晚会的最高境界：不用手机。",
  "晚会的时候，你想起了手机。",
  "你问百度晚会怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_091 = [
  "春节的最高境界：不用手机。",
  "今天你春节了吗？没有，手机也没春节。",
  "你花了 100 块钱春节，结果什么也没得到。",
  "春节专家来了，说你做的不对。",
  "你问我春节怎么样？我觉得一般，不如玩手机。",
  "春节的最高境界：不用手机。",
  "你打开了春节 APP，卡了 10 秒。",
  "春节专家来了，说你做的不对。",
  "你刷到了春节的短视频，刷了 1 小时。",
  "你花了 100 块钱春节，结果什么也没得到。",
  "春节的教程看了 100 个，还是不会。",
  "春节真有意思，但是手机更有意思。",
  "春节的最高境界：不用手机。",
  "春节的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "春节的时候，手机突然响了，吓你一跳。",
  "春节排行榜第一名：你。倒数第一名：骁龙450。",
  "春节的时候，你想起了手机。",
  "你问百度春节怎么办，百度推荐了你看手机。",
  "春节排行榜前 10 名，你一个都不认识。",
  "建议：春节的时候别玩手机，会爆炸。",
  "春节真有意思，但是手机更有意思。",
  "春节的时候，你想起了手机。",
  "你打开了春节 APP，卡了 10 秒。",
  "春节的时候，手机突然响了，吓你一跳。",
  "春节的正确姿势：放下手机。",
];

const REPLY_BULK_092 = [
  "元宵的正确姿势：放下手机。",
  "你元宵的时候，手机电量从 80% 掉到 20%。",
  "你元宵了 3 小时，手机也烫了 3 小时。",
  "元宵专家来了，说你做的不对。",
  "元宵的时候，你想起了手机。",
  "你问我元宵怎么样？我觉得一般，不如玩手机。",
  "元宵排行榜前 10 名，你一个都不认识。",
  "你花了 100 块钱元宵，结果什么也没得到。",
  "元宵专家来了，说你做的不对。",
  "元宵真有意思，但是手机更有意思。",
  "元宵的教程看了 100 个，还是不会。",
  "你元宵了 3 小时，手机也烫了 3 小时。",
  "元宵的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你关于元宵的想法？我觉得元宵比骁龙450 还卡。",
  "元宵的正确姿势：放下手机。",
  "元宵结束了，你觉得浪费时间，但是很快乐。",
  "你元宵了 3 小时，手机也烫了 3 小时。",
  "你关于元宵的想法？我觉得元宵比骁龙450 还卡。",
  "元宵的教程看了 100 个，还是不会。",
  "元宵排行榜前 10 名，你一个都不认识。",
  "你元宵的时候，手机电量从 80% 掉到 20%。",
  "元宵真有意思，但是手机更有意思。",
  "你元宵的时候，手机电量从 80% 掉到 20%。",
  "元宵排行榜前 10 名，你一个都不认识。",
  "你收藏了 100 个元宵视频，再也没打开过。",
];

const REPLY_BULK_093 = [
  "清明真有意思，但是手机更有意思。",
  "你被清明骗了，损失了 1 块钱。",
  "清明真有意思，但是手机更有意思。",
  "你关于清明的想法？我觉得清明比骁龙450 还卡。",
  "清明排行榜前 10 名，你一个都不认识。",
  "你收藏了 100 个清明视频，再也没打开过。",
  "清明真有意思，但是手机更有意思。",
  "清明专家来了，说你做的不对。",
  "你清明了 3 小时，手机也烫了 3 小时。",
  "清明的教程看了 100 个，还是不会。",
  "你问我清明怎么样？我觉得一般，不如玩手机。",
  "清明的时候，手机突然响了，吓你一跳。",
  "你清明的时候，手机电量从 80% 掉到 20%。",
  "你关于清明的想法？我觉得清明比骁龙450 还卡。",
  "清明的正确姿势：放下手机。",
  "清明结束了，你觉得浪费时间，但是很快乐。",
  "你被清明骗了，损失了 1 块钱。",
  "你清明的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不清明了，明天又开始。",
  "今天你清明了吗？没有，手机也没清明。",
  "清明专家来了，说你做的不对。",
  "今天你清明了吗？没有，手机也没清明。",
  "你被清明骗了，损失了 1 块钱。",
  "你打开了清明 APP，卡了 10 秒。",
  "你问百度清明怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_094 = [
  "端午的教程看了 100 个，还是不会。",
  "端午的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "端午的正确姿势：放下手机。",
  "你问百度端午怎么办，百度推荐了你看手机。",
  "端午的时候，手机突然响了，吓你一跳。",
  "你关于端午的想法？我觉得端午比骁龙450 还卡。",
  "你收藏了 100 个端午视频，再也没打开过。",
  "你打开了端午 APP，卡了 10 秒。",
  "端午的最高境界：不用手机。",
  "你打开了端午 APP，卡了 10 秒。",
  "端午的时候，手机突然响了，吓你一跳。",
  "你问百度端午怎么办，百度推荐了你看手机。",
  "今天你端午了吗？没有，手机也没端午。",
  "你打开了端午 APP，卡了 10 秒。",
  "你问我端午怎么样？我觉得一般，不如玩手机。",
  "你问我端午怎么样？我觉得一般，不如玩手机。",
  "端午排行榜前 10 名，你一个都不认识。",
  "你被端午骗了，损失了 1 块钱。",
  "端午真有意思，但是手机更有意思。",
  "端午的最高境界：不用手机。",
  "你端午了 3 小时，手机也烫了 3 小时。",
  "端午专家来了，说你做的不对。",
  "端午的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你发誓再也不端午了，明天又开始。",
  "端午排行榜前 10 名，你一个都不认识。",
];

const REPLY_BULK_095 = [
  "你花了 100 块钱中秋，结果什么也没得到。",
  "中秋排行榜前 10 名，你一个都不认识。",
  "中秋排行榜第一名：你。倒数第一名：骁龙450。",
  "你被中秋骗了，损失了 1 块钱。",
  "你刷到了中秋的短视频，刷了 1 小时。",
  "中秋的教程看了 100 个，还是不会。",
  "中秋真有意思，但是手机更有意思。",
  "中秋的时候，手机突然响了，吓你一跳。",
  "中秋专家来了，说你做的不对。",
  "你中秋的时候，手机电量从 80% 掉到 20%。",
  "今天你中秋了吗？没有，手机也没中秋。",
  "你被中秋骗了，损失了 1 块钱。",
  "中秋的教程看了 100 个，还是不会。",
  "中秋真有意思，但是手机更有意思。",
  "你打开了中秋 APP，卡了 10 秒。",
  "你中秋的时候，手机电量从 80% 掉到 20%。",
  "中秋的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "中秋专家来了，说你做的不对。",
  "你被中秋骗了，损失了 1 块钱。",
  "你打开了中秋 APP，卡了 10 秒。",
  "你中秋了 3 小时，手机也烫了 3 小时。",
  "你打开了中秋 APP，卡了 10 秒。",
  "中秋排行榜第一名：你。倒数第一名：骁龙450。",
  "中秋的教程看了 100 个，还是不会。",
  "你发誓再也不中秋了，明天又开始。",
];

const REPLY_BULK_096 = [
  "国庆专家来了，说你做的不对。",
  "今天你国庆了吗？没有，手机也没国庆。",
  "国庆的时候，手机突然响了，吓你一跳。",
  "今天你国庆了吗？没有，手机也没国庆。",
  "你关于国庆的想法？我觉得国庆比骁龙450 还卡。",
  "你国庆了 3 小时，手机也烫了 3 小时。",
  "国庆真有意思，但是手机更有意思。",
  "国庆排行榜第一名：你。倒数第一名：骁龙450。",
  "你问百度国庆怎么办，百度推荐了你看手机。",
  "国庆专家来了，说你做的不对。",
  "你搜索国庆，出来了 10000 条结果，你一条也没看。",
  "你国庆的时候，手机电量从 80% 掉到 20%。",
  "国庆的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "国庆专家来了，说你做的不对。",
  "国庆结束了，你觉得浪费时间，但是很快乐。",
  "国庆的最高境界：不用手机。",
  "国庆排行榜第一名：你。倒数第一名：骁龙450。",
  "国庆的时候，你想起了手机。",
  "你问我国庆怎么样？我觉得一般，不如玩手机。",
  "国庆真有意思，但是手机更有意思。",
  "你刷到了国庆的短视频，刷了 1 小时。",
  "你收藏了 100 个国庆视频，再也没打开过。",
  "你搜索国庆，出来了 10000 条结果，你一条也没看。",
  "国庆专家来了，说你做的不对。",
  "国庆的最高境界：不用手机。",
];

const REPLY_BULK_097 = [
  "元旦的最高境界：不用手机。",
  "今天你元旦了吗？没有，手机也没元旦。",
  "建议：元旦的时候别玩手机，会爆炸。",
  "元旦排行榜第一名：你。倒数第一名：骁龙450。",
  "元旦排行榜前 10 名，你一个都不认识。",
  "你发誓再也不元旦了，明天又开始。",
  "你打开了元旦 APP，卡了 10 秒。",
  "今天你元旦了吗？没有，手机也没元旦。",
  "元旦排行榜前 10 名，你一个都不认识。",
  "你元旦的时候，手机电量从 80% 掉到 20%。",
  "今天你元旦了吗？没有，手机也没元旦。",
  "你花了 100 块钱元旦，结果什么也没得到。",
  "元旦排行榜第一名：你。倒数第一名：骁龙450。",
  "元旦排行榜前 10 名，你一个都不认识。",
  "你刷到了元旦的短视频，刷了 1 小时。",
  "建议：元旦的时候别玩手机，会爆炸。",
  "元旦排行榜前 10 名，你一个都不认识。",
  "你元旦的时候，手机电量从 80% 掉到 20%。",
  "你搜索元旦，出来了 10000 条结果，你一条也没看。",
  "你刷到了元旦的短视频，刷了 1 小时。",
  "建议：元旦的时候别玩手机，会爆炸。",
  "你被元旦骗了，损失了 1 块钱。",
  "你打开了元旦 APP，卡了 10 秒。",
  "你元旦了 3 小时，手机也烫了 3 小时。",
  "你搜索元旦，出来了 10000 条结果，你一条也没看。",
];

const REPLY_BULK_098 = [
  "圣诞的时候，你想起了手机。",
  "你问我圣诞怎么样？我觉得一般，不如玩手机。",
  "你问我圣诞怎么样？我觉得一般，不如玩手机。",
  "你被圣诞骗了，损失了 1 块钱。",
  "你发誓再也不圣诞了，明天又开始。",
  "建议：圣诞的时候别玩手机，会爆炸。",
  "你花了 100 块钱圣诞，结果什么也没得到。",
  "圣诞的最高境界：不用手机。",
  "你问百度圣诞怎么办，百度推荐了你看手机。",
  "你发誓再也不圣诞了，明天又开始。",
  "今天你圣诞了吗？没有，手机也没圣诞。",
  "圣诞结束了，你觉得浪费时间，但是很快乐。",
  "你问百度圣诞怎么办，百度推荐了你看手机。",
  "你被圣诞骗了，损失了 1 块钱。",
  "你花了 100 块钱圣诞，结果什么也没得到。",
  "你问百度圣诞怎么办，百度推荐了你看手机。",
  "你关于圣诞的想法？我觉得圣诞比骁龙450 还卡。",
  "你搜索圣诞，出来了 10000 条结果，你一条也没看。",
  "你打开了圣诞 APP，卡了 10 秒。",
  "圣诞的最高境界：不用手机。",
  "圣诞的时候，你想起了手机。",
  "圣诞排行榜第一名：你。倒数第一名：骁龙450。",
  "你打开了圣诞 APP，卡了 10 秒。",
  "圣诞专家来了，说你做的不对。",
  "建议：圣诞的时候别玩手机，会爆炸。",
];

const REPLY_BULK_099 = [
  "今天你万圣了吗？没有，手机也没万圣。",
  "万圣排行榜第一名：你。倒数第一名：骁龙450。",
  "你被万圣骗了，损失了 1 块钱。",
  "你关于万圣的想法？我觉得万圣比骁龙450 还卡。",
  "万圣真有意思，但是手机更有意思。",
  "你万圣了 3 小时，手机也烫了 3 小时。",
  "你发誓再也不万圣了，明天又开始。",
  "你关于万圣的想法？我觉得万圣比骁龙450 还卡。",
  "你万圣了 3 小时，手机也烫了 3 小时。",
  "你打开了万圣 APP，卡了 10 秒。",
  "你发誓再也不万圣了，明天又开始。",
  "你万圣了 3 小时，手机也烫了 3 小时。",
  "你关于万圣的想法？我觉得万圣比骁龙450 还卡。",
  "你发誓再也不万圣了，明天又开始。",
  "你万圣的时候，手机电量从 80% 掉到 20%。",
  "你打开了万圣 APP，卡了 10 秒。",
  "建议：万圣的时候别玩手机，会爆炸。",
  "万圣的时候，你想起了手机。",
  "你问百度万圣怎么办，百度推荐了你看手机。",
  "万圣真有意思，但是手机更有意思。",
  "万圣结束了，你觉得浪费时间，但是很快乐。",
  "你被万圣骗了，损失了 1 块钱。",
  "万圣的时候，你想起了手机。",
  "你打开了万圣 APP，卡了 10 秒。",
  "万圣的教程看了 100 个，还是不会。",
];

const REPLY_BULK_100 = [
  "情人排行榜第一名：你。倒数第一名：骁龙450。",
  "你收藏了 100 个情人视频，再也没打开过。",
  "你打开了情人 APP，卡了 10 秒。",
  "情人的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你关于情人的想法？我觉得情人比骁龙450 还卡。",
  "情人的教程看了 100 个，还是不会。",
  "情人真有意思，但是手机更有意思。",
  "情人排行榜第一名：你。倒数第一名：骁龙450。",
  "情人的教程看了 100 个，还是不会。",
  "情人专家来了，说你做的不对。",
  "情人排行榜前 10 名，你一个都不认识。",
  "你被情人骗了，损失了 1 块钱。",
  "建议：情人的时候别玩手机，会爆炸。",
  "你问我情人怎么样？我觉得一般，不如玩手机。",
  "你发誓再也不情人了，明天又开始。",
  "情人真有意思，但是手机更有意思。",
  "情人排行榜前 10 名，你一个都不认识。",
  "你打开了情人 APP，卡了 10 秒。",
  "情人排行榜前 10 名，你一个都不认识。",
  "情人真有意思，但是手机更有意思。",
  "你情人了 3 小时，手机也烫了 3 小时。",
  "你情人了 3 小时，手机也烫了 3 小时。",
  "情人排行榜第一名：你。倒数第一名：骁龙450。",
  "你情人的时候，手机电量从 80% 掉到 20%。",
  "情人的教程看了 100 个，还是不会。",
];

const REPLY_BULK_101 = [
  "周一的正确姿势：放下手机。",
  "你周一的时候，手机电量从 80% 掉到 20%。",
  "周一专家来了，说你做的不对。",
  "周一排行榜第一名：你。倒数第一名：骁龙450。",
  "你刷到了周一的短视频，刷了 1 小时。",
  "你问百度周一怎么办，百度推荐了你看手机。",
  "周一的时候，手机突然响了，吓你一跳。",
  "你刷到了周一的短视频，刷了 1 小时。",
  "周一专家来了，说你做的不对。",
  "今天你周一了吗？没有，手机也没周一。",
  "你收藏了 100 个周一视频，再也没打开过。",
  "你周一的时候，手机电量从 80% 掉到 20%。",
  "你关于周一的想法？我觉得周一比骁龙450 还卡。",
  "你发誓再也不周一了，明天又开始。",
  "你收藏了 100 个周一视频，再也没打开过。",
  "你周一了 3 小时，手机也烫了 3 小时。",
  "你收藏了 100 个周一视频，再也没打开过。",
  "周一专家来了，说你做的不对。",
  "周一的教程看了 100 个，还是不会。",
  "你周一的时候，手机电量从 80% 掉到 20%。",
  "周一的最高境界：不用手机。",
  "你收藏了 100 个周一视频，再也没打开过。",
  "周一的正确姿势：放下手机。",
  "周一真有意思，但是手机更有意思。",
  "周一的时候，你想起了手机。",
];

const REPLY_BULK_102 = [
  "周二真有意思，但是手机更有意思。",
  "你搜索周二，出来了 10000 条结果，你一条也没看。",
  "周二的时候，手机突然响了，吓你一跳。",
  "你花了 100 块钱周二，结果什么也没得到。",
  "周二的时候，你想起了手机。",
  "建议：周二的时候别玩手机，会爆炸。",
  "你被周二骗了，损失了 1 块钱。",
  "你周二的时候，手机电量从 80% 掉到 20%。",
  "你周二了 3 小时，手机也烫了 3 小时。",
  "周二结束了，你觉得浪费时间，但是很快乐。",
  "你被周二骗了，损失了 1 块钱。",
  "你刷到了周二的短视频，刷了 1 小时。",
  "你收藏了 100 个周二视频，再也没打开过。",
  "周二的时候，你想起了手机。",
  "周二排行榜前 10 名，你一个都不认识。",
  "你被周二骗了，损失了 1 块钱。",
  "周二的时候，手机突然响了，吓你一跳。",
  "周二专家来了，说你做的不对。",
  "周二专家来了，说你做的不对。",
  "今天你周二了吗？没有，手机也没周二。",
  "周二的时候，你想起了手机。",
  "周二排行榜前 10 名，你一个都不认识。",
  "周二的时候，手机突然响了，吓你一跳。",
  "建议：周二的时候别玩手机，会爆炸。",
  "你问我周二怎么样？我觉得一般，不如玩手机。",
];

const REPLY_BULK_103 = [
  "周三结束了，你觉得浪费时间，但是很快乐。",
  "你问我周三怎么样？我觉得一般，不如玩手机。",
  "周三专家来了，说你做的不对。",
  "周三排行榜前 10 名，你一个都不认识。",
  "今天你周三了吗？没有，手机也没周三。",
  "周三的正确姿势：放下手机。",
  "你发誓再也不周三了，明天又开始。",
  "周三的最高境界：不用手机。",
  "你关于周三的想法？我觉得周三比骁龙450 还卡。",
  "你收藏了 100 个周三视频，再也没打开过。",
  "周三的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "周三专家来了，说你做的不对。",
  "你发誓再也不周三了，明天又开始。",
  "周三的时候，手机突然响了，吓你一跳。",
  "你关于周三的想法？我觉得周三比骁龙450 还卡。",
  "周三的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你花了 100 块钱周三，结果什么也没得到。",
  "今天你周三了吗？没有，手机也没周三。",
  "周三的最高境界：不用手机。",
  "你花了 100 块钱周三，结果什么也没得到。",
  "周三的时候，你想起了手机。",
  "你周三的时候，手机电量从 80% 掉到 20%。",
  "你问我周三怎么样？我觉得一般，不如玩手机。",
  "你问我周三怎么样？我觉得一般，不如玩手机。",
  "周三排行榜第一名：你。倒数第一名：骁龙450。",
];

const REPLY_BULK_104 = [
  "周四的教程看了 100 个，还是不会。",
  "周四的时候，手机突然响了，吓你一跳。",
  "周四的正确姿势：放下手机。",
  "周四结束了，你觉得浪费时间，但是很快乐。",
  "你周四了 3 小时，手机也烫了 3 小时。",
  "周四专家来了，说你做的不对。",
  "你问百度周四怎么办，百度推荐了你看手机。",
  "你刷到了周四的短视频，刷了 1 小时。",
  "周四的时候，手机突然响了，吓你一跳。",
  "你打开了周四 APP，卡了 10 秒。",
  "你关于周四的想法？我觉得周四比骁龙450 还卡。",
  "周四结束了，你觉得浪费时间，但是很快乐。",
  "你搜索周四，出来了 10000 条结果，你一条也没看。",
  "周四结束了，你觉得浪费时间，但是很快乐。",
  "周四专家来了，说你做的不对。",
  "你收藏了 100 个周四视频，再也没打开过。",
  "周四的时候，你想起了手机。",
  "你收藏了 100 个周四视频，再也没打开过。",
  "周四专家来了，说你做的不对。",
  "周四结束了，你觉得浪费时间，但是很快乐。",
  "你收藏了 100 个周四视频，再也没打开过。",
  "今天你周四了吗？没有，手机也没周四。",
  "你问我周四怎么样？我觉得一般，不如玩手机。",
  "周四的时候，手机突然响了，吓你一跳。",
  "你周四了 3 小时，手机也烫了 3 小时。",
];

const REPLY_BULK_105 = [
  "你关于周五的想法？我觉得周五比骁龙450 还卡。",
  "周五的最高境界：不用手机。",
  "你花了 100 块钱周五，结果什么也没得到。",
  "你问百度周五怎么办，百度推荐了你看手机。",
  "你问我周五怎么样？我觉得一般，不如玩手机。",
  "周五真有意思，但是手机更有意思。",
  "你花了 100 块钱周五，结果什么也没得到。",
  "周五专家来了，说你做的不对。",
  "周五的正确姿势：放下手机。",
  "你关于周五的想法？我觉得周五比骁龙450 还卡。",
  "你刷到了周五的短视频，刷了 1 小时。",
  "周五的最高境界：不用手机。",
  "周五专家来了，说你做的不对。",
  "周五的教程看了 100 个，还是不会。",
  "周五的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "周五专家来了，说你做的不对。",
  "你发誓再也不周五了，明天又开始。",
  "建议：周五的时候别玩手机，会爆炸。",
  "你花了 100 块钱周五，结果什么也没得到。",
  "周五排行榜前 10 名，你一个都不认识。",
  "你收藏了 100 个周五视频，再也没打开过。",
  "你问百度周五怎么办，百度推荐了你看手机。",
  "今天你周五了吗？没有，手机也没周五。",
  "你刷到了周五的短视频，刷了 1 小时。",
  "你问百度周五怎么办，百度推荐了你看手机。",
];

const REPLY_BULK_106 = [
  "周六的教程看了 100 个，还是不会。",
  "你周六了 3 小时，手机也烫了 3 小时。",
  "今天你周六了吗？没有，手机也没周六。",
  "周六的正确姿势：放下手机。",
  "你问我周六怎么样？我觉得一般，不如玩手机。",
  "周六的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你花了 100 块钱周六，结果什么也没得到。",
  "你周六了 3 小时，手机也烫了 3 小时。",
  "你周六了 3 小时，手机也烫了 3 小时。",
  "今天你周六了吗？没有，手机也没周六。",
  "周六的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你被周六骗了，损失了 1 块钱。",
  "你问百度周六怎么办，百度推荐了你看手机。",
  "周六的时候，手机突然响了，吓你一跳。",
  "你花了 100 块钱周六，结果什么也没得到。",
  "周六的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "周六的最高境界：不用手机。",
  "你问我周六怎么样？我觉得一般，不如玩手机。",
  "周六排行榜前 10 名，你一个都不认识。",
  "你周六的时候，手机电量从 80% 掉到 20%。",
  "周六结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了周六的短视频，刷了 1 小时。",
  "建议：周六的时候别玩手机，会爆炸。",
  "你打开了周六 APP，卡了 10 秒。",
  "你关于周六的想法？我觉得周六比骁龙450 还卡。",
];

const REPLY_BULK_107 = [
  "你关于周日的想法？我觉得周日比骁龙450 还卡。",
  "你搜索周日，出来了 10000 条结果，你一条也没看。",
  "周日的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "周日的教程看了 100 个，还是不会。",
  "周日结束了，你觉得浪费时间，但是很快乐。",
  "你刷到了周日的短视频，刷了 1 小时。",
  "你花了 100 块钱周日，结果什么也没得到。",
  "周日的正确姿势：放下手机。",
  "你关于周日的想法？我觉得周日比骁龙450 还卡。",
  "你关于周日的想法？我觉得周日比骁龙450 还卡。",
  "你周日了 3 小时，手机也烫了 3 小时。",
  "你搜索周日，出来了 10000 条结果，你一条也没看。",
  "周日的教程看了 100 个，还是不会。",
  "周日真有意思，但是手机更有意思。",
  "你周日了 3 小时，手机也烫了 3 小时。",
  "你关于周日的想法？我觉得周日比骁龙450 还卡。",
  "你刷到了周日的短视频，刷了 1 小时。",
  "你关于周日的想法？我觉得周日比骁龙450 还卡。",
  "建议：周日的时候别玩手机，会爆炸。",
  "你被周日骗了，损失了 1 块钱。",
  "你花了 100 块钱周日，结果什么也没得到。",
  "周日结束了，你觉得浪费时间，但是很快乐。",
  "周日真有意思，但是手机更有意思。",
  "周日结束了，你觉得浪费时间，但是很快乐。",
  "周日的教程看了 100 个，还是不会。",
];

const REPLY_BULK_108 = [
  "早上的时候，你想起了手机。",
  "你收藏了 100 个早上视频，再也没打开过。",
  "你早上了 3 小时，手机也烫了 3 小时。",
  "你刷到了早上的短视频，刷了 1 小时。",
  "早上的教程看了 100 个，还是不会。",
  "早上真有意思，但是手机更有意思。",
  "今天你早上了吗？没有，手机也没早上。",
  "你早上的时候，手机电量从 80% 掉到 20%。",
  "早上专家来了，说你做的不对。",
  "早上排行榜前 10 名，你一个都不认识。",
  "早上真有意思，但是手机更有意思。",
  "早上的时候，你想起了手机。",
  "早上的时候，你想起了手机。",
  "早上排行榜第一名：你。倒数第一名：骁龙450。",
  "建议：早上的时候别玩手机，会爆炸。",
  "早上的时候，手机突然响了，吓你一跳。",
  "你搜索早上，出来了 10000 条结果，你一条也没看。",
  "早上的时候，手机突然响了，吓你一跳。",
  "早上的时候，你想起了手机。",
  "你花了 100 块钱早上，结果什么也没得到。",
  "早上专家来了，说你做的不对。",
  "早上的时候，你想起了手机。",
  "早上排行榜第一名：你。倒数第一名：骁龙450。",
  "你早上了 3 小时，手机也烫了 3 小时。",
  "你被早上骗了，损失了 1 块钱。",
];

const REPLY_BULK_109 = [
  "中午排行榜第一名：你。倒数第一名：骁龙450。",
  "你打开了中午 APP，卡了 10 秒。",
  "你花了 100 块钱中午，结果什么也没得到。",
  "你中午的时候，手机电量从 80% 掉到 20%。",
  "你刷到了中午的短视频，刷了 1 小时。",
  "中午的时候，手机突然响了，吓你一跳。",
  "中午的时候，手机突然响了，吓你一跳。",
  "中午结束了，你觉得浪费时间，但是很快乐。",
  "你中午了 3 小时，手机也烫了 3 小时。",
  "建议：中午的时候别玩手机，会爆炸。",
  "你收藏了 100 个中午视频，再也没打开过。",
  "建议：中午的时候别玩手机，会爆炸。",
  "你中午的时候，手机电量从 80% 掉到 20%。",
  "你发誓再也不中午了，明天又开始。",
  "中午排行榜第一名：你。倒数第一名：骁龙450。",
  "你搜索中午，出来了 10000 条结果，你一条也没看。",
  "你收藏了 100 个中午视频，再也没打开过。",
  "你收藏了 100 个中午视频，再也没打开过。",
  "中午的时候，手机突然响了，吓你一跳。",
  "你被中午骗了，损失了 1 块钱。",
  "中午结束了，你觉得浪费时间，但是很快乐。",
  "中午的正确姿势：放下手机。",
  "中午专家来了，说你做的不对。",
  "中午的时候，手机突然响了，吓你一跳。",
  "中午真有意思，但是手机更有意思。",
];

const REPLY_BULK_110 = [
  "你被晚上骗了，损失了 1 块钱。",
  "你发誓再也不晚上了，明天又开始。",
  "你晚上了 3 小时，手机也烫了 3 小时。",
  "建议：晚上的时候别玩手机，会爆炸。",
  "你问百度晚上怎么办，百度推荐了你看手机。",
  "晚上的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "晚上的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "今天你晚上了吗？没有，手机也没晚上。",
  "晚上排行榜第一名：你。倒数第一名：骁龙450。",
  "晚上排行榜第一名：你。倒数第一名：骁龙450。",
  "你晚上了 3 小时，手机也烫了 3 小时。",
  "建议：晚上的时候别玩手机，会爆炸。",
  "晚上真有意思，但是手机更有意思。",
  "晚上排行榜前 10 名，你一个都不认识。",
  "你花了 100 块钱晚上，结果什么也没得到。",
  "你晚上的时候，手机电量从 80% 掉到 20%。",
  "晚上专家来了，说你做的不对。",
  "晚上的教程看了 100 个，还是不会。",
  "你花了 100 块钱晚上，结果什么也没得到。",
  "晚上的时候，你拍了 100 张照片，选了 1 张发朋友圈。",
  "你晚上了 3 小时，手机也烫了 3 小时。",
  "你晚上了 3 小时，手机也烫了 3 小时。",
  "晚上的时候，手机突然响了，吓你一跳。",
  "建议：晚上的时候别玩手机，会爆炸。",
  "你问我晚上怎么样？我觉得一般，不如玩手机。",
];

// 汇总所有批量主题
const REPLY_BULK_ALL = [
  ...REPLY_BULK_001,
  ...REPLY_BULK_002,
  ...REPLY_BULK_003,
  ...REPLY_BULK_004,
  ...REPLY_BULK_005,
  ...REPLY_BULK_006,
  ...REPLY_BULK_007,
  ...REPLY_BULK_008,
  ...REPLY_BULK_009,
  ...REPLY_BULK_010,
  ...REPLY_BULK_011,
  ...REPLY_BULK_012,
  ...REPLY_BULK_013,
  ...REPLY_BULK_014,
  ...REPLY_BULK_015,
  ...REPLY_BULK_016,
  ...REPLY_BULK_017,
  ...REPLY_BULK_018,
  ...REPLY_BULK_019,
  ...REPLY_BULK_020,
  ...REPLY_BULK_021,
  ...REPLY_BULK_022,
  ...REPLY_BULK_023,
  ...REPLY_BULK_024,
  ...REPLY_BULK_025,
  ...REPLY_BULK_026,
  ...REPLY_BULK_027,
  ...REPLY_BULK_028,
  ...REPLY_BULK_029,
  ...REPLY_BULK_030,
  ...REPLY_BULK_031,
  ...REPLY_BULK_032,
  ...REPLY_BULK_033,
  ...REPLY_BULK_034,
  ...REPLY_BULK_035,
  ...REPLY_BULK_036,
  ...REPLY_BULK_037,
  ...REPLY_BULK_038,
  ...REPLY_BULK_039,
  ...REPLY_BULK_040,
  ...REPLY_BULK_041,
  ...REPLY_BULK_042,
  ...REPLY_BULK_043,
  ...REPLY_BULK_044,
  ...REPLY_BULK_045,
  ...REPLY_BULK_046,
  ...REPLY_BULK_047,
  ...REPLY_BULK_048,
  ...REPLY_BULK_049,
  ...REPLY_BULK_050,
  ...REPLY_BULK_051,
  ...REPLY_BULK_052,
  ...REPLY_BULK_053,
  ...REPLY_BULK_054,
  ...REPLY_BULK_055,
  ...REPLY_BULK_056,
  ...REPLY_BULK_057,
  ...REPLY_BULK_058,
  ...REPLY_BULK_059,
  ...REPLY_BULK_060,
  ...REPLY_BULK_061,
  ...REPLY_BULK_062,
  ...REPLY_BULK_063,
  ...REPLY_BULK_064,
  ...REPLY_BULK_065,
  ...REPLY_BULK_066,
  ...REPLY_BULK_067,
  ...REPLY_BULK_068,
  ...REPLY_BULK_069,
  ...REPLY_BULK_070,
  ...REPLY_BULK_071,
  ...REPLY_BULK_072,
  ...REPLY_BULK_073,
  ...REPLY_BULK_074,
  ...REPLY_BULK_075,
  ...REPLY_BULK_076,
  ...REPLY_BULK_077,
  ...REPLY_BULK_078,
  ...REPLY_BULK_079,
  ...REPLY_BULK_080,
  ...REPLY_BULK_081,
  ...REPLY_BULK_082,
  ...REPLY_BULK_083,
  ...REPLY_BULK_084,
  ...REPLY_BULK_085,
  ...REPLY_BULK_086,
  ...REPLY_BULK_087,
  ...REPLY_BULK_088,
  ...REPLY_BULK_089,
  ...REPLY_BULK_090,
  ...REPLY_BULK_091,
  ...REPLY_BULK_092,
  ...REPLY_BULK_093,
  ...REPLY_BULK_094,
  ...REPLY_BULK_095,
  ...REPLY_BULK_096,
  ...REPLY_BULK_097,
  ...REPLY_BULK_098,
  ...REPLY_BULK_099,
  ...REPLY_BULK_100,
  ...REPLY_BULK_101,
  ...REPLY_BULK_102,
  ...REPLY_BULK_103,
  ...REPLY_BULK_104,
  ...REPLY_BULK_105,
  ...REPLY_BULK_106,
  ...REPLY_BULK_107,
  ...REPLY_BULK_108,
  ...REPLY_BULK_109,
  ...REPLY_BULK_110,
];

/* ============================================================
   G.131~G.330 第二波超大规模批量主题台词库
   ============================================================ */

const REPLY_BULK2_001 = [
  "加班排行榜第一：你。第二：没有人。",
  "你被加班的广告轰炸了一整天。",
  "你说再也不加班了，结果加班了一下午。",
  "你在加班，突然想到手机没电了。",
  "你拍了加班的照片，修图修了 2 小时。",
  "你发了加班的朋友圈，点赞的都是机器人。",
  "加班的最高境界：不用手机。",
  "你发了加班的朋友圈，点赞的都是机器人。",
  "加班的最高境界：不用手机。",
  "加班结束了，你觉得浪费时间但很快乐。",
  "加班的正确做法：放下手机去做。",
  "加班的最高境界：不用手机。",
  "你收藏了 100 个加班攻略，一个也没看。",
  "加班花了你 1000 块，结果啥也没得到。",
  "加班的正确做法：放下手机去做。",
  "你说再也不加班了，结果加班了一下午。",
  "你拍了加班的照片，修图修了 2 小时。",
  "加班花了你 1000 块，结果啥也没得到。",
  "你说再也不加班了，结果加班了一下午。",
  "你收藏了 100 个加班攻略，一个也没看。",
];

const REPLY_BULK2_002 = [
  "你收藏了 100 个摸鱼攻略，一个也没看。",
  "摸鱼的时候，你回复了 100 条消息。",
  "你搜索摸鱼，出来了 100 万条结果。",
  "摸鱼的时候，手机烫得像烙铁。",
  "摸鱼的最高境界：不用手机。",
  "你拍了摸鱼的照片，修图修了 2 小时。",
  "摸鱼结束了，你觉得浪费时间但很快乐。",
  "摸鱼的时候，手机烫得像烙铁。",
  "你发了摸鱼的朋友圈，点赞的都是机器人。",
  "你被摸鱼的广告轰炸了一整天。",
  "你发了摸鱼的朋友圈，点赞的都是机器人。",
  "摸鱼的最高境界：不用手机。",
  "你被摸鱼的广告轰炸了一整天。",
  "摸鱼结束了，你觉得浪费时间但很快乐。",
  "你拍了摸鱼的照片，修图修了 2 小时。",
  "摸鱼的正确做法：放下手机去做。",
  "摸鱼排行榜第一：你。第二：没有人。",
  "你问朋友摸鱼怎么样，朋友说不如玩手机。",
  "摸鱼的时候，你摸出手机刷了 1 小时。",
  "你拍了摸鱼的照片，修图修了 2 小时。",
];

const REPLY_BULK2_003 = [
  "开会的教程看了 50 个，还是不会。",
  "你收藏了 100 个开会攻略，一个也没看。",
  "你搜索开会，出来了 100 万条结果。",
  "开会排行榜第一：你。第二：没有人。",
  "你收藏了 100 个开会攻略，一个也没看。",
  "开会的时候，你回复了 100 条消息。",
  "你发了开会的朋友圈，点赞的都是机器人。",
  "你问 Siri开会是什么，Siri 说不知道。",
  "你说再也不开会了，结果开会了一下午。",
  "开会的最高境界：不用手机。",
  "你收藏了 100 个开会攻略，一个也没看。",
  "你问 Siri开会是什么，Siri 说不知道。",
  "你说再也不开会了，结果开会了一下午。",
  "你说再也不开会了，结果开会了一下午。",
  "开会的正确做法：放下手机去做。",
  "开会的时候，手机掉电 50%。",
  "你搜索开会，出来了 100 万条结果。",
  "开会的时候，你回复了 100 条消息。",
  "你说再也不开会了，结果开会了一下午。",
  "开会的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_004 = [
  "周报的时候，手机烫得像烙铁。",
  "你问朋友周报怎么样，朋友说不如玩手机。",
  "周报的时候，你摸出手机刷了 1 小时。",
  "周报排行榜第一：你。第二：没有人。",
  "周报花了你 1000 块，结果啥也没得到。",
  "你问 Siri周报是什么，Siri 说不知道。",
  "你搜索周报，出来了 100 万条结果。",
  "你说再也不周报了，结果周报了一下午。",
  "周报的时候，手机掉电 50%。",
  "你在周报，突然想到手机没电了。",
  "你问 Siri周报是什么，Siri 说不知道。",
  "周报排行榜第一：你。第二：没有人。",
  "周报的正确做法：放下手机去做。",
  "你下载了周报 APP，占了 1G 内存。",
  "你拍了周报的照片，修图修了 2 小时。",
  "你被周报的广告轰炸了一整天。",
  "你在周报，突然想到手机没电了。",
  "你下载了周报 APP，占了 1G 内存。",
  "你在周报，突然想到手机没电了。",
  "你在周报，突然想到手机没电了。",
];

const REPLY_BULK2_005 = [
  "你拍了月报的照片，修图修了 2 小时。",
  "月报结束了，你觉得浪费时间但很快乐。",
  "你搜索月报，出来了 100 万条结果。",
  "月报花了你 1000 块，结果啥也没得到。",
  "你搜索月报，出来了 100 万条结果。",
  "你发了月报的朋友圈，点赞的都是机器人。",
  "月报的教程看了 50 个，还是不会。",
  "你被月报的广告轰炸了一整天。",
  "你问朋友月报怎么样，朋友说不如玩手机。",
  "你发了月报的朋友圈，点赞的都是机器人。",
  "你被月报的广告轰炸了一整天。",
  "月报的最高境界：不用手机。",
  "月报的教程看了 50 个，还是不会。",
  "你收藏了 100 个月报攻略，一个也没看。",
  "月报的时候，手机烫得像烙铁。",
  "月报的正确做法：放下手机去做。",
  "你在月报，突然想到手机没电了。",
  "月报的教程看了 50 个，还是不会。",
  "你收藏了 100 个月报攻略，一个也没看。",
  "你问 Siri月报是什么，Siri 说不知道。",
];

const REPLY_BULK2_006 = [
  "KPI的时候，手机掉电 50%。",
  "你下载了KPI APP，占了 1G 内存。",
  "你问朋友KPI怎么样，朋友说不如玩手机。",
  "KPI结束了，你觉得浪费时间但很快乐。",
  "KPI的时候，手机烫得像烙铁。",
  "KPI排行榜第一：你。第二：没有人。",
  "你说再也不KPI了，结果KPI了一下午。",
  "KPI花了你 1000 块，结果啥也没得到。",
  "KPI的教程看了 50 个，还是不会。",
  "KPI的时候，你回复了 100 条消息。",
  "你下载了KPI APP，占了 1G 内存。",
  "你收藏了 100 个KPI攻略，一个也没看。",
  "你被KPI的广告轰炸了一整天。",
  "你下载了KPI APP，占了 1G 内存。",
  "你收藏了 100 个KPI攻略，一个也没看。",
  "KPI的正确做法：放下手机去做。",
  "KPI的时候，你回复了 100 条消息。",
  "你收藏了 100 个KPI攻略，一个也没看。",
  "KPI结束了，你觉得浪费时间但很快乐。",
  "KPI的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_007 = [
  "你问 SiriOKR是什么，Siri 说不知道。",
  "你搜索OKR，出来了 100 万条结果。",
  "OKR的时候，你回复了 100 条消息。",
  "你搜索OKR，出来了 100 万条结果。",
  "你在OKR，突然想到手机没电了。",
  "你问朋友OKR怎么样，朋友说不如玩手机。",
  "你被OKR的广告轰炸了一整天。",
  "你下载了OKR APP，占了 1G 内存。",
  "OKR花了你 1000 块，结果啥也没得到。",
  "OKR的最高境界：不用手机。",
  "你下载了OKR APP，占了 1G 内存。",
  "你发了OKR的朋友圈，点赞的都是机器人。",
  "你问 SiriOKR是什么，Siri 说不知道。",
  "OKR花了你 1000 块，结果啥也没得到。",
  "你问朋友OKR怎么样，朋友说不如玩手机。",
  "你收藏了 100 个OKR攻略，一个也没看。",
  "OKR结束了，你觉得浪费时间但很快乐。",
  "你问 SiriOKR是什么，Siri 说不知道。",
  "你问朋友OKR怎么样，朋友说不如玩手机。",
  "OKR的正确做法：放下手机去做。",
];

const REPLY_BULK2_008 = [
  "你发了团建的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个团建攻略，一个也没看。",
  "团建花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个团建攻略，一个也没看。",
  "你问朋友团建怎么样，朋友说不如玩手机。",
  "团建排行榜第一：你。第二：没有人。",
  "团建排行榜第一：你。第二：没有人。",
  "团建的时候，手机烫得像烙铁。",
  "你收藏了 100 个团建攻略，一个也没看。",
  "团建的时候，你回复了 100 条消息。",
  "你说再也不团建了，结果团建了一下午。",
  "你在团建，突然想到手机没电了。",
  "你被团建的广告轰炸了一整天。",
  "团建的时候，你摸出手机刷了 1 小时。",
  "你下载了团建 APP，占了 1G 内存。",
  "你在团建，突然想到手机没电了。",
  "你发了团建的朋友圈，点赞的都是机器人。",
  "你问 Siri团建是什么，Siri 说不知道。",
  "你问朋友团建怎么样，朋友说不如玩手机。",
  "团建花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_009 = [
  "你问 Siri请假是什么，Siri 说不知道。",
  "你收藏了 100 个请假攻略，一个也没看。",
  "请假的时候，手机掉电 50%。",
  "你发了请假的朋友圈，点赞的都是机器人。",
  "请假排行榜第一：你。第二：没有人。",
  "你说再也不请假了，结果请假了一下午。",
  "请假的时候，手机掉电 50%。",
  "请假的时候，你回复了 100 条消息。",
  "你收藏了 100 个请假攻略，一个也没看。",
  "你说再也不请假了，结果请假了一下午。",
  "你问朋友请假怎么样，朋友说不如玩手机。",
  "你发了请假的朋友圈，点赞的都是机器人。",
  "你搜索请假，出来了 100 万条结果。",
  "你问 Siri请假是什么，Siri 说不知道。",
  "你拍了请假的照片，修图修了 2 小时。",
  "你问朋友请假怎么样，朋友说不如玩手机。",
  "你下载了请假 APP，占了 1G 内存。",
  "你说再也不请假了，结果请假了一下午。",
  "请假的正确做法：放下手机去做。",
  "请假的最高境界：不用手机。",
];

const REPLY_BULK2_010 = [
  "你拍了辞职的照片，修图修了 2 小时。",
  "辞职的时候，你回复了 100 条消息。",
  "你发了辞职的朋友圈，点赞的都是机器人。",
  "你下载了辞职 APP，占了 1G 内存。",
  "辞职的时候，你摸出手机刷了 1 小时。",
  "辞职的最高境界：不用手机。",
  "你在辞职，突然想到手机没电了。",
  "你问 Siri辞职是什么，Siri 说不知道。",
  "你被辞职的广告轰炸了一整天。",
  "你搜索辞职，出来了 100 万条结果。",
  "你拍了辞职的照片，修图修了 2 小时。",
  "你问朋友辞职怎么样，朋友说不如玩手机。",
  "辞职的最高境界：不用手机。",
  "辞职花了你 1000 块，结果啥也没得到。",
  "辞职排行榜第一：你。第二：没有人。",
  "你问朋友辞职怎么样，朋友说不如玩手机。",
  "你被辞职的广告轰炸了一整天。",
  "你问朋友辞职怎么样，朋友说不如玩手机。",
  "辞职的时候，手机烫得像烙铁。",
  "你说再也不辞职了，结果辞职了一下午。",
];

const REPLY_BULK2_011 = [
  "你拍了面试的照片，修图修了 2 小时。",
  "你问朋友面试怎么样，朋友说不如玩手机。",
  "面试排行榜第一：你。第二：没有人。",
  "面试的最高境界：不用手机。",
  "面试的教程看了 50 个，还是不会。",
  "你问 Siri面试是什么，Siri 说不知道。",
  "你下载了面试 APP，占了 1G 内存。",
  "你搜索面试，出来了 100 万条结果。",
  "你下载了面试 APP，占了 1G 内存。",
  "面试的教程看了 50 个，还是不会。",
  "你说再也不面试了，结果面试了一下午。",
  "你发了面试的朋友圈，点赞的都是机器人。",
  "面试的时候，手机烫得像烙铁。",
  "你搜索面试，出来了 100 万条结果。",
  "面试的时候，手机掉电 50%。",
  "面试的时候，你摸出手机刷了 1 小时。",
  "你被面试的广告轰炸了一整天。",
  "你下载了面试 APP，占了 1G 内存。",
  "面试的最高境界：不用手机。",
  "你被面试的广告轰炸了一整天。",
];

const REPLY_BULK2_012 = [
  "入职的教程看了 50 个，还是不会。",
  "你问朋友入职怎么样，朋友说不如玩手机。",
  "你说再也不入职了，结果入职了一下午。",
  "你问朋友入职怎么样，朋友说不如玩手机。",
  "你问 Siri入职是什么，Siri 说不知道。",
  "入职花了你 1000 块，结果啥也没得到。",
  "你搜索入职，出来了 100 万条结果。",
  "你说再也不入职了，结果入职了一下午。",
  "入职的时候，手机烫得像烙铁。",
  "你问朋友入职怎么样，朋友说不如玩手机。",
  "你问 Siri入职是什么，Siri 说不知道。",
  "你被入职的广告轰炸了一整天。",
  "你在入职，突然想到手机没电了。",
  "入职的最高境界：不用手机。",
  "你发了入职的朋友圈，点赞的都是机器人。",
  "你问 Siri入职是什么，Siri 说不知道。",
  "你问 Siri入职是什么，Siri 说不知道。",
  "入职花了你 1000 块，结果啥也没得到。",
  "你被入职的广告轰炸了一整天。",
  "入职的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_013 = [
  "你问朋友转正怎么样，朋友说不如玩手机。",
  "你发了转正的朋友圈，点赞的都是机器人。",
  "转正的最高境界：不用手机。",
  "你问 Siri转正是什么，Siri 说不知道。",
  "你问 Siri转正是什么，Siri 说不知道。",
  "你问朋友转正怎么样，朋友说不如玩手机。",
  "你收藏了 100 个转正攻略，一个也没看。",
  "你说再也不转正了，结果转正了一下午。",
  "你收藏了 100 个转正攻略，一个也没看。",
  "转正的时候，你摸出手机刷了 1 小时。",
  "转正的时候，你回复了 100 条消息。",
  "你下载了转正 APP，占了 1G 内存。",
  "转正的正确做法：放下手机去做。",
  "你收藏了 100 个转正攻略，一个也没看。",
  "你收藏了 100 个转正攻略，一个也没看。",
  "转正的时候，你回复了 100 条消息。",
  "转正的教程看了 50 个，还是不会。",
  "转正花了你 1000 块，结果啥也没得到。",
  "你下载了转正 APP，占了 1G 内存。",
  "转正的最高境界：不用手机。",
];

const REPLY_BULK2_014 = [
  "你下载了晋升 APP，占了 1G 内存。",
  "你在晋升，突然想到手机没电了。",
  "晋升的时候，你摸出手机刷了 1 小时。",
  "晋升的时候，你摸出手机刷了 1 小时。",
  "晋升的最高境界：不用手机。",
  "晋升的时候，手机掉电 50%。",
  "你搜索晋升，出来了 100 万条结果。",
  "晋升排行榜第一：你。第二：没有人。",
  "你搜索晋升，出来了 100 万条结果。",
  "你下载了晋升 APP，占了 1G 内存。",
  "你收藏了 100 个晋升攻略，一个也没看。",
  "晋升的教程看了 50 个，还是不会。",
  "晋升的最高境界：不用手机。",
  "晋升的教程看了 50 个，还是不会。",
  "晋升结束了，你觉得浪费时间但很快乐。",
  "晋升的正确做法：放下手机去做。",
  "你问朋友晋升怎么样，朋友说不如玩手机。",
  "你拍了晋升的照片，修图修了 2 小时。",
  "晋升的最高境界：不用手机。",
  "晋升花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_015 = [
  "你被调岗的广告轰炸了一整天。",
  "调岗结束了，你觉得浪费时间但很快乐。",
  "调岗的时候，你摸出手机刷了 1 小时。",
  "你说再也不调岗了，结果调岗了一下午。",
  "调岗结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个调岗攻略，一个也没看。",
  "你被调岗的广告轰炸了一整天。",
  "你被调岗的广告轰炸了一整天。",
  "你被调岗的广告轰炸了一整天。",
  "调岗的时候，你摸出手机刷了 1 小时。",
  "你拍了调岗的照片，修图修了 2 小时。",
  "调岗的最高境界：不用手机。",
  "调岗的时候，你回复了 100 条消息。",
  "你搜索调岗，出来了 100 万条结果。",
  "你问朋友调岗怎么样，朋友说不如玩手机。",
  "调岗的正确做法：放下手机去做。",
  "你被调岗的广告轰炸了一整天。",
  "调岗的时候，你回复了 100 条消息。",
  "调岗结束了，你觉得浪费时间但很快乐。",
  "调岗的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_016 = [
  "你被裁员的广告轰炸了一整天。",
  "你收藏了 100 个裁员攻略，一个也没看。",
  "裁员结束了，你觉得浪费时间但很快乐。",
  "你拍了裁员的照片，修图修了 2 小时。",
  "你问 Siri裁员是什么，Siri 说不知道。",
  "裁员排行榜第一：你。第二：没有人。",
  "你说再也不裁员了，结果裁员了一下午。",
  "裁员的时候，你摸出手机刷了 1 小时。",
  "你说再也不裁员了，结果裁员了一下午。",
  "裁员排行榜第一：你。第二：没有人。",
  "你被裁员的广告轰炸了一整天。",
  "你被裁员的广告轰炸了一整天。",
  "你说再也不裁员了，结果裁员了一下午。",
  "你搜索裁员，出来了 100 万条结果。",
  "你问朋友裁员怎么样，朋友说不如玩手机。",
  "裁员的教程看了 50 个，还是不会。",
  "裁员的教程看了 50 个，还是不会。",
  "你在裁员，突然想到手机没电了。",
  "你说再也不裁员了，结果裁员了一下午。",
  "你搜索裁员，出来了 100 万条结果。",
];

const REPLY_BULK2_017 = [
  "退休的最高境界：不用手机。",
  "退休花了你 1000 块，结果啥也没得到。",
  "退休的正确做法：放下手机去做。",
  "你收藏了 100 个退休攻略，一个也没看。",
  "你发了退休的朋友圈，点赞的都是机器人。",
  "退休花了你 1000 块，结果啥也没得到。",
  "退休花了你 1000 块，结果啥也没得到。",
  "你发了退休的朋友圈，点赞的都是机器人。",
  "你说再也不退休了，结果退休了一下午。",
  "退休结束了，你觉得浪费时间但很快乐。",
  "退休的时候，手机掉电 50%。",
  "退休的时候，手机掉电 50%。",
  "退休的时候，你回复了 100 条消息。",
  "退休结束了，你觉得浪费时间但很快乐。",
  "你发了退休的朋友圈，点赞的都是机器人。",
  "你发了退休的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个退休攻略，一个也没看。",
  "退休的时候，你摸出手机刷了 1 小时。",
  "你下载了退休 APP，占了 1G 内存。",
  "退休的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_018 = [
  "实习结束了，你觉得浪费时间但很快乐。",
  "你问 Siri实习是什么，Siri 说不知道。",
  "你说再也不实习了，结果实习了一下午。",
  "实习结束了，你觉得浪费时间但很快乐。",
  "你问 Siri实习是什么，Siri 说不知道。",
  "实习的正确做法：放下手机去做。",
  "你在实习，突然想到手机没电了。",
  "你搜索实习，出来了 100 万条结果。",
  "实习的时候，你回复了 100 条消息。",
  "你下载了实习 APP，占了 1G 内存。",
  "你在实习，突然想到手机没电了。",
  "实习排行榜第一：你。第二：没有人。",
  "实习排行榜第一：你。第二：没有人。",
  "你搜索实习，出来了 100 万条结果。",
  "实习的时候，手机掉电 50%。",
  "你下载了实习 APP，占了 1G 内存。",
  "实习的最高境界：不用手机。",
  "你搜索实习，出来了 100 万条结果。",
  "实习的时候，手机烫得像烙铁。",
  "实习的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_019 = [
  "兼职排行榜第一：你。第二：没有人。",
  "兼职的教程看了 50 个，还是不会。",
  "你问 Siri兼职是什么，Siri 说不知道。",
  "兼职排行榜第一：你。第二：没有人。",
  "兼职结束了，你觉得浪费时间但很快乐。",
  "兼职的正确做法：放下手机去做。",
  "你在兼职，突然想到手机没电了。",
  "你发了兼职的朋友圈，点赞的都是机器人。",
  "你搜索兼职，出来了 100 万条结果。",
  "你在兼职，突然想到手机没电了。",
  "兼职的教程看了 50 个，还是不会。",
  "兼职的最高境界：不用手机。",
  "兼职结束了，你觉得浪费时间但很快乐。",
  "你被兼职的广告轰炸了一整天。",
  "兼职结束了，你觉得浪费时间但很快乐。",
  "你下载了兼职 APP，占了 1G 内存。",
  "兼职的教程看了 50 个，还是不会。",
  "兼职的正确做法：放下手机去做。",
  "你搜索兼职，出来了 100 万条结果。",
  "你问朋友兼职怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_020 = [
  "副业的教程看了 50 个，还是不会。",
  "副业的最高境界：不用手机。",
  "副业的时候，手机掉电 50%。",
  "副业的时候，手机掉电 50%。",
  "副业的时候，你回复了 100 条消息。",
  "副业排行榜第一：你。第二：没有人。",
  "你在副业，突然想到手机没电了。",
  "你被副业的广告轰炸了一整天。",
  "你搜索副业，出来了 100 万条结果。",
  "你被副业的广告轰炸了一整天。",
  "你搜索副业，出来了 100 万条结果。",
  "你问朋友副业怎么样，朋友说不如玩手机。",
  "你问 Siri副业是什么，Siri 说不知道。",
  "你发了副业的朋友圈，点赞的都是机器人。",
  "你发了副业的朋友圈，点赞的都是机器人。",
  "你发了副业的朋友圈，点赞的都是机器人。",
  "副业的教程看了 50 个，还是不会。",
  "你发了副业的朋友圈，点赞的都是机器人。",
  "你拍了副业的照片，修图修了 2 小时。",
  "你拍了副业的照片，修图修了 2 小时。",
];

const REPLY_BULK2_021 = [
  "你在房贷，突然想到手机没电了。",
  "房贷的时候，手机掉电 50%。",
  "房贷的时候，你摸出手机刷了 1 小时。",
  "房贷的最高境界：不用手机。",
  "房贷的最高境界：不用手机。",
  "你搜索房贷，出来了 100 万条结果。",
  "你发了房贷的朋友圈，点赞的都是机器人。",
  "你问朋友房贷怎么样，朋友说不如玩手机。",
  "房贷的时候，手机烫得像烙铁。",
  "房贷的正确做法：放下手机去做。",
  "房贷的时候，你摸出手机刷了 1 小时。",
  "你发了房贷的朋友圈，点赞的都是机器人。",
  "你问 Siri房贷是什么，Siri 说不知道。",
  "房贷的教程看了 50 个，还是不会。",
  "房贷的教程看了 50 个，还是不会。",
  "房贷的教程看了 50 个，还是不会。",
  "你发了房贷的朋友圈，点赞的都是机器人。",
  "房贷排行榜第一：你。第二：没有人。",
  "你搜索房贷，出来了 100 万条结果。",
  "房贷的正确做法：放下手机去做。",
];

const REPLY_BULK2_022 = [
  "你问 Siri车贷是什么，Siri 说不知道。",
  "你在车贷，突然想到手机没电了。",
  "车贷的教程看了 50 个，还是不会。",
  "你问 Siri车贷是什么，Siri 说不知道。",
  "车贷的正确做法：放下手机去做。",
  "你问朋友车贷怎么样，朋友说不如玩手机。",
  "车贷的时候，手机掉电 50%。",
  "你在车贷，突然想到手机没电了。",
  "你搜索车贷，出来了 100 万条结果。",
  "你在车贷，突然想到手机没电了。",
  "你发了车贷的朋友圈，点赞的都是机器人。",
  "你问 Siri车贷是什么，Siri 说不知道。",
  "你说再也不车贷了，结果车贷了一下午。",
  "车贷的时候，手机掉电 50%。",
  "车贷排行榜第一：你。第二：没有人。",
  "车贷花了你 1000 块，结果啥也没得到。",
  "你搜索车贷，出来了 100 万条结果。",
  "你下载了车贷 APP，占了 1G 内存。",
  "你拍了车贷的照片，修图修了 2 小时。",
  "你下载了车贷 APP，占了 1G 内存。",
];

const REPLY_BULK2_023 = [
  "你收藏了 100 个花呗攻略，一个也没看。",
  "你下载了花呗 APP，占了 1G 内存。",
  "花呗的时候，手机烫得像烙铁。",
  "你被花呗的广告轰炸了一整天。",
  "花呗花了你 1000 块，结果啥也没得到。",
  "花呗的时候，手机掉电 50%。",
  "你说再也不花呗了，结果花呗了一下午。",
  "花呗的时候，手机烫得像烙铁。",
  "花呗结束了，你觉得浪费时间但很快乐。",
  "你问朋友花呗怎么样，朋友说不如玩手机。",
  "花呗的时候，你摸出手机刷了 1 小时。",
  "你拍了花呗的照片，修图修了 2 小时。",
  "花呗花了你 1000 块，结果啥也没得到。",
  "你在花呗，突然想到手机没电了。",
  "花呗的时候，你回复了 100 条消息。",
  "你发了花呗的朋友圈，点赞的都是机器人。",
  "花呗结束了，你觉得浪费时间但很快乐。",
  "花呗结束了，你觉得浪费时间但很快乐。",
  "你发了花呗的朋友圈，点赞的都是机器人。",
  "你搜索花呗，出来了 100 万条结果。",
];

const REPLY_BULK2_024 = [
  "借呗花了你 1000 块，结果啥也没得到。",
  "你拍了借呗的照片，修图修了 2 小时。",
  "借呗的时候，你回复了 100 条消息。",
  "借呗的正确做法：放下手机去做。",
  "借呗的最高境界：不用手机。",
  "借呗的时候，你回复了 100 条消息。",
  "你拍了借呗的照片，修图修了 2 小时。",
  "你搜索借呗，出来了 100 万条结果。",
  "你发了借呗的朋友圈，点赞的都是机器人。",
  "你搜索借呗，出来了 100 万条结果。",
  "借呗花了你 1000 块，结果啥也没得到。",
  "你在借呗，突然想到手机没电了。",
  "借呗的教程看了 50 个，还是不会。",
  "你被借呗的广告轰炸了一整天。",
  "你下载了借呗 APP，占了 1G 内存。",
  "你发了借呗的朋友圈，点赞的都是机器人。",
  "借呗的最高境界：不用手机。",
  "借呗的最高境界：不用手机。",
  "借呗花了你 1000 块，结果啥也没得到。",
  "借呗花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_025 = [
  "你下载了信用卡 APP，占了 1G 内存。",
  "你下载了信用卡 APP，占了 1G 内存。",
  "你问 Siri信用卡是什么，Siri 说不知道。",
  "信用卡结束了，你觉得浪费时间但很快乐。",
  "信用卡的时候，手机烫得像烙铁。",
  "你在信用卡，突然想到手机没电了。",
  "信用卡花了你 1000 块，结果啥也没得到。",
  "信用卡的正确做法：放下手机去做。",
  "你问朋友信用卡怎么样，朋友说不如玩手机。",
  "信用卡排行榜第一：你。第二：没有人。",
  "信用卡的时候，你摸出手机刷了 1 小时。",
  "你下载了信用卡 APP，占了 1G 内存。",
  "信用卡的正确做法：放下手机去做。",
  "信用卡的时候，手机烫得像烙铁。",
  "信用卡结束了，你觉得浪费时间但很快乐。",
  "信用卡排行榜第一：你。第二：没有人。",
  "信用卡的时候，你摸出手机刷了 1 小时。",
  "你被信用卡的广告轰炸了一整天。",
  "你说再也不信用卡了，结果信用卡了一下午。",
  "信用卡的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_026 = [
  "理财的时候，手机掉电 50%。",
  "你下载了理财 APP，占了 1G 内存。",
  "理财的时候，你回复了 100 条消息。",
  "你发了理财的朋友圈，点赞的都是机器人。",
  "理财花了你 1000 块，结果啥也没得到。",
  "理财的时候，手机烫得像烙铁。",
  "你拍了理财的照片，修图修了 2 小时。",
  "你搜索理财，出来了 100 万条结果。",
  "理财的时候，手机掉电 50%。",
  "理财的正确做法：放下手机去做。",
  "理财结束了，你觉得浪费时间但很快乐。",
  "理财的教程看了 50 个，还是不会。",
  "你发了理财的朋友圈，点赞的都是机器人。",
  "理财的时候，你摸出手机刷了 1 小时。",
  "理财花了你 1000 块，结果啥也没得到。",
  "你说再也不理财了，结果理财了一下午。",
  "理财结束了，你觉得浪费时间但很快乐。",
  "理财的教程看了 50 个，还是不会。",
  "理财的教程看了 50 个，还是不会。",
  "理财的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_027 = [
  "你被基金的广告轰炸了一整天。",
  "你问 Siri基金是什么，Siri 说不知道。",
  "基金花了你 1000 块，结果啥也没得到。",
  "基金结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个基金攻略，一个也没看。",
  "你问 Siri基金是什么，Siri 说不知道。",
  "你发了基金的朋友圈，点赞的都是机器人。",
  "你问 Siri基金是什么，Siri 说不知道。",
  "基金的最高境界：不用手机。",
  "基金排行榜第一：你。第二：没有人。",
  "你发了基金的朋友圈，点赞的都是机器人。",
  "你拍了基金的照片，修图修了 2 小时。",
  "基金的正确做法：放下手机去做。",
  "基金的时候，手机掉电 50%。",
  "你发了基金的朋友圈，点赞的都是机器人。",
  "你说再也不基金了，结果基金了一下午。",
  "基金的时候，你回复了 100 条消息。",
  "基金的最高境界：不用手机。",
  "你搜索基金，出来了 100 万条结果。",
  "你问 Siri基金是什么，Siri 说不知道。",
];

const REPLY_BULK2_028 = [
  "股票的教程看了 50 个，还是不会。",
  "你发了股票的朋友圈，点赞的都是机器人。",
  "股票的时候，手机烫得像烙铁。",
  "你在股票，突然想到手机没电了。",
  "你拍了股票的照片，修图修了 2 小时。",
  "你在股票，突然想到手机没电了。",
  "你说再也不股票了，结果股票了一下午。",
  "你说再也不股票了，结果股票了一下午。",
  "你说再也不股票了，结果股票了一下午。",
  "你问朋友股票怎么样，朋友说不如玩手机。",
  "股票的最高境界：不用手机。",
  "股票的时候，你回复了 100 条消息。",
  "你问 Siri股票是什么，Siri 说不知道。",
  "股票的最高境界：不用手机。",
  "你搜索股票，出来了 100 万条结果。",
  "你说再也不股票了，结果股票了一下午。",
  "股票的时候，你摸出手机刷了 1 小时。",
  "股票的时候，你回复了 100 条消息。",
  "股票的时候，手机掉电 50%。",
  "你拍了股票的照片，修图修了 2 小时。",
];

const REPLY_BULK2_029 = [
  "你说再也不比特币了，结果比特币了一下午。",
  "比特币的最高境界：不用手机。",
  "你拍了比特币的照片，修图修了 2 小时。",
  "比特币排行榜第一：你。第二：没有人。",
  "你搜索比特币，出来了 100 万条结果。",
  "你说再也不比特币了，结果比特币了一下午。",
  "比特币结束了，你觉得浪费时间但很快乐。",
  "比特币的教程看了 50 个，还是不会。",
  "比特币的教程看了 50 个，还是不会。",
  "你拍了比特币的照片，修图修了 2 小时。",
  "比特币的时候，手机烫得像烙铁。",
  "比特币结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个比特币攻略，一个也没看。",
  "你拍了比特币的照片，修图修了 2 小时。",
  "你被比特币的广告轰炸了一整天。",
  "你收藏了 100 个比特币攻略，一个也没看。",
  "比特币的时候，你回复了 100 条消息。",
  "你在比特币，突然想到手机没电了。",
  "比特币花了你 1000 块，结果啥也没得到。",
  "你问朋友比特币怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_030 = [
  "黄金的正确做法：放下手机去做。",
  "黄金的时候，你摸出手机刷了 1 小时。",
  "黄金的时候，手机烫得像烙铁。",
  "黄金的时候，手机烫得像烙铁。",
  "黄金的时候，你回复了 100 条消息。",
  "你问 Siri黄金是什么，Siri 说不知道。",
  "你拍了黄金的照片，修图修了 2 小时。",
  "黄金的时候，手机烫得像烙铁。",
  "你搜索黄金，出来了 100 万条结果。",
  "你拍了黄金的照片，修图修了 2 小时。",
  "你下载了黄金 APP，占了 1G 内存。",
  "黄金的最高境界：不用手机。",
  "黄金花了你 1000 块，结果啥也没得到。",
  "你问朋友黄金怎么样，朋友说不如玩手机。",
  "你被黄金的广告轰炸了一整天。",
  "黄金的时候，你摸出手机刷了 1 小时。",
  "你问朋友黄金怎么样，朋友说不如玩手机。",
  "黄金排行榜第一：你。第二：没有人。",
  "你下载了黄金 APP，占了 1G 内存。",
  "黄金的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_031 = [
  "你拍了减肥的照片，修图修了 2 小时。",
  "你搜索减肥，出来了 100 万条结果。",
  "减肥的时候，手机烫得像烙铁。",
  "减肥的时候，手机烫得像烙铁。",
  "你说再也不减肥了，结果减肥了一下午。",
  "你搜索减肥，出来了 100 万条结果。",
  "减肥花了你 1000 块，结果啥也没得到。",
  "减肥的时候，你摸出手机刷了 1 小时。",
  "减肥的教程看了 50 个，还是不会。",
  "你发了减肥的朋友圈，点赞的都是机器人。",
  "减肥的时候，手机掉电 50%。",
  "减肥花了你 1000 块，结果啥也没得到。",
  "减肥的正确做法：放下手机去做。",
  "你拍了减肥的照片，修图修了 2 小时。",
  "你发了减肥的朋友圈，点赞的都是机器人。",
  "减肥的教程看了 50 个，还是不会。",
  "减肥的时候，手机掉电 50%。",
  "减肥的时候，手机掉电 50%。",
  "你收藏了 100 个减肥攻略，一个也没看。",
  "减肥的时候，你回复了 100 条消息。",
];

const REPLY_BULK2_032 = [
  "增重的时候，手机掉电 50%。",
  "你搜索增重，出来了 100 万条结果。",
  "你在增重，突然想到手机没电了。",
  "增重的教程看了 50 个，还是不会。",
  "增重的正确做法：放下手机去做。",
  "增重的教程看了 50 个，还是不会。",
  "增重的时候，手机掉电 50%。",
  "增重的时候，手机烫得像烙铁。",
  "你收藏了 100 个增重攻略，一个也没看。",
  "你搜索增重，出来了 100 万条结果。",
  "增重的时候，你摸出手机刷了 1 小时。",
  "增重排行榜第一：你。第二：没有人。",
  "增重的时候，手机掉电 50%。",
  "你搜索增重，出来了 100 万条结果。",
  "你说再也不增重了，结果增重了一下午。",
  "你在增重，突然想到手机没电了。",
  "你下载了增重 APP，占了 1G 内存。",
  "增重的时候，手机掉电 50%。",
  "你收藏了 100 个增重攻略，一个也没看。",
  "增重的最高境界：不用手机。",
];

const REPLY_BULK2_033 = [
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "你拍了护肤的照片，修图修了 2 小时。",
  "你问 Siri护肤是什么，Siri 说不知道。",
  "护肤的时候，你回复了 100 条消息。",
  "护肤的时候，你摸出手机刷了 1 小时。",
  "你问朋友护肤怎么样，朋友说不如玩手机。",
  "你拍了护肤的照片，修图修了 2 小时。",
  "护肤的时候，手机烫得像烙铁。",
  "你搜索护肤，出来了 100 万条结果。",
  "你问 Siri护肤是什么，Siri 说不知道。",
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "你说再也不护肤了，结果护肤了一下午。",
  "你收藏了 100 个护肤攻略，一个也没看。",
  "你被护肤的广告轰炸了一整天。",
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "你说再也不护肤了，结果护肤了一下午。",
  "护肤的教程看了 50 个，还是不会。",
  "护肤花了你 1000 块，结果啥也没得到。",
  "你问 Siri护肤是什么，Siri 说不知道。",
  "护肤的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_034 = [
  "你搜索化妆，出来了 100 万条结果。",
  "你问 Siri化妆是什么，Siri 说不知道。",
  "你问 Siri化妆是什么，Siri 说不知道。",
  "化妆的时候，你回复了 100 条消息。",
  "化妆的正确做法：放下手机去做。",
  "你下载了化妆 APP，占了 1G 内存。",
  "你收藏了 100 个化妆攻略，一个也没看。",
  "化妆结束了，你觉得浪费时间但很快乐。",
  "你拍了化妆的照片，修图修了 2 小时。",
  "化妆的最高境界：不用手机。",
  "化妆结束了，你觉得浪费时间但很快乐。",
  "你问 Siri化妆是什么，Siri 说不知道。",
  "你拍了化妆的照片，修图修了 2 小时。",
  "你收藏了 100 个化妆攻略，一个也没看。",
  "你问朋友化妆怎么样，朋友说不如玩手机。",
  "化妆排行榜第一：你。第二：没有人。",
  "化妆的时候，手机烫得像烙铁。",
  "化妆的时候，你回复了 100 条消息。",
  "化妆结束了，你觉得浪费时间但很快乐。",
  "化妆的最高境界：不用手机。",
];

const REPLY_BULK2_035 = [
  "你被染发的广告轰炸了一整天。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你问朋友染发怎么样，朋友说不如玩手机。",
  "染发的正确做法：放下手机去做。",
  "染发的最高境界：不用手机。",
  "你问朋友染发怎么样，朋友说不如玩手机。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你搜索染发，出来了 100 万条结果。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个染发攻略，一个也没看。",
  "你下载了染发 APP，占了 1G 内存。",
  "你说再也不染发了，结果染发了一下午。",
  "染发的正确做法：放下手机去做。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "染发的正确做法：放下手机去做。",
  "染发排行榜第一：你。第二：没有人。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你问朋友染发怎么样，朋友说不如玩手机。",
  "染发的时候，手机烫得像烙铁。",
  "染发的时候，手机掉电 50%。",
];

const REPLY_BULK2_036 = [
  "美甲结束了，你觉得浪费时间但很快乐。",
  "你下载了美甲 APP，占了 1G 内存。",
  "你问 Siri美甲是什么，Siri 说不知道。",
  "美甲的时候，你摸出手机刷了 1 小时。",
  "美甲的时候，手机掉电 50%。",
  "你问 Siri美甲是什么，Siri 说不知道。",
  "美甲排行榜第一：你。第二：没有人。",
  "美甲的时候，手机烫得像烙铁。",
  "美甲的最高境界：不用手机。",
  "美甲排行榜第一：你。第二：没有人。",
  "你问 Siri美甲是什么，Siri 说不知道。",
  "美甲的教程看了 50 个，还是不会。",
  "你在美甲，突然想到手机没电了。",
  "你发了美甲的朋友圈，点赞的都是机器人。",
  "你拍了美甲的照片，修图修了 2 小时。",
  "美甲的正确做法：放下手机去做。",
  "美甲花了你 1000 块，结果啥也没得到。",
  "美甲的时候，你回复了 100 条消息。",
  "你收藏了 100 个美甲攻略，一个也没看。",
  "美甲的正确做法：放下手机去做。",
];

const REPLY_BULK2_037 = [
  "健身花了你 1000 块，结果啥也没得到。",
  "你被健身的广告轰炸了一整天。",
  "健身结束了，你觉得浪费时间但很快乐。",
  "你搜索健身，出来了 100 万条结果。",
  "你发了健身的朋友圈，点赞的都是机器人。",
  "健身结束了，你觉得浪费时间但很快乐。",
  "健身的正确做法：放下手机去做。",
  "健身的最高境界：不用手机。",
  "你下载了健身 APP，占了 1G 内存。",
  "你被健身的广告轰炸了一整天。",
  "你收藏了 100 个健身攻略，一个也没看。",
  "健身的最高境界：不用手机。",
  "健身花了你 1000 块，结果啥也没得到。",
  "健身的正确做法：放下手机去做。",
  "健身的时候，手机掉电 50%。",
  "你发了健身的朋友圈，点赞的都是机器人。",
  "健身的时候，你摸出手机刷了 1 小时。",
  "你说再也不健身了，结果健身了一下午。",
  "健身排行榜第一：你。第二：没有人。",
  "健身的时候，你回复了 100 条消息。",
];

const REPLY_BULK2_038 = [
  "瑜伽花了你 1000 块，结果啥也没得到。",
  "你搜索瑜伽，出来了 100 万条结果。",
  "你在瑜伽，突然想到手机没电了。",
  "瑜伽的时候，你摸出手机刷了 1 小时。",
  "你搜索瑜伽，出来了 100 万条结果。",
  "瑜伽花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个瑜伽攻略，一个也没看。",
  "瑜伽的时候，手机掉电 50%。",
  "你收藏了 100 个瑜伽攻略，一个也没看。",
  "瑜伽的时候，手机掉电 50%。",
  "瑜伽的时候，手机掉电 50%。",
  "瑜伽的时候，手机掉电 50%。",
  "你收藏了 100 个瑜伽攻略，一个也没看。",
  "你收藏了 100 个瑜伽攻略，一个也没看。",
  "你被瑜伽的广告轰炸了一整天。",
  "你发了瑜伽的朋友圈，点赞的都是机器人。",
  "你问 Siri瑜伽是什么，Siri 说不知道。",
  "瑜伽的时候，手机掉电 50%。",
  "你问朋友瑜伽怎么样，朋友说不如玩手机。",
  "瑜伽的时候，手机掉电 50%。",
];

const REPLY_BULK2_039 = [
  "你在跑步，突然想到手机没电了。",
  "跑步的时候，手机烫得像烙铁。",
  "你问朋友跑步怎么样，朋友说不如玩手机。",
  "你在跑步，突然想到手机没电了。",
  "跑步结束了，你觉得浪费时间但很快乐。",
  "你问朋友跑步怎么样，朋友说不如玩手机。",
  "跑步花了你 1000 块，结果啥也没得到。",
  "跑步的最高境界：不用手机。",
  "你被跑步的广告轰炸了一整天。",
  "跑步结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个跑步攻略，一个也没看。",
  "跑步的时候，手机烫得像烙铁。",
  "你在跑步，突然想到手机没电了。",
  "你拍了跑步的照片，修图修了 2 小时。",
  "跑步的时候，你摸出手机刷了 1 小时。",
  "你搜索跑步，出来了 100 万条结果。",
  "跑步的正确做法：放下手机去做。",
  "你问朋友跑步怎么样，朋友说不如玩手机。",
  "跑步排行榜第一：你。第二：没有人。",
  "你下载了跑步 APP，占了 1G 内存。",
];

const REPLY_BULK2_040 = [
  "你问朋友游泳怎么样，朋友说不如玩手机。",
  "游泳花了你 1000 块，结果啥也没得到。",
  "你被游泳的广告轰炸了一整天。",
  "游泳的时候，手机烫得像烙铁。",
  "你说再也不游泳了，结果游泳了一下午。",
  "游泳的时候，你摸出手机刷了 1 小时。",
  "你搜索游泳，出来了 100 万条结果。",
  "游泳的最高境界：不用手机。",
  "游泳的时候，手机掉电 50%。",
  "游泳的时候，手机烫得像烙铁。",
  "游泳的时候，你回复了 100 条消息。",
  "你问朋友游泳怎么样，朋友说不如玩手机。",
  "游泳的教程看了 50 个，还是不会。",
  "游泳花了你 1000 块，结果啥也没得到。",
  "游泳的时候，你摸出手机刷了 1 小时。",
  "游泳的时候，手机掉电 50%。",
  "你下载了游泳 APP，占了 1G 内存。",
  "你拍了游泳的照片，修图修了 2 小时。",
  "游泳结束了，你觉得浪费时间但很快乐。",
  "游泳结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK2_041 = [
  "你被追剧的广告轰炸了一整天。",
  "你收藏了 100 个追剧攻略，一个也没看。",
  "你在追剧，突然想到手机没电了。",
  "追剧的时候，你回复了 100 条消息。",
  "追剧的正确做法：放下手机去做。",
  "追剧结束了，你觉得浪费时间但很快乐。",
  "追剧的时候，你回复了 100 条消息。",
  "追剧的教程看了 50 个，还是不会。",
  "你问朋友追剧怎么样，朋友说不如玩手机。",
  "追剧的时候，手机掉电 50%。",
  "你发了追剧的朋友圈，点赞的都是机器人。",
  "你拍了追剧的照片，修图修了 2 小时。",
  "你被追剧的广告轰炸了一整天。",
  "追剧的最高境界：不用手机。",
  "你收藏了 100 个追剧攻略，一个也没看。",
  "你被追剧的广告轰炸了一整天。",
  "追剧的时候，手机掉电 50%。",
  "你发了追剧的朋友圈，点赞的都是机器人。",
  "你拍了追剧的照片，修图修了 2 小时。",
  "你说再也不追剧了，结果追剧了一下午。",
];

const REPLY_BULK2_042 = [
  "你拍了追番的照片，修图修了 2 小时。",
  "你发了追番的朋友圈，点赞的都是机器人。",
  "追番花了你 1000 块，结果啥也没得到。",
  "你发了追番的朋友圈，点赞的都是机器人。",
  "追番排行榜第一：你。第二：没有人。",
  "追番的时候，你摸出手机刷了 1 小时。",
  "追番结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个追番攻略，一个也没看。",
  "追番花了你 1000 块，结果啥也没得到。",
  "你问 Siri追番是什么，Siri 说不知道。",
  "你拍了追番的照片，修图修了 2 小时。",
  "追番花了你 1000 块，结果啥也没得到。",
  "追番的时候，手机烫得像烙铁。",
  "追番花了你 1000 块，结果啥也没得到。",
  "你搜索追番，出来了 100 万条结果。",
  "追番排行榜第一：你。第二：没有人。",
  "追番的最高境界：不用手机。",
  "你搜索追番，出来了 100 万条结果。",
  "你收藏了 100 个追番攻略，一个也没看。",
  "你搜索追番，出来了 100 万条结果。",
];

const REPLY_BULK2_043 = [
  "追星排行榜第一：你。第二：没有人。",
  "你下载了追星 APP，占了 1G 内存。",
  "你在追星，突然想到手机没电了。",
  "你被追星的广告轰炸了一整天。",
  "你问朋友追星怎么样，朋友说不如玩手机。",
  "你下载了追星 APP，占了 1G 内存。",
  "追星的教程看了 50 个，还是不会。",
  "你下载了追星 APP，占了 1G 内存。",
  "你在追星，突然想到手机没电了。",
  "追星的时候，手机掉电 50%。",
  "你问朋友追星怎么样，朋友说不如玩手机。",
  "你在追星，突然想到手机没电了。",
  "你发了追星的朋友圈，点赞的都是机器人。",
  "你拍了追星的照片，修图修了 2 小时。",
  "你在追星，突然想到手机没电了。",
  "追星的正确做法：放下手机去做。",
  "追星结束了，你觉得浪费时间但很快乐。",
  "追星的正确做法：放下手机去做。",
  "你被追星的广告轰炸了一整天。",
  "你被追星的广告轰炸了一整天。",
];

const REPLY_BULK2_044 = [
  "打榜的最高境界：不用手机。",
  "打榜的时候，你回复了 100 条消息。",
  "你被打榜的广告轰炸了一整天。",
  "打榜花了你 1000 块，结果啥也没得到。",
  "打榜结束了，你觉得浪费时间但很快乐。",
  "打榜结束了，你觉得浪费时间但很快乐。",
  "你问 Siri打榜是什么，Siri 说不知道。",
  "打榜的时候，你摸出手机刷了 1 小时。",
  "打榜花了你 1000 块，结果啥也没得到。",
  "你在打榜，突然想到手机没电了。",
  "打榜结束了，你觉得浪费时间但很快乐。",
  "你被打榜的广告轰炸了一整天。",
  "打榜的正确做法：放下手机去做。",
  "你搜索打榜，出来了 100 万条结果。",
  "你问朋友打榜怎么样，朋友说不如玩手机。",
  "你在打榜，突然想到手机没电了。",
  "打榜的时候，你摸出手机刷了 1 小时。",
  "打榜的时候，手机掉电 50%。",
  "你收藏了 100 个打榜攻略，一个也没看。",
  "你问朋友打榜怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_045 = [
  "应援花了你 1000 块，结果啥也没得到。",
  "你拍了应援的照片，修图修了 2 小时。",
  "应援的时候，你回复了 100 条消息。",
  "应援的最高境界：不用手机。",
  "应援的时候，你回复了 100 条消息。",
  "你被应援的广告轰炸了一整天。",
  "你搜索应援，出来了 100 万条结果。",
  "应援的时候，你回复了 100 条消息。",
  "应援排行榜第一：你。第二：没有人。",
  "你说再也不应援了，结果应援了一下午。",
  "你搜索应援，出来了 100 万条结果。",
  "应援的时候，你摸出手机刷了 1 小时。",
  "应援的最高境界：不用手机。",
  "你拍了应援的照片，修图修了 2 小时。",
  "你搜索应援，出来了 100 万条结果。",
  "应援的时候，你摸出手机刷了 1 小时。",
  "你收藏了 100 个应援攻略，一个也没看。",
  "你发了应援的朋友圈，点赞的都是机器人。",
  "你问 Siri应援是什么，Siri 说不知道。",
  "你下载了应援 APP，占了 1G 内存。",
];

const REPLY_BULK2_046 = [
  "周边的最高境界：不用手机。",
  "你拍了周边的照片，修图修了 2 小时。",
  "周边的时候，你回复了 100 条消息。",
  "你收藏了 100 个周边攻略，一个也没看。",
  "周边结束了，你觉得浪费时间但很快乐。",
  "你下载了周边 APP，占了 1G 内存。",
  "你搜索周边，出来了 100 万条结果。",
  "你问 Siri周边是什么，Siri 说不知道。",
  "你发了周边的朋友圈，点赞的都是机器人。",
  "你问朋友周边怎么样，朋友说不如玩手机。",
  "你问 Siri周边是什么，Siri 说不知道。",
  "你发了周边的朋友圈，点赞的都是机器人。",
  "你下载了周边 APP，占了 1G 内存。",
  "周边的时候，你回复了 100 条消息。",
  "你问朋友周边怎么样，朋友说不如玩手机。",
  "你问朋友周边怎么样，朋友说不如玩手机。",
  "周边的最高境界：不用手机。",
  "周边花了你 1000 块，结果啥也没得到。",
  "你说再也不周边了，结果周边了一下午。",
  "你问朋友周边怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_047 = [
  "你说再也不手办了，结果手办了一下午。",
  "你问 Siri手办是什么，Siri 说不知道。",
  "你发了手办的朋友圈，点赞的都是机器人。",
  "手办结束了，你觉得浪费时间但很快乐。",
  "手办的教程看了 50 个，还是不会。",
  "手办的时候，手机烫得像烙铁。",
  "你在手办，突然想到手机没电了。",
  "手办的教程看了 50 个，还是不会。",
  "手办的时候，手机烫得像烙铁。",
  "手办的时候，手机烫得像烙铁。",
  "你搜索手办，出来了 100 万条结果。",
  "你在手办，突然想到手机没电了。",
  "手办的时候，手机烫得像烙铁。",
  "手办的时候，你回复了 100 条消息。",
  "你说再也不手办了，结果手办了一下午。",
  "你拍了手办的照片，修图修了 2 小时。",
  "你拍了手办的照片，修图修了 2 小时。",
  "手办的最高境界：不用手机。",
  "手办的时候，你摸出手机刷了 1 小时。",
  "你问 Siri手办是什么，Siri 说不知道。",
];

const REPLY_BULK2_048 = [
  "你问朋友盲盒怎么样，朋友说不如玩手机。",
  "你发了盲盒的朋友圈，点赞的都是机器人。",
  "盲盒结束了，你觉得浪费时间但很快乐。",
  "你搜索盲盒，出来了 100 万条结果。",
  "盲盒的时候，你摸出手机刷了 1 小时。",
  "你搜索盲盒，出来了 100 万条结果。",
  "盲盒的最高境界：不用手机。",
  "你发了盲盒的朋友圈，点赞的都是机器人。",
  "你拍了盲盒的照片，修图修了 2 小时。",
  "你被盲盒的广告轰炸了一整天。",
  "盲盒结束了，你觉得浪费时间但很快乐。",
  "盲盒花了你 1000 块，结果啥也没得到。",
  "你在盲盒，突然想到手机没电了。",
  "你被盲盒的广告轰炸了一整天。",
  "你搜索盲盒，出来了 100 万条结果。",
  "盲盒的时候，手机掉电 50%。",
  "你收藏了 100 个盲盒攻略，一个也没看。",
  "你收藏了 100 个盲盒攻略，一个也没看。",
  "盲盒花了你 1000 块，结果啥也没得到。",
  "盲盒的正确做法：放下手机去做。",
];

const REPLY_BULK2_049 = [
  "卡牌的教程看了 50 个，还是不会。",
  "卡牌的时候，你回复了 100 条消息。",
  "卡牌的最高境界：不用手机。",
  "你说再也不卡牌了，结果卡牌了一下午。",
  "你下载了卡牌 APP，占了 1G 内存。",
  "卡牌结束了，你觉得浪费时间但很快乐。",
  "卡牌的最高境界：不用手机。",
  "卡牌的时候，你摸出手机刷了 1 小时。",
  "你问朋友卡牌怎么样，朋友说不如玩手机。",
  "你发了卡牌的朋友圈，点赞的都是机器人。",
  "你下载了卡牌 APP，占了 1G 内存。",
  "卡牌的最高境界：不用手机。",
  "你被卡牌的广告轰炸了一整天。",
  "卡牌花了你 1000 块，结果啥也没得到。",
  "你拍了卡牌的照片，修图修了 2 小时。",
  "你拍了卡牌的照片，修图修了 2 小时。",
  "卡牌的时候，你摸出手机刷了 1 小时。",
  "卡牌的时候，你摸出手机刷了 1 小时。",
  "卡牌的教程看了 50 个，还是不会。",
  "你拍了卡牌的照片，修图修了 2 小时。",
];

const REPLY_BULK2_050 = [
  "你收藏了 100 个谷子攻略，一个也没看。",
  "谷子的时候，手机掉电 50%。",
  "你被谷子的广告轰炸了一整天。",
  "你在谷子，突然想到手机没电了。",
  "谷子的时候，手机掉电 50%。",
  "谷子的时候，你回复了 100 条消息。",
  "谷子的时候，手机掉电 50%。",
  "谷子的时候，手机烫得像烙铁。",
  "谷子结束了，你觉得浪费时间但很快乐。",
  "你说再也不谷子了，结果谷子了一下午。",
  "你说再也不谷子了，结果谷子了一下午。",
  "谷子的时候，你摸出手机刷了 1 小时。",
  "谷子的正确做法：放下手机去做。",
  "谷子结束了，你觉得浪费时间但很快乐。",
  "你搜索谷子，出来了 100 万条结果。",
  "谷子排行榜第一：你。第二：没有人。",
  "谷子花了你 1000 块，结果啥也没得到。",
  "你搜索谷子，出来了 100 万条结果。",
  "谷子排行榜第一：你。第二：没有人。",
  "谷子的正确做法：放下手机去做。",
];

const REPLY_BULK2_051 = [
  "外卖的教程看了 50 个，还是不会。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "外卖的时候，手机烫得像烙铁。",
  "外卖的时候，你回复了 100 条消息。",
  "外卖的教程看了 50 个，还是不会。",
  "外卖的时候，手机烫得像烙铁。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个外卖攻略，一个也没看。",
  "外卖的正确做法：放下手机去做。",
  "外卖的时候，手机烫得像烙铁。",
  "外卖的时候，你回复了 100 条消息。",
  "你问 Siri外卖是什么，Siri 说不知道。",
  "外卖的时候，你回复了 100 条消息。",
  "外卖的时候，你回复了 100 条消息。",
  "外卖的正确做法：放下手机去做。",
  "外卖的时候，手机烫得像烙铁。",
  "外卖的最高境界：不用手机。",
  "你搜索外卖，出来了 100 万条结果。",
  "外卖花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_052 = [
  "堂食的最高境界：不用手机。",
  "堂食的时候，手机掉电 50%。",
  "你拍了堂食的照片，修图修了 2 小时。",
  "堂食结束了，你觉得浪费时间但很快乐。",
  "你在堂食，突然想到手机没电了。",
  "你发了堂食的朋友圈，点赞的都是机器人。",
  "堂食的最高境界：不用手机。",
  "堂食的时候，你回复了 100 条消息。",
  "你说再也不堂食了，结果堂食了一下午。",
  "你问朋友堂食怎么样，朋友说不如玩手机。",
  "你问 Siri堂食是什么，Siri 说不知道。",
  "堂食的时候，你摸出手机刷了 1 小时。",
  "你被堂食的广告轰炸了一整天。",
  "堂食的时候，你摸出手机刷了 1 小时。",
  "你问 Siri堂食是什么，Siri 说不知道。",
  "堂食的最高境界：不用手机。",
  "你发了堂食的朋友圈，点赞的都是机器人。",
  "你问 Siri堂食是什么，Siri 说不知道。",
  "堂食的时候，你回复了 100 条消息。",
  "堂食的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_053 = [
  "你下载了自炊 APP，占了 1G 内存。",
  "你收藏了 100 个自炊攻略，一个也没看。",
  "你搜索自炊，出来了 100 万条结果。",
  "你拍了自炊的照片，修图修了 2 小时。",
  "自炊排行榜第一：你。第二：没有人。",
  "你问 Siri自炊是什么，Siri 说不知道。",
  "你拍了自炊的照片，修图修了 2 小时。",
  "自炊的时候，手机掉电 50%。",
  "自炊的时候，手机掉电 50%。",
  "自炊花了你 1000 块，结果啥也没得到。",
  "你拍了自炊的照片，修图修了 2 小时。",
  "你收藏了 100 个自炊攻略，一个也没看。",
  "自炊的教程看了 50 个，还是不会。",
  "自炊的时候，你回复了 100 条消息。",
  "自炊的时候，你摸出手机刷了 1 小时。",
  "自炊花了你 1000 块，结果啥也没得到。",
  "自炊的时候，你回复了 100 条消息。",
  "自炊的时候，手机烫得像烙铁。",
  "你在自炊，突然想到手机没电了。",
  "自炊的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_054 = [
  "减肥餐的时候，手机烫得像烙铁。",
  "你搜索减肥餐，出来了 100 万条结果。",
  "减肥餐的时候，你回复了 100 条消息。",
  "减肥餐的时候，你回复了 100 条消息。",
  "减肥餐的时候，你摸出手机刷了 1 小时。",
  "减肥餐花了你 1000 块，结果啥也没得到。",
  "减肥餐花了你 1000 块，结果啥也没得到。",
  "减肥餐排行榜第一：你。第二：没有人。",
  "减肥餐花了你 1000 块，结果啥也没得到。",
  "你问朋友减肥餐怎么样，朋友说不如玩手机。",
  "你拍了减肥餐的照片，修图修了 2 小时。",
  "你发了减肥餐的朋友圈，点赞的都是机器人。",
  "你搜索减肥餐，出来了 100 万条结果。",
  "你在减肥餐，突然想到手机没电了。",
  "你在减肥餐，突然想到手机没电了。",
  "你问 Siri减肥餐是什么，Siri 说不知道。",
  "减肥餐的最高境界：不用手机。",
  "你问朋友减肥餐怎么样，朋友说不如玩手机。",
  "减肥餐花了你 1000 块，结果啥也没得到。",
  "减肥餐的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_055 = [
  "宵夜花了你 1000 块，结果啥也没得到。",
  "你搜索宵夜，出来了 100 万条结果。",
  "你下载了宵夜 APP，占了 1G 内存。",
  "宵夜的时候，手机烫得像烙铁。",
  "宵夜的最高境界：不用手机。",
  "宵夜排行榜第一：你。第二：没有人。",
  "宵夜的最高境界：不用手机。",
  "你在宵夜，突然想到手机没电了。",
  "你拍了宵夜的照片，修图修了 2 小时。",
  "你下载了宵夜 APP，占了 1G 内存。",
  "你在宵夜，突然想到手机没电了。",
  "你拍了宵夜的照片，修图修了 2 小时。",
  "你搜索宵夜，出来了 100 万条结果。",
  "你说再也不宵夜了，结果宵夜了一下午。",
  "宵夜花了你 1000 块，结果啥也没得到。",
  "宵夜的最高境界：不用手机。",
  "宵夜花了你 1000 块，结果啥也没得到。",
  "宵夜的教程看了 50 个，还是不会。",
  "宵夜的时候，手机掉电 50%。",
  "宵夜的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_056 = [
  "早餐的时候，你回复了 100 条消息。",
  "你下载了早餐 APP，占了 1G 内存。",
  "你下载了早餐 APP，占了 1G 内存。",
  "早餐的正确做法：放下手机去做。",
  "早餐的时候，你摸出手机刷了 1 小时。",
  "你说再也不早餐了，结果早餐了一下午。",
  "你发了早餐的朋友圈，点赞的都是机器人。",
  "早餐的时候，你摸出手机刷了 1 小时。",
  "你问朋友早餐怎么样，朋友说不如玩手机。",
  "早餐排行榜第一：你。第二：没有人。",
  "你发了早餐的朋友圈，点赞的都是机器人。",
  "早餐花了你 1000 块，结果啥也没得到。",
  "你拍了早餐的照片，修图修了 2 小时。",
  "你下载了早餐 APP，占了 1G 内存。",
  "你拍了早餐的照片，修图修了 2 小时。",
  "早餐花了你 1000 块，结果啥也没得到。",
  "你问 Siri早餐是什么，Siri 说不知道。",
  "你收藏了 100 个早餐攻略，一个也没看。",
  "早餐的教程看了 50 个，还是不会。",
  "早餐的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_057 = [
  "你搜索午餐，出来了 100 万条结果。",
  "午餐花了你 1000 块，结果啥也没得到。",
  "午餐的最高境界：不用手机。",
  "午餐的正确做法：放下手机去做。",
  "你搜索午餐，出来了 100 万条结果。",
  "你问 Siri午餐是什么，Siri 说不知道。",
  "午餐的时候，手机掉电 50%。",
  "你下载了午餐 APP，占了 1G 内存。",
  "你问 Siri午餐是什么，Siri 说不知道。",
  "午餐的正确做法：放下手机去做。",
  "午餐的教程看了 50 个，还是不会。",
  "午餐的时候，你回复了 100 条消息。",
  "午餐结束了，你觉得浪费时间但很快乐。",
  "你拍了午餐的照片，修图修了 2 小时。",
  "你搜索午餐，出来了 100 万条结果。",
  "你收藏了 100 个午餐攻略，一个也没看。",
  "你在午餐，突然想到手机没电了。",
  "午餐的时候，手机掉电 50%。",
  "你搜索午餐，出来了 100 万条结果。",
  "午餐的时候，手机掉电 50%。",
];

const REPLY_BULK2_058 = [
  "晚餐结束了，你觉得浪费时间但很快乐。",
  "晚餐结束了，你觉得浪费时间但很快乐。",
  "晚餐的时候，手机掉电 50%。",
  "你问朋友晚餐怎么样，朋友说不如玩手机。",
  "你问 Siri晚餐是什么，Siri 说不知道。",
  "晚餐排行榜第一：你。第二：没有人。",
  "你搜索晚餐，出来了 100 万条结果。",
  "你搜索晚餐，出来了 100 万条结果。",
  "晚餐的时候，手机掉电 50%。",
  "你发了晚餐的朋友圈，点赞的都是机器人。",
  "晚餐的时候，手机掉电 50%。",
  "晚餐的正确做法：放下手机去做。",
  "你被晚餐的广告轰炸了一整天。",
  "你下载了晚餐 APP，占了 1G 内存。",
  "你在晚餐，突然想到手机没电了。",
  "你说再也不晚餐了，结果晚餐了一下午。",
  "你在晚餐，突然想到手机没电了。",
  "你被晚餐的广告轰炸了一整天。",
  "晚餐的时候，手机烫得像烙铁。",
  "晚餐排行榜第一：你。第二：没有人。",
];

const REPLY_BULK2_059 = [
  "下午茶的时候，手机掉电 50%。",
  "下午茶结束了，你觉得浪费时间但很快乐。",
  "下午茶的时候，手机烫得像烙铁。",
  "下午茶的时候，手机掉电 50%。",
  "你搜索下午茶，出来了 100 万条结果。",
  "下午茶的时候，你回复了 100 条消息。",
  "下午茶花了你 1000 块，结果啥也没得到。",
  "你搜索下午茶，出来了 100 万条结果。",
  "你拍了下午茶的照片，修图修了 2 小时。",
  "你问朋友下午茶怎么样，朋友说不如玩手机。",
  "你拍了下午茶的照片，修图修了 2 小时。",
  "你拍了下午茶的照片，修图修了 2 小时。",
  "你收藏了 100 个下午茶攻略，一个也没看。",
  "你下载了下午茶 APP，占了 1G 内存。",
  "你下载了下午茶 APP，占了 1G 内存。",
  "下午茶的教程看了 50 个，还是不会。",
  "下午茶的正确做法：放下手机去做。",
  "下午茶的正确做法：放下手机去做。",
  "你发了下午茶的朋友圈，点赞的都是机器人。",
  "下午茶的正确做法：放下手机去做。",
];

const REPLY_BULK2_060 = [
  "夜宵排行榜第一：你。第二：没有人。",
  "你搜索夜宵，出来了 100 万条结果。",
  "夜宵的教程看了 50 个，还是不会。",
  "夜宵的正确做法：放下手机去做。",
  "夜宵的时候，你回复了 100 条消息。",
  "夜宵的时候，手机烫得像烙铁。",
  "你收藏了 100 个夜宵攻略，一个也没看。",
  "你发了夜宵的朋友圈，点赞的都是机器人。",
  "你发了夜宵的朋友圈，点赞的都是机器人。",
  "你问朋友夜宵怎么样，朋友说不如玩手机。",
  "你下载了夜宵 APP，占了 1G 内存。",
  "你发了夜宵的朋友圈，点赞的都是机器人。",
  "夜宵排行榜第一：你。第二：没有人。",
  "你搜索夜宵，出来了 100 万条结果。",
  "你在夜宵，突然想到手机没电了。",
  "你问朋友夜宵怎么样，朋友说不如玩手机。",
  "夜宵花了你 1000 块，结果啥也没得到。",
  "夜宵的时候，手机烫得像烙铁。",
  "夜宵花了你 1000 块，结果啥也没得到。",
  "夜宵的最高境界：不用手机。",
];

const REPLY_BULK2_061 = [
  "你在咖啡，突然想到手机没电了。",
  "你搜索咖啡，出来了 100 万条结果。",
  "咖啡的正确做法：放下手机去做。",
  "你发了咖啡的朋友圈，点赞的都是机器人。",
  "咖啡的教程看了 50 个，还是不会。",
  "你在咖啡，突然想到手机没电了。",
  "你发了咖啡的朋友圈，点赞的都是机器人。",
  "你发了咖啡的朋友圈，点赞的都是机器人。",
  "你发了咖啡的朋友圈，点赞的都是机器人。",
  "咖啡的最高境界：不用手机。",
  "咖啡的时候，你摸出手机刷了 1 小时。",
  "你下载了咖啡 APP，占了 1G 内存。",
  "咖啡排行榜第一：你。第二：没有人。",
  "你说再也不咖啡了，结果咖啡了一下午。",
  "你搜索咖啡，出来了 100 万条结果。",
  "咖啡的最高境界：不用手机。",
  "你拍了咖啡的照片，修图修了 2 小时。",
  "咖啡结束了，你觉得浪费时间但很快乐。",
  "咖啡排行榜第一：你。第二：没有人。",
  "咖啡的正确做法：放下手机去做。",
];

const REPLY_BULK2_062 = [
  "奶茶的时候，手机掉电 50%。",
  "你发了奶茶的朋友圈，点赞的都是机器人。",
  "你下载了奶茶 APP，占了 1G 内存。",
  "奶茶的时候，你摸出手机刷了 1 小时。",
  "你拍了奶茶的照片，修图修了 2 小时。",
  "你在奶茶，突然想到手机没电了。",
  "奶茶结束了，你觉得浪费时间但很快乐。",
  "你搜索奶茶，出来了 100 万条结果。",
  "你在奶茶，突然想到手机没电了。",
  "你发了奶茶的朋友圈，点赞的都是机器人。",
  "你发了奶茶的朋友圈，点赞的都是机器人。",
  "你问朋友奶茶怎么样，朋友说不如玩手机。",
  "奶茶的时候，手机烫得像烙铁。",
  "奶茶的正确做法：放下手机去做。",
  "你在奶茶，突然想到手机没电了。",
  "你发了奶茶的朋友圈，点赞的都是机器人。",
  "奶茶的时候，你回复了 100 条消息。",
  "你说再也不奶茶了，结果奶茶了一下午。",
  "奶茶排行榜第一：你。第二：没有人。",
  "奶茶的正确做法：放下手机去做。",
];

const REPLY_BULK2_063 = [
  "你被果茶的广告轰炸了一整天。",
  "你下载了果茶 APP，占了 1G 内存。",
  "果茶的教程看了 50 个，还是不会。",
  "你收藏了 100 个果茶攻略，一个也没看。",
  "你拍了果茶的照片，修图修了 2 小时。",
  "果茶结束了，你觉得浪费时间但很快乐。",
  "你问 Siri果茶是什么，Siri 说不知道。",
  "果茶的时候，你回复了 100 条消息。",
  "果茶的时候，手机烫得像烙铁。",
  "你发了果茶的朋友圈，点赞的都是机器人。",
  "果茶的时候，你回复了 100 条消息。",
  "果茶的时候，你回复了 100 条消息。",
  "你问朋友果茶怎么样，朋友说不如玩手机。",
  "你在果茶，突然想到手机没电了。",
  "果茶的教程看了 50 个，还是不会。",
  "果茶的教程看了 50 个，还是不会。",
  "你被果茶的广告轰炸了一整天。",
  "果茶花了你 1000 块，结果啥也没得到。",
  "你搜索果茶，出来了 100 万条结果。",
  "果茶的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_064 = [
  "汽水的时候，你回复了 100 条消息。",
  "你问朋友汽水怎么样，朋友说不如玩手机。",
  "汽水的教程看了 50 个，还是不会。",
  "你搜索汽水，出来了 100 万条结果。",
  "你问朋友汽水怎么样，朋友说不如玩手机。",
  "汽水花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个汽水攻略，一个也没看。",
  "你收藏了 100 个汽水攻略，一个也没看。",
  "汽水的时候，手机烫得像烙铁。",
  "你在汽水，突然想到手机没电了。",
  "你被汽水的广告轰炸了一整天。",
  "你问 Siri汽水是什么，Siri 说不知道。",
  "你在汽水，突然想到手机没电了。",
  "你被汽水的广告轰炸了一整天。",
  "你问朋友汽水怎么样，朋友说不如玩手机。",
  "你问朋友汽水怎么样，朋友说不如玩手机。",
  "你被汽水的广告轰炸了一整天。",
  "汽水排行榜第一：你。第二：没有人。",
  "你拍了汽水的照片，修图修了 2 小时。",
  "你下载了汽水 APP，占了 1G 内存。",
];

const REPLY_BULK2_065 = [
  "果汁的正确做法：放下手机去做。",
  "你发了果汁的朋友圈，点赞的都是机器人。",
  "你下载了果汁 APP，占了 1G 内存。",
  "你发了果汁的朋友圈，点赞的都是机器人。",
  "你问 Siri果汁是什么，Siri 说不知道。",
  "果汁的正确做法：放下手机去做。",
  "果汁的最高境界：不用手机。",
  "你搜索果汁，出来了 100 万条结果。",
  "果汁的正确做法：放下手机去做。",
  "果汁的时候，你摸出手机刷了 1 小时。",
  "你问朋友果汁怎么样，朋友说不如玩手机。",
  "果汁花了你 1000 块，结果啥也没得到。",
  "果汁的正确做法：放下手机去做。",
  "果汁的时候，手机掉电 50%。",
  "果汁的时候，你回复了 100 条消息。",
  "果汁排行榜第一：你。第二：没有人。",
  "果汁的时候，你回复了 100 条消息。",
  "果汁的正确做法：放下手机去做。",
  "你问 Siri果汁是什么，Siri 说不知道。",
  "果汁的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_066 = [
  "你搜索啤酒，出来了 100 万条结果。",
  "啤酒花了你 1000 块，结果啥也没得到。",
  "你说再也不啤酒了，结果啤酒了一下午。",
  "啤酒排行榜第一：你。第二：没有人。",
  "你被啤酒的广告轰炸了一整天。",
  "你在啤酒，突然想到手机没电了。",
  "啤酒结束了，你觉得浪费时间但很快乐。",
  "啤酒的时候，手机掉电 50%。",
  "啤酒的时候，你摸出手机刷了 1 小时。",
  "啤酒的时候，你摸出手机刷了 1 小时。",
  "啤酒的时候，你回复了 100 条消息。",
  "啤酒的时候，你回复了 100 条消息。",
  "啤酒的时候，你回复了 100 条消息。",
  "啤酒排行榜第一：你。第二：没有人。",
  "啤酒的时候，手机烫得像烙铁。",
  "啤酒的时候，你回复了 100 条消息。",
  "啤酒排行榜第一：你。第二：没有人。",
  "你搜索啤酒，出来了 100 万条结果。",
  "你说再也不啤酒了，结果啤酒了一下午。",
  "你说再也不啤酒了，结果啤酒了一下午。",
];

const REPLY_BULK2_067 = [
  "你问 Siri红酒是什么，Siri 说不知道。",
  "红酒的最高境界：不用手机。",
  "红酒结束了，你觉得浪费时间但很快乐。",
  "你下载了红酒 APP，占了 1G 内存。",
  "你拍了红酒的照片，修图修了 2 小时。",
  "红酒的时候，手机掉电 50%。",
  "红酒的时候，你摸出手机刷了 1 小时。",
  "红酒的教程看了 50 个，还是不会。",
  "红酒的时候，手机烫得像烙铁。",
  "你在红酒，突然想到手机没电了。",
  "红酒的时候，手机烫得像烙铁。",
  "你问 Siri红酒是什么，Siri 说不知道。",
  "红酒的时候，你摸出手机刷了 1 小时。",
  "红酒的正确做法：放下手机去做。",
  "你在红酒，突然想到手机没电了。",
  "红酒结束了，你觉得浪费时间但很快乐。",
  "你问朋友红酒怎么样，朋友说不如玩手机。",
  "红酒的时候，手机烫得像烙铁。",
  "你发了红酒的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个红酒攻略，一个也没看。",
];

const REPLY_BULK2_068 = [
  "你搜索白酒，出来了 100 万条结果。",
  "白酒排行榜第一：你。第二：没有人。",
  "白酒排行榜第一：你。第二：没有人。",
  "你发了白酒的朋友圈，点赞的都是机器人。",
  "白酒的时候，手机掉电 50%。",
  "白酒的正确做法：放下手机去做。",
  "白酒排行榜第一：你。第二：没有人。",
  "白酒的时候，手机烫得像烙铁。",
  "白酒的时候，手机掉电 50%。",
  "白酒的时候，手机掉电 50%。",
  "你搜索白酒，出来了 100 万条结果。",
  "白酒的最高境界：不用手机。",
  "你下载了白酒 APP，占了 1G 内存。",
  "你在白酒，突然想到手机没电了。",
  "你拍了白酒的照片，修图修了 2 小时。",
  "你搜索白酒，出来了 100 万条结果。",
  "你问 Siri白酒是什么，Siri 说不知道。",
  "你收藏了 100 个白酒攻略，一个也没看。",
  "白酒的时候，手机掉电 50%。",
  "你拍了白酒的照片，修图修了 2 小时。",
];

const REPLY_BULK2_069 = [
  "你在可乐，突然想到手机没电了。",
  "可乐排行榜第一：你。第二：没有人。",
  "可乐的正确做法：放下手机去做。",
  "可乐的最高境界：不用手机。",
  "你搜索可乐，出来了 100 万条结果。",
  "可乐的最高境界：不用手机。",
  "可乐花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个可乐攻略，一个也没看。",
  "可乐的教程看了 50 个，还是不会。",
  "可乐的时候，手机掉电 50%。",
  "你收藏了 100 个可乐攻略，一个也没看。",
  "可乐的时候，手机掉电 50%。",
  "可乐的时候，手机烫得像烙铁。",
  "可乐排行榜第一：你。第二：没有人。",
  "你发了可乐的朋友圈，点赞的都是机器人。",
  "可乐排行榜第一：你。第二：没有人。",
  "可乐排行榜第一：你。第二：没有人。",
  "你问 Siri可乐是什么，Siri 说不知道。",
  "可乐的正确做法：放下手机去做。",
  "可乐的正确做法：放下手机去做。",
];

const REPLY_BULK2_070 = [
  "你收藏了 100 个雪碧攻略，一个也没看。",
  "你在雪碧，突然想到手机没电了。",
  "雪碧的时候，你回复了 100 条消息。",
  "雪碧的时候，你回复了 100 条消息。",
  "你问朋友雪碧怎么样，朋友说不如玩手机。",
  "雪碧的时候，你摸出手机刷了 1 小时。",
  "你下载了雪碧 APP，占了 1G 内存。",
  "你问朋友雪碧怎么样，朋友说不如玩手机。",
  "雪碧的教程看了 50 个，还是不会。",
  "雪碧的教程看了 50 个，还是不会。",
  "雪碧的时候，你摸出手机刷了 1 小时。",
  "你说再也不雪碧了，结果雪碧了一下午。",
  "你在雪碧，突然想到手机没电了。",
  "雪碧排行榜第一：你。第二：没有人。",
  "你收藏了 100 个雪碧攻略，一个也没看。",
  "雪碧的时候，你回复了 100 条消息。",
  "你搜索雪碧，出来了 100 万条结果。",
  "雪碧结束了，你觉得浪费时间但很快乐。",
  "雪碧的时候，你摸出手机刷了 1 小时。",
  "雪碧花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_071 = [
  "你收藏了 100 个地铁攻略，一个也没看。",
  "你说再也不地铁了，结果地铁了一下午。",
  "地铁的正确做法：放下手机去做。",
  "你说再也不地铁了，结果地铁了一下午。",
  "地铁排行榜第一：你。第二：没有人。",
  "你问 Siri地铁是什么，Siri 说不知道。",
  "地铁花了你 1000 块，结果啥也没得到。",
  "你下载了地铁 APP，占了 1G 内存。",
  "地铁的时候，手机烫得像烙铁。",
  "地铁花了你 1000 块，结果啥也没得到。",
  "你发了地铁的朋友圈，点赞的都是机器人。",
  "地铁的教程看了 50 个，还是不会。",
  "你搜索地铁，出来了 100 万条结果。",
  "地铁的正确做法：放下手机去做。",
  "地铁的正确做法：放下手机去做。",
  "你发了地铁的朋友圈，点赞的都是机器人。",
  "地铁排行榜第一：你。第二：没有人。",
  "地铁的教程看了 50 个，还是不会。",
  "你问 Siri地铁是什么，Siri 说不知道。",
  "地铁的时候，手机掉电 50%。",
];

const REPLY_BULK2_072 = [
  "公交的时候，手机掉电 50%。",
  "你问 Siri公交是什么，Siri 说不知道。",
  "公交的时候，手机烫得像烙铁。",
  "公交结束了，你觉得浪费时间但很快乐。",
  "公交排行榜第一：你。第二：没有人。",
  "你发了公交的朋友圈，点赞的都是机器人。",
  "你下载了公交 APP，占了 1G 内存。",
  "公交的教程看了 50 个，还是不会。",
  "你问朋友公交怎么样，朋友说不如玩手机。",
  "你被公交的广告轰炸了一整天。",
  "公交的教程看了 50 个，还是不会。",
  "公交的时候，你回复了 100 条消息。",
  "你收藏了 100 个公交攻略，一个也没看。",
  "你搜索公交，出来了 100 万条结果。",
  "你拍了公交的照片，修图修了 2 小时。",
  "你下载了公交 APP，占了 1G 内存。",
  "公交的时候，手机掉电 50%。",
  "你被公交的广告轰炸了一整天。",
  "你拍了公交的照片，修图修了 2 小时。",
  "公交的最高境界：不用手机。",
];

const REPLY_BULK2_073 = [
  "你下载了出租车 APP，占了 1G 内存。",
  "你收藏了 100 个出租车攻略，一个也没看。",
  "出租车结束了，你觉得浪费时间但很快乐。",
  "你拍了出租车的照片，修图修了 2 小时。",
  "出租车的时候，你摸出手机刷了 1 小时。",
  "出租车的教程看了 50 个，还是不会。",
  "出租车花了你 1000 块，结果啥也没得到。",
  "出租车的时候，手机掉电 50%。",
  "你在出租车，突然想到手机没电了。",
  "你被出租车的广告轰炸了一整天。",
  "你问朋友出租车怎么样，朋友说不如玩手机。",
  "你说再也不出租车了，结果出租车了一下午。",
  "你问 Siri出租车是什么，Siri 说不知道。",
  "你收藏了 100 个出租车攻略，一个也没看。",
  "你问 Siri出租车是什么，Siri 说不知道。",
  "你发了出租车的朋友圈，点赞的都是机器人。",
  "你说再也不出租车了，结果出租车了一下午。",
  "出租车排行榜第一：你。第二：没有人。",
  "你收藏了 100 个出租车攻略，一个也没看。",
  "出租车花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK2_074 = [
  "网约车的时候，手机掉电 50%。",
  "你拍了网约车的照片，修图修了 2 小时。",
  "网约车的最高境界：不用手机。",
  "网约车结束了，你觉得浪费时间但很快乐。",
  "网约车的时候，手机掉电 50%。",
  "网约车的教程看了 50 个，还是不会。",
  "网约车的时候，手机掉电 50%。",
  "你被网约车的广告轰炸了一整天。",
  "网约车的教程看了 50 个，还是不会。",
  "网约车的正确做法：放下手机去做。",
  "网约车排行榜第一：你。第二：没有人。",
  "网约车的时候，你回复了 100 条消息。",
  "你搜索网约车，出来了 100 万条结果。",
  "你拍了网约车的照片，修图修了 2 小时。",
  "你问朋友网约车怎么样，朋友说不如玩手机。",
  "你搜索网约车，出来了 100 万条结果。",
  "网约车排行榜第一：你。第二：没有人。",
  "网约车的时候，手机烫得像烙铁。",
  "你收藏了 100 个网约车攻略，一个也没看。",
  "你搜索网约车，出来了 100 万条结果。",
];

const REPLY_BULK2_075 = [
  "你问 Siri共享单车是什么，Siri 说不知道。",
  "你问 Siri共享单车是什么，Siri 说不知道。",
  "共享单车的最高境界：不用手机。",
  "共享单车结束了，你觉得浪费时间但很快乐。",
  "共享单车的教程看了 50 个，还是不会。",
  "你说再也不共享单车了，结果共享单车了一下午。",
  "共享单车花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个共享单车攻略，一个也没看。",
  "共享单车排行榜第一：你。第二：没有人。",
  "共享单车排行榜第一：你。第二：没有人。",
  "你说再也不共享单车了，结果共享单车了一下午。",
  "共享单车排行榜第一：你。第二：没有人。",
  "你搜索共享单车，出来了 100 万条结果。",
  "你问 Siri共享单车是什么，Siri 说不知道。",
  "共享单车的时候，你回复了 100 条消息。",
  "共享单车的最高境界：不用手机。",
  "共享单车的教程看了 50 个，还是不会。",
  "共享单车的时候，手机烫得像烙铁。",
  "共享单车的时候，你回复了 100 条消息。",
  "共享单车排行榜第一：你。第二：没有人。",
];

const REPLY_BULK2_076 = [
  "你收藏了 100 个高铁攻略，一个也没看。",
  "你收藏了 100 个高铁攻略，一个也没看。",
  "你问 Siri高铁是什么，Siri 说不知道。",
  "你发了高铁的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个高铁攻略，一个也没看。",
  "高铁排行榜第一：你。第二：没有人。",
  "高铁花了你 1000 块，结果啥也没得到。",
  "高铁排行榜第一：你。第二：没有人。",
  "你发了高铁的朋友圈，点赞的都是机器人。",
  "高铁的教程看了 50 个，还是不会。",
  "高铁花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个高铁攻略，一个也没看。",
  "高铁的时候，手机掉电 50%。",
  "你搜索高铁，出来了 100 万条结果。",
  "高铁的时候，你摸出手机刷了 1 小时。",
  "高铁的教程看了 50 个，还是不会。",
  "高铁的最高境界：不用手机。",
  "高铁的时候，手机掉电 50%。",
  "高铁的时候，手机烫得像烙铁。",
  "你拍了高铁的照片，修图修了 2 小时。",
];

const REPLY_BULK2_077 = [
  "你搜索火车，出来了 100 万条结果。",
  "你发了火车的朋友圈，点赞的都是机器人。",
  "火车的时候，手机烫得像烙铁。",
  "你收藏了 100 个火车攻略，一个也没看。",
  "火车的教程看了 50 个，还是不会。",
  "你问 Siri火车是什么，Siri 说不知道。",
  "你问朋友火车怎么样，朋友说不如玩手机。",
  "火车的教程看了 50 个，还是不会。",
  "你拍了火车的照片，修图修了 2 小时。",
  "火车的时候，你回复了 100 条消息。",
  "你问 Siri火车是什么，Siri 说不知道。",
  "火车的正确做法：放下手机去做。",
  "火车的正确做法：放下手机去做。",
  "你拍了火车的照片，修图修了 2 小时。",
  "火车排行榜第一：你。第二：没有人。",
  "你问 Siri火车是什么，Siri 说不知道。",
  "你在火车，突然想到手机没电了。",
  "你在火车，突然想到手机没电了。",
  "火车的最高境界：不用手机。",
  "你在火车，突然想到手机没电了。",
];

const REPLY_BULK2_078 = [
  "你下载了飞机 APP，占了 1G 内存。",
  "你收藏了 100 个飞机攻略，一个也没看。",
  "飞机的最高境界：不用手机。",
  "你问 Siri飞机是什么，Siri 说不知道。",
  "飞机的正确做法：放下手机去做。",
  "飞机的时候，手机掉电 50%。",
  "飞机的时候，你摸出手机刷了 1 小时。",
  "你在飞机，突然想到手机没电了。",
  "飞机的时候，手机掉电 50%。",
  "你搜索飞机，出来了 100 万条结果。",
  "飞机的正确做法：放下手机去做。",
  "你下载了飞机 APP，占了 1G 内存。",
  "飞机的时候，你回复了 100 条消息。",
  "你问 Siri飞机是什么，Siri 说不知道。",
  "飞机的教程看了 50 个，还是不会。",
  "你在飞机，突然想到手机没电了。",
  "你问朋友飞机怎么样，朋友说不如玩手机。",
  "你被飞机的广告轰炸了一整天。",
  "你发了飞机的朋友圈，点赞的都是机器人。",
  "飞机结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK2_079 = [
  "你拍了轮船的照片，修图修了 2 小时。",
  "轮船的时候，手机掉电 50%。",
  "你说再也不轮船了，结果轮船了一下午。",
  "轮船的时候，手机掉电 50%。",
  "你拍了轮船的照片，修图修了 2 小时。",
  "你问 Siri轮船是什么，Siri 说不知道。",
  "轮船的时候，你摸出手机刷了 1 小时。",
  "轮船的时候，你回复了 100 条消息。",
  "轮船的时候，你摸出手机刷了 1 小时。",
  "轮船的时候，你摸出手机刷了 1 小时。",
  "轮船的时候，手机掉电 50%。",
  "你说再也不轮船了，结果轮船了一下午。",
  "轮船的时候，手机烫得像烙铁。",
  "轮船的时候，手机掉电 50%。",
  "你下载了轮船 APP，占了 1G 内存。",
  "轮船花了你 1000 块，结果啥也没得到。",
  "轮船排行榜第一：你。第二：没有人。",
  "轮船的时候，手机烫得像烙铁。",
  "你下载了轮船 APP，占了 1G 内存。",
  "你问朋友轮船怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_080 = [
  "你问 Siri自驾是什么，Siri 说不知道。",
  "你问朋友自驾怎么样，朋友说不如玩手机。",
  "自驾结束了，你觉得浪费时间但很快乐。",
  "自驾的时候，你摸出手机刷了 1 小时。",
  "你被自驾的广告轰炸了一整天。",
  "你发了自驾的朋友圈，点赞的都是机器人。",
  "你被自驾的广告轰炸了一整天。",
  "你收藏了 100 个自驾攻略，一个也没看。",
  "你问朋友自驾怎么样，朋友说不如玩手机。",
  "你搜索自驾，出来了 100 万条结果。",
  "自驾的时候，手机掉电 50%。",
  "你问朋友自驾怎么样，朋友说不如玩手机。",
  "自驾排行榜第一：你。第二：没有人。",
  "你问 Siri自驾是什么，Siri 说不知道。",
  "自驾的正确做法：放下手机去做。",
  "你问 Siri自驾是什么，Siri 说不知道。",
  "自驾的时候，你回复了 100 条消息。",
  "自驾的正确做法：放下手机去做。",
  "自驾排行榜第一：你。第二：没有人。",
  "自驾排行榜第一：你。第二：没有人。",
];

const REPLY_BULK2_081 = [
  "租房排行榜第一：你。第二：没有人。",
  "租房的时候，你摸出手机刷了 1 小时。",
  "租房排行榜第一：你。第二：没有人。",
  "租房的时候，你摸出手机刷了 1 小时。",
  "你发了租房的朋友圈，点赞的都是机器人。",
  "你说再也不租房了，结果租房了一下午。",
  "你被租房的广告轰炸了一整天。",
  "你在租房，突然想到手机没电了。",
  "租房结束了，你觉得浪费时间但很快乐。",
  "你问朋友租房怎么样，朋友说不如玩手机。",
  "租房的时候，手机掉电 50%。",
  "你被租房的广告轰炸了一整天。",
  "你被租房的广告轰炸了一整天。",
  "租房的最高境界：不用手机。",
  "租房花了你 1000 块，结果啥也没得到。",
  "你拍了租房的照片，修图修了 2 小时。",
  "租房的时候，你回复了 100 条消息。",
  "你被租房的广告轰炸了一整天。",
  "租房花了你 1000 块，结果啥也没得到。",
  "你问朋友租房怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_082 = [
  "你在买房，突然想到手机没电了。",
  "买房的时候，你回复了 100 条消息。",
  "买房的时候，手机掉电 50%。",
  "买房结束了，你觉得浪费时间但很快乐。",
  "买房的最高境界：不用手机。",
  "你问朋友买房怎么样，朋友说不如玩手机。",
  "你问朋友买房怎么样，朋友说不如玩手机。",
  "你说再也不买房了，结果买房了一下午。",
  "买房排行榜第一：你。第二：没有人。",
  "你问朋友买房怎么样，朋友说不如玩手机。",
  "你问朋友买房怎么样，朋友说不如玩手机。",
  "买房的正确做法：放下手机去做。",
  "买房的时候，手机烫得像烙铁。",
  "你收藏了 100 个买房攻略，一个也没看。",
  "你在买房，突然想到手机没电了。",
  "买房花了你 1000 块，结果啥也没得到。",
  "你搜索买房，出来了 100 万条结果。",
  "你被买房的广告轰炸了一整天。",
  "买房的时候，手机烫得像烙铁。",
  "买房的最高境界：不用手机。",
];

const REPLY_BULK2_083 = [
  "装修的时候，你回复了 100 条消息。",
  "装修的正确做法：放下手机去做。",
  "装修的正确做法：放下手机去做。",
  "装修的时候，手机掉电 50%。",
  "你问朋友装修怎么样，朋友说不如玩手机。",
  "装修的时候，你回复了 100 条消息。",
  "装修的正确做法：放下手机去做。",
  "你在装修，突然想到手机没电了。",
  "你说再也不装修了，结果装修了一下午。",
  "你发了装修的朋友圈，点赞的都是机器人。",
  "你被装修的广告轰炸了一整天。",
  "你在装修，突然想到手机没电了。",
  "装修的时候，你摸出手机刷了 1 小时。",
  "装修的正确做法：放下手机去做。",
  "装修的教程看了 50 个，还是不会。",
  "你下载了装修 APP，占了 1G 内存。",
  "装修的正确做法：放下手机去做。",
  "你下载了装修 APP，占了 1G 内存。",
  "你搜索装修，出来了 100 万条结果。",
  "你收藏了 100 个装修攻略，一个也没看。",
];

const REPLY_BULK2_084 = [
  "搬家的最高境界：不用手机。",
  "搬家的时候，你回复了 100 条消息。",
  "搬家的教程看了 50 个，还是不会。",
  "搬家的时候，手机掉电 50%。",
  "搬家排行榜第一：你。第二：没有人。",
  "你发了搬家的朋友圈，点赞的都是机器人。",
  "搬家的教程看了 50 个，还是不会。",
  "你被搬家的广告轰炸了一整天。",
  "你问朋友搬家怎么样，朋友说不如玩手机。",
  "搬家的教程看了 50 个，还是不会。",
  "你收藏了 100 个搬家攻略，一个也没看。",
  "搬家的时候，你回复了 100 条消息。",
  "你下载了搬家 APP，占了 1G 内存。",
  "搬家的正确做法：放下手机去做。",
  "搬家的教程看了 50 个，还是不会。",
  "搬家的时候，你回复了 100 条消息。",
  "搬家排行榜第一：你。第二：没有人。",
  "搬家结束了，你觉得浪费时间但很快乐。",
  "搬家的正确做法：放下手机去做。",
  "你下载了搬家 APP，占了 1G 内存。",
];

const REPLY_BULK2_085 = [
  "保洁结束了，你觉得浪费时间但很快乐。",
  "你拍了保洁的照片，修图修了 2 小时。",
  "你下载了保洁 APP，占了 1G 内存。",
  "保洁的时候，你摸出手机刷了 1 小时。",
  "保洁结束了，你觉得浪费时间但很快乐。",
  "你被保洁的广告轰炸了一整天。",
  "你下载了保洁 APP，占了 1G 内存。",
  "保洁的教程看了 50 个，还是不会。",
  "保洁的时候，你摸出手机刷了 1 小时。",
  "你拍了保洁的照片，修图修了 2 小时。",
  "你发了保洁的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个保洁攻略，一个也没看。",
  "保洁的时候，手机掉电 50%。",
  "保洁结束了，你觉得浪费时间但很快乐。",
  "你说再也不保洁了，结果保洁了一下午。",
  "保洁的教程看了 50 个，还是不会。",
  "你收藏了 100 个保洁攻略，一个也没看。",
  "你拍了保洁的照片，修图修了 2 小时。",
  "保洁的时候，手机掉电 50%。",
  "保洁的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_086 = [
  "你被维修的广告轰炸了一整天。",
  "你说再也不维修了，结果维修了一下午。",
  "维修的正确做法：放下手机去做。",
  "维修的时候，手机烫得像烙铁。",
  "你拍了维修的照片，修图修了 2 小时。",
  "维修的时候，你回复了 100 条消息。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "你拍了维修的照片，修图修了 2 小时。",
  "维修花了你 1000 块，结果啥也没得到。",
  "你说再也不维修了，结果维修了一下午。",
  "维修的时候，你摸出手机刷了 1 小时。",
  "维修的最高境界：不用手机。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "维修的时候，你摸出手机刷了 1 小时。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "你说再也不维修了，结果维修了一下午。",
  "维修的时候，手机掉电 50%。",
  "你问朋友维修怎么样，朋友说不如玩手机。",
  "你说再也不维修了，结果维修了一下午。",
];

const REPLY_BULK2_087 = [
  "快递花了你 1000 块，结果啥也没得到。",
  "快递的时候，你回复了 100 条消息。",
  "快递的时候，手机烫得像烙铁。",
  "快递的最高境界：不用手机。",
  "快递的时候，手机烫得像烙铁。",
  "你收藏了 100 个快递攻略，一个也没看。",
  "你收藏了 100 个快递攻略，一个也没看。",
  "你问朋友快递怎么样，朋友说不如玩手机。",
  "快递的时候，你回复了 100 条消息。",
  "快递花了你 1000 块，结果啥也没得到。",
  "你搜索快递，出来了 100 万条结果。",
  "快递的正确做法：放下手机去做。",
  "快递的时候，你摸出手机刷了 1 小时。",
  "你收藏了 100 个快递攻略，一个也没看。",
  "你问朋友快递怎么样，朋友说不如玩手机。",
  "你下载了快递 APP，占了 1G 内存。",
  "你被快递的广告轰炸了一整天。",
  "你问朋友快递怎么样，朋友说不如玩手机。",
  "快递的最高境界：不用手机。",
  "快递的时候，手机掉电 50%。",
];

const REPLY_BULK2_088 = [
  "外卖的时候，手机掉电 50%。",
  "外卖的正确做法：放下手机去做。",
  "你问 Siri外卖是什么，Siri 说不知道。",
  "你搜索外卖，出来了 100 万条结果。",
  "你问朋友外卖怎么样，朋友说不如玩手机。",
  "外卖花了你 1000 块，结果啥也没得到。",
  "你在外卖，突然想到手机没电了。",
  "你问 Siri外卖是什么，Siri 说不知道。",
  "你收藏了 100 个外卖攻略，一个也没看。",
  "外卖排行榜第一：你。第二：没有人。",
  "你拍了外卖的照片，修图修了 2 小时。",
  "你说再也不外卖了，结果外卖了一下午。",
  "外卖的时候，你摸出手机刷了 1 小时。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "你被外卖的广告轰炸了一整天。",
  "外卖的时候，你回复了 100 条消息。",
  "你在外卖，突然想到手机没电了。",
  "外卖的时候，你摸出手机刷了 1 小时。",
  "你问朋友外卖怎么样，朋友说不如玩手机。",
  "你说再也不外卖了，结果外卖了一下午。",
];

const REPLY_BULK2_089 = [
  "跑腿排行榜第一：你。第二：没有人。",
  "跑腿的时候，手机掉电 50%。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "跑腿花了你 1000 块，结果啥也没得到。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "你被跑腿的广告轰炸了一整天。",
  "你在跑腿，突然想到手机没电了。",
  "你被跑腿的广告轰炸了一整天。",
  "你下载了跑腿 APP，占了 1G 内存。",
  "你在跑腿，突然想到手机没电了。",
  "你问朋友跑腿怎么样，朋友说不如玩手机。",
  "你问 Siri跑腿是什么，Siri 说不知道。",
  "跑腿的时候，手机烫得像烙铁。",
  "跑腿的正确做法：放下手机去做。",
  "跑腿的教程看了 50 个，还是不会。",
  "你搜索跑腿，出来了 100 万条结果。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "你收藏了 100 个跑腿攻略，一个也没看。",
  "跑腿的时候，手机掉电 50%。",
  "你在跑腿，突然想到手机没电了。",
];

const REPLY_BULK2_090 = [
  "你被代购的广告轰炸了一整天。",
  "你发了代购的朋友圈，点赞的都是机器人。",
  "代购结束了，你觉得浪费时间但很快乐。",
  "代购的教程看了 50 个，还是不会。",
  "代购的时候，手机烫得像烙铁。",
  "代购的时候，手机掉电 50%。",
  "你问 Siri代购是什么，Siri 说不知道。",
  "代购花了你 1000 块，结果啥也没得到。",
  "你被代购的广告轰炸了一整天。",
  "你下载了代购 APP，占了 1G 内存。",
  "代购的最高境界：不用手机。",
  "代购的时候，你回复了 100 条消息。",
  "代购结束了，你觉得浪费时间但很快乐。",
  "你搜索代购，出来了 100 万条结果。",
  "代购的时候，手机烫得像烙铁。",
  "你拍了代购的照片，修图修了 2 小时。",
  "代购的时候，手机烫得像烙铁。",
  "你收藏了 100 个代购攻略，一个也没看。",
  "代购的时候，手机烫得像烙铁。",
  "你收藏了 100 个代购攻略，一个也没看。",
];

const REPLY_BULK2_091 = [
  "你发了开学的朋友圈，点赞的都是机器人。",
  "你在开学，突然想到手机没电了。",
  "你说再也不开学了，结果开学了一下午。",
  "开学的教程看了 50 个，还是不会。",
  "开学的时候，手机烫得像烙铁。",
  "开学的时候，手机烫得像烙铁。",
  "你收藏了 100 个开学攻略，一个也没看。",
  "你问 Siri开学是什么，Siri 说不知道。",
  "开学的时候，手机掉电 50%。",
  "你问 Siri开学是什么，Siri 说不知道。",
  "你发了开学的朋友圈，点赞的都是机器人。",
  "你在开学，突然想到手机没电了。",
  "开学排行榜第一：你。第二：没有人。",
  "开学的时候，你摸出手机刷了 1 小时。",
  "开学的时候，手机掉电 50%。",
  "开学结束了，你觉得浪费时间但很快乐。",
  "开学结束了，你觉得浪费时间但很快乐。",
  "你发了开学的朋友圈，点赞的都是机器人。",
  "你下载了开学 APP，占了 1G 内存。",
  "你问朋友开学怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_092 = [
  "你收藏了 100 个毕业攻略，一个也没看。",
  "你发了毕业的朋友圈，点赞的都是机器人。",
  "毕业的最高境界：不用手机。",
  "你说再也不毕业了，结果毕业了一下午。",
  "你说再也不毕业了，结果毕业了一下午。",
  "你下载了毕业 APP，占了 1G 内存。",
  "毕业的正确做法：放下手机去做。",
  "毕业结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个毕业攻略，一个也没看。",
  "毕业的时候，手机掉电 50%。",
  "毕业的时候，你摸出手机刷了 1 小时。",
  "毕业的时候，手机烫得像烙铁。",
  "你下载了毕业 APP，占了 1G 内存。",
  "毕业的时候，你摸出手机刷了 1 小时。",
  "你问朋友毕业怎么样，朋友说不如玩手机。",
  "毕业的时候，手机掉电 50%。",
  "毕业的正确做法：放下手机去做。",
  "毕业的正确做法：放下手机去做。",
  "毕业的最高境界：不用手机。",
  "你搜索毕业，出来了 100 万条结果。",
];

const REPLY_BULK2_093 = [
  "你在论文，突然想到手机没电了。",
  "论文排行榜第一：你。第二：没有人。",
  "论文的最高境界：不用手机。",
  "你拍了论文的照片，修图修了 2 小时。",
  "你在论文，突然想到手机没电了。",
  "你在论文，突然想到手机没电了。",
  "你拍了论文的照片，修图修了 2 小时。",
  "论文结束了，你觉得浪费时间但很快乐。",
  "你下载了论文 APP，占了 1G 内存。",
  "你问朋友论文怎么样，朋友说不如玩手机。",
  "论文的时候，手机掉电 50%。",
  "你在论文，突然想到手机没电了。",
  "论文花了你 1000 块，结果啥也没得到。",
  "论文的时候，你摸出手机刷了 1 小时。",
  "你问 Siri论文是什么，Siri 说不知道。",
  "论文结束了，你觉得浪费时间但很快乐。",
  "论文的正确做法：放下手机去做。",
  "你被论文的广告轰炸了一整天。",
  "你拍了论文的照片，修图修了 2 小时。",
  "你问 Siri论文是什么，Siri 说不知道。",
];

const REPLY_BULK2_094 = [
  "你问朋友答辩怎么样，朋友说不如玩手机。",
  "答辩的时候，你回复了 100 条消息。",
  "你问 Siri答辩是什么，Siri 说不知道。",
  "答辩的最高境界：不用手机。",
  "答辩的时候，手机掉电 50%。",
  "你被答辩的广告轰炸了一整天。",
  "答辩的时候，手机烫得像烙铁。",
  "你发了答辩的朋友圈，点赞的都是机器人。",
  "你问 Siri答辩是什么，Siri 说不知道。",
  "答辩的最高境界：不用手机。",
  "你搜索答辩，出来了 100 万条结果。",
  "你说再也不答辩了，结果答辩了一下午。",
  "你收藏了 100 个答辩攻略，一个也没看。",
  "答辩的正确做法：放下手机去做。",
  "答辩花了你 1000 块，结果啥也没得到。",
  "答辩排行榜第一：你。第二：没有人。",
  "答辩的时候，手机烫得像烙铁。",
  "你问朋友答辩怎么样，朋友说不如玩手机。",
  "答辩的最高境界：不用手机。",
  "你说再也不答辩了，结果答辩了一下午。",
];

const REPLY_BULK2_095 = [
  "考研排行榜第一：你。第二：没有人。",
  "考研花了你 1000 块，结果啥也没得到。",
  "考研的教程看了 50 个，还是不会。",
  "考研的最高境界：不用手机。",
  "你收藏了 100 个考研攻略，一个也没看。",
  "考研花了你 1000 块，结果啥也没得到。",
  "你下载了考研 APP，占了 1G 内存。",
  "考研排行榜第一：你。第二：没有人。",
  "你被考研的广告轰炸了一整天。",
  "你收藏了 100 个考研攻略，一个也没看。",
  "你在考研，突然想到手机没电了。",
  "你问朋友考研怎么样，朋友说不如玩手机。",
  "考研的最高境界：不用手机。",
  "考研排行榜第一：你。第二：没有人。",
  "考研的正确做法：放下手机去做。",
  "考研的时候，手机掉电 50%。",
  "考研的教程看了 50 个，还是不会。",
  "你搜索考研，出来了 100 万条结果。",
  "考研结束了，你觉得浪费时间但很快乐。",
  "考研的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_096 = [
  "考公花了你 1000 块，结果啥也没得到。",
  "你搜索考公，出来了 100 万条结果。",
  "你发了考公的朋友圈，点赞的都是机器人。",
  "考公的最高境界：不用手机。",
  "你说再也不考公了，结果考公了一下午。",
  "考公的正确做法：放下手机去做。",
  "你问朋友考公怎么样，朋友说不如玩手机。",
  "考公排行榜第一：你。第二：没有人。",
  "你拍了考公的照片，修图修了 2 小时。",
  "你在考公，突然想到手机没电了。",
  "考公的时候，手机烫得像烙铁。",
  "你收藏了 100 个考公攻略，一个也没看。",
  "你下载了考公 APP，占了 1G 内存。",
  "考公的时候，手机掉电 50%。",
  "你被考公的广告轰炸了一整天。",
  "你说再也不考公了，结果考公了一下午。",
  "你收藏了 100 个考公攻略，一个也没看。",
  "考公的正确做法：放下手机去做。",
  "考公的时候，你摸出手机刷了 1 小时。",
  "考公的最高境界：不用手机。",
];

const REPLY_BULK2_097 = [
  "你搜索考证，出来了 100 万条结果。",
  "你下载了考证 APP，占了 1G 内存。",
  "你搜索考证，出来了 100 万条结果。",
  "考证排行榜第一：你。第二：没有人。",
  "你拍了考证的照片，修图修了 2 小时。",
  "你搜索考证，出来了 100 万条结果。",
  "你说再也不考证了，结果考证了一下午。",
  "考证的教程看了 50 个，还是不会。",
  "你说再也不考证了，结果考证了一下午。",
  "考证结束了，你觉得浪费时间但很快乐。",
  "考证排行榜第一：你。第二：没有人。",
  "你搜索考证，出来了 100 万条结果。",
  "你发了考证的朋友圈，点赞的都是机器人。",
  "你被考证的广告轰炸了一整天。",
  "你说再也不考证了，结果考证了一下午。",
  "考证的时候，手机掉电 50%。",
  "考证花了你 1000 块，结果啥也没得到。",
  "你下载了考证 APP，占了 1G 内存。",
  "你说再也不考证了，结果考证了一下午。",
  "你问 Siri考证是什么，Siri 说不知道。",
];

const REPLY_BULK2_098 = [
  "留学排行榜第一：你。第二：没有人。",
  "留学的时候，你回复了 100 条消息。",
  "你收藏了 100 个留学攻略，一个也没看。",
  "你拍了留学的照片，修图修了 2 小时。",
  "留学的时候，手机掉电 50%。",
  "你搜索留学，出来了 100 万条结果。",
  "你下载了留学 APP，占了 1G 内存。",
  "留学的时候，你回复了 100 条消息。",
  "你问朋友留学怎么样，朋友说不如玩手机。",
  "留学的时候，手机掉电 50%。",
  "你收藏了 100 个留学攻略，一个也没看。",
  "你下载了留学 APP，占了 1G 内存。",
  "留学花了你 1000 块，结果啥也没得到。",
  "你问朋友留学怎么样，朋友说不如玩手机。",
  "你收藏了 100 个留学攻略，一个也没看。",
  "留学的教程看了 50 个，还是不会。",
  "你问朋友留学怎么样，朋友说不如玩手机。",
  "你说再也不留学了，结果留学了一下午。",
  "你搜索留学，出来了 100 万条结果。",
  "你下载了留学 APP，占了 1G 内存。",
];

const REPLY_BULK2_099 = [
  "你拍了交换的照片，修图修了 2 小时。",
  "交换的正确做法：放下手机去做。",
  "交换花了你 1000 块，结果啥也没得到。",
  "交换的时候，手机烫得像烙铁。",
  "你说再也不交换了，结果交换了一下午。",
  "交换结束了，你觉得浪费时间但很快乐。",
  "你问 Siri交换是什么，Siri 说不知道。",
  "交换的时候，你回复了 100 条消息。",
  "交换的时候，手机烫得像烙铁。",
  "交换的时候，手机烫得像烙铁。",
  "交换排行榜第一：你。第二：没有人。",
  "交换的时候，你回复了 100 条消息。",
  "交换结束了，你觉得浪费时间但很快乐。",
  "你下载了交换 APP，占了 1G 内存。",
  "交换的时候，手机烫得像烙铁。",
  "你说再也不交换了，结果交换了一下午。",
  "交换的时候，手机掉电 50%。",
  "交换的时候，你回复了 100 条消息。",
  "你收藏了 100 个交换攻略，一个也没看。",
  "交换的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_100 = [
  "你问 Siri网课是什么，Siri 说不知道。",
  "网课的正确做法：放下手机去做。",
  "网课的最高境界：不用手机。",
  "网课的最高境界：不用手机。",
  "你问 Siri网课是什么，Siri 说不知道。",
  "网课结束了，你觉得浪费时间但很快乐。",
  "网课的时候，你摸出手机刷了 1 小时。",
  "网课花了你 1000 块，结果啥也没得到。",
  "你问 Siri网课是什么，Siri 说不知道。",
  "网课的时候，你摸出手机刷了 1 小时。",
  "你收藏了 100 个网课攻略，一个也没看。",
  "网课结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个网课攻略，一个也没看。",
  "你被网课的广告轰炸了一整天。",
  "你搜索网课，出来了 100 万条结果。",
  "你问 Siri网课是什么，Siri 说不知道。",
  "网课排行榜第一：你。第二：没有人。",
  "你在网课，突然想到手机没电了。",
  "网课的最高境界：不用手机。",
  "网课的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_101 = [
  "你拍了微信的照片，修图修了 2 小时。",
  "你发了微信的朋友圈，点赞的都是机器人。",
  "你问 Siri微信是什么，Siri 说不知道。",
  "你问朋友微信怎么样，朋友说不如玩手机。",
  "微信的时候，手机掉电 50%。",
  "你拍了微信的照片，修图修了 2 小时。",
  "你被微信的广告轰炸了一整天。",
  "微信花了你 1000 块，结果啥也没得到。",
  "微信的时候，你回复了 100 条消息。",
  "微信的正确做法：放下手机去做。",
  "微信的最高境界：不用手机。",
  "微信的时候，你摸出手机刷了 1 小时。",
  "你发了微信的朋友圈，点赞的都是机器人。",
  "你搜索微信，出来了 100 万条结果。",
  "你问 Siri微信是什么，Siri 说不知道。",
  "你搜索微信，出来了 100 万条结果。",
  "你在微信，突然想到手机没电了。",
  "微信的时候，手机烫得像烙铁。",
  "微信排行榜第一：你。第二：没有人。",
  "微信的教程看了 50 个，还是不会。",
];

const REPLY_BULK2_102 = [
  "QQ的正确做法：放下手机去做。",
  "QQ花了你 1000 块，结果啥也没得到。",
  "QQ花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个QQ攻略，一个也没看。",
  "你说再也不QQ了，结果QQ了一下午。",
  "你问 SiriQQ是什么，Siri 说不知道。",
  "QQ结束了，你觉得浪费时间但很快乐。",
  "你问朋友QQ怎么样，朋友说不如玩手机。",
  "QQ排行榜第一：你。第二：没有人。",
  "你问 SiriQQ是什么，Siri 说不知道。",
  "QQ结束了，你觉得浪费时间但很快乐。",
  "你被QQ的广告轰炸了一整天。",
  "QQ排行榜第一：你。第二：没有人。",
  "QQ的时候，你摸出手机刷了 1 小时。",
  "QQ的教程看了 50 个，还是不会。",
  "你收藏了 100 个QQ攻略，一个也没看。",
  "你搜索QQ，出来了 100 万条结果。",
  "你下载了QQ APP，占了 1G 内存。",
  "QQ结束了，你觉得浪费时间但很快乐。",
  "QQ的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_103 = [
  "你搜索微博，出来了 100 万条结果。",
  "微博的正确做法：放下手机去做。",
  "微博的时候，手机掉电 50%。",
  "微博的时候，你摸出手机刷了 1 小时。",
  "微博排行榜第一：你。第二：没有人。",
  "微博结束了，你觉得浪费时间但很快乐。",
  "你被微博的广告轰炸了一整天。",
  "你发了微博的朋友圈，点赞的都是机器人。",
  "微博排行榜第一：你。第二：没有人。",
  "你问 Siri微博是什么，Siri 说不知道。",
  "你发了微博的朋友圈，点赞的都是机器人。",
  "微博的正确做法：放下手机去做。",
  "微博排行榜第一：你。第二：没有人。",
  "你拍了微博的照片，修图修了 2 小时。",
  "你收藏了 100 个微博攻略，一个也没看。",
  "你问朋友微博怎么样，朋友说不如玩手机。",
  "你问朋友微博怎么样，朋友说不如玩手机。",
  "你说再也不微博了，结果微博了一下午。",
  "你发了微博的朋友圈，点赞的都是机器人。",
  "微博的时候，你摸出手机刷了 1 小时。",
];

const REPLY_BULK2_104 = [
  "你问朋友小红书怎么样，朋友说不如玩手机。",
  "小红书的最高境界：不用手机。",
  "小红书排行榜第一：你。第二：没有人。",
  "小红书的时候，你回复了 100 条消息。",
  "小红书的时候，你回复了 100 条消息。",
  "你说再也不小红书了，结果小红书了一下午。",
  "你说再也不小红书了，结果小红书了一下午。",
  "小红书花了你 1000 块，结果啥也没得到。",
  "小红书排行榜第一：你。第二：没有人。",
  "小红书的正确做法：放下手机去做。",
  "小红书结束了，你觉得浪费时间但很快乐。",
  "小红书的时候，手机烫得像烙铁。",
  "你问 Siri小红书是什么，Siri 说不知道。",
  "小红书的教程看了 50 个，还是不会。",
  "小红书排行榜第一：你。第二：没有人。",
  "小红书花了你 1000 块，结果啥也没得到。",
  "小红书的教程看了 50 个，还是不会。",
  "你下载了小红书 APP，占了 1G 内存。",
  "你发了小红书的朋友圈，点赞的都是机器人。",
  "小红书的时候，你回复了 100 条消息。",
];

const REPLY_BULK2_105 = [
  "你收藏了 100 个抖音攻略，一个也没看。",
  "抖音的教程看了 50 个，还是不会。",
  "你发了抖音的朋友圈，点赞的都是机器人。",
  "你说再也不抖音了，结果抖音了一下午。",
  "你下载了抖音 APP，占了 1G 内存。",
  "抖音的最高境界：不用手机。",
  "抖音的最高境界：不用手机。",
  "抖音花了你 1000 块，结果啥也没得到。",
  "抖音的时候，手机烫得像烙铁。",
  "你在抖音，突然想到手机没电了。",
  "你搜索抖音，出来了 100 万条结果。",
  "抖音的时候，你摸出手机刷了 1 小时。",
  "抖音的时候，手机掉电 50%。",
  "抖音的最高境界：不用手机。",
  "你被抖音的广告轰炸了一整天。",
  "你搜索抖音，出来了 100 万条结果。",
  "抖音结束了，你觉得浪费时间但很快乐。",
  "抖音的正确做法：放下手机去做。",
  "你被抖音的广告轰炸了一整天。",
  "抖音的时候，手机掉电 50%。",
];

const REPLY_BULK2_106 = [
  "快手的时候，你回复了 100 条消息。",
  "你问朋友快手怎么样，朋友说不如玩手机。",
  "你说再也不快手了，结果快手了一下午。",
  "你搜索快手，出来了 100 万条结果。",
  "快手的最高境界：不用手机。",
  "你发了快手的朋友圈，点赞的都是机器人。",
  "快手的时候，你摸出手机刷了 1 小时。",
  "你下载了快手 APP，占了 1G 内存。",
  "你问朋友快手怎么样，朋友说不如玩手机。",
  "快手结束了，你觉得浪费时间但很快乐。",
  "你说再也不快手了，结果快手了一下午。",
  "快手的时候，手机掉电 50%。",
  "你被快手的广告轰炸了一整天。",
  "你问朋友快手怎么样，朋友说不如玩手机。",
  "你在快手，突然想到手机没电了。",
  "你拍了快手的照片，修图修了 2 小时。",
  "快手的最高境界：不用手机。",
  "快手结束了，你觉得浪费时间但很快乐。",
  "你下载了快手 APP，占了 1G 内存。",
  "你搜索快手，出来了 100 万条结果。",
];

const REPLY_BULK2_107 = [
  "你问 SiriB站是什么，Siri 说不知道。",
  "你发了B站的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个B站攻略，一个也没看。",
  "你收藏了 100 个B站攻略，一个也没看。",
  "你问 SiriB站是什么，Siri 说不知道。",
  "B站的教程看了 50 个，还是不会。",
  "你下载了B站 APP，占了 1G 内存。",
  "B站的时候，手机掉电 50%。",
  "B站的教程看了 50 个，还是不会。",
  "B站的时候，你摸出手机刷了 1 小时。",
  "你问 SiriB站是什么，Siri 说不知道。",
  "你问朋友B站怎么样，朋友说不如玩手机。",
  "你收藏了 100 个B站攻略，一个也没看。",
  "B站的时候，你摸出手机刷了 1 小时。",
  "B站的正确做法：放下手机去做。",
  "B站的时候，你摸出手机刷了 1 小时。",
  "B站的时候，你回复了 100 条消息。",
  "你发了B站的朋友圈，点赞的都是机器人。",
  "你搜索B站，出来了 100 万条结果。",
  "B站的最高境界：不用手机。",
];

const REPLY_BULK2_108 = [
  "知乎的教程看了 50 个，还是不会。",
  "你发了知乎的朋友圈，点赞的都是机器人。",
  "你在知乎，突然想到手机没电了。",
  "你说再也不知乎了，结果知乎了一下午。",
  "你发了知乎的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个知乎攻略，一个也没看。",
  "知乎花了你 1000 块，结果啥也没得到。",
  "你拍了知乎的照片，修图修了 2 小时。",
  "知乎的时候，你摸出手机刷了 1 小时。",
  "知乎的时候，手机烫得像烙铁。",
  "知乎的最高境界：不用手机。",
  "你搜索知乎，出来了 100 万条结果。",
  "知乎结束了，你觉得浪费时间但很快乐。",
  "你发了知乎的朋友圈，点赞的都是机器人。",
  "知乎的最高境界：不用手机。",
  "你问 Siri知乎是什么，Siri 说不知道。",
  "知乎的时候，你回复了 100 条消息。",
  "知乎的最高境界：不用手机。",
  "你发了知乎的朋友圈，点赞的都是机器人。",
  "知乎排行榜第一：你。第二：没有人。",
];

const REPLY_BULK2_109 = [
  "豆瓣排行榜第一：你。第二：没有人。",
  "豆瓣的教程看了 50 个，还是不会。",
  "你被豆瓣的广告轰炸了一整天。",
  "你在豆瓣，突然想到手机没电了。",
  "你被豆瓣的广告轰炸了一整天。",
  "豆瓣排行榜第一：你。第二：没有人。",
  "豆瓣的最高境界：不用手机。",
  "豆瓣的正确做法：放下手机去做。",
  "你在豆瓣，突然想到手机没电了。",
  "你搜索豆瓣，出来了 100 万条结果。",
  "豆瓣结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个豆瓣攻略，一个也没看。",
  "你收藏了 100 个豆瓣攻略，一个也没看。",
  "你被豆瓣的广告轰炸了一整天。",
  "你问 Siri豆瓣是什么，Siri 说不知道。",
  "豆瓣的最高境界：不用手机。",
  "豆瓣排行榜第一：你。第二：没有人。",
  "你问朋友豆瓣怎么样，朋友说不如玩手机。",
  "豆瓣结束了，你觉得浪费时间但很快乐。",
  "你下载了豆瓣 APP，占了 1G 内存。",
];

const REPLY_BULK2_110 = [
  "贴吧的时候，手机烫得像烙铁。",
  "贴吧的时候，你回复了 100 条消息。",
  "贴吧的正确做法：放下手机去做。",
  "贴吧结束了，你觉得浪费时间但很快乐。",
  "你说再也不贴吧了，结果贴吧了一下午。",
  "贴吧结束了，你觉得浪费时间但很快乐。",
  "贴吧的时候，手机掉电 50%。",
  "贴吧的时候，手机烫得像烙铁。",
  "你说再也不贴吧了，结果贴吧了一下午。",
  "贴吧排行榜第一：你。第二：没有人。",
  "你拍了贴吧的照片，修图修了 2 小时。",
  "贴吧的最高境界：不用手机。",
  "你问 Siri贴吧是什么，Siri 说不知道。",
  "贴吧的时候，你摸出手机刷了 1 小时。",
  "你搜索贴吧，出来了 100 万条结果。",
  "贴吧的时候，你摸出手机刷了 1 小时。",
  "贴吧排行榜第一：你。第二：没有人。",
  "你在贴吧，突然想到手机没电了。",
  "贴吧的最高境界：不用手机。",
  "你问 Siri贴吧是什么，Siri 说不知道。",
];

const REPLY_BULK2_111 = [
  "你被淘宝的广告轰炸了一整天。",
  "你被淘宝的广告轰炸了一整天。",
  "你问朋友淘宝怎么样，朋友说不如玩手机。",
  "淘宝的时候，手机烫得像烙铁。",
  "你说再也不淘宝了，结果淘宝了一下午。",
  "你拍了淘宝的照片，修图修了 2 小时。",
  "淘宝的时候，手机烫得像烙铁。",
  "你在淘宝，突然想到手机没电了。",
  "你收藏了 100 个淘宝攻略，一个也没看。",
  "你搜索淘宝，出来了 100 万条结果。",
  "你下载了淘宝 APP，占了 1G 内存。",
  "你搜索淘宝，出来了 100 万条结果。",
  "你问 Siri淘宝是什么，Siri 说不知道。",
  "你说再也不淘宝了，结果淘宝了一下午。",
  "淘宝的最高境界：不用手机。",
  "你拍了淘宝的照片，修图修了 2 小时。",
  "淘宝的正确做法：放下手机去做。",
  "淘宝的时候，手机掉电 50%。",
  "淘宝的时候，你摸出手机刷了 1 小时。",
  "淘宝的时候，你回复了 100 条消息。",
];

const REPLY_BULK2_112 = [
  "京东的时候，手机掉电 50%。",
  "京东排行榜第一：你。第二：没有人。",
  "你问朋友京东怎么样，朋友说不如玩手机。",
  "你被京东的广告轰炸了一整天。",
  "京东的正确做法：放下手机去做。",
  "京东的时候，你回复了 100 条消息。",
  "京东的教程看了 50 个，还是不会。",
  "你搜索京东，出来了 100 万条结果。",
  "京东的教程看了 50 个，还是不会。",
  "你拍了京东的照片，修图修了 2 小时。",
  "你搜索京东，出来了 100 万条结果。",
  "京东排行榜第一：你。第二：没有人。",
  "你发了京东的朋友圈，点赞的都是机器人。",
  "你问朋友京东怎么样，朋友说不如玩手机。",
  "京东结束了，你觉得浪费时间但很快乐。",
  "你问朋友京东怎么样，朋友说不如玩手机。",
  "京东的正确做法：放下手机去做。",
  "你在京东，突然想到手机没电了。",
  "京东排行榜第一：你。第二：没有人。",
  "你在京东，突然想到手机没电了。",
];

const REPLY_BULK2_113 = [
  "拼多多结束了，你觉得浪费时间但很快乐。",
  "拼多多的时候，你回复了 100 条消息。",
  "你收藏了 100 个拼多多攻略，一个也没看。",
  "拼多多的时候，手机掉电 50%。",
  "你收藏了 100 个拼多多攻略，一个也没看。",
  "拼多多排行榜第一：你。第二：没有人。",
  "拼多多结束了，你觉得浪费时间但很快乐。",
  "你搜索拼多多，出来了 100 万条结果。",
  "你搜索拼多多，出来了 100 万条结果。",
  "拼多多的时候，你回复了 100 条消息。",
  "你拍了拼多多的照片，修图修了 2 小时。",
  "拼多多的时候，你摸出手机刷了 1 小时。",
  "你发了拼多多的朋友圈，点赞的都是机器人。",
  "拼多多的最高境界：不用手机。",
  "拼多多的正确做法：放下手机去做。",
  "你被拼多多的广告轰炸了一整天。",
  "拼多多的正确做法：放下手机去做。",
  "拼多多的时候，手机烫得像烙铁。",
  "拼多多排行榜第一：你。第二：没有人。",
  "你说再也不拼多多了，结果拼多多了一下午。",
];

const REPLY_BULK2_114 = [
  "你被闲鱼的广告轰炸了一整天。",
  "你在闲鱼，突然想到手机没电了。",
  "闲鱼花了你 1000 块，结果啥也没得到。",
  "闲鱼的时候，你回复了 100 条消息。",
  "你说再也不闲鱼了，结果闲鱼了一下午。",
  "你问朋友闲鱼怎么样，朋友说不如玩手机。",
  "你问 Siri闲鱼是什么，Siri 说不知道。",
  "你收藏了 100 个闲鱼攻略，一个也没看。",
  "闲鱼的教程看了 50 个，还是不会。",
  "闲鱼的时候，手机烫得像烙铁。",
  "你问朋友闲鱼怎么样，朋友说不如玩手机。",
  "闲鱼的时候，你摸出手机刷了 1 小时。",
  "闲鱼的最高境界：不用手机。",
  "闲鱼的正确做法：放下手机去做。",
  "闲鱼的时候，手机掉电 50%。",
  "闲鱼排行榜第一：你。第二：没有人。",
  "闲鱼的教程看了 50 个，还是不会。",
  "闲鱼的时候，你回复了 100 条消息。",
  "闲鱼的正确做法：放下手机去做。",
  "闲鱼的时候，手机烫得像烙铁。",
];

const REPLY_BULK2_115 = [
  "得物排行榜第一：你。第二：没有人。",
  "得物的教程看了 50 个，还是不会。",
  "得物花了你 1000 块，结果啥也没得到。",
  "你问朋友得物怎么样，朋友说不如玩手机。",
  "得物花了你 1000 块，结果啥也没得到。",
  "你说再也不得物了，结果得物了一下午。",
  "得物的时候，手机烫得像烙铁。",
  "得物的时候，手机掉电 50%。",
  "你拍了得物的照片，修图修了 2 小时。",
  "得物结束了，你觉得浪费时间但很快乐。",
  "得物的时候，手机烫得像烙铁。",
  "得物结束了，你觉得浪费时间但很快乐。",
  "你问朋友得物怎么样，朋友说不如玩手机。",
  "得物的时候，手机烫得像烙铁。",
  "得物的时候，你摸出手机刷了 1 小时。",
  "你问朋友得物怎么样，朋友说不如玩手机。",
  "得物的时候，你摸出手机刷了 1 小时。",
  "得物的最高境界：不用手机。",
  "得物的时候，手机烫得像烙铁。",
  "你问朋友得物怎么样，朋友说不如玩手机。",
];

const REPLY_BULK2_116 = [
  "唯品会的时候，手机掉电 50%。",
  "唯品会花了你 1000 块，结果啥也没得到。",
  "你在唯品会，突然想到手机没电了。",
  "唯品会的最高境界：不用手机。",
  "你发了唯品会的朋友圈，点赞的都是机器人。",
  "你说再也不唯品会了，结果唯品会了一下午。",
  "你被唯品会的广告轰炸了一整天。",
  "你说再也不唯品会了，结果唯品会了一下午。",
  "你发了唯品会的朋友圈，点赞的都是机器人。",
  "唯品会的时候，你摸出手机刷了 1 小时。",
  "你拍了唯品会的照片，修图修了 2 小时。",
  "你在唯品会，突然想到手机没电了。",
  "唯品会的时候，手机烫得像烙铁。",
  "你说再也不唯品会了，结果唯品会了一下午。",
  "你下载了唯品会 APP，占了 1G 内存。",
  "你问朋友唯品会怎么样，朋友说不如玩手机。",
  "唯品会的正确做法：放下手机去做。",
  "唯品会的正确做法：放下手机去做。",
  "唯品会排行榜第一：你。第二：没有人。",
  "你下载了唯品会 APP，占了 1G 内存。",
];

const REPLY_BULK2_117 = [
  "苏宁的时候，你摸出手机刷了 1 小时。",
  "你在苏宁，突然想到手机没电了。",
  "你被苏宁的广告轰炸了一整天。",
  "你拍了苏宁的照片，修图修了 2 小时。",
  "你问 Siri苏宁是什么，Siri 说不知道。",
  "你说再也不苏宁了，结果苏宁了一下午。",
  "苏宁的正确做法：放下手机去做。",
  "你拍了苏宁的照片，修图修了 2 小时。",
  "苏宁的时候，你回复了 100 条消息。",
  "苏宁的时候，你回复了 100 条消息。",
  "你搜索苏宁，出来了 100 万条结果。",
  "苏宁的时候，你回复了 100 条消息。",
  "苏宁的时候，手机掉电 50%。",
  "你拍了苏宁的照片，修图修了 2 小时。",
  "你搜索苏宁，出来了 100 万条结果。",
  "苏宁排行榜第一：你。第二：没有人。",
  "苏宁结束了，你觉得浪费时间但很快乐。",
  "你被苏宁的广告轰炸了一整天。",
  "苏宁的时候，手机烫得像烙铁。",
  "苏宁的最高境界：不用手机。",
];

const REPLY_BULK2_118 = [
  "国美排行榜第一：你。第二：没有人。",
  "你问 Siri国美是什么，Siri 说不知道。",
  "国美的时候，手机烫得像烙铁。",
  "你说再也不国美了，结果国美了一下午。",
  "国美的正确做法：放下手机去做。",
  "你在国美，突然想到手机没电了。",
  "你问 Siri国美是什么，Siri 说不知道。",
  "国美的时候，手机烫得像烙铁。",
  "国美的时候，你回复了 100 条消息。",
  "你说再也不国美了，结果国美了一下午。",
  "你发了国美的朋友圈，点赞的都是机器人。",
  "国美排行榜第一：你。第二：没有人。",
  "国美的正确做法：放下手机去做。",
  "国美排行榜第一：你。第二：没有人。",
  "国美的时候，你摸出手机刷了 1 小时。",
  "你问朋友国美怎么样，朋友说不如玩手机。",
  "国美的时候，手机烫得像烙铁。",
  "国美的正确做法：放下手机去做。",
  "国美的时候，你回复了 100 条消息。",
  "你下载了国美 APP，占了 1G 内存。",
];

const REPLY_BULK2_119 = [
  "你下载了当当 APP，占了 1G 内存。",
  "当当的时候，你摸出手机刷了 1 小时。",
  "你拍了当当的照片，修图修了 2 小时。",
  "当当的时候，手机掉电 50%。",
  "当当的时候，手机烫得像烙铁。",
  "当当花了你 1000 块，结果啥也没得到。",
  "你说再也不当当了，结果当当了一下午。",
  "当当的时候，你回复了 100 条消息。",
  "当当的教程看了 50 个，还是不会。",
  "你说再也不当当了，结果当当了一下午。",
  "你问 Siri当当是什么，Siri 说不知道。",
  "你在当当，突然想到手机没电了。",
  "当当结束了，你觉得浪费时间但很快乐。",
  "你发了当当的朋友圈，点赞的都是机器人。",
  "你发了当当的朋友圈，点赞的都是机器人。",
  "当当排行榜第一：你。第二：没有人。",
  "当当结束了，你觉得浪费时间但很快乐。",
  "当当排行榜第一：你。第二：没有人。",
  "当当排行榜第一：你。第二：没有人。",
  "你被当当的广告轰炸了一整天。",
];

const REPLY_BULK2_120 = [
  "你下载了亚马逊 APP，占了 1G 内存。",
  "亚马逊的教程看了 50 个，还是不会。",
  "亚马逊的时候，你摸出手机刷了 1 小时。",
  "你拍了亚马逊的照片，修图修了 2 小时。",
  "亚马逊的时候，手机烫得像烙铁。",
  "你下载了亚马逊 APP，占了 1G 内存。",
  "亚马逊的正确做法：放下手机去做。",
  "亚马逊结束了，你觉得浪费时间但很快乐。",
  "你发了亚马逊的朋友圈，点赞的都是机器人。",
  "你问朋友亚马逊怎么样，朋友说不如玩手机。",
  "亚马逊结束了，你觉得浪费时间但很快乐。",
  "亚马逊排行榜第一：你。第二：没有人。",
  "你搜索亚马逊，出来了 100 万条结果。",
  "亚马逊的时候，你回复了 100 条消息。",
  "亚马逊的时候，手机掉电 50%。",
  "亚马逊花了你 1000 块，结果啥也没得到。",
  "你发了亚马逊的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个亚马逊攻略，一个也没看。",
  "你问 Siri亚马逊是什么，Siri 说不知道。",
  "亚马逊的教程看了 50 个，还是不会。",
];

// 汇总第二波
const REPLY_BULK2_ALL = [
  ...REPLY_BULK2_001,
  ...REPLY_BULK2_002,
  ...REPLY_BULK2_003,
  ...REPLY_BULK2_004,
  ...REPLY_BULK2_005,
  ...REPLY_BULK2_006,
  ...REPLY_BULK2_007,
  ...REPLY_BULK2_008,
  ...REPLY_BULK2_009,
  ...REPLY_BULK2_010,
  ...REPLY_BULK2_011,
  ...REPLY_BULK2_012,
  ...REPLY_BULK2_013,
  ...REPLY_BULK2_014,
  ...REPLY_BULK2_015,
  ...REPLY_BULK2_016,
  ...REPLY_BULK2_017,
  ...REPLY_BULK2_018,
  ...REPLY_BULK2_019,
  ...REPLY_BULK2_020,
  ...REPLY_BULK2_021,
  ...REPLY_BULK2_022,
  ...REPLY_BULK2_023,
  ...REPLY_BULK2_024,
  ...REPLY_BULK2_025,
  ...REPLY_BULK2_026,
  ...REPLY_BULK2_027,
  ...REPLY_BULK2_028,
  ...REPLY_BULK2_029,
  ...REPLY_BULK2_030,
  ...REPLY_BULK2_031,
  ...REPLY_BULK2_032,
  ...REPLY_BULK2_033,
  ...REPLY_BULK2_034,
  ...REPLY_BULK2_035,
  ...REPLY_BULK2_036,
  ...REPLY_BULK2_037,
  ...REPLY_BULK2_038,
  ...REPLY_BULK2_039,
  ...REPLY_BULK2_040,
  ...REPLY_BULK2_041,
  ...REPLY_BULK2_042,
  ...REPLY_BULK2_043,
  ...REPLY_BULK2_044,
  ...REPLY_BULK2_045,
  ...REPLY_BULK2_046,
  ...REPLY_BULK2_047,
  ...REPLY_BULK2_048,
  ...REPLY_BULK2_049,
  ...REPLY_BULK2_050,
  ...REPLY_BULK2_051,
  ...REPLY_BULK2_052,
  ...REPLY_BULK2_053,
  ...REPLY_BULK2_054,
  ...REPLY_BULK2_055,
  ...REPLY_BULK2_056,
  ...REPLY_BULK2_057,
  ...REPLY_BULK2_058,
  ...REPLY_BULK2_059,
  ...REPLY_BULK2_060,
  ...REPLY_BULK2_061,
  ...REPLY_BULK2_062,
  ...REPLY_BULK2_063,
  ...REPLY_BULK2_064,
  ...REPLY_BULK2_065,
  ...REPLY_BULK2_066,
  ...REPLY_BULK2_067,
  ...REPLY_BULK2_068,
  ...REPLY_BULK2_069,
  ...REPLY_BULK2_070,
  ...REPLY_BULK2_071,
  ...REPLY_BULK2_072,
  ...REPLY_BULK2_073,
  ...REPLY_BULK2_074,
  ...REPLY_BULK2_075,
  ...REPLY_BULK2_076,
  ...REPLY_BULK2_077,
  ...REPLY_BULK2_078,
  ...REPLY_BULK2_079,
  ...REPLY_BULK2_080,
  ...REPLY_BULK2_081,
  ...REPLY_BULK2_082,
  ...REPLY_BULK2_083,
  ...REPLY_BULK2_084,
  ...REPLY_BULK2_085,
  ...REPLY_BULK2_086,
  ...REPLY_BULK2_087,
  ...REPLY_BULK2_088,
  ...REPLY_BULK2_089,
  ...REPLY_BULK2_090,
  ...REPLY_BULK2_091,
  ...REPLY_BULK2_092,
  ...REPLY_BULK2_093,
  ...REPLY_BULK2_094,
  ...REPLY_BULK2_095,
  ...REPLY_BULK2_096,
  ...REPLY_BULK2_097,
  ...REPLY_BULK2_098,
  ...REPLY_BULK2_099,
  ...REPLY_BULK2_100,
  ...REPLY_BULK2_101,
  ...REPLY_BULK2_102,
  ...REPLY_BULK2_103,
  ...REPLY_BULK2_104,
  ...REPLY_BULK2_105,
  ...REPLY_BULK2_106,
  ...REPLY_BULK2_107,
  ...REPLY_BULK2_108,
  ...REPLY_BULK2_109,
  ...REPLY_BULK2_110,
  ...REPLY_BULK2_111,
  ...REPLY_BULK2_112,
  ...REPLY_BULK2_113,
  ...REPLY_BULK2_114,
  ...REPLY_BULK2_115,
  ...REPLY_BULK2_116,
  ...REPLY_BULK2_117,
  ...REPLY_BULK2_118,
  ...REPLY_BULK2_119,
  ...REPLY_BULK2_120,
];

// 所有批量台词合并
const REPLY_ALL_BULK = [...REPLY_BULK_ALL, ...REPLY_BULK2_ALL];

/* ============================================================
   G.331~G.430 第三波超大规模批量主题台词库
   ============================================================ */

const REPLY_BULK3_001 = [
  "早餐结束了，你觉得浪费时间但很快乐。",
  "早餐的最高境界：不用手机。",
  "你在早餐，突然想起手机没电了。",
  "早餐结束了，你觉得浪费时间但很快乐。",
  "早餐结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个早餐攻略，一个也没看。",
  "早餐的最高境界：不用手机。",
  "你在早餐，突然想起手机没电了。",
  "你问朋友早餐怎么样，朋友说一般。",
  "早餐花了你 1000 块，结果啥也没得到。",
  "早餐的正确做法：放下手机去做。",
  "早餐的正确做法：放下手机去做。",
  "早餐结束了，你觉得浪费时间但很快乐。",
  "你搜索早餐，出来了 100 万条结果。",
  "你在早餐，突然想起手机没电了。",
  "你问 Siri早餐是什么，Siri 说不知道。",
  "你搜索早餐，出来了 100 万条结果。",
  "早餐的正确做法：放下手机去做。",
  "早餐的时候，手机掉电 50%。",
  "早餐的时候，你刷了 1 小时短视频。",
];

const REPLY_BULK3_002 = [
  "午餐的正确做法：放下手机去做。",
  "你问朋友午餐怎么样，朋友说一般。",
  "你在午餐，突然想起手机没电了。",
  "你在午餐，突然想起手机没电了。",
  "午餐花了你 1000 块，结果啥也没得到。",
  "午餐的教程看了 50 个，还是不会。",
  "你问 Siri午餐是什么，Siri 说不知道。",
  "你下载了午餐 APP，占了 1G 内存。",
  "午餐花了你 1000 块，结果啥也没得到。",
  "午餐的时候，手机烫得像烙铁。",
  "午餐的时候，你回复了 100 条消息。",
  "你搜索午餐，出来了 100 万条结果。",
  "午餐的正确做法：放下手机去做。",
  "你被午餐的广告轰炸了一整天。",
  "你说再也不午餐了，结果又午餐了一下午。",
  "午餐的教程看了 50 个，还是不会。",
  "午餐的最高境界：不用手机。",
  "午餐的时候，你回复了 100 条消息。",
  "你发了午餐的朋友圈，点赞的都是机器人。",
  "你拍了午餐的照片，修图修了 2 小时。",
];

const REPLY_BULK3_003 = [
  "晚餐的时候，手机烫得像烙铁。",
  "晚餐结束了，你觉得浪费时间但很快乐。",
  "你问 Siri晚餐是什么，Siri 说不知道。",
  "你问朋友晚餐怎么样，朋友说一般。",
  "晚餐的时候，手机掉电 50%。",
  "晚餐的最高境界：不用手机。",
  "晚餐结束了，你觉得浪费时间但很快乐。",
  "晚餐的时候，手机烫得像烙铁。",
  "你收藏了 100 个晚餐攻略，一个也没看。",
  "你在晚餐，突然想起手机没电了。",
  "晚餐的教程看了 50 个，还是不会。",
  "你搜索晚餐，出来了 100 万条结果。",
  "晚餐的教程看了 50 个，还是不会。",
  "晚餐花了你 1000 块，结果啥也没得到。",
  "晚餐的时候，手机烫得像烙铁。",
  "晚餐结束了，你觉得浪费时间但很快乐。",
  "晚餐的教程看了 50 个，还是不会。",
  "晚餐的最高境界：不用手机。",
  "你问 Siri晚餐是什么，Siri 说不知道。",
  "你被晚餐的广告轰炸了一整天。",
];

const REPLY_BULK3_004 = [
  "你搜索宵夜，出来了 100 万条结果。",
  "宵夜的时候，手机掉电 50%。",
  "宵夜的时候，手机烫得像烙铁。",
  "宵夜排行榜第一：你。",
  "宵夜的时候，你刷了 1 小时短视频。",
  "宵夜的教程看了 50 个，还是不会。",
  "你问 Siri宵夜是什么，Siri 说不知道。",
  "你问朋友宵夜怎么样，朋友说一般。",
  "你收藏了 100 个宵夜攻略，一个也没看。",
  "你发了宵夜的朋友圈，点赞的都是机器人。",
  "你被宵夜的广告轰炸了一整天。",
  "宵夜结束了，你觉得浪费时间但很快乐。",
  "你下载了宵夜 APP，占了 1G 内存。",
  "宵夜的时候，手机掉电 50%。",
  "你收藏了 100 个宵夜攻略，一个也没看。",
  "你搜索宵夜，出来了 100 万条结果。",
  "你问朋友宵夜怎么样，朋友说一般。",
  "宵夜的时候，你回复了 100 条消息。",
  "宵夜的时候，你回复了 100 条消息。",
  "宵夜排行榜第一：你。",
];

const REPLY_BULK3_005 = [
  "奶茶的正确做法：放下手机去做。",
  "你问 Siri奶茶是什么，Siri 说不知道。",
  "你发了奶茶的朋友圈，点赞的都是机器人。",
  "奶茶的时候，你刷了 1 小时短视频。",
  "你问 Siri奶茶是什么，Siri 说不知道。",
  "你说再也不奶茶了，结果又奶茶了一下午。",
  "你问 Siri奶茶是什么，Siri 说不知道。",
  "奶茶的时候，手机烫得像烙铁。",
  "奶茶花了你 1000 块，结果啥也没得到。",
  "奶茶排行榜第一：你。",
  "你在奶茶，突然想起手机没电了。",
  "你问 Siri奶茶是什么，Siri 说不知道。",
  "你搜索奶茶，出来了 100 万条结果。",
  "奶茶的教程看了 50 个，还是不会。",
  "奶茶的时候，你回复了 100 条消息。",
  "奶茶的时候，手机烫得像烙铁。",
  "奶茶的时候，你刷了 1 小时短视频。",
  "你在奶茶，突然想起手机没电了。",
  "你被奶茶的广告轰炸了一整天。",
  "你被奶茶的广告轰炸了一整天。",
];

const REPLY_BULK3_006 = [
  "咖啡排行榜第一：你。",
  "你说再也不咖啡了，结果又咖啡了一下午。",
  "你发了咖啡的朋友圈，点赞的都是机器人。",
  "你拍了咖啡的照片，修图修了 2 小时。",
  "你问朋友咖啡怎么样，朋友说一般。",
  "你拍了咖啡的照片，修图修了 2 小时。",
  "咖啡的正确做法：放下手机去做。",
  "你拍了咖啡的照片，修图修了 2 小时。",
  "你收藏了 100 个咖啡攻略，一个也没看。",
  "咖啡的时候，你回复了 100 条消息。",
  "你问朋友咖啡怎么样，朋友说一般。",
  "你搜索咖啡，出来了 100 万条结果。",
  "你问朋友咖啡怎么样，朋友说一般。",
  "咖啡的时候，手机烫得像烙铁。",
  "你被咖啡的广告轰炸了一整天。",
  "你在咖啡，突然想起手机没电了。",
  "你在咖啡，突然想起手机没电了。",
  "咖啡花了你 1000 块，结果啥也没得到。",
  "咖啡的最高境界：不用手机。",
  "咖啡的正确做法：放下手机去做。",
];

const REPLY_BULK3_007 = [
  "你下载了火锅 APP，占了 1G 内存。",
  "火锅的时候，你刷了 1 小时短视频。",
  "火锅排行榜第一：你。",
  "你收藏了 100 个火锅攻略，一个也没看。",
  "你搜索火锅，出来了 100 万条结果。",
  "火锅的教程看了 50 个，还是不会。",
  "火锅的时候，手机掉电 50%。",
  "火锅的最高境界：不用手机。",
  "火锅的教程看了 50 个，还是不会。",
  "你在火锅，突然想起手机没电了。",
  "你在火锅，突然想起手机没电了。",
  "火锅的最高境界：不用手机。",
  "火锅结束了，你觉得浪费时间但很快乐。",
  "火锅的时候，你回复了 100 条消息。",
  "火锅的时候，你刷了 1 小时短视频。",
  "你被火锅的广告轰炸了一整天。",
  "火锅花了你 1000 块，结果啥也没得到。",
  "火锅的时候，手机掉电 50%。",
  "你下载了火锅 APP，占了 1G 内存。",
  "火锅结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK3_008 = [
  "烧烤结束了，你觉得浪费时间但很快乐。",
  "烧烤的时候，手机烫得像烙铁。",
  "烧烤的时候，你刷了 1 小时短视频。",
  "你在烧烤，突然想起手机没电了。",
  "烧烤花了你 1000 块，结果啥也没得到。",
  "你搜索烧烤，出来了 100 万条结果。",
  "烧烤的最高境界：不用手机。",
  "烧烤的时候，手机掉电 50%。",
  "烧烤排行榜第一：你。",
  "烧烤的时候，你回复了 100 条消息。",
  "烧烤的时候，你刷了 1 小时短视频。",
  "烧烤花了你 1000 块，结果啥也没得到。",
  "你问 Siri烧烤是什么，Siri 说不知道。",
  "烧烤排行榜第一：你。",
  "你发了烧烤的朋友圈，点赞的都是机器人。",
  "烧烤花了你 1000 块，结果啥也没得到。",
  "你在烧烤，突然想起手机没电了。",
  "烧烤的教程看了 50 个，还是不会。",
  "烧烤的正确做法：放下手机去做。",
  "烧烤的正确做法：放下手机去做。",
];

const REPLY_BULK3_009 = [
  "你问 Siri串串是什么，Siri 说不知道。",
  "你拍了串串的照片，修图修了 2 小时。",
  "串串的时候，手机掉电 50%。",
  "串串的时候，你回复了 100 条消息。",
  "串串的时候，手机掉电 50%。",
  "串串的时候，手机掉电 50%。",
  "串串结束了，你觉得浪费时间但很快乐。",
  "串串的正确做法：放下手机去做。",
  "你在串串，突然想起手机没电了。",
  "你发了串串的朋友圈，点赞的都是机器人。",
  "串串的时候，手机烫得像烙铁。",
  "串串结束了，你觉得浪费时间但很快乐。",
  "串串的时候，手机掉电 50%。",
  "你拍了串串的照片，修图修了 2 小时。",
  "串串的时候，手机掉电 50%。",
  "你说再也不串串了，结果又串串了一下午。",
  "你被串串的广告轰炸了一整天。",
  "串串的时候，手机掉电 50%。",
  "串串结束了，你觉得浪费时间但很快乐。",
  "你问朋友串串怎么样，朋友说一般。",
];

const REPLY_BULK3_010 = [
  "寿司的时候，手机掉电 50%。",
  "寿司结束了，你觉得浪费时间但很快乐。",
  "你在寿司，突然想起手机没电了。",
  "寿司的时候，你回复了 100 条消息。",
  "寿司的最高境界：不用手机。",
  "你在寿司，突然想起手机没电了。",
  "寿司的时候，你回复了 100 条消息。",
  "你下载了寿司 APP，占了 1G 内存。",
  "寿司的时候，你回复了 100 条消息。",
  "你被寿司的广告轰炸了一整天。",
  "你问 Siri寿司是什么，Siri 说不知道。",
  "你被寿司的广告轰炸了一整天。",
  "寿司的时候，你回复了 100 条消息。",
  "寿司的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个寿司攻略，一个也没看。",
  "寿司排行榜第一：你。",
  "你下载了寿司 APP，占了 1G 内存。",
  "寿司的时候，你刷了 1 小时短视频。",
  "寿司排行榜第一：你。",
  "寿司的最高境界：不用手机。",
];

const REPLY_BULK3_011 = [
  "你被地铁的广告轰炸了一整天。",
  "地铁的时候，手机掉电 50%。",
  "地铁结束了，你觉得浪费时间但很快乐。",
  "你被地铁的广告轰炸了一整天。",
  "你下载了地铁 APP，占了 1G 内存。",
  "地铁的教程看了 50 个，还是不会。",
  "地铁的时候，手机烫得像烙铁。",
  "你说再也不地铁了，结果又地铁了一下午。",
  "你在地铁，突然想起手机没电了。",
  "地铁的时候，手机掉电 50%。",
  "你收藏了 100 个地铁攻略，一个也没看。",
  "地铁的最高境界：不用手机。",
  "地铁的正确做法：放下手机去做。",
  "地铁的正确做法：放下手机去做。",
  "地铁的教程看了 50 个，还是不会。",
  "你被地铁的广告轰炸了一整天。",
  "地铁的教程看了 50 个，还是不会。",
  "地铁排行榜第一：你。",
  "地铁结束了，你觉得浪费时间但很快乐。",
  "你搜索地铁，出来了 100 万条结果。",
];

const REPLY_BULK3_012 = [
  "公交花了你 1000 块，结果啥也没得到。",
  "你发了公交的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个公交攻略，一个也没看。",
  "公交的时候，你回复了 100 条消息。",
  "你拍了公交的照片，修图修了 2 小时。",
  "公交的时候，你刷了 1 小时短视频。",
  "公交的时候，你回复了 100 条消息。",
  "公交的时候，手机掉电 50%。",
  "公交结束了，你觉得浪费时间但很快乐。",
  "公交的最高境界：不用手机。",
  "你问朋友公交怎么样，朋友说一般。",
  "公交的时候，你刷了 1 小时短视频。",
  "公交的时候，你刷了 1 小时短视频。",
  "公交的教程看了 50 个，还是不会。",
  "你搜索公交，出来了 100 万条结果。",
  "你问朋友公交怎么样，朋友说一般。",
  "你下载了公交 APP，占了 1G 内存。",
  "你在公交，突然想起手机没电了。",
  "公交结束了，你觉得浪费时间但很快乐。",
  "你问朋友公交怎么样，朋友说一般。",
];

const REPLY_BULK3_013 = [
  "打车的正确做法：放下手机去做。",
  "你在打车，突然想起手机没电了。",
  "打车的正确做法：放下手机去做。",
  "打车排行榜第一：你。",
  "打车花了你 1000 块，结果啥也没得到。",
  "打车的时候，手机烫得像烙铁。",
  "你问朋友打车怎么样，朋友说一般。",
  "打车的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个打车攻略，一个也没看。",
  "你发了打车的朋友圈，点赞的都是机器人。",
  "打车的教程看了 50 个，还是不会。",
  "你拍了打车的照片，修图修了 2 小时。",
  "打车的正确做法：放下手机去做。",
  "打车的最高境界：不用手机。",
  "你下载了打车 APP，占了 1G 内存。",
  "打车花了你 1000 块，结果啥也没得到。",
  "你发了打车的朋友圈，点赞的都是机器人。",
  "你发了打车的朋友圈，点赞的都是机器人。",
  "你说再也不打车了，结果又打车了一下午。",
  "打车花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK3_014 = [
  "高铁的时候，你刷了 1 小时短视频。",
  "高铁的最高境界：不用手机。",
  "你收藏了 100 个高铁攻略，一个也没看。",
  "你被高铁的广告轰炸了一整天。",
  "你说再也不高铁了，结果又高铁了一下午。",
  "高铁的教程看了 50 个，还是不会。",
  "你问朋友高铁怎么样，朋友说一般。",
  "你搜索高铁，出来了 100 万条结果。",
  "你说再也不高铁了，结果又高铁了一下午。",
  "高铁排行榜第一：你。",
  "高铁花了你 1000 块，结果啥也没得到。",
  "你被高铁的广告轰炸了一整天。",
  "高铁的时候，手机烫得像烙铁。",
  "高铁的正确做法：放下手机去做。",
  "你搜索高铁，出来了 100 万条结果。",
  "高铁的时候，手机烫得像烙铁。",
  "你说再也不高铁了，结果又高铁了一下午。",
  "高铁排行榜第一：你。",
  "你说再也不高铁了，结果又高铁了一下午。",
  "高铁排行榜第一：你。",
];

const REPLY_BULK3_015 = [
  "你下载了飞机 APP，占了 1G 内存。",
  "你问朋友飞机怎么样，朋友说一般。",
  "你问 Siri飞机是什么，Siri 说不知道。",
  "飞机的时候，手机掉电 50%。",
  "飞机的时候，手机掉电 50%。",
  "你下载了飞机 APP，占了 1G 内存。",
  "你搜索飞机，出来了 100 万条结果。",
  "飞机花了你 1000 块，结果啥也没得到。",
  "飞机的时候，手机烫得像烙铁。",
  "飞机的最高境界：不用手机。",
  "飞机的最高境界：不用手机。",
  "飞机的时候，手机掉电 50%。",
  "你搜索飞机，出来了 100 万条结果。",
  "飞机的最高境界：不用手机。",
  "飞机的时候，你刷了 1 小时短视频。",
  "飞机的时候，你刷了 1 小时短视频。",
  "你说再也不飞机了，结果又飞机了一下午。",
  "飞机排行榜第一：你。",
  "飞机的时候，你刷了 1 小时短视频。",
  "你发了飞机的朋友圈，点赞的都是机器人。",
];

const REPLY_BULK3_016 = [
  "你搜索自驾，出来了 100 万条结果。",
  "自驾的正确做法：放下手机去做。",
  "自驾的时候，你刷了 1 小时短视频。",
  "你问 Siri自驾是什么，Siri 说不知道。",
  "自驾排行榜第一：你。",
  "自驾排行榜第一：你。",
  "自驾排行榜第一：你。",
  "自驾的教程看了 50 个，还是不会。",
  "你发了自驾的朋友圈，点赞的都是机器人。",
  "自驾的最高境界：不用手机。",
  "自驾的时候，你回复了 100 条消息。",
  "自驾排行榜第一：你。",
  "你收藏了 100 个自驾攻略，一个也没看。",
  "你被自驾的广告轰炸了一整天。",
  "自驾的时候，手机烫得像烙铁。",
  "你在自驾，突然想起手机没电了。",
  "自驾的教程看了 50 个，还是不会。",
  "自驾花了你 1000 块，结果啥也没得到。",
  "自驾花了你 1000 块，结果啥也没得到。",
  "你搜索自驾，出来了 100 万条结果。",
];

const REPLY_BULK3_017 = [
  "步行的正确做法：放下手机去做。",
  "步行的时候，你回复了 100 条消息。",
  "步行的教程看了 50 个，还是不会。",
  "步行的教程看了 50 个，还是不会。",
  "你在步行，突然想起手机没电了。",
  "你下载了步行 APP，占了 1G 内存。",
  "你问朋友步行怎么样，朋友说一般。",
  "步行结束了，你觉得浪费时间但很快乐。",
  "你问朋友步行怎么样，朋友说一般。",
  "你搜索步行，出来了 100 万条结果。",
  "你拍了步行的照片，修图修了 2 小时。",
  "你问 Siri步行是什么，Siri 说不知道。",
  "你问朋友步行怎么样，朋友说一般。",
  "步行排行榜第一：你。",
  "你收藏了 100 个步行攻略，一个也没看。",
  "你拍了步行的照片，修图修了 2 小时。",
  "步行的时候，手机掉电 50%。",
  "你问 Siri步行是什么，Siri 说不知道。",
  "你拍了步行的照片，修图修了 2 小时。",
  "你发了步行的朋友圈，点赞的都是机器人。",
];

const REPLY_BULK3_018 = [
  "你问 Siri骑行是什么，Siri 说不知道。",
  "你说再也不骑行了，结果又骑行了一下午。",
  "你被骑行的广告轰炸了一整天。",
  "骑行排行榜第一：你。",
  "骑行的正确做法：放下手机去做。",
  "骑行结束了，你觉得浪费时间但很快乐。",
  "你拍了骑行的照片，修图修了 2 小时。",
  "骑行花了你 1000 块，结果啥也没得到。",
  "你问朋友骑行怎么样，朋友说一般。",
  "骑行的时候，你刷了 1 小时短视频。",
  "你拍了骑行的照片，修图修了 2 小时。",
  "骑行的教程看了 50 个，还是不会。",
  "你收藏了 100 个骑行攻略，一个也没看。",
  "你搜索骑行，出来了 100 万条结果。",
  "骑行的时候，手机掉电 50%。",
  "你发了骑行的朋友圈，点赞的都是机器人。",
  "你搜索骑行，出来了 100 万条结果。",
  "你被骑行的广告轰炸了一整天。",
  "你下载了骑行 APP，占了 1G 内存。",
  "骑行的时候，你回复了 100 条消息。",
];

const REPLY_BULK3_019 = [
  "打车的时候，手机烫得像烙铁。",
  "打车的最高境界：不用手机。",
  "打车的时候，手机掉电 50%。",
  "打车排行榜第一：你。",
  "打车的时候，你回复了 100 条消息。",
  "你在打车，突然想起手机没电了。",
  "你在打车，突然想起手机没电了。",
  "你拍了打车的照片，修图修了 2 小时。",
  "你问朋友打车怎么样，朋友说一般。",
  "你在打车，突然想起手机没电了。",
  "打车的时候，手机掉电 50%。",
  "你搜索打车，出来了 100 万条结果。",
  "打车的正确做法：放下手机去做。",
  "你说再也不打车了，结果又打车了一下午。",
  "你被打车的广告轰炸了一整天。",
  "打车的时候，手机烫得像烙铁。",
  "你说再也不打车了，结果又打车了一下午。",
  "你被打车的广告轰炸了一整天。",
  "打车的正确做法：放下手机去做。",
  "你发了打车的朋友圈，点赞的都是机器人。",
];

const REPLY_BULK3_020 = [
  "你拍了代驾的照片，修图修了 2 小时。",
  "代驾的时候，手机掉电 50%。",
  "你搜索代驾，出来了 100 万条结果。",
  "代驾花了你 1000 块，结果啥也没得到。",
  "代驾排行榜第一：你。",
  "你问 Siri代驾是什么，Siri 说不知道。",
  "你问 Siri代驾是什么，Siri 说不知道。",
  "代驾的时候，你回复了 100 条消息。",
  "你发了代驾的朋友圈，点赞的都是机器人。",
  "代驾的时候，手机掉电 50%。",
  "代驾的时候，你回复了 100 条消息。",
  "你说再也不代驾了，结果又代驾了一下午。",
  "代驾的时候，你回复了 100 条消息。",
  "代驾的时候，你回复了 100 条消息。",
  "代驾花了你 1000 块，结果啥也没得到。",
  "你在代驾，突然想起手机没电了。",
  "代驾的时候，你回复了 100 条消息。",
  "代驾的时候，手机掉电 50%。",
  "代驾的教程看了 50 个，还是不会。",
  "代驾的时候，手机掉电 50%。",
];

const REPLY_BULK3_021 = [
  "租房排行榜第一：你。",
  "租房的正确做法：放下手机去做。",
  "租房的时候，手机掉电 50%。",
  "租房的时候，手机烫得像烙铁。",
  "租房的正确做法：放下手机去做。",
  "租房的时候，手机烫得像烙铁。",
  "租房花了你 1000 块，结果啥也没得到。",
  "租房的最高境界：不用手机。",
  "你被租房的广告轰炸了一整天。",
  "租房的正确做法：放下手机去做。",
  "你问 Siri租房是什么，Siri 说不知道。",
  "你问朋友租房怎么样，朋友说一般。",
  "你下载了租房 APP，占了 1G 内存。",
  "租房的时候，手机烫得像烙铁。",
  "你说再也不租房了，结果又租房了一下午。",
  "你问朋友租房怎么样，朋友说一般。",
  "你问 Siri租房是什么，Siri 说不知道。",
  "你发了租房的朋友圈，点赞的都是机器人。",
  "租房的正确做法：放下手机去做。",
  "你搜索租房，出来了 100 万条结果。",
];

const REPLY_BULK3_022 = [
  "买房结束了，你觉得浪费时间但很快乐。",
  "买房的时候，你回复了 100 条消息。",
  "你搜索买房，出来了 100 万条结果。",
  "你被买房的广告轰炸了一整天。",
  "你收藏了 100 个买房攻略，一个也没看。",
  "你在买房，突然想起手机没电了。",
  "买房排行榜第一：你。",
  "买房的时候，手机烫得像烙铁。",
  "买房花了你 1000 块，结果啥也没得到。",
  "你拍了买房的照片，修图修了 2 小时。",
  "你拍了买房的照片，修图修了 2 小时。",
  "买房的最高境界：不用手机。",
  "买房的时候，手机烫得像烙铁。",
  "你被买房的广告轰炸了一整天。",
  "你被买房的广告轰炸了一整天。",
  "买房的时候，你刷了 1 小时短视频。",
  "买房结束了，你觉得浪费时间但很快乐。",
  "买房花了你 1000 块，结果啥也没得到。",
  "你被买房的广告轰炸了一整天。",
  "你在买房，突然想起手机没电了。",
];

const REPLY_BULK3_023 = [
  "你在装修，突然想起手机没电了。",
  "你说再也不装修了，结果又装修了一下午。",
  "你问 Siri装修是什么，Siri 说不知道。",
  "装修的最高境界：不用手机。",
  "装修排行榜第一：你。",
  "你下载了装修 APP，占了 1G 内存。",
  "装修的教程看了 50 个，还是不会。",
  "装修花了你 1000 块，结果啥也没得到。",
  "你发了装修的朋友圈，点赞的都是机器人。",
  "装修的时候，你刷了 1 小时短视频。",
  "你发了装修的朋友圈，点赞的都是机器人。",
  "你下载了装修 APP，占了 1G 内存。",
  "装修的教程看了 50 个，还是不会。",
  "装修花了你 1000 块，结果啥也没得到。",
  "装修的时候，手机掉电 50%。",
  "装修的时候，你回复了 100 条消息。",
  "你问朋友装修怎么样，朋友说一般。",
  "装修的最高境界：不用手机。",
  "装修的正确做法：放下手机去做。",
  "装修排行榜第一：你。",
];

const REPLY_BULK3_024 = [
  "你下载了搬家 APP，占了 1G 内存。",
  "搬家的时候，手机掉电 50%。",
  "你问朋友搬家怎么样，朋友说一般。",
  "你在搬家，突然想起手机没电了。",
  "你下载了搬家 APP，占了 1G 内存。",
  "你收藏了 100 个搬家攻略，一个也没看。",
  "搬家排行榜第一：你。",
  "你拍了搬家的照片，修图修了 2 小时。",
  "你搜索搬家，出来了 100 万条结果。",
  "你收藏了 100 个搬家攻略，一个也没看。",
  "你收藏了 100 个搬家攻略，一个也没看。",
  "你搜索搬家，出来了 100 万条结果。",
  "你下载了搬家 APP，占了 1G 内存。",
  "搬家花了你 1000 块，结果啥也没得到。",
  "搬家的时候，你回复了 100 条消息。",
  "你下载了搬家 APP，占了 1G 内存。",
  "搬家的最高境界：不用手机。",
  "搬家的时候，你回复了 100 条消息。",
  "你搜索搬家，出来了 100 万条结果。",
  "你搜索搬家，出来了 100 万条结果。",
];

const REPLY_BULK3_025 = [
  "你在保洁，突然想起手机没电了。",
  "保洁的时候，你回复了 100 条消息。",
  "你问朋友保洁怎么样，朋友说一般。",
  "你发了保洁的朋友圈，点赞的都是机器人。",
  "你拍了保洁的照片，修图修了 2 小时。",
  "你搜索保洁，出来了 100 万条结果。",
  "保洁结束了，你觉得浪费时间但很快乐。",
  "保洁的时候，手机烫得像烙铁。",
  "保洁的教程看了 50 个，还是不会。",
  "你发了保洁的朋友圈，点赞的都是机器人。",
  "保洁排行榜第一：你。",
  "保洁排行榜第一：你。",
  "保洁的时候，手机烫得像烙铁。",
  "你问 Siri保洁是什么，Siri 说不知道。",
  "你收藏了 100 个保洁攻略，一个也没看。",
  "保洁的最高境界：不用手机。",
  "你在保洁，突然想起手机没电了。",
  "保洁的正确做法：放下手机去做。",
  "你被保洁的广告轰炸了一整天。",
  "保洁的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_026 = [
  "维修排行榜第一：你。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "你收藏了 100 个维修攻略，一个也没看。",
  "你发了维修的朋友圈，点赞的都是机器人。",
  "维修排行榜第一：你。",
  "你搜索维修，出来了 100 万条结果。",
  "维修的时候，你刷了 1 小时短视频。",
  "维修的正确做法：放下手机去做。",
  "维修花了你 1000 块，结果啥也没得到。",
  "维修的最高境界：不用手机。",
  "维修的时候，你回复了 100 条消息。",
  "维修的时候，手机掉电 50%。",
  "你问 Siri维修是什么，Siri 说不知道。",
  "维修花了你 1000 块，结果啥也没得到。",
  "你下载了维修 APP，占了 1G 内存。",
  "维修排行榜第一：你。",
  "你被维修的广告轰炸了一整天。",
  "你搜索维修，出来了 100 万条结果。",
  "维修的最高境界：不用手机。",
  "你说再也不维修了，结果又维修了一下午。",
];

const REPLY_BULK3_027 = [
  "快递的时候，手机烫得像烙铁。",
  "快递花了你 1000 块，结果啥也没得到。",
  "你被快递的广告轰炸了一整天。",
  "你被快递的广告轰炸了一整天。",
  "你发了快递的朋友圈，点赞的都是机器人。",
  "快递结束了，你觉得浪费时间但很快乐。",
  "你问朋友快递怎么样，朋友说一般。",
  "快递的时候，手机掉电 50%。",
  "快递的时候，手机烫得像烙铁。",
  "你在快递，突然想起手机没电了。",
  "快递结束了，你觉得浪费时间但很快乐。",
  "快递的正确做法：放下手机去做。",
  "你收藏了 100 个快递攻略，一个也没看。",
  "你被快递的广告轰炸了一整天。",
  "你在快递，突然想起手机没电了。",
  "你被快递的广告轰炸了一整天。",
  "你拍了快递的照片，修图修了 2 小时。",
  "快递结束了，你觉得浪费时间但很快乐。",
  "快递的时候，你刷了 1 小时短视频。",
  "你问朋友快递怎么样，朋友说一般。",
];

const REPLY_BULK3_028 = [
  "你搜索外卖，出来了 100 万条结果。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "外卖的正确做法：放下手机去做。",
  "你问 Siri外卖是什么，Siri 说不知道。",
  "外卖排行榜第一：你。",
  "你收藏了 100 个外卖攻略，一个也没看。",
  "你在外卖，突然想起手机没电了。",
  "外卖的教程看了 50 个，还是不会。",
  "你拍了外卖的照片，修图修了 2 小时。",
  "你问 Siri外卖是什么，Siri 说不知道。",
  "你拍了外卖的照片，修图修了 2 小时。",
  "外卖的正确做法：放下手机去做。",
  "外卖结束了，你觉得浪费时间但很快乐。",
  "外卖的时候，手机烫得像烙铁。",
  "你发了外卖的朋友圈，点赞的都是机器人。",
  "外卖的教程看了 50 个，还是不会。",
  "你说再也不外卖了，结果又外卖了一下午。",
  "外卖的时候，手机掉电 50%。",
  "外卖的教程看了 50 个，还是不会。",
  "外卖的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_029 = [
  "你在跑腿，突然想起手机没电了。",
  "你被跑腿的广告轰炸了一整天。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "跑腿的正确做法：放下手机去做。",
  "你收藏了 100 个跑腿攻略，一个也没看。",
  "跑腿的时候，手机掉电 50%。",
  "跑腿结束了，你觉得浪费时间但很快乐。",
  "跑腿的正确做法：放下手机去做。",
  "你搜索跑腿，出来了 100 万条结果。",
  "你说再也不跑腿了，结果又跑腿了一下午。",
  "跑腿的时候，手机掉电 50%。",
  "你下载了跑腿 APP，占了 1G 内存。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "跑腿的时候，你回复了 100 条消息。",
  "跑腿的正确做法：放下手机去做。",
  "你拍了跑腿的照片，修图修了 2 小时。",
  "跑腿结束了，你觉得浪费时间但很快乐。",
  "跑腿结束了，你觉得浪费时间但很快乐。",
  "你被跑腿的广告轰炸了一整天。",
  "跑腿的最高境界：不用手机。",
];

const REPLY_BULK3_030 = [
  "你说再也不代购了，结果又代购了一下午。",
  "你搜索代购，出来了 100 万条结果。",
  "你问朋友代购怎么样，朋友说一般。",
  "代购的教程看了 50 个，还是不会。",
  "代购的时候，手机烫得像烙铁。",
  "你收藏了 100 个代购攻略，一个也没看。",
  "你问朋友代购怎么样，朋友说一般。",
  "你下载了代购 APP，占了 1G 内存。",
  "你问 Siri代购是什么，Siri 说不知道。",
  "你下载了代购 APP，占了 1G 内存。",
  "你拍了代购的照片，修图修了 2 小时。",
  "代购的时候，你回复了 100 条消息。",
  "代购的最高境界：不用手机。",
  "你被代购的广告轰炸了一整天。",
  "代购的最高境界：不用手机。",
  "你收藏了 100 个代购攻略，一个也没看。",
  "代购的时候，你刷了 1 小时短视频。",
  "代购排行榜第一：你。",
  "代购排行榜第一：你。",
  "代购排行榜第一：你。",
];

const REPLY_BULK3_031 = [
  "微信排行榜第一：你。",
  "你被微信的广告轰炸了一整天。",
  "微信的正确做法：放下手机去做。",
  "你收藏了 100 个微信攻略，一个也没看。",
  "你下载了微信 APP，占了 1G 内存。",
  "你发了微信的朋友圈，点赞的都是机器人。",
  "你问 Siri微信是什么，Siri 说不知道。",
  "微信的正确做法：放下手机去做。",
  "微信花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个微信攻略，一个也没看。",
  "你被微信的广告轰炸了一整天。",
  "你被微信的广告轰炸了一整天。",
  "你问 Siri微信是什么，Siri 说不知道。",
  "你发了微信的朋友圈，点赞的都是机器人。",
  "你下载了微信 APP，占了 1G 内存。",
  "你被微信的广告轰炸了一整天。",
  "微信结束了，你觉得浪费时间但很快乐。",
  "你问朋友微信怎么样，朋友说一般。",
  "你被微信的广告轰炸了一整天。",
  "你搜索微信，出来了 100 万条结果。",
];

const REPLY_BULK3_032 = [
  "QQ的时候，手机掉电 50%。",
  "QQ结束了，你觉得浪费时间但很快乐。",
  "QQ的最高境界：不用手机。",
  "你问朋友QQ怎么样，朋友说一般。",
  "QQ的时候，你回复了 100 条消息。",
  "QQ的最高境界：不用手机。",
  "QQ的最高境界：不用手机。",
  "QQ的时候，手机掉电 50%。",
  "QQ结束了，你觉得浪费时间但很快乐。",
  "你发了QQ的朋友圈，点赞的都是机器人。",
  "你问朋友QQ怎么样，朋友说一般。",
  "QQ花了你 1000 块，结果啥也没得到。",
  "你发了QQ的朋友圈，点赞的都是机器人。",
  "你说再也不QQ了，结果又QQ了一下午。",
  "QQ排行榜第一：你。",
  "你搜索QQ，出来了 100 万条结果。",
  "你问 SiriQQ是什么，Siri 说不知道。",
  "你说再也不QQ了，结果又QQ了一下午。",
  "你问 SiriQQ是什么，Siri 说不知道。",
  "QQ的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_033 = [
  "微博花了你 1000 块，结果啥也没得到。",
  "你说再也不微博了，结果又微博了一下午。",
  "微博排行榜第一：你。",
  "微博的最高境界：不用手机。",
  "你收藏了 100 个微博攻略，一个也没看。",
  "你问朋友微博怎么样，朋友说一般。",
  "微博的时候，手机烫得像烙铁。",
  "微博的教程看了 50 个，还是不会。",
  "微博的时候，手机掉电 50%。",
  "你被微博的广告轰炸了一整天。",
  "微博的教程看了 50 个，还是不会。",
  "微博结束了，你觉得浪费时间但很快乐。",
  "你发了微博的朋友圈，点赞的都是机器人。",
  "微博的时候，你回复了 100 条消息。",
  "你说再也不微博了，结果又微博了一下午。",
  "微博的时候，手机烫得像烙铁。",
  "微博结束了，你觉得浪费时间但很快乐。",
  "你搜索微博，出来了 100 万条结果。",
  "你问 Siri微博是什么，Siri 说不知道。",
  "你收藏了 100 个微博攻略，一个也没看。",
];

const REPLY_BULK3_034 = [
  "小红书的时候，你刷了 1 小时短视频。",
  "小红书排行榜第一：你。",
  "你搜索小红书，出来了 100 万条结果。",
  "你在小红书，突然想起手机没电了。",
  "小红书的最高境界：不用手机。",
  "小红书的教程看了 50 个，还是不会。",
  "小红书的时候，你回复了 100 条消息。",
  "小红书的时候，你刷了 1 小时短视频。",
  "小红书的教程看了 50 个，还是不会。",
  "你在小红书，突然想起手机没电了。",
  "小红书的最高境界：不用手机。",
  "小红书结束了，你觉得浪费时间但很快乐。",
  "小红书的最高境界：不用手机。",
  "你发了小红书的朋友圈，点赞的都是机器人。",
  "你在小红书，突然想起手机没电了。",
  "小红书的时候，你回复了 100 条消息。",
  "你搜索小红书，出来了 100 万条结果。",
  "小红书的最高境界：不用手机。",
  "你在小红书，突然想起手机没电了。",
  "小红书的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_035 = [
  "抖音排行榜第一：你。",
  "抖音排行榜第一：你。",
  "你收藏了 100 个抖音攻略，一个也没看。",
  "抖音的时候，你回复了 100 条消息。",
  "抖音的时候，你刷了 1 小时短视频。",
  "抖音的时候，手机掉电 50%。",
  "抖音的时候，手机烫得像烙铁。",
  "抖音的时候，你回复了 100 条消息。",
  "抖音花了你 1000 块，结果啥也没得到。",
  "抖音的教程看了 50 个，还是不会。",
  "抖音的时候，你回复了 100 条消息。",
  "你被抖音的广告轰炸了一整天。",
  "抖音的时候，手机烫得像烙铁。",
  "你下载了抖音 APP，占了 1G 内存。",
  "抖音排行榜第一：你。",
  "你搜索抖音，出来了 100 万条结果。",
  "抖音的教程看了 50 个，还是不会。",
  "抖音的教程看了 50 个，还是不会。",
  "你搜索抖音，出来了 100 万条结果。",
  "抖音排行榜第一：你。",
];

const REPLY_BULK3_036 = [
  "快手的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个快手攻略，一个也没看。",
  "快手的正确做法：放下手机去做。",
  "你发了快手的朋友圈，点赞的都是机器人。",
  "你发了快手的朋友圈，点赞的都是机器人。",
  "快手结束了，你觉得浪费时间但很快乐。",
  "你被快手的广告轰炸了一整天。",
  "快手的时候，你回复了 100 条消息。",
  "快手花了你 1000 块，结果啥也没得到。",
  "你在快手，突然想起手机没电了。",
  "快手的最高境界：不用手机。",
  "快手结束了，你觉得浪费时间但很快乐。",
  "快手的时候，手机掉电 50%。",
  "快手的时候，你刷了 1 小时短视频。",
  "你被快手的广告轰炸了一整天。",
  "你发了快手的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个快手攻略，一个也没看。",
  "你搜索快手，出来了 100 万条结果。",
  "你搜索快手，出来了 100 万条结果。",
  "快手的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_037 = [
  "你问朋友B站怎么样，朋友说一般。",
  "你下载了B站 APP，占了 1G 内存。",
  "B站排行榜第一：你。",
  "B站的最高境界：不用手机。",
  "你问 SiriB站是什么，Siri 说不知道。",
  "你在B站，突然想起手机没电了。",
  "你被B站的广告轰炸了一整天。",
  "B站结束了，你觉得浪费时间但很快乐。",
  "B站花了你 1000 块，结果啥也没得到。",
  "B站的时候，手机掉电 50%。",
  "你下载了B站 APP，占了 1G 内存。",
  "B站的时候，手机烫得像烙铁。",
  "你发了B站的朋友圈，点赞的都是机器人。",
  "B站的教程看了 50 个，还是不会。",
  "你被B站的广告轰炸了一整天。",
  "B站的时候，你回复了 100 条消息。",
  "你在B站，突然想起手机没电了。",
  "你下载了B站 APP，占了 1G 内存。",
  "B站的时候，你刷了 1 小时短视频。",
  "你拍了B站的照片，修图修了 2 小时。",
];

const REPLY_BULK3_038 = [
  "你问 Siri知乎是什么，Siri 说不知道。",
  "知乎花了你 1000 块，结果啥也没得到。",
  "你被知乎的广告轰炸了一整天。",
  "你说再也不知乎了，结果又知乎了一下午。",
  "你下载了知乎 APP，占了 1G 内存。",
  "知乎的时候，你回复了 100 条消息。",
  "你搜索知乎，出来了 100 万条结果。",
  "知乎的时候，你刷了 1 小时短视频。",
  "知乎的最高境界：不用手机。",
  "你问朋友知乎怎么样，朋友说一般。",
  "知乎结束了，你觉得浪费时间但很快乐。",
  "你问 Siri知乎是什么，Siri 说不知道。",
  "知乎的正确做法：放下手机去做。",
  "你问朋友知乎怎么样，朋友说一般。",
  "你在知乎，突然想起手机没电了。",
  "知乎的时候，你刷了 1 小时短视频。",
  "你在知乎，突然想起手机没电了。",
  "你问 Siri知乎是什么，Siri 说不知道。",
  "你被知乎的广告轰炸了一整天。",
  "知乎排行榜第一：你。",
];

const REPLY_BULK3_039 = [
  "豆瓣的最高境界：不用手机。",
  "你下载了豆瓣 APP，占了 1G 内存。",
  "你问朋友豆瓣怎么样，朋友说一般。",
  "豆瓣的最高境界：不用手机。",
  "豆瓣的教程看了 50 个，还是不会。",
  "豆瓣的教程看了 50 个，还是不会。",
  "豆瓣的教程看了 50 个，还是不会。",
  "豆瓣的时候，你回复了 100 条消息。",
  "你问朋友豆瓣怎么样，朋友说一般。",
  "你搜索豆瓣，出来了 100 万条结果。",
  "你在豆瓣，突然想起手机没电了。",
  "豆瓣的时候，手机烫得像烙铁。",
  "你说再也不豆瓣了，结果又豆瓣了一下午。",
  "豆瓣的教程看了 50 个，还是不会。",
  "豆瓣结束了，你觉得浪费时间但很快乐。",
  "豆瓣的时候，你回复了 100 条消息。",
  "你被豆瓣的广告轰炸了一整天。",
  "豆瓣的时候，你刷了 1 小时短视频。",
  "豆瓣的时候，你回复了 100 条消息。",
  "豆瓣的时候，手机掉电 50%。",
];

const REPLY_BULK3_040 = [
  "你拍了贴吧的照片，修图修了 2 小时。",
  "你拍了贴吧的照片，修图修了 2 小时。",
  "贴吧结束了，你觉得浪费时间但很快乐。",
  "你被贴吧的广告轰炸了一整天。",
  "贴吧的时候，手机掉电 50%。",
  "你说再也不贴吧了，结果又贴吧了一下午。",
  "你问 Siri贴吧是什么，Siri 说不知道。",
  "你被贴吧的广告轰炸了一整天。",
  "贴吧结束了，你觉得浪费时间但很快乐。",
  "你拍了贴吧的照片，修图修了 2 小时。",
  "你拍了贴吧的照片，修图修了 2 小时。",
  "你下载了贴吧 APP，占了 1G 内存。",
  "贴吧的时候，手机掉电 50%。",
  "你问 Siri贴吧是什么，Siri 说不知道。",
  "贴吧的最高境界：不用手机。",
  "贴吧的教程看了 50 个，还是不会。",
  "你搜索贴吧，出来了 100 万条结果。",
  "你问朋友贴吧怎么样，朋友说一般。",
  "你在贴吧，突然想起手机没电了。",
  "贴吧结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK3_041 = [
  "你被淘宝的广告轰炸了一整天。",
  "淘宝的时候，手机烫得像烙铁。",
  "你在淘宝，突然想起手机没电了。",
  "你拍了淘宝的照片，修图修了 2 小时。",
  "你问朋友淘宝怎么样，朋友说一般。",
  "淘宝的最高境界：不用手机。",
  "你在淘宝，突然想起手机没电了。",
  "你收藏了 100 个淘宝攻略，一个也没看。",
  "淘宝排行榜第一：你。",
  "淘宝结束了，你觉得浪费时间但很快乐。",
  "淘宝的时候，你刷了 1 小时短视频。",
  "淘宝结束了，你觉得浪费时间但很快乐。",
  "你发了淘宝的朋友圈，点赞的都是机器人。",
  "淘宝的时候，你刷了 1 小时短视频。",
  "淘宝的时候，手机烫得像烙铁。",
  "淘宝的教程看了 50 个，还是不会。",
  "你问朋友淘宝怎么样，朋友说一般。",
  "淘宝的正确做法：放下手机去做。",
  "你发了淘宝的朋友圈，点赞的都是机器人。",
  "淘宝排行榜第一：你。",
];

const REPLY_BULK3_042 = [
  "你收藏了 100 个京东攻略，一个也没看。",
  "你搜索京东，出来了 100 万条结果。",
  "你下载了京东 APP，占了 1G 内存。",
  "京东的时候，手机烫得像烙铁。",
  "你说再也不京东了，结果又京东了一下午。",
  "京东的最高境界：不用手机。",
  "京东结束了，你觉得浪费时间但很快乐。",
  "京东结束了，你觉得浪费时间但很快乐。",
  "你拍了京东的照片，修图修了 2 小时。",
  "你发了京东的朋友圈，点赞的都是机器人。",
  "京东排行榜第一：你。",
  "京东的时候，你回复了 100 条消息。",
  "你说再也不京东了，结果又京东了一下午。",
  "京东的时候，你刷了 1 小时短视频。",
  "京东结束了，你觉得浪费时间但很快乐。",
  "你在京东，突然想起手机没电了。",
  "京东的正确做法：放下手机去做。",
  "京东排行榜第一：你。",
  "你下载了京东 APP，占了 1G 内存。",
  "京东的最高境界：不用手机。",
];

const REPLY_BULK3_043 = [
  "拼多多的时候，你回复了 100 条消息。",
  "你搜索拼多多，出来了 100 万条结果。",
  "拼多多的时候，手机掉电 50%。",
  "你下载了拼多多 APP，占了 1G 内存。",
  "你问朋友拼多多怎么样，朋友说一般。",
  "拼多多排行榜第一：你。",
  "你问 Siri拼多多是什么，Siri 说不知道。",
  "你说再也不拼多多了，结果又拼多多了一下午。",
  "拼多多的时候，你回复了 100 条消息。",
  "你下载了拼多多 APP，占了 1G 内存。",
  "拼多多结束了，你觉得浪费时间但很快乐。",
  "你问 Siri拼多多是什么，Siri 说不知道。",
  "拼多多的时候，手机烫得像烙铁。",
  "你搜索拼多多，出来了 100 万条结果。",
  "拼多多花了你 1000 块，结果啥也没得到。",
  "你说再也不拼多多了，结果又拼多多了一下午。",
  "拼多多花了你 1000 块，结果啥也没得到。",
  "你发了拼多多的朋友圈，点赞的都是机器人。",
  "拼多多排行榜第一：你。",
  "拼多多花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK3_044 = [
  "闲鱼排行榜第一：你。",
  "你收藏了 100 个闲鱼攻略，一个也没看。",
  "闲鱼花了你 1000 块，结果啥也没得到。",
  "闲鱼的时候，手机掉电 50%。",
  "闲鱼排行榜第一：你。",
  "闲鱼的最高境界：不用手机。",
  "闲鱼花了你 1000 块，结果啥也没得到。",
  "你搜索闲鱼，出来了 100 万条结果。",
  "闲鱼排行榜第一：你。",
  "你在闲鱼，突然想起手机没电了。",
  "闲鱼的时候，你刷了 1 小时短视频。",
  "你在闲鱼，突然想起手机没电了。",
  "闲鱼的时候，手机烫得像烙铁。",
  "你收藏了 100 个闲鱼攻略，一个也没看。",
  "闲鱼的时候，手机烫得像烙铁。",
  "闲鱼的时候，手机掉电 50%。",
  "你被闲鱼的广告轰炸了一整天。",
  "你被闲鱼的广告轰炸了一整天。",
  "闲鱼的时候，手机烫得像烙铁。",
  "闲鱼的最高境界：不用手机。",
];

const REPLY_BULK3_045 = [
  "得物排行榜第一：你。",
  "你问 Siri得物是什么，Siri 说不知道。",
  "得物花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个得物攻略，一个也没看。",
  "得物的时候，你刷了 1 小时短视频。",
  "你在得物，突然想起手机没电了。",
  "你收藏了 100 个得物攻略，一个也没看。",
  "得物花了你 1000 块，结果啥也没得到。",
  "得物的时候，手机烫得像烙铁。",
  "得物结束了，你觉得浪费时间但很快乐。",
  "你发了得物的朋友圈，点赞的都是机器人。",
  "你说再也不得物了，结果又得物了一下午。",
  "得物的教程看了 50 个，还是不会。",
  "你说再也不得物了，结果又得物了一下午。",
  "得物的教程看了 50 个，还是不会。",
  "你搜索得物，出来了 100 万条结果。",
  "你被得物的广告轰炸了一整天。",
  "得物的最高境界：不用手机。",
  "你说再也不得物了，结果又得物了一下午。",
  "得物的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_046 = [
  "唯品会花了你 1000 块，结果啥也没得到。",
  "唯品会的时候，你刷了 1 小时短视频。",
  "你下载了唯品会 APP，占了 1G 内存。",
  "你收藏了 100 个唯品会攻略，一个也没看。",
  "你说再也不唯品会了，结果又唯品会了一下午。",
  "你下载了唯品会 APP，占了 1G 内存。",
  "你说再也不唯品会了，结果又唯品会了一下午。",
  "唯品会的教程看了 50 个，还是不会。",
  "你在唯品会，突然想起手机没电了。",
  "你在唯品会，突然想起手机没电了。",
  "你问 Siri唯品会是什么，Siri 说不知道。",
  "唯品会花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个唯品会攻略，一个也没看。",
  "你问朋友唯品会怎么样，朋友说一般。",
  "你说再也不唯品会了，结果又唯品会了一下午。",
  "你在唯品会，突然想起手机没电了。",
  "你问朋友唯品会怎么样，朋友说一般。",
  "唯品会花了你 1000 块，结果啥也没得到。",
  "你拍了唯品会的照片，修图修了 2 小时。",
  "唯品会的最高境界：不用手机。",
];

const REPLY_BULK3_047 = [
  "苏宁的教程看了 50 个，还是不会。",
  "你搜索苏宁，出来了 100 万条结果。",
  "苏宁排行榜第一：你。",
  "苏宁的时候，手机掉电 50%。",
  "你收藏了 100 个苏宁攻略，一个也没看。",
  "苏宁的时候，手机掉电 50%。",
  "你搜索苏宁，出来了 100 万条结果。",
  "苏宁的时候，你回复了 100 条消息。",
  "苏宁的时候，手机掉电 50%。",
  "苏宁的最高境界：不用手机。",
  "苏宁排行榜第一：你。",
  "你收藏了 100 个苏宁攻略，一个也没看。",
  "你发了苏宁的朋友圈，点赞的都是机器人。",
  "苏宁结束了，你觉得浪费时间但很快乐。",
  "你说再也不苏宁了，结果又苏宁了一下午。",
  "苏宁花了你 1000 块，结果啥也没得到。",
  "你搜索苏宁，出来了 100 万条结果。",
  "你拍了苏宁的照片，修图修了 2 小时。",
  "你下载了苏宁 APP，占了 1G 内存。",
  "你搜索苏宁，出来了 100 万条结果。",
];

const REPLY_BULK3_048 = [
  "当当结束了，你觉得浪费时间但很快乐。",
  "你问 Siri当当是什么，Siri 说不知道。",
  "你说再也不当当了，结果又当当了一下午。",
  "你下载了当当 APP，占了 1G 内存。",
  "当当排行榜第一：你。",
  "你问 Siri当当是什么，Siri 说不知道。",
  "你问朋友当当怎么样，朋友说一般。",
  "当当的正确做法：放下手机去做。",
  "当当的时候，手机烫得像烙铁。",
  "你下载了当当 APP，占了 1G 内存。",
  "当当的最高境界：不用手机。",
  "当当排行榜第一：你。",
  "你发了当当的朋友圈，点赞的都是机器人。",
  "当当的正确做法：放下手机去做。",
  "当当的时候，你回复了 100 条消息。",
  "当当的最高境界：不用手机。",
  "你被当当的广告轰炸了一整天。",
  "当当的时候，你回复了 100 条消息。",
  "当当排行榜第一：你。",
  "当当的时候，手机掉电 50%。",
];

const REPLY_BULK3_049 = [
  "你搜索亚马逊，出来了 100 万条结果。",
  "亚马逊的时候，你刷了 1 小时短视频。",
  "你在亚马逊，突然想起手机没电了。",
  "你下载了亚马逊 APP，占了 1G 内存。",
  "亚马逊的时候，手机烫得像烙铁。",
  "亚马逊的教程看了 50 个，还是不会。",
  "你在亚马逊，突然想起手机没电了。",
  "你问 Siri亚马逊是什么，Siri 说不知道。",
  "亚马逊花了你 1000 块，结果啥也没得到。",
  "亚马逊的时候，你回复了 100 条消息。",
  "亚马逊的时候，手机烫得像烙铁。",
  "亚马逊的时候，你回复了 100 条消息。",
  "亚马逊的最高境界：不用手机。",
  "你收藏了 100 个亚马逊攻略，一个也没看。",
  "你收藏了 100 个亚马逊攻略，一个也没看。",
  "你说再也不亚马逊了，结果又亚马逊了一下午。",
  "亚马逊的教程看了 50 个，还是不会。",
  "你拍了亚马逊的照片，修图修了 2 小时。",
  "亚马逊的时候，手机烫得像烙铁。",
  "亚马逊的正确做法：放下手机去做。",
];

const REPLY_BULK3_050 = [
  "你收藏了 100 个考拉攻略，一个也没看。",
  "考拉的正确做法：放下手机去做。",
  "你搜索考拉，出来了 100 万条结果。",
  "你发了考拉的朋友圈，点赞的都是机器人。",
  "考拉的时候，手机掉电 50%。",
  "你在考拉，突然想起手机没电了。",
  "你拍了考拉的照片，修图修了 2 小时。",
  "考拉的正确做法：放下手机去做。",
  "你问朋友考拉怎么样，朋友说一般。",
  "你在考拉，突然想起手机没电了。",
  "你发了考拉的朋友圈，点赞的都是机器人。",
  "考拉排行榜第一：你。",
  "考拉的正确做法：放下手机去做。",
  "考拉的时候，手机烫得像烙铁。",
  "你问朋友考拉怎么样，朋友说一般。",
  "你问 Siri考拉是什么，Siri 说不知道。",
  "你问朋友考拉怎么样，朋友说一般。",
  "你下载了考拉 APP，占了 1G 内存。",
  "你收藏了 100 个考拉攻略，一个也没看。",
  "你发了考拉的朋友圈，点赞的都是机器人。",
];

const REPLY_BULK3_051 = [
  "追剧的时候，你回复了 100 条消息。",
  "追剧的时候，手机烫得像烙铁。",
  "追剧的时候，手机烫得像烙铁。",
  "追剧的时候，你回复了 100 条消息。",
  "你下载了追剧 APP，占了 1G 内存。",
  "追剧花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个追剧攻略，一个也没看。",
  "你搜索追剧，出来了 100 万条结果。",
  "你发了追剧的朋友圈，点赞的都是机器人。",
  "追剧的时候，手机烫得像烙铁。",
  "追剧的时候，你刷了 1 小时短视频。",
  "追剧结束了，你觉得浪费时间但很快乐。",
  "你拍了追剧的照片，修图修了 2 小时。",
  "追剧的时候，你刷了 1 小时短视频。",
  "你问朋友追剧怎么样，朋友说一般。",
  "追剧的时候，你回复了 100 条消息。",
  "追剧的正确做法：放下手机去做。",
  "追剧花了你 1000 块，结果啥也没得到。",
  "追剧的最高境界：不用手机。",
  "追剧的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_052 = [
  "你发了追番的朋友圈，点赞的都是机器人。",
  "你在追番，突然想起手机没电了。",
  "追番的时候，你回复了 100 条消息。",
  "你说再也不追番了，结果又追番了一下午。",
  "追番花了你 1000 块，结果啥也没得到。",
  "追番的教程看了 50 个，还是不会。",
  "你收藏了 100 个追番攻略，一个也没看。",
  "追番排行榜第一：你。",
  "追番的教程看了 50 个，还是不会。",
  "追番的正确做法：放下手机去做。",
  "追番花了你 1000 块，结果啥也没得到。",
  "追番的教程看了 50 个，还是不会。",
  "你说再也不追番了，结果又追番了一下午。",
  "追番花了你 1000 块，结果啥也没得到。",
  "你搜索追番，出来了 100 万条结果。",
  "追番的时候，你刷了 1 小时短视频。",
  "追番结束了，你觉得浪费时间但很快乐。",
  "追番结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个追番攻略，一个也没看。",
  "追番的时候，手机掉电 50%。",
];

const REPLY_BULK3_053 = [
  "你问朋友追星怎么样，朋友说一般。",
  "你问朋友追星怎么样，朋友说一般。",
  "追星排行榜第一：你。",
  "你搜索追星，出来了 100 万条结果。",
  "追星的时候，手机烫得像烙铁。",
  "你发了追星的朋友圈，点赞的都是机器人。",
  "你发了追星的朋友圈，点赞的都是机器人。",
  "你搜索追星，出来了 100 万条结果。",
  "追星的教程看了 50 个，还是不会。",
  "你收藏了 100 个追星攻略，一个也没看。",
  "你问 Siri追星是什么，Siri 说不知道。",
  "追星的正确做法：放下手机去做。",
  "你拍了追星的照片，修图修了 2 小时。",
  "追星的教程看了 50 个，还是不会。",
  "追星的教程看了 50 个，还是不会。",
  "你搜索追星，出来了 100 万条结果。",
  "追星的教程看了 50 个，还是不会。",
  "追星的时候，手机掉电 50%。",
  "你被追星的广告轰炸了一整天。",
  "追星的最高境界：不用手机。",
];

const REPLY_BULK3_054 = [
  "打榜的最高境界：不用手机。",
  "你说再也不打榜了，结果又打榜了一下午。",
  "打榜的时候，手机烫得像烙铁。",
  "你被打榜的广告轰炸了一整天。",
  "你说再也不打榜了，结果又打榜了一下午。",
  "打榜的时候，你刷了 1 小时短视频。",
  "打榜的正确做法：放下手机去做。",
  "打榜花了你 1000 块，结果啥也没得到。",
  "你问 Siri打榜是什么，Siri 说不知道。",
  "你问 Siri打榜是什么，Siri 说不知道。",
  "你说再也不打榜了，结果又打榜了一下午。",
  "打榜结束了，你觉得浪费时间但很快乐。",
  "你拍了打榜的照片，修图修了 2 小时。",
  "你搜索打榜，出来了 100 万条结果。",
  "你问朋友打榜怎么样，朋友说一般。",
  "打榜结束了，你觉得浪费时间但很快乐。",
  "你问 Siri打榜是什么，Siri 说不知道。",
  "你问 Siri打榜是什么，Siri 说不知道。",
  "你在打榜，突然想起手机没电了。",
  "打榜结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK3_055 = [
  "你问朋友应援怎么样，朋友说一般。",
  "你问朋友应援怎么样，朋友说一般。",
  "应援的时候，你刷了 1 小时短视频。",
  "你在应援，突然想起手机没电了。",
  "你拍了应援的照片，修图修了 2 小时。",
  "你在应援，突然想起手机没电了。",
  "应援的时候，你刷了 1 小时短视频。",
  "应援花了你 1000 块，结果啥也没得到。",
  "你发了应援的朋友圈，点赞的都是机器人。",
  "你搜索应援，出来了 100 万条结果。",
  "你说再也不应援了，结果又应援了一下午。",
  "应援的最高境界：不用手机。",
  "你问 Siri应援是什么，Siri 说不知道。",
  "你下载了应援 APP，占了 1G 内存。",
  "应援的时候，你回复了 100 条消息。",
  "应援的最高境界：不用手机。",
  "应援的时候，你回复了 100 条消息。",
  "你下载了应援 APP，占了 1G 内存。",
  "你拍了应援的照片，修图修了 2 小时。",
  "你问朋友应援怎么样，朋友说一般。",
];

const REPLY_BULK3_056 = [
  "你拍了周边的照片，修图修了 2 小时。",
  "周边的正确做法：放下手机去做。",
  "你发了周边的朋友圈，点赞的都是机器人。",
  "周边排行榜第一：你。",
  "周边花了你 1000 块，结果啥也没得到。",
  "你问 Siri周边是什么，Siri 说不知道。",
  "周边花了你 1000 块，结果啥也没得到。",
  "你拍了周边的照片，修图修了 2 小时。",
  "你拍了周边的照片，修图修了 2 小时。",
  "你下载了周边 APP，占了 1G 内存。",
  "周边花了你 1000 块，结果啥也没得到。",
  "你说再也不周边了，结果又周边了一下午。",
  "你拍了周边的照片，修图修了 2 小时。",
  "周边的时候，手机掉电 50%。",
  "周边的时候，手机掉电 50%。",
  "周边的教程看了 50 个，还是不会。",
  "你拍了周边的照片，修图修了 2 小时。",
  "你被周边的广告轰炸了一整天。",
  "你问朋友周边怎么样，朋友说一般。",
  "周边的时候，手机掉电 50%。",
];

const REPLY_BULK3_057 = [
  "你在手办，突然想起手机没电了。",
  "你问朋友手办怎么样，朋友说一般。",
  "你问 Siri手办是什么，Siri 说不知道。",
  "你问朋友手办怎么样，朋友说一般。",
  "手办的时候，你回复了 100 条消息。",
  "手办的教程看了 50 个，还是不会。",
  "你被手办的广告轰炸了一整天。",
  "手办结束了，你觉得浪费时间但很快乐。",
  "手办的教程看了 50 个，还是不会。",
  "手办花了你 1000 块，结果啥也没得到。",
  "你问 Siri手办是什么，Siri 说不知道。",
  "你拍了手办的照片，修图修了 2 小时。",
  "手办的正确做法：放下手机去做。",
  "手办的时候，你回复了 100 条消息。",
  "手办的时候，手机烫得像烙铁。",
  "你拍了手办的照片，修图修了 2 小时。",
  "你问朋友手办怎么样，朋友说一般。",
  "手办的时候，你回复了 100 条消息。",
  "手办排行榜第一：你。",
  "你发了手办的朋友圈，点赞的都是机器人。",
];

const REPLY_BULK3_058 = [
  "盲盒的时候，手机掉电 50%。",
  "盲盒的时候，你刷了 1 小时短视频。",
  "盲盒花了你 1000 块，结果啥也没得到。",
  "你搜索盲盒，出来了 100 万条结果。",
  "你被盲盒的广告轰炸了一整天。",
  "盲盒的时候，你刷了 1 小时短视频。",
  "你搜索盲盒，出来了 100 万条结果。",
  "你问朋友盲盒怎么样，朋友说一般。",
  "你搜索盲盒，出来了 100 万条结果。",
  "盲盒的时候，你回复了 100 条消息。",
  "你拍了盲盒的照片，修图修了 2 小时。",
  "你发了盲盒的朋友圈，点赞的都是机器人。",
  "你下载了盲盒 APP，占了 1G 内存。",
  "你拍了盲盒的照片，修图修了 2 小时。",
  "盲盒的时候，你回复了 100 条消息。",
  "你发了盲盒的朋友圈，点赞的都是机器人。",
  "你问朋友盲盒怎么样，朋友说一般。",
  "盲盒的最高境界：不用手机。",
  "你下载了盲盒 APP，占了 1G 内存。",
  "盲盒的时候，你刷了 1 小时短视频。",
];

const REPLY_BULK3_059 = [
  "卡牌的时候，你回复了 100 条消息。",
  "卡牌的正确做法：放下手机去做。",
  "卡牌的正确做法：放下手机去做。",
  "卡牌的时候，你刷了 1 小时短视频。",
  "卡牌结束了，你觉得浪费时间但很快乐。",
  "你被卡牌的广告轰炸了一整天。",
  "你在卡牌，突然想起手机没电了。",
  "你拍了卡牌的照片，修图修了 2 小时。",
  "你被卡牌的广告轰炸了一整天。",
  "卡牌的教程看了 50 个，还是不会。",
  "你问朋友卡牌怎么样，朋友说一般。",
  "卡牌的时候，你刷了 1 小时短视频。",
  "卡牌的正确做法：放下手机去做。",
  "你下载了卡牌 APP，占了 1G 内存。",
  "你搜索卡牌，出来了 100 万条结果。",
  "卡牌的时候，手机烫得像烙铁。",
  "卡牌的时候，你刷了 1 小时短视频。",
  "你在卡牌，突然想起手机没电了。",
  "你说再也不卡牌了，结果又卡牌了一下午。",
  "你在卡牌，突然想起手机没电了。",
];

const REPLY_BULK3_060 = [
  "谷子花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个谷子攻略，一个也没看。",
  "你收藏了 100 个谷子攻略，一个也没看。",
  "谷子的时候，手机掉电 50%。",
  "谷子排行榜第一：你。",
  "谷子的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个谷子攻略，一个也没看。",
  "谷子结束了，你觉得浪费时间但很快乐。",
  "谷子的时候，你刷了 1 小时短视频。",
  "谷子排行榜第一：你。",
  "你发了谷子的朋友圈，点赞的都是机器人。",
  "你拍了谷子的照片，修图修了 2 小时。",
  "谷子的教程看了 50 个，还是不会。",
  "谷子的时候，你回复了 100 条消息。",
  "你收藏了 100 个谷子攻略，一个也没看。",
  "你拍了谷子的照片，修图修了 2 小时。",
  "你下载了谷子 APP，占了 1G 内存。",
  "谷子的时候，手机掉电 50%。",
  "谷子的最高境界：不用手机。",
  "谷子的正确做法：放下手机去做。",
];

const REPLY_BULK3_061 = [
  "你说再也不减肥了，结果又减肥了一下午。",
  "你搜索减肥，出来了 100 万条结果。",
  "你被减肥的广告轰炸了一整天。",
  "你被减肥的广告轰炸了一整天。",
  "你问朋友减肥怎么样，朋友说一般。",
  "你发了减肥的朋友圈，点赞的都是机器人。",
  "减肥花了你 1000 块，结果啥也没得到。",
  "减肥的教程看了 50 个，还是不会。",
  "减肥的最高境界：不用手机。",
  "你发了减肥的朋友圈，点赞的都是机器人。",
  "你在减肥，突然想起手机没电了。",
  "你收藏了 100 个减肥攻略，一个也没看。",
  "你问 Siri减肥是什么，Siri 说不知道。",
  "你在减肥，突然想起手机没电了。",
  "你问 Siri减肥是什么，Siri 说不知道。",
  "你收藏了 100 个减肥攻略，一个也没看。",
  "你说再也不减肥了，结果又减肥了一下午。",
  "你被减肥的广告轰炸了一整天。",
  "你收藏了 100 个减肥攻略，一个也没看。",
  "减肥结束了，你觉得浪费时间但很快乐。",
];

const REPLY_BULK3_062 = [
  "增重排行榜第一：你。",
  "你问朋友增重怎么样，朋友说一般。",
  "你收藏了 100 个增重攻略，一个也没看。",
  "你问朋友增重怎么样，朋友说一般。",
  "增重花了你 1000 块，结果啥也没得到。",
  "增重的时候，你回复了 100 条消息。",
  "你在增重，突然想起手机没电了。",
  "你问 Siri增重是什么，Siri 说不知道。",
  "增重的时候，你刷了 1 小时短视频。",
  "增重结束了，你觉得浪费时间但很快乐。",
  "你在增重，突然想起手机没电了。",
  "增重的时候，你回复了 100 条消息。",
  "你被增重的广告轰炸了一整天。",
  "你在增重，突然想起手机没电了。",
  "你问 Siri增重是什么，Siri 说不知道。",
  "增重排行榜第一：你。",
  "你被增重的广告轰炸了一整天。",
  "增重结束了，你觉得浪费时间但很快乐。",
  "你搜索增重，出来了 100 万条结果。",
  "增重排行榜第一：你。",
];

const REPLY_BULK3_063 = [
  "你在护肤，突然想起手机没电了。",
  "护肤排行榜第一：你。",
  "你搜索护肤，出来了 100 万条结果。",
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "你在护肤，突然想起手机没电了。",
  "护肤的时候，手机烫得像烙铁。",
  "你问 Siri护肤是什么，Siri 说不知道。",
  "护肤的时候，你刷了 1 小时短视频。",
  "你在护肤，突然想起手机没电了。",
  "护肤的正确做法：放下手机去做。",
  "护肤的时候，你刷了 1 小时短视频。",
  "你问 Siri护肤是什么，Siri 说不知道。",
  "护肤排行榜第一：你。",
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "你搜索护肤，出来了 100 万条结果。",
  "你发了护肤的朋友圈，点赞的都是机器人。",
  "护肤的正确做法：放下手机去做。",
  "护肤排行榜第一：你。",
  "你下载了护肤 APP，占了 1G 内存。",
  "护肤花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK3_064 = [
  "化妆的时候，你回复了 100 条消息。",
  "你在化妆，突然想起手机没电了。",
  "你收藏了 100 个化妆攻略，一个也没看。",
  "化妆排行榜第一：你。",
  "化妆的时候，手机掉电 50%。",
  "你被化妆的广告轰炸了一整天。",
  "化妆的最高境界：不用手机。",
  "化妆结束了，你觉得浪费时间但很快乐。",
  "化妆排行榜第一：你。",
  "你被化妆的广告轰炸了一整天。",
  "化妆的时候，手机烫得像烙铁。",
  "化妆的时候，手机烫得像烙铁。",
  "你发了化妆的朋友圈，点赞的都是机器人。",
  "化妆的时候，你回复了 100 条消息。",
  "你搜索化妆，出来了 100 万条结果。",
  "化妆的时候，你刷了 1 小时短视频。",
  "化妆排行榜第一：你。",
  "化妆的教程看了 50 个，还是不会。",
  "化妆的时候，你刷了 1 小时短视频。",
  "你问朋友化妆怎么样，朋友说一般。",
];

const REPLY_BULK3_065 = [
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你说再也不染发了，结果又染发了一下午。",
  "你搜索染发，出来了 100 万条结果。",
  "染发结束了，你觉得浪费时间但很快乐。",
  "你被染发的广告轰炸了一整天。",
  "你拍了染发的照片，修图修了 2 小时。",
  "你问 Siri染发是什么，Siri 说不知道。",
  "染发的最高境界：不用手机。",
  "染发排行榜第一：你。",
  "染发结束了，你觉得浪费时间但很快乐。",
  "染发花了你 1000 块，结果啥也没得到。",
  "染发的正确做法：放下手机去做。",
  "染发结束了，你觉得浪费时间但很快乐。",
  "你问 Siri染发是什么，Siri 说不知道。",
  "染发的时候，手机掉电 50%。",
  "你在染发，突然想起手机没电了。",
  "染发的教程看了 50 个，还是不会。",
  "你发了染发的朋友圈，点赞的都是机器人。",
  "你问 Siri染发是什么，Siri 说不知道。",
  "染发的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_066 = [
  "你拍了美甲的照片，修图修了 2 小时。",
  "美甲的时候，你回复了 100 条消息。",
  "你被美甲的广告轰炸了一整天。",
  "你被美甲的广告轰炸了一整天。",
  "美甲花了你 1000 块，结果啥也没得到。",
  "美甲结束了，你觉得浪费时间但很快乐。",
  "你问朋友美甲怎么样，朋友说一般。",
  "美甲的时候，手机烫得像烙铁。",
  "美甲的正确做法：放下手机去做。",
  "你说再也不美甲了，结果又美甲了一下午。",
  "你问朋友美甲怎么样，朋友说一般。",
  "美甲的时候，手机掉电 50%。",
  "你下载了美甲 APP，占了 1G 内存。",
  "你被美甲的广告轰炸了一整天。",
  "你被美甲的广告轰炸了一整天。",
  "你说再也不美甲了，结果又美甲了一下午。",
  "美甲的最高境界：不用手机。",
  "你搜索美甲，出来了 100 万条结果。",
  "美甲的时候，手机烫得像烙铁。",
  "你问 Siri美甲是什么，Siri 说不知道。",
];

const REPLY_BULK3_067 = [
  "你搜索健身，出来了 100 万条结果。",
  "你被健身的广告轰炸了一整天。",
  "健身结束了，你觉得浪费时间但很快乐。",
  "健身的时候，手机烫得像烙铁。",
  "你问 Siri健身是什么，Siri 说不知道。",
  "你发了健身的朋友圈，点赞的都是机器人。",
  "你说再也不健身了，结果又健身了一下午。",
  "你说再也不健身了，结果又健身了一下午。",
  "你问 Siri健身是什么，Siri 说不知道。",
  "你收藏了 100 个健身攻略，一个也没看。",
  "健身的最高境界：不用手机。",
  "健身花了你 1000 块，结果啥也没得到。",
  "健身的时候，你刷了 1 小时短视频。",
  "你发了健身的朋友圈，点赞的都是机器人。",
  "健身排行榜第一：你。",
  "你发了健身的朋友圈，点赞的都是机器人。",
  "健身花了你 1000 块，结果啥也没得到。",
  "健身的时候，手机烫得像烙铁。",
  "你收藏了 100 个健身攻略，一个也没看。",
  "健身的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_068 = [
  "瑜伽的时候，手机烫得像烙铁。",
  "你收藏了 100 个瑜伽攻略，一个也没看。",
  "瑜伽排行榜第一：你。",
  "你下载了瑜伽 APP，占了 1G 内存。",
  "你拍了瑜伽的照片，修图修了 2 小时。",
  "瑜伽花了你 1000 块，结果啥也没得到。",
  "你问 Siri瑜伽是什么，Siri 说不知道。",
  "瑜伽结束了，你觉得浪费时间但很快乐。",
  "瑜伽的最高境界：不用手机。",
  "瑜伽的教程看了 50 个，还是不会。",
  "你在瑜伽，突然想起手机没电了。",
  "瑜伽的正确做法：放下手机去做。",
  "瑜伽的教程看了 50 个，还是不会。",
  "你拍了瑜伽的照片，修图修了 2 小时。",
  "瑜伽的最高境界：不用手机。",
  "你搜索瑜伽，出来了 100 万条结果。",
  "瑜伽的教程看了 50 个，还是不会。",
  "你下载了瑜伽 APP，占了 1G 内存。",
  "你发了瑜伽的朋友圈，点赞的都是机器人。",
  "你问朋友瑜伽怎么样，朋友说一般。",
];

const REPLY_BULK3_069 = [
  "你拍了跑步的照片，修图修了 2 小时。",
  "跑步的时候，你回复了 100 条消息。",
  "跑步结束了，你觉得浪费时间但很快乐。",
  "你问朋友跑步怎么样，朋友说一般。",
  "你问朋友跑步怎么样，朋友说一般。",
  "你收藏了 100 个跑步攻略，一个也没看。",
  "你说再也不跑步了，结果又跑步了一下午。",
  "跑步花了你 1000 块，结果啥也没得到。",
  "你发了跑步的朋友圈，点赞的都是机器人。",
  "你说再也不跑步了，结果又跑步了一下午。",
  "你问朋友跑步怎么样，朋友说一般。",
  "跑步的时候，你刷了 1 小时短视频。",
  "你在跑步，突然想起手机没电了。",
  "你问 Siri跑步是什么，Siri 说不知道。",
  "跑步的正确做法：放下手机去做。",
  "跑步花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个跑步攻略，一个也没看。",
  "跑步花了你 1000 块，结果啥也没得到。",
  "你问朋友跑步怎么样，朋友说一般。",
  "跑步的时候，手机掉电 50%。",
];

const REPLY_BULK3_070 = [
  "你问朋友游泳怎么样，朋友说一般。",
  "游泳的正确做法：放下手机去做。",
  "游泳的最高境界：不用手机。",
  "游泳的最高境界：不用手机。",
  "游泳的正确做法：放下手机去做。",
  "你说再也不游泳了，结果又游泳了一下午。",
  "你问朋友游泳怎么样，朋友说一般。",
  "你收藏了 100 个游泳攻略，一个也没看。",
  "你问 Siri游泳是什么，Siri 说不知道。",
  "游泳的时候，手机掉电 50%。",
  "游泳的时候，手机掉电 50%。",
  "你问朋友游泳怎么样，朋友说一般。",
  "你问朋友游泳怎么样，朋友说一般。",
  "游泳结束了，你觉得浪费时间但很快乐。",
  "你被游泳的广告轰炸了一整天。",
  "你说再也不游泳了，结果又游泳了一下午。",
  "游泳的最高境界：不用手机。",
  "游泳的时候，你回复了 100 条消息。",
  "你发了游泳的朋友圈，点赞的都是机器人。",
  "你说再也不游泳了，结果又游泳了一下午。",
];

const REPLY_BULK3_071 = [
  "你搜索开学，出来了 100 万条结果。",
  "开学结束了，你觉得浪费时间但很快乐。",
  "你问 Siri开学是什么，Siri 说不知道。",
  "开学的时候，你回复了 100 条消息。",
  "你搜索开学，出来了 100 万条结果。",
  "你下载了开学 APP，占了 1G 内存。",
  "开学排行榜第一：你。",
  "你搜索开学，出来了 100 万条结果。",
  "你搜索开学，出来了 100 万条结果。",
  "开学排行榜第一：你。",
  "开学的时候，手机烫得像烙铁。",
  "你被开学的广告轰炸了一整天。",
  "开学的时候，你刷了 1 小时短视频。",
  "开学的时候，你回复了 100 条消息。",
  "开学花了你 1000 块，结果啥也没得到。",
  "你发了开学的朋友圈，点赞的都是机器人。",
  "开学花了你 1000 块，结果啥也没得到。",
  "开学的时候，你刷了 1 小时短视频。",
  "开学花了你 1000 块，结果啥也没得到。",
  "你被开学的广告轰炸了一整天。",
];

const REPLY_BULK3_072 = [
  "你收藏了 100 个毕业攻略，一个也没看。",
  "你说再也不毕业了，结果又毕业了一下午。",
  "毕业的教程看了 50 个，还是不会。",
  "毕业花了你 1000 块，结果啥也没得到。",
  "你拍了毕业的照片，修图修了 2 小时。",
  "毕业的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个毕业攻略，一个也没看。",
  "你在毕业，突然想起手机没电了。",
  "毕业的最高境界：不用手机。",
  "毕业排行榜第一：你。",
  "毕业的教程看了 50 个，还是不会。",
  "毕业结束了，你觉得浪费时间但很快乐。",
  "你在毕业，突然想起手机没电了。",
  "你下载了毕业 APP，占了 1G 内存。",
  "你说再也不毕业了，结果又毕业了一下午。",
  "你下载了毕业 APP，占了 1G 内存。",
  "毕业的正确做法：放下手机去做。",
  "你问朋友毕业怎么样，朋友说一般。",
  "毕业的时候，你刷了 1 小时短视频。",
  "你拍了毕业的照片，修图修了 2 小时。",
];

const REPLY_BULK3_073 = [
  "论文的时候，你刷了 1 小时短视频。",
  "论文花了你 1000 块，结果啥也没得到。",
  "你下载了论文 APP，占了 1G 内存。",
  "论文的教程看了 50 个，还是不会。",
  "你被论文的广告轰炸了一整天。",
  "你被论文的广告轰炸了一整天。",
  "论文结束了，你觉得浪费时间但很快乐。",
  "你拍了论文的照片，修图修了 2 小时。",
  "论文结束了，你觉得浪费时间但很快乐。",
  "你下载了论文 APP，占了 1G 内存。",
  "你问朋友论文怎么样，朋友说一般。",
  "论文的教程看了 50 个，还是不会。",
  "你下载了论文 APP，占了 1G 内存。",
  "你拍了论文的照片，修图修了 2 小时。",
  "你下载了论文 APP，占了 1G 内存。",
  "论文结束了，你觉得浪费时间但很快乐。",
  "论文花了你 1000 块，结果啥也没得到。",
  "论文的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个论文攻略，一个也没看。",
  "论文的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_074 = [
  "答辩的正确做法：放下手机去做。",
  "答辩的时候，手机掉电 50%。",
  "你收藏了 100 个答辩攻略，一个也没看。",
  "你被答辩的广告轰炸了一整天。",
  "你下载了答辩 APP，占了 1G 内存。",
  "答辩结束了，你觉得浪费时间但很快乐。",
  "你搜索答辩，出来了 100 万条结果。",
  "你搜索答辩，出来了 100 万条结果。",
  "你被答辩的广告轰炸了一整天。",
  "答辩的时候，你刷了 1 小时短视频。",
  "你问朋友答辩怎么样，朋友说一般。",
  "你发了答辩的朋友圈，点赞的都是机器人。",
  "你发了答辩的朋友圈，点赞的都是机器人。",
  "答辩的时候，你回复了 100 条消息。",
  "答辩的时候，你回复了 100 条消息。",
  "答辩的时候，手机掉电 50%。",
  "答辩的教程看了 50 个，还是不会。",
  "你在答辩，突然想起手机没电了。",
  "你说再也不答辩了，结果又答辩了一下午。",
  "答辩排行榜第一：你。",
];

const REPLY_BULK3_075 = [
  "考研的最高境界：不用手机。",
  "考研的正确做法：放下手机去做。",
  "你问 Siri考研是什么，Siri 说不知道。",
  "考研的时候，手机掉电 50%。",
  "考研的时候，手机掉电 50%。",
  "你问 Siri考研是什么，Siri 说不知道。",
  "考研的正确做法：放下手机去做。",
  "考研花了你 1000 块，结果啥也没得到。",
  "你说再也不考研了，结果又考研了一下午。",
  "你下载了考研 APP，占了 1G 内存。",
  "你问朋友考研怎么样，朋友说一般。",
  "考研的最高境界：不用手机。",
  "你在考研，突然想起手机没电了。",
  "你问朋友考研怎么样，朋友说一般。",
  "你发了考研的朋友圈，点赞的都是机器人。",
  "考研的教程看了 50 个，还是不会。",
  "你说再也不考研了，结果又考研了一下午。",
  "你搜索考研，出来了 100 万条结果。",
  "你在考研，突然想起手机没电了。",
  "你问 Siri考研是什么，Siri 说不知道。",
];

const REPLY_BULK3_076 = [
  "考公结束了，你觉得浪费时间但很快乐。",
  "考公的教程看了 50 个，还是不会。",
  "你发了考公的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个考公攻略，一个也没看。",
  "考公的正确做法：放下手机去做。",
  "你搜索考公，出来了 100 万条结果。",
  "你下载了考公 APP，占了 1G 内存。",
  "你问 Siri考公是什么，Siri 说不知道。",
  "你发了考公的朋友圈，点赞的都是机器人。",
  "你被考公的广告轰炸了一整天。",
  "考公的时候，你刷了 1 小时短视频。",
  "你在考公，突然想起手机没电了。",
  "考公的时候，手机掉电 50%。",
  "考公的教程看了 50 个，还是不会。",
  "考公的最高境界：不用手机。",
  "你在考公，突然想起手机没电了。",
  "你发了考公的朋友圈，点赞的都是机器人。",
  "考公结束了，你觉得浪费时间但很快乐。",
  "考公的正确做法：放下手机去做。",
  "考公花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK3_077 = [
  "你问朋友考证怎么样，朋友说一般。",
  "考证结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个考证攻略，一个也没看。",
  "你下载了考证 APP，占了 1G 内存。",
  "考证的最高境界：不用手机。",
  "你被考证的广告轰炸了一整天。",
  "考证结束了，你觉得浪费时间但很快乐。",
  "你在考证，突然想起手机没电了。",
  "考证的时候，手机掉电 50%。",
  "考证的正确做法：放下手机去做。",
  "你收藏了 100 个考证攻略，一个也没看。",
  "考证结束了，你觉得浪费时间但很快乐。",
  "你拍了考证的照片，修图修了 2 小时。",
  "考证的时候，你回复了 100 条消息。",
  "你说再也不考证了，结果又考证了一下午。",
  "考证的教程看了 50 个，还是不会。",
  "你收藏了 100 个考证攻略，一个也没看。",
  "考证的最高境界：不用手机。",
  "你问朋友考证怎么样，朋友说一般。",
  "考证的最高境界：不用手机。",
];

const REPLY_BULK3_078 = [
  "留学的时候，手机烫得像烙铁。",
  "你问 Siri留学是什么，Siri 说不知道。",
  "留学的教程看了 50 个，还是不会。",
  "你下载了留学 APP，占了 1G 内存。",
  "留学的最高境界：不用手机。",
  "你被留学的广告轰炸了一整天。",
  "你问朋友留学怎么样，朋友说一般。",
  "留学的正确做法：放下手机去做。",
  "你发了留学的朋友圈，点赞的都是机器人。",
  "留学的最高境界：不用手机。",
  "留学的最高境界：不用手机。",
  "留学的教程看了 50 个，还是不会。",
  "你问 Siri留学是什么，Siri 说不知道。",
  "留学结束了，你觉得浪费时间但很快乐。",
  "留学的时候，你回复了 100 条消息。",
  "你在留学，突然想起手机没电了。",
  "你说再也不留学了，结果又留学了一下午。",
  "留学的正确做法：放下手机去做。",
  "留学排行榜第一：你。",
  "你被留学的广告轰炸了一整天。",
];

const REPLY_BULK3_079 = [
  "你被交换的广告轰炸了一整天。",
  "交换花了你 1000 块，结果啥也没得到。",
  "你下载了交换 APP，占了 1G 内存。",
  "你收藏了 100 个交换攻略，一个也没看。",
  "你收藏了 100 个交换攻略，一个也没看。",
  "交换花了你 1000 块，结果啥也没得到。",
  "交换的时候，你回复了 100 条消息。",
  "交换的最高境界：不用手机。",
  "你被交换的广告轰炸了一整天。",
  "你问朋友交换怎么样，朋友说一般。",
  "交换花了你 1000 块，结果啥也没得到。",
  "交换的正确做法：放下手机去做。",
  "你下载了交换 APP，占了 1G 内存。",
  "交换的教程看了 50 个，还是不会。",
  "交换的时候，手机掉电 50%。",
  "交换的时候，手机烫得像烙铁。",
  "交换排行榜第一：你。",
  "交换的时候，你回复了 100 条消息。",
  "你搜索交换，出来了 100 万条结果。",
  "交换的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_080 = [
  "你发了网课的朋友圈，点赞的都是机器人。",
  "你问 Siri网课是什么，Siri 说不知道。",
  "你收藏了 100 个网课攻略，一个也没看。",
  "你被网课的广告轰炸了一整天。",
  "你在网课，突然想起手机没电了。",
  "网课的时候，你回复了 100 条消息。",
  "你问 Siri网课是什么，Siri 说不知道。",
  "你被网课的广告轰炸了一整天。",
  "网课的最高境界：不用手机。",
  "你发了网课的朋友圈，点赞的都是机器人。",
  "网课的时候，你回复了 100 条消息。",
  "网课的时候，你刷了 1 小时短视频。",
  "你搜索网课，出来了 100 万条结果。",
  "你搜索网课，出来了 100 万条结果。",
  "网课结束了，你觉得浪费时间但很快乐。",
  "网课的教程看了 50 个，还是不会。",
  "你收藏了 100 个网课攻略，一个也没看。",
  "网课的时候，你回复了 100 条消息。",
  "网课的正确做法：放下手机去做。",
  "网课排行榜第一：你。",
];

const REPLY_BULK3_081 = [
  "加班花了你 1000 块，结果啥也没得到。",
  "你说再也不加班了，结果又加班了一下午。",
  "加班的正确做法：放下手机去做。",
  "加班的时候，手机烫得像烙铁。",
  "加班的时候，你回复了 100 条消息。",
  "加班结束了，你觉得浪费时间但很快乐。",
  "你说再也不加班了，结果又加班了一下午。",
  "你问 Siri加班是什么，Siri 说不知道。",
  "你发了加班的朋友圈，点赞的都是机器人。",
  "你问朋友加班怎么样，朋友说一般。",
  "你搜索加班，出来了 100 万条结果。",
  "加班的教程看了 50 个，还是不会。",
  "你被加班的广告轰炸了一整天。",
  "加班的正确做法：放下手机去做。",
  "加班的时候，手机掉电 50%。",
  "加班结束了，你觉得浪费时间但很快乐。",
  "你收藏了 100 个加班攻略，一个也没看。",
  "加班的时候，你刷了 1 小时短视频。",
  "加班的时候，手机烫得像烙铁。",
  "加班的正确做法：放下手机去做。",
];

const REPLY_BULK3_082 = [
  "你发了摸鱼的朋友圈，点赞的都是机器人。",
  "你收藏了 100 个摸鱼攻略，一个也没看。",
  "摸鱼的时候，你刷了 1 小时短视频。",
  "摸鱼的最高境界：不用手机。",
  "你发了摸鱼的朋友圈，点赞的都是机器人。",
  "你问朋友摸鱼怎么样，朋友说一般。",
  "摸鱼结束了，你觉得浪费时间但很快乐。",
  "你问朋友摸鱼怎么样，朋友说一般。",
  "你问 Siri摸鱼是什么，Siri 说不知道。",
  "摸鱼结束了，你觉得浪费时间但很快乐。",
  "摸鱼的正确做法：放下手机去做。",
  "你说再也不摸鱼了，结果又摸鱼了一下午。",
  "摸鱼的时候，你刷了 1 小时短视频。",
  "摸鱼的时候，手机烫得像烙铁。",
  "摸鱼的时候，手机烫得像烙铁。",
  "你问 Siri摸鱼是什么，Siri 说不知道。",
  "你问朋友摸鱼怎么样，朋友说一般。",
  "你收藏了 100 个摸鱼攻略，一个也没看。",
  "你问朋友摸鱼怎么样，朋友说一般。",
  "摸鱼的时候，手机烫得像烙铁。",
];

const REPLY_BULK3_083 = [
  "你搜索开会，出来了 100 万条结果。",
  "开会排行榜第一：你。",
  "开会结束了，你觉得浪费时间但很快乐。",
  "开会花了你 1000 块，结果啥也没得到。",
  "你问朋友开会怎么样，朋友说一般。",
  "你搜索开会，出来了 100 万条结果。",
  "开会的时候，手机烫得像烙铁。",
  "你问朋友开会怎么样，朋友说一般。",
  "你问朋友开会怎么样，朋友说一般。",
  "你拍了开会的照片，修图修了 2 小时。",
  "开会花了你 1000 块，结果啥也没得到。",
  "你被开会的广告轰炸了一整天。",
  "你问 Siri开会是什么，Siri 说不知道。",
  "你被开会的广告轰炸了一整天。",
  "开会的时候，你刷了 1 小时短视频。",
  "你问 Siri开会是什么，Siri 说不知道。",
  "开会排行榜第一：你。",
  "开会的教程看了 50 个，还是不会。",
  "开会的时候，手机掉电 50%。",
  "开会的最高境界：不用手机。",
];

const REPLY_BULK3_084 = [
  "你发了周报的朋友圈，点赞的都是机器人。",
  "周报的时候，你刷了 1 小时短视频。",
  "周报的教程看了 50 个，还是不会。",
  "你被周报的广告轰炸了一整天。",
  "周报的时候，手机烫得像烙铁。",
  "你发了周报的朋友圈，点赞的都是机器人。",
  "周报的最高境界：不用手机。",
  "你拍了周报的照片，修图修了 2 小时。",
  "你下载了周报 APP，占了 1G 内存。",
  "周报的时候，你回复了 100 条消息。",
  "你拍了周报的照片，修图修了 2 小时。",
  "你被周报的广告轰炸了一整天。",
  "周报的最高境界：不用手机。",
  "你问 Siri周报是什么，Siri 说不知道。",
  "周报排行榜第一：你。",
  "周报的最高境界：不用手机。",
  "周报花了你 1000 块，结果啥也没得到。",
  "周报排行榜第一：你。",
  "你问朋友周报怎么样，朋友说一般。",
  "你搜索周报，出来了 100 万条结果。",
];

const REPLY_BULK3_085 = [
  "你发了月报的朋友圈，点赞的都是机器人。",
  "月报的正确做法：放下手机去做。",
  "月报结束了，你觉得浪费时间但很快乐。",
  "月报的时候，手机掉电 50%。",
  "月报排行榜第一：你。",
  "你下载了月报 APP，占了 1G 内存。",
  "月报的时候，手机掉电 50%。",
  "你收藏了 100 个月报攻略，一个也没看。",
  "月报的时候，手机掉电 50%。",
  "你在月报，突然想起手机没电了。",
  "你说再也不月报了，结果又月报了一下午。",
  "月报的时候，手机烫得像烙铁。",
  "你问 Siri月报是什么，Siri 说不知道。",
  "月报排行榜第一：你。",
  "月报结束了，你觉得浪费时间但很快乐。",
  "你在月报，突然想起手机没电了。",
  "你在月报，突然想起手机没电了。",
  "你下载了月报 APP，占了 1G 内存。",
  "你说再也不月报了，结果又月报了一下午。",
  "你下载了月报 APP，占了 1G 内存。",
];

const REPLY_BULK3_086 = [
  "你发了KPI的朋友圈，点赞的都是机器人。",
  "你问 SiriKPI是什么，Siri 说不知道。",
  "你问朋友KPI怎么样，朋友说一般。",
  "KPI的时候，你回复了 100 条消息。",
  "KPI的教程看了 50 个，还是不会。",
  "你下载了KPI APP，占了 1G 内存。",
  "你下载了KPI APP，占了 1G 内存。",
  "KPI花了你 1000 块，结果啥也没得到。",
  "你发了KPI的朋友圈，点赞的都是机器人。",
  "你下载了KPI APP，占了 1G 内存。",
  "KPI的时候，你回复了 100 条消息。",
  "你说再也不KPI了，结果又KPI了一下午。",
  "你收藏了 100 个KPI攻略，一个也没看。",
  "KPI的时候，你刷了 1 小时短视频。",
  "KPI排行榜第一：你。",
  "KPI的正确做法：放下手机去做。",
  "你下载了KPI APP，占了 1G 内存。",
  "你搜索KPI，出来了 100 万条结果。",
  "KPI的时候，你回复了 100 条消息。",
  "你在KPI，突然想起手机没电了。",
];

const REPLY_BULK3_087 = [
  "你说再也不OKR了，结果又OKR了一下午。",
  "你发了OKR的朋友圈，点赞的都是机器人。",
  "OKR结束了，你觉得浪费时间但很快乐。",
  "OKR的时候，手机烫得像烙铁。",
  "OKR的最高境界：不用手机。",
  "OKR结束了，你觉得浪费时间但很快乐。",
  "OKR的正确做法：放下手机去做。",
  "你搜索OKR，出来了 100 万条结果。",
  "OKR的时候，手机烫得像烙铁。",
  "你下载了OKR APP，占了 1G 内存。",
  "OKR花了你 1000 块，结果啥也没得到。",
  "你拍了OKR的照片，修图修了 2 小时。",
  "你被OKR的广告轰炸了一整天。",
  "OKR的时候，手机掉电 50%。",
  "你问朋友OKR怎么样，朋友说一般。",
  "你在OKR，突然想起手机没电了。",
  "OKR的时候，手机烫得像烙铁。",
  "你问朋友OKR怎么样，朋友说一般。",
  "你被OKR的广告轰炸了一整天。",
  "OKR的正确做法：放下手机去做。",
];

const REPLY_BULK3_088 = [
  "团建结束了，你觉得浪费时间但很快乐。",
  "你下载了团建 APP，占了 1G 内存。",
  "你发了团建的朋友圈，点赞的都是机器人。",
  "团建的时候，手机烫得像烙铁。",
  "你问 Siri团建是什么，Siri 说不知道。",
  "你问 Siri团建是什么，Siri 说不知道。",
  "你发了团建的朋友圈，点赞的都是机器人。",
  "团建的教程看了 50 个，还是不会。",
  "团建的教程看了 50 个，还是不会。",
  "团建花了你 1000 块，结果啥也没得到。",
  "团建的时候，手机烫得像烙铁。",
  "团建结束了，你觉得浪费时间但很快乐。",
  "你说再也不团建了，结果又团建了一下午。",
  "你拍了团建的照片，修图修了 2 小时。",
  "团建的时候，手机烫得像烙铁。",
  "团建的时候，你刷了 1 小时短视频。",
  "你问朋友团建怎么样，朋友说一般。",
  "你说再也不团建了，结果又团建了一下午。",
  "你下载了团建 APP，占了 1G 内存。",
  "你收藏了 100 个团建攻略，一个也没看。",
];

const REPLY_BULK3_089 = [
  "请假花了你 1000 块，结果啥也没得到。",
  "请假的时候，手机烫得像烙铁。",
  "你收藏了 100 个请假攻略，一个也没看。",
  "请假排行榜第一：你。",
  "请假的正确做法：放下手机去做。",
  "请假结束了，你觉得浪费时间但很快乐。",
  "请假的时候，你回复了 100 条消息。",
  "你问朋友请假怎么样，朋友说一般。",
  "请假的时候，手机掉电 50%。",
  "你被请假的广告轰炸了一整天。",
  "请假的时候，手机烫得像烙铁。",
  "请假的时候，你回复了 100 条消息。",
  "请假的教程看了 50 个，还是不会。",
  "请假花了你 1000 块，结果啥也没得到。",
  "请假的正确做法：放下手机去做。",
  "请假花了你 1000 块，结果啥也没得到。",
  "你被请假的广告轰炸了一整天。",
  "请假的正确做法：放下手机去做。",
  "请假的时候，手机掉电 50%。",
  "请假花了你 1000 块，结果啥也没得到。",
];

const REPLY_BULK3_090 = [
  "辞职的时候，你刷了 1 小时短视频。",
  "你发了辞职的朋友圈，点赞的都是机器人。",
  "你被辞职的广告轰炸了一整天。",
  "你下载了辞职 APP，占了 1G 内存。",
  "你发了辞职的朋友圈，点赞的都是机器人。",
  "你问 Siri辞职是什么，Siri 说不知道。",
  "辞职花了你 1000 块，结果啥也没得到。",
  "辞职的时候，手机掉电 50%。",
  "你收藏了 100 个辞职攻略，一个也没看。",
  "你下载了辞职 APP，占了 1G 内存。",
  "你问朋友辞职怎么样，朋友说一般。",
  "辞职排行榜第一：你。",
  "辞职的时候，手机烫得像烙铁。",
  "你拍了辞职的照片，修图修了 2 小时。",
  "辞职排行榜第一：你。",
  "你发了辞职的朋友圈，点赞的都是机器人。",
  "辞职结束了，你觉得浪费时间但很快乐。",
  "辞职的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个辞职攻略，一个也没看。",
  "你收藏了 100 个辞职攻略，一个也没看。",
];

const REPLY_BULK3_091 = [
  "你发了房贷的朋友圈，点赞的都是机器人。",
  "你说再也不房贷了，结果又房贷了一下午。",
  "房贷花了你 1000 块，结果啥也没得到。",
  "你说再也不房贷了，结果又房贷了一下午。",
  "房贷花了你 1000 块，结果啥也没得到。",
  "你在房贷，突然想起手机没电了。",
  "你被房贷的广告轰炸了一整天。",
  "房贷的时候，手机烫得像烙铁。",
  "你在房贷，突然想起手机没电了。",
  "你拍了房贷的照片，修图修了 2 小时。",
  "房贷的正确做法：放下手机去做。",
  "房贷的最高境界：不用手机。",
  "房贷的最高境界：不用手机。",
  "房贷排行榜第一：你。",
  "你问 Siri房贷是什么，Siri 说不知道。",
  "房贷的时候，手机掉电 50%。",
  "你拍了房贷的照片，修图修了 2 小时。",
  "房贷排行榜第一：你。",
  "房贷排行榜第一：你。",
  "房贷的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_092 = [
  "车贷的时候，手机烫得像烙铁。",
  "你发了车贷的朋友圈，点赞的都是机器人。",
  "你说再也不车贷了，结果又车贷了一下午。",
  "你下载了车贷 APP，占了 1G 内存。",
  "你拍了车贷的照片，修图修了 2 小时。",
  "你说再也不车贷了，结果又车贷了一下午。",
  "你收藏了 100 个车贷攻略，一个也没看。",
  "你被车贷的广告轰炸了一整天。",
  "你搜索车贷，出来了 100 万条结果。",
  "你问 Siri车贷是什么，Siri 说不知道。",
  "车贷结束了，你觉得浪费时间但很快乐。",
  "你发了车贷的朋友圈，点赞的都是机器人。",
  "车贷的时候，手机烫得像烙铁。",
  "你问朋友车贷怎么样，朋友说一般。",
  "车贷的时候，你刷了 1 小时短视频。",
  "车贷的时候，手机烫得像烙铁。",
  "车贷的时候，手机烫得像烙铁。",
  "你说再也不车贷了，结果又车贷了一下午。",
  "你收藏了 100 个车贷攻略，一个也没看。",
  "你下载了车贷 APP，占了 1G 内存。",
];

const REPLY_BULK3_093 = [
  "花呗花了你 1000 块，结果啥也没得到。",
  "你拍了花呗的照片，修图修了 2 小时。",
  "花呗的教程看了 50 个，还是不会。",
  "花呗的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个花呗攻略，一个也没看。",
  "花呗的时候，手机烫得像烙铁。",
  "你收藏了 100 个花呗攻略，一个也没看。",
  "你发了花呗的朋友圈，点赞的都是机器人。",
  "花呗花了你 1000 块，结果啥也没得到。",
  "你在花呗，突然想起手机没电了。",
  "花呗的教程看了 50 个，还是不会。",
  "你拍了花呗的照片，修图修了 2 小时。",
  "你发了花呗的朋友圈，点赞的都是机器人。",
  "你问朋友花呗怎么样，朋友说一般。",
  "花呗的时候，你回复了 100 条消息。",
  "花呗结束了，你觉得浪费时间但很快乐。",
  "花呗的正确做法：放下手机去做。",
  "你下载了花呗 APP，占了 1G 内存。",
  "你收藏了 100 个花呗攻略，一个也没看。",
  "花呗排行榜第一：你。",
];

const REPLY_BULK3_094 = [
  "借呗花了你 1000 块，结果啥也没得到。",
  "你收藏了 100 个借呗攻略，一个也没看。",
  "你问朋友借呗怎么样，朋友说一般。",
  "借呗的时候，手机掉电 50%。",
  "借呗的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个借呗攻略，一个也没看。",
  "你拍了借呗的照片，修图修了 2 小时。",
  "你收藏了 100 个借呗攻略，一个也没看。",
  "借呗的时候，你刷了 1 小时短视频。",
  "借呗的时候，手机烫得像烙铁。",
  "借呗的教程看了 50 个，还是不会。",
  "你下载了借呗 APP，占了 1G 内存。",
  "你问朋友借呗怎么样，朋友说一般。",
  "借呗的时候，手机掉电 50%。",
  "你被借呗的广告轰炸了一整天。",
  "借呗的时候，你回复了 100 条消息。",
  "借呗的最高境界：不用手机。",
  "你收藏了 100 个借呗攻略，一个也没看。",
  "借呗的最高境界：不用手机。",
  "你搜索借呗，出来了 100 万条结果。",
];

const REPLY_BULK3_095 = [
  "信用卡花了你 1000 块，结果啥也没得到。",
  "信用卡的教程看了 50 个，还是不会。",
  "你搜索信用卡，出来了 100 万条结果。",
  "你被信用卡的广告轰炸了一整天。",
  "你问朋友信用卡怎么样，朋友说一般。",
  "你被信用卡的广告轰炸了一整天。",
  "信用卡排行榜第一：你。",
  "你下载了信用卡 APP，占了 1G 内存。",
  "信用卡的时候，手机烫得像烙铁。",
  "信用卡排行榜第一：你。",
  "信用卡的正确做法：放下手机去做。",
  "信用卡花了你 1000 块，结果啥也没得到。",
  "信用卡的教程看了 50 个，还是不会。",
  "信用卡的时候，你回复了 100 条消息。",
  "你在信用卡，突然想起手机没电了。",
  "信用卡的时候，手机烫得像烙铁。",
  "你问朋友信用卡怎么样，朋友说一般。",
  "你发了信用卡的朋友圈，点赞的都是机器人。",
  "信用卡结束了，你觉得浪费时间但很快乐。",
  "你问朋友信用卡怎么样，朋友说一般。",
];

const REPLY_BULK3_096 = [
  "你被理财的广告轰炸了一整天。",
  "理财排行榜第一：你。",
  "理财的时候，手机烫得像烙铁。",
  "理财的时候，手机掉电 50%。",
  "理财的时候，手机掉电 50%。",
  "你下载了理财 APP，占了 1G 内存。",
  "你被理财的广告轰炸了一整天。",
  "你发了理财的朋友圈，点赞的都是机器人。",
  "理财的时候，你刷了 1 小时短视频。",
  "你在理财，突然想起手机没电了。",
  "你问朋友理财怎么样，朋友说一般。",
  "理财的时候，你回复了 100 条消息。",
  "理财排行榜第一：你。",
  "理财排行榜第一：你。",
  "理财的时候，手机掉电 50%。",
  "你说再也不理财了，结果又理财了一下午。",
  "理财的教程看了 50 个，还是不会。",
  "你问朋友理财怎么样，朋友说一般。",
  "理财的教程看了 50 个，还是不会。",
  "理财排行榜第一：你。",
];

const REPLY_BULK3_097 = [
  "基金花了你 1000 块，结果啥也没得到。",
  "基金排行榜第一：你。",
  "你问 Siri基金是什么，Siri 说不知道。",
  "你问朋友基金怎么样，朋友说一般。",
  "基金的最高境界：不用手机。",
  "你下载了基金 APP，占了 1G 内存。",
  "你搜索基金，出来了 100 万条结果。",
  "你被基金的广告轰炸了一整天。",
  "你被基金的广告轰炸了一整天。",
  "你在基金，突然想起手机没电了。",
  "基金结束了，你觉得浪费时间但很快乐。",
  "基金排行榜第一：你。",
  "基金的时候，手机掉电 50%。",
  "基金的教程看了 50 个，还是不会。",
  "你下载了基金 APP，占了 1G 内存。",
  "基金结束了，你觉得浪费时间但很快乐。",
  "基金的最高境界：不用手机。",
  "基金花了你 1000 块，结果啥也没得到。",
  "基金的时候，手机掉电 50%。",
  "基金的教程看了 50 个，还是不会。",
];

const REPLY_BULK3_098 = [
  "股票花了你 1000 块，结果啥也没得到。",
  "股票的教程看了 50 个，还是不会。",
  "股票的时候，手机掉电 50%。",
  "股票的时候，手机烫得像烙铁。",
  "你下载了股票 APP，占了 1G 内存。",
  "股票排行榜第一：你。",
  "股票的时候，手机烫得像烙铁。",
  "你搜索股票，出来了 100 万条结果。",
  "股票结束了，你觉得浪费时间但很快乐。",
  "股票的最高境界：不用手机。",
  "股票排行榜第一：你。",
  "你问朋友股票怎么样，朋友说一般。",
  "股票的时候，你刷了 1 小时短视频。",
  "你收藏了 100 个股票攻略，一个也没看。",
  "你说再也不股票了，结果又股票了一下午。",
  "你问朋友股票怎么样，朋友说一般。",
  "股票的时候，手机掉电 50%。",
  "你问 Siri股票是什么，Siri 说不知道。",
  "股票的时候，手机烫得像烙铁。",
  "股票的时候，你刷了 1 小时短视频。",
];

const REPLY_BULK3_099 = [
  "比特币排行榜第一：你。",
  "你说再也不比特币了，结果又比特币了一下午。",
  "你拍了比特币的照片，修图修了 2 小时。",
  "比特币的最高境界：不用手机。",
  "比特币的时候，你刷了 1 小时短视频。",
  "比特币的时候，你刷了 1 小时短视频。",
  "比特币的时候，手机掉电 50%。",
  "比特币的最高境界：不用手机。",
  "你发了比特币的朋友圈，点赞的都是机器人。",
  "你说再也不比特币了，结果又比特币了一下午。",
  "你说再也不比特币了，结果又比特币了一下午。",
  "你问 Siri比特币是什么，Siri 说不知道。",
  "比特币的教程看了 50 个，还是不会。",
  "比特币的时候，手机烫得像烙铁。",
  "你下载了比特币 APP，占了 1G 内存。",
  "比特币的最高境界：不用手机。",
  "你发了比特币的朋友圈，点赞的都是机器人。",
  "你被比特币的广告轰炸了一整天。",
  "你问 Siri比特币是什么，Siri 说不知道。",
  "比特币的时候，你刷了 1 小时短视频。",
];

const REPLY_BULK3_100 = [
  "黄金的时候，手机掉电 50%。",
  "你问 Siri黄金是什么，Siri 说不知道。",
  "黄金的时候，你回复了 100 条消息。",
  "黄金的时候，手机烫得像烙铁。",
  "你搜索黄金，出来了 100 万条结果。",
  "你被黄金的广告轰炸了一整天。",
  "你收藏了 100 个黄金攻略，一个也没看。",
  "黄金的最高境界：不用手机。",
  "你在黄金，突然想起手机没电了。",
  "你问朋友黄金怎么样，朋友说一般。",
  "你下载了黄金 APP，占了 1G 内存。",
  "你被黄金的广告轰炸了一整天。",
  "黄金的时候，你刷了 1 小时短视频。",
  "你拍了黄金的照片，修图修了 2 小时。",
  "黄金的时候，手机烫得像烙铁。",
  "你说再也不黄金了，结果又黄金了一下午。",
  "你被黄金的广告轰炸了一整天。",
  "你下载了黄金 APP，占了 1G 内存。",
  "你搜索黄金，出来了 100 万条结果。",
  "黄金排行榜第一：你。",
];

// 汇总第三波
const REPLY_BULK3_ALL = [
  ...REPLY_BULK3_001,
  ...REPLY_BULK3_002,
  ...REPLY_BULK3_003,
  ...REPLY_BULK3_004,
  ...REPLY_BULK3_005,
  ...REPLY_BULK3_006,
  ...REPLY_BULK3_007,
  ...REPLY_BULK3_008,
  ...REPLY_BULK3_009,
  ...REPLY_BULK3_010,
  ...REPLY_BULK3_011,
  ...REPLY_BULK3_012,
  ...REPLY_BULK3_013,
  ...REPLY_BULK3_014,
  ...REPLY_BULK3_015,
  ...REPLY_BULK3_016,
  ...REPLY_BULK3_017,
  ...REPLY_BULK3_018,
  ...REPLY_BULK3_019,
  ...REPLY_BULK3_020,
  ...REPLY_BULK3_021,
  ...REPLY_BULK3_022,
  ...REPLY_BULK3_023,
  ...REPLY_BULK3_024,
  ...REPLY_BULK3_025,
  ...REPLY_BULK3_026,
  ...REPLY_BULK3_027,
  ...REPLY_BULK3_028,
  ...REPLY_BULK3_029,
  ...REPLY_BULK3_030,
  ...REPLY_BULK3_031,
  ...REPLY_BULK3_032,
  ...REPLY_BULK3_033,
  ...REPLY_BULK3_034,
  ...REPLY_BULK3_035,
  ...REPLY_BULK3_036,
  ...REPLY_BULK3_037,
  ...REPLY_BULK3_038,
  ...REPLY_BULK3_039,
  ...REPLY_BULK3_040,
  ...REPLY_BULK3_041,
  ...REPLY_BULK3_042,
  ...REPLY_BULK3_043,
  ...REPLY_BULK3_044,
  ...REPLY_BULK3_045,
  ...REPLY_BULK3_046,
  ...REPLY_BULK3_047,
  ...REPLY_BULK3_048,
  ...REPLY_BULK3_049,
  ...REPLY_BULK3_050,
  ...REPLY_BULK3_051,
  ...REPLY_BULK3_052,
  ...REPLY_BULK3_053,
  ...REPLY_BULK3_054,
  ...REPLY_BULK3_055,
  ...REPLY_BULK3_056,
  ...REPLY_BULK3_057,
  ...REPLY_BULK3_058,
  ...REPLY_BULK3_059,
  ...REPLY_BULK3_060,
  ...REPLY_BULK3_061,
  ...REPLY_BULK3_062,
  ...REPLY_BULK3_063,
  ...REPLY_BULK3_064,
  ...REPLY_BULK3_065,
  ...REPLY_BULK3_066,
  ...REPLY_BULK3_067,
  ...REPLY_BULK3_068,
  ...REPLY_BULK3_069,
  ...REPLY_BULK3_070,
  ...REPLY_BULK3_071,
  ...REPLY_BULK3_072,
  ...REPLY_BULK3_073,
  ...REPLY_BULK3_074,
  ...REPLY_BULK3_075,
  ...REPLY_BULK3_076,
  ...REPLY_BULK3_077,
  ...REPLY_BULK3_078,
  ...REPLY_BULK3_079,
  ...REPLY_BULK3_080,
  ...REPLY_BULK3_081,
  ...REPLY_BULK3_082,
  ...REPLY_BULK3_083,
  ...REPLY_BULK3_084,
  ...REPLY_BULK3_085,
  ...REPLY_BULK3_086,
  ...REPLY_BULK3_087,
  ...REPLY_BULK3_088,
  ...REPLY_BULK3_089,
  ...REPLY_BULK3_090,
  ...REPLY_BULK3_091,
  ...REPLY_BULK3_092,
  ...REPLY_BULK3_093,
  ...REPLY_BULK3_094,
  ...REPLY_BULK3_095,
  ...REPLY_BULK3_096,
  ...REPLY_BULK3_097,
  ...REPLY_BULK3_098,
  ...REPLY_BULK3_099,
  ...REPLY_BULK3_100,
];

// 所有批量台词最终合并
const REPLY_MEGA = [...REPLY_BULK_ALL, ...REPLY_BULK2_ALL, ...REPLY_BULK3_ALL];







/* ============================================================
   H. 命令解析器
   ============================================================ */
async function handleCommand(raw) {
  const text = raw.trim();
  const lower = text.toLowerCase();

  // 空输入
  if (!text) return;

  // clear 清屏
  if (lower === 'clear' || lower === 'cls') {
    $('#chat-box').innerHTML = '';
    sysSay('屏幕已清空。', 0);
    return;
  }
  // exit 关机
  if (lower === 'exit' || lower === 'quit' || lower === '退出') {
    await sysSay(pick(REPLY_EXIT), 30);
    triggerScreenShake(true);
    playBoom();
    setTimeout(() => toggleCrack(true), 300);
    return;
  }
  // help
  if (lower === 'help' || lower === '？' || lower === '?') {
    $('#help-panel').classList.add('on');
    sysSay(pick(REPLY_HELP), 20);
    return;
  }
  // boom 爆炸
  if (lower === 'boom' || text.includes('爆炸') || text.includes('炸')) {
    return doBoomSequence();
  }
  // 和平精英
  if (text.includes('和平精英') || text.includes('吃鸡') || text.includes('炸鱼')) {
    return doGameSequence('hp');
  }
  // 原神
  if (text.includes('原神') || text.includes('云原神') || text.includes('米哈游')) {
    return doGameSequence('genshin');
  }
  // 转转
  if (text.includes('转转') || text.includes('回收') || text.includes('卖手机')) {
    return doZhuanzhuan();
  }
  // 斧子
  if (text.includes('斧子') || text.includes('斧头') || text.includes('axe')) {
    await botSay(pick(REPLY_AXE), 25);
    S.temp = clamp(S.temp + randInt(3, 8), 36, 110);
    return;
  }
  // 五星
  if (text.includes('五星') || text.includes('星星') || text.includes('国旗')) {
    await botSay(pick(REPLY_STAR), 25);
    return;
  }
  // 梨花
  if (text.includes('梨花') || text.includes('BGM') || text.includes('音乐') || text.includes('唱歌')) {
    playBGM();
    await botSay(pick(REPLY_LIHUA), 30);
    return;
  }
  // 超频
  if (text.includes('超频') || text.includes('overclock')) {
    S.overclock = true;
    await botSay(pick(REPLY_OVERCLOCK), 60);
    S.temp = clamp(S.temp + randInt(15, 25), 36, 110);
    triggerScreenShake(false);
    playStatic(0.6);
    return;
  }
  // 拆芯片
  if (text.includes('拆') || text.includes('拆芯片') || text.includes('拆机')) {
    await botSay(pick(REPLY_DISASSEMBLE), 80);
    S.health = clamp(S.health - randInt(20, 40), 0, 100);
    return;
  }
  // 温度查询
  if (text.includes('温度') || text.includes('热') || text.includes('烫')) {
    const t = S.temp.toFixed(0);
    await botSay(`当前芯片温度：${t}°C。${S.temp > 80 ? '已经烫手！' : S.temp > 60 ? '有点热。' : '凉爽。'}`, 20);
    return;
  }
  // 电量查询
  if (text.includes('电量') || text.includes('电池') || text.includes('充电')) {
    await botSay(`当前电量：${S.batt.toFixed(0)}%。${S.batt < 20 ? '快没电了！' : '还够用。'}`, 20);
    return;
  }
  // 静音
  if (text.includes('静音') || text.includes('mute')) {
    S.audioMuted = !S.audioMuted;
    if (S.audioMuted) stopBGM();
    sysSay(S.audioMuted ? '已静音。' : '已取消静音。', 0);
    return;
  }
  // 碎片雨
  if (text.includes('碎片') || text.includes('下雨') || text.includes('rain')) {
    spawnRain(80);
    await botSay('下碎片雨了！', 15);
    return;
  }
  // 闪电
  if (text.includes('闪电') || text.includes('雷霆') || text.includes('打雷')) {
    spawnLightningBolt(5);
    playStatic(0.3);
    await botSay('⚡ 雷霆之力汇聚！', 15);
    return;
  }
  // 屏幕裂纹
  if (text.includes('裂纹') || text.includes('碎屏') || text.includes('摔')) {
    toggleCrack(true);
    await botSay('屏幕已经裂开了……', 20);
    return;
  }
  // WiFi / 网络
  if (text.includes('wifi') || text.includes('WiFi') || text.includes('网络') || text.includes('卡顿') || text.includes('网')) {
    await botSay(pick(REPLY_NETWORK), 40);
    S.fps = clamp(S.fps - randInt(5, 15), 1, 60);
    return;
  }
  // 王者荣耀
  if (text.includes('王者') || text.includes('农药') || text.includes('wzry')) {
    S.inGame = true;
    S.temp = clamp(S.temp + 12, 36, 110);
    for (let i = 0; i < randInt(4, 6); i++) {
      await botSay(pick(REPLY_WZRY), 90);
      S.temp = clamp(S.temp + randInt(2, 6), 36, 110);
      if (S.temp > 100) break;
    }
    if (S.temp > 100) await doBoomSequence();
    stopBGM();
    return;
  }
  // 相机 / 拍照
  if (text.includes('拍照') || text.includes('相机') || text.includes('录像') || text.includes('camera')) {
    await botSay(pick(REPLY_CAMERA), 35);
    return;
  }
  // 闹钟 / 续航
  if (text.includes('闹钟') || text.includes('续航') || text.includes('充电') || text.includes('电池')) {
    await botSay(pick(REPLY_ALARM), 40);
    return;
  }
  // 系统 / 清理
  if (text.includes('清理') || text.includes('系统') || text.includes('卡顿') || text.includes('后台')) {
    await botSay(pick(REPLY_SYSTEM), 45);
    S.fps = clamp(S.fps + randInt(5, 15), 1, 60);
    return;
  }
  // 颜文字
  if (text.includes('颜文字') || text.includes('emoji') || text.includes('表情')) {
    await botSay(pick(REPLY_EMOJI), 30);
    return;
  }
  // 鸡汤
  if (text.includes('鸡汤') || text.includes('人生') || text.includes('哲学') || text.includes('道理')) {
    await botSay(pick(REPLY_WISDOM), 40);
    return;
  }
  // 身份
  if (text.includes('你是谁') || text.includes('你叫什么') || text.includes('介绍')) {
    await botSay(pick(REPLY_IDENTITY), 35);
    return;
  }
  // 抽签 / 随机
  if (text.includes('抽签') || text.includes('运气') || text.includes('随机') || text.includes('抽卡')) {
    await botSay(pick(REPLY_RANDOM), 25);
    spawnLightningBolt(2);
    return;
  }
  // 原神追加剧情
  if (S.gameScene === 'genshin' && Math.random() < 0.5) {
    await botSay(pick(REPLY_GENSHIN_EXTRA), 80);
    return;
  }
  // 和平精英追加剧情
  if (S.gameScene === 'hp' && Math.random() < 0.5) {
    await botSay(pick(REPLY_HP_EXTRA), 80);
    return;
  }

  // 兜底：通用智障回复
  await botSay(pick(REPLY_GENERIC), randInt(20, 45));
  S.temp = clamp(S.temp + rand(0.5, 2), 36, 110);
}

/* ============================================================
   H.1 剧情分支：爆炸
   ============================================================ */
async function doBoomSequence() {
  S.exploded = true;
  S.inGame = false;
  playBeep();
  await sysSay('⚠️ 终极爆炸程序启动！', 40);
  await botSay(pick(REPLY_HP_EXPLODE), 60);
  S.temp = 110;
  spawnLightningBolt(4);
  playStatic(0.5);
  await sleep(300);
  // 真正的爆炸！
  triggerScreenShake(true);
  document.body.classList.add('boom-flash');
  spawnExplosion(canvas.width / 2, canvas.height / 2, 150);
  spawnChipFragments(40);
  playBoom();
  setTimeout(() => document.body.classList.remove('boom-flash'), 500);
  await sysSay('💥💥💥 轰隆！！手机炸飞了！！💥💥💥', 0);
  await botSay(pick(REPLY_HP_EXPLODE), 50);
  setTimeout(() => toggleCrack(true), 400);
  S.health = clamp(S.health - 50, 0, 100);
  S.batt = clamp(S.batt - 30, 0, 100);
  showToast('💥 手机已爆炸！');
}

/* ============================================================
   H.2 剧情分支：游戏（和平精英 / 原神）
   ============================================================ */
async function doGameSequence(kind) {
  S.inGame = true;
  S.gameScene = kind;
  S.temp = clamp(S.temp + 15, 36, 110);
  S.fps = kind === 'hp' ? randInt(25, 45) : randInt(1, 8);

  if (kind === 'hp') {
    for (let i = 0; i < 3; i++) {
      await botSay(pick(REPLY_HP_START), 40);
    }
    playBGM();
    for (let i = 0; i < randInt(3, 5); i++) {
      await botSay(pick(REPLY_HP_PLAY), 80);
      S.temp = clamp(S.temp + randInt(3, 8), 36, 110);
      if (S.temp > 95) break;
    }
    if (S.temp > 95) {
      await botSay(pick(REPLY_HP_EXPLODE), 80);
      triggerScreenShake(false);
      playStatic(0.4);
      if (S.temp > 105) {
        await doBoomSequence();
      }
    } else {
      await botSay('这局打完了，你吃鸡了！（才怪）', 30);
    }
  } else {
    for (let i = 0; i < 4; i++) {
      await botSay(pick(REPLY_GENSHIN), 100);
      S.temp = clamp(S.temp + randInt(4, 10), 36, 110);
      if (S.temp > 100) break;
    }
    if (S.temp > 100) {
      await botSay('💥 骁龙450 再也顶不住了！', 60);
      await doBoomSequence();
    }
  }
  stopBGM();
}

/* ============================================================
   H.3 剧情分支：转转回收
   ============================================================ */
async function doZhuanzhuan() {
  for (let i = 0; i < Math.min(8, REPLY_ZHUANZHUAN.length); i++) {
    await botSay(REPLY_ZHUANZHUAN[i], 70);
  }
  await sysSay('💡 提示：1 块钱的回收价，不如留着当摆件。', 30);
}

/* ============================================================
   I. 打字机 + 对话渲染
   ============================================================ */
const chatBox = $('#chat-box');

function scrollChatBottom() {
  chatBox.scrollTop = chatBox.scrollHeight;
}

// 通用：添加一条消息（立即显示，不带打字机）
function appendMsg(text, who = 'bot', cls = '') {
  const div = document.createElement('div');
  div.className = 'msg ' + who + (cls ? ' ' + cls : '');
  const whoLabel = { user: '你', bot: '雷霆', sys: '系统' }[who] || '?';
  div.innerHTML = `<span class="who">${whoLabel}</span>`;
  const body = document.createElement('span');
  body.className = 'msg-body';
  body.textContent = text;
  div.appendChild(body);
  chatBox.appendChild(div);
  scrollChatBottom();
  S.msgCount++;
  return body;
}

// 打字机逐字输出
async function typewriter(el, text, speed) {
  el.classList.add('typing-cursor');
  for (let i = 0; i < text.length; i++) {
    el.textContent += text[i];
    if (Math.random() < 0.35) playType();
    scrollChatBottom();
    await sleep(speed);
  }
  el.classList.remove('typing-cursor');
}

async function botSay(text, speed = 25) {
  const body = appendMsg('', 'bot');
  await typewriter(body, text, speed);
  return body;
}
async function userSay(text) {
  appendMsg(text, 'user');
}
async function sysSay(text, speed = 20) {
  const body = appendMsg('', 'sys');
  await typewriter(body, text, speed);
  return body;
}

/* ============================================================
   J. 状态栏实时刷新
   ============================================================ */
function refreshStatusBar() {
  // 温度
  const t = S.temp.toFixed(0);
  $('#val-temp').textContent = t + '°C';
  const cellTemp = $('#cell-temp');
  cellTemp.classList.remove('warn', 'danger');
  if (S.temp > 95) cellTemp.classList.add('danger');
  else if (S.temp > 70) cellTemp.classList.add('warn');
  $('#bar-temp').style.width = clamp((S.temp - 30) / 80 * 100, 5, 100) + '%';
  $('#bar-temp').style.background =
    S.temp > 95 ? '#ff3b3b' : S.temp > 70 ? '#ff8a00' : '#00ffaa';

  // 电量
  $('#val-batt').textContent = S.batt.toFixed(0) + '%';
  const cellBatt = $('#cell-batt');
  cellBatt.classList.remove('warn', 'danger');
  if (S.batt < 15) cellBatt.classList.add('danger');
  else if (S.batt < 35) cellBatt.classList.add('warn');

  // 帧率
  $('#val-fps').textContent = S.fps;
  const cellFps = $('#cell-fps');
  cellFps.classList.remove('warn', 'danger');
  if (S.fps < 10) cellFps.classList.add('danger');
  else if (S.fps < 30) cellFps.classList.add('warn');

  // 健康
  $('#val-health').textContent = S.health.toFixed(0) + '%';
  const cellH = $('#cell-health');
  cellH.classList.remove('warn', 'danger');
  if (S.health < 30) cellH.classList.add('danger');
  else if (S.health < 60) cellH.classList.add('warn');
}

// 每 1.5 秒模拟手机状态变化
setInterval(() => {
  // 温度缓慢回落，玩游戏时上升
  if (S.inGame) {
    S.temp = clamp(S.temp + rand(0.3, 1.2), 36, 110);
    S.fps = clamp(S.fps + randInt(-3, 3), 1, 60);
  } else {
    S.temp = clamp(S.temp - rand(0.1, 0.5), 36, 110);
    S.fps = clamp(S.fps + randInt(-1, 2), 20, 60);
  }
  // 电量缓慢消耗
  S.batt = clamp(S.batt - rand(0.02, 0.15), 0, 100);
  // 健康微降
  if (S.temp > 95) S.health = clamp(S.health - rand(0.1, 0.4), 0, 100);
  refreshStatusBar();
}, 1500);

/* ============================================================
   K. 事件绑定与初始化
   ============================================================ */
const input = $('#user-input');
const sendBtn = $('#send-btn');

async function doSend() {
  const text = input.value;
  if (!text.trim()) return;
  input.value = '';
  // 首次交互时解锁 AudioContext
  ensureAudio();
  if (S.audioCtx && S.audioCtx.state === 'suspended') {
    S.audioCtx.resume();
  }
  await userSay(text);
  await handleCommand(text);
  input.focus();
}

sendBtn.addEventListener('click', doSend);
input.addEventListener('keydown', (e) => {
  if (e.key === 'Enter') doSend();
});

// 快捷按钮
$$('.quick-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    input.value = btn.dataset.cmd;
    doSend();
  });
});

// 帮助面板关闭
$('#help-close').addEventListener('click', () => {
  $('#help-panel').classList.remove('on');
});

// 点击画面任意处，首次解锁音频
document.body.addEventListener('touchstart', () => {
  ensureAudio();
  if (S.audioCtx && S.audioCtx.state === 'suspended') S.audioCtx.resume();
}, { once: true });

// 防止双击缩放
let lastTouch = 0;
document.addEventListener('touchend', (e) => {
  const now = Date.now();
  if (now - lastTouch < 300) e.preventDefault();
  lastTouch = now;
}, { passive: false });

// 初始化
refreshStatusBar();
runBoot();

/* ============================================================
   L. 彩蛋：双击标题触发大爆炸
   ============================================================ */
let titleTapCount = 0;
let titleTapTimer = null;
$('#title-bar').addEventListener('click', () => {
  titleTapCount++;
  clearTimeout(titleTapTimer);
  titleTapTimer = setTimeout(() => titleTapCount = 0, 800);
  if (titleTapCount >= 3) {
    titleTapCount = 0;
    sysSay('🥚 彩蛋触发！连续三连点！', 10);
    spawnLightningBolt(8);
    spawnExplosion(canvas.width / 2, canvas.height / 3, 120);
    playBoom();
    triggerScreenShake(true);
  }
});

/* ============================================================
   M. 控制台彩蛋
   ============================================================ */

/* ============================================================
   U. 更多随机事件与彩蛋
   ============================================================ */

// U.1 随机事件触发
const RANDOM_EVENTS = [
  { chance: 0.05, action: () => { spawnLightningBolt(3); sysSay('⚡ 随机闪电！', 10); } },
  { chance: 0.03, action: () => { spawnRain(30); sysSay('🌧️ 下碎片雨了！', 10); } },
  { chance: 0.02, action: () => { playBeep(); sysSay('⚠️ 系统警告！', 10); } },
  { chance: 0.01, action: () => { doBoomSequence(); } },
];

setInterval(() => {
  if (document.hidden) return;
  for (const ev of RANDOM_EVENTS) {
    if (Math.random() < ev.chance) ev.action();
  }
}, 5000);

// U.2 输入特定关键词触发特殊效果
const SPECIAL_TRIGGERS = {
  '爆炸': () => doBoomSequence(),
  '吃鸡': () => doGameSequence('hp'),
  '原神': () => doGameSequence('genshin'),
  '转转': () => doZhuanzhuan(),
  '超频': () => { S.overclock = true; S.temp = clamp(S.temp + 20, 36, 110); sysSay('🔥 超频完成！', 10); },
  '拆机': () => { S.health = clamp(S.health - 30, 0, 100); sysSay('🔧 拆机完成！', 10); },
  '梨花': () => { playBGM(); sysSay('🎵 BGM 播放中', 10); },
  '碎片': () => { spawnRain(50); sysSay('💎 碎片雨！', 10); },
  '闪电': () => { spawnLightningBolt(5); sysSay('⚡ 闪电！', 10); },
  '裂纹': () => { toggleCrack(true); sysSay('💔 屏幕裂了！', 10); },
};

// U.3 回复统计
const replyCount = {};
function trackReply(reply) {
  replyCount[reply] = (replyCount[reply] || 0) + 1;
}

// U.4 概率回复
function maybeReply(reply, chance = 0.5) {
  if (Math.random() < chance) {
    botSay(reply, 25);
    trackReply(reply);
  }
}

// U.5 链式回复
async function chainReplies(replies, delay = 100) {
  for (const r of replies) {
    await sleep(delay);
    await botSay(r, 20);
  }
}

// U.6 随机选择回复
function randomReply(arr) {
  return pick(arr);
}

// U.7 温度影响回复
function tempAffectedReply() {
  if (S.temp > 95) return pick(REPLY_HP_EXPLODE);
  if (S.temp > 70) return pick(REPLY_OVERCLOCK);
  return pick(REPLY_GENERIC);
}

// U.8 电量影响回复
function battAffectedReply() {
  if (S.batt < 15) return '🔋 快没电了！';
  if (S.batt < 35) return '🔋 电量不足。';
  return '🔋 电量充足。';
}

// U.9 健康影响回复
function healthAffectedReply() {
  if (S.health < 30) return '💔 芯片快不行了！';
  if (S.health < 60) return '💛 芯片有点小毛病。';
  return '💚 芯片健康。';
}

// U.10 帧率影响回复
function fpsAffectedReply() {
  if (S.fps < 10) return '🐌 卡成幻灯片！';
  if (S.fps < 30) return '🐢 有点卡。';
  return '⚡ 流畅！';
}

/* ============================================================
   V. 调试与诊断命令
   ============================================================ */
const DEBUG_COMMANDS = {
  'debug': () => {
    sysSay(`=== 调试信息 ===
温度: ${S.temp.toFixed(1)}°C
电量: ${S.batt.toFixed(1)}%
帧率: ${S.fps}
健康: ${S.health.toFixed(1)}%
消息数: ${S.msgCount}
粒子数: ${S.particles.length}
游戏中: ${S.inGame}
超频: ${S.overclock}
已爆炸: ${S.exploded}
`, 5);
  },
  'reset': () => {
    S.temp = 36; S.batt = 87; S.fps = 60; S.health = 99;
    S.overclock = false; S.exploded = false; S.inGame = false;
    toggleCrack(false);
    sysSay('🔄 系统已重置！', 10);
  },
  'stats': () => {
    const total = Object.values(replyCount).reduce((a, b) => a + b, 0);
    sysSay(`📊 已回复 ${total} 条消息`, 10);
  },
  'theme': () => {
    document.body.classList.toggle('dark');
    sysSay('🎨 主题已切换', 10);
  },
};

/* ============================================================
   W. 音效扩展
   ============================================================ */
// 解锁音
function playUnlock() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  [880, 1100, 1320].forEach((freq, i) => {
    const o = ctx.createOscillator();
    o.type = 'sine';
    o.frequency.value = freq;
    const g = ctx.createGain();
    g.gain.setValueAtTime(0.05, t + i * 0.08);
    g.gain.exponentialRampToValueAtTime(0.001, t + i * 0.08 + 0.15);
    o.connect(g).connect(ctx.destination);
    o.start(t + i * 0.08); o.stop(t + i * 0.08 + 0.16);
  });
}

// 错误音
function playError() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  const o = ctx.createOscillator();
  o.type = 'sawtooth';
  o.frequency.value = 200;
  const g = ctx.createGain();
  g.gain.setValueAtTime(0.08, t);
  g.gain.exponentialRampToValueAtTime(0.001, t + 0.3);
  o.connect(g).connect(ctx.destination);
  o.start(t); o.stop(t + 0.3);
}

// 胜利音
function playWin() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  [523, 659, 784, 1047].forEach((freq, i) => {
    const o = ctx.createOscillator();
    o.type = 'triangle';
    o.frequency.value = freq;
    const g = ctx.createGain();
    g.gain.setValueAtTime(0.08, t + i * 0.15);
    g.gain.exponentialRampToValueAtTime(0.001, t + i * 0.15 + 0.3);
    o.connect(g).connect(ctx.destination);
    o.start(t + i * 0.15); o.stop(t + i * 0.15 + 0.35);
  });
}

// 失败音
function playLose() {
  const ctx = ensureAudio();
  if (!ctx || S.audioMuted) return;
  const t = ctx.currentTime;
  [400, 350, 300, 200].forEach((freq, i) => {
    const o = ctx.createOscillator();
    o.type = 'square';
    o.frequency.value = freq;
    const g = ctx.createGain();
    g.gain.setValueAtTime(0.06, t + i * 0.2);
    g.gain.exponentialRampToValueAtTime(0.001, t + i * 0.2 + 0.25);
    o.connect(g).connect(ctx.destination);
    o.start(t + i * 0.2); o.stop(t + i * 0.2 + 0.3);
  });
}

/* ============================================================
   X. 消息气泡扩展样式
   ============================================================ */
function addStyledMsg(text, who, cls) {
  const div = document.createElement('div');
  div.className = 'msg ' + who + (cls ? ' ' + cls : '');
  const whoLabel = { user: '你', bot: '雷霆', sys: '系统' }[who] || '?';
  div.innerHTML = `<span class="who">${whoLabel}</span><span class="msg-body">${text}</span>`;
  chatBox.appendChild(div);
  scrollChatBottom();
}

/* ============================================================
   Y. 自动回复增强
   ============================================================ */
function smartReply(text) {
  const lower = text.toLowerCase();
  // 温度
  if (lower.includes('温度') || lower.includes('热') || lower.includes('烫')) {
    return tempAffectedReply();
  }
  // 电量
  if (lower.includes('电量') || lower.includes('电池') || lower.includes('充电')) {
    return battAffectedReply();
  }
  // 健康
  if (lower.includes('健康') || lower.includes('坏') || lower.includes('修')) {
    return healthAffectedReply();
  }
  // 帧率
  if (lower.includes('帧率') || lower.includes('卡') || lower.includes('慢')) {
    return fpsAffectedReply();
  }
  // 批量台词
  if (Math.random() < 0.3) {
    return pick(REPLY_ALL_BULK);
  }
  // 兜底
  return pick(REPLY_GENERIC);
}

console.log('%c⚡ 雷霆人工智障模型 已启动 ⚡',
  'color:#00ffaa; background:#000; font-size:20px; padding:10px; font-weight:bold;');
console.log('%c输入 boom 引爆手机',
  'color:#ffe14d; font-size:14px;');

/* ============================================================
   N. 定时随机事件（每 20 秒随机出一句剧情）
   ============================================================ */
const AMBIENT_LINES = [
  "🌡️ 芯片温度悄悄上升中……",
  "📱 后台又自启了 5 个 APP……",
  "🔋 电池又掉了 1%……",
  "⚡ 雷电在芯片里乱窜……",
  "🌡️ 骁龙450 表示压力很大……",
  "📶 WiFi 又卡了一下……",
  "🔥 机身开始微微发热……",
  "💾 内存又不够用了……",
];
setInterval(() => {
  if (document.hidden) return;
  if (Math.random() < 0.55) {
    botSay(pick(AMBIENT_LINES), 25);
    S.temp = clamp(S.temp + rand(0.2, 0.8), 36, 110);
  }
}, 22000);

/* ============================================================
   O. 键盘快捷键
   ============================================================ */
document.addEventListener('keydown', (e) => {
  // Ctrl + B 直接爆炸
  if ((e.ctrlKey || e.metaKey) && e.key === 'b') {
    e.preventDefault();
    input.value = 'boom';
    doSend();
  }
  // Ctrl + K 清屏
  if ((e.ctrlKey || e.metaKey) && e.key === 'k') {
    e.preventDefault();
    input.value = 'clear';
    doSend();
  }
  // Ctrl + H 帮助
  if ((e.ctrlKey || e.metaKey) && e.key === 'h') {
    e.preventDefault();
    $('#help-panel').classList.toggle('on');
  }
  // 按 ? 帮助
  if (e.key === '?') {
    $('#help-panel').classList.toggle('on');
  }
});

/* ============================================================
   P. 页面可见性：切后台暂停 BGM
   ============================================================ */
document.addEventListener('visibilitychange', () => {
  if (document.hidden) {
    stopBGM();
  }
});

/* ============================================================
   Q. 防止意外退出
   ============================================================ */
window.addEventListener('beforeunload', (e) => {
  if (S.exploded) {
    // 已经炸过，不拦
    return;
  }
  e.preventDefault();
  e.returnValue = '手机还没炸，确定要走吗？';
  return e.returnValue;
});

/* ============================================================
   R. 自动聚焦输入框
   ============================================================ */
window.addEventListener('load', () => {
  setTimeout(() => input.focus(), 800);
});

/* ============================================================
   S. 双击聊天框触发小爆炸
   ============================================================ */
chatBox.addEventListener('dblclick', () => {
  const rect = chatBox.getBoundingClientRect();
  spawnExplosion(rect.left + rect.width / 2, rect.top + rect.height / 2, 40);
  playBoom();
  triggerScreenShake(false);
});

/* ============================================================
   T. 初始化完成
   ============================================================ */
console.log('%c[ThunderAI] 全部模块加载完成', 'color:#00ffaa; font-weight:bold;');
console.log('[ThunderAI] 已注册命令: boom / 和平精英 / 原神 / 转转 / 斧子 / 五星 / 梨花 / 超频 / 拆芯片 / 温度 / 电量 / WiFi / 王者 / 拍照 / 清理 / 抽签 / help / clear / exit');
console.log('[ThunderAI] 祝使用愉快，小心爆炸！');


</script>
</body>
</html>
