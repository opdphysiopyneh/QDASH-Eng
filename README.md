# QDASH-Eng

<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>QuickDASH Outcome Measure & Pain Assessment</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0, shrink-to-fit=no, viewport-fit=cover">
  <style>
    :root {
      --primary: #007AFF;
      --primary-active: #0056b3;
      --bg: #F2F2F7;
      --card-bg: #FFFFFF;
      --text-main: #000000;
      --text-muted: #6C6C70;
      --border: #D1D1D6;
      --selected-bg: #E3F0FF;
      --error-border: #FF3B30;
      --error-bg: #FFF2F2;
    }

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      -webkit-text-size-adjust: 100%;
    }

    html, body {
      width: 100%;
      overflow-x: hidden;
      scroll-behavior: smooth;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display", "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      margin: 0;
      padding: env(safe-area-inset-top, 12px) 14px calc(36px + env(safe-area-inset-bottom, 20px)) 14px;
      font-size: clamp(17px, 4.8vw, 20px);
      line-height: 1.45;
    }

    .container {
      width: 100%;
      max-width: 600px;
      margin: 0 auto;
    }

    .header-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 16px 14px;
      margin-top: 6px;
      margin-bottom: 14px;
      text-align: center;
      box-shadow: 0 1px 4px rgba(0,0,0,0.06);
      border: 1px solid var(--border);
    }

    .main-title {
      font-size: clamp(1.4rem, 5.5vw, 1.85rem);
      font-weight: 800;
      margin: 0 0 8px 0;
      color: var(--text-main);
      line-height: 1.25;
      white-space: pre-line;
    }

    .instruction {
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: var(--text-muted);
      margin: 0;
      line-height: 1.5;
    }

    .nprs-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
    }

    .nprs-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      margin-bottom: 8px;
    }

    .nprs-badge {
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--primary);
    }

    .slider-container {
      margin: 20px 0 10px 0;
    }

    .nprs-slider {
      -webkit-appearance: none;
      width: 100%;
      height: 10px;
      border-radius: 5px;
      background: linear-gradient(to right, #34C759 0%, #FFCC00 50%, #FF3B30 100%);
      outline: none;
      cursor: pointer;
    }

    .nprs-slider::-webkit-slider-thumb {
      -webkit-appearance: none;
      appearance: none;
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: #FFFFFF;
      border: 3px solid var(--primary);
      box-shadow: 0 2px 6px rgba(0,0,0,0.3);
      cursor: pointer;
      transition: transform 0.1s;
    }

    .nprs-slider::-webkit-slider-thumb:active {
      transform: scale(1.15);
    }

    .slider-labels {
      display: flex;
      justify-content: space-between;
      margin-top: 10px;
      font-size: 0.95rem;
      font-weight: 700;
    }

    .label-left {
      color: #28A745;
      text-align: left;
    }

    .label-right {
      color: #DC3545;
      text-align: right;
    }

    .question-card {
      background: var(--card-bg);
      border-radius: 16px;
      padding: 18px 14px;
      margin-bottom: 14px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.05);
      border: 1.5px solid var(--border);
      transition: border-color 0.2s, background-color 0.2s;
    }

    .question-card.highlight-error {
      border-color: var(--error-border) !important;
      background-color: var(--error-bg);
      animation: pulse-border 1.5s infinite;
    }

    @keyframes pulse-border {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.01); }
    }

    .question-title {
      font-size: clamp(1.2rem, 4.8vw, 1.4rem);
      font-weight: 700;
      color: var(--text-main);
      line-height: 1.35;
      margin-bottom: 12px;
    }

    .options-group {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .option-item {
      display: flex;
      align-items: center;
      padding: 14px 14px;
      border-radius: 14px;
      background: #F8F8FA;
      border: 2px solid transparent;
      cursor: pointer;
      font-size: clamp(1.05rem, 4.2vw, 1.2rem);
      color: #1C1C1E;
      transition: all 0.15s ease-in-out;
      user-select: none;
    }

    .option-item:active {
      transform: scale(0.99);
      background: #E5E5EA;
    }

    .option-item.selected {
      background: var(--selected-bg);
      border-color: var(--primary);
      color: #004CB8;
      font-weight: 700;
    }

    .custom-radio {
      width: 24px;
      height: 24px;
      border-radius: 50%;
      border: 2px solid #8E8E93;
      margin-right: 12px;
      flex-shrink: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #FFF;
      transition: border-color 0.15s, background-color 0.15s;
    }

    .option-item.selected .custom-radio {
      border-color: var(--primary);
      background: var(--primary);
    }

    .option-item.selected .custom-radio::after {
      content: "";
      width: 10px;
      height: 10px;
      background: #FFF;
      border-radius: 50%;
    }

    .option-text {
      flex-grow: 1;
      line-height: 1.4;
    }

    .hidden-radio {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    .calc-btn {
      margin-top: 16px;
      padding: 18px;
      width: 100%;
      background: var(--primary);
      color: #FFFFFF;
      font-size: clamp(1.2rem, 5vw, 1.35rem);
      font-weight: 700;
      border: none;
      border-radius: 16px;
      cursor: pointer;
      box-shadow: 0 4px 14px rgba(0, 122, 255, 0.35);
      transition: background 0.15s, transform 0.1s;
    }

    .calc-btn:active {
      background: var(--primary-active);
      transform: scale(0.98);
    }

    .modal {
      display: none;
      position: fixed;
      z-index: 999;
      inset: 0;
      background: rgba(0, 0, 0, 0.5);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
      align-items: center;
      justify-content: center;
      padding: 16px;
    }

    .modal-content {
      background: #FFFFFF;
      padding: 24px 18px;
      border-radius: 22px;
      width: 100%;
      max-width: 400px;
      text-align: center;
      box-shadow: 0 12px 36px rgba(0,0,0,0.25);
    }

    .modal-content h2 {
      margin: 0 0 12px 0;
      font-size: 1.6rem;
    }

    .result-block {
      background: #F8F8FA;
      border-radius: 14px;
      padding: 12px;
      margin-bottom: 12px;
    }

    .result-label {
      font-size: 1rem;
      color: var(--text-muted);
      margin: 0 0 4px 0;
    }

    .result-val {
      font-size: 2.2rem;
      font-weight: 800;
      color: var(--primary);
      margin: 0;
    }

    .notice-box {
      background: #FFF9E6;
      border: 1.5px solid #FFD666;
      padding: 14px;
      margin: 16px 0;
      font-size: 1.05rem;
      color: #874D00;
      border-radius: 12px;
      line-height: 1.5;
      font-weight: 700;
    }

    .close-btn {
      width: 100%;
      padding: 16px;
      background: #1C1C1E;
      color: #FFF;
      font-size: 1.2rem;
      font-weight: 700;
      border: none;
      border-radius: 14px;
      cursor: pointer;
    }
  </style>
</head>
<body>

<div class="container">
  <div class="header-card">
    <h1 class="main-title" id="formTitle"></h1>
    <p class="instruction" id="formInstruction"></p>
  </div>

  <form id="evaluationForm">
    <div class="nprs-card" id="nprsCard" style="display: none;">
      <div class="nprs-header">
        <span class="question-title" style="margin-bottom: 0;">Numeric Pain Rating Scale (NPRS)</span>
        <span id="nprsValueDisplay" class="nprs-badge">0 / 10</span>
      </div>
      <p style="font-size: 0.95rem; color: var(--text-muted); margin: 4px 0 14px 0;">Please slide to select your current level of pain:</p>
      
      <div class="slider-container">
        <input type="range" min="0" max="10" value="0" step="1" class="nprs-slider" id="nprsSlider" oninput="updateNprs(this.value)">
      </div>
      
      <div class="slider-labels">
        <span class="label-left">0<br>No Pain</span>
        <span class="label-right">10<br>Worst Imaginable Pain</span>
      </div>
    </div>

    <div id="questionsContainer"></div>
    
    <button type="button" class="calc-btn" onclick="submitAssessment()">Calculate Assessment Result</button>
  </form>
</div>

<div id="scoreModal" class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle" onclick="handleBackdropClick(event)">
  <div class="modal-content" onclick="event.stopPropagation()">
    <h2 id="modalTitle">Assessment Result</h2>
    
    <div class="result-block" id="nprsResultBlock" style="display: none;">
      <p class="result-label">Pain Level (NPRS)</p>
      <p id="modalNprsText" class="result-val">0 / 10</p>
    </div>

    <div class="result-block">
      <p class="result-label" id="modalScoreTitle">QuickDASH Disability Score</p>
      <p id="modalScoreValue" class="result-val">0</p>
      <p id="modalScoreSubtitle" style="font-size: 0.95rem; margin: 4px 0 0 0; color: var(--text-muted);"></p>
    </div>

    <p id="modalScoreNote" style="font-size: 0.95rem; color: var(--text-muted); margin: 8px 0 12px 0;"></p>

    <div class="notice-box">
      Please do not leave this page and present it to your therapist.<br>
      Alternatively, you may take a screenshot.<br>
      Thank you.
    </div>
    
    <button type="button" class="close-btn" onclick="closeModal()">Close</button>
  </div>
</div>

<script>
const difficultyLabels = [
  { key: "1", value: 1, label: "No difficulty" },
  { key: "2", value: 2, label: "Mild difficulty" },
  { key: "3", value: 3, label: "Moderate difficulty" },
  { key: "4", value: 4, label: "Severe difficulty" },
  { key: "5", value: 5, label: "Unable" }
];

const q7SocialImpactLabels = [
  { key: "1", value: 1, label: "Not at all" },
  { key: "2", value: 2, label: "Slightly" },
  { key: "3", value: 3, label: "Moderately" },
  { key: "4", value: 4, label: "Quite a bit" },
  { key: "5", value: 5, label: "Extremely" }
];

const q8ActivityLimitationLabels = [
  { key: "1", value: 1, label: "Not limited at all" },
  { key: "2", value: 2, label: "Slightly limited" },
  { key: "3", value: 3, label: "Moderately limited" },
  { key: "4", value: 4, label: "Very limited" },
  { key: "5", value: 5, label: "Unable" }
];

const severityLabels = [
  { key: "1", value: 1, label: "None" },
  { key: "2", value: 2, label: "Mild" },
  { key: "3", value: 3, label: "Moderate" },
  { key: "4", value: 4, label: "Severe" },
  { key: "5", value: 5, label: "Extreme" }
];

const q11SleepImpactLabels = [
  { key: "1", value: 1, label: "No difficulty" },
  { key: "2", value: 2, label: "Mild difficulty" },
  { key: "3", value: 3, label: "Moderate difficulty" },
  { key: "4", value: 4, label: "Severe difficulty" },
  { key: "5", value: 5, label: "So much difficulty that I can't sleep" }
];

const CONFIG = {
  title: "QuickDASH Outcome Measure",
  instruction: "Please select the single option that best describes your condition <strong>in the past week</strong>.",
  enableNprs: true,
  items: [
    { title: "Open a tight or new jar.", options: difficultyLabels },
    { title: "Do heavy household chores (e.g., wash walls, floors).", options: difficultyLabels },
    { title: "Carry a shopping bag or briefcase.", options: difficultyLabels },
    { title: "Wash your back.", options: difficultyLabels },
    { title: "Use a knife to cut food.", options: difficultyLabels },
    { title: "Recreational activities requiring force/impact through the arm (e.g., golf, hammering, tennis).", options: difficultyLabels },
    { title: "Extent your arm/shoulder/hand problem interfered with normal social activities.", options: q7SocialImpactLabels },
    { title: "Limitation in work or other regular daily activities due to arm/shoulder/hand problem.", options: q8ActivityLimitationLabels },
    { title: "Arm, shoulder or hand pain.", options: severityLabels },
    { title: "Tingling (pins and needles) in your arm, shoulder or hand.", options: severityLabels },
    { title: "During the past week, how much difficulty you had sleeping because of your arm/shoulder/hand pain.", options: q11SleepImpactLabels }
  ]
};

document.addEventListener("DOMContentLoaded", () => {
  initQuestionnaire();
});

function initQuestionnaire() {
  document.getElementById("formTitle").textContent = CONFIG.title;
  document.getElementById("formInstruction").innerHTML = CONFIG.instruction;
  document.getElementById("modalScoreNote").innerHTML = CONFIG.scoreNote || "";

  if (CONFIG.enableNprs) {
    document.getElementById("nprsCard").style.display = "block";
    document.getElementById("nprsResultBlock").style.display = "block";
  }

  const container = document.getElementById("questionsContainer");
  container.innerHTML = "";

  CONFIG.items.forEach((item, index) => {
    const qNum = index + 1;
    const card = document.createElement("div");
    card.className = "question-card";
    card.id = `card-q${qNum}`;

    const title = document.createElement("div");
    title.className = "question-title";
    title.textContent = `${qNum}. ${item.title}`;
    card.appendChild(title);

    const optionsGroup = document.createElement("div");
    optionsGroup.className = "options-group";

    item.options.forEach(opt => {
      const label = document.createElement("label");
      label.className = "option-item";
      label.htmlFor = `q${qNum}_${opt.key}`;

      const radio = document.createElement("input");
      radio.type = "radio";
      radio.name = `q${qNum}`;
      radio.id = `q${qNum}_${opt.key}`;
      radio.value = opt.value;
      radio.className = "hidden-radio";

      radio.addEventListener("change", () => {
        optionsGroup.querySelectorAll(".option-item").forEach(el => el.classList.remove("selected"));
        if (radio.checked) {
          label.classList.add("selected");
          card.classList.remove("highlight-error");
        }
      });

      const dot = document.createElement("span");
      dot.className = "custom-radio";
      dot.setAttribute("aria-hidden", "true");

      const itemText = document.createElement("span");
      itemText.className = "option-text";
      itemText.textContent = opt.label;

      label.append(radio, dot, itemText);
      optionsGroup.appendChild(label);
    });

    card.appendChild(optionsGroup);
    container.appendChild(card);
  });
}

function updateNprs(val) {
  document.getElementById("nprsValueDisplay").textContent = `${val} / 10`;
}

function submitAssessment() {
  const unanswered = [];
  document.querySelectorAll(".question-card").forEach(c => c.classList.remove("highlight-error"));

  for (let i = 1; i <= CONFIG.items.length; i++) {
    if (!document.querySelector(`input[name="q${i}"]:checked`)) {
      unanswered.push(i);
    }
  }

  if (unanswered.length > 0) {
    unanswered.forEach(num => {
      const card = document.getElementById(`card-q${num}`);
      if (card) card.classList.add("highlight-error");
    });

    const firstCard = document.getElementById(`card-q${unanswered[0]}`);
    if (firstCard) {
      firstCard.scrollIntoView({ behavior: "smooth", block: "center" });
    }
    return;
  }

  let total = 0;
  let count = 0;

  for (let i = 1; i <= CONFIG.items.length; i++) {
    const selected = document.querySelector(`input[name="q${i}"]:checked`);
    if (selected) {
      total += parseInt(selected.value, 10);
      count++;
    }
  }

  const mean = total / count;
  const rawScore = (mean - 1) * 25;
  const roundedScore = Math.round(rawScore);

  if (CONFIG.enableNprs) {
    const nprsVal = document.getElementById("nprsSlider").value;
    document.getElementById("modalNprsText").textContent = `${nprsVal} / 10`;
  }

  document.getElementById("modalScoreValue").textContent = `${roundedScore}%`;
  document.getElementById("modalScoreSubtitle").innerHTML = `Raw total score: <strong>${total}</strong> / 55 (Unrounded: ${rawScore.toFixed(1)})`;

  const modal = document.getElementById("scoreModal");
  modal.style.display = "flex";
}

function closeModal() {
  document.getElementById("scoreModal").style.display = "none";
}

function handleBackdropClick(e) {
  if (e.target.id === "scoreModal") {
    closeModal();
  }
}

document.addEventListener("keydown", (e) => {
  if (e.key === "Escape") {
    closeModal();
  }
});
</script>

</body>
</html>
