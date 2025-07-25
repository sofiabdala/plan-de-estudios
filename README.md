<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Diseño Gráfico</title>
  <style>
    body {
      font-family: sans-serif;
      background: #fffff3;
      color: #222;
      margin: 0;
      padding: 0;
    }
    h1 {
      margin: 16px 0;
      text-align: center;
      color: #348dad;
      font-size: 2em;
      background: #deecff;
      border-radius: 12px;
      padding: 10px 0;
      box-shadow: 0 2px 12px #deecff;
    }
    #reiniciar {
      display: block;
      margin: 0 auto 18px auto;
      padding: 8px 18px;
      background: #a3d1e8;
      border: none;
      border-radius: 4px;
      color: #222;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0 2px 8px #deecff;
      transition: background 0.2s, color 0.2s;
    }
    #reiniciar:hover {
      background: #deecff;
      color: #348dad;
    }
    #malla {
      display: flex;
      flex-wrap: wrap;
      gap: 24px;
      justify-content: center;
      margin-bottom: 24px;
    }
    .año-columna {
      background: #f4fbfd;
      border-radius: 12px;
      box-shadow: 0 2px 12px #deecff;
      padding: 18px 16px 16px 16px;
      min-width: 220px;
      flex: 1 1 220px;
      display: flex;
      flex-direction: column;
      align-items: center;
      border: 2px solid #deecff;
    }
    .titulo-año {
      font-size: 1.15em;
      font-weight: bold;
      margin-bottom: 12px;
      color: #348dad;
      text-align: center;
      background: #deecff;
      border-radius: 8px;
      padding: 6px 0;
      width: 100%;
      box-shadow: 0 1px 6px #a3d1e8;
    }
    .materias-lista {
      display: flex;
      flex-direction: column;
      gap: 7px;
      width: 100%;
    }
    .materia {
      padding: 9px 10px;
      border: 2px solid #348dad;
      border-radius: 6px;
      background: #e8f4fa;
      color: #222;
      cursor: pointer;
      transition: background 0.15s, box-shadow 0.2s;
      font-size: 0.98em;
      box-shadow: 0 1px 4px #deecff;
      user-select: none;
    }
    .materia:hover:not(.bloqueada):not(.completada):not(.requisito-no) {
      background: #deecff;
      box-shadow: 0 2px 8px #a3d1e8;
    }
    .completada {
      text-decoration: line-through;
      background: #a3d1e8;
      color: #6c757d;
      border-color: #deecff;
    }
    .bloqueada {
      opacity: 0.6;
      pointer-events: none;
      background: #e0e0e0;
      color: #aaa;
      border-color: #deecff;
    }
    .requisito-no {
      cursor: not-allowed;
      opacity: 0.5;
    }
    #contador {
      text-align: center;
      font-weight: bold;
      margin-top: 10px;
      margin-bottom: 4px;
      background: #deecff;
      border-radius: 6px;
      display: inline-block;
      padding: 4px 16px;
      box-shadow: 0 1px 4px #a3d1e8;
    }
    #listaCompletadas {
      margin-top: 8px;
      text-align: center;
      padding-left: 0;
      list-style: none;
      font-size: 0.98em;
    }
    #listaCompletadas li {
      background: #deecff;
      margin: 3px 0;
      border-radius: 4px;
      display: inline-block;
      padding: 2px 8px;
      color: #348dad;
    }
    .opcion-exclusiva {
      display: flex;
      gap: 10px;
      margin-bottom: 7px;
      justify-content: center;
    }
    .cuadro-electivas {
      max-width: 720px;
      margin: 40px auto 24px auto;
    }
    .cuadro-electivas-title {
      background:#deecff;
      font-weight:bold;
      text-align:center;
      padding:8px 0;
      border-radius:4px;
      border:1px solid #b0cadd;
      margin-bottom:0;
      margin-top: 36px;
    }
    .materias-lista-final {
      display: flex;
      flex-direction: column;
      gap: 7px;
      width: 100%;
      margin-bottom: 18px;
      margin-top: 0;
    }
    @media (max-width: 900px) {
      #malla {
        flex-direction: column;
        align-items: center;
      }
      .año-columna {
        width: 95vw;
        min-width: unset;
      }
      .cuadro-electivas {
        width: 99vw;
        min-width: unset;
      }
    }
  </style>
