<!DOCTYPE html>

<html lang="es">

<head>

  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Cartera de Bolsa</title>

  <!-- Google Fonts -->

  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">

  <style>

    :root {

      --primary-color: #2E3A59;

      --secondary-color: #F9F9FA;

      --accent-color: #4CAF50;

      --text-color: #333333;

      --bg-color: #FFFFFF;

      --card-bg: #FFFFFF;

      --border-radius: 12px;

      --box-shadow: 0 4px 12px rgba(0,0,0,0.05);

    }

    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {

      font-family: 'Inter', sans-serif;

      background-color: var(--bg-color);

      color: var(--text-color);

      line-height: 1.6;

    }

    header {

      background-color: var(--primary-color);

      color: var(--secondary-color);

      padding: 1rem 2rem;

      display: flex;

      justify-content: space-between;

      align-items: center;

      box-shadow: var(--box-shadow);

    }

    header h1 { font-weight: 600; font-size: 1.5rem; }

    nav a {

      color: var(--secondary-color);

      margin-left: 1rem;

      text-decoration: none;

      font-weight: 500;

    }

    main {

      padding: 2rem;

      max-width: 1200px;

      margin: 0 auto;

    }

    .overview {

      display: flex;

      flex-wrap: wrap;

      gap: 1.5rem;

      margin-bottom: 2rem;

    }

    .card {

      background: var(--card-bg);

      border-radius: var(--border-radius);

      box-shadow: var(--box-shadow);

      padding: 1.5rem;

      flex: 1;

      min-width: 240px;

    }

    .card h2 {

      font-size: 1.25rem;

      margin-bottom: 0.5rem;

      font-weight: 600;

    }

    .card p {

      font-size: 2rem;

      font-weight: 700;

      color: var(--accent-color);

    }

    .holdings {

      width: 100%;

      overflow-x: auto;

      margin-bottom: 2rem;

    }

    table {

      width: 100%;

      border-collapse: collapse;

    }

    th, td {

      padding: 0.75rem 1rem;

      text-align: left;

      border-bottom: 1px solid #e0e0e0;

    }

    th {

      background-color: var(--secondary-color);

      font-weight: 600;

    }

    tr:hover { background-color: #f5f5f5; }

    .chart-container {

      background: var(--card-bg);

      border-radius: var(--border-radius);

      box-shadow: var(--box-shadow);

      padding: 1.5rem;

    }

    .chart-container canvas {

      width: 100%;

      height: 300px;

    }

    footer {

      text-align: center;

      padding: 1rem;

      background-color: var(--secondary-color);

      color: var(--text-color);

      margin-top: 2rem;

    }

    @media (max-width: 768px) {

      .overview { flex-direction: column; }

    }

  </style>

</head>

<body>

  <header>

    <h1>Cartera de Bolsa</h1>

    <nav>

      <a href="#">Inicio</a>

      <a href="#holdings">Posiciones</a>

      <a href="#chart">Gráfica</a>

      <a href="#">Perfil</a>

    </nav>

  </header>

  

  <main>

    <!-- Sección de Resumen -->

    <section class="overview">

      <div class="card">

        <h2>Valor Total</h2>

        <p>€25,430.75</p>

      </div>

      <div class="card">

        <h2>Ganancia / Pérdida</h2>

        <p>+€1,230.50</p>

      </div>

      <div class="card">

        <h2>Rendimiento (%)</h2>

        <p>+5.09%</p>

      </div>

    </section>

  

    <!-- Tabla de Posiciones -->

    <section id="holdings" class="holdings">

      <table>

        <thead>

          <tr>

            <th>Acción</th>

            <th>Cantidad</th>

            <th>Precio Actual</th>

            <th>Valor Total</th>

            <th>Var. Día</th>

          </tr>

        </thead>

        <tbody>

          <tr>

            <td>APPL</td>

            <td>50</td>

            <td>€150.25</td>

            <td>€7,512.50</td>

            <td>+1.25%</td>

          </tr>

          <tr>

            <td>GOOGL</td>

            <td>10</td>

            <td>€2,500.00</td>

            <td>€25,000.00</td>

            <td>-0.75%</td>

          </tr>

          <!-- Más filas según sea necesario -->

        </tbody>

      </table>

    </section>

  

    <!-- Gráfica de Rendimiento -->

    <section id="chart" class="chart-container">

      <h2>Rendimiento Histórico</h2>

      <canvas id="portfolioChart"></canvas>

    </section>

  </main>

  

  <footer>

    &copy; 2025 Cartera de Bolsa. Todos los derechos reservados.

  </footer>

  

  <!-- Chart.js -->

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <script>

    const ctx = document.getElementById('portfolioChart').getContext('2d');

    const labels = ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul'];

    const data = {

      labels: labels,

      datasets: [{

        label: 'Valor Cartera',

        data: [22000, 22500, 23000, 23500, 24000, 24500, 25430.75],

        fill: true,

        tension: 0.4,

        borderColor: 'rgba(75, 192, 192, 1)',

        backgroundColor: 'rgba(75, 192, 192, 0.2)'

      }]

    };

    new Chart(ctx, {

      type: 'line',

      data: data,

      options: {

        responsive: true,

        scales: {

          y: { beginAtZero: false }

        }

      }

    });

  </script>

</body>

</html>