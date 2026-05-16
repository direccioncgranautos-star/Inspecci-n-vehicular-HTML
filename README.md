# Inspecci-n-vehicular-HTML
Formulario de Inspección vehicular Inspectores peritos y Auxiliares 
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=5, viewport-fit=cover" />
<meta name="theme-color" content="#1976d2" />
<meta name="apple-mobile-web-app-capable" content="yes" />
<meta name="mobile-web-app-capable" content="yes" />
<title>Lista de Chequeo Vehículos — Granautos</title>
<style>
  :root{
    --azul:#1976d2; --azul-d:#0d47a1; --azul-l:#e3f2fd;
    --gris:#37474f; --gris-l:#eceff1; --bg:#f5f7fa;
    --ok:#2e7d32; --warn:#ef6c00; --err:#c62828;
    --txt:#212121; --muted:#607d8b;
    --card:#ffffff;
    --radius:12px; --shadow:0 2px 8px rgba(0,0,0,.08);
  }
  @media (prefers-color-scheme: dark){
    :root{
      --bg:#121212; --card:#1e1e1e; --txt:#e0e0e0; --muted:#9e9e9e;
      --gris-l:#2a2a2a;
    }
    .field{background:#262626!important;border-color:#333!important}
    input,select,textarea{background:#2a2a2a!important;color:var(--txt)!important;border-color:#444!important}
    table.grid td.row-label{background:#262626!important;color:#ddd!important}
    .grid-wrap{background:#1e1e1e!important;border-color:#333!important}
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  html,body{margin:0;padding:0;background:var(--bg);color:var(--txt);
    font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
    font-size:16px;line-height:1.4;
    padding-top:env(safe-area-inset-top);
    padding-bottom:env(safe-area-inset-bottom)}
  header{position:sticky;top:0;z-index:50;background:var(--card);border-bottom:1px solid #e0e0e0;
    padding:10px 14px;display:flex;align-items:center;gap:10px;box-shadow:var(--shadow)}
  header .logo{font-weight:800;font-size:22px;letter-spacing:-.5px;color:var(--gris)}
  header .logo span{color:var(--azul)}
  header .sub{font-size:12px;color:var(--muted);margin-left:auto;text-align:right;line-height:1.2}
  .progress{height:4px;background:#e0e0e0;position:sticky;top:54px;z-index:49}
  .progress>div{height:100%;background:linear-gradient(90deg,var(--azul),var(--ok));width:0%;transition:width .3s}
  main{max-width:880px;margin:0 auto;padding:14px;padding-bottom:160px}
  h1{font-size:22px;margin:0 0 4px}
  .intro{background:var(--card);border-radius:var(--radius);padding:14px 16px;box-shadow:var(--shadow);margin-bottom:14px}
  .intro p{margin:6px 0 0;color:var(--muted);font-size:14px}
  .toolbar{display:flex;gap:8px;margin-bottom:10px;flex-wrap:wrap}
  .toolbar button{flex:1;min-width:140px;padding:10px;border-radius:8px;border:1.5px solid var(--azul);
    background:var(--card);color:var(--azul);font-weight:600;cursor:pointer;font-size:14px}
  details.section{background:var(--card);border-radius:var(--radius);box-shadow:var(--shadow);margin-bottom:12px;overflow:hidden}
  details.section>summary{list-style:none;cursor:pointer;padding:14px 16px;background:linear-gradient(90deg,var(--azul),var(--azul-d));
    color:#fff;font-weight:700;font-size:16px;display:flex;align-items:center;gap:10px}
  details.section>summary::-webkit-details-marker{display:none}
  details.section>summary .badge{margin-left:auto;background:rgba(255,255,255,.2);padding:3px 10px;border-radius:30px;font-size:12px;font-weight:600}
  details.section>summary .chev{transition:transform .2s;display:inline-block}
  details.section[open]>summary .chev{transform:rotate(90deg)}
  .body{padding:12px 14px}
  .field{margin:0 0 14px;padding:12px;border:1px solid #eceff1;border-radius:10px;background:#fafbfc}
  .field>label.q{display:block;font-weight:600;margin-bottom:8px;font-size:15px}
  .field .req{color:var(--err);margin-left:3px}
  input[type=text], input[type=number], input[type=tel], select, textarea{
    width:100%;padding:12px;border:1px solid #cfd8dc;border-radius:10px;font-size:16px;background:#fff;font-family:inherit;color:var(--txt)}
  textarea{min-height:90px;resize:vertical}
  input:focus, select:focus, textarea:focus{outline:none;border-color:var(--azul);box-shadow:0 0 0 3px var(--azul-l)}
  .grid-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch;border:1px solid #cfd8dc;border-radius:10px;background:#fff}
  table.grid{border-collapse:collapse;width:100%;min-width:520px;font-size:14px}
  table.grid th, table.grid td{padding:10px 6px;text-align:center;border-bottom:1px solid #eceff1}
  table.grid th{background:var(--azul-l);color:var(--azul-d);font-weight:600;position:sticky;top:0}
  table.grid td.row-label{text-align:left;font-weight:500;color:var(--gris);white-space:nowrap;background:#fafbfc;position:sticky;left:0;z-index:1;padding-left:10px;padding-right:10px}
  table.grid input[type=radio]{transform:scale(1.4);accent-color:var(--azul);cursor:pointer;margin:6px}
  .actions{position:fixed;left:0;right:0;bottom:0;background:var(--card);border-top:1px solid #e0e0e0;padding:10px;
    padding-bottom:calc(10px + env(safe-area-inset-bottom));
    display:grid;grid-template-columns:repeat(3,1fr);gap:8px;box-shadow:0 -2px 8px rgba(0,0,0,.06);z-index:40}
  .actions button{padding:12px 6px;border-radius:10px;border:0;font-weight:700;font-size:13px;cursor:pointer;
    display:flex;align-items:center;justify-content:center;gap:6px;min-height:48px}
  .btn-primary{background:var(--azul);color:#fff}
  .btn-success{background:#25d366;color:#fff}
  .btn-secondary{background:var(--gris);color:#fff}
  .btn-outline{background:#fff;color:var(--azul);border:1.5px solid var(--azul)}
  .btn-warn{background:var(--warn);color:#fff}
  .btn-danger{background:var(--err);color:#fff}
  .actions button:active{transform:scale(.97)}
  .toast{position:fixed;left:50%;bottom:140px;transform:translateX(-50%);background:#263238;color:#fff;
    padding:10px 16px;border-radius:30px;font-size:14px;opacity:0;transition:opacity .25s;z-index:100;pointer-events:none;max-width:90%;text-align:center}
  .toast.show{opacity:1}
  .modal{position:fixed;inset:0;background:rgba(0,0,0,.55);display:none;align-items:center;justify-content:center;z-index:200;padding:14px}
  .modal.show{display:flex}
  .modal .card{background:var(--card);border-radius:var(--radius);max-width:680px;width:100%;max-height:85vh;display:flex;flex-direction:column}
  .modal h3{margin:0;padding:14px 16px;border-bottom:1px solid #eceff1;font-size:18px;color:var(--azul-d)}
  .modal pre{margin:0;padding:14px 16px;overflow:auto;flex:1;font-family:ui-monospace,Menlo,Consolas,monospace;
    font-size:13px;white-space:pre-wrap;word-break:break-word;background:#fafbfc;color:var(--txt)}
  .modal .foot{padding:10px;border-top:1px solid #eceff1;display:flex;gap:8px;flex-wrap:wrap;justify-content:flex-end}
  .modal .foot button{padding:10px 14px;border-radius:8px;border:0;font-weight:700;cursor:pointer}
  .field.error{border-color:var(--err);background:#ffebee}
  .field.error label.q{color:var(--err)}
  @media (min-width:640px){
    .actions{grid-template-columns:repeat(6,1fr)}
  }
  @media print{
    header,.actions,.progress,.toolbar{display:none}
    details.section{box-shadow:none;border:1px solid #ccc;page-break-inside:avoid}
    details.section>.body{display:block!important}
    body{background:#fff}
    main{padding-bottom:0}
  }
</style>
</head>
<body>

<header>
  <div class="logo">Gran<span>a</span>utos</div>
  <div class="sub">
    <div><strong>FO-GO-04</strong></div>
    <div id="hdrFecha"></div>
  </div>
</header>
<div class="progress"><div id="progBar"></div></div>

<main>
  <section class="intro">
    <h1>Lista de Chequeo Vehículos — Granautos</h1>
    <p>Formato de inspección <strong>FO-GO-04</strong> | Diligencia todos los campos antes de enviar.</p>
  </section>

  <div class="toolbar">
    <button type="button" onclick="toggleAll(true)">⬇️ Expandir todo</button>
    <button type="button" onclick="toggleAll(false)">⬆️ Colapsar todo</button>
  </div>

  <form id="form" novalidate></form>
</main>

<div class="actions">
  <button type="button" class="btn-primary"   onclick="guardar()">💾 Guardar</button>
  <button type="button" class="btn-outline"   onclick="generarResumen()">📋 Resumen</button>
  <button type="button" class="btn-success"   onclick="compartirWA()">🟢 WhatsApp</button>
  <button type="button" class="btn-secondary" onclick="exportarPDF()">📄 PDF</button>
  <button type="button" class="btn-warn"      onclick="limpiar()">🧹 Limpiar</button>
  <button type="button" class="btn-danger"    onclick="nuevaInspeccion()">➕ Nueva</button>
</div>

<div class="toast" id="toast"></div>

<div class="modal" id="modal">
  <div class="card">
    <h3 id="modalTitle">Resumen</h3>
    <pre id="modalBody"></pre>
    <div class="foot">
      <button class="btn-secondary" onclick="copiarResumen()">Copiar</button>
      <button class="btn-success"   onclick="compartirWA()">WhatsApp</button>
      <button class="btn-outline"   onclick="cerrarModal()">Cerrar</button>
    </div>
  </div>
</div>

<script>
/* === DEFINICIÓN DEL FORMULARIO === */
const FORM = [
  {y:'sec', t:'Información general (Sección 1 de 7)'},
  {y:0, t:'Placa', req:true},
  {y:0, t:'Marca', req:true},
  {y:0, t:'Línea', req:false},
  {y:0, t:'Modelo (año)', req:true, mode:'numeric'},
  {y:0, t:'Kilometraje', req:true, mode:'numeric'},
  {y:0, t:'Nombre del inspector', req:true, remember:true},
  {y:3, t:'Tipo de caja', req:true, opt:['Manual','Automática','Secuencial','CVT','Doble embrague']},
  {y:3, t:'Botón / Código de seguridad', req:true, opt:['Sí','No','N/A']},
  {y:3, t:'Protección a pintura', req:false, opt:['Sí','No']},
  {y:3, t:'Acompañamiento contraparte', req:false, opt:['Sí','No']},

  {y:'sec', t:'Interior (Sección 2 de 7)'},
  {y:7, t:'Tapizados',
    r:['Tapizado sillas','Tapizado techo','Tapizado piso','Cinturones','Cabeceros','Carteras puertas','Millare','Parasoles','Guantera','Volante','Tablero acrílico','Pomo','Consola central'],
    c:['B (Bueno)','R (Regular)','D (Dañado)','M (Malo)']},
  {y:7, t:'Electro interior',
    r:['Radio','Bocina','Tablero','Limpiabrisa','Calefacción','Aire acondicionado','Elevavidrios','Sunroof','Espejos','Testigos tablero','Alarma','Mecanismo sillas'],
    c:['B (Bueno)','R (Regular)','M (Malo)','N/A']},
  {y:3, t:'Códigos de falla presentes', req:false, opt:['Sí','No']},
  {y:1, t:'Observaciones interior', req:false},

  {y:'sec', t:'Luces (Sección 3 de 7)'},
  {y:7, t:'Luces',
    r:['Altas','Bajas','Cocuyos','Exploradoras','Direccionales','Estacionarias','Stop trasero','Stop baúl','Tercer stop','Reversa','Luz placa','Luz techo'],
    c:['B (Bueno)','R (Regular)','M (Malo)','N/A']},

  {y:'sec', t:'Carrocería y estructura (Sección 4 de 7)'},
  {y:7, t:'Carrocería',
    r:['Guardabarro izq','Puerta delantera izq','Puerta trasera izq','Estribo izq','Costado izq','Bomper trasero','Tapa baúl','Costado der','Estribo der','Puerta trasera der','Puerta delantera der','Guardabarro der','Bomper delantero','Capot','Capota','Espejos laterales','Espaldar cabina','Piso baúl'],
    c:['Bueno','Rayón','Repintado','Sumido','Regular reparación','Mala reparación','Deformación media','Deformación fuerte','Impermeabilizado','Pintura deteriorada','Oxidación','Corrosión','Fisura','N/A']},
  {y:1, t:'Observaciones carrocería', req:false},
  {y:7, t:'Estructura',
    r:['Punta delantera der','Punta delantera izq','Viga derecha','Viga izquierda','Traviesas','Paral panorámico','Parales centrales','Largueros capota','Parales costado','Parales baúl','Punta trasera der','Punta trasera izq','Guardapolvo met','Panel trasero','Cajas de impacto'],
    c:['Bueno','Rayón','Repintado','Sumido','Regular reparación','Mala reparación','Deformación media','Deformación fuerte','Impermeabilizado','Pintura deteriorada','Oxidación','Corrosión','Fisura','N/A']},
  {y:1, t:'Observaciones estructura', req:false},

  {y:'sec', t:'Fluidos, fugas y llantas (Sección 5 de 7)'},
  {y:7, t:'Nivel de fluidos',
    r:['Aceite de motor','Refrigerante','Dirección hidráulica','Líquido frenos','Limpiabrisa'],
    c:['N (Normal)','M (Medio)','B (Bajo)','C (Crítico)']},
  {y:7, t:'Fugas',
    r:['Aceite motor','Aceite caja','Dirección hidráulica','Amortiguadores','Refrigerante','Frenos','Guardapolvos','Diferencial','Combustible'],
    c:['S (Sí hay fuga)','N (No hay fuga)','H (Hay humedad)']},
  {y:0, t:'Llantas — Delantera izquierda (profundidad mm)', req:false, mode:'numeric'},
  {y:0, t:'Llantas — Trasera izquierda (profundidad mm)', req:false, mode:'numeric'},
  {y:0, t:'Llantas — Delantera derecha (profundidad mm)', req:false, mode:'numeric'},
  {y:0, t:'Llantas — Trasera derecha (profundidad mm)', req:false, mode:'numeric'},
  {y:0, t:'Llantas — Repuesto (profundidad mm)', req:false, mode:'numeric'},
  {y:1, t:'Observaciones fluidos / llantas', req:false},

  {y:'sec', t:'Suspensión y partes bajas (Sección 6 de 7)'},
  {y:7, t:'Suspensión',
    r:['Discos','Past delantera','Past trasera','Espirales','Muelles','Ejes','Caja de dirección','Brazo axial','Terminales','Rótulas','Estabilizadora','Tijeras','Bujes','Rodamientos'],
    c:['B (Bueno)','R (Regular)','M (Malo)','N/A']},
  {y:7, t:'Partes bajas',
    r:['Catalizador','Silenciador','Tubería','Cuna motor','Protectores inferiores','Paso ruedas','Refuerzo piso','Impermeabilizado'],
    c:['B (Bueno)','R (Regular)','M (Malo)','N/A']},
  {y:1, t:'Observaciones suspensión / partes bajas', req:false},

  {y:'sec', t:'Rechazos y cierre (Sección 7 de 7)'},
  {y:3, t:'Rechazo general',     req:true, opt:['SÍ','NO','Sin precedente']},
  {y:3, t:'Asegurable',          req:true, opt:['SÍ','NO','Sujeto a políticas']},
  {y:3, t:'Rechazo estructural', req:true, opt:['SÍ','NO']},
  {y:3, t:'Rechazo carrocería',  req:true, opt:['SÍ','NO']},
  {y:3, t:'Rechazo eléctrico',   req:true, opt:['SÍ','NO']},
  {y:3, t:'Rechazo mecánico',    req:true, opt:['SÍ','NO']},
  {y:1, t:'Observaciones finales', req:false}
];

const STORAGE_KEY = 'granautos_inspeccion_v2';
const REMEMBER_KEY = 'granautos_remember_v1';
const AUTOSAVE_MS = 1000;

const esc = s => String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const slug = s => s.toLowerCase().normalize('NFD').replace(/[\u0300-\u036f]/g,'').replace(/[^a-z0-9]+/g,'_').replace(/^_|_$/g,'');
const cssEsc = s => String(s).replace(/(["\\])/g,'\\$1');

/* === RENDER === */
function render(){
  const form = document.getElementById('form');
  let html = '';
  let secOpen = false;
  let secIdx = 0;

  FORM.forEach((f,i)=>{
    if(f.y==='sec'){
      if(secOpen) html += '</div></details>';
      secIdx++;
      const open = secIdx===1 ? 'open' : '';
      html += `<details class="section" ${open}><summary><span class="chev">▶</span> ${esc(f.t)} <span class="badge">Sec ${secIdx}</span></summary><div class="body">`;
      secOpen = true;
      return;
    }
    const id = 'f_'+slug(f.t)+'_'+i;
    const req = f.req ? '<span class="req">*</span>' : '';
    html += `<div class="field" data-name="${esc(f.t)}" data-req="${f.req?1:0}">`;
    html += `<label class="q" for="${id}">${esc(f.t)}${req}</label>`;

    if(f.y===0){
      const mode = f.mode==='numeric' ? 'inputmode="numeric" pattern="[0-9]*"' : '';
      html += `<input type="text" id="${id}" name="${esc(f.t)}" autocomplete="off" ${mode} />`;
    } else if(f.y===1){
      html += `<textarea id="${id}" name="${esc(f.t)}"></textarea>`;
    } else if(f.y===3){
      html += `<select id="${id}" name="${esc(f.t)}"><option value="">Elige</option>`;
      f.opt.forEach(o => html += `<option>${esc(o)}</option>`);
      html += `</select>`;
    } else if(f.y===7){
      html += `<div class="grid-wrap"><table class="grid"><thead><tr><th></th>`;
      f.c.forEach(c => html += `<th>${esc(c)}</th>`);
      html += `</tr></thead><tbody>`;
      f.r.forEach((r,ri)=>{
        const gname = id+'_r'+ri;
        html += `<tr><td class="row-label">${esc(r)}</td>`;
        f.c.forEach(c=>{
          html += `<td><input type="radio" name="${gname}" data-grid="${esc(f.t)}" data-row="${esc(r)}" value="${esc(c)}" /></td>`;
        });
        html += `</tr>`;
      });
      html += `</tbody></table></div>`;
    }
    html += `</div>`;
  });
  if(secOpen) html += '</div></details>';
  form.innerHTML = html;

  bindAutosave();
  cargar();
  cargarRecordados();
  actualizarProgreso();
  document.getElementById('hdrFecha').textContent = new Date().toLocaleDateString('es-CO');
}

/* === DATOS === */
function recolectar(){
  const data = {};
  document.querySelectorAll('#form input[type=text], #form textarea, #form select').forEach(el=>{
    if(el.value!=='') data[el.name] = el.value.trim();
  });
  document.querySelectorAll('#form input[type=radio]:checked').forEach(r=>{
    const g = r.dataset.grid, row = r.dataset.row;
    if(!data[g]) data[g] = {};
    data[g][row] = r.value;
  });
  return data;
}

/* === PROGRESO === */
function actualizarProgreso(){
  const total = document.querySelectorAll('#form .field').length;
  let done = 0;
  document.querySelectorAll('#form .field').forEach(f=>{
    const inp = f.querySelector('input[type=text], textarea, select');
    if(inp && inp.value.trim()){ done++; return; }
    const r = f.querySelector('input[type=radio]:checked');
    if(r){ done++; }
  });
  const pct = total ? Math.round((done/total)*100) : 0;
  document.getElementById('progBar').style.width = pct+'%';
}

/* === VALIDACIÓN === */
function validar(){
  let ok = true, firstErr = null;
  document.querySelectorAll('.field').forEach(f=>f.classList.remove('error'));
  document.querySelectorAll('.field[data-req="1"]').forEach(f=>{
    const inp = f.querySelector('input[type=text], textarea, select');
    if(inp && !inp.value.trim()){
      f.classList.add('error'); ok=false;
      if(!firstErr) firstErr = f;
    }
  });
  if(!ok && firstErr){
    const sec = firstErr.closest('details.section');
    if(sec) sec.open = true;
    firstErr.scrollIntoView({behavior:'smooth',block:'center'});
    toast('Faltan campos obligatorios');
  }
  return ok;
}

/* === PERSISTENCIA === */
let saveTimer = null;
function bindAutosave(){
  const f = document.getElementById('form');
  f.addEventListener('input', ()=>{
    clearTimeout(saveTimer);
    saveTimer = setTimeout(()=>{ autoguardar(); actualizarProgreso(); }, AUTOSAVE_MS);
  });
  f.addEventListener('change', ()=>{ autoguardar(); actualizarProgreso(); });
}
function autoguardar(){
  try{ localStorage.setItem(STORAGE_KEY, JSON.stringify(recolectar())); }catch(e){}
}
function cargar(){
  try{
    const raw = localStorage.getItem(STORAGE_KEY);
    if(!raw) return;
    const data = JSON.parse(raw);
    Object.keys(data).forEach(k=>{
      const v = data[k];
      if(typeof v === 'string'){
        const el = document.querySelector(`#form [name="${cssEsc(k)}"]`);
        if(el) el.value = v;
      } else if(v && typeof v === 'object'){
        Object.keys(v).forEach(row=>{
          const sel = `#form input[type=radio][data-grid="${cssEsc(k)}"][data-row="${cssEsc(row)}"][value="${cssEsc(v[row])}"]`;
          const r = document.querySelector(sel);
          if(r) r.checked = true;
        });
      }
    });
  }catch(e){}
}

/* === RECORDAR campos (ej. inspector) === */
function cargarRecordados(){
  try{
    const raw = localStorage.getItem(REMEMBER_KEY);
    if(!raw) return;
    const data = JSON.parse(raw);
    FORM.filter(f=>f.remember).forEach(f=>{
      if(data[f.t]){
        const el = document.querySelector(`#form [name="${cssEsc(f.t)}"]`);
        if(el && !el.value) el.value = data[f.t];
      }
    });
  }catch(e){}
}
function guardarRecordados(){
  try{
    const memo = {};
    FORM.filter(f=>f.remember).forEach(f=>{
      const el = document.querySelector(`#form [name="${cssEsc(f.t)}"]`);
      if(el && el.value.trim()) memo[f.t] = el.value.trim();
    });
    localStorage.setItem(REMEMBER_KEY, JSON.stringify(memo));
  }catch(e){}
}

/* === ACCIONES === */
function guardar(){
  if(!validar()) return;
  autoguardar();
  guardarRecordados();
  toast('✓ Inspección guardada localmente');
}
function limpiar(){
  if(!confirm('¿Limpiar todo el formulario? Esta acción no se puede deshacer.')) return;
  document.querySelectorAll('#form input[type=text], #form textarea').forEach(el=>el.value='');
  document.querySelectorAll('#form select').forEach(el=>el.value='');
  document.querySelectorAll('#form input[type=
