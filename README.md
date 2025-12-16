<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Backburner Server</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box;font-family:'Inter',sans-serif}
body{
margin:0;
height:100vh;
background:linear-gradient(135deg,#6366f1,#8b5cf6);
display:flex;
overflow:hidden;
transition:.4s;
}
.dark{
background:#0f172a;
}

/* LOGIN */
#login{
position:fixed;inset:0;
display:flex;
align-items:center;
justify-content:center;
backdrop-filter:blur(20px);
}
.login-box{
background:rgba(255,255,255,.15);
padding:30px;
border-radius:20px;
width:320px;
color:#fff;
box-shadow:0 20px 50px rgba(0,0,0,.3);
}
.login-box h2{text-align:center}
select,input,button{
width:100%;
padding:12px;
margin:10px 0;
border-radius:12px;
border:none;
outline:none;
}
button{
background:#fff;
color:#4f46e5;
font-weight:600;
cursor:pointer;
}

/* APP */
#app{
display:none;
width:100%;
}

/* SIDEBAR */
.sidebar{
width:260px;
background:rgba(255,255,255,.12);
backdrop-filter:blur(18px);
padding:20px;
color:#fff;
transition:.4s;
}
.sidebar.collapsed{width:90px}
.avatar{
width:64px;height:64px;
border-radius:50%;
background:#fff;
color:#4f46e5;
display:flex;
align-items:center;
justify-content:center;
font-size:26px;
font-weight:700;
margin:auto;
}
.username{text-align:center;margin-top:10px;font-weight:600}

.menu button{
background:rgba(255,255,255,.15);
color:#fff;
border:none;
margin:8px 0;
padding:14px;
border-radius:14px;
cursor:pointer;
transition:.3s;
}
.menu button:hover{
background:rgba(255,255,255,.3);
}

/* MAIN */
.main{
flex:1;
padding:25px;
background:#f8fafc;
overflow:auto;
border-top-left-radius:30px;
}
.dark .main{background:#020617;color:#fff}

.cards{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(160px,1fr));
gap:20px;
}
.card{
background:#fff;
padding:20px;
border-radius:20px;
box-shadow:0 10px 30px rgba(0,0,0,.1);
}
.dark .card{background:#020617;border:1px solid #1e293b}

.hidden{display:none}

textarea{
width:100%;
height:200px;
border-radius:14px;
padding:15px;
border:1px solid #ccc;
}
</style>
</head>

<body>

<div id="login">
<div class="login-box">
<h2>Backburner Login</h2>
<select id="user">
<option>Nicolas Tok</option>
<option>clairine</option>
<option>wixander</option>
<option>angel</option>
</select>
<input type="password" id="pass" placeholder="Password">
<button onclick="login()">Masuk</button>
</div>
</div>

<div id="app">
<div class="sidebar" id="sidebar">
<div class="avatar" id="ava">N</div>
<div class="username" id="uname"></div>

<div class="menu">
<button onclick="show('dash')">Dashboard</button>
<button onclick="show('editor')">Code Editor</button>
<button onclick="show('upload')">Upload File</button>
<button onclick="show('profile')">Profile</button>
<button onclick="toggle()">Collapse</button>
<button onclick="theme()">Dark / Light</button>
</div>
</div>

<div class="main">
<div id="dash">
<h1>Dashboard</h1>
<div class="cards">
<div class="card">📁 Project: 12</div>
<div class="card">🔥 Active Session</div>
<div class="card">💾 Storage Ready</div>
</div>
</div>

<div id="editor" class="hidden">
<h1>Code Editor</h1>
<textarea placeholder="// tulis kode di sini"></textarea>
</div>

<div id="upload" class="hidden">
<h1>Upload Coding File</h1>
<input type="file">
</div>

<div id="profile" class="hidden">
<h1>Edit Profile</h1>
<input placeholder="Nama">
<input placeholder="Password Baru">
<button>Simpan</button>
</div>
</div>
</div>

<script>
const users={
"Nicolas Tok":"ber217an",
"clairine":"backburner",
"wixander":"backburner",
"angel":"backburner"
}

function login(){
if(users[user.value]===pass.value){
login.style.display="none";
app.style.display="flex";
uname.innerText=user.value;
ava.innerText=user.value[0];
}else alert("Password salah")
}

function show(id){
["dash","editor","upload","profile"].forEach(x=>{
document.getElementById(x).classList.add("hidden")
})
document.getElementById(id).classList.remove("hidden")
}

function toggle(){sidebar.classList.toggle("collapsed")}
function theme(){document.body.classList.toggle("dark")}
</script>

</body>
</html>
