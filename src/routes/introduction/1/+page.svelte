<script lang="ts">
	import ArcRotateCamera from '$lib/ArcRotateCamera.svelte';
	import Babylon from '$lib/Babylon.svelte';
	import Exec from '$lib/Exec.svelte';
	import HemisphericLight from '$lib/HemisphericLight.svelte';
	import { MeshBuilder } from '@babylonjs/core';
</script>

<Babylon let:scene let:canvas>
	<ArcRotateCamera
		{scene}
		{canvas}
		camera={{ alpha: -Math.PI / 2, beta: Math.PI / 2.5, radius: 3, target: [0, 1, 0] }}
	/>
	<HemisphericLight {scene} vector={[0, 1, 0]} />
	<Exec
		{scene}
		command={(scene) => {
			MeshBuilder.CreateBox('box', {}, scene);
		}}
	/>
</Babylon>
