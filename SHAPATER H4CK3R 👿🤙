<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>CORE IDENTITY RESOLVER | V2.0</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --neon-cyan: #00f2ff;
            --neon-purple: #bc13fe;
            --neon-red: #ff0055;
            --bg-deep: #020617;
            --glass: rgba(255, 255, 255, 0.03);
            --border-glow: rgba(0, 242, 255, 0.4);
        }

        * { box-sizing: border-box; margin: 0; padding: 0; cursor: crosshair; }

        body {
            background-color: var(--bg-deep);
            color: #fff;
            font-family: 'Rajdhani', sans-serif;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 50% 50%, rgba(0, 242, 255, 0.1) 0%, transparent 80%),
                linear-gradient(rgba(0, 242, 255, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 242, 255, 0.05) 1px, transparent 1px);
            background-size: 100% 100%, 30px 30px, 30px 30px;
        }

        .main-wrapper {
            width: 95%;
            max-width: 480px;
            position: relative;
            padding: 20px;
        }

        /* --- LOGO ANIMATION --- */
        .logo-container {
            position: relative;
            width: 150px;
            height: 150px;
            margin: 0 auto 30px;
        }

        .logo-ring {
            position: absolute;
            width: 100%;
            height: 100%;
            border: 2px solid var(--neon-cyan);
            border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%;
            animation: morph 8s linear infinite;
        }

        .logo-ring.inner {
            width: 80%; height: 80%; top: 10%; left: 10%;
            border-color: var(--neon-purple);
            animation-direction: reverse;
        }

        .logo-img {
            position: absolute;
            width: 100px;
            height: 100px;
            top: 25px; left: 25px;
            border-radius: 50%;
            object-fit: cover;
            border: 2px solid #fff;
            box-shadow: 0 0 25px var(--neon-cyan);
            z-index: 5;
            background: #000;
        }

        @keyframes morph {
            0% { border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%; transform: rotate(0deg); }
            50% { border-radius: 26% 74% 42% 58% / 28% 32% 68% 72%; }
            100% { border-radius: 38% 62% 63% 37% / 41% 44% 56% 59%; transform: rotate(360deg); }
        }

        /* --- UI CARD --- */
        .search-card {
            background: rgba(10, 15, 30, 0.8);
            backdrop-filter: blur(20px);
            border: 1px solid var(--border-glow);
            border-radius: 20px;
            padding: 35px 25px;
            box-shadow: 0 0 40px rgba(0, 242, 255, 0.1);
            position: relative;
            overflow: hidden;
        }

        input {
            width: 100%;
            background: rgba(0, 0, 0, 0.6);
            border: 1px solid var(--neon-purple);
            padding: 20px;
            border-radius: 12px;
            color: #fff;
            font-family: 'Orbitron', sans-serif;
            font-size: 1.1rem;
            text-align: center;
            margin-bottom: 20px;
        }

        .btn-glow {
            width: 100%;
            padding: 18px;
            background: linear-gradient(45deg, var(--neon-cyan), var(--neon-purple));
            border: none;
            color: #000;
            font-family: 'Orbitron', sans-serif;
            font-weight: 900;
            border-radius: 12px;
            cursor: pointer;
            text-transform: uppercase;
        }

        .btn-group { display: flex; gap: 10px; margin-top: 20px; }
        .mini-link {
            flex: 1; padding: 12px; text-decoration: none; color: #fff;
            font-size: 0.75rem; font-weight: bold; border-radius: 8px;
            background: rgba(255,255,255,0.05); border: 1px solid rgba(255,255,255,0.1);
            text-align: center;
        }

        /* --- RESULTS --- */
        .data-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid var(--neon-cyan);
            border-radius: 15px;
            padding: 15px;
            margin-top: 20px;
        }
        .data-strip {
            padding: 12px;
            border-bottom: 1px solid rgba(0, 242, 255, 0.1);
            display: flex;
            justify-content: space-between;
        }
        .loader { display: none; text-align: center; margin: 20px; color: var(--neon-cyan); }
    </style>
</head>
<body>

<div class="main-wrapper">
    <div class="logo-container">
        <div class="logo-ring"></div>
        <div class="logo-ring inner"></div>
        <img src="https://new-hosting.page.gd/view.php?file=Selfish%20girl%20logo.jpg&u=90" alt="Core" class="logo-img" loading="eager">
    </div>

    <div class="search-card">
        <input type="tel" id="queryInput" placeholder="ENTER PHONE NUMBER" maxlength="11">
        <button class="btn-glow" onclick="executeSearch()">
            <i class="fas fa-microchip"></i> Start Deep Scan
        </button>

        <div class="btn-group">
            <a href="https://wa.me/27740532694?text=Hello%20Admin,%20I%20need%20help%20with%20the%20Core%20Identity%20Resolver." target="_blank" class="mini-link"><i class="fab fa-whatsapp"></i> SUPPORT</a>
            <a href="https://whatsapp.com/channel/0029Vb6NKJ5GehEHnqkoKx3d" target="_blank" class="mini-link"><i class="fas fa-satellite-dish"></i> CHANNEL</a>
        </div>
    </div>

    <div id="loader" class="loader"><i class="fas fa-atom fa-spin fa-3x"></i><p>DECRYPTING...</p></div>
    <div id="display-area"></div>
</div>

<script>
    const API_URL = "https://howler-database-api.vercel.app/api/lookup?phone=";

    async function executeSearch() {
        const phone = document.getElementById('queryInput').value.trim();
        const area = document.getElementById('display-area');
        const loader = document.getElementById('loader');

        if(phone.length < 10) { alert("ENTER VALID NUMBER"); return; }

        area.innerHTML = '';
        loader.style.display = 'block';

        try {
            const response = await fetch(`${API_URL}${phone}`);
            const data = await response.json();
            loader.style.display = 'none';

            if (data.success && data.result) {
                data.result.forEach(item => {
                    area.innerHTML += `
                    <div class="data-card">
                        <div class="data-strip"><span>NAME</span><span>${item.name}</span></div>
                        <div class="data-strip"><span>CNIC</span><span>${item.cnic}</span></div>
                        <div class="data-strip"><span>ADDRESS</span><span>${item.address}</span></div>
                    </div>`;
                });
            } else {
                area.innerHTML = "<p style='text-align:center; color:red;'>NOT FOUND</p>";
            }
        } catch (e) { loader.style.display = 'none'; }
    }
</script>

</body>
</html>
