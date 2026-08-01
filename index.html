/* ============================================================
   CONFIG — Configuración principal
   ============================================================ */
const CONFIG = {
  clave: "TECHNO2026",               // Clave de acceso para la fiesta
  // aquí URL que dio Google Apps Script al implementar como Web App:
  driveScriptURL: "https://script.google.com/macros/s/AKfycbxLkzMMTHjC2G0P8mEOoDB-eARnhVGqAVkZvrs3EwV-1VG0i31ftwU-d7ZJG1GvJUPX/exec", 
  siteURL: window.location.href,     // Toma automáticamente la URL del hosting actual

  fotos: [
    {cap:"Fiesta", img:"Assets/Fotos/fiesta1.jpg"},
    {cap:"Roadtrip", img:"Assets/Fotos/Rodada1.png"},
    {cap:"Cumple pasado", img:"Assets/Fotos/cumple1.jpg"},
    {cap:"Con amigos", img:"Assets/Fotos/amigos.png"},
    {cap:"EDC 2026", img:"Assets/Fotos/edc.jpg"},
    {cap:"Trabajo", img:"Assets/Fotos/trabalo.jpeg"},
    {cap:"🐣💚🐺", img:"Assets/Fotos/anillo.jpg"},
    {cap:"Perrhijo", img:"Assets/Fotos/scooby2.jpg"}
  ],

  tracks: [
    {title:"Man on the Run", sub:"Dash Berlin", youtube:"https://youtu.be/C7Qsj6MGVHE?si=HE7ywI0s7FcAe4TI"},
    {title:"Records", sub:"DJ Issac", youtube:"https://youtu.be/h1rg6NSwd28?si=h0ayniU-SuOi9QtK"},
    {title:"Me Estás Matando", sub:"Daniel", youtube:"https://youtu.be/MkZ8MlUO_Dw?si=YTCe9yNm6C2Mo4hp"},
    {title:"Parecemos Tontos", sub:"Enrique Bunbury", youtube:"https://youtu.be/k34IA_MtTYs?si=xMg-KL2aGbHX5kK9"}
  ]
};

/* ---------- GATE / ACCESO ---------- */
/* ---------- ACCESO PERMANENTE (localStorage) ---------- */
function verificarClave(){
  const val = document.getElementById('claveInput').value.trim().toUpperCase();
  if(val === CONFIG.clave.toUpperCase()){
    localStorage.setItem('cumple_ok','1');
    document.getElementById('gate').classList.add('hidden');
    document.getElementById('site').style.display = 'block';
  } else {
    document.getElementById('claveErr').textContent = "Clave incorrecta, intenta de nuevo";
  }
}

(function initGate(){
  const params = new URLSearchParams(window.location.search);
  const claveParam = params.get('clave');
  if(sessionStorage.getItem('cumple_ok') === '1' || (claveParam && claveParam.toUpperCase() === CONFIG.clave.toUpperCase())){
    sessionStorage.setItem('cumple_ok','1');
    document.getElementById('gate').classList.add('hidden');
    document.getElementById('site').style.display = 'block';
  }
})();

/* ---------- CARRUSEL ---------- */
let carouselIndex = 0;
function renderDesk(){
  const desk = document.getElementById('desk');
  if(!desk) return;
  desk.innerHTML = '';

  // Detectar si estamos en celular para ajustar el número de fotos visibles y la separación
  const esMovil = window.innerWidth < 600;
  const visible = esMovil ? 3 : 5; 
  const spacing = esMovil ? 60 : 100; // Menos distancia entre tarjetas en cel

  for(let i = 0; i < visible; i++){
    const idx = (carouselIndex + i) % CONFIG.fotos.length;
    const foto = CONFIG.fotos[idx];
    const div = document.createElement('div');
    div.className = 'polaroid';
    
    const rot = (i % 2 === 0 ? -1 : 1) * (4 + i * 2);
    // Centramos el abanico de fotos dinámicamente
    const centerOffset = ((visible - 1) * spacing) / 2;
    const leftPos = `calc(50% - 55px + ${i * spacing - centerOffset}px)`;
    const topPos = 20 + (i % 2) * 15;

    div.style.left = leftPos;
    div.style.top = topPos + 'px';
    div.style.transform = `rotate(${rot}deg)`;
    div.style.zIndex = visible - i;

    // Aseguramos la ruta de la imagen
    const estiloFondo = foto.img 
      ? `background-image: url('${foto.img}');` 
      : `background: ${foto.color || '#333'};`;

    div.innerHTML = `<div class="swatch" style="${estiloFondo}"></div><div class="cap">${foto.cap}</div>`;
    desk.appendChild(div);
  }

  const dots = document.getElementById('dots');
  if(dots){
    dots.innerHTML = '';
    CONFIG.fotos.forEach((_, i) => {
      const d = document.createElement('span');
      if(i === carouselIndex % CONFIG.fotos.length) d.className = 'active';
      dots.appendChild(d);
    });
  }
}

