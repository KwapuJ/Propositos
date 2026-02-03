# Propositos
SARAH JUÁREZ SILVA: PROPÓSITOS DE AÑO NUEVO
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Propósitos de Año Nuevo</title>

  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      color: #fff;
      background: radial-gradient(circle at bottom, #0b1d3a, #020617);
      overflow: hidden;
    }

    /* Fondo de fuegos artificiales */
    .fireworks::before,
    .fireworks::after {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle, rgba(255,255,255,.9) 2px, transparent 3px) 10% 20%/120px 120px,
        radial-gradient(circle, rgba(255,0,120,.8) 2px, transparent 3px) 70% 30%/160px 160px,
        radial-gradient(circle, rgba(0,200,255,.8) 2px, transparent 3px) 40% 70%/140px 140px,
        radial-gradient(circle, rgba(255,200,0,.8) 2px, transparent 3px) 80% 80%/180px 180px;
      animation: float 12s linear infinite;
      pointer-events: none;
    }

    .fireworks::after {
      animation-duration: 18s;
      opacity: .7;
    }

    @keyframes float {
      from { transform: translateY(0); }
      to { transform: translateY(-40px); }
    }

    .card {
      position: relative;
      z-index: 1;
      background: rgba(0,0,0,.45);
      backdrop-filter: blur(6px);
      border-radius: 16px;
      padding: 28px 32px 32px;
      width: min(90vw, 520px);
      text-align: center;
      box-shadow: 0 20px 50px rgba(0,0,0,.45);
    }

    h1 {
      margin: 0 0 14px;
      font-size: 1.8rem;
    }

    #proposito {
      min-height: 72px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.25rem;
      margin: 18px 0 22px;
      padding: 14px 16px;
      border-radius: 12px;
      background: rgba(255,255,255,.08);
      transition: transform .4s ease, opacity .4s ease;
    }

    .animate {
      animation: pop .6s ease;
    }

    @keyframes pop {
      0% { transform: scale(.85); opacity: 0; }
      60% { transform: scale(1.05); opacity: 1; }
      100% { transform: scale(1); }
    }

    button {
      border: none;
      border-radius: 999px;
      padding: 12px 26px;
      font-size: 1rem;
      cursor: pointer;
      color: #020617;
      background: linear-gradient(135deg, #fbbf24, #fb7185);
      box-shadow: 0 10px 25px rgba(251,191,36,.35);
    }

    /* Explosión */
    .burst {
      position: absolute;
      left: 50%;
      top: 50%;
      width: 10px;
      height: 10px;
      border-radius: 50%;
      pointer-events: none;
      animation: burst 700ms ease-out forwards;
      background: radial-gradient(circle, #fff, transparent 60%);
    }

    @keyframes burst {
      0% { transform: translate(-50%, -50%) scale(.2); opacity: 1; }
      100% { transform: translate(-50%, -50%) scale(18); opacity: 0; }
    }
  </style>
</head>

<body class="fireworks">
  <div class="card">
    <h1>Propósitos de Año Nuevo 🎆</h1>
    <div id="proposito">Comenzar</div>
    <button id="btnNuevo">Nuevo</button>
  </div>

  <script>
    const propositos = [
      "Hacer ejercicio al menos 3 veces por semana",
      "Aprender una nueva habilidad o idioma",
      "Ahorrar dinero de forma constante",
      "Leer más libros durante el año",
      "Comer de manera más saludable",
      "Dormir mejor y cuidar mi descanso",
      "Organizar mejor mi tiempo",
      "Viajar y conocer nuevos lugares",
      "Pasar más tiempo con mi familia",
      "Cuidar mi salud mental y emocional"
    ];

    let disponibles = [...propositos];

    const box = document.getElementById("proposito");
    const btn = document.getElementById("btnNuevo");

    function nuevoProposito() {
      if (disponibles.length === 0) {
        disponibles = [...propositos];
      }

      const i = Math.floor(Math.random() * disponibles.length);
      const texto = disponibles.splice(i, 1)[0];

      box.classList.remove("animate");
      void box.offsetWidth;
      box.textContent = texto;
      box.classList.add("animate");

      const b = document.createElement("div");
      b.className = "burst";
      document.body.appendChild(b);
      setTimeout(() => b.remove(), 800);
    }

    btn.addEventListener("click", nuevoProposito);
  </script>
</body>
</html>
