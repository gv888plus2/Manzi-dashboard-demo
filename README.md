# Manzi-dashboard-demo<!DOCTYPE html>
<html>
<head>
    <title>Manzi Water Command Center</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        :root { --manzi-blue: #1a5f9e; --manzi-green: #4caf50; }
        body { font-family: 'Segoe UI', sans-serif; margin: 0; padding: 20px; background: #f8f9fa; }
        .dashboard-header { background: linear-gradient(120deg, var(--manzi-blue), #28a745); color: white; padding: 20px; border-radius: 10px; margin-bottom: 20px; }
        .kpi-container { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 15px; margin-bottom: 25px; }
        .kpi-card { background: white; border-radius: 8px; padding: 15px; box-shadow: 0 3px 10px rgba(0,0,0,0.08); }
        .kpi-value { font-size: 2em; font-weight: 700; margin: 10px 0; }
        .table-container { margin: 25px 0; background: white; padding: 15px; border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15); }
        table { width: 100%; border-collapse: collapse; }
        th, td { padding: 12px; text-align: left; border-bottom: 1px solid #ddd; }
        tr:hover { background-color: #f5f5f5; }
        .status-active { color: var(--manzi-green); font-weight: bold; }
        .status-downtime { color: #d32f2f; font-weight: bold; }
        .chart-row { display: flex; gap: 20px; margin-top: 30px; flex-wrap: wrap; }
        .chart-container { flex: 1; min-width: 300px; background: white; padding: 15px; border-radius: 8px; box-shadow: 0 3px 10px rgba(0,0,0,0.08); }
    </style>
</head>
<body>
    <div class="dashboard-header">
        <h1>MANZI WATER STRATEGIC COMMAND CENTER</h1>
        <p>Real-time Operations • Franchise Risk • Sustainability Impact</p>
    </div>

    <!-- KPI CARDS -->
    <div class="kpi-container">
        <div class="kpi-card" style="border-left: 4px solid var(--manzi-blue);">
            <div>Total Outlets</div>
            <div class="kpi-value" id="totalOutlets">105</div>
            <div>+8 this month</div>
        </div>
        <div class="kpi-card" style="border-left: 4px solid var(--manzi-green);">
            <div>Plastic Saved</div>
            <div class="kpi-value" id="plasticSaved">28,560 kg</div>
            <div>Equivalent to 1.2M bottles</div>
        </div>
        <div class="kpi-card" style="border-left: 4px solid #ff6b00;">
            <div>Franchise Risk</div>
            <div class="kpi-value" id="highRisk">3 ALERTS</div>
            <div>Oasis conflicts in Gauteng</div>
        </div>
        <div class="kpi-card" style="border-left: 4px solid #d32f2f;">
            <div>Revenue Loss</div>
            <div class="kpi-value" id="downtimeLoss">R42,800</div>
            <div>From station downtime</div>
        </div>
    </div>

    <!-- OUTLET STATUS TABLE -->
    <div class="table-container">
        <h2>Outlet Status Overview</h2>
        <table>
            <thead>
                <tr>
                    <th>Outlet Name</th>
                    <th>Location</th>
                    <th>Status</th>
                    <th>Last Update</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Port Elizabeth (Walmer)</td>
                    <td>Eastern Cape</td>
                    <td class="status-active">Active</td>
                    <td>10 mins ago</td>
                </tr>
                <tr>
                    <td>Johannesburg (Sandton)</td>
                    <td>Gauteng</td>
                    <td class="status-downtime">Downtime</td>
                    <td>1 hour ago</td>
                </tr>
                <tr>
                    <td>Cape Town CBD</td>
                    <td>Western Cape</td>
                    <td class="status-active">Active</td>
                    <td>15 mins ago</td>
                </tr>
                <tr>
                    <td>Kuruman Refill Station</td>
                    <td>Northern Cape</td>
                    <td class="status-active">Active</td>
                    <td>5 mins ago</td>
                </tr>
            </tbody>
        </table>
    </div>

    <!-- CHARTS -->
    <div class="chart-row">
        <div class="chart-container">
            <canvas id="sustainabilityChart"></canvas>
        </div>
        <div class="chart-container">
            <canvas id="revenueChart"></canvas>
        </div>
    </div>

    <script>
        // ===== SUSTAINABILITY CHART =====
        new Chart(document.getElementById('sustainabilityChart'), {
            type: 'bar',
            data: {
                labels: ['Plastic Saved', 'CO2 Reduced', 'Water Provided'],
                datasets: [{
                    label: 'Monthly Impact',
                    data: [28560, 42, 845000],
                    backgroundColor: ['#4caf50', '#2196f3', '#1a5f9e']
                }]
            },
            options: {
                plugins: { 
                    title: { display: true, text: 'SUSTAINABILITY IMPACT (Liters/Kg)' }
                }
            }
        });

        // ===== REVENUE CHART =====
        new Chart(document.getElementById('revenueChart'), {
            type: 'line',
            data: {
                labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May'],
                datasets: [{
                    label: 'Still Water Sales',
                    data: [185000, 210000, 198000, 240000, 265000],
                    borderColor: '#1a5f9e',
                    tension: 0.3
                },{
                    label: 'Sparkling/Juice',
                    data: [42000, 48000, 51000, 62500, 71000],
                    borderColor: '#4caf50',
                    tension: 0.3
                }]
            },
            options: {
                plugins: { 
                    title: { display: true, text: 'REVENUE GROWTH (Rand)' }
                }
            }
        });

        // ===== DYNAMIC KPI UPDATES =====
        setInterval(() => {
            // Simulate live data changes for downtime loss
            document.getElementById('downtimeLoss').textContent = 
                'R' + (42000 + Math.floor(Math.random() * 5000)).toLocaleString();
        }, 5000);
    </script>
</body>
</html>
