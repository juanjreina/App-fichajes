<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control de Jornada Histórico</title>
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <style>
        :root {
            --bg-color: #121212;
            --card-bg: #1e1e1e;
            --text-color: #e0e0e0;
            --accent-color: #3b82f6;
            --success-color: #10b981;
            --danger-color: #ef4444;
            --border-color: #333;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .container {
            width: 100%;
            max-width: 450px;
        }

        h1 {
            text-align: center;
            font-size: 1.3rem;
            margin-bottom: 15px;
            color: #fff;
        }

        .card {
            background: var(--card-bg);
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
        }

        .date-picker-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 10px;
        }

        input[type="date"] {
            background: #2b2b2b;
            border: 1px solid #444;
            color: #fff;
            padding: 10px;
            border-radius: 8px;
            font-size: 1rem;
            flex: 1;
            text-align: center;
        }

        .progress-container {
            margin: 10px 0;
            background: #333;
            border-radius: 10px;
            overflow: hidden;
            height: 20px;
            position: relative;
        }

        .progress-bar {
            background: var(--accent-color);
            height: 100%;
            width: 0%;
            transition: width 0.3s;
        }

        .progress-text {
            position: absolute;
            width: 100%;
            text-align: center;
            font-size: 0.8rem;
            font-weight: bold;
            line-height: 20px;
            color: #fff;
        }

        .tramo-row {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
            padding-bottom: 10px;
            border-bottom: 1px solid #2a2a2a;
        }

        .tramo-row:last-child {
            border-bottom: none;
            margin-bottom: 0;
        }

        input[type="time"] {
            background: #2b2b2b;
            border: 1px solid #444;
            color: #fff;
            padding: 8px;
            border-radius: 5px;
            font-size: 0.95rem;
            width: 85px;
            text-align: center;
        }

        .btn-icon {
            background: none;
            border: none;
            font-size: 1.2rem;
            cursor: pointer;
            padding: 5px;
        }

        .btn-add {
            width: 100%;
            padding: 10px;
            background: #2b2b2b;
            color: var(--accent-color);
            border: 1px dashed var(--accent-color);
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 5px;
        }

        .section-title {
            font-size: 0.9rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: #888;
            margin-bottom: 10px;
            font-weight: 600;
        }

        .summary-text {
            display: flex;
            justify-content: space-between;
            font-size: 1rem;
            margin: 5px 0;
        }

        .info-semana {
            font-size: 0.8rem;
            color: #888;
            text-align: center;
            margin-top: -5px;
            margin-bottom: 15px;
        }

        .backup-zone {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .btn-backup {
            flex: 1;
            padding: 8px;
            background: #252525;
            color: #aaa;
            border: 1px solid #333;
            border-radius: 6px;
            font-size: 0.75rem;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>📅 Control de Jornada Real</h1>

    <div class="card">
        <div class="section-title">Seleccionar Fecha</div>
        <div class="date-picker-container">
            <input type="date" id="fechaActual" onchange="cambiarFecha()">
        </div>
    </div>

    <div class="card">
        <div class="section-title" id="tituloSemana">Resumen Semanal</div>
        <div class="info-semana" id="rangoSemana">(Lun -- a Dom --)</div>
        <div class="summary-text">
            <span>Total trabajado:</span>
            <strong id="totalSemana">0h 00m</strong>
        </div>
        <div class="summary-text">
            <span>Estado (Objetivo 35h):</span>
            <strong id="estadoSemana" style="color: var(--accent-color);">35h 00m restantes</strong>
        </div>
        <div class="progress-container">
            <div class="progress-bar" id="progressBar"></div>
            <div class="progress-text" id="progressPct">0%</div>
        </div>
    </div>

    <div class="card">
        <div class="section-title" style="display:flex; justify-content:space-between;">
            <span>Fichajes del día</span>
            <span id="totalDia" style="color: var(--success-color); font-weight: bold;">Total: 0h 00m</span>
        </div>
        <div id="tramosContenedor"></div>
        <button class="btn-add" onclick="agregarTramoVacio()">➕ Añadir Tramo (Entrada/Salida)</button>
    </div>

    <div class="backup-zone">
        <button class="btn-backup" onclick="exportarDatos()">📥 Copia de Seguridad</button>
        <button class="btn-backup" onclick="importarDatos()">📤 Restaurar Datos</button>
    </div>
</div>

<script>
    const OBJETIVO_SEMANAL = 35;
    let baseDatos = JSON.parse(localStorage.getItem('registro_calendario_v2')) || {};

    function establecerFechaDeHoy() {
        const hoy = new Date();
        const offset = hoy.getTimezoneOffset();
        const hoyCorregido = new Date(hoy.getTime() - (offset * 60 * 1000));
        document.getElementById('fechaActual').value = hoyCorregido.toISOString().split('T')[0];
    }

    function inicializar() {
        if (!document.getElementById('fechaActual').value) {
            establecerFechaDeHoy();
        }
        cargarDiaActual();
    }

    function cambiarFecha() {
        cargarDiaActual();
    }

    function cargarDiaActual() {
        const fecha = document.getElementById('fechaActual').value;
        const contenedor = document.getElementById('tramosContenedor');
        contenedor.innerHTML = '';

        const tramos = baseDatos[fecha] || [];

        if (tramos.length === 0) {
            contenedor.innerHTML = '<div style="text-align:center; color:#666; font-size:0.9rem; padding: 10px 0;">No hay fichajes registrados para este día.</div>';
        } else {
            tramos.forEach((tramo, index) => {
                const div = document.createElement('div');
                div.className = 'tramo-row';
                div.innerHTML = `
                    <input type="time" value="${tramo.entrada || ''}" onchange="actualizarTramo(${index}, 'entrada', this.value)">
                    <span>a</span>
                    <input type="time" value="${tramo.salida || ''}" onchange="actualizarTramo(${index}, 'salida', this.value)">
                    <button class="btn-icon" onclick="eliminarTramo(${index})">❌</button>
                `;
                contenedor.appendChild(div);
            });
        }

        calcularMetricas(fecha);
    }

    function agregarTramoVacio() {
        const fecha = document.getElementById('fechaActual').value;
        if (!baseDatos[fecha]) baseDatos[fecha] = [];
        baseDatos[fecha].push({ entrada: '', salida: '' });
        guardarYActualizar();
    }

    function actualizarTramo(index, tipo, valor) {
        const fecha = document.getElementById('fechaActual').value;
        baseDatos[fecha][index][tipo] = valor;
        guardarYActualizar();
    }

    function eliminarTramo(index) {
        const fecha = document.getElementById('fechaActual').value;
        baseDatos[fecha].splice(index, 1);
        if (baseDatos[fecha].length === 0) delete baseDatos[fecha];
        guardarYActualizar();
    }

    function guardarYActualizar() {
        localStorage.setItem('registro_calendario_v2', JSON.stringify(baseDatos));
        cargarDiaActual();
    }

    function obtenerLunesYDomingo(fechaStr) {
        const fecha = new Date(fechaStr + 'T00:00:00');
        const diaSemana = fecha.getDay();
        const distanciaAlLunes = diaSemana === 0 ? -6 : 1 - diaSemana;
        const lunes = new Date(fecha);
        lunes.setDate(fecha.getDate() + distanciaAlLunes);
        const domingo = new Date(lunes);
        domingo.setDate(lunes.getDate() + 6);
        return { lunes, domingo };
    }

    function formatearFechaCorta(date) {
        return `${date.getDate().toString().padStart(2, '0')}/${(date.getMonth() + 1).toString().padStart(2, '0')}`;
    }

    function obtenerMinutosEntreHoras(entrada, salida) {
        if (!entrada || !salida) return 0;
        const [hIn, mIn] = entrada.split(':').map(Number);
        const [hOut, mOut] = salida.split(':').map(Number);
        let minIn = hIn * 60 + mIn;
        let minOut = hOut * 60 + mOut;
        if (minOut < minIn) minOut += 24 * 60;
        return minOut - minIn;
    }

    function calcularMetricas(fechaSeleccionada) {
        let minutosDia = 0;
        if (baseDatos[fechaSeleccionada]) {
            baseDatos[fechaSeleccionada].forEach(t => {
                minutosDia += obtenerMinutosEntreHoras(t.entrada, t.salida);
            });
        }
        const hDia = Math.floor(minutosDia / 60);
        const mDia = minutosDia % 60;
        document.getElementById('totalDia').innerText = `Total: ${hDia}h ${mDia.toString().padStart(2, '0')}m`;

        const { lunes, domingo } = obtenerLunesYDomingo(fechaSeleccionada);
        document.getElementById('rangoSemana').innerText = `Semana del ${formatearFechaCorta(lunes)} al ${formatearFechaCorta(domingo)}`;

        let minutosSemana = 0;
        let diaBucle = new Date(lunes);
        for (let i = 0; i < 7; i++) {
            const ISOStr = diaBucle.toISOString().split('T')[0];
            if (baseDatos[ISOStr]) {
                baseDatos[ISOStr].forEach(t => {
                    minutosSemana += obtenerMinutosEntreHoras(t.entrada, t.salida);
                });
            }
            diaBucle.setDate(diaBucle.getDate() + 1);
        }

        const hSem = Math.floor(minutosSemana / 60);
        const mSem = minutosSemana % 60;
        document.getElementById('totalSemana').innerText = `${hSem}h ${mSem.toString().padStart(2, '0')}m`;

        const faltanMinutos = (OBJETIVO_SEMANAL * 60) - minutosSemana;
        const estadoLabel = document.getElementById('estadoSemana');

        if (faltanMinutos > 0) {
            const hFaltan = Math.floor(faltanMinutos / 60);
            const mFaltan = faltanMinutos % 60;
            estadoLabel.innerText = `Faltan ${hFaltan}h ${mFaltan.toString().padStart(2, '0')}m`;
            estadoLabel.style.color = 'var(--accent-color)';
        } else if (faltanMinutos === 0) {
            estadoLabel.innerText = '¡Objetivo 35h cumplido! 🎉';
            estadoLabel.style.color = 'var(--success-color)';
        } else {
            const extraMinutos = Math.abs(faltanMinutos);
            const hExtra = Math.floor(extraMinutos / 60);
            const mExtra = extraMinutos % 60;
            estadoLabel.innerText = `Horas Extra: +${hExtra}h ${mExtra.toString().padStart(2, '0')}m`;
            estadoLabel.style.color = 'var(--success-color)';
        }

        let porcentaje = ((minutosSemana / 60) / OBJETIVO_SEMANAL) * 100;
        if (porcentaje > 100) porcentaje = 100;
        document.getElementById('progressBar').style.width = `${porcentaje}%`;
        document.getElementById('progressPct').innerText = `${Math.floor(porcentaje)}%`;
    }

    function exportarDatos() {
        const datosTexto = JSON.stringify(baseDatos);
        navigator.clipboard.writeText(datosTexto).then(() => {
            alert('¡Copia de seguridad copiada al portapapeles! Guárdala en tus notas o envíatela por mensaje.');
        }).catch(() => {
            alert('No se pudo copiar automáticamente. Aquí tienes tus datos:\n\n' + datosTexto);
        });
    }

    function importarDatos() {
        const texto = prompt('Pega aquí el texto de tu copia de seguridad anterior:');
        if (texto) {
            try {
                const json = JSON.parse(texto);
                if (typeof json === 'object') {
                    baseDatos = json;
                    localStorage.setItem('registro_calendario_v2', JSON.stringify(baseDatos));
                    inicializar();
                    alert('¡Datos restaurados con éxito!');
                }
            } catch(e) {
                alert('Error: El texto introducido no es válido.');
            }
        }
    }

    window.onload = inicializar;
</script>
</body>
</html>
