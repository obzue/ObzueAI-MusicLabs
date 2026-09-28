<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>OBZUEAI MusicLabs Studio 2.5 (Flagship Suite)</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    body { font-family: 'Inter', -apple-system, sans-serif; user-select: none; }
    .glass { background: rgba(18, 18, 24, 0.92); backdrop-filter: blur(16px); border: 1px solid rgba(255, 255, 255, 0.08); }
    .custom-scrollbar::-webkit-scrollbar { width: 5px; height: 5px; }
    .custom-scrollbar::-webkit-scrollbar-thumb { background: #334155; border-radius: 4px; }
    
    .mixer-channel {
      background: linear-gradient(180deg, #23252a 0%, #17181c 100%);
      border-right: 1px solid #0d0e11;
      border-left: 1px solid #32353e;
      box-shadow: inset 0 1px 0 rgba(255,255,255,0.08);
    }
    .knob {
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: radial-gradient(circle, #4a4d57 0%, #1a1b20 100%);
      border: 2px solid #0f1013;
      box-shadow: 0 2px 4px rgba(0,0,0,0.8);
    }
    .fader-track {
      width: 6px;
      background: #090a0c;
      border: 1px solid #2d3039;
      box-shadow: inset 0 0 4px #000;
    }
    .fader-cap {
      width: 20px;
      height: 34px;
      background: linear-gradient(180deg, #d1d5db 0%, #4b5563 50%, #1f2937 100%);
      border: 1px solid #000;
      border-radius: 2px;
      box-shadow: 0 4px 8px rgba(0,0,0,0.9);
    }
    .vu-meter-bar {
      background: linear-gradient(0deg, #22c55e 0%, #eab308 75%, #ef4444 100%);
    }
    .m4l-device-card {
      background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
      border: 1px solid #334155;
    }
  </style>
</head>
<body class="bg-slate-950 text-slate-100 min-h-screen flex flex-col overflow-hidden relative" id="appBody" oncontextmenu="handleGlobalContextMenu(event)">

  <!-- TRANSPORT CONTROLS -->
  <div id="floatingTransport" class="fixed top-14 right-6 z-50 glass rounded-2xl px-4 py-2 flex items-center gap-3 shadow-2xl border border-indigo-500/30 cursor-move">
    <button onclick="toggleRecord()" id="recBtn" class="w-7 h-7 rounded-full bg-red-600/20 text-red-500 border border-red-500 flex items-center justify-center hover:bg-red-600 hover:text-white transition">
      <div class="w-2.5 h-2.5 rounded-full bg-current"></div>
    </button>
    <button onclick="transportRewind()" class="text-slate-400 hover:text-white"><i data-lucide="rewind" class="w-4 h-4"></i></button>
    <button onclick="togglePlay()" id="playBtn" class="w-8 h-8 rounded-xl bg-indigo-600 hover:bg-indigo-500 text-white flex items-center justify-center shadow-lg shadow-indigo-600/40">
      <i data-lucide="play" class="w-4 h-4 fill-current"></i>
    </button>
    <button onclick="transportFastForward()" class="text-slate-400 hover:text-white"><i data-lucide="fast-forward" class="w-4 h-4"></i></button>
    <button onclick="toggleMicListen()" id="micBtn" class="p-1.5 rounded-lg bg-slate-800 hover:bg-indigo-600/30 text-indigo-400 border border-slate-700">
      <i data-lucide="mic" class="w-4 h-4"></i>
    </button>
    <div class="h-5 w-px bg-slate-800"></div>
    <span id="timecodeDisplay" class="font-mono text-xs text-indigo-300 font-bold">00:00:00</span>
  </div>

  <!-- HEADER -->
  <header class="glass z-20 px-5 py-2.5 flex items-center justify-between border-b border-slate-800">
    <div class="flex items-center space-x-3">
      <div class="w-8 h-8 rounded-xl bg-gradient-to-tr from-indigo-600 to-pink-500 flex items-center justify-center font-black text-base">O</div>
      <div>
        <h1 class="font-extrabold text-sm tracking-wider text-indigo-400">OBZUEAI MusicLabs 2.5</h1>
        <p class="text-[10px] text-emerald-400">Flagship Suite (Unlocked Dev)</p>
      </div>
    </div>

    <!-- TABS -->
    <div class="flex items-center bg-slate-900 p-1 rounded-xl border border-slate-800 text-xs">
      <button onclick="switchTab('create')" id="tabCreate" class="px-4 py-1.5 rounded-lg bg-indigo-600 text-white font-bold transition">Suno Create</button>
      <button onclick="switchTab('studio')" id="tabStudio" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition">Studio & Mixer</button>
      <button onclick="switchTab('devices')" id="tabDevices" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition">Max for Live & Synths</button>
      <button onclick="switchTab('packs')" id="tabPacks" class="px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition">GitHub Creative Packs</button>
    </div>

    <div class="flex items-center space-x-3">
      <button onclick="openLocalDirectory()" class="px-3 py-1.5 rounded-lg bg-slate-800 hover:bg-slate-700 border border-slate-700 text-xs font-semibold text-slate-200 flex items-center gap-1.5">
        <i data-lucide="folder-open" class="w-3.5 h-3.5 text-amber-400"></i>
        <span>Open Drive</span>
      </button>
    </div>
  </header>

  <!-- WORKSPACE CONTAINER -->
  <div id="mainContainer" class="flex-1 flex overflow-hidden z-10">
    
    <!-- SYSTEM BROWSER -->
    <aside class="w-64 glass border-r border-slate-800 flex flex-col text-xs">
      <div class="p-3 border-b border-slate-800 font-bold text-slate-300 flex items-center justify-between">
        <span class="flex items-center gap-1.5"><i data-lucide="hard-drive" class="w-4 h-4 text-indigo-400"></i> Local & Repo Browser</span>
      </div>
      <div id="fileBrowserTree" class="flex-1 p-2 overflow-y-auto custom-scrollbar space-y-1">
        <div class="p-1.5 rounded bg-slate-900/60 border border-slate-800 text-indigo-300 cursor-pointer" onclick="switchTab('devices')">🎛️ Max for Live Devices</div>
        <div class="p-1.5 rounded bg-slate-900/60 border border-slate-800 text-pink-300 cursor-pointer" onclick="switchTab('devices')">🎹 Wavetable, Sampler, Operator</div>
        <div class="p-1.5 rounded bg-slate-900/60 border border-slate-800 text-amber-300 cursor-pointer" onclick="switchTab('packs')">📦 GitHub Sound Toolkits</div>
        <div class="p-1.5 rounded bg-slate-900/60 border border-slate-800 text-emerald-300 cursor-pointer" onclick="switchTab('packs')">🎻 GitHub Acoustic Collections</div>
        <div class="p-1.5 rounded bg-slate-900/60 border border-slate-800 text-slate-300 cursor-pointer">📁 Local Drive & Projects</div>
      </div>
    </aside>

    <!-- 1. SUNO CREATE VIEW -->
    <div id="viewCreate" class="flex-1 flex overflow-hidden">
      <div class="w-80 glass border-r border-slate-800/80 flex flex-col p-4 space-y-4 overflow-y-auto custom-scrollbar text-xs">
        <div>
          <label class="font-bold text-slate-300">Lyrics</label>
          <textarea id="lyricsInput" rows="7" placeholder="[Verse 1]&#10;Enter lyrics here..." class="w-full bg-slate-900 border border-slate-800 rounded-xl p-3 text-indigo-200 font-mono text-xs focus:outline-none focus:border-indigo-500 resize-none"></textarea>
        </div>

        <div>
          <label class="block font-bold text-slate-300 mb-1">Style of Music</label>
          <textarea id="styleInput" rows="3" placeholder="hip-hop, orchestral brass, pitch-shifted loops..." class="w-full bg-slate-900 border border-slate-800 rounded-xl p-3 text-slate-200 text-xs focus:outline-none focus:border-indigo-500 resize-none"></textarea>
        </div>

        <button onclick="triggerSunoCreate()" class="w-full py-3 rounded-xl bg-gradient-to-r from-indigo-600 to-purple-600 hover:from-indigo-500 hover:to-purple-500 font-extrabold text-white text-xs shadow-lg shadow-indigo-600/30">
          🎵 Generate Full Tracks
        </button>
      </div>

      <div class="flex-1 p-4 bg-slate-950/80 overflow-y-auto custom-scrollbar">
        <h3 class="font-bold text-sm text-slate-200 mb-3">Workspace Stems</h3>
        <div id="sunoWorkspaceList" class="space-y-2"></div>
      </div>
    </div>

    <!-- 2. STUDIO DAW & ANALOG MIXER VIEW -->
    <div id="viewStudio" class="flex-1 flex flex-col overflow-hidden hidden">
      <div class="h-1/2 bg-slate-950 border-b border-slate-800 flex flex-col overflow-hidden">
        <div class="p-2 bg-slate-900/80 border-b border-slate-800 flex items-center justify-between text-xs px-4">
          <span class="font-bold text-indigo-400 flex items-center gap-2"><i data-lucide="layers" class="w-4 h-4"></i> Multitrack Timeline</span>
        </div>
        <div id="sequencerTimeline" class="flex-1 overflow-y-auto p-2 space-y-1.5 custom-scrollbar">
          <div class="h-12 bg-slate-900 border border-slate-800 rounded-lg flex items-center px-3 gap-3">
            <span class="w-24 font-bold text-xs text-slate-300">Wavetable Synth</span>
            <div class="flex-1 h-8 bg-indigo-950/60 rounded border border-indigo-500/30 relative overflow-hidden flex items-center px-2">
              <div class="w-3/4 h-full bg-gradient-to-r from-indigo-600/40 to-purple-600/40 rounded border border-indigo-400/50"></div>
            </div>
          </div>
        </div>
      </div>

      <div class="h-1/2 bg-[#121316] border-t-2 border-[#2a2d35] flex flex-col overflow-hidden">
        <div id="mixerConsole" class="flex-1 overflow-x-auto p-3 flex gap-1 custom-scrollbar bg-[#121316]">
          <div class="w-24 mixer-channel rounded-lg p-2 flex flex-col items-center justify-between border-2 border-amber-600/30">
            <span class="text-[10px] font-bold text-amber-400 uppercase">MASTER</span>
            <div class="knob my-1"></div>
            <div class="fader-cap my-2"></div>
            <span class="text-[9px] font-mono text-slate-400">0.0 dB</span>
          </div>
        </div>
      </div>
    </div>

    <!-- 3. EXCLUSIVE DEVICES & SYNTHS (MAX FOR LIVE, WAVETABLE, SAMPLER, OPERATOR) -->
    <div id="viewDevices" class="flex-1 p-6 bg-slate-950 overflow-y-auto custom-scrollbar hidden">
      <div class="max-w-6xl mx-auto space-y-6">
        <div>
          <h2 class="text-base font-extrabold text-indigo-400 flex items-center gap-2">
            <i data-lucide="cpu" class="w-5 h-5"></i> Max for Live Platform
          </h2>
          <p class="text-xs text-slate-400">Build, hack, or download custom multi-effects, tools, and venue lighting controllers directly within the browser.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
          <div class="m4l-device-card p-4 rounded-xl space-y-2">
            <div class="flex justify-between items-center">
              <span class="font-bold text-xs text-indigo-300">PitchLoop89 Pro</span>
              <span class="text-[10px] bg-indigo-900/60 text-indigo-300 px-2 py-0.5 rounded">M4L Device</span>
            </div>
            <p class="text-[11px] text-slate-400">Glitchy pitch-shifting delay and real-time micro-looping effects device.</p>
            <button onclick="cloneGithubDevice('PitchLoop89 Pro')" class="w-full py-1.5 bg-indigo-600 hover:bg-indigo-500 rounded text-xs font-bold text-white">Load Device</button>
          </div>

          <div class="m4l-device-card p-4 rounded-xl space-y-2">
            <div class="flex justify-between items-center">
              <span class="font-bold text-xs text-pink-300">Pegasus Multi Synth</span>
              <span class="text-[10px] bg-pink-900/60 text-pink-300 px-2 py-0.5 rounded">Organic Series</span>
            </div>
            <p class="text-[11px] text-slate-400">6-voice organic synthesis engine generating evolving microtonal layers.</p>
            <button onclick="cloneGithubDevice('Pegasus Multi Synth')" class="w-full py-1.5 bg-pink-600 hover:bg-pink-500 rounded text-xs font-bold text-white">Load Device</button>
          </div>

          <div class="m4l-device-card p-4 rounded-xl space-y-2">
            <div class="flex justify-between items-center">
              <span class="font-bold text-xs text-emerald-300">Beats Maker</span>
              <span class="text-[10px] bg-emerald-900/60 text-emerald-300 px-2 py-0.5 rounded">Organic Series</span>
            </div>
            <p class="text-[11px] text-slate-400">Generative algorithmic rhythm generator with dynamic velocity randomization.</p>
            <button onclick="cloneGithubDevice('Beats Maker')" class="w-full py-1.5 bg-emerald-600 hover:bg-emerald-500 rounded text-xs font-bold text-white">Load Device</button>
          </div>
        </div>

        <div>
          <h2 class="text-base font-extrabold text-purple-400 flex items-center gap-2 mt-4">
            <i data-lucide="sliders" class="w-5 h-5"></i> Flagship Synthesizer Engine
          </h2>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
          <div class="glass p-4 rounded-xl space-y-2 border border-purple-500/30">
            <h3 class="font-bold text-xs text-purple-300">Wavetable</h3>
            <p class="text-[11px] text-slate-400">Advanced morphing synthesis with native MPE expression support.</p>
            <button onclick="cloneGithubDevice('Wavetable Synth')" class="w-full py-1.5 bg-purple-600 hover:bg-purple-500 rounded text-xs font-bold text-white">Unlock via GitHub Repo</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-blue-500/30">
            <h3 class="font-bold text-xs text-blue-300">Sampler</h3>
            <p class="text-[11px] text-slate-400">Deep multi-sample editing, keyzone mapping, and multi-filter routing.</p>
            <button onclick="cloneGithubDevice('Sampler Engine')" class="w-full py-1.5 bg-blue-600 hover:bg-blue-500 rounded text-xs font-bold text-white">Unlock via GitHub Repo</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-amber-500/30">
            <h3 class="font-bold text-xs text-amber-300">Operator</h3>
            <p class="text-[11px] text-slate-400">Classic 4-operator FM sound generator with customizable algorithms.</p>
            <button onclick="cloneGithubDevice('Operator FM Synth')" class="w-full py-1.5 bg-amber-600 hover:bg-amber-500 rounded text-xs font-bold text-white">Unlock via GitHub Repo</button>
          </div>
        </div>
      </div>
    </div>

    <!-- 4. GITHUB CREATIVE PACKS & ACOUSTIC COLLECTIONS VIEW -->
    <div id="viewPacks" class="flex-1 p-6 bg-slate-950 overflow-y-auto custom-scrollbar hidden">
      <div class="max-w-6xl mx-auto space-y-6">
        <div>
          <h2 class="text-base font-extrabold text-amber-400 flex items-center gap-2">
            <i data-lucide="package" class="w-5 h-5"></i> GitHub Acoustic & Creative Toolkits
          </h2>
          <p class="text-xs text-slate-400">Cloned open-source acoustic collections and specialized vocal/ambient soundscapes.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
          <div class="glass p-4 rounded-xl space-y-2 border border-amber-500/20">
            <span class="font-bold text-xs text-amber-300 block">Upright Piano Collection</span>
            <p class="text-[11px] text-slate-400">Deeply sampled felt and vintage upright piano instruments engineered from GitHub repos.</p>
            <button onclick="cloneGithubDevice('Upright Piano')" class="w-full py-1.5 bg-amber-600 hover:bg-amber-500 rounded text-xs font-bold text-white">Clone Pack</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-amber-500/20">
            <span class="font-bold text-xs text-amber-300 block">String & Brass Quartets</span>
            <p class="text-[11px] text-slate-400">Full expressive chamber string quartet and brass ensemble virtual instruments.</p>
            <button onclick="cloneGithubDevice('String & Brass Quartet')" class="w-full py-1.5 bg-amber-600 hover:bg-amber-500 rounded text-xs font-bold text-white">Clone Pack</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-purple-500/20">
            <span class="font-bold text-xs text-purple-300 block">Voice Box Vocal Suite</span>
            <p class="text-[11px] text-slate-400">Targeted sound toolkit for processing, pitching, and tuning vocal tracks.</p>
            <button onclick="cloneGithubDevice('Voice Box')" class="w-full py-1.5 bg-purple-600 hover:bg-purple-500 rounded text-xs font-bold text-white">Clone Pack</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-blue-500/20">
            <span class="font-bold text-xs text-blue-300 block">Mood Reel Cinematic Pack</span>
            <p class="text-[11px] text-slate-400">Atmospheric narrative soundscapes, textural pads, and cinematic sub-bass hits.</p>
            <button onclick="cloneGithubDevice('Mood Reel')" class="w-full py-1.5 bg-blue-600 hover:bg-blue-500 rounded text-xs font-bold text-white">Clone Pack</button>
          </div>

          <div class="glass p-4 rounded-xl space-y-2 border border-emerald-500/20">
            <span class="font-bold text-xs text-emerald-300 block">Drone Lab Complex Tones</span>
            <p class="text-[11px] text-slate-400">Complex, evolving sustained drone generators for ambient film scoring.</p>
            <button onclick="cloneGithubDevice('Drone Lab')" class="w-full py-1.5 bg-emerald-600 hover:bg-emerald-500 rounded text-xs font-bold text-white">Clone Pack</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    lucide.createIcons();

    function switchTab(tab) {
      document.getElementById('viewCreate').classList.toggle('hidden', tab !== 'create');
      document.getElementById('viewStudio').classList.toggle('hidden', tab !== 'studio');
      document.getElementById('viewDevices').classList.toggle('hidden', tab !== 'devices');
      document.getElementById('viewPacks').classList.toggle('hidden', tab !== 'packs');

      ['tabCreate', 'tabStudio', 'tabDevices', 'tabPacks'].forEach(t => {
        const btn = document.getElementById(t);
        const isActive = t.toLowerCase().includes(tab);
        btn.className = isActive 
          ? 'px-4 py-1.5 rounded-lg bg-indigo-600 text-white font-bold transition'
          : 'px-4 py-1.5 rounded-lg text-slate-400 hover:text-white font-bold transition';
      });
    }

    function cloneGithubDevice(name) {
      alert(`🎉 Cloned "${name}" from GitHub into your OBZUEAI MusicLabs local device rack!`);
    }

    function triggerSunoCreate() {
      const lyrics = document.getElementById('lyricsInput').value || "[Instrumental]";
      const style = document.getElementById('styleInput').value || "synthwave";
      const list = document.getElementById('sunoWorkspaceList');
      list.innerHTML = `
        <div class="p-3 bg-slate-900 border border-slate-800 rounded-xl flex items-center justify-between">
          <div>
            <h4 class="font-bold text-xs text-slate-100">Track Rendered (${style})</h4>
            <p class="text-[10px] text-indigo-400 font-mono">${lyrics.substring(0, 30)}...</p>
          </div>
          <span class="text-[10px] text-emerald-400 font-bold">Ready</span>
        </div>
      ` + list.innerHTML;
    }
  </script>
</body>
</html>
Update to Studio 2.5 - Max for Live & GitHub Packs
