<script lang="ts">
	import '@babylonjs/core/Debug/debugLayer';

	import { Engine, Scene } from '@babylonjs/core';
	import { onMount } from 'svelte';

	let canvas: HTMLCanvasElement;
	let scene: Scene;

	let success = false;

	onMount(() => {
		const engine = new Engine(canvas, true);
		scene = new Scene(engine);

		engine.runRenderLoop(() => {
			scene.render();
		});

		success = true;
	});
</script>

<canvas bind:this={canvas} />

{#if success}
	<slot {scene} {canvas} />
{/if}

<style>
	canvas {
		width: 100%;
		height: 100%;
	}
</style>
