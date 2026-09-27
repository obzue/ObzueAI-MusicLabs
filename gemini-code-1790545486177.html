<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>OBZUEAI MusicLabs - Suno Style Studio & Community</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    body { font-family: 'Inter', -apple-system, sans-serif; }
    .glass { background: rgba(15, 23, 42, 0.88); backdrop-filter: blur(16px); border: 1px solid rgba(255, 255, 255, 0.08); }
    .custom-scrollbar::-webkit-scrollbar { width: 5px; height: 5px; }
    .custom-scrollbar::-webkit-scrollbar-thumb { background: rgba(255, 255, 255, 0.2); border-radius: 4px; }
    .pulse-mic { animation: pulse 1.5s infinite; }
    @keyframes pulse { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.15); } }
  </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col overflow-hidden relative" id="appBody">

  <!-- Dynamic Background Overlay -->
  <div id="bgOverlay" class="absolute inset-0 bg-cover bg-center opacity-25 pointer-events-none transition-all duration-500 z-0"></div>

  <!-- Hardware Lock Security Header -->
  <div class="z-20 bg-amber-500/10 border-b border-amber-500/20 px-4 py-1.5 text-[11px] text-amber-400 flex items-center justify-between">
    <span class="flex items-center gap-1.5">
      <i data-lucide="shield-check" class="w-3.5 h-3.5"></i>
      <strong>Hardware Lock Active:</strong> License cryptographically bound to <code class="bg-amber-950/60 px-1 py-0.5 rounded text-amber-300">OBZ-HW-88392-X</code> (Single-Device Pass $25/Yr).
    </span>
    <span class="text-slate-400">Free Daily Tier: <strong id="timerDisplay" class="text-emerald-400 font-mono">06:00:00</strong></span>
  </div>

  <!-- Main Application Header -->
  <header class="glass z-20 px-5 py-2.5 flex items-center justify-between border-b border-slate-800">
    <div class="flex items-center space-x-3">
      <div class="w-9 h-9 rounded-xl bg-gradient-to-tr from-indigo-600 to-pink-500 flex items-center justify-center font-black text-lg shadow-lg shadow-indigo-500/30">O</div>
      <div>
        <h1 class="font-extrabold text-base tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 via-purple-300 to-pink-400">OBZUEAI MusicLabs</h1>
        <p class="text-[10px] text-slate-400">Full Song, Video, Image & Coding Agent Studio</p>
      </div>
    </div>

    <!-- View Tabs: Studio vs Community -->
    <div class="flex items-center bg-slate-900/90 p-1 rounded-xl border border-slate-800 text-xs">
      <button onclick="switchTab('studio')" id="tabStudio" class="px-4 py-1.5 rounded-lg bg-indigo-600 text-white font-bold transition flex items-center gap-1.5">
        <i data-lucide="music" class="w-3.5 h-3.5"></i>
        <span>Studio Workspace</span>
      </button>
      <button onclick="switchTab('community')" id="tabCommunity" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition flex items-center gap-1.5">
        <i data-lucide="users" class="w-3.5 h-3.5"></i>
        <span>Community Feed</span>
      </button>
    </div>

    <!-- User Profile & Settings Drawer Controls -->
    <div class="flex items-center space-x-3">
      <button onclick="toggleVoiceMode()" id="voiceToggleBtn" class="flex items-center gap-1.5 px-3 py-1.5 rounded-full bg-slate-800 hover:bg-slate-700 text-xs font-bold text-slate-200 border border-slate-700 transition">
        <i data-lucide="mic" class="w-3.5 h-3.5 text-indigo-400"></i>
        <span id="voiceStatus">Voice: OFF</span>
      </button>

      <!-- Settings Dropdown Button -->
      <button onclick="toggleSettingsDrawer()" class="p-2 rounded-xl bg-slate-800 hover:bg-slate-700 border border-slate-700 text-slate-300">
        <i data-lucide="sliders" class="w-4 h-4"></i>
      </button>

      <!-- User Profile Thumbnail -->
      <div class="flex items-center gap-2 pl-2 border-l border-slate-800">
        <img id="userAvatar" src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=100" class="w-8 h-8 rounded-full border border-indigo-500 object-cover cursor-pointer" onclick="toggleProfileModal()" />
        <button onclick="toggleAuth()" id="authBtn" class="text-xs font-semibold text-slate-300 hover:text-white">Sign In</button>
      </div>
    </div>
  </header>

  <!-- MAIN VIEW CONTAINER -->
  <div id="mainContainer" class="flex-1 flex overflow-hidden z-10">
    
    <!-- STUDIO VIEW (Suno Layout: Left Controls/Lyrics, Top Tracks, Center Chat) -->
    <div id="viewStudio" class="flex-1 flex overflow-hidden w-full">
      
      <!-- LEFT PANEL: Lyrics Preview Pane & Quick Creators -->
      <aside class="w-80 glass border-r border-slate-800/80 flex flex-col overflow-hidden text-xs">
        <div class="p-3 border-b border-slate-800 flex items-center justify-between">
          <span class="font-bold text-slate-300 uppercase tracking-wider text-[10px]">Lyrics & Prompt Editor</span>
          <button onclick="generateLyricsPrompt()" class="text-[10px] text-indigo-400 hover:underline">Auto-Structure</button>
        </div>

        <!-- Lyrics Editor Box -->
        <div class="flex-1 p-3 flex flex-col space-y-2 overflow-y-auto custom-scrollbar">
          <textarea id="lyricsPane" placeholder="[Verse 1]&#10;Neon lights on the digital street...&#10;&#10;[Chorus]&#10;OBZUEAI takes the beat higher..." class="w-full flex-1 bg-slate-900/90 border border-slate-800 rounded-xl p-3 text-xs text-indigo-200 focus:outline-none focus:border-indigo-500 font-mono leading-relaxed resize-none custom-scrollbar"></textarea>
          
          <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800/80 space-y-1 text-[11px]">
            <div class="text-slate-400 font-bold">Generation Output Mode:</div>
            <div class="text-emerald-400 font-semibold">✓ 2 Full Songs + 2 Samples + High-Res Cover Art</div>
          </div>
        </div>
      </aside>

      <!-- CENTER AREA: Top Generated Tracks List + Center AI Chat Engine -->
      <main class="flex-1 flex flex-col bg-slate-950/70 overflow-hidden">
        
        <!-- TOP GENERATED TRACKS LIST (Populates above chat) -->
        <div class="p-3 border-b border-slate-800 bg-slate-900/40">
          <div class="flex items-center justify-between mb-2">
            <span class="text-xs font-bold text-slate-300 flex items-center gap-1.5">
              <i data-lucide="disc" class="w-4 h-4 text-purple-400"></i>
              Generated Songs & Samples Queue
            </span>
            <span class="text-[10px] text-slate-400">Auto-created 4 stems on every prompt</span>
          </div>

          <div id="generatedTracksQueue" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-2.5">
            <div class="text-xs text-slate-500 italic col-span-full py-2 text-center">No tracks generated in this session yet. Issue a command in the chat below!</div>
          </div>
        </div>

        <!-- VOICE WAVEFORM ANIMATION BAR -->
        <div id="waveBar" class="hidden p-2.5 bg-indigo-950/50 border-b border-indigo-500/30 flex items-center justify-center gap-2">
          <div class="w-1 h-3 bg-indigo-400 rounded pulse-mic"></div>
          <div class="w-1 h-6 bg-purple-400 rounded pulse-mic"></div>
          <div class="w-1 h-2 bg-pink-400 rounded pulse-mic"></div>
          <span class="text-xs text-indigo-300 font-medium ml-2">OBZUEAI Aware Brain Listening & Conversing...</span>
        </div>

        <!-- CENTER CHAT FEED -->
        <div id="chatFeed" class="flex-1 overflow-y-auto p-4 space-y-3 text-xs custom-scrollbar">
          <div class="flex items-start space-x-2">
            <div class="w-7 h-7 rounded-lg bg-indigo-600 flex items-center justify-center font-bold text-white">AI</div>
            <div class="glass p-3 rounded-2xl max-w-xl leading-relaxed text-slate-200">
              <strong>OBZUEAI Brain:</strong> Welcome to your hardware-locked studio! I am fully aware of your project state. Select a genre or mood from the settings drawer, talk to me via mic, or type below to generate full tracks, videos, and code.
            </div>
          </div>
        </div>

        <!-- BOTTOM CHAT INPUT BAR WITH MIC -->
        <div class="p-3 glass border-t border-slate-800 flex items-center gap-2">
          <button onclick="toggleMicListen()" id="micBtn" class="p-2.5 rounded-xl bg-slate-800 hover:bg-indigo-600/30 border border-slate-700 text-indigo-400 transition">
            <i data-lucide="mic" class="w-5 h-5"></i>
          </button>
          <input type="text" id="userInput" placeholder="Generate a synthwave song, video timeline, or web code..." class="flex-1 bg-slate-900 border border-slate-800 rounded-xl px-4 py-2.5 text-xs text-slate-100 focus:outline-none focus:border-indigo-500" />
          <button onclick="handleSendMessage()" class="px-5 py-2.5 rounded-xl bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500 text-white font-bold text-xs shadow-lg shadow-indigo-600/30">
            Generate
          </button>
        </div>
      </main>
    </div>

    <!-- COMMUNITY FEED VIEW -->
    <div id="viewCommunity" class="flex-1 flex overflow-hidden w-full hidden">
      <!-- Left Community Chat Tab -->
      <aside class="w-80 glass border-r border-slate-800 flex flex-col text-xs">
        <div class="p-3 border-b border-slate-800 font-bold text-indigo-400 flex items-center justify-between">
          <span>Global Community Chat</span>
          <span class="w-2 h-2 rounded-full bg-emerald-500"></span>
        </div>
        <div id="communityChatMessages" class="flex-1 overflow-y-auto p-3 space-y-2 custom-scrollbar">
          <div class="bg-slate-900/80 p-2 rounded border border-slate-800">
            <span class="font-bold text-purple-400">@ProducerJohn:</span> Just dropped a Reggae Dub remix! Check the feed.
          </div>
        </div>
        <div class="p-2.5 border-t border-slate-800 flex gap-2">
          <input type="text" id="communityMsgInput" placeholder="Share a track or chat..." class="flex-1 bg-slate-900 border border-slate-800 rounded-lg px-2.5 py-1.5 text-xs" />
          <button onclick="sendCommunityMsg()" class="px-3 py-1.5 bg-indigo-600 text-white rounded-lg font-bold">Post</button>
        </div>
      </aside>

      <!-- Right Community Showcase Grid -->
      <main class="flex-1 p-6 overflow-y-auto custom-scrollbar bg-slate-950/80">
        <h2 class="text-base font-extrabold text-slate-100 mb-4 flex items-center gap-2">
          <i data-lucide="globe" class="w-5 h-5 text-indigo-400"></i>
          Community Trending Showcase
        </h2>
        <div id="communityGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
          <!-- Community Cards Populated Dynamically -->
        </div>
      </main>
    </div>
  </div>

  <!-- SETTINGS & PROFILE DRAWER (Tucked underneath dropdown) -->
  <div id="settingsDrawer" class="fixed inset-y-0 right-0 w-80 glass z-50 transform translate-x-full transition-transform duration-300 p-5 flex flex-col space-y-4 text-xs border-l border-slate-700">
    <div class="flex items-center justify-between border-b border-slate-800 pb-3">
      <h3 class="font-bold text-sm text-slate-100">Studio Settings & Profiles</h3>
      <button onclick="toggleSettingsDrawer()"><i data-lucide="x" class="w-5 h-5 text-slate-400"></i></button>
    </div>

    <div class="flex-1 overflow-y-auto space-y-4 custom-scrollbar pr-1">
      <!-- Global Genre Profile Selection -->
      <div>
        <label class="block font-bold text-slate-300 mb-1">Global Genre Profile</label>
        <select id="genreSelect" class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2 text-slate-200">
          <optgroup label="Reggae & Subgenres">
            <option>Roots Reggae</option><option>Dancehall</option><option>Dub</option><option>Rocksteady</option><option>Ska</option><option>Ragga</option><option>Reggae Fusion</option>
          </optgroup>
          <optgroup label="Hip-Hop & Subgenres">
            <option>Boom Bap</option><option>Trap</option><option>Drill</option><option>Conscious Hip-Hop</option><option>Lo-Fi Hip-Hop</option><option>Phonk</option><option>G-Funk</option><option>Cloud Rap</option>
          </optgroup>
          <optgroup label="Global Music">
            <option>Afrobeats</option><option>Latin Reggaeton</option><option>Amapiano</option><option>K-Pop</option><option>Samba</option><option>Highlife</option><option>Celtic Folk</option>
          </optgroup>
        </select>
      </div>

      <!-- 30 Song Mood Selector -->
      <div>
        <label class="block font-bold text-slate-300 mb-1">Song Mood Profile (30 Moods)</label>
        <select id="moodSelect" class="w-full bg-slate-900 border border-slate-700 rounded-lg p-2 text-slate-200">
          <option>1. Energetic</option><option>2. Melancholic</option><option>3. Chill / Relaxed</option><option>4. Aggressive</option><option>5. Euphoric</option>
          <option>6. Dark / Mysterious</option><option>7. Romantic</option><option>8. Nostalgic</option><option>9. Uplifting</option><option>10. Dreamy</option>
          <option>11. Hypnotic</option><option>12. Tense / Suspenseful</option><option>13. Funky</option><option>14. Epic / Cinematic</option><option>15. Rebellious</option>
          <option>16. Soulful</option><option>17. Trippy</option><option>18. Atmospheric</option><option>19. Playful</option><option>20. Gritty</option>
          <option>21. Peaceful</option><option>22. Futuristic</option><option>23. Hopeful</option><option>24. Sad</option><option>25. Fierce</option>
          <option>26. Groovy</option><option>27. Ethereal</option><option>28. Fiery</option><option>29. Smooth</option><option>30. Rowdy</option>
        </select>
      </div>

      <!-- Background Profile Image Upload -->
      <div>
        <label class="block font-bold text-slate-300 mb-1">Custom Background Image</label>
        <input type="file" accept="image/*" onchange="uploadBackground(event)" class="w-full bg-slate-900 border border-slate-700 rounded p-1.5 text-[11px] text-slate-400" />
      </div>

      <!-- Password Recovery & Device Locking -->
      <div class="pt-3 border-t border-slate-800 space-y-2">
        <button onclick="togglePasswordModal()" class="w-full py-2 bg-slate-800 hover:bg-slate-700 rounded text-slate-300 font-semibold">Account Password Recovery</button>
      </div>
    </div>
  </div>

  <!-- PASSWORD RECOVERY MODAL -->
  <div id="pwdModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm hidden flex items-center justify-center p-4 z-50">
    <div class="glass max-w-sm w-full rounded-2xl p-5 space-y-4 border border-slate-700">
      <div class="flex justify-between items-center border-b border-slate-800 pb-2">
        <h3 class="font-bold text-xs text-slate-100">Password Recovery</h3>
        <button onclick="togglePasswordModal()"><i data-lucide="x" class="w-4 h-4 text-slate-400"></i></button>
      </div>
      <p class="text-[11px] text-slate-300">Enter your registered Google email for a reset token.</p>
      <input type="email" placeholder="user@gmail.com" class="w-full bg-slate-900 border border-slate-800 rounded p-2 text-xs text-slate-100" />
      <button onclick="alert('Recovery token dispatched!'); togglePasswordModal();" class="w-full py-2 bg-indigo-600 text-white font-bold text-xs rounded">Send Reset Email</button>
    </div>
  </div>

  <script>
    lucide.createIcons();
    let isListening = false;
    let voiceActive = false;
    let currentTab = 'studio';

    // Speech Recognition
    const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
    let recognition = SpeechRecognition ? new SpeechRecognition() : null;

    if (recognition) {
      recognition.onresult = (e) => {
        document.getElementById('userInput').value = e.results[0][0].transcript;
        handleSendMessage();
      };
    }

    function toggleMicListen() {
      if (!recognition) return alert("Speech recognition not supported in this browser.");
      if (!isListening) {
        recognition.start();
        isListening = true;
        document.getElementById('micBtn').classList.add('bg-indigo-600', 'text-white');
      } else {
        recognition.stop();
        isListening = false;
        document.getElementById('micBtn').classList.remove('bg-indigo-600', 'text-white');
      }
    }

    function toggleVoiceMode() {
      voiceActive = !voiceActive;
      document.getElementById('voiceStatus').innerText = `Voice: ${voiceActive ? 'ON' : 'OFF'}`;
      document.getElementById('waveBar').classList.toggle('hidden', !voiceActive);
    }

    function switchTab(tab) {
      currentTab = tab;
      document.getElementById('viewStudio').classList.toggle('hidden', tab !== 'studio');
      document.getElementById('viewCommunity').classList.toggle('hidden', tab !== 'community');
      document.getElementById('tabStudio').className = tab === 'studio' ? 'px-4 py-1.5 rounded-lg bg-indigo-600 text-white font-bold transition flex items-center gap-1.5' : 'px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition flex items-center gap-1.5';
      document.getElementById('tabCommunity').className = tab === 'community' ? 'px-4 py-1.5 rounded-lg bg-indigo-600 text-white font-bold transition flex items-center gap-1.5' : 'px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition flex items-center gap-1.5';
    }

    function handleSendMessage() {
      const input = document.getElementById('userInput');
      const text = input.value.trim();
      if (!text) return;

      const feed = document.getElementById('chatFeed');
      feed.innerHTML += `
        <div class="flex items-start space-x-2 justify-end">
          <div class="glass p-3 rounded-2xl max-w-xl text-indigo-200"><strong>You:</strong> ${text}</div>
        </div>
      `;
      input.value = '';
      feed.scrollTop = feed.scrollHeight;

      // Generate 4 Tracks Automatically
      setTimeout(() => {
        const genre = document.getElementById('genreSelect').value;
        const mood = document.getElementById('moodSelect').value;

        // Populate top tracks queue
        const queue = document.getElementById('generatedTracksQueue');
        queue.innerHTML = `
          <div class="p-2 bg-slate-900 border border-indigo-500/30 rounded-xl flex items-center gap-2">
            <img src="https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?w=100" class="w-10 h-10 rounded-lg object-cover" />
            <div class="overflow-hidden text-[11px]">
              <div class="font-bold text-slate-100 truncate">${text} (Full Song 1)</div>
              <div class="text-indigo-400 text-[10px]">${genre} • ${mood}</div>
            </div>
          </div>
          <div class="p-2 bg-slate-900 border border-indigo-500/30 rounded-xl flex items-center gap-2">
            <img src="https://images.unsplash.com/photo-1514525253161-7a46d19cd819?w=100" class="w-10 h-10 rounded-lg object-cover" />
            <div class="overflow-hidden text-[11px]">
              <div class="font-bold text-slate-100 truncate">${text} (Full Song 2)</div>
              <div class="text-purple-400 text-[10px]">${genre} • ${mood}</div>
            </div>
          </div>
          <div class="p-2 bg-slate-900 border border-slate-800 rounded-xl flex items-center gap-2 opacity-80">
            <img src="https://images.unsplash.com/photo-1470225620780-dba8ba36b745?w=100" class="w-10 h-10 rounded-lg object-cover" />
            <div class="overflow-hidden text-[11px]">
              <div class="font-bold text-slate-200 truncate">${text} (Sample A)</div>
              <div class="text-slate-400 text-[10px]">0:30 Preview Stem</div>
            </div>
          </div>
          <div class="p-2 bg-slate-900 border border-slate-800 rounded-xl flex items-center gap-2 opacity-80">
            <img src="https://images.unsplash.com/photo-1508700115892-45ecd05ae2ad?w=100" class="w-10 h-10 rounded-lg object-cover" />
            <div class="overflow-hidden text-[11px]">
              <div class="font-bold text-slate-200 truncate">${text} (Sample B)</div>
              <div class="text-slate-400 text-[10px]">0:30 Preview Stem</div>
            </div>
          </div>
        `;

        feed.innerHTML += `
          <div class="flex items-start space-x-2">
            <div class="w-7 h-7 rounded-lg bg-indigo-600 flex items-center justify-center font-bold text-white">AI</div>
            <div class="glass p-3 rounded-2xl max-w-xl leading-relaxed text-slate-200">
              <strong>OBZUEAI Brain:</strong> Generated 2 full songs and 2 samples for <em>"${text}"</em> under <strong>${genre}</strong> [${mood}]. High-resolution artwork compiled to top queue!
            </div>
          </div>
        `;
        feed.scrollTop = feed.scrollHeight;
      }, 800);
    }

    function toggleSettingsDrawer() {
      document.getElementById('settingsDrawer').classList.toggle('translate-x-full');
    }
    function togglePasswordModal() {
      document.getElementById('pwdModal').classList.toggle('hidden');
    }
    function uploadBackground(e) {
      const file = e.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = (evt) => {
          document.getElementById('bgOverlay').style.backgroundImage = `url('${evt.target.result}')`;
        };
        reader.readAsDataURL(file);
      }
    }
    function generateLyricsPrompt() {
      document.getElementById('lyricsPane').value = "[Verse 1]\nDigital waves across the screen...\nOBZUEAI powering the dream...\n\n[Chorus]\nFour tracks rendered in the night,\nMusic and code shining bright!";
    }
    function sendCommunityMsg() {
      const input = document.getElementById('communityMsgInput');
      if (!input.value.trim()) return;
      document.getElementById('communityChatMessages').innerHTML += `
        <div class="bg-slate-900 p-2 rounded border border-slate-800">
          <span class="font-bold text-indigo-400">@You:</span> ${input.value}
        </div>
      `;
      input.value = '';
    }
  </script>
</body>
</html>
