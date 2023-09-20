<script lang="ts">
	import { Sound, type ISoundOptions, type Scene } from '@babylonjs/core';
	import { onDestroy, onMount } from 'svelte';

	let sound: Sound;

	export let scene: Scene;
	export let name = 'sound';
	export let path: string;
	export let options: ISoundOptions = {};

	onMount(() => {
		sound = new Sound(name, path, scene, null, options);
	});

	onDestroy(() => {
		sound.stop();
	});
</script>
