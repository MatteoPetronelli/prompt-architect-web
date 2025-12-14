<script lang="ts">
  import { Canvas } from '@threlte/core';
  import Scene from './Scene.svelte';
</script>

<div class="absolute inset-0 z-0 h-full w-full">
    <Canvas>
        <Scene />
    </Canvas>
</div>