# nhsajal.github.io

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Md. Nahid Hasan — Faculty | BUET</title>
  <meta name="description" content="Md. Nahid Hasan — Assistant Professor, Department of Mathematics, BUET." />

  <style>
    :root {
      --bg:#ffffff; 
      --text:#0b1220; 
      --muted:#555; 
      --accent:#002b80; 
      --card:#f4f7fb;
    }

    *{box-sizing:border-box}

    body{
      margin:0;
      font-family:Georgia,'Times New Roman',serif;
      color:var(--text);
      background:var(--bg);
    }

    a{color:var(--accent);text-decoration:none}

    .container{
      width:1100px;
      max-width:94%;
      margin:32px auto;
    }

    /* Header */
    header.site{
      display:flex;
      gap:22px;
      align-items:center;
    }

    .avatar{
      width:140px;
      height:140px;
      border-radius:8px;
      overflow:hidden;
      border:1px solid #e6e9ef;
    }

    .avatar img{
      width:100%;
      height:100%;
      object-fit:cover;
    }

    h1{margin:0 0 6px}

    .affil{color:var(--muted)}
    .muted{color:var(--muted); line-height:1.6}

    /* NAV FIXED */
    nav.main{
      margin-top:16px;
      display:flex;
      gap:10px;
      flex-wrap:wrap;
    }

    nav.main a{
      padding:8px 14px;
      border-radius:6px;
      background:var(--card);
      color:var(--text);
      font-weight:600;
      transition:all 0.2s ease;
    }

    nav.main a:hover{
      background:#e6ecf5;
      color:var(--accent);
    }

    nav.main a.active{
      background:var(--accent);
      color:#fff;
    }

    nav.main a:focus{
      outline:2px solid var(--accent);
      outline-offset:2px;
    }

    /* Layout */
    .layout{
      display:grid;
      grid-template-columns:300px 1fr;
      gap:24px;
      margin-top:20px;
    }

    aside{
      background:#fbfcfe;
      padding:18px;
      border-radius:8px;
      border:1px solid #eee;
    }

    .maincard{
      background:#fff;
      padding:20px;
      border-radius:8px;
      border:1px solid #eee;
      animation:fadeIn 0.25s ease;
    }

    @keyframes fadeIn{
      from{opacity:0; transform:translateY(5px)}
      to{opacity:1; transform:translateY(0)}
    }

    /* Buttons */
    .btn{
      display:inline-block;
      padding:8px 14px;
      border-radius:6px;
      background:var(--accent);
      color:#fff;
      font-weight:600;
      margin-top:8px;
    }

    .btn.ghost{
      background:transparent;
      border:1px solid var(--accent);
      color:var(--accent);
    }

    .btn.ghost:hover{
      background:var(--accent);
      color:#fff;
    }

    footer{
      text-align:center;
      margin-top:30px;
      color:var(--muted);
    }

    /* Dark Mode */
    :root.dark-mode{
      --bg:#0b1220;
      --text:#f8f8f8;
      --muted:#aaa;
      --accent:#1e90ff;
      --card:#1a1f2a;
    }

    :root.dark-mode nav.main a:hover{
      background:#2a3140;
    }

    /* Responsive */
    @media(max-width:900px){
      .layout{grid-template-columns:1fr}
    }
  </style>
</head>

<body>

<div class="container">

<header class="site">
  <div class="avatar">
    <img src="https://raw.githubusercontent.com/nhsajal/nhsajal.github.io/main/assets/nahid_photo.jpg" alt="Nahid Hasan">
  </div>

  <div>
    <h1>Md. Nahid Hasan</h1>
    <p class="affil">Lecturer, Mathematics — BUET</p>
    <p class="muted">Computational Mathematics · ML · Modeling</p>

    <nav class="main">
      <a href="#home" data-route="home" class="active">Home</a>
      <a href="#research" data-route="research">Research</a>
      <a href="#publications" data-route="publications">Publications</a>
      <a href="#teaching" data-route="teaching">Teaching</a>
      <a href="#cv" data-route="cv">CV</a>
      <button id="darkToggle" class="btn ghost">Dark</button>
    </nav>
  </div>
</header>

<div class="layout">

<aside>
  <p class="muted">BUET, Dhaka</p>
  <p class="muted">+8801844255970</p>

  <p><a href="https://github.com/nhsajal">github.com/nhsajal</a></p>

  <a class="btn" href="assets/CV_Nahid.pdf">Download CV</a>
</aside>

<section class="maincard" id="content"></section>

</div>

<footer>
© <span id="year"></span> Md. Nahid Hasan
</footer>

</div>

<script>
const content = document.getElementById('content');
const links = document.querySelectorAll('nav.main a');
document.getElementById('year').textContent = new Date().getFullYear();

const pages = {
  home: `<h2>Overview</h2><p class="muted">Welcome to my academic page.</p>`,
  research: `<h2>Research</h2><p class="muted">My research focuses on ML and modeling.</p>`,
  publications: `<h2>Publications</h2><p class="muted">List of publications.</p>`,
  teaching: `<h2>Teaching</h2><p class="muted">Courses taught.</p>`,
  cv: `<iframe src="assets/CV_Nahid.pdf" style="width:100%;height:600px"></iframe>`
};

function setActive(route){
  links.forEach(l=>{
    l.classList.toggle('active', l.dataset.route===route);
  });
}

function render(route){
  content.innerHTML = pages[route] || pages.home;
  setActive(route);
}

links.forEach(a=>a.addEventListener('click', e=>{
  e.preventDefault();
  const r=a.dataset.route;
  history.pushState({r},'',`#${r}`);
  render(r);
}));

window.addEventListener('popstate', ()=>{
  const r=(location.hash||'#home').replace('#','');
  render(r);
});

render((location.hash||'#home').replace('#',''));

document.getElementById('darkToggle').onclick=()=>{
  document.documentElement.classList.toggle('dark-mode');
};
</script>

</body>
</html>
