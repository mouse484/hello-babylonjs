<script lang="ts">
	import { HemisphericLight, Scene, Vector3 } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let scene: Scene;
	export let vector: [number, number, number];

	onMount(() => {
		new HemisphericLight('light', new Vector3(...vector), scene);
	});
</script>
