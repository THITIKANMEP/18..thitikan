<html lang="th" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>คณิตศาสตร์การเงิน ป.5</title>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@400;500;600;700&amp;display=swap" rel="stylesheet">
  <style>
    body {
      box-sizing: border-box;
      font-family: 'Kanit', sans-serif;
    }
    
    .problem-card {
      transition: all 0.3s ease;
    }
    
    .problem-card:hover {
      transform: translateY(-4px);
    }
    
    .coin-icon {
      animation: float 3s ease-in-out infinite;
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }
    
    .result-show {
      animation: slideDown 0.4s ease-out;
    }
    
    @keyframes slideDown {
      from {
        opacity: 0;
        transform: translateY(-10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    .btn-calculate {
      transition: all 0.2s ease;
    }
    
    .btn-calculate:active {
      transform: scale(0.95);
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full w-full">
  <div id="app-wrapper" class="h-full w-full overflow-auto"><!-- Main Container -->
   <div class="min-h-full p-6"><!-- Header -->
    <header class="text-center mb-8">
     <div class="coin-icon text-6xl mb-4">
      💰
     </div>
     <h1 id="main-title" class="text-5xl font-bold mb-2">คณิตศาสตร์การเงิน</h1>
     <p id="subtitle" class="text-xl">สำหรับนักเรียนชั้นประถมศึกษาปีที่ 5</p>
    </header><!-- Problems Grid -->
    <div class="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-6"><!-- Problem 1: Savings -->
     <div class="problem-card rounded-2xl p-6 shadow-lg">
      <div class="text-4xl mb-4">
       🏦
      </div>
      <h2 id="savings-title" class="text-2xl font-bold mb-4">การออมเงิน</h2>
      <p class="mb-4 text-base">ถ้าคุณออมเงินวันละ 20 บาท จะได้เงินเท่าไหร่ใน 30 วัน?</p>
      <div class="space-y-3">
       <div><label for="daily-saving" class="block text-sm font-medium mb-1">ออมวันละ (บาท)</label> <input type="number" id="daily-saving" value="20" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div>
       <div><label for="days-saving" class="block text-sm font-medium mb-1">จำนวนวัน</label> <input type="number" id="days-saving" value="30" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div><button onclick="calculateSavings()" class="btn-calculate w-full py-3 rounded-lg font-semibold text-lg shadow-md"> คำนวณ </button>
       <div id="savings-result" class="mt-4 p-4 rounded-lg text-center font-bold text-xl" style="display: none;"></div>
      </div>
     </div><!-- Problem 2: Interest -->
     <div class="problem-card rounded-2xl p-6 shadow-lg">
      <div class="text-4xl mb-4">
       📈
      </div>
      <h2 id="interest-title" class="text-2xl font-bold mb-4">คำนวณดอกเบี้ย</h2>
      <p class="mb-4 text-base">ฝากเงินในธนาคาร จะได้ดอกเบี้ยเท่าไหร่?</p>
      <div class="space-y-3">
       <div><label for="principal" class="block text-sm font-medium mb-1">เงินต้น (บาท)</label> <input type="number" id="principal" value="1000" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div>
       <div><label for="interest-rate" class="block text-sm font-medium mb-1">อัตราดอกเบี้ย (%/ปี)</label> <input type="number" id="interest-rate" value="2" step="0.1" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div>
       <div><label for="years" class="block text-sm font-medium mb-1">จำนวนปี</label> <input type="number" id="years" value="1" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div><button onclick="calculateInterest()" class="btn-calculate w-full py-3 rounded-lg font-semibold text-lg shadow-md"> คำนวณ </button>
       <div id="interest-result" class="mt-4 p-4 rounded-lg text-center font-bold text-xl" style="display: none;"></div>
      </div>
     </div><!-- Problem 3: Budget -->
     <div class="problem-card rounded-2xl p-6 shadow-lg">
      <div class="text-4xl mb-4">
       💵
      </div>
      <h2 id="budget-title" class="text-2xl font-bold mb-4">จัดการงบประมาณ</h2>
      <p class="mb-4 text-base">คุณมีเงิน 500 บาท จะซื้อของได้กี่ชิ้น?</p>
      <div class="space-y-3">
       <div><label for="total-money" class="block text-sm font-medium mb-1">เงินที่มี (บาท)</label> <input type="number" id="total-money" value="500" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div>
       <div><label for="item-price" class="block text-sm font-medium mb-1">ราคาต่อชิ้น (บาท)</label> <input type="number" id="item-price" value="35" class="w-full px-4 py-2 border-2 rounded-lg focus:outline-none focus:ring-2">
       </div><button onclick="calculateBudget()" class="btn-calculate w-full py-3 rounded-lg font-semibold text-lg shadow-md"> คำนวณ </button>
       <div id="budget-result" class="mt-4 p-4 rounded-lg text-center font-bold" style="display: none;"></div>
      </div>
     </div>
    </div><!-- Tips Section -->
    <div class="max-w-6xl mx-auto mt-8 rounded-2xl p-6 shadow-lg">
     <h3 class="text-2xl font-bold mb-4">💡 เคล็ดลับการใช้เงิน</h3>
     <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div class="p-4 rounded-lg">
       <div class="text-3xl mb-2">
        🎯
       </div>
       <h4 class="font-semibold mb-1">ตั้งเป้าหมาย</h4>
       <p class="text-sm">วางแผนก่อนใช้เงินทุกครั้ง</p>
      </div>
      <div class="p-4 rounded-lg">
       <div class="text-3xl mb-2">
        📝
       </div>
       <h4 class="font-semibold mb-1">จดบันทึก</h4>
       <p class="text-sm">บันทึกรายรับรายจ่ายทุกวัน</p>
      </div>
      <div class="p-4 rounded-lg">
       <div class="text-3xl mb-2">
        🌟
       </div>
       <h4 class="font-semibold mb-1">ออมสม่ำเสมอ</h4>
       <p class="text-sm">ออมเงินเป็นประจำทุกวัน</p>
      </div>
     </div>
    </div>
   </div>
  </div>
  <script>
    const defaultConfig = {
      background_color: '#E3F2FD',
      card_color: '#FFFFFF',
      primary_color: '#2196F3',
      text_color: '#1565C0',
      accent_color: '#00BCD4',
      font_family: 'Kanit',
      font_size: 16,
      main_title: 'คณิตศาสตร์การเงิน',
      subtitle: 'สำหรับนักเรียนชั้นประถมศึกษาปีที่ 5',
      savings_title: 'การออมเงิน',
      interest_title: 'คำนวณดอกเบี้ย',
      budget_title: 'จัดการงบประมาณ'
    };

    async function onConfigChange(config) {
      const backgroundColor = config.background_color || defaultConfig.background_color;
      const cardColor = config.card_color || defaultConfig.card_color;
      const primaryColor = config.primary_color || defaultConfig.primary_color;
      const textColor = config.text_color || defaultConfig.text_color;
      const accentColor = config.accent_color || defaultConfig.accent_color;
      const fontFamily = config.font_family || defaultConfig.font_family;
      const fontSize = config.font_size || defaultConfig.font_size;

      // Apply colors
      document.getElementById('app-wrapper').style.background = backgroundColor;
      document.body.style.color = textColor;
      
      const cards = document.querySelectorAll('.problem-card');
      cards.forEach(card => {
        card.style.backgroundColor = cardColor;
        card.style.color = textColor;
      });
      
      const buttons = document.querySelectorAll('.btn-calculate');
      buttons.forEach(btn => {
        btn.style.backgroundColor = primaryColor;
        btn.style.color = '#FFFFFF';
      });
      
      const inputs = document.querySelectorAll('input');
      inputs.forEach(input => {
        input.style.borderColor = primaryColor;
        input.style.color = textColor;
      });
      
      document.querySelector('.max-w-6xl.mt-8').style.backgroundColor = cardColor;
      document.querySelector('.max-w-6xl.mt-8').style.color = textColor;
      
      const tipCards = document.querySelectorAll('.max-w-6xl.mt-8 .p-4.rounded-lg');
      tipCards.forEach(card => {
        card.style.backgroundColor = backgroundColor;
      });

      // Apply font
      const baseFontStack = 'sans-serif';
      document.body.style.fontFamily = `${fontFamily}, ${baseFontStack}`;
      
      // Apply font sizes
      document.getElementById('main-title').style.fontSize = `${fontSize * 2.5}px`;
      document.getElementById('subtitle').style.fontSize = `${fontSize * 1.25}px`;
      
      const h2Elements = document.querySelectorAll('h2');
      h2Elements.forEach(h2 => {
        h2.style.fontSize = `${fontSize * 1.5}px`;
      });
      
      const h3Elements = document.querySelectorAll('h3');
      h3Elements.forEach(h3 => {
        h3.style.fontSize = `${fontSize * 1.5}px`;
      });
      
      const h4Elements = document.querySelectorAll('h4');
      h4Elements.forEach(h4 => {
        h4.style.fontSize = `${fontSize * 1}px`;
      });
      
      const pElements = document.querySelectorAll('p');
      pElements.forEach(p => {
        p.style.fontSize = `${fontSize}px`;
      });
      
      const labels = document.querySelectorAll('label');
      labels.forEach(label => {
        label.style.fontSize = `${fontSize * 0.875}px`;
      });
      
      buttons.forEach(btn => {
        btn.style.fontSize = `${fontSize * 1.125}px`;
      });

      // Apply text content
      document.getElementById('main-title').textContent = config.main_title || defaultConfig.main_title;
      document.getElementById('subtitle').textContent = config.subtitle || defaultConfig.subtitle;
      document.getElementById('savings-title').textContent = config.savings_title || defaultConfig.savings_title;
      document.getElementById('interest-title').textContent = config.interest_title || defaultConfig.interest_title;
      document.getElementById('budget-title').textContent = config.budget_title || defaultConfig.budget_title;
    }

    function calculateSavings() {
      const daily = parseFloat(document.getElementById('daily-saving').value) || 0;
      const days = parseFloat(document.getElementById('days-saving').value) || 0;
      const total = daily * days;
      
      const resultDiv = document.getElementById('savings-result');
      resultDiv.textContent = `ออมได้ ${total.toLocaleString()} บาท! ���`;
      resultDiv.style.display = 'block';
      resultDiv.className = 'result-show mt-4 p-4 rounded-lg text-center font-bold text-xl';
      resultDiv.style.backgroundColor = window.elementSdk?.config?.accent_color || defaultConfig.accent_color;
      resultDiv.style.color = '#FFFFFF';
    }

    function calculateInterest() {
      const principal = parseFloat(document.getElementById('principal').value) || 0;
      const rate = parseFloat(document.getElementById('interest-rate').value) || 0;
      const years = parseFloat(document.getElementById('years').value) || 0;
      
      const interest = (principal * rate * years) / 100;
      const total = principal + interest;
      
      const resultDiv = document.getElementById('interest-result');
      resultDiv.innerHTML = `ดอกเบี้ย: ${interest.toLocaleString()} บาท<br>รวม��ั้งหม��: ${total.toLocaleString()} บาท 💵`;
      resultDiv.style.display = 'block';
      resultDiv.className = 'result-show mt-4 p-4 rounded-lg text-center font-bold text-xl';
      resultDiv.style.backgroundColor = window.elementSdk?.config?.accent_color || defaultConfig.accent_color;
      resultDiv.style.color = '#FFFFFF';
    }

    function calculateBudget() {
      const money = parseFloat(document.getElementById('total-money').value) || 0;
      const price = parseFloat(document.getElementById('item-price').value) || 0;
      
      if (price === 0) {
        const resultDiv = document.getElementById('budget-result');
        resultDiv.textContent = 'กรุณาใส่ราคาที่มากกว่า 0';
        resultDiv.style.display = 'block';
        resultDiv.style.backgroundColor = '#EF4444';
        resultDiv.style.color = '#FFFFFF';
        return;
      }
      
      const items = Math.floor(money / price);
      const leftover = money % price;
      
      const resultDiv = document.getElementById('budget-result');
      resultDiv.innerHTML = `ซื้อได้ ${items} ชิ้น<br>เงินเหลือ ${leftover.toLocaleString()} บาท 🛍️`;
      resultDiv.style.display = 'block';
      resultDiv.className = 'result-show mt-4 p-4 rounded-lg text-center font-bold';
      resultDiv.style.backgroundColor = window.elementSdk?.config?.accent_color || defaultConfig.accent_color;
      resultDiv.style.color = '#FFFFFF';
    }

    // Initialize SDK
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities: (config) => ({
          recolorables: [
            {
              get: () => config.background_color || defaultConfig.background_color,
              set: (value) => {
                config.background_color = value;
                window.elementSdk.setConfig({ background_color: value });
              }
            },
            {
              get: () => config.card_color || defaultConfig.card_color,
              set: (value) => {
                config.card_color = value;
                window.elementSdk.setConfig({ card_color: value });
              }
            },
            {
              get: () => config.text_color || defaultConfig.text_color,
              set: (value) => {
                config.text_color = value;
                window.elementSdk.setConfig({ text_color: value });
              }
            },
            {
              get: () => config.primary_color || defaultConfig.primary_color,
              set: (value) => {
                config.primary_color = value;
                window.elementSdk.setConfig({ primary_color: value });
              }
            },
            {
              get: () => config.accent_color || defaultConfig.accent_color,
              set: (value) => {
                config.accent_color = value;
                window.elementSdk.setConfig({ accent_color: value });
              }
            }
          ],
          borderables: [],
          fontEditable: {
            get: () => config.font_family || defaultConfig.font_family,
            set: (value) => {
              config.font_family = value;
              window.elementSdk.setConfig({ font_family: value });
            }
          },
          fontSizeable: {
            get: () => config.font_size || defaultConfig.font_size,
            set: (value) => {
              config.font_size = value;
              window.elementSdk.setConfig({ font_size: value });
            }
          }
        }),
        mapToEditPanelValues: (config) => new Map([
          ['main_title', config.main_title || defaultConfig.main_title],
          ['subtitle', config.subtitle || defaultConfig.subtitle],
          ['savings_title', config.savings_title || defaultConfig.savings_title],
          ['interest_title', config.interest_title || defaultConfig.interest_title],
          ['budget_title', config.budget_title || defaultConfig.budget_title]
        ])
      });

      onConfigChange(window.elementSdk.config);
    } else {
      onConfigChange(defaultConfig);
    }
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9c133d9e14607334',t:'MTc2ODk2MTA2NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
