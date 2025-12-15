<script lang="ts">
  import { T, useTask } from '@threlte/core';
  import { HTML, Environment } from '@threlte/extras';
  import { Vector3, Group, MathUtils } from 'three';

  const layoutHero: { id: string, position: [number, number, number] }[] = [
    { id: 'hero', position: [0, 5, 0] },
    { id: 'features', position: [-10, 0.5, 2] },
    { id: 'steps', position: [11, -0.5, -2] },
    { id: 'footer', position: [0, -5, 0] }
  ];

  const layoutList: { id: string, position: [number, number, number] }[] = [
    { id: 'hero', position: [14, 2.5, 0] },
    { id: 'features', position: [14, 1, 0] },
    { id: 'steps', position: [14, -0.5, 0] },
    { id: 'footer', position: [14, -2, 0] }
  ];

  const nodesData: Record<string, { label: string, color: string }> = {
    hero: { label: 'Accueil', color: '#60a5fa' },
    features: { label: 'Fonctionnalités', color: '#c084fc' },
    steps: { label: 'Guide', color: '#34d399' },
    footer: { label: 'Liens', color: '#f472b6' }
  };

  let scrollY = 0;
  let innerHeight = 0;
  $: isHeroMode = scrollY < innerHeight * 0.3;

  let group: Group;
  let hoveredNode: string | null = null;
  
  let currentNodes = layoutHero.map(n => ({
    id: n.id,
    x: n.position[0],
    y: n.position[1],
    z: n.position[2],
    scale: 1,
    rotation: Math.random() * 10,
    floatOffset: Math.random() * 100
  }));

  let lineOpacity = 0.15;
  let linePoints: Vector3[] = [];

  useTask((delta) => {
    if (group) {
        group.rotation.y = MathUtils.lerp(group.rotation.y, 0, delta * 2);
        group.rotation.z = MathUtils.lerp(group.rotation.z, 0, delta * 2);
    }
    const targetLineOpacity = isHeroMode ? 0.15 : 0;
    lineOpacity = MathUtils.lerp(lineOpacity, targetLineOpacity, delta * 5);

    currentNodes.forEach((node, i) => {
      const targetConfig = isHeroMode ? layoutHero[i] : layoutList[i];
      const speed = delta * 3;

      let targetX = targetConfig.position[0];
      let targetY = targetConfig.position[1];
      let targetZ = targetConfig.position[2];

      if (isHeroMode) {
          const time = Date.now() * 0.001;
          targetY += Math.sin(time + node.floatOffset) * 0.2; // Mouvement doux haut/bas
      }

      node.x = MathUtils.lerp(node.x, targetX, speed);
      node.y = MathUtils.lerp(node.y, targetY, speed);
      node.z = MathUtils.lerp(node.z, targetZ, speed);

      const isHovered = hoveredNode === node.id;
      const targetScale = isHovered ? 1.4 : 1;
      
      node.scale = MathUtils.lerp(node.scale, targetScale, delta * 8);
      node.rotation += delta * (isHovered ? 2 : 0.5); 
    });
    
    currentNodes = currentNodes;
  });

  $: linePoints = currentNodes.map(n => new Vector3(n.x, n.y, n.z));

  const handleNav = (id: string) => {
    const el = document.getElementById(id);
    if(el) el.scrollIntoView({ behavior: 'smooth' });
  };

</script>

<svelte:window bind:scrollY bind:innerHeight />

<Environment 
  url="https://dl.polyhaven.org/file/ph-assets/HDRIs/hdr/1k/studio_small_09_1k.hdr"
  isBackground={false}
/>

<T.PerspectiveCamera makeDefault position={[0, 0, 18]} fov={45} />

<T.AmbientLight intensity={0.2} />
<T.PointLight position={[10, 10, 10]} intensity={1} color="#4f46e5" />
<T.PointLight position={[-10, -10, -5]} intensity={2} color="#ec4899" />

<T.Group bind:ref={group}>
  
  {#if lineOpacity > 0.01}
    <T.Line>
      <T.BufferGeometry>
        <T.BufferAttribute
          args={[new Float32Array([...linePoints, linePoints[0] || new Vector3()].flatMap(v => [v.x, v.y, v.z])), 3]}
          attach="attributes-position"
        />
      </T.BufferGeometry>
      <T.LineBasicMaterial color="#94a3b8" transparent opacity={lineOpacity} linewidth={1} />
    </T.Line>
  {/if}

  {#each currentNodes as node}
    <T.Group 
      position={[node.x, node.y, node.z]}
      scale={node.scale}
    >
      
      <T.Mesh 
        visible={false}
        on:pointerenter={() => { document.body.style.cursor = 'pointer'; hoveredNode = node.id; }}
        on:pointerleave={() => { document.body.style.cursor = 'auto'; hoveredNode = null; }}
        on:click={() => handleNav(node.id)}
      >
          <T.SphereGeometry args={[1.5, 16, 16]} />
      </T.Mesh>

      <T.Mesh>
        <T.IcosahedronGeometry args={[0.3, 2]} /> 
        <T.MeshStandardMaterial
          color={nodesData[node.id].color}
          emissive={nodesData[node.id].color}
          emissiveIntensity={hoveredNode === node.id ? 3 : 1} 
          roughness={0.1}
          metalness={0.1}
        />
      </T.Mesh>

      <T.Group rotation.y={node.rotation} rotation.z={node.rotation * 0.5}>
          <T.Mesh>
            <T.IcosahedronGeometry args={[0.55, 1]} /> 
            <T.MeshStandardMaterial
              color={nodesData[node.id].color}
              wireframe={true}
              transparent
              opacity={0.3}
              emissive={nodesData[node.id].color}
              emissiveIntensity={0.5}
            />
          </T.Mesh>
      </T.Group>

      <T.Group rotation.x={node.rotation * -0.5}>
          <T.Mesh position={[0.7, 0, 0]}>
            <T.BoxGeometry args={[0.05, 0.05, 0.05]} />
            <T.MeshBasicMaterial color={nodesData[node.id].color} />
          </T.Mesh>
      </T.Group>

      <HTML position={isHeroMode ? [0, 0, 0] : [-0.5, 0, 0]} transform={false}>
          <div class="{isHeroMode ? 'flex justify-center' : 'flex justify-end pr-6'} w-48 -ml-24">
             <button 
                on:click={() => handleNav(node.id)}
                class="pointer-events-auto cursor-pointer px-3 py-1.5 rounded-lg text-xs font-bold text-white border border-white/10 backdrop-blur-md transition-all duration-300 tracking-widest uppercase hover:bg-white/10"
                style="
                    text-shadow: 0 2px 10px {nodesData[node.id].color};
                    opacity: {hoveredNode === node.id ? 1 : 0.7};
                    transform: scale({hoveredNode === node.id ? 1.1 : 1});
                    background: linear-gradient(to bottom, {nodesData[node.id].color}10, transparent);
                    
                    /* 2rem Validé : Le texte est proche et stable */
                    margin-top: {isHeroMode ? '2rem' : '0'};
                "
            >
                {nodesData[node.id].label}
            </button>
          </div>
      </HTML>

    </T.Group>
  {/each}

</T.Group>