function moveCarousel(dir){
  carouselIndex = (carouselIndex + dir + CONFIG.fotos.length) % CONFIG.fotos.length;
  renderDesk();
}

/* ---------- QR DE SUBIDA ---------- */
/* ---------- AUTO-ACCESO ---------- */
document.addEventListener("DOMContentLoaded", () => {
  renderDesk();
  const qrElem = document.getElementById("qrbox");
  if(qrElem && typeof QRCode !== 'undefined'){
    // Construimos la URL agregando la clave automáticamente
    const baseUrl = window.location.href.split('?')[0];
    const urlConClave = `${baseUrl}?clave=${encodeURIComponent(CONFIG.clave)}`;

    new QRCode(qrElem, {
      text: urlConClave, // El celular al escanear entrará directo sin pedir clave
      width: 128,
      height: 128,
      colorDark: "#150a28",
      colorLight: "#ffffff"
    });
  }
});

/* ---------- SUBIDA A DRIVE (vía Google Apps Script) ---------- */
const fileInput = document.getElementById('fileInput');
if(fileInput){
  fileInput.addEventListener('change', async (e)=>{
    const files = Array.from(e.target.files);
    if(!files.length) return;
    const btn = document.getElementById('btnUpload');
    const status = document.getElementById('uploadStatus');
    const thumbs = document.getElementById('thumbs');

    btn.disabled = true;
    for(const file of files){
      status.textContent = `Subiendo ${file.name}...`;
      try{
        const base64 = await fileToBase64(file);
        
        // Se realiza petición POST enviando payload en JSON
        const resp = await fetch(CONFIG.driveScriptURL, {
          method: 'POST',
          headers: { 'Content-Type': 'text/plain;charset=utf-8' }, // Usamos text/plain para evitar preflight de CORS
          body: JSON.stringify({
            filename: file.name,
            mimeType: file.type,
            data: base64
          })
        });
        
        const result = await resp.json();
        if(result.status === 'ok'){
          status.textContent = `✅ ${file.name} subido correctamente`;
          const th = document.createElement('div');
          th.className = 'th';
          if(file.type.startsWith('image/')){
            th.innerHTML = `<img src="${URL.createObjectURL(file)}" alt="subida">`;
          } else if(file.type.startsWith('video/')){
            th.innerHTML = `<video src="${URL.createObjectURL(file)}" muted></video>`;
          } else {
            th.textContent = '📁';
          }
          thumbs.appendChild(th);
        } else {
          status.textContent = `❌ Error al subir ${file.name}: ${result.message || ''}`;
        }
      } catch(err){
        console.error(err);
        status.textContent = `❌ No se pudo subir ${file.name}`;
      }
    }
    btn.disabled = false;
    e.target.value = '';
  });
}

function fileToBase64(file){
  return new Promise((resolve,reject)=>{
    const reader = new FileReader();
    reader.onload = () => resolve(reader.result.split(',')[1]);
    reader.onerror = reject;
    reader.readAsDataURL(file);
  });
}

/* ---------- REPRODUCTOR (YouTube API) ---------- */
let trackIndex = 0;
let isPlaying = false;
let ytPlayer = null;
let ytReady = false;

function getYouTubeId(url){
  const match = url.match(/(?:youtu\.be\/|youtube\.com\/(?:watch\?v=|embed\/|shorts\/))([a-zA-Z0-9_-]{11})/);
  return match ? match[1] : null;
}

function renderPlaylist(){
  const ul = document.getElementById('playlist');
  if(!ul) return;
  ul.innerHTML = '';
  CONFIG.tracks.forEach((t,i)=>{
    const li = document.createElement('li');
    if(i === trackIndex) li.className = 'active';
    li.innerHTML = `<span>${i+1}. ${t.title}</span><span>♫</span>`;
    li.onclick = ()=>{ trackIndex = i; loadTrack(); playAudio(); };
    ul.appendChild(li);
  });
}

function loadTrack(){
  const t = CONFIG.tracks[trackIndex];
  if(!t) return;
  document.getElementById('nowTitle').textContent = t.title;
  document.getElementById('nowSub').textContent = t.sub;
  renderPlaylist();
  const videoId = getYouTubeId(t.youtube || '');
  if(!videoId){
    document.getElementById('nowSub').textContent = '⚠️ Link de YouTube inválido';
    return;
  }
  if(ytReady && ytPlayer && ytPlayer.loadVideoById){
    ytPlayer.loadVideoById(videoId);
  }
}

