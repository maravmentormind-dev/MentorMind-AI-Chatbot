<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MentorMind | Founded by R. MARAV</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        body { background: #0b0d11; font-family: 'Inter', sans-serif; overflow: hidden; }
        #auth-gate { display: flex; position: fixed; inset: 0; background: #0b0d11; z-index: 2000; align-items: center; justify-content: center; }
        .auth-card { background: #161922; border: 1px solid #2d333f; padding: 40px; border-radius: 30px; width: 100%; max-width: 400px; text-align: center; }
        #main-app { display: none; height: 100vh; width: 100vw; background: #fcfcfc; color: #1a1a1a; }
        .sidebar { background: #ffffff; border-right: 1px solid #eee; width: 280px; }
        .tool-btn { background: #f8fafc; border: 1px solid #e2e8f0; padding: 10px; border-radius: 12px; margin-bottom: 8px; font-size: 11px; cursor: pointer; text-align: left; transition: 0.2s; }
        .tool-btn:hover { background: #eff6ff; border-color: #3b82f6; }
        video { width: 100%; border-radius: 12px; margin-top: 10px; display: none; border: 2px solid #3b82f6; }
    </style>
</head>
<body class="flex">

    <!-- 1. LOGIN GATE (R.MARAV STYLE) -->
    <div id="auth-gate">
        <div class="auth-card shadow-2xl">
            <h1 class="text-4xl font-black italic tracking-tighter text-blue-500 mb-2 leading-none text-center">MentorMind</h1>
            <p class="text-gray-400 text-sm mb-10 italic">"Life-Changing Education for Students"</p>
            <div class="flex gap-4 mb-8">
                <button onclick="access()" class="flex-1 py-4 bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-2xl shadow-lg">LOGIN</button>
                <button onclick="access()" class="flex-1 py-4 bg-white text-black font-bold rounded-2xl border-2 border-white hover:bg-gray-200">SIGN UP</button>
            </div>
            <div class="flex justify-center gap-6 mb-8 text-gray-400 text-3xl">
                <i onclick="access()" class="fab fa-google hover:text-white cursor-pointer transition"></i>
                <i onclick="access()" class="fab fa-apple hover:text-white cursor-pointer transition"></i>
                <i onclick="access()" class="fab fa-windows hover:text-white cursor-pointer transition"></i>
            </div>
            <p class="text-[9px] text-gray-600 font-bold uppercase tracking-[0.3em]">Founded by R. MARAV</p>
        </div>
    </div>

    <!-- 2. MAIN APPLICATION -->
    <div id="main-app" class="flex w-full">
        <!-- SIDEBAR -->
        <aside class="sidebar flex flex-col p-6 shadow-sm">
            <div class="text-2xl font-black italic text-blue-600 mb-8 tracking-tighter">MentorMind</div>
            
            <p class="text-[10px] font-bold text-gray-400 mb-3 tracking-widest uppercase italic border-b pb-1">📚 Formula Vault</p>
            <div onclick="setQ('Math: Quadratic Formula derivation')" class="tool-btn font-bold italic text-blue-800">● Math: Algebra</div>
            <div onclick="setQ('Physics: Force and Motion formulas')" class="tool-btn font-bold italic text-blue-800">● Physics: Dynamics</div>

            <p class="text-[10px] font-bold text-gray-400 mb-3 tracking-widest uppercase italic border-b pb-1 mt-6">🧬 Classifications</p>
            <div onclick="setQ('Biology: 5 Kingdoms Classification')" class="tool-btn font-bold italic text-green-800">● Bio: Taxonomy</div>
            <div onclick="setQ('Chemistry: Periodic Table Group 18')" class="tool-btn font-bold italic text-green-800">● Chem: Noble Gases</div>

            <p class="text-[10px] font-bold text-gray-400 mb-2 mt-8 tracking-widest">ACTIVITY</p>
            <div id="history" class="text-[10px] text-gray-300 italic flex-1 overflow-y-auto">No recent history...</div>
            
            <video id="webcam" autoplay playsinline></video>

            <div class="mt-auto border-t pt-5 flex items-center gap-3">
                <div class="bg-blue-600 w-10 h-10 rounded-full flex items-center justify-center text-white text-xs font-bold shadow-md">MM</div>
                <div class="flex-1 overflow-hidden">
                    <p class="text-sm font-bold truncate">R. MARAV</p>
                    <p class="text-[9px] text-blue-500 font-black uppercase tracking-tighter">CREATOR / ADMIN</p>
                </div>
            </div>
        </aside>

        <!-- MAIN DASHBOARD -->
        <main class="flex-1 flex flex-col items-center justify-center p-8 relative">
            <h1 class="text-4xl font-bold text-gray-800 mb-14 tracking-tight italic">How can I help you study today?</h1>
            
            <!-- INPUT BAR (Real Enter Working) -->
            <div class="w-full max-w-2xl bg-white border border-gray-200 rounded-[2.5rem] p-2 shadow-xl flex items-center px-8 gap-5 transition duration-300 focus-within:border-blue-300">
                <i onclick="cam()" class="fa-solid fa-camera text-gray-300 hover:text-blue-500 cursor-pointer"></i>
                <i onclick="mic()" class="fa-solid fa-microphone text-gray-300 hover:text-red-500 cursor-pointer"></i>
                
                <input id="q-input" 
                       onkeydown="checkEnter(event)" 
                       placeholder="Ask MentorMind anything..." 
                       class="flex-1 outline-none text-xl py-4 placeholder:text-gray-300 font-medium italic" />
                
                <button onclick="askAI()" class="text-4xl text-blue-600 transition hover:scale-110 active:scale-90">
                    <i class="fa-solid fa-circle-arrow-up"></i>
                </button>
            </div>

            <!-- FAKE STATS (789+ Students) -->
            <div class="flex gap-4 mt-10">
                <div class="px-5 py-2 bg-blue-50 text-blue-600 rounded-full text-[10px] font-black uppercase tracking-widest italic border border-blue-100 italic">789+ Students Verified</div>
                <div class="px-5 py-2 bg-yellow-50 text-yellow-600 rounded-full text-[10px] font-black uppercase tracking-widest italic border border-yellow-100 italic">⭐ 5.0 High Performance AI</div>
            </div>

            <footer class="absolute bottom-10 text-[11px] text-gray-300 font-black tracking-[0.3em] uppercase">
                Designed by R.MARAV &bull; SECURED TECHNOLOGY &copy; 2024
            </footer>
        </main>
    </div>

    <script>
        function access() {
            document.getElementById('auth-gate').style.display = 'none';
            document.getElementById('main-app').style.display = 'flex';
        }

        function checkEnter(e) {
            if(e.key === "Enter") askAI();
        }

        function setQ(val) {
            document.getElementById('q-input').value = val;
            document.getElementById('q-input').focus();
        }

        // NO-API MENTOR BRAIN (Programmed by R.MARAV)
        function askAI() {
            const input = document.getElementById('q-input');
            const history = document.getElementById('history');
            const userText = input.value.trim();

            if(userText !== "") {
                if(history.innerText.includes("No recent")) history.innerHTML = "";
                
                // Add to history sidebar
                history.innerHTML = `<div class="p-2 border-l-2 border-blue-600 bg-gray-50 text-gray-700 font-bold mb-1 truncate italic">● ${userText}</div>` + history.innerHTML;
                
                // SIMULATED BRAIN RESPONSE
                setTimeout(() => {
                    alert("R.MARAV AI MENTOR SAYS:\n\n'I am processing your query: " + userText + ". Since this is the R.MARAV version, I will search the study database and show you the formula steps next.'");
                }, 500);
                
                input.value = ""; // Clear for next search
            }
        }

        // DEVICE ACCESS (Camera/Mic)
        async function cam() {
            const v = document.getElementById('webcam');
            try {
                if(v.style.display === 'block') { v.style.display='none'; v.srcObject.getTracks().forEach(t=>t.stop()); }
                else { v.srcObject = await navigator.mediaDevices.getUserMedia({video:true}); v.style.display='block'; }
            } catch(e) { alert("Camera Access: Request Permissions Settings."); }
        }

        async function mic() {
            try { await navigator.mediaDevices.getUserMedia({audio:true}); alert("R.MARAV AI: Microphone Access Granted. Listening..."); }
            catch(e) { alert("Mic Access Error."); }
        }
    </script>
</body>
</html>
