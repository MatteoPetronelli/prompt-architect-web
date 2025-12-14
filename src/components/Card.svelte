<script lang="ts">
  export let title: string;
  export let description: string;
  export let icon: string;
</script>

<div class="group relative p-8 bg-slate-800/50 backdrop-blur-md border border-slate-700/50 rounded-2xl overflow-hidden hover:border-blue-500/50 transition-colors duration-300 h-full">
  
  <div class="absolute -inset-2 bg-gradient-to-r from-blue-600 to-cyan-600 rounded-2xl opacity-0 group-hover:opacity-10 blur-xl transition-opacity duration-500"></div>

  <div class="relative z-10 flex flex-col items-start h-full">
    
    <div class="mb-4 p-3 bg-slate-900/80 rounded-lg text-blue-400 group-hover:text-white group-hover:bg-blue-600 transition-all duration-300 shadow-lg border border-slate-700 group-hover:border-blue-500 group-hover:scale-110">
      {@html icon}
    </div>

    <h3 class="text-xl font-bold text-white mb-3 group-hover:text-blue-200 transition-colors">
      {title}
    </h3>

    <p class="text-slate-400 leading-relaxed text-sm">
      {description}
    </p>
  </div>

</div>