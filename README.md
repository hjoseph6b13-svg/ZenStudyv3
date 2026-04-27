<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ZenStudy — Tu bienestar estudiantil</title>
  <link rel="stylesheet" href="css/style.css" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.4.0/css/all.min.css" />
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>

  <!-- ===== HEADER ===== -->
  <header class="app-header">
    <div class="header-logo">
      <span class="logo-icon">🌿</span>
      <span class="logo-text">ZenStudy</span>
    </div>
    <div class="header-time" id="headerTime"></div>
  </header>

  <!-- ===== NAVEGACIÓN POR PESTAÑAS ===== -->
  <nav class="tab-nav" id="tabNav">
    <button class="tab-btn active" data-tab="inicio">
      <i class="fas fa-home"></i>
      <span>Inicio</span>
    </button>
    <button class="tab-btn" data-tab="calendario">
      <i class="fas fa-calendar-week"></i>
      <span>Calendario</span>
    </button>
    <button class="tab-btn" data-tab="temporizador">
      <i class="fas fa-clock"></i>
      <span>Timer</span>
    </button>
    <button class="tab-btn" data-tab="relajacion">
      <i class="fas fa-wind"></i>
      <span>Relajación</span>
    </button>
    <button class="tab-btn" data-tab="musica">
      <i class="fas fa-music"></i>
      <span>Música</span>
    </button>
    <button class="tab-btn" data-tab="notificaciones">
      <i class="fas fa-bell"></i>
      <span>Avisos</span>
    </button>
    <button class="tab-btn" data-tab="progreso">
      <i class="fas fa-chart-line"></i>
      <span>Progreso</span>
    </button>
    <button class="tab-btn" data-tab="perfil">
      <i class="fas fa-user-circle"></i>
      <span>Perfil</span>
    </button>
  </nav>

  <!-- ===== CONTENIDO PRINCIPAL ===== -->
  <main class="app-content">

    <!-- ══════════════════════════════════════
         PESTAÑA: INICIO
    ══════════════════════════════════════ -->
    <section class="tab-panel active" id="tab-inicio">
      <div class="panel-inner">
        <div class="welcome-card card">
          <div class="welcome-top">
            <div>
              <h1 class="welcome-title" id="welcomeTitle">¡Hola, estudiante! 👋</h1>
              <p class="welcome-sub" id="welcomeSub">¿Cómo está tu día hoy?</p>
            </div>
            <div class="weather-badge" id="weatherBadge">
              <i class="fas fa-map-marker-alt"></i>
              <span id="locationText">Mi lugar</span>
            </div>
          </div>

          <!-- Pregunta: ¿Cómo te sientes? -->
          <div class="feeling-section">
            <p class="section-label">¿Cómo te sientes hoy?</p>
            <div class="feeling-grid" id="feelingGrid">
              <button class="feeling-btn" data-feeling="excelente" data-val="1">😄 Excelente</button>
              <button class="feeling-btn" data-feeling="bien" data-val="2">🙂 Bien</button>
              <button class="feeling-btn" data-feeling="regular" data-val="3">😐 Regular</button>
              <button class="feeling-btn" data-feeling="cansado" data-val="4">😴 Cansado</button>
              <button class="feeling-btn" data-feeling="ansioso" data-val="5">😰 Ansioso</button>
              <button class="feeling-btn" data-feeling="mal" data-val="6">😟 Mal</button>
            </div>
          </div>

          <!-- Nivel de estrés -->
          <div class="stress-section">
            <p class="section-label">Nivel de estrés <span class="stress-value" id="stressDisplay">5</span>/10</p>
            <div class="slider-track">
              <input type="range" id="stressSlider" min="1" max="10" value="5" class="stress-slider" />
              <div class="slider-labels">
                <span>Tranquilo 😊</span>
                <span>Muy estresado 😤</span>
              </div>
            </div>
          </div>

          <!-- Lugar y tiempo libre -->
          <div class="context-row">
            <div class="context-field">
              <label class="context-label"><i class="fas fa-map-marker-alt"></i> ¿Dónde estás?</label>
              <select id="locationSelect" class="pill-select">
                <option value="casa">🏠 En casa</option>
                <option value="universidad">🎓 Universidad</option>
                <option value="cafe">☕ Cafetería</option>
                <option value="biblioteca">📚 Biblioteca</option>
                <option value="transporte">🚌 Transporte</option>
                <option value="otro">📍 Otro lugar</option>
              </select>
            </div>
            <div class="context-field">
              <label class="context-label"><i class="fas fa-hourglass-half"></i> Tiempo libre</label>
              <select id="freeTimeSelect" class="pill-select">
                <option value="15">⚡ 15 minutos</option>
                <option value="30">🕐 30 minutos</option>
                <option value="60" selected>🕐 1 hora</option>
                <option value="120">🕑 2 horas</option>
                <option value="180">🕒 3+ horas</option>
              </select>
            </div>
          </div>

          <!-- Botón principal -->
          <button class="btn-primary btn-large" id="btnRecomendacion" onclick="generarRecomendacion()">
            <i class="fas fa-magic"></i> Obtener recomendación
          </button>
        </div>

        <!-- Tarjeta de recomendación -->
        <div class="recommendation-card card hidden" id="recommendationCard">
          <div class="rec-header">
            <span class="rec-icon" id="recIcon">✨</span>
            <h3 id="recTitle">Tu recomendación personalizada</h3>
          </div>
          <p id="recBody" class="rec-body"></p>
          <div class="rec-actions" id="recActions"></div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: CALENDARIO
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-calendario">
      <div class="panel-inner">
        <div class="panel-header">
          <h2><i class="fas fa-calendar-week"></i> Calendario semanal</h2>
          <button class="btn-secondary" onclick="openEventModal()"><i class="fas fa-plus"></i> Agregar</button>
        </div>

        <!-- Días de la semana -->
        <div class="week-nav">
          <button class="week-nav-btn" id="prevWeek" onclick="changeWeek(-1)"><i class="fas fa-chevron-left"></i></button>
          <span class="week-label" id="weekLabel">Semana actual</span>
          <button class="week-nav-btn" id="nextWeek" onclick="changeWeek(1)"><i class="fas fa-chevron-right"></i></button>
        </div>

        <div class="calendar-grid" id="calendarGrid">
          <!-- Generado por JS -->
        </div>

        <!-- Leyenda -->
        <div class="legend-row">
          <span class="legend-item"><span class="dot dot-clases"></span> Clases</span>
          <span class="legend-item"><span class="dot dot-academia"></span> Academia</span>
          <span class="legend-item"><span class="dot dot-ingles"></span> Inglés</span>
          <span class="legend-item"><span class="dot dot-descanso"></span> Descanso</span>
          <span class="legend-item"><span class="dot dot-sueno"></span> Sueño</span>
          <span class="legend-item"><span class="dot dot-alarma"></span> Alarma</span>
        </div>
      </div>

      <!-- Modal agregar evento -->
      <div class="modal-overlay hidden" id="eventModal">
        <div class="modal-card card">
          <h3 class="modal-title">📅 Nuevo evento</h3>
          <div class="form-group">
            <label>Tipo de evento</label>
            <select id="eventType" class="pill-select">
              <option value="clases">📖 Clases</option>
              <option value="academia">🏫 Academia</option>
              <option value="ingles">🌐 Inglés</option>
              <option value="descanso">😴 Descanso</option>
              <option value="sueno">🌙 Sueño</option>
              <option value="recordatorio">🔔 Recordatorio</option>
              <option value="alarma">⏰ Alarma</option>
              <option value="pausa">🧘 Pausa activa</option>
            </select>
          </div>
          <div class="form-group">
            <label>Día</label>
            <select id="eventDay" class="pill-select">
              <option value="0">Lunes</option>
              <option value="1">Martes</option>
              <option value="2">Miércoles</option>
              <option value="3">Jueves</option>
              <option value="4">Viernes</option>
              <option value="5">Sábado</option>
              <option value="6">Domingo</option>
            </select>
          </div>
          <div class="form-row">
            <div class="form-group">
              <label>Hora inicio</label>
              <input type="time" id="eventStart" class="pill-input" value="08:00" />
            </div>
            <div class="form-group">
              <label>Hora fin</label>
              <input type="time" id="eventEnd" class="pill-input" value="09:00" />
            </div>
          </div>
          <div class="form-group">
            <label>Descripción</label>
            <input type="text" id="eventDesc" class="pill-input" placeholder="ej. Matemáticas, Yoga..." />
          </div>
          <div class="modal-actions">
            <button class="btn-ghost" onclick="closeEventModal()">Cancelar</button>
            <button class="btn-primary" onclick="saveEvent()"><i class="fas fa-check"></i> Guardar</button>
          </div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: TEMPORIZADOR
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-temporizador">
      <div class="panel-inner timer-panel">
        <h2 class="panel-title"><i class="fas fa-clock"></i> Temporizador Pomodoro</h2>

        <!-- Selector de modo -->
        <div class="mode-selector">
          <button class="mode-btn active" data-mode="pomodoro" onclick="setTimerMode('pomodoro')">
            📚 Estudio (25 min)
          </button>
          <button class="mode-btn" data-mode="short" onclick="setTimerMode('short')">
            ☕ Descanso corto (5 min)
          </button>
          <button class="mode-btn" data-mode="long" onclick="setTimerMode('long')">
            🛋️ Descanso largo (15 min)
          </button>
          <button class="mode-btn" data-mode="custom" onclick="setTimerMode('custom')">
            ⚙️ Personalizado
          </button>
        </div>

        <!-- Custom inputs -->
        <div class="custom-timer hidden" id="customTimer">
          <div class="form-row">
            <div class="form-group">
              <label>Minutos estudio</label>
              <input type="number" id="customStudy" class="pill-input" value="25" min="1" max="120" />
            </div>
            <div class="form-group">
              <label>Minutos descanso</label>
              <input type="number" id="customBreak" class="pill-input" value="5" min="1" max="60" />
            </div>
          </div>
          <button class="btn-secondary small" onclick="applyCustomTimer()">Aplicar</button>
        </div>

        <!-- Círculo de tiempo -->
        <div class="timer-circle-wrap">
          <svg class="timer-svg" viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg">
            <circle class="timer-bg-circle" cx="100" cy="100" r="88" />
            <circle class="timer-progress-circle" id="timerProgressCircle" cx="100" cy="100" r="88"
              stroke-dasharray="553"
              stroke-dashoffset="0"
              transform="rotate(-90 100 100)" />
          </svg>
          <div class="timer-text-wrap">
            <div class="timer-display" id="timerDisplay">25:00</div>
            <div class="timer-mode-label" id="timerModeLabel">Estudio</div>
            <div class="pomodoro-count">
              <span>🍅</span>
              <span id="pomodoroCount">0</span> pomodoros
            </div>
          </div>
        </div>

        <!-- Controles -->
        <div class="timer-controls">
          <button class="timer-btn btn-ghost" onclick="resetTimer()" title="Reiniciar">
            <i class="fas fa-redo"></i>
          </button>
          <button class="timer-btn btn-primary large" id="timerPlayBtn" onclick="toggleTimer()">
            <i class="fas fa-play" id="timerPlayIcon"></i>
          </button>
          <button class="timer-btn btn-ghost" onclick="skipTimer()" title="Saltar">
            <i class="fas fa-forward"></i>
          </button>
        </div>

        <!-- Estadísticas de sesión -->
        <div class="timer-stats card">
          <div class="stat-item">
            <span class="stat-num" id="statStudyTime">0</span>
            <span class="stat-label">min estudiados</span>
          </div>
          <div class="stat-item">
            <span class="stat-num" id="statBreaks">0</span>
            <span class="stat-label">descansos</span>
          </div>
          <div class="stat-item">
            <span class="stat-num" id="statPomodoros">0</span>
            <span class="stat-label">pomodoros hoy</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: RELAJACIÓN
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-relajacion">
      <div class="panel-inner">
        <h2 class="panel-title"><i class="fas fa-wind"></i> Técnicas de relajación</h2>

        <!-- Selector de ejercicio -->
        <div class="relax-selector">
          <button class="relax-choice active" data-exercise="box" onclick="selectExercise('box')">
            <span>📦</span> Respiración cuadrada
          </button>
          <button class="relax-choice" data-exercise="478" onclick="selectExercise('478')">
            <span>4️⃣</span> Técnica 4-7-8
          </button>
          <button class="relax-choice" data-exercise="deep" onclick="selectExercise('deep')">
            <span>🌊</span> Respiración profunda
          </button>
          <button class="relax-choice" data-exercise="scan" onclick="selectExercise('scan')">
            <span>🧘</span> Escaneo corporal
          </button>
        </div>

        <!-- Descripción del ejercicio -->
        <div class="card exercise-desc" id="exerciseDesc">
          <p id="exerciseDescText">Inhala 4s → Mantén 4s → Exhala 4s → Mantén 4s. Repite y relájate.</p>
        </div>

        <!-- Visualización de respiración -->
        <div class="breath-container">
          <div class="breath-circle" id="breathCircle">
            <span id="breathText">Listo</span>
          </div>
          <div class="breath-instruction" id="breathInstruction">Presiona Iniciar para comenzar</div>
          <div class="breath-countdown" id="breathCountdown"></div>
        </div>

        <!-- Controles de relajación -->
        <div class="relax-controls">
          <button class="btn-ghost" onclick="stopBreathing()"><i class="fas fa-stop"></i> Detener</button>
          <button class="btn-primary" id="breathStartBtn" onclick="startBreathing()">
            <i class="fas fa-play"></i> Iniciar
          </button>
        </div>

        <!-- Ciclos completados -->
        <div class="cycles-info card">
          <p>Ciclos completados: <strong id="breathCycles">0</strong></p>
          <p class="cycles-sub">Cada ciclo = ~1 min de calma 💚</p>
        </div>

        <!-- Pausas activas -->
        <div class="active-pauses card">
          <h4><i class="fas fa-running"></i> Pausas activas rápidas</h4>
          <div class="pauses-grid">
            <button class="pause-btn" onclick="startActivePause('cuello')">🔄 Cuello</button>
            <button class="pause-btn" onclick="startActivePause('hombros')">💪 Hombros</button>
            <button class="pause-btn" onclick="startActivePause('ojos')">👁️ Ojos</button>
            <button class="pause-btn" onclick="startActivePause('espalda')">🦴 Espalda</button>
          </div>
          <div class="pause-instruction hidden" id="pauseInstruction"></div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: MÚSICA Y SONIDOS
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-musica">
      <div class="panel-inner">
        <h2 class="panel-title"><i class="fas fa-music"></i> Música & Sonidos</h2>

        <!-- Sonidos ambientales -->
        <div class="music-section">
          <h3 class="music-category">🌿 Sonidos de la naturaleza</h3>
          <div class="sound-grid" id="natureSounds">
            <div class="sound-card" data-sound="rain" onclick="toggleSound('rain')">
              <div class="sound-icon">🌧️</div>
              <div class="sound-name">Lluvia</div>
              <div class="sound-wave hidden" id="wave-rain"></div>
              <div class="volume-wrap hidden" id="vol-rain">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('rain', this.value)" />
              </div>
            </div>
            <div class="sound-card" data-sound="ocean" onclick="toggleSound('ocean')">
              <div class="sound-icon">🌊</div>
              <div class="sound-name">Mar</div>
              <div class="sound-wave hidden" id="wave-ocean"></div>
              <div class="volume-wrap hidden" id="vol-ocean">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('ocean', this.value)" />
              </div>
            </div>
            <div class="sound-card" data-sound="forest" onclick="toggleSound('forest')">
              <div class="sound-icon">🌲</div>
              <div class="sound-name">Bosque</div>
              <div class="sound-wave hidden" id="wave-forest"></div>
              <div class="volume-wrap hidden" id="vol-forest">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('forest', this.value)" />
              </div>
            </div>
            <div class="sound-card" data-sound="white" onclick="toggleSound('white')">
              <div class="sound-icon">📻</div>
              <div class="sound-name">Ruido blanco</div>
              <div class="sound-wave hidden" id="wave-white"></div>
              <div class="volume-wrap hidden" id="vol-white">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('white', this.value)" />
              </div>
            </div>
            <div class="sound-card" data-sound="fire" onclick="toggleSound('fire')">
              <div class="sound-icon">🔥</div>
              <div class="sound-name">Chimenea</div>
              <div class="sound-wave hidden" id="wave-fire"></div>
              <div class="volume-wrap hidden" id="vol-fire">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('fire', this.value)" />
              </div>
            </div>
            <div class="sound-card" data-sound="cafe" onclick="toggleSound('cafe')">
              <div class="sound-icon">☕</div>
              <div class="sound-name">Café</div>
              <div class="sound-wave hidden" id="wave-cafe"></div>
              <div class="volume-wrap hidden" id="vol-cafe">
                <input type="range" class="vol-slider" min="0" max="1" step="0.05" value="0.5"
                  oninput="setVolume('cafe', this.value)" />
              </div>
            </div>
          </div>
        </div>

        <!-- Música Minecraft -->
        <div class="music-section">
          <h3 class="music-category">🎮 Música de Minecraft <span class="badge-mc">Lo-fi Study</span></h3>
          <div class="mc-tracks" id="mcTracks">
            <div class="track-card" onclick="playMCTrack('sweden')">
              <div class="track-art">🎵</div>
              <div class="track-info">
                <div class="track-name">Sweden</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-sweden">
                <i class="fas fa-play"></i>
              </button>
            </div>
            <div class="track-card" onclick="playMCTrack('wethands')">
              <div class="track-art">🎶</div>
              <div class="track-info">
                <div class="track-name">Wet Hands</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-wethands">
                <i class="fas fa-play"></i>
              </button>
            </div>
            <div class="track-card" onclick="playMCTrack('calm')">
              <div class="track-art">🌙</div>
              <div class="track-info">
                <div class="track-name">Calm</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-calm">
                <i class="fas fa-play"></i>
              </button>
            </div>
            <div class="track-card" onclick="playMCTrack('living')">
              <div class="track-art">🌿</div>
              <div class="track-info">
                <div class="track-name">Living Mice</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-living">
                <i class="fas fa-play"></i>
              </button>
            </div>
            <div class="track-card" onclick="playMCTrack('minecraft')">
              <div class="track-art">⛏️</div>
              <div class="track-info">
                <div class="track-name">Minecraft</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-minecraft">
                <i class="fas fa-play"></i>
              </button>
            </div>
            <div class="track-card" onclick="playMCTrack('subwoofer')">
              <div class="track-art">🔊</div>
              <div class="track-info">
                <div class="track-name">Subwoofer Lullaby</div>
                <div class="track-artist">C418 • Minecraft OST</div>
              </div>
              <button class="track-play-btn" id="btn-subwoofer">
                <i class="fas fa-play"></i>
              </button>
            </div>
          </div>
        </div>

        <!-- Mini reproductor -->
        <div class="mini-player card hidden" id="miniPlayer">
          <div class="player-info">
            <span class="player-icon" id="playerIcon">🎵</span>
            <div>
              <div class="player-title" id="playerTitle">—</div>
              <div class="player-sub" id="playerSub">—</div>
            </div>
          </div>
          <div class="player-controls">
            <button class="player-btn" onclick="stopMCTrack()"><i class="fas fa-stop"></i></button>
          </div>
        </div>

        <p class="music-note">
          <i class="fas fa-info-circle"></i>
          Los sonidos se generan mediante Web Audio API. Las pistas de Minecraft simulan el ambiente
          con tonos suaves. Para audio real, importa tus archivos MP3.
        </p>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: NOTIFICACIONES
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-notificaciones">
      <div class="panel-inner">
        <h2 class="panel-title"><i class="fas fa-bell"></i> Centro de notificaciones</h2>

        <!-- Estado de permisos -->
        <div class="notif-permission card" id="notifPermCard">
          <div class="notif-perm-info">
            <i class="fas fa-shield-alt notif-shield"></i>
            <div>
              <strong>Activar notificaciones del navegador</strong>
              <p>Para recibir recordatorios aunque la app esté minimizada</p>
            </div>
          </div>
          <button class="btn-primary" id="btnPermission" onclick="requestNotifPermission()">
            Activar
          </button>
        </div>

        <!-- Lista de notificaciones configurables -->
        <div class="notif-list" id="notifList">
          <!-- Cada notificación -->
        </div>

        <!-- Historial de notificaciones -->
        <div class="notif-history card">
          <h4><i class="fas fa-history"></i> Historial reciente</h4>
          <div id="notifHistory" class="notif-history-list">
            <p class="empty-msg">Sin notificaciones recientes.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: PROGRESO / ENCUESTA
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-progreso">
      <div class="panel-inner">
        <h2 class="panel-title"><i class="fas fa-chart-line"></i> Progreso & Encuesta diaria</h2>

        <!-- Encuesta diaria -->
        <div class="survey-card card" id="surveyCard">
          <h3><i class="fas fa-clipboard-list"></i> ¿Cómo fue tu día?</h3>
          <p class="survey-date" id="surveyDate"></p>

          <div class="survey-field">
            <label>¿Cómo te sentiste hoy?</label>
            <div class="feeling-grid small" id="surveyFeeling">
              <button class="feeling-btn small" data-feeling="excelente" data-val="1" onclick="selectSurveyFeeling(this)">😄 Excelente</button>
              <button class="feeling-btn small" data-feeling="bien" data-val="2" onclick="selectSurveyFeeling(this)">🙂 Bien</button>
              <button class="feeling-btn small" data-feeling="regular" data-val="3" onclick="selectSurveyFeeling(this)">😐 Regular</button>
              <button class="feeling-btn small" data-feeling="cansado" data-val="4" onclick="selectSurveyFeeling(this)">😴 Cansado</button>
              <button class="feeling-btn small" data-feeling="ansioso" data-val="5" onclick="selectSurveyFeeling(this)">😰 Ansioso</button>
              <button class="feeling-btn small" data-feeling="mal" data-val="6" onclick="selectSurveyFeeling(this)">😟 Mal</button>
            </div>
          </div>

          <div class="survey-field">
            <label>Nivel de estrés hoy <span id="surveyStressVal">5</span>/10</label>
            <input type="range" id="surveyStress" min="1" max="10" value="5" class="stress-slider"
              oninput="updateSurveyStress(this.value)" />
          </div>

          <div class="survey-field">
            <label>¿Qué te ayudó hoy? (puedes seleccionar varios)</label>
            <div class="checkbox-grid" id="helpedGrid">
              <label class="check-item"><input type="checkbox" value="ejercicio" /> 🏃 Ejercicio</label>
              <label class="check-item"><input type="checkbox" value="musica" /> 🎵 Música</label>
              <label class="check-item"><input type="checkbox" value="descansos" /> 😴 Descansos</label>
              <label class="check-item"><input type="checkbox" value="respiracion" /> 🌬️ Respiración</label>
              <label class="check-item"><input type="checkbox" value="amigos" /> 👥 Amigos</label>
              <label class="check-item"><input type="checkbox" value="naturaleza" /> 🌿 Naturaleza</label>
              <label class="check-item"><input type="checkbox" value="comida" /> 🍎 Buena comida</label>
              <label class="check-item"><input type="checkbox" value="pomodoro" /> 🍅 Pomodoro</label>
            </div>
          </div>

          <div class="survey-field">
            <label>¿Qué NO te ayudó?</label>
            <div class="checkbox-grid" id="notHelpedGrid">
              <label class="check-item"><input type="checkbox" value="distracciones" /> 📱 Distracciones</label>
              <label class="check-item"><input type="checkbox" value="ruido" /> 🔊 Mucho ruido</label>
              <label class="check-item"><input type="checkbox" value="cansancio" /> 😴 Cansancio</label>
              <label class="check-item"><input type="checkbox" value="ansiedad" /> 😰 Ansiedad</label>
              <label class="check-item"><input type="checkbox" value="procrastinacion" /> ⏳ Procrastinación</label>
              <label class="check-item"><input type="checkbox" value="hambre" /> 🍕 Hambre/sed</label>
            </div>
          </div>

          <div class="survey-field">
            <label>Nota adicional (opcional)</label>
            <textarea id="surveyNote" class="pill-textarea" rows="2" placeholder="Cuéntame más sobre tu día..."></textarea>
          </div>

          <button class="btn-primary btn-large" onclick="submitSurvey()">
            <i class="fas fa-check-circle"></i> Guardar encuesta
          </button>
        </div>

        <!-- Gráfico semanal -->
        <div class="chart-card card">
          <h3><i class="fas fa-chart-bar"></i> Evolución del estrés — últimos 7 días</h3>
          <div style="height: 260px; position: relative;">
            <canvas id="stressChart"></canvas>
          </div>
          <div class="chart-insights" id="chartInsights"></div>
        </div>
      </div>
    </section>

    <!-- ══════════════════════════════════════
         PESTAÑA: PERFIL
    ══════════════════════════════════════ -->
    <section class="tab-panel" id="tab-perfil">
      <div class="panel-inner">
        <h2 class="panel-title"><i class="fas fa-user-circle"></i> Mi perfil</h2>

        <!-- Avatar y datos principales -->
        <div class="profile-header card">
          <div class="avatar-wrap">
            <div class="avatar" id="avatarDisplay">😊</div>
            <div class="avatar-picker" id="avatarPicker">
              <span onclick="setAvatar('😊')">😊</span><span onclick="setAvatar('😎')">😎</span>
              <span onclick="setAvatar('🧑‍🎓')">🧑‍🎓</span><span onclick="setAvatar('👩‍💻')">👩‍💻</span>
              <span onclick="setAvatar('🧘')">🧘</span><span onclick="setAvatar('🌟')">🌟</span>
              <span onclick="setAvatar('🦋')">🦋</span><span onclick="setAvatar('🌸')">🌸</span>
            </div>
            <button class="btn-ghost small" onclick="toggleAvatarPicker()">Cambiar avatar</button>
          </div>
          <div class="profile-main-info">
            <div class="form-group">
              <label>Nombre</label>
              <input type="text" id="profileName" class="pill-input" placeholder="Tu nombre" />
            </div>
            <div class="form-row">
              <div class="form-group">
                <label>Edad</label>
                <input type="number" id="profileAge" class="pill-input" placeholder="20" min="10" max="99" />
              </div>
              <div class="form-group">
                <label>Carrera / Nivel</label>
                <input type="text" id="profileCareer" class="pill-input" placeholder="Ingeniería, Bachillerato..." />
              </div>
            </div>
            <div class="form-group">
              <label>Ciudad</label>
              <input type="text" id="profileCity" class="pill-input" placeholder="Tu ciudad" />
            </div>
          </div>
        </div>

        <!-- Actividades que sí ayudan -->
        <div class="card">
          <h4><i class="fas fa-heart"></i> Actividades que me ayudan</h4>
          <p class="section-sub">Basado en tus encuestas, estas actividades te funcionan:</p>
          <div class="helped-tags" id="helpedTagsDisplay">
            <span class="empty-msg">Completa encuestas diarias para ver patrones 💙</span>
          </div>
        </div>

        <!-- Historial emocional resumido -->
        <div class="card">
          <h4><i class="fas fa-history"></i> Historial emocional (últimos 7 días)</h4>
          <div class="emotion-history" id="emotionHistory">
            <p class="empty-msg">Sin registros aún. ¡Completa tu primera encuesta! 🌱</p>
          </div>
        </div>

        <!-- Estadísticas del perfil -->
        <div class="profile-stats card">
          <div class="stat-box">
            <span class="stat-big" id="statTotalDays">0</span>
            <span class="stat-desc">días registrados</span>
          </div>
          <div class="stat-box">
            <span class="stat-big" id="statAvgStress">—</span>
            <span class="stat-desc">estrés promedio</span>
          </div>
          <div class="stat-box">
            <span class="stat-big" id="statPomodoros">0</span>
            <span class="stat-desc">🍅 pomodoros</span>
          </div>
        </div>

        <!-- Guardar perfil -->
        <button class="btn-primary btn-large" onclick="saveProfile()">
          <i class="fas fa-save"></i> Guardar perfil
        </button>

        <!-- Zona de datos -->
        <div class="card danger-zone">
          <h4><i class="fas fa-database"></i> Datos</h4>
          <div class="danger-row">
            <button class="btn-secondary small" onclick="exportData()">
              <i class="fas fa-download"></i> Exportar datos
            </button>
            <button class="btn-danger small" onclick="clearAllData()">
              <i class="fas fa-trash"></i> Borrar todo
            </button>
          </div>
        </div>
      </div>
    </section>

  </main>

  <!-- ===== TOAST NOTIFICATION ===== -->
  <div class="toast" id="toast"></div>

  <!-- ===== SCRIPTS ===== -->
  <script src="js/app.js"></script>
</body>
</html>
