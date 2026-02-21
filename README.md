
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>HC Web Services</title>
  <style>
    /* BODY & FONTS */
    body { font-family: Arial, sans-serif; margin:0; padding:0; color:#333; overflow-x:hidden; background:#f7f3ff; transition: background 0.5s, color 0.5s;}
    h1,h2,h3,h4,h5,h6 { color:#7b3fe4; margin-bottom:10px; }
    p,li { margin-bottom:8px; }
    ul { margin-left:20px; }
    a { color:#7b3fe4; text-decoration:none; }
    a:hover { text-decoration:underline; }

    /* BUTTONS */
    .btn { background-color:#5a2bb5; color:white; padding:10px 20px; border-radius:8px; font-weight:bold; cursor:pointer; display:inline-block; margin-top:10px; border:none; }
    .btn:hover, .nav-btn.active { background-color:white; color:#5a2bb5; border:1px solid #5a2bb5; }

    /* HEADER NAVIGATION */
    header { background:#7b3fe4; padding:10px; position:sticky; top:0; z-index:999; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; }
    .logo { color:white; font-size:1.5em; font-weight:bold; }
    nav { display:flex; gap:10px; }
    .nav-btn { background:#5a2bb5; padding:8px 15px; border-radius:5px; border:none; color:white; cursor:pointer; font-weight:bold; }
    .nav-btn:hover, .nav-btn.active { background:white; color:#5a2bb5; border:1px solid #5a2bb5; }
    
    /* Dropdown menu */
    .dropdown { position:relative; display:inline-block; }
    .dropdown-content { display:none; position:absolute; background:#f4f4f4; min-width:120px; box-shadow:0 2px 10px rgba(0,0,0,0.2); border-radius:5px; z-index:1; }
    .dropdown-content button { width:100%; text-align:left; padding:8px; border:none; background:none; cursor:pointer; }
    .dropdown-content button:hover { background:#ddd; color:#5a2bb5; }
    .dropdown:hover .dropdown-content { display:block; }

    /* SECTIONS */
    section { border-radius:10px; padding:25px; margin:20px auto; max-width:1000px; box-shadow:0 2px 10px rgba(0,0,0,0.1); position:relative; z-index:2; background:#f7f3ff; }
    .box { border:1px solid #ddd; padding:20px; border-radius:10px; margin-bottom:20px; background:#f7f3ff; position:relative; z-index:2; }
    .flex { display:flex; flex-wrap:wrap; gap:20px; }
    .card { flex:1 1 250px; background:#f1f1f1; padding:15px; border-radius:10px; }

    /* FORM */
    form input, form select, form textarea, form button { width:100%; padding:10px; margin-bottom:10px; border-radius:6px; border:1px solid #ccc; }
    form button { background:#7b3fe4; color:white; border:none; font-weight:bold; cursor:pointer; }
    form button:hover { background:#5a2bb5; }

    /* AI CHAT BOX */
    #chat-container { position:fixed; bottom:20px; right:20px; width:280px; background:#fff; border-radius:10px; box-shadow:0 2px 12px rgba(0,0,0,0.2); font-size:0.9em; overflow:hidden; z-index:999; }
    #chat-header { background:#7b3fe4; color:white; padding:10px; text-align:center; cursor:pointer; }
    #chat-body { display:none; max-height:300px; overflow-y:auto; padding:10px; }
    #chat-messages { margin-bottom:10px; }
    .message { margin-bottom:10px; }
    .bot { background:#f1f1f1; padding:5px 10px; border-radius:5px; }
    .user { background:#7b3fe4; color:white; padding:5px 10px; border-radius:5px; text-align:right; }

    /* Star Rating */
    .star-rating { display:flex; flex-direction:row-reverse; font-size:1.5em; justify-content:flex-end; margin-bottom:10px; }
    .star-rating input { display:none; }
    .star-rating label { color:#ccc; cursor:pointer; }
    .star-rating input:checked ~ label,
    .star-rating label:hover,
    .star-rating label:hover ~ label { color:gold; }

    /* DARK MODE */
    body.dark { background:#111; color:white; }
    body.dark section.box { background:#222; color:white; }
    body.dark .card { background:#333; color:white; }

    /* MOVING ORBS */
    .orb { position:absolute; border-radius:50%; background:#3b82f6; opacity:0.4; animation:moveOrb linear infinite; }
    @keyframes moveOrb {
      0% { transform:translate(0,0);}
      50% { transform:translate(500px,500px);}
      100% { transform:translate(0,0);}
    }
  </style>
</head>
<body>

<!-- MOVING ORBS -->
<!-- MOVING ORBS -->
<div class="orb" style="width:50px;height:50px;top:10%;left:15%; animation-duration:28s;"></div>
<div class="orb" style="width:35px;height:35px;top:20%;left:70%; animation-duration:35s;"></div>
<div class="orb" style="width:40px;height:40px;top:45%;left:25%; animation-duration:30s;"></div>
<div class="orb" style="width:60px;height:60px;top:55%;left:50%; animation-duration:40s;"></div>
<div class="orb" style="width:30px;height:30px;top:70%;left:10%; animation-duration:22s;"></div>
<div class="orb" style="width:45px;height:45px;top:75%;left:65%; animation-duration:33s;"></div>
<div class="orb" style="width:25px;height:25px;top:30%;left:40%; animation-duration:27s;"></div>
<div class="orb" style="width:55px;height:55px;top:60%;left:80%; animation-duration:38s;"></div>
<div class="orb" style="width:35px;height:35px;top:15%;left:50%; animation-duration:25s;"></div>
<div class="orb" style="width:50px;height:50px;top:50%;left:20%; animation-duration:36s;"></div>

<!-- HEADER WITH NAVIGATION -->
<header>
  <div class="logo">HC Web Services</div>
  <nav class="desktop-nav">
    <button class="nav-btn" onclick="scrollToSection('home')">Home</button>
    <button class="nav-btn" onclick="scrollToSection('about')">About Me</button>
    <button class="nav-btn" onclick="scrollToSection('pricing')">Pricing</button>
    <button class="nav-btn" onclick="scrollToSection('features')">Features</button>
    <button class="nav-btn" onclick="scrollToSection('demo')">Demo</button>
    <button class="nav-btn" onclick="scrollToSection('contact')">Contact</button>
  </nav>
  <div class="dropdown">
    <button class="nav-btn">Menu ▾</button>
    <div class="dropdown-content">
      <button onclick="scrollToSection('home')">Home</button>
      <button onclick="scrollToSection('about')">About Me</button>
      <button onclick="scrollToSection('pricing')">Pricing</button>
      <button onclick="scrollToSection('features')">Features</button>
      <button onclick="scrollToSection('demo')">Demo</button>
      <button onclick="scrollToSection('contact')">Contact</button>
    </div>
  </div>
  <button class="btn" onclick="toggleDarkMode()">Dark Mode</button>
</header>

<!-- HOME SECTION -->
<section class="box" id="home">
  <h1>Welcome to HC Web Services</h1>
  <p>We create clean, professional websites that bring your business to life.</p>
</section>

<!-- ABOUT ME SECTION -->
<section class="box" id="about">
  <h2>About Me</h2>
  <p>Hi, I'm Handy Celestin. I started HC Services in 2025 to support my family and help local businesses grow.</p>
</section>

<!-- PRICING SECTION -->
<section class="box" id="pricing">
  <h2>Pricing Packages</h2>
  <div class="flex">
    <div class="card">
      <h3>Starter – $15</h3>
      <ul>
        <li>1–2 pages</li>
        <li>Clean, professional design</li>
        <li>Mobile-friendly</li>
      </ul>
    </div>
    <div class="card">
      <h3>Growth – $25</h3>
      <ul>
        <li>4–6 pages</li>
        <li>Custom colors & style</li>
        <li>Contact form + CTA</li>
      </ul>
    </div>
    <div class="card">
      <h3>Elite – $35</h3>
      <ul>
        <li>6–10 pages</li>
        <li>Fully custom design</li>
        <li>SEO & speed optimization</li>
      </ul>
    </div>
  </div>
</section>

<!-- FEATURES SECTION -->
<section class="box" id="features">
  <h2>Features</h2>
  <div class="flex">
    <div class="card">
      <h3>AI-Powered Responses</h3>
      <p>Guide your clients intelligently through your website.</p>
    </div>
    <div class="card">
      <h3>Improvement Quiz</h3>
      <p>Engage visitors with smart, interactive quizzes.</p>
    </div>
    <div class="card">
      <h3>Links Feature</h3>
      <p>Clickable text links for better navigation.</p>
    </div>
  </div>
</section>

<!-- DEMO SITE SECTION -->
<section class="box" id="demo">
  <h2>Demo Website</h2>
  <p>See our HC Barbers demo to visualize your future website!</p>
  <a href="https://handyc615-create.github.io/hc-barbers/" class="btn" target="_blank">Visit HC Barbers Demo →</a>
</section>

<!-- BUILD WEBSITE BOX -->
<section class="box">
  <h2>Build Your Website</h2>
  <p>Provide your info, choose a package, and I’ll handle the rest.</p>
  <a href="https://docs.google.com/forms/d/e/1FAIpQLSfyvRIC9p4ngxOnphzVIa5oe-Kuo44Sx-kWdyBmu464cWJyjA/viewform?usp=publish-editor" class="btn" target="_blank">Click to Build Your Website →</a>
</section>

<!-- CONTACT BOX -->
<section class="box" id="contact">
  <h2>Contact</h2>
  <p>Call or Text: 347-309-9586</p>
  <p>Email: <a href="mailto:handyc615@gmail.com">handyc615@gmail.com</a></p>
  <p>Cash App: $HandyCelestin7</p>
  <p>Instagram: @zoeflyxc</p>
</section>

<!-- AI CHAT BOX -->
<div id="chat-container">
  <div id="chat-header">😊 Click to Chat</div>
  <div id="chat-body">
    <div id="chat-messages"></div>
    <div id="chat-input">
      <input type="text" id="user-input" placeholder="Ask about packages, features, or help...">
      <button id="send-btn">Send</button>
    </div>
  </div>
</div>

<footer class="box">
  <p>© 2026 HC Web Services | Built by Handy Celestin</p>
</footer>

<script>
  // Scroll to Section
  function scrollToSection(id){
    document.getElementById(id).scrollIntoView({behavior:'smooth'});
  }

  // Dark Mode
  function toggleDarkMode(){
    document.body.classList.toggle('dark');
  }

  // AI Chat Toggle
  const chatHeader = document.getElementById('chat-header');
  const chatBody = document.getElementById('chat-body');
  chatHeader.addEventListener('click', () => {
    chatBody.style.display = chatBody.style.display === 'block' ? 'none' : 'block';
  });

  // AI Chat Responses
  const chatMessages = document.getElementById('chat-messages');
  const userInput = document.getElementById('user-input');
  const sendBtn = document.getElementById('send-btn');
  const botResponses = {
    'hello':'😊 Hi! Looking for a website or feature?',
    'price':'😊 Starter $15, Growth $25, Elite $35.',
    'feature':'😊 We offer quiz, AI responses, links, and demo sites!',
    'help':'😊 I can guide you through choosing a package or features.'
  };

  function addMessage(text, sender){
    const msg = document.createElement('div');
    msg.className='message '+sender;
    msg.innerText=text;
    chatMessages.appendChild(msg);
    chatMessages.scrollTop=chatMessages.scrollHeight;
  }

  sendBtn.addEventListener('click',()=>{
    const text=userInput.value.toLowerCase();
    if(!text) return;
    addMessage('🤔 '+text,'user');
    let reply='😢 Sorry, I do not understand. Try asking "hello", "price", "feature", or "help".';
    for(const key in botResponses){ if(text.includes(key)) reply=botResponses[key]; }
    setTimeout(()=>addMessage(reply,'bot'),500);
    userInput.value='';
  });
</script>

</body>
</html>
