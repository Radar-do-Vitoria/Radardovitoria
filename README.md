## Hi there 👋

<!--
**radardovitoria/Radardovitoria** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

<!DOCTYPE html><html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Radar do Vitória</title>
  <meta name="description" content="Radar do Vitória – notícias, live e interação da torcida rubro-negra." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --vitoria-red:#E10600;
      --vitoria-black:#111111;
      --vitoria-dark:#0b0b0b;
      --vitoria-gray:#1c1c1c;
      --accent:#ffcc00;
      --card:#151515;
      --muted:#9aa0a6;
      --ring: #ffffff22;
    }
    *{box-sizing:border-box}
    body{
      margin:0; font-family:Montserrat,system-ui,-apple-system,Segoe UI,Roboto,Ubuntu,Arial,sans-serif;
      color:#fff; background:linear-gradient(180deg,var(--vitoria-black),#000);
    }
    header{
      position:sticky; top:0; z-index:30;
      backdrop-filter:saturate(1.4) blur(8px);
      background:#000000cc; border-bottom:1px solid var(--ring);
    }
    .container{max-width:1100px; margin:0 auto; padding:16px;}
    .brand{display:flex; align-items:center; gap:12px}
    .logo{width:42px; height:42px; border-radius:12px; background:conic-gradient(from 0deg at 50% 50%, var(--vitoria-red), var(--vitoria-red) 50%, #000 50%, #000); box-shadow:0 0 0 3px #000, 0 8px 24px #000 inset; display:grid; place-items:center}
    .logo::after{content:"V"; font-weight:800; color:#fff; text-shadow:0 2px 10px #0007}
    h1{font-size:clamp(20px,3.2vw,32px); margin:0; font-weight:800; letter-spacing:0.5px}
    .meta{display:flex; flex-wrap:wrap; gap:12px; color:#ddd; font-size:14px;}
    .pill{display:inline-flex; align-items:center; gap:8px; padding:6px 10px; border:1px solid var(--ring); border-radius:999px; background: #0a0a0acc}
    .grid{display:grid; gap:16px; grid-template-columns:1.3fr 0.7fr;}
    @media (max-width:900px){.grid{grid-template-columns:1fr}}/* Cards */
.card{background:linear-gradient(180deg, #151515, #0e0e0e); border:1px solid var(--ring); border-radius:20px; padding:16px; box-shadow:0 10px 30px #0008}
.card h2{margin:0 0 10px; font-size:20px}

/* LIVE */
.live-wrap{position:relative; border-radius:16px; overflow:hidden;}
video, .live-placeholder{width:100%; aspect-ratio:16/9; display:block; background:#000}
.live-badge{position:absolute; top:12px; left:12px; background:var(--vitoria-red); color:#fff; padding:6px 10px; border-radius:999px; font-weight:700; letter-spacing:.5px; box-shadow:0 6px 18px #0007}
.controls{display:flex; gap:8px; flex-wrap:wrap; margin-top:12px}
button, input, textarea, select{font:inherit}
button{background:var(--vitoria-red); color:#fff; border:none; padding:10px 14px; border-radius:12px; font-weight:700; cursor:pointer; box-shadow:0 6px 20px #0008}
button.secondary{background:#222}
button:disabled{opacity:.55; cursor:not-allowed}
input[type="password"], input[type="text"], input[type="url"], input[type="search"], textarea{
  background:#0b0b0b; color:#fff; border:1px solid var(--ring); border-radius:12px; padding:10px 12px; width:100%
}
.row{display:flex; gap:8px;}
.row > *{flex:1}

/* Rating */
.stars{display:inline-flex; gap:6px; align-items:center}
.star{cursor:pointer; font-size:24px; filter:drop-shadow(0 4px 10px #0006)}
.star[data-active="true"]{color:var(--accent)}
.rating-summary{font-size:14px; color:#ddd}

/* Comments & Chat */
.comments-list{display:grid; gap:12px; margin-top:10px; max-height:320px; overflow:auto; padding-right:4px}
.comment{background:var(--card); border:1px solid var(--ring); border-radius:14px; padding:10px}
.comment .who{font-weight:700}
.comment .when{color:#bbb; font-size:12px}

/* Footer */
footer{opacity:.8; border-top:1px solid var(--ring); margin-top:24px}
.tiny{font-size:12px; color:#bdbdbd}
.sep{height:1px; background:linear-gradient(90deg,#fff0,#ffffff22,#fff0); margin:12px 0}

/* Toast */
#toast{position:fixed; bottom:18px; left:50%; transform:translateX(-50%); background:#0e0e0e; color:#fff; border:1px solid var(--ring); padding:10px 14px; border-radius:12px; box-shadow:0 10px 30px #000a; display:none}

  </style>
</head>
<body>
  <header>
    <div class="container" style="display:flex; justify-content:space-between; align-items:center; gap:14px;">
      <div class="brand">
        <div class="logo" aria-hidden="true"></div>
        <h1>Radar do Vitória</h1>
      </div>
      <div class="meta">
        <div class="pill" title="Data e hora"><span>📅</span><span id="now"></span></div>
        <div class="pill" title="Pessoas online (estimativa)"><span>👥</span><span><strong id="onlineCount">1</strong> online</span></div>
        <div class="pill" title="Nota média do site"><span>⭐</span> <span id="ratingSummary" class="rating-summary">–</span></div>
      </div>
    </div>
  </header>  <main class="container" style="padding-top:18px;">
    <div class="grid">
      <!-- COLUNA ESQUERDA: LIVE + CHAT -->
      <section class="card">
        <h2>🔴 Live do Radar</h2>
        <div class="live-wrap">
          <video id="liveVideo" autoplay playsinline controls></video>
          <div id="liveBadge" class="live-badge" style="display:none">AO VIVO</div>
        </div><div class="controls" id="viewerControls">
      <input id="externalStream" type="url" placeholder="Cole aqui a URL do stream (HLS .m3u8) para os visitantes" />
      <button id="useExternal" class="secondary">Usar stream externo</button>
    </div>

    <div class="sep"></div>

    <!-- BLOCO DO ADMIN (PROTEGIDO) -->
    <details id="adminBox" class="card" style="background:#101010; border-radius:16px">
      <summary style="cursor:pointer; list-style:none; font-weight:800">🎛️ Área do Apresentador (com senha)</summary>
      <div style="margin-top:10px; display:grid; gap:8px">
        <div class="row">
          <input id="adminPassword" type="password" placeholder="Digite a senha" />
          <button id="unlock">Desbloquear</button>
        </div>
        <div id="adminControls" style="display:none;">
          <div class="controls">
            <button id="startLive">Iniciar Live (câmera/microfone)</button>
            <button id="stopLive" class="secondary" disabled>Encerrar Live</button>
            <button id="muteBtn" class="secondary" disabled>Mutar</button>
            <button id="flipCam" class="secondary" disabled>Trocar câmera</button>
          </div>
          <small class="tiny">Dica: Para transmissão real para todos os visitantes, você precisará de um servidor/serviço de streaming (HLS ou WebRTC). Aqui você pode colar a URL no campo acima "stream externo". O modo "Iniciar Live" transmite apenas localmente neste navegador.</small>
        </div>
      </div>
    </details>

    <div class="sep"></div>

    <!-- CHAT AO VIVO / COMENTÁRIOS DA LIVE -->
    <h3 style="margin:0 0 8px">💬 Chat da Live</h3>
    <form id="chatForm" class="row" autocomplete="off">
      <input id="chatName" type="text" placeholder="Seu nome" required>
      <input id="chatMsg" type="text" placeholder="Escreva sua mensagem" required>
      <button>Enviar</button>
    </form>
    <div class="comments-list" id="chatList"></div>
  </section>

  <!-- COLUNA DIREITA: RATING + COMENTÁRIOS GERAIS -->
  <aside class="card">
    <h2>⭐ Vote no site</h2>
    <div class="stars" aria-label="Avaliação do site">
      <span class="star" data-value="1">★</span>
      <span class="star" data-value="2">★</span>
      <span class="star" data-value="3">★</span>
      <span class="star" data-value="4">★</span>
      <span class="star" data-value="5">★</span>
    </div>
    <div class="rating-summary" id="ratingText" style="margin-top:6px">Dê sua nota!</div>

    <div class="sep"></div>

    <h2>🗨️ Comentários gerais</h2>
    <form id="cmtForm" autocomplete="off">
      <div class="row">
        <input id="cmtName" type="text" placeholder="Seu nome" required>
        <input id="cmtText" type="text" placeholder="Seu comentário" required>
      </div>
      <button style="margin-top:8px">Publicar</button>
    </form>
    <div class="comments-list" id="cmtList"></div>
  </aside>
</div>

<footer class="container" style="padding-bottom:28px">
  <p class="tiny">⚠️ Observação: contagem de "online" global, comentários e live para todos os visitantes exigem um backend/serviço. Esta versão salva dados no seu navegador (localStorage) e faz uma estimativa local de presença.</p>
  <p class="tiny">Feito com ❤️ pela Nação Rubro-Negra.</p>
</footer>

  </main>  <div id="toast"></div>  <script>
    // ===== Utilidades =====
    const $ = sel => document.querySelector(sel);
    const $$ = sel => Array.from(document.querySelectorAll(sel));
    const toast = (msg) => { const t = $('#toast'); t.textContent = msg; t.style.display='block'; clearTimeout(t._h); t._h=setTimeout(()=>t.style.display='none', 2500) };

    // ===== Data/Hora =====
    const fmtDate = (d=new Date()) => d.toLocaleString('pt-BR', { dateStyle:'full', timeStyle:'short' });
    const tickNow = () => { $('#now').textContent = fmtDate(); };
    tickNow(); setInterval(tickNow, 1000);

    // ===== Presença (estimativa local por navegador) =====
    // Conta abas ativas neste mesmo dispositivo. Para contagem global, use um backend.
    (function presence(){
      const KEY = 'radar_vitoria_presence';
      const id = Math.random().toString(36).slice(2);
      const bc = ('BroadcastChannel' in window) ? new BroadcastChannel('radar_presence') : null;
      const updateUI = () => {
        const raw = localStorage.getItem(KEY);
        let list = [];
        try { list = raw ? JSON.parse(raw) : []; } catch(e){}
        const now = Date.now();
        // expira itens com > 20s sem ping
        list = list.filter(x => now - x.lastSeen < 20000);
        $('#onlineCount').textContent = Math.max(1, list.length);
        localStorage.setItem(KEY, JSON.stringify(list));
      }
      const heartbeat = () => {
        const raw = localStorage.getItem(KEY);
        let list = [];
        try { list = raw ? JSON.parse(raw) : []; } catch(e){}
        const now = Date.now();
        const mine = list.find(x => x.id === id);
        if(mine){ mine.lastSeen = now; }
        else { list.push({id, lastSeen: now}); bc && bc.postMessage({type:'join'}); }
        localStorage.setItem(KEY, JSON.stringify(list));
        updateUI();
      }
      window.addEventListener('beforeunload', ()=>{
        try{
          const raw = localStorage.getItem(KEY);
          let list = raw ? JSON.parse(raw) : [];
          list = list.filter(x => x.id !== id);
          localStorage.setItem(KEY, JSON.stringify(list));
          bc && bc.postMessage({type:'leave'});
        }catch(e){}
      });
      setInterval(heartbeat, 5000);
      heartbeat();
      bc && bc.addEventListener('message', updateUI);
    })();

    // ===== Rating =====
    const rating = {
      KEY: 'radar_vitoria_rating',
      get(){ const r = localStorage.getItem(this.KEY); return r ? JSON.parse(r) : {sum:0, count:0}; },
      set(v){ localStorage.setItem(this.KEY, JSON.stringify(v)); render(); }
    };
    const renderStars = (value) => {
      $$('.star').forEach(s=>{ s.dataset.active = (+s.dataset.value <= value).toString(); });
    };
    const render = () => {
      const {sum, count} = rating.get();
      const avg = count ? (sum / count) : 0;
      $('#ratingSummary').textContent = count ? `${avg.toFixed(1)} / 5 (${count})` : 'Sem notas';
      $('#ratingText').textContent = count ? `Média ${avg.toFixed(2)} com ${count} voto(s)` : 'Dê sua nota!';
      renderStars(Math.round(avg));
    };
    $$('.star').forEach(star => {
      star.addEventListener('click', ()=>{
        const v = +star.dataset.value;
        const data = rating.get();
        data.sum += v; data.count += 1; rating.set(data);
        toast(`Obrigado! Você deu ${v} estrela(s).`);
      });
    });
    render();

    // ===== Comentários Gerais =====
    const cmtKEY = 'radar_vitoria_comments';
    const loadCmts = () => { try{ return JSON.parse(localStorage.getItem(cmtKEY)) || [] }catch(e){ return [] } };
    const saveCmts = (arr) => localStorage.setItem(cmtKEY, JSON.stringify(arr));
    const drawCmts = () => {
      const list = loadCmts();
      const box = $('#cmtList'); box.innerHTML='';
      list.slice().reverse().forEach(c => {
        const el = document.createElement('div'); el.className='comment';
        el.innerHTML = `<div class="who">${c.name}</div><div class="when">${new Date(c.at).toLocaleString('pt-BR')}</div><div>${c.text}</div>`;
        box.appendChild(el);
      });
    };
    $('#cmtForm').addEventListener('submit', e=>{
      e.preventDefault();
      const name = $('#cmtName').value.trim();
      const text = $('#cmtText').value.trim();
      if(!name || !text) return;
      const arr = loadCmts(); arr.push({name, text, at: Date.now()}); saveCmts(arr);
      e.target.reset(); drawCmts(); toast('Comentário publicado!');
    });
    drawCmts();

    // ===== Chat da Live =====
    const chatKEY = 'radar_vitoria_livechat';
    const loadChat = () => { try{ return JSON.parse(localStorage.getItem(chatKEY)) || [] }catch(e){ return [] } };
    const saveChat = (arr) => localStorage.setItem(chatKEY, JSON.stringify(arr));
    const drawChat = () => {
      const list = loadChat();
      const box = $('#chatList'); box.innerHTML='';
      list.slice(-200).forEach(c => {
        const el = document.createElement('div'); el.className='comment';
        el.innerHTML = `<div class="who">${c.name} <span class="when">• ${new Date(c.at).toLocaleTimeString('pt-BR')}</span></div><div>${c.text}</div>`;
        box.appendChild(el);
      }); box.scrollTop = box.scrollHeight;
    }
    $('#chatForm').addEventListener('submit', e=>{
      e.preventDefault();
      const name = $('#chatName').value.trim() || 'Torcedor';
      const text = $('#chatMsg').value.trim(); if(!text) return;
      const arr = loadChat(); arr.push({name, text, at: Date.now()}); saveChat(arr);
      e.target.reset(); drawChat();
    });
    drawChat();

    // ===== Stream Externo (HLS) =====
    // Dica: para HLS no Safari funciona direto. No Chrome/Firefox, use hls.js (CDN).
    let hls; // instância dinâmica se necessário
    const ensureHlsLib = async () => {
      if('canPlayType' in $('#liveVideo') && $('#liveVideo').canPlayType('application/vnd.apple.mpegURL')) return null;
      if(!window.Hls){
        await new Promise((res,rej)=>{
          const s = document.createElement('script');
          s.src = 'https://cdn.jsdelivr.net/npm/hls.js@1.5.8/dist/hls.min.js';
          s.onload = res; s.onerror = rej; document.head.appendChild(s);
        });
      }
      if(window.Hls && window.Hls.isSupported()){
        if(hls) { hls.destroy(); }
        hls = new Hls();
        return hls;
      }
      return null;
    };
    $('#useExternal').addEventListener('click', async ()=>{
      const url = $('#externalStream').value.trim();
      if(!url){ toast('Cole a URL do stream HLS (.m3u8).'); return; }
      const video = $('#liveVideo');
      const inst = await ensureHlsLib();
      if(inst){ inst.loadSource(url); inst.attachMedia(video); }
      else { video.src = url; }
      $('#liveBadge').style.display = 'inline-flex';
      toast('Stream carregado.');
    });

    // ===== Área do Apresentador (senha: 2310) =====
    const ADMIN_PASS = '2310';
    $('#unlock').addEventListener('click', ()=>{
      const ok = $('#adminPassword').value === ADMIN_PASS;
      if(ok){ $('#adminControls').style.display = 'block'; toast('Acesso liberado.'); }
      else { toast('Senha incorreta.'); }
    });

    // ===== Live Local com Câmera/Mic (sem servidor) =====
    let currentStream = null;
    let currentDeviceId = null;

    const toggleMute = () => {
      if(!currentStream) return;
      currentStream.getAudioTracks().forEach(t=> t.enabled = !t.enabled);
      const anyOn = currentStream.getAudioTracks().some(t=>t.enabled);
      $('#muteBtn').textContent = anyOn ? 'Mutar' : 'Desmutar';
    };

    async function startLocalLive(){
      try{
        const constraints = { audio:true, video: { width:{ideal:1280}, height:{ideal:720}, deviceId: currentDeviceId ? {exact: currentDeviceId} : undefined } };
        currentStream = await navigator.mediaDevices.getUserMedia(constraints);
        $('#liveVideo').srcObject = currentStream;
        $('#liveBadge').style.display = 'inline-flex';
        $('#startLive').disabled = true; $('#stopLive').disabled = false; $('#muteBtn').disabled = false; $('#flipCam').disabled = false;
        toast('Live iniciada localmente.');
      }catch(err){
        console.error(err); toast('Não foi possível acessar câmera/microfone.');
      }
    }
    function stopLocalLive(){
      if(currentStream){ currentStream.getTracks().forEach(t=>t.stop()); currentStream = null; }
      $('#liveVideo').srcObject = null; $('#liveVideo').removeAttribute('src');
      $('#startLive').disabled = false; $('#stopLive').disabled = true; $('#muteBtn').disabled = true; $('#flipCam').disabled = true;
      $('#liveBadge').style.display = 'none'; toast('Live encerrada.');
    }
    async function flipCamera(){
      try{
        const devices = await navigator.mediaDevices.enumerateDevices();
        const videos = devices.filter(d=>d.kind==='videoinput');
        if(!videos.length){ toast('Nenhuma câmera encontrada.'); return; }
        // pega o próximo id
        const idx = videos.findIndex(d=>d.deviceId===currentDeviceId);
        const next = videos[(idx+1) % videos.length];
        currentDeviceId = next.deviceId; stopLocalLive(); startLocalLive();
      }catch(e){ toast('Não foi possível trocar a câmera.'); }
    }

    $('#startLive').addEventListener('click', startLocalLive);
    $('#stopLive').addEventListener('click', stopLocalLive);
    $('#muteBtn').addEventListener('click', toggleMute);
    $('#flipCam').addEventListener('click', flipCamera);
  </script></body>
</html>
https://radardovitoria.github.io/RadarDoVitoria/
