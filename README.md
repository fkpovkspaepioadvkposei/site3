<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>С Днём Программиста!</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      background-color: #0a2540;
      overflow: hidden;
      font-family: 'Orbitron', sans-serif;
      position: relative;
    }
    svg {
      width: 100vw;
      height: 100vh;
      display: block;
    }
    .digit {
      font-size: 16px;
      fill: #00eaff;
      animation: fall linear infinite;
      animation-play-state: paused;
    }
    @keyframes fall {
      from { transform: translateY(-100px); opacity: 1; }
      to { transform: translateY(110vh); opacity: 0; }
    }
    .matrix-bg.active .digit {
      animation-play-state: running;
    }
    .frame {
      pointer-events: all;
      filter: drop-shadow(0 0 5px #00eaff);
    }
    .slider-box {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: 300px;
      background-color: #123b5a;
      border: 2px solid #00eaff;
      border-radius: 0 0 10px 10px;
      color: white;
      font-size: 14px;
      padding: 15px;
      box-shadow: 0 2px 20px rgba(0, 234, 255, 0.4);
      transition: top 0.6s ease, opacity 0.6s ease;
      z-index: 10;
      opacity: 0;
    }
    .slider-box.show {
      opacity: 1;
      animation: fadeBounce 0.8s ease;
    }
    @keyframes fadeBounce {
      0% { opacity: 0; transform: translate(-50%, -20px); }
      50% { transform: translate(-50%, 10px); }
      100% { transform: translate(-50%, 0); }
    }
  </style>
</head>
<body>
  <svg viewBox="0 0 1000 600" id="mainSVG">
    <!-- Рамка -->
    <rect x="250" y="150" width="500" height="300" rx="10" ry="10" fill="#123b5a" stroke="#00eaff" stroke-width="2" class="frame"/>
    <!-- Лого омгту -->
    <a href="https://www.omgtu.ru/" target="_blank">
      <image href="omgtu.png" x="235" y="140" width="100" height="100"/>
    </a>
    <!-- Круги  -->
    <g id="circles">
      <g class="circle-btn" transform="translate(700, 200)" data-msg="Поздравляем с праздником от ИСТ-241! Как HTML задаёт структуру сайту, так пусть и в твоей жизни будет четкий план, прочный каркас и уверенное будущее! ">
        <circle cx="0" cy="0" r="30" fill="#ff6a00" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">HTML</text>
      </g>
      <g class="circle-btn" transform="translate(630, 250)" data-msg="Поздравляем с праздником от ИСТ-241! CSS учит нас красоте в деталях — пусть и в твоей жизни будет как можно больше изящества, баланса и ярких цветов!">
        <circle cx="0" cy="0" r="30" fill="#0056d6" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">CSS</text>
      </g>
      <g class="circle-btn" transform="translate(700, 300)" data-msg="Поздравляем с праздником от ИСТ-241! JS оживляет всё — пусть и твоя жизнь будет полна динамики!">
        <circle cx="0" cy="0" r="30" fill="#669d34" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">JS</text>
      </g>
      <!-- Полукруг C# сверху над CSS -->
      <g class="circle-btn" transform="translate(630, 151)" data-msg="Поздравляем с праздником от ИСТ-241! C# учит нас дисциплине и структуре — желаем тебе целеустремлённости, стабильности и продуктивности в каждой строке жизни!">
        <path d="M -30 0 A 30 30 0 0 1 30 0 L 0 0 Z" fill="#61187c" transform="rotate(180)" style="cursor: pointer;"/>
        <text x="-11" y="18" font-size="15" fill="white">C#</text>
      </g>
      <!-- Полукруг Python справа от рамки -->
      <g class="circle-btn" transform="translate(749, 360)" data-msg="Поздравляем с праздником от ИСТ-241! Python всё упрощает — пусть в твоей жизни всё будет легко!">
        <path d="M 0 -30 A 30 30 0 0 1 0 30 L 0 0 Z" fill="#d2d202" transform="scale(-1,1)" style="cursor: pointer;"/>
        <text x="-13" y="5" font-size="13" fill="white" text-anchor="middle">Pyt</text>
      </g>
    </g>
    <!-- Надпись внизу слева -->
    <text x="280" y="340" font-size="40" fill="white">С днём</text>
    <text x="280" y="390" font-size="52" fill="#00eaff">Программиста!</text>
    <!-- Эффект матрицы -->
    <g id="binaryDigits" class="matrix-bg"></g>
  </svg>
  <div id="slider" class="slider-box"></div>
  <script>
    const digitGroup = document.getElementById('binaryDigits');
    const numDigits = 100;
    for (let i = 0; i < numDigits; i++) {
      const digit = document.createElementNS("http://www.w3.org/2000/svg", "text");
      digit.textContent = Math.random() > 0.5 ? '1' : '0';
      digit.setAttribute("class", "digit");
      digit.setAttribute("x", Math.random() * 1000);
      digit.setAttribute("y", Math.random() * -600);
      digit.style.animationDuration = (5 + Math.random() * 5) + "s";
      digit.style.animationDelay = (Math.random() * 5) + "s";
      digitGroup.appendChild(digit);
    }
    const matrixBg = document.querySelector('.matrix-bg');
    const frameRect = document.querySelector('.frame');
    const svg = document.getElementById('mainSVG');
    const slider = document.getElementById('slider');
    frameRect.addEventListener('mouseenter', () => matrixBg.classList.add('active'));
    frameRect.addEventListener('mouseleave', () => matrixBg.classList.remove('active'));
    const circles = document.querySelectorAll('.circle-btn');
    let sliderVisible = false;
    function getFrameTopPosition() {
      const svgRect = svg.getBoundingClientRect();
      const frameTop = svgRect.top + 150 * (svg.clientHeight / 600);
      return frameTop;
    }
    circles.forEach(circle => {
      circle.addEventListener('click', () => {
        const msg = circle.getAttribute('data-msg');
        const frameTop = getFrameTopPosition();
        if (!sliderVisible) {
          slider.textContent = msg;
          slider.style.top = (frameTop - 100) + 'px';
          slider.classList.add('show');
        } else {
          slider.classList.remove('show');
        }
        sliderVisible = !sliderVisible;
      });
    });
    window.addEventListener('resize', () => {
      if (sliderVisible) {
        const frameTop = getFrameTopPosition();
        slider.style.top = (frameTop - 100) + 'px';
      }
    });
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>С Днём Программиста!</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      background-color: #0a2540;
      overflow: hidden;
      font-family: 'Orbitron', sans-serif;
      position: relative;
    }
    svg {
      width: 100vw;
      height: 100vh;
      display: block;
    }
    .digit {
      font-size: 16px;
      fill: #00eaff;
      animation: fall linear infinite;
      animation-play-state: paused;
    }
    @keyframes fall {
      from { transform: translateY(-100px); opacity: 1; }
      to { transform: translateY(110vh); opacity: 0; }
    }
    .matrix-bg.active .digit {
      animation-play-state: running;
    }
    .frame {
      pointer-events: all;
      filter: drop-shadow(0 0 5px #00eaff);
    }
    .slider-box {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      width: 300px;
      background-color: #123b5a;
      border: 2px solid #00eaff;
      border-radius: 0 0 10px 10px;
      color: white;
      font-size: 14px;
      padding: 15px;
      box-shadow: 0 2px 20px rgba(0, 234, 255, 0.4);
      transition: top 0.6s ease, opacity 0.6s ease;
      z-index: 10;
      opacity: 0;
    }
    .slider-box.show {
      opacity: 1;
      animation: fadeBounce 0.8s ease;
    }
    @keyframes fadeBounce {
      0% { opacity: 0; transform: translate(-50%, -20px); }
      50% { transform: translate(-50%, 10px); }
      100% { transform: translate(-50%, 0); }
    }
  </style>
</head>
<body>
  <svg viewBox="0 0 1000 600" id="mainSVG">
    <!-- Рамка -->
    <rect x="250" y="150" width="500" height="300" rx="10" ry="10" fill="#123b5a" stroke="#00eaff" stroke-width="2" class="frame"/>
    <!-- Лого омгту -->
    <a href="https://www.omgtu.ru/" target="_blank">
      <image href="omgtu.png" x="235" y="140" width="100" height="100"/>
    </a>
    <!-- Круги  -->
    <g id="circles">
      <g class="circle-btn" transform="translate(700, 200)" data-msg="Поздравляем с праздником от ИСТ-241! Как HTML задаёт структуру сайту, так пусть и в твоей жизни будет четкий план, прочный каркас и уверенное будущее! ">
        <circle cx="0" cy="0" r="30" fill="#ff6a00" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">HTML</text>
      </g>
      <g class="circle-btn" transform="translate(630, 250)" data-msg="Поздравляем с праздником от ИСТ-241! CSS учит нас красоте в деталях — пусть и в твоей жизни будет как можно больше изящества, баланса и ярких цветов!">
        <circle cx="0" cy="0" r="30" fill="#0056d6" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">CSS</text>
      </g>
      <g class="circle-btn" transform="translate(700, 300)" data-msg="Поздравляем с праздником от ИСТ-241! JS оживляет всё — пусть и твоя жизнь будет полна динамики!">
        <circle cx="0" cy="0" r="30" fill="#669d34" style="cursor: pointer;"/>
        <text x="0" y="5" font-size="15" fill="white" text-anchor="middle">JS</text>
      </g>
      <!-- Полукруг C# сверху над CSS -->
      <g class="circle-btn" transform="translate(630, 151)" data-msg="Поздравляем с праздником от ИСТ-241! C# учит нас дисциплине и структуре — желаем тебе целеустремлённости, стабильности и продуктивности в каждой строке жизни!">
        <path d="M -30 0 A 30 30 0 0 1 30 0 L 0 0 Z" fill="#61187c" transform="rotate(180)" style="cursor: pointer;"/>
        <text x="-11" y="18" font-size="15" fill="white">C#</text>
      </g>
      <!-- Полукруг Python справа от рамки -->
      <g class="circle-btn" transform="translate(749, 360)" data-msg="Поздравляем с праздником от ИСТ-241! Python всё упрощает — пусть в твоей жизни всё будет легко!">
        <path d="M 0 -30 A 30 30 0 0 1 0 30 L 0 0 Z" fill="#d2d202" transform="scale(-1,1)" style="cursor: pointer;"/>
        <text x="-13" y="5" font-size="13" fill="white" text-anchor="middle">Pyt</text>
      </g>
    </g>
    <!-- Надпись внизу слева -->
    <text x="280" y="340" font-size="40" fill="white">С днём</text>
    <text x="280" y="390" font-size="52" fill="#00eaff">Программиста!</text>
    <!-- Эффект матрицы -->
    <g id="binaryDigits" class="matrix-bg"></g>
  </svg>
  <div id="slider" class="slider-box"></div>
  <script>
    const digitGroup = document.getElementById('binaryDigits');
    const numDigits = 100;
    for (let i = 0; i < numDigits; i++) {
      const digit = document.createElementNS("http://www.w3.org/2000/svg", "text");
      digit.textContent = Math.random() > 0.5 ? '1' : '0';
      digit.setAttribute("class", "digit");
      digit.setAttribute("x", Math.random() * 1000);
      digit.setAttribute("y", Math.random() * -600);
      digit.style.animationDuration = (5 + Math.random() * 5) + "s";
      digit.style.animationDelay = (Math.random() * 5) + "s";
      digitGroup.appendChild(digit);
    }
    const matrixBg = document.querySelector('.matrix-bg');
    const frameRect = document.querySelector('.frame');
    const svg = document.getElementById('mainSVG');
    const slider = document.getElementById('slider');
    frameRect.addEventListener('mouseenter', () => matrixBg.classList.add('active'));
    frameRect.addEventListener('mouseleave', () => matrixBg.classList.remove('active'));
    const circles = document.querySelectorAll('.circle-btn');
    let sliderVisible = false;
    function getFrameTopPosition() {
      const svgRect = svg.getBoundingClientRect();
      const frameTop = svgRect.top + 150 * (svg.clientHeight / 600);
      return frameTop;
    }
    circles.forEach(circle => {
      circle.addEventListener('click', () => {
        const msg = circle.getAttribute('data-msg');
        const frameTop = getFrameTopPosition();
        if (!sliderVisible) {
          slider.textContent = msg;
          slider.style.top = (frameTop - 100) + 'px';
          slider.classList.add('show');
        } else {
          slider.classList.remove('show');
        }
        sliderVisible = !sliderVisible;
      });
    });
    window.addEventListener('resize', () => {
      if (sliderVisible) {
        const frameTop = getFrameTopPosition();
        slider.style.top = (frameTop - 100) + 'px';
      }
    });
  </script>
</body>
</html>
