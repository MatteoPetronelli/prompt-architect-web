<script lang="ts">
  import { T, useTask } from '@threlte/core';
  
  let rotation = 0;

  useTask(() => {
    rotation += 0.005;
  });
</script>

<T.AmbientLight intensity={0.5} />

<T.DirectionalLight position={[10, 10, 5]} intensity={1} />

<T.Mesh 
  position={[0, 0, 0]} 
  rotation.y={rotation} 
  rotation.z={rotation}
  scale={2}
>
  <T.IcosahedronGeometry args={[1, 0]} />
  
  <T.MeshStandardMaterial 
    color="#00ffff" 
    wireframe={true}
  />
</T.Mesh>