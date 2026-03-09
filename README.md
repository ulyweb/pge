



```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Power Plan</title>
    <style>
        /* Base styles for Desktop & Tablet */
        body { 
            font-family: Arial, sans-serif; 
            background-color: #2c3e50; 
            color: #fff; 
            padding: 20px; 
            text-align: center;
            font-size: 140%; 
        }
        
        h1 { font-size: 2.5em; text-shadow: 2px 2px 4px #000; margin-bottom: 5px; }
        
        .subtitle { 
            font-size: 1.8em; 
            color: #4da6ff; 
            text-shadow: 1px 1px 3px #000; 
            margin-top: 0; 
            margin-bottom: 20px; 
            font-weight: bold;
        }
        
        .dashboard { 
            display: flex; 
            flex-direction: column; 
            gap: 30px; 
            max-width: 800px; 
            margin: 0 auto; 
        }
        
        .card { 
            padding: 30px; 
            border-radius: 20px; 
            box-shadow: 0 10px 20px rgba(0,0,0,0.5); 
            border: 6px solid transparent;
        }
        
        .icon { font-size: 4em; margin-bottom: 10px; }
        
        .green-light { background: linear-gradient(145deg, #1e7e34, #28a745); }
        .yellow-light { background: linear-gradient(145deg, #d39e00, #ffc107); color: #000; }
        .red-light { background: linear-gradient(145deg, #bd2130, #dc3545); }
        
        h2 { font-size: 2.2em; margin: 10px 0; }
        
        .price { 
            font-size: 1.6em; 
            font-weight: bold; 
            background: rgba(255,255,255,0.3); 
            display: inline-block; 
            padding: 10px 20px; 
            border-radius: 10px; 
            margin: 15px 0; 
        }
        
        .action { font-size: 1.5em; font-weight: bold; }

        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(255, 255, 255, 0.8); }
            70% { box-shadow: 0 0 0 25px rgba(255, 255, 255, 0); }
            100% { box-shadow: 0 0 0 0 rgba(255, 255, 255, 0); }
        }
        
        .active-now {
            animation: pulse 2s infinite;
            border: 6px solid #fff;
            transform: scale(1.03);
        }

        /* Responsive styles for Mobile Devices */
        @media (max-width: 600px) {
            body { font-size: 100%; padding: 10px; }
            h1 { font-size: 2em; }
            .subtitle { font-size: 1.4em; }
            .dashboard { gap: 15px; }
            .card { padding: 20px; border-radius: 15px; }
            .icon { font-size: 3em; }
            h2 { font-size: 1.8em; }
            .price { font-size: 1.3em; padding: 8px 15px; }
            .action { font-size: 1.3em; }
            .active-now { transform: scale(1.02); }
        }
    </style>
</head>
<body>

    <h1>⚡ Live Power Dashboard ⚡</h1>
    <div class="subtitle">PG&E EV2-A Plan</div>
    
    <p style="font-size: 1.8em; font-weight: bold;">Current Time: <span id="clock">Loading...</span></p>

    <div class="dashboard">
        <div id="green-card" class="card green-light">
            <div class="icon">🚗 🍽️ 👕</div>
            <h2>🟢 12:00 AM to 3:00 PM</h2>
            <div class="price">Rate: ~$0.39 / kWh</div>
            <div class="action">GO! Do the heavy lifting now!</div>
        </div>

        <div id="yellow-card" class="card yellow-light">
            <div class="icon">⚠️ 🧹 📺</div>
            <h2>🟡 3:00 PM to 4:00 PM<br>& 9:00 PM to 12:00 AM</h2>
            <div class="price">Rate: ~$0.58 / kWh</div>
            <div class="action">CAUTION! Finish up chores.</div>
        </div>

        <div id="red-card" class="card red-light">
            <div class="icon">🛑 📚 🎲</div>
            <h2>🔴 4:00 PM to 9:00 PM</h2>
            <div class="price">Rate: ~$0.61 / kWh</div>
            <div class="action">STOP! No heavy appliances!</div>
        </div>
    </div>

    <script>
        function updateDashboard() {
            const now = new Date();
            document.getElementById('clock').innerText = now.toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
            
            const hour = now.getHours(); 
            
            document.getElementById('green-card').classList.remove('active-now');
            document.getElementById('yellow-card').classList.remove('active-now');
            document.getElementById('red-card').classList.remove('active-now');

            if (hour >= 0 && hour < 15) {
                document.getElementById('green-card').classList.add('active-now');
            } else if (hour >= 16 && hour < 21) {
                document.getElementById('red-card').classList.add('active-now');
            } else {
                document.getElementById('yellow-card').classList.add('active-now');
            }
        }
        
        setInterval(updateDashboard, 1000);
        updateDashboard(); 
    </script>
</body>
</html>


```
