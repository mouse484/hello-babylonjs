<script lang="ts">
	import { Sound, type ISoundOptions, type Scene } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let scene: Scene;
	export let name = 'sound';
	export let path: string;
	export let options: ISoundOptions = {};

	onMount(() => {
		const sound = new Sound(name, path, scene, null, options);
	});
</script>
