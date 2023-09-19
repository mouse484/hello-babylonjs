<script lang="ts">
	import { ArcRotateCamera, Scene, Vector3 } from '@babylonjs/core';
	import { onMount } from 'svelte';

	export let scene: Scene;
	export let canvas: HTMLCanvasElement;

	export let camera: {
		alpha: number;
		beta: number;
		radius: number;
		target: [number, number, number];
	};

	onMount(() => {
		const arcCamera = new ArcRotateCamera(
			'Camera',
			camera.alpha,
			camera.beta,
			camera.radius,
			new Vector3(...camera.target),
			scene
		);
		arcCamera.attachControl(canvas, true);
	});
</script>
