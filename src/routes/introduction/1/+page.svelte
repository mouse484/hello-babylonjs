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
	<Mesh type="CreateBox" options={['box']} />
</Babylon>
