<script lang="ts">
	import '@babylonjs/core/Debug/debugLayer';

	import { Engine, Scene } from '@babylonjs/core';
	import { onMount } from 'svelte';

	let canvas: HTMLCanvasElement;
	let engine: Engine;
	let scene: Scene;

	let success = false;

	onMount(() => {
		engine = new Engine(canvas, true);
		scene = new Scene(engine);

		engine.runRenderLoop(() => {
			scene.render();
		});

		success = true;
	});
</script>

<svelte:window
	on:resize={() => {
		engine?.resize();
	}}
/>

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
