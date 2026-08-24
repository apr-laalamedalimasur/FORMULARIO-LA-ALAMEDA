<!-- v2 -->
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Formulario — Alameda Lima Sur</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,600;9..144,700&family=Inter:wght@400;500;600;700&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#EEF2EF; --paper:#FFFFFF; --ink:#182823; --ink-soft:#4B5D57;
  --line:#D7E0DA; --line-soft:#E7ECE8; --primary:#1F5C4F; --primary-dark:#123D34;
  --accent:#C4882F; --accent-soft:#F3E2C3; --ok:#2F8558; --ok-bg:#E5F3EA;
  --bad:#AF4B37; --bad-bg:#FBE9E4;
}
*{box-sizing:border-box;}
body{margin:0; background:var(--bg); color:var(--ink); font-family:'Inter',sans-serif; min-height:100vh;}
.app{max-width:640px; margin:0 auto; padding:20px 16px 70px;}
.hero{background:var(--primary); border-radius:14px; padding:22px 20px; color:#fff; margin-bottom:18px;}
.hero .eyebrow{font-family:'JetBrains Mono',monospace; font-size:11px; letter-spacing:.12em; text-transform:uppercase; color:var(--accent-soft); margin:0 0 6px;}
.hero h1{font-family:'Fraunces',serif; font-size:21px; margin:0 0 6px; line-height:1.25;}
.hero p{margin:0; font-size:13px; color:#D7E6DE; line-height:1.5;}

.seg{display:flex; gap:6px; margin-bottom:16px; background:#fff; border:1px solid var(--line); border-radius:12px; padding:5px;}
.seg button{flex:1; border:none; background:none; padding:11px 8px; border-radius:8px; font-family:'Inter',sans-serif; font-weight:700; font-size:13px; color:var(--ink-soft); cursor:pointer;}
.seg button.active{background:var(--primary); color:#fff;}

.card{background:var(--paper); border:1px solid var(--line); border-radius:12px; padding:18px; margin-bottom:16px;}
.card h2{font-family:'Fraunces',serif; font-size:17px; margin:0 0 3px;}
.card .sub{color:var(--ink-soft); font-size:12.5px; margin:0 0 14px; line-height:1.5;}

.section{display:none;}
.section.active{display:block;}

.grid2{display:grid; grid-template-columns:1fr 1fr; gap:10px 12px;}
@media(max-width:480px){.grid2{grid-template-columns:1fr;}}
.field{margin-bottom:0;}
.field.full{grid-column:1/-1;}
.field label{display:block; font-size:11px; font-weight:700; text-transform:uppercase; letter-spacing:.03em; color:var(--ink-soft); margin-bottom:4px;}
.field input, .field select, .field textarea{
  width:100%; padding:10px 11px; border:1px solid var(--line); border-radius:8px;
  font-family:'Inter',sans-serif; font-size:14px; background:#FBFCFB; color:var(--ink);
}
.field textarea{min-height:60px; resize:vertical;}
.grid2 .field{margin-bottom:10px;}

.chk-row{display:flex; flex-wrap:wrap; gap:8px 16px; font-size:13px;}
.chk-row label{display:flex; align-items:center; gap:6px; font-weight:500; color:var(--ink-soft);}

.rep-row{display:flex; gap:6px; flex-wrap:wrap; align-items:center; margin-bottom:8px; background:#FBFCFB; border:1px solid var(--line-soft); border-radius:8px; padding:8px;}
.rep-row input, .rep-row select{flex:1; min-width:90px; padding:7px 8px; border:1px solid var(--line); border-radius:6px; font-size:12.5px;}
.rep-row .narrow{flex:0 0 62px; min-width:0;}
.rep-row button{flex:0 0 auto; background:none; border:none; color:var(--bad); font-size:16px; cursor:pointer; padding:0 4px;}
.btn-add{background:none; border:1px dashed var(--line); color:var(--primary-dark); border-radius:8px; padding:9px; font-size:12.5px; font-weight:600; width:100%; cursor:pointer;}

.send-row{display:flex; flex-direction:column; gap:8px; margin-top:16px;}
.btn{border:none; border-radius:10px; padding:13px 16px; font-weight:700; font-size:14px; cursor:pointer; font-family:'Inter',sans-serif;}
.btn:disabled{opacity:.5; cursor:not-allowed;}
.btn-wa{background:#25D366; color:#fff;}
.btn-mail{background:var(--primary); color:#fff;}
.btn-copy{background:none; border:1.5px dashed var(--line); color:var(--ink-soft); font-weight:600;}
.btn-note{font-size:11.5px; color:var(--ink-soft); text-align:center; margin-top:2px;}

.msg{margin-top:10px; font-size:13px; padding:10px 12px; border-radius:8px;}
.msg.ok{background:var(--ok-bg); color:var(--ok);}
.msg.err{background:var(--bad-bg); color:var(--bad);}

.policy{border:1px solid var(--line); border-radius:8px; padding:10px 12px; background:#FBFCFB; margin-top:14px; font-size:12.5px;}
.policy summary{cursor:pointer; font-weight:700; color:var(--primary-dark); list-style:none;}
.policy summary::-webkit-details-marker{display:none;}
.policy summary::before{content:"ℹ️ "; }
.policy[open] summary{margin-bottom:8px;}
.policy p{margin:6px 0; color:var(--ink-soft); line-height:1.5;}
.policy strong{color:var(--ink);}

footer{text-align:center; color:var(--ink-soft); font-size:11px; margin-top:20px; font-family:'JetBrains Mono',monospace;}
</style>
</head>
<body>
<div class="app">

  <div class="hero">
    <p class="eyebrow">Asociación Alameda Lima Sur</p>
    <h1>Verifica si estás empadronado o actualiza tus datos</h1>
    <p>Completa el formulario y envíalo por WhatsApp o correo — no necesitas crear ninguna cuenta.</p>
  </div>

  <div class="seg" id="seg">
    <button class="active" data-s="datos">Verifica si estás empadronado</button>
    <button data-s="censo">Actualiza tus datos padrón</button>
  </div>

  <!-- ===== ACTUALIZA TUS DATOS ===== -->
  <div class="section active" id="sec-datos">
    <div class="card">
      <h2>Verifica si estás empadronado</h2>
      <p class="sub">Escribe tu DNI para verificar si ya estás registrado en el padrón de asociados. Si lo estás, revisa/actualiza tus datos aquí. Si no apareces, ve a "Actualiza tus datos padrón" para registrarte.</p>
      <div class="grid2">
        <div class="field"><label>DNI</label><input type="text" id="as_dni" inputmode="numeric" maxlength="8"></div>
        <div class="field full" id="as_padron_status" style="margin-top:-8px;"></div>
        <div class="field"><label>Nombres</label><input type="text" id="as_nombres"></div>
        <div class="field"><label>Apellidos</label><input type="text" id="as_apellidos"></div>
        <div class="field"><label>Teléfono</label><input type="text" id="as_telefono"></div>
        <div class="field"><label>Email</label><input type="email" id="as_email"></div>
        <div class="field full"><label>Dirección de domicilio (si difiere del lote)</label><input type="text" id="as_direccion"></div>
        <div class="field"><label>Etapa</label><input type="text" id="as_etapa" placeholder="Ej. I, II, VII"></div>
        <div class="field"><label>Manzana</label><input type="text" id="as_manzana"></div>
        <div class="field"><label>Lote</label><input type="text" id="as_lote"></div>
        <div class="field"><label>Cónyuge / pareja — nombre</label><input type="text" id="as_conyugeNombre"></div>
        <div class="field"><label>Cónyuge / pareja — DNI</label><input type="text" id="as_conyugeDni"></div>
      </div>
      <div class="field full" style="margin-top:6px;">
        <label>Hijos / dependientes</label>
        <div id="as_dependientesList"></div>
        <button type="button" class="btn-add" onclick="agregarDependiente()">+ Agregar hijo/dependiente</button>
      </div>

      <details class="policy">
        <summary>Política de tratamiento de datos personales (Ley N° 29733)</summary>
        <p><strong>Responsable:</strong> Asociación de Propietarios y Residentes de la Urbanización Alameda Lima Sur.</p>
        <p><strong>Finalidad:</strong> administrar el padrón de asociados, gestionar cuotas, seguridad y comunicación vecinal.</p>
        <p><strong>Cómo se envían sus datos:</strong> al darle a "Enviar", usted mismo los manda directo por su WhatsApp o correo al Consejo Directivo. Esta página no los guarda ni los transmite a ningún servidor propio.</p>
        <p><strong>Conservación:</strong> mientras dure su condición de asociado o residente, o hasta que solicite su eliminación.</p>
        <p><strong>Sus derechos:</strong> puede pedir acceso, rectificación, cancelación u oposición al uso de sus datos (derechos ARCO) escribiendo al mismo WhatsApp o correo de contacto de la asociación.</p>
        <p>No se comparten con terceros ajenos a la asociación.</p>
      </details>
      <div class="field full" style="margin-top:10px;">
        <label style="text-transform:none; font-weight:500; display:flex; gap:6px; align-items:flex-start;">
          <input type="checkbox" id="as_consiento" style="width:auto; margin-top:3px;">
          <span>Autorizo el uso de mis datos personales para fines de administración, comunicación y seguridad de la asociación (Ley N° 29733).</span>
        </label>
      </div>

      <div class="send-row">
        <button class="btn btn-wa" onclick="enviarDatosWhatsapp()">📲 Registrar y enviar por WhatsApp</button>
        <button class="btn btn-mail" onclick="enviarDatosCorreo()">✉️ Registrar y enviar por correo</button>
        <button class="btn btn-copy" onclick="copiarDatos()">📋 Registrar y copiar mensaje</button>
      </div>
      <div id="as_msg"></div>
    </div>
  </div>

  <!-- ===== FICHA DE CENSO ===== -->
  <div class="section" id="sec-censo">
    <div class="card">
      <h2>Actualiza tus datos padrón · Ficha de registro y censo de predios</h2>
      <p class="sub">Urb. La Alameda Lima Sur · Villa del Sur 1, 2 y 3. Complétala aunque no seas asociado todavía.</p>
      <div class="grid2">
        <div class="field full"><label>Sector</label>
          <select id="cn_sector">
            <option>Urb. La Alameda Lima Sur</option><option>Villa del Sur 1</option>
            <option>Villa del Sur 2</option><option>Villa del Sur 3</option>
          </select>
        </div>
        <div class="field"><label>Nombres</label><input type="text" id="cn_nombres"></div>
        <div class="field"><label>Apellidos</label><input type="text" id="cn_apellidos"></div>
        <div class="field"><label>DNI</label><input type="text" id="cn_dni"></div>
        <div class="field"><label>Teléfono</label><input type="text" id="cn_telefono"></div>
        <div class="field"><label>Teléfono alterno</label><input type="text" id="cn_telefonoAlt"></div>
        <div class="field"><label>Email</label><input type="email" id="cn_email"></div>
        <div class="field"><label>Etapa</label><input type="text" id="cn_etapa"></div>
        <div class="field"><label>Calle</label><input type="text" id="cn_calle"></div>
        <div class="field"><label>Manzana</label><input type="text" id="cn_manzana"></div>
        <div class="field"><label>Lote</label><input type="text" id="cn_lote"></div>
        <div class="field"><label>Condición de propiedad</label>
          <select id="cn_condicionPropiedad"><option>Propietario</option><option>Familiar de Propietario Residente</option><option>Compra de Bien Futuro</option><option>Inquilino</option></select>
        </div>
        <div class="field"><label>Condición del predio</label>
          <select id="cn_condicionPredio"><option>Terreno sin construir</option><option>En construcción</option><option>Terminado</option><option>Deshabitado / sin residente</option></select>
        </div>
        <div class="field"><label>N° suministro luz</label><input type="text" id="cn_luz"></div>
        <div class="field"><label>N° suministro agua</label><input type="text" id="cn_agua"></div>
        <div class="field full"><label>N° de partida SUNARP del predio (opcional, si lo tiene a la mano)</label><input type="text" id="cn_partidaSunarp" placeholder="No indispensable — déjelo en blanco si no lo sabe"></div>
        <div class="field full"><label>N° de personas que viven en el predio</label><input type="number" id="cn_personas" min="0"></div>
      </div>

      <div class="field full" style="margin-top:6px;">
        <label>Vehículos</label>
        <div id="cn_vehiculosList"></div>
        <button type="button" class="btn-add" onclick="agregarVehiculo()">+ Agregar vehículo</button>
      </div>

      <div class="grid2" style="margin-top:10px;">
        <div class="field full"><label>¿Tiene mascotas en la urbanización?</label>
          <select id="cn_mascotas" onchange="toggleMascotas()"><option value="No">No</option><option value="Si">Sí</option></select>
        </div>
      </div>
      <div class="field full" id="cn_mascotasWrap" style="display:none;">
        <label>Detalle de cada mascota</label>
        <div id="cn_mascotasList"></div>
        <button type="button" class="btn-add" onclick="agregarMascota()">+ Agregar mascota</button>
      </div>

      <div class="field full" style="margin-top:10px;">
        <label>Contacto(s) de emergencia (hasta 3)</label>
        <div id="cn_contactosList"></div>
        <button type="button" class="btn-add" id="btnAddContacto" onclick="agregarContacto()">+ Agregar contacto</button>
      </div>

      <div class="grid2" style="margin-top:10px;">
        <div class="field full"><label>¿Desea ser parte de la Asociación de Propietarios y Residentes La Alameda Lima-Sur?</label>
          <select id="cn_desea"><option value="Si">Sí</option><option value="No">No</option></select>
        </div>
        <div class="field full"><label>Si su respuesta es "No", ¿por qué? (opcional)</label>
          <select id="cn_motivoNo">
            <option value="">— No aplica —</option>
            <option>Ya pertenezco a otra organización vecinal</option>
            <option>No conozco los beneficios de asociarme</option>
            <option>No estoy de acuerdo con la gestión actual</option>
            <option>Prefiero decidir más adelante</option>
            <option value="Otro">Otro (especifique abajo)</option>
          </select>
        </div>
        <div class="field full"><label>Detalle (si eligió "Otro")</label><input type="text" id="cn_motivoNoOtro"></div>
      </div>

      <div class="field full" style="margin-top:6px;">
        <label>Estaría de acuerdo en aportar para (esto todavía no significa un compromiso):</label>
        <div class="chk-row">
          <label><input type="checkbox" id="cn_apVigilancia"> Vigilancia</label>
          <label><input type="checkbox" id="cn_apAlarma"> Alarma vecinal</label>
          <label><input type="checkbox" id="cn_apCamaras"> Cámaras</label>
          <label><input type="checkbox" id="cn_apGestion"> Gestión</label>
          <label><input type="checkbox" id="cn_apMoto"> Moto eléctrica ronda</label>
        </div>
      </div>
      <div class="field full" style="margin-top:10px;">
        <label>¿Participaría en jornadas para recaudar fondos para cubrir estos gastos?</label>
        <select id="cn_jornadas"><option value="No">No</option><option value="Si">Sí</option></select>
        <p class="sub" style="margin:4px 0 0;">(pollada, rifa, tómbola, otros) · (campeonatos deportivos: vóley, básket, fulbito)</p>
      </div>
      <div class="field full" style="margin-top:10px;">
        <label>Preferencias deportivas</label>
        <div class="chk-row">
          <label><input type="checkbox" id="cn_depFulbito"> Fulbito</label>
          <label><input type="checkbox" id="cn_depFutbol"> Fútbol</label>
          <label><input type="checkbox" id="cn_depVoley"> Vóley</label>
          <label><input type="checkbox" id="cn_depBasquet"> Básquet</label>
          <label><input type="checkbox" id="cn_depNatacion"> Natación</label>
          <label><input type="checkbox" id="cn_depOtroCheck"> Otro:</label>
        </div>
        <input type="text" id="cn_depOtro" placeholder="Especifique otro deporte" style="margin-top:8px;">
      </div>
      <details class="policy">
        <summary>Política de tratamiento de datos personales (Ley N° 29733)</summary>
        <p><strong>Responsable:</strong> Asociación de Propietarios y Residentes de la Urbanización Alameda Lima Sur.</p>
        <p><strong>Finalidad:</strong> elaborar el censo de predios y asociados, gestionar cuotas, seguridad y comunicación vecinal.</p>
        <p><strong>Cómo se envían sus datos:</strong> al darle a "Enviar", usted mismo los manda directo por su WhatsApp o correo al Consejo Directivo. Esta página no los guarda ni los transmite a ningún servidor propio.</p>
        <p><strong>Conservación:</strong> mientras dure su condición de asociado o residente, o hasta que solicite su eliminación.</p>
        <p><strong>Sus derechos:</strong> puede pedir acceso, rectificación, cancelación u oposición al uso de sus datos (derechos ARCO) escribiendo al mismo WhatsApp o correo de contacto de la asociación.</p>
        <p>No se comparten con terceros ajenos a la asociación.</p>
      </details>
      <div class="field full" style="margin-top:10px;">
        <label style="text-transform:none; font-weight:500; display:flex; gap:6px; align-items:flex-start;">
          <input type="checkbox" id="cn_consiento" style="width:auto; margin-top:3px;">
          <span>Autorizo el uso de mis datos personales para fines de administración, comunicación y seguridad de la asociación (Ley N° 29733).</span>
        </label>
      </div>

      <div class="send-row">
        <button class="btn btn-wa" onclick="enviarCensoWhatsapp()">📲 Registrar y enviar por WhatsApp</button>
        <button class="btn btn-mail" onclick="enviarCensoCorreo()">✉️ Registrar y enviar por correo</button>
        <button class="btn btn-copy" onclick="copiarCenso()">📋 Registrar y copiar mensaje</button>
      </div>
      <div id="cn_msg"></div>
    </div>
  </div>

  <footer>ASOCIACIÓN ALAMEDA LIMA SUR · formulario de contacto directo</footer>
</div>

<script>
const PADRON = [{"dni": "09873784", "apellidos": "ALCEDO BUSTAMANTE", "nombres": "JUAN CARLOS"}, {"dni": "46181633", "apellidos": "ALDAUF ABANTO", "nombres": "MARCO ANTONIO"}, {"dni": "10638624", "apellidos": "ALDUNATE VILLANO", "nombres": "FILOMENA ADELA"}, {"dni": "10036628", "apellidos": "ALEGRIA RIOS", "nombres": "LIZARDO EUGENIO"}, {"dni": "06139856", "apellidos": "ALIAGA ALIAGA", "nombres": "GILBERT PERCY"}, {"dni": "22090634", "apellidos": "ARBIETO CAMPOS", "nombres": "ARNALDO IVAN"}, {"dni": "09896361", "apellidos": "ARQUINIGO HUERTA", "nombres": "LUIS ANTONIO"}, {"dni": "42960260", "apellidos": "ARQUIÑEGO BENDITA", "nombres": "JASMIN JANET"}, {"dni": "08662969", "apellidos": "BENDEZU DOMINGUEZ", "nombres": "MICHELL ANGELLA"}, {"dni": "74944058", "apellidos": "BERMUDEZ LOPEZ", "nombres": "YZAVHO SASHA"}, {"dni": "08121022", "apellidos": "CABRERA CRUZADO", "nombres": "JUAN GILBERTO"}, {"dni": "74377185", "apellidos": "CABRERA SASAKI", "nombres": "SAORI"}, {"dni": "09688066", "apellidos": "CAMASITA VARGAS", "nombres": "ARTEMIO ORLANDO"}, {"dni": "08038956", "apellidos": "CARRANZA RENGIFO", "nombres": "OMAR"}, {"dni": "20112511", "apellidos": "CERDA RAMIREZ", "nombres": "FLORMIRA"}, {"dni": "40564784", "apellidos": "CERECEDA MANRIQUE", "nombres": "AUGUSTIN FERNANDO"}, {"dni": "45493272", "apellidos": "CHACON OLIVA", "nombres": "MARCOS ISAIAS"}, {"dni": "40374711", "apellidos": "CHAVEZ HERNANDEZ", "nombres": "AGUSTIN JOHN"}, {"dni": "40943997", "apellidos": "CHAVEZ HERNANDEZ", "nombres": "RICARDO ANTONIO"}, {"dni": "43455891", "apellidos": "CHAVEZ ORTIZ", "nombres": "MIRCO SAUL"}, {"dni": "08123578", "apellidos": "CHAVEZ PONCE", "nombres": "NANCY ROSARIO"}, {"dni": "08570117", "apellidos": "CHI YONG CASTILLO", "nombres": "JAVIER ENRIQUE"}, {"dni": "06052583", "apellidos": "CHIANG IJHII", "nombres": "JORGE DANIEL"}, {"dni": "47109621", "apellidos": "CHINGO TORRES", "nombres": "MERY"}, {"dni": "10093426", "apellidos": "CHOQUE CHAVEZ", "nombres": "JOSE LUIS"}, {"dni": "40735381", "apellidos": "CHUQUILLANQUI JIMENEZ", "nombres": "ROCIO LIZ"}, {"dni": "40536821", "apellidos": "CONTRERAS PEREZ", "nombres": "FELIPE MARTIN"}, {"dni": "10009531", "apellidos": "CORRALES MORMOMUY", "nombres": "GLORIA"}, {"dni": "43865295", "apellidos": "COTRINA TOCAS", "nombres": "MARIA MARUJA"}, {"dni": "25811108", "apellidos": "CURO GONZALES", "nombres": "FANIA AGUSTINA"}, {"dni": "43374114", "apellidos": "CURTI QUISPE", "nombres": "ROSARIO"}, {"dni": "41209087", "apellidos": "DA CRUZ AVALOS", "nombres": "ANA MARIA"}, {"dni": "42219912", "apellidos": "DA CRUZ AVALOS", "nombres": "IRMA ZORAIDA"}, {"dni": "06801838", "apellidos": "DELGADO FLORES", "nombres": "AQUILES INDOLECIO"}, {"dni": "06800411", "apellidos": "DELGADO MANRIQUE", "nombres": "DONALD AUGUSTO"}, {"dni": "09665179", "apellidos": "DIAZ ARCE", "nombres": "NOEMI DEL PILAR"}, {"dni": "09573336", "apellidos": "DOMINGUEZ GARCIA", "nombres": "BEATRIZ ELENA"}, {"dni": "10628856", "apellidos": "DURAND HUACHO", "nombres": "RINA YSABEL"}, {"dni": "18176315", "apellidos": "ELORREAGA ORBEGOSO", "nombres": "JOSE LUIS"}, {"dni": "40006376", "apellidos": "ESPINOZA VERDE", "nombres": "IGOR ROEL"}, {"dni": "07446361", "apellidos": "FIGUEROA ZAPATA", "nombres": "MARIA TERESA"}, {"dni": "07486618", "apellidos": "FLORES TIPIANI", "nombres": "DOMINGO MARTIN"}, {"dni": "27077268", "apellidos": "GARAY ROJAS", "nombres": "JOSE ALEXANDER"}, {"dni": "06195259", "apellidos": "GARCIA PINILLOS", "nombres": "CARLOS MANUEL"}, {"dni": "43591496", "apellidos": "GUERRA TORRES", "nombres": "ENRIQUE"}, {"dni": "06102936", "apellidos": "GUERRERO HOSORIO", "nombres": "DANTE DANIEL"}, {"dni": "10761071", "apellidos": "HERRERA ANTEZANA", "nombres": "JOEL JESUS"}, {"dni": "09378167", "apellidos": "HUAMANI CARDENAS", "nombres": "ROMAN ODON"}, {"dni": "43258609", "apellidos": "HUAMANI CLARES", "nombres": "GASPAR ARTURO"}, {"dni": "22079624", "apellidos": "HURTADO GARCIA", "nombres": "RICARDO MOISES"}, {"dni": "45265515", "apellidos": "IDROGO GONZALES", "nombres": "YONE MELVA"}, {"dni": "06666272", "apellidos": "JIRALDO GAMARRA", "nombres": "BORIS EDWIN"}, {"dni": "42953642", "apellidos": "JUCAN DIAZ", "nombres": "AINER"}, {"dni": "40771852", "apellidos": "LAGOS CUESTAS", "nombres": "DENICE KARINA"}, {"dni": "10090970", "apellidos": "LARA GELDRES", "nombres": "AURORA ROSARIO"}, {"dni": "44389016", "apellidos": "LAREDO CHAUCA", "nombres": "MERLENE JULIA"}, {"dni": "09353629", "apellidos": "LARTIGA COTERA", "nombres": "LUIS IGNACIO"}, {"dni": "45499415", "apellidos": "LAYA SOLANO", "nombres": "KATIA ESTHER"}, {"dni": "09452719", "apellidos": "LAYA SOLANO", "nombres": "MOISES MARTIN"}, {"dni": "07947351", "apellidos": "LENGUA CALLE", "nombres": "CARLOS IGNACIO"}, {"dni": "02578799", "apellidos": "LINARES CALDERON", "nombres": "ARTURO RAUL"}, {"dni": "10712861", "apellidos": "LLANOS ITURRIZAGA", "nombres": "RAUL ANDRE"}, {"dni": "10607659", "apellidos": "MANIÑAS AMESQUITA", "nombres": "JOSE"}, {"dni": "10120974", "apellidos": "MARTINEZ TELLO", "nombres": "ARMANDO JAVIER"}, {"dni": "32909376", "apellidos": "MEDINA SALVADOR", "nombres": "PEGUI"}, {"dni": "40166027", "apellidos": "MELGAR EGOAVIL", "nombres": "JOSE MANUEL"}, {"dni": "08072579", "apellidos": "MELGAR TIPISMANA", "nombres": "CARLOS ANTONIO"}, {"dni": "40435019", "apellidos": "MENDOZA DIAZ", "nombres": "GOUDI CRISTELL"}, {"dni": "32037431", "apellidos": "MENDRANO VILLANUEVA", "nombres": "MERI ZENAIDA"}, {"dni": "07537695", "apellidos": "MENENDEZ CASTILLO", "nombres": "RAMON FRANCISCO"}, {"dni": "09715716", "apellidos": "MOGROVEJO MEDINA", "nombres": "JULIO FRANCISCO"}, {"dni": "07716444", "apellidos": "MOLINA CARBAJAL", "nombres": "SIDNEY PAULINO"}, {"dni": "40628000", "apellidos": "MONTUFAR MEDINA", "nombres": "YIPSA"}, {"dni": "40219666", "apellidos": "MORIN NINA", "nombres": "ALEXANDER MOISES"}, {"dni": "09107787", "apellidos": "NALVARTE GIL", "nombres": "JOSE LUIS"}, {"dni": "10701261", "apellidos": "NEYRA DEL CARPIO", "nombres": "JHOE"}, {"dni": "42054053", "apellidos": "NOBLECILLA MIRANO", "nombres": "LEONARDO ERICK"}, {"dni": "46934895", "apellidos": "OCUPA CRUZ", "nombres": "MAYTHE"}, {"dni": "10841219", "apellidos": "ORBEGOSO VILCA", "nombres": "ROGER ALBERTO"}, {"dni": "72206838", "apellidos": "ORMEÑO ROMERO", "nombres": "CARLOS MANUEL ALAN"}, {"dni": "07926310", "apellidos": "PACHERRE CASTILLO", "nombres": "GERMAN MARTIN"}, {"dni": "10620355", "apellidos": "PALOMAREZ SARTOR", "nombres": "JANET NANOY"}, {"dni": "46488179", "apellidos": "PASTOR WIDDUP", "nombres": "MILUDY KATHERINE"}, {"dni": "07940013", "apellidos": "PATIÑO ZEGARRA", "nombres": "JUSTO ARMANDO"}, {"dni": "45880266", "apellidos": "PAZOS CASTRO", "nombres": "JUAN MANUEL"}, {"dni": "22303074", "apellidos": "PEBES MARCACOZCO", "nombres": "JUAN"}, {"dni": "08404425", "apellidos": "PEÑA CORDOVA", "nombres": "MARISABEL"}, {"dni": "25681905", "apellidos": "PERALTA GUERRERO", "nombres": "ELIZABETH GIANINA"}, {"dni": "47532199", "apellidos": "PEREZ VENTURIZO", "nombres": "LEYLA KARINA"}, {"dni": "32950345", "apellidos": "PIZARRO SANCHEZ", "nombres": "LUIS EMILIO"}, {"dni": "47268301", "apellidos": "PORTALES ARBUQUEQUE", "nombres": "MARIA SOLANCH"}, {"dni": "08716822", "apellidos": "PRADO BOCANGEL", "nombres": "ROXANA"}, {"dni": "06780430", "apellidos": "PRETEL PLASENCIA", "nombres": "SUSANA ELIZABETH"}, {"dni": "41297845", "apellidos": "PUENTE CONTRERAS", "nombres": "MYDORY MABEL"}, {"dni": "07495372", "apellidos": "PUENTE PUENTE", "nombres": "MARIA ELENA"}, {"dni": "08448343", "apellidos": "QUIROZ CIEZA", "nombres": "GUILLERMO"}, {"dni": "40614259", "apellidos": "QUISPE MOSCO", "nombres": "SONIA ISABEL"}, {"dni": "73797130", "apellidos": "QUISPE ROJAS", "nombres": "ROSA YASMIRA"}, {"dni": "80114899", "apellidos": "QUISPE VILLAGARAY", "nombres": "OSCAR ANTONIO"}, {"dni": "10007031", "apellidos": "RECARTE PERALES", "nombres": "SERGIO RICARDO"}, {"dni": "72555493", "apellidos": "REYES FUGUEROA", "nombres": "DANIEL ENRIQUE"}, {"dni": "47936177", "apellidos": "RODRIGUEZ PEREZ", "nombres": "LUIS ALBERTO"}, {"dni": "06666012", "apellidos": "ROJAS VELEZ", "nombres": "EMMA YRIS"}, {"dni": "40443125", "apellidos": "ROMERO SANCHEZ", "nombres": "VICTOR CARLOS"}, {"dni": "06696136", "apellidos": "RONDON NUÑEZ", "nombres": "RICARDO"}, {"dni": "08731096", "apellidos": "SALAZAR LAOS", "nombres": "JULIO CESAR"}, {"dni": "72707762", "apellidos": "SANCHEZ CHAVEZ", "nombres": "LUIS ENRIQUE"}, {"dni": "70465049", "apellidos": "SANCHEZ HERRERA", "nombres": "HENRY JUNIOR"}, {"dni": "40945960", "apellidos": "SANCHEZ MAQUIÑA", "nombres": "MANUEL ALEJANDRO"}, {"dni": "43618334", "apellidos": "SANTIAGO PEREZ", "nombres": "JOEL IVAN"}, {"dni": "07802984", "apellidos": "SOLARI PALET", "nombres": "CESAR FORTUNATO"}, {"dni": "40736188", "apellidos": "SOLORZANO CASTILLO", "nombres": "EDWIN CELSO"}, {"dni": "10091419", "apellidos": "SOTOMAYOR SANTOS", "nombres": "JORGE LUIS"}, {"dni": "40121439", "apellidos": "SUAREZ SUAREZ", "nombres": "ALAN PAUL"}, {"dni": "80538067", "apellidos": "SUAREZ SUAREZ", "nombres": "JORGE LUIS"}, {"dni": "10438279", "apellidos": "TINEO PILLACA", "nombres": "HECTOR ALBERTO"}, {"dni": "10738694", "apellidos": "TRUJILLO ORTEGA", "nombres": "GLENDA RITA"}, {"dni": "25745456", "apellidos": "VALENCIA TEJADA", "nombres": "HUGO OSCAR"}, {"dni": "40082765", "apellidos": "VARGAS MEJIA", "nombres": "ALEX ADRIAN"}, {"dni": "07276973", "apellidos": "VASQUEZ VASQUEZ", "nombres": "EDGAR"}, {"dni": "20118250", "apellidos": "YUNKOR ROMERO", "nombres": "YURELO"}, {"dni": "90881411", "apellidos": "ZAPATA GONSALEZ", "nombres": "FIORELLA"}, {"dni": "07736682", "apellidos": "ZARATE OLIVARI", "nombres": "VICTOR ADRIAN"}, {"dni": "06040557", "apellidos": "ZEGARRA MONTOYA", "nombres": "ALFREDO"}];
const CONTACTO_TEL = "987714309";
const CONTACTO_EMAIL = "sosalamedalimasur@gmail.com";
const APPS_SCRIPT_URL = "https://script.google.com/macros/s/AKfycbymkVA2Sm_w510seLTaqNnDs2cdDmm6pngfI5WP7K3wBMwWcy2IqC63YX5X80fs3CCv/exec";

function uid(p){ return p+"_"+Math.random().toString(36).slice(2,8); }
function val(id){ const el=document.getElementById(id); return el?el.value.trim():""; }

function verificarDniPadron(){
  const dniEl = document.getElementById("as_dni");
  const box = document.getElementById("as_padron_status");
  if(!dniEl || !box) return;
  const dni = dniEl.value.trim();
  if(dni.length < 8){ box.innerHTML=""; return; }
  const encontrado = PADRON.find(p => p.dni === dni.padStart(8,"0"));
  if(encontrado){
    box.innerHTML = '<div class="msg ok">✔ Estás registrado en el padrón como <strong>'+encontrado.apellidos+', '+encontrado.nombres+'</strong>. Verifica que tus datos estén correctos y actualízalos si hace falta.</div>';
    if(!val("as_nombres")) document.getElementById("as_nombres").value = encontrado.nombres;
    if(!val("as_apellidos")) document.getElementById("as_apellidos").value = encontrado.apellidos;
  } else {
    box.innerHTML = '<div class="msg err">No encontramos ese DNI en el padrón de asociados. Si eres nuevo o el dato está mal registrado, completa tus datos igual y usa "Actualiza tus datos padrón" para el registro completo.</div>';
  }
}
function telefonoWa(tel){
  const d = String(tel||"").replace(/\D/g,"");
  if(!d) return null;
  return d.length===9 ? "51"+d : d;
}

/* ---- Segmentos ---- */
document.getElementById("seg").addEventListener("click", e=>{
  const b = e.target.closest("button"); if(!b) return;
  document.querySelectorAll("#seg button").forEach(x=>x.classList.remove("active"));
  b.classList.add("active");
  document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
  document.getElementById("sec-"+b.dataset.s).classList.add("active");
});

/* ---- Dependientes ---- */
function filaDep(d){
  d = d || {};
  return `<div class="rep-row">
    <input type="text" class="dep-nombre" placeholder="Nombre">
    <select class="dep-sexo narrow"><option value="">Sexo</option><option value="F">F</option><option value="M">M</option></select>
    <input type="date" class="dep-fecha" style="flex:0 0 130px;">
    <select class="dep-parentesco" style="flex:0 0 130px;"><option>Hijo/a</option><option>Otro dependiente</option></select>
    <button type="button" onclick="this.closest('.rep-row').remove()">✕</button>
  </div>`;
}
function agregarDependiente(){ document.getElementById("as_dependientesList").insertAdjacentHTML("beforeend", filaDep()); }
function leerDependientes(){
  return Array.from(document.querySelectorAll("#as_dependientesList .rep-row")).map(r=>({
    nombre:r.querySelector(".dep-nombre").value.trim(),
    sexo:r.querySelector(".dep-sexo").value,
    fecha:r.querySelector(".dep-fecha").value,
    parentesco:r.querySelector(".dep-parentesco").value
  })).filter(d=>d.nombre);
}

/* ---- Vehículos ---- */
function filaVeh(){
  return `<div class="rep-row">
    <input type="text" class="veh-placa" placeholder="Placa">
    <input type="text" class="veh-marca" placeholder="Marca">
    <input type="text" class="veh-color" placeholder="Color">
    <select class="veh-tipo" style="flex:0 0 110px;"><option>Auto</option><option>Camioneta</option><option>Camión</option><option>Moto</option><option>Otro</option></select>
    <button type="button" onclick="this.closest('.rep-row').remove()">✕</button>
  </div>`;
}
function agregarVehiculo(){ document.getElementById("cn_vehiculosList").insertAdjacentHTML("beforeend", filaVeh()); }
function leerVehiculos(){
  return Array.from(document.querySelectorAll("#cn_vehiculosList .rep-row")).map(r=>({
    placa:r.querySelector(".veh-placa").value.trim(), marca:r.querySelector(".veh-marca").value.trim(),
    color:r.querySelector(".veh-color").value.trim(), tipo:r.querySelector(".veh-tipo").value
  })).filter(v=>v.placa||v.marca);
}

/* ---- Mascotas ---- */
function toggleMascotas(){
  const si = document.getElementById("cn_mascotas").value==="Si";
  document.getElementById("cn_mascotasWrap").style.display = si?"block":"none";
  if(si && !document.getElementById("cn_mascotasList").children.length) agregarMascota();
}
function filaMas(){
  return `<div class="rep-row">
    <input type="text" class="mas-nombre" placeholder="Nombre">
    <input type="text" class="mas-raza" placeholder="Raza">
    <select class="mas-sexo narrow"><option value="">Sexo</option><option>Macho</option><option>Hembra</option></select>
    <input type="number" class="mas-anios narrow" placeholder="Años" min="0">
    <input type="number" class="mas-meses narrow" placeholder="Meses" min="0" max="11">
    <select class="mas-ester" style="flex:0 0 110px;"><option value="">¿Esteriliz.?</option><option value="Si">Sí</option><option value="No">No</option></select>
    <select class="mas-tenencia" style="flex:1 1 180px;">
      <option>Mascota de compañía propia</option><option>Can comunitario / vecinal</option><option>Can callejero sin soporte</option>
    </select>
    <button type="button" onclick="this.closest('.rep-row').remove()">✕</button>
  </div>`;
}
function agregarMascota(){ document.getElementById("cn_mascotasList").insertAdjacentHTML("beforeend", filaMas()); }
function edadTxt(a,m){
  const p=[]; if(a) p.push(a+"a"); if(m) p.push(m+"m");
  return p.length?p.join(" "):"edad s/d";
}
function leerMascotas(){
  return Array.from(document.querySelectorAll("#cn_mascotasList .rep-row")).map(r=>({
    nombre:r.querySelector(".mas-nombre").value.trim(), raza:r.querySelector(".mas-raza").value.trim(),
    sexo:r.querySelector(".mas-sexo").value, anios:r.querySelector(".mas-anios").value, meses:r.querySelector(".mas-meses").value,
    ester:r.querySelector(".mas-ester").value, tenencia:r.querySelector(".mas-tenencia").value
  })).filter(m=>m.nombre);
}

/* ---- Contactos de emergencia (máx 3) ---- */
function filaCon(){
  return `<div class="rep-row">
    <select class="con-rel narrow"><option value="">Relación</option><option>Papá</option><option>Mamá</option><option>Esposo/a</option><option>Hijo/a</option><option>Amigo/a</option><option>Otro</option></select>
    <input type="text" class="con-nombre" placeholder="Nombres y apellidos">
    <input type="text" class="con-tel1" placeholder="Teléfono 1">
    <input type="text" class="con-tel2" placeholder="Teléfono 2 (opcional)">
    <button type="button" onclick="this.closest('.rep-row').remove(); actualizarBtnContacto();">✕</button>
  </div>`;
}
function agregarContacto(){
  if(document.querySelectorAll("#cn_contactosList .rep-row").length>=3) return;
  document.getElementById("cn_contactosList").insertAdjacentHTML("beforeend", filaCon());
  actualizarBtnContacto();
}
function actualizarBtnContacto(){
  const n = document.querySelectorAll("#cn_contactosList .rep-row").length;
  document.getElementById("btnAddContacto").style.display = n>=3?"none":"block";
}
function leerContactos(){
  return Array.from(document.querySelectorAll("#cn_contactosList .rep-row")).map(r=>({
    rel:r.querySelector(".con-rel").value, nombre:r.querySelector(".con-nombre").value.trim(),
    tel1:r.querySelector(".con-tel1").value.trim(), tel2:r.querySelector(".con-tel2").value.trim()
  })).filter(c=>c.nombre||c.tel1);
}

/* ---- Mensajes ---- */
function construirMensajeDatos(){
  const dep = leerDependientes();
  const lines = [
    "ACTUALIZACIÓN DE DATOS — Asociación Alameda Lima Sur",
    "DNI: "+val("as_dni"), "Nombres: "+val("as_nombres"), "Apellidos: "+val("as_apellidos"),
    "Teléfono: "+val("as_telefono"), "Email: "+val("as_email"), "Dirección: "+val("as_direccion"),
    "Etapa/Mz/Lote: "+val("as_etapa")+" / "+val("as_manzana")+" / "+val("as_lote")
  ];
  if(val("as_conyugeNombre")) lines.push("Cónyuge: "+val("as_conyugeNombre")+" (DNI "+val("as_conyugeDni")+")");
  if(dep.length) lines.push("Hijos/dependientes: "+dep.map(d=>`${d.nombre} (${d.sexo||"?"}, ${d.fecha||"s/fecha"}, ${d.parentesco})`).join("; "));
  return lines.join("\n");
}
function construirMensajeCenso(){
  const veh=leerVehiculos(), mas=leerMascotas(), con=leerContactos();
  const aportesMap = {cn_apVigilancia:"Vigilancia", cn_apAlarma:"Alarma vecinal", cn_apCamaras:"Cámaras", cn_apGestion:"Gestión", cn_apMoto:"Moto eléctrica"};
  const aportesSi = Object.entries(aportesMap).filter(([id])=>document.getElementById(id).checked).map(([,l])=>l);
  const motivoNo = document.getElementById("cn_motivoNo").value==="Otro" ? val("cn_motivoNoOtro") : document.getElementById("cn_motivoNo").value;
  const lines = [
    "FICHA DE CENSO — Urb. La Alameda Lima Sur",
    "Sector: "+val("cn_sector"), "DNI: "+val("cn_dni"), "Nombres: "+val("cn_nombres"), "Apellidos: "+val("cn_apellidos"),
    "Teléfono: "+val("cn_telefono")+(val("cn_telefonoAlt")?" / "+val("cn_telefonoAlt"):""), "Email: "+val("cn_email"),
    "Etapa/Calle/Mz/Lote: "+val("cn_etapa")+" / "+val("cn_calle")+" / "+val("cn_manzana")+" / "+val("cn_lote"),
    "Condición propiedad: "+val("cn_condicionPropiedad"), "Condición predio: "+val("cn_condicionPredio"),
    "Luz/Agua: "+val("cn_luz")+" / "+val("cn_agua"), "N° partida SUNARP: "+(val("cn_partidaSunarp")||"no indica"), "N° personas: "+val("cn_personas"),
    "Vehículos: "+(veh.length? veh.map(v=>`${v.placa||"s/placa"} ${v.tipo} ${v.marca} ${v.color}`).join("; "):"ninguno"),
    "Mascotas: "+(mas.length? mas.map(m=>`${m.nombre} (${m.raza||"s/raza"}, ${m.sexo||"?"}, ${edadTxt(m.anios,m.meses)}, ester.: ${m.ester||"?"}, ${m.tenencia})`).join("; ") : (val("cn_mascotas")==="Si"?"marcó que sí, sin detalle":"no tiene")),
    "Contactos emergencia: "+(con.length? con.map(c=>`${c.rel||"?"}: ${c.nombre} (${[c.tel1,c.tel2].filter(Boolean).join(" / ")})`).join("; "):"ninguno"),
    "¿Desea asociarse?: "+val("cn_desea")+(motivoNo?" — "+motivoNo:""),
    "Estaría de acuerdo en aportar para: "+(aportesSi.length?aportesSi.join(", "):"ninguno"),
    "¿Participaría en jornadas de recaudación?: "+val("cn_jornadas"),
    "Deportes de preferencia: "+deportesTxt()
  ];
  return lines.join("\n");
}
function deportesTxt(){
  const m = {cn_depFulbito:"Fulbito", cn_depFutbol:"Fútbol", cn_depVoley:"Vóley", cn_depBasquet:"Básquet", cn_depNatacion:"Natación"};
  const list = Object.entries(m).filter(([id])=>document.getElementById(id).checked).map(([,l])=>l);
  if(document.getElementById("cn_depOtroCheck").checked && val("cn_depOtro")) list.push(val("cn_depOtro"));
  return list.length ? list.join(", ") : "ninguna marcada";
}

/* ---- Guardado automático en Google Sheets ---- */
function construirPayloadDatos(){
  const dep = leerDependientes();
  return {
    tipo: "datos",
    dni: val("as_dni"), nombres: val("as_nombres"), apellidos: val("as_apellidos"),
    telefono: val("as_telefono"), email: val("as_email"), direccion: val("as_direccion"),
    etapa: val("as_etapa"), manzana: val("as_manzana"), lote: val("as_lote"),
    conyugeNombre: val("as_conyugeNombre"), conyugeDni: val("as_conyugeDni"),
    dependientes: dep.length ? dep.map(d=>`${d.nombre} (${d.sexo||"?"}, ${d.fecha||"s/fecha"}, ${d.parentesco})`).join("; ") : ""
  };
}
function construirPayloadCenso(){
  const veh=leerVehiculos(), mas=leerMascotas(), con=leerContactos();
  const aportesMap = {cn_apVigilancia:"Vigilancia", cn_apAlarma:"Alarma vecinal", cn_apCamaras:"Cámaras", cn_apGestion:"Gestión", cn_apMoto:"Moto eléctrica"};
  const aportesSi = Object.entries(aportesMap).filter(([id])=>document.getElementById(id).checked).map(([,l])=>l);
  const motivoNo = document.getElementById("cn_motivoNo").value==="Otro" ? val("cn_motivoNoOtro") : document.getElementById("cn_motivoNo").value;
  return {
    tipo: "censo",
    sector: val("cn_sector"), dni: val("cn_dni"), nombres: val("cn_nombres"), apellidos: val("cn_apellidos"),
    telefono: val("cn_telefono"), telefonoAlt: val("cn_telefonoAlt"), email: val("cn_email"),
    etapa: val("cn_etapa"), calle: val("cn_calle"), manzana: val("cn_manzana"), lote: val("cn_lote"),
    condicionPropiedad: val("cn_condicionPropiedad"), condicionPredio: val("cn_condicionPredio"),
    luz: val("cn_luz"), agua: val("cn_agua"), partidaSunarp: val("cn_partidaSunarp"), personas: val("cn_personas"),
    vehiculos: veh.length? veh.map(v=>`${v.placa||"s/placa"} ${v.tipo} ${v.marca} ${v.color}`).join("; "):"",
    mascotas: mas.length? mas.map(m=>`${m.nombre} (${m.raza||"s/raza"}, ${m.sexo||"?"}, ${edadTxt(m.anios,m.meses)}, ester.: ${m.ester||"?"}, ${m.tenencia})`).join("; ") : "",
    contactosEmergencia: con.length? con.map(c=>`${c.rel||"?"}: ${c.nombre} (${[c.tel1,c.tel2].filter(Boolean).join(" / ")})`).join("; "):"",
    desea: val("cn_desea"), motivoNo: motivoNo||"",
    aportes: aportesSi.length?aportesSi.join(", "):"",
    jornadas: val("cn_jornadas"),
    deportes: deportesTxt()
  };
}
let datosGuardadoEnHoja = false;
let censoGuardadoEnHoja = false;
async function guardarEnHoja(payload){
  if(!APPS_SCRIPT_URL) return "no-configurado";
  if(payload.tipo==="datos"){ if(datosGuardadoEnHoja) return "ya-guardado"; datosGuardadoEnHoja = true; }
  if(payload.tipo==="censo"){ if(censoGuardadoEnHoja) return "ya-guardado"; censoGuardadoEnHoja = true; }
  try{
    await fetch(APPS_SCRIPT_URL, { method:"POST", mode:"no-cors", body: JSON.stringify(payload) });
    return "ok";
  }catch(e){
    console.error("No se pudo guardar en la hoja de cálculo", e);
    if(payload.tipo==="datos") datosGuardadoEnHoja = false;
    if(payload.tipo==="censo") censoGuardadoEnHoja = false;
    return "error";
  }
}
document.getElementById("sec-datos").addEventListener("input", function(){ datosGuardadoEnHoja = false; setBotonesHabilitados("as", true); });
document.getElementById("as_dni").addEventListener("input", verificarDniPadron);
document.getElementById("as_dni").addEventListener("blur", verificarDniPadron);
document.getElementById("sec-censo").addEventListener("input", function(){ censoGuardadoEnHoja = false; setBotonesHabilitados("cn", true); });
function setBotonesHabilitados(prefijo, habilitado){
  document.querySelectorAll('#sec-'+(prefijo==="as"?"datos":"censo")+' .btn').forEach(function(b){ b.disabled = !habilitado; });
}

/* ---- Envíos ---- */
function textoGuardado(estado){
  if(estado==="ok") return " ✓ Registrado en la hoja de cálculo.";
  if(estado==="ya-guardado") return " (ya estaba registrado en la hoja).";
  if(estado==="error") return " ⚠ No se pudo registrar en la hoja de cálculo — avisa al Consejo Directivo.";
  return "";
}
async function enviarDatosWhatsapp(){
  if(!val("as_nombres")||!val("as_dni")){ document.getElementById("as_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("as_consiento").checked){ document.getElementById("as_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("as", false);
  const estado = await guardarEnHoja(construirPayloadDatos());
  window.open(`https://wa.me/${telefonoWa(CONTACTO_TEL)}?text=${encodeURIComponent(construirMensajeDatos())}`, "_blank");
  document.getElementById("as_msg").innerHTML='<div class="msg ok">Intentamos abrir WhatsApp. Si no pasó nada, usa "Copiar mensaje" abajo y pégalo donde puedas enviarlo.'+textoGuardado(estado)+'</div>';
  if(estado==="error") setBotonesHabilitados("as", true);
}
async function enviarDatosCorreo(){
  if(!val("as_nombres")||!val("as_dni")){ document.getElementById("as_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("as_consiento").checked){ document.getElementById("as_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("as", false);
  const estado = await guardarEnHoja(construirPayloadDatos());
  const asunto = "Verificación de empadronamiento - "+val("as_nombres")+" "+val("as_apellidos");
  window.open(`mailto:${encodeURIComponent(CONTACTO_EMAIL)}?subject=${encodeURIComponent(asunto)}&body=${encodeURIComponent(construirMensajeDatos())}`, "_blank");
  document.getElementById("as_msg").innerHTML='<div class="msg ok">Intentamos abrir tu correo. Si no pasó nada, usa "Copiar mensaje" abajo y pégalo donde puedas enviarlo.'+textoGuardado(estado)+'</div>';
  if(estado==="error") setBotonesHabilitados("as", true);
}
async function enviarCensoWhatsapp(){
  if(!val("cn_nombres")||!val("cn_dni")){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("cn_consiento").checked){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("cn", false);
  const estado = await guardarEnHoja(construirPayloadCenso());
  window.open(`https://wa.me/${telefonoWa(CONTACTO_TEL)}?text=${encodeURIComponent(construirMensajeCenso())}`, "_blank");
  document.getElementById("cn_msg").innerHTML='<div class="msg ok">Intentamos abrir WhatsApp. Si no pasó nada, usa "Copiar mensaje" abajo y pégalo donde puedas enviarlo.'+textoGuardado(estado)+'</div>';
  if(estado==="error") setBotonesHabilitados("cn", true);
}
async function enviarCensoCorreo(){
  if(!val("cn_nombres")||!val("cn_dni")){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("cn_consiento").checked){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("cn", false);
  const estado = await guardarEnHoja(construirPayloadCenso());
  const asunto = "Actualiza tus datos padrón - "+val("cn_nombres")+" "+val("cn_apellidos");
  window.open(`mailto:${encodeURIComponent(CONTACTO_EMAIL)}?subject=${encodeURIComponent(asunto)}&body=${encodeURIComponent(construirMensajeCenso())}`, "_blank");
  document.getElementById("cn_msg").innerHTML='<div class="msg ok">Intentamos abrir tu correo. Si no pasó nada, usa "Copiar mensaje" abajo y pégalo donde puedas enviarlo.'+textoGuardado(estado)+'</div>';
  if(estado==="error") setBotonesHabilitados("cn", true);
}
async function copiarAlPortapapeles(texto, msgElId, sufijo){
  try{
    await navigator.clipboard.writeText(texto);
    document.getElementById(msgElId).innerHTML = '<div class="msg ok">✓ Mensaje copiado. Pégalo (mantén presionado y elige "Pegar") en WhatsApp, correo o donde prefieras enviarlo.'+(sufijo||"")+'</div>';
  }catch(e){
    document.getElementById(msgElId).innerHTML = '<div class="msg err">No se pudo copiar automáticamente. Mantén presionado el mensaje de más abajo para copiarlo manualmente.</div>';
  }
}
async function copiarDatos(){
  if(!val("as_nombres")||!val("as_dni")){ document.getElementById("as_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("as_consiento").checked){ document.getElementById("as_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("as", false);
  const estado = await guardarEnHoja(construirPayloadDatos());
  await copiarAlPortapapeles(construirMensajeDatos(), "as_msg", textoGuardado(estado));
  if(estado==="error") setBotonesHabilitados("as", true);
}
async function copiarCenso(){
  if(!val("cn_nombres")||!val("cn_dni")){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Ingresa al menos tu nombre y tu DNI.</div>'; return; }
  if(!document.getElementById("cn_consiento").checked){ document.getElementById("cn_msg").innerHTML='<div class="msg err">Debes autorizar el uso de tus datos personales.</div>'; return; }
  setBotonesHabilitados("cn", false);
  const estado = await guardarEnHoja(construirPayloadCenso());
  await copiarAlPortapapeles(construirMensajeCenso(), "cn_msg", textoGuardado(estado));
  if(estado==="error") setBotonesHabilitados("cn", true);
}
</script>
</body>
</html>