function playAudio(){
  if(ytReady && ytPlayer && ytPlayer.playVideo) ytPlayer.playVideo();
  isPlaying = true;
  document.getElementById('playBtn').textContent = '⏸';
}

function pauseAudio(){
  if(ytReady && ytPlayer && ytPlayer.pauseVideo) ytPlayer.pauseVideo();
  isPlaying = false;
  document.getElementById('playBtn').textContent = '▶';
}

function togglePlay(){ isPlaying ? pauseAudio() : playAudio(); }
function nextTrack(){ trackIndex = (trackIndex+1) % CONFIG.tracks.length; loadTrack(); if(isPlaying) setTimeout(playAudio, 300); }
function prevTrack(){ trackIndex = (trackIndex-1+CONFIG.tracks.length) % CONFIG.tracks.length; loadTrack(); if(isPlaying) setTimeout(playAudio, 300); }

const progressBar = document.getElementById('progressBar');
if(progressBar){
  progressBar.addEventListener('click', (e)=>{
    if(!ytReady || !ytPlayer || !ytPlayer.getDuration) return;
    const rect = e.currentTarget.getBoundingClientRect();
    const pct = (e.clientX - rect.left)/rect.width;
    const duration = ytPlayer.getDuration();
    if(duration) ytPlayer.seekTo(duration * pct, true);
  });
}

function updateProgress(){
  if(ytReady && ytPlayer && ytPlayer.getDuration && isPlaying){
    const duration = ytPlayer.getDuration();
    const current = ytPlayer.getCurrentTime();
    if(duration){
      document.getElementById('progressFill').style.width = (current/duration*100)+'%';
    }
  }
}
setInterval(updateProgress, 500);

function onYouTubeIframeAPIReady(){
  const first = CONFIG.tracks[0];
  const firstId = getYouTubeId(first?.youtube || '') || '';
  ytPlayer = new YT.Player('ytPlayer', {
    height: '1', width: '1',
    videoId: firstId,
    host: 'https://www.youtube-nocookie.com',
    playerVars: { autoplay: 0, controls: 0 },
    events: {
      onReady: ()=>{ ytReady = true; },
      onStateChange: (e)=>{
        if(e.data === YT.PlayerState.ENDED) nextTrack();
        if(e.data === YT.PlayerState.PLAYING){ isPlaying = true; document.getElementById('playBtn').textContent = '⏸'; }
        if(e.data === YT.PlayerState.PAUSED){ isPlaying = false; document.getElementById('playBtn').textContent = '▶'; }
      }
    }
  });

  
}
/* ---------- MURO DE MENSAJES ---------- */
function guardarMensaje(e){
  if(e) e.preventDefault(); // Evita que la pag se refresque en movil.
  const nameInput = document.getElementById('guestName');
  const msgInput = document.getElementById('guestMsg');

  const nombre = document.getElementById('guestName').value.trim() || 'Invitado/a Anónimo/a';
  const mensaje = document.getElementById('guestMsg').value.trim();
  
  if(!mensaje) return;

  const msgs = JSON.parse(localStorage.getItem('mensajes_cumple') || '[]');
  msgs.unshift({
     nombre:nombre,
     mensaje:mensaje,
     fecha: new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'}) 
    });
  localStorage.setItem('mensajes_cumple', JSON.stringify(msgs));
    if(msgInput) msgInput.value = '';
  if(nameInput) nameInput.value = '';

  // Quitar el foco del teclado en celulares al enviar
  if(document.activeElement) document.activeElement.blur();
  renderMensajes();
}

function renderMensajes(){
  const contenedor = document.getElementById('mensajesLista');
  if(!contenedor) return;
  const msgs = JSON.parse(localStorage.getItem('mensajes_cumple') || '[]');
  
  contenedor.innerHTML = msgs.map(m => `
    <div style="background:var(--bg-panel-soft); border:1px solid #3a2568; border-radius:8px; padding:8px 10px; text-align:left;">
      <div style="font-size:11px; color:var(--accent-lime); font-weight:bold;">${m.nombre} <span style="color:var(--text-dim); font-weight:normal; font-size:9px;">· ${m.fecha}</span></div>
      <div style="font-size:12px; color:var(--text-light); margin-top:2px;">"${m.mensaje}"</div>
    </div>
  `).join('');
}

// Cargar mensajes existentes al iniciar
document.addEventListener("DOMContentLoaded", renderMensajes);

loadTrack();
