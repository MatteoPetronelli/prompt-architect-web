<script lang="ts">
  import Card from './Card.svelte';

  const features = [
    {
      title: "Méthode CO-STAR",
      description: "Ne laissez plus rien au hasard. Le bot guide vos utilisateurs pour structurer Context, Objective, Style, Tone, Audience et Response.",
      icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="7" height="7" x="3" y="3" rx="1"/><rect width="7" height="7" x="14" y="3" rx="1"/><rect width="7" height="7" x="14" y="14" rx="1"/><rect width="7" height="7" x="3" y="14" rx="1"/></svg>`
    },
    {
      title: "Export Instantané",
      description: "Transformez vos conversations en documents structurés. Exportez en Texte pour que les modéls d'IA les plus avacés fassent de vos idées une réalité.",
      icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" x2="12" y1="15" y2="3"/></svg>`
    },
    {
      title: "Conversation en Branches",
      description: "Une logique non-linéaire unique. Revenez en arrière, changez une décision dans l'arbre binaire et explorez différentes variations de votre prompt sans tout recommencer.",
      icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="6" x2="6" y1="3" y2="15"/><circle cx="18" cy="6" r="3"/><circle cx="6" cy="18" r="3"/><path d="M18 9a9 9 0 0 1-9 9"/></svg>` 
    },
    {
      title: "Sauvegarde & Chargement",
      description: "Bâtissez votre bibliothèque. Sauvegardez vos configurations de prompts préférées en JSON et rechargez-les instantanément pour itérer dessus plus tard.",
      icon: `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 21H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h11l5 5v11a2 2 0 0 1-2 2z"/><polyline points="17 21 17 13 7 13 7 21"/><polyline points="7 3 7 8 15 8"/></svg>`
    }
  ];
</script>

<section id="features" class="py-24 relative z-10">
  <div class="max-w-6xl mx-auto px-6">
    
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-5xl font-bold text-white mb-6">
        Plus qu'un simple bot, <br />
        <span class="text-blue-400">un architecte de pensée.</span>
      </h2>
      <p class="text-slate-400 max-w-2xl mx-auto text-lg">
        Conçu pour structurer vos idées complexes grâce à une navigation intelligente et une persistance des données.
      </p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
      {#each features as item}
        <Card 
          title={item.title} 
          description={item.description} 
          icon={item.icon} 
        />
      {/each}
    </div>

  </div>
</section>