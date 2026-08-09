<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🎉 Party Invite | With Admin & Video 🎉</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            color: #fff;
            overflow-x: hidden;
            position: relative;
        }

        /* ----- FULLSCREEN BACKGROUND VIDEO ----- */
        .bg-video {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            object-fit: cover;
            z-index: -2;
        }
        .video-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: rgba(0,0,0,0.55); /* dim for readability */
            z-index: -1;
        }

        /* ----- HERO ----- */
        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 2rem;
        }
        .hero h1 {
            font-size: clamp(2.5rem, 6vw, 5rem);
            margin-bottom: 1.5rem;
            text-shadow: 0 0 20px rgba(0,0,0,0.6);
            animation: pulse 2s infinite alternate;
        }
        .hero p.tagline {
            font-size: clamp(1.2rem, 3vw, 2rem);
            margin-bottom: 3rem;
            max-width: 800px;
        }
        @keyframes pulse {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }

        /* ----- BUTTONS ----- */
        .btn {
            padding: 1rem 2.5rem;
            font-size: 1.2rem;
            border: none;
            border-radius: 50px;
            background: #fff;
            color: #e91e63;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            text-decoration: none;
            display: inline-block;
            margin: 0.5rem;
        }
        .btn:hover {
            transform: translateY(-5px);
            background: #222;
            color: #fff;
        }
        .btn-admin { background: #ffc107; color: #000; }
        .btn-admin:hover { background: #b78900; color: #fff; }

        /* ----- COUNTDOWN ----- */
        .countdown {
            display: flex;
            gap: 1.5rem;
            justify-content: center;
            flex-wrap: wrap;
            margin: 2rem 0;
        }
        .count-box {
            background: rgba(0,0,0,0.4);
            padding: 1rem 1.5rem;
            border-radius: 10px;
            min-width: 80px;
            backdrop-filter: blur(8px);
        }
        .count-box span {
            font-size: 2.5rem;
            font-weight: bold;
            display: block;
        }

        /* ----- DETAILS ----- */
        .section-title {
            text-align: center;
            font-size: 2.2rem;
            margin: 4rem 0 2rem;
        }
        .details {
            max-width: 1000px;
            margin: 0 auto 4rem;
            padding: 0 2rem;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }
        .detail-card {
            background: rgba(255,255,255,0.15);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(255,255,255,0.2);
        }
        .detail-card h3 { margin-bottom: 1rem; font-size: 1.5rem; }

        /* ----- RSVP ----- */
        .rsvp {
            max-width: 600px;
            margin: 0 auto 5rem;
            padding: 0 2rem;
        }
        .rsvp-form {
            background: rgba(255,255,255,0.15);
            backdrop-filter: blur(10px);
            padding: 2.5rem;
            border-radius: 15px;
            border: 1px solid rgba(255,255,255,0.2);
        }
        .rsvp-form input, .rsvp-form select, .admin-form input, .admin-form textarea {
            width: 100%;
            padding: 1rem;
            margin: 0.5rem 0 1.5rem;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
        }

        /* ----- ADMIN PORTAL ----- */
        .admin-login, .admin-panel {
            max-width: 700px;
            margin: 3rem auto;
            padding: 2rem;
            background: rgba(0,0,0,0.7);
            border-radius: 15px;
            display: none;
        }
        .admin-panel.active, .admin-login.active { display: block; }
        .admin-form label { display: block; margin: 1rem 0 0.3rem; font-weight: bold; }

        /* ----- FOOTER ----- */
        footer { text-align: center; padding: 2rem; opacity: 0.8; }
    </style>
</head>
<body>

    <!-- 🎥 AUTOPLAY BACKGROUND VIDEO (muted required for browsers!) -->
    <video class="bg-video" autoplay muted loop playsinline>
        <source src="https://assets.mixkit.co/videos/preview/mixkit-people-dancing-at-a-colorful-party-4223-large.mp4" type="video/mp4">
        Your browser does not support video.
    </video>
    <div class="video-overlay"></div>


    <!-- 🔘 ADMIN BUTTON -->
    <button class="btn btn-admin" style="position:fixed; top:15px; right:15px; z-index:999;" onclick="toggleAdminLogin()">⚙️ Admin</button>


    <!-- 🎉 MAIN PARTY SITE -->
    <section class="hero">
        <h1 id="main-title">🎉 SUMMER BASH PARTY 🎉</h1>
        <p class="tagline" id="main-tagline">Food • Music • Dancing • Great Memories<br>Join the biggest party of the season!</p>

        <div class="countdown">
            <div class="count-box"><span id="days">00</span>Days</div>
            <div class="count-box"><span id="hours">00</span>Hours</div>
            <div class="count-box"><span id="minutes">00</span>Mins</div>
            <div class="count-box"><span id="seconds">00</span>Secs</div>
        </div>

        <a href="#rsvp" class="btn">RSVP NOW</a>
    </section>


    <h2 class="section-title">Party Details</h2>
    <section class="details">
        <div class="detail-card">
            <h3>📅 When</h3>
            <p id="text-date">Saturday 22 August 2026<br>4:00 PM till late</p>
        </div>
        <div class="detail-card">
            <h3>📍 Where</h3>
            <p id="text-location">Sunset Garden, London W5<br><a href="#" style="color:#fff; text-decoration:underline;">View Map</a></p>
        </div>
        <div class="detail-card">
            <h3>🎊 What's On</h3>
            <p id="text-extras">Live DJ • Free Food & Drinks<br>Games • Photo Booth • Prizes</p>
        </div>
    </section>


    <section class="rsvp" id="rsvp">
        <h2 class="section-title">Can You Come?</h2>
        <form class="rsvp-form" onsubmit="return alert('Thanks for RSVP! 🥳')">
            <input type="text" placeholder="Your Full Name" required>
            <input type="email" placeholder="Your Email" required>
            <select required>
                <option value="">I will attend?</option>
                <option>Yes! 🎉</option>
                <option>No, sadly 😔</option>
            </select>
            <button type="submit" class="btn">Send RSVP</button>
        </form>
    </section>


    <!-- 🔐 ADMIN LOGIN & EDIT PORTAL -->
    <div class="admin-login" id="adminLoginBox">
        <h2 style="text-align:center; margin-bottom:1rem;">Admin Login</h2>
        <input type="password" id="adminPass" placeholder="Enter Admin Password (default: 1234)">
        <button class="btn" onclick="adminLogin()">Login</button>
    </div>

    <div class="admin-panel" id="adminPanelBox">
        <h2 style="text-align:center; margin-bottom:1rem;">✏️ Edit Party Details</h2>
        <form class="admin-form" onsubmit="saveEdits(event)">
            <label>Main Title</label>
            <input type="text" id="edit-title">

            <label>Tagline</label>
            <textarea id="edit-tagline" rows="3"></textarea>

            <label>Date & Time Text</label>
            <textarea id="edit-date" rows="2"></textarea>

            <label>Location Text</label>
            <textarea id="edit-location" rows="2"></textarea>

            <label>What's On / Extras</label>
            <textarea id="edit-extras" rows="3"></textarea>

            <label>Party Date (for Countdown: YYYY-MM-DD HH:MM)</label>
            <input type="text" id="edit-partydate" placeholder="2026-08-22 16:00">

            <button type="submit" class="btn">💾 Save All Changes</button>
            <button type="button" class="btn" onclick="adminLogout()">🚪 Logout</button>
        </form>
    </div>


    <footer id="footer-text">© 2026 Summer Bash Party — Let’s celebrate!</footer>


    <script>
        // ---- LOAD SAVED CONTENT ON START ----
        window.onload = function() {
            const saved = JSON.parse(localStorage.getItem('partyContent'));
            if(saved) {
                document.getElementById('main-title').innerText = saved.title;
                document.getElementById('main-tagline').innerHTML = saved.tagline;
                document.getElementById('text-date').innerHTML = saved.dateText;
                document.getElementById('text-location').innerHTML = saved.locText;
                document.getElementById('text-extras').innerHTML = saved.extraText;
                startCountdown(saved.partyDate || "2026-08-22 16:00");
            } else {
                startCountdown("2026-08-22 16:00");
            }
        };

        // ---- ADMIN LOGIC ----
        function toggleAdminLogin() {
            document.getElementById('adminLoginBox').classList.toggle('active');
        }
        function adminLogin() {
            const pass = document.getElementById('adminPass').value;
            if(pass === "1234") { // change password here!
                document.getElementById('adminLoginBox').classList.remove('active');
                document.getElementById('adminPanelBox').classList.add('active');
                // fill form with current values
                document.getElementById('edit-title').value = document.getElementById('main-title').innerText;
                document.getElementById('edit-tagline').value = document.getElementById('main-tagline').innerHTML.replace(/<br\s*[\/]?>/gi, '\n');
                document.getElementById('edit-date').value = document.getElementById('text-date').innerHTML.replace(/<br\s*[\/]?>/gi, '\n');
                document.getElementById('edit-location').value = document.getElementById('text-location').innerHTML.replace(/<br\s*[\/]?>/gi, '\n');
                document.getElementById('edit-extras').value = document.getElementById('text-extras').innerHTML.replace(/<br\s*[\/]?>/gi, '\n');
            } else alert("Wrong password!");
        }
        function adminLogout() {
            document.getElementById('adminPanelBox').classList.remove('active');
        }

        // ---- SAVE EDITS TO BROWSER STORAGE ----
        function saveEdits(e) {
            e.preventDefault();
            // replace newlines with <br>
            const title = document.getElementById('edit-title').value;
            const tagline = document.getElementById('edit-tagline').value.replace(/\n/g, '<br>');
            const dateText = document.getElementById('edit-date').value.replace(/\n/g, '<br>');
            const locText = document.getElementById('edit-location').value.replace(/\n/g, '<br>');
            const extraText = document.getElementById('edit-extras').value.replace(/\n/g, '<br>');
            const partyDate = document.getElementById('edit-partydate').value;

            // update live page
            document.getElementById('main-title').innerText = title;
            document.getElementById('main-tagline').innerHTML = tagline;
            document.getElementById('text-date').innerHTML = dateText;
            document.getElementById('text-location').innerHTML = locText;
            document.getElementById('text-extras').innerHTML = extraText;

            // save locally
            const content = {title, tagline, dateText, locText, extraText, partyDate};
            localStorage.setItem('partyContent', JSON.stringify(content));

            if(partyDate) startCountdown(partyDate);
            alert("✅ Saved! Changes stay even after closing browser!");
        }

        // ---- COUNTDOWN TIMER ----
        function startCountdown(dateStr) {
            const partyTime = new Date(dateStr).getTime();
            setInterval(() => {
                const now = Date.now();
                const diff = partyTime - now;
                if(diff < 0) {
                    document.getElementById('days').innerText = "00";
                    document.getElementById('hours').innerText = "00";
                    document.getElementById('minutes').innerText = "00";
                    document.getElementById('seconds').innerText = "00";
                    return;
                }
                const days = Math.floor(diff/(1000*60*60*24));
                const hours = Math.floor((diff%(1000*60*60*24))/(1000*60*60));
                const mins = Math.floor((diff%(1000*60*60))/(1000*60));
                const secs = Math.floor((diff%(1000*60))/1000);
                document.getElementById('days').innerText = String(days).padStart(2,'0');
                document.getElementById('hours').innerText = String(hours).padStart(2,'0');
                document.getElementById('minutes').innerText = String(mins).padStart(2,'0');
                document.getElementById('seconds').innerText = String(secs).padStart(2,'0');
            }, 1000);
        }
    </script>
</body>
</html>
