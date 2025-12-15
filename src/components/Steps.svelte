<script lang="ts">
  const steps = [
    {
      number: "01",
      title: "Lancez l'Initialisation",
      description: "Démarrez une nouvelle session d'architecture en fournissant votre idée de base. L'arbre de dialogue est créé.",
      code: '/prompt idee:"Stratégie marketing Instagram"'
    },
    {
      number: "02",
      title: "Affinez par le Dialogue",
      description: "Le bot vous pose des questions pour préciser le Contexte et l'Audience. Répondez simplement dans le chat pour guider l'IA.",
      code: "> Bot: Quel est le style souhaité ?\n> Vous: Professionnel et engageant."
    },
    {
      number: "03",
      title: "Générez et Exportez",
      description: "L'IA compile l'analyse CO-STAR complète. Une fois la conclusion atteinte, l'IA génère une réponse que le bot affiche. Ensuite, récupérez le fichier final.",
      code: "Analyse CO-STAR terminée.\n/export"
    }
  ];
</script>

<section id="steps" class="py-24 relative pointer-events-none">
  
  <div class="max-w-6xl mx-auto px-6 relative z-10 pointer-events-auto">
    
    <div class="text-center mb-20">
      <h2 class="text-3xl md:text-5xl font-bold text-white mb-6">
        De l'idée au prompt parfait <br />
        <span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-cyan-400">en 3 étapes.</span>
      </h2>
      <p class="text-slate-400">Basé sur un arbre de dialogue intelligent.</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 relative">
      
      <div class="hidden md:block absolute top-12 left-[16%] right-[16%] h-0.5 bg-gradient-to-r from-blue-900 via-cyan-900 to-blue-900 z-0"></div>

      {#each steps as step}
        <div class="relative flex flex-col items-center text-center group bg-slate-900/40 backdrop-blur-sm rounded-2xl p-4 border border-white/5 hover:border-blue-500/30 transition-colors">
          
          <div class="w-24 h-24 rounded-full bg-slate-800 border-4 border-slate-900 flex items-center justify-center mb-6 relative z-10 shadow-xl group-hover:scale-110 transition-transform duration-300">
            <span class="text-2xl font-bold text-blue-400 font-mono">{step.number}</span>
            <div class="absolute inset-0 rounded-full border border-blue-500/30 group-hover:border-blue-500/80 transition-colors"></div>
          </div>

          <h3 class="text-xl font-bold text-white mb-3">{step.title}</h3>
          <p class="text-slate-400 text-sm leading-relaxed mb-6 max-w-xs min-h-[80px]">
            {step.description}
          </p>

          <div class="w-full bg-slate-950 rounded-lg p-4 border border-slate-800 text-left shadow-inner flex flex-col gap-2 h-32 justify-center">
            <div class="flex gap-1.5 mb-1 opacity-50">
              <div class="w-2.5 h-2.5 rounded-full bg-red-500"></div>
              <div class="w-2.5 h-2.5 rounded-full bg-yellow-500"></div>
              <div class="w-2.5 h-2.5 rounded-full bg-green-500"></div>
            </div>
            
            <code class="text-xs font-mono text-cyan-300 block whitespace-pre-wrap leading-relaxed">
              {step.code}
            </code>
          </div>

        </div>
      {/each}

    </div>

  </div>
</section>