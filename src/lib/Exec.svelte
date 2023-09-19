<script lang="ts">
	import type { Scene } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let scene: Scene;
	export let command: (scene: Scene) => unknown;

	onMount(() => {
		command(scene);
	});
</script>