</head>
<body>
  <h1>Diseño Gráfico</h1>
  <button id="reiniciar">Reiniciar progreso</button>
  <div id="contador"></div>
  <ul id="listaCompletadas"></ul>
  <div id="malla">
    <div class="año-columna">
      <div class="titulo-año">CBC</div>
      <div class="materias-lista">
        <div class="materia" data-id="IPC" data-prerequisitos="">Introducción al Pensamiento Científico (CBC)</div>
        <div class="materia bloqueada" data-id="ICSE" data-prerequisitos="IPC">Introducción al Conocimiento de la Sociedad y el Estado (CBC)</div>
        <div class="materia bloqueada" data-id="ICP1" data-prerequisitos="IPC">Introducción al Conocimiento Proyectual 1 (CBC)</div>
        <div class="materia bloqueada" data-id="ICP2" data-prerequisitos="ICP1">Introducción al Conocimiento Proyectual 2 (CBC)</div>
        <div class="materia bloqueada" data-id="TD" data-prerequisitos="">Taller de Dibujo (CBC)</div>
        <div class="materia bloqueada" data-id="MAT" data-prerequisitos="">Matemática (CBC)</div>
        <div class="materia bloqueada" data-id="SEM" data-prerequisitos="">Semiología (CBC)</div>
      </div>
    </div>
    <div class="año-columna">
      <div class="titulo-año">Primer Año</div>
      <div class="materias-lista">
        <div class="materia bloqueada" data-id="DG1" data-prerequisitos="ICP2,TD">Diseño Gráfico 1</div>
        <div class="materia bloqueada" data-id="M1" data-prerequisitos="TD">Morfología 1</div>
        <div class="materia bloqueada" data-id="TIP1" data-prerequisitos="TD">Tipografía 1</div>
        <div class="materia bloqueada" data-id="H1" data-prerequisitos="ICSE">Historia 1</div>
        <div class="materia bloqueada" data-id="C1" data-prerequisitos="ICSE">Comunicación 1</div>
        <div class="materia bloqueada" data-id="TEC1" data-prerequisitos="MAT">Tecnología 1</div>
        <div class="opcion-exclusiva">
          <div class="materia bloqueada opcion-fot" data-id="Fot" data-prerequisitos="IPC,ICSE,ICP1,ICP2,TD,MAT,SEM" data-exclusiva="Ilus">Fotografía</div>
          <div class="materia bloqueada opcion-ilus" data-id="Ilus" data-prerequisitos="IPC,ICSE,ICP1,ICP2,TD,MAT,SEM" data-exclusiva="Fot">Ilustración</div>
        </div>
      </div>
    </div>
    <div class="año-columna">
      <div class="titulo-año">Segundo Año</div>
      <div class="materias-lista">
        <div class="materia bloqueada" data-id="DG2" data-prerequisitos="DG1,M1,TIP1">Diseño Gráfico 2</div>
        <div class="materia bloqueada" data-id="M2" data-prerequisitos="M1">Morfología 2</div>
        <div class="materia bloqueada" data-id="MO" data-prerequisitos="TIP1">Diseño Gráfico por Computación</div>
        <div class="materia bloqueada" data-id="H2" data-prerequisitos="H1">Historia 2</div>
        <div class="materia bloqueada" data-id="C2" data-prerequisitos="C1">Comunicación 2</div>
        <div class="materia bloqueada" data-id="TEC2" data-prerequisitos="TEC1">Tecnología 2</div>
        <div class="materia bloqueada" data-id="ME1" data-prerequisitos="Fot|Ilus">Medios Expresivos 1</div>
      </div>
    </div>
    <div class="año-columna">
      <div class="titulo-año">Tercer Año</div>
      <div class="materias-lista">
        <div class="materia bloqueada" data-id="DG3" data-prerequisitos="DG2,M2,MO,C2,H2,TEC2,ME1">Diseño Gráfico 3</div>
        <div class="materia bloqueada" data-id="ME2" data-prerequisitos="ME1">Medios Expresivos 2</div>
        <div class="materia bloqueada" data-id="TIP2" data-prerequisitos="TIP1">Tipografía 2</div>
        <div class="materia bloqueada" data-id="SocHum" data-prerequisitos="H1,H2,C1,C2">Electiva Socio Humanística</div>
        <div class="materia bloqueada" data-id="LPP" data-prerequisitos="DG3,ME2">Legislación y Práctica Profesional</div>
      </div>
    </div>
    <div class="año-columna">
      <div class="titulo-año">Cuarto Año</div>
      <div class="materias-lista">
        <div class="materia bloqueada" data-id="DG4" data-prerequisitos="H2,C2,DG3,M2,TIP2,ME1,TEC2">Diseño Gráfico 4</div>
        <div class="materia bloqueada" data-id="Elect1" data-prerequisitos="H2,C2,DG3,M2,TIP2,ME1,TEC2">Electiva Orientada 1</div>
        <div class="materia bloqueada" data-id="Elect2" data-prerequisitos="H2,C2,DG3,M2,TIP2,ME1,TEC2">Electiva Orientada 2</div>
        <div class="materia bloqueada" data-id="Opt1" data-prerequisitos="DG2,M2,TIP2,TEC2,ME1,H2,C2">Optativa 1</div>
        <div class="materia bloqueada" data-id="Opt2" data-prerequisitos="DG2,M2,TIP2,TEC2,ME1,H2,C2">Optativa 2</div>
      </div>
      <!-- Requisitos ocultos por pedido del usuario -->
    </div>
  </div>

  <div class="cuadro-electivas">
    <div class="cuadro-electivas-title">
      MATERIAS ELECTIVAS ORIENTADA (SE ELIGEN 2 EN EL ÚLTIMO AÑO)
    </div>
    <div class="materias-lista-final" id="electivas-orientada">
      <div class="materia" data-id="EO1">Análisis del Discurso Visual</div>
      <div class="materia" data-id="EO2">Diseño de Identidad Institucional</div>
      <div class="materia" data-id="EO3">Gestión de Proyecto</div>
      <div class="materia" data-id="EO4">Diseño Gráfico Editorial</div>
      <div class="materia" data-id="EO5">Diseño de la Información</div>
      <div class="materia" data-id="EO6">Diseño de Interfases Digitales</div>
      <div class="materia" data-id="EO7">Heurística</div>
      <div class="materia" data-id="EO8">Teoría del Habitar</div>
    </div>

    <div class="cuadro-electivas-title" style="margin-top:36px;">
      MATERIAS ELECTIVAS SOCIO HUMANÍSTICA (SE ELIGE 1)
    </div>
    <div class="materias-lista-final" id="electivas-socio">
      <div class="materia" data-id="SH1">Aspectos Económicos del Diseño</div>
      <div class="materia" data-id="SH2">Teoría de los Medios</div>
      <div class="materia" data-id="SH3">Diseño y Estudios Culturales</div>
      <div class="materia" data-id="SH4">Elementos de Psicología</div>
      <div class="materia" data-id="SH5">Diseño y Estudio de Género</div>
    </div>
  </div>

  <script>
    const materias = document.querySelectorAll('.materia');
    const contador = document.getElementById('contador');
    const listaCompletadas = document.getElementById('listaCompletadas');
    const STORAGE_KEY = 'mallaDG18Completadas';

    let completadas = JSON.parse(localStorage.getItem(STORAGE_KEY)) || [];

    function actualizarContadorYLista() {
      const completadasActual = Array.from(materias)
        .filter(mat => mat.classList.contains('completada'));
      contador.textContent = `Materias completadas: ${completadasActual.length} / ${materias.length}`;
      listaCompletadas.innerHTML = '';
      completadasActual.forEach(mat => {
        const li = document.createElement('li');
        li.textContent = mat.textContent;
        listaCompletadas.appendChild(li);
      });
    }

    function aplicarCompletadas() {
      materias.forEach(materia => {
        const id = materia.dataset.id;
        if (completadas.includes(id)) {
          materia.classList.add('completada');
        } else {
          materia.classList.remove('completada');
        }
      });
      aplicarExclusividad();
      desbloquearMaterias();
      actualizarContadorYLista();
    }

    function aplicarExclusividad() {
      const fot = document.querySelector('.materia[data-id="Fot"]');
      const ilus = document.querySelector('.materia[data-id="Ilus"]');
      if (fot && ilus) {
        if (fot.classList.contains('completada')) {
          ilus.classList.add('bloqueada');
        } else if (ilus.classList.contains('completada')) {
          fot.classList.add('bloqueada');
        } else {
          fot.classList.remove('bloqueada');
          ilus.classList.remove('bloqueada');
        }
      }
    }

    materias.forEach(materia => {
      materia.addEventListener('click', () => {
        if (materia.classList.contains('bloqueada')) return;
        if (materia.classList.contains('opcion-fot')) {
          document.querySelector('.materia[data-id="Ilus"]').classList.remove('completada');
        } else if (materia.classList.contains('opcion-ilus')) {
          document.querySelector('.materia[data-id="Fot"]').classList.remove('completada');
        }
        materia.classList.toggle('completada');
        const id = materia.dataset.id;
        if (materia.classList.contains('completada')) {
          if (!completadas.includes(id)) completadas.push(id);
        } else {
          completadas = completadas.filter(cid => cid !== id);
        }
        localStorage.setItem(STORAGE_KEY, JSON.stringify(completadas));
        aplicarCompletadas();
        aplicarTachadoElectivas();
      });
    });

    function desbloquearMaterias() {
      materias.forEach(m => {
        const prerequisitosRaw = m.dataset.prerequisitos;
        if (prerequisitosRaw && prerequisitosRaw.includes('|')) {
          const opciones = prerequisitosRaw.split('|').map(p => p.trim()).filter(Boolean);
          const algunoCompletado = opciones.some(id => {
            const elem = document.querySelector(`.materia[data-id="${id}"]`);
            return elem && elem.classList.contains('completada');
          });
          if (algunoCompletado) {
            m.classList.remove('bloqueada');
          } else if (!m.classList.contains('completada')) {
            m.classList.add('bloqueada');
          }
        } else {
          const prerequisitos = prerequisitosRaw ? prerequisitosRaw.split(',').filter(p => p) : [];
          const completados = prerequisitos.every(id => {
            const elem = document.querySelector(`.materia[data-id="${id}"]`);
            return id === "" || (elem && elem.classList.contains('completada'));
          });
          if (completados) {
            m.classList.remove('bloqueada');
          } else if (!m.classList.contains('completada')) {
            m.classList.add('bloqueada');
          }
        }
      });
      aplicarExclusividad();
    }

    // --- Electivas tachables al final ---
    const electivasOrientada = document.querySelectorAll('#electivas-orientada .materia');
    const electivasSocio = document.querySelectorAll('#electivas-socio .materia');
    const electivasTachables = [...electivasOrientada, ...electivasSocio];
    let electivasTachadas = JSON.parse(localStorage.getItem('mallaDG18ElectivasTachadas')) || [];

    // Requisitos electivas orientadas (no se muestran en la interfaz)
    const requisitosElectivaOrientada = [
      "H2", "C2", "DG3", "M2", "TIP2", "ME1", "TEC2"
    ];
    // Requisitos electiva socio humanística (no se muestran en la interfaz)
    const requisitosElectivaSocio = [
      "H1", "H2", "C1", "C2"
    ];

    function puedeTacharElectivaOrientada() {
      return requisitosElectivaOrientada.every(id => {
        const mat = document.querySelector(`.materia[data-id="${id}"]`);
        return mat && mat.classList.contains('completada');
      });
    }
    function puedeTacharElectivaSocio() {
      return requisitosElectivaSocio.every(id => {
        const mat = document.querySelector(`.materia[data-id="${id}"]`);
        return mat && mat.classList.contains('completada');
      });
    }

    function aplicarTachadoElectivas() {
      const puedeTacharOri = puedeTacharElectivaOrientada();
      const puedeTacharSocio = puedeTacharElectivaSocio();

      let orientadaSeleccionadas = electivasTachadas.filter(id =>
        Array.from(electivasOrientada).some(mat => mat.dataset.id === id)
      );
      let socioSeleccionadas = electivasTachadas.filter(id =>
        Array.from(electivasSocio).some(mat => mat.dataset.id === id)
      );

      electivasOrientada.forEach(mat => {
        if (!puedeTacharOri) {
          mat.classList.add('requisito-no');
        } else {
          mat.classList.remove('requisito-no');
        }
        // Solo permitir hasta 2 seleccionadas
        if (
          electivasTachadas.includes(mat.dataset.id) ||
          orientadaSeleccionadas.length < 2
        ) {
          if (electivasTachadas.includes(mat.dataset.id)) {
            mat.classList.add('completada');
          } else {
            mat.classList.remove('completada');
          }
        } else {
          mat.classList.remove('completada');
        }
      });

      electivasSocio.forEach(mat => {
        if (!puedeTacharSocio) {
          mat.classList.add('requisito-no');
        } else {
          mat.classList.remove('requisito-no');
        }
        // Solo permitir 1 seleccionada
        if (
          electivasTachadas.includes(mat.dataset.id) ||
          socioSeleccionadas.length < 1
        ) {
          if (electivasTachadas.includes(mat.dataset.id)) {
            mat.classList.add('completada');
          } else {
            mat.classList.remove('completada');
          }
        } else {
          mat.classList.remove('completada');
        }
      });
    }

    electivasTachables.forEach(materia => {
      materia.addEventListener('click', function () {
        // Orientada: solo si requisitos y menos de 2 elegidas o está elegida
        if (
          this.parentElement.id === "electivas-orientada"
        ) {
          if (!puedeTacharElectivaOrientada()) {
            alert("Debes aprobar todas las materias requeridas para poder seleccionar una Electiva Orientada.");
            return;
          }
          let orientadaSeleccionadas = electivasTachadas.filter(id =>
            Array.from(electivasOrientada).some(mat => mat.dataset.id === id)
          );
          // Solo permitir 2 seleccionadas, permitir desmarcar
          if (
            orientadaSeleccionadas.length >= 2 &&
            !this.classList.contains('completada')
          ) {
            alert("Solo puedes seleccionar 2 materias Electivas Orientadas.");
            return;
          }
        }
        // Socio: solo si requisitos y menos de 1 elegida o está elegida
        if (
          this.parentElement.id === "electivas-socio"
        ) {
          if (!puedeTacharElectivaSocio()) {
            alert("Debes aprobar Historia 1 y 2, Comunicación 1 y 2 para poder seleccionar una Electiva Socio Humanística.");
            return;
          }
          let socioSeleccionadas = electivasTachadas.filter(id =>
            Array.from(electivasSocio).some(mat => mat.dataset.id === id)
          );
          if (
            socioSeleccionadas.length >= 1 &&
            !this.classList.contains('completada')
          ) {
            alert("Solo puedes seleccionar 1 materia Electiva Socio Humanística.");
            return;
          }
        }
        this.classList.toggle('completada');
        const id = this.dataset.id;
        if (this.classList.contains('completada')) {
          if (!electivasTachadas.includes(id)) electivasTachadas.push(id);
        } else {
          electivasTachadas = electivasTachadas.filter(cid => cid !== id);
        }
        localStorage.setItem('mallaDG18ElectivasTachadas', JSON.stringify(electivasTachadas));
        aplicarTachadoElectivas();
      });
    });

    document.getElementById('reiniciar').addEventListener('click', () => {
      completadas = [];
      electivasTachadas = [];
      localStorage.removeItem('mallaDG18Completadas');
      localStorage.removeItem('mallaDG18ElectivasTachadas');
      aplicarCompletadas();
      aplicarTachadoElectivas();
    });

    aplicarCompletadas();
    aplicarTachadoElectivas();
  </script>
</body>
</html>
