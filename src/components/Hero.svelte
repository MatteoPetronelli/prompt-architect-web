<script>
    import { fade, fly } from 'svelte/transition';
    import { cubicOut } from 'svelte/easing';
</script>

<div id="hero" class="pointer-events-none relative z-10 flex flex-col items-center justify-center min-h-[100svh] px-4 text-center max-w-5xl mx-auto selection:bg-cyan-500 selection:text-white">
    <h1 
        in:fly={{ y: 20, duration: 800, delay: 200, easing: cubicOut }}
        class="pointer-events-auto text-5xl md:text-7xl font-extrabold text-white tracking-tight mb-6 drop-shadow-lg"
    >
      L'Architecte de <br />
      <span class="bg-clip-text text-transparent bg-gradient-to-r from-cyan-400 via-blue-500 to-purple-600">
        Vos Scénarios
      </span>
    </h1>

    <p 
        in:fade={{ duration: 1000, delay: 400 }}
        class="pointer-events-auto text-lg md:text-xl text-slate-300 mb-10 max-w-2xl mx-auto leading-relaxed drop-shadow-md"
    >
      Fini la page blanche. Générez des prompts complexes, structurez vos idées et gardez une trace de vos créations.
    </p>

    <div 
        in:fly={{ y: 20, duration: 800, delay: 600, easing: cubicOut }}
        class="flex flex-col sm:flex-row gap-4 justify-center items-center w-full pointer-events-auto"
    >
      
      <a 
        href="https://discord.com" 
        target="_blank" 
        rel="noopener noreferrer" 
        class="group relative inline-flex items-center gap-2 px-8 py-4 bg-blue-600 hover:bg-blue-500 text-white rounded-xl font-bold transition-all transform hover:scale-105 shadow-lg shadow-blue-500/25 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-offset-2 focus:ring-offset-slate-900 w-full sm:w-auto justify-center"
      >
        <svg class="w-5 h-5 fill-current transition-transform group-hover:rotate-12" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M20.317 4.3698a19.7913 19.7913 0 00-4.8851-1.5152.0741.0741 0 00-.0785.0371c-.211.3753-.4447.8648-.6083 1.2495-1.8447-.2762-3.68-.2762-5.4868 0-.1636-.3933-.4058-.8742-.6177-1.2495a.077.077 0 00-.0785-.037 19.7363 19.7363 0 00-4.8852 1.515.0699.0699 0 00-.0321.0277C.5334 9.0458-.319 13.5799.0992 18.0578a.0824.0824 0 00.0312.0561c2.0528 1.5076 4.0413 2.4228 5.9929 3.0294a.0777.0777 0 00.0842-.0276c.4616-.6304.8731-1.2952 1.226-1.9942a.076.076 0 00-.0416-.1057c-.6528-.2476-1.2743-.5495-1.8722-.8923a.077.077 0 01-.0076-.1277c.1258-.0943.2517-.1923.3718-.2914a.0743.0743 0 01.0776-.0105c3.9278 1.7933 8.18 1.7933 12.0614 0a.0739.0739 0 01.0785.0095c.1202.099.246.1981.3728.2924a.077.077 0 01-.0066.1276 12.2986 12.2986 0 01-1.873.8914.0766.0766 0 00-.0407.1067c.3604.698.7719 1.3628 1.225 1.9932a.076.076 0 00.0842.0286c1.961-.6067 3.9495-1.5219 6.0023-3.0294a.077.077 0 00.0313-.0552c.5004-5.177-.8382-9.6739-3.5485-13.6604a.061.061 0 00-.0312-.0286zM8.02 15.3312c-1.1825 0-2.1569-1.0857-2.1569-2.419 0-1.3332.9555-2.4189 2.157-2.4189 1.2108 0 2.1757 1.0952 2.1568 2.419 0 1.3332-.946 2.419-2.1568 2.419zm7.9748 0c-1.1825 0-2.1569-1.0857-2.1569-2.419 0-1.3332.9554-2.4189 2.1569-2.4189 1.2108 0 2.1757 1.0952 2.1568 2.419 0 1.3332-.946 2.419-2.1568 2.419z"/></svg>
        <span>Ajouter au Serveur</span>
      </a>
      
      <a 
        href="#features" 
        class="group inline-flex items-center gap-2 px-8 py-4 bg-slate-800/80 backdrop-blur-sm hover:bg-slate-700 text-slate-200 border border-slate-700 rounded-xl font-semibold transition-all w-full sm:w-auto justify-center focus:outline-none focus:ring-2 focus:ring-slate-400 focus:ring-offset-2 focus:ring-offset-slate-900"
      >
        <span>Découvrir</span>
        <svg class="w-4 h-4 transition-transform group-hover:translate-y-1" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>
      </a>

    </div>

</div>