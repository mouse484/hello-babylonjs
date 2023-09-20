<script lang="ts">
	import ArcRotateCamera from '$lib/ArcRotateCamera.svelte';
	import Babylon from '$lib/Babylon.svelte';
	import HemisphericLight from '$lib/HemisphericLight.svelte';
	import Mesh from '$lib/Mesh.svelte';
</script>

<Babylon let:scene let:canvas>
	<ArcRotateCamera
		{scene}
		{canvas}
		camera={{ alpha: -Math.PI / 2, beta: Math.PI / 2.5, radius: 15, target: [0, 0, 0] }}
	/>
	<HemisphericLight {scene} vector={[1, 1, 0]} />

	<Mesh type="CreateGround" options={['ground', { width: 10, height: 10 }]} />
	<Mesh
		type="CreateBox"
		options={['base']}
		exec={(box) => {
			box.position.y = 0.5;
		}}
	/>
	<Mesh
		type="CreateCylinder"
		options={['roof', { diameter: 1.3, height: 1.2, tessellation: 3 }]}
		exec={(roof) => {
			roof.scaling.x = 0.75;
			roof.rotation.z = Math.PI / 2;
			roof.position.y = 1.22;
		}}
	/>
</Babylon>
