<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>JamChat</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:system-ui,Segoe UI,Arial,sans-serif;background:#1e1f22;color:#e3e5e8;height:100vh;display:flex;flex-direction:column}
#top{display:flex;align-items:center;gap:8px;padding:10px;background:#2b2d31;border-bottom:1px solid #1a1b1e}
#top b{color:#fff;font-size:15px}
#pseudo{background:#404249;color:#fff;border:none;border-radius:6px;padding:6px 10px;font-size:14px;width:140px}
button{cursor:pointer;border:none;border-radius:6px;padding:6px 10px;font-size:14px;background:#404249;color:#fff}
button:hover{background:#4e5058}
#msgs{flex:1;overflow-y:auto;padding:16px}
.msg{display:flex;gap:12px;margin-bottom:14px;max-width:800px}
.avatar{width:38px;height:38px;border-radius:50%;background:#5865f2;color:#fff;display:flex;align-items:center;justify-content:center;font-weight:bold;flex-shrink:0}
.msg .body{min-width:0}
.who{font-weight:600;color:#fff;font-size:14px}
.date{font-size:11px;color:#949ba4;margin-left:8px;font-weight:normal}
.text{font-size:14px;line-height:1.4;white-space:pre-wrap;word-wrap:break-word}
.att{margin-top:6px;display:flex;flex-direction:column;gap:6px}
.att a{color:#00a8fc;text-decoration:none;font-size:13px;word-break:break-all}
.att img{max-width:320px;max-height:240px;border-radius:8px;display:block}
#bottom{padding:10px;background:#2b2d31;border-top:1px solid #1a1b1e;display:flex;gap:8px;align-items:flex-end}
#inp{flex:1;background:#383a40;border:none;border-radius:8px;color:#fff;padding:10px;resize:none;font-family:inherit;font-size:14px;max-height:120px}
#filecount{font-size:11px;color:#949ba4;margin-top:4px}
</style>
</head>
<body>
<div id="top"><b>💬 JamChat</b><input id="pseudo" placeholder="Ton pseudo"></div>
<div id="msgs"></div>
<div id="bottom">
<button id="btnatt" title="Joindre un fichier">📎</button>
<textarea id="inp" rows="1" placeholder="Message... (Entrée = envoyer, Maj+Entrée = saut de ligne)"></textarea>
<button id="btnload" title="Charger l'historique (chat.json)">📥</button>
<button id="btnsave" title="Exporter l'historique (chat.json)">💾</button>
<input type="file" id="file" hidden multiple>
</div>
<div id="filecount"></div>
<script>
var pending=[];
var msgs=JSON.parse(localStorage.getItem('jamchat')||'[]');
document.getElementById('pseudo').value=localStorage.getItem('jampseudo')||'Anonyme';
document.getElementById('pseudo').oninput=function(){localStorage.setItem('jampseudo',this.value)};
function save(){localStorage.setItem('jamchat',JSON.stringify(msgs))}
function fmt(n){return n.toLocaleString('fr-FR')+' octets'}
function esc(s){return s.replace(/&/g,'&amp;').replace(/</g,'&lt;')}
function render(){
var d=document.getElementById('msgs');d.innerHTML='';
msgs.forEach(function(m){
var a=document.createElement('div');a.className='msg';
var av=document.createElement('div');av.className='avatar';av.textContent=(m.who||'?').charAt(0).toUpperCase();
var b=document.createElement('div');b.className='body';
b.innerHTML='<span class="who">'+esc(m.who||'Anonyme')+'</span><span class="date">'+esc(m.date||'')+'</span><div class="text">'+esc(m.text||'')+'</div>';
(m.att||[]).forEach(function(f){
var w=document.createElement('div');w.className='att';
if((f.data||'').indexOf('data:image')===0){var im=document.createElement('img');im.src=f.data;w.appendChild(im)}
var l=document.createElement('a');l.href=f.data;l.download=f.name;l.textContent='📄 '+f.name+' ('+fmt(f.size||0)+')';
w.appendChild(l);b.appendChild(w)});
a.appendChild(av);a.appendChild(b);d.appendChild(a)});
d.scrollTop=d.scrollHeight}
function send(){
var t=document.getElementById('inp').value.trim();
if(!t&&!pending.length)return;
msgs.push({who:document.getElementById('pseudo').value||'Anonyme',date:new Date().toLocaleString('fr-FR'),text:t,att:pending.slice()});
pending=[];document.getElementById('inp').value='';updFiles();save();render()}
function updFiles(){
document.getElementById('filecount').textContent=pending.length?'📎 '+pending.length+' fichier(s) joint(s) — ils partiront avec le prochain message':'';
document.getElementById('btnatt').textContent=pending.length?'📎('+pending.length+')':'📎'}
document.getElementById('btnatt').onclick=function(){document.getElementById('file').click()};
document.getElementById('file').onchange=function(){
for(var i=0;i<this.files.length;i++){(function(f){
if(f.size>1048576){alert(f.name+' dépasse 1 Mo (max par pièce jointe)');return}
var r=new FileReader();r.onload=function(){pending.push({name:f.name,size:f.size,data:r.result});updFiles()};
r.readAsDataURL(f)})(this.files[i])}
this.value=''};
document.getElementById('inp').addEventListener('keydown',function(e){
if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();send()}});
document.getElementById('btnsave').onclick=function(){
var b=new Blob([JSON.stringify(msgs)],{type:'application/json'});
var a=document.createElement('a');a.href=URL.createObjectURL(b);a.download='chat.json';a.click();
alert('chat.json téléchargé — glisse-le dans le repo GitHub (remplace l\u2019ancien)')};
document.getElementById('btnload').onclick=function(){
if(location.protocol.indexOf('http')===0){
fetch('chat.json',{cache:'no-store'}).then(function(r){if(!r.ok)throw 0;return r.json()})
.then(function(j){msgs=j;save();render();alert('Historique chargé depuis le repo ✓')})
.catch(function(){fallbackFile()});
}else{fallbackFile()}};
function fallbackFile(){
var i=document.createElement('input');i.type='file';i.accept='.json';
i.onchange=function(){var r=new FileReader();r.onload=function(){
try{msgs=JSON.parse(r.result);save();render();alert('Historique chargé ✓')}catch(e){alert('Fichier JSON invalide')}};
r.readAsText(i.files[0])};i.click()}
render();
</script>
</body>
</html>
